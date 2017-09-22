---
title: "Установка Advanced Threat Analytics. Шаг 7 | Документация Майкрософт"
description: "На этом этапе установки ATA интегрируется VPN."
keywords: 
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 09/19/2017
ms.topic: get-started-article
ms.prod: 
ms.service: advanced-threat-analytics
ms.technology: 
ms.assetid: e0aed853-ba52-46e1-9c55-b336271a68e7
ms.reviewer: bennyl
ms.suite: ems
ms.openlocfilehash: 384384ebd6b6fadcaa5636200ccd08667d9c41a5
ms.sourcegitcommit: 34c3d6f56f175994b672842c7576040956ceea69
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/19/2017
---
*Применяется к Advanced Threat Analytics версии 1.8*



# <a name="install-ata---step-7"></a>Установка ATA. Шаг 7

>[!div class="step-by-step"]
[« Шаг 5](install-ata-step5.md)
[Шаг 8 »](install-ata-step7.md)

## <a name="step-7-integrate-vpn"></a>Шаг 7. Интеграция VPN

### <a name="configuring-vpn"></a>Настройка VPN

ATA собирает данные VPN. Они помогают профилировать расположения, из которых компьютеры подключаются к сети, и подготовиться к установке чрезмерного числа VPN-подключений.

Чтобы настроить данные VPN в ATA, сделайте следующее:

1. Перейдите к элементу **Конфигурация** и щелкните вкладку **VPN**.

2. Введите **общий секрет учетной записи** для сервера RADIUS. Чтобы получить общий секрет, ознакомьтесь с документацией по VPN.

 ![Настройка VPN в ATA](media/vpn.png)

3.  Когда эта функция включена, все шлюзы ATA и упрощенные шлюзы прослушивают порт 1813 на предмет учетных событий RADIUS. 

4.  Учетные события RADIUS в VPN должны перенаправляться в любой шлюз ATA и упрощенный шлюз ATA после его настройки.

5.  Шлюз ATA получает события VPN и отправляет их в центр ATA для обработки. Центру ATA требуется подключение к Интернету для HTTPS-порта 443, чтобы разрешить внешние IP-адреса в событиях VPN в их географическом расположении.

Вызов для разрешения внешних IP-адресов в расположении является анонимным. Личный идентификатор в этом вызове не отправляется.

Поддерживаются следующие поставщики VPN.
- Microsoft
- F5
- Check Point
- Cisco ASA




>[!div class="step-by-step"]
[« Шаг 6](install-ata-step5.md)
[Шаг 8 »](install-ata-step7.md)



## <a name="related-videos"></a>Видео по теме
- [Выбор правильного типа шлюза ATA](https://channel9.msdn.com/Shows/Microsoft-Security/ATA-Deployment-Choose-the-Right-Gateway-Type)


## <a name="see-also"></a>См. также
- [Руководство по развертыванию среды для подтверждения концепции ATA](http://aka.ms/atapoc)
- [Средство изменения размера ATA](http://aka.ms/atasizingtool)
- [Ознакомьтесь с форумом ATA.](https://social.technet.microsoft.com/Forums/security/home?forum=mata)
- [Настройка сбора данных о событиях](configure-event-collection.md)
- [Предварительные требования ATA](ata-prerequisites.md)

