---
title: "Установка Azure Advanced Threat Protection. Шаг 7 | Документы Майкрософт"
description: "На заключительном этапе установки Azure ATP нужно настроить пользователя Honeytoken."
keywords: 
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 2/21/2017
ms.topic: get-started-article
ms.prod: 
ms.service: azure-advanced-threat-protection
ms.technology: 
ms.assetid: 1ad5e923-9bbd-4f56-839a-b11a9f387d4b
ms.reviewer: itargoet
ms.suite: ems
ms.openlocfilehash: bef13d0f4799a4483eda6604a8ed96befaa13508
ms.sourcegitcommit: 03e959b7ce4b6df421297e1872e028793c967302
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/21/2018
---
*Применяется к: Azure Advanced Threat Protection*



# <a name="install-azure-atp---step-7"></a>Установка Azure ATP. Шаг 7

>[!div class="step-by-step"]
[« Шаг 6](install-atp-step6-vpn.md)
[Шаг 8 »](install-atp-step8-samr.md)

## <a name="step-7-configure-detection-exclusions-and-honeytoken-user"></a>Шаг 7. Настройка пользователя Honeytoken и исключений из обнаружения

В Azure ATP можно исключать из обнаружения определенные IP-адреса или пользователей. 

Например, **исключением исследования DNS** является сканер безопасности, использующий DNS в качестве механизма сканирования. Благодаря этому исключению Azure ATP игнорирует такие сканеры.  

Кроме того, Azure ATP позволяет настраивать пользователя Honeytoken, который играет роль ловушки для вредоносных субъектов: в связи с любой аутентификацией, которая относится к этой (обычно неактивной) учетной записи, срабатывает оповещение.

Чтобы настроить ATA, сделайте следующее:

1.  На портале рабочей области Azure ATP щелкните значок параметров и выберите пункт **Конфигурация**.

    ![Параметры конфигурации Azure ATP](media/atp-config-menu.png)

2.  В разделе **Обнаружение** выберите пункт **Теги сущности**.

3. В разделе **Учетные записи Honeytoken** введите имя учетной записи Honeytoken и нажмите значок **+**. Поле "Учетные записи Honeytoken" поддерживает поиск, и в нем автоматически отображаются сущности, имеющиеся в вашей сети. Нажмите кнопку **Сохранить**.

   ![Honeytoken](media/honeytoken-sensitive.png)

4. Щелкните **Исключения**. Для каждого типа угрозы введите учетную запись пользователя или IP-адрес, которые следует исключить при обнаружении этих угроз, а затем щелкните знак *плюс*. Поле **Добавить сущность** (пользователя или компьютер) поддерживает поиск и автоматически заполняется сущностями из вашей сети. Дополнительные сведения см. в статье [Исключение сущностей из результатов обнаружения](excluding-entities-from-detections.md) и в [руководстве по подозрительным действиям](suspicious-activity-guide.md).

   ![Исключения](media/exclusions.png)

5.  Нажмите кнопку **Сохранить**.


На этом развертывание Azure Advanced Threat Protection завершено.

Просмотрите временную шкалу атак, чтобы увидеть обнаруженные подозрительные действия, найти пользователей или компьютеры и изучить их профили.

В Azure ATP начнется проверка на наличие подозрительных действий. Для некоторых обнаружений, например чрезмерных изменений группы, требуется период распознавания, поэтому они недоступны сразу же после развертывания Azure ATP.



>[!div class="step-by-step"]
[« Шаг 6](install-atp-step6-vpn.md)
[Шаг 8 »](install-atp-step8-samr.md)

## <a name="see-also"></a>См. также
- [Средство изменения размера Azure ATP](http://aka.ms/aatpsizingtool)
- [Настройка сбора данных о событиях](configure-event-collection.md)
- [Предварительные требования к Azure ATP](atp-prerequisites.md)
- [Обязательно ознакомьтесь с форумом ATP](https://aka.ms/azureatpcommunity)
