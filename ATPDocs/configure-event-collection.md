---
title: Установка Microsoft Defender для удостоверений
description: На этом этапе установки Microsoft Defender для удостоверений настраиваются источники данных.
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
ms.openlocfilehash: 627c30146e2543501da9d5970c9c8a087e3320bf
ms.sourcegitcommit: c5f63d621f4f1e875f8c24adc2bd4770e07e0a62
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/12/2020
ms.locfileid: "94558242"
---
# <a name="configure-event-collection"></a>Настройка сбора данных о событиях

[!INCLUDE [Rebranding notice](includes/rebranding.md)]

Для расширения возможностей обнаружения службе "[!INCLUDE [Product long](includes/product-long.md)]" требуется доступ к событиям Windows, приведенным в статье [Настройка сбора данных о событиях Windows](configure-windows-event-collection.md#configure-event-collection). Эти события может автоматически считывать датчик [!INCLUDE [Product short](includes/product-short.md)]. Если датчик [!INCLUDE [Product short](includes/product-short.md)] не развернут, они передаются в автономный датчик [!INCLUDE [Product short](includes/product-short.md)]. Для этого в автономном датчике [!INCLUDE [Product short](includes/product-short.md)] настраивается ожидание передачи событий SIEM или [пересылка событий Windows](configure-event-forwarding.md).

> [!NOTE]
>
> - Автономные датчики [!INCLUDE [Product short](includes/product-short.md)] не поддерживают сбор записей журнала трассировки событий Windows (ETW), которые предоставляют данные для нескольких обнаружений. Для полного охвата среды рекомендуется развернуть датчик [!INCLUDE [Product short](includes/product-short.md)].
> - Очень важно выполнить скрипт аудита [!INCLUDE [Product short](includes/product-short.md)] перед настройкой сбора данных о событиях, чтобы обеспечить правильность настройки контроллеров домена для записи необходимых событий.

Кроме сбора и анализа входящего и исходящего сетевого трафика контроллеров домена, [!INCLUDE [Product short](includes/product-short.md)] может использовать события Windows для улучшенного обнаружения. Эти события можно получать из системы SIEM или путем настройки пересылки событий Windows с контроллера домена. Собранные события предоставляют [!INCLUDE [Product short](includes/product-short.md)] дополнительные данные, которые невозможно получить через сетевой трафик контроллера домена.

## <a name="ntlm-authentication-using-windows-event-8004"></a>Аутентификация NTLM с использованием события Windows 8004

Чтобы настроить сбор событий Windows 8004, выполните следующие действия:

1. Перейдите к расположению *Конфигурация компьютера\Политики\Параметры Windows\Параметры безопасности\Локальные политики\Security Options*
1. Настройте **групповую политику домена** следующим образом:
    - Сетевая безопасность: Ограничение NTLM: Исходящий трафик NTLM к удаленным серверам = **Аудит всего**
    - Сетевая безопасность: Ограничение NTLM: Аудит аутентификации NTLM в этом домене = **Включить все**
    - Сетевая безопасность: Ограничение NTLM: Аудит входящего трафика NTLM = **Включить аудит для всех учетных записей**

Когда датчик [!INCLUDE [Product short](includes/product-short.md)] анализирует события Windows 8004, действия аутентификации NTLM [!INCLUDE [Product short](includes/product-short.md)] обогащаются данными, к которым получает доступ сервер.

## <a name="siemsyslog"></a>Система SIEM/системный журнал

Автономные датчики [!INCLUDE [Product short](includes/product-short.md)] по умолчанию настроены для получения данных системного журнала. Чтобы использовать эти данные, необходимо перенаправить данные системного журнала на автономный датчик [!INCLUDE [Product short](includes/product-short.md)].

> [!NOTE]
> [!INCLUDE [Product short](includes/product-short.md)] прослушивает только IPv4, но не IPv6.

> [!IMPORTANT]
>
> - Не выполняйте пересылку всех данных системного журнала в датчик [!INCLUDE [Product short](includes/product-short.md)].
> - [!INCLUDE [Product short](includes/product-short.md)] поддерживает трафик UDP с сервера SIEM или системного журнала.

Подробности о настройке пересылки событий на другой сервер см. в документации по серверу SIEM или системному журналу.

> [!NOTE]
> Если сервер SIEM или сервер системного журнала отсутствует, настройку контроллеров домена Windows можно выполнить так, чтобы включить сбор и анализ всех необходимых событий с помощью [!INCLUDE [Product short](includes/product-short.md)].

## <a name="configuring-the-product-short-sensor-to-listen-for-siem-events"></a>Настройка прослушивания событий SIEM в датчике [!INCLUDE [Product short](includes/product-short.md)]

- Выполните настройку сервера SIEM или сервера системного журнала так, чтобы все необходимые события направлялись на IP-адрес одного из автономных датчиков [!INCLUDE [Product short](includes/product-short.md)]. Дополнительные сведения о настройке SIEM см. в справке в Интернете. Сведения об особых требованиях к форматированию каждого сервера SIEM см. в вариантах технической поддержки.

[!INCLUDE [Product short](includes/product-short.md)] поддерживает события SIEM в следующих форматах:

### <a name="rsa-security-analytics"></a>Аналитика безопасности RSA

&lt;Заголовок системного журнала&gt;RsaSA\n2015-May-19 09:07:09\n4776\nMicrosoft-Windows-Security-Auditing\nSecurity\XXXXX.subDomain.domain.org.il\nYYYYY$\nMMMMM \n0x0

- Заголовок системного журнала необязателен.

- Между всеми полями должен стоять символ-разделитель \n.
- Поля в порядке очередности:
    1. Постоянное значение RsaSA (должно появиться).
    2. Метка времени фактического события (убедитесь, что это значение не является меткой времени поступления в SIEM или отправки в [!INCLUDE [Product short](includes/product-short.md)]). Важно! Значение желательно представлять в миллисекундах.
    3. код события Windows.
    4. Имя поставщика событий Windows
    5. Имя журнала событий Windows
    6. Имя компьютера, получающего событие (в данном случае контроллера домена)
    7. Имя пользователя, подлинность которого проверяется
    8. Имя исходного узла
    9. Код результата NTLM
- Поскольку порядок важен, в сообщении не должно быть ничего другого.

### <a name="microfocus-arcsight"></a>MicroFocus ArcSight

CEF:0|Microsoft|Microsoft Windows||Microsoft-Windows-Security-Auditing:4776|Контроллер домена попытался проверить учетные данные для учетной записи.|Low| externalId=4776 cat=Security rt=1426218619000 shost=KKKKKK dhost=YYYYYY.subDomain.domain.com duser=XXXXXX cs2=Security cs3=Microsoft-Windows-Security-Auditing cs4=0x0 cs3Label=EventSource cs4Label=Reason or Error Code

- Должно соответствовать определению протокола.

- Отсутствует заголовок системного журнала.
- Заголовок (часть, разделенная вертикальной линией) должен существовать (как указано в протоколе).
- В _расширении_ должны присутствовать следующие ключи:
  - externalId = код события Windows
  - rt — метка времени фактического события (убедитесь в том, что это значение не является меткой времени поступления на SIEM или отправки в [!INCLUDE [Product short](includes/product-short.md)]). Важно! Значение желательно представлять в миллисекундах.
  - cat = имя журнала событий Windows
  - shost = имя исходного узла
  - dhost = имя компьютера, получающего событие (в данном случае контроллера домена)
  - duser = имя пользователя, подлинность которого проверяется
- Для _расширения_ порядок представления неважен
- Для следующих двух полей следует назначить отдельный ключ и метку ключа:
  - EventSource
  - Reason or Error Code — код результата NTLM

### <a name="splunk"></a>Splunk

&lt;Заголовок системного журнала&gt;\r\nEventCode=4776\r\nLogfile=Security\r\nSourceName=Microsoft-Windows-Security-Auditing\r\nTimeGenerated=20150310132717.784882-000\r\ComputerName=YYYYY\r\nMessage=

Компьютер попытался проверить учетные данные для учетной записи.

Пакет проверки подлинности: MICROSOFT_AUTHENTICATION_PACKAGE_V1_0

Учетная запись входа: Администратор

Исходная рабочая станция: SIEM

Код ошибки: 0x0

- Заголовок системного журнала необязателен.

- Между всеми обязательными полями должен стоять символ-разделитель \r\n. Обратите внимание, что это управляющие символы CRLF (0D0A в шестнадцатеричном формате), а не литеральные символы.
- Поля имеют формат ключ = значение.
- Наличие следующих ключей и их значений обязательно:
  - EventCode = код события Windows
  - Logfile = имя журнала событий Windows
  - SourceName = имя поставщика событий Windows
  - TimeGenerated — метка времени фактического события (убедитесь, что это значение не является меткой времени поступления в SIEM или отправки в [!INCLUDE [Product short](includes/product-short.md)]). Важно! Значение должно быть представлено в формате yyyyMMddHHmmss.FFFFFF, желательно в миллисекундах.
  - ComputerName = имя исходного узла
  - Message = исходный текст события Windows
- Ключ сообщения и его значение должны быть в конце.
- Для пар ключ=значение порядок представления неважен.

### <a name="qradar"></a>QRadar

QRadar активирует сбор данных о событиях через агента. Если сбор данных происходит с помощью агента, то формат времени представляется без указания миллисекунд. Так как [!INCLUDE [Product short](includes/product-short.md)] требуются данные о миллисекундах, необходимо настроить в QRadar сбор данных о событиях Windows без агента. Дополнительные сведения см. в разделе [http://www-01.ibm.com/support/docview.wss?uid=swg21700170](http://www-01.ibm.com/support/docview.wss?uid=swg21700170 "QRadar: безагентный сбор данных о событиях Windows с помощью протокола MSRPC").

```text
<13>Feb 11 00:00:00 %IPADDRESS% AgentDevice=WindowsLog AgentLogFile=Security Source=Microsoft-Windows-Security-Auditing Computer=%FQDN% User= Domain= EventID=4776 EventIDCode=4776 EventType=8 EventCategory=14336 RecordNumber=1961417 TimeGenerated=1456144380009 TimeWritten=1456144380009 Message=The computer attempted to validate the credentials for an account. Authentication Package: MICROSOFT_AUTHENTICATION_PACKAGE_V1_0 Logon Account: Administrator Source Workstation: HOSTNAME Error Code: 0x0
```

Необходимо задать следующие сведения в полях:

- тип агента для сбора данных;

- имя поставщика журнала событий Windows;
- источник журнала событий Windows;
- полное доменное имя контроллера домена;
- код события Windows.

TimeGenerated — метка времени фактического события (убедитесь, что это значение не является меткой времени поступления в SIEM или отправки в [!INCLUDE [Product short](includes/product-short.md)]). Важно! Значение должно быть представлено в формате yyyyMMddHHmmss.FFFFFF, желательно в миллисекундах.

Message — это исходный текст события Windows.

Между парами "ключ-значение" должен быть разделитель \t.

>[!NOTE]
> Использование WinCollect для сбора данных о событиях Windows не поддерживается.

## <a name="see-also"></a>См. также

- [Средство определения размера [!INCLUDE [Product short](includes/product-short.md)]](https://aka.ms/aatpsizingtool)
- [Справочник по журналу SIEM [!INCLUDE [Product short](includes/product-short.md)]](cef-format-sa.md)
- [Предварительные требования для работы с [!INCLUDE [Product short](includes/product-short.md)]](prerequisites.md)
- [Посетите форум по [!INCLUDE [Product short](includes/product-short.md)].](https://aka.ms/MDIcommunity)
