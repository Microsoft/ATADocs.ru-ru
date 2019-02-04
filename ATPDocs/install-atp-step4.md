---
title: Установка Azure Advanced Threat Protection | Документы Майкрософт
description: На четвертом шаге установки Azure ATP выполняется установка датчика Azure ATP.
keywords: ''
author: mlottner
ms.author: mlottner
manager: mbaldwin
ms.date: 1/27/2019
ms.topic: conceptual
ms.prod: ''
ms.service: azure-advanced-threat-protection
ms.technology: ''
ms.assetid: 51911e39-76c7-4dcd-bc0b-ec6235d0403f
ms.reviewer: itargoet
ms.suite: ems
ms.openlocfilehash: 5c357ea537c9fe9a23fc426670d47bf85d53f316
ms.sourcegitcommit: 19ff0ed88e450506b5725bbcbb0d0bd2f0c5e4bb
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/27/2019
ms.locfileid: "55085254"
---
# <a name="install-azure-atp---step-4"></a>Установка Azure ATP. Шаг 4

> [!div class="step-by-step"]
> [« Шаг 3](install-atp-step3.md)
> [Шаг 5 »](install-atp-step5.md)

## <a name="install-the-azure-atp-sensor"></a>Установка датчика Azure ATP

> [!IMPORTANT]
>На компьютере должна быть установлена платформа Microsoft .NET Framework 4.7. Если она не установлена, пакет установки датчика Azure ATP установит ее, что может потребовать перезагрузку сервера.

Выполните следующие действия на контроллере домена.

1. Проверьте подключение компьютера к необходимым конечным точкам облачной службы Azure ATP:
   - [https://triprd1wceuw1sensorapi.atp.azure.com](https://triprd1wceuw1sensorapi.atp.azure.com) 
   - [https://triprd1wceun1sensorapi.atp.azure.com](https://triprd1wceun1sensorapi.atp.azure.com)
   <br>(для Европы)  
   - [https://triprd1wcuse1sensorapi.atp.azure.com](https://triprd1wcuse1sensorapi.atp.azure.com)
   - [https://triprd1wcusw1sensorapi.atp.azure.com](https://triprd1wcusw1sensorapi.atp.azure.com)
   - [https://triprd1wcuswb1sensorapi.atp.azure.com](https://triprd1wcuswb1sensorapi.atp.azure.com)
   <br>(для США)
   - [https://triprd1wcasse1sensorapi.atp.azure.com](https://triprd1wcasse1sensorapi.atp.azure.com)<br>(для Азии)

2. Извлеките файлы установки из ZIP-файла. 
   > [!NOTE] 
   > При установке непосредственно из ZIP-файла произойдет сбой.

3. Запустите файл **setup.exe датчика Azure ATP** и следуйте указаниям мастера установки.

4. На странице **приветствия** выберите язык и нажмите кнопку **Далее**.

    ![Язык установки автономного датчика Azure ATP](media/sensor-install-language.png)


5. Мастер установки автоматически проверит, является ли сервер контроллером домена или выделенным сервером. Если это контроллер домена, будет установлен датчик Azure ATP, если это выделенный сервер, устанавливается автономный датчик Azure ATP. 
    
    Если устанавливается датчик Azure ATP, вы увидите приведенный ниже экран, который сообщает, что на выделенном сервере будет установлен датчик Azure ATP.
    
    ![Установка датчика Azure ATP](media/sensor-install-deployment-type.png)

   Нажмите кнопку **Далее**.

    > [!NOTE] 
    > Если контроллер домена или выделенный сервер не удовлетворяет минимальным требованиям к оборудованию для установки, выдается предупреждение. Тем не менее вы сможете продолжить установку, нажав кнопку **Далее**. Это может быть удобно, если вы устанавливаете Azure ATP в небольшой тестовой среде, где для хранения данных требуется меньше места. Для установки в рабочей среде настоятельно рекомендуется изучить [руководство по планированию ресурсов](atp-capacity-planning.md) для Azure ATP и обеспечить выполнение всех требований для контроллера домена или выделенного сервера.

6. В разделе **Настройка датчика** введите путь установки и ключ доступа, скопированный на предыдущем шаге, в зависимости от вашей среды:

    ![Изображение конфигурации датчика Azure ATP](media/sensor-install-config.png)

      - Путь установки — это расположение для установки датчика Azure ATP. По умолчанию используется %programfiles%\Azure Advanced Threat Protection sensor. Оставьте значение по умолчанию.

     - Ключ доступа — это ключ, полученный на портале Azure ATP на предыдущем шаге.
    
7. Нажмите кнопку **Установить**. Во время установки автономного датчика Azure ATP устанавливаются и настраиваются следующие компоненты.

    -   KB 3047154 (только для Windows Server 2012 R2)

        > [!IMPORTANT]
        > -   Не устанавливайте исправление KB 3047154 на узел виртуализации. (Узел, на котором выполняется виртуализация. Ее можно запустить на виртуальной машине.) Это может привести к неправильному зеркальному отображению портов. 
        > -   Если Wireshark устанавливается на компьютере с датчиком ATP, после запуска Wireshark необходимо перезапустить датчик ATP, так как он использует те же драйверы.

    -   Служба датчика Azure ATP и служба средства обновления датчика Azure ATP
    -   Распространяемый пакет Microsoft Visual C++ 2013.

8. После завершения установки нажмите кнопку **Запустить**, чтобы открыть браузер и войти на портал Azure ATP.


> [!div class="step-by-step"]
> [« Шаг 3](install-atp-step3.md)
> [Шаг 5 »](install-atp-step5.md)


## <a name="see-also"></a>См. также

- [Средство изменения размера Azure ATP](http://aka.ms/aatpsizingtool)

- [Настройка сбора данных о событиях](configure-event-collection.md)

- [Предварительные требования к Azure ATP](atp-prerequisites.md)

- [Загляните на форум Azure ATP!](https://aka.ms/azureatpcommunity)
