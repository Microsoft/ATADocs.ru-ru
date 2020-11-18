---
title: Политика Microsoft Defender для личных данных удостоверения
description: Ссылки на сведения об удалении частной информации и персональных данных из защитника Майкрософт для идентификации.
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 10/26/2020
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.service: azure-advanced-threat-protection
ms.reviewer: ophir
ms.suite: ems
ms.openlocfilehash: 648d12d6135e5ab09319580142807f930e595eda
ms.sourcegitcommit: e2227c0b0e5aaa5163dc56d4131ca82f8dca8fb0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/18/2020
ms.locfileid: "94846975"
---
# <a name="product-long-data-security-and-privacy"></a>[!INCLUDE [Product long](includes/product-long.md)] безопасность и конфиденциальность данных

[!INCLUDE [Handle personal data](../includes/gdpr-intro-sentence.md)]

## <a name="search-for-and-identify-personal-data"></a>Поиск и идентификация персональных данных

С [!INCLUDE [Product short](includes/product-short.md)] помощью [панели поиска](workspace-portal.md#search-bar)можно просматривать идентифицируемые персональные данные с [ [!INCLUDE [Product long](includes/product-long.md)] портала](workspace-portal.md) .

Вы можете выполнить поиск конкретного пользователя или компьютера. Щелкнув сущность, вы попадете на [страницу профиля](entity-profiles.md) пользователя или компьютера. В профиле содержатся подробные сведения о сущности из Active Directory, включая сетевую активность, связанную с этой сущностью, и ее историю.

[!INCLUDE [Product short](includes/product-short.md)] личные данные собираются из Active Directory с помощью [!INCLUDE [Product short](includes/product-short.md)] датчика и хранятся в серверной базе данных.

## <a name="update-personal-data"></a>Обновление персональных данных

[!INCLUDE [Product short](includes/product-short.md)]личные данные пользователя получаются из объекта пользователя в Active Directory организации. Поэтому изменения, вносимые в профиль пользователя в AD, отражаются в [!INCLUDE [Product short](includes/product-short.md)] .

## <a name="delete-personal-data"></a>Удаление персональных данных

- После удаления пользователя из Active Directory организации [!INCLUDE [Product short](includes/product-short.md)] автоматически удаляет профиль пользователя и все связанные действия сети в течение года. Вы также можете [удалить](working-with-suspicious-activities.md#review-suspicious-activities-on-the-attack-time-line) любые предупреждения безопасности, содержащие персональные данные.

- Рекомендуется задать разрешения **только для чтения** в контейнере **Удаленные объекты**. Дополнительные сведения о том, как служба разрешает доступ к контейнеру "удаленные объекты" [!INCLUDE [Product short](includes/product-short.md)] , см. в статье рекомендации по использованию контейнера удаленных объектов в [ [!INCLUDE [Product short](includes/product-short.md)] предварительных требованиях](prerequisites.md#before-you-start).

## <a name="export-personal-data"></a>Экспорт персональных данных

В [!INCLUDE [Product short](includes/product-short.md)] вы можете [экспортировать](working-with-suspicious-activities.md#review-suspicious-activities-on-the-attack-time-line) сведения об оповещениях безопасности в Excel. Эта функция также экспортирует персональные данные.

## <a name="audit-personal-data"></a>Аудит персональных данных

[!INCLUDE [Product short](includes/product-short.md)] реализует аудит изменений персональных данных, включая удаление и экспорт записей персональных данных. Срок хранения журнала аудита составляет 90 дней. Аудит в [!INCLUDE [Product short](includes/product-short.md)] — это серверная функция, которая недоступна клиентам.

## <a name="additional-resources"></a>Дополнительные ресурсы

- Сведения о [!INCLUDE [Product short](includes/product-short.md)] доверии и соответствии требованиям см. на [портале доверия службы](https://servicetrust.microsoft.com/ViewPage/GDPRGetStarted) и на [сайте соответствия Microsoft 365 корпоративный GDPR](/microsoft-365/compliance/gdpr?view=o365-worldwide&preserve-view=true).

## <a name="security-and-privacy-for-product-short-us-government-gcc-high-customers"></a>Безопасность и конфиденциальность для [!INCLUDE [Product short](includes/product-short.md)] государственных организаций США — GCC High

Дополнительные сведения о [!INCLUDE [Product short](includes/product-short.md)] стандартах соответствия и расположении данных о клиентах для государственных организаций США от версии GCC High см. в [описании Enterprise Mobility + Security для службы США для государственных организаций](/enterprise-mobility-security/solutions/ems-govt-service-description).
