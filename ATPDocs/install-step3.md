---
title: Краткое руководство. Скачивание пакета установки датчика Azure ATP
description: На третьем шаге установки Azure ATP выполняется скачивание пакета установки датчика Azure ATP.
keywords: ''
author: shsagir
ms.author: shsagir
ms.date: 02/19/2020
ms.topic: quickstart
ms.collection: M365-security-compliance
ms.service: azure-advanced-threat-protection
ms.assetid: 95bb4ec1-841f-41b7-92fe-fbd144085724
ms.openlocfilehash: 04e1df3e375d48c17a42590521b9de06373f4799
ms.sourcegitcommit: c7c0a4c9f7507f3e8e0f219798ed7d347c03e792
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/22/2020
ms.locfileid: "90910217"
---
# <a name="quickstart-download-the-azure-atp-sensor-setup-package"></a>Краткое руководство. Скачивание пакета установки датчика Azure ATP

[!INCLUDE [Rebranding notice](includes/rebranding.md)]

В этом кратком руководстве вы скачаете пакет установки датчика Azure ATP с портала.

## <a name="prerequisites"></a>Предварительные условия

- [Экземпляр Azure ATP](install-step1.md), [подключенный к Active Directory](install-step2.md).

## <a name="download-the-setup-package"></a>Скачивание пакета установки

Настроив параметры подключения к домену, скачайте пакет установки датчика Azure ATP. Дополнительные сведения о датчике Azure ATP см. в статье [Архитектура Azure ATP](architecture.md).

В списке действий в верхней части страницы щелкните **Скачать**, чтобы перейти на страницу **Датчик**.

![Параметры конфигурации датчика Azure ATP](media/atp-sensor-config.png)

 Чтобы открыть окно конфигурации позже, щелкните **значок параметров** (правый верхний угол), выберите **Конфигурация**, а затем в разделе **Система** щелкните **Датчик**.  

1. Щелкните **Датчик**.
1. Сохраните пакет на локальном компьютере.
1. Скопируйте **ключ** **доступа**. Ключ доступа требуется для подключения датчика Azure ATP к экземпляру Azure ATP. Ключ доступа представляет собой одноразовый пароль для развертывания датчика, после чего осуществляется полный обмен данными с использованием сертификатов для проверки подлинности и шифрования по протоколу TLS. Нажмите кнопку **Повторно создать**, если вам потребуется повторно создать новый ключ доступа. Он не повлияет на ранее развернутые датчики, так как используется только для первоначальной регистрации датчика.
1. Скопируйте пакет на выделенный сервер или контроллер домена, на который устанавливается датчик Azure ATP. Кроме того, можно открыть портал экземпляра Azure ATP с выделенного сервера или контроллера домена и пропустить этот шаг.

ZIP-файл содержит следующие файлы:

- установщик датчика Azure ATP;

- файл параметров конфигурации с данными для подключения к облачной службе Azure ATP.

## <a name="next-steps"></a>Следующие шаги

> [!div class="step-by-step"]
> ["Шаг 2. Подключение к Active Directory](install-step2.md)
> [Шаг 4. Установка датчика Azure ATP"](install-step4.md)

## <a name="join-the-community"></a>Присоединяйтесь к сообществу!

Возникли дополнительные вопросы или желание обсудить с другими пользователями службу Azure ATP и связанные с ней вопросы безопасности? Присоединяйтесь к [сообществу Azure ATP](https://aka.ms/azureatpcommunity)!