---
title: Экспорт и импорт конфигурации Advanced Threat Analytics | Документация Майкрософт
description: Как выполнять экспорт и импорт конфигурации ATA.
keywords: ''
author: mlottner
ms.author: mlottner
manager: mbaldwin
ms.date: 9/04/2018
ms.topic: article
ms.prod: ''
ms.service: advanced-threat-analytics
ms.technology: ''
ms.assetid: 1d27dba8-fb30-4cce-a68a-f0b1df02b977
ms.reviewer: bennyl
ms.suite: ems
ms.openlocfilehash: f8847d8ca3671f765a1d101121eefad62073f60f
ms.sourcegitcommit: 6f1406f28c4c2af6a36bc691ebaf4e819adc6b4b
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/04/2018
ms.locfileid: "43675157"
---
*Применяется к: Advanced Threat Analytics версии 1.9*



# <a name="export-and-import-the-ata-configuration"></a>Экспорт и импорт конфигурации ATA
Конфигурация ATA хранится в коллекции SystemProfile в базе данных.
Служба центра АТА каждые четыре часа проводит резервное копирование этой коллекции в файлы **SystemProfile_*метка времени*.json**. Сохраняются последние 300 версий.
Эти файлы расположены во вложенной папке с именем **Резервная копия**. По умолчанию их можно найти здесь: *C:\Program Files\Microsoft Advanced Threat Analytics\Center\Backup\SystemProfile_* timestamp *.json*. 

**Примечание**. Рекомендуем создавать резервную копию этого файла, когда в ATA вносятся важные изменения.

Можно восстановить все параметры, выполнив следующую команду:

`mongoimport.exe --db ATA --collection SystemProfile --file "<SystemProfile.json backup file>" --upsert`

## <a name="see-also"></a>См. также
- [Архитектура ATA](ata-architecture.md)
- [Предварительные требования ATA](ata-prerequisites.md)
- [Ознакомьтесь с форумом ATA.](https://social.technet.microsoft.com/Forums/security/home?forum=mata)

