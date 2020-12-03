---
title: Защитник Майкрософт для идентификации в Microsoft Cloud App Security
description: Обзор защитника Майкрософт для функций идентификации в Microsoft Cloud App Security.
ms.date: 01/05/2020
ms.topic: how-to
ms.openlocfilehash: ef4cbe9f0c49311a3d10b79e03fc725ea5131105
ms.sourcegitcommit: cdb7ae4580851e25aae24d07e7d66a750aa54405
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/03/2020
ms.locfileid: "96543864"
---
# <a name="using-product-long-with-microsoft-cloud-app-security"></a>Использование [!INCLUDE [Product long](includes/product-long.md)] с Microsoft Cloud App Security

Эта статья поможет вам понять и проанализировать улучшенное исследование при использовании Microsoft Cloud App Security портала с [!INCLUDE [Product long](includes/product-long.md)] .

Благодаря использованию существующих локальных обнаружений и анализа аномальных поведений доступ [!INCLUDE [Product short](includes/product-short.md)] с помощью Microsoft Cloud App Security портала обеспечивает возможность обнаружения и оповещения о конфиденциальных данных, утечканых на предприятии, а также действия фильтров и создание политик с поддержкой действий. Это гибридное предложение анализирует действия и оповещения на основе анализа поведения пользователей и сущностей, чтобы выявить схемы опасного поведения, и предоставляет оценку приоритета для изучения, чтобы оптимизировать реагирование на инциденты для скомпрометированных удостоверений.

В этой статье рассматриваются следующие темы:

> [!div class="checklist"]
>
> - Обзор службы
> - Новые способы доступа [!INCLUDE [Product short](includes/product-short.md)]
> - лицензирование необходимых компонентов;
> - Где найти [!INCLUDE [Product short](includes/product-short.md)] Отслеживание действий в Cloud App Security

## <a name="service-overview"></a>Обзор службы

При интеграции с [!INCLUDE [Product short](includes/product-short.md)] портал Cloud App Security предоставляет оповещения и аналитические сведения из:

- Решение Microsoft Cloud App Security, идентифицирующее атаки при работе в облаке, поддерживает не только продукты Майкрософт, но и сторонние приложения.
- [!INCLUDE [Product long](includes/product-long.md)], которая использует машинное обучение и аналитику поведения для обнаружения атак по локальной сети.
- Защита идентификации Azure Active Directory позволяет выявить и предотвратить риски идентификации, связанные с пользователями и их учетными данными, при работе в облачных приложениях.

## <a name="access-product-short"></a>Имеет [!INCLUDE [Product short](includes/product-short.md)]

Нажмите, чтобы продолжить использование на [!INCLUDE [Product short](includes/product-short.md)] [!INCLUDE [Product short](includes/product-short.md)] портале, или можно получить доступ к [!INCLUDE [Product short](includes/product-short.md)] оповещениям и оценкам удостоверений с помощью портала Microsoft Cloud App Security. В любом рабочем процессе [!INCLUDE [Product short](includes/product-short.md)] задачи настройки и настройки продолжают обрабатываться на [!INCLUDE [Product short](includes/product-short.md)] портале.

## <a name="prerequisites"></a>Предварительные условия

Чтобы получить все возможности изучения поведения пользователей в гибридной среде, вам понадобится следующее:

- Действительная лицензия для Microsoft Cloud App Security
- Действительная лицензия для [!INCLUDE [Product long](includes/product-long.md)] подключения к экземпляру Active Directory

>[!NOTE]
>
> - Если у вас нет подписки на Cloud App Security, вы по-прежнему сможете использовать портал Cloud App Security для изучения [!INCLUDE [Product short](includes/product-short.md)] оповещений и углубленного исследования пользователей и их локальных управляемых действий, но вы не будете получать связанные данные из облачных приложений.
> - [!INCLUDE [Product short](includes/product-short.md)] администраторам могут потребоваться новые разрешения для доступа к Cloud App Security. Дополнительные сведения о назначении разрешений Cloud App Security см. в разделе [Управление доступом администратора](/cloud-app-security/manage-admins).

Дополнительные [ [!INCLUDE [Product short](includes/product-short.md)] ](/cloud-app-security/mdi-integration) сведения о том, как быстро включить [!INCLUDE [Product short](includes/product-short.md)] в Cloud App Security, см. в разделе Интеграция.

## <a name="product-short-in-cloud-app-security"></a>[!INCLUDE [Product short](includes/product-short.md)] в Cloud App Security

Основы использования портала Cloud App Security см. в [кратком руководстве по Cloud App Security](/cloud-app-security/getting-started-with-cloud-app-security).

Получите доступ к [!INCLUDE [Product short](includes/product-short.md)] данным и новым гибридным функциям в Cloud App Security оповещениях, действиях и страницах пользователей.

## <a name="alerts"></a>Предупреждения

[!INCLUDE [Product short](includes/product-short.md)] оповещения отображаются в очереди Cloud App Security **предупреждения** . Дополнительные параметры фильтрации оповещений доступны только при просмотре оповещений в Cloud App Security. [!INCLUDE [Product short](includes/product-short.md)] оповещения фильтруются с помощью фильтра приложений для **Active Directory**.

## <a name="alert-management"></a>Управление оповещениями

При использовании [!INCLUDE [Product short](includes/product-short.md)] с Cloud App Security Закрытие оповещений в одной службе не будет автоматически закрыто в другой службе. Определите, где вы будете обрабатывать оповещения, чтобы не повторять одни и те же действия.

## <a name="siem-notification"></a>Уведомление SIEM

Если в [!INCLUDE [Product short](includes/product-short.md)] настоящее время службы (и Cloud App Security) настроены для отправки уведомлений о предупреждениях в SIEM, то после включения [!INCLUDE [Product short](includes/product-short.md)] интеграции в Cloud App Security вы начнете получать дублирующиеся SIEM уведомления для одного и того же оповещения. Каждая служба будет выдавать свое оповещение со своим идентификатором. Чтобы избежать дублирования и путаницы, решите, в какой службе вы хотите обрабатывать оповещения, и остановите отправку в SIEM уведомлений из другой службы.

## <a name="activities"></a>Действия

[!INCLUDE [Product short](includes/product-short.md)] оповещения отображаются в **журнале действий** Cloud App Security. Дополнительные параметры и возможности фильтрации действий доступны только при просмотре оповещений в Cloud App Security. Сведения о том, как фильтровать и создавать новые политики действий, см. в разделе [ [!INCLUDE [Product short](includes/product-short.md)] действия, использующие Microsoft Cloud App Security](activities-filtering-mcas.md) .

## <a name="user-pages"></a>Страницы пользователя

Страницы пользователя содержат [оценку приоритета для изучения](/cloud-app-security/tutorial-ueba) по каждому пользователю и журнал всех действий.

Чтобы получить доступ к странице системного пользователя:

1. Откройте **Оповещения** в главном меню.
1. Выберите и отфильтруйте очередь оповещений для конкретного пользователя с помощью поля **Имя пользователя**.

 или

1. Из меню **Исследовать** выберите **Журнал действий**.
1. Отфильтруйте очередь журнала действий по пользователям.

    ![Журнал действий](media/mcas-activity-filter.png)

## <a name="next-steps"></a>Дальнейшие шаги

Сведения о том, как фильтровать и создавать новые политики действий, см. в разделе [ [!INCLUDE [Product short](includes/product-short.md)] действия, использующие Microsoft Cloud App Security](activities-filtering-mcas.md) .

## <a name="join-the-community"></a>Присоединяйтесь к сообществу!

У вас есть дополнительные вопросы или вы хотите обсудить с другими пользователями особенности использования [!INCLUDE [Product short](includes/product-short.md)] или вопросы, связанные с безопасностью? Присоединяйтесь к [сообществу [!INCLUDE [Product short](includes/product-short.md)]](https://techcommunity.microsoft.com/t5/Azure-Advanced-Threat-Protection/bd-p/AzureAdvancedThreatProtection).
