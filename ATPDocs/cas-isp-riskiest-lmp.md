---
title: Оценка путей бокового смещения с наибольшим риском в Расширенной защите от угроз Azure
description: В этой статье представлен обзор отчета об оценке состояния безопасности удостоверений Azure ATP, который сообщает о конфиденциальных сущностях с путями бокового смещения, несущими наибольший риск.
keywords: ''
author: shsagir
ms.author: shsagir
manager: rkarlin
ms.date: 08/25/2020
ms.topic: how-to
ms.collection: M365-security-compliance
ms.service: azure-advanced-threat-protection
ms.assetid: 2fe62047-75ef-4b2e-b4aa-72860e39b4e4
ms.reviewer: itargoet
ms.suite: ems
ms.openlocfilehash: 04b1cefbb1c03d3dfe38c743b2a910a97664d01e
ms.sourcegitcommit: c7c0a4c9f7507f3e8e0f219798ed7d347c03e792
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/22/2020
ms.locfileid: "90913154"
---
# <a name="security-assessment-riskiest-lateral-movement-paths-lmp"></a>Оценка безопасности: пути бокового смещения с максимальным риском

[!INCLUDE [Rebranding notice](includes/rebranding.md)]

## <a name="what-are-risky-lateral-movement-paths"></a>Что такое рискованные пути бокового смещения?

Azure ATP постоянно отслеживает вашу среду, чтобы выявлять **конфиденциальные** учетные записи с путями бокового смещения, создающими максимальный риск для безопасности, и сообщает об этих учетных записях, помогая вам держать среду под контролем. Пути считаются рискованными, если они затрагивают как минимум три неконфиденциальные учетные записи, создающие возможность кражи учетных данных **конфиденциальной** записи злоумышленниками.

Дополнительные сведения о путях бокового смещения:

- [Пути бокового смещения Azure ATP](use-case-lateral-movement-path.md)
- [Боковое смещение на сайте MITRE ATT&CK](https://attack.mitre.org/tactics/TA0008/)

## <a name="what-risk-do-risky-lateral-movement-paths-pose"></a>Какой риск несут пути бокового смещения?

Организации, которые не могут защитить свои **конфиденциальные** учетные записи, оставляют незапертую дверь для злонамеренных субъектов.

Вредоносные субъекты, как и другие мошенники, часто ищут самый простой и тихий способ действовать в любой среде. Конфиденциальные учетные записи с рискованными путями бокового смещения открывают окна возможностей для злоумышленников и способны создавать риски.

Например, самые рискованные из этих путей более заметны для злоумышленников и в случае компрометации могут предоставить им доступ к наиболее конфиденциальным сущностям вашей организации.

## <a name="how-do-i-use-this-security-assessment"></a>Как использовать эту оценку безопасности?

1. Узнать, какие из ваших **конфиденциальных** учетных записей имеют рискованные пути бокового движения, можно в таблице отчета.
    ![Обзор наиболее затронутых сущностей и создание плана действий](media/atp-cas-isp-riskiest-lmp-1.png)
1. Примите необходимые меры:
    - Удалите сущность из группы, как указано в рекомендации.
    - Удалите разрешения локального администратора для сущности с устройства, указанного в рекомендации.

    > [!NOTE]
    > Подождите 24 часа и убедитесь, что эта рекомендация больше не отображается в списке.

> [!NOTE]
> Эта оценка обновляется каждые 24 часа.

## <a name="see-also"></a>См. также

- [Фильтрация действий Azure ATP в Cloud App Security](activities-filtering-mcas.md)
- [Загляните на форум Azure ATP!](https://aka.ms/azureatpcommunity)