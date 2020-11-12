---
title: Краткое руководство по установке датчика Microsoft Defender для удостоверений
description: На четвертом шаге установки Microsoft Defender для удостоверений происходит установка датчика Defender для удостоверений.
author: shsagir
ms.author: shsagir
ms.date: 10/26/2020
ms.topic: quickstart
ms.collection: M365-security-compliance
ms.service: azure-advanced-threat-protection
ms.reviewer: itargoet
ms.suite: ems
ms.openlocfilehash: 9c612167b4d87958c6a27235443a0dd5ab464613
ms.sourcegitcommit: f434dbff577d9944df18ca7533d026acdab0bb42
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/03/2020
ms.locfileid: "93276235"
---
# <a name="quickstart-install-the-product-long-sensor"></a>Краткое руководство. Установка датчика [!INCLUDE [Product long](includes/product-long.md)]

[!INCLUDE [Rebranding notice](includes/rebranding.md)]

Из этого краткого руководства вы узнаете, как установить датчик [!INCLUDE [Product long](includes/product-long.md)] на контроллере домена. Если вы предпочитаете автоматическую установку, прочтите статью [Автоматическая установка](silent-installation.md).

## <a name="prerequisites"></a>Предварительные условия

- [Экземпляр [!INCLUDE [Product short](includes/product-short.md)]](install-step1.md), [подключенный к Active Directory](install-step2.md).
- Скачанная копия [пакета установки датчика [!INCLUDE [Product short](includes/product-short.md)]](install-step3.md) и ключ доступа.
- На компьютере должна быть установлена платформа Microsoft .NET Framework 4.7 или более поздняя версия. Если она не установлена, пакет установки датчика [!INCLUDE [Product short](includes/product-short.md)] установит ее, что может потребовать перезагрузки сервера.

## <a name="install-the-sensor"></a>Установка датчика

Выполните следующие действия на контроллере домена.

1. Проверьте подключение компьютера к необходимым конечным точкам [облачной службы [!INCLUDE [Product short](includes/product-short.md)]](configure-proxy.md#enable-access-to-azure-atp-service-urls-in-the-proxy-server):
1. Извлеките файлы установки из ZIP-файла. При установке непосредственно из ZIP-файла произойдет сбой.
1. Запустите файл **setup.exe датчика Azure ATP** и следуйте указаниям мастера установки.
1. На странице **приветствия** выберите язык и нажмите кнопку **Далее**.

    ![Язык установки автономного датчика [!INCLUDE [Product short](includes/product-short.md)]](media/sensor-install-language.png)

1. Мастер установки автоматически проверит, является ли сервер контроллером домена или выделенным сервером. Если это контроллер домена, будет установлен датчик [!INCLUDE [Product short](includes/product-short.md)]. Если это выделенный сервер, будет установлен автономный датчик [!INCLUDE [Product short](includes/product-short.md)].

    Если устанавливается датчик [!INCLUDE [Product short](includes/product-short.md)], вы увидите приведенный ниже экран, который сообщает, что на выделенном сервере будет установлен датчик [!INCLUDE [Product short](includes/product-short.md)].

    ![Установка датчика [!INCLUDE [Product short](includes/product-short.md)]](media/sensor-install-deployment-type.png)

    Нажмите кнопку **Далее**.

    > [!NOTE]
    > Если контроллер домена или выделенный сервер не удовлетворяет минимальным требованиям к оборудованию для установки, выдается предупреждение. Несмотря на предупреждение, вы можете щелкнуть **Далее** и продолжить установку. Такой вариант все равно может подойти для установки [!INCLUDE [Product short](includes/product-short.md)] в небольшой лабораторной среде тестирования, требующей меньше места для хранения данных. Для установки в рабочей среде мы настоятельно рекомендуем изучить [руководство по планированию ресурсов](capacity-planning.md) для [!INCLUDE [Product short](includes/product-short.md)] и обеспечить выполнение всех требований для контроллера домена или выделенного сервера.

1. В разделе **Настройка датчика** введите путь установки и ключ доступа, скопированный на предыдущем шаге, в зависимости от вашей среды:

    ![Изображение конфигурации датчика [!INCLUDE [Product short](includes/product-short.md)]](media/sensor-install-config.png)

    - Путь установки: это расположение для установки датчика [!INCLUDE [Product short](includes/product-short.md)]. По умолчанию используется %programfiles%\Azure Advanced Threat Protection sensor. Оставьте значение по умолчанию.
    - Ключ доступа — это ключ, полученный на портале [!INCLUDE [Product short](includes/product-short.md)] на предыдущем шаге.

1. Щелкните **Install** (Установить). Во время установки датчика [!INCLUDE [Product short](includes/product-short.md)] устанавливаются и настраиваются следующие компоненты:

    - KB 3047154 (только для Windows Server 2012 R2)

        > [!IMPORTANT]
        >
        > - Не устанавливайте исправление KB 3047154 на узел виртуализации. (Узел, на котором выполняется виртуализация. Ее можно запустить на виртуальной машине.) Это может привести к неправильному зеркальному отображению портов.
        > - Если Wireshark устанавливается на компьютере с датчиком [!INCLUDE [Product short](includes/product-short.md)], после запуска Wireshark необходимо перезапустить датчик [!INCLUDE [Product short](includes/product-short.md)], так как он использует те же драйверы.

    - Служба датчика [!INCLUDE [Product short](includes/product-short.md)] и служба обновления датчика [!INCLUDE [Product short](includes/product-short.md)]
    - Распространяемый пакет Microsoft Visual C++ 2013.

## <a name="next-steps"></a>Дальнейшие шаги

Датчик [!INCLUDE [Product short](includes/product-short.md)] оказывает минимальное влияние на ресурсы контроллера домена и сетевую активность. Чтобы создать оценку производительности, см. сведения о [планировании ресурсов для [!INCLUDE [Product short](includes/product-short.md)]](capacity-planning.md).

## <a name="join-the-community"></a>Присоединяйтесь к сообществу!

У вас есть дополнительные вопросы или вы хотите обсудить с другими пользователями особенности использования [!INCLUDE [Product short](includes/product-short.md)] или вопросы, связанные с безопасностью? Присоединяйтесь к [сообществу [!INCLUDE [Product short](includes/product-short.md)]](https://aka.ms/MDIcommunity).
