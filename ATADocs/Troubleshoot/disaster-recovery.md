---
title: "Аварийное восстановление в Advanced Threat Analytics | Документация Майкрософт"
description: "Быстрое восстановление функций ATA после аварии"
keywords: 
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 02/12/2017
ms.topic: article
ms.prod: 
ms.service: advanced-threat-analytics
ms.technology: 
ms.assetid: 7620e171-76d5-4e3f-8b03-871678217a3a
ms.reviewer: bennyl
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: e3f763f7c1cce6c451a1cc969771b73543c76673
ms.openlocfilehash: 0669ccb78207dde1ede06a229af896bed0b19d28


---

*Область применения: Advanced Threat Analytics версии 1.7*



# <a name="ata-disaster-recovery"></a>Аварийное восстановление АТА
В этой статье описано, как быстро восстановить центр и функции ATA после сбоя, когда центр АТА отключен, а шлюзы АТА работают. 

>[!NOTE]
> Описанный процесс не позволяет восстановить ранее обнаруженные подозрительные действия, но возвращает центр ATA в состояние полной работоспособности. Кроме того, будет повторно запущено обучение с целью обнаружения некоторых моделей поведения. Большая часть таких обнаруженных моделей, предлагаемых ATA, будет работоспособной после восстановления центра ATA. 

## <a name="how-to-recover-your-ata-center-after-a-disaster"></a>Как восстановить центр ATA после аварии

1. Резервная копия конфигурации центра ATA записывается в файл каждый час. Найдите последнюю резервную копию конфигурации центра ATA и сохраните ее на отдельном компьютере. Полное описание того, как найти эти файлы, см. в статье [Экспорт и импорт конфигурации ATA](/advanced-threat-analytics/deploy-use/ata-configuration-file). 
2. Экспортируйте сертификат центра ATA.
    1. В диспетчере сертификатов щелкните **Сертификаты — локальный компьютер** -> **Личные** ->**Сертификаты** и выберите **Центр ATA**.
    2. Щелкните правой кнопкой мыши **Центр ATA**, а затем выберите **Все задачи** и **Экспорт**. 
     ![Сертификат центра ATA](media/ata-center-cert.png)
    3. Следуйте инструкциям, чтобы экспортировать сертификат и (обязательно) закрытый ключ.

    > [!NOTE] 
    > Если экспортировать закрытый ключ не удается, создайте другой сертификат и разверните его в ATA, как описано в статье [Изменение конфигурации ATA. Сертификат центра ATA](/advanced-threat-analytics/deploy-use/modifying-ata-config-centercert), а затем экспортируйте его. 

    4. Создайте резервную копию экспортированного файла сертификата на отдельном компьютере.
3. Создайте сервер Windows Server, используя те же IP-адрес и имя компьютера, как и для предыдущего сервера с центром ATA.
4. Импортируйте на новый сервер резервную копию сертификата, созданную на шаге 2.
5. Следуйте инструкциям, чтобы [развернуть центр ATA](/advanced-threat-analytics/deploy-use/install-ata-step1) на только что созданном сервере Windows Server. Развертывать шлюзы ATA снова не нужно. При появлении соответствующего запроса укажите сертификат, используемый на шаге 2. 
![Восстановление центра ATA](media/ata-center-restore.png)
6. Импортируйте резервную конфигурацию центра ATA:
    1. Удалите из MongoDB документ с системным профилем центра ATA по умолчанию: 
        1. Перейдите в каталог **C:\Program Files\Microsoft Advanced Threat Analytics\Center\MongoDB\bin**. 
        2. Выполнить `mongo.exe` 
        3. Выполните следующую команду, чтобы удалить системный профиль по умолчанию: `db.SystemProfile.remove({})`.
    2. Выполните команду `mongoimport.exe --db ATA --collection SystemProfile --file "<SystemProfile.json backup file>" --upsert`, используя файл резервной копии из шага 1.</br>
    Полное описание того, как найти и импортировать файлы резервной копии, см. в статье [Экспорт и импорт конфигурации ATA](/advanced-threat-analytics/deploy-use/ata-configuration-file). 
    3. Завершив импорт, выполните следующую команду, чтобы удалить некоторые стандартные средства обнаружения и профилирования (сбросить их перед использованием новой среды): `db.SystemProfile.remove({$or:[{"_t":"DetectorProfile"}, "_t":"DirectoryServicesSystemProfile"}]}) `.
    4. Откройте консоль ATA. Вы должны увидеть все связанные шлюзы ATA на вкладке с конфигурациями и шлюзами. 
    5. Обязательно определите **пользователя службы каталогов** и выберите **синхронизатор контроллера домена**. 






## <a name="see-also"></a>См. также
- [Предварительные требования ATA](/advanced-threat-analytics/plan-design/ata-prerequisites)
- [Планирование производительности ATA](/advanced-threat-analytics/plan-design/ata-capacity-planning)
- [Настройка сбора данных о событиях](/advanced-threat-analytics/deploy-use/configure-event-collection)
- [Настройка пересылки событий Windows](/advanced-threat-analytics/deploy-use/configure-event-collection#configuring-windows-event-forwarding)
- [Ознакомьтесь с форумом ATA.](https://social.technet.microsoft.com/Forums/security/home?forum=mata)



<!--HONumber=Feb17_HO3-->


