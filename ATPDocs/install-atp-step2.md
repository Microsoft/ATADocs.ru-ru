---
title: Установка Azure Advanced Threat Protection. Шаг 2 | Документы Майкрософт
description: На втором этапе установки Azure ATP выполняется настройка параметров подключения к домену в облачной службе Azure ATP.
keywords: ''
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 2/21/2017
ms.topic: get-started-article
ms.prod: ''
ms.service: azure-advanced-threat-protection
ms.technology: ''
ms.assetid: ae8a95f0-278c-4a12-ae69-14282364fba1
ms.reviewer: itargoet
ms.suite: ems
ms.openlocfilehash: 11f9d5bf69ffda0843a94c7a2bb31869dc980dce
ms.sourcegitcommit: 03e959b7ce4b6df421297e1872e028793c967302
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/21/2018
ms.locfileid: "29445580"
---
*Применяется к: Azure Advanced Threat Protection*



# <a name="install-azure-atp---step-2"></a>Установка Azure ATP. Шаг 2

>[!div class="step-by-step"]
[« Шаг 1](install-atp-step1.md)
[Шаг 3 »](install-atp-step3.md)

## <a name="step-2-provide-a-username-and-password-to-connect-to-your-active-directory-forest"></a>Шаг 2. Указание имени пользователя и пароля для подключения к лесу Active Directory

При первом открытии портала рабочей области Azure ATP открывается такой экран:

![начальный экран Azure ATP на шаге 1](media/directory-services.png)

> [!IMPORTANT]
> Здесь должны быть указаны учетные данные пользователя для учетной записи пользователя в локальной среде Active Directory. 


1.  Введите следующие сведения и нажмите кнопку **Save** (Сохранить).

    |Поле|Комментарии|
    |---------|------------|
    |**Имя пользователя** (указывается обязательно)|Введите имя пользователя Active Directory только для чтения, например **ATPuser**.|
    |**Пароль** (указывается обязательно)|Введите пароль для имени пользователя только для чтения, например **Parolch1k**.|
    |**Домен** (указывается обязательно)|Введите домен для имени пользователя только для чтения, например **contoso.com**. **Примечание**. Для домена, в котором находится пользователь, необходимо указать полное доменное имя. Например, если учетная запись пользователя находится в домене corp.contoso.com, необходимо ввести `corp.contoso.com`, а не contoso.com|

3. На портале рабочей области щелкните **Download sensor setup and install the first sensor** (Скачать пакет установки датчиков и установить первый датчик), чтобы продолжить.


>[!div class="step-by-step"]
[« Шаг 1](install-atp-step1.md)
[Шаг 3 »](install-atp-step3.md)


## <a name="see-also"></a>См. также
- [Средство изменения размера Azure ATP](http://aka.ms/aatpsizingtool)
- [Настройка сбора данных о событиях](configure-event-collection.md)
- [Предварительные требования к Azure ATP](atp-prerequisites.md)
- [Обязательно ознакомьтесь с форумом ATP](https://aka.ms/azureatpcommunity)