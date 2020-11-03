---
title: Часто задаваемые вопросы об удостоверении защитника Майкрософт
description: Содержит список часто задаваемых вопросов о Microsoft Defender для идентификации и соответствующих ответах.
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 10/27/2020
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.service: azure-advanced-threat-protection
ms.reviewer: itargoet
ms.suite: ems
ms.openlocfilehash: ccb3ee9afe32615246f8e6dc63e181475094a8b7
ms.sourcegitcommit: f434dbff577d9944df18ca7533d026acdab0bb42
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/03/2020
ms.locfileid: "93274378"
---
# <a name="product-long-frequently-asked-questions"></a>[!INCLUDE [Product long](includes/product-long.md)] часто задаваемые вопросы

[!INCLUDE [Rebranding notice](includes/rebranding.md)]

В этой статье содержится список часто задаваемых вопросов и ответов на [!INCLUDE [Product long](includes/product-long.md)] следующие категории:

- [Что такое [!INCLUDE [Product short](includes/product-short.md)]](#what-is-azure-atp)
- [Лицензирование и конфиденциальность](#licensing-and-privacy)
- [Развертывание](#deployment)
- [Операции](#operation)
- [Устранение неполадок](#troubleshooting)

<a name="what-is-azure-atp"></a>

## <a name="what-is-product-short"></a>Что такое [!INCLUDE [Product short](includes/product-short.md)]?

### <a name="what-can-product-short-detect"></a>Что может [!INCLUDE [Product short](includes/product-short.md)] обнаружить?

[!INCLUDE [Product short](includes/product-short.md)] обнаруживает известные вредоносные атаки и методы, проблемы безопасности и риски, связанные с сетью.
Полный список [!INCLUDE [Product short](includes/product-short.md)] обнаружений см. в статье [что такое обнаружение [!INCLUDE [Product short](includes/product-short.md)] выполняется?](suspicious-activity-guide.md).

### <a name="what-data-does-product-short-collect"></a>Какие данные [!INCLUDE [Product short](includes/product-short.md)] собираются?

[!INCLUDE [Product short](includes/product-short.md)] собирает и сохраняет сведения из настроенных серверов (контроллеров домена, рядовых серверов и т. д.) в базе данных, относящейся к службе для администрирования, отслеживания и создания отчетов. Собираются такие данные, как входящий и исходящий сетевой трафик контроллеров домена (например, проверка подлинности Kerberos, проверка подлинности NTLM, запросы DNS), журналы безопасности (например, события безопасности Windows), сведения об Active Directory (структура, подсети, сайты) и сведения о сущностях (например, имена, адреса электронной почты и номера телефонов).

Корпорация Майкрософт использует эти сведения в следующих целях:

- заблаговременное определение индикаторов атак (IOA) в организации;
- создание оповещений в случае обнаружения возможной атаки;
- выполнение операций безопасности с предоставлением сведений о сущностях, связанных с сигналами об угрозах из локальной сети, что позволяет анализировать и изучать угрозы безопасности в сети.

Корпорация Майкрософт не выполняет интеллектуальный анализ данных для рекламы или в любых других целях, отличных от предоставления вам службы.

### <a name="how-many-directory-service-credentials-does-product-short-support"></a>Сколько учетных данных службы каталогов [!INCLUDE [Product short](includes/product-short.md)] поддерживает?

[!INCLUDE [Product short](includes/product-short.md)] в настоящее время поддерживает добавление до 10 разных учетных данных службы каталогов для поддержки Active Directory сред с недоверенными лесами. Если вам нужны дополнительные учетные записи, отправьте запрос в службу поддержки.

### <a name="does-product-short-only-leverage-traffic-from-active-directory"></a>[!INCLUDE [Product short](includes/product-short.md)]Использует ли трафик только Active Directory?

Помимо анализа трафика Active Directory с помощью технологии глубокой проверки пакетов, [!INCLUDE [Product short](includes/product-short.md)] также собирает соответствующие события Windows из контроллера домена и создает профили сущностей на основе информации из домен Active Directory служб. [!INCLUDE [Product short](includes/product-short.md)] также поддерживает получение RADIUS-учета журналов VPN от различных поставщиков (Microsoft, Cisco, F5 и Checkpoint).

### <a name="does-product-short-monitor-only-domain-joined-devices"></a>Выполняет ли [!INCLUDE [Product short](includes/product-short.md)] мониторинг только присоединенных к домену устройств?

Нет. [!INCLUDE [Product short](includes/product-short.md)] отслеживает все устройства в сети, выполняющие запросы проверки подлинности и авторизации, к Active Directory, включая устройства, отличные от Windows и мобильные.

### <a name="does-product-short-monitor-computer-accounts-as-well-as-user-accounts"></a>[!INCLUDE [Product short](includes/product-short.md)]Отслеживает ли учетные записи компьютеров и учетные записи пользователей?

Да. Так как учетные записи компьютеров (а также любые другие сущности) можно использовать для выполнения вредоносных действий, [!INCLUDE [Product short](includes/product-short.md)] следит за работой всех учетных записей компьютеров и всеми другими сущностями в среде.

### <a name="what-is-the-difference-between-advanced-threat-analytics-ata-and-product-short"></a>В чем разница между Advanced Threat Analytics (ATA) и [!INCLUDE [Product short](includes/product-short.md)] ?

ATA — это автономное локальное решение, включающее несколько компонентов, например, центр ATA, для которого требуется специальное оборудование в локальной среде.

[!INCLUDE [Product short](includes/product-short.md)] — это облачное решение для обеспечения безопасности, которое использует локальные сигналы Active Directory (Azure AD). Решение обладает высокой степенью масштабируемости и часто обновляется.

Окончательная версия ATA доступна в [целом](https://support.microsoft.com/help/4568997/update-3-for-microsoft-advanced-threat-analytics-1-9). Поддержка ATA будет завершаться 12 января 2021. Расширенная поддержка будет продолжена до 2026 января. Дополнительные сведения см. в [нашем блоге](https://techcommunity.microsoft.com/t5/microsoft-security-and/end-of-mainstream-support-for-advanced-threat-analytics-january/ba-p/1539181).

В отличие от датчика ATA, [!INCLUDE [Product short](includes/product-short.md)] датчик также использует источники данных, такие как трассировка событий для Windows (ETW), позволяющие [!INCLUDE [Product short](includes/product-short.md)] доставлять дополнительные обнаружения.

[!INCLUDE [Product short](includes/product-short.md)]к частым обновлениям относятся следующие функции и возможности.

- **Поддержка [сред с несколькими лесами](multi-forest.md)** : Обеспечивает видимость организаций в разных лесах AD.

- **[Оценки состояния безопасности удостоверений](isp-overview.md)** : Определяет распространенные ошибки в конфигурации и компоненты, подверженные злонамеренному использованию, а также предоставляет пути исправления для сокращения направлений атак.

- **[Возможности UEBA](/cloud-app-security/tutorial-ueba)** : Получение ценных сведений о рисках для отдельных пользователей благодаря оценке приоритета исследования для пользователей. Оценка может помочь специалистам по безопасности (SecOps) в проведении исследований, а также может помочь аналитикам в анализе необычных действий для пользователя и организации.

- **Встроенная интеграция** : Интеграция с Microsoft Cloud App Security и Защитой идентификации Azure AD для получения гибридного представления событий, происходящих как в локальных, так и в гибридных средах.

- **Участие в защитнике Microsoft 365** : вносит данные оповещений и угроз в Microsoft 365 Defender. Защитник Microsoft 365 использует портфолио безопасности Microsoft 365 (удостоверения, конечные точки, данные и приложения) для автоматического анализа данных об угрозах между доменами, создание полной картины каждой атаки на одной панели мониторинга. Благодаря этой простоте, средства защиты могут сосредоточиться на критически важных угрозах и поиске сложных нарушений, а также доверять Microsoft 365 мощной автоматизации защитника, в любом месте в цепочке уничтожения и возвращающей организацию в безопасном состоянии.

## <a name="licensing-and-privacy"></a>Лицензирование и конфиденциальность

### <a name="where-can-i-get-a-license-for-product-long"></a>Где можно получить лицензию [!INCLUDE [Product long](includes/product-long.md)] ?

[!INCLUDE [Product short](includes/product-short.md)] доступен в составе Enterprise Mobility + Security 5 Suite (EMS, и в качестве автономной лицензии). Вы можете приобрести лицензию непосредственно на [портале Microsoft 365](https://www.microsoft.com/cloud-platform/enterprise-mobility-security-pricing) или по модели лицензирования Cloud Solution Partner (партнер по облачным решениям, CSP).

### <a name="does-product-short-need-only-a-single-license-or-does-it-require-a-license-for-every-user-i-want-to-protect"></a>Требуется ли [!INCLUDE [Product short](includes/product-short.md)] только одна лицензия или требуется лицензия для каждого пользователя, которого требуется защитить?

Сведения о [!INCLUDE [Product short](includes/product-short.md)] требованиях к лицензированию см. в разделе [ [!INCLUDE [Product short](includes/product-short.md)] руководство по лицензированию](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance#azure-advanced-threat-protection).

### <a name="is-my-data-isolated-from-other-customer-data"></a>Мои данные изолированы от данных других клиентов?

Да, ваши данные изолированы посредством проверки подлинности для доступа и логического разделения на основе идентификаторов клиента. Каждый клиент имеет доступ только к данным, собранным в его организации, а также к универсальным данным, предоставляемым корпорацией Майкрософт.

### <a name="do-i-have-the-flexibility-to-select-where-to-store-my-data"></a>Можно ли выбирать расположения для хранения данных?

Нет. При [!INCLUDE [Product short](includes/product-short.md)] создании экземпляра он автоматически хранится в стране, ближайшей к географическому расположению клиента AAD. [!INCLUDE [Product short](includes/product-short.md)] невозможно переместить данные после [!INCLUDE [Product short](includes/product-short.md)] создания экземпляра в другой центр обработки данных.

### <a name="how-does-microsoft-prevent-malicious-insider-activities-and-abuse-of-high-privilege-roles"></a>Каким образом корпорация Майкрософт препятствует выполнению злоумышленных действий внутри организации и злоупотреблению привилегированными ролями?

Изначально разработчикам и администраторам Майкрософт предоставлены полномочия, необходимые для выполнения возложенных на них обязанностей по эксплуатации и развитию этой службы. Корпорация Майкрософт создала комплекс средств управления с поддержкой профилактических, аналитических и противодействующих механизмов защиты от неправомочных действий разработчиков и администраторов:

- жесткий контроль доступа к конфиденциальным данным;
- сочетание средств управления, расширяющих независимое обнаружение вредоносной активности;
- несколько уровней мониторинга, ведения журнала и формирования отчетности.

Кроме того, корпорация Майкрософт регулярно проводит проверку квалификации персонала и по результатам проверки ограничивает доступ персонала к приложениям, системам и сетевой инфраструктуре. Процесс получения доступа к учетной записи клиента или сопутствующей информации формализован и инициируется только по запросу клиента.

## <a name="deployment"></a>Deployment (Развертывание)

### <a name="how-many-product-short-sensors-do-i-need"></a>Сколько [!INCLUDE [Product short](includes/product-short.md)] нужно датчиков?

Каждый контроллер домена в среде должен быть охвачен [!INCLUDE [Product short](includes/product-short.md)] датчиком или автономным датчиком. Дополнительные сведения см. в разделе [ [!INCLUDE [Product short](includes/product-short.md)] изменение размера датчика](capacity-planning.md#sizing).

### <a name="does-product-short-work-with-encrypted-traffic"></a>[!INCLUDE [Product short](includes/product-short.md)]Работает с зашифрованным трафиком?

Сетевые протоколы с зашифрованным трафиком (например AtSvc и WMI) не расшифровываются, но анализируются датчиками.

### <a name="does-product-short-work-with-kerberos-armoring"></a>Работает ли служба [!INCLUDE [Product short](includes/product-short.md)] защиты Kerberos?

Включение защиты Kerberos, также известное как гибкое безопасное туннелирование с проверкой подлинности (FAST), поддерживается [!INCLUDE [Product short](includes/product-short.md)] , за исключением того, что обнаружение хэша не работает с защитой Kerberos.

### <a name="how-do-i-monitor-a-virtual-domain-controller-using-product-short"></a>Разделы справки отслеживать виртуальный контроллер домена с помощью [!INCLUDE [Product short](includes/product-short.md)] ?

Для большинства виртуальных контроллеров домена можно использовать [!INCLUDE [Product short](includes/product-short.md)] датчик, чтобы определить, подходит ли [!INCLUDE [Product short](includes/product-short.md)] датчик для вашей среды, в разделе [ [!INCLUDE [Product short](includes/product-short.md)] планирование ресурсов](capacity-planning.md).

Если датчик не может быть охвачен виртуальным контроллером домена [!INCLUDE [Product short](includes/product-short.md)] , можно использовать как виртуальный, так и физический [!INCLUDE [Product short](includes/product-short.md)] датчик, как описано в разделе [Настройка зеркального отображения портов](configure-port-mirroring.md).  
Самый простой способ — установить виртуальный [!INCLUDE [Product short](includes/product-short.md)] Автономный датчик на каждом узле, где существует виртуальный контроллер домена.  
Если виртуальные контроллеры домена перемещаются между узлами, необходимо выполнить один из следующих шагов:

- Когда виртуальный контроллер домена перемещается на другой узел, необходимо предварительно настроить [!INCLUDE [Product short](includes/product-short.md)] Автономный датчик на этом узле для получения трафика от недавно перемещенного виртуального контроллера домена.
- Убедитесь, что виртуальный [!INCLUDE [Product short](includes/product-short.md)] изолированный датчик присоединен к виртуальному контроллеру домена, чтобы при его перемещении [!INCLUDE [Product short](includes/product-short.md)] перемещается автономный датчик.
- Используйте виртуальные коммутаторы, которые могут отправлять трафик между узлами.

### <a name="how-do-i-configure-the-product-short-sensors-to-communicate-with-product-short-cloud-service-when-i-have-a-proxy"></a>Разделы справки настроить [!INCLUDE [Product short](includes/product-short.md)] датчики для связи с [!INCLUDE [Product short](includes/product-short.md)] облачной службой, если у меня есть прокси-сервер?

Чтобы контроллеры домена могли обмениваться данными с облачной службой, откройте порт 443 *.atp.azure.com в брандмауэре или на прокси-сервере. Инструкции по выполнению этой задачи см. в разделе [Настройка прокси-сервера или брандмауэра для подключения к [!INCLUDE [Product short](includes/product-short.md)] датчикам](configure-proxy.md).

### <a name="can-product-short-monitored-domain-controllers-be-virtualized-on-your-iaas-solution"></a>Можно [!INCLUDE [Product short](includes/product-short.md)] ли виртуализованные контроллеры домена в решении IaaS?

Да, можно использовать [!INCLUDE [Product short](includes/product-short.md)] датчик для мониторинга контроллеров домена, которые находятся в любом решении IaaS.

### <a name="can-product-short-support-multi-domain-and-multi-forest"></a>Может [!INCLUDE [Product short](includes/product-short.md)] поддерживать несколько доменов и несколько лесов?

[!INCLUDE [Product short](includes/product-short.md)] поддерживает многодоменные среды и несколько лесов. Дополнительные сведения и требования безопасности см. в описании [поддержки множества лесов](multi-forest.md).

### <a name="can-you-see-the-overall-health-of-the-deployment"></a>Можно ли проверить общую работоспособность развертывания?

Да, вы можете просмотреть общую работоспособность развертывания, а также конкретные проблемы, связанные с конфигурацией, подключением и т. д., и вы получаете оповещения о том, что они возникают с [!INCLUDE [Product short](includes/product-short.md)] оповещениями о работоспособности.

## <a name="operation"></a>Операция

### <a name="what-kind-of-integration-does-product-short-have-with-siems"></a>Какой тип интеграции [!INCLUDE [Product short](includes/product-short.md)] имеет решения Siem?

[!INCLUDE [Product short](includes/product-short.md)] можно настроить для отправки оповещений syslog на любой сервер SIEM, использующий формат CEF, для оповещений о работоспособности и при обнаружении предупреждения системы безопасности. Дополнительные сведения см. в [справочнике по журналу SIEM](cef-format-sa.md).

### <a name="why-are-certain-accounts-considered-sensitive"></a>Почему некоторые учетные записи рассматриваются как конфиденциальные?

Такие учетные записи могут быть у участников групп, которые считаются конфиденциальными (например, у участников группы администраторов домена).

Чтобы понять, почему учетная запись конфиденциальная, нужно просмотреть, к каким конфиденциальным группам она относится. Группы, к которым она принадлежит, также могут быть конфиденциальными из-за другой группы, поэтому необходимо обнаружить группу с самым высоким уровнем конфиденциальности. Можно также вручную [пометить учетные записи как конфиденциальные](sensitive-accounts.md).

### <a name="do-you-have-to-write-your-own-rules-and-create-a-thresholdbaseline"></a>Нужно ли писать собственные правила и определять ограничения или базовые показатели?

В [!INCLUDE [Product short](includes/product-short.md)] нет необходимости создавать правила, пороговые значения или базовые показатели, а затем выполнять тонкую настройку. [!INCLUDE [Product short](includes/product-short.md)] анализирует поведение пользователей, устройств и ресурсов, а также их связь друг с другом и может быстро обнаруживать подозрительные действия и известные атаки. Через три недели после развертывания [!INCLUDE [Product short](includes/product-short.md)] начинается обнаружение подозрительных действий в поведении. С другой стороны, [!INCLUDE [Product short](includes/product-short.md)] начнет обнаружение известных вредоносных атак и проблем безопасности сразу после развертывания.

### <a name="which-traffic-does-product-short-generate-in-the-network-from-domain-controllers-and-why"></a>Какой трафик [!INCLUDE [Product short](includes/product-short.md)] создается в сети с контроллеров домена и почему?

[!INCLUDE [Product short](includes/product-short.md)] создает трафик от контроллеров домена к компьютерам организации в одном из трех сценариев:

1. **Разрешение сетевых имен**  
[!INCLUDE [Product short](includes/product-short.md)] захватывает трафик и события, изучая и профилирование пользователей и действий компьютеров в сети. Для изучения и профилирования действий в соответствии с компьютерами Организации необходимо [!INCLUDE [Product short](includes/product-short.md)] Разрешить IP-адреса учетным записям компьютеров. Чтобы разрешить IP-адреса для [!INCLUDE [Product short](includes/product-short.md)] датчиков имен компьютеров, запросите IP-адрес для имени компьютера, *за* которым он расположен.

    Запросы выполняются одним из четырех методов:
    - NTLM через RPC (TCP-порт 135)
    - NetBIOS (UDP-порт 137)
    - RDP (TCP-порт 3389)
    - Запросы к DNS-серверу с помощью обратного поиска IP-адреса в DNS (UDP 53).

    После получения имени компьютера  [!INCLUDE [Product short](includes/product-short.md)] датчики перекрестно проверяют сведения в Active Directory, чтобы узнать, существует ли объект компьютера с тем же именем компьютера. Если соответствие найдено, устанавливается связь между IP-адресом и соответствующим объектом-компьютером.
2. **Путь бокового смещения (LMP)**  
Для создания потенциальных Лмпс для конфиденциальных пользователей [!INCLUDE [Product short](includes/product-short.md)] требуются сведения о локальных администраторах на компьютерах. В этом сценарии [!INCLUDE [Product short](includes/product-short.md)] датчик использует SAM-R (TCP 445) для запроса IP-адреса, указанного в сетевом трафике, для определения локальных администраторов компьютера. Дополнительные сведения о [!INCLUDE [Product short](includes/product-short.md)] и SAM-r см. в статье [Настройка необходимых разрешений для Sam-r](install-step8-samr.md).

3. **Запрос Active Directory с помощью LDAP** для данных сущности  
[!INCLUDE [Product short](includes/product-short.md)] датчики запрашивают контроллер домена из домена, к которому принадлежит сущность. Это может быть тот же датчик или другой контроллер домена из этого домена.

|Протокол|Служба|Port|Источник| Direction|
|---------|---------|---------|---------|--------|
|LDAP|TCP и UDP|389|Контроллеры домена|Исходящее|
|Защищенный LDAP (LDAPS)|TCP|636|Контроллеры домена|Исходящее|
|LDAP для глобального каталога|TCP|3268|Контроллеры домена|Исходящее|
|LDAPS для глобального каталога|TCP|3269|Контроллеры домена|Исходящее|

### <a name="why-dont-activities-always-show-both-the-source-user-and-computer"></a>Почему для действий не всегда отображается исходный пользователь и компьютер?

[!INCLUDE [Product short](includes/product-short.md)] фиксирует действия по множеству различных протоколов. В некоторых случаях [!INCLUDE [Product short](includes/product-short.md)] не получает данные исходного пользователя в трафике. [!INCLUDE [Product short](includes/product-short.md)] пытается сопоставить сеанс пользователя с действием, и при успешном выполнении попытки отображается исходный пользователь действия. Если сопоставить пользователя не удается, отображается только исходный компьютер.

## <a name="troubleshooting"></a>Устранение неполадок

### <a name="what-should-i-do-if-the-product-short-sensor-or-standalone-sensor-doesnt-start"></a>Что делать, если [!INCLUDE [Product short](includes/product-short.md)] датчик или автономный датчик не запускается?

Просмотрите последнюю ошибку в текущем [журнале](troubleshooting-using-logs.md) ошибок (где устанавливается [!INCLUDE [Product short](includes/product-short.md)] в папку "Logs").

## <a name="see-also"></a>См. также:

- [[!INCLUDE [Product short](includes/product-short.md)] требований](prerequisites.md)
- [[!INCLUDE [Product short](includes/product-short.md)] Планирование ресурсов](capacity-planning.md)
- [Настройка сбора данных о событиях](configure-event-collection.md)
- [Настройка пересылки событий Windows](configure-event-forwarding.md)
- [Устранение неполадок](troubleshooting-known-issues.md)
- [Посетите [!INCLUDE [Product short](includes/product-short.md)] форум!](https://aka.ms/MDIcommunity)
