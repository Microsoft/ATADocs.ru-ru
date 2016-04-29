---
# required metadata

title: Установка ATA | Microsoft Advanced Threat Analytics
description: На заключительном этапе установки ATA нужно настроить подсети с краткосрочным использованием IP-адресов и пользователя Honeytoken.
keywords:
author: rkarlin
manager: stevenpo
ms.date: 04/28/2016
ms.topic: get-started-article
ms.prod: identity-ata
ms.service: advanced-threat-analytics
ms.technology: security
ms.assetid: 8980e724-06a6-40b0-8477-27d4cc29fd2b

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: bennyl
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# Установка ATA. Шаг 6

>[!div class="step-by-step"]
[« Шаг 5](install-ata-step5.md)

## Шаг 6. Настройка пользователя Honeytoken и подсетей с краткосрочным использованием IP-адресов
В подсетях с краткосрочным использованием IP-адресов назначенные IP-адреса быстро меняются, буквально через несколько секунд или минут (например, IP-адреса для VPN и Wi-Fi). Чтобы указать список таких подсетей (которые используются в вашей организации), сделайте вот что:

1.  В консоли ATA на компьютере шлюза ATA щелкните значок параметров и выберите пункт **Конфигурация**.

    ![Параметры конфигурации ATA](media/ATA-config-icon.JPG)

2.  В разделе **Обнаружение** укажите подсети с краткосрочным использованием IP-адресов с помощью косой черты, например `192.168.0.0/24`, и щелкните значок плюса.

3.  В качестве SID учетной записи Honeytoken укажите SID учетной записи пользователя, у которой не будет сетевой активности. Затем щелкните значок плюса. Например, введите `S-1-5-21-72081277-1610778489-2625714895-10511`.

    > [!NOTE]
    > Чтобы найти SID пользователя, выполните командлет Windows PowerShell `Get-ADUser UserName`.

4.  Настройте исключения. Некоторые IP-адреса можно исключить из проверки на предмет определенных подозрительных действий. Дополнительные сведения см. в статье [Работа с параметрами обнаружения ATA](working-with-detection-settings.md).

5.  Нажмите кнопку **Сохранить**.

![Сохранить изменения](media/ATA-VPN-Subnets.JPG)

На этом развертывание Microsoft Advanced Threat Analytics завершено.

Просмотрите временную шкалу атак, чтобы увидеть обнаруженные подозрительные действия, найти пользователей или компьютеры и изучить их профили.

Помните, что для создания поведенческих профилей решению ATA требуется как минимум три недели. В течение первых трех недель вы не будете видеть никаких подозрительных действий.


>[!div class="step-by-step"]
[« Шаг 5](install-ata-step5.md)


## См. также

- [Для получения поддержки посетите наш форум.](https://social.technet.microsoft.com/Forums/security/en-US/home?forum=mata)
- [Настройка сбора данных о событиях](/advanced-threat-analytics/plandesign/configure-event-collection)
- [Предварительные требования для ATA](/advanced-threat-analytics/plandesign/ata-prerequisites)


<!--HONumber=Apr16_HO2-->


