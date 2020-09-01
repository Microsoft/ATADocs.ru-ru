---
title: Настройка уведомлений Расширенной защиты от угроз Azure
description: В этой статье описано, как настроить оповещения системы безопасности Azure ATP, чтобы получать уведомления при обнаружении подозрительных действий.
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 10/04/2018
ms.topic: how-to
ms.collection: M365-security-compliance
ms.service: azure-advanced-threat-protection
ms.assetid: 4308f03e-b2a7-4e38-a750-540ff94faa81
ms.reviewer: itargoet
ms.suite: ems
ms.openlocfilehash: b54f609074c7e2a17eec51629682bade14e40cfa
ms.sourcegitcommit: 2be59f0bd4c9fd0d3827e9312ba20aa8eb43c6b5
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/27/2020
ms.locfileid: "88953411"
---
# <a name="set-azure-atp-notifications"></a>Настройка уведомлений Azure ATP

Azure ATP может по электронной почте отправлять уведомления при обнаружении подозрительных действий, а также оповещения системы безопасности и оповещения о проблемах с работоспособностью. 

Чтобы получать уведомления на конкретный адрес электронной почты, установите следующие параметры.


1. На портале Azure ATP на панели инструментов щелкните значок параметров и выберите пункт **Конфигурация**.

    ![Значок параметров конфигурации Azure ATP](media/atp-config-menu.png)

1. Щелкните **Уведомления**.
1. В разделе **Почтовые уведомления** укажите, какие уведомления следует отправлять по электронной почте. Это могут быть уведомления о новых подозрительных действиях и новых проблемах с работоспособностью. 
 
   > [!NOTE]
   > Электронные оповещения ATA о подозрительной активности отправляются только в случае ее обнаружения.
 
1. Нажмите кнопку **Сохранить**.

    ![Уведомления Azure ATP](media/atp-notifications.png)



## <a name="see-also"></a>См. также

- [Настройка сбора данных о событиях](configure-event-collection.md)

- [Настройка параметров системного журнала](setting-syslog.md)
- [Загляните на форум Azure ATP!](https://aka.ms/azureatpcommunity)
