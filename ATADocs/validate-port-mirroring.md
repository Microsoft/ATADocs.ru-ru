---
title: Проверка зеркального отображения портов в Advanced Threat Analytics
description: Описание проверки правильной настройки зеркального отображения портов.
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 3/21/2018
ms.topic: conceptual
ms.prod: advanced-threat-analytics
ms.technology: ''
ms.assetid: ebd41719-c91a-4fdd-bcab-2affa2a2cace
ms.reviewer: bennyl
ms.suite: ems
ms.openlocfilehash: 7677cbdb0f6b236d0be4230a1166026053ac2acc
ms.sourcegitcommit: e844155ea57f73dfe2b47f4c5c1c7f5292ccbf1e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2020
ms.locfileid: "94689570"
---
# <a name="validate-port-mirroring"></a>Проверка зеркального отображения портов

[!INCLUDE [Banner for top of topics](includes/banner.md)]

> [!NOTE]
> Эта статья имеет отношение только к развертыванию шлюзов ATA, а не упрощенных шлюзов ATA. Чтобы определить, нужно ли использовать шлюзы ATA, ознакомьтесь со статьей [Выбор правильных шлюзов для развертывания](ata-capacity-planning.md#choosing-the-right-gateway-type-for-your-deployment).

Ниже описана последовательность проверки правильной настройки зеркального отображения портов. Для правильной работы решения ATA шлюз ATA должен видеть входящий и исходящий трафик контроллера домена. Основные сведения, требуемые для работы ATA, решение получает посредством тщательного анализа пакетов входящего и исходящего сетевого трафика контроллеров домена. Чтобы решение ATA могло видеть сетевой трафик, нужно настроить зеркальное отображение портов. Эта функция копирует трафик из одного порта (исходный порт) в другой порт (конечный порт).

## <a name="validate-port-mirroring-using-a-windows-powershell-script"></a>Проверка зеркального отображения портов с помощью сценария Windows PowerShell

1. Сохраните текст этого сценария в файл с именем *ATAdiag.ps1*.
1. Выполните этот скрипт в шлюзе ATA, который нужно проверить.
Этот сценарий создает ICMP-трафик от шлюза ATA в контроллер домена и ищет этот трафик в сетевом адаптере в контроллере домена.
Если шлюз ATA видит, что IP-адрес назначения ICMP-трафика соответствует IP-адресу контроллера домена, введенному в консоли ATA, зеркальное отображение портов считается настроенным.

Пример выполнения сценария:

```powershell
# ATAdiag.ps1 -CaptureIP n.n.n.n -DCIP n.n.n.n -TestCount n
param([parameter(Mandatory=$true)][string]$CaptureIP, [parameter(Mandatory=$true)][string]$DCIP, [int]$PingCount = 10)

# Set variables
$ErrorActionPreference = "stop"
$starttime = get-date
$byteIn = new-object byte[] 4
$byteOut = new-object byte[] 4
$byteData = new-object byte[] 4096  # size of data

$byteIn[0] = 1  # for promiscuous mode
$byteIn[1-3] = 0
$byteOut[0-3] = 0

# Convert network data to host format
function NetworkToHostUInt16 ($value)
{
    [Array]::Reverse($value)
    [BitConverter]::ToUInt16($value,0)
}
function NetworkToHostUInt32 ($value)
{
    [Array]::Reverse($value)
    [BitConverter]::ToUInt32($value,0)
}
function ByteToString ($value)
{
    $AsciiEncoding = new-object system.text.asciiencoding
    $AsciiEncoding.GetString($value)
}

Write-Host "Testing Port Mirroring..." -ForegroundColor Yellow
Write-Host ""
Write-Host "Here is a summary of the connection we will test." -ForegroundColor Yellow

# Initialize a first ping connection
Test-Connection -Count 1 -ComputerName $DCIP -ea SilentlyContinue
Write-Host ""
Write-Host "Press any key to continue..." -ForegroundColor Red
[void][System.Console]::ReadKey($true)
Write-Host ""
Write-Host "Sending ICMP and Capturing data..." -ForegroundColor Yellow

# Open a socket
$socket = new-object system.net.sockets.socket([Net.Sockets.AddressFamily]::InterNetwork,[Net.Sockets.SocketType]::Raw,[Net.Sockets.ProtocolType]::IP)

# Include the IP header
$socket.setsocketoption("IP","HeaderIncluded",$true)
$socket.ReceiveBufferSize = 10000
$ipendpoint = new-object system.net.ipendpoint([net.ipaddress]"$CaptureIP",0)
$socket.bind($ipendpoint)

# Enable promiscuous mode
[void]$socket.iocontrol([net.sockets.iocontrolcode]::ReceiveAll,$byteIn,$byteOut)

# Initialize test variables
$tests = 0
$TestResult = "Noise"
$OneSuccess = 0

while ($tests -le $PingCount)
{
    if (!$socket.Available)  # see if any packets are in the queue
    {
        start-sleep -milliseconds 500
        continue
    }

    # Capture traffic
    $rcv = $socket.receive($byteData,0,$byteData.length,[net.sockets.socketflags]::None)

    # Decode the header so we can read ICMP
    $MemoryStream = new-object System.IO.MemoryStream($byteData,0,$rcv)
    $BinaryReader = new-object System.IO.BinaryReader($MemoryStream)

    # Set IP version & header length
    $VersionAndHeaderLength = $BinaryReader.ReadByte()

    # TOS
    $TypeOfService= $BinaryReader.ReadByte()

    # More values, and the Protocol Number for ICMP traffic
    # Convert network format of big-endian to host format of little-endian
    $TotalLength = NetworkToHostUInt16 $BinaryReader.ReadBytes(2)
    $Identification = NetworkToHostUInt16 $BinaryReader.ReadBytes(2)
    $FlagsAndOffset = NetworkToHostUInt16 $BinaryReader.ReadBytes(2)
    $TTL = $BinaryReader.ReadByte()
    $ProtocolNumber = $BinaryReader.ReadByte()
    $Checksum = [Net.IPAddress]::NetworkToHostOrder($BinaryReader.ReadInt16())

    # The source and destination IP addresses
    $SourceIPAddress = $BinaryReader.ReadUInt32()
    $DestinationIPAddress = $BinaryReader.ReadUInt32()

    # The source and destimation ports
    $sourcePort = [uint16]0
    $destPort = [uint16]0

    # Close the stream reader
    $BinaryReader.Close()
    $memorystream.Close()

    # Cast DCIP into an IPaddress type
    $DCIPP = [ipaddress] $DCIP
    $DestinationIPAddressP = [ipaddress] $DestinationIPAddress

    #Ping the DC at the end after starting the capture
    Test-Connection -Count 1 -ComputerName $DCIP -ea SilentlyContinue | Out-Null

    # This is the match logic - check to see if Destination IP from the Ping sent matches the DCIP entered by in the ATA Console
    # The only way the ATA Gateway should see a destination of the DC is if Port Spanning is configured

    if ($DestinationIPAddressP -eq $DCIPP)  # is the destination IP eq to the DC IP?
    {
        $TestResult = "Port Spanning success!"
        $OneSuccess = 1
    } else {
        $TestResult = "Noise"
    }

    # Put source, destination, test result in Powershell object
    new-object psobject | add-member -pass noteproperty CaptureSource $([system.net.ipaddress]$SourceIPAddress) | add-member -pass noteproperty CaptureDestination $([system.net.ipaddress]$DestinationIPAddress) | Add-Member -pass NoteProperty Result $TestResult | Format-List | Out-Host
    #Count tests
    $tests ++
}

if ($OneSuccess -eq 1)
{
    Write-Host "Port Spanning Success!" -ForegroundColor Green
    Write-Host ""
    Write-Host "At least one packet which was addressed to the DC, was picked up by the Gateway." -ForegroundColor Yellow
    Write-Host "A little noise is OK, but if you don't see a majority of successes, you might want to re-run." -ForegroundColor Yellow
} else {
    Write-Host "No joy, all noise.  You may want to re-run, increase the number of Ping Counts, or check your config." -ForegroundColor Red
}

Write-Host ""
Write-Host "Press any key to continue..." -ForegroundColor Red
[void][System.Console]::ReadKey($true)
```

## <a name="validate-port-mirroring-using-net-mon"></a>Проверка зеркального отображения портов с помощью сетевого монитора
1. Установите [Microsoft Network Monitor 3,4](https://www.microsoft.com/download/details.aspx?id=4865) на шлюз ATA, который требуется проверить.

    > [!IMPORTANT]
    > Не устанавливайте на шлюз ATA анализатор сообщений Microsoft Message Analyzer или другое программное обеспечение для записи сетевого трафика.

1. Откройте сетевой монитор и создайте новую вкладку записи.

    1. Выберите только сетевой адаптер для записи (**Capture**) или сетевой адаптер, подключенный к порту коммутатора, который настроен как конечный порт.

    1. Активируйте неизбирательный режим.

    1. Щелкните **New Capture** (Создать запись).

        ![Создание новой вкладки записи (рисунок)](media/ATA-Port-Mirroring-Capture.jpg)

1. В окне Display Filter (Фильтр отображения) укажите фильтр **KerberosV5 OR LDAP** и нажмите кнопку **Apply** (Применить).

    ![Применение фильтра "KerberosV5 или LDAP" (рисунок)](media/ATA-Port-Mirroring-filter-settings.jpg)

1. Щелкните **Start** (Начать), чтобы начать сеанс записи. Если входящий и исходящий трафик контроллера домена не отображается, проверьте настройки зеркального отображения портов.

    ![Начало сеанса записи (рисунок)](media/ATA-Port-Mirroring-Capture-traffic.jpg)

    > [!NOTE]
    > Очень важно убедиться, что вы видите входящий и исходящий трафик контроллера домена.

1. Если вы видите только входящий или исходящий трафик, обратитесь за помощью к специалистам по сетям или виртуализации. Они помогут вам устранить ошибки в настройках зеркального отображения портов.

## <a name="see-also"></a>См. также:

- [Настройка зеркального отображения портов](configure-port-mirroring.md)
- [Обязательно ознакомьтесь с форумом ATA.](https://social.technet.microsoft.com/Forums/security/home?forum=mata)
