---
title: Управление базой данных Advanced Threat Analytics | Документация Майкрософт
description: Процедуры перемещения, резервного копирования и восстановления базы данных ATA.
keywords: ''
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 3/21/2018
ms.topic: article
ms.prod: ''
ms.service: advanced-threat-analytics
ms.technology: ''
ms.assetid: 05e49e23-6e0a-4ec0-9a63-a2093173c8a1
ms.reviewer: bennyl
ms.suite: ems
ms.openlocfilehash: 20762e0d944adaa0c81de9f3ad1c32de445157fe
ms.sourcegitcommit: 49c3e41714a5a46ff2607cbced50a31ec90fc90c
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/22/2018
ms.locfileid: "30009376"
---
*Применяется к: Advanced Threat Analytics версии 1.9*



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
- [Архитектура ATA](ata-architecture.md)
- [Предварительные требования ATA](ata-prerequisites.md)
- [Ознакомьтесь с форумом ATA.](https://social.technet.microsoft.com/Forums/security/home?forum=mata)

