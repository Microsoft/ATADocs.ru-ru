---
title: Руководство по оповещениям системы безопасности Azure ATP
d|Description: This article provides a list of the security alerts issued by Azure ATP.
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 04/23/2020
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.service: azure-advanced-threat-protection
ms.assetid: ca5d1c7b-11a9-4df3-84a5-f53feaf6e561
ms.reviewer: itargoet
ms.suite: ems
ms.openlocfilehash: ef739a54b271bcac344f282da547dff3c6d68eb7
ms.sourcegitcommit: fbb0768c392f9bccdd7e4adf0e9a0303c8d1922c
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2020
ms.locfileid: "84775868"
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

В следующей таблице приведено сопоставление между именами оповещений, их уникальными внешними идентификаторами и идентификаторами оповещений Microsoft Cloud App Security. Для сценариев и автоматизации специалисты Майкрософт рекомендуют использовать для оповещений внешние коды, а не имена, поскольку только внешние коды оповещений безопасности являются постоянными и не подлежат изменению.

# <a name="external-ids"></a>[Внешние идентификаторы](#tab/external)

> [!div class="mx-tdBreakAll"]
> |Имя оповещения системы безопасности|Уникальный внешний идентификатор|Статус|MITRE ATT&CK Matrix™|
> |---|---|---|---|
> |[Разведывательная атака путем перечисления учетных записей](atp-reconnaissance-alerts.md#account-enumeration-reconnaissance-external-id-2003)|2003|Средняя|Обнаружение|
> |[Кража данных по SMB](atp-exfiltration-alerts.md#data-exfiltration-over-smb-external-id-2030)|2030|Высокий|Exfiltration,<br>Боковое смещение,<br>Управление и контроль|
> |[Действие Honeytoken](atp-compromised-credentials-alerts.md#honeytoken-activity-external-id-2014)|2014|Средняя|Доступ к учетным данным,<br>Обнаружение|
> |[Вредоносный запрос главного ключа API защиты данных](atp-domain-dominance-alerts.md#malicious-request-of-data-protection-api-master-key-external-id-2020)|2020|Высокий|Доступ к учетным данным|
> |[Разведывательная атака путем сетевого сопоставления (DNS)](atp-reconnaissance-alerts.md#network-mapping-reconnaissance-dns-external-id-2007)|2007|Средняя|Обнаружение|
> |[Попытка удаленного выполнения кода](atp-domain-dominance-alerts.md#remote-code-execution-attempt-external-id-2019)|2019|Средняя|Execution,<br>Persistence,<br>Повышение привилегий,<br>Обход защиты,<br>Боковое смещение|
> |[Удаленное выполнение кода через DNS](atp-lateral-movement-alerts.md#remote-code-execution-over-dns-external-id-2036)|2036|Средняя|Повышение привилегий,<br>Боковое смещение|
> |[Разведывательная атака, направленная на субъект безопасности (LDAP)](atp-reconnaissance-alerts.md#security-principal-reconnaissance-ldap-external-id-2038)|2038|Средняя|Доступ к учетным данным|
> |[Предполагаемая атака методом подбора (Kerberos, NTLM)](atp-compromised-credentials-alerts.md#suspected-brute-force-attack-kerberos-ntlm-external-id-2023)|2023|Средняя|Доступ к учетным данным|
> |[Предполагаемая атака методом подбора (протокол LDAP)](atp-compromised-credentials-alerts.md#suspected-brute-force-attack-ldap-external-id-2004)|2004|Средняя|Доступ к учетным данным|
> |[Предполагаемая атака методом подбора (SMB)](atp-compromised-credentials-alerts.md#suspected-brute-force-attack-smb-external-id-2033)|2033|Средняя|Боковое смещение|
> |[Предполагаемая атака DCShadow (повышение роли контроллера домена)](atp-domain-dominance-alerts.md#suspected-dcshadow-attack-domain-controller-promotion-external-id-2028)|2028|Высокий|Обход защиты|
> |[Предполагаемая атака DCShadow (запрос на репликацию контроллера домена)](atp-domain-dominance-alerts.md#suspected-dcshadow-attack-domain-controller-replication-request-external-id-2029)|2029|Высокий|Обход защиты|
> |[Предполагаемая атака DCSync (репликация служб каталогов)](atp-domain-dominance-alerts.md#suspected-dcsync-attack-replication-of-directory-services-external-id-2006)|2006|Высокий|Persistence,<br>Доступ к учетным данным|
> |[Предполагаемое использование Golden Ticket (понижение уровня шифрования)](atp-domain-dominance-alerts.md#suspected-golden-ticket-usage-encryption-downgrade-external-id-2009)|2009|Средняя|Повышение привилегий,<br>Боковое смещение,<br>Persistence|
> |[Предполагаемое использование Golden Ticket (поддельные данные авторизации)](atp-domain-dominance-alerts.md#suspected-golden-ticket-usage-forged-authorization-data-external-id-2013)|2013|Высокий|Повышение привилегий,<br>Боковое смещение,<br>Persistence|
> |[Предполагаемое использование Golden Ticket (несуществующая учетная запись)](atp-domain-dominance-alerts.md#suspected-golden-ticket-usage-nonexistent-account-external-id-2027)|2027|Высокий|Повышение привилегий,<br>Боковое смещение,<br>Persistence|
> |[Предполагаемое использование Golden Ticket (аномалия билета)](atp-domain-dominance-alerts.md#suspected-golden-ticket-usage-ticket-anomaly-external-id-2032)|2032|Высокий|Повышение привилегий,<br>Боковое смещение,<br>Persistence|
> |[Предполагаемое использование Golden Ticket (аномальное время)](atp-domain-dominance-alerts.md#suspected-golden-ticket-usage-time-anomaly-external-id-2022)|2022|Высокий|Повышение привилегий,<br>Боковое смещение,<br>Persistence|
> |[Предполагаемая кража удостоверения (Pass-the-Hash)](atp-lateral-movement-alerts.md#suspected-identity-theft-pass-the-hash-external-id-2017)|2017|Высокий|Боковое смещение|
> |[Предполагаемая кража удостоверения (Pass-the-Ticket)](atp-lateral-movement-alerts.md#suspected-identity-theft-pass-the-ticket-external-id-2018)|2018|Высокая или средняя|Боковое смещение|
> |[Предполагаемые незаконные изменения при аутентификации NTLM](atp-lateral-movement-alerts.md#suspected-ntlm-authentication-tampering-external-id-2039)|2039|Средняя|Повышение привилегий, <br>Боковое смещение|
> |[Предполагаемая атака ретрансляции NTLM](atp-lateral-movement-alerts.md#suspected-ntlm-relay-attack-exchange-account-external-id-2037)|2037|Средняя или низкая, если наблюдается при использовании протокола NTLM версии 2 с подписью|Повышение привилегий, <br>Боковое смещение|
> |[Предполагаемая атака Overpass-the-Hash (понижение уровня шифрования)](atp-lateral-movement-alerts.md#suspected-overpass-the-hash-attack-encryption-downgrade-external-id-2008)|2008|Средняя|Боковое смещение|
> |[Предполагаемая атака Overpass-the-Hash (Kerberos)](atp-lateral-movement-alerts.md#suspected-overpass-the-hash-attack-kerberos-external-id-2002)|2002|Средняя|Боковое смещение|
> |[Предполагаемая атака путем использования мастер-ключа (понижение уровня шифрования)](atp-domain-dominance-alerts.md#suspected-skeleton-key-attack-encryption-downgrade-external-id-2010)|2010|Средняя|Боковое смещение,<br>Persistence|
> |[Возможная манипуляция с пакетами SMB (использование уязвимости CVE-2020-0796) — (предварительная версия)](atp-lateral-movement-alerts.md#suspected-smb-packet-manipulation-cve-2020-0796-exploitation-external-id-2406)|2406|Высокий|Боковое смещение|
> |[Предполагаемое использование платформы взлома Metasploit](atp-compromised-credentials-alerts.md#suspected-use-of-metasploit-hacking-framework-external-id-2034)|2034|Средняя|Боковое смещение|
> |[Предполагаемая атака программы-шантажиста WannaCry](atp-compromised-credentials-alerts.md#suspected-wannacry-ransomware-attack-external-id-2035)|2035|Средняя|Боковое смещение|
> |[Подозрительные добавления в привилегированные группы](atp-domain-dominance-alerts.md#suspicious-additions-to-sensitive-groups-external-id-2024)|2024|Средняя|Доступ к учетным данным,<br>Persistence|
> |[Подозрительный обмен данными через DNS](atp-exfiltration-alerts.md#suspicious-communication-over-dns-external-id-2031)|2031|Средняя|Exfiltration|
> |[Создание подозрительной службы](atp-domain-dominance-alerts.md#suspicious-service-creation-external-id-2026)|2026|Средняя|Execution,<br>Persistence,<br>Повышение привилегий,<br>Обход защиты,<br>Боковое смещение|
> |[Подозрительные VPN-подключения](atp-compromised-credentials-alerts.md#suspicious-vpn-connection-external-id-2025)|2025|Средняя|Persistence,<br>Обход защиты|
> |[Разведывательная атака с использованием пользователей и членства в группах (SAMR)](atp-reconnaissance-alerts.md#user-and-group-membership-reconnaissance-samr-external-id-2021)|2021|Средняя|Обнаружение|
> |[Разведывательная атака с применением данных пользователя и IP-адреса (SMB)](atp-reconnaissance-alerts.md#user-and-ip-address-reconnaissance-smb-external-id-2012)|2012|Средняя|Обнаружение|

# <a name="cloud-app-security-ids"></a>[Идентификаторы Cloud App Security](#tab/cloud-app-security)

> [!div class="mx-tdBreakAll"]
> |Имя оповещения системы безопасности|Идентификатор оповещения Cloud App Security|
> |---|---|
> |[Разведывательная атака путем перечисления учетных записей](atp-reconnaissance-alerts.md#account-enumeration-reconnaissance-external-id-2003)|ALERT_EXTERNAL_AATP_ACCOUNT_ENUMERATION_SECURITY_ALERT|
> |[Кража данных по SMB](atp-exfiltration-alerts.md#data-exfiltration-over-smb-external-id-2030)|ALERT_EXTERNAL_AATP_SMB_DATA_EXFILTRATION_SECURITY_ALERT|
> |[Действие Honeytoken](atp-compromised-credentials-alerts.md#honeytoken-activity-external-id-2014)|ALERT_EXTERNAL_AATP_HONEYTOKEN_ACTIVITY_SECURITY_ALERT|
> |[Вредоносный запрос главного ключа API защиты данных](atp-domain-dominance-alerts.md#malicious-request-of-data-protection-api-master-key-external-id-2020)|ALERT_EXTERNAL_AATP_RETRIEVE_DATA_PROTECTION_BACKUP_KEY_SECURITY_ALERT|
> |[Разведывательная атака путем сетевого сопоставления (DNS)](atp-reconnaissance-alerts.md#network-mapping-reconnaissance-dns-external-id-2007)|ALERT_EXTERNAL_AATP_DNS_RECONNAISSANCE_SECURITY_ALERT|
> |[Попытка удаленного выполнения кода](atp-domain-dominance-alerts.md#remote-code-execution-attempt-external-id-2019)|ALERT_EXTERNAL_AATP_REMOTE_EXECUTION_SECURITY_ALERT|
> |[Удаленное выполнение кода через DNS](atp-lateral-movement-alerts.md#remote-code-execution-over-dns-external-id-2036)|ALERT_EXTERNAL_AATP_DNS_REMOTE_CODE_EXECUTION_SECURITY_ALERT|
> |[Разведывательная атака, направленная на субъект безопасности (LDAP)](atp-reconnaissance-alerts.md#security-principal-reconnaissance-ldap-external-id-2038)|ALERT_EXTERNAL_AATP_LDAP_SEARCH_RECONNAISSANCE_SECURITY_ALERT|
> |[Предполагаемая атака методом подбора (Kerberos, NTLM)](atp-compromised-credentials-alerts.md#suspected-brute-force-attack-kerberos-ntlm-external-id-2023)|ALERT_EXTERNAL_AATP_BRUTE_FORCE_SECURITY_ALERT|
> |[Предполагаемая атака методом подбора (протокол LDAP)](atp-compromised-credentials-alerts.md#suspected-brute-force-attack-ldap-external-id-2004)|ALERT_EXTERNAL_AATP_LDAP_BRUTE_FORCE_SECURITY_ALERT|
> |[Предполагаемая атака методом подбора (SMB)](atp-compromised-credentials-alerts.md#suspected-brute-force-attack-smb-external-id-2033)|ALERT_EXTERNAL_AATP_ABNORMAL_SMB_BRUTE_FORCE_SECURITY_ALERT|
> |[Предполагаемая атака DCShadow (повышение роли контроллера домена)](atp-domain-dominance-alerts.md#suspected-dcshadow-attack-domain-controller-promotion-external-id-2028)|ALERT_EXTERNAL_AATP_DIRECTORY_SERVICES_ROGUE_PROMOTION_SECURITY_ALERT|
> |[Предполагаемая атака DCShadow (запрос на репликацию контроллера домена)](atp-domain-dominance-alerts.md#suspected-dcshadow-attack-domain-controller-replication-request-external-id-2029)|ALERT_EXTERNAL_AATP_DIRECTORY_SERVICES_ROGUE_REPLICATION_SECURITY_ALERT|
> |[Предполагаемая атака DCSync (репликация служб каталогов)](atp-domain-dominance-alerts.md#suspected-dcsync-attack-replication-of-directory-services-external-id-2006)|ALERT_EXTERNAL_AATP_DIRECTORY_SERVICES_REPLICATION_SECURITY_ALERT|
> |[Предполагаемое использование Golden Ticket (понижение уровня шифрования)](atp-domain-dominance-alerts.md#suspected-golden-ticket-usage-encryption-downgrade-external-id-2009)|ALERT_EXTERNAL_AATP_GOLDEN_TICKET_ENCRYPTION_DOWNGRADE_SECURITY_ALERT|
> |[Предполагаемое использование Golden Ticket (поддельные данные авторизации)](atp-domain-dominance-alerts.md#suspected-golden-ticket-usage-forged-authorization-data-external-id-2013)|ALERT_EXTERNAL_AATP_FORGED_PAC_SECURITY_ALERT|
> |[Предполагаемое использование Golden Ticket (несуществующая учетная запись)](atp-domain-dominance-alerts.md#suspected-golden-ticket-usage-nonexistent-account-external-id-2027)|ALERT_EXTERNAL_AATP_FORGED_PRINCIPAL_SECURITY_ALERT|
> |[Предполагаемое использование Golden Ticket (аномалия билета)](atp-domain-dominance-alerts.md#suspected-golden-ticket-usage-ticket-anomaly-external-id-2032)|ALERT_EXTERNAL_AATP_GOLDEN_TICKET_SIZE_ANOMALY_SECURITY_ALERT|
> |[Предполагаемое использование Golden Ticket (аномальное время)](atp-domain-dominance-alerts.md#suspected-golden-ticket-usage-time-anomaly-external-id-2022)|ALERT_EXTERNAL_AATP_GOLDEN_TICKET_SECURITY_ALERT|
> |[Предполагаемая кража удостоверения (Pass-the-Hash)](atp-lateral-movement-alerts.md#suspected-identity-theft-pass-the-hash-external-id-2017)|ALERT_EXTERNAL_AATP_PASS_THE_HASH_SECURITY_ALERT|
> |[Предполагаемая кража удостоверения (Pass-the-Ticket)](atp-lateral-movement-alerts.md#suspected-identity-theft-pass-the-ticket-external-id-2018)|ALERT_EXTERNAL_AATP_PASS_THE_TICKET_SECURITY_ALERT|
> |[Предполагаемые незаконные изменения при аутентификации NTLM](atp-lateral-movement-alerts.md#suspected-ntlm-authentication-tampering-external-id-2039)|ALERT_EXTERNAL_AATP_ABNORMAL_NTLM_SIGNING_SECURITY_ALERT|
> |[Предполагаемая атака ретрансляции NTLM](atp-lateral-movement-alerts.md#suspected-ntlm-relay-attack-exchange-account-external-id-2037)|ALERT_EXTERNAL_AATP_NTLM_RELAY_SECURITY_ALERT|
> |[Предполагаемая атака Overpass-the-Hash (понижение уровня шифрования)](atp-lateral-movement-alerts.md#suspected-overpass-the-hash-attack-encryption-downgrade-external-id-2008)|ALERT_EXTERNAL_AATP_OVERPASS_THE_HASH_ENCRYPTION_DOWNGRADE_SECURITY_ALERT|
> |[Предполагаемая атака Overpass-the-Hash (Kerberos)](atp-lateral-movement-alerts.md#suspected-overpass-the-hash-attack-kerberos-external-id-2002)|ALERT_EXTERNAL_AATP_ABNORMAL_KERBEROS_OVERPASS_THE_HASH_SECURITY_ALERT|
> |[Предполагаемая атака путем использования мастер-ключа (понижение уровня шифрования)](atp-domain-dominance-alerts.md#suspected-skeleton-key-attack-encryption-downgrade-external-id-2010)|ALERT_EXTERNAL_AATP_SKELETON_KEY_ENCRYPTION_DOWNGRADE_SECURITY_ALERT|
> |[Возможная манипуляция с пакетами SMB (использование уязвимости CVE-2020-0796) — (предварительная версия)](atp-lateral-movement-alerts.md#suspected-smb-packet-manipulation-cve-2020-0796-exploitation-external-id-2406)|ALERT_EXTERNAL_AATP_SMB_GHOST_SECURITY_ALERT|
> |[Предполагаемое использование платформы взлома Metasploit](atp-compromised-credentials-alerts.md#suspected-use-of-metasploit-hacking-framework-external-id-2034)|ALERT_EXTERNAL_AATP_ABNORMAL_SMB_METASPLOIT_SECURITY_ALERT|
> |[Предполагаемая атака программы-шантажиста WannaCry](atp-compromised-credentials-alerts.md#suspected-wannacry-ransomware-attack-external-id-2035)|ALERT_EXTERNAL_AATP_ABNORMAL_SMB_WANNA_CRY_SECURITY_ALERT|
> |[Подозрительные добавления в привилегированные группы](atp-domain-dominance-alerts.md#suspicious-additions-to-sensitive-groups-external-id-2024)|ALERT_EXTERNAL_AATP_ABNORMAL_SENSITIVE_GROUP_MEMBERSHIP_CHANGE_SECURITY_ALERT|
> |[Подозрительный обмен данными через DNS](atp-exfiltration-alerts.md#suspicious-communication-over-dns-external-id-2031)|ALERT_EXTERNAL_AATP_DNS_SUSPICIOUS_COMMUNICATION_SECURITY_ALERT|
> |[Создание подозрительной службы](atp-domain-dominance-alerts.md#suspicious-service-creation-external-id-2026)|ALERT_EXTERNAL_AATP_MALICIOUS_SERVICE_CREATION_SECURITY_ALERT|
> |[Подозрительные VPN-подключения](atp-compromised-credentials-alerts.md#suspicious-vpn-connection-external-id-2025)|ALERT_EXTERNAL_AATP_ABNORMAL_VPN_SECURITY_ALERT|
> |[Разведывательная атака с использованием пользователей и членства в группах (SAMR)](atp-reconnaissance-alerts.md#user-and-group-membership-reconnaissance-samr-external-id-2021)|ALERT_EXTERNAL_AATP_SAMR_RECONNAISSANCE_SECURITY_ALERT|
> |[Разведывательная атака с применением данных пользователя и IP-адреса (SMB)](atp-reconnaissance-alerts.md#user-and-ip-address-reconnaissance-smb-external-id-2012)|ALERT_EXTERNAL_AATP_ENUMERATE_SESSIONS_SECURITY_ALERT|

> [!NOTE]
> Чтобы отключить оповещение системы безопасности, обратитесь в службу поддержки.

## <a name="see-also"></a>См. также

- [Работа с оповещениями системы безопасности](working-with-suspicious-activities.md)
- [Основные сведения об оповещениях безопасности](understanding-security-alerts.md)
- [Загляните на форум Azure ATP!](https://aka.ms/azureatpcommunity)
