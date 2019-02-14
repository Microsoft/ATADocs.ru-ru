---
title: Настройка прокси-сервера или брандмауэра для взаимодействия Azure ATP с датчиком | Документы Майкрософт
description: Сведения о настройке брандмауэра или прокси-сервера для взаимодействия облачной службы Azure ATP и датчиков Azure ATP
keywords: ''
author: mlottner
ms.author: mlottner
manager: barbkess
ms.date: 12/02/2018
ms.topic: conceptual
ms.prod: ''
ms.service: azure-advanced-threat-protection
ms.technology: ''
ms.assetid: 9c173d28-a944-491a-92c1-9690eb06b151
ms.reviewer: itargoet
ms.suite: ems
ms.openlocfilehash: 702da9fdcf7c16b3c53d59f91f7a41899c8e42a2
ms.sourcegitcommit: 78748bfd75ae68230d72ad11010ead37d96b0c58
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/12/2019
ms.locfileid: "56076595"
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

Если прокси-сервер или брандмауэр по умолчанию блокирует весь трафик, разрешая только доступ к определенным доменам, или разрешено HTTPS-сканирование (проверка SSL), обязательно включите в список разрешений следующие URL-адреса, чтобы разрешить обмен данными со службой Azure ATP по порту 443.

|Обнаружение службы|DNS-запись .Atp.Azure.com|
|----|----|
|США |triprd1wcusw1sensorapi.atp.azure.com<br>triprd1wcuswb1sensorapi.atp.azure.com<br>triprd1wcuse1sensorapi.atp.azure.com|
|Европа|triprd1wceun1sensorapi.atp.azure.com<br>triprd1wceuw1sensorapi.atp.azure.com|
|Азия|triprd1wcasse1sensorapi.atp.azure.com|


Вы можете также усилить защиту брандмауэра или правил прокси-сервера для конкретного экземпляра, создав правило для следующих записей DNS:
- \<имя_экземпляра>.atp.azure.com — для подключения консоли. Например, "Contoso-corp.atp.azure.com"
- \<иvя_экземпляра>sensorapi.atp.azure.com — для подключения датчиков. Например, "contoso-corpsensorapi.atp.azure.com"

 
> [!NOTE]
> Для выполнения проверки SSL сетевого трафика Azure ATP (между датчиком и службой Azure ATP) необходимо, чтобы проверка SSL поддерживала взаимную проверку.


## <a name="see-also"></a>См. также
- [Настройка пересылки событий](configure-event-forwarding.md)
- [Загляните на форум Azure ATP!](https://aka.ms/azureatpcommunity)