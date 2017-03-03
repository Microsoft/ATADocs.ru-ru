---
title: "Установка Advanced Threat Analytics. Шаг 6 | Документация Майкрософт"
description: "На заключительном этапе установки ATA нужно настроить пользователя Honeytoken."
keywords: 
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 01/23/2017
ms.topic: get-started-article
ms.prod: 
ms.service: advanced-threat-analytics
ms.technology: 
ms.assetid: 8980e724-06a6-40b0-8477-27d4cc29fd2b
ms.reviewer: bennyl
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: b28cb3a0da844b7c460c03726222bc775a9e47da
ms.openlocfilehash: b5954bd6f0cd9ef8c8b0b958a92840e905189d71


---

*Область применения: Advanced Threat Analytics версии 1.7*



# <a name="install-ata---step-6"></a>Установка ATA. Шаг 6

>[!div class="step-by-step"]
[" Шаг 5](install-ata-step5.md)

## <a name="step-6-configure--ip-address-exclusions-and-honeytoken-user"></a>Шаг 6. Настройка исключений IP-адреса и пользователя Honeytoken
ATA позволяет исключать определенные IP-адреса при обнаружении атак типа **DNS Reconnaissance** и **Pass-the-Ticket**. 

Например, **исключением исследования DNS** является сканер безопасности, использующий DNS в качестве механизма сканирования. Благодаря этому исключению ATA игнорирует такие сканеры. Примером исключения *Pass-the-Ticket* является устройство NAT.    

Кроме того, ATA позволяет настраивать пользователя Honeytoken, который играет роль ловушки для вредоносных субъектов: в связи с любой аутентификацией, которая относится к этой (обычно неактивной) учетной записи, срабатывает оповещение.

Чтобы настроить описанное выше, выполните такие действия:

1.  В консоли ATA щелкните значок параметров и выберите пункт **Конфигурация**.

    ![Параметры конфигурации ATA](media/ATA-config-icon.JPG)

2.  В разделе **исключений обнаружения** укажите IP-адреса для атак *DNS Reconnaissance* или *Pass-the-Ticket*, а затем щелкните знак *плюс*.

    ![Сохранить изменения](media/ATA-exclusions.png)

3.  В разделе **Detection settings** (Параметры обнаружения) введите идентификаторы безопасности учетной записи Honeytoken и щелкните знак "плюс". Например: `S-1-5-21-72081277-1610778489-2625714895-10511`.

    ![Параметры конфигурации ATA](media/ATA-honeytoken.png)

    > [!NOTE]
    > Чтобы найти идентификатор безопасности пользователя, найдите пользователя в консоли ATA и выберите вкладку**Сведения об учетной записи**. 

4.  Нажмите кнопку **Сохранить**.


На этом развертывание Microsoft Advanced Threat Analytics завершено.

Просмотрите временную шкалу атак, чтобы увидеть обнаруженные подозрительные действия, найти пользователей или компьютеры и изучить их профили.

В ATA сразу же начнется проверка на наличие подозрительных действий. Некоторые действия, например подозрительные действия, связанные с поведением, будут недоступны, пока ATA не создаст профили поведения (минимум три недели).


>[!div class="step-by-step"]
[" Шаг 5](install-ata-step5.md)


## <a name="see-also"></a>См. также

- [Ознакомьтесь с форумом ATA.](https://social.technet.microsoft.com/Forums/security/home?forum=mata)
- [Настройка сбора данных о событиях](configure-event-collection.md)
- [Предварительные требования ATA](/advanced-threat-analytics/plan-design/ata-prerequisites)




<!--HONumber=Feb17_HO1-->


