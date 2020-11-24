---
title: Архитектура Microsoft Defender для удостоверений
description: Описание архитектуры Microsoft Defender для удостоверений
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 10/26/2020
ms.topic: overview
ms.collection: M365-security-compliance
ms.service: azure-advanced-threat-protection
ms.reviewer: itargoet
ms.suite: ems
ms.openlocfilehash: cb67a36402c0b6b193fbd5ee11b63113714cd885
ms.sourcegitcommit: e2227c0b0e5aaa5163dc56d4131ca82f8dca8fb0
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/18/2020
ms.locfileid: "94848811"
---
# <a name="microsoft-defender-for-identity-architecture"></a>Архитектура Microsoft Defender для удостоверений

[!INCLUDE [Product long](includes/product-long.md)] отслеживает контроллеры домена, регистрируя и анализируя сетевой трафик, а также используя события Windows (которые пересылаются непосредственно из контроллеров домена) и анализируя данные, связанные с атаками и угрозами. С помощью профилирования, детерминированного обнаружения и алгоритмов машинного обучения и анализа поведения [!INCLUDE [Product short](includes/product-short.md)] получает сведения о сети, выявляет аномалии и сообщает о подозрительных действиях.

Архитектура [!INCLUDE [Product short](includes/product-short.md)]:

![[!INCLUDE [Product short](includes/product-short.md)]: схема топологии архитектуры](media/architecture-topology.png)

В этом разделе рассматривается поток операций отслеживания сетевого трафика и событий, а также подробно описаны функции основных компонентов [!INCLUDE [Product short](includes/product-short.md)]: портала [!INCLUDE [Product short](includes/product-short.md)], датчика [!INCLUDE [Product short](includes/product-short.md)] и облачной службы [!INCLUDE [Product short](includes/product-short.md)].

При установке непосредственно на контроллерах домена датчик [!INCLUDE [Product short](includes/product-short.md)] обращается к требуемым журналам событий напрямую из контроллера домена. После того как датчик проанализирует журналы и сетевой трафик, [!INCLUDE [Product short](includes/product-short.md)] отправит в облачную службу [!INCLUDE [Product short](includes/product-short.md)] только проанализированные данные (некоторую часть всех журналов).

## <a name="product-short-components"></a>составные части компонента [!INCLUDE [Product short](includes/product-short.md)].

[!INCLUDE [Product short](includes/product-short.md)] включает в себя следующие компоненты.

- **Портал [!INCLUDE [Product short](includes/product-short.md)]**  
На портале [!INCLUDE [Product short](includes/product-short.md)] можно создать экземпляр [!INCLUDE [Product short](includes/product-short.md)], просматривать данные, полученные от датчиков [!INCLUDE [Product short](includes/product-short.md)], а также отслеживать, контролировать и изучать угрозы в сетевой среде.

- **Датчик [!INCLUDE [Product short](includes/product-short.md)]**  
Датчики [!INCLUDE [Product short](includes/product-short.md)] устанавливаются непосредственно на контроллерах домена. Датчик напрямую отслеживает трафик контроллера домена. Для этого не нужен выделенный сервер и не требуется настраивать зеркальное отображение портов.
- **Облачная служба [!INCLUDE [Product short](includes/product-short.md)]**  
Облачная служба [!INCLUDE [Product short](includes/product-short.md)] работает на основе инфраструктуры Azure. В настоящее время она развернута в США, Европе и Азии. Облачная служба [!INCLUDE [Product short](includes/product-short.md)] подключена к Microsoft Intelligent Security Graph.

## <a name="product-short-portal"></a>Портал [!INCLUDE [Product short](includes/product-short.md)]

Портал [!INCLUDE [Product short](includes/product-short.md)] позволяет выполнять следующие действия:

- создание экземпляра [!INCLUDE [Product short](includes/product-short.md)];
- выполнять интеграцию с другими службами безопасности Майкрософт.
- управление параметрами конфигурации датчика [!INCLUDE [Product short](includes/product-short.md)];
- просмотр данных, полученных от датчиков [!INCLUDE [Product short](includes/product-short.md)];
- отслеживание обнаруженных подозрительных действий и предположительных атак на основе модели цепочки атаки.
- **Необязательно**: портал можно также настроить для отправки сообщений электронной почты и событий при обнаружении проблем, связанных с безопасностью или работоспособностью.

> [!NOTE]
> Если в вашем экземпляре [!INCLUDE [Product short](includes/product-short.md)] в течение 60 дней не будет установлен датчик, экземпляр может быть удален и вам потребуется создать его заново.

## <a name="product-short-sensor"></a>Датчик [!INCLUDE [Product short](includes/product-short.md)]

Датчик [!INCLUDE [Product short](includes/product-short.md)] обеспечивает следующие основные возможности:

- фиксация и проверка сетевого трафика контроллеров домена (локального трафика);
- получение событий Windows непосредственно из контроллеров домена;
- получение сведений об учете RADIUS от поставщика VPN;
- получение данных о пользователях и компьютерах из домена Active Directory;
- разрешение сетевых сущностей (пользователей, групп и компьютеров);
- передача соответствующих данных в облачную службу [!INCLUDE [Product short](includes/product-short.md)].

## <a name="product-short-sensor-features"></a>Функции датчика [!INCLUDE [Product short](includes/product-short.md)]

Датчик [!INCLUDE [Product short](includes/product-short.md)] считывает события локально. Для этого не нужно приобретать и обслуживать дополнительное оборудование или производить настройку. Датчик [!INCLUDE [Product short](includes/product-short.md)] также поддерживает трассировку событий Windows (ETW), которая позволяет получить сведения журнала для нескольких обнаружений. Обнаружения на основе трассировки событий Windows включают предполагаемую атаку DCShadow путем запроса на репликацию контроллера домена и повышения роли контроллера домена.

### <a name="domain-synchronizer-process"></a>Процесс назначения синхронизатора домена

Процесс назначения синхронизатора домена отвечает за своевременную синхронизацию всех сущностей из определенного домена Active Directory (аналогичный механизм используется самими контроллерами домена для репликации). Один датчик автоматически выбирается случайным образом из всех доступных датчиков и используется в качестве синхронизатора домена.

Если синхронизатор более 30 минут отключен, вместо него автоматически выбирается другой датчик.

### <a name="resource-limitations"></a>Ограничения ресурсов

Датчик [!INCLUDE [Product short](includes/product-short.md)] содержит компонент мониторинга, который оценивает доступный объем вычислительных ресурсов и памяти на контроллере домена, в котором он выполняется. Мониторинг выполняется каждые 10 секунд. При этом также осуществляется динамическое обновление квоты использования ресурсов ЦП и памяти для датчика [!INCLUDE [Product short](includes/product-short.md)]. Благодаря этому в любой момент времени в контроллере домена доступно по крайней мере 15 % свободных вычислительных ресурсов и ресурсов памяти.

Независимо от операций, выполняемых в контроллере домена, в результате всегда освобождаются ресурсы, чтобы обеспечить непрерывную работу основных функций контроллера домена.

Если процесс мониторинга приводит к нехватке ресурсов датчика [!INCLUDE [Product short](includes/product-short.md)], отслеживается только часть трафика, а на странице работоспособности на портале [!INCLUDE [Product short](includes/product-short.md)] появляется оповещение о работоспособности "Сетевой трафик зеркально отображенных портов сброшен".

### <a name="windows-events"></a>События Windows

Чтобы расширить охват [!INCLUDE [Product short](includes/product-short.md)] для обнаружения угроз, связанных с аутентификацией NTLM, изменений в привилегированных группах и создания подозрительных служб, службе [!INCLUDE [Product short](includes/product-short.md)] необходимо проанализировать журналы со следующими событиями Windows: 4776,4732,4733,4728,4729,4756,4757,7045 и 8004. Эти события автоматически считываются датчиками [!INCLUDE [Product short](includes/product-short.md)], в которых [расширенная политика аудита](configure-windows-event-collection.md) настроена надлежащим образом. Чтобы [обеспечить аудит события Windows 8004](configure-windows-event-collection.md#ntlm-authentication-using-windows-event-8004) в соответствии с требованиями службы, проверьте [параметры аудита NTLM](/archive/blogs/askds/ntlm-blocking-and-you-application-analysis-and-auditing-methodologies-in-windows-7).

## <a name="next-steps"></a>Следующие шаги

- [Предварительные требования для работы с [!INCLUDE [Product short](includes/product-short.md)]](prerequisites.md)
- [Средство определения размера [!INCLUDE [Product short](includes/product-short.md)]](https://aka.ms/trisizingtool)
- [Планирование ресурсов [!INCLUDE [Product short](includes/product-short.md)]](capacity-planning.md)
- [Настройка пересылки событий](configure-event-forwarding.md)
- [Настройка пересылки событий Windows](configure-event-forwarding.md)
- [Посетите форум по [!INCLUDE [Product short](includes/product-short.md)].](https://aka.ms/MDIcommunity)
