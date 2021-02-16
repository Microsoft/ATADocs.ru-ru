---
title: Настройка уведомлений Microsoft Defender для удостоверений
description: В этой статье описано, как настроить оповещения системы безопасности Microsoft Defender для удостоверений, чтобы получать уведомления при обнаружении подозрительных действий.
ms.date: 10/26/2020
ms.topic: how-to
ms.openlocfilehash: ad02fab44b76fc9d30af59a331ec5243796224d5
ms.sourcegitcommit: a892419a5cb95412e4643c35a9a72092421628ec
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/16/2021
ms.locfileid: "100533653"
---
# <a name="set-microsoft-defender-for-identity-notifications"></a>Настройка уведомлений Microsoft Defender для удостоверений

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
