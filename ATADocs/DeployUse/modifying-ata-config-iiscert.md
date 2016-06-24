---
# required metadata

title: Изменение конфигурации ATA. Сертификат IIS | Microsoft Advanced Threat Analytics
description: Процедура изменения сертификата, используемого службой IIS для центра ATA.
keywords:
author: rkarlin
manager: stevenpo
ms.date: 04/28/2016
ms.topic: article
ms.prod: identity-ata
ms.service: advanced-threat-analytics
ms.technology: security
ms.assetid: e58a0390-57ef-4c68-a987-2e75e5f3d6b3

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: bennyl
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# Изменение конфигурации ATA. Сертификат IIS

>[!div class="step-by-step"]
[« Изменение IP-адреса консоли ATA](modifying-ata-config-consoleip.md)
[Пароль для подключения к домену »](modifying-ata-config-dcpassword.md)

## Изменение сертификата IIS
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
[« Изменение IP-адреса консоли ATA](modifying-ata-config-consoleip.md)
[Пароль для подключения к домену »](modifying-ata-config-dcpassword.md)

## См. также
- [Работа с консолью ATA](/advanced-threat-analytics/understand/working-with-ata-console)
- [Установка ATA](install-ata.md)
- [Для получения поддержки посетите наш форум.](https://social.technet.microsoft.com/Forums/security/en-US/home?forum=mata)


<!--HONumber=Apr16_HO2-->


