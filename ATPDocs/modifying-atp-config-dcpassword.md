---
title: Изменение конфигурации Расширенной защиты от угроз Azure с использованием пароля для подключения к домену
description: Процедура изменения пароля для подключения к домену на автономном датчике Azure ATP.
keywords: ''
author: shsagir
ms.author: shsagir
manager: rkarlin
ms.date: 02/19/2020
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.service: azure-advanced-threat-protection
ms.assetid: e7f065fa-1ad1-4e87-bd80-99cc695efbf5
ms.reviewer: itargoet
ms.suite: ems
ms.openlocfilehash: 77ec242769d15eb3681f9e511709a0e6953878e8
ms.sourcegitcommit: bf5f58317121f1fb0fffc83d8b419cdd7ef27d9a
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/05/2020
ms.locfileid: "80669516"
---
# <a name="change-azure-atp-portal-configuration---domain-connectivity-password"></a>Изменение конфигурации портала Azure ATP с использованием пароля для подключения к домену

## <a name="change-the-domain-connectivity-password"></a>Изменение пароля для подключения к домену

Если необходимо изменить пароль для подключения к домену, указывайте правильный пароль. В противном случае служба датчика Azure ATP будет остановлена для всех развернутых датчиков.

В таком случае посмотрите, есть ли в файле Microsoft.Tri.sensor-Errors.log следующие ошибки: `The supplied credential is invalid.`

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

1. Нажмите кнопку **Сохранить**.

1. На портале Azure ATP в разделе **Конфигурация** откройте страницу **Датчик** и проверьте состояние датчиков.

## <a name="see-also"></a>См. также

- [Интеграция Azure ATP с ATP в Microsoft Defender](integrate-wd-atp.md)
- [Загляните на форум Azure ATP!](https://aka.ms/azureatpcommunity)
