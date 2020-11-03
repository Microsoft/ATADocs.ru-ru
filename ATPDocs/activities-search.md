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
ms.openlocfilehash: 2767e9ccbac82e9770a89a1f436f7ed44f3b6bb5
ms.sourcegitcommit: f434dbff577d9944df18ca7533d026acdab0bb42
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/03/2020
ms.locfileid: "93277613"
---
# <a name="product-long-monitored-activities-search-and-filter"></a>[!INCLUDE [Product long](includes/product-long.md)] Поиск и фильтрация отслеживаемых действий

[!INCLUDE [Rebranding notice](includes/rebranding.md)]

> [!NOTE]
> [!INCLUDE [Product short](includes/product-short.md)]Функции, описанные на этой странице, также доступны с помощью нового [портала](https://portal.cloudappsecurity.com).

Действия, обнаруженные [!INCLUDE [Product short](includes/product-short.md)] в сети, можно искать и фильтровать для упрощения детализации и организации при исследовании и исследовании оповещений системы безопасности.

На [!INCLUDE [Product short](includes/product-short.md)] временной шкале выберите любую сущность в сети (DC, компьютер или пользователь) в качестве точки доступа фильтра. Затем выберите фильтрацию по **оповещениям системы безопасности** или **действиям** , или любые сочетания. После применения фильтра на временной шкале угроз для сущности появится отфильтрованная информация. Отфильтрованные оповещения и действия также можно скачать, чтобы продолжить их изучение или отслеживание другими инструментами.

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
- [Посетите [!INCLUDE [Product short](includes/product-short.md)] форум!](https://aka.ms/MDIcommunity)
