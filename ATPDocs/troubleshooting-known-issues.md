---
title: Устранение известных неполадок с Azure ATP
description: В этой статье описываются способы устранения неполадок в службе Azure ATP.
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 09/07/2020
ms.topic: how-to
ms.collection: M365-security-compliance
ms.service: azure-advanced-threat-protection
ms.assetid: 23386e36-2756-4291-923f-fa8607b5518a
ms.reviewer: itargoet
ms.suite: ems
ms.openlocfilehash: 4153df2c2811217fcff813b333bdaf13fbe46858
ms.sourcegitcommit: 0c356b0860ae8663254e0cf6f04001bcc91ce207
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/21/2020
ms.locfileid: "90828453"
---
# <a name="troubleshooting-azure-atp-known-issues"></a>Устранение известных неполадок Azure ATP

## <a name="sensor-failure-communication-error"></a>Ошибка связи из-за сбоя датчика

Если вы получили следующую ошибку о сбое датчика, выполните описанные ниже действия:

System.Net.Http.HttpRequestException: An error occurred while sending the request. ---> System.Net.WebException: Не удалось подключиться к удаленному серверу. ---> System.Net.Sockets.SocketException: Попытка установить соединение была безуспешной, т.к. от другого компьютера за требуемое время не получен нужный отклик, или было разорвано уже установленное соединение из-за неверного отклика уже подключенного компьютера.

**Решение:**

Убедитесь, что для localhost (TCP-порт 444) не заблокирован обмен данными. Дополнительные сведения о предварительных требованиях Azure ATP см. в разделе [Порты](prerequisites.md#ports).

## <a name="deployment-log-location"></a>Расположение журнала развертывания

Журналы развертывания Azure ATP расположены во временном каталоге пользователя, установившего продукт. Расположение установки по умолчанию: C:\Users\Administrator\AppData\Local\Temp (или на один каталог выше %temp%). См. дополнительные сведения об [устранении неполадок с ATP при использовании журналов](troubleshooting-using-logs.md).

## <a name="proxy-authentication-problem-presents-as-a-licensing-error"></a>Проблема с аутентификацией прокси-сервера отображается как ошибка лицензирования

Во время установки датчика возникает следующая ошибка:  **The sensor failed to register due to licensing issues** (Не удалось зарегистрировать датчик из-за проблем с лицензированием).

**Записи журнала развертывания:**

[1C60:1AA8][2018-03-24T23:59:13]i000: 2018-03-25 02:59:13.1237 Info  InteractiveDeploymentManager ValidateCreateSensorAsync returned [validateCreateSensorResult=LicenseInvalid]] [1C60:1AA8][2018-03-24T23:59:56]i000: 2018-03-25 02:59:56.4856 Info  InteractiveDeploymentManager ValidateCreateSensorAsync returned [validateCreateSensorResult=LicenseInvalid]] [1C60:1AA8][2018-03-25T00:27:56]i000: 2018-03-25 03:27:56.7399 Debug SensorBootstrapperApplication Engine.Quit [deploymentResultStatus=1602 isRestartRequired=False]] [1C60:15B8][2018-03-25T00:27:56]i500: Shutting down, exit code: 0x642

**Причина**.

Когда обмен данными выполняется через прокси-сервер, во время аутентификации он может отвечать на обращение датчика Azure ATP, возвращая ошибку 401 или 403 вместо ошибки 407. Датчик Azure ATP будет интерпретировать ошибку 401 или 403 как проблему с лицензированием, а не с аутентификацией прокси-сервера.

**Решение:**

Датчик должен обращаться по адресу *.atp.azure.com через настроенный прокси-сервер без аутентификации. См. дополнительные сведения о [настройке прокси-сервера для включения обмена данными](configure-proxy.md).

## <a name="proxy-authentication-problem-presents-as-a-connection-error"></a>Проблема с аутентификацией прокси-сервера отображается как ошибка подключения

Во время установки датчика возникает следующая ошибка: **Датчику не удалось подключиться к службе.**

**Причина.**

Проблема может возникать из-за ошибки конфигурации прозрачного прокси-сервера в Server Core, например когда требуемые Azure ATP корневые сертификаты не актуальны или отсутствуют.

**Решение:**

Выполните следующий командлет PowerShell, чтобы проверить существование доверенного корневого сертификата службы Azure ATP в системе Server Core. В следующем примере используется сертификат DigiCert Baltimore Root и DigiCert Global Root.

```powershell
Get-ChildItem -Path "Cert:\LocalMachine\Root" | where { $_.Thumbprint -eq "D4DE20D05E66FC53FE1A50882C78DB2852CAE474"} | fl
Get-ChildItem -Path "Cert:\LocalMachine\Root" | where { $_.Thumbprint -eq "df3c24f9bfd666761b268073fe06d1cc8d4f82a4"} | fl
```

```Output
Subject      : CN=Baltimore CyberTrust Root, OU=CyberTrust, O=Baltimore, C=IE
Issuer       : CN=Baltimore CyberTrust Root, OU=CyberTrust, O=Baltimore, C=IE
Thumbprint   : D4DE20D05E66FC53FE1A50882C78DB2852CAE474
FriendlyName : DigiCert Baltimore Root
NotBefore    : 5/12/2000 11:46:00 AM
NotAfter     : 5/12/2025 4:59:00 PM
Extensions   : {System.Security.Cryptography.Oid, System.Security.Cryptography.Oid, System.Security.Cryptography.Oid}

Subject      : CN=DigiCert Global Root G2, OU=www.digicert.com, O=DigiCert Inc, C=US
Issuer       : CN=DigiCert Global Root G2, OU=www.digicert.com, O=DigiCert Inc, C=US
Thumbprint   : DF3C24F9BFD666761B268073FE06D1CC8D4F82A4
FriendlyName : DigiCert Global Root G2
NotBefore    : 01/08/2013 15:00:00
NotAfter     : 15/01/2038 14:00:00
Extensions   : {System.Security.Cryptography.Oid, System.Security.Cryptography.Oid, System.Security.Cryptography.Oid}
```

Если ожидаемые выходные данные не отобразятся, выполните следующие действия:

1. Скачайте корневой сертификат [Baltimore CyberTrust](https://cacert.omniroot.com/bc2025.crt) и [DigiCert Global Root G2](https://cacerts.digicert.com/DigiCertGlobalRootG2.crt) на компьютер с Server Core.
1. Запустите следующий командлет PowerShell, чтобы установить сертификат.

    ```powershell
    Import-Certificate -FilePath "<PATH_TO_CERTIFICATE_FILE>\bc2025.crt" -CertStoreLocation Cert:\LocalMachine\Root
    Import-Certificate -FilePath "<PATH_TO_CERTIFICATE_FILE>\DigiCertGlobalRootG2.crt" -CertStoreLocation Cert:\LocalMachine\Root
    ```

## <a name="silent-installation-error-when-attempting-to-use-powershell"></a>Ошибка автоматической установки при попытке использовать PowerShell

Во время автоматической установки датчика при попытке использовать PowerShell может произойти следующая ошибка:

```powershell
"Azure ATP sensor Setup.exe" "/quiet" NetFrameworkCommandLineArguments="/q" Acce ... Unexpected token '"/quiet"' in expression or statement."
```

**Причина.**

Эту ошибку вызывает отсутствие префикса ./, необходимого для установки при использовании PowerShell.

**Решение:**

Для успешной установки используйте полную команду.

```powershell
./"Azure ATP sensor Setup.exe" /quiet NetFrameworkCommandLineArguments="/q" AccessKey="<Access Key>"
```

## <a name="azure-atp-sensor-nic-teaming-issue"></a>Проблема с датчиком ATP на компьютере с функцией объединения сетевых карт <a name="nic-teaming"></a>

При попытке установить датчик ATP на компьютере, настроенном с функцией объединения сетевых карт, возникает ошибка установки. Чтобы установить датчик ATP на компьютере с функцией объединения сетевых карт, следуйте приведенным ниже инструкциям:

1. Скачайте установщик Npcap версии 0.9984 по адресу [https://nmap.org/npcap/](https://nmap.org/npcap/dist/npcap-0.9984.exe).
    - Кроме того, запросите в службе техподдержки OEM-версию драйвера Npcap (который поддерживает автоматическую установку).
    - Копии Npcap не учитываются в лицензионных ограничениях на пять копий, пять компьютеров или пять пользователей, если они установлены и используются исключительно совместно с Azure ATP. Дополнительные сведения см. в разделе [Лицензирование NPCAP](https://github.com/nmap/npcap/blob/master/LICENSE).

Если вы еще не установили датчик:

1. Удалите библиотеку WinPcap, если она установлена.
1. Установите Npcap со следующими параметрами: loopback_support=no, winpcap_mode=yes.
    - При использовании установщика графического пользовательского интерфейса снимите флажок **поддержка замыкания на себя**, а затем выберите режим **WinPcap**.
1. Установите пакет датчика.

Если вы уже установили датчик, сделайте следующее:

1. Удалите датчик.
1. Удалите WinPcap.
1. Установите Npcap со следующими параметрами: loopback_support=no, winpcap_mode=yes.
    - При использовании установщика графического пользовательского интерфейса снимите флажок **поддержка замыкания на себя**, а затем выберите режим **WinPcap**.
1. Переустановите пакет датчика.

## <a name="multi-processor-group-mode"></a>Многопроцессорный групповой режим

В операционных системах Windows 2008 R2 и 2012 датчик Azure ATP не поддерживается в многопроцессорном групповом режиме.

Возможные обходные пути:

- Если технология Hyper-Threading включена, отключите ее. Это может сократить количество логических ядер, чтобы избежать необходимости запуска в **многопроцессорном групповом** режиме.

- Если у виртуальной машины менее 64 логических ядер и она выполняется на узле HP, для параметра BIOS **NUMA Group Size Optimization** (Оптимизация размера группы NUMA) можно изменить значение по умолчанию **Clustered** (Кластеризовано) значением **Flat** (Фиксировано).

## <a name="microsoft-defender-atp-integration-issue"></a>Проблема с интеграцией ATP в Microsoft Defender

Службу "Расширенная защита от угроз Azure" можно интегрировать с ATP в Microsoft Defender. Дополнительные сведения см. в статье [Интеграция Расширенной защиты от угроз Azure с ATP в Microsoft Defender](integrate-msde.md).

## <a name="vmware-virtual-machine-sensor-issue"></a>Проблема с датчиком виртуальной машины VMware

Если на виртуальных машинах VMware установлен датчик Azure ATP, может появиться оповещение о работоспособности **Some network traffic is not being analyzed** (Часть сетевого трафика не анализируется). Это может происходить из-за несоответствия конфигураций в VMware.

Чтобы решить эту проблему, выполните указанные ниже действия.

Установите для следующего параметра значение **Disabled** (Отключено) в конфигурации сетевого адаптера виртуальной машины: **IPv4 TSO Offload**.

 ![Проблема с датчиком VMware](media/vm-sensor-issue.png)

Используйте следующую команду, чтобы проверить, включена или отключена ли Разгрузка большой отправки (LSO).

`Get-NetAdapterAdvancedProperty | Where-Object DisplayName -Match "^Large*"`

![Проверка состояния LSO](media/missing-network-traffic-health-alert.png)

Если параметр LSO включен, отключите его с помощью следующей команды:

`Disable-NetAdapterLso -Name {name of adapter}`

![Состояние отключения LSO](media/disable-lso-vmware.png)

## <a name="sensor-failed-to-retrieve-group-managed-service-account-gmsa-credentials"></a>Датчику не удалось получить учетные данные групповой управляемой учетной записи службы (gMSA)

Если вы получаете следующее оповещение о работоспособности: **Неправильные учетные данные пользователя служб каталогов**

**Записи журнала датчика:**

2020-02-17 14:01:36.5315 Info ImpersonationManager CreateImpersonatorAsync started [UserName=account_name Domain=domain1.test.local IsGroupManagedServiceAccount=True] 2020-02-17 14:01:36.5750 Info ImpersonationManager CreateImpersonatorAsync finished [UserName=account_name Domain=domain1.test.local IsSuccess=False]

**Записи журнала обновления датчика:**

2020-02-17 14:02:19.6258 Warn GroupManagedServiceAccountImpersonationHelper GetGroupManagedServiceAccountAccessTokenAsync failed GMSA password could not be retrieved [errorCode=AccessDenied AccountName=account_name DomainDnsName=domain1.test.local]

**Причина**.

Датчику не удалось получить назначенную учетную запись gMSA с портала Azure ATP.

**Решение:**

Убедитесь, что учетные данные учетной записи gMSA правильные и что датчик предоставил разрешение на получение учетных данных учетной записи. В примененной политике может потребоваться добавить учетную запись gMSA в назначения прав пользователя **Вход в качестве службы**.

## <a name="report-downloads-cannot-contain-more-than-300000-entries"></a>Скачиваемые отчеты не могут содержать больше 300 000 записей

Azure ATP не поддерживает скачивание отчетов, содержащих больше 300 000 записей. Отчеты, в которых больше 300 000 записей, будут отображаться неполными.

**Причина**.

Это инженерное ограничение.

**Решение:**

Известного решения не существует.

## <a name="see-also"></a>См. также

- [Предварительные требования к Azure ATP](prerequisites.md)
- [Планирование производительности Azure ATP](capacity-planning.md)
- [Настройка сбора данных о событиях](configure-event-collection.md)
- [Настройка пересылки событий Windows](configure-event-forwarding.md)
- [Загляните на форум Azure ATP!](https://aka.ms/azureatpcommunity)
