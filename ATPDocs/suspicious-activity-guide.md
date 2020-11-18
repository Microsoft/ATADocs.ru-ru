---
title: Руководство. Оповещения системы безопасности в Microsoft Defender для удостоверений
description: В этой статье приводится список оповещений системы безопасности, отправляемых Microsoft Defender для удостоверений.
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 10/27/2020
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.service: azure-advanced-threat-protection
ms.reviewer: itargoet
ms.suite: ems
ms.openlocfilehash: 11184c7bea435ae1168deb810ec54ec163d990f5
ms.sourcegitcommit: 38266d01b28ea6b084687b9bc3c4aa18e2dbb3b7
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/18/2020
ms.locfileid: "94851232"
---
# <a name="product-long-security-alerts"></a>Оповещения системы безопасности [!INCLUDE [Product long](includes/product-long.md)]

> [!NOTE]
> Функции [!INCLUDE [Product long](includes/product-long.md)], описанные на этой странице, также доступны на новом [портале](https://portal.cloudappsecurity.com).

В оповещениях системы безопасности [!INCLUDE [Product long](includes/product-long.md)] сообщается о подозрительных действиях, обнаруженных датчиками [!INCLUDE [Product short](includes/product-short.md)] в сети, а также о субъектах и компьютерах, вовлеченных в угрозы. Списки свидетельств оповещений содержат прямые ссылки на связанных пользователей и компьютеры, упрощая анализ.

Оповещения системы безопасности [!INCLUDE [Product short](includes/product-short.md)] можно разделить на следующие категории или этапы (соответствующие этапам в стандартной цепочке устранения кибератак). Ниже приведены ссылки на дополнительные сведения о каждом этапе, оповещениях, предназначенных для выявления разных типов атак, а также сведения об использовании этих оповещений для защиты сети.

1. [Оповещения этапа разведывательной атаки](reconnaissance-alerts.md)
1. [Оповещения этапа компрометации учетных данных](compromised-credentials-alerts.md)
1. [Оповещения этапа бокового смещения](lateral-movement-alerts.md)
1. [Оповещения этапа захвата управления доменом](domain-dominance-alerts.md)
1. [Оповещения этапа кражи данных](exfiltration-alerts.md)

Дополнительные сведения о структуре и общих компонентах всех оповещений системы безопасности [!INCLUDE [Product short](includes/product-short.md)] см. в руководстве [Основные сведения об оповещениях безопасности](understanding-security-alerts.md).

## <a name="security-alert-name-mapping-and-unique-external-ids"></a>Сопоставление имен оповещений безопасности и уникальные внешние коды

В следующей таблице приведено сопоставление между именами оповещений, их уникальными внешними идентификаторами и идентификаторами оповещений Microsoft Cloud App Security. Для сценариев и автоматизации специалисты Майкрософт рекомендуют использовать для оповещений внешние коды, а не имена, поскольку только внешние коды оповещений безопасности являются постоянными и не подлежат изменению.

### <a name="external-ids"></a>[Внешние идентификаторы](#tab/external)

> [!div class="mx-tdBreakAll"]
> |Имя оповещения системы безопасности|Уникальный внешний идентификатор|Статус|MITRE ATT&CK Matrix&trade;|
> |---|---|---|---|
> |[Разведывательная атака путем перечисления учетных записей](reconnaissance-alerts.md#account-enumeration-reconnaissance-external-id-2003)|2003|Средняя|Обнаружение|
> |[Рекогносцировка атрибутов Active Directory (протокол LDAP)](reconnaissance-alerts.md#active-directory-attributes-reconnaissance-ldap-external-id-2210)|2210|Средняя|Обнаружение|
> |[Кража данных по SMB](exfiltration-alerts.md#data-exfiltration-over-smb-external-id-2030)|2030|Высокий|Exfiltration,<br>Lateral movement,<br>Команды и управление|
> |[Действие Honeytoken](compromised-credentials-alerts.md#honeytoken-activity-external-id-2014)|2014|Средняя|Credential access,<br>Обнаружение|
> |[Вредоносный запрос главного ключа API защиты данных](domain-dominance-alerts.md#malicious-request-of-data-protection-api-master-key-external-id-2020)|2020|Высокий|Credential access|
> |[Рекогносцировка путем сетевого сопоставления (DNS)](reconnaissance-alerts.md#network-mapping-reconnaissance-dns-external-id-2007)|2007 г.|Средняя|Обнаружение|
> |[Попытка удаленного выполнения кода](domain-dominance-alerts.md#remote-code-execution-attempt-external-id-2019)|2019|Средняя|Execution,<br>Persistence,<br>Privilege escalation,<br>Defense evasion,<br>Путешествие по компьютерам|
> |[Удаленное выполнение кода через DNS](lateral-movement-alerts.md#remote-code-execution-over-dns-external-id-2036)|2036|Средняя|Privilege escalation,<br>Путешествие по компьютерам|
> |[Разведывательная атака, направленная на субъект безопасности (LDAP)](reconnaissance-alerts.md#security-principal-reconnaissance-ldap-external-id-2038)|2038|Средняя|Credential access|
> |[Предполагаемая атака методом подбора (Kerberos, NTLM)](compromised-credentials-alerts.md#suspected-brute-force-attack-kerberos-ntlm-external-id-2023)|2023|Средняя|Credential access|
> |[Предполагаемая атака методом подбора (протокол LDAP)](compromised-credentials-alerts.md#suspected-brute-force-attack-ldap-external-id-2004)|2004|Средняя|Credential access|
> |[Предполагаемая атака методом подбора (SMB)](compromised-credentials-alerts.md#suspected-brute-force-attack-smb-external-id-2033)|2033|Средняя|Путешествие по компьютерам|
> |[Предполагаемая атака DCShadow (повышение роли контроллера домена)](domain-dominance-alerts.md#suspected-dcshadow-attack-domain-controller-promotion-external-id-2028)|2028|Высокий|Defense evasion|
> |[Предполагаемая атака DCShadow (запрос на репликацию контроллера домена)](domain-dominance-alerts.md#suspected-dcshadow-attack-domain-controller-replication-request-external-id-2029)|2029|Высокий|Defense evasion|
> |[Предполагаемая атака DCSync (репликация служб каталогов)](domain-dominance-alerts.md#suspected-dcsync-attack-replication-of-directory-services-external-id-2006)|2006|Высокий|Persistence,<br>Credential access|
> |[Предполагаемое использование Golden Ticket (понижение уровня шифрования)](domain-dominance-alerts.md#suspected-golden-ticket-usage-encryption-downgrade-external-id-2009)|2009|Средняя|Privilege Escalation,<br>Lateral movement,<br>Persistence|
> |[Предполагаемое использование Golden Ticket (поддельные данные авторизации)](domain-dominance-alerts.md#suspected-golden-ticket-usage-forged-authorization-data-external-id-2013)|2013|Высокий|Privilege escalation,<br>Lateral movement,<br>Persistence|
> |[Предполагаемое использование Golden Ticket (несуществующая учетная запись)](domain-dominance-alerts.md#suspected-golden-ticket-usage-nonexistent-account-external-id-2027)|2027|Высокий|Privilege Escalation,<br>Lateral movement,<br>Persistence|
> |[Предполагаемое использование Golden Ticket (аномалия билета)](domain-dominance-alerts.md#suspected-golden-ticket-usage-ticket-anomaly-external-id-2032)|2032|Высокий|Privilege Escalation,<br>Lateral movement,<br>Persistence|
> |[Предполагаемое использование Golden Ticket (аномалия билета с использованием RBCD)](domain-dominance-alerts.md#suspected-golden-ticket-usage-ticket-anomaly-using-rbcd-external-id-2040)|2040|Высокий|Persistence|
> |[Предполагаемое использование Golden Ticket (аномальное время)](domain-dominance-alerts.md#suspected-golden-ticket-usage-time-anomaly-external-id-2022)|2022|Высокий|Privilege Escalation,<br>Lateral movement,<br>Persistence|
> |[Предполагаемая кража удостоверения (Pass-the-Hash)](lateral-movement-alerts.md#suspected-identity-theft-pass-the-hash-external-id-2017)|2017|Высокий|Боковое смещение|
> |[Предполагаемая кража удостоверения (Pass-the-Ticket)](lateral-movement-alerts.md#suspected-identity-theft-pass-the-ticket-external-id-2018)|2018|Высокая или средняя|Путешествие по компьютерам|
> |[Подозрение на раскрытие имени субъекта-службы Kerberos (внешний идентификатор 2410)](compromised-credentials-alerts.md#suspected-kerberos-spn-exposure-external-id-2410)|2 410|Высокий|Credential access|
> |[Предполагаемая попытка повышения прав доступа к службе Netlogon (использование уязвимости CVE-2020-1472)](compromised-credentials-alerts.md#suspected-netlogon-priv-elev-2411)|2411|Высокий|Повышение привилегий|
> |[Предполагаемые незаконные изменения при аутентификации NTLM](lateral-movement-alerts.md#suspected-ntlm-authentication-tampering-external-id-2039)|2039|Средняя|Privilege escalation, <br>Путешествие по компьютерам|
> |[Предполагаемая атака ретрансляции NTLM](lateral-movement-alerts.md#suspected-ntlm-relay-attack-exchange-account-external-id-2037)|2037|Средняя или низкая, если наблюдается при использовании протокола NTLM версии 2 с подписью|Privilege escalation, <br>Путешествие по компьютерам|
> |[Предполагаемая атака Overpass-the-Hash (Kerberos)](lateral-movement-alerts.md#suspected-overpass-the-hash-attack-kerberos-external-id-2002)|2002|Средняя|Путешествие по компьютерам|
> |[Подозрение на использование незаконного сертификата Kerberos](lateral-movement-alerts.md#suspected-rogue-kerberos-certificate-usage-external-id-2047)|2047|Высокий|Боковое смещение|
> |[Предполагаемая атака путем использования мастер-ключа (понижение уровня шифрования)](domain-dominance-alerts.md#suspected-skeleton-key-attack-encryption-downgrade-external-id-2010)|2010|Средняя|Lateral movement,<br>Persistence|
> |[Возможная манипуляция с пакетами SMB (использование уязвимости CVE-2020-0796) — (предварительная версия)](lateral-movement-alerts.md#suspected-smb-packet-manipulation-cve-2020-0796-exploitation-external-id-2406)|2406|Высокий|Боковое смещение|
> |[Предполагаемое использование платформы взлома Metasploit](compromised-credentials-alerts.md#suspected-use-of-metasploit-hacking-framework-external-id-2034)|2034|Средняя|Боковое смещение|
> |[Предполагаемая атака программы-шантажиста WannaCry](compromised-credentials-alerts.md#suspected-wannacry-ransomware-attack-external-id-2035)|2035|Средняя|Путешествие по компьютерам|
> |[Подозрительные добавления в привилегированные группы](domain-dominance-alerts.md#suspicious-additions-to-sensitive-groups-external-id-2024)|2024|Средняя|Credential access,<br>Сохраняемость|
> |[Подозрительный обмен данными через DNS](exfiltration-alerts.md#suspicious-communication-over-dns-external-id-2031)|2031|Средняя|Exfiltration|
> |[Создание подозрительной службы](domain-dominance-alerts.md#suspicious-service-creation-external-id-2026)|2026|Средняя|Execution,<br>Persistence,<br>Privilege Escalation,<br>Defense evasion,<br>Путешествие по компьютерам|
> |[Подозрительные VPN-подключения](compromised-credentials-alerts.md#suspicious-vpn-connection-external-id-2025)|2025|Средняя|Persistence,<br>Defense evasion|
> |[Разведывательная атака с использованием пользователей и членства в группах (SAMR)](reconnaissance-alerts.md#user-and-group-membership-reconnaissance-samr-external-id-2021)|2021|Средняя|Обнаружение|
> |[Разведывательная атака с применением данных пользователя и IP-адреса (SMB)](reconnaissance-alerts.md#user-and-ip-address-reconnaissance-smb-external-id-2012)|2012|Средняя|Обнаружение|

### <a name="cloud-app-security-ids"></a>[Идентификаторы Cloud App Security](#tab/cloud-app-security)

> [!div class="mx-tdBreakAll"]
> |Имя оповещения системы безопасности|Идентификатор оповещения Cloud App Security|
> |---|---|
> |[Разведывательная атака путем перечисления учетных записей](reconnaissance-alerts.md#account-enumeration-reconnaissance-external-id-2003)|ALERT_EXTERNAL_AATP_ACCOUNT_ENUMERATION_SECURITY_ALERT|
> |[Рекогносцировка атрибутов Active Directory (протокол LDAP)](reconnaissance-alerts.md#active-directory-attributes-reconnaissance-ldap-external-id-2210)|ALERT_EXTERNAL_AATP_LDAP_SENSITIVE_ATTRIBUTE_RECONNAISSANCE_SECURITY_ALERT|
> |[Кража данных по SMB](exfiltration-alerts.md#data-exfiltration-over-smb-external-id-2030)|ALERT_EXTERNAL_AATP_SMB_DATA_EXFILTRATION_SECURITY_ALERT|
> |[Действие Honeytoken](compromised-credentials-alerts.md#honeytoken-activity-external-id-2014)|ALERT_EXTERNAL_AATP_HONEYTOKEN_ACTIVITY_SECURITY_ALERT|
> |[Вредоносный запрос главного ключа API защиты данных](domain-dominance-alerts.md#malicious-request-of-data-protection-api-master-key-external-id-2020)|ALERT_EXTERNAL_AATP_RETRIEVE_DATA_PROTECTION_BACKUP_KEY_SECURITY_ALERT|
> |[Рекогносцировка путем сетевого сопоставления (DNS)](reconnaissance-alerts.md#network-mapping-reconnaissance-dns-external-id-2007)|ALERT_EXTERNAL_AATP_DNS_RECONNAISSANCE_SECURITY_ALERT|
> |[Попытка удаленного выполнения кода](domain-dominance-alerts.md#remote-code-execution-attempt-external-id-2019)|ALERT_EXTERNAL_AATP_REMOTE_EXECUTION_SECURITY_ALERT|
> |[Удаленное выполнение кода через DNS](lateral-movement-alerts.md#remote-code-execution-over-dns-external-id-2036)|ALERT_EXTERNAL_AATP_DNS_REMOTE_CODE_EXECUTION_SECURITY_ALERT|
> |[Разведывательная атака, направленная на субъект безопасности (LDAP)](reconnaissance-alerts.md#security-principal-reconnaissance-ldap-external-id-2038)|ALERT_EXTERNAL_AATP_LDAP_SEARCH_RECONNAISSANCE_SECURITY_ALERT|
> |[Предполагаемая атака методом подбора (Kerberos, NTLM)](compromised-credentials-alerts.md#suspected-brute-force-attack-kerberos-ntlm-external-id-2023)|ALERT_EXTERNAL_AATP_BRUTE_FORCE_SECURITY_ALERT|
> |[Предполагаемая атака методом подбора (протокол LDAP)](compromised-credentials-alerts.md#suspected-brute-force-attack-ldap-external-id-2004)|ALERT_EXTERNAL_AATP_LDAP_BRUTE_FORCE_SECURITY_ALERT|
> |[Предполагаемая атака методом подбора (SMB)](compromised-credentials-alerts.md#suspected-brute-force-attack-smb-external-id-2033)|ALERT_EXTERNAL_AATP_ABNORMAL_SMB_BRUTE_FORCE_SECURITY_ALERT|
> |[Предполагаемая атака DCShadow (повышение роли контроллера домена)](domain-dominance-alerts.md#suspected-dcshadow-attack-domain-controller-promotion-external-id-2028)|ALERT_EXTERNAL_AATP_DIRECTORY_SERVICES_ROGUE_PROMOTION_SECURITY_ALERT|
> |[Предполагаемая атака DCShadow (запрос на репликацию контроллера домена)](domain-dominance-alerts.md#suspected-dcshadow-attack-domain-controller-replication-request-external-id-2029)|ALERT_EXTERNAL_AATP_DIRECTORY_SERVICES_ROGUE_REPLICATION_SECURITY_ALERT|
> |[Предполагаемая атака DCSync (репликация служб каталогов)](domain-dominance-alerts.md#suspected-dcsync-attack-replication-of-directory-services-external-id-2006)|ALERT_EXTERNAL_AATP_DIRECTORY_SERVICES_REPLICATION_SECURITY_ALERT|
> |[Предполагаемое использование Golden Ticket (понижение уровня шифрования)](domain-dominance-alerts.md#suspected-golden-ticket-usage-encryption-downgrade-external-id-2009)|ALERT_EXTERNAL_AATP_GOLDEN_TICKET_ENCRYPTION_DOWNGRADE_SECURITY_ALERT|
> |[Предполагаемое использование Golden Ticket (поддельные данные авторизации)](domain-dominance-alerts.md#suspected-golden-ticket-usage-forged-authorization-data-external-id-2013)|ALERT_EXTERNAL_AATP_FORGED_PAC_SECURITY_ALERT|
> |[Предполагаемое использование Golden Ticket (несуществующая учетная запись)](domain-dominance-alerts.md#suspected-golden-ticket-usage-nonexistent-account-external-id-2027)|ALERT_EXTERNAL_AATP_FORGED_PRINCIPAL_SECURITY_ALERT|
> |[Предполагаемое использование Golden Ticket (аномалия билета)](domain-dominance-alerts.md#suspected-golden-ticket-usage-ticket-anomaly-external-id-2032)|ALERT_EXTERNAL_AATP_GOLDEN_TICKET_SIZE_ANOMALY_SECURITY_ALERT|
> |[Предполагаемое использование Golden Ticket (аномалия билета с использованием RBCD)](domain-dominance-alerts.md#suspected-golden-ticket-usage-ticket-anomaly-using-rbcd-external-id-2040)|ALERT_EXTERNAL_AATP_RESOURCE_BASED_CONSTRAINED_DELEGATION_GOLDEN_TICKET_SECURITY_ALERT|
> |[Предполагаемое использование Golden Ticket (аномальное время)](domain-dominance-alerts.md#suspected-golden-ticket-usage-time-anomaly-external-id-2022)|ALERT_EXTERNAL_AATP_GOLDEN_TICKET_SECURITY_ALERT|
> |[Предполагаемая кража удостоверения (Pass-the-Hash)](lateral-movement-alerts.md#suspected-identity-theft-pass-the-hash-external-id-2017)|ALERT_EXTERNAL_AATP_PASS_THE_HASH_SECURITY_ALERT|
> |[Предполагаемая кража удостоверения (Pass-the-Ticket)](lateral-movement-alerts.md#suspected-identity-theft-pass-the-ticket-external-id-2018)|ALERT_EXTERNAL_AATP_PASS_THE_TICKET_SECURITY_ALERT|
> |[Подозрение на раскрытие имени субъекта-службы Kerberos (внешний идентификатор 2410)](compromised-credentials-alerts.md#suspected-kerberos-spn-exposure-external-id-2410)|ALERT_EXTERNAL_AATP_KERBEROASTING_SECURITY_ALERT|
> |[Предполагаемая попытка повышения прав доступа к службе Netlogon (использование уязвимости CVE-2020-1472)](compromised-credentials-alerts.md#suspected-netlogon-priv-elev-2411)|ALERT_EXTERNAL_AATP_NETLOGON_BYPASS_SECURITY_ALERT|
> |[Предполагаемые незаконные изменения при аутентификации NTLM](lateral-movement-alerts.md#suspected-ntlm-authentication-tampering-external-id-2039)|ALERT_EXTERNAL_AATP_ABNORMAL_NTLM_SIGNING_SECURITY_ALERT|
> |[Предполагаемая атака ретрансляции NTLM](lateral-movement-alerts.md#suspected-ntlm-relay-attack-exchange-account-external-id-2037)|ALERT_EXTERNAL_AATP_NTLM_RELAY_SECURITY_ALERT|
> |[Предполагаемая атака Overpass-the-Hash (Kerberos)](lateral-movement-alerts.md#suspected-overpass-the-hash-attack-kerberos-external-id-2002)|ALERT_EXTERNAL_AATP_ABNORMAL_KERBEROS_OVERPASS_THE_HASH_SECURITY_ALERT|
> |[Подозрение на использование незаконного сертификата Kerberos](lateral-movement-alerts.md#suspected-rogue-kerberos-certificate-usage-external-id-2047)|ALERT_EXTERNAL_AATP_ROGUE_CERTIFICATE_USAGE_SECURITY_ALERT|
> |[Предполагаемая атака путем использования мастер-ключа (понижение уровня шифрования)](domain-dominance-alerts.md#suspected-skeleton-key-attack-encryption-downgrade-external-id-2010)|ALERT_EXTERNAL_AATP_SKELETON_KEY_ENCRYPTION_DOWNGRADE_SECURITY_ALERT|
> |[Возможная манипуляция с пакетами SMB (использование уязвимости CVE-2020-0796) — (предварительная версия)](lateral-movement-alerts.md#suspected-smb-packet-manipulation-cve-2020-0796-exploitation-external-id-2406)|ALERT_EXTERNAL_AATP_SMB_GHOST_SECURITY_ALERT|
> |[Предполагаемое использование платформы взлома Metasploit](compromised-credentials-alerts.md#suspected-use-of-metasploit-hacking-framework-external-id-2034)|ALERT_EXTERNAL_AATP_ABNORMAL_SMB_METASPLOIT_SECURITY_ALERT|
> |[Предполагаемая атака программы-шантажиста WannaCry](compromised-credentials-alerts.md#suspected-wannacry-ransomware-attack-external-id-2035)|ALERT_EXTERNAL_AATP_ABNORMAL_SMB_WANNA_CRY_SECURITY_ALERT|
> |[Подозрительные добавления в привилегированные группы](domain-dominance-alerts.md#suspicious-additions-to-sensitive-groups-external-id-2024)|ALERT_EXTERNAL_AATP_ABNORMAL_SENSITIVE_GROUP_MEMBERSHIP_CHANGE_SECURITY_ALERT|
> |[Подозрительный обмен данными через DNS](exfiltration-alerts.md#suspicious-communication-over-dns-external-id-2031)|ALERT_EXTERNAL_AATP_DNS_SUSPICIOUS_COMMUNICATION_SECURITY_ALERT|
> |[Создание подозрительной службы](domain-dominance-alerts.md#suspicious-service-creation-external-id-2026)|ALERT_EXTERNAL_AATP_MALICIOUS_SERVICE_CREATION_SECURITY_ALERT|
> |[Подозрительные VPN-подключения](compromised-credentials-alerts.md#suspicious-vpn-connection-external-id-2025)|ALERT_EXTERNAL_AATP_ABNORMAL_VPN_SECURITY_ALERT|
> |[Разведывательная атака с использованием пользователей и членства в группах (SAMR)](reconnaissance-alerts.md#user-and-group-membership-reconnaissance-samr-external-id-2021)|ALERT_EXTERNAL_AATP_SAMR_RECONNAISSANCE_SECURITY_ALERT|
> |[Разведывательная атака с применением данных пользователя и IP-адреса (SMB)](reconnaissance-alerts.md#user-and-ip-address-reconnaissance-smb-external-id-2012)|ALERT_EXTERNAL_AATP_ENUMERATE_SESSIONS_SECURITY_ALERT|

<!-- FROM TOP TABLE |[Suspected over-pass-the-hash attack (encryption downgrade)](lateral-movement-alerts.md#suspected-overpass-the-hash-attack-encryption-downgrade-external-id-2008)|2008|Medium|Lateral movement|-->
<!-- FROM BOTTOM TABLE |[Suspected over-pass-the-hash attack (encryption downgrade)](lateral-movement-alerts.md#suspected-overpass-the-hash-attack-encryption-downgrade-external-id-2008)|ALERT_EXTERNAL_AATP_OVERPASS_THE_HASH_ENCRYPTION_DOWNGRADE_SECURITY_ALERT|-->

---

> [!NOTE]
> Чтобы отключить оповещение системы безопасности, обратитесь в службу поддержки.

## <a name="see-also"></a>См. также

- [Работа с оповещениями системы безопасности](working-with-suspicious-activities.md)
- [Основные сведения об оповещениях безопасности](understanding-security-alerts.md)
- [Посетите форум по [!INCLUDE [Product short](includes/product-short.md)].](https://aka.ms/MDIcommunity)
