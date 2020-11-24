---
title: Краткое руководство по созданию экземпляра Microsoft Defender для удостоверений
description: Краткое руководство по созданию экземпляра для развертывания Microsoft Defender для удостоверений, что является первым шагом установки Defender для удостоверений.
keywords: ''
author: shsagir
ms.author: shsagir
ms.date: 10/26/2020
ms.topic: quickstart
ms.collection: M365-security-compliance
ms.service: azure-advanced-threat-protection
ms.reviewer: itargoet
ms.suite: ems
ms.openlocfilehash: fcb99edccdd8ce98be4b9335d7703503307fd0ac
ms.sourcegitcommit: e2227c0b0e5aaa5163dc56d4131ca82f8dca8fb0
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/18/2020
ms.locfileid: "94848590"
---
# <a name="quickstart-create-your-product-long-instance"></a>Краткое руководство. Создание экземпляра [!INCLUDE [Product long](includes/product-long.md)]

В этом кратком руководстве вы создадите экземпляр [!INCLUDE [Product long](includes/product-long.md)] на портале [!INCLUDE [Product short](includes/product-short.md)]. В [!INCLUDE [Product short](includes/product-short.md)] в вашем распоряжении будет один экземпляр, который раньше назывался рабочей областью. Он позволяет управлять несколькими лесами на одной панели.

> [!IMPORTANT]
> Сейчас центры обработки данных [!INCLUDE [Product short](includes/product-short.md)] развертываются в Европе, Великобритании, Северной Америке и Центральной Америке, в странах Карибского бассейна и Азии. Экземпляр создается автоматически в центре обработки данных, географически ближайшем к Azure Active Directory (Azure AD). После создания экземпляры [!INCLUDE [Product short](includes/product-short.md)] не получится переместить.

## <a name="prerequisites"></a>Предварительные требования

- [Лицензия [!INCLUDE [Product long](includes/product-long.md)]](technical-faq.md#licensing-and-privacy).
- Для доступа к порталу [!INCLUDE [Product short](includes/product-short.md)] требуются права [глобального администратора или администратора безопасности в клиенте](/azure/active-directory/users-groups-roles/directory-assign-admin-roles#available-roles).
- Знакомство со статьей [Архитектура [!INCLUDE [Product short](includes/product-short.md)]](architecture.md).
- Знакомство со статьей [Предварительные требования [!INCLUDE [Product short](includes/product-short.md)]](prerequisites.md).

## <a name="sign-in-to-the-product-short-portal"></a>Вход на портал [!INCLUDE [Product short](includes/product-short.md)]

После проверки сети на соответствие требованиям датчика можно приступить к созданию экземпляра [!INCLUDE [Product short](includes/product-short.md)].

1. Перейдите на [портал [!INCLUDE [Product short](includes/product-short.md)]](https://portal.atp.azure.com)*.

1. Войдите в систему по учетной записи пользователя Azure Active Directory.

\* Клиентам GCC High необходимо использовать портал [[!INCLUDE [Product short](includes/product-short.md)] для GCC High](http://portal.atp.azure.us).

## <a name="create-your-instance"></a>Создание экземпляра

1. Нажмите кнопку **Создать экземпляр**.

    ![Создание экземпляра [!INCLUDE [Product short](includes/product-short.md)]](media/create-instance.png)

1. Экземпляр [!INCLUDE [Product short](includes/product-short.md)] автоматически получает имя исходного домена Azure AD и выделяется в центре обработки данных, ближайшем к вашему клиенту Azure AD.

    ![Созданный экземпляр Azure](media/instance-created.png)

    > [!NOTE]
    > Для входа в [!INCLUDE [Product short](includes/product-short.md)] необходимо использовать учетную запись пользователя, которому была назначена роль [!INCLUDE [Product short](includes/product-short.md)] с правами доступа к порталу [!INCLUDE [Product short](includes/product-short.md)]. Дополнительные сведения об управлении доступом на основе ролей (RBAC) в [!INCLUDE [Product short](includes/product-short.md)] см. в статье [Использование групп ролей [!INCLUDE [Product short](includes/product-short.md)]](role-groups.md).

1. Выберите пункт **Конфигурация**, **Управление группами ролей** и перейдите по ссылке [Центр администрирования Azure AD](/azure/active-directory/active-directory-assign-admin-roles-azure-portal), чтобы приступить к управлению группами ролей.

    ![Управление группами ролей](media/creation-manage-role-groups.png)

- Хранение данных — ранее удаленные экземпляры [!INCLUDE [Product short](includes/product-short.md)] не отображаются в пользовательском интерфейсе. Дополнительные сведения о хранении данных в [!INCLUDE [Product short](includes/product-short.md)] см. в разделе [Безопасность и конфиденциальность данных в [!INCLUDE [Product short](includes/product-short.md)]](privacy-compliance.md).

## <a name="next-steps"></a>Дальнейшие шаги

> [!div class="step-by-step"]
> ["Предварительные требования](prerequisites.md)
> [Шаг 2. Подключение к Active Directory"](install-step2.md)

## <a name="join-the-community"></a>Присоединяйтесь к сообществу!

У вас есть дополнительные вопросы или вы хотите обсудить с другими пользователями особенности использования [!INCLUDE [Product short](includes/product-short.md)] или вопросы, связанные с безопасностью? Присоединяйтесь к [сообществу [!INCLUDE [Product short](includes/product-short.md)]](https://aka.ms/MDIcommunity).
