---
title: "Изменение конфигурации ATA. Сертификат IIS | Microsoft Advanced Threat Analytics"
description: "Процедура изменения сертификата, используемого службой IIS для центра ATA."
keywords: 
author: rkarlin
manager: stevenpo
ms.date: 04/28/2016
ms.topic: article
ms.prod: identity-ata
ms.service: advanced-threat-analytics
ms.technology: security
ms.assetid: e58a0390-57ef-4c68-a987-2e75e5f3d6b3
ms.reviewer: bennyl
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 8d1dedaf86031e8585cca23241aead58f7f3db4e
ms.openlocfilehash: 07888a46e26a7f87dc3b6424d97aba0813b43d02


---

# Изменение конфигурации ATA. Сертификат IIS

>[!div class="step-by-step"]
[« IP-адрес консоли ATA](modifying-ata-config-consoleip.md)
[Пароль для подключения к домену »](modifying-ata-config-dcpassword.md)

## Как изменить сертификат IIS.
В консоли можно выбрать и изменить сертификат для службы центра ATA, но изменить сертификат, используемый службой IIS, нельзя.

Чтобы изменить этот сертификат, выполните описанные ниже действия.

> [!NOTE]
> После изменения сертификата IIS перед установкой новых шлюзов ATA необходимо скачать пакет установки шлюза ATA.

Если вам нужно изменить сертификат, используемый службой IIS для центра ATA, выполните на сервере центра ATA следующие действия.

1.  Установите новый сертификат на сервере центра ATA.

2.  Откройте диспетчер IIS.

3.  Разверните узел с именем сервера, а затем — узел **Сайты**.

4.  Выберите сайт консоли Microsoft ATA и в области **Действия** щелкните **Привязки**.

    ![Пункт "Привязки" в области действий для консоли ATA](media/ATA-console-change-IP-bindings.jpg)

5.  Выберите **HTTPS** и щелкните **Изменить**.

6.  В разделе **SSL-сертификат** выберите новый сертификат.

7.  Перед установкой нового шлюза ATA скачайте пакет установки шлюза ATA.

>[!div class="step-by-step"]
[« IP-адрес консоли ATA](modifying-ata-config-consoleip.md)
[Пароль для подключения к домену »](modifying-ata-config-dcpassword.md)

## См. также
- [Работа с консолью ATA](working-with-ata-console.md)
- [Установка ATA](install-ata.md)
- [Обязательно ознакомьтесь с форумом ATA.](https://social.technet.microsoft.com/Forums/security/home?forum=mata)



<!--HONumber=Jun16_HO4-->


