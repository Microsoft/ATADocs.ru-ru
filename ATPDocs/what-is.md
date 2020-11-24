---
title: Что такое Microsoft Defender для удостоверений?
description: Здесь описывается решение Microsoft Defender для удостоверений и подозрительные действия, которые оно может обнаружить
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 10/27/2020
ms.topic: overview
ms.collection: M365-security-compliance
ms.service: azure-advanced-threat-protection
ms.reviewer: itargoet
ms.suite: ems
ms.openlocfilehash: 306ecc4fa1022420627d0f12cea43a738d50b45a
ms.sourcegitcommit: e2227c0b0e5aaa5163dc56d4131ca82f8dca8fb0
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/18/2020
ms.locfileid: "94848862"
---
# <a name="what-is-product-long"></a>Что такое [!INCLUDE [Product long](includes/product-long.md)]?

[!INCLUDE [Product long](includes/product-long.md)] (ранее Расширенная защита от угроз Azure или Azure ATP) — это облачное решение безопасности, которое использует сигналы локальной службы Active Directory для обнаружения и анализа сложных угроз, скомпрометированных удостоверений и вредоносных действий внутренних пользователей, направленных на вашу организацию.

[!INCLUDE [Product short](includes/product-short.md)] позволяет аналитикам и специалистам службы безопасности, занимающимся выявлением современных угроз в гибридных средах, решать следующие задачи:

- отслеживать пользователей, поведение сущностей и действия с помощью аналитики на основе обучения;
- защищать удостоверения и учетные данные пользователей, хранящиеся в Active Directory;
- выявлять и изучать подозрительные действия пользователей и современные атаки на основе модели цепочки атаки;
- получать сведения об инцидентах в четко установленные сроки для быстрого рассмотрения.

## <a name="monitor-and-profile-user-behavior-and-activities"></a>Отслеживание и профилирование поведения и действий пользователей

[!INCLUDE [Product short](includes/product-short.md)] отслеживает и анализирует действия пользователей в сети и информацию о них, такую как разрешения и членство в группах, формируя базовые показатели для каждого пользователя. Затем [!INCLUDE [Product short](includes/product-short.md)] определяет аномалии с помощью встроенных адаптивных интеллектуальных функций, предоставляя вам информацию о подозрительных действиях и событиях и выявляя современные угрозы, скомпрометированные учетные записи и внутренние угрозы, направленные на организацию. Собственные датчики [!INCLUDE [Product short](includes/product-short.md)] отслеживают контроллеры домена организации, что позволяет получать подробное представление обо всех действиях пользователей на каждом устройстве.

## <a name="protect-user-identities-and-reduce-the-attack-surface"></a>Защита удостоверений пользователей и сокращение уязвимой зоны

[!INCLUDE [Product short](includes/product-short.md)] предоставляет бесценную информацию о конфигурациях удостоверений и рекомендации по обеспечению безопасности. Благодаря отчетам о безопасности и аналитике пользовательских профилей [!INCLUDE [Product short](includes/product-short.md)] помогает существенно сократить число направлений атак, угрожающих вашей организации, усложняя взлом учетных данных пользователей и затрудняя проведение атак. С помощью визуальных путей бокового смещения в [!INCLUDE [Product short](includes/product-short.md)] можно быстро узнать, как злоумышленник может перемещаться по сети вашей организации с целью взлома важных учетных записей, и заранее предотвратить эти риски. Отчеты о безопасности [!INCLUDE [Product short](includes/product-short.md)] помогают выявлять пользователей и устройства, которые проходят проверку подлинности с помощью открытых паролей. Они также предоставляют дополнительную информацию для оптимизации корпоративной защиты и ваших политик.

## <a name="identify-suspicious-activities-and-advanced-attacks-across-the-cyber-attack-kill-chain"></a>Выявление подозрительных действий и современных кибератак на основе модели цепочки атаки

Как правило, атаки изначально направлены на доступные объекты, например пользователей с низким уровнем прав, а затем быстро распространяются по горизонтали, пока злоумышленник не получит доступ к ценным ресурсам, например важным учетным записям, в том числе с правами администратора домена, или конфиденциальным данным. [!INCLUDE [Product short](includes/product-short.md)] позволяет устанавливать источники таких современных угроз, прослеживая всю цепочку кибератаки.

### <a name="reconnaissance"></a>Разведывательная атака

Выявляйте попытки пользователей-мошенников и злоумышленников получить информацию. Злоумышленники ищут сведения об именах пользователей, их членстве в группах, о назначенных устройствам IP-адресах, ресурсах, а также другую информацию самыми разными методами.

### <a name="compromised-credentials"></a>Компрометация учетных данных.

Выявляйте попытки получить учетные данные пользователей, обнаруживая атаки методом подбора, неудачные попытки проверки подлинности, изменение членства пользователей в группах и другие подозрительные действия.

### <a name="lateral-movements"></a>Боковое смещение

Определяйте попытки бокового смещения в вашей сети с целью получения контроля над важными учетными записями с использованием таких методов, как Pass-the-Ticket, Pass-the-Hash, Overpass-the-Hash и других.

### <a name="domain-dominance"></a>Полное управление доменом

Azure ATP позволяет обнаруживать перехват контроля над доменом, полученный через удаленное выполнение кода на контроллере домена или такими методами, как DC Shadow, несанкционированная репликация контроллера домена и Golden Ticket.

## <a name="investigate-alerts-and-user-activities"></a>Изучайте оповещения и действия пользователей

[!INCLUDE [Product short](includes/product-short.md)] предоставляет только важные оповещения системы безопасности в режиме реального времени, что позволяет не отвлекаться на ненужную информацию. Представление временной шкалы атак [!INCLUDE [Product short](includes/product-short.md)] позволяет сосредоточиться на том, что действительно имеет значение, и использовать интеллектуальные аналитические функции. [!INCLUDE [Product short](includes/product-short.md)] позволяет быстро анализировать угрозы и получать информацию о пользователях, устройствах и сетевых ресурсах в масштабе всей организации. Тесная интеграция с Microsoft Defender для конечных точек обеспечивает дополнительный уровень безопасности благодаря обнаружению современных постоянных угроз в операционной системе и защите от них.

## <a name="additional-resources-for-product-short"></a>Дополнительные ресурсы о [!INCLUDE [Product short](includes/product-short.md)]

### <a name="start-a-free-trial"></a>Запустите бесплатную пробную версию

[https://signup.microsoft.com/Signup?OfferId=87dd2714-d452-48a0-a809-d2f58c4f68b7&ali=1](https://signup.microsoft.com/Signup?OfferId=87dd2714-d452-48a0-a809-d2f58c4f68b7&ali=1 "Enterprise Mobility + Security E5")

### <a name="follow-product-short-on-microsoft-tech-community"></a>Подпишитесь на [!INCLUDE [Product short](includes/product-short.md)] в Microsoft Tech Community

[https://aka.ms/MDIcommunity](https://aka.ms/MDIcommunity "[!INCLUDE [Product short](includes/product-short.md)] on Microsoft Tech Community")

### <a name="join-the-product-short-yammer-community"></a>Вступите в сообщество Yammer по [!INCLUDE [Product short](includes/product-short.md)]

[https://www.yammer.com/azureadvisors/#/threads/inGroup?type=in_group&feedId=9386893](https://www.yammer.com/azureadvisors/#/threads/inGroup?type=in_group&feedId=9386893 "[!INCLUDE [Product short](includes/product-short.md)] Yammer community")

### <a name="visit-the-product-short-product-page"></a>Посетите страницу продукта [!INCLUDE [Product short](includes/product-short.md)]

[https://www.microsoft.com/microsoft-365/security/identity-defender](https://www.microsoft.com/microsoft-365/security/identity-defender "[!INCLUDE [Product short](includes/product-short.md)] product page")

### <a name="learn-more-about-product-short-architecture"></a>Изучите архитектуру [!INCLUDE [Product short](includes/product-short.md)]

[Архитектура [!INCLUDE [Product short](includes/product-short.md)]](architecture.md)

### <a name="watch-our-videos"></a>Просмотрите наши видеоролики

[Повысьте уровень безопасности с помощью [!INCLUDE [Product short](includes/product-short.md)]](https://techcommunity.microsoft.com/t5/video-hub/bolster-your-security-posture-with-microsoft-defender-for/m-p/1698841). Выявляйте и заранее устраняйте известные ошибки конфигурации, делая свою среду более работоспособной и устойчивой к действиям злоумышленников. Посмотрите [видео на YouTube](https://youtu.be/nx5rrxVuRTk).

[Анализ инцидентов с помощью [!INCLUDE [Product short](includes/product-short.md)]](https://techcommunity.microsoft.com/t5/video-hub/incident-investigation-with-microsoft-defender-for-identity/m-p/1698840). Узнайте, как с помощью [!INCLUDE [Product short](includes/product-short.md)] обнаруживать, анализировать и реагировать на расширенные угрозы, нацеленные на удостоверения и контроллеры домена. Начиная с предупреждения в [!INCLUDE [Product short](includes/product-short.md)] мы продемонстрируем, как эти сведения соотносятся с инцидентом, как отслеживать угрозы с помощью информации, полученной [!INCLUDE [Product short](includes/product-short.md)], и как можно инициировать автоматическое реагирование на инцидент для его устранения, прежде чем он перерастет в более крупную проблему. Посмотрите [видео YouTube](https://youtu.be/geWU4It6S48).

## <a name="whats-next"></a>Что дальше?

Развертывать [!INCLUDE [Product short](includes/product-short.md)] рекомендуется в три этапа:

### <a name="phase-1"></a>Этап 1

1. Настройте в [!INCLUDE [Product short](includes/product-short.md)] защиту основных сред. Модель быстрого развертывания [!INCLUDE [Product short](includes/product-short.md)] позволяет немедленно защитить организацию. [Установка [!INCLUDE [Product short](includes/product-short.md)]](install-step1.md)
1. Настройте [конфиденциальные учетные записи](sensitive-accounts.md) и [учетные записи honeytoken](install-step7.md).
1. Просматривайте отчеты и [пути бокового смещения](use-case-lateral-movement-path.md).

### <a name="phase-2"></a>Этап 2

1. Защитите все контроллеры домена и [леса](multi-forest.md) в вашей организации.
1. Отслеживайте все [оповещения](working-with-suspicious-activities.md) — изучайте оповещения о боковом смещении и перехвате контроля над доменом.
1. Обратитесь к [руководству по оповещениям системы безопасности](suspicious-activity-guide.md), чтобы научиться распознавать угрозы и потенциальные атаки.

### <a name="phase-3"></a>Этап 3

1. Интегрируйте оповещения [!INCLUDE [Product short](includes/product-short.md)] в рабочие процессы службы безопасности.

## <a name="see-also"></a>См. также:

- [Часто задаваемые вопросы по [!INCLUDE [Product short](includes/product-short.md)]](technical-faq.md)
- [Работа с оповещениями системы безопасности](working-with-suspicious-activities.md)
- [Посетите форум по [!INCLUDE [Product short](includes/product-short.md)].](https://aka.ms/MDIcommunity)
