---
title: Оценка состояния безопасности удостоверений расширенной защиты от угроз Azure с ненадежным шифром | Документация Майкрософт
description: В этой статье представлен обзор отчетов об оценке состояния безопасности удостоверений с ненадежным шифром Azure ATP.
keywords: ''
author: mlottner
ms.author: mlottner
manager: rkarlin
ms.date: 07/08/2019
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.service: azure-advanced-threat-protection
ms.assetid: cc82212b-7d25-4ec7-828d-2475ff40d685
ms.reviewer: itargoet
ms.suite: ems
ms.openlocfilehash: 97ea6d080d2aae84bcf0675da853f503fd10b314
ms.sourcegitcommit: 15f882cf45776877fdaca8367a7a0fe7f06a7917
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/23/2019
ms.locfileid: "71185519"
---
# <a name="security-assessment-weak-cipher-usage---preview"></a>Оценка безопасности: использование ненадежного шифра — предварительная версия


## <a name="what-are-weak-ciphers"></a>Что такое слабые шифры? 

Шифрование использует шифры для шифрования данных. Например, шифр RC4 (Rivest Cipher 4, также известен как ARC4 или ARCFOUR, то есть Alleged RC4) — это один из них. Хотя RC4 отличается простотой и скоростью, с момента первоначального выпуска RC4 обнаружено несколько уязвимостей, что делает его небезопасным. Алгоритм RC4 особенно уязвим, если начало потока выходного ключа не отброшено или если используются неслучайные или связанные ключи. 

## <a name="how-do-i-use-this-security-assessment-to-improve-my-organizational-security-posture"></a>Как использовать эту оценку безопасности для повышения безопасности организации? 

1. Ознакомьтесь с оценкой безопасности по использованию ненадежного шифра. 
    ![Оценка использования ненадежного шифра](media/atp-cas-isp-weak-cipher-2.png)
1. Узнайте, почему идентифицированные клиенты и серверы используют ненадежные шифры.   
1. Устраните проблемы и отключите использование RC4 и других ненадежных шифров (таких как DES и 3DES). 
1. Подробные сведения об отключении RC4 см. в статье [Советы корпорации Майкрософт по безопасности](https://support.microsoft.com/help/2868725/microsoft-security-advisory-update-for-disabling-rc4). 

## <a name="remediation"></a>Серверы

Отключите клиенты и серверы, на которых требуется запретить использование комплектов шифров RC4, задав следующие разделы реестра. После отключения любой сервер или клиент, который обменивается данными с другим клиентом или сервером, который требует использования RC4, может предотвратить подключение. Клиенты, на которых развернут этот параметр, не смогут подключиться к сайтам, которым требуется RC4, а серверы, где развернут этот параметр, не смогут обслуживать клиенты, которым требуется RC4.

> [!NOTE]
>Обязательно протестируйте следующие параметры в управляемой среде, прежде чем включать их в рабочую среду. 
- [HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\SecurityProviders\SCHANNEL\Ciphers\RC4 128/128]   "Enabled"=dword:00000000 
- [HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\SecurityProviders\SCHANNEL\Ciphers\RC4 40/128]   "Enabled"=dword:00000000
- [HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\SecurityProviders\SCHANNEL\Ciphers\RC4 56/128]   "Enabled"=dword:00000000

Дополнительные сведения о скачивании и обновлении изменений реестра см. в статье [Советы корпорации Майкрософт по безопасности](https://docs.microsoft.com/security-updates/SecurityAdvisories/2013/2868725).


## <a name="next-steps"></a>Дальнейшие шаги
- [Фильтрация действий Azure ATP в Cloud App Security](atp-activities-filtering-mcas.md)
- [Загляните на форум Azure ATP!](https://aka.ms/azureatpcommunity)