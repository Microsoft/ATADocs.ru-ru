---
title: "Управление базой данных ATA | Microsoft ATA"
description: "Процедуры перемещения, резервного копирования и восстановления базы данных ATA."
keywords: 
author: rkarlin
manager: mbaldwin
ms.date: 10/31/2016
ms.topic: article
ms.prod: 
ms.service: advanced-threat-analytics
ms.technology: 
ms.assetid: 1d27dba8-fb30-4cce-a68a-f0b1df02b977
ms.reviewer: bennyl
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: f334f9c8440e4bb0202579de220f6530d0aabad8
ms.openlocfilehash: e295e0a0a8b5adbd40ddeb7e389ff82c7482c6d9


---

*Область применения: Advanced Threat Analytics версии 1.7*



# <a name="ata-database-management"></a>Управление базой данных ATA
Из этой статьи вы узнаете, как перемещать и восстанавливать базу данных ATA, а также создавать ее резервные копии на примере MongoDB.

## <a name="backing-up-the-ata-database"></a>Резервное копирование базы данных ATA
См. [соответствующую документацию MongoDB](http://docs.mongodb.org/manual/administration/backup/).

## <a name="restoring-the-ata-database"></a>Восстановление базы данных ATA
См. [соответствующую документацию MongoDB](http://docs.mongodb.org/manual/administration/backup/).

## <a name="moving-the-ata-database-to-another-drive"></a>Перемещение базы данных ATA на другой диск

1.  Остановите службу **центра Microsoft Advanced Threat Analytics**.

2.  Остановите службу **MongoDB**.

3.  Откройте файл конфигурации Mongo: C:\Program Files\Microsoft Advanced Threat Analytics\Center\MongoDB\bin\mongod.cfg (расположение по умолчанию).

    Найдите параметр `storage: dbPath`.

4.  Переместите папку, указанную в параметре `dbPath`, в новое расположение.

5.  В файле конфигурации Mongo в параметре `dbPath` укажите новый путь к папке, сохраните изменения и закройте файл.

    ![Изменение конфигурации MongoDB (рисунок)](media/ATA-mongoDB-moveDB.png)

6.  Запустите службу **MongoDB**.

7. Запустите службу **центра Microsoft Advanced Threat Analytics**.

## <a name="see-also"></a>См. также
- [Архитектура ATA](/advanced-threat-analytics/plan-design/ata-architecture)
- [Предварительные требования ATA](/advanced-threat-analytics/plan-design/ata-prerequisites)
- [Ознакомьтесь с форумом ATA.](https://social.technet.microsoft.com/Forums/security/home?forum=mata)




<!--HONumber=Oct16_HO5-->


