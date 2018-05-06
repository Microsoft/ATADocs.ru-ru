---
title: Настройка SAM-R для включения обнаружения пути бокового смещения в Azure ATP | Документы Майкрософт
description: Сведения о настройке SAM-R для включения обнаружения пути бокового смещения в Azure ATP
keywords: ''
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 4/29/2018
ms.topic: get-started-article
ms.prod: ''
ms.service: azure-advanced-threat-protection
ms.technology: ''
ms.assetid: b09adce3-0fbc-40e3-a53f-31f57fe79ca3
ms.reviewer: itargoet
ms.suite: ems
ms.openlocfilehash: 24b42c5425933d8931a85e0ba454a69e0ca94a21
ms.sourcegitcommit: 5c0f914b44bfb8e03485f12658bfa9a7cd3d8bbc
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/30/2018
---
*Применяется к: Azure Advanced Threat Protection*

# <a name="install-azure-atp---step-8"></a>Установка Azure ATP. Шаг 8

>[!div class="step-by-step"]
[«Шаг 7»](install-atp-step7.md)

## <a name="step-8-configure-sam-r-required-permissions"></a>Шаг 8. Настройка необходимых разрешений для SAM-R

Обнаружение [пути бокового смещения](use-case-lateral-movement-path.md) основано на запросах, определяющих локальных администраторов на конкретных компьютерах. Эти запросы выполняются с использованием протокола SAM-R с помощью учетной записи службы ATP Azure, созданной на [шаге 2. Подключение к AD](install-atp-step2.md).
 
Чтобы клиенты и серверы Windows позволяли учетной записи Azure ATP выполнять эту операцию SAM-R, в **групповую политику** необходимо внести изменение по добавлению учетной записи службы Azure ATP помимо настроенных учетных записей, указанных в политике **Сетевой доступ**.

1. Найдите политику.

 - Имя политики: сетевой доступ — ограничение клиентов, которые могут выполнять удаленные вызовы SAM
 - Расположение: конфигурация компьютера, параметры Windows, параметры безопасности, локальные политики, параметры безопасности
  
  ![Поиск политики](./media/samr-policy-location.png)

2. Добавьте службу Azure ATP в список утвержденных учетных записей, которые могут выполнять это действие в современных системах Windows.
 
  ![Добавление службы](./media/samr-add-service.png)

3. Теперь у **службы AATP** (службы Azure ATP, созданной во время установки) есть соответствующие права для выполнения SAMR в среде.

Дополнительные сведения о SAM-R и групповой политике см. в статье [Network access: Restrict clients allowed to make remote calls to SAM](https://docs.microsoft.com/windows/security/threat-protection/security-policy-settings/network-access-restrict-clients-allowed-to-make-remote-sam-calls) (Сетевой доступ: ограничение клиентов, которые могут выполнять удаленные вызовы SAM).


>[!div class="step-by-step"]
[«Шаг 7»](install-atp-step7.md)



## <a name="see-also"></a>См. также
- [Анализ атак, использующих пути бокового смещения, в Azure ATP](use-case-lateral-movement-path.md)
- [Обязательно ознакомьтесь с форумом ATP](https://aka.ms/azureatpcommunity)