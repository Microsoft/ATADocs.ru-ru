---
title: Экспорт и импорт конфигурации Advanced Threat Analytics
description: Как выполнять экспорт и импорт конфигурации ATA.
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 9/04/2018
ms.topic: conceptual
ms.prod: advanced-threat-analytics
ms.technology: ''
ms.assetid: 1d27dba8-fb30-4cce-a68a-f0b1df02b977
ms.reviewer: bennyl
ms.suite: ems
ms.openlocfilehash: 3d596b1833db7221027295014e114a07b45f2f6f
ms.sourcegitcommit: e844155ea57f73dfe2b47f4c5c1c7f5292ccbf1e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2020
ms.locfileid: "94691100"
---
# <a name="export-and-import-the-ata-configuration"></a>Экспорт и импорт конфигурации ATA

[!INCLUDE [Banner for top of topics](includes/banner.md)]

Конфигурация ATA хранится в коллекции SystemProfile в базе данных.
Служба центра АТА каждые четыре часа проводит резервное копирование этой коллекции в файлы **SystemProfile_ *метка времени*.json**. Сохраняются последние 300 версий.
Эти файлы расположены во вложенной папке с именем **Резервная копия**. По умолчанию их можно найти здесь: <em>C:\Program Files\Microsoft Advanced Threat Analytics\Center\Backup\SystemProfile_</em>timestamp<em>.json</em>. 

**Примечание**. Рекомендуем создавать резервную копию этого файла, когда в ATA вносятся важные изменения.

Можно восстановить все параметры, выполнив следующую команду:

`mongoimport.exe --db ATA --collection SystemProfile --file "<SystemProfile.json backup file>" --upsert`

## <a name="see-also"></a>См. также:
- [Архитектура ATA](ata-architecture.md)
- [Предварительные требования ATA](ata-prerequisites.md)
- [Обязательно ознакомьтесь с форумом ATA.](https://social.technet.microsoft.com/Forums/security/home?forum=mata)

