---
title: Настройка SAM-R для включения обнаружения пути бокового движения в Azure ATP
description: Описание процесса настройки Azure ATP для выполнения удаленных вызовов SAM
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 05/16/2019
ms.topic: how-to
ms.collection: M365-security-compliance
ms.service: azure-advanced-threat-protection
ms.assetid: b09adce3-0fbc-40e3-a53f-31f57fe79ca3
ms.reviewer: itargoet
ms.suite: ems
ms.openlocfilehash: d752b23fb339bfdcbd1b202716c97a027f5b86dc
ms.sourcegitcommit: c7c0a4c9f7507f3e8e0f219798ed7d347c03e792
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/22/2020
ms.locfileid: "90912934"
---
# <a name="configure-azure-atp-to-make-remote-calls-to-sam"></a>Настройка Azure ATP для выполнения удаленных вызовов SAM

[!INCLUDE [Rebranding notice](includes/rebranding.md)]

Обнаружение [пути бокового движения](use-case-lateral-movement-path.md) в Azure ATP основано на запросах, определяющих локальных администраторов на конкретных компьютерах. Эти запросы выполняются с протоколом SAM-R с использованием учетной записи службы Azure ATP, созданной на [шаге 2 в процессе установки Azure ATP. Подключение к AD](install-step2.md).

## <a name="configure-sam-r-required-permissions"></a>Настройка необходимых разрешений для SAM-R

Чтобы клиенты и серверы Windows позволяли вашей учетной записи службы "Расширенная защита SQL от угроз" выполнять эту операцию SAM-R, в **групповую политику** необходимо внести изменение по добавлению учетной записи службы "Расширенная защита SQL от угроз" помимо настроенных учетных записей, указанных в политике **Сетевой доступ**. Обязательно примените групповые политики ко всем компьютерам, кроме контроллеров домена.

> [!Note]
> Перед применением новых политик, таких как эта, важно убедиться, что среда останется защищенной и никакие изменения не затронут совместимость приложений. Для этого активируйте предлагаемые изменения и проверьте их на совместимость в режиме аудита, прежде чем вносить их в рабочую среду.

1. Найдите политику.

   - Имя политики: сетевой доступ — ограничение клиентов, которые могут выполнять удаленные вызовы SAM
   - Расположение: конфигурация компьютера, параметры Windows, параметры безопасности, локальные политики, параметры безопасности

    ![Поиск политики](media/samr-policy-location.png)

1. Добавьте службу Azure ATP в список утвержденных учетных записей, которые могут выполнять это действие в современных системах Windows.

    ![Добавление службы](media/samr-add-service.png)

3. Теперь у **службы "Расширенная защита SQL от угроз"** (службы "Расширенная защита SQL от угроз", созданной во время установки) есть привилегии, необходимые для выполнения SAM-R в среде.

Дополнительные сведения о SAM-R и этой групповой политики см. в статье [Network access: Restrict clients allowed to make remote calls to SAM](/windows/security/threat-protection/security-policy-settings/network-access-restrict-clients-allowed-to-make-remote-sam-calls) (Сетевой доступ — ограничение клиентов, которые могут выполнять удаленные вызовы SAM).

## <a name="see-also"></a>См. также

- [Анализ атак, использующих пути бокового движения, в Azure ATP](use-case-lateral-movement-path.md)
- [Загляните на форум Azure ATP!](https://aka.ms/azureatpcommunity)