---
title: "Устранение неполадок по журналу ошибок ATA | Документация Майкрософт"
description: "В этой статье описываются способы устранения распространенных ошибок в ATA"
keywords: 
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 10/25/2016
ms.topic: article
ms.prod: 
ms.service: advanced-threat-analytics
ms.technology: 
ms.assetid: d89e7aff-a6ef-48a3-ae87-6ac2e39f3bdb
ms.reviewer: bennyl
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 3ba53b7b1c34359f00da9fc9717496cfc7d4271d
ms.openlocfilehash: 8687263977c7bfdf12581a200bba3a60633fca4d


---

*Область применения: Advanced Threat Analytics версии 1.7*



# <a name="troubleshooting-the-ata-error-log"></a>Устранение неполадок журнала ошибок ATA
В этом разделе подробно описываются возможные ошибки в развертываниях ATA и действия, необходимые для их устранения.
## <a name="ata-gateway-errors"></a>Ошибки шлюза ATA
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
|System.IO.IOException: проверка подлинности не пройдена из-за закрытия транспортного потока удаленной стороной.|Протокол TLS 1.0 отключен в шлюзе ATA, но для .NET настроено использование TLS 1.2.|Используйте один из следующих вариантов: </br> Включите TLS 1.0 в шлюзе ATA. </br>Включите TLS 1.2 в .NET, настроив в разделах реестра использование стандартных значений операционной системы для LLS и TLS: `[HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\.NETFramework\v4.0.30319] "SystemDefaultTlsVersions"=dword:00000001` </br>`[HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\.NETFramework\v4.0.30319] "SystemDefaultTlsVersions"`|



## <a name="ata-lightweight-gateway-errors"></a>Ошибки в упрощенных шлюзах ATA

**Ошибка**. Оповещения о пропущенном трафике зеркального отражения портов при использовании упрощенного шлюза в VMware.

**Описание**. Если используются контроллеры доменов на виртуальных машинах VMware, вам могут приходить оповещения о **пропущенном сетевом трафике зеркального отражения портов**. Это происходит из-за несоответствия конфигурации в VMware. 
**Решение**. Чтобы избежать этих оповещений, задайте значение "0" или "Disabled" (Отключено) для следующих параметров: TsoEnable, LargeSendOffload, IPv4 и TSO Offload. Кроме того, рекомендуется отключить IPv4 Giant TSO Offload. Для получения дополнительной информации обратитесь к документации VMware.


## <a name="ata-iis-errors-not-applicable-for-ata-v17-and-above"></a>Ошибки ATA IIS (неприменимо для ATA 1.7 и более поздних версий)
|Ошибка|Описание|Разрешение|
|-------------|----------|---------|
|Ошибка HTTP 500.19 — внутренняя ошибка сервера|Не удалось правильно установить модуль переопределения URL-адресов для IIS.|Удалите и повторно установите модуль переопределения URL-адресов для IIS.<br>[Скачать модуль переопределения URL-адресов для IIS](http://go.microsoft.com/fwlink/?LinkID=615137)|

## <a name="deployment-errors"></a>Ошибки развертывания
|Ошибка|Описание|Разрешение|
|-------------|----------|---------|
|Происходит сбой установки .NET Framework 4.6.1 с ошибкой 0x800713ec|На сервере не установлены необходимые компоненты для платформы .NET Framework 4.6.1. |Перед установкой ATA убедитесь, что на сервере установлены обновления Windows [KB2919442](https://www.microsoft.com/download/details.aspx?id=42135) и [KB2919355](https://support.microsoft.com/kb/2919355).|

![Изображение ошибки установки .NET для ATA](media/netinstallerror.png)


## <a name="see-also"></a>См. также
- [Предварительные требования ATA](/advanced-threat-analytics/plan-design/ata-prerequisites)
- [Планирование производительности ATA](/advanced-threat-analytics/plan-design/ata-capacity-planning)
- [Настройка сбора данных о событиях](/advanced-threat-analytics/deploy-use/configure-event-collection)
- [Настройка пересылки событий Windows](/advanced-threat-analytics/deploy-use/configure-event-collection#configuring-windows-event-forwarding)
- [Ознакомьтесь с форумом ATA.](https://social.technet.microsoft.com/Forums/security/home?forum=mata)



<!--HONumber=Nov16_HO4-->


