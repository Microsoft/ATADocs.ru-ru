---
title: Анализ оповещений о работоспособности Microsoft Defender для удостоверений
description: В этой статье описаны все оповещения о работоспособности для каждого компонента с указанием причины и действий, необходимых для устранения проблемы
ms.date: 10/26/2020
ms.topic: how-to
ms.openlocfilehash: 30f88e239ac7c9fb2853688d3977e03401e8a353
ms.sourcegitcommit: cdb7ae4580851e25aae24d07e7d66a750aa54405
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/03/2020
ms.locfileid: "96543099"
---
# <a name="understanding-product-long-sensor-health-alerts"></a>Анализ оповещений о работоспособности датчика [!INCLUDE [Product long](includes/product-long.md)]

Центр обеспечения работоспособности [!INCLUDE [Product long](includes/product-long.md)] сообщает о возникновении проблем с экземплярами [!INCLUDE [Product short](includes/product-short.md)], создавая оповещения о работоспособности. В этой статье описаны все оповещения о работоспособности для каждого компонента с указанием причины и действий, необходимых для устранения проблемы.

## <a name="all-domain-controllers-are-unreachable-by-a-sensor"></a>Все контроллеры домена недоступны для датчика

|Оповещение|Описание:|Решение|Статус|
|----|----|----|----|
|Датчик [!INCLUDE [Product short](includes/product-short.md)] сейчас находится в автономном режиме из-за проблем с подключением ко всем настроенным контроллерам домена.|Это сказывается на возможности обнаружения [!INCLUDE [Product short](includes/product-short.md)] подозрительных действий, связанных с контроллерами домена, которые отслеживает этот датчик [!INCLUDE [Product short](includes/product-short.md)].| Убедитесь, что контроллеры домена работают и что датчик [!INCLUDE [Product short](includes/product-short.md)] может открывать подключения LDAP к ним. Также в области **Параметры** обязательно настройте учетную запись службы каталогов для каждого развернутого леса.|Средняя|

## <a name="allsome-of-the-capture-network-adapters-on-a-sensor-are-not-available"></a>Недоступны все или некоторые сетевые адаптеры записи в датчике

|Оповещение|Описание:|Решение|Статус|
|----|----|----|----|
|All/Some of the selected capture network adapters on the [!INCLUDE [Product short](includes/product-short.md)] sensor are disabled or disconnected (Все или некоторые выбранные сетевые адаптеры записи в датчике [!INCLUDE [Product short](includes/product-short.md)] для удостоверений отключены или не работают).|Сетевой трафик для некоторых или всех контроллеров домена больше не записывается датчиком [!INCLUDE [Product short](includes/product-short.md)]. Это скажется на возможности обнаружения подозрительных действий, связанных с этими контроллерами домена.|Убедитесь, что выбранные сетевые адаптеры записи в датчике [!INCLUDE [Product short](includes/product-short.md)] подключены и работают.|Средняя|

## <a name="directory-services-user-credentials-are-incorrect"></a>Неправильные учетные данные пользователя служб каталогов

|Оповещение|Описание:|Решение|Статус|
|----|----|----|----|
|Учетные данные пользователя служб каталогов неправильные.|Это влияет на способность датчиков определять действия, используя запросы LDAP к контроллерам доменов.|— Для **стандартных** учетных записей AD: проверьте правильность имени пользователя, пароля и домена на странице конфигурации **Служба каталогов**.<br>— Для **групповых управляемых учетных записей служб**: проверьте правильность имени пользователя и домена на странице конфигурации **Служба каталогов**. Также проверьте остальные предварительные требования для **учетной записи gMSA**, описанные в руководстве по [подключению к лесу Active Directory](install-step2.md#prerequisites).|Средняя|

## <a name="low-success-rate-of-active-name-resolution"></a>Низкая частота успешных активных разрешений имен

|Оповещение|Описание:|Решение|Статус|
|----|----|----|----|
|Перечисленные датчики [!INCLUDE [Product short](includes/product-short.md)] не разрешают IP-адреса в имена устройств в более 90 % случаев при использовании следующих методов:<br />- NTLM через RPC<br />- NetBIOS<br />- Обратный поиск в DNS|Это влияет на возможности обнаружения в [!INCLUDE [Product short](includes/product-short.md)] и может увеличить количество ложноположительных оповещений.|- Для NTLM через RPC: Убедитесь, что порт 135 открыт для входящего подключения от датчиков [!INCLUDE [Product short](includes/product-short.md)] на всех компьютерах в среде.<br />— Для обратного поиска в DNS: убедитесь, что датчик может устанавливать связь с DNS-сервером, а зоны обратного просмотра включены.<br />- Для NetBIOS: Убедитесь, что порт 137 открыт для входящего подключения от датчиков [!INCLUDE [Product short](includes/product-short.md)] на всех компьютерах в среде.<br />Кроме того, убедитесь, что конфигурация сети (например, брандмауэры) не препятствует обмену данными с использованием соответствующих портов.|Низкая|

## <a name="no-traffic-received-from-domain-controller"></a>От контроллера домена не поступает трафик

|Оповещение|Описание:|Решение|Статус|
|----|----|----|----|
|No traffic was received from the domain controller via this [!INCLUDE [Product short](includes/product-short.md)] sensor (Трафик не поступает от контроллера домена через этот датчик Defender для удостоверений.)|Это может означать, что зеркалирование портов с контроллеров домена на датчик [!INCLUDE [Product short](includes/product-short.md)] еще не настроено или не работает.|Проверьте, [правильно ли настроено зеркалирование портов в сетевых устройствах](configure-port-mirroring.md).<br></br>Для сетевого адаптера записи в датчике [!INCLUDE [Product short](includes/product-short.md)] отключите следующие функции в разделе "Дополнительные параметры":<br></br>объединение полученных сегментов (IPv4);<br></br>объединение полученных сегментов (IPv6).|Средняя|

## <a name="read-only-user-password-to-expire-shortly"></a>Истекает срок действия пароля пользователя, у которого ест доступ только для чтения

|Оповещение|Описание:|Решение|Статус|
|----|----|----|----|
|Срок действия доступного только для чтения пароля пользователя, используемого для разрешения сущностей в Active Directory, истекает менее чем через 30 дней.|Когда срок действия пароля пользователя истекает, все датчики [!INCLUDE [Product short](includes/product-short.md)] перестают работать и новые данные не собираются.|[Измените пароль для подключения к домену](modifying-config-dcpassword.md), а затем обновите пароль на портале [!INCLUDE [Product short](includes/product-short.md)].|Средняя|

## <a name="read-only-user-password-expired"></a>Срок действия доступного только для чтения пароля пользователя истек

|Оповещение|Описание:|Решение|Статус|
|----|----|----|----|
|Срок действия доступного только для чтения пароля пользователя, используемого для получения данных каталога, истек.|Все датчики [!INCLUDE [Product short](includes/product-short.md)] перестают работать (или перестанут работать вскоре), и новые данные не собираются.|[Измените пароль для подключения к домену](modifying-config-dcpassword.md), а затем обновите пароль на портале [!INCLUDE [Product short](includes/product-short.md)].|Высокий|

## <a name="sensor-outdated"></a>Датчик устарел

|Оповещение|Описание:|Решение|Статус|
|----|----|----|----|
|A [!INCLUDE [Product short](includes/product-short.md)] sensor is outdated (Датчик [!INCLUDE [Product short](includes/product-short.md)] для удостоверений устарел).|Датчик [!INCLUDE [Product short](includes/product-short.md)] работает под управлением версии, которая не может взаимодействовать с облачной инфраструктурой [!INCLUDE [Product short](includes/product-short.md)].|Обновите датчик вручную и выясните, почему он не обновляется автоматически. Если это не помогло, скачайте последний пакет установки датчика и переустановите датчик. Дополнительные сведения см. в кратком руководстве [Установка датчика [!INCLUDE [Product short](includes/product-short.md)]](install-step4.md).|Средняя|

## <a name="sensor-reached-a-memory-resource-limit"></a>Датчик достиг ограничения на ресурсы памяти

|Оповещение|Описание:|Решение|Статус|
|----|----|----|----|
|Датчик [!INCLUDE [Product short](includes/product-short.md)] остановил работу и будет перезапущен автоматически для защиты контроллера домена от нехватки памяти.|Использование памяти датчиком [!INCLUDE [Product short](includes/product-short.md)] ограничено для того, чтобы контроллер домена не испытывал нехватки ресурсов. Такая нехватка может возникать при интенсивном использовании памяти на контроллере домена. Данные от этого контроллера домена отслеживаются лишь частично.|Увеличьте объем памяти (ОЗУ) на контроллере домена или добавьте больше контроллеров домена, чтобы снять часть нагрузки с этого контроллера домена.|Средняя|

## <a name="sensor-service-failed-to-start"></a>Не удалось запустить службу датчика

|Оповещение|Описание:|Решение|Статус|
|----|----|----|----|
|The [!INCLUDE [Product short](includes/product-short.md)] sensor service failed to start for at least 30 minutes (Не удалось запустить службу датчика [!INCLUDE [Product short](includes/product-short.md)] для удостоверений в течение по крайней мере 30 минут.)|Это может повлиять на возможность обнаружения подозрительных действий, выполняющихся на контроллерах домена, которые отслеживаются этим датчиком [!INCLUDE [Product short](includes/product-short.md)].|Просмотрите журналы датчика [!INCLUDE [Product short](includes/product-short.md)], чтобы выяснить основную причину сбоя службы датчика [!INCLUDE [Product short](includes/product-short.md)].|Высокий|

## <a name="sensor-stopped-communicating"></a>Датчик перестал обмениваться данными

|Оповещение|Описание:|Решение|Статус|
|----|----|----|----|
|There has been no communication from the [!INCLUDE [Product short](includes/product-short.md)] sensor (От датчика [!INCLUDE [Product short](includes/product-short.md)] для удостоверений не поступают данные). Период времени по умолчанию для этого оповещения составляет 5 минут.|Сетевой трафик больше не записывается сетевым адаптером в датчике [!INCLUDE [Product short](includes/product-short.md)]. Это влияет на возможность обнаружения подозрительных действий решением ATA, так как сетевой трафик не поступает в облачный экземпляр [!INCLUDE [Product short](includes/product-short.md)].|Проверьте, не блокируется ли порт, используемый для обмена данными между датчиком [!INCLUDE [Product short](includes/product-short.md)] и облачным экземпляром [!INCLUDE [Product short](includes/product-short.md)], маршрутизаторами или брандмауэрами.|Средняя|

## <a name="some-domain-controllers-are-unreachable-by-a-sensor"></a>Некоторые контроллеры домена недоступны для датчика

|Оповещение|Описание:|Решение|Статус|
|----|----|----|----|
|Датчик [!INCLUDE [Product short](includes/product-short.md)] имеет ограниченную функциональность из-за проблем с подключением к некоторым из настроенных контроллеров домена.|Если датчик [!INCLUDE [Product short](includes/product-short.md)] не может отправлять запросы на некоторые контроллеры домена, обнаружение атак Pass-the-Hash может быть менее точным.|Убедитесь, что контроллеры домена работают и что датчик [!INCLUDE [Product short](includes/product-short.md)] может открывать подключения LDAP к ним.|Средняя|

## <a name="some-windows-events-are-not-being-analyzed"></a>Некоторые события Windows не анализируются

|Оповещение|Описание:|Решение|Статус|
|----|----|----|----|
|The [!INCLUDE [Product short](includes/product-short.md)] sensor is receiving more events than it can process (Датчик [!INCLUDE [Product short](includes/product-short.md)] для удостоверений получает больше событий, чем он может обработать).|Некоторые события Windows не анализируются. Это может затруднить обнаружение подозрительных действий, выполняемых на контроллерах домена, которые отслеживаются этим датчиком [!INCLUDE [Product short](includes/product-short.md)].|Убедитесь, что только необходимые события пересылаются в датчик [!INCLUDE [Product short](includes/product-short.md)], или попытайтесь сделать так, чтобы некоторые события пересылались в другой датчик [!INCLUDE [Product short](includes/product-short.md)].|Средняя|

## <a name="some-network-traffic-could-not-be-analyzed"></a>Не удалось проанализировать часть сетевого трафика

|Оповещение|Описание:|Решение|Статус|
|----|----|----|----|
|Датчик [!INCLUDE [Product short](includes/product-short.md)] получает больше сетевого трафика, чем может обработать.|Не удалось проанализировать часть сетевого трафика, что может сказаться на возможности обнаружения подозрительных действий, выполняемых на контроллерах домена, которые отслеживаются этим датчиком [!INCLUDE [Product short](includes/product-short.md)].|Рекомендуется [добавить необходимое количество дополнительных процессоров и памяти](capacity-planning.md). Если это автономный датчик [!INCLUDE [Product short](includes/product-short.md)], сократите число отслеживаемых контроллеров домена.<br></br>Это также может произойти, если контроллеры домена установлены на виртуальные машины VMware. Чтобы эти оповещения не появлялись, присвойте следующим параметрам виртуальной машины значение "0" или "Отключено":<br></br>– TsoEnable;<br></br>– LargeSendOffload(IPv4);<br></br>– IPv4 TSO Offload.<br></br>Кроме того, рекомендуется отключить IPv4 Giant TSO Offload. Дополнительные сведения см. в документации по VMware.|Средняя|

## <a name="some-etw-events-are-not-being-analyzed"></a>Некоторые события ETW не анализируются

|Оповещение|Описание:|Решение|Статус|
|----|----|----|----|
|The [!INCLUDE [Product short](includes/product-short.md)] sensor is receiving more Event Tracing for Windows (ETW) events than it can process (Датчик [!INCLUDE [Product short](includes/product-short.md)] для удостоверений получает больше данных трассировки событий Windows (ETW), чем может обработать).|Некоторые события трассировки событий Windows (ETW) не анализируются. Это может затруднить обнаружение подозрительных действий, выполняемых на контроллерах домена, которые отслеживаются этим датчиком [!INCLUDE [Product short](includes/product-short.md)].|Убедитесь, что только необходимые события пересылаются в датчик [!INCLUDE [Product short](includes/product-short.md)], или попытайтесь сделать так, чтобы некоторые события пересылались в другой датчик [!INCLUDE [Product short](includes/product-short.md)].|Средняя|

<!--
## Windows events missing from domain controller audit policy

|Alert|Description|Resolution|Severity|
|----|----|----|----|
| Windows events missing from domain controller audit policy|For the correct events to be audited and included in the Windows Event Log, your domain controllers require accurate Advanced Audit Policy settings. Incorrect Advanced Audit Policy settings leave critical events out of your logs, and result in incomplete [!INCLUDE [Product short](includes/product-short.md)] coverage.|Review your [Advanced Audit policy](configure-windows-event-collection.md) and modify as needed. | Medium|
-->

## <a name="see-also"></a>См. также

- [Предварительные требования для работы с [!INCLUDE [Product short](includes/product-short.md)]](prerequisites.md)
- [Планирование ресурсов [!INCLUDE [Product short](includes/product-short.md)]](capacity-planning.md)
- [Настройка сбора данных о событиях](configure-event-collection.md)
- [Настройка пересылки событий Windows](configure-event-forwarding.md)
- [Посетите форум по [!INCLUDE [Product short](includes/product-short.md)].](https://aka.ms/MDIcommunity)
