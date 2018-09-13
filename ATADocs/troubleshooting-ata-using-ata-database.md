---
title: Устранение неполадок в Advanced Threat Analytics с использованием базы данных | Документация Майкрософт
description: В данной статье рассказывается о том, как устранять неполадки с помощью базы данных ATA.
keywords: ''
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 3/21/2018
ms.topic: conceptual
ms.prod: ''
ms.service: advanced-threat-analytics
ms.technology: ''
ms.assetid: 377a3c81-5c1d-486f-8942-85249aacf560
ms.reviewer: bennyl
ms.suite: ems
ms.openlocfilehash: 7b6073de5b6a7ae5e53f0070dab7b9d62cd5d988
ms.sourcegitcommit: 5ad28d7b0607c7ea36d795b72928769c629fb80a
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/07/2018
ms.locfileid: "44166637"
---
*Применяется к: Advanced Threat Analytics версии 1.9*



# <a name="troubleshooting-ata-using-the-ata-database"></a>Устранение неполадок в ATA с помощью базы данных ATA
В качестве своей базы данных ATA использует MongoDB.
Для взаимодействия с базой данных можно использовать заданную по умолчанию командную строку или инструмент пользовательского интерфейса для выполнения дополнительных задач и устранения неполадок.

## <a name="interacting-with-the-database"></a>Взаимодействие с базой данных
Чтобы отправить запрос в базу данных, проще всего (и это стандартный способ) использовать оболочку Mongo. Сделать это можно так:

1.  Откройте окно командной строки и измените путь к папке Bin службы MongoDB. По умолчанию задан путь **C:\Program Files\Microsoft Advanced Threat Analytics\Center\MongoDB\bin**.

2.  Запустите `mongo.exe ATA`. Убедитесь, что значение ATA указано прописными буквами.

> [!div class="mx-tableFixed"]
|Как...|Синтаксис|"Заметки"|
|-------------|----------|---------|
|проверить наличие коллекций в базе данных.|`show collections`|Полезно использовать в качестве полной проверки, чтобы убедиться, что трафик записывается в базу данных и что АТА получает сведения о событии 4776.|
|получить сведения о пользователе, компьютере или группе (UniqueEntity). Это, например, могут быть сведения об идентификаторе пользователя.|`db.UniqueEntity.find({CompleteSearchNames: "<name of entity in lower case>"})`||
|найти исходящий трафик проверки подлинности Kerberos с конкретного компьютера в определенный день.|`db.KerberosAs_<datetime>.find({SourceComputerId: "<Id of the source computer>"})`|Чтобы получить &lt;идентификатор исходного компьютера&gt;, выполните запрос к коллекциям UniqueEntity, как показано в примере.<br /><br />Каждый тип сетевой активности, например проверка подлинности Kerberos, имеет собственную коллекцию для каждой даты в формате UTC.|
|найти исходящий трафик NTLM с конкретного компьютера, имеющего отношение к конкретной учетной записи, в определенный день.|`db.Ntlm_<datetime>.find({SourceComputerId: "<Id of the source computer>", SourceAccountId: "<Id of the account>"})`|Чтобы получить &lt;идентификатор исходного компьютера&gt; и &lt;идентификатор учетной записи&gt;, выполните запрос к коллекциям UniqueEntity, как показано в примере.<br /><br />Каждый тип сетевых операций, например проверка подлинности NTLM, имеет собственную коллекцию для каждой даты в формате UTC.|
|выполнять расширенные изменения конфигурации. В этом примере измените размер очереди отправки для всех шлюзов ATA до 10 000.|`db.SystemProfile.update( {_t: "GatewaySystemProfile"} ,`<br>`{$set:{"Configuration.EntitySenderConfiguration.EntityBatchBlockMaxSize" : "10000"}})`|`|

Ниже приведен пример кода, в котором используется синтаксис, приведенный ранее. Он предусмотрен для такого сценария — вы анализируете подозрительную активность, зафиксированную 20 октября 2015 года, и хотите узнать больше о действиях NTLM, совершенных в этот день пользователем John Doe:<br /><br />Сначала найдите идентификатор пользователя John Doe.

`db.UniqueEntity.find({Name: "John Doe"})`<br>Запишите идентификатор, обозначенный значением `_id`. Предположим, что в примере используется идентификатор `123bdd24-b269-h6e1-9c72-7737as875351`.<br>Затем выполните поиск коллекции, в которой ближайшая дата предшествует искомой дате. В примере это 20 октября 2015 г.<br>После этого выполните поиск действий NTLM для учетной записи John Doe: 

`db.Ntlms_<closest date>.find({SourceAccountId: "123bdd24-b269-h6e1-9c72-7737as875351"})`

## <a name="see-also"></a>См. также
- [Предварительные требования ATA](ata-prerequisites.md)
- [Планирование производительности ATA](ata-capacity-planning.md)
- [Настройка сбора данных о событиях](configure-event-collection.md)
- [Настройка пересылки событий Windows](configure-event-collection.md#configuring-windows-event-forwarding)
- [Ознакомьтесь с форумом ATA.](https://social.technet.microsoft.com/Forums/security/home?forum=mata)
