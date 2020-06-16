---
title: Установка Advanced Threat Analytics. шаг 8
description: На заключительном этапе установки ATA нужно настроить пользователя Honeytoken.
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 6/14/2018
ms.topic: conceptual
ms.prod: advanced-threat-analytics
ms.technology: ''
ms.assetid: 8980e724-06a6-40b0-8477-27d4cc29fd2b
ms.reviewer: bennyl
ms.suite: ems
ms.openlocfilehash: 9482053a183dfd41f20028d00c15c171cea725c7
ms.sourcegitcommit: fbb0768c392f9bccdd7e4adf0e9a0303c8d1922c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2020
ms.locfileid: "84775154"
---
# <a name="install-ata---step-8"></a>Установка ATA. Шаг 8

*Применяется к: Advanced Threat Analytics версии 1.9*

> [!div class="step-by-step"]
> [«Шаг 7](vpn-integration-install-step.md) 
>  [Шаг 9](install-ata-step9-samr.md)

## <a name="step-8-configure-ip-address-exclusions-and-honeytoken-user"></a>Шаг 8. Настройка исключений IP-адресов и пользователя Honeytoken

В ATA можно исключать из обнаружения определенные IP-адреса или пользователей. 

Например, **исключением исследования DNS** является сканер безопасности, использующий DNS в качестве механизма сканирования. Благодаря этому исключению ATA игнорирует такие сканеры. Примером исключения *Pass-the-Ticket* является устройство NAT.    

Кроме того, ATA позволяет настраивать пользователя Honeytoken, который играет роль ловушки для вредоносных субъектов: в связи с любой аутентификацией, которая относится к этой (обычно неактивной) учетной записи, срабатывает оповещение.

Чтобы настроить ATA, сделайте следующее:

1.  В консоли ATA щелкните значок параметров и выберите **Конфигурация**.

    ![Параметры конфигурации ATA](media/ATA-config-icon.png)

2.  В разделе **Обнаружение**щелкните **теги сущностей**.

2. В разделе **Учетные записи Honeytoken** введите имя учетной записи Honeytoken. Поле "Учетные записи Honeytoken" поддерживает поиск, и в нем автоматически отображаются сущности, имеющиеся в вашей сети.

   ![Honeytoken](media/honeytoken.png)

3. Щелкните **Исключения**. Для каждого типа угрозы введите учетную запись пользователя или IP-адрес, которые следует исключить при обнаружении этих угроз, а затем щелкните знак *плюс*. Поле **Добавить сущность** (пользователя или компьютер) поддерживает поиск и автоматически заполняется сущностями из вашей сети. См. дополнительные сведения об [исключении сущностей из результатов обнаружения](excluding-entities-from-detections.md).

   ![Исключения](media/exclusions.png)

4.  Нажмите кнопку **Сохранить**.


На этом развертывание Microsoft Advanced Threat Analytics завершено.

Просмотрите временную шкалу атак, чтобы увидеть обнаруженные подозрительные действия, найти пользователей или компьютеры и изучить их профили.

В ATA начнется проверка на наличие подозрительных действий. Некоторые действия, например подозрительные действия, связанные с поведением, будут недоступны, пока ATA не создаст профили поведения (минимум три недели).

Чтобы проверить, запущена ли служба ATA и выявляет ли она бреши в вашей сети, см. [Сборник тренировочных заданий по моделированию атаки](https://docs.microsoft.com/enterprise-mobility-security/solutions/ata-attack-simulation-playbook).


> [!div class="step-by-step"]
> [«Шаг 7](vpn-integration-install-step.md) 
>  [Шаг 9](install-ata-step9-samr.md)


## <a name="related-videos"></a>Видео по теме
- [Обзор развертывания ATA](https://channel9.msdn.com/Shows/Microsoft-Security/Overview-of-ATA-Deployment-in-10-Minutes)
- [Выбор правильного типа шлюза ATA](https://channel9.msdn.com/Shows/Microsoft-Security/ATA-Deployment-Choose-the-Right-Gateway-Type)


## <a name="see-also"></a>См. также:
- [Руководство по развертыванию среды для подтверждения концепции ATA](https://aka.ms/atapoc)
- [Средство изменения размера ATA](https://aka.ms/atasizingtool)
- [Обязательно ознакомьтесь с форумом ATA.](https://social.technet.microsoft.com/Forums/security/home?forum=mata)
- [Настройка сбора данных о событиях](configure-event-collection.md)
- [Предварительные требования ATA](ata-prerequisites.md)

