---
title: Основные сведения об оповещениях о работоспособности ATA
description: Описывает все оповещения о работоспособности для каждого компонента, список причин и шаги, необходимые для решения проблемы.
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 02/20/2019
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.prod: advanced-threat-analytics
ms.technology: ''
ms.assetid: b04fb8a4-b366-4b55-9d4c-6f054fa58a90
ms.reviewer: elofek
ms.suite: ems
ms.openlocfilehash: 1fc64d0102cc93cc212045956c6cab9f47bd7797
ms.sourcegitcommit: e844155ea57f73dfe2b47f4c5c1c7f5292ccbf1e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2020
ms.locfileid: "94690318"
---
# <a name="understanding-ata-health-alerts"></a>Основные сведения об оповещениях о работоспособности ATA

[!INCLUDE [Banner for top of topics](includes/banner.md)]

Центр работоспособности ATA позволяет получить сведения о проблемах с развертыванием ATA, вызывая оповещение о работоспособности.
В этой статье описаны все оповещения о работоспособности для каждого компонента с указанием причины и действий, необходимых для устранения проблемы.
## <a name="ata-center-issues"></a>Проблемы с центром ATA
### <a name="center-running-out-of-disk-space"></a>Нехватка места на диске для центра
|Предупреждение|Описание|Решение|Статус|
|----|----|----|----|
|Свободное место на диске компьютера центра ATA, который служит для хранения базы данных ATA, заканчивается.|Это означает, что на жестком диске осталось менее 200 ГБ или 20 % свободного места. Когда решение ATA определяет, что свободное место на диске заканчивается, оно начинает удалять старые данные из базы данных. Если старые данные удалить не удается, так как они все еще нужны для подсистемы обнаружения, выводится это оповещение. При получении этого оповещения ATA прекращает отслеживать новые действия.|Увеличьте размер диска или освободите на нем место.|Высокий|
### <a name="failure-sending-mail"></a>Сбой при отправке электронной почты
|Предупреждение|Описание|Решение|Статус|
|----|----|----|----|
|ATA не удалось отправить по электронной почте уведомление на указанный почтовый сервер.|Сообщения электронной почты не отправляются из ATA.|Проверьте конфигурацию SMTP-сервера.|Низкий|

### <a name="center-overloaded"></a>Центр перегружен
|Предупреждение|Описание|Решение|Статус|
|----|----|----|----|
|Центр ATA не может обработать весь объем данных, передаваемых из шлюзов ATA. |Центр ATA прекращает анализ нового сетевого трафика и событий. Это означает, что точность обнаружений и профилей уменьшается, пока это оповещение о работоспособности активно.|Предоставьте достаточное количество ресурсов для центра ATA. Дополнительные сведения о надлежащем планировании ресурсов для центра ATA см. в статье [Планирование производительности ATA](ata-capacity-planning.md). Проанализируйте производительность центра ATA согласно указаниям в статье [Устранение неполадок ATA с помощью счетчиков производительности](troubleshooting-ata-using-perf-counters.md).|Высокий|

### <a name="failure-connecting-to-the-siem-server-using-syslog"></a>Не удалось подключиться к серверу SIEM с помощью системного журнала
|Предупреждение|Описание|Решение|Статус|
|----|----|----|----|
|ATA не удалось отправить события на указанный сервер SIEM.|Это означает, что центр ATA не может отправить подозрительные действия и оповещения о работоспособности в SIEM.|Проверьте, [правильно ли настроены параметры сервера системного журнала](setting-syslog-email-server-settings.md).|Низкий|
### <a name="center-certificate-is-about-to-expire"></a>Истекает срок действия сертификата центра
|Предупреждение|Описание|Решение|Статус|
|----|----|----|----|
|Срок действия сертификата центра ATA истекает менее чем через 3 недели.|После того как срок действия сертификата истечет: подключение шлюзов ATA к центру ATA станет невозможным; Процесс центра ATA будет аварийно завершаться, и все функциональные возможности ATA прекратятся.|[Замените сертификат центра ATA](modifying-ata-center-configuration.md).|Средний|
### <a name="ata-center-certificate-expired"></a>Срок действия сертификата центра ATA истек
|Предупреждение|Описание|Решение|Статус|
|----|----|----|----|
|Срок действия сертификата центра ATA истек.|После того как срок действия сертификата истекает: подключение шлюзов ATA к центру ATA невозможно. Происходит аварийное завершение процесса ATA, и ATA перестает функционировать.|[Повторное развертывание центра ATA](install-ata-step1.md)|Высокий|
## <a name="ata-gateway-issues"></a>Проблемы со шлюзом ATA
### <a name="read-only-user-password-to-expire-shortly"></a>Истекает срок действия пароля пользователя, у которого ест доступ только для чтения
|Оповещение|Описание|Решение|Статус|
|----|----|----|----|
|Срок действия доступного только для чтения пароля пользователя, используемого для разрешения сущностей в Active Directory, истекает менее чем через 30 дней.|Если срок действия пароля пользователя истечет, все шлюзы ATA перестают работать и новые данные не собираются.|[Измените пароль для подключения к домену](modifying-ata-config-dcpassword.md), а затем обновите пароль в консоли ATA.|Средняя|
### <a name="read-only-user-password-expired"></a>Срок действия доступного только для чтения пароля пользователя истек
|Оповещение|Описание|Решение|Статус|
|----|----|----|----|
|Срок действия доступного только для чтения пароля пользователя, используемого для получения данных каталога, истек.|Все шлюзы ATA перестают работать (или перестанут работать вскоре), и новые данные не собираются.|[Измените пароль для подключения к домену](modifying-ata-config-dcpassword.md), а затем обновите пароль в консоли ATA.|Высокий|
### <a name="gateway-certificate-about-to-expire"></a>Истекает срок действия сертификата шлюза
|Предупреждение|Описание|Решение|Статус|
|----|----|----|----|
|Срок действия сертификата шлюза ATA истекает менее чем через 3 недели.|Не удалось подключиться от соответствующего шлюза ATA к центру ATA. Данные из этого шлюза ATA не передаются.|Сертификат шлюза ATA должен был продлиться автоматически. Просмотрите журналы шлюза ATA и центра ATA, чтобы понять, почему этого не произошло.|Средний|

### <a name="gateway-certificate-expired"></a>Срок действия сертификата шлюза истек
|Предупреждение|Описание|Решение|Статус|
|----|----|----|----|
|Срок действия сертификата шлюза ATA истек.|Подключение этого шлюза ATA к центру ATA отсутствует. Данные из этого шлюза ATA не передаются.|[Удалите и повторно установите шлюз ATA](install-ata-step3.md).|Высокий|
### <a name="domain-synchronizer-not-assigned"></a>Синхронизатор домена не назначен
|Предупреждение|Описание|Решение|Статус|
|----|----|----|----|
|Ни одному из шлюзов ATA не назначен синхронизатор домена. Причиной может быть то, что ни один из шлюзов ATA не настроен как потенциальный синхронизатор домена.|Если домен не синхронизирован, внесение изменений в сущности может привести к тому, что сведения о них в ATA могут устареть или отсутствовать, но на обнаружение это не влияет.|Настройте по крайней мере один шлюз ATA как [синхронизатор домена](install-ata-step5.md).|Низкий|
### <a name="allsome-of-the-capture-network-adapters-on-a-gateway-are-not-available"></a>Недоступны все или некоторые сетевые адаптеры записи в шлюзе
|Предупреждение|Описание|Решение|Статус|
|----|----|----|----|
|Все или некоторые выбранные сетевые адаптеры записи в шлюзе ATA отключены или не работают.|Сетевой трафик для некоторых или всех контроллеров домена больше не записывается шлюзом ATA. Это скажется на возможности обнаружения подозрительных действий, связанных с этими контроллерами домена.|Убедитесь в том, что выбранные сетевые адаптеры записи в шлюзе ATA подключены и работают.|Средний|
### <a name="some-domain-controllers-are-unreachable-by-a-gateway"></a>Некоторые контроллеры домена недоступны для шлюза
|Предупреждение|Описание|Решение|Статус|
|----|----|----|----|
|Функциональность шлюза ATA ограничена из-за проблем с подключением к некоторым из настроенных контроллеров домена.|Если шлюз ATA не может отправлять запросы на некоторые контроллеры домена, обнаружение атак Pass-the-Hash может быть менее точным.|Убедитесь в том, что контроллеры домена работают и что шлюз ATA может открывать подключения LDAP к ним.|Средний|
### <a name="all-domain-controllers-are-unreachable-by-a-gateway"></a>Все контроллеры домена недоступны для шлюза
|Предупреждение|Описание|Решение|Статус|
|----|----|----|----|
|Шлюз ATA в настоящее время находится в автономном режиме из-за проблем с подключением ко всем настроенным контроллерам домена.|Это влияет на способность ATA обнаруживать подозрительные действия, связанные с контроллерами домена, отслеживаемыми этим шлюзом ATA.| Убедитесь в том, что контроллеры домена работают и что шлюз ATA может открывать подключения LDAP к ним.|Средний|
### <a name="gateway-stopped-communicating"></a>Шлюз перестал обмениваться данными
|Предупреждение|Описание|Решение|Статус|
|----|----|----|----|
|Из шлюза ATA не поступают данные. Период времени по умолчанию для этого оповещения составляет 5 минут.|Сетевой трафик больше не записывается сетевым адаптером в этом шлюзе ATA. Это влияет на способность ATA обнаруживать подозрительные действия, так как сетевой трафик не может подключиться к центру ATA.|Проверьте не блокируется ли порт, используемый для обмена данными между шлюзом ATA и службой центра ATA, маршрутизаторами или брандмауэрами.|Средний|
### <a name="no-traffic-received-from-domain-controller"></a>От контроллера домена не поступает трафик
|Оповещение|Описание|Решение|Статус|
|----|----|----|----|
|Трафик не поступает от контроллера домена через этот шлюз ATA.|Это может означать, что зеркалирование портов с контроллеров домена на шлюз ATA еще не настроено или не работает.|Проверьте, [правильно ли настроено зеркалирование портов в сетевых устройствах](configure-port-mirroring.md).<br></br>В шлюзе ATA в дополнительных параметрах сетевого адаптера записи отключите следующие функции:<br></br>объединение полученных сегментов (IPv4);<br></br>объединение полученных сегментов (IPv6).|Средняя|
### <a name="some-forwarded-events-are-not-being-analyzed"></a>Некоторые пересылаемые события не анализируются
|Оповещение|Описание|Решение|Статус|
|----|----|----|----|
|Шлюз ATA получает больше событий, чем он может обработать.|Некоторые пересылаемые события не анализируются, что может сказаться на возможности обнаружения подозрительных действий, производящихся на контроллерах домена, которые отслеживаются этим шлюзом ATA.|Убедитесь в том, что только необходимые события пересылаются в шлюз ATA, или попытайтесь сделать так, чтобы некоторые события пересылались в другой шлюз ATA.|Средний|
### <a name="some-network-traffic-is-not-being-analyzed"></a>Часть сетевого трафика не анализируется
|Предупреждение|Описание|Решение|Статус|
|----|----|----|----|
|Шлюз ATA получает больше сетевого трафика, чем он может обработать.|Часть сетевого трафика не анализируется, что может сказаться на возможности обнаружения подозрительных действий, производящихся на контроллерах домена, которые отслеживаются этим шлюзом ATA.|Рекомендуется [добавить необходимое количество дополнительных процессоров и памяти](ata-capacity-planning.md). Если это отдельный шлюз ATA, сократите число отслеживаемых контроллеров домена.<br></br>Это также может произойти, если контроллеры домена установлены на виртуальные машины VMware. Чтобы эти оповещения не появлялись, присвойте следующим параметрам виртуальной машины значение "0" или "Отключено":<br></br>– TsoEnable;<br></br>– LargeSendOffload(IPv4);<br></br>– IPv4 TSO Offload.<br></br>Кроме того, рекомендуется отключить IPv4 Giant TSO Offload. Для получения дополнительной информации см. документацию VMware.|Средний|

### <a name="gateway-version-outdated"></a>Версия шлюза устарела
|Предупреждение|Описание|Решение|Статус|
|----|----|----|----|
|Версия центра ATA более поздняя, чем версия шлюза ATA. Из-за этого шлюз ATA работает не так, как ожидается.|Это может сказаться на возможности обнаружения подозрительных действий, производящихся на контроллерах домена, которые отслеживаются этим шлюзом ATA.|Обновляйте шлюз ATA до последней версии автоматически, включив [автоматическое обновление](install-ata-step1.md) в консоли ATA, или скачайте последний пакет шлюза ATA, доступный в консоли ATA.|Высокий|
### <a name="gateway-service-failed-to-start"></a>Не удалось запустить службу шлюза
|Предупреждение|Описание|Решение|Статус|
|----|----|----|----|
|Не удалось запустить службу шлюза ATA в течение по крайней мере 30 минут.|Это может сказаться на возможности обнаружения подозрительных действий, производящихся на контроллерах домена, которые отслеживаются этим шлюзом ATA.|Просмотрите журналы шлюза ATA, чтобы [выяснить основную причину сбоев при запуске службы шлюза ATA](troubleshooting-ata-using-logs.md).|Высокий|
## <a name="lightweight-gateway"></a>Упрощенный шлюз
### <a name="lightweight--gateway-reached-a-memory-resource-limit"></a>Упрощенный шлюз достиг ограничения на ресурсы памяти
|Предупреждение|Описание|Решение|Статус|
|----|----|----|----|
|Работа упрощенного шлюза ATA была остановлена, и он будет перезапущен автоматически, чтобы защитить контроллер домена от возникновения состояния нехватки памяти.|Использование памяти упрощенным шлюзом ATA ограничено для того, чтобы контроллер домена не испытывал нехватку ресурсов. Такая нехватка может возникать при интенсивном использовании памяти на контроллере домена. Данные от этого контроллера домена отслеживаются лишь частично.|Увеличьте объем памяти (ОЗУ) на контроллере домена или добавьте больше контроллеров домена, чтобы снять часть нагрузки с этого контроллера домена.|Средняя|


## <a name="see-also"></a>См. также
- [Предварительные требования ATA](ata-prerequisites.md)
- [Планирование производительности ATA](ata-capacity-planning.md)
- [Настройка сбора данных о событиях](configure-event-collection.md)
- [Настройка пересылки событий Windows](configure-event-collection.md)
- [Обязательно ознакомьтесь с форумом ATA.](https://social.technet.microsoft.com/Forums/security/home?forum=mata)
