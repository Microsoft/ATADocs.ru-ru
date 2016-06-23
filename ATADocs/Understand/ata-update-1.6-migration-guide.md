---
# required metadata

title: Руководство по миграции на обновленную версию ATA 1.6 | Microsoft Advanced Threat Analytics
description: Процедуры по обновлению ATA до версии 1.6
keywords:
author: rkarlin
manager: stevenpo
ms.date: 04/28/2016
ms.topic: article
ms.prod: identity-ata
ms.service: advanced-threat-analytics
ms.technology: security
ms.assetid: fb65eb41-b215-4530-93a2-0b8991f4e980

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: bennyl
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# Руководство по миграции на обновленную версию ATA 1.6
При обновлении ATA до версии 1.6 появляются следующие улучшения:

-   новые обнаружения;

-   улучшения имеющихся обнаружений;

-   упрощенный шлюз ATA;

-   автоматические обновления;

-   улучшение производительности центра ATA;

-   более низкие требования к хранению;

-   поддержка IBM QRadar.

## Обновление ATA до версии 1.6
> [!NOTE] Если в вашей среде решение ATA не установлено, скачайте его полную версию, включая версию 1.6, и выполните стандартную процедуру установки, описанную в статье [Установка ATA](/advanced-threat-analytics/deploy-use/install-ata).

Если в вашей среде уже развернута версия ATA 1.5, эта процедура поможет вам выполнить действия, необходимые для обновления развертывания.

> [!NOTE] Невозможно установить ATA версии 1.6 непосредственно поверх ATA версии 1.4. Сначала следует установить ATA версии 1.5. Если вы случайно попытались установить ATA 1.6, не устанавливая ATA 1.5, появится ошибка: **На компьютере уже установлена более новая версия.** Перед установкой ATA версии 1.5 необходимо удалить оставшиеся файлы ATA 1.6 с компьютера, даже если произошел сбой установки.

Выполните следующие действия, чтобы установить обновление для ATA версии 1.6:

1. Убедитесь, что перед началом обновления вы выполнили процедуру для обработки [сбоя миграции при обновлении до ATA версии 1.6](whats-new-version-1.6#Migration-failure-when-updating-from-ATA-1.5)
2. Убедитесь, что у вас достаточно свободного места для обновления. Вы можете выполнить установку до проверки готовности, чтобы оценить, сколько свободного места требуется, а затем выделить место и перезапустить обновление. Обновление использует по меньшей мере 20 % размера базы данных. Дополнительные сведения см. в разделе [Планирование емкости ATA](/advanced-threat-analytics/plan-design/ata-capacity-planning).
1.  [Скачайте обновление 1.6.](http://www.microsoft.com/en-us/evalcenter/evaluate-microsoft-advanced-threat-analytics)<br>
В этой версии файл установки (Setup.exe центра Microsoft ATA) используется как для установки развертывания ATA, так и для обновления имеющихся развертываний.

2.  Обновите центр ATA.

3.  Скачайте обновленный пакет шлюза ATA.

4.  Обновите шлюзы АТА.

    > [!IMPORTANT] Обновите все шлюзы ATA, чтобы убедиться, что ATA правильно работает.

### Шаг 1. Обновление центра ATA

1.  Создайте резервную копию базы данных (необязательно).

    -   Если центр АТА работает как виртуальная машина и вы хотите создать контрольную точку, сначала отключите виртуальную машину.

    -   Если центр ATA работает на физическом сервере, следуйте рекомендованной процедуре, чтобы выполнить [резервное копирование MongoDB](https://docs.mongodb.org/manual/core/backups/).

2.  Запустите файл установки Setup.exe центра Microsoft ATA и следуйте указаниям в окнах, чтобы установить обновление.

    1.  Для версии ATA 1.6 требуется платформа .NET Framework 4.6.1. Если этой платформы нет в системе, она установится в рамках установки решения ATA.<br>
    > [!NOTE]Для установки платформы .NET Framework 4.6.1 может потребоваться перезагрузка сервера. Установка ATA продолжится только после перезагрузки сервера.
5.  На странице **приветствия** выберите язык и нажмите кнопку **Далее**.

    6.  Прочтите лицензионное соглашение и, если вы принимаете условия, нажмите кнопку **Далее**.

    7.  Теперь можно использовать Центр обновления Майкрософт для ATA, чтобы быть в курсе обновлений.  На странице Центра обновления Майкрософт установите флажок **Использовать Центр обновления Майкрософт при проверке наличия обновлений (рекомендуется)**.
    ![Постоянное обновление ATA ](media/ata_ms_update.png) Таким образом параметры Windows будут разрешать обновление для других продуктов Майкрософт, включая ATA, как показано ниже. 
     ![Изображение. Настройка автоматического обновления Windows](media/ata_installupdatesautomatically.png)

    8.  Перед началом установки ATA выполнит проверку готовности. Просмотрите результаты проверки, чтобы убедиться, что необходимые компоненты настроены и у вас есть по крайней мере минимальный объем места на диске. 
    ![Изображение. Проверка готовности ATA](media/ata_install_readinesschecks.png)

    3.  Нажмите кнопку **Обновить**. После нажатия кнопки "Обновить" ATA переходит в автономный режим до завершения обновления.

4.  После обновления центра ATA вы получите отчет о том, что шлюзы ATA устарели.

    ![Изображение устаревших шлюзов](media/ATA-center-outdated.png)

> [!IMPORTANT]
> - Обновите все шлюзы ATA, чтобы решение ATA работало правильно.

### Шаг 2. Скачивание пакета установки шлюза ATA
Настроив параметры подключения к домену, скачайте пакет установки шлюза ATA.

Чтобы скачать пакет шлюза ATA, сделайте вот что:

1.  Удалите все предыдущие версии ранее загруженного пакета шлюза ATA.

2.  На компьютере шлюза ATA откройте браузер и введите IP-адрес, настроенный в центре ATA для консоли ATA. Когда откроется консоль ATA, щелкните значок параметров и выберите **Конфигурация**.

    ![Значок параметров конфигурации](media/ATA-config-icon.JPG)

3.  На вкладке **Шлюзы ATA** щелкните **Скачать программу установки шлюза ATA**.

4.  Сохраните пакет на локальном компьютере.

ZIP-файл содержит:

-   установщик шлюза ATA;

-   файл конфигурации с данными для подключения к центру ATA.

### Шаг 3. Обновление шлюзов АТА

1.  На каждом шлюзе ATA извлеките файлы из пакета шлюза ATA и запустите файл **Setup.exe шлюза Microsoft ATA**.

    > [!NOTE] Вы можете также использовать этот пакет шлюза ATA для установки новых шлюзов ATA.

2.  Ранее указанные параметры будут сохранены, а установка может занять несколько минут, после чего будет выполнен перезапуск службы.

3.  Повторите этот шаг для всех остальных развернутых шлюзов АТА.

> [!NOTE] После успешного обновления шлюза ATA устаревшие уведомления для конкретного шлюза ATA будут разрешены.

Вы будете знать, что все шлюзы ATA обновлены, когда все шлюзы ATA сообщат о своей успешной синхронизации и перестанет отображаться сообщение о том, что доступен обновленный пакет шлюза АТА.

![Изображение обновленных шлюзов](media/ATA-gw-updated.png)


## См. также

- [Обязательно ознакомьтесь с форумом ATA.](https://social.technet.microsoft.com/Forums/security/en-US/home?forum=mata)


<!--HONumber=May16_HO4-->

