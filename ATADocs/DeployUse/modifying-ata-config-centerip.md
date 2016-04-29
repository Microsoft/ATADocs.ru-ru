---
# required metadata

title: Изменение конфигурации ATА. IP-адрес центра АТА | Microsoft Advanced Threat Analytics
description: Описание способов изменения IP-адреса, порта или сертификата центра обработки ATA.
keywords:
author: rkarlin
manager: stevenpo
ms.date: 04/28/2016
ms.topic: article
ms.prod: identity-ata
ms.service: advanced-threat-analytics
ms.technology: security
ms.assetid: 93b27f15-f7e5-49bb-870a-d81d09dfe9fc

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: bennyl
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# Изменение конфигурации АТА. IP-адрес центра АТА

>[!div class="step-by-step"]
[Сертификат центра ATA »](modifying-ata-config-centercert.md)

После первоначального развертывания необходимо аккуратно внести изменения в центр ATA. При обновлении IP-адреса, порта или сертификата используйте следующую процедуру.

## Изменение IP-адреса, используемого сервером центра ATA
Если вам нужно изменить IP-адрес, порт или сертификат центра ATA, учитывайте следующие факторы.

Шлюзы ATA локально хранят IP-адрес центра ATA, к которому они подключаются. Шлюзы регулярно подключаются к центру ATA и подтягивают изменения конфигурации. Способ подключения шлюзов ATA к центру ATA следует изменять в два этапа.

-   Первый этап — изменение IP-адреса и порта, используемых центром ATA. На этом этапе центр ATA по-прежнему ведет прослушивание исходного IP-адреса. Когда шлюз ATA в следующий раз будет синхронизировать свою конфигурацию, он будет иметь два IP-адреса для центра ATA. Пока шлюз ATA может подключаться с помощью исходного IP-адреса, новый IP-адрес и порт использоваться не будут.

-   Второй этап — по завершении синхронизации обновленной конфигурации на всех шлюзах АТА вы сможете активировать новый IP-адрес и порт, которые прослушивает центр АТА. После активации нового IP-адреса служба центра ATA будет привязана к нему. Шлюзы ATA не смогут подключиться к исходному адресу и теперь будут пытаться подключиться к новому IP-адресу центра ATA. После подключения к центру ATA с помощью нового IP-адреса шлюз ATA подтянет последнюю конфигурацию и будет использовать один IP-адрес для центра ATA. (Пока вы снова не измените IP-адрес).

> [!NOTE]
> -   Если на первом этапе шлюз ATA работал в автономном режиме и не получил обновленную конфигурацию, вам нужно будет вручную обновить файл конфигурации JSON на шлюзе ATA.
> -   Если на сервере центра ATA установлен новый IP-адрес, можно выбрать его из списка IP-адресов при внесении изменений. Если по какой-то причине невозможно установить IP-адрес на сервере центра ATA, вы можете выбрать пользовательский IP-адрес и добавить его вручную. Вы не сможете активировать новый IP-адрес, пока IP-адрес не будет установлен на сервере.
> -   Если необходимо развернуть новый шлюз ATA после активации нового IP-адреса, необходимо загрузить пакет установки шлюза ATA еще раз.

1.  Откройте консоль ATA.

2.  На панели инструментов щелкните значок параметров и выберите пункт **Конфигурация**.

    ![Значок параметров конфигурации ATA](media/ATA-config-icon.JPG)

3.  Выберите **Центр ATA**.

4.  В разделе **IP-адрес службы центра ATA: порт** выберите один из существующих IP-адресов или выберите **Добавить пользовательский IP-адрес** и введите IP-адрес.

5.  Нажмите кнопку **Сохранить**.

6.  Вы увидите уведомление о том, сколько шлюзов ATA синхронизировано с последней конфигурацией.

    ![Изображение синхронизированных шлюзов центра ATA](media/ATA-chge-IP-after-clicking-save.png)

7.  Когда все шлюзы ATA будут синхронизированы, нажмите кнопку **Активировать**, чтобы активировать новый IP-адрес.

    > [!NOTE]
    > Если вы ввели пользовательский IP-адрес, вы не сможете нажать кнопку **Активировать**, пока IP-адрес не будет установлен в центре ATA.

8.  Убедитесь, что после активации изменений все шлюзы ATA смогут синхронизировать свои конфигурации. На панели уведомлений будет видно, сколько шлюзов ATA успешно синхронизировали свои конфигурации.

>[!div class="step-by-step"]
[Изменение сертификата центра ATA »](modifying-ata-config-centercert.md)


## См. также
- [Работа с консолью ATA](/advanced-threat-analytics/understand/working-with-ata-console)
- [Установка ATA](install-ata.md)
- [Для получения поддержки посетите наш форум.](https://social.technet.microsoft.com/Forums/security/en-US/home?forum=mata)


<!--HONumber=Apr16_HO2-->

