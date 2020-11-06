---
title: Проверка зеркального отображения портов в Microsoft Defender для удостоверений
description: В этой статье описано, как проверить, правильно ли настроено зеркальное отображение портов в Microsoft Defender для удостоверений.
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 10/27/2020
ms.topic: how-to
ms.collection: M365-security-compliance
ms.service: azure-advanced-threat-protection
ms.reviewer: bennyl
ms.suite: ems
ms.openlocfilehash: 7a665a20da3940b3146a007eea6ee75bd35d7930
ms.sourcegitcommit: f434dbff577d9944df18ca7533d026acdab0bb42
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/03/2020
ms.locfileid: "93274091"
---
# <a name="validate-port-mirroring"></a>Проверка зеркального отображения портов

[!INCLUDE [Rebranding notice](includes/rebranding.md)]

Сведения в этой статье относятся только к развертыванию автономного датчика [!INCLUDE [Product long](includes/product-long.md)], а не датчика [!INCLUDE [Product short](includes/product-short.md)].

> [!NOTE]
> Автономные датчики [!INCLUDE [Product short](includes/product-short.md)] не поддерживают сбор записей журнала трассировки событий Windows (ETW), которые предоставляют данные для нескольких обнаружений. Для полного охвата среды рекомендуется развернуть датчик [!INCLUDE [Product short](includes/product-short.md)].

Ниже описана последовательность проверки правильной настройки зеркального отображения портов. Для правильной работы службы "[!INCLUDE [Product short](includes/product-short.md)]" автономный датчик [!INCLUDE [Product short](includes/product-short.md)] должен отслеживать входящий и исходящий трафик контроллера домена. Основным способом получения данных, используемых [!INCLUDE [Product short](includes/product-short.md)], является тщательный анализ пакетов входящего и исходящего сетевого трафика контроллеров домена. Чтобы служба "[!INCLUDE [Product short](includes/product-short.md)]" могла отслеживать сетевой трафик, нужно настроить зеркальное отображение портов. Эта функция копирует трафик из одного порта (исходный порт) в другой порт (конечный порт).

## <a name="validate-port-mirroring-using-net-mon"></a>Проверка зеркального отображения портов с помощью сетевого монитора

1. Установите [Microsoft Network Monitor 3.4](https://www.microsoft.com/download/details.aspx?id=4865) на автономном датчике [!INCLUDE [Product short](includes/product-short.md)], который нужно проверить.

    > [!IMPORTANT]
    > Если вы решили установить Wireshark для проверки зеркального отображения портов, перезапустите службу автономного датчика [!INCLUDE [Product short](includes/product-short.md)] после проверки.

1. Откройте сетевой монитор и создайте новую вкладку записи.

    1. Выберите только сетевой адаптер для записи ( **Capture** ) или сетевой адаптер, подключенный к порту коммутатора, который настроен как конечный порт.

    1. Активируйте неизбирательный режим.

    1. Щелкните **New Capture** (Создать запись).

        ![Создание новой вкладки записи (рисунок)](media/port-mirroring-capture.png)

1. В окне Display Filter (Фильтр отображения) укажите фильтр **KerberosV5 OR LDAP** и нажмите кнопку **Apply** (Применить).

    ![Применение фильтра "KerberosV5 или LDAP" (рисунок)](media/port-mirroring-filter-settings.png)

1. Щелкните **Start** (Начать), чтобы начать сеанс записи. Если входящий и исходящий трафик контроллера домена не отображается, проверьте настройки зеркального отображения портов.

    ![Начало сеанса записи (рисунок)](media/port-mirroring-capture-traffic.png)

    > [!NOTE]
    > Очень важно убедиться, что вы видите входящий и исходящий трафик контроллера домена.

1. Если отслеживается только входящий или исходящий трафик, обратитесь за помощью к специалистам по сетям или виртуализации. Они помогут вам устранить ошибки в настройках зеркального отображения портов.

## <a name="see-also"></a>См. также

- [Настройка пересылки событий](configure-event-forwarding.md)
- [Настройка зеркального отображения портов](configure-port-mirroring.md)
- [Посетите форум по [!INCLUDE [Product short](includes/product-short.md)].](https://aka.ms/MDIcommunity)
