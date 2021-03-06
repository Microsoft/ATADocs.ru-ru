---
title: Оценка неотслеживаемых контроллеров домена в защитнике Майкрософт
description: В этой статье представлен обзор защитника Майкрософт для неотслеживаемого отчета об оценке контроллеров домена с удостоверениями.
ms.date: 10/26/2020
ms.topic: how-to
ms.openlocfilehash: 86a1e02b84cf874f23fbf7b69d50c482cd15713b
ms.sourcegitcommit: cdb7ae4580851e25aae24d07e7d66a750aa54405
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/03/2020
ms.locfileid: "96544153"
---
# <a name="security-assessment-unmonitored-domain-controllers"></a>Оценка безопасности: Неотслеживаемые контроллеры домена

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
- [Посетите форум по [!INCLUDE [Product short](includes/product-short.md)].](https://aka.ms/MDIcommunity)
