---
title: Работа с журналами аудита ATA
description: В этой статье описывается работа с журналами аудита ATA в журнале событий Windows.
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 3/21/2018
ms.topic: conceptual
ms.prod: advanced-threat-analytics
ms.technology: ''
ms.assetid: 1d186a96-ef70-4787-aa64-c03d1db94ce0
ms.reviewer: bennyl
ms.suite: ems
ms.openlocfilehash: 60819b4e941de53820f7ef858a73716a9f56bfa2
ms.sourcegitcommit: e844155ea57f73dfe2b47f4c5c1c7f5292ccbf1e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2020
ms.locfileid: "94690080"
---
# <a name="working-with-ata-audit-logs"></a>Работа с журналами аудита ATA


[!INCLUDE [Banner for top of topics](includes/banner.md)]

Журналы аудита ATA хранятся в журналах событий Windows в разделе **Приложения и службы** > **Microsoft ATA** как на компьютере центра ATA, так и на компьютерах шлюзов ATA.

Журнал аудита центра ATA содержит следующие сведения:
- сведения о подозрительных действиях;
- Оповещения о работоспособности (страница работоспособности)
- сведения о входе в консоль ATA;
- сведения о всех изменениях конфигурации. *

Журнал аудита шлюза ATA содержит следующие сведения:
- сведения об изменениях конфигурации шлюза. * 

(Все изменения в конфигурации шлюза ATA настраиваются в центре ATA, но их аудит проводится на компьютере шлюза.)

* Журнал аудита изменений конфигурации содержит сведения как о прежней, так и о новой конфигурации.


## <a name="see-also"></a>См. также:
- [Обработка подозрительных действий](working-with-suspicious-activities.md)
- [Обязательно ознакомьтесь с форумом ATA.](https://social.technet.microsoft.com/Forums/security/home?forum=mata)
