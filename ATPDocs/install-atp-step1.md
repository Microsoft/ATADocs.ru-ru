---
title: Краткое руководство. Создание экземпляра Azure ATP
description: Краткое руководство по созданию экземпляра для развертывания Azure ATP — первого шага установки Azure ATP.
keywords: ''
author: shsagir
ms.author: shsagir
ms.date: 10/31/2019
ms.topic: quickstart
ms.collection: M365-security-compliance
ms.service: azure-advanced-threat-protection
ms.reviewer: itargoet
ms.suite: ems
ms.openlocfilehash: 22e37d606ca5f6057408c59a7384082737fa0029
ms.sourcegitcommit: 63be53de5b84eabdeb8c006438dab45bd35a4ab7
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/21/2020
ms.locfileid: "81436130"
---
# <a name="quickstart-create-your-azure-atp-instance"></a>Краткое руководство. создание экземпляра Azure ATP;

В этом кратком руководстве вы создадите экземпляр Azure ATP на портале Azure ATP. В Azure ATP в вашем распоряжении будет один экземпляр, который раньше назывался рабочей областью. Он позволяет управлять несколькими лесами на одной панели.

> [!IMPORTANT]
> Сейчас центры обработки данных Azure ATP развертываются в Европе, Северной Америке и Центральной Америке, в странах Карибского бассейна и Азии. Экземпляр создается автоматически в центре обработки данных, географически ближайшем к Azure Active Directory (Azure AD). После создания экземпляры Azure ATP не получится переместить.

## <a name="prerequisites"></a>Предварительные условия

- [Лицензия Azure ATP](atp-technical-faq.md#licensing-and-privacy).
- Для доступа к порталу Azure ATP требуются права [глобального администратора или администратора безопасности в клиенте](https://docs.microsoft.com/azure/active-directory/users-groups-roles/directory-assign-admin-roles#available-roles).
- См. дополнительные сведения об [архитектуре Azure ATP](atp-architecture.md).
- См. дополнительные сведения о [предварительных условиях для Azure ATP](atp-prerequisites.md). 

## <a name="sign-in-to-the-azure-atp-portal"></a>Вход на портал Azure ATP

После проверки сети на соответствие требованиям датчика можно приступить к созданию экземпляра Azure ATP.

1. Перейдите на [портал Azure ATP](https://portal.atp.azure.com)*.

2. Войдите в систему по учетной записи пользователя Azure Active Directory.

* Клиенты GCC High могут использовать портал [Azure ATP GCC High](http://portal.atp.azure.us).  

## <a name="create-your-instance"></a>Создание экземпляра

1. Нажмите кнопку **Создать экземпляр**. 

    ![Создание экземпляра Azure ATP](media/create-instance.png)

2. Экземпляр Azure ATP автоматически получает имя исходного домена Azure AD и выделяется в центре обработки данных, ближайшем к вашему клиенту Azure AD. 

    ![Созданный экземпляр Azure](media/instance-created.png)

    > [!NOTE]
    > Для входа в Azure ATP необходимо использовать учетную запись пользователя, которому была назначена роль Azure ATP с правами доступа к порталу Azure ATP. Дополнительные сведения об управлении доступом на основе ролей (RBAC) в Azure ATP см. в статье о [группах ролей Azure ATP](atp-role-groups.md).
 
3. Нажмите кнопку **Конфигурация**, **Управление группами ролей** и перейдите по ссылке [Центр администрирования Azure AD](https://docs.microsoft.com/azure/active-directory/active-directory-assign-admin-roles-azure-portal), чтобы приступить к управлению группами ролей.

    ![Управление группами ролей](media/creation-manage-role-groups.png)

- Хранение данных — ранее удаленные экземпляры Azure ATP не отображаются в пользовательском интерфейсе. См. сведения о хранении данных в Azure ATP в руководстве по [обеспечению безопасности и конфиденциальности данных в Azure ATP](atp-privacy-compliance.md).

## <a name="next-steps"></a>Дальнейшие шаги

> [!div class="step-by-step"]
> ["Предварительные требования](atp-prerequisites.md)
> [Шаг 2. Подключение к Active Directory"](install-atp-step2.md)

## <a name="join-the-community"></a>Присоединяйтесь к сообществу!

Возникли дополнительные вопросы или желание обсудить с другими пользователями службу Azure ATP и связанные с ней вопросы безопасности? Присоединяйтесь к [сообществу Azure ATP](https://aka.ms/azureatpcommunity)!

