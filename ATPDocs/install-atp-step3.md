---
title: Установка Azure Advanced Threat Protection | Документы Майкрософт
description: На третьем шаге установки Azure ATP выполняется скачивание пакета установки датчика Azure ATP.
keywords: ''
author: mlottner
ms.author: mlottner
manager: mbaldwin
ms.date: 12/02/2018
ms.topic: get-started-article
ms.prod: ''
ms.service: azure-advanced-threat-protection
ms.technology: ''
ms.assetid: 95bb4ec1-841f-41b7-92fe-fbd144085724
ms.reviewer: itargoet
ms.suite: ems
ms.openlocfilehash: 9e397d669ba4df7fe9f1ea6b497368b730abc938
ms.sourcegitcommit: f4f2a1b2c674c4dba7a46ece0624f5ea10c4865e
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/02/2018
ms.locfileid: "52744903"
---
*Применяется к: Azure Advanced Threat Protection*



# <a name="install-azure-atp---step-3"></a>Установка Azure ATP. Шаг 3

> [!div class="step-by-step"]
> [« Шаг 2](install-atp-step2.md)
> [Шаг 4 »](install-atp-step4.md)

## <a name="step-3-download-the-azure-atp-sensor-setup-package"></a>Шаг 3. Скачивание пакета установки датчика Azure ATP
Настроив параметры подключения к домену, скачайте пакет установки датчика Azure ATP. Пакет установки датчика Azure ATP можно устанавливать на выделенном сервере или на контроллере домена. При установке на контроллере домена пакет устанавливается в виде датчика Azure ATP, при установке на выделенном сервере и использовании зеркального отображения портов пакет устанавливается как автономный датчик Azure ATP. Дополнительные сведения о датчике Azure ATP см. в статье [Архитектура Azure ATP](atp-architecture.md). 

В списке действий в верхней части страницы щелкните **Скачать**, чтобы перейти на страницу **Датчик**.

![Параметры конфигурации датчика Azure ATP](media/atp-sensor-config.png)

> [!NOTE] 
> Чтобы открыть окно конфигурации позже, щелкните **значок параметров** (верхний правый угол), выберите **Конфигурация**, а затем в разделе **Система** щелкните **Датчик**.  

1.  Щелкните **Датчик**.
2.  Сохраните пакет на локальном компьютере.
3.  Скопируйте **ключ** **доступа**. Ключ доступа требуется для подключения датчика Azure ATP к экземпляру Azure ATP. Ключ доступа представляет собой одноразовый пароль для развертывания датчика, после чего осуществляется полный обмен данными с использованием сертификатов для проверки подлинности и шифрования по протоколу TLS. Воспользуйтесь кнопкой **Regenerate** (Повторно создать), если вам потребуется повторно создать новый ключ доступа. Он не повлияет на ранее развернутые датчики, так как используется только для первоначальной регистрации датчика.
4.  Скопируйте пакет на выделенный сервер или контроллер домена, на который устанавливается датчик Azure ATP. Кроме того, можно открыть портал экземпляра Azure ATP с выделенного сервера или контроллера домена и пропустить этот шаг.

ZIP-файл содержит следующие файлы:

-   установщик датчика Azure ATP;

-   файл параметров конфигурации с данными для подключения к облачной службе Azure ATP.


> [!div class="step-by-step"]
> [« Шаг 2](install-atp-step2.md)
> [Шаг 4 »](install-atp-step4.md)


## <a name="see-also"></a>См. также

- [Средство изменения размера Azure ATP](http://aka.ms/aatpsizingtool)

- [Настройка сбора данных о событиях](configure-event-collection.md)

- [Предварительные требования к Azure ATP](atp-prerequisites.md)

- [Загляните на форум Azure ATP!](https://aka.ms/azureatpcommunity)