---
title: Установка защитника Майкрософт для интеграции удостоверений VPN
description: Собирать сведения об учетных данных для защитника Майкрософт для идентификации путем интеграции VPN.
ms.date: 10/26/2020
ms.topic: how-to
ms.openlocfilehash: e7c406a198eb78c98c795ba43d9b4076610540c7
ms.sourcegitcommit: cdb7ae4580851e25aae24d07e7d66a750aa54405
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/03/2020
ms.locfileid: "96543966"
---
# <a name="integrate-vpn"></a>Интеграция VPN

[!INCLUDE [Product long](includes/product-long.md)] может получать данные учета из решений VPN. Если настроить эту функцию, страница профиля пользователя будет включать сведения из VPN-подключений, в том числе IP-адреса и расположения, из которых осуществлялись подключения. Дополнительные данные о действиях пользователей помогут в процессе анализа, а также при обнаружении неправильных VPN-подключений. Вызов для разрешения внешних IP-адресов в расположении является анонимным. Личный идентификатор в этом вызове не отправляется.

[!INCLUDE [Product short](includes/product-short.md)] интегрируется с решением VPN путем прослушивания событий учета RADIUS, перенаправленных на [!INCLUDE [Product short](includes/product-short.md)] датчики. Этот механизм основан на стандартном учете RADIUS ([RFC 2866](https://tools.ietf.org/html/rfc2866)). Поддерживаются следующие поставщики VPN.

- Microsoft
- F5
- Check Point
- Cisco ASA

## <a name="prerequisites"></a>Предварительные условия

Чтобы включить интеграцию VPN, задайте следующие параметры:

- Откройте порт UDP 1813 на [!INCLUDE [Product short](includes/product-short.md)] датчиках и (или) [!INCLUDE [Product short](includes/product-short.md)] автономных датчиках.

> [!NOTE]
> При включении **учета RADIUS** [!INCLUDE [Product short](includes/product-short.md)] датчик включит предварительно подготовленную политику брандмауэра Windows, называемую **[!INCLUDE [Product long](includes/product-long.md)] датчиком** , чтобы разрешить входящий учет RADIUS через порт UDP 1813.

В примере ниже описан процесс настройки VPN с использованием сервера маршрутизации и удаленного доступа Майкрософт (RRAS).

Если вы используете стороннее решение VPN, инструкции по включению учета RADIUS см. в соответствующей документации.

## <a name="configure-radius-accounting-on-the-vpn-system"></a>Настройка учета RADIUS в системе VPN

Выполните следующие действия на RRAS-сервере.

1. Откройте консоль маршрутизации и удаленного доступа.
1. Щелкните правой кнопкой мыши имя сервера и выберите **Свойства**.
1. На вкладке **Безопасность** в разделе **Поставщик учета**  выберите **Учет RADIUS** и щелкните **Настроить**.

    ![Настройка RADIUS](media/radius-setup.png)

1. В окне **Добавление сервера RADIUS** введите **имя сервера** для ближайшего [!INCLUDE [Product short](includes/product-short.md)] датчика (с сетевым подключением). Для обеспечения высокой доступности можно добавить дополнительные [!INCLUDE [Product short](includes/product-short.md)] датчики в качестве серверов RADIUS. В поле **порт** должно быть указано значение по умолчанию: 1813. Щелкните **Изменить** и введите новую строку общего секрета из букв и цифр. Запишите новую строку общего секрета, так как ее потребуется заполнить позже во время [!INCLUDE [Product short](includes/product-short.md)] настройки. Установите флажок **Отправлять сообщения о включении и отключении учета RADIUS** и нажмите кнопку **ОК** во всех открывшихся диалоговых окнах.

    ![Настройка VPN](media/vpn-set-accounting.png)

### <a name="configure-vpn-in-product-short"></a>Настройка VPN в [!INCLUDE [Product short](includes/product-short.md)]

[!INCLUDE [Product short](includes/product-short.md)] собирает данные VPN, которые помогают профилировать местоположения, с которых компьютеры подключаются к сети и могут обнаруживать подозрительные VPN-подключения.

Чтобы настроить данные VPN в, [!INCLUDE [Product short](includes/product-short.md)] выполните следующие действия.

1. На [!INCLUDE [Product short](includes/product-short.md)] портале щелкните конфигурацию шестеренки, а затем — **VPN**.
1. Включите **Учет Radius** и введите **общий секрет**, настроенный ранее на VPN-сервере RRAS. Затем нажмите кнопку **Сохранить**.

    ![Настройка [! ВКЛЮЧИТЬ [продукт Short] (включая/Product-Short. md)] VPN](media/vpn-radius.png)

После включения этого [!INCLUDE [Product short](includes/product-short.md)] действия все датчики прослушивают порт 1813 для событий учета RADIUS, и настройка VPN будет завершена.

 После того как [!INCLUDE [Product short](includes/product-short.md)] датчик получит события VPN и отправит их в [!INCLUDE [Product short](includes/product-short.md)] облачную службу для обработки, профиль сущности будет указывать на различные доступные расположения VPN, а действия в профиле будут указывать на расположения.

## <a name="see-also"></a>См. также

- [Средство определения размера [!INCLUDE [Product short](includes/product-short.md)]](https://aka.ms/aatpsizingtool)
- [Настройка сбора данных о событиях](configure-event-collection.md)
- [Предварительные требования для работы с [!INCLUDE [Product short](includes/product-short.md)]](prerequisites.md)
- [Посетите форум по [!INCLUDE [Product short](includes/product-short.md)].](https://aka.ms/MDIcommunity)
