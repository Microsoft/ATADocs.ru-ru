---
title: "Экспорт и импорт конфигурации Advanced Threat Analytics | Документация Майкрософт"
description: "Как выполнять экспорт и импорт конфигурации ATA."
keywords: 
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 6/13/2017
ms.topic: article
ms.prod: 
ms.service: advanced-threat-analytics
ms.technology: 
ms.assetid: 1d27dba8-fb30-4cce-a68a-f0b1df02b977
ms.reviewer: bennyl
ms.suite: ems
ms.openlocfilehash: a04378838fab20c43df159ef3259530b8a599ed4
ms.sourcegitcommit: 470675730967e0c36ebc90fc399baa64e7901f6b
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/30/2017
---
*Применяется к Advanced Threat Analytics версии 1.8*



# Экспорт и импорт конфигурации ATA
<a id="export-and-import-the-ata-configuration" class="xliff"></a>
Конфигурация ATA хранится в коллекции SystemProfile в базе данных.
Служба центра АТА каждый час выполняет резервное копирование этой коллекции в файлы, которые называются SystemProfile_*timestamp*.json. Сохраняются последние 10 файлов.
Они расположены в подпапке с именем Backup (Резервная копия). По умолчанию их можно найти здесь: *C:\Program Files\Microsoft Advanced Threat Analytics\Center\Backup\SystemProfile_*timestamp*.json*. 

**Примечание**. Рекомендуем создавать резервную копию этого файла, когда в ATA вносятся важные изменения.

Можно восстановить все параметры, выполнив следующую команду:

`mongoimport.exe --db ATA --collection SystemProfile --file "<SystemProfile.json backup file>" --upsert`

## См. также
<a id="see-also" class="xliff"></a>
- [Архитектура ATA](ata-architecture.md)
- [Предварительные требования ATA](ata-prerequisites.md)
- [Ознакомьтесь с форумом ATA.](https://social.technet.microsoft.com/Forums/security/home?forum=mata)

