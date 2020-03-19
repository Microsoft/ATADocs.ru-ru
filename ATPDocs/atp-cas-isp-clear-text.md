---
title: Проверка раскрытия простого текста в Расширенной защите от угроз Azure
description: В этой статье представлен обзор отчетов об оценке состояния безопасности удостоверений с раскрытием простого текста Azure ATP.
keywords: ''
author: shsagir
ms.author: shsagir
manager: rkarlin
ms.date: 07/08/2019
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.service: azure-advanced-threat-protection
ms.assetid: 124957bb-5882-4fcf-bab2-b74b0c69571d
ms.reviewer: itargoet
ms.suite: ems
ms.openlocfilehash: 6993c0caf30c1ea783cf47304219f1203648e3c5
ms.sourcegitcommit: 11fff9d4ebf1c50b04f7789a22c80cdbc3e4416a
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/15/2020
ms.locfileid: "79411332"
---
# <a name="security-assessment-entities-exposing-credentials-in-clear-text"></a>Оценка безопасности: раскрытие сущностями учетных данных в виде открытого текста 

![Оценка предотвращения раскрытия учетных данных в виде открытого текста в Cloud App Security](media/atp-cas-isp-clear-text-1.png)

## <a name="what-information-does-the-prevent-clear-text-security-assessment-provide"></a>Какие сведения обеспечивает оценка предотвращения раскрытия открытого текста? 

Эта оценка безопасности отслеживает трафик любых сущностей, предоставляющих учетные данные в виде открытого текста, и предупреждает о текущих рисках раскрытия (сильнее всего затронутых сущностях) в организации, одновременно предлагая исправления. 

## <a name="why-is-clear-text-credential-exposure-risky"></a>В чем риск раскрытия учетных данных в виде открытого текста?  
Передача учетных данных в виде открытого текста опасна не только для самой сущности, но и для всей организации.  

Повышенный риск заключается в том, что небезопасный трафик, такой как простая привязка LDAP, в значительной степени уязвим для перехвата в ходе атак типа "злоумышленник в середине". Эти типы атак приводят к вредоносным действиям, включая раскрытие учетных данных, при котором злоумышленник может использовать учетные данные для вредоносных целей. 

## <a name="how-do-i-use-this-security-assessment-to-improve-my-organizational-security-posture"></a>Как использовать эту оценку безопасности для повышения безопасности организации? 

1. Ознакомьтесь с оценкой безопасности, найдя затронутые сущности. 
    ![Обзор затронутых сущностей и создание плана действий](media/atp-cas-isp-clear-text-2.png)
1. Выясните, почему эти сущности используют LDAP в виде открытого текста. 
1. Устраните проблемы и прекратите раскрытие. 
1. Убедившись, что проблема устранена, включите обязательное подписывание LDAP на уровне контроллера домена. Дополнительные сведения о подписывании сервера LDAP см. в статье [Требования к подписыванию сервера LDAP контроллера домена](https://docs.microsoft.com/windows/security/threat-protection/security-policy-settings/domain-controller-ldap-server-signing-requirements). 
 

## <a name="next-steps"></a>Дальнейшие шаги
- [Фильтрация действий Azure ATP в Cloud App Security](atp-activities-filtering-mcas.md)
- [Загляните на форум Azure ATP!](https://aka.ms/azureatpcommunity)
