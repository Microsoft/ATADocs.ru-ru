---
title: Установка Azure Advanced Threat Protection | Документы Майкрософт
description: На втором этапе установки Azure ATP выполняется настройка параметров подключения к домену в облачной службе Azure ATP.
keywords: ''
author: mlottner
ms.author: mlottner
manager: mbaldwin
ms.date: 12/30/2018
ms.topic: conceptual
ms.prod: ''
ms.service: azure-advanced-threat-protection
ms.technology: ''
ms.assetid: ae8a95f0-278c-4a12-ae69-14282364fba1
ms.reviewer: itargoet
ms.suite: ems
ms.openlocfilehash: ada659d86088cb9f93eba4aca54dd2553e8fb69a
ms.sourcegitcommit: 19ff0ed88e450506b5725bbcbb0d0bd2f0c5e4bb
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/27/2019
ms.locfileid: "55085458"
---
# <a name="install-azure-atp---step-2"></a>Установка Azure ATP. Шаг 2

> [!div class="step-by-step"]
> [« Шаг 1](install-atp-step1.md)
> [Шаг 3 »](install-atp-step3.md)

## <a name="provide-a-username-and-password-to-connect-to-your-active-directory-forest"></a>Указание имени пользователя и пароля для подключения к лесу Active Directory

При первом запуске портала Azure ATP открывается такой экран:

![начальный экран Azure ATP на шаге 1](media/directory-services.png)

> [!IMPORTANT]
> Здесь должны быть указаны учетные данные пользователя для учетной записи пользователя в локальной среде Active Directory. 


1.  Введите следующие сведения и нажмите кнопку **Save** (Сохранить).

    |Поле|Комментарии|
    |---------|------------|
    |**Имя пользователя** (указывается обязательно)|Введите имя для пользователя Active Directory с правами только на чтение, например **ATPuser**. **Примечание.** **Не** используйте формат имени участника-пользователя для имени пользователя.|
    |**Пароль** (указывается обязательно)|Введите пароль для пользователя с правами только на чтение, например **Parolch1k**.|
    |**Домен** (указывается обязательно)|Введите домен для имени пользователя только для чтения, например **contoso.com**. **Примечание.** Для домена, в котором находится пользователь, необходимо указать полное доменное имя. Например, если учетная запись пользователя находится в домене corp.contoso.com, необходимо ввести `corp.contoso.com`, а не contoso.com|

2. На портале Azure ATP щелкните **Скачать пакет установки датчиков и установить первый датчик**, чтобы продолжить.


> [!div class="step-by-step"]
> [« Шаг 1](install-atp-step1.md)
> [Шаг 3 »](install-atp-step3.md)


## <a name="see-also"></a>См. также
- [Средство изменения размера Azure ATP](http://aka.ms/aatpsizingtool)
- [Настройка сбора данных о событиях](configure-event-collection.md)
- [Предварительные требования к Azure ATP](atp-prerequisites.md)
- [Загляните на форум Azure ATP!](https://aka.ms/azureatpcommunity)