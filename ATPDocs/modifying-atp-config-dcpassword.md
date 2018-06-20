---
title: Изменение конфигурации Azure Advanced Threat Protection с использованием пароля для подключения к домену | Документы Майкрософт
description: Процедура изменения пароля для подключения к домену на автономном датчике Azure ATP.
keywords: ''
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 2/14/2018
ms.topic: article
ms.prod: ''
ms.service: azure-advanced-threat-protection
ms.technology: ''
ms.assetid: e7f065fa-1ad1-4e87-bd80-99cc695efbf5
ms.reviewer: itargoet
ms.suite: ems
ms.openlocfilehash: 369f00b1b33fe509850bc331b0d5b45ae161f91c
ms.sourcegitcommit: 03e959b7ce4b6df421297e1872e028793c967302
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/21/2018
ms.locfileid: "29444830"
---
*Применяется к: Azure Advanced Threat Protection*



# <a name="change-azure-atp-workspace-portal-configuration---domain-connectivity-password"></a>Изменение конфигурации портала рабочей области Azure ATP с использованием пароля для подключения к домену



## <a name="change-the-domain-connectivity-password"></a>Изменение пароля для подключения к домену
Если необходимо изменить пароль для подключения к домену, указывайте правильный пароль. В противном случае служба датчика Azure ATP будет остановлена для всех развернутых датчиков.

В таком случае откройте на автономном датчике Azure ATP файл Microsoft.Tri.sensor-Errors.log и найдите в нем следующие ошибки: `The supplied credential is invalid.`.

Чтобы изменить пароль для подключения к домену на портале рабочей области Azure ATP, выполните описанную ниже процедуру.

> [!NOTE]
> Это имя пользователя и пароль из локального развертывания Active Directory, а не из Azure AD.

1.  Откройте портал рабочей области Azure ATP, воспользовавшись URL-адресом рабочей области.

2.  На панели инструментов щелкните значок параметров и выберите пункт **Конфигурация**.

    ![Значок параметров конфигурации Azure ATP](media/atp-config-menu.png)

3.  Выберите **Directory Services** (Службы каталогов).

    ![Изображение: изменение пароля автономного датчика Azure ATP](media/directory-services.png)

4.  В разделе **Password** (Пароль) измените пароль.

 > [!NOTE]
 > Введите имя пользователя и пароль для Active Directory, а не для Azure Active Directory.

5.  Нажмите кнопку **Сохранить**.

6.  После изменения пароля вручную проверьте, что служба автономного датчика Azure ATP запущена на серверах автономного датчика Azure ATP.

7. На портале рабочей области в разделе **Конфигурация** откройте страницу **Датчик** и проверьте состояние датчиков.

## <a name="see-also"></a>См. также

- [Интеграция с ATP в Защитнике Windows](integrate-wd-atp.md)
- [Обязательно ознакомьтесь с форумом ATP](https://aka.ms/azureatpcommunity)