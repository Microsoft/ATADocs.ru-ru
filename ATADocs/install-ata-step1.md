---
title: Установка Advanced Threat Analytics. шаг 1
description: На первом шаге установки ATA необходимо скачать и установить центр ATA на выбранный сервер.
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 01/12/2021
ms.topic: conceptual
ms.prod: advanced-threat-analytics
ms.technology: ''
ms.assetid: b3cceb18-0f3c-42ac-8630-bdc6b310f1d6
ms.reviewer: bennyl
ms.suite: ems
ms.openlocfilehash: bef73309e71acd067c02a5ff597f0b5397a09fc7
ms.sourcegitcommit: 5bf0c6a204b71126306a0c64108eaf9cb7fc042f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/18/2021
ms.locfileid: "101097561"
---
# <a name="install-ata---step-1"></a>Установка ATA. Шаг 1

[!INCLUDE [Banner for top of topics](includes/banner.md)]

> [!NOTE]
> **Жизненный цикл поддержки**
>
> Окончательная версия ATA доступна в [целом](https://support.microsoft.com/help/4568997/update-3-for-microsoft-advanced-threat-analytics-1-9). Основная фаза поддержки ATA закончилась 12 января 2021 г. Расширенная поддержка будет продолжена до 2026 января. Дополнительные сведения см. в [нашем блоге](https://techcommunity.microsoft.com/t5/microsoft-security-and/end-of-mainstream-support-for-advanced-threat-analytics-january/ba-p/1539181).

> [!div class="step-by-step"]
> [Шаг 2](install-ata-step2.md)

В этой процедуре установки приведены указания по выполнению новой установки ATA 1.9. Сведения об обновлении имеющегося развертывания ATA с более ранней версии см. в [руководстве по миграции для ATA версии 1.9](ata-update-1.9-migration-guide.md).

> [!IMPORTANT]
> Если вы используете Windows 2012 R2, то, прежде чем устанавливать ATA, установите обновление KB2934520 на сервер центра ATA и серверы шлюза ATA. Иначе обновление, устанавливаемое вместе с ATA, потребует перезагрузки во время процесса установки.

## <a name="step-1-download-and-install-the-ata-center"></a>Шаг 1. Скачивание и установка центра ATA.

Проверив соответствие сервера требованиям, можно приступить к установке центра ATA.

> [!NOTE]
> Если вы приобрели лицензию Enterprise Mobility + Security (EMS) непосредственно на портале Microsoft 365 или по модели лицензирования Cloud Solution Partner (CSP) и у вас нет доступа к Advanced Threat Analytics (ATA) на веб-сайте Microsoft Volume Licensing Center (VLSC), обратитесь в службу поддержки Майкрософт, чтобы узнать, как активировать решение ATA.

На сервере шлюза ATA сделайте следующее:

1. Скачайте ATA из [центра поддержки корпоративных лицензий Майкрософт](https://www.microsoft.com/Licensing/servicecenter/default.aspx) или из [центра оценки TechNet](https://www.microsoft.com/evalcenter/) или с сайта [MSDN](/powerapps/developer/common-data-service/org-service/subscribe-sdk-assembly-updates-using-nuget).

1. Войдите на компьютер, на котором вы устанавливаете центр ATA, как участник локальной группы администраторов.

1. Запустите **центр Microsoft ATA Setup.EXE** с повышенными привилегиями (**Запуск от имени администратора**) и следуйте указаниям мастера установки.

    > [!NOTE]
    > Запустите файл установки на локальном диске, а не из подключенного ISO-файла, чтобы избежать проблем в том случае, если при установке потребуется перезагрузка.

1. Если платформа Microsoft .NET Framework не установлена, при запуске установки будет предложено установить ее. После установки платформы .NET Framework может появиться запрос на перезагрузку.
1. На странице **приветствия** выберите язык, который будет использоваться для экранов установки ATA, и нажмите кнопку **Далее**.

1. Прочтите условия лицензионного соглашения об использовании программного обеспечения Майкрософт. Если вы принимаете условия, установите флажок и нажмите кнопку **Далее**.

1. Для ATA рекомендуется включить автоматическое обновление. Если на вашем компьютере не настроено автоматическое обновление Windows, откроется окно **Use Microsoft Update to help keep your computer secure and up to date** (Использовать Центр обновления Майкрософт для защиты и обновления компьютера).
    ![Изображение. Поддержка актуальности ATA](media/ata_ms_update.png)

1. Установите флажок **Использовать центр обновления Майкрософт (Microsoft) при проверке наличия обновлений (рекомендуется)**. Так вы разрешите в Windows обновлять другие продукты Майкрософт, включая ATA.

    ![Изображение. Настройка автоматического обновления Windows](media/ata_installupdatesautomatically.png)

1. На странице **настройки центра** введите указанные ниже сведения с учетом используемой среды.

    |Поле|Описание|Комментарии|
    |---------|---------------|------------|
    |Путь установки|Это расположение для установки центра ATA. По умолчанию этот путь — %programfiles%\Microsoft Advanced Threat Analytics\Center.|Оставьте значение по умолчанию|
    |Путь к данным базы данных|Это расположение, в котором размещены файлы базы данных MongoDB. По умолчанию используется путь %programfiles%\Microsoft Advanced Threat Analytics\Center\MongoDB\bin\data.|Выберите расположение, где предусмотрено достаточно пространства для будущего роста данных с учетом требований к размеру. **Примечание**. <ul><li>В рабочих средах следует использовать диск, на котором достаточно свободного места с учетом планирования ресурсов.</li><li>При крупных развертываниях база данных должна находиться на отдельном физическом диске.</li></ul>Дополнительные сведения о размерах см. в статье [Планирование производительности ATA](ata-capacity-planning.md).|
    |SSL-сертификат службы центра|Это сертификат, который используется службами центра ATA и консоли ATA.|Щелкните значок ключа, чтобы выбрать установленный сертификат, или установите флажок, чтобы создать самозаверяющий сертификат.|

    ![Изображение конфигурации центра ATA](media/ATA-Center-Configuration.png)

    > [!NOTE]
    > Следите за оповещениями о работоспособности центра сертификации SSL и предупреждениями об истечении срока действия. Если срок действия сертификата истечет, вам потребуется полностью повторно развернуть ATA.

1. Нажмите кнопку **Установить**, чтобы установить центр ATA вместе с его компонентами.  
Во время установки центра ATA устанавливаются и настраиваются следующие компоненты:

    - Служба центра ATA

    - MongoDB

    - Пользовательский набор сбора данных системного монитора.

    - самозаверяющие сертификаты (если выбраны во время установки).

1. По завершении установки щелкните **Запуск**, чтобы открыть консоль ATA и выполнить настройку на странице **Конфигурация**.
    Страница параметров **Общие** откроется автоматически. Там вы сможете продолжить настройку и развертывание шлюзов ATA.
    Так как вход на сайт выполняется с помощью IP-адреса, вы получаете предупреждение относительно сертификата. Это вполне нормально. Просто щелкните **Continue to this website** (Продолжить открытие этого веб-сайта).

### <a name="validate-installation"></a>Проверка установки

1. Убедитесь, что запущена служба центра **Microsoft Advanced Threat Analytics**.
1. На рабочем столе щелкните ярлык **Microsoft Advanced Threat Analytics** , чтобы подключиться к консоли ATA. Войдите под учетными данными пользователя, которые использовалась для установки центра ATA.

### <a name="set-anti-virus-exclusions"></a>Настройка исключений антивируса

После установки центра ATA исключите каталог баз данных MongoDB из содержимого, постоянно сканируемого антивирусным приложением. По умолчанию путь в базе данных — **C:\Program Files\Microsoft Advanced Threat Analytics\Center\MongoDB\bin\data**.

Кроме того, необходимо исключить следующие папки и процессы из сканирования антивирусной программой:

**Папки**  
C:\Program Files\Microsoft Advanced Threat Analytics\Center\ParentKerberosAsBloomFilters  
C:\Program Files\Microsoft Advanced Threat Analytics\Center\ParentKerberosTgsBloomFilters  
C:\Program Files\Microsoft Advanced Threat Analytics\Center\Backup  
C:\Program Files\Microsoft Advanced Threat Analytics\Center\Logs

**Процессы**  
mongod.exe  
Microsoft.Tri.Center.exe

Если вы установили ATA в другой каталог, измените пути к папкам соответствующим образом.

> [!div class="step-by-step"]
> [«Перед установкой](configure-port-mirroring.md) 
>  [Шаг 2](install-ata-step2.md)

## <a name="related-videos"></a>Видео по теме

- [Выбор правильного типа шлюза ATA](https://channel9.msdn.com/Shows/Microsoft-Security/ATA-Deployment-Choose-the-Right-Gateway-Type)
- [Обзор развертывания ATA](https://channel9.msdn.com/Shows/Microsoft-Security/Overview-of-ATA-Deployment-in-10-Minutes)

## <a name="see-also"></a>См. также

- [Руководство по развертыванию среды для подтверждения концепции ATA](/samples/browse/?redirectedfrom=TechNet-Gallery)
- [Средство изменения размера ATA](https://aka.ms/atasizingtool)
- [Обязательно ознакомьтесь с форумом ATA.](https://social.technet.microsoft.com/Forums/security/home?forum=mata)
- [Настройка сбора данных о событиях](configure-event-collection.md)
- [Предварительные требования ATA](ata-prerequisites.md)