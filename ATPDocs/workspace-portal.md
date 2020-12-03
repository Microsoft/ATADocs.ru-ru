---
title: Основные сведения о портале Microsoft Defender для удостоверений
description: Узнайте, как войти на портал Microsoft Defender для удостоверений и ознакомьтесь с компонентами портала
ms.date: 10/27/2020
ms.topic: conceptual
ms.openlocfilehash: 00e29d828a58a76bfdbec1e28582135466d756ea
ms.sourcegitcommit: cdb7ae4580851e25aae24d07e7d66a750aa54405
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/03/2020
ms.locfileid: "96544578"
---
# <a name="working-with-the-product-long-portal"></a>Работа с порталом [!INCLUDE [Product long](includes/product-long.md)]

> [!NOTE]
> Все функции [!INCLUDE [Product long](includes/product-long.md)], описанные на этой странице, также доступны на новом [портале Cloud App Security](https://portal.cloudappsecurity.com).

C помощью портала [!INCLUDE [Product long](includes/product-long.md)] можно отслеживать обнаруженные [!INCLUDE [Product short](includes/product-short.md)] подозрительные действия и принимать соответствующие меры.

Если вы введете `?`, будет выведен список сочетаний клавиш для доступа к специальным возможностям портала [!INCLUDE [Product short](includes/product-short.md)].

Портал [!INCLUDE [Product short](includes/product-short.md)] позволяет быстро просмотреть все оповещения о подозрительных действиях в хронологическом порядке и позволяет получить дополнительные сведения о любой активности и связанных с ней действиями. На портале [!INCLUDE [Product short](includes/product-short.md)] также отображаются оповещения и уведомления о проблемах, обнаруженных [!INCLUDE [Product short](includes/product-short.md)], или о новых подозрительных действиях.

В этой статье показано, как начать работу с основными элементами портала [!INCLUDE [Product short](includes/product-short.md)].

## <a name="enabling-access-to-the-product-short-portal"></a>Доступ к порталу [!INCLUDE [Product short](includes/product-short.md)]

Для входа на портал [!INCLUDE [Product short](includes/product-short.md)] необходимо использовать учетную запись пользователя, которому было назначено членство в соответствующей группе безопасности Azure Active Directory с правами доступа к порталу [!INCLUDE [Product short](includes/product-short.md)].
Дополнительные сведения об управлении доступом на основе ролей (RBAC) в [!INCLUDE [Product short](includes/product-short.md)] см. в статье [Использование групп ролей [!INCLUDE [Product short](includes/product-short.md)]](role-groups.md).

## <a name="logging-into-the-product-short-portal"></a>Выполнение входа на портал [!INCLUDE [Product short](includes/product-short.md)]

1. Для входа на портал [!INCLUDE [Product short](includes/product-short.md)] вы можете войти на портал [https://portal.atp.azure.com](https://portal.atp.azure.com) и выбрать свой экземпляр либо перейти по URL-адресу экземпляра: `https://*instancename*.atp.azure.com`.

1. [!INCLUDE [Product short](includes/product-short.md)] поддерживает единый вход, интегрированный с проверкой подлинности Windows. Когда вы выполняете вход на компьютер, [!INCLUDE [Product short](includes/product-short.md)] использует существующий маркер для входа на портал [!INCLUDE [Product short](includes/product-short.md)]. Кроме того, можно выполнять вход в систему с помощью смарт-карты. Ваши разрешения в [!INCLUDE [Product short](includes/product-short.md)] будут соответствовать вашей [роли администратора](role-groups.md).

   > [!NOTE]
   > Выполняя вход на компьютер, с которого вы будете обращаться к порталу [!INCLUDE [Product short](includes/product-short.md)], используйте имя пользователя и пароль администратора [!INCLUDE [Product short](includes/product-short.md)]. Вы также можете запустить браузер от имени другого пользователя или выйти из Windows и войти как администратор [!INCLUDE [Product short](includes/product-short.md)]. В отличие от портала [!INCLUDE [Product short](includes/product-short.md)] на новом портале [Cloud App Security](https://portal.cloudappsecurity.com) есть функция многопользовательского входа. Дополнительная лицензия на использование с [!INCLUDE [Product short](includes/product-short.md)] не требуется.

### <a name="attack-time-line"></a>Временная шкала атак

Временная шкала атак — это целевая страница по умолчанию, на которую вы попадаете сразу после входа на портал [!INCLUDE [Product short](includes/product-short.md)]. По умолчанию на временной шкале атак отображаются все открытые подозрительные действия. Временную шкалу атак можно фильтровать, чтобы просмотреть все, открытые, закрытые или заблокированные подозрительные действия. Вы также можете просмотреть уровень серьезности каждого действия.

![[!INCLUDE [Product short](includes/product-short.md)]: изображение временной шкалы атак](media/sa-timeline.png)

Дополнительные сведения: [Обработка оповещений системы безопасности](working-with-suspicious-activities.md).

### <a name="whats-new"></a>Новые возможности

После выпуска новой версии [!INCLUDE [Product short](includes/product-short.md)] справа вверху отображается окно **Новые возможности** со сведениями о добавленных в последнюю версию функциях. В нем также содержатся ссылки для скачивания новой версии.

### <a name="filtering-panel"></a>Панель фильтров

Подозрительные действия, которые отображаются на временной шкале атак или на вкладке подозрительных действий в профиле сущности, можно фильтровать по состоянию и уровню серьезности.

<a name="search-bar"></a>

### <a name="search-bar"></a>Панель поиска

Панель поиска расположена в верхнем меню. С ее помощью можно найти конкретного пользователя, компьютер или группы в [!INCLUDE [Product short](includes/product-short.md)]. Чтобы воспользоваться панелью поиска, просто начните вводить текст в текстовом поле. В нижней части панели поиска указывается количество результатов поиска.

![[!INCLUDE [Product short](includes/product-short.md)]: изображение панели поиска на портале](media/workspace-portal-search.png)

Если щелкнуть указанное количество, откроется страница результатов поиска, где можно отфильтровать результаты по типу сущности для дальнейшего изучения.

![результаты поиска](media/search-results.png)

### <a name="health-center"></a>Центр работоспособности

В центре работоспособности отображаются оповещения об аномальном поведении компонентов в экземпляре [!INCLUDE [Product short](includes/product-short.md)].

![[!INCLUDE [Product short](includes/product-short.md)]: изображение центра работоспособности](media/health-issue.png)

При обнаружении каких-либо ошибок сети (например, ошибки подключения или отключения автономного датчика [!INCLUDE [Product short](includes/product-short.md)]) на значке центра работоспособности появится красная точка.

![[!INCLUDE [Product short](includes/product-short.md)]: изображение красной точки на значке центра работоспособности](media/health-bar.png)

### <a name="sensitive-groups"></a>Привилегированные группы

Сведения о привилегированных группах в [!INCLUDE [Product short](includes/product-short.md)] см. в статье [Работа с привилегированными группами](sensitive-accounts.md).

### <a name="mini-profile"></a>Мини-профиль

При наведении указателя мыши на сущность на портале [!INCLUDE [Product short](includes/product-short.md)] (где представлена одна сущность, например пользователь или компьютер) автоматически отображается мини-профиль сущности, в котором содержатся следующие сведения:

![[!INCLUDE [Product short](includes/product-short.md)]: изображение мини-профиля](media/mini-profile.png)

- Имя
- Название
- Отдел
- Теги AD
- Электронная почта
- Office
- Номер телефона
- Домен
- Имя SAM
- Дата создания: дата создания сущности в Active Directory. Если сущность была создана до запуска мониторинга в [!INCLUDE [Product short](includes/product-short.md)], она не будет отображаться.
- Первое появление: дата первого обнаружения [!INCLUDE [Product short](includes/product-short.md)] действия из этой сущности.
- Последнее появление: дата последнего обнаружения [!INCLUDE [Product short](includes/product-short.md)] действия из этой сущности.
- Эмблема SA: отображается при наличии подозрительных действий, связанных с данной сущностью.
- Эмблема ATP в Microsoft Defender: будет отображаться при наличии подозрительных действий, связанных сущностью, в Microsoft Defender для удостоверений.
- Эмблема путей бокового смещения: будет отображаться, если для этой сущности в течение последних двух дней были обнаружены пути бокового смещения.

## <a name="see-also"></a>См. также

- [Создание экземпляров [!INCLUDE [Product short](includes/product-short.md)]](install-step1.md)
- [Посетите форум по [!INCLUDE [Product short](includes/product-short.md)].](https://aka.ms/MDIcommunity)
