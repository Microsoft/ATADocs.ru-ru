---
title: "Экспорт и импорт конфигурации Advanced Threat Analytics | Документация Майкрософт"
description: "Как выполнять экспорт и импорт конфигурации ATA."
keywords: 
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 1/23/2017
ms.topic: article
ms.prod: 
ms.service: advanced-threat-analytics
ms.technology: 
ms.assetid: 1d27dba8-fb30-4cce-a68a-f0b1df02b977
ms.reviewer: bennyl
ms.suite: ems
ms.openlocfilehash: b0d85b60129e2638880c11b5f1faadca2feeae2c
ms.sourcegitcommit: 49e892a82275efa5146998764e850959f20d3216
translationtype: HT
---
*Область применения: Advanced Threat Analytics версии 1.7*



# <a name="export-and-import-the-ata-configuration"></a>Экспорт и импорт конфигурации ATA
Конфигурация ATA хранится в коллекции SystemProfile в базе данных.
Служба центра АТА каждый час выполняет резервное копирование этой коллекции в файлы, которые называются SystemProfile_*timestamp*.json. Сохраняются последние 10 файлов.
Они расположены в подпапке с именем Backup (Резервная копия). По умолчанию их можно найти здесь: *C:\Program Files\Microsoft Advanced Threat Analytics\Center\Backup\SystemProfile_*timestamp*.json*. 

**Примечание**. Рекомендуем создавать резервную копию этого файла, когда в ATA вносятся важные изменения.

Можно восстановить все параметры, выполнив следующую команду:

`mongoimport.exe --db ATA --collection SystemProfile --file "<SystemProfile.json backup file>" --upsert`

## <a name="see-also"></a>См. также
- [Архитектура ATA](/advanced-threat-analytics/plan-design/ata-architecture)
- [Предварительные требования ATA](/advanced-threat-analytics/plan-design/ata-prerequisites)
- [Ознакомьтесь с форумом ATA.](https://social.technet.microsoft.com/Forums/security/home?forum=mata)

