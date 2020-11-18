---
title: Мониторинг работоспособности и событий системы идентификации в защитнике Майкрософт
description: Используйте центр работоспособности для проверки работы защитника Майкрософт для службы идентификации и оповещения о потенциальных проблемах и просмотра системных событий в средстве просмотра событий.
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
ms.openlocfilehash: 5bf828278e0223aaaf52b41932b2612c7225dd7f
ms.sourcegitcommit: e2227c0b0e5aaa5163dc56d4131ca82f8dca8fb0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/18/2020
ms.locfileid: "94847944"
---
# <a name="work-with-product-long-health-and-events"></a>Работа с [!INCLUDE [Product long](includes/product-long.md)] работоспособностью и событиями

## <a name="product-long-health-center"></a>[!INCLUDE [Product long](includes/product-long.md)] центр работоспособности

[!INCLUDE [Product long](includes/product-long.md)]Центр работоспособности позволяет вам понять, как выполняется [!INCLUDE [Product short](includes/product-short.md)] экземпляр, и оповещать вас при возникновении проблем.

## <a name="working-with-the-product-short-health-center"></a>Работа с [!INCLUDE [Product short](includes/product-short.md)] центром работоспособности

[!INCLUDE [Product short](includes/product-short.md)]Центр работоспособности позволяет выяснить, что возникла проблема, вызывая предупреждение (красную точку) над значком центра работоспособности на панели навигации.

![[! ВКЛЮЧИТЬ [продукт Short] (включая/Product-Short. md)] панель инструментов Red Dot центра работоспособности](media/health-bar.png)

### <a name="managing-product-short-health"></a>Управление [!INCLUDE [Product short](includes/product-short.md)] работоспособностью

Чтобы проверить общую работоспособность вашего [!INCLUDE [Product short](includes/product-short.md)] экземпляра, выберите **работоспособность** ![ [! ВКЛЮЧИТЬ [продукт Short] (включая/Product-Short. md)] значок центра работоспособности](media/red-dot.png)

- Всеми открытыми проблемами можно управлять. Для этого щелкните многоточие в углу предупреждения и выберите нужный вариант: **Закрыть**, **Заблокировать**.

- **Открыть**: в этом списке отображаются все новые подозрительные действия.

- **Закрыть**: используется для отслеживания подозрительных действий, которые были выявлены и изучены и возможные последствия которых минимизированы.

    > [!NOTE]
    > [!INCLUDE [Product short](includes/product-short.md)] может повторно открыть закрытое действие, если одно и то же действие будет обнаружено снова в течение короткого периода времени.

- **Заблокировать**: блокировка действия означает, что в настоящее время оно игнорируется и что оповещение о нем выводится снова, только если оно обнаружено повторно. Если такое же оповещение [!INCLUDE [Product short](includes/product-short.md)] не открывается повторно, Но если оповещение отсутствует в течение семи дней, а затем снова возникает, оно будет выведено повторно.

- **Открыть повторно**: вы можете повторно открыть закрытое или заблокированное оповещение, чтобы оно снова отображалось на временной шкале как **открытое**.

- **Удалить**: на временной шкале оповещений безопасности можно удалить проблему с работоспособностью. Если вы удаляете оповещение, оно будет удалено из экземпляра. Восстановить его невозможно. Щелкнув "Удалить", можно удалить все оповещения системы безопасности одного типа.

![[! ВКЛЮЧИТЬ [продукт Short] (включая/Product-Short. md)] изображение проблем центра работоспособности](media/health-issue.png)

## <a name="see-also"></a>См. также:

- [Обработка подозрительных действий](working-with-suspicious-activities.md)
- [Посетите форум по [!INCLUDE [Product short](includes/product-short.md)].](https://aka.ms/MDIcommunity)
