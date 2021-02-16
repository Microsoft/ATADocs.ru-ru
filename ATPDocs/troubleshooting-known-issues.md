---
title: Устранение известных проблем в защитнике Майкрософт
description: В этой статье описывается, как устранять неполадки в защитнике Майкрософт для идентификации.
ms.date: 02/04/2021
ms.topic: how-to
ms.openlocfilehash: f11d840aa46ec86c88c04ea2892443fd2dc20db3
ms.sourcegitcommit: a892419a5cb95412e4643c35a9a72092421628ec
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/16/2021
ms.locfileid: "100534503"
---
# <a name="troubleshooting-microsoft-defender-for-identity-known-issues"></a>Устранение известных проблем в защитнике Майкрософт

## <a name="sensor-failure-communication-error"></a>Ошибка связи из-за сбоя датчика

Если вы получили следующую ошибку о сбое датчика, выполните описанные ниже действия:

System.Net.Http.HttpRequestException: An error occurred while sending the request. ---> System.Net.WebException: Не удалось подключиться к удаленному серверу. ---> System.Net.Sockets.SocketException: Попытка установить соединение была безуспешной, т.к. от другого компьютера за требуемое время не получен нужный отклик, или было разорвано уже установленное соединение из-за неверного отклика уже подключенного компьютера.

**Решение:**

Убедитесь, что для localhost (TCP-порт 444) не заблокирован обмен данными. Дополнительные сведения о [!INCLUDE [Product long](includes/product-long.md)] предварительных требованиях см. в разделе [порты](prerequisites.md#ports).

## <a name="deployment-log-location"></a>Расположение журнала развертывания

[!INCLUDE [Product short](includes/product-short.md)]Журналы развертывания находятся во временном каталоге пользователя, установившего продукт. Расположение установки по умолчанию: C:\Users\Administrator\AppData\Local\Temp (или на один каталог выше %temp%). Дополнительные сведения см. в разделе [Устранение неполадок [!INCLUDE [Product short](includes/product-short.md)] с помощью журналов](troubleshooting-using-logs.md) .

## <a name="proxy-authentication-problem-presents-as-a-licensing-error"></a>Проблема с аутентификацией прокси-сервера отображается как ошибка лицензирования

Во время установки датчика возникает следующая ошибка:  **The sensor failed to register due to licensing issues** (Не удалось зарегистрировать датчик из-за проблем с лицензированием).

**Записи журнала развертывания:**

[1C60:1AA8][2018-03-24T23:59:13]i000: 2018-03-25 02:59:13.1237 Info  InteractiveDeploymentManager ValidateCreateSensorAsync returned [validateCreateSensorResult=LicenseInvalid]] [1C60:1AA8][2018-03-24T23:59:56]i000: 2018-03-25 02:59:56.4856 Info  InteractiveDeploymentManager ValidateCreateSensorAsync returned [validateCreateSensorResult=LicenseInvalid]] [1C60:1AA8][2018-03-25T00:27:56]i000: 2018-03-25 03:27:56.7399 Debug SensorBootstrapperApplication Engine.Quit [deploymentResultStatus=1602 isRestartRequired=False]] [1C60:15B8][2018-03-25T00:27:56]i500: Shutting down, exit code: 0x642

**Причина**.

В некоторых случаях при обмене данными через прокси-сервер во время проверки подлинности он может ответить на [!INCLUDE [Product short](includes/product-short.md)] датчик с ошибкой 401 или 403 вместо ошибки 407. [!INCLUDE [Product short](includes/product-short.md)]Датчик будет интерпретировать ошибку 401 или 403 в качестве проблемы с лицензией и не является проблемой проверки подлинности прокси-сервера.

**Решение:**

Датчик должен обращаться по адресу *.atp.azure.com через настроенный прокси-сервер без аутентификации. См. дополнительные сведения о [настройке прокси-сервера для включения обмена данными](configure-proxy.md).

## <a name="proxy-authentication-problem-presents-as-a-connection-error"></a>Проблема с аутентификацией прокси-сервера отображается как ошибка подключения

Во время установки датчика возникает следующая ошибка: **Датчику не удалось подключиться к службе.**

**Причина.**

Эта неполадка может быть вызвана ошибкой конфигурации прозрачного прокси-сервера в Server Core, например, если корневые сертификаты, необходимые для, [!INCLUDE [Product short](includes/product-short.md)] не являются актуальными или отсутствуют.

**Решение:**

Выполните следующий командлет PowerShell, чтобы убедиться, что [!INCLUDE [Product short](includes/product-short.md)] доверенный корневой сертификат службы существует на сервере Core. В следующем примере используется сертификат DigiCert Baltimore Root и DigiCert Global Root.

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

<a name="nic-teaming"></a>

## <a name="defender-for-identity-sensor-nic-teaming-issue"></a>Защитник для проблемы объединения сетевых адаптеров датчика удостоверений

При попытке установить [!INCLUDE [Product short](includes/product-short.md)] датчик на компьютере, настроенном с помощью адаптера объединения сетевых карт, возникает ошибка установки. Если вы хотите установить [!INCLUDE [Product short](includes/product-short.md)] датчик на компьютере, где настроено объединение сетевых карт, выполните следующие действия:

1. Скачайте установщик Npcap версии 1,0 из  [https://nmap.org/npcap/](https://nmap.org/npcap/dist/npcap-1.00.exe) .
    - Кроме того, запросите в службе техподдержки OEM-версию драйвера Npcap (который поддерживает автоматическую установку).
    - Копии Npcap не учитываются с пятью, пятью компьютерами или пятью ограничениями на лицензирование пользователей, если они установлены и используются исключительно вместе с [!INCLUDE [Product short](includes/product-short.md)] . Дополнительные сведения см. в разделе [Лицензирование NPCAP](https://github.com/nmap/npcap/blob/master/LICENSE).

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

В операционных системах Windows 2008 R2 и 2012 датчик [!INCLUDE [Product short](includes/product-short.md)] не поддерживается в многопроцессорном групповом режиме.

Возможные обходные пути:

- Если технология Hyper-Threading включена, отключите ее. Это может сократить количество логических ядер, чтобы избежать необходимости запуска в **многопроцессорном групповом** режиме.

- Если у виртуальной машины менее 64 логических ядер и она выполняется на узле HP, для параметра BIOS **NUMA Group Size Optimization** (Оптимизация размера группы NUMA) можно изменить значение по умолчанию **Clustered** (Кластеризовано) значением **Flat** (Фиксировано).

## <a name="microsoft-defender-for-endpoint-integration-issue"></a>Проблемы с интеграцией конечных точек в защитнике Майкрософт

[!INCLUDE [Product short](includes/product-short.md)] позволяет интегрироваться [!INCLUDE [Product short](includes/product-short.md)] с защитником Майкрософт для конечной точки. Дополнительные сведения см. [в разделе Интеграция [!INCLUDE [Product short](includes/product-short.md)] с защитником Майкрософт для конечных точек](integrate-mde.md) .

## <a name="vmware-virtual-machine-sensor-issue"></a>Проблема с датчиком виртуальной машины VMware

Если у вас есть [!INCLUDE [Product short](includes/product-short.md)] датчик на виртуальных машинах VMware, вы можете получить оповещение о работоспособности, которое **не анализирует сетевой трафик**. Это может происходить из-за несоответствия конфигураций в VMware.

Чтобы решить эту проблему, выполните указанные ниже действия.

В гостевой ОС в конфигурации сетевого адаптера виртуальной машины **Отключите** следующие параметры: **разгрузка TSO Offload IPv4**.

![Проблема с датчиком VMware](media/vm-sensor-issue.png)

Используйте следующую команду, чтобы проверить, включена или отключена ли Разгрузка большой отправки (LSO).

`Get-NetAdapterAdvancedProperty | Where-Object DisplayName -Match "^Large*"`

![Проверка состояния LSO](media/missing-network-traffic-health-alert.png)

Если параметр LSO включен, отключите его с помощью следующей команды:

`Disable-NetAdapterLso -Name {name of adapter}`

![Состояние отключения LSO](media/disable-lso-vmware.png)

> [!NOTE]
>
> - Чтобы изменения вступили в силу, может потребоваться перезагрузить компьютер.
> - Эти действия могут различаться в зависимости от версии VMWare. Ознакомьтесь с документацией по VMWare, чтобы узнать, как отключить LSO/TSO OFFLOAD для вашей версии VMWare.

## <a name="sensor-failed-to-retrieve-group-managed-service-account-gmsa-credentials"></a>Датчику не удалось получить учетные данные групповой управляемой учетной записи службы (gMSA)

Если вы получаете следующее оповещение о работоспособности: **Неправильные учетные данные пользователя служб каталогов**

**Записи журнала датчика:**

2020-02-17 14:01:36.5315 Info ImpersonationManager CreateImpersonatorAsync started [UserName=account_name Domain=domain1.test.local IsGroupManagedServiceAccount=True] 2020-02-17 14:01:36.5750 Info ImpersonationManager CreateImpersonatorAsync finished [UserName=account_name Domain=domain1.test.local IsSuccess=False]

**Записи журнала обновления датчика:**

2020-02-17 14:02:19.6258 Warn GroupManagedServiceAccountImpersonationHelper GetGroupManagedServiceAccountAccessTokenAsync failed GMSA password could not be retrieved [errorCode=AccessDenied AccountName=account_name DomainDnsName=domain1.test.local]

**Причина**.

Датчику не удалось получить назначенную учетную запись gMSA с [!INCLUDE [Product short](includes/product-short.md)] портала.

**Решение:**

Убедитесь, что учетные данные учетной записи gMSA правильные и что датчик предоставил разрешение на получение учетных данных учетной записи. Хотя не [!INCLUDE [Product short](includes/product-short.md)]  требует разрешения **Вход в качестве службы** для учетных записей gMSA, эта проблема часто устраняется путем добавления разрешения к учетной записи.

## <a name="report-downloads-cannot-contain-more-than-300000-entries"></a>Скачиваемые отчеты не могут содержать больше 300 000 записей

[!INCLUDE [Product short](includes/product-short.md)] не поддерживает загрузку отчетов, содержащих более 300 000 записей по каждому отчету. Отчеты, в которых больше 300 000 записей, будут отображаться неполными.

**Причина**.

Это инженерное ограничение.

**Решение:**

Известного решения не существует.

## <a name="sensor-fails-to-enumerate-event-logs"></a>Датчик не может перечислить журналы событий

Если вы видите ограниченное число или не хватает, оповещений о событиях безопасности или логических действий в [!INCLUDE [Product short](includes/product-short.md)] консоли, но оповещение о работоспособности не запускается. 

**Записи журнала датчика:**

Ошибка Евентложексцептион System. Diagnostics. Eventing. Reader. Евентложексцептион. недопустимый маркер в void System. Diagnostics. Eventing. читатель. Евентложексцептион. Throw (int errorCode) в объекте System. Diagnostics. Eventing. Reader. Нативевраппер. Евтжетевентинфо (EventLogHandle Handle, EvtEventPropertyId enumType) в строке System.Diagnostics.Eventing.Reader.EventLogRecord.get_ContainerLog ()

**Причина**.

Список управления доступом на уровне пользователей ограничивает доступ к необходимым журналам событий учетной записью локальной службы.

**Решение:**

Убедитесь, что список управления доступом на уровне пользователей включает следующую запись:

`(A;;0x1;;;S-1-5-80-818380073-2995186456-1411405591-3990468014-3617507088)`

## <a name="see-also"></a>См. также

- [Предварительные требования для работы с [!INCLUDE [Product short](includes/product-short.md)]](prerequisites.md)
- [Планирование ресурсов [!INCLUDE [Product short](includes/product-short.md)]](capacity-planning.md)
- [Настройка сбора данных о событиях](configure-event-collection.md)
- [Настройка пересылки событий Windows](configure-event-forwarding.md)
- [Посетите форум по [!INCLUDE [Product short](includes/product-short.md)].](https://aka.ms/MDIcommunity)
