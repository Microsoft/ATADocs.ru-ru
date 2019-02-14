---
title: Изменение конфигурации Azure Advanced Threat Protection с использованием пароля для подключения к домену | Документы Майкрософт
description: Процедура изменения пароля для подключения к домену на автономном датчике Azure ATP.
keywords: ''
author: mlottner
ms.author: mlottner
manager: barbkess
ms.date: 12/02/2018
ms.topic: conceptual
ms.prod: ''
ms.service: azure-advanced-threat-protection
ms.technology: ''
ms.assetid: e7f065fa-1ad1-4e87-bd80-99cc695efbf5
ms.reviewer: itargoet
ms.suite: ems
ms.openlocfilehash: bc8f03ae87532937e4337776824d617e83f6a7d4
ms.sourcegitcommit: 78748bfd75ae68230d72ad11010ead37d96b0c58
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/12/2019
ms.locfileid: "56076255"
---
# <a name="change-azure-atp-portal-configuration---domain-connectivity-password"></a>Изменение конфигурации портала Azure ATP с использованием пароля для подключения к домену



## <a name="change-the-domain-connectivity-password"></a>Изменение пароля для подключения к домену
Если необходимо изменить пароль для подключения к домену, указывайте правильный пароль. В противном случае служба датчика Azure ATP будет остановлена для всех развернутых датчиков.

В таком случае откройте на автономном датчике Azure ATP файл Microsoft.Tri.sensor-Errors.log и найдите в нем следующие ошибки: `The supplied credential is invalid.`.

Чтобы изменить пароль для подключения к домену на портале Azure ATP, выполните описанную ниже процедуру:

> [!NOTE]
> Это имя пользователя и пароль из локального развертывания Active Directory, а не из Azure AD.

1. Откройте портал Azure ATP, воспользовавшись его URL-адресом.

2. На панели инструментов щелкните значок параметров и выберите пункт **Конфигурация**.

   ![Значок параметров конфигурации Azure ATP](media/atp-config-menu.png)

3. Выберите **Directory Services** (Службы каталогов).

   ![Изображение: изменение пароля автономного датчика Azure ATP](media/directory-services.png)

4. В разделе **Password** (Пароль) измените пароль.

   > [!NOTE]
   > Введите имя пользователя и пароль для Active Directory, а не для Azure Active Directory.

5. Нажмите кнопку **Сохранить**.

6. После изменения пароля вручную проверьте, что служба автономного датчика Azure ATP запущена на серверах автономного датчика Azure ATP.

7. На портале Azure ATP в разделе **Конфигурация** откройте страницу **Датчик** и проверьте состояние датчиков.

## <a name="see-also"></a>См. также

- [Интеграция с ATP в Защитнике Windows](integrate-wd-atp.md)
- [Загляните на форум Azure ATP!](https://aka.ms/azureatpcommunity)