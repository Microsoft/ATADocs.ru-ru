---
title: Справочник по журналу SIEM Microsoft Defender для удостоверений
description: Примеры журналов подозрительных действий, отправляемых из Microsoft Defender для удостоверений в систему SIEM.
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 10/26/2020
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.service: azure-advanced-threat-protection
ms.reviewer: arzinger
ms.suite: ems
ms.openlocfilehash: e2ac1109454e3bef9baec2197d4db7f73698ed6c
ms.sourcegitcommit: f434dbff577d9944df18ca7533d026acdab0bb42
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/03/2020
ms.locfileid: "93276492"
---
# <a name="product-long-siem-log-reference"></a>Справочник по журналу SIEM [!INCLUDE [Product long](includes/product-long.md)]

[!INCLUDE [Rebranding notice](includes/rebranding.md)]

[!INCLUDE [Product short](includes/product-short.md)] может пересылать события оповещений системы безопасности и оповещений о работоспособности в систему SIEM. Оповещения и события передаются в формате CEF. В этой справочной статье приводятся примеры журналов, пересылаемых в систему SIEM.

## <a name="sample-product-short-security-alerts-in-cef-format"></a>Пример оповещений системы безопасности [!INCLUDE [Product short](includes/product-short.md)] в формате CEF

В систему SIEM пересылаются следующие поля и их значения:

|Сведения|Описание|
|---------|---------------|
|start|Время начала оповещения.|
|suser|Учетная запись (обычно пользовательская), связанная с оповещением.|
|shost|Учетная запись (обычно учетная запись компьютера), связанная с оповещением.|
|outcome|Показывает, выполнено ли успешно подозрительное действие из оповещения (если актуально).|
|msg|Описание оповещения.|
|cnt|Число выполнений действия в оповещениях со счетчиком (например, число угаданных паролей при атаке методом подбора).|
|app |Используемый в оповещении протокол.|
|externalId|Идентификатор события, который [!INCLUDE [Product short](includes/product-short.md)] записывает в журнал событий по каждому типу оповещения. При пересылке оповещений в Microsoft Cloud App Security это поле заполняется соответствующим идентификатором предупреждения Cloud App Security.|
|cs#label|Пользовательские строки, разрешенные форматом CEF, где cs#label — это имя нового поля. |
|cs#|Пользовательские строки, разрешенные форматом CEF, где cs# — это значение.|

- Пример: `cs1Label=url cs1=https\://192.168.0.220/suspiciousActivity/5909ae198ca1ec04d05e65fa`  
Поле cs1 является URL-адресом оповещения.

- Пример: `cs2Label=trigger cs2=new`  
Поле cs2 определяет, является оповещение новым или обновленным.

> [!NOTE]
> Если вы планируете создавать автоматические действия или скрипты для журналов SIEM в [!INCLUDE [Product short](includes/product-short.md)], рекомендуем для идентификации типа оповещения использовать не имя оповещения, а поле **externalId**. Имена оповещений иногда могут меняться, а **externalId** остается неизменным. Список внешних идентификаторов: [Сопоставление имен оповещений безопасности и уникальные внешние идентификаторы](suspicious-activity-guide.md#security-alert-name-mapping-and-unique-external-ids).

## <a name="sample-logs"></a>Образцы журналов

Примеры журналов соответствуют требованиям RFC 5424, но [!INCLUDE [Product short](includes/product-short.md)] также поддерживает RFC 3164.

Уровни приоритета:

- 3 — низкий;
- 5 — средний;
- 10 — высокий.

### <a name="account-enumeration-reconnaissance"></a>Разведывательная атака путем перечисления учетных записей

02-21-2018 16:19:35 Auth.Warning 192.168.0.220 1 2018-02-21T14:19:27.540731+00:00 CENTER CEF 6076 AccountEnumerationSecurityAlert ï»¿0|Microsoft|Azure ATP|2.22.4228.22540|AccountEnumerationSecurityAlert|Разведывательная атака с использованием перечисления учетных записей|5|start=2018-02-21T14:19:02.6045416Z app=Kerberos shost=CLIENT1 suser=LMaldonado msg=Lamon Maldonado (разработчик программного обеспечения) обнаружил и успешно определил подозрительное действие в отношении перечисления учетных записей с использованием протокола Kerberos, исходящее с компьютера CLIENT1. externalId=2003 cs1Label=url cs1=https\://contoso-corp.atp.azure.com/securityAlert/eb6a35da-ff7f-4ab5-a1b5-a07529a89e6d cs2Label=trigger cs2=new

### <a name="data-exfiltration-over-smb"></a>Кража данных по SMB

12-19-2018 14:17:46 Auth.Error 127.0.0.1 1 2018-12-19T12:17:34.645993+00:00 DC1 CEF 3288 SmbDataExfiltrationSecurityAlert ï»¿0|Microsoft|Azure ATP|2.60.0.0|SmbDataExfiltrationSecurityAlert|[Предварительная версия] Кража данных по SMB|10|start=2018-12-19T12:14:12.4932821Z app=Smb shost=CLIENT1 msg=Eugene Jenkins (разработчик программного обеспечения) на DC2 скопировал подозрительные файлы на компьютер CLIENT1. externalId=2030 cs1Label=url cs1=https\://contoso-corp.atp.azure.com:13000/securityAlert/3ca2ec9d-2c67-44cc-a2d6-391716611bb6 cs2Label=trigger cs2=new

### <a name="honeytoken-activity"></a>Действие Honeytoken

02-21-2018 16:20:36 Auth.Warning 192.168.0.220 1 2018-02-21T14:20:34.106162+00:00 CENTER CEF 6076 HoneytokenActivitySecurityAlert ï»¿0|Microsoft|Azure ATP|2.22.4228.22540|HoneytokenActivitySecurityAlert|Активность учетной записи honeytoken|5|start=2018-02-21T14:20:26.6705617Z app=Kerberos suser=honey msg=С помощью учетной записи honey были выполнены следующие действия:\r\nВход на компьютер CLIENT2 через DC1. externalId=2014 cs1Label=url cs1=https\://contoso-corp.atp.azure.com/securityAlert/9249fe9a-c883-46dd-a4da-2a1fca5f211c cs2Label=trigger cs2=new

### <a name="malicious-request-of-data-protection-api-master-key"></a>Вредоносный запрос главного ключа API защиты данных

10-29-2018 11:22:04 Auth.Error 192.168.0.202 1 2018-10-29T09:22:00.350864+00:00 DC3 CEF 3908 RetrieveDataProtectionBackupKeyS ï»¿0|Microsoft|Azure ATP|2.52.5704.46184|RetrieveDataProtectionBackupKeySecurityAlert|Вредоносный запрос конфиденциальных сведений для защиты данных|10|start=2018-10-29T09:19:45.6307993Z app=LsaRpc shost=CLIENT1 msg=Пользователь user1 предпринял 1 успешную попытку получить с компьютера CLIENT1 резервный ключ домена DPAPI из DC1. externalId=2020 cs1Label=url cs1=https\://contoso-corp.atp.azure.com/securityAlert/2f5717cb-2434-4d54-8af4-b2c6d14bc15c cs2Label=trigger cs2=new

### <a name="network-mapping-reconnaissance-dns"></a>Разведывательная атака путем сетевого сопоставления (DNS)

10-29-2018 11:20:02 Auth.Warning 192.168.0.202 1 2018-10-29T09:19:59.056894+00:00 DC3 CEF 3908 DnsReconnaissanceSecurityAlert ï»¿0|Microsoft|Azure ATP|2.52.5704.46184|DnsReconnaissanceSecurityAlert|Разведывательная атака с помощью DNS|5|start=2018-10-29T09:19:43.5033765Z app=Dns shost=CLIENT1 msg=Обнаружено подозрительное действие DNS, исходящее с компьютера CLIENT1 (который не является DNS-сервером), в отношении DC1. externalId=2007 cs1Label=url cs1=https\://contoso-corp.atp.azure.com/securityAlert/23937d33-ff71-484d-be0a-3c417fe573ce cs2Label=trigger cs2=new

### <a name="reconnaissance-using-directory-services-queries"></a>разведывательная атака с использованием запросов к службам каталогов;

02-21-2018 16:22:08 Auth.Warning 192.168.0.220 1 2018-02-21T14:21:54.267658+00:00 CENTER CEF 6076 SamrReconnaissanceSecurityAlert ï»¿0|Microsoft|Azure ATP|2.22.4228.22540|SamrReconnaissanceSecurityAlert| Разведывательная атака с использованием перечисления служб каталогов |5|start=2018-02-21T14:19:41.9912772Z app= Samr shost=CLIENT1 suser=user1 outcome=Success msg= Были предприняты следующие попытки перечисления служб каталогов с использованием протокола SAMR в отношении DC1 с компьютера CLIENT1:\r\nУспешное перечисление всех групп в domain1.test.local пользователем user1. externalId=2019 cs1Label=url cs1=https\://contoso-corp.atp.azure.com/securityAlert/f295029a-ffae-408b-9dd0-55424c81eac0 cs2Label=trigger cs2=new

### <a name="remote-code-execution-attempt"></a>Попытка удаленного выполнения кода

10-29-2018 11:22:04 Auth.Warning 192.168.0.202 1 2018-10-29T09:22:00.100856+00:00 DC3 CEF 3908 RemoteExecutionSecurityAlert ï»¿0|Microsoft|Azure ATP|2.52.5704.46184|RemoteExecutionSecurityAlert|Попытка удаленного выполнения кода|5|start=2018-10-29T09:19:45.0552367Z shost=CLIENT1 msg=На DC1 с компьютера CLIENT1 были предприняты следующие попытки удаленного выполнения кода.\r\nУспешное удаленное планирование одной или нескольких задач пользователем user1.\r\nНеуспешное удаленное планирование одной или нескольких задач пользователем user1.\r\nУспешное удаленное выполнение одного или нескольких методов WMI пользователем user1. externalId=2019 cs1Label=url cs1=https\://contoso-corp.atp.azure.com/securityAlert/f063c778-830c-4e9f-98d1-bc6c11c94e11 cs2Label=trigger cs2=new

### <a name="remote-code-execution-over-dns"></a>Удаленное выполнение кода через DNS

1-17-2019 08:24:54 Auth.Warning 192.168.0.202 1 2019-01-17T08:24:54.100856+00:00 DC3 CEF 3908 DnsRemoteCodeExecutionSecurityAlert ï»¿0|Microsoft|Azure ATP|2.63.0.0|DnsRemoteCodeExecutionSecurityAlert|[Предварительная версия] Удаленное выполнение кода по DNS|5|start=2019-01-17T08:24:54.5293800Z app=Dns shost=CLIENT1 msg=Субъект попытался удаленно выполнить команду на компьютере CLIENT1 из DC1 по протоколу DNS. externalId=2036 cs1Label=url cs1=https\:////contoso-corp.atp.azure.com:13000/securityAlert/591f9769-d904-40b1-89fa-c307c2ca814f cs2Label=trigger cs2=new

### <a name="security-principal-reconnaissance-ldap"></a>Рекогносцировка, направленная на субъект безопасности (LDAP)

02-18-2019 16:48:08 Auth.Warning 127.0.0.1 1 2019-02-18T14:48:02.912264+00:00 DC1 CEF 4656 LdapSearchReconnaissanceSecurity ï»¿0|Microsoft|Azure ATP|2.66.0.0|LdapSearchReconnaissanceSecurityAlert|[Предварительная версия] Разведывательная атака с помощью запросов LDAP|5|start=2019-02-18T14:46:29.4644276Z app=LdapSearch shost=CLIENT1 msg=Субъект на компьютере CLIENT1 отправил на DC1 подозрительные запросы LDAP, с помощью которых выполнялся поиск 4 типов перечислений и операторов серверов (участников, которые могут администрировать серверы домена) в 2 доменах externalId=2038 cs1Label=url cs1=https\://contoso-corp.atp.azure..com:13000/securityAlert/81ea99c4-ce1f-4581-ac8f-7440fbed7cd0 cs2Label=trigger cs2=new

### <a name="suspected-brute-force-attack-ldap"></a>Предполагаемая атака методом подбора (протокол LDAP)

02-21-2018 16:20:21 Auth.Warning 192.168.0.220 1 2018-02-21T14:20:06.156238+00:00 CENTER CEF 6076 LdapBruteForceSecurityAlert ï»¿0|Microsoft|Azure ATP|2.22.4228.22540|LdapBruteForceSecurityAlert|Атака методом подбора с использованием простой привязки LDAP|5|start=2018-02-21T14:19:41.7422810Z app=Ldap suser=Wofford Thurston shost=CLIENT1 msg=Предпринята попытка атаки методом подбора с использованием протокола LDAP в отношении Wofford Thurston (разработчика программного обеспечения) с компьютера CLIENT1 (100 попыток подбора). cnt=100 externalId=2004 cs1Label=url cs1=https\://contoso-corp.atp.azure.com/securityAlert/57b8ac96-7907-4971-9b27-ec77ad8c029a cs2Label=trigger cs2=update

### <a name="suspected-brute-force-attack-kerberos-ntlm"></a>Предполагаемая атака методом подбора (Kerberos, NTLM)

10-29-2018 11:20:47 Auth.Warning 192.168.0.202 1 2018-10-29T09:20:44.478827+00:00 DC3 CEF 3908 BruteForceSecurityAlert ï»¿0|Microsoft|Azure ATP|2.52.5704.46184|BruteForceSecurityAlert|Подозрительные неудачные попытки проверки подлинности|5|start=2018-10-29T09:19:44.9512286Z app=Kerberos shost=CLIENT1 msg=Обнаружены исходящие с компьютера CLIENT1 подозрительные неудачные попытки проверки подлинности, означающие возможную атаку методом подбора. externalId=2023 cs1Label=url cs1=https\://contoso-corp.atp.azure.com/securityAlert/85042c8e-27fa-49b3-8667-dabc1aa31580 cs2Label=trigger cs2=new

### <a name="suspected-dcsync-attack-replication-of-directory-services"></a>Предполагаемая атака DCSync (репликация служб каталогов)

02-21-2018 16:20:06 Auth.Warning 192.168.0.220 1 2018-02-21T14:19:54.254930+00:00 CENTER CEF 6076 MaliciousServiceCreationSecurity ï»¿0|Microsoft|Azure ATP|2.22.4228.22540|MaliciousServiceCreationSecurityAlert|Создание вредоносной службы|5|start=2018-02-21T14:19:41.7897808Z app=ServiceInstalledEvent shost=CLIENT1 msg=Пользователь user1 создал вредоносную службу для выполнения потенциально опасных команд на компьютере CLIENT1. externalId=2026 cs1Label=url cs1=https\://contoso-corp.atp.azure.com/securityAlert/179229b6-b791-4895-b5aa-fdf3747a325c cs2Label=trigger cs2=update

### <a name="suspected-golden-ticket-usage-encryption-downgrade"></a>Предполагаемое использование Golden Ticket (понижение уровня шифрования)

10-29-2018 11:25:07 Auth.Warning 192.168.0.202 1 2018-10-29T09:25:01.007701+00:00 DC3 CEF 3908 GoldenTicketEncryptionDowngradeS ï»¿0|Microsoft|Azure ATP|2.52.5704.46184|GoldenTicketEncryptionDowngradeSecurityAlert|Понижение уровня шифрования (потенциальная атака Golden Ticket)|5|start=2018-10-29T09:37:49.0849130Z app=Kerberos msg=W10-000007-Lap использовал более слабый метод шифрования (RC4) в запросе службы Kerberos (TGS_REQ) из W10-000007-Lap для доступа к host/domain1.test.local. externalId=2009 cs1Label=url cs1=https\://contoso-corp.atp.azure.com/securityAlert/f01f8403-88b2-437e-b4ad-d72485fe05ac cs2Label=trigger cs2=new

### <a name="suspected-golden-ticket-usage-non-existent-account"></a>Предполагаемое использование Golden Ticket (несуществующая учетная запись)

07-01-2018 14:28:49 Auth.Error 192.168.0.100 1 2018-07-01T11:28:35.546638+00:00 CENTER CEF 38768 ForgedPrincipalSecurityAlert ï»¿0|Microsoft|Azure ATP|2.39.0.0|ForgedPrincipalSecurityAlert|Билет Kerberos Golden Ticket — несуществующая учетная запись|10|start=2018-07-01T09:48:31.2567987Z app=Kerberos suser=domain1.test.local\fake msg=Учетная запись domain1.test.local\fake, которая не существует в Active Directory, использовала билет Kerberos. С 2 компьютеров был обнаружен билет, используемый для доступа к 3 ресурсам. Это может свидетельствовать о потенциальной атаке Golden Ticket. externalId=2027 cs1Label=url cs1=https\://contoso-corp.atp.azure.com:13000/securityAlert/98f050d4-9134-429c-8e54-d8eeb19849c4 cs2Label=trigger cs2=update

### <a name="suspected-golden-ticket-usage-ticket-anomaly"></a>Предполагаемое использование Golden Ticket (аномалия билета)

1 2018-11-18T10:46:23.346946+00:00 MAXIMG-7050 CEF 24284 GoldenTicketSizeAnomalySecurityA 0|Microsoft|Azure ATP|2.56.0.0|GoldenTicketSizeAnomalySecurityAlert|[PREVIEW] Suspected Golden Ticket usage (ticket anomaly)|10|start=2018-11-18T10:44:12.9317797Z app=Kerberos shost=CLIENT2 suser=RFosdyke msg=Пользователь Renzo Fosdyke (Software Engineer) использовал подозрительный билет Kerberos с CLIENT2 для доступа к ldap/domain1.test.local. externalId=2032 cs1Label=url cs1=https\://contoso-corp.atp.azure.com:13000/securityAlert/63600e03-f423-49bf-a92d-4010e1d52b9f cs2Label=trigger cs2=update

### <a name="suspected-golden-ticket-usage-time-anomaly"></a>Предполагаемое использование Golden Ticket (аномальное время)

02-21-2018 16:22:39 Auth.Error 192.168.0.220 1 2018-02-21T14:22:34.274054+00:00 CENTER CEF 6076 GoldenTicketSecurityAlert ï»¿0|Microsoft|Azure ATP|2.22.4228.22540|GoldenTicketSecurityAlert|Действие с использованием "золотого" билета Kerberos|10|start=2018-02-21T14:19:03.2416152Z app=Kerberos suser=Обнаружено подозрительное использование билета Kerberos, принадлежащего Lanell Campos (разработчику программного обеспечения), что указывает на возможную атаку Golden Ticket. externalId=2022 cs1Label=url cs1=https\://contoso-corp.atp.azure.com/securityAlert/702c836e-6f49-4479-9892-80e8bccbfac0 cs2Label=trigger cs2=update

### <a name="suspected-golden-ticket-usage-forged-authorization-data"></a>Предполагаемое использование Golden Ticket (поддельные данные авторизации)

10-29-2018 11:22:04 Auth.Error 192.168.0.202 1 2018-10-29T09:21:59.288337+00:00 DC3 CEF 3908 ForgedPacSecurityAlert ï»¿0|Microsoft|Azure ATP|2.52.5704.46184|ForgedPacSecurityAlert|Повышение привилегий с использованием поддельных данных авторизации|10|start=2018-10-29T09:19:43.6403358Z app=Kerberos suser=user1 msg=Пользователь user1 предпринял неудачную попытку повысить привилегии в DC1 на host/domain1.test.local с компьютера CLIENT1 при помощи поддельных данных авторизации. externalId=2013 cs1Label=url cs1=https\://contoso-corp.atp.azure.com/securityAlert/b698d438-5013-4bca-be0b-f219f8b69108 cs2Label=trigger cs2=new

### <a name="suspected-identity-theft-pass-the-hash"></a>Предполагаемая кража удостоверения (Pass-the-Hash)

02-21-2018 17:04:47 Auth.Error 192.168.0.220 1 2018-02-21T15:04:33.537583+00:00 CENTER CEF 6076 PassTheHashSecurityAlert ï»¿0|Microsoft|Azure ATP|2.22.4228.22540|PassTheHashSecurityAlert|Хищение удостоверения с помощью атаки Pass-the-Hash|10|start=2018-02-21T15:02:22.2577465Z app=Kerberos suser=Eugene Jenkins msg=Был украден хэш Eugene Jenkins (разработчика программного обеспечения) с одного из компьютеров, вход на который был выполнен ранее Eugene Jenkins (разработчиком программного обеспечения). Хэш использовался с компьютера CLIENT1. externalId=2017 cs1Label=url cs1=https\://contoso-corp.atp.azure.com/securityAlert/511f1487-2915-477d-be2e-04cfba702ccd cs2Label=trigger cs2=update

### <a name="suspected-identity-theft-pass-the-ticket"></a>Предполагаемая кража удостоверения (Pass-the-Ticket)

02-21-2018 17:04:47 Auth.Error 192.168.0.220 1 2018-02-21T15:04:33.537583+00:00 CENTER CEF 6076 PassTheTicketSecurityAlert ï»¿0|Microsoft|Azure ATP|2.22.4228.22540|PassTheTicketSecurityAlert|Хищение удостоверения с помощью атаки Pass-the-Ticket|10|start=2018-02-21T15:02:22.2577465Z app=Kerberos suser=Eugene Jenkins msg=Были украдены билеты Kerberos, принадлежащие Eugene Jenkins (разработчику программного обеспечения), с компьютера Admin-PC на компьютер Victim-PC. Они использовались для доступа к krbtgt/DOMAIN1.TEST.LOCAL. externalId=2018 cs1Label=url cs1=https\://contoso-corp.atp.azure.com/securityAlert/511f1487-2915-477d-be2e-04cfba702ccd cs2Label=trigger cs2=new

### <a name="suspected-ntlm-authentication-tampering"></a>Предполагаемые незаконные изменения при аутентификации NTLM

07-17-2019 18:18:44 Auth.Warning 192.168.0.77 1 2019-07-09T15:18:30.967118+00:00 CENTER CEF 7144 AbnormalNtlmSigningSecurityAlert ï»¿0|Microsoft|Azure ATP|2.86.0.0|AbnormalNtlmSigningSecurityAlert|[Предварительная версия] Предполагаемые незаконные изменения при проверке подлинности NTLM|5|start=2019-07-09T15:14:57.5280720Z app=Ntlm shost=CLIENT1 msg=Две учетные записи на компьютере CLIENT1 предпринимают подозрительные попытки пройти проверку подлинности на двух компьютерах с использованием протокола NTLM. externalId=2039 cs1Label=url cs1=https\://contoso-corp.atp.azure.com:13000/securityAlert/d4ce6252-2c0f-47f6-a534-47ee8ad983be cs2Label=trigger cs2=new

### <a name="suspected-over-pass-the-hash-attack-encryption-downgrade"></a>Предполагаемая атака Overpass-the-Hash (понижение уровня шифрования)

02-21-2018 16:21:07 Auth.Warning 192.168.0.220 1 2018-02-21T14:20:54.145833+00:00 CENTER CEF 6076 EncryptionDowngradeSecurityAlert ï»¿0|Microsoft|Azure ATP|2.22.4228.22540|EncryptionDowngradeSecurityAlert|Переход на более слабое шифрование|5|start=2018-02-21T14:19:41.8737870Z app=Kerberos msg= Согласно ранее установленному поведению для поля Encrypted_Timestamp сообщения AS_REQ от компьютера CLIENT1 был выполнен переход на более слабый метод шифрования. Это может быть результатом кражи учетных данных с помощью атаки Overpass-the-Hash с компьютера CLIENT1. externalId=2008 cs1Label=url cs1=https\://contoso-corp.atp.azure.com/securityAlert/6354b9ed-6a39-4f5b-b10e-f51bbee879d2 cs2Label=trigger cs2=update

### <a name="suspected-skeleton-key-attack-encryption-downgrade"></a>Предполагаемая атака путем использования мастер-ключа (понижение уровня шифрования)

02-21-2018 16:21:07 Auth.Warning 192.168.0.220 1 2018-02-21T14:20:54.145833+00:00 CENTER CEF 6076 EncryptionDowngradeSecurityAlert ï»¿0|Microsoft|Azure ATP|2.22.4228.22540|EncryptionDowngradeSecurityAlert|Переход на более слабое шифрование|5|start=2018-02-21T14:19:41.8737870Z app=Kerberos msg=Согласно ранее установленному поведению для поля ETYPE_INFO2 сообщения KRB_ERR от компьютера CLIENT1 был выполнен переход на более слабый метод шифрования. Это может быть результатом использования мастер-ключа в DC1. externalId=2010 cs1Label=url cs1=https\://contoso-corp.atp.azure.com/securityAlert/6354b9ed-6a39-4f5b-b10e-f51bbee879d2 cs2Label=trigger cs2=new

### <a name="suspicious-authentication-failures"></a>Подозрительные неудачные попытки проверки подлинности

02-21-2018 16:19:20 Auth.Warning 192.168.0.220 1 2018-02-21T14:19:15.397995+00:00 CENTER CEF 6076 BruteForceSecurityAlert ï»¿0|Microsoft|Azure ATP|2.22.4228.22540|BruteForceSecurityAlert|Подозрительные неудачные попытки проверки подлинности|5|start=2018-02-21T14:19:03.3831122Z app=Kerberos shost=CLIENT1 msg=Обнаружены исходящие с компьютера CLIENT1 подозрительные неудачные попытки проверки подлинности, означающие возможную атаку методом подбора. externalId=2023 cs1Label=url cs1=https\://contoso-corp.atp.azure.com/securityAlert/fea88fc7-4110-454d-816d-349032474fd6 cs2Label=trigger cs2=new

### <a name="suspicious-communication-over-dns"></a>Подозрительный обмен данными через DNS

10-04-2018 14:49:38 Auth.Warning 192.168.0.202 1 2018-10-04T11:49:25.954059+00:00 DC3 CEF 3604 DnsSuspiciousCommunicationSecuri ï»¿0|Microsoft|Azure ATP|2.49.5589.58606|DnsSuspiciousCommunicationSecurityAlert|Подозрительный обмен данными по DNS|5|start=2018-10-04T11:49:11.0822077Z app=DnsEvent dhost= suspiciousdomainname msg=Компьютер CLIENT1 отправлял подозрительные запросы DNS на разрешение suspiciousdomainname externalId=2031 cs1Label=url cs1=https\://contoso-corp.atp.azure.com/securityAlert/0fc77777-49ca-40b3-a7ba-7644f355539e cs2Label=trigger cs2=new

### <a name="suspicious-domain-controller-promotion-potential-dcshadow-attack"></a>Подозрительное повышение роли контроллера домена (потенциальная атака DCShadow)

07-12-2018 11:18:07 Auth.Error 192.168.0.200 1 2018-07-12T08:18:06.883880+00:00 DC1 CEF 3868 DirectoryServicesRoguePromotionS ï»¿0|Microsoft|Azure ATP|2.40.0.0|DirectoryServicesRoguePromotionSecurityAlert| **Подозрительное повышение роли контроллера домена (потенциальная атака DCShadow)** |10|start=2018-07-12T08:17:55.4067092Z app=Ldap shost=CLIENT1 msg=CLIENT1, который является компьютером в domain1.test.local, зарегистрирован как контроллер домена в DC1. externalId=2028 cs1Label=url cs1=https\://contoso-corp.atp.azure.com:13000/securityAlert/97c59b43-dc18-44ee-9826-8fd5d03bd53 cs2Label=trigger cs2=update

### <a name="suspicious-additions-to-sensitive-groups"></a>Подозрительные добавления в привилегированные группы

10-29-2018 11:21:03 Auth.Warning 192.168.0.202 1 2018-10-29T09:20:49.667014+00:00 DC3 CEF 3908 AbnormalSensitiveGroupMembership ï»¿0|Microsoft|Azure ATP|2.52.5704.46184|AbnormalSensitiveGroupMembershipChangeSecurityAlert|Подозрительное изменение конфиденциальных групп|5|start=2018-10-29T09:19:43.3013729Z app=GroupMembershipChangeEvent suser=user1 msg=Пользователь user1 нехарактерным образом изменил членство в конфиденциальных группах. externalId=2024 cs1Label=url cs1=https\://contoso-corp.atp.azure.com/securityAlert/6f7e677e-f068-41e5-bada-708cd5a322b9 cs2Label=trigger cs2=new

### <a name="suspicious-replication-of-directory-services"></a>Подозрительная репликация служб каталогов

02-21-2018 16:21:22 Auth.Error 192.168.0.220 1 2018-02-21T14:21:13.978554+00:00 CENTER CEF 6076 DirectoryServicesReplicationSecu ï»¿0|Microsoft|Azure ATP|2.22.4228.22540|DirectoryServicesReplicationSecurityAlert|Вредоносная репликация служб каталогов|10|start=2018-02-21T14:19:03.9975656Z app=Drsr shost=CLIENT1 msg=Пользователь user1 успешно выполнил запросы на вредоносную репликацию с компьютера CLIENT1 на DC1. outcome=Success externalId=2006 cs1Label=url cs1=https\://contoso-corp.atp.azure.com/securityAlert/cb95648e-1b6f-4d3b-81b9-7605532787d7 cs2Label=trigger cs2=new

### <a name="suspicious-replication-request-potential-dcshadow-attack"></a>Подозрительный запрос на репликацию (потенциальная атака DCShadow)

07-12-2018 11:18:37 Auth.Error 192.168.0.200 1 2018-07-12T08:18:32.265989+00:00 DC1 CEF 3868 DirectoryServicesRogueReplicatio ï»¿0|Microsoft|Azure ATP|2.40.0.0|DirectoryServicesRogueReplicationSecurityAlert| **Подозрительный запрос на репликацию (потенциальная атака DCShadow)** |10|start=2018-07-12T08:17:55.3816102Z **app=Replication Activity** shost=CLIENT1 msg=CLIENT1, который не является допустимым контроллером домена в domain1.test.local, отправил изменения в объекты каталога в DC1. externalId=2029 cs1Label=url cs1=https\://contoso-corp.atp.azure.com:13000/securityAlert/1d5d1444-12cf-4db9-be48-39ebc2f51515 cs2Label=trigger cs2=new

### <a name="suspicious-service-creation"></a>Создание подозрительной службы

10-29-2018 11:20:02 Auth.Warning 192.168.0.202 1 2018-10-29T09:19:59.164874+00:00 DC3 CEF 3908 MaliciousServiceCreationSecurity ï»¿0|Microsoft|Azure ATP|2.52.5704.46184|MaliciousServiceCreationSecurityAlert|Создание вредоносной службы|5|start=2018-10-29T09:19:44.9471965Z app=ServiceInstalledEvent shost=CLIENT1 msg=Пользователь user1 создал вредоносную службу для выполнения потенциально опасных команд на компьютере CLIENT1. externalId=2026 cs1Label=url cs1=https\://contoso-corp.atp.azure.com/securityAlert/118bbe3d-fe72-40de-80d0-2678b68aa027 cs2Label=trigger cs2=new

### <a name="suspicious-vpn-connection"></a>Подозрительные VPN-подключения

07-03-2018 13:13:12 Auth.Warning 192.168.0.200 1 2018-07-03T10:13:06.187834+00:00 DC1 CEF 2520 AbnormalVpnSecurityAlert ï»¿0|Microsoft|Azure ATP|2.39.0.0|AbnormalVpnSecurityAlert|Подозрительные VPN-подключения|5|start=2018-06-30T15:34:05.3887333Z app=VpnConnection suser=user1 msg=user1 подключился к VPN, используя три компьютера из трех местоположений. externalId=2025 cs1Label=url cs1=https\://contoso-corp.eng.atp.azure.com:13000/securityAlert/88c46b0e-372f-4c06-9935-67bd512c4f68 cs2Label=trigger cs2=new

### <a name="suspected-wannacry-ransomware-attack"></a>Предполагаемая атака программы-шантажиста WannaCry

02-21-2018 16:21:22 Auth.Warning 192.168.0.220 1 2018-02-21T14:21:13.916050+00:00 CENTER CEF 6076 AbnormalProtocolSecurityAlert ï»¿0|Microsoft|Azure ATP|2.22.4228.22540|AbnormalProtocolSecurityAlert|Предполагаемая атака программы-шантажиста WannaCry|5|start=2018-02-21T14:19:03.1981155Z app=Ntlm shost=CLIENT2 outcome=Success msg=Были предприняты попытки аутентификации с компьютера CLIENT2 в DC1 с использованием нестандартной реализации протоколов. Это может быть результатом выполнения атак с использованием вредоносных средств, таких как WannaCry. externalId=2035 cs1Label=url cs1=https\://contoso-corp.atp.azure.com/securityAlert/40fe98dd-aa42-4540-9d73-831486fdd1e4 cs2Label=trigger cs2=new

### <a name="suspected-brute-force-attack-smb"></a>Предполагаемая атака методом подбора (SMB)

002-21-2018 16:21:22 Auth.Warning 192.168.0.220 1 2018-02-21T14:21:13.916050+00:00 CENTER CEF 6076 AbnormalProtocolSecurityAlert ï»¿0|Microsoft|Azure ATP|2.22.4228.22540|AbnormalProtocolSecurityAlert|Предполагаемая атака методом подбора|5|start=2018-02-21T14:19:03.1981155Z app=Ntlm shost=CLIENT2 outcome=Success msg=Были предприняты попытки аутентификации с компьютера CLIENT2 в DC1 с использованием нестандартной реализации протоколов. Это может быть результатом выполнения атак с использованием вредоносных средств, таких как Hydra. externalId=2033 cs1Label=url cs1=https\://contoso-corp.atp.azure.com/securityAlert/40fe98dd-aa42-4540-9d73-831486fdd1e4 cs2Label=trigger cs2=new

### <a name="suspected-use-of-metasploit-hacking-framework"></a>Предполагаемое использование платформы взлома Metasploit

002-21-2018 16:21:22 Auth.Warning 192.168.0.220 1 2018-02-21T14:21:13.916050+00:00 CENTER CEF 6076 AbnormalProtocolSecurityAlert ï»¿0|Microsoft|Azure ATP|2.22.4228.22540|AbnormalProtocolSecurityAlert|Предполагаемая атака с использованием Metasploit|5|start=2018-02-21T14:19:03.1981155Z app=Ntlm shost=CLIENT2 outcome=Success msg=Были предприняты попытки аутентификации с компьютера CLIENT2 в DC1 с использованием нестандартной реализации протоколов. Это может быть результатом выполнения атак с использованием вредоносных средств, таких как Metasploit. externalId=2034 cs1Label=url cs1=https\://contoso-corp.atp.azure.com/securityAlert/40fe98dd-aa42-4540-9d73-831486fdd1e4 cs2Label=trigger cs2=new

### <a name="suspected-overpass-the-hash-attack-kerberos"></a>Предполагаемая атака Overpass-the-Hash (Kerberos)

002-21-2018 16:21:22 Auth.Warning 192.168.0.220 1 2018-02-21T14:21:13.916050+00:00 CENTER CEF 6076 AbnormalProtocolSecurityAlert ï»¿0|Microsoft|Azure ATP|2.22.4228.22540|AbnormalProtocolSecurityAlert|Pre-Approved	Предполагаемая атака Overpass-the-Hash|5|start=2018-02-21T14:19:03.1981155Z app=Ntlm shost=CLIENT2 outcome=Success msg=Были предприняты попытки аутентификации с компьютера CLIENT2 в DC1 с использованием нестандартной реализации протоколов. Это может быть результатом совершения злонамеренных действий с использованием протокола Kerberos. externalId=2002 cs1Label=url cs1=https\://contoso-corp.atp.azure.com/securityAlert/40fe98dd-aa42-4540-9d73-831486fdd1e4 cs2Label=trigger cs2=new

### <a name="user-and-ip-address-reconnaissance-smb"></a>Разведывательная атака с использованием пользователя и IP-адреса (SMB)

002-21-2018 16:21:22 Auth.Warning 192.168.0.220 1 2018-02-21T14:21:13.916050+00:00 CENTER CEF 6076 AbnormalProtocolSecurityAlert ï»¿0|Microsoft|Azure ATP|2.22.4228.22540|AbnormalProtocolSecurityAlert|Разведывательная атака с использованием перечисления сеансов SMB|5|start=2018-02-21T14:19:03.1981155Z app=Ntlm shost=CLIENT2 outcome=Success msg=Были предприняты попытки аутентификации с компьютера CLIENT2 в DC1 с использованием нестандартной реализации протоколов. Это может быть результатом выполнения атак с использованием вредоносных средств, таких как Metasploit. externalId=2034 cs1Label=url cs1=https\://contoso-corp.atp.azure.com/securityAlert/40fe98dd-aa42-4540-9d73-831486fdd1e4 cs2Label=trigger cs2=new

## <a name="see-also"></a>См. также

- [Предварительные требования для работы с [!INCLUDE [Product short](includes/product-short.md)]](prerequisites.md)
- [Планирование ресурсов [!INCLUDE [Product short](includes/product-short.md)]](capacity-planning.md)
- [Настройка сбора данных о событиях](configure-event-collection.md)
- [Настройка пересылки событий Windows](configure-event-forwarding.md)
- [Посетите форум по [!INCLUDE [Product short](includes/product-short.md)].](https://aka.ms/MDIcommunity)
