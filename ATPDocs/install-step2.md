---
title: Краткое руководство по подключению Microsoft Defender для удостоверений к Active Directory
description: На втором шаге установки Microsoft Defender для удостоверений происходит настройка параметров подключения к домену в облачной службе Defender для удостоверений
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 10/26/2020
ms.topic: quickstart
ms.collection: M365-security-compliance
ms.service: azure-advanced-threat-protection
ms.reviewer: itargoet
ms.suite: ems
ms.openlocfilehash: 58a5f6c37a5b5bc4e224393aac5ad9771d6a1f6b
ms.sourcegitcommit: e2227c0b0e5aaa5163dc56d4131ca82f8dca8fb0
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/18/2020
ms.locfileid: "94847876"
---
# <a name="quickstart-connect-to-your-active-directory-forest"></a>Краткое руководство. Подключение к лесу Active Directory

В этом кратком руководстве вы подключите [!INCLUDE [Product long](includes/product-long.md)] к Active Directory (AD), чтобы получить данные о пользователях и компьютерах. Если вы подключаете несколько лесов, см. статью [Поддержка нескольких лесов](multi-forest.md).

## <a name="prerequisites"></a>Предварительные требования

- [Экземпляр [!INCLUDE [Product short](includes/product-short.md)]](install-step1.md).
- Знакомство со статьей [Предварительные требования [!INCLUDE [Product short](includes/product-short.md)]](prerequisites.md).
- По крайней мере одна из следующих учетных записей служб каталогов с доступом на чтение ко всем объектам в отслеживаемых доменах:
  - **Стандартная** учетная запись пользователя AD и пароль. Требуется для датчиков под управлением Windows Server 2008 R2 с пакетом обновления 1 (SP1).
  - **Групповая управляемая учетная запись службы** (gMSA). Требуется Windows Server 2012 или более поздней версии.  
  Все датчики должны иметь разрешения на получение пароля учетной записи gMSA. См. сведения о создании учетной записи gMSA в руководстве по [настройке учетной записи gMSA](#how-to-set-up-a-gmsa-account).

    > [!NOTE]
    >
    > - Для компьютеров с датчиками под управлением Windows Server 2012 и более поздних версий рекомендуется использовать учетную запись **gMSA** для повышения уровня безопасности и включения автоматического управления паролями.
    > - Если у вас есть датчики под управлением Windows Server 2008 и Windows Server 2012 или более поздней версии, рекомендуется использовать не только учетную запись **gMSA**, но и по крайней мере одну **стандартную** учетную запись пользователя AD.

### <a name="how-to-set-up-a-gmsa-account"></a>Настройка учетной записи gMSA

1. Создайте [учетную запись gMSA](/windows-server/security/group-managed-service-accounts/getting-started-with-group-managed-service-accounts#BKMK_CreateGMSA).
1. Создайте [группу безопасности, содержащую все контроллеры домена с датчиками (под управлением Windows Server 2012 или более поздней версии)](/windows-server/security/group-managed-service-accounts/getting-started-with-group-managed-service-accounts#BKMK_AddMemberHosts) с разрешениями на получение пароля учетной записи gMSA. (Рекомендовано)

## <a name="provide-a-username-and-password-to-connect-to-your-active-directory-forest"></a>Указание имени пользователя и пароля для подключения к лесу Active Directory

При первом запуске портала [!INCLUDE [Product short](includes/product-short.md)] открывается такой экран:

![[!INCLUDE [Product short](includes/product-short.md)]: этап 1 приветствия](media/directory-services.png)

1. Введите следующие сведения и нажмите кнопку **Save** (Сохранить).

    |Поле|Комментарии|
    |---|---|
    |**Имя пользователя** (указывается обязательно)|Введите имя пользователя AD, доступное только для чтения. Пример. **DefenderForIdentityUser**. Необходимо использовать **стандартную** учетную запись пользователя AD или gMSA. **Не** используйте формат имени участника-пользователя для имени пользователя.|
    |**Пароль** (требуется для стандартной учетной записи пользователя AD)|Только для учетной записи пользователя AD: введите пароль пользователя (только для чтения). Пример. **Parolch1k**.|
    |**Групповая управляемая учетная запись службы** (требуется для учетной записи gMSA).|Только для учетной записи gMSA: выберите **групповую управляемую учетную запись службы**.|
    |**Домен** (указывается обязательно)|Введите домен для пользователя с правами только на чтение. Например, **contoso.com**. Для домена, в котором находится пользователь, необходимо указать полное доменное имя. Например, если учетная запись пользователя находится в домене corp.contoso.com, необходимо ввести `corp.contoso.com`, а не contoso.com|

1. На портале [!INCLUDE [Product short](includes/product-short.md)] щелкните **Скачать пакет установки датчиков и установить первый датчик**, чтобы продолжить.

## <a name="next-steps"></a>Следующие шаги

> [!div class="step-by-step"]
> ["Шаг 1. Создание экземпляра [!INCLUDE [Product short](includes/product-short.md)]](install-step1.md)
> [Шаг 3. Скачивание пакета установки датчика"](install-step3.md)

## <a name="join-the-community"></a>Присоединяйтесь к сообществу!

У вас есть дополнительные вопросы или вы хотите обсудить с другими пользователями особенности использования [!INCLUDE [Product short](includes/product-short.md)] или вопросы, связанные с безопасностью? Присоединяйтесь к [сообществу [!INCLUDE [Product short](includes/product-short.md)]](https://aka.ms/MDIcommunity).
