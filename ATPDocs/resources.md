---
title: Список полезных ресурсов для защитника Майкрософт по удостоверениям
description: В этой статье содержится список полезных ресурсов для защитника Майкрософт по удостоверениям.
ms.date: 10/27/2020
ms.topic: conceptual
ms.openlocfilehash: 1878f8b9cbc8047083c927de612e88e50b1947ca
ms.sourcegitcommit: af41733212c2102c223fed8c8602a21a1f667080
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/14/2021
ms.locfileid: "100515518"
---
# <a name="product-long-readiness-guide"></a>[!INCLUDE [Product long](includes/product-long.md)] рекомендации по готовности

В этой статье содержится список ресурсов с планом готовности, которые помогут приступить к работе [!INCLUDE [Product long](includes/product-long.md)] .

## <a name="understanding-product-long"></a>Поможет [!INCLUDE [Product long](includes/product-long.md)]

[!INCLUDE [Product long](includes/product-long.md)] — это облачная служба, которая помогает вычислить и защитить предприятие от нескольких типов сложных целевых кибератак атак и угроз для предварительной оценки.

Дополнительные сведения см. в разделе [!INCLUDE [Product short](includes/product-short.md)].

- [Общие сведения о [!INCLUDE [Product short](includes/product-short.md)]](what-is.md)
- [[!INCLUDE [Product short](includes/product-short.md)] Вводное видео (25 минут) — полное](https://www.youtube.com/watch?v=EGY2m8yU_KE)
- [[!INCLUDE [Product short](includes/product-short.md)] видео с подробным обзором (75 минут) — полное](https://www.youtube.com/watch?v=QXZIfH0wP3Q)

## <a name="deployment-decisions"></a>Решения, принимаемые при развертывании

[!INCLUDE [Product short](includes/product-short.md)] состоит из облачной службы, размещенной в Azure, и интегрированных датчиков, которые можно установить на контроллерах домена. Если вы используете физические серверы, очень важно выполнить планирование емкости. Воспользуйтесь средством определения размера, чтобы выделить место для датчиков.

- [ [!INCLUDE [Product short](includes/product-short.md)] средство изменения размера](https://aka.ms/aatpsizingtool) — средство изменения размера автоматизирует сбор данных о количестве [!INCLUDE [Product short](includes/product-short.md)] мониторов трафика. Он автоматически обеспечивает поддержку и рекомендует ресурсы для датчиков.
- [[!INCLUDE [Product short](includes/product-short.md)] Руководство по планированию ресурсов](capacity-planning.md)

## <a name="deploy-product-short"></a>Развертывание [!INCLUDE [Product short](includes/product-short.md)]

Используйте эти ресурсы для настройки [!INCLUDE [Product short](includes/product-short.md)] , подключения к Active Directory, загрузки пакета датчика, настройки сбора данных о событиях и, при необходимости, интеграции с VPN, а также настройки учетных записей и исключений honeytoken.

- [Попробуйте [!INCLUDE [Product short](includes/product-short.md)] (часть EMS)](https://aka.ms/aatptrial)  пробная версия действительна в течение 90 дней.
- Чтобы [ [!INCLUDE [Product short](includes/product-short.md)] выполнить развертывание](install-step1.md) [!INCLUDE [Product short](includes/product-short.md)] в вашей среде, выполните следующие действия.
- [Интеграция [!INCLUDE [Product short](includes/product-short.md)] с защитником Майкрософт для конечной точки](integrate-mde.md)

## <a name="product-short-settings"></a>Параметры[!INCLUDE [Product short](includes/product-short.md)]

При создании [!INCLUDE [Product short](includes/product-short.md)] экземпляра основные необходимые параметры настраиваются автоматически. Существует несколько дополнительных настраиваемых параметров в [!INCLUDE [Product short](includes/product-short.md)] для улучшения обнаружения и точности предупреждений для вашей среды, таких как интеграция VPN, SAM необходимые разрешения и расширенные параметры политики аудита.

- [Интеграция VPN](install-step6-vpn.md)
- [Необходимые разрешения SAM-R](install-step8-samr.md)
- [Параметры политики аудита](configure-windows-event-collection.md) — аудит работоспособности контроллера домена до и после [!INCLUDE [Product short](includes/product-short.md)] развертывания.

## <a name="work-with-product-short"></a>Работа с [!INCLUDE [Product short](includes/product-short.md)]

Когда [!INCLUDE [Product short](includes/product-short.md)] Служба будет запущена, просмотрите оповещения системы безопасности на [!INCLUDE [Product short](includes/product-short.md)] временной шкале действия портала. Временная шкала действий — это Целевая страница по умолчанию после входа на [!INCLUDE [Product short](includes/product-short.md)] портал. По умолчанию на временной шкале активности отображаются все открытые оповещения системы безопасности. Вы также можете просмотреть уровень серьезности каждого оповещения. Для анализа оповещений вы можете открывать страницы профиля с дополнительными сведениями о сущностях (компьютерах, устройствах, пользователях). Пути бокового смещения служат для отображения возможных смещений в сети и конфиденциальных пользователей под угрозой. Используя пути бокового смещения, вы можете анализировать и устранять угрозы. Эти ресурсы помогут вам работать с [!INCLUDE [Product short](includes/product-short.md)] оповещениями системы безопасности:

- [ [!INCLUDE [Product short](includes/product-short.md)] руководство по оповещениям системы безопасности](suspicious-activity-guide.md) Узнайте о рассмотрении и выполните следующие действия с помощью [!INCLUDE [Product short](includes/product-short.md)] обнаруженных.
- [[!INCLUDE [Product short](includes/product-short.md)] пути перемещения бокового смещения](use-case-lateral-movement-path.md)
- [Работа с конфиденциальными учетными записями](sensitive-accounts.md). Отслеживайте риски раскрытия учетных данных в привилегированных группах безопасности.

## <a name="security-best-practices"></a>Рекомендации по безопасности

- [ [!INCLUDE [Product short](includes/product-short.md)] Часто задаваемые вопросы](technical-faq.yml) . в этой статье содержится список часто задаваемых вопросов о [!INCLUDE [Product short](includes/product-short.md)] и предоставлены подробные сведения и ответы на них.

## <a name="community-resources"></a>Ресурсы сообщества

Блог: [ [!INCLUDE [Product short](includes/product-short.md)] блог](https://aka.ms/aatpblog)

Общедоступное сообщество: [ [!INCLUDE [Product short](includes/product-short.md)] сообщество Tech](https://aka.ms/AatpCom)

Частное сообщество: [ [!INCLUDE [Product short](includes/product-short.md)] Группа Yammer](https://www.yammer.com/azureadvisors/#/threads/inGroup?type=in_group&feedId=9386893&view=all&preserve-view=true)

Channel 9: [страница по безопасности Майкрософт на портале Channel 9](https://channel9.msdn.com/Shows/Microsoft-Security/)

## <a name="see-also"></a>См. также

- [Работа с конфиденциальными учетными записями](sensitive-accounts.md)
- [Посетите форум по [!INCLUDE [Product short](includes/product-short.md)].](https://aka.ms/MDIcommunity)
