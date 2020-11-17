---
title: Настройка SAM-R для включения обнаружения пути перемещения бокового смещения в Advanced Threat Analytics
description: Сведения о настройке SAM-R для включения обнаружения пути бокового смещения в Advanced Threat Analytics (ATA)
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 09/08/2019
ms.topic: conceptual
ms.prod: advanced-threat-analytics
ms.technology: ''
ms.assetid: 7597ed25-87f5-472c-a496-d5f205c9c391
ms.reviewer: itargoet
ms.suite: ems
ms.openlocfilehash: 7ce78fc1f03dd310aa454063692e8ee1aae5c22c
ms.sourcegitcommit: e844155ea57f73dfe2b47f4c5c1c7f5292ccbf1e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2020
ms.locfileid: "94690556"
---
# <a name="install-ata---step-9"></a>Установка ATA. Шаг 9

[!INCLUDE [Banner for top of topics](includes/banner.md)]

> [!div class="step-by-step"]
> [«Шаг 8»](install-ata-step7.md)

> [!NOTE]
> Перед применением новой политики всегда обеспечьте безопасность среды, не влияя на совместимость приложений, при первом включении и проверке предлагаемых изменений в режиме аудита. 

## <a name="step-9-configure-sam-r-required-permissions"></a>Шаг 9. Настройка необходимых разрешений для SAM-R

Обнаружение [пути бокового смещения](use-case-lateral-movement-path.md) основано на запросах, определяющих локальных администраторов на конкретных компьютерах. Эти запросы выполняются с помощью протокола SAM-R через учетную запись службы ATA, созданную на [шаге 2. Подключитесь к AD](install-ata-step2.md).
 
Чтобы клиенты и серверы Windows позволяли учетной записи службы ATA выполнять эту операцию SAM-R, в **групповую политику** необходимо внести изменение, добавляющее учетную запись службы ATA помимо настроенных учетных записей, указанных в политике **Сетевой доступ**. Эта групповая политика должна применяться ко всем устройствам в Организации. 

1. Найдите политику.

   - Имя политики: сетевой доступ — ограничение клиентов, которые могут выполнять удаленные вызовы SAM
   - Расположение: конфигурация компьютера, параметры Windows, параметры безопасности, локальные политики, параметры безопасности
  
    ![Поиск политики](media/samr-policy-location.png)

1. Добавьте службу ATA в список утвержденных учетных записей, которые могут выполнять это действие в современных системах Windows.
 
    ![Добавление службы](media/samr-add-service.png)

1. **Служба ATA** (служба ATA, созданная во время установки) теперь имеет необходимые привилегии для выполнения SAM-R в среде.

 Дополнительные сведения о SAM-R и групповой политике см. в статье [Network access: Restrict clients allowed to make remote calls to SAM](/windows/security/threat-protection/security-policy-settings/network-access-restrict-clients-allowed-to-make-remote-sam-calls) (Сетевой доступ: ограничение клиентов, которые могут выполнять удаленные вызовы SAM).


> [!div class="step-by-step"]
> [«Шаг 8»](install-ata-step7.md)

## <a name="see-also"></a>См. также:
- [Руководство по развертыванию среды для подтверждения концепции ATA](https://aka.ms/atapoc)
- [Средство изменения размера ATA](https://aka.ms/atasizingtool)
- [Обязательно ознакомьтесь с форумом ATA.](https://social.technet.microsoft.com/Forums/security/home?forum=mata)
- [Настройка сбора данных о событиях](configure-event-collection.md)
- [Предварительные требования ATA](ata-prerequisites.md)