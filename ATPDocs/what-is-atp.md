---
title: Что такое Azure Advanced Threat Protection (Azure ATP)? | Документация Майкрософт
description: Описание решения Azure Advanced Threat Protection (Azure ATP) и подозрительных действий, которые оно может обнаруживать
keywords: ''
author: mlottner
ms.author: mlottner
manager: mbaldwin
ms.date: 1/3/2019
ms.topic: article
ms.prod: ''
ms.service: azure-advanced-threat-protection
ms.technology: ''
ms.assetid: 2d14d0e9-1b03-4bcc-ae97-8fd41526ffc5
ms.reviewer: itargoet
ms.suite: ems
ms.openlocfilehash: 345b6285dbef34d0a72e789fc3d884214be4b79d
ms.sourcegitcommit: f37127601166216e57e56611f85dd783c291114c
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/24/2019
ms.locfileid: "54840951"
---
# <a name="what-is-azure-advanced-threat-protection"></a>Что такое Azure Advanced Threat Protection?
Azure Advanced Threat Protection (ATP) — это облачное решение для обеспечения безопасности, которое помогает обнаруживать и анализировать современные угрозы, направленные на вашу организацию, скомпрометированные удостоверения и действия внутренних нарушителей. Azure ATP позволяет аналитикам и специалистам службы безопасности, занимающимся выявлением современных угроз в гибридных средах, решать следующие задачи:  
- отслеживать пользователей, поведение сущностей и действия с помощью аналитики на основе обучения;  
- защищать удостоверения и учетные данные пользователей, хранящиеся в Active Directory;  
- выявлять и изучать подозрительные действия пользователей и современные атаки на основе модели цепочки атаки; 
- получать сведения об инцидентах в четко установленные сроки для быстрого рассмотрения. 
 
## <a name="monitor-and-profile-user-behavior-and-activities"></a>Отслеживание и профилирование поведения и действий пользователей  
Azure ATP отслеживает и анализирует действия пользователей в сети и информацию о них, такую как разрешения и членство в группах, формируя базовые показатели для каждого пользователя. Затем Azure ATP определяет аномалии с помощью встроенных адаптивных интеллектуальных функций, предоставляя вам информацию о подозрительных действиях и событиях и выявляя современные угрозы, скомпрометированные учетные записи и внутренние угрозы, направленные на организацию. Собственные датчики Azure ATP отслеживают контроллеры домена организации, что позволяет получать подробное представление всех действий пользователей на каждом устройстве. 
 
## <a name="protect-user-identities-and-reduce-the-attack-surface"></a>Защита удостоверений пользователей и сокращение уязвимой зоны   
Azure ATP предоставляет бесценную информацию о конфигурациях удостоверений и рекомендации по обеспечению безопасности. Благодаря отчетам о безопасности и аналитике пользовательских профилей Azure ATP помогает существенно сократить число направлений атак, угрожающих вашей организации, усложняя взлом учетных данных пользователей и затрудняя проведение атак. С помощью визуальных путей бокового смещения в Azure ATP можно быстро узнать, как злоумышленник может перемещаться по сети вашей организации с целью взлома важных учетных записей, и заранее предотвратить эти риски. Отчеты о безопасности Azure ATP помогают выявлять пользователей и устройства, которые проходят проверку подлинности с помощью открытых паролей. Они также предоставляют дополнительную информацию для оптимизации корпоративной защиты и ваших политик.  
 
## <a name="identify-suspicious-activities-and-advanced-attacks-across-the-cyber-attack-kill-chain"></a>Выявление подозрительных действий и современных кибератак на основе модели цепочки атаки 

Как правило, атаки изначально направлены на доступные объекты, например пользователей с низким уровнем прав, а затем быстро распространяются по горизонтали, пока злоумышленник не получит доступ к ценным ресурсам, например важным учетным записям, в том числе с правами администратора домена, или конфиденциальным данным. Azure ATP позволяет устанавливать источники таких современных угроз, прослеживая всю цепочку кибератаки. 

### <a name="reconnaissance"></a>Разведывательная атака 
Выявляйте попытки незаконных пользователей и злоумышленников получить информацию. Злоумышленники ищут сведения об именах пользователей, их членстве в группах, о назначенных устройствам IP-адресах, ресурсах, а также другую информацию самыми разными методами.  

### <a name="compromised-credentials"></a>Компрометация учетных данных.
Выявляйте попытки получить учетные данные пользователей, обнаруживая атаки методом подбора, неудачные попытки проверки подлинности, изменение членства пользователей в группах и другие подозрительные действия.  

### <a name="lateral-movements"></a>Боковое смещение
Определяйте попытки бокового смещения в вашей сети с целью получения контроля над важными учетными записями с использованием таких методов, как Pass-the-Ticket, Pass-the-Hash, Overpass-the-Hash и других.  

### <a name="domain-dominance"></a>Полное управление доменом
Azure ATP позволяет обнаруживать перехват контроля над доменом, полученный через удаленное выполнение кода на контроллере домена или такими методами, как DC Shadow, несанкционированная репликация контроллера домена и Golden Ticket.

## <a name="investigate-alerts-and-user-activities"></a>Изучайте оповещения и действия пользователей  
Azure ATP предоставляет только важные оповещения системы безопасности в режиме реального времени, что позволяет не отвлекаться на ненужную информацию. Представление временной шкалы атак Azure ATP позволяет сосредоточиться на том, что действительно имеет значение, и использовать интеллектуальные аналитические функции. Azure ATP позволяет быстро анализировать угрозы и получать информацию о пользователях, устройствах и сетевых ресурсах в масштабе всей организации. Тесная интеграция с ATP в Защитнике Windows обеспечивает дополнительный уровень безопасности благодаря обнаружению современных постоянных угроз в операционной системе и защите от них.  

## <a name="additional-resources-for-azure-atp"></a>Дополнительные ресурсы по Azure ATP  
### <a name="start-a-free-trial"></a>Запустите бесплатную пробную версию  
[https://signup.microsoft.com/Signup?OfferId=87dd2714-d452-48a0-a809-d2f58c4f68b7&ali=1](https://signup.microsoft.com/Signup?OfferId=87dd2714-d452-48a0-a809-d2f58c4f68b7&ali=1 "Enterprise Mobility + Security E5")
 
### <a name="follow-azure-atp-on-microsoft-tech-community"></a>Следите за Azure ATP в Microsoft Tech Community  
[https://techcommunity.microsoft.com/t5/Azure-Advanced-Threat-Protection/bd-p/AzureAdvancedThreatProtection](https://techcommunity.microsoft.com/t5/Azure-Advanced-Threat-Protection/bd-p/AzureAdvancedThreatProtection "Azure ATP в Microsoft Tech Community")
 
### <a name="join-the-azure-atp-yammer-community"></a>Присоединяйтесь к сообществу Yammer по Azure ATP 
[https://www.yammer.com/azureadvisors/#/threads/inGroup?type=in_group&feedId=9386893](https://www.yammer.com/azureadvisors/#/threads/inGroup?type=in_group&feedId=9386893 "Сообщество Yammer по Azure ATP")
 
### <a name="visit-the-azure-atp-product-page"></a>Посетите страницу продукта Azure ATP  
[https://azure.microsoft.com/features/azure-advanced-threat-protection/](https://azure.microsoft.com/features/azure-advanced-threat-protection/ "Страница продукта Azure ATP")

### <a name="learn-more-about-azure-atp-architecture"></a>Дополнительные сведения об архитектуре Azure ATP
 [Архитектура Azure ATP](atp-architecture.md)
 
## <a name="microsoft-ignite"></a>Microsoft Ignite
На Microsoft Ignite 2018 прошло несколько мероприятий, посвященных [Расширенной защите от угроз Azure](https://myignite.techcommunity.microsoft.com/sessions?q=Azure%2520Advanced%2520Threat%2520Protection&t=%257B%2522from%2522%253A%25222018-09-23T08%253A00%253A00-04%253A00%2522%252C%2522to%2522%253A%25222018-09-28T19%253A00%253A00-04%253A00%2522%257D). Если вы на них не были, рекомендуем посмотреть записи:

### <a name="azure-atp"></a>Azure ATP 
[BRK3117](https://myignite.techcommunity.microsoft.com/sessions/65780?source=sessions#ignite-html-anchor). Меры безопасности и устранение инцидентов с Azure ATP: [видео на YouTube](https://www.youtube.com/watch?v=QXZIfH0wP3Q)

### <a name="azure-atp-and-azure-ad-ip-active-directory-identity-protection"></a>Azure ATP и Защита идентификации Azure Active Directory
[BRK3237](https://myignite.techcommunity.microsoft.com/sessions/64523?source=sessions#ignite-html-anchor). Защита гибридной облачной среды с помощью Защиты идентификации Azure AD и Azure ATP: [видео на YouTube](https://www.youtube.com/watch?v=X7CXaok6GbM)

[BRK2157](https://myignite.techcommunity.microsoft.com/sessions/65776?source=sessions#ignite-html-anchor). Ускорение развертывания и внедрения решений Microsoft Information Protection: [видео на YouTube](https://www.youtube.com/watch?v=Foh-XDVbPog)

Сводку новостей об Azure ATP с мероприятия Ignite 2018 см. в записи блога [Azure Advanced Threat Protection Expands Integrations, Detections, and Forensic Capabilities](https://techcommunity.microsoft.com/t5/Enterprise-Mobility-Security/Azure-Advanced-Threat-Protection-Expands-Integrations-Detections/ba-p/262409) (Расширенная защита от угроз Azure получает новые возможности интеграции, обнаружения и анализа).

## <a name="whats-next"></a>Дальнейшие действия 

Развертывать Azure ATP рекомендуется в три этапа:  

### <a name="phase-1"></a>Этап 1

1. Настройте в Azure ATP защиту основных сред. Модель быстрого развертывания Azure ATP позволяет немедленно защитить организацию. [Установка Azure ATP](install-atp-step1.md)  
2. Настройте [конфиденциальные учетные записи](sensitive-accounts.md) и [учетные записи honeytoken](install-atp-step7.md).
3. Просматривайте отчеты и [пути бокового смещения](use-case-lateral-movement-path.md).  


### <a name="phase-2"></a>Этап 2

1. Защитите все контроллеры домена и [леса](atp-multi-forest.md) в вашей организации.  
2.  Отслеживайте все [оповещения](working-with-suspicious-activities.md) — изучайте оповещения о боковом смещении и перехвате контроля над доменом.  
3. Обратитесь к [руководству по оповещениям системы безопасности](suspicious-activity-guide.md), чтобы научиться распознавать угрозы и потенциальные атаки.


### <a name="phase-3"></a>Этап 3

1. Интегрируйте оповещения Azure ATP в рабочие процессы службы безопасности.

## <a name="see-also"></a>См. также
- [Часто задаваемые вопросы об Azure ATP](atp-technical-faq.md)
- [Работа с оповещениями системы безопасности](working-with-suspicious-activities.md)
- [Загляните на форум Azure ATP!](https://aka.ms/azureatpcommunity)
