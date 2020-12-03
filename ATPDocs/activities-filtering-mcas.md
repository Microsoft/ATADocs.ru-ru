---
title: Фильтрация и политики в защитнике Майкрософт для действий с удостоверениями в Microsoft Cloud App Security
description: Обзор защитника Майкрософт для фильтрации и политик действий идентификации с помощью Microsoft Cloud App Security.
ms.date: 10/26/2020
ms.topic: how-to
ms.openlocfilehash: 5956ebfb9904465e876a21b918255f44ec651ae9
ms.sourcegitcommit: cdb7ae4580851e25aae24d07e7d66a750aa54405
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/03/2020
ms.locfileid: "96544255"
---
# <a name="use-activity-filters-and-create-action-policies-with-product-long-in-microsoft-cloud-app-security"></a>Использование фильтров действий и создание политик действий с помощью [!INCLUDE [Product long](includes/product-long.md)] в Microsoft Cloud App Security

Эта статья поможет вам понять, как фильтровать и создавать политики действий [!INCLUDE [Product short](includes/product-short.md)] с помощью Microsoft Cloud App Security.

Дополнительные сведения о том, как выполнить интеграцию, см. [ [!INCLUDE [Product short](includes/product-short.md)] в разделе интеграция с Cloud App Security](/cloud-app-security/aatp-integration).

Использование [!INCLUDE [Product short](includes/product-short.md)] с Microsoft Cloud App Security предлагает анализ действий и оповещения на основе анализа поведения пользователей и сущностей (уеба), определение поведения угрожаемый на предприятии, предоставление комплексной оценки приоритета расследования, а также фильтрацию действий и настраиваемые политики действий.

## <a name="prerequisites"></a>Предварительные условия

Чтобы получить все возможности изучения поведения пользователей в гибридной среде, вам понадобится следующее:

- Действительная лицензия для Microsoft Cloud App Security
- Действительная лицензия для [!INCLUDE [Product long](includes/product-long.md)] подключения к экземпляру Active Directory

>[!NOTE]
>Если у вас нет подписки на Cloud App Security, вы можете использовать портал Cloud App Security для изучения [!INCLUDE [Product short](includes/product-short.md)] оповещений и глубокого исследования пользователей и их локальных управляемых действий, однако аналитические данные, связанные с облачными приложениями, останутся недоступными.

## <a name="filter-product-short-activities-in-cloud-app-security"></a>Фильтрация [!INCLUDE [Product short](includes/product-short.md)] действий в Cloud App Security

[!INCLUDE [Product short](includes/product-short.md)] доступ к действиям можно получить из главного меню Cloud App Security **исследовать** , выбрав подменю **журнала действий** или меню **оповещения** , указав состояние, категорию, серьезность, приложение, имя пользователя или политика.

Для доступа к [!INCLUDE [Product short](includes/product-short.md)] действиям по пользователям:

1. Отфильтруйте очередь **Оповещения** с использованием поля "Имя пользователя".
    ![Фильтрация оповещений по имени пользователя](media/mcas-alerts-queue.png)
1. Щелкните имя пользователя для какого-либо оповещения в полученном списке, чтобы открыть **страницу пользователя**, поведение которого нужно изучить.

1. Отфильтруйте действия пользователя, используя доступные поля, или добавьте новое правило фильтра с помощью кнопки +.
    ![Фильтрация действий пользователя](media/mcas-activity-filter.png)

## <a name="create-activity-policies-in-cloud-app-security"></a>Создание политик действий в Cloud App Security

Отфильтровав действия и определив, какие политики действий вы хотите реализовать, а также что сейчас не соответствует требованиям вашей организации, используйте функцию **Создать политику действия** в меню фильтра, чтобы мгновенно создать настраиваемую политику для пользователя, устройства или клиента.

Чтобы создать политику действия:

1. На любой странице **Журнала действий** примените фильтр (например, приложение, имя пользователя, тип действия и т. д.).
    - Чтобы выполнить фильтрацию по действиям [!INCLUDE [Product short](includes/product-short.md)] , выберите параметр **Active Directory** в фильтре приложения.
    ![Создание политики действия](media/mcas-create-new-policy.png)
1. Нажмите кнопку **Новая политика из поиска**.
1. Добавьте **имя политики**.
    ![Создание политики действия — шаг 2](media/mcas-create-policy.png)
1. Добавьте **описание** политики.
1. Назначьте **серьезность** политики.
1. Выберите **категорию** политики.
1. Выберите или измените фильтры, чтобы создать и назначить политику.
1. Уточните или добавьте фильтры.
1. Сохраните и примените новую политику.

## <a name="next-steps"></a>Дальнейшие действия

Узнайте больше об оценке приоритета для изучения и дополнительных возможностях функций [Microsoft Cloud App Security](/cloud-app-security/).

## <a name="join-the-community"></a>Присоединяйтесь к сообществу!

У вас есть дополнительные вопросы или вы хотите обсудить с другими пользователями особенности использования [!INCLUDE [Product short](includes/product-short.md)] или вопросы, связанные с безопасностью? Присоединяйтесь к [сообществу [!INCLUDE [Product short](includes/product-short.md)]](https://techcommunity.microsoft.com/t5/Azure-Advanced-Threat-Protection/bd-p/AzureAdvancedThreatProtection).