---
title: Краткое руководство по установке датчика Microsoft Defender для удостоверений
description: На четвертом шаге установки Microsoft Defender для удостоверений происходит установка датчика Defender для удостоверений.
ms.date: 02/17/2021
ms.topic: quickstart
ms.openlocfilehash: a9837c36dcdb90dba124eda5f8d6b9f082787d74
ms.sourcegitcommit: 5bf0c6a204b71126306a0c64108eaf9cb7fc042f
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/18/2021
ms.locfileid: "101097421"
---
# <a name="quickstart-install-the-microsoft-defender-for-identity-sensor"></a>Краткое руководство. Установка датчика Microsoft Defender для удостоверений

Из этого краткого руководства вы узнаете, как установить датчик [!INCLUDE [Product long](includes/product-long.md)] на контроллере домена. Если вы предпочитаете автоматическую установку, прочтите статью [Автоматическая установка](silent-installation.md).

## <a name="prerequisites"></a>Предварительные условия

- [Экземпляр [!INCLUDE [Product short](includes/product-short.md)]](install-step1.md), [подключенный к Active Directory](install-step2.md).
- Скачанная копия [пакета установки датчика [!INCLUDE [Product short](includes/product-short.md)]](install-step3.md) и ключ доступа.
- На компьютере должна быть установлена платформа Microsoft .NET Framework 4.7 или более поздняя версия. Если она не установлена, пакет установки датчика [!INCLUDE [Product short](includes/product-short.md)] установит ее, что может потребовать перезагрузки сервера.
- Если при установке датчиков на серверах AD FS используется внешний сервер SQL, настройте его так, чтобы предоставить учетной записи *службы каталогов* (**Конфигурация** > **Службы каталогов** > **Имя пользователя**) разрешения на *подключение*, *вход*, *чтение* и *выбор* для базы данных **AdfsConfiguration**.

## <a name="install-the-sensor"></a>Установка датчика

Выполните следующие действия на контроллере домена.

1. Проверьте подключение компьютера к необходимым конечным точкам [облачной службы [!INCLUDE [Product short](includes/product-short.md)]](configure-proxy.md#enable-access-to-azure-atp-service-urls-in-the-proxy-server).
1. Извлеките файлы установки из ZIP-файла. При установке непосредственно из ZIP-файла произойдет сбой.
1. Запустите **программу установки датчика Azure ATP (файл setup.exe)** с повышенными привилегиями (**Запуск от имени администратора**) и следуйте указаниям мастера установки.
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

1. Щелкните **Install**(Установить). Во время установки датчика [!INCLUDE [Product short](includes/product-short.md)] устанавливаются и настраиваются следующие компоненты:

    - KB 3047154 (только для Windows Server 2012 R2)

        > [!IMPORTANT]
        >
        > - Не устанавливайте исправление KB 3047154 на узел виртуализации. (Узел, на котором выполняется виртуализация. Ее можно запустить на виртуальной машине.) Это может привести к неправильному зеркальному отображению портов.
        > - Если Wireshark устанавливается на компьютере с датчиком [!INCLUDE [Product short](includes/product-short.md)], после запуска Wireshark необходимо перезапустить датчик [!INCLUDE [Product short](includes/product-short.md)], так как он использует те же драйверы.

    - Служба датчика [!INCLUDE [Product short](includes/product-short.md)] и служба обновления датчика [!INCLUDE [Product short](includes/product-short.md)]
    - Распространяемый пакет Microsoft Visual C++ 2013.

## <a name="post-installation-steps-for-ad-fs-servers"></a>Действия после установки на серверах AD FS

Выполните следующие действия, чтобы настроить Defender для удостоверений после завершения установки датчика на сервере AD FS.

1. На портале [!INCLUDE [Product short](includes/product-short.md)] выберите **Конфигурация**.

1. В разделе **Система** выберите **Датчики**.

    ![Страница конфигурации датчика [!INCLUDE [Product short](includes/product-short.md)]](media/sensor-config.png)

1. Выберите датчик, установленный на сервере AD FS.
1. Во всплывающем окне в поле **Контроллер домена сопоставителя** введите полное доменное имя контроллеров домена сопоставителя, затем щелкните значок "плюс" **(+)** , после чего нажмите кнопку **Сохранить**.  

    ![Настройка сопоставителя датчика AD FS в [!INCLUDE [Product short](includes/product-short.md)]](media/sensor-config-adfs-resolver.png)

    Инициализация датчика может занять несколько минут. В это время состояние службы датчика AD FS должно измениться с **Остановлено** на **Работает**.

## <a name="next-steps"></a>Дальнейшие шаги

Датчик [!INCLUDE [Product short](includes/product-short.md)] оказывает минимальное влияние на ресурсы контроллера домена и сетевую активность. Чтобы создать оценку производительности, см. сведения о [планировании ресурсов для [!INCLUDE [Product short](includes/product-short.md)]](capacity-planning.md).

## <a name="join-the-community"></a>Присоединяйтесь к сообществу!

У вас есть дополнительные вопросы или вы хотите обсудить с другими пользователями особенности использования [!INCLUDE [Product short](includes/product-short.md)] или вопросы, связанные с безопасностью? Присоединяйтесь к [сообществу [!INCLUDE [Product short](includes/product-short.md)]](https://aka.ms/MDIcommunity).
