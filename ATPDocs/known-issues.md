---
title: Известные проблемы с Azure ATP | Документация Майкрософт
description: Описание текущих известных проблем в Azure ATP.
keywords: ''
author: mlottner
ms.author: mlottner
manager: mbaldwin
ms.date: 11/15/2018
ms.topic: conceptual
ms.prod: ''
ms.service: azure-advanced-threat-protection
ms.technology: ''
ms.assetid: feea1982-ba23-48be-a468-98d2586cf840
ms.reviewer: itargoet
ms.suite: ems
ms.openlocfilehash: 1d478957b33e65e0016600826718ae6efd4e0e43
ms.sourcegitcommit: f4e1d3e28037afc7b9a22355808a04a8dc8b9605
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/04/2018
ms.locfileid: "52831448"
---
*Применяется к: Azure Advanced Threat Protection*

# <a name="azure-atp-known-issues"></a>Известные проблемы с Azure ATP

В Azure ATP имеется ряд ограничений инженерного и функционального характера, иногда способных затруднять или блокировать использование служб Azure ATP вашей организацией. Здесь описаны известные проблемы, не имеющие обходных решений, или те, над которыми ведется работа без указания даты решения. 

Проблемы Azure ATP с известными обходными решениями см. в разделе [Устранение известных неполадок Azure ATP](troubleshooting-atp-known-issues.md). Проверить состояние клиента Azure ATP можно в [центре работоспособности Azure ATP](atp-health-center.md). 

## <a name="ad-groups-with-more-than-1000-members-have-limited-detail-sync"></a>Ограниченная синхронизация сведений в группах AD с более чем 1000 участников
> [!div class="mx-tableFixed"]  
|Проблема|Состояние|
|----|----|
|Azure ATP не поддерживает синхронизацию сведений о сущностях в группах AD, имеющих больше 1000 участников. При анализе сущностей в группах, где больше 1000 участников, синхронизация или отображение сведений некоторых сущностей могут не работать.|Это инженерное ограничение. Известного решения не существует.|

## <a name="report-downloads-cannot-contain-more-than-100000-entries"></a>Скачиваемые отчеты не могут включать больше 100 000 записей
> [!div class="mx-tableFixed"]  
|Проблема|Состояние|
|----|----|
|Azure ATP не поддерживает скачивание отчетов, содержащих больше 100 000 записей. Отчеты, в которых больше 100 000 записей, будут отображаться неполными.|Это инженерное ограничение. Известного решения не существует.|

# <a name="closed"></a>Закрыто 

Эта группа известных проблем закрыта. Проверьте номер версии исправления для справки.   
## <a name="remote-code-execution-attempts-using-remote-powershell-commands-or-scripts-are-not-detected-when-using-windows-server-2016---v257-december-2-2018"></a>Попытки удаленного выполнения кода использовать удаленные команды или скрипты PowerShell не обнаруживаются при использовании Windows Server 2016 — версия 2.57 (2 декабря 2018 г.)
> [!div class="mx-tableFixed"]  
|Проблема|Состояние|
|----|----|
|Попытки удаленного выполнения кода использовать удаленные команды PowerShell сейчас не обнаруживаются на компьютерах с датчиками, на которых запущена Windows Server 2016. Связанные обнаружения и полученные оповещения недоступны.|Инженеры работают над устранением этой проблемы и добавлением поддержки Windows Server 2016.|

## <a name="see-also"></a>См. также

- [Устранение известных неполадок Azure ATP](troubleshooting-atp-known-issues.md)
- [Устранение неполадок Azure ATP с помощью журналов](troubleshooting-atp-using-logs.md)
- [Новые возможности Azure ATP](atp-whats-new.md)
- [Загляните на форум Azure ATP!](https://aka.ms/azureatpcommunity)