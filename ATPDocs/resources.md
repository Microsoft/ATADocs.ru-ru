---
title: Список полезных ресурсов для Azure Advanced Threat protection
description: В этой статье приводится перечень полезных ресурсов по Azure ATP
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 02/19/2020
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.service: azure-advanced-threat-protection
ms.assetid: 34dc152c-6b7f-4128-93fe-aad56c282730
ms.reviewer: itargoet
ms.suite: ems
ms.openlocfilehash: 4afff7abad10684c362afd789a896b721165e6eb
ms.sourcegitcommit: c7c0a4c9f7507f3e8e0f219798ed7d347c03e792
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/22/2020
ms.locfileid: "90912572"
---
# <a name="azure-atp-readiness-guide"></a>План подготовки Azure ATP к работе

[!INCLUDE [Rebranding notice](includes/rebranding.md)]

В этой статье описывается стратегия подготовки и приводится список ресурсов для начала работы со службой расширенной защиты от угроз Azure Advanced Threat Protection.

## <a name="understanding-azure-atp"></a>Общие сведения об Azure ATP

Облачная служба расширенной защиты от угроз (Azure ATP) — это облачная служба, которая помогает обнаруживать разные типы изощренных целевых кибератак и внутренних угроз, а также защитить предприятие от них.

Дополнительные сведения об Azure ATP приведены в следующих статьях:

- [Что такое Azure Advanced Threat Protection?](what-is.md)
- [Полное ознакомительное видео по Azure ATP (25 минут)](https://www.youtube.com/watch?v=EGY2m8yU_KE)
- [Подробный видеообзор Azure ATP (75 минут)](https://www.youtube.com/watch?v=QXZIfH0wP3Q)

## <a name="deployment-decisions"></a>Решения, принимаемые при развертывании

Azure ATP состоит из облачной службы, размещенной в Azure, и интегрированных датчиков, которые можно установить на контроллерах домена. Если вы используете физические серверы, очень важно выполнить планирование емкости. Воспользуйтесь средством определения размера, чтобы выделить место для датчиков.

- [Azure ATP sizing tool](https://aka.ms/aatpsizingtool) (Средство определения размера Azure ATP) — это инструмент, который автоматизирует сбор данных об отслеживаемом Azure ATP объеме трафика. Он автоматически обеспечивает поддержку и рекомендует ресурсы для датчиков.
- [Руководство по планированию ресурсов ATP](capacity-planning.md)

## <a name="deploy-azure-atp"></a>Развертывание Azure ATP

Следующие ресурсы помогут вам настроить Azure ATP, подключиться к Active Directory, скачать пакет для датчика, настроить сбор данных о событиях и при необходимости обеспечить интеграцию с VPN, а также создать учетные записи в качестве приманки для злоумышленников и настроить нужные исключения.

- [Попробуйте решение ATP Azure (часть EMS E5)](https://aka.ms/aatptrial) — пробная версия действительна в течение 90 дней.
- [Настройка Azure ATP](install-step1.md) — выполните приведенные инструкции, чтобы развернуть Azure ATP в своей среде.
- [Интеграция Расширенной защиты от угроз Azure с ATP в Microsoft Defender](integrate-msde.md)

## <a name="azure-atp-settings"></a>Параметры Azure ATP

При создании экземпляра Azure ATP основные необходимые параметры настраиваются автоматически. В Azure ATP есть несколько дополнительных настраиваемых параметров, которые обеспечивают более высокую точность обнаружения и оповещения в вашей среде. К ним относятся необходимые разрешения SAM и расширенные параметры политики аудита.

- [Интеграция VPN](install-step6-vpn.md)
- [Необходимые разрешения SAM-R](install-step8-samr.md)
- [Параметры политики аудита](configure-windows-event-collection.md) — проводите аудит работоспособности контроллера домена до и после развертывания ATP.

## <a name="work-with-azure-atp"></a>Работа с Azure ATP

После запуска Azure ATP просмотрите оповещения системы безопасности на временной шкале действий на портале Azure ATP. Временная шкала — это целевая страница, которая отображается по умолчанию, когда пользователь входит на портал Azure ATP. По умолчанию на временной шкале активности отображаются все открытые оповещения системы безопасности. Вы также можете просмотреть уровень серьезности каждого оповещения. Для анализа оповещений вы можете открывать страницы профиля с дополнительными сведениями о сущностях (компьютерах, устройствах, пользователях). Пути бокового смещения служат для отображения возможных смещений в сети и конфиденциальных пользователей под угрозой. Используя пути бокового смещения, вы можете анализировать и устранять угрозы. Следующие ресурсы помогут вам в работе с оповещениями системы безопасности в Azure ATP:

- [Руководство по оповещениям системы безопасности в Azure ATP](suspicious-activity-guide.md). Научитесь анализировать действия, обнаруживаемые Azure ATP, и принимать соответствующие меры.
- [Пути перемещения бокового смещения Azure ATP](use-case-lateral-movement-path.md)
- [Работа с конфиденциальными учетными записями](sensitive-accounts.md). Отслеживайте риски раскрытия учетных данных в привилегированных группах безопасности.

## <a name="security-best-practices"></a>Лучшие методики обеспечения безопасности

- [Часто задаваемые вопросы об Azure ATP](technical-faq.md). В этой статье содержатся ответы на часто задаваемые вопросы о решении Azure ATP.

## <a name="community-resources"></a>Ресурсы сообщества

Блог: [блог по Azure ATP](https://aka.ms/aatpblog)

Публичное сообщество: [Azure ATP Tech Community](https://aka.ms/AatpCom)

Частное сообщество: [группа ATP Azure в Yammer](https://www.yammer.com/azureadvisors/#/threads/inGroup?type=in_group&feedId=9386893&view=all&preserve-view=true)

Channel 9: [страница по безопасности Майкрософт на портале Channel 9](https://channel9.msdn.com/Shows/Microsoft-Security/)

## <a name="see-also"></a>См. также

- [Работа с конфиденциальными учетными записями](sensitive-accounts.md)
- [Загляните на форум Azure ATP!](https://aka.ms/azureatpcommunity)