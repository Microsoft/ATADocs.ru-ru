---
title: Изменение конфигурации Azure Advanced Threat Protection с использованием пароля для подключения к домену | Документы Майкрософт
description: Процедура изменения пароля для подключения к домену на автономном датчике Azure ATP.
keywords: ''
author: mlottner
ms.author: mlottner
manager: rkarlin
ms.date: 12/02/2018
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.service: azure-advanced-threat-protection
ms.assetid: e7f065fa-1ad1-4e87-bd80-99cc695efbf5
ms.reviewer: itargoet
ms.suite: ems
ms.openlocfilehash: d8c0a38b1a02f8d9eee1f9955cf2c950c501be15
ms.sourcegitcommit: 6dd002b5a34f230aaada55a6f6178c2f9e1584d9
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/05/2019
ms.locfileid: "65196578"
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
