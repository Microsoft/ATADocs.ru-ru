---
title: "Устранение неполадок в Advanced Threat Analytics с использованием журналов | Документация Майкрософт"
description: "В этой статье описывается, как использовать журналы событий ATA для устранения неполадок"
keywords: 
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 06/26/2017
ms.topic: article
ms.prod: 
ms.service: advanced-threat-analytics
ms.technology: 
ms.assetid: 5a65285c-d1de-4025-9bb4-ef9c20b13cfa
ms.reviewer: bennyl
ms.suite: ems
ms.openlocfilehash: 1291281273188a21b61b29f06a5220eee589767c
ms.sourcegitcommit: 470675730967e0c36ebc90fc399baa64e7901f6b
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/30/2017
---
*Применяется к Advanced Threat Analytics версии 1.8*



# Устранение неполадок при запуске службы центра ATA
<a id="troubleshooting-ata-center-service-startup" class="xliff"></a>

Если центр ATA не запускается, выполните описанную ниже процедуру устранения неполадок.

1.  Выполните следующую команду Windows PowerShell: Get-Service Pla | Выберите "Состояние", чтобы убедиться в том, что служба счетчиков производительности запущена. Если она не запущена, это неполадка платформы и эту службу необходимо снова запустить.
2.  Если она была запущена, попробуйте перезапустить ее, чтобы проверить, не исчезнет ли проблема: Restart-Service Pla
3.  Попробуйте создать новый сборщик данных вручную (достаточно любого сборщика, например, для сбора данных по ЦП компьютера).
Если он запускается, скорее всего, платформа исправна. В противном случае имеется неполадка платформы.

4.  Попробуйте повторно создать сборщик данных ATA вручную, выполнив следующие команды в командной строке с повышенными привилегиями: sc stop ATACenter logman stop "Microsoft ATA Center" logman export "Microsoft ATA Center" -xml c:\center.xml logman delete "Microsoft ATA Center" logman import "Microsoft ATA Center" -xml c:\center.xml logman start "Microsoft ATA Center" sc start ATACenter.



## См. также
<a id="see-also" class="xliff"></a>
- [Предварительные требования ATA](ata-prerequisites.md)
- [Планирование производительности ATA](ata-capacity-planning.md)
- [Настройка сбора данных о событиях](configure-event-collection.md)
- [Настройка пересылки событий Windows](configure-event-collection.md#configuring-windows-event-forwarding)
- [Ознакомьтесь с форумом ATA.](https://social.technet.microsoft.com/Forums/security/home?forum=mata)
