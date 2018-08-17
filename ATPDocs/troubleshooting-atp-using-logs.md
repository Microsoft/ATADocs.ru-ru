---
title: Использование журналов для устранения неполадок Azure Advanced Threat Protection | Документация Майкрософт
description: В этой статье описывается, как использовать журналы Azure ATP для устранения неполадок.
keywords: ''
author: mlottner
ms.author: mlottner
manager: mbaldwin
ms.date: 8/13/2018
ms.topic: article
ms.prod: ''
ms.service: azure-advanced-threat-protection
ms.technology: ''
ms.assetid: de796346-647d-48e1-970a-8f072e990f1e
ms.reviewer: ''
ms.suite: ''
ms.openlocfilehash: 4cac2722bcfaf51996b201d379991dc335bcf371
ms.sourcegitcommit: dc56b9e9533db1a2dc314b199e90191bb25adaba
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/14/2018
ms.locfileid: "40102343"
---
*Область применения: Advanced Threat Protection*



# <a name="troubleshooting-azure-advanced-threat-protection-atp-sensor-using-the-atp-logs"></a>Использование журналов для устранения неполадок датчика Azure Advanced Threat Protection (ATP)
Журналы ATP содержат полезные сведения о работе всех компонентов датчика Azure ATP в любой момент времени.


Эти журналы размещаются в каталоге установки ATP (по умолчанию **C:\Program Files\Azure Advanced Threat Protection Sensor\\**) в подпапке **Logs**. В каталоге установки по умолчанию журналы находятся по следующему пути: **C:\Program Files\Azure Advanced Threat Protection Sensor\version number\Logs**.

Датчик Azure ATP включает следующие журналы:

-   **Microsoft.Tri.Sensor.log** — содержит информацию обо всем, что происходит в датчике Azure ATP (включая разрешения и ошибки). Его основное назначение заключается в получении сведений о состоянии всех операций в хронологическом порядке.

-   **Microsoft.Tri.Sensor-Resolution.log** — содержит сведения о разрешении сущностей на основе трафика, отслеживаемого датчиком ATP. Его основное назначение — изучение событий разрешения сущностей.

-   **Microsoft.Tri.Sensor-Errors.log** — содержит только ошибки, которые обнаруживает датчик ATP. Его основное назначение — проверка работоспособности и изучение событий, которые необходимо сопоставить с моментом времени.

-   **Microsoft.Tri.Sensor.Updater.log** — этот журнал используется для процесса автоматического обновления датчика ATP, если оно настроено. 


> [!NOTE]
> Максимальный размер каждого файла первых трех журналов — 50 МБ. При достижении этого размера открывается новый файл журнала, а предыдущий переименовывается на &lt;имя исходного файла&gt;-Archived-00000. С каждым переименованием число в названии увеличивается. По умолчанию, если накопилось более 10 файлов одного типа, самые старые из них удаляются.

## <a name="azure-atp-deployment-logs"></a>Журналы развертывания Azure ATP
Журналы развертывания Azure ATP расположены во временном каталоге пользователя, установившего продукт. Их можно найти по следующему пути в месте установки по умолчанию: **C:\Users\Administrator\AppData\Local\Temp** (или на один каталог выше %temp%).

Журналы развертывания датчика Azure ATP:

-   **Azure Advanced Threat Protection Sensor_ГГГГММДДЧЧММСС.log** — здесь перечислены действия процесса развертывания датчика Azure ATP. Основное назначение журнала — отслеживание этого процесса.

-   **Azure Advanced Threat Protection Sensor_ГГГГММДДЧЧММСС_001_MsiPackage.log** — в этом файле журнала перечислены действия процесса развертывания двоичных файлов датчика Azure ATP. Его основное назначение — отслеживание развертывания этих двоичных файлов.


> [!NOTE] 
> Помимо упомянутых здесь журналов развертывания, есть и другие журналы, имя которых начинается с "Azure Advanced Threat Protection", которые могут содержать дополнительные сведения о процессе развертывания.


## <a name="see-also"></a>См. также
- [Предварительные требования к Azure ATP](atp-prerequisites.md)
- [Планирование производительности Azure ATP](atp-capacity-planning.md)
- [Настройка сбора данных о событиях](configure-event-collection.md)
- [Настройка пересылки событий Windows](configure-event-forwarding.md#configuring-windows-event-forwarding)
- [Обязательно ознакомьтесь с форумом ATP](https://aka.ms/azureatpcommunity)