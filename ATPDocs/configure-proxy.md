---
title: Настройка прокси-сервера или брандмауэра для взаимодействия Azure ATP с датчиком | Документы Майкрософт
description: Сведения о настройке брандмауэра или прокси-сервера для взаимодействия облачной службы Azure ATP и датчиков Azure ATP
keywords: ''
author: mlottner
ms.author: mlottner
manager: barbkess
ms.date: 03/17/2019
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: azure-advanced-threat-protection
ms.technology: ''
ms.assetid: 9c173d28-a944-491a-92c1-9690eb06b151
ms.reviewer: itargoet
ms.suite: ems
ms.openlocfilehash: 5490688653edddae020a8b63191a1c9a7b6e9f8a
ms.sourcegitcommit: 9252c74620abb99d8fa2b8d2cc2169018078bec9
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/19/2019
ms.locfileid: "58136813"
---
# <a name="configure-endpoint-proxy-and-internet-connectivity-settings-for-your-azure-atp-sensor"></a>Настройка конечной точки прокси-сервера и подключения к Интернету для датчика ATP в Azure

Для успешной работы датчику Advanced Threat Protection (ATP) Azure требуется подключение через Интернет к облачной службе Azure ATP. В некоторых организациях контроллеры домена подключаются к Интернету не напрямую, а через веб-прокси. Для каждого датчика Azure ATP необходимо настроить параметры прокси-сервера Microsoft Windows Internet (WinINET) для передачи данных и взаимодействия со службой Azure ATP. Даже если вы используете для настройки прокси-сервера WinHTTP, необходимо отдельно настроить параметры прокси-сервера в браузере Windows Internet (WinINet) для взаимодействия между датчиком и облачной службой Azure ATP.


При настройке прокси-сервера следует помнить, что внедренная служба датчика Azure ATP выполняется в системном контексте от имени учетной записи **LocalService**, а служба обновления датчика Azure ATP выполняется в системном контексте от имени учетной записи **LocalSystem**. 

> [!NOTE]
> Если в топологии сети используется прозрачный прокси или WPAD, настраивать WinINET для прокси-сервера не нужно.

## <a name="configure-the-proxy"></a>Настройка прокси-сервера 

Если компьютер не имеет подключения к Интернету, настройте статическое подключение к прокси-серверу вручную через системный реестр, чтобы датчик Azure ATP мог передавать диагностические данные и взаимодействовать с облачной службой Azure ATP.

> [!NOTE]
> Изменения в реестре следует вносить только в ветви LocalService и LocalSystem.

Статическое подключение к прокси-серверу настраивается через реестр. Скопируйте настройки прокси-сервера, используемые в контексте пользователя, в ветви LocalService и LocalSystem. Чтобы скопировать параметры прокси-сервера из контекста пользователя, выполните следующее:

1.   Обязательно создайте резервные копии разделов реестра перед внесением в их изменений.

2. Выполните в разделе реестра `HKCU\Software\Microsoft\Windows\CurrentVersion\Internet Settings\Connections\DefaultConnectionSettings` поиск по значению `DefaultConnectionSettings` (REG_BINARY) и скопируйте результат.
 
2.  Если в LocalSystem отсутствуют допустимые параметры прокси-сервера (прокси не настроен или отличается от настроек в Current_User), скопируйте параметры прокси-сервера из Current_User в LocalSystem. Перейдите к разделу реестра `HKU\S-1-5-18\Software\Microsoft\Windows\CurrentVersion\Internet Settings\Connections\DefaultConnectionSettings`.

3.  Вставьте значение из Current_User `DefaultConnectionSettings` в формате REG_BINARY.

4.  Если в LocalService отсутствуют допустимые параметры прокси-сервера, скопируйте эти параметры из Current_User в LocalService. Перейдите к разделу реестра `HKU\S-1-5-19\Software\Microsoft\Windows\CurrentVersion\Internet Settings\Connections\DefaultConnectionSettings`.

5.  Вставьте значение из Current_User `DefaultConnectionSettings` в формате REG_BINARY.

> [!NOTE]
> Это повлияет на все приложения, включая службы Windows, которые используют WinINET в контексте LocalService или LocalSytem.


## <a name="enable-access-to-azure-atp-service-urls-in-the-proxy-server"></a>Разрешение доступа прокси-сервера к URL-адресам служб Azure ATP

Чтобы разрешить доступ к Azure ATP, разрешите трафик для следующих URL-адресов:

- \<имя_экземпляра>.atp.azure.com — для подключения консоли. Например, "Contoso-corp.atp.azure.com"

- \<иvя_экземпляра>sensorapi.atp.azure.com — для подключения датчиков. Например, "contoso-corpsensorapi.atp.azure.com"

Предыдущие URL-адреса автоматически сопоставляются с корректным расположением служб для вашего экземпляра Azure ATP. Если требуется более детальный контроль, попробуйте разрешить трафик к нужным конечным точкам из следующей таблицы:

|Обнаружение службы|DNS-запись *.atp.azure.com|
|----|----|
|США |triprd1wcusw1sensorapi.atp.azure.com<br>triprd1wcuswb1sensorapi.atp.azure.com<br>triprd1wcuse1sensorapi.atp.azure.com|
|Европа|triprd1wceun1sensorapi.atp.azure.com<br>triprd1wceuw1sensorapi.atp.azure.com|
|Азия|triprd1wcasse1sensorapi.atp.azure.com|

 
> [!NOTE]
> Для выполнения проверки SSL сетевого трафика Azure ATP (между датчиком и службой Azure ATP) необходимо, чтобы проверка SSL поддерживала взаимную проверку.


## <a name="see-also"></a>См. также
- [Настройка пересылки событий](configure-event-forwarding.md)
- [Загляните на форум Azure ATP!](https://aka.ms/azureatpcommunity)
