---
title: Архитектура Azure Advanced Threat Protection | Документы Майкрософт
description: В этой статье описывается архитектура Azure Advanced Threat Protection (ATP).
keywords: ''
author: mlottner
ms.author: mlottner
manager: mbaldwin
ms.date: 1/27/2019
ms.topic: article
ms.prod: ''
ms.service: azure-advanced-threat-protection
ms.technology: ''
ms.assetid: 90f68f2c-d421-4339-8e49-1888b84416e6
ms.reviewer: itargoet
ms.suite: ems
ms.openlocfilehash: 6988b41b64dc3d8afef5f7af614f78b41501e2af
ms.sourcegitcommit: 19ff0ed88e450506b5725bbcbb0d0bd2f0c5e4bb
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/27/2019
ms.locfileid: "55085322"
---
# <a name="azure-atp-architecture"></a>Архитектура Azure ATP

Azure ATP отслеживает контроллеры домена, регистрируя и анализируя сетевой трафик, а также используя события Windows (которые пересылаются непосредственно из контроллеров домена) и анализируя данные, связанные с атаками и угрозами. С помощью профилирования, детерминированного обнаружения и алгоритмов машинного обучения и анализа поведения Azure ATP получает сведения о сети, выявляет аномалии и сообщает о подозрительных действиях.

Архитектура "Расширенная защита SQL от угроз":

![Схема топологии архитектуры Azure ATP](media/atp-architecture-topology.png)

В этом разделе рассматривается процесс фиксации сетевого трафика и событий, а также подробно описаны функции основных компонентов Azure ATP: портала Azure ATP, датчика Azure ATP и облачной службы Azure ATP. 

При установке непосредственно на контроллерах домена датчик Azure ATP обращается к требуемым журналам событий напрямую из контроллера домена. После того как датчик проанализирует журналы и сетевой трафик, Azure ATP отправит в облачную службу Azure ATP только проанализированные данные (некоторую часть всех журналов). 

## <a name="azure-atp-components"></a>Компоненты Azure ATP
Azure ATP включает в себя следующие компоненты.

-   **Портал Azure ATP** <br>
На портале Azure ATP можно создать экземпляр Azure ATP, просматривать данные, полученные от датчиков Azure ATP, а также отслеживать, контролировать и изучать угрозы в сетевой среде.  
-   **Датчик Azure ATP**<br>
Датчики Azure ATP устанавливаются непосредственно на контроллерах домена. Датчик напрямую отслеживает трафик контроллера домена. Для этого не нужен выделенный сервер и не требуется настраивать зеркальное отображение портов.

-   **Облачная служба Azure ATP**<br>
Облачная служба Azure ATP работает на основе инфраструктуры Azure. В настоящее время она развернута в США, Европе и Азии. Облачная служба Azure ATP подключена к Microsoft Intelligent Security Graph. 

## <a name="azure-atp-portal"></a>Портал Azure ATP 
Портал Azure ATP служит для выполнения следующих задач:
- создание экземпляра Azure ATP;
- выполнять интеграцию с другими службами безопасности Майкрософт. 
- управление параметрами конфигурации датчика Azure ATP; 
- просмотр данных, полученных от датчиков Azure ATP;
- отслеживание обнаруженных подозрительных действий и предположительных атак на основе модели цепочки атаки.
- **Необязательно**: портал можно также настроить для отправки сообщений электронной почты и событий при обнаружении проблем, связанных с безопасностью или работоспособностью.

> [!NOTE]
> - Если в вашем экземпляре Azure ATP в течение 60 дней не будет установлен датчик, экземпляр может быть удален и вам потребуется создать его заново.

## <a name="azure-atp-sensor"></a>Датчик Azure ATP
Датчик Azure ATP обеспечивает следующие основные возможности:
- фиксация и проверка сетевого трафика контроллеров домена (локального трафика);
- получение событий Windows непосредственно из контроллеров домена; 
- получение сведений об учете RADIUS от поставщика VPN;
- получение данных о пользователях и компьютерах из домена Active Directory;
- разрешение сетевых сущностей (пользователей, групп и компьютеров);
- передача соответствующих данных в облачную службу Azure ATP;

 
## <a name="azure-atp-sensor-features"></a>Функции датчика Azure ATP
Датчик Azure ATP считывает события локально. Для этого не нужно приобретать и обслуживать дополнительное оборудование или производить настройку. Датчик Azure ATP также поддерживает трассировку событий Windows (ETW), которая позволяет получить сведения журнала для нескольких обнаружений. Обнаружения на основе трассировки событий Windows включают предполагаемую атаку DCShadow путем запроса на репликацию контроллера домена и повышения роли контроллера домена.

### <a name="domain-synchronizer-candidate"></a>Синхронизатор домена-кандидат

    The domain synchronizer candidate is responsible for synchronizing all entities from a specific Active Directory domain proactively (similar to the mechanism used by the domain controllers themselves for replication). One sensor is chosen randomly, from the list of candidates, to serve as the domain synchronizer. 

    If the synchronizer is offline for more than 30 minutes, another candidate is chosen instead. If there is no domain synchronizer available for a specific domain, Azure ATP proactively synchronizes entities and their changes, however Azure ATP retrieves new entities as they are detected in the monitored traffic. 
    
    If there is no domain synchronizer available, and you search for an entity that did not have any traffic related to it, no search results are displayed.

    By default, Azure ATP sensors are not synchronizer candidates. To manually set an Azure ATP sensor as a domain synchronizer candidate, follow the steps in the [Azure ATP installation workflow](install-atp-step5.md#configure-azure-atp-sensor-settings).

### <a name="resource-limitations"></a>Ограничения ресурсов

    The Azure ATP sensor includes a monitoring component that evaluates the available compute and memory capacity on the domain controller on which it is running. The monitoring process runs every 10 seconds and dynamically updates the CPU and memory utilization quota on the Azure ATP sensor process. The monitoring process makes sure the domain controller always has at least 15% of free compute and memory resources available.

    No matter what occurs on the domain controller, the monitoring process continually frees up resources to make sure the domain controller's core functionality is never affected.

    If the monitoring process causes the Azure ATP sensor to run out of resources, only partial traffic is monitored and the monitoring alert "Dropped port mirrored network traffic" appears in the Azure ATP portal Health page.

### <a name="windows-events"></a>События Windows

    To enhance Azure ATP detection coverage of suspected identity theft (pass-the-hash), suspicious authentication failures,modifications to sensitive groups, creation of suspicious services, and Honeytoken activity types of attack, Azure ATP needs to analyze the logs of the following Windows events: 4776,4732,4733,4728,4729,4756,4757, and 7045. These events are read automatically by Azure ATP sensors with correct [advanced audit policy settings](atp-advanced-audit-policy.md). 

## <a name="see-also"></a>См. также
- [Предварительные требования к Azure ATP](atp-prerequisites.md)
- [Средство изменения размера Azure ATP](http://aka.ms/trisizingtool)
- [Планирование производительности Azure ATP](atp-capacity-planning.md)
- [Настройка пересылки событий](configure-event-forwarding.md)
- [Настройка пересылки событий Windows](configure-event-forwarding.md)
- [Загляните на форум Azure ATP!](https://aka.ms/azureatpcommunity)
