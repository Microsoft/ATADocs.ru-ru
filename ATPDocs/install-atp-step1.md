---
title: Установка Azure Advanced Threat Protection | Документы Майкрософт
description: На первом этапе установки Azure ATP создается экземпляр для развертывания Azure ATP.
keywords: ''
author: mlottner
ms.author: mlottner
manager: mbaldwin
ms.date: 10/4/2018
ms.topic: conceptual
ms.prod: ''
ms.service: azure-advanced-threat-protection
ms.technology: ''
ms.assetid: 15ee7d0b-9a0c-46b9-bc71-98d0b4619ed0
ms.reviewer: itargoet
ms.suite: ems
ms.openlocfilehash: 7a7bdd045a0964c4ed4ccc4ebe2315b3c3465be2
ms.sourcegitcommit: c10a1c5d1e5408b5473a31485346915908688680
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/29/2018
ms.locfileid: "50208108"
---
*Применяется к: Azure Advanced Threat Protection*


# <a name="creating-your-azure-atp-instance-in-the-portal---step-1"></a>Создание экземпляра Azure ATP на портале. Шаг 1

> [!div class="step-by-step"]
> [Шаг 2 "](install-atp-step2.md)

Здесь приводятся инструкции по созданию экземпляра или рабочей области Azure ATP и управлению ими. Сведения об архитектуре Azure ATP см. в статье [Архитектура Azure ATP](atp-architecture.md).

В Azure ATP в вашем распоряжении будет один экземпляр или одна рабочая область для управления несколькими лесами из одного места. 

> [!NOTE]
> Сейчас центры обработки данных Azure ATP развертываются в Европе, Северной Америке и Центральной Америке, в странах Карибского бассейна и Азии.

## <a name="step-1-enter-the-azure-atp-portal"></a>Шаг 1. Вход на портал Azure ATP

После проверки сети на соответствие требованиям датчика можно приступить к созданию рабочей области Azure ATP.

> [!NOTE]
>Для доступа к порталу управления требуются права глобального администратора или администратора безопасности на этом клиенте.


1.  Войдите на [портал Azure ATP](https://portal.atp.azure.com).

2.  Войдите в систему по учетной записи пользователя Azure Active Directory.

## <a name="step-2-create-your-workspace"></a>Шаг 2. Создание рабочей области

1. Щелкните **Создать рабочую область**.

2. В диалоговом окне **Создание рабочей области** задайте имя для рабочей области, а затем выберите значение для параметра **Географическое положение** для центра обработки данных. По умолчанию создается **основная** рабочая область. 
 > [!NOTE]
 > Выбранное географическое расположение изменить невозможно.
    ![Рабочая область Azure ATP](media/create-workspace.png)

3. Щелкните ссылку **Управление ролями пользователей ATP Azure**, чтобы сразу же перейти в [Центр администрирования Azure Active Directory](https://docs.microsoft.com/azure/active-directory/active-directory-assign-admin-roles-azure-portal) и управлять группами ролей.

 > [!NOTE]
 > Для успешного входа в Azure ATP необходимо использовать учетную запись пользователя, которому была назначена соответствующая роль Azure ATP с правами доступа к порталу Azure ATP. Дополнительные сведения об управлении доступом на основе ролей (RBAC) в Azure ATP см. в статье о [группах ролей Azure ATP](atp-role-groups.md).

4. Щелкните имя рабочей области для доступа к порталу Azure ATP.

    ![Рабочие области Azure ATP](media/atp-workspaces.png)

- Изменять можно только основную рабочую область. Если нужно удалить основную рабочую область, сначала следует отключить возможности интеграции. После этого она будет доступна для удаления.

- Хранение данных — ранее удаленные рабочие области не отображаются в пользовательском интерфейсе. Дополнительные сведения о хранении данных в Azure ATP см. в разделе [Безопасность и конфиденциальность данных в Azure ATP](atp-privacy-compliance.md).

> [!div class="step-by-step"]
> [« Перед установкой](atp-prerequisites.md)
> [Шаг 2 »](install-atp-step2.md)



## <a name="see-also"></a>См. также
- [Средство изменения размера Azure ATP](http://aka.ms/aatpsizingtool)
- [Настройка сбора данных о событиях](configure-event-collection.md)
- [Предварительные требования к Azure ATP](atp-prerequisites.md)
- [Загляните на форум Azure ATP!](https://aka.ms/azureatpcommunity)
