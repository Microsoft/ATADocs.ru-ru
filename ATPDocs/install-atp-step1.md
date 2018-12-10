---
title: Установка Azure Advanced Threat Protection | Документы Майкрософт
description: На первом этапе установки Azure ATP создается экземпляр для развертывания Azure ATP.
keywords: ''
author: mlottner
ms.author: mlottner
manager: mbaldwin
ms.date: 12/02/2018
ms.topic: conceptual
ms.prod: ''
ms.service: azure-advanced-threat-protection
ms.technology: ''
ms.assetid: 15ee7d0b-9a0c-46b9-bc71-98d0b4619ed0
ms.reviewer: itargoet
ms.suite: ems
ms.openlocfilehash: 3fb857308d945fcae04e7dc3d501404a2334382e
ms.sourcegitcommit: f4f2a1b2c674c4dba7a46ece0624f5ea10c4865e
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/02/2018
ms.locfileid: "52744699"
---
*Применяется к: Azure Advanced Threat Protection*


# <a name="creating-your-azure-atp-instance-in-the-azure-atp-portal---step-1"></a>Создание экземпляра Azure ATP на портале Azure ATP. Шаг 1

> [!div class="step-by-step"]
> [Шаг 2 "](install-atp-step2.md)

Здесь приводятся инструкции по созданию экземпляров (прежнее название "рабочая область") Azure ATP и управлению ими. Сведения об архитектуре Azure ATP см. в статье [Архитектура Azure ATP](atp-architecture.md).

В Azure ATP в вашем распоряжении будет один экземпляр для управления несколькими лесами из одного места. 

> [!NOTE]
> Сейчас центры обработки данных Azure ATP развертываются в Европе, Северной Америке и Центральной Америке, в странах Карибского бассейна и Азии. Экземпляр создается автоматически в центре обработки данных, географически ближайшем к AAD. После создания экземпляры Azure ATP перемещать нельзя. 

## <a name="step-1-enter-the-azure-atp-portal"></a>Шаг 1. Вход на портал Azure ATP

После проверки сети на соответствие требованиям датчика можно приступить к созданию экземпляра Azure ATP.

> [!NOTE]
>Для доступа к порталу Azure ATP требуются права глобального администратора или администратора безопасности на этом клиенте.


1.  Войдите на [портал Azure ATP](https://portal.atp.azure.com).

2.  Войдите в систему по учетной записи пользователя Azure Active Directory.

## <a name="step-2-create-your-instance"></a>Шаг 2. Создание экземпляра

1. Нажмите кнопку **Создать экземпляр**. 

    ![Создание экземпляра Azure ATP](media/create-instance.png)

2. Создаваемый экземпляр Azure ATP автоматически получает имя исходного домена AAD и выделяется в центре обработки данных, ближайшем к вашему клиенту AAD. 

    ![Созданный экземпляр Azure](media/instance-created.png)

> [!NOTE]
 > Для входа в Azure ATP необходимо использовать учетную запись пользователя, которому была назначена роль Azure ATP с правами доступа к порталу Azure ATP. Дополнительные сведения об управлении доступом на основе ролей (RBAC) в Azure ATP см. в статье о [группах ролей Azure ATP](atp-role-groups.md).
 
3. Нажмите кнопку **Конфигурация**, **Управление группами ролей** и перейдите по ссылке [Центр администрирования Azure AD](https://docs.microsoft.com/azure/active-directory/active-directory-assign-admin-roles-azure-portal), чтобы приступить к управлению группами ролей. .

    ![Управление группами ролей](media/creation-manage-role-groups.png)

- Хранение данных — ранее удаленные экземпляры Azure ATP не отображаются в пользовательском интерфейсе. Дополнительные сведения о хранении данных в Azure ATP см. в разделе [Безопасность и конфиденциальность данных в Azure ATP](atp-privacy-compliance.md).


>[!div class="step-by-step"]
[« Перед установкой](atp-prerequisites.md)
[Шаг 2 »](install-atp-step2.md)



## <a name="see-also"></a>См. также
- [Средство изменения размера Azure ATP](http://aka.ms/aatpsizingtool)
- [Настройка сбора данных о событиях](configure-event-collection.md)
- [Предварительные требования к Azure ATP](atp-prerequisites.md)
- [Загляните на форум Azure ATP!](https://aka.ms/azureatpcommunity)
