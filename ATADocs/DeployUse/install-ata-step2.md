---
title: "Установка ATA. Шаг 2 | Microsoft ATA"
description: "На втором этапе установки ATA вы настроите параметры подключения к домену на сервере центра ATA."
keywords: 
author: rkarlin
manager: mbaldwin
ms.date: 08/24/2016
ms.topic: get-started-article
ms.prod: 
ms.service: advanced-threat-analytics
ms.technology: 
ms.assetid: e1c5ff41-d989-46cb-aa38-5a3938f03c0f
ms.reviewer: bennyl
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 050f1ef0b39d69b64ede53243a7fa2d33d0e4813
ms.openlocfilehash: fc268bcb2e3d027b09fa3349427934f60783b971


---

*Применяется к Advanced Threat Analytics версии 1.7*



# Установка ATA. Шаг 2

>[!div class="step-by-step"]
[Шаг 1](install-ata-step1.md)
[Шаг 3](install-ata-step3.md)

## Шаг 2. Укажите имя пользователя и пароль для подключения к лесу Active Directory

При первом открытии консоли ATA открывается такой экран:

![Этап приветствия ATA 1](media/ATA_1.7-welcome-provide-username.png)

1.  Введите следующие сведения и нажмите кнопку **Save** (Сохранить).

    |Поле|Комментарии|
    |---------|------------|
    |**Имя пользователя** (указывается обязательно)|Введите имя пользователя только для чтения, например **ATAuser**.|
    |**Пароль** (указывается обязательно)|Введите пароль для имени пользователя только для чтения, например **Parolch1k**.|
    |**Домен** (указывается обязательно)|Введите домен для имени пользователя только для чтения, например **contoso.com**. **Примечание**. Для домена, в котором находится пользователь, необходимо указать полное доменное имя. Например, если учетная запись пользователя находится в домене corp.contoso.com, необходимо ввести `corp.contoso.com`, а не contoso.com|
    |Автоматическое обновление всех шлюзов ATA |Если этот параметр включен, в последующих версиях выпусков при обновлении центра ATA все шлюзы ATA будут автоматически обновляться.|

    После сохранения приветственное сообщение в консоли изменяется на следующее: ![ATA welcome stage 1 finished (Этап приветствия 1 в ATA завершен).](media/ATA_1.7-welcome-provide-username-finished.png)

2. Чтобы продолжить, щелкните в консоли **Download Gateway setup and install the first Gateway** (Скачать средство установки шлюза и установить первый шлюз).


>[!div class="step-by-step"]
[Шаг 1](install-ata-step1.md)
[Шаг 3](install-ata-step3.md)


## См. также

- [Обязательно ознакомьтесь с форумом ATA.](https://social.technet.microsoft.com/Forums/security/home?forum=mata)
- [Настройка сбора данных о событиях](configure-event-collection.md)
- [Предварительные требования для ATA](/advanced-threat-analytics/plan-design/ata-prerequisites)



<!--HONumber=Aug16_HO5-->


