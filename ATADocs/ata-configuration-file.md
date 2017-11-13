---
title: "Экспорт и импорт конфигурации Advanced Threat Analytics | Документация Майкрософт"
description: "Как выполнять экспорт и импорт конфигурации ATA."
keywords: 
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 11/7/2017
ms.topic: article
ms.prod: 
ms.service: advanced-threat-analytics
ms.technology: 
ms.assetid: 1d27dba8-fb30-4cce-a68a-f0b1df02b977
ms.reviewer: bennyl
ms.suite: ems
ms.openlocfilehash: e1e032adefc650bd4578f29043be313d2c44a866
ms.sourcegitcommit: 4d2ac5b02c682840703edb0661be09055d57d728
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/07/2017
---
*Применяется к Advanced Threat Analytics версии 1.8*



# <a name="export-and-import-the-ata-configuration"></a>Экспорт и импорт конфигурации ATA
Конфигурация ATA хранится в коллекции SystemProfile в базе данных.
Служба центра АТА каждый час выполняет резервное копирование этой коллекции в файлы **SystemProfile_*timestamp*.json**. Сохраняются последние 10 файлов. Эти файлы расположены во вложенной папке с именем **Резервная копия**. По умолчанию их можно найти здесь: *C:\Program Files\Microsoft Advanced Threat Analytics\Center\Backup\SystemProfile_*timestamp*.json*. 

**Примечание**. Рекомендуем создавать резервную копию этого файла, когда в ATA вносятся важные изменения.

Можно восстановить все параметры, выполнив следующую команду:

`mongoimport.exe --db ATA --collection SystemProfile --file "<SystemProfile.json backup file>" --upsert`

## <a name="see-also"></a>См. также
- [Архитектура ATA](ata-architecture.md)
- [Предварительные требования ATA](ata-prerequisites.md)
- [Ознакомьтесь с форумом ATA.](https://social.technet.microsoft.com/Forums/security/home?forum=mata)

