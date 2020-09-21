---
title: Изменение конфигурации Azure Advanced Threat protection — пароль для подключения к домену
description: Процедура изменения пароля для подключения к домену на автономном датчике Azure ATP.
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 02/19/2020
ms.topic: how-to
ms.collection: M365-security-compliance
ms.service: azure-advanced-threat-protection
ms.assetid: e7f065fa-1ad1-4e87-bd80-99cc695efbf5
ms.reviewer: itargoet
ms.suite: ems
ms.openlocfilehash: 3d35651f0741caa6189ae8ef79e14e8b0db78eff
ms.sourcegitcommit: 0c356b0860ae8663254e0cf6f04001bcc91ce207
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/21/2020
ms.locfileid: "90828588"
---
# <a name="change-azure-atp-portal-configuration---domain-connectivity-password"></a>Изменение конфигурации портала Azure ATP с использованием пароля для подключения к домену

## <a name="change-the-domain-connectivity-password"></a>Изменение пароля для подключения к домену

Если необходимо изменить пароль для подключения к домену, указывайте правильный пароль. В противном случае служба датчика Azure ATP будет остановлена для всех развернутых датчиков.

Если вы считаете, что это произошло, проверьте файл Microsoft. втрое. sensor-Errors. log на наличие следующих ошибок: `The supplied credential is invalid.`

Чтобы изменить пароль для подключения к домену на портале Azure ATP, выполните описанную ниже процедуру:

> [!NOTE]
> Это имя пользователя и пароль из локального развертывания Active Directory, а не из Azure AD.

1. Откройте портал Azure ATP, воспользовавшись его URL-адресом.

1. На панели инструментов щелкните значок параметров и выберите пункт **Конфигурация**.

    ![Значок параметров конфигурации Azure ATP](media/atp-config-menu.png)

1. Выберите **Directory Services** (Службы каталогов).

    ![Изображение: изменение пароля автономного датчика Azure ATP](media/directory-services.png)

1. В разделе **Password** (Пароль) измените пароль.

    > [!NOTE]
    > Введите имя пользователя и пароль для Active Directory, а не для Azure Active Directory.

1. Выберите команду **Сохранить**.

1. На портале Azure ATP в разделе **Конфигурация** откройте страницу **Датчик** и проверьте состояние датчиков.

## <a name="see-also"></a>См. также

- [Интеграция Azure ATP с ATP в Microsoft Defender](integrate-msde.md)
- [Загляните на форум Azure ATP!](https://aka.ms/azureatpcommunity)
