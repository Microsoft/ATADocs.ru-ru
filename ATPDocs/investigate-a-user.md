---
title: Руководство по анализу пользователей в Azure ATP | Документация Майкрософт
d|Description: This article explains how to user Azure ATP security alerts to investigate a suspicious user.
keywords: ''
author: mlottner
ms.author: mlottner
manager: mbaldwin
ms.date: 1/14/2019
ms.topic: tutorial
ms.prod: ''
ms.service: azure-advanced-threat-protection
ms.technology: ''
ms.assetid: e9cf68d2-36bd-4b0d-b36e-7cf7ded2618e
ms.reviewer: itargoet
ms.suite: ems
ms.openlocfilehash: 126653dd2831e0e3dbd9c777d84d32b1c2e74bd9
ms.sourcegitcommit: 1ee052c4c6b04b290e2d5384c24b65a108b1f1f3
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/14/2019
ms.locfileid: "54253407"
---
# <a name="tutorial-investigate-a-user"></a>Руководство. Анализ пользователя

Свидетельства оповещений Azure ATP и пути бокового смещения обеспечивают четкое указание на выполнение пользователями подозрительных действий или компрометацию их учетных записей. Предложения функций анализа помогают определить риск для организации, выбрать способ устранения и определить лучшую стратегию для предотвращения подобных атак в будущем.  

## <a name="recommended-investigation-steps-for-suspicious-users"></a>Рекомендуемые действия по анализу подозрительных пользователей

Проверьте и исследуйте профиль пользователя на предмет следующих сведений и действий:

1. Кем является [пользователь](entity-profiles.md)?
     1. Является ли пользователь [привилегированным пользователем](sensitive-accounts.md) (например, является администратором, указан в списке отслеживания и т. д.)?  
     2. Какова его роль в организации?
     3. Занимает ли он важное место в организационном дереве?

2. Подозрительные действия для [анализа](investigate-entity.md)
     1. Есть ли для пользователя другое открытое оповещение в Azure ATP или в других средствах обеспечения безопасности, таких как ATP в Защитнике Windows, Центр безопасности Azure и (или) центры сертификации Майкрософт?
     2. Были ли у пользователя неудачные попытки входа?
     3. К каким ресурсам пользователь получает доступ?  
     4. Получает ли пользователь доступ к ценным ресурсам?  
     5. Должен ли пользователь получать доступ к этим ресурсам?  
     6. На каких компьютерах пользователь выполнял вход? 
     7. Правомерно ли пользователь выполнял вход на этих компьютерах?
     8. Есть ли [путь бокового смещения](use-case-lateral-movement-path.md) (LMP) между пользователем и привилегированным пользователем?


## <a name="see-also"></a>См. также

- [Проверка компьютера](investigate-a-computer.md)
- [Работа с оповещениями системы безопасности](working-with-suspicious-activities.md)
- [Работа с путями бокового смещения](use-case-lateral-movement-path.md)
- [Оповещения о разведывательных атаках](atp-reconnaissance-alerts.md)
- [Оповещения о компрометации учетных данных](atp-compromised-credentials-alerts.md)
- [Оповещения об атаках бокового смещения](atp-lateral-movement-alerts.md)
- [Оповещения о захвате управления доменом](atp-domain-dominance-alerts.md)
- [Оповещения о краже данных](atp-exfiltration-alerts.md)
- [Загляните на форум Azure ATP!](https://aka.ms/azureatpcommunity)
