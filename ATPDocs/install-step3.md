---
title: Краткое руководство по скачиванию пакета установки датчика Microsoft Defender для удостоверений
description: На третьем шаге установки Microsoft Defender для удостоверений происходит скачивание пакета установки датчика Defender для удостоверений.
keywords: ''
author: shsagir
ms.author: shsagir
ms.date: 10/26/2020
ms.topic: quickstart
ms.collection: M365-security-compliance
ms.service: azure-advanced-threat-protection
ms.reviewer: itargoet
ms.suite: ems
ms.openlocfilehash: f971bf0ccadf2eba52b40c95591abaff0c963e0e
ms.sourcegitcommit: f434dbff577d9944df18ca7533d026acdab0bb42
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/03/2020
ms.locfileid: "93277082"
---
# <a name="quickstart-download-the-product-long-sensor-setup-package"></a>Краткое руководство. Скачивание пакета установки датчика [!INCLUDE [Product long](includes/product-long.md)]

[!INCLUDE [Rebranding notice](includes/rebranding.md)]

В этом кратком руководстве вы скачаете пакет установки датчика [!INCLUDE [Product long](includes/product-long.md)] с портала.

## <a name="prerequisites"></a>Предварительные условия

- [Экземпляр [!INCLUDE [Product short](includes/product-short.md)]](install-step1.md), [подключенный к Active Directory](install-step2.md).

## <a name="download-the-setup-package"></a>Скачивание пакета установки

Настроив параметры подключения к домену, скачайте пакет установки датчика [!INCLUDE [Product short](includes/product-short.md)]. Дополнительные сведения о датчике [!INCLUDE [Product short](includes/product-short.md)] см. в статье [Архитектура [!INCLUDE [Product short](includes/product-short.md)]](architecture.md).

В списке действий в верхней части страницы щелкните **Скачать** , чтобы перейти на страницу **Датчики**.

![[!INCLUDE [Product short](includes/product-short.md)]: параметры конфигурации датчика](media/sensor-config.png)

Чтобы открыть окно конфигурации позже, выберите **Конфигурация** , а затем в разделе **Система** щелкните **Датчики**.  

1. Нажмите кнопку **Скачать** , чтобы сохранить пакет локально.
1. Скопируйте **ключ** **доступа**. Ключ доступа требуется для подключения датчика [!INCLUDE [Product short](includes/product-short.md)] к экземпляру [!INCLUDE [Product short](includes/product-short.md)]. Ключ доступа представляет собой одноразовый пароль для развертывания датчика, после чего осуществляется полный обмен данными с использованием сертификатов для проверки подлинности и шифрования по протоколу TLS. Нажмите кнопку **Повторно создать** , если вам потребуется повторно создать новый ключ доступа. Он не повлияет на ранее развернутые датчики, так как используется только для первоначальной регистрации датчика.
1. Скопируйте пакет на выделенный сервер или контроллер домена, на который устанавливается датчик [!INCLUDE [Product short](includes/product-short.md)]. Кроме того, можно открыть портал [!INCLUDE [Product short](includes/product-short.md)] с выделенного сервера или контроллера домена и пропустить этот шаг.

ZIP-файл содержит следующие файлы:

- установщик датчика [!INCLUDE [Product short](includes/product-short.md)];

- файл параметров конфигурации с данными для подключения к облачной службе [!INCLUDE [Product short](includes/product-short.md)].

## <a name="next-steps"></a>Дальнейшие действия

> [!div class="step-by-step"]
> ["Шаг 2. Подключение к Active Directory](install-step2.md)
> [Шаг 4. Установка датчика [!INCLUDE [Product short](includes/product-short.md)]"](install-step4.md)

## <a name="join-the-community"></a>Присоединяйтесь к сообществу!

У вас есть дополнительные вопросы или вы хотите обсудить с другими пользователями особенности использования [!INCLUDE [Product short](includes/product-short.md)] или вопросы, связанные с безопасностью? Присоединяйтесь к [сообществу [!INCLUDE [Product short](includes/product-short.md)]](https://aka.ms/MDIcommunity).
