---
title: Настройка уведомлений Microsoft Defender для удостоверений
description: В этой статье описано, как настроить оповещения системы безопасности Microsoft Defender для удостоверений, чтобы получать уведомления при обнаружении подозрительных действий.
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
ms.openlocfilehash: 3eb687b716ce69bb4be0aabc2b128b1cf46242ff
ms.sourcegitcommit: e2227c0b0e5aaa5163dc56d4131ca82f8dca8fb0
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/18/2020
ms.locfileid: "94847145"
---
# <a name="set-product-long-notifications"></a>Настройка уведомлений [!INCLUDE [Product long](includes/product-long.md)]

[!INCLUDE [Product long](includes/product-long.md)] может по электронной почте отправлять уведомления при обнаружении подозрительных действий, а также оповещения системы безопасности и оповещения о проблемах с работоспособностью.

Чтобы получать уведомления на конкретный адрес электронной почты, установите следующие параметры.

1. На портале [!INCLUDE [Product short](includes/product-short.md)] на панели инструментов щелкните значок параметров и выберите пункт **Конфигурация**.

    ![[!INCLUDE [Product short](includes/product-short.md)]: значок параметров конфигурации](media/config-menu.png)

1. Щелкните **Уведомления**.
1. В разделе **Уведомления по почте** добавьте адреса электронной почты для получения интересующих вас уведомлений. Это могут быть новые предупреждения (о подозрительных действиях) и новые уведомления о проблемах с работоспособностью.

    > [!NOTE]
    >
    > - Письма отправляются только для уведомлений с заданными адресами.
    > - Электронные оповещения ATA о подозрительной активности отправляются только в случае ее обнаружения.

1. Нажмите кнопку **Сохранить**.

    ![[!INCLUDE [Product short](includes/product-short.md)]: уведомления](media/notifications.png)

## <a name="see-also"></a>См. также

- [Настройка сбора данных о событиях](configure-event-collection.md)

- [Настройка параметров системного журнала](setting-syslog.md)
- [Посетите форум по [!INCLUDE [Product short](includes/product-short.md)].](https://aka.ms/MDIcommunity)
