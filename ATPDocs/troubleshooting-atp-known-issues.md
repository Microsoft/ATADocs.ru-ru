---
title: Устранение известных неполадок Azure ATP | Документация Майкрософт
description: В этой статье описываются способы устранения неполадок в службе Azure ATP.
keywords: ''
author: shsagir
ms.author: shsagir
manager: rkarlin
ms.date: 02/06/2020
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.service: azure-advanced-threat-protection
ms.assetid: 23386e36-2756-4291-923f-fa8607b5518a
ms.reviewer: itargoet
ms.suite: ems
ms.openlocfilehash: d84102528e3423ed149cdc64c010a7f190a40f68
ms.sourcegitcommit: 20cf564885aa01985524c9c995ae5ba282606fac
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2020
ms.locfileid: "77045129"
---
# <a name="troubleshooting-azure-atp-known-issues"></a>Устранение известных неполадок Azure ATP

## <a name="sensor-failure-communication-error"></a>Ошибка связи из-за сбоя датчика

Если вы получили следующую ошибку о сбое датчика, выполните описанные ниже действия:

System.Net.Http.HttpRequestException: An error occurred while sending the request. ---> System.Net.WebException: Не удалось подключиться к удаленному серверу. ---> System.Net.Sockets.SocketException: Попытка установить соединение была безуспешной, т.к. от другого компьютера за требуемое время не получен нужный отклик, или было разорвано уже установленное соединение из-за неверного отклика уже подключенного компьютера.

**Решение:**

Убедитесь, что для localhost (TCP-порт 444) не заблокирован обмен данными. Дополнительные сведения о предварительных требованиях Azure ATP см. в разделе [Порты](atp-prerequisites.md#ports).

## <a name="deployment-log-location"></a>Расположение журнала развертывания

Журналы развертывания Azure ATP расположены во временном каталоге пользователя, установившего продукт. Расположение установки по умолчанию: C:\Users\Administrator\AppData\Local\Temp (или на один каталог выше %temp%). См. дополнительные сведения об [устранении неполадок с ATP при использовании журналов](troubleshooting-atp-using-logs.md).

## <a name="proxy-authentication-problem-presents-as-a-licensing-error"></a>Проблема с аутентификацией прокси-сервера отображается как ошибка лицензирования

Во время установки датчика возникает следующая ошибка:  **The sensor failed to register due to licensing issues** (Не удалось зарегистрировать датчик из-за проблем с лицензированием).

Deployment log entries: [1C60:1AA8][2018-03-24T23:59:13]i000: 2018-03-25 02:59:13.1237 Info  InteractiveDeploymentManager ValidateCreateSensorAsync returned [\[]validateCreateSensorResult=LicenseInvalid[\]] [1C60:1AA8][2018-03-24T23:59:56]i000: 2018-03-25 02:59:56.4856 Info  InteractiveDeploymentManager ValidateCreateSensorAsync returned [\[]validateCreateSensorResult=LicenseInvalid[\]] [1C60:1AA8][2018-03-25T00:27:56]i000: 2018-03-25 03:27:56.7399 Debug SensorBootstrapperApplication Engine.Quit [\[]deploymentResultStatus=1602 isRestartRequired=False[\]] [1C60:15B8][2018-03-25T00:27:56]i500: Shutting down, exit code: 0x642


**Причина**.

Когда обмен данными выполняется через прокси-сервер, во время аутентификации он может отвечать на обращение датчика Azure ATP, возвращая ошибку 401 или 403 вместо ошибки 407. Датчик Azure ATP будет интерпретировать ошибку 401 или 403 как проблему с лицензированием, а не с аутентификацией прокси-сервера.

**Решение:**

Датчик должен обращаться по адресу *.atp.azure.com через настроенный прокси-сервер без аутентификации. См. дополнительные сведения о [настройке прокси-сервера для включения обмена данными](configure-proxy.md).

## <a name="silent-installation-error-when-attempting-to-use-powershell"></a>Ошибка автоматической установки при попытке использовать PowerShell

Во время автоматической установки датчика при попытке использовать PowerShell может произойти следующая ошибка:

    "Azure ATP sensor Setup.exe" "/quiet" NetFrameworkCommandLineArguments="/q" Acce ...           Unexpected token '"/quiet"' in expression or statement."

**Причина**. Эту ошибку вызывает отсутствие префикса ./, необходимого для установки при использовании PowerShell.

**Решение:** Для успешной установки используйте полную команду.

    ./"Azure ATP sensor Setup.exe" /quiet NetFrameworkCommandLineArguments="/q" AccessKey="<Access Key>"

## Проблема с датчиком ATP на компьютере с функцией объединения сетевых карт <a name="nic-teaming"></a>

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

## <a name="windows-defender-atp-integration-issue"></a>Проблема интеграции ATP в Защитнике Windows

Azure Advanced Threat Protection позволяет интегрировать Azure ATP с ATP в Защитнике Windows. Дополнительные сведения см. в статье [Интеграция Azure ATP с ATP в Защитнике Windows](integrate-wd-atp.md).

## <a name="vmware-virtual-machine-sensor-issue"></a>Проблема с датчиком виртуальной машины VMware

Если на виртуальных машинах VMware установлен датчик Azure ATP, может появиться предупреждение системы мониторинга **Some network traffic is not being analyzed** (Часть сетевого трафика не анализируется). Это может происходить из-за несоответствия конфигураций в VMware.

Чтобы решить эту проблему, выполните указанные ниже действия.

Установите для следующего параметра значение **Disabled** (Отключено) в конфигурации сетевого адаптера виртуальной машины: **IPv4 TSO Offload**.

 ![Проблема с датчиком VMware](./media/vm-sensor-issue.png)

Используйте следующую команду, чтобы проверить, включена или отключена ли Разгрузка большой отправки (LSO).

`Get-NetAdapterAdvancedProperty | Where-Object DisplayName -Match "^Large*"`

![Проверка состояния LSO](./media/missing-network-traffic-health-alert.png)

Если параметр LSO включен, отключите его с помощью следующей команды:

`Disable-NetAdapterLso -Name {name of adapter}`

![Состояние отключения LSO](./media/disable-lso-vmware.png)


## <a name="see-also"></a>См. также
- [Предварительные требования к Azure ATP](atp-prerequisites.md)
- [Планирование производительности Azure ATP](atp-capacity-planning.md)
- [Настройка сбора данных о событиях](configure-event-collection.md)
- [Настройка пересылки событий Windows](configure-event-forwarding.md)
- [Загляните на форум Azure ATP!](https://aka.ms/azureatpcommunity)
