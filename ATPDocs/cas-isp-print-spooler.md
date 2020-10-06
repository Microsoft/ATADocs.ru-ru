---
title: Оценка состояния безопасности удостоверений Расширенной защиты от угроз Azure с очередью печати принтера
description: В этой статье представлен обзор отчетов об оценке состояния безопасности удостоверений Azure ATP для очереди печати принтера.
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 08/25/2020
ms.topic: how-to
ms.collection: M365-security-compliance
ms.service: azure-advanced-threat-protection
ms.assetid: 1a7d9525-8923-4dae-af51-02a68aa61644
ms.reviewer: itargoet
ms.suite: ems
ms.openlocfilehash: 3d49284e21f235e70698bb6a79d015af4fb4a321
ms.sourcegitcommit: c7c0a4c9f7507f3e8e0f219798ed7d347c03e792
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/22/2020
ms.locfileid: "90913165"
---
# <a name="security-assessment-domain-controllers-with-print-spooler-service-available"></a>Оценка безопасности: служба очереди печати принтера на контроллерах домена

[!INCLUDE [Rebranding notice](includes/rebranding.md)]

![Отключение службы очереди печати принтера](media/atp-cas-isp-print-spooler-1.png)

## <a name="what-is-the-print-spooler-service"></a>Что такое служба **очереди печати принтера**?

Очередь печати принтера — это программная служба, которая управляет процессами печати. Она принимает задания печати с компьютеров и гарантирует доступность ресурсов принтера. Она также планирует порядок отправки заданий печати в очередь на печать. На ранних этапах существования персональных компьютеров пользователям приходилось ждать, пока будут напечатаны файлы, перед выполнением других действий. Благодаря современным очередям печати этот процесс теперь оказывает минимальное влияние на общую производительность пользователей.

## <a name="what-risks-does-the-print-spooler-service-on-domain-controllers-introduce"></a>Какие риски несет служба **очереди печати принтера** на контроллерах домена?

Хотя это и кажется безобидным, любой прошедший проверку подлинности пользователь может удаленно подключиться к службе очереди печати и запросить список новых заданий печати. Кроме того, пользователи могут сообщить контроллеру домена о необходимости отправки уведомления в систему с [неограниченным делегированием](cas-isp-unconstrained-kerberos.md). Эти действия проверяют подключение и раскрывают учетную запись компьютера контроллера домена (**служба очереди печати** принадлежит к SYSTEM).

Из-за возможности раскрытия на контроллерах домена и в системах администрирования Active Directory нужно отключить службу **очереди печати**. Для этого рекомендуется использовать объект групповой политики (GPO).

Хотя эта оценка безопасности сосредоточена на контроллерах домена, любой сервер потенциально подвержен риску атак такого типа.

   > [!NOTE]
   > Обязательно изучите параметры, конфигурации и зависимости службы **очереди печати**, прежде чем отключить ее и остановить активные рабочие процессы печати.

## <a name="how-do-i-use-this-security-assessment"></a>Как использовать эту оценку безопасности?

1. Используйте таблицу отчета, чтобы определить, на каких контроллерах домена включена **служба очереди печати**.

    ![Оценка безопасности: отключение службы очереди печати принтера](media/atp-cas-isp-print-spooler-2.png)
1. Выполните необходимые действия на контроллерах домена, где есть этот риск, и сами удалите службу очереди печати вручную, через GPO или другие типы удаленных команд.

> [!NOTE]
> Эта оценка обновляется практически в реальном времени.

## <a name="remediation"></a>Серверы

Чтобы устранить эту проблему, отключите службу очереди печати принтера на всех серверах, которым она не требуется.

## <a name="next-steps"></a>Дальнейшие шаги

- [Фильтрация действий Azure ATP в Cloud App Security](activities-filtering-mcas.md)
- [Загляните на форум Azure ATP!](https://aka.ms/azureatpcommunity)