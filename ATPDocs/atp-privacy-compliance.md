---
title: Политика конфиденциальности персональных данных Azure Advanced Threat Protection | Документация Майкрософт
description: В этой статье содержатся ссылки на сведения о том, как удалить персональные данные из Azure ATP.
keywords: ''
author: mlottner
ms.author: mlottner
manager: barbkess
ms.date: 10/04/2018
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.service: azure-advanced-threat-protection
ms.assetid: 224e629a-0e82-458c-bb03-b67070a9241d
ms.reviewer: ophirp
ms.suite: ems
ms.openlocfilehash: 915bf9f03b716ca3d5cad17bc78c2b5c30084acf
ms.sourcegitcommit: b468d9060eb784c16b64a9cc46dbe2d246046cdd
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/30/2019
ms.locfileid: "58674941"
---
# <a name="azure-atp-data-security-and-privacy"></a>Безопасность и конфиденциальность данных в Azure ATP

[!INCLUDE [Handle personal data](../includes/gdpr-intro-sentence.md)]

## <a name="search-for-and-identify-personal-data"></a>Поиск и идентификация персональных данных 

В Azure Advanced Threat Protection вы можете просмотреть идентифицируемые персональные данные на [портале Azure ATP](workspace-portal.md), используя [панель поиска](workspace-portal.md#search-bar). 

Вы можете выполнить поиск конкретного пользователя или компьютера. Щелкнув сущность, вы попадете на [страницу профиля](entity-profiles.md) пользователя или компьютера. В профиле содержатся подробные сведения о сущности из Active Directory, включая сетевую активность, связанную с этой сущностью, и ее историю.

Персональные данные Azure ATP собираются из Active Directory через датчик Azure ATP и сохраняются в серверной базе данных.

## <a name="update-personal-data"></a>Обновление персональных данных 

Персональные данные пользователя Azure ATP являются производными от объекта пользователя в корпоративном каталоге Active Directory. По этой причине все изменения, внесенные в профиль пользователя в корпоративном каталоге AD, отражаются в Azure ATP.


## <a name="delete-personal-data"></a>Удаление персональных данных 

После удаления пользователя из Active Directory организации Azure ATP автоматически удаляет профиль пользователя и любую связанную с ним сетевую активность за последний год. Вы также можете [удалить](working-with-suspicious-activities.md#review-suspicious-activities-on-the-attack-time-line) любые предупреждения безопасности, содержащие персональные данные. 

## <a name="export-personal-data"></a>Экспорт персональных данных 

Azure ATP поддерживает [экспорт](working-with-suspicious-activities.md#review-suspicious-activities-on-the-attack-time-line) данных, содержащихся в оповещениях системы безопасности, в Excel. Эта функция также экспортирует персональные данные. 
 
## <a name="audit-personal-data"></a>Аудит персональных данных

Azure ATP реализует аудит изменений персональных данных, включая удаление и экспорт записей с персональными данными. Срок хранения журнала аудита составляет 90 дней. Аудит в Azure ATP является функцией серверной части, недоступной для клиентов.
 
## <a name="additional-resources"></a>Дополнительные ресурсы

- Сведения о надежности и соответствии требованиям Azure ATP см. на портале [Service Trust](https://servicetrust.microsoft.com/ViewPage/GDPRGetStarted) и на сайте [соответствия GDPR Microsoft 365 Enterprise](https://docs.microsoft.com/microsoft-365/compliance/compliance-solutions-overview).
