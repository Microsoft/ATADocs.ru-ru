---
title: "Установка Advanced Threat Analytics. Шаг 2 | Документация Майкрософт"
description: "На втором этапе установки ATA вы настроите параметры подключения к домену на сервере центра ATA."
keywords: 
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 07/2/2017
ms.topic: get-started-article
ms.prod: 
ms.service: advanced-threat-analytics
ms.technology: 
ms.assetid: e1c5ff41-d989-46cb-aa38-5a3938f03c0f
ms.reviewer: bennyl
ms.suite: ems
ms.openlocfilehash: aa5e752fa10644165cb70d2cd8c08a1145261edb
ms.sourcegitcommit: fa50f37b134d7579d7c310852dff60e5f1996eaa
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/03/2017
---
*Применяется к Advanced Threat Analytics версии 1.8*



# Установка ATA. Шаг 2
<a id="install-ata---step-2" class="xliff"></a>

>[!div class="step-by-step"]
[Шаг 1](install-ata-step1.md)
[Шаг 3](install-ata-step3.md)

## Шаг 2. Укажите имя пользователя и пароль для подключения к лесу Active Directory
<a id="step-2-provide-a-username-and-password-to-connect-to-your-active-directory-forest" class="xliff"></a>

При первом открытии консоли ATA открывается такой экран:

![Этап приветствия ATA 1](media/ATA_1.7-welcome-provide-username.png)

1.  Введите следующие сведения и нажмите кнопку **Save** (Сохранить).

    |Поле|Комментарии|
    |---------|------------|
    |**Имя пользователя** (указывается обязательно)|Введите имя пользователя только для чтения, например **ATAuser**.|
    |**Пароль** (указывается обязательно)|Введите пароль для имени пользователя только для чтения, например **Parolch1k**.|
    |**Домен** (указывается обязательно)|Введите домен для имени пользователя только для чтения, например **contoso.com**. **Примечание**. Для домена, в котором находится пользователь, необходимо указать полное доменное имя. Например, если учетная запись пользователя находится в домене corp.contoso.com, необходимо ввести `corp.contoso.com`, а не contoso.com|

2. Чтобы проверить подключение к домену и убедиться в том, что по указанным учетным данным можно получить доступ, можно нажать кнопку **Проверить подключение**. Работает, только если Центр ATA подключен к домену.   

    После сохранения приветственное сообщение в консоли изменится на следующее: ![ATA welcome stage 1 finished](media/ATA_1.7-welcome-provide-username-finished.png) (Этап приветствия 1 в ATA завершен).

3. Чтобы продолжить, щелкните в консоли **Download Gateway setup and install the first Gateway** (Скачать средство установки шлюза и установить первый шлюз).


>[!div class="step-by-step"]
[Шаг 1](install-ata-step1.md)
[Шаг 3](install-ata-step3.md)


## См. также
<a id="see-also" class="xliff"></a>

- [Ознакомьтесь с форумом ATA.](https://social.technet.microsoft.com/Forums/security/home?forum=mata)
- [Настройка сбора данных о событиях](configure-event-collection.md)
- [Предварительные требования ATA](ata-prerequisites.md)
