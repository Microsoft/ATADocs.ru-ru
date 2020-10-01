---
title: Настройка уведомлений Расширенной защиты от угроз Azure
description: В этой статье описано, как настроить оповещения системы безопасности Azure ATP, чтобы получать уведомления при обнаружении подозрительных действий.
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 09/29/2020
ms.topic: how-to
ms.collection: M365-security-compliance
ms.service: azure-advanced-threat-protection
ms.assetid: 4308f03e-b2a7-4e38-a750-540ff94faa81
ms.reviewer: itargoet
ms.suite: ems
ms.openlocfilehash: b60044cbc2ccf05ff1802ecce6e3e11d42543f97
ms.sourcegitcommit: dd8435ba20f76a6fc4590980c040c6fc7ec6c62b
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/29/2020
ms.locfileid: "91451754"
---
# <a name="set-azure-atp-notifications"></a>Настройка уведомлений Azure ATP

[!INCLUDE [Rebranding notice](includes/rebranding.md)]

Azure ATP может по электронной почте отправлять уведомления при обнаружении подозрительных действий, а также оповещения системы безопасности и оповещения о проблемах с работоспособностью.

Чтобы получать уведомления на конкретный адрес электронной почты, установите следующие параметры.

1. На портале Azure ATP на панели инструментов щелкните значок параметров и выберите пункт **Конфигурация**.

    ![Значок параметров конфигурации Azure ATP](media/atp-config-menu.png)

1. Щелкните **Уведомления**.
1. В разделе **Уведомления по почте** добавьте адреса электронной почты для получения интересующих вас уведомлений. Это могут быть новые предупреждения (о подозрительных действиях) и новые уведомления о проблемах с работоспособностью.

    > [!NOTE]
    >
    > - Письма отправляются только для уведомлений с заданными адресами.
    > - Электронные оповещения ATA о подозрительной активности отправляются только в случае ее обнаружения.

1. Нажмите кнопку **Сохранить**.

    ![Уведомления Azure ATP](media/atp-notifications.png)

## <a name="see-also"></a>См. также

- [Настройка сбора данных о событиях](configure-event-collection.md)

- [Настройка параметров системного журнала](setting-syslog.md)
- [Загляните на форум Azure ATP!](https://aka.ms/azureatpcommunity)
