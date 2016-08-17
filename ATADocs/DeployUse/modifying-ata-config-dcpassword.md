---
title: "Изменение конфигурации ATA. Пароль для подключения к домену | Microsoft Advanced Threat Analytics"
description: "Процедура изменения пароля для подключения к домену на шлюзе ATA."
keywords: 
author: rkarlin
manager: stevenpo
ms.date: 04/28/2016
ms.topic: article
ms.prod: identity-ata
ms.service: advanced-threat-analytics
ms.technology: security
ms.assetid: 4a25561b-a5ed-44aa-9b72-366976b3c72a
ms.reviewer: bennyl
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 8d1dedaf86031e8585cca23241aead58f7f3db4e
ms.openlocfilehash: df1dbed75ad0c88de5a6c51d2e5d7e521a2577c4


---

# Изменение конфигурации ATA. Пароль для подключения к домену

>[!div class="step-by-step"]
[« Сертификат IIS](modifying-ata-config-iiscert.md)


## Изменение пароля для подключения к домену
Изменяя пароль для подключения к домену, указывайте правильный пароль. Если указать неправильный пароль, служба ATA на шлюзах ATA перестанет работать.

Если у вас возникло подозрение, что служба перестала работать, на шлюзе ATA откройте файл Microsoft.Tri.Gateway-Errors.log и найдите в нем такую строку:
`The supplied credential is invalid.`

Чтобы исправить эту ошибку, в шлюзе ATA измените пароль для подключения к домену, как описано ниже.

1.  Откройте на шлюзе ATA консоль ATA.

2.  На панели инструментов щелкните значок параметров и выберите пункт **Конфигурация**.

    ![Значок параметров конфигурации ATA](media/ATA-config-icon.JPG)

3.  Выберите пункт **Общие**.

    ![Изменение пароля для шлюзов ATA (рисунок)](media/ATA-GW-change-DC-password.JPG)

4.  В разделе **Общие** измените пароль.

5.  Нажмите кнопку **Сохранить**.

6.  После изменения пароля убедитесь, что служба шлюза ATA работает на всех шлюзах ATA.

>[!div class="step-by-step"]
[« Сертификат IIS](modifying-ata-config-iiscert.md)

## См. также
- [Работа с консолью ATA](working-with-ata-console.md)
- [Установка ATA](install-ata.md)
- [Обязательно ознакомьтесь с форумом ATA.](https://social.technet.microsoft.com/Forums/security/home?forum=mata)



<!--HONumber=Jun16_HO4-->


