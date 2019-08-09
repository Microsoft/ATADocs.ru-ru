---
title: Настройка SAM-R для включения обнаружения пути бокового смещения в Advanced Threat Analytics | Документация Майкрософт
description: Сведения о настройке SAM-R для включения обнаружения пути бокового смещения в Advanced Threat Analytics (ATA)
keywords: ''
author: mlottner
ms.author: mlottner
manager: rkarlin
ms.date: 08/08/2019
ms.topic: conceptual
ms.prod: advanced-threat-analytics
ms.technology: ''
ms.assetid: 7597ed25-87f5-472c-a496-d5f205c9c391
ms.reviewer: itargoet
ms.suite: ems
ms.openlocfilehash: bd47ebbe059014015b180ad568e4c519ba1b95b7
ms.sourcegitcommit: db35bae8354fa35644e9334bfc37b9ffbafdaacc
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/09/2019
ms.locfileid: "68862583"
---
# <a name="install-ata---step-9"></a>Установка ATA. Шаг 9

*Область применения: Advanced Threat Analytics версии 1.9*

> [!div class="step-by-step"]
> [«Шаг 8»](install-ata-step7.md)

> [!NOTE]
> Перед применением новой политики всегда обеспечьте безопасность среды, не влияя на совместимость приложений, при первом включении и проверке предлагаемых изменений в режиме аудита. 

## <a name="step-9-configure-sam-r-required-permissions"></a>Шаг 9. Настройка необходимых разрешений для SAM-R

Обнаружение [пути бокового смещения](use-case-lateral-movement-path.md) основано на запросах, определяющих локальных администраторов на конкретных компьютерах. Эти запросы выполняются с использованием протокола SAM-R с помощью учетной записи службы ATA, созданной на [шаге 2. Подключение к AD](install-ata-step2.md).
 
Чтобы клиенты и серверы Windows позволяли учетной записи службы ATA выполнять эту операцию SAM-R, в **групповую политику** необходимо внести изменение, добавляющее учетную запись службы ATA помимо настроенных учетных записей, указанных в политике **Сетевой доступ**.

1. Найдите политику.

   - Имя политики: сетевой доступ — ограничение клиентов, которые могут выполнять удаленные вызовы SAM
   - Расположение: конфигурация компьютера, параметры Windows, параметры безопасности, локальные политики, параметры безопасности
  
   ![Поиск политики](./media/samr-policy-location.png)

2. Добавьте службу ATA в список утвержденных учетных записей, которые могут выполнять это действие в современных системах Windows.
 
   ![Добавление службы](./media/samr-add-service.png)

3. Теперь у **службы ATA** (службы ATA, созданной во время установки) есть соответствующие права для выполнения SAM-R в среде.

 Дополнительные сведения о SAM-R и групповой политики см. в статье [Network access: Restrict clients allowed to make remote calls to SAM](https://docs.microsoft.com/windows/security/threat-protection/security-policy-settings/network-access-restrict-clients-allowed-to-make-remote-sam-calls) (Сетевой доступ — ограничение клиентов, которые могут выполнять удаленные вызовы SAM).


> [!div class="step-by-step"]
> [«Шаг 8»](install-ata-step7.md)

## <a name="see-also"></a>См. также
- [Руководство по развертыванию среды для подтверждения концепции ATA](http://aka.ms/atapoc)
- [Средство изменения размера ATA](http://aka.ms/atasizingtool)
- [Ознакомьтесь с форумом ATA.](https://social.technet.microsoft.com/Forums/security/home?forum=mata)
- [Настройка сбора данных о событиях](configure-event-collection.md)
- [Предварительные требования ATA](ata-prerequisites.md)
