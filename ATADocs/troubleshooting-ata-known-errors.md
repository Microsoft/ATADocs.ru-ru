---
title: "Устранение известных неполадок ATA | Документы Майкрософт"
description: "Описывается устранение известных ошибок в ATA."
keywords: 
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 8/6/2017
ms.topic: article
ms.prod: 
ms.service: advanced-threat-analytics
ms.technology: 
ms.assetid: d89e7aff-a6ef-48a3-ae87-6ac2e39f3bdb
ms.reviewer: arzinger
ms.suite: ems
ms.openlocfilehash: 675543c11e07bcc243131e2350cfb33bfe8e7e39
ms.sourcegitcommit: 28f5d0f39149955c0d1059e13db289d13be9b642
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/07/2017
---
*Применяется к Advanced Threat Analytics версии 1.8*



# <a name="troubleshooting-ata-known-issues"></a>Устранение известных неполадок ATA

В этом разделе подробно описываются возможные ошибки в развертываниях ATA и действия, необходимые для их устранения.

## <a name="ata-gateway-and-lightweight-gateway-errors"></a>Ошибки шлюза ATA и упрощенного шлюза ATA

> [!div class="mx-tableFixed"]
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
|System.InvalidOperationException: Instance 'Microsoft.Tri.Gateway' does not exist in the specified Category (System.InvalidOperationException: экземпляр "Microsoft.Tri.Gateway" не существует в указанной категории).|Идентификаторы процессов включены для имен процессов в шлюзе ATA.|Чтобы отключить их, ознакомьтесь со статьей [KB281884](https://support.microsoft.com/kb/281884).|
|System.InvalidOperationException: Category does not exist (System.InvalidOperationException: категория не существует).|Счетчики, возможно, отключены в реестре.|Чтобы перестроить счетчики производительности, ознакомьтесь со статьей [KB2554336](https://support.microsoft.com/kb/2554336).|
|System.ApplicationException: Unable to start ETW session MMA-ETW-Livecapture-a4f595bd-f567-49a7-b963-20fa4e370329 (System.ApplicationException: не удается запустить сеанс ETW MMA-ETW-Livecapture-a4f595bd-f567-49a7-b963-20fa4e370329)|Файл HOSTS, указывающий на имя компьютера, содержит запись узла.|Удалите запись узла из файла C:\Windows\System32\drivers\etc\HOSTS или сделайте ее полным доменным именем.|
|System.IO.IOException: проверка подлинности не пройдена из-за закрытия транспортного потока удаленной стороной.|Протокол TLS 1.0 отключен в шлюзе ATA, но для .NET настроено использование TLS 1.2|Используйте один из следующих вариантов: </br> Включите TLS 1.0 в шлюзе ATA. </br>Чтобы включить TLS 1.2 в .NET, настройте в разделах реестра использование значений операционной системы по умолчанию для SSL и TLS: </br>`[HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\.NETFramework\v4.0.30319] "SystemDefaultTlsVersions"=dword:00000001` </br>`[HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\.NETFramework\v4.0.30319] "SystemDefaultTlsVersions"=dword:00000001`</br>`[HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\.NETFramework\v4.0.30319] "SchUseStrongCrypto"=dword:00000001 `</br>
`[HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\.NETFramework\v4.0.30319] " SchUseStrongCrypto"=dword:00000001`|
|System.TypeLoadException: не удалось загрузить тип "Microsoft.Opn.Runtime.Values.BinaryValueBufferManager" из сборки "Microsoft.Opn.Runtime, Version=4.0.0.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35"|Шлюзу ATA не удалось загрузить необходимые файлы анализа.|Проверьте, установлен ли анализатор сообщений Майкрософт. Установка анализатора сообщений вместе со шлюзом ATA или упрощенным шлюзом ATA не поддерживается. Удалите анализатор сообщений и перезапустите службу шлюза.|
|Оповещения о пропущенном трафике зеркального отражения портов при использовании упрощенного шлюза в VMware|Если используются контроллеры домена на виртуальных машинах VMware, вам могут приходить оповещения о **пропущенном сетевом трафике зеркального отражения портов**. Это происходит из-за несоответствия конфигурации в VMware. |Чтобы избежать этих оповещений, задайте значение «0» или «Отключено» для следующих параметров: TsoEnable, LargeSendOffload, IPv4 и TSO Offload. Кроме того, рекомендуется отключить IPv4 Giant TSO Offload. Для получения дополнительной информации обратитесь к документации VMware.|
|System.Net.WebException: удаленный сервер вернул ошибку: требуется проверка подлинности прокси-сервера (407)|Связь шлюза ATA с центром ATA прерывается прокси-сервером.|Отключите прокси-сервер на компьютере со шлюзом ATA. <br></br>Обратите внимание, что параметры прокси-сервера могут применяться к отдельным учетным записям.|
|System.IO.DirectoryNotFoundException: система не может найти указанный путь. (Исключение из HRESULT: 0x80070003)|Не запущена одна или несколько служб, необходимых для работы ATA.|Запустите следующие службы: <br></br>Журналы и оповещения производительности (PLA), планировщик задач (расписание).|
|System.Net.WebException: удаленный сервер возвратил ошибку "403 —запрещено".|Шлюзу ATA или упрощенному шлюзу было отказано в установлении HTTP-подключения, так как центр ATA не является доверенным.|Добавьте имя NetBIOS и полное доменное имя центра ATA в список доверенных веб-сайтов и очистите кэш браузера Interne Explorer. Если в конфигурации указано имя центра ATA, отличное от имени NetBIOS или полного доменного имени, укажите имя из конфигурации.|

## <a name="deployment-errors"></a>Ошибки развертывания
> [!div class="mx-tableFixed"]
|Ошибка|Описание|Разрешение|
|-------------|----------|---------|
|Происходит сбой установки .NET Framework 4.6.1 с ошибкой 0x800713ec|На сервере не установлены необходимые компоненты для платформы .NET Framework 4.6.1. |Перед установкой ATA убедитесь, что на сервере установлены обновления Windows [KB2919442](https://www.microsoft.com/download/details.aspx?id=42135) и [KB2919355](https://support.microsoft.com/kb/2919355).|
|System.Threading.Tasks.TaskCanceledException: отменена задача|Истекло время ожидания процесса развертывания, так как ему не удалось связаться с центром ATA.|1.    Проверьте сетевое подключение к центру ATA, перейдя по его IP-адресу в браузере. <br></br>2.    Проверьте конфигурацию прокси-сервера или брандмауэра.|
|System.Net.Http.HttpRequestException: произошла ошибка при отправке запроса. ---> System.Net.WebException: удаленный сервер возвратил ошибку: (407) Требуется проверка подлинности прокси.|Истекло время ожидания процесса развертывания, так как ему не удалось связаться с центром ATA из-за неправильной настройки прокси-сервера.|Отключите конфигурацию прокси-сервера перед развертыванием, а затем включите ее повторно. Вы также можете настроить исключение на прокси-сервере.|
|System.Net.Sockets.SocketException: существующее подключение было принудительно закрыто удаленным узлом|Используйте один из следующих вариантов: </br>Включите TLS 1.0 в шлюзе ATA. </br>Чтобы включить TLS 1.2 в .NET, настройте в разделах реестра использование значений операционной системы по умолчанию для SSL и TLS:</br> `[HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\.NETFramework\v4.0.30319] "SystemDefaultTlsVersions"=dword:00000001`</br> `[HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\.NETFramework\v4.0.30319] "SystemDefaultTlsVersions"=dword:00000001`</br>`[HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\.NETFramework\v4.0.30319] "SchUseStrongCrypto"=dword:00000001` </br>`[HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\.NETFramework\v4.0.30319] " SchUseStrongCrypto"=dword:00000001`


## <a name="ata-gateway-and-lightweight-gateway-issues"></a>Проблемы со шлюзом ATA и упрощенным шлюзом

> [!div class="mx-tableFixed"]
|Проблема|Описание|Разрешение|
|-------------|----------|---------|
|От контроллера домена не поступает трафик, но оповещения мониторинга выводятся|    От контроллера домена не поступает трафик с использованием зеркального отображения портов через шлюз ATA|В сетевом адаптере захвата в шлюзе ATA отключите следующие функции в разделе **Дополнительные параметры**:<br></br>объединение полученных сегментов (IPv4);<br></br>объединение полученных сегментов (IPv6).|
|Отображается следующее предупреждение системы мониторинга: **Часть сетевого трафика не анализируется**|Вы можете получить это предупреждение, если у вас есть шлюз ATA или упрощенный шлюз на виртуальных машинах VMware. Это происходит из-за несоответствия конфигураций в VMware.|Задайте в конфигурации сетевого адаптера виртуальной машины значения **0** или **Отключено** для следующих параметров: TsoEnable, LargeSendOffload, TSO Offload, Giant TSO Offload|Протокол TLS 1.0 отключен в шлюзе ATA, но для .NET настроено использование TLS 1.2|




## <a name="see-also"></a>См. также
- [Предварительные требования ATA](ata-prerequisites.md)
- [Планирование производительности ATA](ata-capacity-planning.md)
- [Настройка сбора данных о событиях](configure-event-collection.md)
- [Настройка пересылки событий Windows](configure-event-collection.md#configuring-windows-event-forwarding)
- [Ознакомьтесь с форумом ATA.](https://social.technet.microsoft.com/Forums/security/home?forum=mata)
