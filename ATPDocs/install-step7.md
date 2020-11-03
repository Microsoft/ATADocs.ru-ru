---
title: Исключения и учетные записи honeytoken в защитнике Майкрософт для настройки обнаружения удостоверений
description: Настройка учетных записей пользователей Honeytoken и исключений из обнаружения.
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
ms.openlocfilehash: 68ed20a243a307992b2d11c633728bf34abf6302
ms.sourcegitcommit: f434dbff577d9944df18ca7533d026acdab0bb42
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/03/2020
ms.locfileid: "93277052"
---
# <a name="configure-detection-exclusions-and-honeytoken-accounts"></a>Настройка учетных записей Honeytoken и исключений из обнаружения

[!INCLUDE [Rebranding notice](includes/rebranding.md)]

[!INCLUDE [Product long](includes/product-long.md)] разрешает исключение конкретных IP-адресов или пользователей из нескольких обнаружений.

Например, **исключением исследования DNS** является сканер безопасности, использующий DNS в качестве механизма сканирования. Исключение помогает [!INCLUDE [Product short](includes/product-short.md)] игнорировать такие сканеры.

[!INCLUDE [Product short](includes/product-short.md)] также позволяет настроить учетные записи honeytoken, используемые в качестве ловушек для вредоносных субъектов. Любая проверка подлинности, связанная с этими учетными записями honeytoken (обычно неактивна), запускает оповещение.

Для настройки выполните следующее:

1. На [!INCLUDE [Product short](includes/product-short.md)] портале щелкните значок параметров и выберите **Конфигурация**.

    ![[! ВКЛЮЧИТЬ [продукт Short] (включая/Product-Short. md)] параметры конфигурации](media/config-menu.png)

1. В разделе **Обнаружение** выберите пункт **Теги сущности**.

1. В разделе **Учетные записи Honeytoken** введите имя учетной записи Honeytoken и щелкните значок **+** . Поле "Учетные записи Honeytoken" поддерживает поиск, и в нем автоматически отображаются сущности, имеющиеся в вашей сети. Нажмите кнопку **Сохранить**.

    ![Honeytoken](media/honeytoken-sensitive.png)

1. Щелкните **Исключения**. Для каждого типа угрозы введите учетную запись пользователя или IP-адрес, которые следует исключить при обнаружении.
1. Щелкните знак *плюс*. Поле **Добавить сущность** (пользователя или компьютер) поддерживает поиск и автоматически заполняется сущностями из вашей сети. Дополнительные сведения см. в статье [Исключение сущностей из результатов обнаружения](excluding-entities-from-detections.md) и в [руководстве по оповещениям системы безопасности](suspicious-activity-guide.md).

    ![Исключение сущностей из результатов обнаружения](media/exclusions.png)

1. Нажмите кнопку **Сохранить**.

Поздравляем! вы успешно развернули [!INCLUDE [Product long](includes/product-long.md)] !

Просмотрите временную шкалу атак, чтобы увидеть оповещения безопасности об обнаружении подозрительных действий, найти пользователей или компьютеры и изучить профили.

[!INCLUDE [Product short](includes/product-short.md)] сканирование начинается немедленно. Некоторые обнаружения, например [подозрительные дополнения к конфиденциальным группам](domain-dominance-alerts.md#suspicious-additions-to-sensitive-groups-external-id-2024), нуждаются в обучающем периоде и недоступны сразу после [!INCLUDE [Product short](includes/product-short.md)] развертывания. Период обучения для каждого оповещения содержится в подробном [пошаговом руководству по безопасности](suspicious-activity-guide.md).

## <a name="see-also"></a>См. также:

- [[!INCLUDE [Product short](includes/product-short.md)] средство изменения размера](https://aka.ms/aatpsizingtool)
- [Настройка сбора данных о событиях](configure-event-collection.md)
- [[!INCLUDE [Product short](includes/product-short.md)] требований](prerequisites.md)
- [Посетите [!INCLUDE [Product short](includes/product-short.md)] форум!](https://aka.ms/MDIcommunity)
