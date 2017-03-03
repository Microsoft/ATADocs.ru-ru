---
title: "Изменение конфигурации Advanced Threat Analytics с использованием пароля для подключения к домену | Документация Майкрософт"
description: "Процедура изменения пароля для подключения к домену на шлюзе ATA."
keywords: 
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 1/23/2017
ms.topic: article
ms.prod: 
ms.service: advanced-threat-analytics
ms.technology: 
ms.assetid: 4a25561b-a5ed-44aa-9b72-366976b3c72a
ms.reviewer: bennyl
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: b28cb3a0da844b7c460c03726222bc775a9e47da
ms.openlocfilehash: fce61880e1d47ac006ca919992d1766e5ef8eca3


---

*Область применения: Advanced Threat Analytics версии 1.7*



# <a name="change-ata-configuration---domain-connectivity-password"></a>Изменение конфигурации ATA. Пароль для подключения к домену

>[!div class="step-by-step"]
[" URL-адрес консоли ATA](modifying-ata-config-consoleurl.md)


## <a name="change-the-domain-connectivity-password"></a>Изменение пароля для подключения к домену
Изменяя пароль для подключения к домену, указывайте правильный пароль. Если указать неправильный пароль, служба ATA на шлюзах ATA перестанет работать.

В таком случае откройте на шлюзе ATA файл Microsoft.Tri.Gateway-Errors.log и найдите в нем такую строку: `The supplied credential is invalid.`.

Чтобы исправить эту ошибку, в центре ATA измените пароль для подключения к домену, как описано ниже.

1.  Откройте в центре ATA консоль ATA.

2.  На панели инструментов щелкните значок параметров и выберите пункт **Конфигурация**.

    ![Значок параметров конфигурации ATA](media/ATA-config-icon.JPG)

3.  Выберите **Directory Services** (Службы каталогов).

    ![Изменение пароля для шлюзов ATA (рисунок)](media/ATA-GW-change-DC-password.png)

4.  В разделе **Password** (Пароль) измените пароль.

    Если у центра ATA есть подключение к домену, то, чтобы проверить учетные данные, нажмите кнопку **Test Connection** (Проверить подключение).

5.  Нажмите кнопку **Сохранить**.

6.  После изменения пароля убедитесь, что служба шлюза ATA работает на всех шлюзах ATA.

>[!div class="step-by-step"]
[" URL-адрес консоли ATA](modifying-ata-config-consoleurl.md)

## <a name="see-also"></a>См. также
- [Работа с консолью ATA](working-with-ata-console.md)
- [Ознакомьтесь с форумом ATA.](https://social.technet.microsoft.com/Forums/security/home?forum=mata)



<!--HONumber=Feb17_HO1-->


