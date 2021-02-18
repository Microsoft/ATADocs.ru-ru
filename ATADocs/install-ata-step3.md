---
title: Установка Advanced Threat Analytics. шаг 3
description: На третьем этапе установки ATA вам нужно скачать пакет установки шлюза ATA.
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 3/21/2018
ms.topic: conceptual
ms.prod: advanced-threat-analytics
ms.technology: ''
ms.assetid: 7fb024e6-297a-4ad9-b962-481bb75a0ba3
ms.reviewer: bennyl
ms.suite: ems
ms.openlocfilehash: 3f022f070bc924388bee2fb3a0dda250b59ce053
ms.sourcegitcommit: 5bf0c6a204b71126306a0c64108eaf9cb7fc042f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/18/2021
ms.locfileid: "101097520"
---
# <a name="install-ata---step-3"></a>Установка ATA. Шаг 3

[!INCLUDE [Banner for top of topics](includes/banner.md)]

> [!div class="step-by-step"]
> [« Шаг 2](install-ata-step2.md)
> [Шаг 4 »](install-ata-step4.md)

## <a name="step-3-download-the-ata-gateway-setup-package"></a>Шаг 3. Скачивание пакета установки шлюза ATA

Настроив параметры подключения к домену, скачайте пакет установки шлюза ATA. Шлюз ATA можно устанавливать на выделенном сервере или на контроллере домена. При установке на контроллере домена он установится как упрощенный шлюз ATA. Дополнительные сведения об упрощенном шлюзе ATA см. в статье [архитектура ATA](ata-architecture.md). 

Щелкните **скачать настройки шлюза** в списке шагов в верхней части страницы, чтобы открыть страницу **шлюзы** .

![Параметры конфигурации шлюза ATA](media/ATA_1.7-welcome-download-gateway.PNG)

> [!NOTE] 
> Чтобы открыть окно настройки шлюза позже, щелкните **значок параметров** (правый верхний угол), выберите **Конфигурация**, а затем в разделе **Система** щелкните **Шлюзы**.  

1. Щелкните **Установка шлюза**.
  ![Скачивание программы установки шлюза ATA](media/download-gateway-setup.png)
1. Сохраните пакет на локальном компьютере.
1. Скопируйте пакет на выделенный сервер или контроллер домена, на который устанавливается шлюз ATA. Кроме того, можно открыть консоль ATA с выделенного сервера или контроллера домена и пропустить этот шаг.

ZIP-файл содержит следующие файлы:

- установщик шлюза ATA;

- файл конфигурации с данными для подключения к центру ATA.


> [!div class="step-by-step"]
> [« Шаг 2](install-ata-step2.md)
> [Шаг 4 »](install-ata-step4.md)


## <a name="related-videos"></a>Видео по теме
- [Обзор развертывания ATA](https://channel9.msdn.com/Shows/Microsoft-Security/Overview-of-ATA-Deployment-in-10-Minutes)
- [Выбор правильного типа шлюза ATA](https://channel9.msdn.com/Shows/Microsoft-Security/ATA-Deployment-Choose-the-Right-Gateway-Type)

## <a name="see-also"></a>См. также
- [Руководство по развертыванию среды для подтверждения концепции ATA](/samples/browse/?redirectedfrom=TechNet-Gallery)
- [Средство изменения размера ATA](https://aka.ms/atasizingtool)
- [Обязательно ознакомьтесь с форумом ATA.](https://social.technet.microsoft.com/Forums/security/home?forum=mata)
- [Настройка сбора данных о событиях](configure-event-collection.md)
- [Предварительные требования ATA](ata-prerequisites.md)