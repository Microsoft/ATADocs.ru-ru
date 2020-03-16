---
title: Экспорт и импорт конфигурации Advanced Threat Analytics
description: Как выполнять экспорт и импорт конфигурации ATA.
keywords: ''
author: shsagir
ms.author: shsagir
manager: rkarlin
ms.date: 9/04/2018
ms.topic: conceptual
ms.prod: advanced-threat-analytics
ms.technology: ''
ms.assetid: 1d27dba8-fb30-4cce-a68a-f0b1df02b977
ms.reviewer: bennyl
ms.suite: ems
ms.openlocfilehash: f9e6c68fa0adcfa44707a42f7cd798ad7d3d8345
ms.sourcegitcommit: 11fff9d4ebf1c50b04f7789a22c80cdbc3e4416a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/15/2020
ms.locfileid: "79411485"
---
# <a name="export-and-import-the-ata-configuration"></a>Экспорт и импорт конфигурации ATA

*Применяется к: Advanced Threat Analytics версии 1.9*

Конфигурация ATA хранится в коллекции SystemProfile в базе данных.
Служба центра АТА каждые четыре часа проводит резервное копирование этой коллекции в файлы **SystemProfile_*метка времени*.json**. Сохраняются последние 300 версий.
Эти файлы расположены во вложенной папке с именем **Резервная копия**. По умолчанию их можно найти здесь: <em>C:\Program Files\Microsoft Advanced Threat Analytics\Center\Backup\SystemProfile_</em>timestamp<em>.json</em>. 

**Примечание**. Рекомендуем создавать резервную копию этого файла, когда в ATA вносятся важные изменения.

Можно восстановить все параметры, выполнив следующую команду:

`mongoimport.exe --db ATA --collection SystemProfile --file "<SystemProfile.json backup file>" --upsert`

## <a name="see-also"></a>См. также
- [Архитектура ATA](ata-architecture.md)
- [Предварительные требования ATA](ata-prerequisites.md)
- [Ознакомьтесь с форумом ATA.](https://social.technet.microsoft.com/Forums/security/home?forum=mata)

