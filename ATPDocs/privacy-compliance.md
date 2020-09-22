---
title: Политика конфиденциальности персональных данных Расширенной защиты от угроз Azure
description: В этой статье содержатся ссылки на сведения о том, как удалить персональные данные из Azure ATP.
keywords: ''
author: shsagir
ms.author: shsagir
manager: rkarlin
ms.date: 06/21/2020
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.service: azure-advanced-threat-protection
ms.assetid: 224e629a-0e82-458c-bb03-b67070a9241d
ms.reviewer: ophirp
ms.suite: ems
ms.openlocfilehash: 8cfd442e05827811c929f5d6e89ab03dad8a3367
ms.sourcegitcommit: c7c0a4c9f7507f3e8e0f219798ed7d347c03e792
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/22/2020
ms.locfileid: "90912404"
---
# <a name="azure-atp-data-security-and-privacy"></a>Безопасность и конфиденциальность данных в Azure ATP

[!INCLUDE [Rebranding notice](includes/rebranding.md)]

[!INCLUDE [Handle personal data](../includes/gdpr-intro-sentence.md)]

## <a name="search-for-and-identify-personal-data"></a>Поиск и идентификация персональных данных

В Azure Advanced Threat Protection вы можете просмотреть идентифицируемые персональные данные на [портале Azure ATP](workspace-portal.md), используя [панель поиска](workspace-portal.md#search-bar).

Вы можете выполнить поиск конкретного пользователя или компьютера. Щелкнув сущность, вы попадете на [страницу профиля](entity-profiles.md) пользователя или компьютера. В профиле содержатся подробные сведения о сущности из Active Directory, включая сетевую активность, связанную с этой сущностью, и ее историю.

Персональные данные Azure ATP собираются из Active Directory через датчик Azure ATP и сохраняются в серверной базе данных.

## <a name="update-personal-data"></a>Обновление персональных данных

Персональные данные пользователя Azure ATP являются производными от объекта пользователя в корпоративном каталоге Active Directory. По этой причине все изменения, внесенные в профиль пользователя в корпоративном каталоге AD, отражаются в Azure ATP.


## <a name="delete-personal-data"></a>Удаление персональных данных

- После удаления пользователя из Active Directory организации Azure ATP автоматически удаляет профиль пользователя и любую связанную с ним сетевую активность за последний год. Вы также можете [удалить](working-with-suspicious-activities.md#review-suspicious-activities-on-the-attack-time-line) любые предупреждения безопасности, содержащие персональные данные.

- Рекомендуется задать разрешения **только для чтения** в контейнере **Удаленные объекты**. Дополнительные сведения о том, как служба Azure ATP использует разрешения для контейнера **удаленных объектов, см. в соответствующих рекомендациях статьи [Предварительные требования к Azure ATP](prerequisites.md#before-you-start).

## <a name="export-personal-data"></a>Экспорт персональных данных

Azure ATP поддерживает [экспорт](working-with-suspicious-activities.md#review-suspicious-activities-on-the-attack-time-line) данных, содержащихся в оповещениях системы безопасности, в Excel. Эта функция также экспортирует персональные данные.

## <a name="audit-personal-data"></a>Аудит персональных данных

Azure ATP реализует аудит изменений персональных данных, включая удаление и экспорт записей с персональными данными. Срок хранения журнала аудита составляет 90 дней. Аудит в Azure ATP является функцией серверной части, недоступной для клиентов.

## <a name="additional-resources"></a>Дополнительные ресурсы

- Сведения о надежности и соответствии требованиям Azure ATP см. на портале [Service Trust](https://servicetrust.microsoft.com/ViewPage/GDPRGetStarted) и на сайте [соответствия GDPR Microsoft 365 Enterprise](/microsoft-365/compliance/gdpr?view=o365-worldwide&preserve-view=true).

## <a name="security-and-privacy-for-azure-atp-us-government-gcc-high-customers"></a>Безопасность и конфиденциальность для клиентов US Government GCC High Azure ATP
Дополнительные сведения о стандартах соответствия требованиям Azure ATP и расположении данных клиентов US Government GCC High см. в статье [Описание службы Enterprise Mobility + Security для государственных организаций США](/enterprise-mobility-security/solutions/ems-govt-service-description).