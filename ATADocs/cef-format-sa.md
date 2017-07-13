---
title: "Справочник по журналу ATA SIEM | Документы Майкрософт"
description: "Примеры журналов подозрительных действий, отправляемых из ATA в систему SIEM."
keywords: 
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 6/21/2017
ms.topic: article
ms.prod: 
ms.service: advanced-threat-analytics
ms.technology: 
ms.assetid: 601b48ba-a327-4aff-a1f9-2377a2bb7a42
ms.reviewer: arzinger
ms.suite: ems
ms.openlocfilehash: ca460647fbed07820e8d19083d5aca19a05bc0a8
ms.sourcegitcommit: 470675730967e0c36ebc90fc399baa64e7901f6b
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/30/2017
---
*Применяется к Advanced Threat Analytics версии 1.8*


# Справочник по журналу ATA SIEM
<a id="ata-siem-log-reference" class="xliff"></a>

ATA может пересылать события, связанные с подозрительными действиями и оповещениями мониторинга, в систему SIEM. События, связанные с подозрительными действиями, передаются в формате CEF. В этой справочной статье приводятся примеры журналов подозрительных действий, пересылаемых в систему SIEM.

## Пример сведений о подозрительных действиях, обнаруженных ATA, в формате CEF
<a id="sample-ata-suspicious-activities-in-cef-format" class="xliff"></a>
В систему SIEM пересылаются следующие поля и их значения:

-   start — время начала оповещения;
-   suser — учетная запись (как правило, учетная запись пользователя), с которой связано оповещение;
-   shost — исходный компьютер оповещения;
-   outcome — указывает на успешность выполнения действия, указанного в оповещении;  
-   msg — описание оповещения;
-   cnt — число раз инициации оповещения (например, число угаданных паролей при атаке методом подбора);
-   app — протокол, используемый в оповещении;
-   externalId — идентификатор события, соответствующий оповещению, который ATA записывает в журнал событий;
-   cs#label и cs# — пользовательские строки, которые можно использовать в CEF. cs#label — это имя нового поля, а cs# — значение, например: cs1Label=url cs1=https://192.168.0.220/suspiciousActivity/5909ae198ca1ec04d05e65fa

В этом примере cs1 — это поле, содержащее URL-адрес оповещения.

## Образцы журналов
<a id="sample-logs" class="xliff"></a>

Приоритеты: 3=низкий; 5=средний; 10=высокий.

### Атака методом подбора — LDAP
<a id="bruteforce--ldap" class="xliff"></a>
05-03-2017          13:35:01               Auth.Warning    192.168.0.220     3 мая 10:35:01 CENTER ATA:CEF:0|Microsoft|ATA|.5942.64854|BruteForceSuspiciousActivity|Атака методом подбора с использованием простой привязки LDAP|5|start=2017-05-03T10:34:57.2785534Z app=Ldap suser=Darris Woods shost=CLIENT1 msg=Попытка атаки методом подбора с использованием протокола LDAP была предпринята в отношении пользователя Darris Woods (разработчик ПО) с компьютера CLIENT1 (76 попыток подбора). cnt=76 cs1Label=url cs1=https://192.168.0.220/suspiciousActivity/5909b2458ca1ec04d05e6a70

05-03-2017          13:35:05               Auth.Warning    192.168.0.220     3 мая 10:35:05 CENTER ATA:CEF:0|Microsoft|ATA|1.8.5942.64854|BruteForceSuspiciousActivity|Атака методом подбора с использованием простой привязки LDAP|5|start=2017-05-03T10:34:58.7004159Z app=Ldap suser=Dino Hopkins shost=CLIENT1 msg=Попытка атаки методом подбора с использованием протокола LDAP была предпринята в отношении пользователя Dino Hopkins (разработчик ПО) с компьютера CLIENT1 (3 попытки подбора). cnt=3 cs1Label=url cs1=https://192.168.0.220/suspiciousActivity/5909b2458ca1ec04d05e6a70

05-03-2017          13:35:05               Auth.Warning    192.168.0.220     3 мая 10:35:05 CENTER ATA:CEF:0|Microsoft|ATA|1.8.5942.64854|BruteForceSuspiciousActivity|Атака методом подбора с использованием простой привязки LDAP|5|start=2017-05-03T10:34:59.7269332Z app=Ldap suser=Dino Hopkins shost=CLIENT1 msg=Атака методом подбора с использованием протокола LDAP успешно проведена в отношении пользователя Dino Hopkins (разработчик ПО) с компьютера CLIENT1 (77 попыток подбора). cnt=77 cs1Label=url cs1=https://192.168.0.220/suspiciousActivity/5909b2458ca1ec04d05e6a70
### Атака методом подбора
<a id="bruteforce" class="xliff"></a>
05-14-2017          13:27:05               Auth.Warning    192.168.0.220     1 2017-05- ï»¿CEF:0|Microsoft|ATA|1.8.6455.41882|BruteForceSuspiciousActivity|Подозрительные ошибки проверки подлинности|5|start=2017-05-14T10:27:04.3904739Z app=Kerberos shost=CLIENT1 msg=Обнаружены подозрительные ошибки проверки подлинности с компьютера CLIENT1, указывающие на потенциальную атаку методом подбора. externalId=2023 cs1Label=url cs1=https://center/suspiciousActivity/591830f98ca1ec11d0c0d7f5
### Повышение привилегий
<a id="privilege-escalation" class="xliff"></a>
#### "Серебряный" билет
<a id="silver" class="xliff"></a>
05-10-2017          17:14:15               Auth.Error           192.168.0.220     1 2017-05-10T14:14:15.589415+00:00 CENTER ATA 596 ForgedPacSuspiciousActivity ï»¿CEF:0|Microsoft|ATA|1.8.6455.41882|ForgedPacSuspiciousActivity|Повышение привилегий с использованием поддельных данных авторизации|10|start=2017-05-10T14:11:51.8053059Z app=Kerberos suser=user1 msg=Пользователь user1 попытался повысить привилегии до HOST/client1 с компьютера CLIENT2 с помощью поддельных данных авторизации. externalId=2013 cs1Label=url cs1=https://center/suspiciousActivity/591320378ca1ec02543e4747
#### Золотой
<a id="gold" class="xliff"></a>
05-10-2017          17:13:30               Auth.Error           192.168.0.220     1 2017-05-10T14:13:30.244377+00:00 CENTER ATA 596 ForgedPacSuspiciousActivity ï»¿CEF:0|Microsoft|ATA|1.8.6455.41882|ForgedPacSuspiciousActivity|Повышение привилегий с использованием поддельных данных авторизации|10|start=2017-05-10T14:11:27.6455273Z app=Kerberos suser=user1 msg=Пользователь user1 попытался повысить привилегии для DC4 с компьютера CLIENT1 с помощью поддельных данных авторизации. externalId=2013 cs1Label=url cs1=https://center/suspiciousActivity/5913200a8ca1ec02543e3ea8
### Golden ticket
<a id="golden-ticket" class="xliff"></a>
05-14-2017          15:57:10               Auth.Warning    192.168.0.220     1 2017-05-14T12:57:10.392730+00:00 CENTER ATA 4732 EncryptionDowngradeSuspiciousAct ï»¿CEF:0|Microsoft|ATA|1.8.6455.41882|EncryptionDowngradeSuspiciousActivity|Переход на более слабое шифрование|5|start=2017-05-14T12:55:08.6913033Z app=Kerberos msg=Согласно ранее установленному поведению для поля TGT сообщения TGS_REQ от компьютера CLIENT1 был выполнен переход на более слабый метод шифрования. Это может быть результатом использования "золотого" билета на компьютере CLIENT1. externalId=2009 cs1Label=url cs1=https://center/suspiciousActivity/591854268ca1ec127ceec396
### Активность учетной записи honeytoken
<a id="honey-token-activity" class="xliff"></a>
05-11-2017          16:49:10               Auth.Warning    192.168.0.220     1 2017-05-11T13:49:10.725605+00:00 CENTER ATA 876 HoneytokenActivitySuspiciousActi ï»¿CEF:0|Microsoft|ATA|1.8.6455.41882|HoneytokenActivitySuspiciousActivity|Активность учетной записи honeytoken|5|start=2017-05-11T13:49:09.6455794Z app=Kerberos suser=privtriservice msg=Учетной записью privtriservice были выполнены следующие действия:\r\nПроверка подлинности с контроллера домена DC1 с использованием NTLM для доступа к корпоративным ресурсам через DC1. externalId=2014 cs1Label=url cs1=https://center/suspiciousActivity/59146bd68ca1ec036ce57d29
### Подозрительная репликация служб каталогов
<a id="suspicious-replication-of-directory-services" class="xliff"></a>
3 мая 11:02:28 CENTER ATA:CEF:0|Microsoft|ATA|1.8.5942.64854|DirectoryServicesReplicationSuspiciousActivity|Вредоносная репликация служб каталогов|10|start=2017-05-03T11:00:13.6560919Z suser=user1 shost=CLIENT1 outcome=Failure msg=Пользователем user1 выполнены попытки отправки вредоносных запросов репликации с компьютера CLIENT1 на контроллер домена DC1. cs1Label=url cs1=https://192.168.0.220/suspiciousActivity/5909b8c48ca1ec04d05ed28d
### Вредоносный запрос конфиденциальных сведений для защиты данных.
<a id="malicious-data-protection-private-information-request" class="xliff"></a>
3 мая 13:39:18 CENTER ATA:CEF:0|Microsoft|ATA|1.8.5942.64854|RetrieveDataProtectionBackupKeySuspiciousActivity|Вредоносный запрос конфиденциальных сведений для защиты данных|10|start=2017-05-03T13:37:06.4039886Z app=LsaRpc shost=CLIENT1 suser= outcome=Success msg=Неизвестный пользователь выполнил с компьютера CLIENT1 4 успешные попытки получить резервный ключ домена DPAPI из DC1. cs1Label=url cs1=https://192.168.0.220/suspiciousActivity/5909dd868ca1ec04d05fb01d
### Массовое удаление объектов
<a id="massive-object-deletion" class="xliff"></a>
05-14-2017          14:38:34               Auth.Warning    192.168.0.220     1 2017-05-14T11:38:34.898810+00:00 CENTER ATA 3748 MassiveObjectDeletionSuspiciousA ï»¿CEF:0|Microsoft|ATA|1.8.6455.41882|MassiveObjectDeletionSuspiciousActivity|Массовое удаление объектов|5|start=2017-05-14T11:33:32.0000000Z msg=496 объектов (9,75 % общего количества объектов AD) были удалены за короткий промежуток времени из домена domain1.test.local. cnt=496 externalId=2016 cs1Label=url cs1=https://center/suspiciousActivity/591841ba8ca1ec0ea4ad587a
### Over-Pass-the-Hash
<a id="over-pass-the-hash" class="xliff"></a>
05-14-2017          12:07:46               Auth.Warning    192.168.0.220     1 2017-05-14T09:07:46.652319+00:00 CENTER ATA 1116 EncryptionDowngradeSuspiciousAct ï»¿CEF:0|Microsoft|ATA|1.8.6455.41882|EncryptionDowngradeSuspiciousActivity|Переход на более слабое шифрование|5|start=2017-05-14T09:07:44.9933773Z app=Kerberos msg=Согласно ранее установленному поведению для поля Encrypted_Timestamp сообщения AS_REQ от компьютера CLIENT1 был выполнен переход на более слабый метод шифрования. Это может быть результатом кражи учетных данных с помощью атаки Overpass-the-Hash с компьютера CLIENT1. externalId=2010 cs1Label=url cs1=https://center/suspiciousActivity/59181e628ca1ec045cdfa929
### Pass-the-Hash
<a id="pass-the-hash" class="xliff"></a>
05-10-2017          17:48:51               Auth.Error           192.168.0.220     1 2017-05-10T14:48:51.998620+00:00 CENTER ATA 596 PassTheHashSuspiciousActivity ï»¿CEF:0|Microsoft|ATA|1.8.6455.41882|PassTheHashSuspiciousActivity|Кража идентификационных данных с помощью атаки Pass-the-Hash|10|start=2017-05-10T14:46:50.9463800Z app=Ntlm suser=user2 msg=Хэш пользователя user2 был украден с одного из компьютеров, на которые ранее входил пользователь user2, и был использован с компьютера CLIENT1. externalId=2017 cs1Label=url cs1=https://center/suspiciousActivity/591328538ca1ec02543f9a1a
### Перечисление учетных записей
<a id="account-enumeration" class="xliff"></a>
05-10-2017          16:44:22               Auth.Warning    192.168.0.220     1 2017-05-10T13:44:22.706381+00:00 CENTER ATA 596 AccountEnumerationSuspiciousActi ï»¿CEF:0|Microsoft|ATA|1.8.6455.41882|AccountEnumerationSuspiciousActivity|Разведывательная атака с использованием перечисления учетных записей|5|start=2017-05-10T13:44:20.9930644Z app=Kerberos shost=CLIENT3 msg=Обнаружено подозрительное перечисление учетных записей с использованием протокола Kerberos с компьютера CLIENT3. Злоумышленник предпринял всего 72 попытки подобрать имена учетных записей; в 2 случаях имена совпали с имеющимися именами учетных записей в Active Directory. externalId=2003 cs1Label=url cs1=https://center/suspiciousActivity/591319368ca1ec02543c56ee
### Проверка DNS
<a id="dns-recon" class="xliff"></a>
05-03-2017          13:16:57               Auth.Warning    192.168.0.220     3 мая 10:16:57 CENTER ATA:CEF:0|Microsoft|ATA|1.8.5942.64854|DnsReconnaissanceSuspiciousActivity|Разведывательная атака с использованием DNS|5|start=2017-05-03T10:16:41.8297467Z app=Dns shost=CLIENT1 msg=Обнаружена подозрительная активность DNS с компьютера CLIENT1 (не являющегося DNS-сервером) в отношении DC1. cs1Label=url cs1=https://192.168.0.220/suspiciousActivity/5909ae198ca1ec04d05e65fa 05-03-2017          13:24:21               Auth.Warning    192.168.0.220     3 мая 10:24:21 CENTER ATA:CEF:0|Microsoft|ATA|1.8.5942.64854|DnsReconnaissanceSuspiciousActivity|Разведывательная атака с использованием DNS|5|start=2017-05-03T10:24:08.0950753Z app=Dns shost=CLIENT1 request=contoso.com requestMethod=Axfr reason=NameError outcome=Failure msg=Обнаружена подозрительная активность DNS с компьютера CLIENT1 (не являющегося DNS-сервером). Был выполнен запрос к contoso.com (типа Axfr). Получен ответ NameError. cs1Label=url cs1=https://192.168.0.220/suspiciousActivity/5909ae198ca1ec04d05e65fa
### Перечисление сеансов SMB
<a id="smb-session-enumeration" class="xliff"></a>
3 мая 11:55:43 CENTER ATA:CEF:0|Microsoft|ATA|1.8.5942.64854|EnumerateSessionsSuspiciousActivity|Разведывательная атака с использованием перечисления сеансов SMB|5|start=2017-05-03T11:52:02.4360718Z app=SrvSvc shost=CLIENT1 msg=Попытки перечисления сеансов SMB были успешно выполнены с компьютера CLIENT1 в отношении DC1; получен доступ к учетной записи user1 (daf::1). cs1Label=url cs1=https://192.168.0.220/suspiciousActivity/5909c53f8ca1ec04d05f1cf1
### Перечисление SAMR
<a id="samr-enumeration" class="xliff"></a>
3 мая 11:44:48 CENTER ATA:CEF:0|Microsoft|ATA|1.8.5942.64854|SamrReconnaissanceSuspiciousActivity|Разведывательная атака с использованием перечисления служб каталогов|5|start=2017-05-03T11:42:46.5911225Z app=Samr shost=CLIENT1 suser=user1 outcome=Success msg=Были предприняты следующие попытки перечисления служб каталогов с использованием протокола SAMR в отношении DC1 с компьютера CLIENT1:\r\nУспешное перечисление всех групп в домене domain1.test.local пользователем user1 cs1Label=url cs1=https://192.168.0.220/suspiciousActivity/5909c2b08ca1ec04d05f0e19
### Удаленное выполнение
<a id="remote-execution" class="xliff"></a>
3 мая 12:36:47 CENTER ATA:CEF:0|Microsoft|ATA|1.8.5942.64854|RemoteExecutionSuspiciousActivity|Обнаружена попытка удаленного выполнения|3|start=2017-05-03T12:34:32.3714348Z app=ServiceControl shost=CLIENT1 suser=Administrator outcome=Success msg=Были выполнены следующие попытки удаленного выполнения в отношении DC1 с компьютера CLIENT1:\r\nУспешное удаленное создание PSEXESVC администратором. cs1Label=url cs1=https://192.168.0.220/suspiciousActivity/5909cedf8ca1ec04d05f5692
### использование мастер-ключа;
<a id="skeleton-key" class="xliff"></a>
05-14-2017          12:13:12               Auth.Warning    192.168.0.220     1 2017-05-14T09:13:12.102468+00:00 CENTER ATA 1116 EncryptionDowngradeSuspiciousAct ï»¿CEF:0|Microsoft|ATA|1.8.6455.41882|EncryptionDowngradeSuspiciousActivity|Переход на более слабое шифрование|5|start=2017-05-14T09:13:03.3509467Z app=Kerberos msg=Согласно ранее установленному поведению для поля ETYPE_INFO2 сообщения KRB_ERR от компьютера CLIENT2 был выполнен переход на более слабый метод шифрования. Это может быть результатом использования мастер-ключа в DC3. externalId=2011 cs1Label=url cs1=https://center/suspiciousActivity/59181fa88ca1ec045cdfe630
### Внедрение нестандартных протоколов.
<a id="unusual-protocol-implementation" class="xliff"></a>
3 мая 12:28:19 CENTER ATA:CEF:0|Microsoft|ATA|1.8.5942.64854|AbnormalProtocolSuspiciousActivity|Внедрение нестандартного протокола|5|start=2017-05-03T12:28:05.3561302Z app=Ntlm shost=CLIENT1 suser=Administrator outcome=Success msg=Администратор успешно прошел проверку подлинности с компьютера CLIENT1 в DC1 с использованием нестандартного протокола. Это может быть результатом использования вредоносных средств для проведения таких атак, как Pass-the-Hash или атака методом подбора. cs1Label=url cs1=https://192.168.0.220/suspiciousActivity/5909cce38ca1ec04d05f4ab4
### Предоставление данных привилегированной учетной записи
<a id="sensitive-account-credentials-exposed" class="xliff"></a>
3 мая 13:23:18 CENTER ATA:CEF:0|Microsoft|ATA|1.8.5942.64854|LdapSimpleBindCleartextPasswordSuspiciousActivity|Предоставление данных привилегированной учетной записи|3|start=2017-05-03T13:23:09.7798589Z app=Ldap shost=CLIENT1 suser=Administrator msg=Учетные данные администратора были предоставлены в виде обычного текста с использованием простой привязки LDAP с компьютера CLIENT1. cs1Label=url cs1=https://192.168.0.220/suspiciousActivity/5909d9c68ca1ec04d05f9918
### Предоставление учетных данных службами
<a id="services-exposing-account-credentials" class="xliff"></a>
3 мая 13:34:23 CENTER ATA:CEF:0|Microsoft|ATA|1.8.5942.64854|LdapSimpleBindCleartextPasswordSuspiciousActivity|Предоставление учетных данных службами|3|start=2017-05-03T13:28:36.5159194Z app=Ldap shost=daf::220 msg=Службы, работающие в daf::220 (daf::220), предоставляют данные учетных записей в виде обычного текста с использованием простой привязки LDAP. cs1Label=url cs1=https://192.168.0.220/suspiciousActivity/5909dc5f8ca1ec04d05fa8b1
### Атака Pass-the-Ticket.
<a id="pass-the-ticket" class="xliff"></a>
4 мая 13:15:41 CENTER ATA:CEF:0|Microsoft|ATA|1.8.5942.64854|PassTheTicketSuspiciousActivity|Кража идентификационных данных с использованием атаки Pass-the-Ticket|10|start=2017-05-04T13:13:44.5160000Z app=Kerberos shost=CLIENT1 suser=Administrator request=krbtgt/DOMAIN1.TEST.LOCAL msg=Билеты Kerberos администратора были украдены с компьютера CLIENT2 на компьютер CLIENT1 и использованы для доступа к krbtgt/DOMAIN1.TEST.LOCAL. cs2Label=ticketSourceComputer cs2=CLIENT2 cs3Label=ticketSourceComputerIpAddress cs3= cs1Label=url cs1=https://192.168.0.220/suspiciousActivity/590b29168ca1ec0ba438acf6

## См. также
<a id="see-also" class="xliff"></a>
- [Предварительные требования ATA](ata-prerequisites.md)
- [Планирование производительности ATA](ata-capacity-planning.md)
- [Настройка сбора данных о событиях](configure-event-collection.md)
- [Настройка пересылки событий Windows](configure-event-collection.md#configuring-windows-event-forwarding)
- [Ознакомьтесь с форумом ATA.](https://social.technet.microsoft.com/Forums/security/home?forum=mata)
