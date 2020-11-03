---
title: Наблюдение за контроллерами домена и установленными датчиками, установленными на контроллерах домена, с помощью защитника Майкрософт для идентификации
description: Описывается мониторинг защитника Майкрософт для датчиков удостоверений и покрытия датчика с помощью защитника для идентификации.
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 10/27/2020
ms.topic: how-to
ms.collection: M365-security-compliance
ms.service: azure-advanced-threat-protection
ms.reviewer: itargoet
ms.suite: ems
ms.openlocfilehash: af05ee5bbd064e31b231ad36374b4c069d8f7cfc
ms.sourcegitcommit: f434dbff577d9944df18ca7533d026acdab0bb42
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/03/2020
ms.locfileid: "93275417"
---
# <a name="monitoring-your-domain-controller-coverage"></a>Мониторинг покрытия контроллеров домена

[!INCLUDE [Rebranding notice](includes/rebranding.md)]

После [!INCLUDE [Product long](includes/product-long.md)] установки и настройки первого датчика на любом контроллере домена в сети [!INCLUDE [Product short](includes/product-short.md)] начнется мониторинг среды для контроллеров домена.

После [!INCLUDE [Product short](includes/product-short.md)] установки и настройки датчика на контроллере домена в сети датчик обменивается данными со [!INCLUDE [Product short](includes/product-short.md)] службой на постоянной основе, отправляя состояние датчика, сведения о работоспособности и версии, а также собрал Active Directory события и изменения.

## <a name="domain-controller-status"></a>Состояние контроллера домена

[!INCLUDE [Product short](includes/product-short.md)] постоянно отслеживает среду для неотслеживаемых контроллеров домена, появившихся в вашей среде, и сообщает о них, чтобы помочь вам в управлении полным охватом среды.

1. Чтобы проверить состояние обнаруженных отслеживаемых и неотслеживаемых контроллеров домена и их состояния, перейдите в область **конфигурации** на [!INCLUDE [Product short](includes/product-short.md)] портале и в разделе " **система** " выберите **датчики**.

    ![[! ВКЛЮЧИТЬ [продукт Short] (включая/Product-Short. md)] мониторинг состояния датчика](media/sensors-status-monitoring.png)

1. Текущие отслеживаемые и неотслеживаемые контроллеры домена отображаются в верхней части экрана. Для загрузки подробных сведений о состоянии мониторинга контроллеров домена выберите **Загрузить сведения**.

В загруженном Excel-файле покрытия контроллеров домена содержатся следующие сведения обо всех контроллерах домена в вашей организации:

|Заголовок|Описание|
|----|----|
|Hostname (Имя узла)|Имя компьютера|
|Доменное имя|Доменное имя|
|Monitored|[!INCLUDE [Product short](includes/product-short.md)] состояние мониторинга|
|Тип датчика|[!INCLUDE [Product short](includes/product-short.md)] датчик или [!INCLUDE [Product short](includes/product-short.md)] Автономный датчик|
|Подразделение|Расположение в Active Directory |
|Версия операционной системы| Обнаруженная версия операционной системы|
|IP-адрес|Обнаруженный IP-адрес|

## <a name="search-domain-controllers"></a>Поиск контроллеров домена

Управление парком датчиков и контроллеров домена может быть непростой задачей. Для упрощения поиска и определения контроллеров домена можно выполнять поиск с помощью функции поиска в [!INCLUDE [Product short](includes/product-short.md)] списке датчиков.

1. Для поиска контроллеров домена перейдите в область **настройки** [!INCLUDE [Product short](includes/product-short.md)] портала и в разделе **система** выберите **датчики**.
1. Выберите параметр фильтра в столбце **контроллеров домена** в списке таблиц контроллеров домена.
1. Введите имя для поиска. Сейчас подстановочные знаки не поддерживаются в поле поиска.

    ![[! INCLUDE [продукт Short] (включает/Product-Short. md)] Поиск контроллера домена](media/search-sensor.png)

> [!NOTE]
> [!INCLUDE [Product short](includes/product-short.md)] страницы конфигурации портала могут быть изменены [!INCLUDE [Product short](includes/product-short.md)] только администраторами.

## <a name="see-also"></a>См. также:

- [[!INCLUDE [Product short](includes/product-short.md)] AHA](architecture.md)
- [Настройка [!INCLUDE [Product short](includes/product-short.md)] датчиков](install-step5.md)
- [Поддержка нескольких лесов](multi-forest.md)
- [Посетите [!INCLUDE [Product short](includes/product-short.md)] форум!](https://aka.ms/MDIcommunity)
