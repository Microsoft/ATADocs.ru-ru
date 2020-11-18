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
ms.openlocfilehash: 6a5d110d35ad3b49205d4c0b7b03412fe26626ae
ms.sourcegitcommit: e2227c0b0e5aaa5163dc56d4131ca82f8dca8fb0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/18/2020
ms.locfileid: "94848794"
---
# <a name="security-assessment-entities-exposing-credentials-in-clear-text"></a>Оценка безопасности: раскрытие сущностями учетных данных в виде открытого текста

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
- [Посетите форум по [!INCLUDE [Product short](includes/product-short.md)].](https://aka.ms/MDIcommunity)