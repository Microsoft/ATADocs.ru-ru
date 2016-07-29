---
title: "Изменение конфигурации ATA. Пароль для подключения к домену | Microsoft ATA"
description: "Процедура изменения пароля для подключения к домену на шлюзе ATA."
keywords: 
author: rkarlin
manager: mbaldwin
ms.date: 04/28/2016
ms.topic: article
ms.prod: 
ms.service: advanced-threat-analytics
ms.technology: 
ms.assetid: 4a25561b-a5ed-44aa-9b72-366976b3c72a
ms.reviewer: bennyl
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: f13750f9cdff98aadcd59346bfbbb73c2f3a26f0
ms.openlocfilehash: 7b8904bcb379004b2038e6b9a14c87c3914f1e1f


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



<!--HONumber=Jul16_HO4-->


