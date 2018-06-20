---
title: Список полезных ресурсов по Azure Advanced Threat Protection | Документация Майкрософт
description: В этой статье приводится перечень полезных ресурсов по Azure ATP
keywords: ''
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 4/29/2018
ms.topic: article
ms.prod: ''
ms.service: azure-advanced-threat-protection
ms.technology: ''
ms.assetid: 34dc152c-6b7f-4128-93fe-aad56c282730
ms.reviewer: itargoet
ms.suite: ems
ms.openlocfilehash: b8d91468664a76436078772ad1fc8510ea56d67a
ms.sourcegitcommit: 5c0f914b44bfb8e03485f12658bfa9a7cd3d8bbc
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/30/2018
ms.locfileid: "32298487"
---
*Применяется к: Azure Advanced Threat Protection*



# <a name="azure-atp-readiness-guide"></a>План подготовки Azure ATP к работе

В этой статье описывается стратегия подготовки и приводится список ресурсов, которые помогут начать работу с Azure Advanced Threat Analytics. 

## <a name="understanding-azure-atp"></a>Общие сведения об Azure ATP

Azure Advanced Threat Protection (ATP) — это облачная служба, которая помогает защитить предприятие от разнообразных типов изощренных целевых кибератак и внутренних угроз. Чтобы получить дополнительные сведения об ATP, воспользуйтесь следующими ресурсами. 
- [Что такое Azure Advanced Threat Protection?](what-is-atp.md)
- [Полное ознакомительное видео по Azure ATP](https://www.youtube.com/watch?v=KX-xpFc0sBw) 

## <a name="deployment-decisions"></a>Решения, принимаемые при развертывании

Azure ATP состоит из облачной службы, размещенной в Azure, и датчиков, которые могут быть установлены на контроллере домена или выделенных серверах. Прежде чем приступить к работе с Azure ATP, следует выбрать тип датчиков, оптимально подходящих для существующего развертывания.<br>Если вы используете физические серверы, необходимо планирование емкости. Выделить место для датчиков поможет средство определения размера. 
- [Azure ATP sizing tool](http://aka.ms/aatpsizingtool) (Средство определения размера Azure ATP) — это инструмент, который автоматизирует сбор данных об отслеживаемом Azure ATP объеме трафика. Он автоматически обеспечивает поддержку и рекомендует ресурсы для датчиков. 
- [Планирование производительности ATA](atp-capacity-planning.md)

## <a name="deploy-azure-atp"></a>Развертывание Azure ATP

Следующие ресурсы помогут вам настроить Azure ATP, подключиться к Active Directory, скачать пакет для датчика, настроить сбор данных о событиях и при необходимости обеспечить интеграцию с VPN, а также создать учетные записи в качестве приманки для злоумышленников и настроить нужные исключения. 
- [Попробуйте решение ATP Azure (часть EMS E5)](http://aka.ms/aatptrial) — пробная версия действительна в течение 90 дней.
- [Создание рабочей области на портале управления](install-atp-step1.md) — разверните Azure ATP в своей среде, выполнив приведенные инструкции.
- [Интеграция Azure ATP с ATP в Защитнике Windows](integrate-wd-atp.md)
- 
## <a name="azure-atp-settings"></a>Параметры Azure ATP

Основные необходимые параметры в Azure ATP настраиваются при создании рабочей области. Однако помимо них существует несколько других параметров для детализированной настройки Azure ATP, например интеграция SIEM и настройки аудита, которые обеспечивают более высокую точность обнаружения в вашей среде. 

- [Что такое Azure Advanced Threat Protection?](what-is-atp.md)
- [Параметры аудита](https://blogs.technet.microsoft.com/positivesecurity/2017/08/18/ata-auditing-auditpol-advanced-audit-settings-enforcement-lightweight-gateway-service-discovery/) — проводите аудит работоспособности контроллера домена до и после развертывания ATA. 

## <a name="work-with-azure-atp"></a>Работа с Azure ATP

После запуска Azure ATP вы сможете просматривать обнаруженные подозрительные действия на временной шкале действий. Это целевая страница по умолчанию, на которую вы попадаете сразу после входа на портал Azure ATP. По умолчанию на временной шкале атак отображаются все открытые подозрительные действия. Вы также можете просмотреть уровень серьезности каждого действия. Для анализа подозрительных действий вы можете открывать детализированные страницы профиля сущностей (компьютеров, устройств, пользователей), которые содержат дополнительные сведения. Следующие ресурсы помогут вам в работе с подозрительными действиями в Azure ATP. 

- [Руководство по подозрительным действиям, обнаруживаемым Azure Advanced Threat Protection](suspicious-activity-guide.md). Научитесь анализировать действия, обнаруживаемые Azure ATP, и принимать соответствующие меры.
- [Работа с конфиденциальными учетными записями](sensitive-accounts.md). Отслеживайте риски раскрытия учетных данных в привилегированных группах безопасности.

## <a name="security-best-practices"></a>Рекомендации по безопасности

- [Часто задаваемые вопросы об Azure ATP](atp-technical-faq.md). В этой статье содержатся ответы на часто задаваемые вопросы о решении Azure ATP. 
## <a name="community-resources"></a>Ресурсы сообщества

Блог: [блог по Azure ATP](https://aka.ms/aatpblog)

Публичное сообщество: [Azure ATP Tech Community](https://aka.ms/AatpCom)

Частное сообщество: [группа ATP Azure в Yammer](https://www.yammer.com/azureadvisors/#/threads/inGroup?type=in_group&feedId=9386893&view=all)

Channel 9: [страница по безопасности Майкрософт на портале Channel 9](https://channel9.msdn.com/Shows/Microsoft-Security/)



## <a name="see-also"></a>См. также

- [Работа с конфиденциальными учетными записями](sensitive-accounts.md)
- [Обязательно ознакомьтесь с форумом ATP](https://aka.ms/azureatpcommunity)