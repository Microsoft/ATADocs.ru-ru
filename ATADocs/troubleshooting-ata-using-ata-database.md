---
title: Устранение неполадок в Advanced Threat Analytics с использованием базы данных
description: В данной статье рассказывается о том, как устранять неполадки с помощью базы данных ATA.
keywords: ''
author: rkarlin
ms.author: rkarlin
manager: rkarlin
ms.date: 3/21/2018
ms.topic: conceptual
ms.prod: advanced-threat-analytics
ms.technology: ''
ms.assetid: 377a3c81-5c1d-486f-8942-85249aacf560
ms.reviewer: bennyl
ms.suite: ems
ms.openlocfilehash: 1efc5aee15527212a6f2eb53c147fe8fa1d62ea3
ms.sourcegitcommit: 11fff9d4ebf1c50b04f7789a22c80cdbc3e4416a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/15/2020
ms.locfileid: "79414222"
---
# <a name="troubleshooting-ata-using-the-ata-database"></a>Устранение неполадок в ATA с помощью базы данных ATA

*Применяется к: Advanced Threat Analytics версии 1.9*

В качестве своей базы данных ATA использует MongoDB.
Для взаимодействия с базой данных можно использовать заданную по умолчанию командную строку или инструмент пользовательского интерфейса для выполнения дополнительных задач и устранения неполадок.

## <a name="interacting-with-the-database"></a>Взаимодействие с базой данных
Чтобы отправить запрос в базу данных, проще всего (и это стандартный способ) использовать оболочку Mongo. Сделать это можно так:

1.  Откройте окно командной строки и измените путь к папке Bin службы MongoDB. По умолчанию задан путь **C:\Program Files\Microsoft Advanced Threat Analytics\Center\MongoDB\bin**.

2.  Запустите `mongo.exe ATA`. Убедитесь, что значение ATA указано прописными буквами.

> [!div class="mx-tableFixed"]
> 
> |Инструкции...|Синтаксис|Примечания|
> |-------------|----------|---------|
> |проверить наличие коллекций в базе данных.|`show collections`|Полезно использовать в качестве полной проверки, чтобы убедиться, что трафик записывается в базу данных и что АТА получает сведения о событии 4776.|
> |получить сведения о пользователе, компьютере или группе (UniqueEntity). Это, например, могут быть сведения об идентификаторе пользователя.|`db.UniqueEntity.find({CompleteSearchNames: "<name of entity in lower case>"})`||
> |найти исходящий трафик проверки подлинности Kerberos с конкретного компьютера в определенный день.|`db.KerberosAs_<datetime>.find({SourceComputerId: "<Id of the source computer>"})`|Чтобы получить &lt;идентификатор исходного компьютера&gt;, выполните запрос к коллекциям UniqueEntity, как показано в примере.<br /><br />Каждый тип сетевой активности, например проверка подлинности Kerberos, имеет собственную коллекцию для каждой даты в формате UTC.|
> |выполнять расширенные изменения конфигурации. В этом примере измените размер очереди отправки для всех шлюзов ATA до 10 000.|`db.SystemProfile.update( {_t: "GatewaySystemProfile"} ,`<br>`{$set:{"Configuration.EntitySenderConfiguration.EntityBatchBlockMaxSize" : "10000"}})`|`|

Ниже приведен пример кода, в котором используется синтаксис, приведенный ранее. Он предусмотрен для такого сценария — вы анализируете подозрительную активность, зафиксированную 20 октября 2015 года, и хотите узнать больше о действиях NTLM, совершенных в этот день пользователем John Doe:<br /><br />Сначала найдите идентификатор пользователя John Doe.

`db.UniqueEntity.find({Name: "John Doe"})`<br>Запишите идентификатор, обозначенный значением `_id`. Предположим, что в примере используется идентификатор `123bdd24-b269-h6e1-9c72-7737as875351`.<br>Затем выполните поиск коллекции, в которой ближайшая дата предшествует искомой дате. В примере это 20 октября 2015 г.<br>После этого выполните поиск действий NTLM для учетной записи John Doe: 

`db.Ntlms_<closest date>.find({SourceAccountId: "123bdd24-b269-h6e1-9c72-7737as875351"})`

## <a name="see-also"></a>См. также
- [Предварительные требования ATA](ata-prerequisites.md)
- [Планирование производительности ATA](ata-capacity-planning.md)
- [Настройка сбора данных о событиях](configure-event-collection.md)
- [Настройка пересылки событий Windows](configure-event-collection.md)
- [Ознакомьтесь с форумом ATA.](https://social.technet.microsoft.com/Forums/security/home?forum=mata)
