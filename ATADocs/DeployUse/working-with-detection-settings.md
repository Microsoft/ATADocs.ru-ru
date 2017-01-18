---
title: "Работа с параметрами обнаружения ATA | Документация Майкрософт"
description: "В этом документе объясняется, как настроить список IP-адресов и подсетей, для которых возникли непредвиденные обстоятельства и которые нужно обрабатывать отдельно от остальных сущностей в сети."
keywords: 
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 08/24/2016
ms.topic: article
ms.prod: 
ms.service: advanced-threat-analytics
ms.technology: 
ms.assetid: f4f2ae30-4849-4a4f-8f6d-bfe99a32c746
ms.reviewer: bennyl
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 85e285c5d88e5916e0bf0eb7dd327cb4cb45b4cb
ms.openlocfilehash: 93f2a72c9623674c73b3ee83ecf12be8e0766365


---

*Область применения: Advanced Threat Analytics версии 1.7*



# <a name="working-with-ata-detection-settings"></a>Работа с параметрами обнаружения ATA
На странице настройки **обнаружения** вы можете настроить список IP-адресов и подсетей, для которых возникли непредвиденные обстоятельства и которые нужно обрабатывать отдельно от остальных сущностей в сети.

## <a name="setting-up-detection"></a>Настройка обнаружения
В разделе **Detection** (Обнаружение) вы можете задать такие элементы:

-   **Идентификатор безопасности учетных записей Honeytoken** — это учетная запись пользователя, в которой не должны выполняться сетевые операции. Эта учетная запись будет настроена как пользователь Honeytoken ATA. Если кто-то попытается использовать эту учетную запись, ATA создаст запись о подозрительных действиях, что будет означать вредоносные действия. Для настройки пользователя Honeytoken потребуется идентификатор безопасности учетной записи пользователя, а не имя пользователя.

>[!NOTE]
> Найти идентификатор безопасности пользователя вы можете на вкладке *Account Info* (Сведения об учетной записи) профиля пользователя в консоли ATA.


![Параметры обнаружения ATA (honeytoken)](media/ata-detection-settings-honeytoken-1.7.png)


**Исключения обнаружения**: вы можете исключить IP-адреса из следующих случаев обнаружения. Если ввести IP-адрес в один из этих списков, ATA исключит такой IP-адрес из этого типа обнаруженных действий.

-   Исключаемые IP-адреса в случае проверки DNS

-   Исключаемые IP-адреса в случае атаки Pass-the-Ticket

![Исключения в параметрах обнаружения ATA](media/ata-detection-settings-exclusions-1.7.png)


## <a name="see-also"></a>См. также
- [Обработка подозрительных действий](working-with-suspicious-activities.md)
- [Изменение конфигурации ATA](modifying-ata-configuration.md)
- [Ознакомьтесь с форумом ATA.](https://social.technet.microsoft.com/Forums/security/home?forum=mata)



<!--HONumber=Jan17_HO1-->


