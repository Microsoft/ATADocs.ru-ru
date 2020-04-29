---
title: Работа с журналами аудита ATA
description: В этой статье описывается работа с журналами аудита ATA в журнале событий Windows.
keywords: ''
author: rkarlin
ms.author: rkarlin
manager: rkarlin
ms.date: 3/21/2018
ms.topic: conceptual
ms.prod: advanced-threat-analytics
ms.technology: ''
ms.assetid: 1d186a96-ef70-4787-aa64-c03d1db94ce0
ms.reviewer: bennyl
ms.suite: ems
ms.openlocfilehash: b1498ebf6cd11fad1eaec9d0f6c95dc4fc1f849c
ms.sourcegitcommit: 8c0222dc8333b5aa47430c5daee9bc7f1d82df31
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2020
ms.locfileid: "81524809"
---
# <a name="working-with-ata-audit-logs"></a>Работа с журналами аудита ATA


*Применяется к: Advanced Threat Analytics версии 1.9*

Журналы аудита ATA хранятся в журналах событий Windows в разделе **Приложения и службы** > **Microsoft ATA** как на компьютере центра ATA, так и на компьютерах шлюзов ATA.

Журнал аудита центра ATA содержит следующие сведения:
-   сведения о подозрительных действиях;
-   Оповещения о работоспособности (страница работоспособности)
-   сведения о входе в консоль ATA;
-   сведения о всех изменениях конфигурации. *

Журнал аудита шлюза ATA содержит следующие сведения:
-   сведения об изменениях конфигурации шлюза. * 

(Все изменения в конфигурации шлюза ATA настраиваются в центре ATA, но их аудит проводится на компьютере шлюза.)

* Журнал аудита изменений конфигурации содержит сведения как о прежней, так и о новой конфигурации.


## <a name="see-also"></a>См. также:
- [Обработка подозрительных действий](working-with-suspicious-activities.md)
- [Обязательно ознакомьтесь с форумом ATA.](https://social.technet.microsoft.com/Forums/security/home?forum=mata)
