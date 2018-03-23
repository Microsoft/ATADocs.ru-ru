---
title: "Сведения об оповещениях мониторинга Azure ATP | Документы Майкрософт"
description: "В этой статье описывается, как использовать журналы Azure ATP для устранения неполадок."
keywords: 
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 2/21/2018
ms.topic: article
ms.prod: 
ms.service: azure-advanced-threat-protection
ms.technology: 
ms.assetid: d0551e91-3b21-47d5-ad9d-3362df6d47c0
ms.reviewer: itargoet
ms.suite: ems
ms.openlocfilehash: cdb440e92aef0f9d09d3aa9411d0ce65435469d1
ms.sourcegitcommit: 03e959b7ce4b6df421297e1872e028793c967302
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/21/2018
---
*Применяется к: Azure Advanced Threat Protection*

# <a name="understanding-azure-atp-sensor-and-standalone-sensor-monitoring-alerts"></a>Общие сведения об оповещениях мониторинга датчика и автономного датчика Azure ATP

Центр обеспечения работоспособности Azure ATP сообщает о возникновении проблем с рабочими областями Azure ATP, создавая оповещения мониторинга. В этой статье описываются все оповещения мониторинга для каждого компонента с указанием причины и действий, необходимых для устранения проблемы.

## <a name="read-only-user-password-to-expire-shortly"></a>Истекает срок действия пароля пользователя, у которого ест доступ только для чтения

|Оповещение|Описание|Решение|Статус|
|----|----|----|----|
|Срок действия доступного только для чтения пароля пользователя, используемого для разрешения сущностей в Active Directory, истекает менее чем через 30 дней.|Если срок действия пароля пользователя истечет, все датчики Azure ATP перестают работать и новые данные не собираются.|[Измените пароль для подключения к домену](modifying-atp-config-dcpassword.md), а затем обновите пароль в консоли Azure ATP.|Средняя|

## <a name="read-only-user-password-expired"></a>Срок действия доступного только для чтения пароля пользователя истек

|Оповещение|Описание|Решение|Статус|
|----|----|----|----|
|Срок действия доступного только для чтения пароля пользователя, используемого для получения данных каталога, истек.|Все датчики Azure ATP перестают работать (или перестанут работать вскоре), и новые данные не собираются.|[Измените пароль для подключения к домену](modifying-atp-config-dcpassword.md), а затем обновите пароль в консоли Azure ATP.|Высокий|

## <a name="domain-synchronizer-not-assigned"></a>Синхронизатор домена не назначен

|Оповещение|Описание|Решение|Статус|
|----|----|----|----|
|Ни одному из датчиков Azure ATP не назначен синхронизатор домена. Причиной может быть то, что ни один из датчиков Azure ATP не настроен как потенциальный синхронизатор домена.|Если домен не синхронизирован, внесение изменений в сущности может привести к тому, что сведения о них в Azure ATP могут устареть или отсутствовать, но на обнаружение это не влияет.|Настройте по крайней мере один датчик Azure ATP как [синхронизатор домена](install-atp-step5.md).|Низкая|

## <a name="allsome-of-the-capture-network-adapters-on-a-sensor-are-not-available"></a>Недоступны все или некоторые сетевые адаптеры записи в датчике

|Оповещение|Описание|Решение|Статус|
|----|----|----|----|
|Все или некоторые выбранные сетевые адаптеры записи в датчике Azure ATP отключены или не работают.|Сетевой трафик для некоторых или всех контроллеров домена больше не записывается датчиком Azure ATP. Это скажется на возможности обнаружения подозрительных действий, связанных с этими контроллерами домена.|Убедитесь в том, что выбранные сетевые адаптеры записи в датчике Azure ATP подключены и работают.|Средняя|

## <a name="some-domain-controllers-are-unreachable-by-a-sensor"></a>Некоторые контроллеры домена недоступны для датчика

|Оповещение|Описание|Решение|Статус|
|----|----|----|----|
|Функциональность датчика Azure ATP ограничена из-за проблем с подключением к некоторым из настроенных контроллеров домена.|Если датчик Azure ATP не может отправлять запросы на некоторые контроллеры домена, обнаружение атак Pass-the-Hash может быть менее точным.|Убедитесь в том, что контроллеры домена работают и что датчик Azure ATP может открывать подключения LDAP к ним.|Средняя|

## <a name="all-domain-controllers-are-unreachable-by-a-sensor"></a>Все контроллеры домена недоступны для датчика

|Оповещение|Описание|Решение|Статус|
|----|----|----|----|
|Датчик Azure ATP в настоящее время находится в автономном режиме из-за проблем с подключением ко всем настроенным контроллерам домена.|Это скажется на возможности обнаружения решением Azure ATP подозрительных действий, связанных с контроллерами домена, отслеживаемых этим датчиком Azure ATP.| Убедитесь в том, что контроллеры домена работают и что датчик Azure ATP может открывать подключения LDAP к ним.|Средняя|

## <a name="sensor-stopped-communicating"></a>Датчик перестал обмениваться данными

|Оповещение|Описание|Решение|Статус|
|----|----|----|----|
|Из датчика Azure ATP не поступают данные. Период времени по умолчанию для этого оповещения составляет 5 минут.|Сетевой трафик больше не записывается сетевым адаптером в этом датчике Azure ATP. Это скажется на возможности обнаружения подозрительных действий решением ATA, так как сетевой трафик не поступает в облачную службу Azure ATP.|Проверьте, не блокируется ли порт, используемый для обмена данными между датчиком Azure ATP и облачной службой Azure ATP, маршрутизаторами или брандмауэрами.|Средняя|

## <a name="no-traffic-received-from-domain-controller"></a>От контроллера домена не поступает трафик

|Оповещение|Описание|Решение|Статус|
|----|----|----|----|
|Трафик не поступает от контроллера домена через этот датчик Azure ATP.|Это может означать, что зеркалирование портов с контроллеров домена на датчик Azure ATP еще не настроено или не работает.|Проверьте, [правильно ли настроено зеркалирование портов в сетевых устройствах](configure-port-mirroring.md).<br></br>В сетевом адаптере захвата в датчике Azure ATP отключите следующие функции в разделе "Дополнительные параметры":<br></br>объединение полученных сегментов (IPv4);<br></br>объединение полученных сегментов (IPv6).|Средняя|

## <a name="some-forwarded-events-are-not-being-analyzed"></a>Некоторые пересылаемые события не анализируются

|Оповещение|Описание|Решение|Статус|
|----|----|----|----|
|Датчик Azure ATP получает больше событий, чем он может обработать.|Некоторые пересылаемые события не анализируются, что может сказаться на возможности обнаружения подозрительных действий, производящихся на контроллерах домена, которые отслеживаются этим датчиком Azure ATP.|Убедитесь в том, что только необходимые события пересылаются в датчик Azure ATP, или попытайтесь сделать так, чтобы некоторые события пересылались в другой датчик Azure ATP.|Средняя|

## <a name="some-network-traffic-is-not-being-analyzed"></a>Часть сетевого трафика не анализируется

|Оповещение|Описание|Решение|Статус|
|----|----|----|----|
|Датчик Azure ATP получает больше сетевого трафика, чем он может обработать.|Часть сетевого трафика не анализируется, что может сказаться на возможности обнаружения подозрительных действий, производящихся на контроллерах домена, которые отслеживаются этим датчиком Azure ATP.|Рекомендуется [добавить необходимое количество дополнительных процессоров и памяти](atp-capacity-planning.md). Если это автономный датчик Azure ATP, сократите число отслеживаемых контроллеров домена.<br></br>Это также может произойти, если контроллеры домена установлены на виртуальные машины VMware. Чтобы эти оповещения не появлялись, присвойте следующим параметрам виртуальной машины значение "0" или "Отключено":<br></br>– TsoEnable;<br></br>– LargeSendOffload(IPv4);<br></br>– IPv4 TSO Offload.<br></br>Кроме того, рекомендуется отключить IPv4 Giant TSO Offload. Дополнительные сведения см. в документации по VMware.|Средняя|

## <a name="sensor-service-failed-to-start"></a>Не удалось запустить службу датчика

|Оповещение|Описание|Решение|Статус|
|----|----|----|----|
|Не удалось запустить службу датчика Azure ATP в течение по крайней мере 30 минут.|Это может сказаться на возможности обнаружения подозрительных действий, производящихся на контроллерах домена, которые отслеживаются этим датчиком Azure ATP.|Просмотрите журналы датчика Azure ATP, чтобы выяснить основную причину сбоя службы датчика Azure ATP.|Высокий|

## <a name="sensor-reached-a-memory-resource-limit"></a>Датчик достиг ограничения на ресурсы памяти

|Оповещение|Описание|Решение|Статус|
|----|----|----|----|
|Работа датчика Azure ATP остановлена, и он будет перезапущен автоматически, чтобы защитить контроллер домена от возникновения состояния нехватки памяти.|Использование памяти датчиком Azure ATP ограничено для того, чтобы контроллер домена не испытывал нехватки ресурсов. Такая нехватка может возникать при интенсивном использовании памяти на контроллере домена. Данные от этого контроллера домена отслеживаются лишь частично.|Увеличьте объем памяти (ОЗУ) на контроллере домена или добавьте больше контроллеров домена, чтобы снять часть нагрузки с этого контроллера домена.|Средняя|


## <a name="see-also"></a>См. также

- [Предварительные требования к Azure ATP](atp-prerequisites.md)
- [Планирование производительности Azure ATP](atp-capacity-planning.md)
- [Настройка сбора данных о событиях](configure-event-collection.md)
- [Настройка пересылки событий Windows](configure-event-forwarding.md#configuring-windows-event-forwarding)
- [Обязательно ознакомьтесь с форумом ATP](https://aka.ms/azureatpcommunity)