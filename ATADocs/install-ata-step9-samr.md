---
title: Настройка SAM-R для включения обнаружения пути бокового смещения в Advanced Threat Analytics | Документация Майкрософт
description: Сведения о настройке SAM-R для включения обнаружения пути бокового смещения в Advanced Threat Analytics (ATA)
keywords: ''
author: shsagir
ms.author: shsagir
manager: rkarlin
ms.date: 09/08/2019
ms.topic: conceptual
ms.prod: advanced-threat-analytics
ms.technology: ''
ms.assetid: 7597ed25-87f5-472c-a496-d5f205c9c391
ms.reviewer: itargoet
ms.suite: ems
ms.openlocfilehash: 1b8e8924fe0cd00985252c04edfb92ec51759b48
ms.sourcegitcommit: 9673eb49729a06d3a25d52c0f43c76ac61b9cf89
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/12/2020
ms.locfileid: "75907966"
---
# <a name="install-ata---step-9"></a>Установка ATA. Шаг 9

*Применяется к: Advanced Threat Analytics версии 1.9*

> [!div class="step-by-step"]
> [«Шаг 8»](install-ata-step7.md)

> [!NOTE]
> Перед применением новой политики всегда обеспечьте безопасность среды, не влияя на совместимость приложений, при первом включении и проверке предлагаемых изменений в режиме аудита. 

## <a name="step-9-configure-sam-r-required-permissions"></a>Шаг 9. Настройка необходимых разрешений для SAM-R

Обнаружение [пути бокового смещения](use-case-lateral-movement-path.md) основано на запросах, определяющих локальных администраторов на конкретных компьютерах. Эти запросы выполняются с помощью протокола SAM-R через учетную запись службы ATA, созданную на [шаге 2. Подключитесь к AD](install-ata-step2.md).
 
Чтобы клиенты и серверы Windows позволяли учетной записи службы ATA выполнять эту операцию SAM-R, в **групповую политику** необходимо внести изменение, добавляющее учетную запись службы ATA помимо настроенных учетных записей, указанных в политике **Сетевой доступ**. Эта групповая политика должна применяться ко всем устройствам в Организации. 

1. Найдите политику.

   - Имя политики: сетевой доступ — ограничение клиентов, которые могут выполнять удаленные вызовы SAM
   - Расположение: конфигурация компьютера, параметры Windows, параметры безопасности, локальные политики, параметры безопасности
  
   ![Поиск политики](./media/samr-policy-location.png)

2. Добавьте службу ATA в список утвержденных учетных записей, которые могут выполнять это действие в современных системах Windows.
 
   ![Добавление службы](./media/samr-add-service.png)

3. Теперь у **службы ATA** (службы ATA, созданной во время установки) есть соответствующие права для выполнения SAM-R в среде.

 Дополнительные сведения о SAM-R и групповой политике см. в статье [Network access: Restrict clients allowed to make remote calls to SAM](https://docs.microsoft.com/windows/security/threat-protection/security-policy-settings/network-access-restrict-clients-allowed-to-make-remote-sam-calls) (Сетевой доступ: ограничение клиентов, которые могут выполнять удаленные вызовы SAM).


> [!div class="step-by-step"]
> [«Шаг 8»](install-ata-step7.md)

## <a name="see-also"></a>См. также
- [Руководство по развертыванию среды для подтверждения концепции ATA](https://aka.ms/atapoc)
- [Средство изменения размера ATA](https://aka.ms/atasizingtool)
- [Ознакомьтесь с форумом ATA.](https://social.technet.microsoft.com/Forums/security/home?forum=mata)
- [Настройка сбора данных о событиях](configure-event-collection.md)
- [Предварительные требования ATA](ata-prerequisites.md)
