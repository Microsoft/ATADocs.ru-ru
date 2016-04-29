---
# required metadata

title: Изменение конфигурации ATA. Пароль для подключения к домену | Microsoft Advanced Threat Analytics
description: Процедура изменения пароля для подключения к домену на шлюзе ATA.
keywords:
author: rkarlin
manager: stevenpo
ms.date: 04/28/2016
ms.topic: article
ms.prod: identity-ata
ms.service: advanced-threat-analytics
ms.technology: security
ms.assetid: 4a25561b-a5ed-44aa-9b72-366976b3c72a

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: bennyl
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# Изменение конфигурации ATA. Пароль для подключения к домену

>[!div class="step-by-step"]
[« Сертификат IIS](modifying-ata-config-iiscert.md)
[Имя сетевого адаптера для записи »](modifying-ata-config-nicname.md)

## Изменение пароля для подключения к домену
Изменяя пароль для подключения к домену, указывайте правильный пароль. Если указать неправильный пароль, служба ATA на шлюзах ATA перестанет работать.

Если у вас возникло подозрение, что служба перестала работать, на шлюзе ATA откройте файл Microsoft.Tri.Gateway-Errors.log и найдите в нем такую строку:
`The supplied credential is invalid.`

Чтобы исправить эту ошибку, в шлюзе ATA измените пароль для подключения к домену, как описано ниже.

1.  Откройте на шлюзе ATA консоль ATA.

2.  На панели инструментов щелкните значок параметров и выберите пункт **Конфигурация**.

    ![Значок параметров конфигурации ATA](media/ATA-config-icon.JPG)

3.  Выберите **Шлюз ATA**.

    ![Изменение пароля для шлюзов ATA (рисунок)](media/ATA-GW-change-DC-password.JPG)

4.  В разделе **Параметры подключения к домену** измените пароль.

5.  Нажмите кнопку **Сохранить**.

6.  После изменения пароля убедитесь, что служба шлюза ATA работает на всех шлюзах ATA.

>[!div class="step-by-step"]
[« Сертификат IIS](modifying-ata-config-iiscert.md)
[Имя сетевого адаптера для записи »](modifying-ata-config-nicname.md)

## См. также
- [Работа с консолью ATA](/advanced-threat-analytics/understand/working-with-ata-console)
- [Установка ATA](install-ata.md)
- [Для получения поддержки посетите наш форум.](https://social.technet.microsoft.com/Forums/security/en-US/home?forum=mata)


<!--HONumber=Apr16_HO2-->


