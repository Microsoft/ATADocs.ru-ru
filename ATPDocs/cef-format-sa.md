---
title: Справочник по журналу Azure ATP SIEM | Документы Майкрософт
description: Примеры журналов подозрительных действий, отправляемых из Azure ATP в систему SIEM.
keywords: ''
author: mlottner
ms.author: mlottner
manager: barbkess
ms.date: 02/11/2019
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: azure-advanced-threat-protection
ms.technology: ''
ms.assetid: 3261155c-3c72-4327-ba29-c113c63a4e6d
ms.reviewer: arzinger
ms.suite: ems
ms.openlocfilehash: 4b2e3177b269581b849944c257cdc52c11ea8b5b
ms.sourcegitcommit: c48db18274edb2284e281960c6262d97f96e01d2
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/14/2019
ms.locfileid: "56264123"
---
# <a name="azure-atp-siem-log-reference"></a>Справочник по журналу Azure ATP SIEM

Azure ATP может пересылать события оповещений системы безопасности и мониторинга в систему SIEM. Оповещения и события передаются в формате CEF. В этой справочной статье приводятся примеры журналов, пересылаемых в систему SIEM.

## <a name="sample-azure-atp-security-alerts-in-cef-format"></a>Пример оповещения системы безопасности Azure ATP в формате CEF
В систему SIEM пересылаются следующие поля и их значения:

|Сведения|Описание|
|---------|---------------|
|start|Время возникновения оповещения.|
|suser|Учетная запись (обычно пользовательская), связанная с оповещением.|
|Учетная запись компьютера|Учетная запись (обычно пользовательская), связанная с оповещением.|
|outcome|Если это актуально, показывает успешность выполнения подозрительного действия, о котором сообщает оповещение.|
|msg|Описание оповещения.|
|cnt|Число выполнений подозрительного действия (например, число угаданных паролей при атаке методом подбора).|
|app |Протокол, используемый в оповещении.|
|externalId|Идентификатор типа события, который Azure ATP записывает в журнал событий по каждому из типов оповещений.|
|cs#label|Пользовательские строки, разрешенные форматом CEF. Cs#label — это имя нового поля. |
|cs#|Пользовательские строки, разрешенные форматом CEF. Cs# — это значение.|
|
- Например: cs1Label=url cs1=https\://192.168.0.220/suspiciousActivity/5909ae198ca1ec04d05e65fa
<br> Поле cs1 является URL-адресом оповещения. 

- Пример: cs2Label=trigger cs2=new
<br> Поле cs2 определяет, является оповещение новым или обновленным.


> [!NOTE]
> Если вы планируете создавать автоматические действия или сценарии для журналов SIEM в Azure ATP, рекомендуем для идентификации типа оповещения использовать не имя, а поле **externalId**. Имена оповещений иногда могут меняться, а **externalId** остается неизменным.  

## <a name="azure-atp-security-alert-unique-externalids"></a>Уникальный идентификатор externalIds оповещения системы безопасности Azure ATP

> [!div class="mx-tableFixed"] 

|Новое имя оповещения системы безопасности|Предыдущее имя оповещения системы безопасности|Уникальный внешний идентификатор|
|---------|----------|---------|
|[Разведывательная атака путем перечисления учетных записей](atp-reconnaissance-alerts.md#account-enumeration-reconnaissance-external-id-2003)|Разведывательная атака с использованием перечисления учетных записей.|2003|
|[Кража данных по SMB](atp-exfiltration-alerts.md#data-exfiltration-over-smb-external-id-2030)| Н/Д| 2030|
|[Действие Honeytoken](atp-compromised-credentials-alerts.md#honeytoken-activity-external-id-2014)|Действие Honeytoken|2014|
|[Вредоносный запрос главного ключа API защиты данных](atp-domain-dominance-alerts.md#malicious-request-of-data-protection-api-master-key-external-id-2020)|Вредоносный запрос конфиденциальных сведений для защиты данных.|2020|
|[Рекогносцировка путем сетевого сопоставления (DNS)](atp-reconnaissance-alerts.md#network-mapping-reconnaissance-dns-external-id-2007)|Разведывательная атака с использованием DNS.|2007|
|[Попытка удаленного выполнения кода](atp-domain-dominance-alerts.md#remote-code-execution-attempt-external-id-2019)|Попытка удаленного выполнения кода|2019|
|[Удаленное выполнение кода через DNS](atp-lateral-movement-alerts.md#remote-code-execution-over-dns-external-id-2036)|Н/Д|2036|
|[Предполагаемая атака методом подбора (протокол LDAP)](atp-compromised-credentials-alerts.md#suspected-brute-force-attack-ldap-external-id-2004)|Атака методом подбора с помощью простой привязки LDAP|2004|
|[Предполагаемая атака методом подбора (Kerberos, NTLM)](atp-compromised-credentials-alerts.md#suspected-brute-force-attack-kerberos-ntlm-external-id-2023)|Подозрительные неудачные попытки проверки подлинности|2023|
|[Предполагаемая атака методом подбора (SMB)](atp-compromised-credentials-alerts.md#suspected-brute-force-attack-smb-external-id-2033)|Нестандартная реализация протоколов (потенциальное использование вредоносных средств, таких как Hydra)|2033|
|[Предполагаемая атака DCShadow (повышение роли контроллера домена)](atp-domain-dominance-alerts.md#suspected-dcshadow-attack-domain-controller-promotion-external-id-2028)|Подозрительное повышение роли контроллера домена (потенциальная атака DCShadow)|2028|
|[Предполагаемая атака DCShadow (запрос на репликацию контроллера домена)](atp-domain-dominance-alerts.md#suspected-dcshadow-attack-domain-controller-replication-request-external-id-2029)|Подозрительный запрос на репликацию контроллера домена (потенциальная атака DCShadow)|2029|
|[Предполагаемая атака DCSync (репликация служб каталогов)](atp-domain-dominance-alerts.md#suspected-dcsync-attack-replication-of-directory-services-external-id-2006)|вредоносная репликация служб каталогов;|2006|
|[Предполагаемое использование Golden Ticket (понижение уровня шифрования)](atp-domain-dominance-alerts.md#suspected-golden-ticket-usage-encryption-downgrade-external-id-2009)|Понижение уровня шифрования (потенциальная атака Golden Ticket)|2009|
|[Предполагаемое использование Golden Ticket (поддельные данные авторизации)](atp-domain-dominance-alerts.md#suspected-golden-ticket-usage-forged-authorization-data-external-id-2013) |Атака, направленная на повышение привилегий с использованием поддельных данных авторизации|2013|
|[Предполагаемое использование Golden Ticket (несуществующая учетная запись)](atp-domain-dominance-alerts.md#suspected-golden-ticket-usage-nonexistent-account-external-id-2027)|Атака Golden Ticket Kerberos — несуществующая учетная запись|2027|
|[Предполагаемое использование Golden Ticket (аномалия билета)](atp-domain-dominance-alerts.md#suspected-golden-ticket-usage-ticket-anomaly-external-id-2032)|Н/Д|2032|
|[Предполагаемое использование Golden Ticket (аномальное время)](atp-domain-dominance-alerts.md#suspected-golden-ticket-usage-time-anomaly-external-id-2022)|Атака Golden Ticket в Kerberos — аномальное время|2022|
|[Предполагаемая кража удостоверения (Pass-the-Hash)](atp-lateral-movement-alerts.md#suspected-identity-theft-pass-the-hash-external-id-2017)|Кража удостоверения с помощью атаки Pass-the-Hash|2017|
|[Предполагаемая кража удостоверения (Pass-the-Ticket)](atp-lateral-movement-alerts.md#suspected-identity-theft-pass-the-ticket-external-id-2018)|Кража удостоверения с помощью атаки Pass-the-Ticket|2018|
|[Предполагаемая атака Overpass-the-Hash (понижение уровня шифрования)](atp-lateral-movement-alerts.md#suspected-overpass-the-hash-attack-encryption-downgrade-external-id-2008)|Понижение уровня шифрования (потенциальная атака Overpass-the-Hash)|2008|
|[Предполагаемая атака Overpass-the-Hash (Kerberos)](atp-lateral-movement-alerts.md#suspected-overpass-the-hash-attack-kerberos-external-id-2002)|Нестандартная реализация протокола Kerberos (потенциальная атака Overpass-the-Hash)|2002|
|[Предполагаемое использование платформы взлома Metasploit](atp-compromised-credentials-alerts.md#suspected-use-of-metasploit-hacking-framework-external-id-2034)|Нестандартная реализация протоколов (потенциальное использование средств взлома Metasploit)|2034|
|[Предполагаемая атака путем использования мастер-ключа (понижение уровня шифрования)](atp-domain-dominance-alerts.md#suspected-skeleton-key-attack-encryption-downgrade-external-id-2010)|Понижение уровня шифрования (потенциальная атака с использованием мастер-ключа)|2010|
|[Предполагаемая атака программы-шантажиста WannaCry](atp-compromised-credentials-alerts.md#suspected-wannacry-ransomware-attack-external-id-2035)|Нестандартная реализация протоколов (потенциальная атака программы-шантажиста WannaCry)|2035|
|[Потенциальная атака ретранслятора NTLM (учетная запись Exchange) — предварительная версия](atp-lateral-movement-alerts.md#suspected-ntlm-relay-attack-exchange-account-external-id-2037---preview)|Н/Д|2037|
|[Подозрительный обмен данными через DNS](atp-exfiltration-alerts.md#suspicious-communication-over-dns-external-id-2031)|Подозрительный обмен данными через DNS|2031|
|[Подозрительное изменение привилегированных групп](atp-domain-dominance-alerts.md#suspicious-modification-of-sensitive-groups-external-id-2024)|Подозрительное изменение привилегированных групп|2024|
|[Создание подозрительной службы](atp-domain-dominance-alerts.md#suspicious-service-creation-external-id-2026)|Создание подозрительной службы|2026|
|[Подозрительные VPN-подключения](atp-compromised-credentials-alerts.md#suspicious-vpn-connection-external-id-2025)|Подозрительные VPN-подключения|2025|
|[Разведывательная атака с использованием пользователей и членства в группах (SAMR)](atp-reconnaissance-alerts.md#user-and-group-membership-reconnaissance-samr-external-id-2021)|разведывательная атака с использованием запросов к службам каталогов;|2021|
|[Разведывательная атака с использованием пользователя и IP-адреса (SMB)](atp-reconnaissance-alerts.md#user-and-ip-address-reconnaissance-smb-external-id-2012)|Разведывательная атака с использованием перечисления сеансов SMB|2012|

## <a name="sample-logs"></a>Образцы журналов

Примеры журналов соответствуют требованиям RFC 5242, но Azure ATP также поддерживает RFC 3164.

Уровни приоритета:

- 3 — низкий;
- 5 — средний;
- 10 — высокий.

### <a name="account-enumeration-reconnaissance"></a>Разведывательная атака путем перечисления учетных записей 
02-21-2018  16:19:35    Auth.Warning    192.168.0.220   1 2018-02-21T14:19:27.540731+00:00 CENTER CEF 6076 AccountEnumerationSecurityAlert ï»¿0|Microsoft|Azure ATP|2.22.4228.22540|AccountEnumerationSecurityAlert|Разведывательная атака с использованием перечисления учетных записей|5|start=2018-02-21T14:19:02.6045416Z app=Kerberos shost=CLIENT1 suser=LMaldonado msg=Lamon Maldonado (разработчик программного обеспечения) обнаружил и успешно определил подозрительное действие в отношении перечисления учетных записей с использованием протокола Kerberos, исходящее с компьютера CLIENT1. externalId=2003 cs1Label=url cs1=https\://contoso-corp.atp.azure.com/securityAlert/eb6a35da-ff7f-4ab5-a1b5-a07529a89e6d cs2Label=trigger cs2=new

### <a name="data-exfiltration-over-smb"></a>Кража данных по SMB
12-19-2018  14:17:46    Auth.Error     127.0.0.1      1 2018-12-19T12:17:34.645993+00:00 DC1 CEF 3288 SmbDataExfiltrationSecurityAlert ï»¿0|Microsoft|Azure ATP|2.60.0.0|SmbDataExfiltrationSecurityAlert|[PREVIEW] Кража данных по SMB|10|start=2018-12-19T12:14:12.4932821Z app=Smb shost=CLIENT1 msg=Eugene Jenkins (инженер ПО) на DC2 скопировал подозрительные файлы на CLIENT1. externalId=2030 cs1Label=url cs1=https\://contoso-corp.atp.azure.com:13000/securityAlert/3ca2ec9d-2c67-44cc-a2d6-391716611bb6 cs2Label=trigger cs2=new

### <a name="honeytoken-activity"></a>Действие Honeytoken
02-21-2018  16:20:36    Auth.Warning  192.168.0.220 1 2018-02-21T14:20:34.106162+00:00 CENTER CEF 6076 HoneytokenActivitySecurityAlert ï»¿0|Microsoft|Расширенная защита SQL от угроз|2.22.4228.22540|HoneytokenActivitySecurityAlert|Активность учетной записи honeytoken|5|start=2018-02-21T14:20:26.6705617Z app=Kerberos suser=honey msg=С помощью учетной записи honey были выполнены следующие действия:\r\nВход на компьютер CLIENT2 через DC1. externalId=2014 cs1Label=url cs1=https\://contoso-corp.atp.azure.com/securityAlert/9249fe9a-c883-46dd-a4da-2a1fca5f211c cs2Label=trigger cs2=new

### <a name="malicious-request-of-data-protection-api-master-key"></a>Вредоносный запрос главного ключа API защиты данных 
10-29-2018  11:22:04    Auth.Error  192.168.0.202   1 2018-10-29T09:22:00.350864+00:00 DC3 CEF 3908 RetrieveDataProtectionBackupKeyS ï»¿0|Microsoft|Azure ATP|2.52.5704.46184|RetrieveDataProtectionBackupKeySecurityAlert|Вредоносный запрос конфиденциальных сведений для защиты данных|10|start=2018-10-29T09:19:45.6307993Z app=LsaRpc shost=CLIENT1 msg=Пользователь user1 предпринял 1 успешную попытку получить с компьютера CLIENT1 резервный ключ домена DPAPI из DC1. externalId=2020 cs1Label=url cs1=https\://contoso-corp.atp.azure.com/securityAlert/2f5717cb-2434-4d54-8af4-b2c6d14bc15c cs2Label=trigger cs2=new

### <a name="network-mapping-reconnaissance-dns"></a>Разведывательная атака путем сетевого сопоставления (DNS)
10-29-2018  11:20:02    Auth.Warning    192.168.0.202   1 2018-10-29T09:19:59.056894+00:00 DC3 CEF 3908 DnsReconnaissanceSecurityAlert ï»¿0|Microsoft|Azure ATP|2.52.5704.46184|DnsReconnaissanceSecurityAlert|Reconnaissance using DNS|5|start=2018-10-29T09:19:43.5033765Z app=Dns shost=CLIENT1 msg=Обнаружено подозрительное действие DNS, исходящее с компьютера CLIENT1 (который не является DNS-сервером), в отношении DC1. externalId=2007 cs1Label=url cs1=https\://contoso-corp.atp.azure.com/securityAlert/23937d33-ff71-484d-be0a-3c417fe573ce cs2Label=trigger cs2=new

### <a name="reconnaissance-using-directory-services-queries"></a>разведывательная атака с использованием запросов к службам каталогов; 
02-21-2018  16:22:08    Auth.Warning    192.168.0.220   1 2018-02-21T14:21:54.267658+00:00 CENTER CEF 6076 SamrReconnaissanceSecurityAlert ï»¿0|Microsoft|Azure ATP|2.22.4228.22540|SamrReconnaissanceSecurityAlert| Разведывательная атака с использованием перечисления служб каталогов |5|start=2018-02-21T14:19:41.9912772Z app= Samr shost=CLIENT1 suser=user1 outcome=Success msg= Были предприняты следующие попытки перечисления служб каталогов с использованием протокола SAMR в отношении DC1 с компьютера CLIENT1:\r\nУспешное перечисление всех групп в domain1.test.local пользователем user1. externalId=2019 cs1Label=url cs1=https\://contoso-corp.atp.azure.com/securityAlert/f295029a-ffae-408b-9dd0-55424c81eac0 cs2Label=trigger cs2=new

### <a name="remote-code-execution-attempt"></a>Попытка удаленного выполнения кода
10-29-2018  11:22:04    Auth.Warning    192.168.0.202   1 2018-10-29T09:22:00.100856+00:00 DC3 CEF 3908 RemoteExecutionSecurityAlert ï»¿0|Microsoft|Azure ATP|2.52.5704.46184|RemoteExecutionSecurityAlert|Remote code execution attempt|5|start=2018-10-29T09:19:45.0552367Z shost=CLIENT1 msg=На DC1 с компьютера CLIENT1 были предприняты следующие попытки удаленного выполнения.\r\nУспешное удаленное планирование одной или нескольких задач пользователем user1.\r\nНеуспешное удаленное планирование одной или нескольких задач пользователем user1.\r\nУспешное удаленное выполнение одного или нескольких методов WMI пользователем user1. externalId=2019 cs1Label=url cs1=https\://contoso-corp.atp.azure.com/securityAlert/f063c778-830c-4e9f-98d1-bc6c11c94e11 cs2Label=trigger cs2=new

### <a name="remote-code-execution-over-dns"></a>Удаленное выполнение кода через DNS
1-17-2019   08:24:54    Auth.Warning    192.168.0.202   1 2019-01-17T08:24:54.100856+00:00 DC3 CEF 3908 DnsRemoteCodeExecutionSecurityAlert ï»¿0|Microsoft|Azure ATP|2.63.0.0|DnsRemoteCodeExecutionSecurityAlert|[PREVIEW] Remote code execution over DNS|5|start=2019-01-17T08:24:54.5293800Z app=Dns shost=CLIENT1 msg=An actor attempted to run commands remotely on CLIENT1 from DC1, over DNS protocol. externalId=2036 cs1Label=url cs1=https\:////contoso-corp.atp.azure.com:13000/securityAlert/591f9769-d904-40b1-89fa-c307c2ca814f cs2Label=trigger cs2=new

### <a name="suspected-brute-force-attack-ldap"></a>Предполагаемая атака методом подбора (протокол LDAP)
02-21-2018  16:20:21    Auth.Warning    192.168.0.220   1 2018-02-21T14:20:06.156238+00:00 CENTER CEF 6076 LdapBruteForceSecurityAlert ï»¿0|Microsoft|Azure ATP|2.22.4228.22540|LdapBruteForceSecurityAlert|Атака методом подбора с использованием простой привязки LDAP|5|start=2018-02-21T14:19:41.7422810Z app=Ldap suser=Wofford Thurston shost=CLIENT1 msg=Предпринята попытка атаки методом подбора с использованием протокола Ldap в отношении Wofford Thurston (разработчика программного обеспечения) с компьютера CLIENT1 (100 попыток подбора). cnt=100 externalId=2004 cs1Label=url cs1=https\://contoso-corp.atp.azure.com/securityAlert/57b8ac96-7907-4971-9b27-ec77ad8c029a cs2Label=trigger cs2=update

### <a name="suspected-brute-force-attack-kerberos-ntlm"></a>Предполагаемая атака методом подбора (Kerberos, NTLM)
10-29-2018  11:20:47    Auth.Warning    192.168.0.202   1 2018-10-29T09:20:44.478827+00:00 DC3 CEF 3908 BruteForceSecurityAlert ï»¿0|Microsoft|Azure ATP|2.52.5704.46184|BruteForceSecurityAlert|Подозрительные неудачные попытки проверки подлинности|5|start=2018-10-29T09:19:44.9512286Z app=Kerberos shost=CLIENT1 msg=Обнаружены исходящие с компьютера CLIENT1 подозрительные неудачные попытки проверки подлинности, означающие возможную атаку методом подбора. externalId=2023 cs1Label=url cs1=https\://contoso-corp.atp.azure.com/securityAlert/85042c8e-27fa-49b3-8667-dabc1aa31580 cs2Label=trigger cs2=new

### <a name="suspected-golden-ticket-usage-encryption-downgrade"></a>Предполагаемое использование Golden Ticket (понижение уровня шифрования)
10-29-2018  11:25:07    Auth.Warning    192.168.0.202   1 2018-10-29T09:25:01.007701+00:00 DC3 CEF 3908 GoldenTicketEncryptionDowngradeS ï»¿0|Microsoft|Azure ATP|2.52.5704.46184|GoldenTicketEncryptionDowngradeSecurityAlert|Понижение уровня шифрования (потенциальная атака Golden Ticket)|5|start=2018-10-29T09:37:49.0849130Z app=Kerberos msg=W10-000007-Lap использовал более слабый метод шифрования (RC4) в запросе службы Kerberos (TGS_REQ) из W10-000007-Lap для доступа к host/domain1.test.local. externalId=2009 cs1Label=url cs1=https\://contoso-corp.atp.azure.com/securityAlert/f01f8403-88b2-437e-b4ad-d72485fe05ac cs2Label=trigger cs2=new

### <a name="suspected-golden-ticket-usage-non-existent-account"></a>Предполагаемое использование Golden Ticket (несуществующая учетная запись)
07-01-2018  14:28:49    Auth.Error  192.168.0.100   1 2018-07-01T11:28:35.546638+00:00 CENTER CEF 38768 ForgedPrincipalSecurityAlert ï»¿0|Microsoft|Расширенная защита SQL от угроз|2.39.0.0|ForgedPrincipalSecurityAlert|Билет Kerberos Golden Ticket — несуществующая учетная запись|10|start=2018-07-01T09:48:31.2567987Z app=Kerberos suser=domain1.test.local\fake msg=Учетная запись domain1.test.local\fake, которая не существует в Active Directory, использовала билет Kerberos. С 2 компьютеров был обнаружен билет, используемый для доступа к 3 ресурсам. Это может свидетельствовать о потенциальной атаке Golden Ticket. externalId=2027 cs1Label=url cs1=https\://contoso-corp.atp.azure.com:13000/securityAlert/98f050d4-9134-429c-8e54-d8eeb19849c4 cs2Label=trigger cs2=update

### <a name="suspected-golden-ticket-usage-ticket-anomaly"></a>Предполагаемое использование Golden Ticket (аномалия билета) 
1 2018-11-18T10:46:23.346946+00:00 MAXIMG-7050 CEF 24284 GoldenTicketSizeAnomalySecurityA 0|Microsoft|Azure ATP|2.56.0.0|GoldenTicketSizeAnomalySecurityAlert|[PREVIEW] Suspected Golden Ticket usage (ticket anomaly)|10|start=2018-11-18T10:44:12.9317797Z app=Kerberos shost=CLIENT2 suser=RFosdyke msg=Пользователь Renzo Fosdyke (Software Engineer) использовал подозрительный билет Kerberos с CLIENT2 для доступа к ldap/domain1.test.local. externalId=2032 cs1Label=url cs1=https\://contoso-corp.atp.azure.com:13000/securityAlert/63600e03-f423-49bf-a92d-4010e1d52b9f cs2Label=trigger cs2=update

### <a name="suspected-golden-ticket-usage-time-anomaly"></a>Предполагаемое использование Golden Ticket (аномальное время) 
02-21-2018  16:22:39    Auth.Error  192.168.0.220   1 2018-02-21T14:22:34.274054+00:00 CENTER CEF 6076 GoldenTicketSecurityAlert ï»¿0|Microsoft|Azure ATP|2.22.4228.22540|GoldenTicketSecurityAlert|Действие с использованием "золотого" билета Kerberos|10|start=2018-02-21T14:19:03.2416152Z app=Kerberos suser=Lanell Campos msg=Обнаружено подозрительное использование билета Kerberos, принадлежащего Lanell Campos (разработчику программного обеспечения), что указывает на возможную атаку Golden ticket. externalId=2022 cs1Label=url cs1=https\://contoso-corp.atp.azure.com/securityAlert/702c836e-6f49-4479-9892-80e8bccbfac0 cs2Label=trigger cs2=update

### <a name="suspected-golden-ticket-usage-forged-authorization-data"></a>Предполагаемое использование Golden Ticket (поддельные данные авторизации) 
10-29-2018  11:22:04    Auth.Error  192.168.0.202   1 2018-10-29T09:21:59.288337+00:00 DC3 CEF 3908 ForgedPacSecurityAlert ï»¿0|Microsoft|Azure ATP|2.52.5704.46184|ForgedPacSecurityAlert|Повышение привилегий с использованием поддельных данных авторизации|10|start=2018-10-29T09:19:43.6403358Z app=Kerberos suser=user1 msg=Пользователь user1 предпринял неудачную попытку повысить привилегии в DC1 на host/domain1.test.local с компьютера CLIENT1 при помощи поддельных данных авторизации. externalId=2013 cs1Label=url cs1=https\://contoso-corp.atp.azure.com/securityAlert/b698d438-5013-4bca-be0b-f219f8b69108 cs2Label=trigger cs2=new

### <a name="suspected-identity-theft-pass-the-hash"></a>Предполагаемая кража удостоверения (Pass-the-Hash)
02-21-2018  17:04:47    Auth.Error  192.168.0.220   1 2018-02-21T15:04:33.537583+00:00 CENTER CEF 6076 PassTheHashSecurityAlert ï»¿0|Microsoft|Azure ATP|2.22.4228.22540|PassTheHashSecurityAlert|Хищение удостоверения с помощью атаки Pass-the-Hash|10|start=2018-02-21T15:02:22.2577465Z app=Kerberos suser=Eugene Jenkins msg=Был украден хэш Eugene Jenkins (разработчика программного обеспечения) с одного из компьютеров, вход на который был выполнен ранее Eugene Jenkins (разработчиком программного обеспечения). Хэш использовался с компьютера CLIENT1. externalId=2017 cs1Label=url cs1=https\://contoso-corp.atp.azure.com/securityAlert/511f1487-2915-477d-be2e-04cfba702ccd cs2Label=trigger cs2=update

### <a name="suspected-identity-theft-pass-the-ticket"></a>Предполагаемая кража удостоверения (Pass-the-Ticket) 
02-21-2018  17:04:47    Auth.Error  192.168.0.220   1 2018-02-21T15:04:33.537583+00:00 CENTER CEF 6076 PassTheTicketSecurityAlert ï»¿0|Microsoft|Расширенная защита SQL от угроз|2.22.4228.22540|PassTheTicketSecurityAlert|Хищение удостоверения с помощью атаки Pass-the-Ticket|10|start=2018-02-21T15:02:22.2577465Z app=Kerberos suser=Eugene Jenkins msg=Были украдены билеты Kerberos, принадлежащие Eugene Jenkins (разработчику программного обеспечения), с компьютера Admin-PC на компьютер Victim-PC. Они использовались для доступа к krbtgt/DOMAIN1.TEST.LOCAL. externalId=2018 cs1Label=url cs1=https\://contoso-corp.atp.azure.com/securityAlert/511f1487-2915-477d-be2e-04cfba702ccd cs2Label=trigger cs2=new

### <a name="suspected-over-pass-the-hash-attack-encryption-downgrade"></a>Предполагаемая атака Overpass-the-Hash (понижение уровня шифрования) 
02-21-2018  16:21:07    Auth.Warning    192.168.0.220   1 2018-02-21T14:20:54.145833+00:00 CENTER CEF 6076 EncryptionDowngradeSecurityAlert ï»¿0|Microsoft|Azure ATP|2.22.4228.22540|EncryptionDowngradeSecurityAlert|Переход на более слабое шифрование|5|start=2018-02-21T14:19:41.8737870Z app=Kerberos msg= Согласно ранее установленному поведению для поля Encrypted_Timestamp сообщения AS_REQ от компьютера CLIENT1 был выполнен переход на более слабый метод шифрования. Это может быть результатом кражи учетных данных с помощью атаки Overpass-the-Hash с компьютера CLIENT1. externalId=2008 cs1Label=url cs1=https\://contoso-corp.atp.azure.com/securityAlert/6354b9ed-6a39-4f5b-b10e-f51bbee879d2 cs2Label=trigger cs2=update

### <a name="suspected-skeleton-key-attack-encryption-downgrade"></a>Предполагаемая атака путем использования мастер-ключа (понижение уровня шифрования) 
02-21-2018  16:21:07    Auth.Warning    192.168.0.220   1 2018-02-21T14:20:54.145833+00:00 CENTER CEF 6076 EncryptionDowngradeSecurityAlert ï»¿0|Microsoft|Azure ATP|2.22.4228.22540|EncryptionDowngradeSecurityAlert|переход на более слабое шифрование|5|start=2018-02-21T14:19:41.8737870Z app=Kerberos msg=Согласно ранее установленному поведению для поля ETYPE_INFO2 сообщения KRB_ERR от компьютера CLIENT1 был выполнен переход на более слабый метод шифрования. Это может быть результатом использования мастер-ключа в DC1. externalId=2010 cs1Label=url cs1=https\://contoso-corp.atp.azure.com/securityAlert/6354b9ed-6a39-4f5b-b10e-f51bbee879d2 cs2Label=trigger cs2=new

### <a name="suspected-dcsync-attack-replication-of-directory-services"></a>Предполагаемая атака DCSync (репликация служб каталогов)
02-21-2018  16:20:06    Auth.Warning    192.168.0.220   1 2018-02-21T14:19:54.254930+00:00 CENTER CEF 6076 MaliciousServiceCreationSecurity ï»¿0|Microsoft|Azure ATP|2.22.4228.22540|MaliciousServiceCreationSecurityAlert|Создание вредоносной службы|5|start=2018-02-21T14:19:41.7897808Z app=ServiceInstalledEvent shost=CLIENT1 msg=Пользователь user1 создал вредоносную службу для выполнения потенциально опасных команд на компьютере CLIENT1. externalId=2026 cs1Label=url cs1=https\://contoso-corp.atp.azure.com/securityAlert/179229b6-b791-4895-b5aa-fdf3747a325c cs2Label=trigger cs2=update

### <a name="suspicious-authentication-failures"></a>Подозрительные неудачные попытки проверки подлинности
02-21-2018  16:19:20    Auth.Warning    192.168.0.220   1 2018-02-21T14:19:15.397995+00:00 CENTER CEF 6076 BruteForceSecurityAlert ï»¿0|Microsoft|Azure ATP|2.22.4228.22540|BruteForceSecurityAlert|Подозрительные неудачные попытки проверки подлинности|5|start=2018-02-21T14:19:03.3831122Z app=Kerberos shost=CLIENT1 msg=Обнаружены исходящие с компьютера CLIENT1 подозрительные неудачные попытки проверки подлинности, означающие возможную атаку методом подбора. externalId=2023 cs1Label=url cs1=https\://contoso-corp.atp.azure.com/securityAlert/fea88fc7-4110-454d-816d-349032474fd6 cs2Label=trigger cs2=new

### <a name="suspicious-communication-over-dns"></a>Подозрительный обмен данными через DNS
10-04-2018  14:49:38    Auth.Warning    192.168.0.202   1 2018-10-04T11:49:25.954059+00:00 DC3 CEF 3604 DnsSuspiciousCommunicationSecuri ï»¿0|Microsoft|Azure ATP|2.49.5589.58606|DnsSuspiciousCommunicationSecurityAlert|Suspicious Communication over DNS|5|start=2018-10-04T11:49:11.0822077Z app=DnsEvent dhost= suspiciousdomainname msg=Клиент CLIENT1 отправлял подозрительные запросы DNS на разрешение suspiciousdomainname externalId=2031 cs1Label=url cs1=https\://contoso-corp.atp.azure.com/securityAlert/0fc77777-49ca-40b3-a7ba-7644f355539e cs2Label=trigger cs2=new

### <a name="suspicious-domain-controller-promotion-potential-dcshadow-attack"></a>Подозрительное повышение роли контроллера домена (потенциальная атака DCShadow)
07-12-2018  11:18:07    Auth.Error  192.168.0.200    1 2018-07-12T08:18:06.883880+00:00 DC1 CEF 3868 DirectoryServicesRoguePromotionS ï»¿0|Microsoft|Расширенная защита SQL от угроз|2.40.0.0|DirectoryServicesRoguePromotionSecurityAlert| **Подозрительное повышение роли контроллера домена (потенциальная атака DCShadow)**|10|start=2018-07-12T08:17:55.4067092Z app=Ldap shost=CLIENT1 msg=CLIENT1, который является компьютером в domain1.test.local, зарегистрирован как контроллер домена в DC1. externalId=2028 cs1Label=url cs1=https\://contoso-corp.atp.azure.com:13000/securityAlert/97c59b43-dc18-44ee-9826-8fd5d03bd53 cs2Label=trigger cs2=update

### <a name="suspicious-modification-of-sensitive-groups"></a>Подозрительное изменение привилегированных групп
10-29-2018  11:21:03    Auth.Warning    192.168.0.202   1 2018-10-29T09:20:49.667014+00:00 DC3 CEF 3908 AbnormalSensitiveGroupMembership ï»¿0|Microsoft|Azure ATP|2.52.5704.46184|AbnormalSensitiveGroupMembershipChangeSecurityAlert|Подозрительное изменение конфиденциальных групп|5|start=2018-10-29T09:19:43.3013729Z app=GroupMembershipChangeEvent suser=user1 msg=Пользователь user1 нехарактерным образом изменил членство в конфиденциальных группах. externalId=2024 cs1Label=url cs1=https\://contoso-corp.atp.azure.com/securityAlert/6f7e677e-f068-41e5-bada-708cd5a322b9 cs2Label=trigger cs2=new

### <a name="suspicious-replication-of-directory-services"></a>Подозрительная репликация служб каталогов
02-21-2018  16:21:22    Auth.Error  192.168.0.220   1 2018-02-21T14:21:13.978554+00:00 CENTER CEF 6076 DirectoryServicesReplicationSecu ï»¿0|Microsoft|Azure ATP|2.22.4228.22540|DirectoryServicesReplicationSecurityAlert|Подозрительная репликация служб каталогов|10|start=2018-02-21T14:19:03.9975656Z app=Drsr shost=CLIENT1 msg=Пользователь user1 успешно выполнил запросы на подозрительную репликацию с компьютера CLIENT1 на DC1. outcome=Success externalId=2006 cs1Label=url cs1=https\://contoso-corp.atp.azure.com/securityAlert/cb95648e-1b6f-4d3b-81b9-7605532787d7 cs2Label=trigger cs2=new

### <a name="suspicious-replication-request-potential-dcshadow-attack"></a>Подозрительный запрос на репликацию (потенциальная атака DCShadow)
07-12-2018  11:18:37    Auth.Error  192.168.0.200    1 2018-07-12T08:18:32.265989+00:00 DC1 CEF 3868 DirectoryServicesRogueReplicatio ï»¿0|Microsoft|Расширенная защита SQL от угроз|2.40.0.0|DirectoryServicesRogueReplicationSecurityAlert| **Подозрительный запрос на репликацию (потенциальная атака DCShadow)**|10|start=2018-07-12T08:17:55.3816102Z **app=Replication Activity** shost=CLIENT1 msg=CLIENT1, который не является допустимым контроллером домена в domain1.test.local, отправил изменения в объекты каталога в DC1. externalId=2029 cs1Label=url cs1=https\://contoso-corp.atp.azure.com:13000/securityAlert/1d5d1444-12cf-4db9-be48-39ebc2f51515 cs2Label=trigger cs2=new

### <a name="suspicious-service-creation"></a>Создание подозрительной службы 
10-29-2018  11:20:02    Auth.Warning    192.168.0.202   1 2018-10-29T09:19:59.164874+00:00 DC3 CEF 3908 MaliciousServiceCreationSecurity ï»¿0|Microsoft|Azure ATP|2.52.5704.46184|MaliciousServiceCreationSecurityAlert|Создание подозрительной службы|5|start=2018-10-29T09:19:44.9471965Z app=ServiceInstalledEvent shost=CLIENT1 msg=Пользователь user1 создал вредоносную службу для выполнения потенциально опасных команд на клиенте CLIENT1. externalId=2026 cs1Label=url cs1=https\://contoso-corp.atp.azure.com/securityAlert/118bbe3d-fe72-40de-80d0-2678b68aa027 cs2Label=trigger cs2=new

### <a name="suspicious-vpn-connection"></a>Подозрительные VPN-подключения
07-03-2018  13:13:12    Auth.Warning  192.168.0.200   1 2018-07-03T10:13:06.187834+00:00 DC1 CEF 2520 AbnormalVpnSecurityAlert ï»¿0|Microsoft|Расширенная защита SQL от угроз|2.39.0.0|AbnormalVpnSecurityAlert|Подозрительные VPN-подключения|5|start=2018-06-30T15:34:05.3887333Z app=VpnConnection suser=user1 msg=user1 подключился к VPN, используя 3 компьютера из 3 местоположений.     externalId=2025 cs1Label=url cs1=https\://contoso-corp.eng.atp.azure.com:13000/securityAlert/88c46b0e-372f-4c06-9935-67bd512c4f68 cs2Label=trigger cs2=new

### <a name="suspected-wannacry-ransomware-attack"></a>Предполагаемая атака программы-шантажиста WannaCry
02-21-2018  16:21:22    Auth.Warning    192.168.0.220   1 2018-02-21T14:21:13.916050+00:00 CENTER CEF 6076 AbnormalProtocolSecurityAlert ï»¿0|Microsoft|Azure ATP|2.22.4228.22540|AbnormalProtocolSecurityAlert|SuspectedWannaCryRansomwareAttack|5|start=2018-02-21T14:19:03.1981155Z app=Ntlm shost=CLIENT2 outcome=Success msg=Были предприняты попытки аутентификации с компьютера CLIENT2 в DC1 с использованием нестандартной реализации протоколов. Это может быть результатом выполнения атак с использованием вредоносных средств, таких как WannaCry. externalId=2035 cs1Label=url cs1=https\://contoso-corp.atp.azure.com/securityAlert/40fe98dd-aa42-4540-9d73-831486fdd1e4 cs2Label=trigger cs2=new

### <a name="suspected-brute-force-attack-smb"></a>Предполагаемая атака методом подбора (SMB)
002-21-2018 16:21:22    Auth.Warning    192.168.0.220   1 2018-02-21T14:21:13.916050+00:00 CENTER CEF 6076 AbnormalProtocolSecurityAlert ï»¿0|Microsoft|Azure ATP|2.22.4228.22540|AbnormalProtocolSecurityAlert|SuspectedBrutForceAttack|5|start=2018-02-21T14:19:03.1981155Z app=Ntlm shost=CLIENT2 outcome=Success msg=Были предприняты попытки аутентификации с компьютера CLIENT2 в DC1 с использованием нестандартной реализации протоколов. Это может быть результатом выполнения атак с использованием вредоносных средств, таких как Hydra. externalId=2033 cs1Label=url cs1=https\://contoso-corp.atp.azure.com/securityAlert/40fe98dd-aa42-4540-9d73-831486fdd1e4 cs2Label=trigger cs2=new

### <a name="suspected-use-of-metasploit-hacking-framework"></a>Предполагаемое использование платформы взлома Metasploit
002-21-2018 16:21:22    Auth.Warning    192.168.0.220   1 2018-02-21T14:21:13.916050+00:00 CENTER CEF 6076 AbnormalProtocolSecurityAlert ï»¿0|Microsoft|Azure ATP|2.22.4228.22540|AbnormalProtocolSecurityAlert|SuspectedAttackUsingMetasploit|5|start=2018-02-21T14:19:03.1981155Z app=Ntlm shost=CLIENT2 outcome=Success msg=Были предприняты попытки аутентификации с компьютера CLIENT2 в DC1 с использованием нестандартной реализации протоколов. Это может быть результатом выполнения атак с использованием вредоносных средств, таких как Metasploit. externalId=2034 cs1Label=url cs1=https\://contoso-corp.atp.azure.com/securityAlert/40fe98dd-aa42-4540-9d73-831486fdd1e4 cs2Label=trigger cs2=new

### <a name="suspected-overpass-the-hash-attack-kerberos"></a>Предполагаемая атака Overpass-the-Hash (Kerberos)
002-21-2018 16:21:22    Auth.Warning    192.168.0.220   1 2018-02-21T14:21:13.916050+00:00 CENTER CEF 6076 AbnormalProtocolSecurityAlert ï»¿0|Microsoft|Azure ATP|2.22.4228.22540|AbnormalProtocolSecurityAlert|SuspectedOverPassTheHashAttack|5|start=2018-02-21T14:19:03.1981155Z app=Ntlm shost=CLIENT2 outcome=Success msg=Были предприняты попытки аутентификации с компьютера CLIENT2 в DC1 с использованием нестандартной реализации протоколов. Это может быть результатом совершения злонамеренных действий с использованием протокола Kerberos. externalId=2002 cs1Label=url cs1=https\://contoso-corp.atp.azure.com/securityAlert/40fe98dd-aa42-4540-9d73-831486fdd1e4 cs2Label=trigger cs2=new

### <a name="user-and-ip-address-reconnaissance-smb"></a>Разведывательная атака с использованием пользователя и IP-адреса (SMB) 
002-21-2018 16:21:22    Auth.Warning    192.168.0.220   1 2018-02-21T14:21:13.916050+00:00 CENTER CEF 6076 AbnormalProtocolSecurityAlert ï»¿0|Microsoft|Azure ATP|2.22.4228.22540|AbnormalProtocolSecurityAlert|ReconnaissanceusingSMBSessionEnumeration|5|start=2018-02-21T14:19:03.1981155Z app=Ntlm shost=CLIENT2 outcome=Success msg=Были предприняты попытки аутентификации с компьютера CLIENT2 в DC1 с использованием нестандартной реализации протоколов. Это может быть результатом выполнения атак с использованием вредоносных средств, таких как Metasploit. externalId=2034 cs1Label=url cs1=https\://contoso-corp.atp.azure.com/securityAlert/40fe98dd-aa42-4540-9d73-831486fdd1e4 cs2Label=trigger cs2=new

## <a name="see-also"></a>См. также
- [Предварительные требования к Azure ATP](atp-prerequisites.md)
- [Планирование производительности Azure ATP](atp-capacity-planning.md)
- [Настройка сбора данных о событиях](configure-event-collection.md)
- [Настройка пересылки событий Windows](configure-event-forwarding.md)
- [Загляните на форум Azure ATP!](https://aka.ms/azureatpcommunity)
