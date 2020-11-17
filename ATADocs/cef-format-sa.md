---
title: Справочник по журналу ATA SIEM | Документы Майкрософт
description: Предоставляет примеры журналов оповещений системы безопасности, отправляемых из ATA в SIEM.
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 12/20/2018
ms.topic: conceptual
ms.prod: advanced-threat-analytics
ms.technology: ''
ms.assetid: 601b48ba-a327-4aff-a1f9-2377a2bb7a42
ms.reviewer: ort
ms.suite: ems
ms.openlocfilehash: fcab8aa33185b24f4ad1903c429b15decebf5e20
ms.sourcegitcommit: e844155ea57f73dfe2b47f4c5c1c7f5292ccbf1e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2020
ms.locfileid: "94690811"
---
# <a name="ata-siem-log-reference"></a>Справочник по журналу ATA SIEM


[!INCLUDE [Banner for top of topics](includes/banner.md)]

ATA может пересылать события оповещений о безопасности и работоспособности в SIEM. Оповещения переадресовываются в формате CEF. Ниже приведен пример каждого типа журнала оповещений системы безопасности для отправления в SIEM.

## <a name="sample-ata-security-alerts-in-cef-format"></a>Пример оповещений системы безопасности ATA в формате CEF
В систему SIEM пересылаются следующие поля и их значения:

- start — время появления оповещения;
- suser — учетная запись (обычно пользовательская), связанная с оповещением;
- shost — исходный компьютер, выдавший оповещение;
- outcome — оповещения с определенным успешным или неуспешным действием, выполненным в оповещении;  
- msg — описание оповещения;
- cnt — оповещение с числом выполнений подозрительного действия (например, число угаданных паролей при атаке методом подбора);
- app — протокол оповещений;
- externalId — идентификатор события, соответствующий оповещению, который ATA записывает в журнал событий*;
- cs#label и cs# — пользовательские строки, которые можно использовать в CEF. cs#label — это имя нового поля, а cs# — значение, например cs1Label=url cs1=https\://192.168.0.220/suspiciousActivity/5909ae198ca1ec04d05e65fa.

В этом примере cs1 — это поле, содержащее URL-адрес оповещения.

* При создании сценариев или автоматизации на основе журналов вместо использования имен журналов используйте постоянный externalID каждого журнала, так как имена журналов могут быть изменены без предварительного уведомления. 

|Имена оповещений|Идентификаторы событий оповещения|
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



## <a name="sample-logs"></a>Образцы журналов

Приоритеты: 3=низкий; 5=средний; 10=высокий.

### <a name="abnormal-modification-of-sensitive-groups"></a>аномальное изменение привилегированных групп;
1 2018-12-12T16:53:22.925757+00:00 CENTER ATA 4688 AbnormalSensitiveGroupMembership CEF:0|Microsoft|ATA|1.9.0.0|AbnormalSensitiveGroupMembershipChangeSuspiciousActivity|Неправильное изменение конфиденциальных групп|5|start=2018-12-12T18:52:58.0000000Z app=GroupMembershipChangeEvent suser=krbtgt msg=krbtgt нехарактерным образом изменило членство в конфиденциальных группах. externalId=2024 cs1Label=url cs1=https\://192.168.0.220/suspiciousActivity/5c113d028ca1ec1250ca0491

### <a name="brute-force-attack-using-ldap-simple-bind"></a>Атака методом подбора с помощью простой привязки LDAP
12-12-2018 19:52:18 auth. Warning 192.168.0.222 1 2018-12-12T17:52:18.899690 + 00:00 CENTER ATA 4688 ЛдапбрутефорцесуспиЦиаусактивити ‹ ̄ ̈ЦЕФ: 0 | Microsoft | ATA | 1.9.0.0 | ЛдапбрутефорцесуспиЦиаусактивити | Атака методом подбора с помощью простой привязки LDAP | 5 | Start = 2018-12-12T17:52:10.2350665 Z App = LDAP MSG = 10000, попыток подбора пароля в 100 учетных записей из W2012R2-000000-Server. Успешно определено один пароль учетной записи. externalId=2004 cs1Label=url cs1=https\://192.168.0.220/suspiciousActivity/5c114acb8ca1ec1250cacdcb

### <a name="encryption-downgrade-activity-golden-ticket"></a>Переход на использование более ранней версии шифрования (Golden Ticket)
12-12-2018 20:12:35 auth. Warning 192.168.0.222 1 2018-12-12T18:12:35.105942 + 00:00 CENTER ATA 4688 ЕнкриптиондовнградесуспиЦиаусакт ‹ ̄ ̈ЦЕФ: 0 | Microsoft | ATA | 1.9.0.0 | ЕнкриптиондовнградесуспиЦиаусактивити | Действие по переходу на предыдущее шифрование | 5 | Start = 2018-12-12T18:10:35.0334169 Z App = Kerberos MSG = метод шифрования поля TGT TGS_REQ сообщения от W2012R2-000000-Server был понижен на основе ранее полученного поведения. Это может быть результатом использования Golden Ticket на сервере W2012R2-000000-Server. externalId=2009 cs1Label=url cs1=https\://192.168.0.220/suspiciousActivity/5c114f938ca1ec1250cafcfa

### <a name="encryption-downgrade-activity-overpass-the-hash"></a>Переход на использование более ранней версии шифрования (Overpass-the-Hash)
12-12-2018 19:00:31 auth. Warning 192.168.0.222 1 2018-12-12T17:00:31.963485 + 00:00 CENTER ATA 4688 ЕнкриптиондовнградесуспиЦиаусакт ‹ ̄ ̈ЦЕФ: 0 | Microsoft | ATA | 1.9.0.0 | ЕнкриптиондовнградесуспиЦиаусактивити | Действие шифрования с переходом на более раннюю версию | 5 | Start = 2018-12-12T17:00:31.2975188 Z App = Kerberos MSG = метод шифрования поля Encrypted_Timestamp AS_REQ сообщения от W2012R2-000000-Server повышеен в соответствии с предыдущим поведением. Это может быть результатом кражи учетных данных с помощью атаки Overpass-the-Hash с сервера W2012R2-000000-Server. externalId=2010 cs1Label=url cs1=https\://192.168.0.220/suspiciousActivity/5c113eaf8ca1ec1250ca0883

###  <a name="encryption-downgrade-activity-skeleton-key"></a>переход на более слабое шифрование (вредоносные программы, использующие мастер-ключи);
12-12-2018 20:07:24 auth. Warning 192.168.0.222 1 2018-12-12T18:07:24.065140 + 00:00 CENTER ATA 4688 ЕнкриптиондовнградесуспиЦиаусакт ‹ ̄ ̈ЦЕФ: 0 | Microsoft | ATA | 1.9.0.0 | ЕнкриптиондовнградесуспиЦиаусактивити | Действие по переходу на предыдущее шифрование | 5 | Start = 2018-12-12T18:07:24.0222746 Z App = Kerberos MSG = метод шифрования поля ETYPE_INFO2 KRB_ERR сообщения от W2012R2-000000-Server был понижен на основе ранее полученного поведения. Это может быть результатом использования мастер-ключа в DC1. externalId=2011 cs1Label=url cs1=https\://192.168.0.220/suspiciousActivity/5c114e5c8ca1ec1250cafafe

### <a name="honeytoken-activity"></a>Действие Honeytoken
12-12-2018 19:51:52 auth. Warning 192.168.0.222 1 2018-12-12T17:51:52.659618 + 00:00 CENTER ATA 4688 ХонэйтокенактивитисуспиЦиаусакти ‹ ̄ ̈ЦЕФ: 0 | Microsoft | ATA | 1.9.0.0 | ХонэйтокенактивитисуспиЦиаусактивити | Действие Honeytoken | 5 | Start = 2018-12-12T17:51:52.5855994 Z App = Kerberos SUSE = USR78982 MSG = следующие действия выполнялись USR78982 LAST78982: \Р\наусентикатед с компьютера КЛИЕНТ1 с использованием NTLM при доступе к domain1. Test. локал\Цифс на DC1. externalId=2014 cs1Label=url cs1=https\://192.168.0.220/suspiciousActivity/5c114ab88ca1ec1250ca7f76

### <a name="identity-theft-using-pass-the-hash-attack"></a>Кража удостоверения с помощью атаки Pass-the-Hash
12-12-2018 19:56:02 auth. Error 192.168.0.222 1 2018-12-12T17:56:02.047236 + 00:00 CENTER ATA 4688 ПасссехашсуспиЦиаусактивити ‹ ̄ ̈ЦЕФ: 0 | Microsoft | ATA | 1.9.0.0 | ПасссехашсуспиЦиаусактивити | Кража удостоверений с помощью атаки Pass-a-hash | 10 | Start = 2018-12-12T17:54:01.9582400 Z приложение = NTLM SUSE = USR46829 LAST46829 MSG = USR46829 LAST46829's hash был украден с одного из компьютеров, ранее вошедших в USR46829 LAST46829, и использоваться из W2012R2-000000-Server. externalId=2017 cs1Label=url cs1=https\://192.168.0.220/suspiciousActivity/5c114bb28ca1ec1250caf673

### <a name="identity-theft-using-pass-the-ticket-attack"></a>Кража удостоверения с помощью атаки Pass-the-Ticket
12-12-2018 22:03:51 auth. Error 192.168.0.222 1 2018-12-12T20:03:51.643633 + 00:00 CENTER ATA 4688 ПасссетиккетсуспиЦиаусактивити ‹ ̄ ̈ЦЕФ: 0 | Microsoft | ATA | 1.9.0.0 | ПасссетиккетсуспиЦиаусактивити | Хищение личных идентификаторов с помощью атаки Pass-a-Ticket | 10 | Start = 2018-12-12T17:54:12.9960662 Z App = Kerberos SUSE = Бирдие Лэмб MSG = Бирдие Лэмб (программный инженер) билеты Kerberos были украдены с W2012R2-000106-Server до W2012R2-000051-Server и использоваться для доступа к domain1. Test. локал\хост. externalId=2018 cs1Label=url cs1=https\://192.168.0.220/suspiciousActivity/5c114b458ca1ec1250caf5b7

### <a name="kerberos-golden-ticket-activity"></a>действие с использованием "золотого" билета Kerberos;
12-12-2018 19:53:26 auth. Error 192.168.0.222 1 2018-12-12T17:53:26.869091 + 00:00 CENTER ATA 4688 ГолдентиккетсуспиЦиаусактивити ‹ ̄ ̈ЦЕФ: 0 | Microsoft | ATA | 1.9.0.0 | ГолдентиккетсуспиЦиаусактивити | Действие по предопределенному билету Kerberos | 10 | Start = 2018-12-13T06:51:26.7290524 Z App = Kerberos SUSE = Сонжа Чадсэй MSG = подозрительное использование билета Kerberos Сонжа Чадсэй (программного инженера), которое указывает на возможную атаку с золотым билетом. externalId=2022 cs1Label=url cs1=https\://192.168.0.220/suspiciousActivity/5c114b168ca1ec1250caf556

### <a name="malicious-data-protection-private-information-request"></a>Вредоносный запрос конфиденциальных сведений для защиты данных
12-12-2018 20:03:49 auth. Error 192.168.0.222 1 2018-12-12T18:03:49.814620 + 00:00 CENTER ATA 4688 Ретриеведатапротектионбаккупкэйс ‹ ̄ ̈ЦЕФ: 0 | Microsoft | ATA | 1.9.0.0 | РетриеведатапротектионбаккупкэйсуспиЦиаусактивити | Запрос частной информации о защите данных от вредоносных программ | 10 | начало = 2018-12-12T17:58:56.3537533 Z App = LsaRpc shost = W2012R2-000000-Server MSG = неизвестный пользователь успешно выполнил попытку от W2012R2-000000-Server получить ключ резервного копирования домена DPAPI с DC1. externalId=2020 cs1Label=url cs1=https\://192.168.0.220/suspiciousActivity/5c114d858ca1ec1250caf983

### <a name="malicious-replication-of-directory-services"></a>Вредоносная репликация служб каталогов
12-12-2018 19:56:49 auth. Error 192.168.0.222 1 2018-12-12T17:56:49.312648 + 00:00 CENTER ATA 4688 Директорисервицесрепликатионсусп ‹ ̄ ̈ЦЕФ: 0 | Microsoft | ATA | 1.9.0.0 | ДиректорисервицесрепликатионсуспиЦиаусактивити | Вредоносная репликация служб каталогов | 10 | Start = 2018-12-12T17:52:34.3287329 Z App = Drsr shost = W2012R2-000000-Server MSG = вредоносные запросы на репликацию успешно выполнены из W2012R2-000000-Server для DC1. outcome=Success externalId=2006 cs1Label=url cs1=https\://192.168.0.220/suspiciousActivity/5c114be18ca1ec1250caf6b8

### <a name="privilege-escalation-using-forged-authorization-data"></a>Атака, направленная на повышение привилегий с использованием поддельных данных авторизации
12-12-2018 19:51:15 auth. Error 192.168.0.222 1 2018-12-12T17:51:15.658608 + 00:00 CENTER ATA 4688 ФоржедпаксуспиЦиаусактивити ‹ ̄ ̈ЦЕФ: 0 | Microsoft | ATA | 1.9.0.0 | ФоржедпаксуспиЦиаусактивити | Укрупнение привилегий с использованием подложных данных авторизации | 10 | Start = 2018-12-12T17:51:15.0261128 Z App = Kerberos SUSE = трисервице MSG = трисервице попытались расширить привилегии для DC1 с W2012R2-000000-Server, используя подложные данные авторизации. externalId=2013 cs1Label=url cs1=https\://192.168.0.220/suspiciousActivity/5c114a938ca1ec1250ca7f48

### <a name="reconnaissance-using-directory-services-queries"></a>Рекогносцировка с использованием запросов к службам каталогов
12-12-2018 20:23:52 auth. Warning 192.168.0.222 1 2018-12-12T18:23:52.155531 + 00:00 CENTER ATA 4688 СамрреконнаиссанцесуспиЦиаусакти ‹ ̄ ̈ЦЕФ: 0 | Microsoft | ATA | 1.9.0.0 | СамрреконнаиссанцесуспиЦиаусактивити | Разведывательная атака с использованием запросов к службам каталогов | 5 | Start = 2018-12-12T18:04:12.9868815 Z App = SAMR shost = W2012R2-000000-Server MSG = следующие запросы служб каталогов, использующие Протокол SAMR, были выполнены для DC1 из W2012R2-000000-Server: \ Р\нсукцессфул запрос о построителях входящих доверий лесов (члены этой группы могут создавать входящие, односторонние отношения доверия для этого леса) в domain1. Test. local externalId = 2021 cs1Label = URL CS1 = HTTPS \: //192.168.0.220/suspiciousActivity/5c114e758ca1ec1250cafb2e

### <a name="reconnaissance-using-account-enumeration"></a>Разведывательная атака с использованием перечисления учетных записей.
1 2018-12-12T16:57:09.661680+00:00 CENTER ATA 4688 AccountEnumerationSuspiciousActi CEF:0|Microsoft|ATA|1.9.0.0|AccountEnumerationSuspiciousActivity|Рекогносцировка с использованием перечисления учетных записей|5|start=2018-12-12T16:57:09.1706828Z app=Kerberos shost=W2012R2-000000-Server msg=Обнаружено подозрительное перечисление учетных записей с использованием протокола Kerberos с сервера W2012R2-000000-Server. Злоумышленник предпринял всего 100 попыток подобрать имена учетных записей; 1 попытка подбора имени совпала с имеющимися именами учетных записей в Active Directory. externalId=2003 cs1Label=url cs1=https\://192.168.0.220/suspiciousActivity/5c113de58ca1ec1250ca06d8

### <a name="reconnaissance-using-dns"></a>Разведывательная атака с использованием DNS.
1 2018-12-12T16:57:20.743634+00:00 CENTER ATA 4688 DnsReconnaissanceSuspiciousActiv CEF:0|Microsoft|ATA|1.9.0.0|DnsReconnaissanceSuspiciousActivity|Рекогносцировка с использованием DNS|5|start=2018-12-12T16:57:20.2556472Z app=Dns shost=W2012R2-000000-Server msg=Обнаружена подозрительная активность DNS с сервера W2012R2-000000-Server (не являющегося DNS-сервером) в DC1. externalId=2007 cs1Label=url cs1=https\://192.168.0.220/suspiciousActivity/5c113df08ca1ec1250ca074c

### <a name="reconnaissance-using-smb-session-enumeration"></a>Рекогносцировка с использованием перечисления сеансов SMB
12-12-2018 19:50:51 auth. Warning 192.168.0.222 1 2018-12-12T17:50:51.090247 + 00:00 CENTER ATA 4688 ЕнумератесессионссуспиЦиаусактив ‹ ̄ ̈ЦЕФ: 0 | Microsoft | ATA | 1.9.0.0 | ЕнумератесессионссуспиЦиаусактивити | Разведывательная атака, использующий перечисление сеансов SMB | 5 | Start = 2018-12-12T17:00:42.7234229 Z App = SrvSvc shost = W2012R2-000000-Server MSG = неудачные попытки перечисления сеансов SMB от W2012R2-000000-Server к DC1. Учетные записи не раскрыты. externalId=2012 cs1Label=url cs1=https\://192.168.0.220/suspiciousActivity/5c114a788ca1ec1250ca7735

### <a name="remote-execution-attempt-detected"></a>Обнаружение попытки удаленного выполнения
12-12-2018 19:58:45 auth. Warning 192.168.0.222 1 2018-12-12T17:58:45.082799 + 00:00 CENTER ATA 4688 РемотиксекутионсуспиЦиаусактивит ‹ ̄ ̈ЦЕФ: 0 | Microsoft | ATA | 1.9.0.0 | РемотиксекутионсуспиЦиаусактивити | Обнаружена попытка удаленного выполнения | 5 | Start = 2018-12-12T17:54:23.9523766 Z shost = W2012R2-000000-Server MSG = следующие попытки удаленного выполнения были выполнены на DC1 с W2012R2-000000-Server: \ Р\нфаилед удаленное планирование одной или нескольких задач. externalId=2019 cs1Label=url cs1=https\://192.168.0.220/suspiciousActivity/5c114c548ca1ec1250caf783

### <a name="unusual-protocol-implementation"></a>Внедрение нестандартных протоколов.
1 2018-12-12T16:50:46.930234+00:00 CENTER ATA 4688 AbnormalProtocolSuspiciousActivi CEF:0|Microsoft|ATA|1.9.0.0|AbnormalProtocolSuspiciousActivity|Внедрение нестандартных протоколов|5|start=2018-12-12T16:48:46.6480337Z app=Ntlm shost=W2012R2-000000-Server outcome=Success msg=triservice успешно прошел проверку подлинности с сервера W2012R2-000000-Server относительно DC1 с использованием внедрения нестандартных протоколов. Это может быть результатом использования вредоносных средств для проведения таких атак, как Pass-the-Hash или атака методом подбора. externalId=2002 cs1Label=url cs1=https\://192.168.0.220/suspiciousActivity/5c113c668ca1ec1250ca0397

### <a name="suspicion-of-identity-theft-based-on-abnormal-behavior"></a>Подозрение на кражу идентификационных данных на основе аномального поведения
1 2018-12-12T16:50:35.746877+00:00 CENTER AТA 4688 AbnormalBehaviorSuspiciousActivi CEF:0|Microsoft|ATA|1.9.0.0|AbnormalBehaviorSuspiciousActivity|Подозрение на кражу идентификационных данных на основе аномального поведения|5|start=2018-12-12T16:48:35.5501183Z app=Kerberos suser=USR45964 msg=USR45964 LAST45964 демонстрирует аномальное поведение при выполнении действий, которые не наблюдались за последний месяц и также не соответствуют действиям других учетных записей в организации. Аномальное поведение зависит от следующих действий.\r\nВыполнено интерактивный вход из 30 неправильных рабочих станций.\r\nЗапрошено доступ к 30 аномальным ресурсам. externalId=2001 cs1Label=url cs1=https\://192.168.0.220/suspiciousActivity/5c113c5b8ca1ec1250ca0355

### <a name="suspicious-authentication-failures"></a>Подозрительные неудачные попытки проверки подлинности
12-12-2018 19:50:34 auth. Warning 192.168.0.222 1 2018-12-12T17:04:25.214067 + 00:00 CENTER ATA 4688 БрутефорцесуспиЦиаусактивити ‹ ̄ ̈ЦЕФ: 0 | Microsoft | ATA | 1.9.0.0 | БрутефорцесуспиЦиаусактивити | Подозрительные ошибки проверки подлинности | 5 | Start = 2018-12-12T17:03:58.5892462 Z App = Kerberos shost = W2012R2-000106-Server MSG = подозрительные сбои проверки подлинности, указывающие на то, что в W2012R2-000106-Server обнаружена потенциальная атака методом подбора. externalId=2023 cs1Label=url cs1=https\://192.168.0.220/suspiciousActivity/5c113f988ca1ec1250ca5810

### <a name="suspicious-service-creation"></a>Создание подозрительной службы
12-12-2018 19:53:49 auth. Warning 192.168.0.222 1 2018-12-12T17:53:49.913034 + 00:00 CENTER ATA 4688 МалиЦиауссервицекреатионсуспиЦио ‹ ̄ ̈ЦЕФ: 0 | Microsoft | ATA | 1.9.0.0 | МалиЦиауссервицекреатионсуспиЦиаусактивити | Создание подозрительных служб | 5 | Start = 2018-12-12T19:53:49.0000000 Z App = Сервицеинсталледевент shost = W2012R2-000000-Server MSG = трисервице Create Факесервице для выполнения потенциально вредоносных команд на W2012R2-000000-Server. externalId=2026 cs1Label=url cs1=https\://192.168.0.220/suspiciousActivity/5c114b2d8ca1ec1250caf577

## <a name="health-alerts"></a>Оповещения о работоспособности

### <a name="gatewaydisconnectedmonitoringalert"></a>GatewayDisconnectedMonitoringAlert
1 2018-12-12T16:52:41.520759+00:00 CENTER ATA 4688 GatewayDisconnectedMonitoringAle CEF:0|Microsoft|ATA|1.9.0.0|GatewayDisconnectedMonitoringAlert|GatewayDisconnectedMonitoringAlert|5|externalId=1011 cs1Label=url cs1=https\://192.168.0.220/monitoring msg=На протяжении 5 минут отсутствовал обмен данными в Gateway CENTER. Последний обмен данными был 12 декабря 2018 г. в 16:47:03 UTC.

### <a name="gatewaystartfailuremonitoringalert"></a>GatewayStartFailureMonitoringAlert
1 2018-12-12T15:36:59.701097+00:00 CENTER ATA 1372 GatewayStartFailureMonitoringAle CEF:0|Microsoft|ATA|1.9.0.0|GatewayStartFailureMonitoringAlert|GatewayStartFailureMonitoringAlert|5|externalId=1018 cs1Label=url cs1=https\://192.168.0.220/monitoring msg=Не удалось запустить службу шлюзов на DC1. Последний раз она была запущена 12 декабря 2018 г. в 15:04:12 UTC.

> [!NOTE]
> Все оповещения о работоспособности отправляются с тем же шаблоном, что и выше.


## <a name="see-also"></a>См. также:
- [Предварительные требования ATA](ata-prerequisites.md)
- [Планирование производительности ATA](ata-capacity-planning.md)
- [Настройка сбора данных о событиях](configure-event-collection.md)
- [Настройка пересылки событий Windows](configure-event-collection.md)
- [Обязательно ознакомьтесь с форумом ATA.](https://social.technet.microsoft.com/Forums/security/home?forum=mata)
