---
title: Устранение неполадок защитника Майкрософт для идентификации с помощью журналов
description: В этой статье описывается, как можно использовать защитник Майкрософт для журналов удостоверений для устранения неполадок.
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 10/27/2020
ms.topic: how-to
ms.collection: M365-security-compliance
ms.service: azure-advanced-threat-protection
ms.reviewer: ''
ms.suite: ''
ms.openlocfilehash: ea19abd7497d0d925e764a80666dc595862566f9
ms.sourcegitcommit: f434dbff577d9944df18ca7533d026acdab0bb42
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/03/2020
ms.locfileid: "93275007"
---
# <a name="troubleshooting-product-long-sensor-using-the-product-short-logs"></a>Устранение неполадок [!INCLUDE [Product long](includes/product-long.md)] датчика с помощью [!INCLUDE [Product short](includes/product-short.md)] журналов

[!INCLUDE [Rebranding notice](includes/rebranding.md)]

В [!INCLUDE [Product short](includes/product-short.md)] журналах представлены сведения о том, что делает каждый компонент [!INCLUDE [Product long](includes/product-long.md)] датчика в любой определенный момент времени.

[!INCLUDE [Product short](includes/product-short.md)]Журналы находятся во вложенной папке Logs ( **журналы** ) [!INCLUDE [Product short](includes/product-short.md)] , где установлен; расположение по умолчанию: **C:\Program files\azure Multi Advanced Threat Protection \\ Sensor**. В каталоге установки по умолчанию журналы находятся по следующему пути: **C:\Program Files\Azure Advanced Threat Protection Sensor\version number\Logs**.

[!INCLUDE [Product short](includes/product-short.md)]Датчик имеет следующие журналы:

- **Microsoft. Тройн. датчик. log** — этот журнал содержит все, что происходит в [!INCLUDE [Product short](includes/product-short.md)] датчике (включая разрешение и ошибки). Его основное назначение заключается в получении сведений о состоянии всех операций в хронологическом порядке.

- **Microsoft. Тройн. Sensor-Errors. log** — этот журнал содержит только ошибки, перехваченные [!INCLUDE [Product short](includes/product-short.md)] датчиком. Его основное назначение — проверка работоспособности и изучение событий, которые необходимо сопоставить с моментом времени.

- **Microsoft. Тройн. датчик. обновление. log** — этот журнал используется для процесса обновления датчика, который отвечает за обновление [!INCLUDE [Product short](includes/product-short.md)] датчика, если он настроен для автоматического выполнения.

> [!NOTE]
> Максимальный размер каждого файла первых трех журналов — 50 МБ. При достижении этого размера открывается новый файл журнала, а предыдущий переименовывается на &lt;имя исходного файла&gt;-Archived-00000. С каждым переименованием число в названии увеличивается. По умолчанию, если накопилось более 10 файлов одного типа, самые старые из них удаляются.

## <a name="product-short-deployment-logs"></a>[!INCLUDE [Product short](includes/product-short.md)] Журналы развертывания

[!INCLUDE [Product short](includes/product-short.md)]Журналы развертывания находятся во временном каталоге для пользователя, установившего продукт. В папке установки по умолчанию ее можно найти по адресу: **C:\Users\Administrator\AppData\Local\Temp** (или по одному каталогу выше% TEMP%).

[!INCLUDE [Product short](includes/product-short.md)] журналы развертывания датчика:

- **Azure Advanced Threat Protection Microsoft.Tri.Sensor.Deployment.Deployer_YYYYMMDDHHMMSS.log**  — этот файл журнала регистрирует весь процесс развертывания датчика. Он доступен в упомянутой выше папке temp или в папке C:\Windows\Temp.

- **Azure Advanced Threat Protection Sensor_YYYYMMDDHHMMSS. log** — в этом журнале перечислены этапы процесса развертывания [!INCLUDE [Product short](includes/product-short.md)] датчика. Его основное использование — отслеживание [!INCLUDE [Product short](includes/product-short.md)] процесса развертывания датчика.

- **Azure Advanced Threat Protection Sensor_YYYYMMDDHHMMSS_001_MsiPackage. log.** в этом файле журнала перечислены этапы процесса развертывания [!INCLUDE [Product short](includes/product-short.md)] двоичных файлов датчика. Его основное использование заключается в отслеживании развертывания [!INCLUDE [Product short](includes/product-short.md)] двоичных файлов датчика.

> [!NOTE]
> Помимо упомянутых здесь журналов развертывания, есть и другие журналы, имя которых начинается с "Azure Advanced Threat Protection", которые могут содержать дополнительные сведения о процессе развертывания.

## <a name="see-also"></a>См. также:

- [[!INCLUDE [Product short](includes/product-short.md)] требований](prerequisites.md)
- [[!INCLUDE [Product short](includes/product-short.md)] Планирование ресурсов](capacity-planning.md)
- [Настройка сбора данных о событиях](configure-event-collection.md)
- [Настройка пересылки событий Windows](configure-event-forwarding.md)
- [Посетите [!INCLUDE [Product short](includes/product-short.md)] форум!](https://aka.ms/MDIcommunity)
