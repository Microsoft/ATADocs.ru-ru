---
title: "Установка ATA. Шаг 3 | Документация Майкрософт"
description: "На третьем этапе установки ATA вам нужно скачать пакет установки шлюза ATA."
keywords: 
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 08/24/2016
ms.topic: get-started-article
ms.prod: 
ms.service: advanced-threat-analytics
ms.technology: 
ms.assetid: 7fb024e6-297a-4ad9-b962-481bb75a0ba3
ms.reviewer: bennyl
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 85e285c5d88e5916e0bf0eb7dd327cb4cb45b4cb
ms.openlocfilehash: c8f3f5453757fbc7a95aa2377a84c3a133d38181


---

*Область применения: Advanced Threat Analytics версии 1.7*



# <a name="install-ata---step-3"></a>Установка ATA. Шаг 3

>[!div class="step-by-step"]
[« Шаг 2](install-ata-step2.md)
[Шаг 4 »](install-ata-step4.md)

## <a name="step-3-download-the-ata-gateway-setup-package"></a>Шаг 3. Скачивание пакета установки шлюза ATA
Настроив параметры подключения к домену, скачайте пакет установки шлюза ATA. Шлюз ATA можно устанавливать на выделенном сервере или на контроллере домена. При установке на контроллере домена он установится как упрощенный шлюз ATA. Дополнительные сведения об упрощенном шлюзе ATA см. в статье [Архитектура ATA](/advanced-threat-analytics/plan-design/ata-architecture). 

Если вы скачиваете шлюз ATA впервые, отобразится такой экран:

![Параметры конфигурации шлюза ATA](media/ATA_1.7-welcome-download-gateway.PNG)

А если это уже не первое скачивание, приветственное сообщение не появится.

> [!NOTE] 
> Чтобы открыть окно конфигурации позже, щелкните **значок настройки** (верхний правый угол), выберите **Configuration** (Конфигурация), а затем в разделе **System** (Система) щелкните **Gateways** (Шлюзы).  

1.  Щелкните **"Download Gateway Setup"** (Скачать средство установки шлюза).
2.  Сохраните пакет на локальном компьютере.
3.  Скопируйте пакет на выделенный сервер или контроллер домена, на который устанавливается шлюз ATA. Кроме того, можно открыть консоль ATA с выделенного сервера или контроллера домена и пропустить этот шаг.

ZIP-файл содержит:

-   установщик шлюза ATA;

-   файл конфигурации с данными для подключения к центру ATA.


>[!div class="step-by-step"]
[« Шаг 2](install-ata-step2.md)
[Шаг 4 »](install-ata-step4.md)

## <a name="see-also"></a>См. также

- [Ознакомьтесь с форумом ATA.](https://social.technet.microsoft.com/Forums/security/home?forum=mata)
- [Настройка сбора данных о событиях](configure-event-collection.md)
- [Предварительные требования ATA](/advanced-threat-analytics/plan-design/ata-prerequisites)



<!--HONumber=Jan17_HO1-->


