---
title: Настройка уведомлений Advanced Threat Protection | Документы Майкрософт
description: В этой статье описано, как настроить оповещения системы безопасности Azure ATP, чтобы получать уведомления при обнаружении подозрительных действий.
keywords: ''
author: shsagir
ms.author: shsagir
manager: rkarlin
ms.date: 10/04/2018
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.service: azure-advanced-threat-protection
ms.assetid: 4308f03e-b2a7-4e38-a750-540ff94faa81
ms.reviewer: itargoet
ms.suite: ems
ms.openlocfilehash: 39b1c0835402ff4ff688a28451fd7505f2cd364c
ms.sourcegitcommit: 9673eb49729a06d3a25d52c0f43c76ac61b9cf89
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/12/2020
ms.locfileid: "75906141"
---
# <a name="set-azure-atp-notifications"></a>Настройка уведомлений Azure ATP

Azure ATP может по электронной почте отправлять уведомления при обнаружении подозрительных действий, а также оповещения системы безопасности и оповещения о проблемах с работоспособностью. 

Чтобы получать уведомления на конкретный адрес электронной почты, установите следующие параметры.


1. На портале Azure ATP на панели инструментов щелкните значок параметров и выберите пункт **Конфигурация**.

   ![Значок параметров конфигурации Azure ATP](media/atp-config-menu.png)

2. Щелкните **Уведомления**.
3. В разделе **Почтовые уведомления** укажите, какие уведомления следует отправлять по электронной почте. Это могут быть уведомления о новых подозрительных действиях и новых проблемах с работоспособностью. 
 
   > [!NOTE]
   > Электронные оповещения ATA о подозрительной активности отправляются только в случае ее обнаружения.
 
4. Нажмите кнопку **Сохранить**.

   ![Уведомления Azure ATP](media/atp-notifications.png)



## <a name="see-also"></a>См. также

- [Настройка сбора данных о событиях](configure-event-collection.md)

- [Настройка параметров системного журнала](setting-syslog.md)
- [Загляните на форум Azure ATP!](https://aka.ms/azureatpcommunity)
