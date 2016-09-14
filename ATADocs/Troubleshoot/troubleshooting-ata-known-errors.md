---
title: "Устранение неполадок по журналу ошибок ATA | Microsoft ATA"
description: "В этой статье описываются способы устранения распространенных ошибок в ATA"
keywords: 
author: rkarlin
manager: mbaldwin
ms.date: 08/24/2016
ms.topic: article
ms.prod: 
ms.service: advanced-threat-analytics
ms.technology: 
ms.assetid: d89e7aff-a6ef-48a3-ae87-6ac2e39f3bdb
ms.reviewer: bennyl
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 15c1a0d7ae213876c0e3a955eaeea8887281b4e6
ms.openlocfilehash: b073a1b969f8841c9bbe540722349a5ef70340d4


---

*Применяется к Advanced Threat Analytics версии 1.7*



# Устранение неполадок журнала ошибок ATA
В этом разделе подробно описываются возможные ошибки в развертываниях ATA и действия, необходимые для их устранения.
## Ошибки шлюза ATA
|Ошибка|Описание|Решение|
|-------------|----------|---------|
|System.DirectoryServices.Protocols.LdapException: произошла локальная ошибка|Шлюзу ATA не удалось выполнить аутентификацию в контроллере домена.|1. Убедитесь, что запись DNS контроллера домена на DNS-сервере настроена надлежащим образом. <br>2. Убедитесь, что время шлюза ATA синхронизировано с временем контроллера домена.|
|System.IdentityModel.Tokens.SecurityTokenValidationException: не удалось проверить цепочку сертификатов|Шлюзу ATA не удалось проверить сертификат центра ATA.|1. Убедитесь, что сертификат корневого ЦС установлен в хранилище сертификатов доверенного центра сертификации на шлюзе ATA. <br>2. Убедитесь, что список отзыва сертификатов доступен и можно выполнить проверку отзыва сертификатов.|
|Microsoft.Common.ExtendedException: не удалось проанализировать время создания|Шлюзу ATA не удалось проанализировать сообщения системного журнала, пересланные с SIEM.|Убедитесь, что SIEM настроен для пересылки сообщений в одном из форматов, поддерживаемых ATA.|
|System.ServiceModel.FaultException: ошибка при проверке безопасности сообщения.|Шлюзу ATA не удалось выполнить аутентификацию в центре ATA.|Убедитесь, что время шлюза ATA синхронизировано с временем центра ATA.|
|System.ServiceModel.EndpointNotFoundException: не удалось подключиться к net.tcp://center.ip.addr:443/IEntityReceiver|Шлюзу ATA не удалось установить подключение к центру ATA.|Убедитесь, что параметры сети правильные, а сетевое подключение между шлюзом ATA и центром ATA активно.|
|System.DirectoryServices.Protocols.LdapException: LDAP-сервер недоступен.|Шлюзу ATA не удалось выполнить запрос к контроллеру домена, используя протокол LDAP.|1. Убедитесь, что учетная запись пользователя, используемая ATA для подключения к домену Active Directory, имеет доступ на чтение для всех объектов в дереве Active Directory. <br>2. Убедитесь, что в контроллере домена не настроена защита, которая предотвращает выполнение запросов LDAP из учетной записи пользователя, используемой ATA.|
|Microsoft.Tri.Infrastructure.ContractException: исключение контракта|Шлюзу ATA не удалось синхронизировать конфигурацию из центра ATA.|Завершите настройку шлюза ATA в консоли ATA.|
|System.Reflection.ReflectionTypeLoadException: не удалось загрузить один из запрошенных типов или несколько. Для получения дополнительных сведений извлеките свойство LoaderExceptions.|Анализатор сообщений устанавливается в шлюзе ATA.| Удалите анализатор сообщений.|
|Ошибка [Layout] System.OutOfMemoryException: возникло исключение типа "System.OutOfMemoryException".|В шлюзе ATA недостаточно памяти.|Увеличьте объем памяти в контроллере домена.|
|Не удалось запустить динамический потребитель ---> Microsoft.Opn.Runtime.Monitoring.MessageSessionException: поставщик события PEFNDIS не готов|PEF (анализатор сообщений) неправильно установлен.|Если вы используете Hyper-V, попробуйте обновить службы интеграции Hyper-V по-другому. Чтобы найти временное решение, обратитесь в службу поддержки.|
|Сбой установки с ошибкой: 0x80070652|На компьютере есть другие незавершенные установки.|Дождитесь завершения других установок и при необходимости перезагрузите компьютер.|
|System.InvalidOperationException: Instance 'Microsoft.Tri.Gateway' does not exist in the specified Category (System.InvalidOperationException: экземпляр "Microsoft.Tri.Gateway" не существует в указанной категории).|Идентификаторы процессов включены для имен процессов в шлюзе ATA.|Чтобы отключить их, ознакомьтесь со статьей [KB281884](https://support.microsoft.com/en-us/kb/281884).|
|System.InvalidOperationException: Category does not exist (System.InvalidOperationException: категория не существует).|Счетчики, возможно, отключены в реестре.|Чтобы перестроить счетчики производительности, ознакомьтесь со статьей [KB2554336](https://support.microsoft.com/en-us/kb/2554336).|
|System.ApplicationException: Unable to start ETW session MMA-ETW-Livecapture-a4f595bd-f567-49a7-b963-20fa4e370329 (System.ApplicationException: не удается запустить сеанс ETW MMA-ETW-Livecapture-a4f595bd-f567-49a7-b963-20fa4e370329)|Файл HOSTS, указывающий на имя компьютера, содержит запись узла.|Удалите запись узла из файла C:\Windows\System32\drivers\etc\HOSTS или сделайте ее полным доменным именем.|


## Ошибки ATA IIS (неприменимо для ATA 1.7 и более поздних версий)
|Ошибка|Описание|Разрешение|
|-------------|----------|---------|
|Ошибка HTTP 500.19 — внутренняя ошибка сервера|Не удалось правильно установить модуль переопределения URL-адресов для IIS.|Удалите и повторно установите модуль переопределения URL-адресов для IIS.<br>[Скачать модуль переопределения URL-адресов для IIS](http://go.microsoft.com/fwlink/?LinkID=615137)|

## Ошибки развертывания
|Ошибка|Описание|Разрешение|
|-------------|----------|---------|
|Происходит сбой установки .NET Framework 4.6.1 с ошибкой 0x800713ec|На сервере не установлены необходимые компоненты для платформы .NET Framework 4.6.1. |Перед установкой ATA убедитесь, что на сервере установлены обновления Windows [KB2919442](https://www.microsoft.com/download/details.aspx?id=42135) и [KB2919355](https://support.microsoft.com/kb/2919355).|

![Изображение ошибки установки .NET для ATA](media/netinstallerror.png)


## См. также
- [Предварительные требования для ATA](/advanced-threat-analytics/plan-design/ata-prerequisites)
- [Планирование производительности ATA](/advanced-threat-analytics/plan-design/ata-capacity-planning)
- [Настройка сбора данных о событиях](/advanced-threat-analytics/deploy-use/configure-event-collection)
- [Настройка пересылки событий Windows](/advanced-threat-analytics/deploy-use/configure-event-collection#configuring-windows-event-forwarding)
- [Обязательно ознакомьтесь с форумом ATA.](https://social.technet.microsoft.com/Forums/security/home?forum=mata)



<!--HONumber=Aug16_HO5-->


