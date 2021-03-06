---
title: Microsoft Defender для идентификации оценки использования Microsoft Lap
description: В этой статье приводятся общие сведения о защитнике Майкрософт в отчете об оценке уровня безопасности для идентификации Microsoft Lap Usage.
ms.date: 10/26/2020
ms.topic: how-to
ms.openlocfilehash: d829636ac9659a19453db6f4cadfba54d129593d
ms.sourcegitcommit: cdb7ae4580851e25aae24d07e7d66a750aa54405
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/03/2020
ms.locfileid: "96543643"
---
# <a name="security-assessment-microsoft-laps-usage"></a>Оценка безопасности: Использование Microsoft LAPS

## <a name="what-is-microsoft-laps"></a>Что такое Microsoft LAPS?

Решение Майкрософт "Local Administrator Password Solution" (LAPS) позволяет управлять паролями учетных записей локальных администраторов для компьютеров, присоединенных к домену. Пароли являются случайными, хранятся в Active Directory (AD) и защищаются списками управления доступом (ACL), поэтому только соответствующие пользователи могут читать их или запрашивать их сброс.

## <a name="what-risk-does-not-implementing-laps-pose-to-an-organization"></a>Какому риску подвержена организация, не внедрившая LAPS?

LAPS предоставляет решение проблемы использования общей локальной учетной записи с одинаковым паролем на каждом компьютере в домене. LAPS решает эту проблему, устанавливая другой, циклически сдвигаемый случайный пароль для общей учетной записи локального администратора на каждом компьютере в домене.

LAPS упрощает управление паролями, в то же время помогая клиентам реализовать дополнительные рекомендуемые средства защиты от кибератак. В частности, это решение снижает риск эскалации бокового смещения, которая возникает, когда клиенты используют одну и ту же комбинацию учетной записи и пароля администратора на своих компьютерах. LAPS безопасно хранит пароль локальной учетной записи администратора для каждого компьютера в AD, в конфиденциальном атрибуте в соответствующем объекте AD компьютера. Компьютер может обновлять свои данные паролей в AD, а администраторы домена могут предоставлять доступ на чтение полномочным пользователям или группам, например, администраторам службы поддержки рабочих станций.

## <a name="how-do-i-use-this-security-assessment"></a>Как использовать эту оценку безопасности?

1. С помощью таблицы отчета можно определить, в каких из ваших доменов имеются совместимые устройства Windows, не защищенные LAPS, или пароли которых, управляемые LAPS, не изменялись за последние 60 дней.
1. Для частично защищенных доменов выберите соответствующую строку, чтобы просмотреть список не защищенных LAPS устройств в этом домене.
    ![Выбор домена с устройствами LAPS](media/cas-isp-laps-1.png)
1. Выполните необходимые действия на этих устройствах — загрузите, установите и настройте [Microsoft LAPS](https://go.microsoft.com/fwlink/?linkid=2104282) или устраните неполадки, используя документацию, представленную в загружаемом файле.
    ![Исправление устройства LAPS](media/cas-isp-laps-2.png)

> [!NOTE]
> Эта оценка обновляется каждые 24 часа.

## <a name="see-also"></a>См. также

- [Посетите форум по [!INCLUDE [Product short](includes/product-short.md)].](https://aka.ms/MDIcommunity)
