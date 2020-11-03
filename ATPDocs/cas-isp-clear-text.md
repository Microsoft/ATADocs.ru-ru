---
title: Оценка уязвимости в защитнике Майкрософт для идентификации открытого текста
description: В этой статье приводятся общие сведения о защитнике Майкрософт для отчета об оценке уровня защиты идентификации открытого текста.
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 08/25/2020
ms.topic: how-to
ms.collection: M365-security-compliance
ms.service: azure-advanced-threat-protection
ms.reviewer: itargoet
ms.suite: ems
ms.openlocfilehash: 9586c5441f09959970752a15cfff3c2f953f1842
ms.sourcegitcommit: f434dbff577d9944df18ca7533d026acdab0bb42
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/03/2020
ms.locfileid: "93277602"
---
# <a name="security-assessment-entities-exposing-credentials-in-clear-text"></a>Оценка безопасности: раскрытие сущностями учетных данных в виде открытого текста

[!INCLUDE [Rebranding notice](includes/rebranding.md)]

![Оценка предотвращения раскрытия учетных данных в виде открытого текста в Cloud App Security](media/cas-isp-clear-text-1.png)

## <a name="what-information-does-the-prevent-clear-text-security-assessment-provide"></a>Какие сведения обеспечивает оценка предотвращения раскрытия открытого текста?

Эта оценка безопасности отслеживает трафик любых сущностей, предоставляющих учетные данные в виде открытого текста, и предупреждает о текущих рисках раскрытия (сильнее всего затронутых сущностях) в организации, одновременно предлагая исправления.

## <a name="why-is-clear-text-credential-exposure-risky"></a>В чем риск раскрытия учетных данных в виде открытого текста?

Передача учетных данных в виде открытого текста опасна не только для самой сущности, но и для всей организации.

Повышенный риск заключается в том, что небезопасный трафик, такой как простая привязка LDAP, в значительной степени уязвим для перехвата в ходе атак типа "злоумышленник в середине". Эти типы атак приводят к вредоносным действиям, включая раскрытие учетных данных, при котором злоумышленник может использовать учетные данные для вредоносных целей.

## <a name="how-do-i-use-this-security-assessment-to-improve-my-organizational-security-posture"></a>Как использовать эту оценку безопасности для повышения безопасности организации?

1. Ознакомьтесь с оценкой безопасности, найдя затронутые сущности.
    ![Обзор затронутых сущностей и создание плана действий](media/cas-isp-clear-text-2.png)
1. Выясните, почему эти сущности используют LDAP в виде открытого текста.
1. Устраните проблемы и прекратите раскрытие.
1. Убедившись, что проблема устранена, включите обязательное подписывание LDAP на уровне контроллера домена. Дополнительные сведения о подписывании сервера LDAP см. в статье [Требования к подписыванию сервера LDAP контроллера домена](/windows/security/threat-protection/security-policy-settings/domain-controller-ldap-server-signing-requirements).

> [!NOTE]
> Эта оценка обновляется практически в реальном времени.

## <a name="next-steps"></a>Дальнейшие шаги

- [[!INCLUDE [Product short](includes/product-short.md)] Фильтрация действий в Cloud App Security](activities-filtering-mcas.md)
- [Посетите [!INCLUDE [Product short](includes/product-short.md)] форум!](https://aka.ms/MDIcommunity)