---
title: "Установка Advanced Threat Analytics. Шаг 2 | Документация Майкрософт"
description: "На втором этапе установки ATA вы настроите параметры подключения к домену на сервере центра ATA."
keywords: 
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 01/23/2017
ms.topic: get-started-article
ms.prod: 
ms.service: advanced-threat-analytics
ms.technology: 
ms.assetid: e1c5ff41-d989-46cb-aa38-5a3938f03c0f
ms.reviewer: bennyl
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: b28cb3a0da844b7c460c03726222bc775a9e47da
ms.openlocfilehash: 23ea3185e0d3556f524d8131a715a6057988f04c


---

*Область применения: Advanced Threat Analytics версии 1.7*



# <a name="install-ata---step-2"></a>Установка ATA. Шаг 2

>[!div class="step-by-step"]
[Шаг 1](install-ata-step1.md)
[Шаг 3](install-ata-step3.md)

## <a name="step-2-provide-a-username-and-password-to-connect-to-your-active-directory-forest"></a>Шаг 2. Укажите имя пользователя и пароль для подключения к лесу Active Directory

При первом открытии консоли ATA открывается такой экран:

![Этап приветствия ATA 1](media/ATA_1.7-welcome-provide-username.png)

1.  Введите следующие сведения и нажмите кнопку **Save** (Сохранить).

    |Поле|Комментарии|
    |---------|------------|
    |**Имя пользователя** (указывается обязательно)|Введите имя пользователя только для чтения, например **ATAuser**.|
    |**Пароль** (указывается обязательно)|Введите пароль для имени пользователя только для чтения, например **Parolch1k**.|
    |**Домен** (указывается обязательно)|Введите домен для имени пользователя только для чтения, например **contoso.com**. **Примечание**. Для домена, в котором находится пользователь, необходимо указать полное доменное имя. Например, если учетная запись пользователя находится в домене corp.contoso.com, необходимо ввести `corp.contoso.com`, а не contoso.com|

2. Кроме того, можно нажать кнопку **Test connection** (Проверить подключение), чтобы проверить подключение к домену и убедиться, что по указанным учетным данным можно получить доступ. Работает, только если Центр ATA подключен к домену.   

    После сохранения приветственное сообщение в консоли изменится на следующее: ![ATA welcome stage 1 finished](media/ATA_1.7-welcome-provide-username-finished.png) (Этап приветствия 1 в ATA завершен).

3. Чтобы продолжить, щелкните в консоли **Download Gateway setup and install the first Gateway** (Скачать средство установки шлюза и установить первый шлюз).


>[!div class="step-by-step"]
[Шаг 1](install-ata-step1.md)
[Шаг 3](install-ata-step3.md)


## <a name="see-also"></a>См. также

- [Ознакомьтесь с форумом ATA.](https://social.technet.microsoft.com/Forums/security/home?forum=mata)
- [Настройка сбора данных о событиях](configure-event-collection.md)
- [Предварительные требования ATA](/advanced-threat-analytics/plan-design/ata-prerequisites)



<!--HONumber=Feb17_HO1-->


