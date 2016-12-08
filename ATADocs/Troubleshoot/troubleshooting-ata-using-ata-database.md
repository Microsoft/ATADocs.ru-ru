---
title: "Устранение неполадок в ATA с помощью базы данных ATA | Документация Майкрософт"
description: "В данной статье рассказывается о том, как устранять неполадки с помощью базы данных ATA."
keywords: 
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 11/29/2016
ms.topic: article
ms.prod: 
ms.service: advanced-threat-analytics
ms.technology: 
ms.assetid: 377a3c81-5c1d-486f-8942-85249aacf560
ms.reviewer: bennyl
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 7dc860fe31da1374a4466f8e56e55e6520bc10dc
ms.openlocfilehash: fd2cc788ec3fb2c64d47694997762f740f5af503


---

*Область применения: Advanced Threat Analytics версии 1.7*



# <a name="troubleshooting-ata-using-the-ata-database"></a>Устранение неполадок в ATA с помощью базы данных ATA
В качестве своей базы данных ATA использует MongoDB.
Для взаимодействия с базой данных можно использовать заданную по умолчанию командную строку или инструмент пользовательского интерфейса для выполнения дополнительных задач и устранения неполадок.

## <a name="interacting-with-the-database"></a>Взаимодействие с базой данных
Чтобы отправить запрос в базу данных, проще всего (и это стандартный способ) использовать оболочку Mongo. Сделать это можно так:

1.  Откройте окно командной строки и измените путь к папке Bin службы MongoDB. По умолчанию задан путь **C:\Program Files\Microsoft Advanced Threat Analytics\Center\MongoDB\bin**.

2.  Запустите `mongo.exe ATA`. Убедитесь, что значение ATA указано прописными буквами.

|Как...|Синтаксис|Примечания|
|-------------|----------|---------|
|проверить наличие коллекций в базе данных.|`show collections`|Полезно использовать в качестве полной проверки, чтобы убедиться, что трафик записывается в базу данных и что АТА получает сведения о событии 4776.|
|получить сведения о пользователе, компьютере или группе (UniqueEntity). Это, например, могут быть сведения об идентификаторе пользователя.|`db.UniqueEntity.find({SearchNames: "<name of entity in lower case>"})`||
|найти исходящий трафик проверки подлинности Kerberos с конкретного компьютера в определенный день.|`db.KerberosAs_<datetime>.find({SourceComputerId: "<Id of the source computer>"})`|Чтобы получить &lt;идентификатор исходного компьютера&gt;, выполните запрос к коллекциям UniqueEntity, как показано в примере.<br /><br />Каждый тип сетевой активности, например проверка подлинности Kerberos, имеет собственную коллекцию для каждой даты в формате UTC.|
|найти исходящий трафик NTLM с конкретного компьютера, имеющего отношение к конкретной учетной записи, в определенный день.|`db.Ntlm_<datetime>.find({SourceComputerId: "<Id of the source computer>", SourceAccountId: "<Id of the account>"})`|Чтобы получить &lt;идентификатор исходного компьютера&gt; и &lt;идентификатор учетной записи&gt;, выполните запрос к коллекциям UniqueEntity, как показано в примере.<br /><br />Каждый тип сетевых операций, например проверка подлинности NTLM, имеет собственную коллекцию для каждой даты в формате UTC.|
|искать дополнительные свойства, например даты активности учетной записи. |`db.UniqueEntityProfile.find({UniqueEntityId: "<Id of the account>")`|Чтобы получить &lt;идентификатор учетной записи&gt;, выполните запрос к коллекциям UniqueEntity, как показано в примере.<br>Свойство, отображающее даты активности учетной записи, называется ActiveDates. Например, вам нужно узнать, была ли учетная запись активна как минимум 21 день, так как в этом случае алгоритм машинного обучения для аномального поведения сможет обрабатывать данные из этой учетной записи.|
|выполнять расширенные изменения конфигурации. В этом примере мы изменим размер очереди отправки для всех шлюзов ATA до 10 000.|`db.SystemProfile.update( {_t: "GatewaySystemProfile"} ,`<br>`{$set:{"Configuration.EntitySenderConfiguration.EntityBatchBlockMaxSize" : "10000"}})`|`|

Ниже приведен пример кода, в котором используется синтаксис. Он предусмотрен для такого сценария — вы анализируете подозрительную активность, зафиксированную 20 октября 2015 года, и хотите узнать больше о действиях NTLM, совершенных в этот день пользователем John Doe:<br /><br />Сначала найдите идентификатор пользователя John Doe.

`db.UniqueEntity.find({Name: "John Doe"})`<br>Запишите его идентификатор, обозначенный значением `_id`. В нашем примере предположим, что используется идентификатор `123bdd24-b269-h6e1-9c72-7737as875351`.<br>Затем выполните поиск коллекции, в которой ближайшая дата предшествует искомой дате. В нашем примере это 20 октября 2015 г.<br>После этого выполните поиск действий NTLM для учетной записи John Doe: 

`db.Ntlms_<closest date>.find({SourceAccountId: "123bdd24-b269-h6e1-9c72-7737as875351"})`

## <a name="see-also"></a>См. также
- [Предварительные требования ATA](/advanced-threat-analytics/plan-design/ata-prerequisites)
- [Планирование производительности ATA](/advanced-threat-analytics/plan-design/ata-capacity-planning)
- [Настройка сбора данных о событиях](/advanced-threat-analytics/deploy-use/configure-event-collection)
- [Настройка пересылки событий Windows](/advanced-threat-analytics/deploy-use/configure-event-collection#configuring-windows-event-forwarding)
- [Ознакомьтесь с форумом ATA.](https://social.technet.microsoft.com/Forums/security/home?forum=mata)



<!--HONumber=Nov16_HO5-->


