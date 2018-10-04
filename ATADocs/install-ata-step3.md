---
title: Установка Advanced Threat Analytics. Шаг 3 | Документация Майкрософт
description: На третьем этапе установки ATA вам нужно скачать пакет установки шлюза ATA.
keywords: ''
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 3/21/2018
ms.topic: conceptual
ms.prod: advanced-threat-analytics
ms.service: ''
ms.technology: ''
ms.assetid: 7fb024e6-297a-4ad9-b962-481bb75a0ba3
ms.reviewer: bennyl
ms.suite: ems
ms.openlocfilehash: d49770f435985027690ddfc05a9359e84841c0ff
ms.sourcegitcommit: b283bf66e63d76e6dba4564a229e804792794c6d
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/29/2018
ms.locfileid: "47454043"
---
*Применяется к: Advanced Threat Analytics версии 1.9*



# <a name="install-ata---step-3"></a>Установка ATA. Шаг 3

> [!div class="step-by-step"]
> [« Шаг 2](install-ata-step2.md)
> [Шаг 4 »](install-ata-step4.md)

## <a name="step-3-download-the-ata-gateway-setup-package"></a>Шаг 3. Скачивание пакета установки шлюза ATA
Настроив параметры подключения к домену, скачайте пакет установки шлюза ATA. Шлюз ATA можно устанавливать на выделенном сервере или на контроллере домена. При установке на контроллере домена он установится как упрощенный шлюз ATA. Дополнительные сведения об упрощенном шлюзе ATA см. в статье [Архитектура ATA](ata-architecture.md). 

В списке действий в верхней части страницы щелкните **Download Gateway Setup** (Скачать программу установки шлюза), чтобы перейти на страницу **Шлюзы**.

![Параметры конфигурации шлюза ATA](media/ATA_1.7-welcome-download-gateway.PNG)

> [!NOTE] 
> Чтобы открыть окно настройки шлюза позже, щелкните **значок параметров** (правый верхний угол), выберите **Конфигурация**, а затем в разделе **Система** щелкните **Шлюзы**.  

1.  Щелкните **Установка шлюза**.
  ![Скачивание программы установки шлюза ATA](media/download-gateway-setup.png)
2.  Сохраните пакет на локальном компьютере.
3.  Скопируйте пакет на выделенный сервер или контроллер домена, на который устанавливается шлюз ATA. Кроме того, можно открыть консоль ATA с выделенного сервера или контроллера домена и пропустить этот шаг.

ZIP-файл содержит следующие файлы:

-   установщик шлюза ATA;

-   файл конфигурации с данными для подключения к центру ATA.


> [!div class="step-by-step"]
> [« Шаг 2](install-ata-step2.md)
> [Шаг 4 »](install-ata-step4.md)


## <a name="related-videos"></a>Видео по теме
- [Обзор развертывания ATA](https://channel9.msdn.com/Shows/Microsoft-Security/Overview-of-ATA-Deployment-in-10-Minutes)
- [Выбор правильного типа шлюза ATA](https://channel9.msdn.com/Shows/Microsoft-Security/ATA-Deployment-Choose-the-Right-Gateway-Type)

## <a name="see-also"></a>См. также
- [Руководство по развертыванию среды для подтверждения концепции ATA](http://aka.ms/atapoc)
- [Средство изменения размера ATA](http://aka.ms/atasizingtool)
- [Ознакомьтесь с форумом ATA.](https://social.technet.microsoft.com/Forums/security/home?forum=mata)
- [Настройка сбора данных о событиях](configure-event-collection.md)
- [Предварительные требования ATA](ata-prerequisites.md)
