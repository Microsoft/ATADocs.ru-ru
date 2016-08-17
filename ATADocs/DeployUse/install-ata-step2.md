---
title: "Установка ATA. Шаг 2 | Microsoft Advanced Threat Analytics"
description: "На втором этапе установки ATA вы настроите параметры подключения к домену на сервере центра ATA."
keywords: 
author: rkarlin
manager: stevenpo
ms.date: 04/28/2016
ms.topic: get-started-article
ms.prod: identity-ata
ms.service: advanced-threat-analytics
ms.technology: security
ms.assetid: e1c5ff41-d989-46cb-aa38-5a3938f03c0f
ms.reviewer: bennyl
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 8d1dedaf86031e8585cca23241aead58f7f3db4e
ms.openlocfilehash: 73e2eb84e1e21cbc5afcb7a100f9a67da63c66a5


---

# Установка ATA. Шаг 2

>[!div class="step-by-step"]
[« Шаг 1](install-ata-step1.md)
[Шаг 3 »](install-ata-step3.md)

## Шаг 2. Настройка общих параметров шлюза ATA
Настройки на вкладке **Общие** применяются ко всем шлюзам, которыми управляет центр ATA.

Чтобы настроить общие параметры шлюза ATA, сделайте следующее:

1.  Откройте консоль ATA и войдите в нее. Указания см. в статье [Работа с консолью ATA](working-with-ata-console.md).

2.  Щелкните значок параметров и выберите **Конфигурация**.

    ![Параметры конфигурации шлюза ATA](media/ATA-config-icon.JPG)

3.  На вкладке **Общие** в разделе **ATA Gateways** (Шлюзы ATA) введите следующие сведения и нажмите кнопку **Сохранить**.

    |Поле|Комментарии|
    |---------|------------|
    |**Имя пользователя** (указывается обязательно)|Введите имя пользователя только для чтения, например **user1**.|
    |**Пароль** (указывается обязательно)|Введите пароль для имени пользователя только для чтения, например **Parolch1k**. **Примечание**. Убедитесь, что вы указываете правильный пароль. Если указать неверный пароль, служба ATA на серверах шлюзов ATA перестанет работать.|
    |**Домен** (указывается обязательно)|Введите домен для имени пользователя только для чтения, например **contoso.com**. **Примечание**. Для домена, в котором находится пользователь, необходимо указать полное доменное имя. Например, если учетная запись пользователя находится в домене corp.contoso.com, необходимо ввести `corp.contoso.com`, а не contoso.com|
    |Автоматическое обновление всех шлюзов ATA |Если этот параметр включен, в последующих версиях выпусков при обновлении центра ATA все шлюзы ATA будут автоматически обновляться.|

    ![Параметры подключения к домену ATA (рисунок)](media/ata-domain-connectivity-user.jpg)



>[!div class="step-by-step"]
[« Шаг 1](install-ata-step1.md)
[Шаг 3 »](install-ata-step3.md)


## См. также

- [Обязательно ознакомьтесь с форумом ATA.](https://social.technet.microsoft.com/Forums/security/home?forum=mata)
- [Настройка сбора данных о событиях](configure-event-collection.md)
- [Предварительные требования для ATA](/advanced-threat-analytics/plan-design/ata-prerequisites)



<!--HONumber=Jun16_HO4-->


