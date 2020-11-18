---
title: Отчет об оценке уровня безопасности ненадежного шифра в защитнике Майкрософт для идентификации
description: В этой статье приводятся общие сведения о защитнике Майкрософт для отчета об оценке ненадежного шифрования с помощью удостоверения.
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 10/26/2020
ms.topic: how-to
ms.collection: M365-security-compliance
ms.service: azure-advanced-threat-protection
ms.reviewer: itargoet
ms.suite: ems
ms.openlocfilehash: a27d972e95c2c6b4ed4d87ebad747ef14ac0f24d
ms.sourcegitcommit: e2227c0b0e5aaa5163dc56d4131ca82f8dca8fb0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/18/2020
ms.locfileid: "94848709"
---
# <a name="security-assessment-weak-cipher-usage"></a>Оценка безопасности: использование ненадежного шифра

## <a name="what-are-weak-ciphers"></a>Что такое слабые шифры?

Шифрование использует шифры для шифрования данных. Например, шифр RC4 (Rivest Cipher 4, также известен как ARC4 или ARCFOUR, то есть Alleged RC4) — это один из них. Хотя RC4 отличается простотой и скоростью, с момента первоначального выпуска RC4 обнаружено несколько уязвимостей, что делает его небезопасным. Алгоритм RC4 особенно уязвим, если начало потока выходного ключа не отброшено или если используются неслучайные или связанные ключи.

## <a name="how-do-i-use-this-security-assessment-to-improve-my-organizational-security-posture"></a>Как использовать эту оценку безопасности для повышения безопасности организации?

1. Ознакомьтесь с оценкой безопасности по использованию ненадежного шифра.
    ![Оценка использования ненадежного шифра](media/cas-isp-weak-cipher-2.png)
1. Узнайте, почему идентифицированные клиенты и серверы используют ненадежные шифры.
1. Устраните проблемы и отключите использование RC4 и других ненадежных шифров (таких как DES и 3DES).
1. Подробные сведения об отключении RC4 см. в статье [Советы корпорации Майкрософт по безопасности](https://support.microsoft.com/help/2868725/microsoft-security-advisory-update-for-disabling-rc4).

> [!NOTE]
> Эта оценка обновляется практически в реальном времени.

## <a name="remediation"></a>Серверы

Отключите клиенты и серверы, на которых требуется запретить использование комплектов шифров RC4, задав следующие разделы реестра. После отключения любой сервер или клиент, который обменивается данными с другим клиентом или сервером, который требует использования RC4, может предотвратить подключение. Клиенты, на которых развернут этот параметр, не смогут подключиться к сайтам, требующим RC4, а серверы, развертывающие этот параметр, не смогут обслуживать клиентов, которым требуется использовать RC4.

> [!NOTE]
> Обязательно протестируйте следующие параметры в управляемой среде, прежде чем включать их в рабочую среду.
>
> - [HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\SecurityProviders\SCHANNEL\Ciphers\RC4 128/128]   "Enabled"=dword:00000000
> - [HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\SecurityProviders\SCHANNEL\Ciphers\RC4 40/128]   "Enabled"=dword:00000000
> - [HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\SecurityProviders\SCHANNEL\Ciphers\RC4 56/128]   "Enabled"=dword:00000000

Дополнительные сведения о скачивании и обновлении изменений реестра см. в статье [Советы корпорации Майкрософт по безопасности](/security-updates/SecurityAdvisories/2013/2868725).

## <a name="next-steps"></a>Дальнейшие шаги

- [[!INCLUDE [Product short](includes/product-short.md)] Фильтрация действий в Cloud App Security](activities-filtering-mcas.md)
- [Посетите форум по [!INCLUDE [Product short](includes/product-short.md)].](https://aka.ms/MDIcommunity)
