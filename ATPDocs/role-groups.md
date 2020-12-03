---
title: Защитник Майкрософт для групп ролей удостоверений для управления доступом
description: Руководство по работе с защитником Майкрософт для групп ролей удостоверений.
ms.date: 02/27/2020
ms.topic: conceptual
ms.openlocfilehash: cbfb13ace446ba980af649f07951eed3aabbe4fd
ms.sourcegitcommit: cdb7ae4580851e25aae24d07e7d66a750aa54405
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/03/2020
ms.locfileid: "96544391"
---
# <a name="product-long-role-groups"></a>[!INCLUDE [Product long](includes/product-long.md)] группы ролей

[!INCLUDE [Product long](includes/product-long.md)] обеспечивает безопасность на основе ролей для защиты данных в соответствии с потребностями Организации в обеспечении безопасности и соответствия требованиям. [!INCLUDE [Product short](includes/product-short.md)] Поддержка трех отдельных ролей: Администраторы, пользователи и средства просмотра.

[!INCLUDE [Handle personal data](../includes/gdpr-intro-sentence.md)]

Группы ролей включают управление доступом для [!INCLUDE [Product short](includes/product-short.md)] . С помощью групп ролей вы можете разделить обязанности сотрудников безопасности, предоставив каждому только такой объем доступа, который требуется для их работы. В этой статье объясняется управление доступом, авторизация ролей и приводятся сведения о [!INCLUDE [Product short](includes/product-short.md)] работе с группами ролей в [!INCLUDE [Product short](includes/product-short.md)] .

> [!NOTE]
> Любой глобальный администратор или администратор безопасности на Azure Active Directory клиента автоматически является [!INCLUDE [Product short](includes/product-short.md)] администратором.

## <a name="accessing-the-product-short-portal"></a>Доступ к [!INCLUDE [Product short](includes/product-short.md)] порталу

Доступ к [!INCLUDE [Product short](includes/product-short.md)] порталу (Portal.ATP.Azure.com) может осуществлять только пользователь Azure AD, имеющий роль каталога глобального администратора или администратора безопасности. После ввода на портале требуемой роли можно создать [!INCLUDE [Product short](includes/product-short.md)] экземпляр. [!INCLUDE [Product short](includes/product-short.md)] служба создает три группы безопасности в клиенте Azure Active Directory: Администраторы, пользователи и зрители.

> [!NOTE]
> Доступ к [!INCLUDE [Product short](includes/product-short.md)] порталу предоставляется только пользователям в пределах [!INCLUDE [Product short](includes/product-short.md)] группы безопасности в пределах Azure Active Directory, а также глобальным администраторам и администраторов безопасности пользователи клиента.

## <a name="types-of-product-short-security-groups"></a>Типы [!INCLUDE [Product short](includes/product-short.md)] групп безопасности

[!INCLUDE [Product short](includes/product-short.md)] предоставляет три типа групп безопасности: "Администраторы Azure ATP *(имя экземпляра)* ", "Пользователи Azure ATP *(имя экземпляра)"* и "средства просмотра Azure ATP *(имя экземпляра)* ". В следующей таблице описывается тип доступа на [!INCLUDE [Product short](includes/product-short.md)] портале, доступный для каждой роли. В зависимости от назначенной роли различные экраны и параметры меню на [!INCLUDE [Product short](includes/product-short.md)] портале недоступны для этих пользователей следующим образом.

|Действие |Администраторы Azure ATP *(имя экземпляра)*|Пользователи Azure ATP *(имя экземпляра)*|Средства просмотра Azure ATP *(имя экземпляра)*|
|----|----|----|----|
|Изменение состояния оповещений о работоспособности|Доступно|Недоступно|Недоступно|
|Изменение состояния оповещений системы безопасности (открыть повторно, закрыть, исключить, игнорировать)|Доступно|Доступно|Недоступно|
|Удалить экземпляр|Доступно|Недоступно|Недоступно|
|Загрузка отчета|Доступно|Доступно|Доступно|
|Вход|Доступно|Доступно|Доступно|
|Передача или экспорт оповещений системы безопасности (по электронной почте, посредством ссылки или путем предоставления сведений для скачивания)|Доступно|Доступно|Доступно|
|Обновление [!INCLUDE [Product short](includes/product-short.md)] конфигурации — обновления|Доступно|Недоступно|Недоступно|
|[!INCLUDE [Product short](includes/product-short.md)]Конфигурация обновления — Теги сущностей (конфиденциальные и honeytoken)|Доступно|Доступно|Недоступно|
|[!INCLUDE [Product short](includes/product-short.md)]Конфигурация обновления — исключения|Доступно|Доступно|Недоступно|
|[!INCLUDE [Product short](includes/product-short.md)]Конфигурация обновления — язык|Доступно|Доступно|Недоступно|
|[!INCLUDE [Product short](includes/product-short.md)]Конфигурация обновления — уведомления (электронная почта и системный журнал)|Доступно|Доступно|Недоступно|
|[!INCLUDE [Product short](includes/product-short.md)]Конфигурация обновления — определения предварительной версии|Доступно|Доступно|Недоступно|
|Обновление [!INCLUDE [Product short](includes/product-short.md)] конфигурации — запланированные отчеты|Доступно|Доступно|Недоступно|
|[!INCLUDE [Product short](includes/product-short.md)]Конфигурация обновления — источники данных (службы каталогов, SIEM, VPN WD-ATP)|Доступно|Недоступно|Недоступно|
|Обновление [!INCLUDE [Product short](includes/product-short.md)] конфигурации. датчики (скачивание, повторное создание ключа, Настройка, удаление)|Доступно|Недоступно|Недоступно|
|Просмотр профилей сущностей и оповещений системы безопасности|Доступно|Доступно|Доступно|

Когда пользователи пытаются получить доступ к странице, недоступной для их группы ролей, они перенаправляются на [!INCLUDE [Product short](includes/product-short.md)] несанкционированную страницу.

## <a name="add-and-remove-users"></a>Добавление и удаление пользователей

[!INCLUDE [Product short](includes/product-short.md)] использует группы безопасности Azure AD в качестве базиса для групп ролей. Управлять группами ролей можно на [странице Управление группами](https://aad.portal.azure.com/#blade/Microsoft_AAD_IAM/GroupsManagementMenuBlade/All%20groups). Добавлять в группы безопасности или удалять из этих групп можно только пользователей Azure Active Directory.

## <a name="see-also"></a>См. также

- [Средство определения размера [!INCLUDE [Product short](includes/product-short.md)]](https://aka.ms/aatpsizingtool)
- [Архитектура [!INCLUDE [Product short](includes/product-short.md)]](architecture.md)
- [Установка [!INCLUDE [Product short](includes/product-short.md)]](install-step1.md)
- [Посетите форум по [!INCLUDE [Product short](includes/product-short.md)].](https://aka.ms/MDIcommunity)
