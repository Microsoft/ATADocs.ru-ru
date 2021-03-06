---
title: Установка Advanced Threat Analytics. шаг 2
description: На втором этапе установки ATA вы настроите параметры подключения к домену на сервере центра ATA.
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 12/30/2018
ms.topic: conceptual
ms.prod: advanced-threat-analytics
ms.technology: ''
ms.assetid: e1c5ff41-d989-46cb-aa38-5a3938f03c0f
ms.reviewer: bennyl
ms.suite: ems
ms.openlocfilehash: e7f88831d10cfb1ba15d2fe650a056e7a3004d2f
ms.sourcegitcommit: 5bf0c6a204b71126306a0c64108eaf9cb7fc042f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/18/2021
ms.locfileid: "101097527"
---
# <a name="install-ata---step-2"></a>Установка ATA. Шаг 2

[!INCLUDE [Banner for top of topics](includes/banner.md)]

> [!div class="step-by-step"]
> [«Шаг 1](install-ata-step1.md) 
>  [Шаг 3»](install-ata-step3.md)

## <a name="step-2-provide-a-username-and-password-to-connect-to-your-active-directory-forest"></a>Шаг 2. Укажите имя пользователя и пароль для подключения к лесу Active Directory

При первом открытии консоли ATA открывается такой экран:

![Этап приветствия ATA 1](media/ATA_1.7-welcome-provide-username.png)

1. Введите следующие сведения и нажмите кнопку **Save** (Сохранить).

    |Поле|Комментарии|
    |---------|------------|
    |**Имя пользователя** (указывается обязательно)|Введите имя пользователя только для чтения, например **ATAuser**. **Примечание.** **Не** используйте формат имени участника-пользователя.|
    |**Пароль** (обязательно)|Введите пароль для имени пользователя только для чтения, например **Parolch1k**.|
    |**Домен** (указывается обязательно)|Введите домен для имени пользователя только для чтения, например **contoso.com**. **Примечание**. Для домена, в котором находится пользователь, необходимо указать полное доменное имя. Например, если учетная запись пользователя находится в домене corp.contoso.com, необходимо ввести `corp.contoso.com`, а не contoso.com|

1. Чтобы проверить подключение к домену и убедиться в том, что по указанным учетным данным можно получить доступ, можно нажать кнопку **Проверить подключение**. Работает, только если Центр ATA подключен к домену.

    После сохранения приветственное сообщение в консоли изменится на следующее: ![Этап приветствия 1 в ATA завершен](media/ATA_1.7-welcome-provide-username-finished.png).

1. Чтобы продолжить, щелкните в консоли **Download Gateway setup and install the first Gateway** (Скачать средство установки шлюза и установить первый шлюз).

> [!div class="step-by-step"]
> [«Шаг 1](install-ata-step1.md) 
>  [Шаг 3»](install-ata-step3.md)

## <a name="related-videos"></a>Видео по теме

- [Обзор развертывания ATA](https://channel9.msdn.com/Shows/Microsoft-Security/Overview-of-ATA-Deployment-in-10-Minutes)
- [Выбор правильного типа шлюза ATA](https://channel9.msdn.com/Shows/Microsoft-Security/ATA-Deployment-Choose-the-Right-Gateway-Type)

## <a name="see-also"></a>См. также

- [Руководство по развертыванию среды для подтверждения концепции ATA](/samples/browse/?redirectedfrom=TechNet-Gallery)
- [Средство изменения размера ATA](https://aka.ms/atasizingtool)
- [Обязательно ознакомьтесь с форумом ATA.](https://social.technet.microsoft.com/Forums/security/home?forum=mata)
- [Настройка сбора данных о событиях](configure-event-collection.md)
- [Предварительные требования ATA](ata-prerequisites.md)