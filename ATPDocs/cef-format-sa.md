---
title: Справочник по журналу Azure ATP SIEM | Документы Майкрософт
description: Примеры журналов подозрительных действий, отправляемых из Azure ATP в систему SIEM.
keywords: ''
author: mlottner
ms.author: mlottner
manager: mbaldwin
ms.date: 8/06/2018
ms.topic: article
ms.prod: ''
ms.service: azure-advanced-threat-protection
ms.technology: ''
ms.assetid: 3261155c-3c72-4327-ba29-c113c63a4e6d
ms.reviewer: arzinger
ms.suite: ems
ms.openlocfilehash: adfb47e8dd006b660c4a031080eaecd6d2d5be84
ms.sourcegitcommit: ca6153d046d8ba225ee5bf92cf55d0bd57cf4765
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/07/2018
ms.locfileid: "39585260"
---
*Применяется к: Azure Advanced Threat Protection*


# <a name="azure-atp-siem-log-reference"></a>Справочник по журналу Azure ATP SIEM

Azure ATP может пересылать события, связанные с подозрительными действиями и оповещениями мониторинга, в систему SIEM. События, связанные с подозрительными действиями, передаются в формате CEF. В этой справочной статье приводятся примеры журналов подозрительных действий, пересылаемых в систему SIEM.

## <a name="sample-azure-atp-suspicious-activities-in-cef-format"></a>Пример сведений о подозрительных действиях, обнаруженных Azure ATP, в формате CEF
В систему SIEM пересылаются следующие поля и их значения:

-   start — время начала оповещения;
-   suser — учетная запись (как правило, учетная запись пользователя), с которой связано оповещение;
-   shost — исходный компьютер оповещения;
-   outcome — указывает на успешность или неуспешность выполнения действия, указанного в оповещении;  
-   msg — описание оповещения;
-   cnt — число инициации оповещения (например, число угаданных паролей при атаке методом подбора);
-   app — протокол, используемый в оповещении;
-   externalId — идентификатор события, соответствующий оповещению, который Azure ATP записывает в журнал событий;
-   cs#label и cs# — пользовательские строки, которые можно использовать в CEF. cs#label — это имя нового поля, а cs# — значение, например cs1Label=url cs1=https://192.168.0.220/suspiciousActivity/5909ae198ca1ec04d05e65fa

В этом примере cs1 — это поле, содержащее URL-адрес оповещения.

## <a name="sample-logs"></a>Образцы журналов

Следующие примеры журналов соответствуют требованиям RFC 5242, но Azure ATP также поддерживает RFC 3164.

Уровни приоритета:

- 3 — низкий;
- 5 — средний;
- 10 — высокий.

### <a name="bruteforce--ldap"></a>Атака методом подбора — LDAP
02-21-2018  16:20:21    Auth.Warning    192.168.0.220   1 2018-02-21T14:20:06.156238+00:00 CENTER CEF 6076 LdapBruteForceSecurityAlert ï»¿0|Microsoft|Azure ATP|2.22.4228.22540|LdapBruteForceSecurityAlert|Атака методом подбора с использованием простой привязки LDAP|5|start=2018-02-21T14:19:41.7422810Z app=Ldap suser=Wofford Thurston shost=CLIENT1 msg=Предпринята попытка атаки методом подбора с использованием протокола Ldap в отношении Wofford Thurston (разработчика программного обеспечения) с компьютера CLIENT1 (100 попыток подбора). cnt=100 externalId=2004 cs1Label=url cs1=https://contoso-corp.atp.azure.com/securityAlert/57b8ac96-7907-4971-9b27-ec77ad8c029a


### <a name="bruteforce"></a>Атака методом подбора
02-21-2018  16:19:20    Auth.Warning    192.168.0.220   1 2018-02-21T14:19:15.397995+00:00 CENTER CEF 6076 BruteForceSecurityAlert ï»¿0|Microsoft|Azure ATP|2.22.4228.22540|BruteForceSecurityAlert|Подозрительные неудачные попытки проверки подлинности|5|start=2018-02-21T14:19:03.3831122Z app=Kerberos shost=CLIENT1 msg=Обнаружены исходящие с компьютера CLIENT1 подозрительные неудачные попытки проверки подлинности, означающие возможную атаку методом подбора. externalId=2023 cs1Label=url cs1=https://contoso-corp.atp.azure.com/securityAlert/fea88fc7-4110-454d-816d-349032474fd6
### <a name="privilege-escalation"></a>Повышение привилегий
#### <a name="silver"></a>"Серебряный" билет
02-21-2018  16:19:20    Auth.Error  192.168.0.220   1 2018-02-21T14:19:15.186167+00:00 CENTER CEF 6076 ForgedPacSecurityAlert ï»¿0|Microsoft|Azure ATP|2.22.4228.22540|ForgedPacSecurityAlert|Атака, направленная на повышение привилегий с использованием поддельных данных авторизации|10|start=2018-02-21T14:19:02.8595383Z app=Kerberos suser=user1 msg=Пользователь user1 попытался повысить привилегии до host/domain1.test.local с компьютера CLIENT1 с помощью поддельных данных авторизации. externalId=2013 cs1Label=url cs1=https://contoso-corp.atp.azure.com/securityAlert/029189e1-6bb4-490b-bcaf-5fac4457e9f3
#### <a name="gold"></a>Золотой
02-21-2018  16:19:20    Auth.Error  192.168.0.220   1 2018-02-21T14:19:14.358037+00:00 CENTER CEF 6076 ForgedPacSecurityAlert ï»¿0|Microsoft|Azure ATP|2.22.4228.22540|ForgedPacSecurityAlert|Атака, направленная на повышение привилегий с использованием поддельных данных авторизации|10|start=2018-02-21T14:19:02.8595383Z app=Kerberos suser=user1 msg=Пользователю user1 не удалось повысить привилегии DC1 до host/domain1.test.local с компьютера CLIENT1 с помощью поддельных данных авторизации. externalId=2013 cs1Label=url cs1=https://contoso-corp.atp.azure.com/securityAlert/f3359eff-cb59-44b9-82b6-5e82ff06e6c8
### <a name="golden-ticket"></a>Golden ticket
02-21-2018  16:22:39    Auth.Error  192.168.0.220   1 2018-02-21T14:22:34.274054+00:00 CENTER CEF 6076 GoldenTicketSecurityAlert ï»¿0|Microsoft|Azure ATP|2.22.4228.22540|GoldenTicketSecurityAlert|Действие с использованием "золотого" билета Kerberos|10|start=2018-02-21T14:19:03.2416152Z app=Kerberos suser=Lanell Campos msg=Обнаружено подозрительное использование билета Kerberos, принадлежащего Lanell Campos (разработчику программного обеспечения), что указывает на возможную атаку Golden ticket. externalId=2022 cs1Label=url cs1=https://contoso-corp.atp.azure.com/securityAlert/702c836e-6f49-4479-9892-80e8bccbfac0
### <a name="kerberos-golden-ticket-nonexistent-account"></a>Билет Kerberos Golden Ticket — несуществующая учетная запись
07-01-2018  14:28:49    Auth.Error  192.168.0.100   1 2018-07-01T11:28:35.546638+00:00 CENTER CEF 38768 ForgedPrincipalSecurityAlert ï»¿0|Microsoft|Расширенная защита SQL от угроз|2.39.0.0|ForgedPrincipalSecurityAlert|Билет Kerberos Golden Ticket — несуществующая учетная запись|10|start=2018-07-01T09:48:31.2567987Z app=Kerberos suser=domain1.test.local\fake msg=Учетная запись domain1.test.local\fake, которая не существует в Active Directory, использовала билет Kerberos. С 2 компьютеров был обнаружен билет, используемый для доступа к 3 ресурсам. Это может свидетельствовать о потенциальной атаке Golden Ticket. externalId=2027 cs1Label=url cs1=https://contoso-corp.atp.azure.com:13000/securityAlert/98f050d4-9134-429c-8e54-d8eeb19849c4


### <a name="honey-token-activity"></a>Активность учетной записи honeytoken
02-21-2018  16:20:36    Auth.Warning  192.168.0.220 1 2018-02-21T14:20:34.106162+00:00 CENTER CEF 6076 HoneytokenActivitySecurityAlert ï»¿0|Microsoft|Расширенная защита SQL от угроз|2.22.4228.22540|HoneytokenActivitySecurityAlert|Активность учетной записи honeytoken|5|start=2018-02-21T14:20:26.6705617Z app=Kerberos suser=honey msg=С помощью учетной записи honey были выполнены следующие действия:\r\nВход на компьютер CLIENT2 через DC1. externalId=2014 cs1Label=url cs1=https://contoso-corp.atp.azure.com/securityAlert/9249fe9a-c883-46dd-a4da-2a1fca5f211c
### <a name="suspicious-replication-of-directory-services"></a>Подозрительная репликация служб каталогов
02-21-2018  16:21:22    Auth.Error  192.168.0.220   1 2018-02-21T14:21:13.978554+00:00 CENTER CEF 6076 DirectoryServicesReplicationSecu ï»¿0|Microsoft|Azure ATP|2.22.4228.22540|DirectoryServicesReplicationSecurityAlert|Подозрительная репликация служб каталогов|10|start=2018-02-21T14:19:03.9975656Z app=Drsr shost=CLIENT1 msg=Пользователь user1 успешно выполнил запросы на подозрительную репликацию с компьютера CLIENT1 на DC1. outcome=Success externalId=2006 cs1Label=url cs1=https://contoso-corp.atp.azure.com/securityAlert/cb95648e-1b6f-4d3b-81b9-7605532787d7
### <a name="suspicious-replication-request-potential-dcshadow-attack"></a>Подозрительный запрос на репликацию (потенциальная атака DCShadow)
07-12-2018  11:18:37    Auth.Error  192.168.0.200    1 2018-07-12T08:18:32.265989+00:00 DC1 CEF 3868 DirectoryServicesRogueReplicatio ï»¿0|Microsoft|Расширенная защита SQL от угроз|2.40.0.0|DirectoryServicesRogueReplicationSecurityAlert|[ПРЕДВАРИТЕЛЬНАЯ ВЕРСИЯ] **Подозрительный запрос на репликацию (потенциальная атака DCShadow)**|10|start=2018-07-12T08:17:55.3816102Z **app=Replication Activity** shost=CLIENT1 msg=CLIENT1, который не является допустимым контроллером домена в domain1.test.local, отправил изменения в объекты каталога в DC1. externalId=2029 cs1Label=url cs1=https://contoso-corp.atp.azure.com:13000/securityAlert/1d5d1444-12cf-4db9-be48-39ebc2f51515
### <a name="suspicious-domain-controller-promotion-potential-dcshadow-attack"></a>Подозрительное повышение роли контроллера домена (потенциальная атака DCShadow)
07-12-2018  11:18:07    Auth.Error  192.168.0.200    1 2018-07-12T08:18:06.883880+00:00 DC1 CEF 3868 DirectoryServicesRoguePromotionS ï»¿0|Microsoft|Расширенная защита SQL от угроз|2.40.0.0|DirectoryServicesRoguePromotionSecurityAlert|[ПРЕДВАРИТЕЛЬНАЯ ВЕРСИЯ] **Подозрительное повышение роли контроллера домена (потенциальная атака DCShadow)**|10|start=2018-07-12T08:17:55.4067092Z app=Ldap shost=CLIENT1 msg=CLIENT1, который является компьютером в domain1.test.local, зарегистрирован как контроллер домена в DC1. externalId=2028 cs1Label=url cs1=https://contoso-corp.atp.azure.com:13000/securityAlert/97c59b43-dc18-44ee-9826-8fd5d03bd53

### <a name="malicious-data-protection-private-information-request"></a>Вредоносный запрос конфиденциальных сведений для защиты данных.
02-21-2018  16:22:08    Auth.Error  192.168.0.220   1 2018-02-21T14:21:54.080266+00:00 CENTER CEF 6076 RetrieveDataProtectionBackupKeyS ï»¿0|Microsoft|Azure ATP|2.22.4228.22540|RetrieveDataProtectionBackupKeySecurityAlert|Вредоносный запрос конфиденциальных сведений для защиты данных|10|start=2018-02-21T14:19:41.8382786Z app=LsaRpc shost=CLIENT1 msg=Пользователь user1 выполнил 1 успешную попытку с компьютера CLIENT1 для получения ключа резервной копии домена DPAPI из DC1. externalId=2020 cs1Label=url cs1=https://contoso-corp.atp.azure.com/securityAlert/b22221d1-764a-4fae-a5ce-e6a0c69dc55a

### <a name="over-pass-the-hash"></a>Over-Pass-the-Hash
02-21-2018  16:21:07    Auth.Warning    192.168.0.220   1 2018-02-21T14:20:54.145833+00:00 CENTER CEF 6076 EncryptionDowngradeSecurityAlert ï»¿0|Microsoft|Azure ATP|2.22.4228.22540|EncryptionDowngradeSecurityAlert|Переход на более слабое шифрование|5|start=2018-02-21T14:19:41.8737870Z app=Kerberos msg= Согласно ранее установленному поведению для поля Encrypted_Timestamp сообщения AS_REQ от компьютера CLIENT1 был выполнен переход на более слабый метод шифрования. Это может быть результатом кражи учетных данных с помощью атаки Overpass-the-Hash с компьютера CLIENT1. externalId=2011 cs1Label=url cs1=https://contoso-corp.atp.azure.com/securityAlert/6354b9ed-6a39-4f5b-b10e-f51bbee879d2
### <a name="pass-the-hash"></a>Pass-the-Hash
02-21-2018  17:04:47    Auth.Error  192.168.0.220   1 2018-02-21T15:04:33.537583+00:00 CENTER CEF 6076 PassTheHashSecurityAlert ï»¿0|Microsoft|Azure ATP|2.22.4228.22540|PassTheHashSecurityAlert|Хищение удостоверения с помощью атаки Pass-the-Hash|10|start=2018-02-21T15:02:22.2577465Z app=Kerberos suser=Eugene Jenkins msg=Был украден хэш Eugene Jenkins (разработчика программного обеспечения) с одного из компьютеров, вход на который был выполнен ранее Eugene Jenkins (разработчиком программного обеспечения). Хэш использовался с компьютера CLIENT1. externalId=2017 cs1Label=url cs1=https://contoso-corp.atp.azure.com/securityAlert/511f1487-2915-477d-be2e-04cfba702ccd
### <a name="account-enumeration"></a>Перечисление учетных записей
02-21-2018  16:19:35    Auth.Warning    192.168.0.220   1 2018-02-21T14:19:27.540731+00:00 CENTER CEF 6076 AccountEnumerationSecurityAlert ï»¿0|Microsoft|Azure ATP|2.22.4228.22540|AccountEnumerationSecurityAlert|Разведывательная атака с использованием перечисления учетных записей|5|start=2018-02-21T14:19:02.6045416Z app=Kerberos shost=CLIENT1 suser=LMaldonado msg=Lamon Maldonado (разработчик программного обеспечения) обнаружил и успешно определил подозрительное действие в отношении перечисления учетных записей с использованием протокола Kerberos, исходящее с компьютера CLIENT1. externalId=2003 cs1Label=url cs1=https://contoso-corp.atp.azure.com/securityAlert/eb6a35da-ff7f-4ab5-a1b5-a07529a89e6d
### <a name="dns-recon"></a>Проверка DNS
02-21-2018  16:20:06    Auth.Warning    192.168.0.220   1 2018-02-21T14:19:54.063994+00:00 CENTER CEF 6076 DnsReconnaissanceSecurityAlert ï»¿0|Microsoft|Azure ATP|2.22.4228.22540|DnsReconnaissanceSecurityAlert|Проверка DN5|start=2018-02-21T14:19:41.9417776Z app=Dns shost=CLIENT1 request=demo query requestMethod=Axfr reason=NoError outcome=Success msg=Было обнаружено подозрительное действие DNS, исходящее с компьютера CLIENT1 (который не является DNS-сервером). Был отправлен запрос на демонстрационный запрос (тип Axfr). Получен ответ NoError. externalId=2007 cs1Label=url cs1=https://contoso-corp.atp.azure.com/securityAlert/6f69e1e7-304a-4054-8edf-33f26c1f004c


### <a name="smb-session-enumeration"></a>Перечисление сеансов SMB
02-21-2018  16:21:22    Auth.Warning    192.168.0.220   1 2018-02-21T14:21:13.962930+00:00 CENTER CEF 6076 EnumerateSessionsSecurityAlert ï»¿0|Microsoft|Azure ATP|2.22.4228.22540|EnumerateSessionsSecurityAlert|Разведывательная атака с использованием перечисления сеансов SMB|5|start=2018-02-21T14:19:03.2071170Z app=SrvSvc shost=CLIENT1 msg=Пользователь user1 успешно предпринял попытки перечисления сеанса SMB с компьютера CLIENT1 в отношении DC1 с представлением Eugene Jenkins (user2-computer). externalId=2012 cs1Label=url cs1=https://contoso-corp.atp.azure.com/securityAlert/622c38ab-324f-4c1f-9caa-1fe85db3b440
### <a name="sam-r-enumeration"></a>Перечисление SAM-R
02-21-2018  16:22:08    Auth.Warning    192.168.0.220   1 2018-02-21T14:21:54.267658+00:00 CENTER CEF 6076 SamrReconnaissanceSecurityAlert ï»¿0|Microsoft|Azure ATP|2.22.4228.22540|SamrReconnaissanceSecurityAlert| Разведывательная атака с использованием перечисления служб каталогов |5|start=2018-02-21T14:19:41.9912772Z app= Samr shost=CLIENT1 suser=user1 outcome=Success msg= Были предприняты следующие попытки перечисления служб каталогов с использованием протокола SAMR в отношении DC1 с компьютера CLIENT1:\r\nУспешное перечисление всех групп в domain1.test.local пользователем user1. externalId=2019 cs1Label=url cs1=https://contoso-corp.atp.azure.com/securityAlert/f295029a-ffae-408b-9dd0-55424c81eac0
### <a name="remote-execution"></a>Удаленное выполнение
02-21-2018  16:22:08    Auth.Warning    192.168.0.220   1 2018-02-21T14:21:54.267658+00:00 CENTER CEF 6076 RemoteExecutionSecurityAlert ï»¿0|Microsoft|Azure ATP|2.22.4228.22540|RemoteExecutionSecurityAlert|Обнаружена попытка удаленного выполнения|5|start=2018-02-21T14:19:41.9912772Z app=Wmi shost=CLIENT1 suser=user1 outcome=Success msg=На DC1 с компьютера CLIENT1 были предприняты следующие попытки удаленного выполнения:\r\nУспешное удаленное выполнение одного или нескольких методов WMI пользователем user1. externalId=2019 cs1Label=url cs1=https://contoso-corp.atp.azure.com/securityAlert/f295029a-ffae-408b-9dd0-55424c81eac0
### <a name="skeleton-key"></a>использование мастер-ключа;
02-21-2018  16:21:07    Auth.Warning    192.168.0.220   1 2018-02-21T14:20:54.145833+00:00 CENTER CEF 6076 EncryptionDowngradeSecurityAlert ï»¿0|Microsoft|Azure ATP|2.22.4228.22540|EncryptionDowngradeSecurityAlert|переход на более слабое шифрование|5|start=2018-02-21T14:19:41.8737870Z app=Kerberos msg=Согласно ранее установленному поведению для поля ETYPE_INFO2 сообщения KRB_ERR от компьютера CLIENT1 был выполнен переход на более слабый метод шифрования. Это может быть результатом использования мастер-ключа в DC1. externalId=2011 cs1Label=url cs1=https://contoso-corp.atp.azure.com/securityAlert/6354b9ed-6a39-4f5b-b10e-f51bbee879d2

### <a name="unusual-protocol-implementation"></a>Внедрение нестандартных протоколов.
02-21-2018  16:21:22    Auth.Warning    192.168.0.220   1 2018-02-21T14:21:13.916050+00:00 CENTER CEF 6076 AbnormalProtocolSecurityAlert ï»¿0|Microsoft|Azure ATP|2.22.4228.22540|AbnormalProtocolSecurityAlert|Внедрение нестандартных протоколов|5|start=2018-02-21T14:19:03.1981155Z app=Ntlm shost=CLIENT2 outcome=Success msg=Были предприняты попытки проверки подлинности с компьютера CLIENT2 в отношении DC1 с использованием внедрения нестандартных протоколов. Это может быть результатом использования вредоносных средств для проведения таких атак, как Pass-the-Hash или атака методом подбора. externalId=2002 cs1Label=url cs1=https://contoso-corp.atp.azure.com/securityAlert/40fe98dd-aa42-4540-9d73-831486fdd1e4 cs1=https://192.168.0.220/suspiciousActivity/5909cce38ca1ec04d05f4ab4

### <a name="malicious-service-creation"></a>Создание вредоносной службы
02-21-2018  16:20:06    Auth.Warning    192.168.0.220   1 2018-02-21T14:19:54.254930+00:00 CENTER CEF 6076 MaliciousServiceCreationSecurity ï»¿0|Microsoft|Azure ATP|2.22.4228.22540|MaliciousServiceCreationSecurityAlert|Создание вредоносной службы|5|start=2018-02-21T14:19:41.7897808Z app=ServiceInstalledEvent shost=CLIENT1 msg=Пользователь user1 создал вредоносную службу для выполнения потенциально опасных команд на компьютере CLIENT1. externalId=2026 cs1Label=url cs1=https://contoso-corp.atp.azure.com/securityAlert/179229b6-b791-4895-b5aa-fdf3747a325c

### <a name="pass-the-ticket"></a>Атака Pass-the-Ticket.
02-21-2018  17:04:47    Auth.Error  192.168.0.220   1 2018-02-21T15:04:33.537583+00:00 CENTER CEF 6076 PassTheTicketSecurityAlert ï»¿0|Microsoft|Расширенная защита SQL от угроз|2.22.4228.22540|PassTheTicketSecurityAlert|Хищение удостоверения с помощью атаки Pass-the-Ticket|10|start=2018-02-21T15:02:22.2577465Z app=Kerberos suser=Eugene Jenkins msg=Были украдены билеты Kerberos, принадлежащие Eugene Jenkins (разработчику программного обеспечения), с компьютера Admin-PC на компьютер Victim-PC. Они использовались для доступа к krbtgt/DOMAIN1.TEST.LOCAL. externalId=2017 cs1Label=url cs1=https://contoso-corp.eng.atp.azure.com/securityAlert/511f1487-2915-477d-be2e-04cfba702ccd


## <a name="see-also"></a>См. также
- [Предварительные требования к Azure ATP](atp-prerequisites.md)
- [Планирование производительности Azure ATP](atp-capacity-planning.md)
- [Настройка сбора данных о событиях](configure-event-collection.md)
- [Настройка пересылки событий Windows](configure-event-forwarding.md#configuring-windows-event-forwarding)
- [Обязательно ознакомьтесь с форумом ATP](https://aka.ms/azureatpcommunity)