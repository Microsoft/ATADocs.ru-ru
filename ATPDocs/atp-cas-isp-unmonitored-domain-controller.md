---
title: Оценки неотслеживаемых контроллеров домена в Расширенной защите от угроз Azure
description: В этой статье содержится описание отчета Azure ATP по оценке состояния безопасности удостоверений для неотслеживаемых контроллеров домена.
keywords: ''
author: shsagir
ms.author: shsagir
manager: rkarlin
ms.date: 02/17/2020
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.service: azure-advanced-threat-protection
ms.assetid: 2fe62047-75ef-4b2e-b4aa-72860e39b4e4
ms.reviewer: itargoet
ms.suite: ems
ms.openlocfilehash: b82aa4af317b1eb913794f164449716180842c3c
ms.sourcegitcommit: d9abce00e781d47009e317767698d1729f70dc35
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/20/2020
ms.locfileid: "77478820"
---
# <a name="security-assessment-unmonitored-domain-controllers"></a>Оценка безопасности: Неотслеживаемые контроллеры домена

## <a name="what-are-unmonitored-domain-controllers"></a>Что такое неотслеживаемые контроллеры домена?

Основная часть решения Azure ATP требует, чтобы его датчики были развернуты на всех контроллерах домена в организации, обеспечивая исчерпывающее представление обо всех действиях пользователей на каждом устройстве.

По этой причине Azure ATP постоянно отслеживает вашу среду, чтобы определить контроллеры домена без установленных датчиков Azure ATP, а отчеты по этим неотслеживаемым серверам помогут вам в управлении вашей средой в целом.

## <a name="what-risk-do-unmonitored-domain-controllers-pose-to-an-organization"></a>Какие риски неотслеживаемые контроллеры домена налагают на организацию?

Чтобы обеспечить максимальную эффективность работы, все контроллеры домена должны отслеживаться с помощью датчиков Azure ATP. Организации, которые не могут исключить неотслеживаемые контроллеры домена из среды, сокращают возможности видимости среды и потенциально подвергают свои активы воздействию вредоносных факторов.

## <a name="how-do-i-use-this-security-assessment"></a>Как использовать эту оценку безопасности?

1. Используйте таблицу отчета, чтобы определить, какие контроллеры домена не отслеживаются.
    ![Устранение неотслеживаемых контроллеров домена](media/atp-cas-isp-unmonitored-domain-controller-1.png)
1. Выполните необходимые действия на этих контроллерах домена, [установив и настроив датчики мониторинга](atp-sensor-monitoring.md#domain-controller-status).

## <a name="see-also"></a>См. также

- [Мониторинг покрытия контроллеров домена](atp-sensor-monitoring.md)
- [Загляните на форум Azure ATP!](https://aka.ms/azureatpcommunity)
