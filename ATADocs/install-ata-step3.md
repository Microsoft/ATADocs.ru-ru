---
title: "Установка Advanced Threat Analytics. Шаг 3 | Документация Майкрософт"
description: "На третьем этапе установки ATA вам нужно скачать пакет установки шлюза ATA."
keywords: 
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 08/20/2017
ms.topic: get-started-article
ms.prod: 
ms.service: advanced-threat-analytics
ms.technology: 
ms.assetid: 7fb024e6-297a-4ad9-b962-481bb75a0ba3
ms.reviewer: bennyl
ms.suite: ems
ms.openlocfilehash: 22541007bd6ebf0e37818e205bac57191ca6f28d
ms.sourcegitcommit: 129bee06ff89b72d21b64f9aa0d1a29f66bf9153
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/20/2017
---
*Применяется к Advanced Threat Analytics версии 1.8*



# <a name="install-ata---step-3"></a>Установка ATA. Шаг 3

>[!div class="step-by-step"]
[« Шаг 2](install-ata-step2.md)
[Шаг 4 »](install-ata-step4.md)

## <a name="step-3-download-the-ata-gateway-setup-package"></a>Шаг 3. Скачивание пакета установки шлюза ATA
Настроив параметры подключения к домену, скачайте пакет установки шлюза ATA. Шлюз ATA можно устанавливать на выделенном сервере или на контроллере домена. При установке на контроллере домена он установится как упрощенный шлюз ATA. Дополнительные сведения об упрощенном шлюзе ATA см. в статье [Архитектура ATA](ata-architecture.md). 

В списке действий в верхней части страницы щелкните "Скачать программу установки шлюза", чтобы перейти на страницу "Шлюзы".

![Параметры конфигурации шлюза ATA](media/ATA_1.7-welcome-download-gateway.PNG)

> [!NOTE] 
> Чтобы открыть окно настройки шлюза позже, щелкните **значок параметров** (правый верхний угол), выберите **Конфигурация**, а затем в разделе **Система** щелкните **Шлюзы**.  

1.  Щелкните **Установка шлюза**.
  ![Скачивание программы установки шлюза ATA](media/download-gateway-setup.png)
2.  Сохраните пакет на локальном компьютере.
3.  Скопируйте пакет на выделенный сервер или контроллер домена, на который устанавливается шлюз ATA. Кроме того, можно открыть консоль ATA с выделенного сервера или контроллера домена и пропустить этот шаг.

ZIP-файл содержит:

-   установщик шлюза ATA;

-   файл конфигурации с данными для подключения к центру ATA.


>[!div class="step-by-step"]
[« Шаг 2](install-ata-step2.md)
[Шаг 4 »](install-ata-step4.md)


## <a name="related-videos"></a>Видео по теме
- [Выбор правильного типа шлюза ATA](https://channel9.msdn.com/Shows/Microsoft-Security/ATA-Deployment-Choose-the-Right-Gateway-Type)

## <a name="see-also"></a>См. также
- [Руководство по развертыванию среды для подтверждения концепции ATA](http://aka.ms/atapoc)
- [Средство изменения размера ATA](http://aka.ms/atasizingtool)
- [Ознакомьтесь с форумом ATA.](https://social.technet.microsoft.com/Forums/security/home?forum=mata)
- [Настройка сбора данных о событиях](configure-event-collection.md)
- [Предварительные требования ATA](ata-prerequisites.md)
