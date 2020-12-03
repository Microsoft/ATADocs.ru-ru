---
title: Изменение защитника Майкрософт для настройки удостоверения — пароль для подключения к домену
description: Описывает, как изменить пароль для подключения к домену в защитнике Майкрософт для изолированного датчика идентификации.
ms.date: 10/26/2020
ms.topic: how-to
ms.openlocfilehash: 294786515c45136be77447b9ad1e9ddf5e2e5e95
ms.sourcegitcommit: cdb7ae4580851e25aae24d07e7d66a750aa54405
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/03/2020
ms.locfileid: "96544510"
---
# <a name="change-product-long-portal-configuration---domain-connectivity-password"></a>Изменение [!INCLUDE [Product long](includes/product-long.md)] конфигурации портала — пароль для подключения к домену

## <a name="change-the-domain-connectivity-password"></a>Изменение пароля для подключения к домену

Если необходимо изменить пароль для подключения к домену, указывайте правильный пароль. Если это не так, то [!INCLUDE [Product long](includes/product-long.md)] Служба датчика останавливается для всех развернутых датчиков.

Если вы считаете, что это произошло, проверьте файл Microsoft. втрое. sensor-Errors. log на наличие следующих ошибок: `The supplied credential is invalid.`

Выполните следующую процедуру, чтобы обновить пароль для подключения к домену на [!INCLUDE [Product short](includes/product-short.md)] портале:

> [!NOTE]
> Это имя пользователя и пароль из локального развертывания Active Directory, а не из Azure AD.

1. Откройте [!INCLUDE [Product short](includes/product-short.md)] портал, перейдя по URL-адресу портала.

1. На панели инструментов щелкните значок параметров и выберите пункт **Конфигурация**.

    ![[!INCLUDE [Product short](includes/product-short.md)]: значок параметров конфигурации](media/config-menu.png)

1. Выберите **Directory Services** (Службы каталогов).

    ![[! ВКЛЮЧИТЬ [продукт Short] (включая/Product-Short. md)] изображение для изменения пароля автономного датчика](media/directory-services.png)

1. В разделе **Password** (Пароль) измените пароль.

    > [!NOTE]
    > Введите имя пользователя и пароль для Active Directory, а не для Azure Active Directory.

1. Выберите команду **Сохранить**.

1. На портале [!INCLUDE [Product short](includes/product-short.md)] выберите пункт **Конфигурация**.
1. В разделе **система** выберите страницу **датчиков** и проверьте состояние датчиков.

## <a name="see-also"></a>См. также:

- [Интеграция с Microsoft Defender для конечной точки](integrate-mde.md)
- [Посетите форум по [!INCLUDE [Product short](includes/product-short.md)].](https://aka.ms/MDIcommunity)
