---
title: Экспорт и импорт конфигурации Advanced Threat Analytics | Документация Майкрософт
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
ms.openlocfilehash: 522c4e197a52c6ccbd40d7ab1e8dea1764bce275
ms.sourcegitcommit: 9673eb49729a06d3a25d52c0f43c76ac61b9cf89
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/12/2020
ms.locfileid: "75905421"
---
# <a name="export-and-import-the-ata-configuration"></a>Экспорт и импорт конфигурации ATA

*Применяется к: Advanced Threat Analytics версии 1.9*

Конфигурация ATA хранится в коллекции SystemProfile в базе данных.
Служба центра АТА каждые четыре часа проводит резервное копирование этой коллекции в файлы **SystemProfile_*метка времени*.json**. Сохраняются последние 300 версий.
Этот файл находится во вложенной папке с именем **BACKUP**. По умолчанию их можно найти здесь: <em>C:\Program Files\Microsoft Advanced Threat Analytics\Center\Backup\SystemProfile_</em>timestamp<em>.json</em>. 

**Примечание**. Рекомендуем создавать резервную копию этого файла, когда в ATA вносятся важные изменения.

Можно восстановить все параметры, выполнив следующую команду:

`mongoimport.exe --db ATA --collection SystemProfile --file "<SystemProfile.json backup file>" --upsert`

## <a name="see-also"></a>См. также
- [Архитектура ATA](ata-architecture.md)
- [Предварительные требования ATA](ata-prerequisites.md)
- [Ознакомьтесь с форумом ATA.](https://social.technet.microsoft.com/Forums/security/home?forum=mata)

