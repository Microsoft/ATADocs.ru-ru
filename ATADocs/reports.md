---
title: "Работа с отчетами ATA | Документы Майкрософт"
description: "Описывается создание отчетов в ATA для мониторинга сети."
keywords: 
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 06/12/2017
ms.topic: article
ms.prod: 
ms.service: advanced-threat-analytics
ms.technology: 
ms.assetid: 38ea49b5-cd5e-43e5-bc39-5071f759633b
ms.reviewer: bennyl
ms.suite: ems
ms.openlocfilehash: 4f29dfcc8b18ff755f6c0dcdaa08eaa807b08072
ms.sourcegitcommit: 470675730967e0c36ebc90fc399baa64e7901f6b
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/30/2017
---
*Применяется к Advanced Threat Analytics версии 1.8*


# Отчеты ATA
<a id="ata-reports" class="xliff"></a>

Раздел отчетов в консоли ATA позволяет создавать отчеты, которые содержат сведения о состоянии системы (ее работоспособности и подозрительных действиях, обнаруженных в среде).

Чтобы открыть страницу отчетов, щелкните в строке меню значок отчета: ![значок отчета](./media/ata-report-icon.png).
Доступны указанные ниже отчеты. 
- Сводный отчет: представляет собой панель мониторинга состояния системы. Он содержит три вкладки: **Сводка** — сведения об угрозах, обнаруженных в сети; **Открытые подозрительные действия** — список подозрительных действий, на которые следует обратить внимание; **Открытые проблемы с работоспособностью** — список проблем с работоспособностью ATA, на которые следует обратить внимание. Подозрительные действия и проблемы с работоспособностью в списках разбиты по типам. 
- Изменение привилегированных групп: в этом отчете указано время каждого изменения, внесенного в привилегированные группы (например, группу администраторов).

Создавать отчеты можно двумя способами: по требованию или путем запланированной отправки отчета на ваш адрес электронной почты.

Чтобы создать отчет по требованию, выполните указанные ниже действия.

1. В строке меню консоли ATA щелкните значок отчета: ![значок отчета](./media/ata-report-icon.png).
2. В разделе **Сводка** или **Изменение привилегированных групп** укажите даты в полях **От** и **До**, а затем щелкните **Скачать**. 
![отчеты](./media/reports.png)

Чтобы настроить получение отчета по расписанию, выполните указанные ниже действия.
 
1. На странице **Отчеты** щелкните **Настроить запланированные отчеты** либо на странице настройки консоли ATA в разделе "Уведомления и отчеты" щелкните **Запланированные отчеты**.

   ![Планирование создания отчетов](./media/ata-sched-reports.png)

2. Рядом с элементом **Сводка** или **Изменение привилегированных групп** щелкните **Запланировать**, чтобы указать периодичность и адрес электронной почты, на который будут доставляться отчеты. Чтобы добавить адреса электронной почты, щелкните знак "плюс" рядом с ними. Нажмите кнопку **Сохранить**.

   ![Задание периодичности создания отчетов и адреса электронной почты](./media/sched-report1.png)


> [!NOTE]
> Запланированные отчеты доставляются по электронной почте. Их отправка возможна, только если вы уже настроили почтовый сервер. Для этого на странице **Конфигурация** в разделе "Уведомления и отчеты" выберите пункт **Почтовый сервер**.


## См. также
<a id="see-also" class="xliff"></a>
- [Предварительные требования ATA](ata-prerequisites.md)
- [Планирование производительности ATA](ata-capacity-planning.md)
- [Настройка сбора данных о событиях](configure-event-collection.md)
- [Настройка пересылки событий Windows](configure-event-collection.md#configuring-windows-event-forwarding)
- [Ознакомьтесь с форумом ATA.](https://social.technet.microsoft.com/Forums/security/home?forum=mata)