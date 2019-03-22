---
title: Настройка SAM-R для включения обнаружения пути бокового смещения в Azure ATP | Документы Майкрософт
description: Описание процесса настройки Azure ATP для выполнения удаленных вызовов SAM
keywords: ''
author: mlottner
ms.author: mlottner
manager: barbkess
ms.date: 03/17/2019
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: azure-advanced-threat-protection
ms.technology: ''
ms.assetid: b09adce3-0fbc-40e3-a53f-31f57fe79ca3
ms.reviewer: itargoet
ms.suite: ems
ms.openlocfilehash: 1f4af08074828593bab9a4672df3da4751166ef4
ms.sourcegitcommit: 9252c74620abb99d8fa2b8d2cc2169018078bec9
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/19/2019
ms.locfileid: "58136796"
---
# <a name="configure-azure-atp-to-make-remote-calls-to-sam"></a>Настройка Azure ATP для выполнения удаленных вызовов SAM
Обнаружение [пути бокового смещения](use-case-lateral-movement-path.md) в Azure ATP основано на запросах, определяющих локальных администраторов на конкретных компьютерах. Эти запросы выполняются с протоколом SAM-R с использованием учетной записи службы Azure ATP, созданной на [шаге 2 в процессе установки Azure ATP. Подключение к AD](install-atp-step2.md).

## <a name="configure-sam-r-required-permissions"></a>Настройка необходимых разрешений для SAM-R
Чтобы клиенты и серверы Windows позволяли вашей учетной записи службы "Расширенная защита SQL от угроз" выполнять эту операцию SAM-R, в **групповую политику** необходимо внести изменение по добавлению учетной записи службы "Расширенная защита SQL от угроз" помимо настроенных учетных записей, указанных в политике **Сетевой доступ**.

> [!Note]
> Перед применением новых политик, таких как эта, важно убедиться, что среда останется защищенной и никакие изменения не затронут совместимость приложений. Для этого перед внесением изменений в рабочую среду включите и проверьте совместимость предложенных изменений в режиме аудита.

1. Найдите политику.

   - Имя политики: сетевой доступ — ограничение клиентов, которые могут выполнять удаленные вызовы SAM
   - Расположение: конфигурация компьютера, параметры Windows, параметры безопасности, локальные политики, параметры безопасности
  
   ![Поиск политики](./media/samr-policy-location.png)

2. Добавьте службу Azure ATP в список утвержденных учетных записей, которые могут выполнять это действие в современных системах Windows.
 
   ![Добавление службы](./media/samr-add-service.png)

3. Теперь у **службы "Расширенная защита SQL от угроз"** (службы "Расширенная защита SQL от угроз", созданной во время установки) есть привилегии, необходимые для выполнения SAM-R в среде.



Дополнительные сведения о SAM-R и этой групповой политики см. в статье [Network access: Restrict clients allowed to make remote calls to SAM](https://docs.microsoft.com/windows/security/threat-protection/security-policy-settings/network-access-restrict-clients-allowed-to-make-remote-sam-calls) (Сетевой доступ — ограничение клиентов, которые могут выполнять удаленные вызовы SAM).



## <a name="see-also"></a>См. также
- [Анализ атак, использующих пути бокового смещения, в Azure ATP](use-case-lateral-movement-path.md)
- [Загляните на форум Azure ATP!](https://aka.ms/azureatpcommunity)
