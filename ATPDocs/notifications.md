---
title: Настройка уведомлений Advanced Threat Protection | Документы Майкрософт
description: В этой статье описано, как настроить оповещения Azure ATP, чтобы получать уведомления при обнаружении подозрительных действий.
keywords: ''
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 2/21/2018
ms.topic: article
ms.prod: ''
ms.service: azure-advanced-threat-protection
ms.technology: ''
ms.assetid: 4308f03e-b2a7-4e38-a750-540ff94faa81
ms.reviewer: itargoet
ms.suite: ems
ms.openlocfilehash: 85fe887df373d8132df932cdb3d1eaf5ab954a1d
ms.sourcegitcommit: 03e959b7ce4b6df421297e1872e028793c967302
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/21/2018
ms.locfileid: "29444850"
---
*Применяется к: Azure Advanced Threat Protection*


# <a name="set-azure-atp-notifications"></a>Настройка уведомлений Azure ATP

Azure ATP может по электронной почте отправлять уведомления при обнаружении подозрительных действий или при возникновении проблем с работоспособностью. 

Чтобы получать уведомления на конкретный адрес электронной почты, установите следующие параметры.


1. На портале рабочей области Azure ATP на панели инструментов щелкните значок параметров и выберите пункт **Конфигурация**.

![Значок параметров конфигурации Azure ATP](media/atp-config-menu.png)

2. Щелкните **Уведомления**.
3. В разделе **Почтовые уведомления** укажите, какие уведомления следует отправлять по электронной почте. Это могут быть уведомления о новых подозрительных действиях и новых проблемах с работоспособностью. 
 
 >  [!NOTE]
 >   Электронные оповещения ATA о подозрительной активности отправляются только в случае ее обнаружения.

5. Нажмите кнопку **Сохранить**.

 ![Уведомления Azure ATP](media/atp-notifications.png)



## <a name="see-also"></a>См. также

- [Настройка сбора данных о событиях](configure-event-collection.md)

- [Настройка параметров системного журнала](setting-syslog.md)
- [Обязательно ознакомьтесь с форумом ATP](https://aka.ms/azureatpcommunity)