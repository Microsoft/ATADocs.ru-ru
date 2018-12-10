---
title: Настройка SAM-R для включения обнаружения пути бокового смещения в Azure ATP | Документы Майкрософт
description: Описание процесса настройки Azure ATP для выполнения удаленных вызовов SAM
keywords: ''
author: mlottner
ms.author: mlottner
manager: mbaldwin
ms.date: 12/02/2018
ms.topic: conceptual
ms.prod: ''
ms.service: azure-advanced-threat-protection
ms.technology: ''
ms.assetid: b09adce3-0fbc-40e3-a53f-31f57fe79ca3
ms.reviewer: itargoet
ms.suite: ems
ms.openlocfilehash: 020517e576f93b79e00158bbb7c6553d722a73b1
ms.sourcegitcommit: f4f2a1b2c674c4dba7a46ece0624f5ea10c4865e
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/02/2018
ms.locfileid: "52744393"
---
*Применяется к: Azure Advanced Threat Protection*

# <a name="configure-azure-atp-to-make-remote-calls-to-sam"></a>Настройка Azure ATP для выполнения удаленных вызовов SAM
Обнаружение [пути бокового смещения](use-case-lateral-movement-path.md) в Azure ATP основано на запросах, определяющих локальных администраторов на конкретных компьютерах. Эти запросы выполняются с протоколом SAM-R с использованием учетной записи службы Azure ATP, созданной на [шаге 2 в процессе установки Azure ATP. Подключение к AD](install-atp-step2.md).

## <a name="configure-sam-r-required-permissions"></a>Настройка необходимых разрешений для SAM-R
Чтобы клиенты и серверы Windows позволяли вашей учетной записи службы "Расширенная защита SQL от угроз" выполнять эту операцию SAM-R, в **групповую политику** необходимо внести изменение по добавлению учетной записи службы "Расширенная защита SQL от угроз" помимо настроенных учетных записей, указанных в политике **Сетевой доступ**.

1. Найдите политику.

 - Имя политики: сетевой доступ — ограничение клиентов, которые могут выполнять удаленные вызовы SAM
 - Расположение: конфигурация компьютера, параметры Windows, параметры безопасности, локальные политики, параметры безопасности
  
  ![Поиск политики](./media/samr-policy-location.png)

2. Добавьте службу Azure ATP в список утвержденных учетных записей, которые могут выполнять это действие в современных системах Windows.
 
  ![Добавление службы](./media/samr-add-service.png)

3. Теперь у **службы "Расширенная защита SQL от угроз"** (службы "Расширенная защита SQL от угроз", созданной во время установки) есть привилегии, необходимые для выполнения SAM-R в среде.

> [!NOTE]
> Прежде чем применять новую политику, путем включения и проверки предложенных изменений в режиме аудита убедитесь, что среда остается защищенной без влияния на совместимость приложений.

Дополнительные сведения о SAM-R и этой групповой политике см. в статье [Network access: Restrict clients allowed to make remote calls to SAM](https://docs.microsoft.com/windows/security/threat-protection/security-policy-settings/network-access-restrict-clients-allowed-to-make-remote-sam-calls) (Сетевой доступ: ограничение клиентов, которые могут выполнять удаленные вызовы SAM).



## <a name="see-also"></a>См. также
- [Анализ атак, использующих пути бокового смещения, в Azure ATP](use-case-lateral-movement-path.md)
- [Загляните на форум Azure ATP!](https://aka.ms/azureatpcommunity)