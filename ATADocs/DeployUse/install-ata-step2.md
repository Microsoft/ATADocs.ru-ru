---
# required metadata

title: Установка ATA. Шаг 2 | Microsoft Advanced Threat Analytics
description: На втором этапе установки ATA вы настроите параметры подключения к домену на сервере центра ATA.
keywords:
author: rkarlin
manager: stevenpo
ms.date: 04/28/2016
ms.topic: get-started-article
ms.prod: identity-ata
ms.service: advanced-threat-analytics
ms.technology: security
ms.assetid: e1c5ff41-d989-46cb-aa38-5a3938f03c0f

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: bennyl
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# Установка ATA. Шаг 2

>[!div class="step-by-step"]
[« Шаг 1](install-ata-step1.md)
[Шаг 3 »](install-ata-step3.md)

## Шаг 2. Настройка параметров подключения для домена шлюза ATA.
Настройки в разделе параметров подключения к домену применяются ко всем шлюзам, которыми управляет центр ATA.

Чтобы настроить параметры подключения к домену, сделайте на сервере центра ATA следующее.

1.  Откройте консоль ATA и войдите в нее. Инструкции см. в статье [Работа с консолью ATA](/advanced-threat-analytics/understand/working-with-ata-console).

2.  При первом входе в консоль ATA после установки центра ATA вы автоматически попадете на страницу конфигурации шлюзов ATA. Если в будущем вам потребуется изменить какие-либо настройки, щелкните значок параметров и выберите пункт **Конфигурация**.

    ![Параметры конфигурации шлюза ATA](media/ATA-config-icon.JPG)

3.  На странице **Шлюзы** щелкните **Параметры подключения к домену**, введите приведенные ниже сведения и нажмите кнопку **Сохранить**.

    |Поле|Комментарии|
    |---------|------------|
    |**Имя пользователя** (указывается обязательно)|Введите имя пользователя только для чтения, например **user1**.|
    |**Пароль** (указывается обязательно)|Введите пароль для имени пользователя только для чтения, например **Parolch1k**. **Примечание**. Убедитесь, что вы указываете правильный пароль. Если указать неверный пароль, служба ATA на серверах шлюзов ATA перестанет работать.|
    |**Домен** (указывается обязательно)|Введите домен для имени пользователя только для чтения, например **contoso.com**. **Примечание**. Для домена, в котором находится пользователь, необходимо указать полное доменное имя. Например, если учетная запись пользователя находится в домене corp.contoso.com, необходимо ввести `corp.contoso.com`, а не contoso.com|
    ![Параметры подключения к домену ATA (рисунок)](media/ATA-Domain-Connectivity-User.JPG)


>[!div class="step-by-step"]
[« Шаг 1](install-ata-step1.md)
[Шаг 3 »](install-ata-step3.md)


## См. также

- [Для получения поддержки посетите наш форум.](https://social.technet.microsoft.com/Forums/security/en-US/home?forum=mata)
- [Настройка сбора данных о событиях](/advanced-threat-analytics/plandesign/configure-event-collection)
- [Предварительные требования для ATA](/advanced-threat-analytics/plandesign/ata-prerequisites)


<!--HONumber=Apr16_HO2-->


