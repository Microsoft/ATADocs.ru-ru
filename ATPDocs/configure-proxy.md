---
title: Настройка прокси-сервера или брандмауэра для обмена данными между Microsoft Defender для удостоверений и датчиком
description: Узнайте, как настроить брандмауэр или прокси-сервер для обмена данными между облачным экземпляром Microsoft Defender для удостоверений и датчиками Microsoft Defender для удостоверений
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 10/26/2020
ms.topic: how-to
ms.collection: M365-security-compliance
ms.service: azure-advanced-threat-protection
ms.reviewer: itargoet
ms.suite: ems
ms.openlocfilehash: 9b3aa953324e855cfe4aafb77ea6b1b1959b7f8c
ms.sourcegitcommit: 90a332d67f62636b2d3a935f6bbdcbf24d74e6f0
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/12/2020
ms.locfileid: "94551669"
---
# <a name="configure-endpoint-proxy-and-internet-connectivity-settings-for-your-product-long-sensor"></a>Настройка прокси-сервера конечной точки и подключения к Интернету для датчика [!INCLUDE [Product long](includes/product-long.md)]

[!INCLUDE [Rebranding notice](includes/rebranding.md)]

Для успешной работы и передачи данных датчика [!INCLUDE [Product long](includes/product-long.md)] каждый датчик должен быть подключен к облачному экземпляру [!INCLUDE [Product short](includes/product-short.md)] через Интернет. В некоторых организациях контроллеры домена подключаются к Интернету не напрямую, а через веб-прокси.

Для настройки прокси-сервера мы рекомендуем использовать командную строку. Таким образом, через этот прокси-сервер будут проходить данные только служб датчиков [!INCLUDE [Product short](includes/product-short.md)].

## <a name="configure-proxy-server-using-the-command-line"></a>Настройка прокси-сервера с помощью командной строки

Вы можете настроить прокси-сервер во время установки датчика, используя следующие параметры командной строки.

### <a name="syntax"></a>Синтаксис

"Azure ATP sensor Setup.exe" [/quiet] [/Help] [ProxyUrl="http://proxy.internal.com"] [ProxyUserName="domain\proxyuser"] [ProxyUserPassword="ProxyPassword"]

### <a name="switch-descriptions"></a>Описание параметров

> [!div class="mx-tableFixed"]
>
> |Имя|Синтаксис|Обязательно для автоматической установки?|Описание:|
> |-------------|----------|---------|---------|
> |ProxyUrl|ProxyUrl="http\://proxy.contoso.com:8080"|Нет|Определяет URL-адрес и номер порта прокси-сервера для датчика [!INCLUDE [Product short](includes/product-short.md)].|
> |ProxyUserName|ProxyUserName="Contoso\ProxyUser"|Нет|Если служба прокси-сервера требует проверки подлинности, укажите имя пользователя в формате "ДОМЕН\пользователь".|
> |ProxyUserPassword|ProxyUserPassword="P@ssw0rd"|Нет|Указывает пароль для имени пользователя прокси-сервера. * Датчик [!INCLUDE [Product short](includes/product-short.md)] шифрует учетные данные и сохраняет их локально.|

## <a name="alternative-methods-to-configure-your-proxy-server"></a>Альтернативные способы настройки прокси-сервера

Для настройки прокси-сервера можно использовать один из следующих альтернативных методов. При настройке параметров прокси-сервера с помощью этих методов другие службы, работающие в контексте локальной системы или локальной службы, также будут направлять трафик через прокси-сервер.

- [Настройка прокси-сервера с помощью WinINet](#configure-proxy-server-using-wininet)
- [Настройка прокси-сервера с помощью реестра](#configure-proxy-server-using-the-registry)

### <a name="configure-proxy-server-using-wininet"></a>Настройка прокси-сервера с помощью WinINet

Если компьютер не подключен к Интернету, вы можете настроить прокси-сервер с использованием конфигурации прокси-сервера Microsoft Windows Internet (WinINet), чтобы датчик [!INCLUDE [Product short](includes/product-short.md)] мог передавать диагностические данные и взаимодействовать с облачным экземпляром [!INCLUDE [Product short](includes/product-short.md)]. Даже если вы используете для настройки прокси-сервера WinHTTP, необходимо отдельно настроить параметры прокси-сервера в браузере Windows Internet (WinINet) для передачи данных между датчиком и облачным экземпляром [!INCLUDE [Product short](includes/product-short.md)].

При настройке прокси-сервера следует помнить, что встроенная служба датчика [!INCLUDE [Product short](includes/product-short.md)] выполняется в системном контексте от имени учетной записи **LocalService** , а служба обновления датчика [!INCLUDE [Product short](includes/product-short.md)] выполняется в системном контексте от имени учетной записи **LocalSystem**.

> [!NOTE]
> Если в топологии сети используется прозрачный прокси или WPAD, настраивать WinINET для прокси-сервера не нужно.

### <a name="configure-proxy-server-using-the-registry"></a>Настройка прокси-сервера с помощью реестра

Кроме того, если компьютер не подключен к Интернету, вы можете настроить статическое подключение к прокси-серверу вручную через системный реестр, чтобы датчик [!INCLUDE [Product short](includes/product-short.md)] мог передавать диагностические данные и взаимодействовать с облачным экземпляром [!INCLUDE [Product short](includes/product-short.md)].

> [!NOTE]
> Изменения в реестре следует вносить только в ветви LocalService и LocalSystem.

Статическое подключение к прокси-серверу настраивается через реестр. Скопируйте настройки прокси-сервера, используемые в контексте пользователя, в ветви LocalService и LocalSystem. Чтобы скопировать параметры прокси-сервера из контекста пользователя, выполните следующее:

1. Обязательно создайте резервные копии разделов реестра перед внесением в их изменений.

1. Выполните в разделе реестра `HKCU\Software\Microsoft\Windows\CurrentVersion\Internet Settings\Connections\DefaultConnectionSettings` поиск по значению `DefaultConnectionSettings` (REG_BINARY) и скопируйте результат.

1. Если в LocalSystem отсутствуют допустимые параметры прокси-сервера (прокси не настроен или отличается от настроек в Current_User), скопируйте параметры прокси-сервера из Current_User в LocalSystem. Перейдите к разделу реестра `HKU\S-1-5-18\Software\Microsoft\Windows\CurrentVersion\Internet Settings\Connections\DefaultConnectionSettings`.

1. Вставьте значение из Current_User `DefaultConnectionSettings` в формате REG_BINARY.

1. Если в LocalService отсутствуют допустимые параметры прокси-сервера, скопируйте эти параметры из Current_User в LocalService. Перейдите к разделу реестра `HKU\S-1-5-19\Software\Microsoft\Windows\CurrentVersion\Internet Settings\Connections\DefaultConnectionSettings`.

1. Вставьте значение из Current_User `DefaultConnectionSettings` в формате REG_BINARY.

> [!NOTE]
> Это повлияет на все приложения, включая службы Windows, которые используют WinINET в контексте LocalService или LocalSytem.

<a name="enable-access-to-azure-atp-service-urls-in-the-proxy-server"></a>

## <a name="enable-access-to-product-short-service-urls-in-the-proxy-server"></a>Разрешение доступа прокси-сервера к URL-адресам служб [!INCLUDE [Product short](includes/product-short.md)]

Чтобы разрешить доступ к [!INCLUDE [Product short](includes/product-short.md)], рекомендуется разрешить трафик для приведенных ниже URL-адресов. URL-адреса автоматически сопоставляются с корректным расположением служб для вашего экземпляра [!INCLUDE [Product short](includes/product-short.md)].

- `<your-instance-name>.atp.azure.com` — для подключения консоли. Например, `contoso-corp.atp.azure.com`

- `<your-instance-name>sensorapi.atp.azure.com` — для подключения датчиков. Например, `contoso-corpsensorapi.atp.azure.com`

Также можно использовать диапазоны IP-адресов в нашем теге службы Azure ( **AzureAdvancedThreatProtection** ) для предоставления доступа к [!INCLUDE [Product short](includes/product-short.md)]. Дополнительные сведения о тегах службы: статья [Теги службы виртуальной сети](/azure/virtual-network/service-tags-overview) или [загружаемый файл тегов службы](https://www.microsoft.com/download/details.aspx?id=56519).

Если же требуется более детальный контроль, попробуйте разрешить трафик к нужным конечным точкам из следующей таблицы:

|Обнаружение службы|DNS-запись *.atp.azure.com|
|----|----|
|США |`triprd1wcusw2sensorapi.atp.azure.com`<br>`triprd1wcuswb3sensorapi.atp.azure.com`<br>`triprd1wcuse3sensorapi.atp.azure.com`|
|GCC High в США|`https://triff1wcva2sensorapi.atp.azure.us`|
|Европа|`triprd1wceun2sensorapi.atp.azure.com`<br>`triprd1wceuw3sensorapi.atp.azure.com`|
|Азия|`triprd1wcasse2sensorapi.atp.azure.com`|
|Великобритания|`triprd1wcuks2sensorapi.atp.azure.com`|

> [!NOTE]
>
> - Чтобы обеспечить максимальную безопасность и конфиденциальность данных, [!INCLUDE [Product short](includes/product-short.md)] использует взаимную проверку подлинности на основе сертификатов между каждым датчиком [!INCLUDE [Product short](includes/product-short.md)] и облачной серверной частью [!INCLUDE [Product short](includes/product-short.md)]. Если в вашей среде используется проверка SSL, убедитесь, что она настроена для взаимной проверки подлинности и не препятствует процессу проверки подлинности.
> - IP-адреса службы [!INCLUDE [Product short](includes/product-short.md)] могут изменяться с течением времени. Таким образом, если вы настраиваете IP-адреса вручную или если прокси-сервер автоматически разрешает DNS-имена в IP-адреса и использует эти IP-адреса, следует периодически проверять, что настроенные IP-адреса все еще актуальны.

## <a name="see-also"></a>См. также

- [Настройка пересылки событий](configure-event-forwarding.md)
- [Посетите форум по [!INCLUDE [Product short](includes/product-short.md)].](https://aka.ms/MDIcommunity)
