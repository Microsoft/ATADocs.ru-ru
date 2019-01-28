---
title: Использование журналов для устранения неполадок Azure Advanced Threat Protection | Документация Майкрософт
description: В этой статье описывается, как использовать журналы Azure ATP для устранения неполадок.
keywords: ''
author: mlottner
ms.author: mlottner
manager: mbaldwin
ms.date: 10/04/2018
ms.topic: conceptual
ms.prod: ''
ms.service: azure-advanced-threat-protection
ms.technology: ''
ms.assetid: de796346-647d-48e1-970a-8f072e990f1e
ms.reviewer: ''
ms.suite: ''
ms.openlocfilehash: cc8008f79758f314321c59f170e9099610824e54
ms.sourcegitcommit: a0ebb0b6f140d4abf091ebd9d756b975b3d96b9d
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/23/2019
ms.locfileid: "54458527"
---
# <a name="troubleshooting-azure-advanced-threat-protection-atp-sensor-using-the-atp-logs"></a>Использование журналов для устранения неполадок датчика Azure Advanced Threat Protection (ATP)
Журналы ATP содержат полезные сведения о работе всех компонентов датчика Azure ATP в любой момент времени.


Журналы Azure ATP размещаются в подкаталоге с именем **Logs** того каталога, где установлено решение ATA (по умолчанию это **C:\Program Files\Azure Advanced Threat Protection Sensor\\**). Расположение установки по умолчанию: **C:\Program Files\Azure Advanced Threat Protection Sensor\номер_версии\Logs**.

Датчик Azure ATP включает следующие журналы:

-   **Microsoft.Tri.Sensor.log** — содержит информацию обо всем, что происходит в датчике Azure ATP (включая разрешения и ошибки). Его основное назначение заключается в получении сведений о состоянии всех операций в хронологическом порядке.

-   **Microsoft.Tri.Sensor-Resolution.log** — содержит сведения о разрешении сущностей на основе трафика, отслеживаемого датчиком ATP. Его основное назначение — изучение событий разрешения сущностей.

-   **Microsoft.Tri.Sensor-Errors.log** — содержит только ошибки, которые обнаруживает датчик ATP. Его основное назначение — проверка работоспособности и изучение событий, которые необходимо сопоставить с моментом времени.

-   **Microsoft.Tri.Sensor.Updater.log** — этот журнал используется для процесса автоматического обновления датчика ATP, если оно настроено. 


> [!NOTE]
> Максимальный размер каждого файла первых трех журналов — 50 МБ. При достижении этого размера открывается новый файл журнала, а предыдущий переименовывается на &lt;имя исходного файла&gt;-Archived-00000. С каждым переименованием число в названии увеличивается. По умолчанию, если накопилось более 10 файлов одного типа, самые старые из них удаляются.

## <a name="azure-atp-deployment-logs"></a>Журналы развертывания Azure ATP
Журналы развертывания Azure ATP расположены во временном каталоге пользователя, установившего продукт. Расположение установки по умолчанию: **C:\Users\Administrator\AppData\Local\Temp** (или на один каталог выше %temp%).

Журналы развертывания датчика Azure ATP:

-   **Azure Advanced Threat Protection Sensor_ГГГГММДДЧЧММСС.log** — здесь перечислены действия процесса развертывания датчика Azure ATP. Основное назначение журнала — отслеживание этого процесса.

-   **Azure Advanced Threat Protection Sensor_ГГГГММДДЧЧММСС_001_MsiPackage.log** — в этом файле журнала перечислены действия процесса развертывания двоичных файлов датчика Azure ATP. Его основное назначение — отслеживание развертывания этих двоичных файлов.


> [!NOTE] 
> Помимо упомянутых здесь журналов развертывания, есть и другие журналы, имя которых начинается с "Azure Advanced Threat Protection", которые могут содержать дополнительные сведения о процессе развертывания.


## <a name="see-also"></a>См. также
- [Предварительные требования к Azure ATP](atp-prerequisites.md)
- [Планирование производительности Azure ATP](atp-capacity-planning.md)
- [Настройка сбора данных о событиях](configure-event-collection.md)
- [Настройка пересылки событий Windows](configure-event-forwarding.md)
- [Загляните на форум Azure ATP!](https://aka.ms/azureatpcommunity)