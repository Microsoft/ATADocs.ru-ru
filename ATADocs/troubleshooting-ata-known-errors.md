---
title: Устранение известных неполадок ATA | Документы Майкрософт
description: Описывается устранение известных ошибок в ATA.
keywords: ''
author: mlottner
ms.author: mlottner
manager: barbkess
ms.date: 7/25/2018
ms.topic: conceptual
ms.prod: advanced-threat-analytics
ms.service: ''
ms.technology: ''
ms.assetid: d89e7aff-a6ef-48a3-ae87-6ac2e39f3bdb
ms.reviewer: arzinger
ms.suite: ems
ms.openlocfilehash: bf014e43711d45b74d5bb5efa7a93d7c3e1532d7
ms.sourcegitcommit: 78748bfd75ae68230d72ad11010ead37d96b0c58
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/12/2019
ms.locfileid: "56077734"
---
# <a name="troubleshooting-ata-known-issues"></a>Устранение известных неполадок ATA


*Область применения: Advanced Threat Analytics версии 1.9*

В этом разделе подробно описываются возможные ошибки в развертываниях ATA и действия, необходимые для их устранения.

## <a name="ata-gateway-and-lightweight-gateway-errors"></a>Ошибки шлюза ATA и упрощенного шлюза ATA

> [!div class="mx-tableFixed"]
> 
> |Ошибка|Описание|Решение|
> |-------------|----------|---------|
> |System.DirectoryServices.Protocols.LdapException: A local error occurred|Шлюзу ATA не удалось выполнить аутентификацию в контроллере домена.|1. Убедитесь, что запись DNS контроллера домена на DNS-сервере настроена надлежащим образом. <br>2. Убедитесь, что время шлюза ATA синхронизировано с временем контроллера домена.|
> |System.IdentityModel.Tokens.SecurityTokenValidationException: Failed to validate certificate chain|Шлюзу ATA не удалось проверить сертификат центра ATA.|1. Убедитесь, что сертификат корневого ЦС установлен в хранилище сертификатов доверенного центра сертификации на шлюзе ATA. <br>2. Убедитесь, что список отзыва сертификатов доступен и можно выполнить проверку отзыва сертификатов.|
> |Microsoft.Common.ExtendedException: Failed to parse time generated|Шлюзу ATA не удалось проанализировать сообщения системного журнала, пересланные с SIEM.|Убедитесь, что SIEM настроен для пересылки сообщений в одном из форматов, поддерживаемых ATA.|
> |System.ServiceModel.FaultException: An error occurred when verifying security for the message.|Шлюзу ATA не удалось выполнить аутентификацию в центре ATA.|Убедитесь, что время шлюза ATA синхронизировано с временем центра ATA.|
> |System.ServiceModel.EndpointNotFoundException: Could not connect to net.tcp://center.ip.addr:443/IEntityReceiver|Шлюзу ATA не удалось установить подключение к центру ATA.|Убедитесь, что параметры сети правильные, а сетевое подключение между шлюзом ATA и центром ATA активно.|
> |System.DirectoryServices.Protocols.LdapException: The LDAP server is unavailable.|Шлюзу ATA не удалось выполнить запрос к контроллеру домена, используя протокол LDAP.|1. Убедитесь, что учетная запись пользователя, используемая ATA для подключения к домену Active Directory, имеет доступ на чтение для всех объектов в дереве Active Directory. <br>2. Убедитесь, что в контроллере домена не настроена защита, которая предотвращает выполнение запросов LDAP из учетной записи пользователя, используемой ATA.|
> |Microsoft.Tri.Infrastructure.ContractException: Contract exception|Шлюзу ATA не удалось синхронизировать конфигурацию из центра ATA.|Завершите настройку шлюза ATA в консоли ATA.|
> |System.Reflection.ReflectionTypeLoadException: Unable to load one or more of the requested types. Для получения дополнительных сведений извлеките свойство LoaderExceptions.|Анализатор сообщений устанавливается в шлюзе ATA.| Удалите анализатор сообщений.|
> |Error [Layout] System.OutOfMemoryException: Exception of type 'System.OutOfMemoryException' was thrown.|В шлюзе ATA недостаточно памяти.|Увеличьте объем памяти в контроллере домена.|
> |Fail to start live consumer  ---> Microsoft.Opn.Runtime.Monitoring.MessageSessionException: The PEFNDIS event provider is not ready|PEF (анализатор сообщений) неправильно установлен.|Если вы используете Hyper-V, попробуйте обновить службы интеграции Hyper-V по-другому. Чтобы найти временное решение, обратитесь в службу поддержки.|
> |Installation failed with error: 0x80070652|На компьютере есть другие незавершенные установки.|Дождитесь завершения других установок и при необходимости перезагрузите компьютер.|
> |System.InvalidOperationException: Instance 'Microsoft.Tri.Gateway' does not exist in the specified Category.|Идентификаторы процессов включены для имен процессов в шлюзе ATA.|Чтобы отключить их, ознакомьтесь со статьей [KB281884](https://support.microsoft.com/kb/281884).|
> |System.InvalidOperationException: Category does not exist.|Счетчики, возможно, отключены в реестре.|Чтобы перестроить счетчики производительности, ознакомьтесь со статьей [KB2554336](https://support.microsoft.com/kb/2554336).|
> |System.ApplicationException: Unable to start ETW session MMA-ETW-Livecapture-a4f595bd-f567-49a7-b963-20fa4e370329|Файл HOSTS, указывающий на имя компьютера, содержит запись узла.|Удалите запись узла из файла C:\Windows\System32\drivers\etc\HOSTS или сделайте ее полным доменным именем.|
> |System.IO.IOException: Authentication failed because the remote party has closed the transport stream.|Протокол TLS 1.0 отключен в шлюзе ATA, но для .NET настроено использование TLS 1.2|Используйте один из следующих вариантов: </br> Включите TLS 1.0 в шлюзе ATA. </br>Чтобы включить TLS 1.2 в .NET, настройте в разделах реестра использование значений операционной системы по умолчанию для SSL и TLS: </br>`[HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\.NETFramework\v4.0.30319] "SystemDefaultTlsVersions"=dword:00000001` </br>`[HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\.NETFramework\v4.0.30319] "SystemDefaultTlsVersions"=dword:00000001`</br>`[HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\.NETFramework\v4.0.30319] "SchUseStrongCrypto"=dword:00000001 `</br>`[HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\.NETFramework\v4.0.30319] " SchUseStrongCrypto"=dword:00000001`|
> |System.TypeLoadException: Could not load type 'Microsoft.Opn.Runtime.Values.BinaryValueBufferManager' from assembly 'Microsoft.Opn.Runtime, Version=4.0.0.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35'|Шлюзу ATA не удалось загрузить необходимые файлы анализа.|Проверьте, установлен ли анализатор сообщений Майкрософт. Установка анализатора сообщений вместе со шлюзом ATA или упрощенным шлюзом ATA не поддерживается. Удалите анализатор сообщений и перезапустите службу шлюза.|
> |System.Net.WebException: The remote server returned an error: (407) Proxy Authentication Required|Связь шлюза ATA с центром ATA прерывается прокси-сервером.|Отключите прокси-сервер на компьютере со шлюзом ATA. <br></br>Обратите внимание, что параметры прокси-сервера могут применяться к отдельным учетным записям.|
> |System.IO.DirectoryNotFoundException: Системе не удается найти указанный путь. (Исключение из HRESULT: 0x80070003)|Не запущена одна или несколько служб, необходимых для работы ATA.|Запустите следующие службы: <br></br>Журналы и оповещения производительности (PLA), планировщик задач (расписание).|
> |System.Net.WebException: The remote server returned an error: (403) Forbidden|Шлюзу ATA или упрощенному шлюзу было отказано в установлении HTTP-подключения, так как центр ATA не является доверенным.|Добавьте имя NetBIOS и полное доменное имя центра ATA в список доверенных веб-сайтов и очистите кэш браузера Interne Explorer. Если в конфигурации указано имя центра ATA, отличное от имени NetBIOS или полного доменного имени, укажите имя из конфигурации.|
> |System.Net.Http.HttpRequestException: PostAsync failed [requestTypeName=StopNetEventSessionRequest]|Шлюзу ATA или упрощенному шлюзу ATA не удается остановить и запустить сеанс трассировки событий Windows, в котором собирается трафик, из-за проблемы с инструментарием WMI.|Чтобы устранить проблему с репозиторием WMI, следуйте инструкциям по [повторной сборке репозитория WMI](https://blogs.technet.microsoft.com/askperf/2009/04/13/wmi-rebuilding-the-wmi-repository/).|
> |System.Net.Sockets.SocketException: An attempt was made to access a socket in a way forbidden by its access permissions|Другое приложение использует порт 514 на шлюзе ATA|Используйте `netstat -o`, чтобы определить, какой процесс использует этот порт.|

## <a name="deployment-errors"></a>Ошибки развертывания
> [!div class="mx-tableFixed"]
> 
> |Ошибка|Описание|Решение|
> |-------------|----------|---------|
> |Происходит сбой установки .NET Framework 4.6.1 с ошибкой 0x800713ec|На сервере не установлены необходимые компоненты для платформы .NET Framework 4.6.1. |Перед установкой ATA убедитесь, что на сервере установлены обновления Windows [KB2919442](https://www.microsoft.com/download/details.aspx?id=42135) и [KB2919355](https://support.microsoft.com/kb/2919355).|
> |System.Threading.Tasks.TaskCanceledException: A task was canceled|Истекло время ожидания процесса развертывания, так как ему не удалось связаться с центром ATA.|1.    Проверьте сетевое подключение к центру ATA, перейдя по его IP-адресу в браузере. <br></br>2.    Проверьте конфигурацию прокси-сервера или брандмауэра.|
> |System.Net.Http.HttpRequestException: An error occurred while sending the request. ---> System.Net.WebException: The remote server returned an error: (407) Proxy Authentication Required.|Истекло время ожидания процесса развертывания, так как ему не удалось связаться с центром ATA из-за неправильной настройки прокси-сервера.|Отключите конфигурацию прокси-сервера перед развертыванием, а затем включите ее повторно. Вы также можете настроить исключение на прокси-сервере.|
> |System.Net.Sockets.SocketException: An existing connection was forcibly closed by the remote host||Используйте один из следующих вариантов: </br>Включите TLS 1.0 в шлюзе ATA. </br>Чтобы включить TLS 1.2 в .NET, настройте в разделах реестра использование значений операционной системы по умолчанию для SSL и TLS:</br> `[HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\.NETFramework\v4.0.30319] "SystemDefaultTlsVersions"=dword:00000001`</br> `[HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\.NETFramework\v4.0.30319] "SystemDefaultTlsVersions"=dword:00000001`</br>`[HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\.NETFramework\v4.0.30319] "SchUseStrongCrypto"=dword:00000001` </br>`[HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\.NETFramework\v4.0.30319] " SchUseStrongCrypto"=dword:00000001`|
> |Ошибка [\[]DeploymentModel[\]] Сбой аутентификации управления [\[]CurrentlyLoggedOnUser=<domain>\<имя_пользователя>Status=FailedAuthentication Exception=[\]]|При развертывании шлюза ATA и упрощенного шлюза ATA не удалось выполнить аутентификацию в центре ATA.|Откройте браузер на компьютере, где произошел сбой развертывания, и попробуйте получить доступ к консоли ATA. </br>Если это нельзя сделать, запустите процесс устранения неполадок, чтобы узнать, почему браузер не может выполнить аутентификацию в центре ATA. </br>Проверьте следующее: </br>настройки прокси-сервера;</br>возможные проблемы с сетью;</br>параметры групповой политики для аутентификации на этом компьютере, которые отличаются от параметров в центре ATA.|


## <a name="ata-center-errors"></a>Ошибки центра ATA
> [!div class="mx-tableFixed"]
> 
> |Ошибка|Описание|Решение|
> |-------------|----------|---------|
> |System.Security.Cryptography.CryptographicException: Доступ запрещен.|Центру ATA не удалось использовать выданный сертификат для расшифровки. Вероятно, это произошло из-за использования сертификата, в котором для KeySpec (KeyNumber) вместо KeyExchange (AT\_KEYEXCHANGE) задано значение Signature (AT\_SIGNATURE), что не поддерживается для расшифровки.|1.    Остановите службу центра ATA. <br></br>2.     Удалите сертификат центра АТА из хранилища сертификатов центра. (Перед удалением убедитесь, что у вас есть сертификат с копией закрытого ключа в PFX-файле.) <br></br>3.    Откройте командную строку с повышенными привилегиями и выполните certutil -importpfx "CenterCertificate.pfx" AT\_KEYEXCHANGE. <br></br>4.     Запустите службу центра ATA. <br></br>5.     Убедитесь, что теперь все работает правильно.|


## <a name="ata-gateway-and-lightweight-gateway-issues"></a>Проблемы со шлюзом ATA и упрощенным шлюзом

> [!div class="mx-tableFixed"]
> 
> |Проблема|Описание|Решение|
> |-------------|----------|---------|
> |От контроллера домена не поступает трафик, но оповещения мониторинга выводятся|    От контроллера домена не поступает трафик с использованием зеркального отображения портов через шлюз ATA|В сетевом адаптере захвата в шлюзе ATA отключите следующие функции в разделе **Дополнительные параметры**:<br></br>объединение полученных сегментов (IPv4);<br></br>объединение полученных сегментов (IPv6).|
> |Отображается следующее оповещение системы мониторинга: Часть сетевого трафика не анализируется|Вы можете получить это предупреждение, если у вас есть шлюз ATA или упрощенный шлюз на виртуальных машинах VMware. Это происходит из-за несоответствия конфигураций в VMware.|Установите следующие параметры равными 0 или отключите их в меню настройки сетевого адаптера виртуальной машины: TsoEnable, LargeSendOffload, TSO Offload, Giant TSO Offload. Протокол TLS 1.0 отключен в шлюзе ATA, но для .Net задано использование TLS 1.2.|





## <a name="see-also"></a>См. также
- [Предварительные требования ATA](ata-prerequisites.md)
- [Планирование производительности ATA](ata-capacity-planning.md)
- [Настройка сбора данных о событиях](configure-event-collection.md)
- [Настройка пересылки событий Windows](configure-event-collection.md)
- [Ознакомьтесь с форумом ATA.](https://social.technet.microsoft.com/Forums/security/home?forum=mata)
