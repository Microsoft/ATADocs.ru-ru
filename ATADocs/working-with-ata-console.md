---
title: Основные сведения о консоли Advanced Threat Analytics
description: В этой статье описывается процедура входа в консоль ATA и ее компоненты
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 3/21/2018
ms.topic: conceptual
ms.prod: advanced-threat-analytics
ms.technology: ''
ms.assetid: 1bf264d9-9697-44b5-9533-e1c498da4f07
ms.reviewer: bennyl
ms.suite: ems
ms.openlocfilehash: 831b3cec06a943136c19b706d1b68063ec578dfa
ms.sourcegitcommit: e844155ea57f73dfe2b47f4c5c1c7f5292ccbf1e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2020
ms.locfileid: "94689468"
---
# <a name="working-with-the-ata-console"></a>Работа с консолью ATA


[!INCLUDE [Banner for top of topics](includes/banner.md)]

C помощью консоли можно отслеживать обнаруженные решением ATA подозрительные действия и принимать соответствующие меры.

Если вы введете ключ `?`, будет выведен список сочетаний клавиш для работы с порталом ATA. 

## <a name="enabling-access-to-the-ata-console"></a>Предоставление доступа к консоли ATA
Чтобы успешно войти в консоль ATA, следует войти в качестве пользователя, которому назначена роль ATA, нужная для доступа к консоли ATA. Дополнительные сведения об управлении доступом на основе ролей (RBAC) в ATA см. в статье [Группы ролей ATA](ata-role-groups.md).

## <a name="logging-into-the-ata-console"></a>Вход в консоль ATA

>[!NOTE]
 > Начиная с ATA 1.8, процесс входа в консоль ATA выполняется с использованием единого входа.

1. На сервере центра ATA щелкните значок **консоли Microsoft ATA** на рабочем столе или откройте браузер и перейдите к консоли ATA.

    ![Значок сервера ATA](media/ata-server-icon.png)

   >[!NOTE]
   > Кроме того, можно открыть браузер из центра или шлюза ATA и ввести в адресную строку IP-адрес, указанный для консоли ATA при установке центра ATA.    

1. Если компьютер, на котором установлен центр ATA, и компьютер, с которого вы пытаетесь получить доступ к консоли ATA, присоединены к домену, ATA поддерживает единый вход, интегрированный с проверкой подлинности. Если вы уже вошли в компьютер, ATA будет использовать соответствующий токен для входа в консоль ATA. Кроме того, можно выполнять вход в систему с помощью смарт-карты. Ваши разрешения в ATA будут соответствовать вашей [роли администратора](ata-role-groups.md).

   > [!NOTE]
   > При входе в компьютер, с которого вы будете получать доступ к консоли ATA, используйте имя пользователя и пароль администратора ATA. Вы также можете запустить браузер от имени другого пользователя или выйти из системы Windows и снова войти как администратор ATA. Чтобы при доступе к консоли ATA был выведен запрос на ввод учетных данных, откройте ее, перейдя по соответствующему IP-адресу.

1. Для выполнения входа с использованием функции единого входа сайт консоли ATA должен быть определен в браузере как сайт местной интрасети, а доступ должен осуществляться с помощью краткого имени или localhost.

> [!NOTE]
> Помимо записи в журнал всех подозрительных действий и оповещений о работоспособности, выполняется аудит всех изменений конфигурации, вносимых в консоли ATA, в журнале событий Windows на компьютере центра ATA (**Журнал приложений и служб** > **Microsoft ATA**). Кроме того, выполняется аудит всех операций входа в консоль ATA.<br></br>  Сведения об изменениях конфигурации, влияющих на работу шлюза ATA, также записываются в журнал событий Windows на компьютере шлюза ATA. 



## <a name="the-ata-console"></a>Консоль ATA

Консоль ATA предоставляет краткий обзор всех оповещений о подозрительных действиях в хронологическом порядке и позволяет получить дополнительные сведения о любой активности и связанных с ней действиями. В консоли также отображаются оповещения и уведомления о неполадках сети ATA или о новых подозрительных действиях.

Ниже приведены основные элементы консоли ATA.


### <a name="attack-time-line"></a>Временная шкала атак

Целевая страница по умолчанию, на которую вы попадаете сразу после входа в консоль ATA. По умолчанию на временной шкале атак отображаются все открытые подозрительные действия. Временную шкалу атак можно фильтровать, чтобы просмотреть все, открытые, закрытые или заблокированные подозрительные действия. Вы также можете просмотреть уровень серьезности каждого действия.

![Изображение временной шкалы атак ATA](media/ATA-Suspicious-Activity-Timeline.jpg)

Дополнительные сведения см. в статье [Обработка подозрительных действий](working-with-suspicious-activities.md).

### <a name="notification-bar"></a>Панель уведомлений

При обнаружении нового подозрительного действия панель уведомлений автоматически открывается с правой стороны. Если подозрительные действия были обнаружены после того, как вы покинули консоль, панель уведомлений откроется после выполнения входа. Чтобы открыть панель уведомлений, щелкните стрелку справа.

![Изображение панели уведомлений ATA](media/notification-bar-1.7.png)

### <a name="whats-new"></a>Новые возможности

После выпуска новой версии ATA в правой верхней части отображается окно **Новые возможности** со сведениями о добавленных в последнюю версию функциях. В нем также содержатся ссылки для скачивания новой версии.

### <a name="filtering-panel"></a>Панель фильтров

Подозрительные действия, которые отображаются на временной шкале атак или на вкладке подозрительных действий в профиле сущности, можно фильтровать по состоянию и уровню серьезности.

### <a name="search-bar"></a>Панель поиска

Панель поиска расположена в верхнем меню. С ее помощью можно найти конкретного пользователя, компьютер или группы в ATA. Чтобы воспользоваться панелью поиска, просто начните вводить текст в текстовом поле.

![Изображение панели поиска консоли ATA](media/ATA-console-search.png)

### <a name="health-center"></a>Центр работоспособности

В центре работоспособности отображаются оповещения об аномальном поведении компонентов в развернутом решении ATA.

![Изображение центра работоспособности ATA](media/ATA-Health-Issue.jpg)

При обнаружении каких-либо ошибок сети (например, ошибки подключения или отключения шлюза ATA) на значке центра работоспособности появится красная точка. ![Красная точка над значком центра работоспособности ATA (рисунок)](media/ATA-Health-Center-Alert-red-dot.png)

### <a name="sensitive-groups"></a>Привилегированные группы

Перечисленные ниже группы рассматриваются в ATA как **привилегированные**. Любая сущность, которая входит в эти группы, считается конфиденциальной:

- Контроллеры домена предприятия — только чтение 
- Администраторы домена 
- Контроллеры домена 
- Администраторы схемы
- Администраторы предприятия 
- Владельцы-создатели групповой политики 
- Контроллеры домена только для чтения 
- Администраторы  
- Опытные пользователи  
- Операторы учета  
- Операторы сервера   
- Операторы печати
- Операторы архива
- Репликаторы 
- Пользователи удаленного рабочего стола 
- Операторы настройки сети 
- Создатели входящего доверия леса 
- Администраторы DNS 


### <a name="mini-profile"></a>Мини-профиль

При наведении в консоли указателя мыши на сущность (где представлена одна сущность, например пользователь или компьютер) автоматически отображается мини-профиль сущности, в котором содержатся следующие сведения:

![Изображение мини-профиля ATA](media/ATA-mini-profile.jpg)

- Имя

- Picture

- Email

- Telephone

- Сведения о количестве подозрительных действий по уровню серьезности



## <a name="see-also"></a>См. также:
[Обязательно ознакомьтесь с форумом ATA.](https://social.technet.microsoft.com/Forums/security/home?forum=mata)
