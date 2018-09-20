---
title: Работа с журналами аудита ATA | Документы Майкрософт
description: В этой статье описывается работа с журналами аудита ATA в журнале событий Windows.
keywords: ''
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 3/21/2018
ms.topic: conceptual
ms.prod: advanced-threat-analytics
ms.service: ''
ms.technology: ''
ms.assetid: 1d186a96-ef70-4787-aa64-c03d1db94ce0
ms.reviewer: bennyl
ms.suite: ems
ms.openlocfilehash: 55712dfcb74e8779c2e06137ac3ea08f132a4f0f
ms.sourcegitcommit: 959b1f7753b9a8ad94870d2014376d55296fbbd4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/18/2018
ms.locfileid: "46133435"
---
*Применяется к: Advanced Threat Analytics версии 1.9*

# <a name="working-with-ata-audit-logs"></a>Работа с журналами аудита ATA

Журналы аудита ATA хранятся в журналах событий Windows в разделе **Приложения и службы** > **Microsoft ATA** как на компьютере центра ATA, так и на компьютерах шлюзов ATA.

Журнал аудита центра ATA содержит следующие сведения:
-   сведения о подозрительных действиях;
-   оповещения мониторинга (страница работоспособности);
-   сведения о входе в консоль ATA;
-   сведения о всех изменениях конфигурации. *

Журнал аудита шлюза ATA содержит следующие сведения:
-   сведения об изменениях конфигурации шлюза. * 

(Все изменения в конфигурации шлюза ATA настраиваются в центре ATA, но их аудит проводится на компьютере шлюза.)

* Журнал аудита изменений конфигурации содержит сведения как о прежней, так и о новой конфигурации.


## <a name="see-also"></a>См. также
- [Обработка подозрительных действий](working-with-suspicious-activities.md)
- [Ознакомьтесь с форумом ATA.](https://social.technet.microsoft.com/Forums/security/home?forum=mata)
