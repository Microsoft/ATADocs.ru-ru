---
title: "Аварийное восстановление в Advanced Threat Analytics | Документация Майкрософт"
description: "Быстрое восстановление функций ATA после аварии"
keywords: 
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 3/7/2017
ms.topic: article
ms.prod: 
ms.service: advanced-threat-analytics
ms.technology: 
ms.assetid: 7620e171-76d5-4e3f-8b03-871678217a3a
ms.reviewer: arzinger
ms.suite: ems
ms.openlocfilehash: ce06038a3c3f2e5a6f2a5d57ad814ab8393c0b0c
ms.sourcegitcommit: 470675730967e0c36ebc90fc399baa64e7901f6b
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/30/2017
---
*Применяется к Advanced Threat Analytics версии 1.8*



# <a name="ata-disaster-recovery"></a>Аварийное восстановление АТА
В этой статье описано, как быстро восстановить центр и функции ATA после сбоя, когда центр АТА отключен, а шлюзы АТА работают. 

>[!NOTE]
> Описанный процесс не позволяет восстановить ранее обнаруженные подозрительные действия, но возвращает центр ATA в состояние полной работоспособности. Кроме того, будет повторно запущено обучение с целью обнаружения некоторых моделей поведения. Большая часть таких обнаруженных моделей, предлагаемых ATA, будет работоспособной после восстановления центра ATA. 

## <a name="back-up-your-ata-center-configuration"></a>Резервное копирование конфигурации центра ATA

1. Резервная копия конфигурации центра ATA записывается в файл каждый час. Найдите последнюю резервную копию конфигурации центра ATA и сохраните ее на отдельном компьютере. Полное описание того, как найти эти файлы, см. в статье [Экспорт и импорт конфигурации ATA](/advanced-threat-analytics/deploy-use/ata-configuration-file). 
2. Экспортируйте сертификат центра ATA.
    1. В диспетчере сертификатов щелкните **Сертификаты — локальный компьютер** -> **Личные** ->**Сертификаты** и выберите **Центр ATA**.
    2. Щелкните правой кнопкой мыши **Центр ATA**, а затем выберите **Все задачи** и **Экспорт**. 
     ![Сертификат центра ATA](media/ata-center-cert.png)
    3. Следуйте инструкциям, чтобы экспортировать сертификат и (обязательно) закрытый ключ.
    4. Создайте резервную копию экспортированного файла сертификата на отдельном компьютере.

  > [!NOTE] 
  > Если экспортировать закрытый ключ не удается, создайте другой сертификат и разверните его в ATA, как описано в статье [Изменение конфигурации ATA. Сертификат центра ATA](/advanced-threat-analytics/deploy-use/modifying-ata-config-centercert), а затем экспортируйте его. 

## <a name="recover-your-ata-center"></a>Восстановление центра ATA

1. Создайте сервер Windows Server, используя те же IP-адрес и имя компьютера, как и для предыдущего сервера с центром ATA.
4. Импортируйте на новый сервер резервную копию сертификата, созданную на предыдущем шаге.
5. Следуйте инструкциям, чтобы [развернуть центр ATA](/advanced-threat-analytics/deploy-use/install-ata-step1) на только что созданном сервере Windows Server. Развертывать шлюзы ATA снова не нужно. При появлении запроса на сертификат укажите сертификат, экспортированный при резервном копировании конфигурации центра ATA. 
![Восстановление центра ATA](media/disaster-recovery-deploymentss.png)
6. Импортируйте резервную конфигурацию центра ATA:
    1. Удалите из MongoDB документ с системным профилем центра ATA по умолчанию: 
        1. Перейдите в каталог **C:\Program Files\Microsoft Advanced Threat Analytics\Center\MongoDB\bin**. 
        2. Выполнить `mongo.exe` 
        3. Выполните следующую команду, чтобы удалить системный профиль по умолчанию: `db.SystemProfile.remove({})`
    2. Выполните команду `mongoimport.exe --db ATA --collection SystemProfile --file "<SystemProfile.json backup file>" --upsert`, используя файл резервной копии из шага 1.</br>
    Полное описание того, как найти и импортировать файлы резервной копии, см. в статье [Экспорт и импорт конфигурации ATA](/advanced-threat-analytics/deploy-use/ata-configuration-file). 
    3. Откройте консоль ATA. Вы должны увидеть все связанные шлюзы ATA на вкладке с конфигурациями и шлюзами. 
    5. Обязательно определите [**пользователя служб каталогов**](/advanced-threat-analytics/deploy-use/install-ata-step2) и выберите [**синхронизатор контроллера домена**](/advanced-threat-analytics/deploy-use/install-ata-step5). 






## <a name="see-also"></a>См. также
- [Предварительные требования ATA](/advanced-threat-analytics/plan-design/ata-prerequisites)
- [Планирование производительности ATA](/advanced-threat-analytics/plan-design/ata-capacity-planning)
- [Настройка сбора данных о событиях](/advanced-threat-analytics/deploy-use/configure-event-collection)
- [Настройка пересылки событий Windows](/advanced-threat-analytics/deploy-use/configure-event-collection#configuring-windows-event-forwarding)
- [Ознакомьтесь с форумом ATA.](https://social.technet.microsoft.com/Forums/security/home?forum=mata)
