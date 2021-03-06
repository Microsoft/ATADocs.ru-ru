---
title: Справочник по идентификаторам событий ATA | Microsoft Docs
description: Предоставляет список идентификаторов событий ATA и их описания.
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 12/20/2018
ms.topic: conceptual
ms.prod: advanced-threat-analytics
ms.technology: ''
ms.assetid: 5d639e84-2e37-43a9-9667-49be6c4fa8b7
ms.reviewer: arzinger
ms.suite: ems
ms.openlocfilehash: 3d7c66c907cc237ae3458d77b25e486a90f01e2b
ms.sourcegitcommit: e844155ea57f73dfe2b47f4c5c1c7f5292ccbf1e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2020
ms.locfileid: "94690709"
---
# <a name="ata-event-id-reference"></a>Справочник по идентификаторам событий ATA


[!INCLUDE [Banner for top of topics](includes/banner.md)]

Средство просмотра событий центра ATA записывает события ATA в журнал. В этой статье приводится список идентификаторов событий и описание каждого из них.

События можно найти здесь:

![расположение идентификатора события](media/event-id-location.png)

## <a name="ata-health-events"></a>События работоспособности ATA

|Идентификатор события|Имя оповещения|
|---------|---------------|
|1001|Нехватка места на диске для центра|
|1003|Центр перегружен|
|1004|"Срок действия сертификата центра скоро истечет" или "Срок действия сертификата центра истек"|
|1005|"MongoDB не работает"|
|1006|"Истекает срок действия пароля пользователя, у которого есть доступ только на чтение" или "Истек срок действия пароля пользователя с доступом только на чтение"|
|1007|Синхронизатор домена не назначен|
|1008|Недоступны все или некоторые сетевые адаптеры записи в шлюзе|
|1009|"Сетевой адаптер записи больше не существует в шлюзе"|
|1010|"Некоторые контроллеры домена недоступны для шлюза" или "Все контроллеры домена недоступны для шлюза"|
|1011|Шлюз перестал обмениваться данными|
|1012|Некоторые пересылаемые события не анализируются|
|1013|Часть сетевого трафика не анализируется|
|1014|Сбой при отправке электронной почты|
|1015|Не удалось подключиться к серверу SIEM с помощью системного журнала|
|1016|Версия шлюза устарела|
|1017|От контроллера домена не поступает трафик|
|1018|Не удалось запустить службу шлюза|
|1019|Упрощенный шлюз достиг ограничения на ресурсы памяти|
|1020|Шлюз не обрабатывает события Radius|
|1021|Шлюз не обрабатывает события Syslog|
|1022|Служба геолокации недоступна|
 
## <a name="ata-security-alert-events"></a>Оповещения системы безопасности ATA

|Идентификатор события|Имя оповещения|
|---------|---------------|
|2001|Подозрение на кражу идентификационных данных на основе аномального поведения|
|2002|Внедрение нестандартных протоколов.|
|2003|Разведывательная атака с использованием перечисления учетных записей.|
|2004|Атака методом подбора с помощью простой привязки LDAP|
|2006|Вредоносная репликация служб каталогов|
|2007 г.|Разведывательная атака с использованием DNS.|
|2008|Переход на более слабое шифрование|
|2009|Действие понижения уровня шифрования (потенциальная атака Golden Ticket)|
|2010|Действие понижения уровня шифрования (потенциальная атака Overpass-the-Hash)|
|2011|Действие понижения уровня шифрования (потенциальная атака с использованеим мастер-ключа)|
|2012|Рекогносцировка с использованием перечисления сеансов SMB|
|2013|Атака, направленная на повышение привилегий с использованием поддельных данных авторизации|
|2014|Действие Honeytoken|
|2016|Массовое удаление объектов|
|2017|Кража удостоверения с помощью атаки Pass-the-Hash|
|2018|Кража удостоверения с помощью атаки Pass-the-Ticket|
|2019|Обнаружение попытки удаленного выполнения|
|2020|Вредоносный запрос конфиденциальных сведений для защиты данных|
|2021|Рекогносцировка с использованием запросов к службам каталогов|
|2022|действие с использованием "золотого" билета Kerberos;|
|2023|Подозрительные неудачные попытки проверки подлинности|
|2024|аномальное изменение привилегированных групп;|
|2026|Создание подозрительной службы|

## <a name="ata-auditing-events"></a>События аудита ATA

|Идентификатор события|Имя оповещения|
|---------|---------------|
|3001|Изменение конфигурации ATA|
|3002|Добавление шлюза ATA|
|3003|Удаление шлюза ATA|
|3004|Активация лицензии ATA|
|3005|Вход в консоль ATA|
|3006|Изменение состояния действия работоспособности вручную|
|3007|Изменение состояния подозрительного действия вручную|

## <a name="see-also"></a>См. также:
- [Предварительные требования ATA](ata-prerequisites.md)
- [Планирование производительности ATA](ata-capacity-planning.md)
- [Настройка сбора данных о событиях](configure-event-collection.md)
- [Настройка пересылки событий Windows](configure-event-collection.md)
- [Обязательно ознакомьтесь с форумом ATA.](https://social.technet.microsoft.com/Forums/security/home?forum=mata)
