---
title: "Управление базой данных ATA | Microsoft ATA"
description: "Процедуры перемещения, резервного копирования и восстановления базы данных ATA."
keywords: 
author: rkarlin
manager: stevenpo
ms.date: 04/28/2016
ms.topic: article
ms.prod: identity-ata
ms.service: advanced-threat-analytics
ms.technology: security
ms.assetid: 1d27dba8-fb30-4cce-a68a-f0b1df02b977
ms.reviewer: bennyl
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 115ec28877665c79e5cbcd557528da156c8d7149
ms.openlocfilehash: fd00623f9be396b3a2c384cce436996b5093cc3f


---

# Управление базой данных ATA
Из этой статьи вы узнаете, как перемещать и восстанавливать базу данных ATA, а также создавать ее резервные копии на примере MongoDB.

## Резервное копирование базы данных ATA
См. [соответствующую документацию MongoDB](http://docs.mongodb.org/manual/administration/backup/).

## Восстановление базы данных ATA
См. [соответствующую документацию MongoDB](http://docs.mongodb.org/manual/administration/backup/).

## Перемещение базы данных ATA на другой диск

1.  Остановите службу **центра Microsoft Advanced Threat Analytics**.

2.  Остановите службу **MongoDB**.

3.  Откройте файл конфигурации Mongo: C:\Program Files\Microsoft Advanced Threat Analytics\Center\MongoDB\bin\mongod.cfg (расположение по умолчанию).

    Поиск параметра `storage: dbPath`

4.  Переместите папку, указанную в параметре `dbPath`, в новое расположение.

5.  В файле конфигурации Mongo в параметре `dbPath` укажите новый путь к папке, сохраните изменения и закройте файл.

    ![Изменение конфигурации MongoDB (рисунок)](media/ATA-mongoDB-moveDB.png)

6.  Запустите службу **MongoDB**.

7.  Откройте командную строку и с помощью команды `mongo.exe ATA` запустите оболочку Mongo.

    По умолчанию файл mongo.exe хранится в расположении C:\Program Files\Microsoft Advanced Threat Analytics\Center\MongoDB\bin.

8.  Выполните следующую команду. `db.SystemProfiles.update( {_t: "CenterSystemProfile"} , {$set:{"Configuration.CenterDatabaseClientConfiguration.DataPath" : "<New DB Location>"}})`

   Вместо <New DB Location>, где `&lt;New DB Location&gt;` — это новый путь к папке.

9.  Обновите путь к папке HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft Advanced Threat Analytics\Center\DatabaseDataPath.

9. Запустите службу **центра Microsoft Advanced Threat Analytics**.

## См. также
- [Архитектура ATA](/advanced-threat-analytics/plan-design/ata-architecture)
- [Предварительные требования для ATA](/advanced-threat-analytics/plan-design/ata-prerequisites)
- [Обязательно ознакомьтесь с форумом ATA.](https://social.technet.microsoft.com/Forums/security/home?forum=mata)




<!--HONumber=Jul16_HO3-->


