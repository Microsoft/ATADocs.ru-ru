---
title: Управление базой данных Advanced Threat Analytics
description: Процедуры перемещения, резервного копирования и восстановления базы данных ATA.
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 3/21/2018
ms.topic: conceptual
ms.prod: advanced-threat-analytics
ms.technology: ''
ms.assetid: 05e49e23-6e0a-4ec0-9a63-a2093173c8a1
ms.reviewer: bennyl
ms.suite: ems
ms.openlocfilehash: f6f39619aa3ba960384b646f2b4237118cabf725
ms.sourcegitcommit: e844155ea57f73dfe2b47f4c5c1c7f5292ccbf1e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2020
ms.locfileid: "94691083"
---
# <a name="ata-database-management"></a>Управление базой данных ATA

[!INCLUDE [Banner for top of topics](includes/banner.md)]

Из этой статьи вы узнаете, как перемещать и восстанавливать базу данных ATA, а также создавать ее резервные копии на примере MongoDB.

## <a name="backing-up-the-ata-database"></a>Резервное копирование базы данных ATA
См. [соответствующую документацию по MongoDB](http://docs.mongodb.org/manual/administration/backup/).

## <a name="restoring-the-ata-database"></a>Восстановление базы данных ATA
См. [соответствующую документацию по MongoDB](http://docs.mongodb.org/manual/administration/backup/).

## <a name="moving-the-ata-database-to-another-drive"></a>Перемещение базы данных ATA на другой диск

1. Остановите службу **центра Microsoft Advanced Threat Analytics**.
   > [!Important] 
   > Прежде чем продолжать, убедитесь, что служба центра ATA остановлена.

1. Остановите службу **MongoDB**.

1. Откройте файл конфигурации Mongo: C:\Program Files\Microsoft Advanced Threat Analytics\Center\MongoDB\bin\mongod.cfg (расположение по умолчанию).

   Найдите параметр `storage: dbPath`.

1. Переместите папку, указанную в параметре `dbPath`, в новое расположение.

1. В файле конфигурации Mongo в параметре `dbPath` укажите новый путь к папке, сохраните изменения и закройте файл.

    ![Изменение конфигурации MongoDB (рисунок)](media/ATA-mongoDB-moveDB.png)

1. Запустите службу **MongoDB** .

1. Запустите службу **центра Microsoft Advanced Threat Analytics**.

## <a name="see-also"></a>См. также:
- [Архитектура ATA](ata-architecture.md)
- [Предварительные требования ATA](ata-prerequisites.md)
- [Обязательно ознакомьтесь с форумом ATA.](https://social.technet.microsoft.com/Forums/security/home?forum=mata)

