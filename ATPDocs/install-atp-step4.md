---
title: Установка Azure Advanced Threat Protection | Документы Майкрософт
description: На четвертом шаге установки Azure ATP выполняется установка датчика Azure ATP.
keywords: ''
author: mlottner
ms.author: mlottner
manager: mbaldwin
ms.date: 12/16/2018
ms.topic: conceptual
ms.prod: ''
ms.service: azure-advanced-threat-protection
ms.technology: ''
ms.assetid: 51911e39-76c7-4dcd-bc0b-ec6235d0403f
ms.reviewer: itargoet
ms.suite: ems
ms.openlocfilehash: 5b5d588f11bb1c7a665cf4727cb996e5261b7237
ms.sourcegitcommit: 281d8ea451b6ac726331d0032c344651b1a964b7
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/16/2018
ms.locfileid: "53450394"
---
*Область применения: Расширенная защита от угроз Azure*



# <a name="install-azure-atp---step-4"></a>Установка Azure ATP. Шаг 4

> [!div class="step-by-step"]
> [« Шаг 3](install-atp-step3.md)
> [Шаг 5 »](install-atp-step5.md)

## <a name="step-4-install-the-azure-atp-sensor"></a>Шаг 4. Установка датчика Azure ATP

> [!IMPORTANT]
>На компьютере должна быть установлена платформа Microsoft .NET Framework 4.7. Если платформа .NET Framework 4.7 не установлена, пакет установки датчика Azure ATP установит ее, после чего потребуется перезагрузить сервер.

Выполните следующие действия на контроллере домена.

1. Убедитесь, что компьютер подключен к правильной конечной точке облачной службы Azure ATP:
  - [https://triprd1wceuw1sensorapi.atp.azure.com](https://triprd1wceuw1sensorapi.atp.azure.com) (для Европы)  
  - [https://triprd1wcuse1sensorapi.atp.azure.com](https://triprd1wcuse1sensorapi.atp.azure.com) (для США)
  - [https://triprd1wcasse1sensorapi.atp.azure.com](https://triprd1wcasse1sensorapi.atp.azure.com) (для Азии)

2. Извлеките файлы установки из ZIP-файла. 
> [!NOTE] 
> При установке непосредственно из ZIP-файла произойдет сбой.

3.  Запустите файл **setup.exe датчика Azure ATP** и следуйте указаниям мастера установки.

4.  На странице **приветствия** выберите язык и нажмите кнопку **Далее**.

     ![Язык установки автономного датчика Azure ATP](media/sensor-install-language.png)


5.  Мастер установки автоматически проверит, является ли сервер контроллером домена или выделенным сервером. Если это контроллер домена, будет установлен датчик Azure ATP, если это выделенный сервер, устанавливается автономный датчик Azure ATP. 
    
    Если устанавливается автономный датчик Azure ATP, вы увидите приведенный ниже экран, который сообщает, что на выделенном сервере будет установлен автономный датчик Azure ATP.
    
    ![Установка автономного датчика Azure ATP](media/sensor-install-deployment-type.png)

    Нажмите кнопку **Далее**.

    > [!NOTE] 
    > Если контроллер домена или выделенный сервер не удовлетворяет минимальным требованиям к оборудованию для установки, вы получите предупреждение. Но при этом вы все равно сможете продолжить установку, нажав кнопку **Далее**. Это может быть полезным, если вы устанавливаете Azure ATP в небольшой тестовой среде, где для хранения данных не потребуется много места. Для установки в рабочей среде настоятельно рекомендуется изучить [руководство по планированию ресурсов](atp-capacity-planning.md) для Azure ATP и обеспечить выполнение всех требований для контроллера домена или выделенного сервера.

6.  В разделе **Настройка датчика** введите путь установки и ключ доступа, скопированный на предыдущем шаге, в зависимости от вашей среды:

    ![Изображение: настройка автономного датчика Azure ATP](media/sensor-install-config.png)

      - Путь установки — это расположение для установки автономного датчика Azure ATP. По умолчанию используется %programfiles%\Azure Advanced Threat Protection sensor. Оставьте значение по умолчанию.

      - Ключ доступа — это ключ, полученный на портале Azure ATP на предыдущем шаге.
    
7. Нажмите кнопку **Установить**. Во время установки автономного датчика Azure ATP устанавливаются и настраиваются следующие компоненты.

    -   KB 3047154 (только для Windows Server 2012 R2)

        > [!IMPORTANT]
        > -   Не устанавливайте исправление KB 3047154 на узел виртуализации. (Узел, на котором выполняется виртуализация. Ее можно запустить на виртуальной машине.) Это может привести к неправильному зеркальному отображению портов. 
        > -   Если Wireshark устанавливается на компьютере с датчиком ATP, после запуска Wireshark необходимо перезапустить датчик ATP, так как он использует те же драйверы.

    -   Служба датчика Azure ATP и служба средства обновления датчика Azure ATP
    -   Распространяемый пакет Microsoft Visual C++ 2013.

8.  После завершения установки нажмите кнопку **Запустить**, чтобы открыть браузер и войти на портал Azure ATP.


> [!div class="step-by-step"]
> [« Шаг 3](install-atp-step3.md)
> [Шаг 5 »](install-atp-step5.md)


## <a name="see-also"></a>См. также

- [Средство изменения размера Azure ATP](http://aka.ms/aatpsizingtool)

- [Настройка сбора данных о событиях](configure-event-collection.md)

- [Предварительные требования к Azure ATP](atp-prerequisites.md)

- [Загляните на форум Azure ATP!](https://aka.ms/azureatpcommunity)
