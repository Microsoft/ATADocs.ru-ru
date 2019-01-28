---
title: Экспорт и импорт конфигурации Advanced Threat Analytics | Документация Майкрософт
description: Как выполнять экспорт и импорт конфигурации ATA.
keywords: ''
author: mlottner
ms.author: mlottner
manager: mbaldwin
ms.date: 9/04/2018
ms.topic: conceptual
ms.prod: advanced-threat-analytics
ms.service: ''
ms.technology: ''
ms.assetid: 1d27dba8-fb30-4cce-a68a-f0b1df02b977
ms.reviewer: bennyl
ms.suite: ems
ms.openlocfilehash: b470bc1a7de358d5326539aaf91d71ef08cb1282
ms.sourcegitcommit: f37127601166216e57e56611f85dd783c291114c
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/24/2019
ms.locfileid: "54839938"
---
# <a name="export-and-import-the-ata-configuration"></a>Экспорт и импорт конфигурации ATA

*Область применения: Advanced Threat Analytics версии 1.9*

Конфигурация ATA хранится в коллекции SystemProfile в базе данных.
Служба центра АТА каждые четыре часа проводит резервное копирование этой коллекции в файлы **SystemProfile_*timestamp*.json**. Сохраняются последние 300 версий.
Эти файлы расположены во вложенной папке с именем **Резервная копия**. Расположение установки АТА по умолчанию —  <em>C:\Program Files\Microsoft Advanced Threat Analytics\Center\Backup\SystemProfile_</em>timestamp<em>.json</em>. 

**Примечание**. Рекомендуем создавать резервную копию этого файла, когда в АТА вносятся важные изменения.

Можно восстановить все параметры, выполнив следующую команду:

`mongoimport.exe --db ATA --collection SystemProfile --file "<SystemProfile.json backup file>" --upsert`

## <a name="see-also"></a>См. также
- [Архитектура ATA](ata-architecture.md)
- [Предварительные требования ATA](ata-prerequisites.md)
- [Ознакомьтесь с форумом ATA.](https://social.technet.microsoft.com/Forums/security/home?forum=mata)

