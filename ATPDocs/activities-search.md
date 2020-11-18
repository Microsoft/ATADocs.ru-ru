---
title: Фильтрация и поиск действий, отслеживаемых защитником Майкрософт для операций идентификации
description: В этой статье содержатся общие сведения о фильтрации и поиске отслеживаемых действий с помощью защитника Майкрософт для идентификации.
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
ms.openlocfilehash: a35906a4d21dc5c3f9087956f7c7d4a3ad6dafdf
ms.sourcegitcommit: e2227c0b0e5aaa5163dc56d4131ca82f8dca8fb0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/18/2020
ms.locfileid: "94848845"
---
# <a name="product-long-monitored-activities-search-and-filter"></a>[!INCLUDE [Product long](includes/product-long.md)] Поиск и фильтрация отслеживаемых действий

> [!NOTE]
> Функции [!INCLUDE [Product short](includes/product-short.md)], описанные на этой странице, также доступны на новом [портале](https://portal.cloudappsecurity.com).

Действия, обнаруженные [!INCLUDE [Product short](includes/product-short.md)] в сети, можно искать и фильтровать для упрощения детализации и организации при исследовании и исследовании оповещений системы безопасности.

На [!INCLUDE [Product short](includes/product-short.md)] временной шкале выберите любую сущность в сети (DC, компьютер или пользователь) в качестве точки доступа фильтра. Затем выберите фильтрацию по **оповещениям системы безопасности** или **действиям**, или любые сочетания. После применения фильтра на временной шкале угроз для сущности появится отфильтрованная информация. Отфильтрованные оповещения и действия также можно скачать, чтобы продолжить их изучение или отслеживание другими инструментами.

![Фильтрация оповещений и действий](media/activities-filter.png)

Для фильтрации оповещений и действий сделайте следующее:

 1. Выберите сущность для изучения с [!INCLUDE [Product short](includes/product-short.md)] временной шкалы.
 2. Щелкните **Фильтровать по** и выберите оповещения и действия для фильтрации.
 3. Щелкните **Применить**. Временная шкала сущности изменится в соответствии с выбранными фильтрами.
 4. Чтобы скачать отфильтрованные действия, щелкните **Скачать действия** и выберите диапазон дат для скачиваемого отчета.
 5. Чтобы на временной шкале сущности отобразились все оповещения и действия, щелкните **Сброс** или закройте фильтр.

## <a name="see-also"></a>См. также:

- [Анализ сущностей](investigate-entity.md)
- [Оповещения о работоспособности](health-alerts.md)
- [Работа с оповещениями системы безопасности](working-with-suspicious-activities.md)
- [Посетите форум по [!INCLUDE [Product short](includes/product-short.md)].](https://aka.ms/MDIcommunity)
