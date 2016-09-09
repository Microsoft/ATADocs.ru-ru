---
title: "Работа с консолью ATA | Microsoft ATA"
description: "В этой статье описывается процедура входа в консоль ATA и ее компоненты"
keywords: 
author: rkarlin
manager: mbaldwin
ms.date: 04/28/2016
ms.topic: article
ms.prod: 
ms.service: advanced-threat-analytics
ms.technology: 
ms.assetid: 1bf264d9-9697-44b5-9533-e1c498da4f07
ms.reviewer: bennyl
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: f13750f9cdff98aadcd59346bfbbb73c2f3a26f0
ms.openlocfilehash: 1eb9397b541eb64cef553f61e8517568d16b0092


---

# Работа с консолью ATA

C помощью консоли можно отслеживать обнаруженные решением ATA подозрительные действия и принимать соответствующие меры.

## Предоставление доступа к консоли ATA
Каждый пользователь, который состоит в локальной группе администраторов на сервере центра ATA, может войти в консоль ATA и управлять параметрами ATA.
Чтобы предоставить пользователю разрешение на вход в консоль ATA без прав локального администратора, необходимо добавить его в локальную группу **администраторов Microsoft Advanced Threat Analytics**.

## Вход в консоль ATA

1. На рабочем столе сервера центра ATA щелкните значок **консоли Microsoft ATA** или откройте браузер и перейдите к консоли ATA.

    ![Значок сервера ATA](media/ata-server-icon.png)

>[!NOTE]
> Кроме того, можно открыть браузер из центра или шлюза ATA и ввести в адресную строку IP-адрес, указанный для консоли ATA при установке центра ATA.    

2.  Введите имя пользователя и пароль, а затем нажмите кнопку **Войти**.

![Изображения экрана входа в ATA](media/ATA-log-in-screen.jpg)

> [!NOTE]
> Необходимо войти в консоль от имени участника локальной группы администраторов или группы администраторов Microsoft Advanced Threat Analytics.

## Консоль ATA

Консоль ATA предоставляет краткий обзор всех оповещений о подозрительных действиях в хронологическом порядке и позволяет получить дополнительные сведения о любой активности и связанных с ней действиями. В консоли также отображаются оповещения и уведомления о неполадках сети ATA или о новых подозрительных действиях.

Ниже приведены основные элементы консоли ATA.


### Временная шкала атак

Целевая страница по умолчанию, на которую вы попадаете сразу после входа в консоль ATA. По умолчанию на временной шкале атак отображаются все открытые подозрительные действия. Временную шкалу атак можно фильтровать, чтобы просмотреть все, открытые, закрытые или устраненные подозрительные действия. Вы также можете просмотреть уровень серьезности каждого действия.

![Изображение временной шкалы атак ATA](media/attack-timeline.png)

Дополнительные сведения см. в статье [Обработка подозрительных действий](/advanced-threat-analytics/deploy-use/working-with-suspicious-activities).

### Панель уведомлений

При обнаружении нового подозрительного действия панель уведомлений автоматически открывается с правой стороны. Если подозрительные действия были обнаружены после того, как вы покинули консоль, панель уведомлений откроется после выполнения входа. Чтобы открыть панель уведомлений, щелкните стрелку справа.

![Изображение панели уведомлений ATA](media/notification-bar.png)

### Панель фильтров

Подозрительные действия, которые отображаются на временной шкале атак или на вкладке подозрительных действий в профиле сущности, можно фильтровать по состоянию и уровню серьезности.

### Панель поиска

Панель поиска расположена в верхнем меню. С ее помощью можно найти конкретного пользователя, компьютер или группу в ATA. Чтобы воспользоваться панелью поиска, просто начните вводить текст в текстовом поле.

![Изображение панели поиска консоли ATA](media/ATA-console-search.png)

### Центр работоспособности

В центре работоспособности отображаются оповещения об аномальном поведении компонентов в развернутом решении ATA.

![Изображение центра работоспособности ATA](media/health-center.png)

При обнаружении каких-либо ошибок сети (например, ошибки подключения или отключения шлюза ATA) на значке центра работоспособности появится красная точка. ![Красная точка над значком центра работоспособности ATA (рисунок)](media/ATA-Health-Center-Alert-red-dot.png)

Оповещения центра работоспособности можно закрывать или разрешать, а также фильтровать по уровню серьезности (высокий, средний или низкий). Если разрешить оповещение, которое служба ATA все еще распознает как активное, оно автоматически перемещается в список открытых оповещений. Если система обнаруживает, что проблема устранена, оповещение автоматически помещается в список разрешенных.

### Профили пользователей и компьютеров

Решение ATA создает профиль для каждого пользователя и компьютера в сети. В профиле пользователя отображаются общие сведения (например, членство в группе, история операций входа и недавно запрашиваемые ресурсы).

![Профиль пользователя](media/user-profile.png)

В профиле компьютера отображаются общие сведения о компьютере (например, история операций входа и недавно запрашиваемые ресурсы).

![Профиль компьютера](media/computer-profile.png)

Дополнительные сведения об объектах (компьютерах, устройствах, пользователях) отображаются на страницах ATA "Сводка", "Действия" и "Подозрительные действия".

Возле профиля, который ATA не удалось полностью опознать, будет отображаться наполовину заполненный круг.


![Изображение неразрешенного профиля ATA](media/ATA-Unresolved-Profile.jpg)

### Мини-профиль

При наведении в консоли указателя мыши на пользователя или компьютер автоматически отображается мини-профиль сущности, в котором содержатся следующие сведения:

![Изображение мини-профиля ATA](media/ATA-mini-profile.jpg)

-   Имя

-   Изображение

-   Электронная почта

-   Телефон

-   Сведения о количестве подозрительных действий по уровню серьезности



## См. также
[Обязательно ознакомьтесь с форумом ATA.](https://social.technet.microsoft.com/Forums/security/home?forum=mata)



<!--HONumber=Jul16_HO4-->

