---
title: Известные проблемы с Azure ATP | Документация Майкрософт
description: Описание текущих известных проблем в Azure ATP.
keywords: ''
author: mlottner
ms.author: mlottner
manager: mbaldwin
ms.date: 11/12/2018
ms.topic: conceptual
ms.prod: ''
ms.service: azure-advanced-threat-protection
ms.technology: ''
ms.assetid: feea1982-ba23-48be-a468-98d2586cf840
ms.reviewer: itargoet
ms.suite: ems
ms.openlocfilehash: c1c5aa0359ac0d24d2bf3fc3033986657c3fc897
ms.sourcegitcommit: 2afc1486b40431f442d51a53df06e289796de87e
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/12/2018
ms.locfileid: "51561435"
---
*Применяется к: Azure Advanced Threat Protection*

# <a name="azure-atp-known-issues"></a>Известные проблемы с Azure ATP

В Azure ATP имеется ряд ограничений инженерного и функционального характера, иногда способных затруднять или блокировать использование служб Azure ATP вашей организацией. Здесь описаны известные проблемы, не имеющие обходных решений, или те, над которыми ведется работа без указания даты решения. 

Проблемы Azure ATP с известными обходными решениями см. в разделе [Устранение известных неполадок Azure ATP](troubleshooting-atp-known-issues.md). Проверить состояние клиента Azure ATP можно в [центре работоспособности Azure ATP](atp-health-center.md). 

## <a name="winrm-not-supported-using-windows-server-2016"></a>WinRM не поддерживается в Windows Server 2016
> [!div class="mx-tableFixed"]  
|Проблема|Состояние|
|----|----|
|WinRM сейчас не поддерживает Windows Server 2016. Относящиеся сюда обнаружения и оповещения (попытки удаленного выполнения кода) недоступны на компьютерах с ОС Windows Server 2016.|Инженеры работают над устранением этой проблемы и добавлением поддержки Windows Server 2016.|

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

## <a name="see-also"></a>См. также

- [Устранение известных неполадок Azure ATP](troubleshooting-atp-known-issues.md)
- [Устранение неполадок Azure ATP с помощью журналов](troubleshooting-atp-using-logs.md)
- [Новые возможности Azure ATP](atp-whats-new.md)
- [Загляните на форум Azure ATP!](https://aka.ms/azureatpcommunity)