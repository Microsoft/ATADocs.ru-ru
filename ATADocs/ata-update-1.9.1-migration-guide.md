---
title: Руководство по миграции на обновленную версию Advanced Threat Analytics 1.9.1 | Документация Майкрософт
description: Процедуры по обновлению ATA до версии 1.9.1
keywords: ''
author: mlottner
ms.author: mlottner
manager: barbkess
ms.date: 12/10/2018
ms.topic: conceptual
ms.prod: advanced-threat-analytics
ms.service: ''
ms.technology: ''
ms.assetid: 2946310a-8e4e-48fc-9450-fc9647efeb22
ms.reviewer: ort
ms.suite: ems
ms.openlocfilehash: 67d4c7df5d85daefa51a6b8e38a5996bab766d5e
ms.sourcegitcommit: 78748bfd75ae68230d72ad11010ead37d96b0c58
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/12/2019
ms.locfileid: "56078142"
---
# <a name="ata-version-191"></a>ATA версии 1.9.1


В этой статье описываются проблемы, устраненные в обновлении 1 для Microsoft Advanced Threat Analytics (ATA) версии 1.9. Номер сборки этого обновления — 1.9.7412.

## <a name="fixed-issues-included-in-this-update"></a>Ошибки, исправленные в этом обновлении

- Вероятность сбоев при переносе больших баз данных с ATA версии 1.8 на версию 1.9.
- Зависание последней версии браузера Microsoft Edge при смене пользователя.
- Отсутствие информации о данных каталога на странице профиля пользователя в некоторых сценариях.
- При добавлении пользователя в список исключений для обнаружения аномального поведения исключение не всегда применялось. 
- База данных MongoDB обновлена до последней версии.
- Несогласованная повторная синхронизация после обновления всех сущностей доменных служб Active Directory до версии ATA 1.9.
- Несогласованный экспорт подозрительных действий в Microsoft Excel. Случайные сбои вместе с генерацией ошибок.  


## <a name="improvements-included-in-this-update"></a>Улучшения, содержащиеся в этом обновлении
- Изменения, требуемые для сертификации Microsoft Accessibility Standards (MAS).
- Улучшена производительность и система безопасности.

## <a name="get-this-update"></a>Получение обновления

Вы можете получить Microsoft Advanced Threat Analytics версии 1.9 в Центре обновления Майкрософт или скачать это обновление вручную.

### <a name="microsoft-update"></a>Центр обновления Майкрософт
Это обновление доступно в Центре обновления Майкрософт. Дополнительные сведения о том, как использовать Центр обновления Майкрософт, см. в разделе [Как получить обновление из Центра обновления Windows](https://support.microsoft.com/help/3067639).

### <a name="manual-download"></a>Скачивание вручную
Чтобы скачать автономный пакет с этим обновлением, перейдите на веб-сайт Центра загрузки Майкрософт: [Загрузить пакет ATA 1.9](https://www.microsoft.com/en-us/download/details.aspx?id=56725).

### <a name="prerequisites"></a>Предварительные условия
Чтобы установить это обновление, требуется наличие ATA версии 1.9 (1.9.7312), обновления 1 для ATA версии 1.8 (1.8.6765) или ATA версии 1.8 (1.8.6645).

### <a name="restart-requirement"></a>Необходимость перезапуска
Может потребоваться перезапуск компьютера после установки этого обновления.

### <a name="update-replacement-information"></a>Информация о замене версий
Это обновление заменяет ATA версии 1.9 (1.9.7312).


## <a name="see-also"></a>См. также

- [Ознакомьтесь с форумом ATA.](https://social.technet.microsoft.com/Forums/security/home?forum=mata)
- [Версии ATA](ata-versions.md)