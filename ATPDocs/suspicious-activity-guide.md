---
title: Руководство по оповещениям системы безопасности Azure ATP | Документы Майкрософт
d|Description: This article provides a list of the security alerts issued by Azure ATP.
keywords: ''
author: shsagir
ms.author: shsagir
manager: rkarlin
ms.date: 09/15/2019
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.service: azure-advanced-threat-protection
ms.assetid: ca5d1c7b-11a9-4df3-84a5-f53feaf6e561
ms.reviewer: itargoet
ms.suite: ems
ms.openlocfilehash: d889c92d29b8c578c5af9596bc6a9946bc9d87f9
ms.sourcegitcommit: 9673eb49729a06d3a25d52c0f43c76ac61b9cf89
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/12/2020
ms.locfileid: "75907794"
---
# <a name="azure-atp-security-alerts"></a>Оповещения системы безопасности Azure ATP

> [!NOTE]
> Функции Azure ATP, описанные на этой странице, также доступны на новом [портале](https://portal.cloudappsecurity.com).

Оповещения системы безопасности Azure ATP сообщают о подозрительных действиях, обнаруженных датчиками Azure ATP в сети, а также о субъектах и компьютерах, вовлеченных в угрозы. Списки свидетельств оповещений содержат прямые ссылки на связанных пользователей и компьютеры, упрощая анализ.

Предупреждения системы безопасности Azure ATP можно разделить на следующие категории или этапы (соответствующие этапам в стандартной цепочке устранения кибератак). Ниже приведены ссылки на дополнительные сведения о каждом этапе, оповещениях, предназначенных для выявления разных типов атак, а также сведения об использовании этих оповещений для защиты сети.

  1. [Оповещения этапа разведывательной атаки](atp-reconnaissance-alerts.md)
  2. [Оповещения этапа компрометации учетных данных](atp-compromised-credentials-alerts.md)
  3. [Оповещения этапа бокового смещения](atp-lateral-movement-alerts.md)
  4. [Оповещения этапа захвата управления доменом](atp-domain-dominance-alerts.md)
  5. [Оповещения этапа кражи данных](atp-exfiltration-alerts.md)

Дополнительные сведения о структуре и общих компонентах всех оповещений системы безопасности Azure ATP см. в разделе [Основные сведения об оповещениях безопасности](understanding-security-alerts.md).

## <a name="security-alert-name-mapping-and-unique-external-ids"></a>Сопоставление имен оповещений безопасности и уникальные внешние коды

В версии 2.56 все существующие оповещения безопасности Azure ATP были переименованы для упрощения. Сопоставление между старыми и новыми именами и соответствующие уникальные коды externalId приведены в следующей таблице. Для сценариев и автоматизации специалисты Майкрософт рекомендуют использовать для оповещений внешние коды, а не имена, поскольку только внешние коды оповещений безопасности являются постоянными и не подлежат изменению.

> [!div class="mx-tableFixed"] 

|Новое имя оповещения системы безопасности|Предыдущее имя оповещения системы безопасности|Уникальный внешний идентификатор|Статус|MITRE ATT&CK Matrix™ |
|---------|----------|---------|---------|---------|
|[Разведывательная атака путем перечисления учетных записей](atp-reconnaissance-alerts.md#account-enumeration-reconnaissance-external-id-2003)|Разведывательная атака с использованием перечисления учетных записей.|2003|Средняя|Обнаружение|
|[Кража данных по SMB](atp-exfiltration-alerts.md#data-exfiltration-over-smb-external-id-2030)| Н/Д| 2030|Высокий|Exfiltration,<br>Lateral movement,<br>Command and control|
|[Действие Honeytoken](atp-compromised-credentials-alerts.md#honeytoken-activity-external-id-2014)|Действие Honeytoken|2014|Средняя|Credential access,<br> Обнаружение|
|[Вредоносный запрос главного ключа API защиты данных](atp-domain-dominance-alerts.md#malicious-request-of-data-protection-api-master-key-external-id-2020)|Вредоносный запрос конфиденциальных сведений для защиты данных.|2020|Высокий|Credential access|
|[Рекогносцировка путем сетевого сопоставления (DNS)](atp-reconnaissance-alerts.md#network-mapping-reconnaissance-dns-external-id-2007)|Разведывательная атака с использованием DNS.|2007|Средняя|Обнаружение|
|[Попытка удаленного выполнения кода](atp-domain-dominance-alerts.md#remote-code-execution-attempt-external-id-2019)|Попытка удаленного выполнения кода|2019|Средняя|Execution,<br> Persistence,<br> Privilege escalation,<br> Defense evasion,<br> Боковое смещение|
|[Удаленное выполнение кода через DNS](atp-lateral-movement-alerts.md#remote-code-execution-over-dns-external-id-2036)|Н/Д|2036|Средняя|Privilege escalation,<br> Боковое смещение|
|[Рекогносцировка, направленная на субъект безопасности (LDAP)](atp-reconnaissance-alerts.md#security-principal-reconnaissance-ldap-external-id-2038)|Н/Д|2038|Средняя|Credential access|
|[Предполагаемая атака методом подбора (Kerberos, NTLM)](atp-compromised-credentials-alerts.md#suspected-brute-force-attack-kerberos-ntlm-external-id-2023)|Подозрительные неудачные попытки проверки подлинности|2023|Средняя|Credential access|
|[Предполагаемая атака методом подбора (протокол LDAP)](atp-compromised-credentials-alerts.md#suspected-brute-force-attack-ldap-external-id-2004)|Атака методом подбора с помощью простой привязки LDAP|2004|Средняя|Credential access|
|[Предполагаемая атака методом подбора (SMB)](atp-compromised-credentials-alerts.md#suspected-brute-force-attack-smb-external-id-2033)|Нестандартная реализация протоколов (потенциальное использование вредоносных средств, таких как Hydra)|2033|Средняя|Боковое смещение|
|[Предполагаемая атака DCShadow (повышение роли контроллера домена)](atp-domain-dominance-alerts.md#suspected-dcshadow-attack-domain-controller-promotion-external-id-2028)|Подозрительное повышение роли контроллера домена (потенциальная атака DCShadow)|2028|Высокий|Defense evasion|
|[Предполагаемая атака DCShadow (запрос на репликацию контроллера домена)](atp-domain-dominance-alerts.md#suspected-dcshadow-attack-domain-controller-replication-request-external-id-2029)|Подозрительный запрос на репликацию контроллера домена (потенциальная атака DCShadow)|2029|Высокий|Defense evasion|
|[Предполагаемая атака DCSync (репликация служб каталогов)](atp-domain-dominance-alerts.md#suspected-dcsync-attack-replication-of-directory-services-external-id-2006)|вредоносная репликация служб каталогов;|2006|Высокий|Persistence,<br> Credential access|
|[Предполагаемое использование Golden Ticket (понижение уровня шифрования)](atp-domain-dominance-alerts.md#suspected-golden-ticket-usage-encryption-downgrade-external-id-2009)|Понижение уровня шифрования (потенциальная атака Golden Ticket)|2009|Средняя|Privilege Escalation,<br> Lateral movement,<br>Persistence|
|[Предполагаемое использование Golden Ticket (поддельные данные авторизации)](atp-domain-dominance-alerts.md#suspected-golden-ticket-usage-forged-authorization-data-external-id-2013)|Атака, направленная на повышение привилегий с использованием поддельных данных авторизации|2013|Высокий|Privilege escalation,<br>Lateral movement,<br>Persistence|
|[Предполагаемое использование Golden Ticket (несуществующая учетная запись)](atp-domain-dominance-alerts.md#suspected-golden-ticket-usage-nonexistent-account-external-id-2027)|Атака Golden Ticket Kerberos — несуществующая учетная запись|2027|Высокий|Privilege Escalation,<br> Lateral movement,<br>Persistence|
|[Предполагаемое использование Golden Ticket (аномалия билета)](atp-domain-dominance-alerts.md#suspected-golden-ticket-usage-ticket-anomaly-external-id-2032)|Н/Д|2032|Высокий|Privilege Escalation,<br> Lateral movement,<br>Persistence|
|[Предполагаемое использование Golden Ticket (аномальное время)](atp-domain-dominance-alerts.md#suspected-golden-ticket-usage-time-anomaly-external-id-2022)|Атака Golden Ticket в Kerberos — аномальное время|2022|Высокий|Privilege Escalation,<br> Lateral movement,<br>Persistence|
|[Предполагаемая кража удостоверения (Pass-the-Hash)](atp-lateral-movement-alerts.md#suspected-identity-theft-pass-the-hash-external-id-2017)|Кража удостоверения с помощью атаки Pass-the-Hash|2017|Высокий|Боковое смещение|
|[Предполагаемая кража удостоверения (Pass-the-Ticket)](atp-lateral-movement-alerts.md#suspected-identity-theft-pass-the-ticket-external-id-2018)|Кража удостоверения с помощью атаки Pass-the-Ticket|2018|Высокая или средняя|Боковое смещение|
|[Предполагаемые незаконные изменения при аутентификации NTLM](atp-lateral-movement-alerts.md#suspected-ntlm-authentication-tampering-external-id-2039)|Н/Д|2039|Средняя|Privilege escalation, <br>Боковое смещение|
|[Предполагаемая атака ретрансляции NTLM](atp-lateral-movement-alerts.md#suspected-ntlm-relay-attack-exchange-account-external-id-2037)|Н/Д|2037|Средняя или низкая, если наблюдается при использовании протокола NTLM версии 2 с подписью|Privilege escalation, <br> Боковое смещение|
|[Предполагаемая атака Overpass-the-Hash (понижение уровня шифрования)](atp-lateral-movement-alerts.md#suspected-overpass-the-hash-attack-encryption-downgrade-external-id-2008)|Понижение уровня шифрования (потенциальная атака Overpass-the-Hash)|2008|Средняя|Боковое смещение|
|[Предполагаемая атака Overpass-the-Hash (Kerberos)](atp-lateral-movement-alerts.md#suspected-overpass-the-hash-attack-kerberos-external-id-2002)|Нестандартная реализация протокола Kerberos (потенциальная атака Overpass-the-Hash)|2002|Средняя|Боковое смещение|
|[Предполагаемая атака путем использования мастер-ключа (понижение уровня шифрования)](atp-domain-dominance-alerts.md#suspected-skeleton-key-attack-encryption-downgrade-external-id-2010)|Понижение уровня шифрования (потенциальная атака с использованием мастер-ключа)|2010|Средняя|Lateral movement,<br> Persistence|
|[Предполагаемое использование платформы взлома Metasploit](atp-compromised-credentials-alerts.md#suspected-use-of-metasploit-hacking-framework-external-id-2034)|Нестандартная реализация протоколов (потенциальное использование средств взлома Metasploit)|2034|Средняя|Боковое смещение|
|[Предполагаемая атака программы-шантажиста WannaCry](atp-compromised-credentials-alerts.md#suspected-wannacry-ransomware-attack-external-id-2035)|Нестандартная реализация протоколов (потенциальная атака программы-шантажиста WannaCry)|2035|Средняя|Боковое смещение|
|[Подозрительный обмен данными через DNS](atp-exfiltration-alerts.md#suspicious-communication-over-dns-external-id-2031)|Подозрительный обмен данными через DNS|2031|Средняя|Exfiltration|
|[Подозрительные добавления в привилегированные группы](atp-domain-dominance-alerts.md#suspicious-additions-to-sensitive-groups-external-id-2024)|Подозрительные добавления в привилегированные группы|2024|Средняя|Credential access,<br>Persistence|
|[Создание подозрительной службы](atp-domain-dominance-alerts.md#suspicious-service-creation-external-id-2026)|Создание подозрительной службы|2026|Средняя|Execution,<br> Persistence,<br> Privilege Escalation,<br> Defense evasion,<br>Боковое смещение|
|[Подозрительные VPN-подключения](atp-compromised-credentials-alerts.md#suspicious-vpn-connection-external-id-2025)|Подозрительные VPN-подключения|2025|Средняя|Persistence,<br>Defense evasion|
|[Разведывательная атака с использованием пользователей и членства в группах (SAMR)](atp-reconnaissance-alerts.md#user-and-group-membership-reconnaissance-samr-external-id-2021)|разведывательная атака с использованием запросов к службам каталогов;|2021|Средняя|Обнаружение|
|[Разведывательная атака с использованием пользователя и IP-адреса (SMB)](atp-reconnaissance-alerts.md#user-and-ip-address-reconnaissance-smb-external-id-2012)|Разведывательная атака с использованием перечисления сеансов SMB|2012|Средняя|Обнаружение|
|

> [!NOTE]
> Чтобы отключить оповещение системы безопасности, обратитесь в службу поддержки.


## <a name="see-also"></a>См. также
- [Работа с оповещениями системы безопасности](working-with-suspicious-activities.md)
- [Основные сведения об оповещениях безопасности](understanding-security-alerts.md)
- [Загляните на форум Azure ATP!](https://aka.ms/azureatpcommunity)
