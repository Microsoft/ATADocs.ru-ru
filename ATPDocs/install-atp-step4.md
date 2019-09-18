---
title: Краткое руководство по установке датчика Azure ATP | Документация Майкрософт
description: На четвертом шаге установки Azure ATP выполняется установка датчика Azure ATP.
author: mlottner
ms.author: mlottner
ms.date: 03/03/2019
ms.topic: quickstart
ms.collection: M365-security-compliance
ms.service: azure-advanced-threat-protection
ms.reviewer: itargoet
ms.suite: ems
ms.openlocfilehash: f3af1034b73d1fc058a966c5d90eaf24dd282140
ms.sourcegitcommit: 939c098dd02a1f4191c528d10d69d059a62042b2
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/15/2019
ms.locfileid: "71004879"
---
# <a name="quickstart-install-the-azure-atp-sensor"></a>Краткое руководство. Установка датчика Azure ATP

Из этого краткого руководства вы узнаете, как установить датчик Azure ATP на контроллере домена. Если вы предпочитаете автоматическую установку, прочтите статью [Автоматическая установка](atp-silent-installation.md).

## <a name="prerequisites"></a>Предварительные условия

- [Экземпляр Azure ATP](install-atp-step1.md), [подключенный к Active Directory](install-atp-step2.md).
- Скачанная копия [пакета установки датчика ATP](install-atp-step3.md) и ключ доступа.
- На компьютере должна быть установлена платформа Microsoft .NET Framework 4.7. Если она не установлена, пакет установки датчика Azure ATP установит ее, что может потребовать перезагрузку сервера.

## <a name="install-the-sensor"></a>Установка датчика

Выполните следующие действия на контроллере домена.

1. Проверьте подключение компьютера к необходимым конечным точкам облачной службы Azure ATP:
   - Европа
      - [https://triprd1wceuw1sensorapi.atp.azure.com](https://triprd1wceuw1sensorapi.atp.azure.com) 
      - [https://triprd1wceun1sensorapi.atp.azure.com](https://triprd1wceun1sensorapi.atp.azure.com)
   - США 
      - [https://triprd1wcuse1sensorapi.atp.azure.com](https://triprd1wcuse1sensorapi.atp.azure.com)
      - [https://triprd1wcusw1sensorapi.atp.azure.com](https://triprd1wcusw1sensorapi.atp.azure.com)
      - [https://triprd1wcuswb1sensorapi.atp.azure.com](https://triprd1wcuswb1sensorapi.atp.azure.com)
   - Азия
      - [https://triprd1wcasse1sensorapi.atp.azure.com](https://triprd1wcasse1sensorapi.atp.azure.com)

2. Извлеките файлы установки из ZIP-файла. При установке непосредственно из ZIP-файла произойдет сбой.

3. Запустите файл **setup.exe датчика Azure ATP** и следуйте указаниям мастера установки.

4. На странице **приветствия** выберите язык и нажмите кнопку **Далее**.

    ![Язык установки автономного датчика Azure ATP](media/sensor-install-language.png)


5. Мастер установки автоматически проверит, является ли сервер контроллером домена или выделенным сервером. Если это контроллер домена, будет установлен датчик Azure ATP. Если это выделенный сервер, будет установлен автономный датчик Azure ATP.
    
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

    - KB 3047154 (только для Windows Server 2012 R2)

        > [!IMPORTANT]
        > - Не устанавливайте исправление KB 3047154 на узел виртуализации. (Узел, на котором выполняется виртуализация. Ее можно запустить на виртуальной машине.) Это может привести к неправильному зеркальному отображению портов. 
        > - Если Wireshark устанавливается на компьютере с датчиком ATP, после запуска Wireshark необходимо перезапустить датчик ATP, так как он использует те же драйверы.

    - Служба датчика Azure ATP и служба средства обновления датчика Azure ATP
    - Распространяемый пакет Microsoft Visual C++ 2013.


## <a name="next-steps"></a>Дальнейшие шаги

Датчик Azure ATP оказывает минимальное влияние на ресурсы контроллера домена и сетевую активность. Для создания оценки производительности см. [Планирование емкости для решения Azure ATP](install-atp-step5.md).


## <a name="join-the-community"></a>Присоединяйтесь к сообществу!

Возникли дополнительные вопросы или желание обсудить с другими пользователями службу Azure ATP и связанные с ней вопросы безопасности? Присоединяйтесь к [сообществу Azure ATP](https://aka.ms/azureatpcommunity)!
