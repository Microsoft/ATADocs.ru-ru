---
# required metadata

title: Изменение конфигурации ATA — имя сетевого адаптера для записи | Microsoft Advanced Threat Analytics
description: В этой статье описывается, как изменить имя сетевого адаптера, который настроен как сетевой адаптер для записи, без прерывания подключения шлюза ATA.
keywords:
author: rkarlin
manager: stevenpo
ms.date: 04/28/2016
ms.topic: article
ms.prod: identity-ata
ms.service: advanced-threat-analytics
ms.technology: security
ms.assetid: 3225a81e-0395-43ca-9a48-0cbe7171e5de

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: bennyl
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# Изменение конфигурации ATA — имя сетевого адаптера записи

>[!div class="step-by-step"]
[« Пароль для подключения к домену](modifying-ata-config-dcpassword.md)

## Как изменить имя сетевого адаптера для записи шлюза ATA
Если изменить имя сетевого адаптера, который в данный момент настроен как сетевой адаптер для записи, то сервер шлюза ATA не сможет запуститься. Чтобы безболезненно изменить имя, не прерывая подключение шлюза ATA, выполните следующие действия.

1.  На странице настройки шлюза ATA снимите флажок для сетевого адаптера, который требуется переименовать, и выберите вместо него другой сетевой адаптер для записи. Это может быть промежуточный сетевой адаптер или даже сетевой адаптер управления. В течение этого времени ATA не будет записывать трафик зеркально отображенного порта контроллера домена. Сохраните конфигурацию.

2.  В шлюзе ATA переименуйте сетевой адаптер, откройте панель управления и выберите пункт "Сетевые подключения".

3.  Затем вернитесь на страницу настройки шлюза ATA в консоли ATA. Обновите страницу, чтобы увидеть в списке сетевой адаптер с новым именем. Отмените выбор адаптера на шаге 1 и выберите адаптер с новым именем. Теперь сохраните конфигурацию.

Если вы переименуете сетевой адаптер без соблюдения этого процесса, шлюз ATA не запустится, а в файле журнала шлюза ATA появится ошибка Microsoft.Tri.Gateway Errors.log. В следующем примере **Запись** — исходное имя сетевого адаптера:

`Error [NetworkListener] Microsoft.Tri.Infrastructure.ExtendedException: Unavailable network adapters [UnavailableCaptureNetworkAdapterNames=Capture]`

Чтобы устранить эту проблему, присвойте сетевому адаптеру имя, которое изначально было назначено ему во время настройки ATA, а затем выполните описанные выше инструкции по изменению имени.

>[!div class="step-by-step"]
[« Пароль для подключения к домену](modifying-ata-config-dcpassword.md)


## См. также
- [Работа с консолью ATA](/advanced-threat-analytics/understand/working-with-ata-console)
- [Установка ATA](install-ata.md)
- [Для получения поддержки посетите наш форум.](https://social.technet.microsoft.com/Forums/security/en-US/home?forum=mata)


<!--HONumber=Apr16_HO2-->


