---
title: "Управление базой данных ATA | Документация Майкрософт"
description: "Процедуры перемещения, резервного копирования и восстановления базы данных ATA."
keywords: 
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 11/29/2016
ms.topic: article
ms.prod: 
ms.service: advanced-threat-analytics
ms.technology: 
ms.assetid: 05e49e23-6e0a-4ec0-9a63-a2093173c8a1
ms.reviewer: bennyl
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: fca7f1b2b8260cad6e0ce32aad1c9e1b53fc0ad5
ms.openlocfilehash: 9d7e2a03633acc97d6f918c97f9b67b553d5202e


---

*Область применения: Advanced Threat Analytics версии 1.7*



# <a name="ata-database-management"></a>Управление базой данных ATA
Из этой статьи вы узнаете, как перемещать и восстанавливать базу данных ATA, а также создавать ее резервные копии на примере MongoDB.

## <a name="backing-up-the-ata-database"></a>Резервное копирование базы данных ATA
См. [соответствующую документацию MongoDB](http://docs.mongodb.org/manual/administration/backup/).

## <a name="restoring-the-ata-database"></a>Восстановление базы данных ATA
См. [соответствующую документацию MongoDB](http://docs.mongodb.org/manual/administration/backup/).

## <a name="moving-the-ata-database-to-another-drive"></a>Перемещение базы данных ATA на другой диск

1.  Остановите службу **центра Microsoft Advanced Threat Analytics**.
> [!Important] 
> Прежде чем продолжать, убедитесь, что служба центра ATA остановлена.

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




<!--HONumber=Nov16_HO3-->


