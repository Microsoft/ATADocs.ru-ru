---
title: Оценка неотслеживаемых контроллеров домена в защитнике Майкрософт
description: В этой статье представлен обзор защитника Майкрософт для неотслеживаемого отчета об оценке контроллеров домена с удостоверениями.
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 10/26/2020
ms.topic: how-to
ms.collection: M365-security-compliance
ms.service: azure-advanced-threat-protection
ms.reviewer: itargoet
ms.suite: ems
ms.openlocfilehash: ffa62906d0c4f8a40c1beb388e497ed12ee41733
ms.sourcegitcommit: f434dbff577d9944df18ca7533d026acdab0bb42
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/03/2020
ms.locfileid: "93276626"
---
# <a name="security-assessment-unmonitored-domain-controllers"></a>Оценка безопасности: Неотслеживаемые контроллеры домена

[!INCLUDE [Rebranding notice](includes/rebranding.md)]

## <a name="what-are-unmonitored-domain-controllers"></a>Что такое неотслеживаемые контроллеры домена?

Основная часть [!INCLUDE [Product long](includes/product-long.md)] решения требует, чтобы его датчики были развернуты на всех организационных контроллерах домена, обеспечивая исчерпывающее представление для всех действий пользователей с каждого устройства.

По этой причине [!INCLUDE [Product short](includes/product-short.md)] постоянно отслеживает среду для определения контроллеров домена без установленного [!INCLUDE [Product short](includes/product-short.md)] датчика, а также отчеты на этих неотслеживаемых серверах, чтобы помочь в управлении полным покрытием среды.

## <a name="what-risk-do-unmonitored-domain-controllers-pose-to-an-organization"></a>Какие риски неотслеживаемые контроллеры домена налагают на организацию?

Для обеспечения максимальной эффективности все контроллеры домена должны отслеживаться с помощью [!INCLUDE [Product short](includes/product-short.md)] датчиков. Организации, которые не могут исключить неотслеживаемые контроллеры домена из среды, сокращают возможности видимости среды и потенциально подвергают свои активы воздействию вредоносных факторов.

## <a name="how-do-i-use-this-security-assessment"></a>Как использовать эту оценку безопасности?

1. Используйте таблицу отчета, чтобы определить, какие контроллеры домена не отслеживаются.
    ![Устранение неотслеживаемых контроллеров домена](media/cas-isp-unmonitored-domain-controller-1.png)
1. Выполните необходимые действия на этих контроллерах домена, [установив и настроив датчики мониторинга](sensor-monitoring.md#domain-controller-status).

> [!NOTE]
> Эта оценка обновляется практически в реальном времени.

## <a name="see-also"></a>См. также

- [Мониторинг покрытия контроллеров домена](sensor-monitoring.md)
- [Посетите [!INCLUDE [Product short](includes/product-short.md)] форум!](https://aka.ms/MDIcommunity)
