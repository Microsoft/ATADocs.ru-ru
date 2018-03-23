---
title: Пометка конфиденциальных учетных записей с помощью ATA | Документация Майкрософт
description: Сведения о пометке конфиденциальных учетных записей с помощью Advanced Threat Analytics (ATA)
keywords: ''
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 3/21/2018
ms.topic: article
ms.prod: ''
ms.service: advanced-threat-analytics
ms.technology: ''
ms.assetid: 40a1c5c4-b8d6-477c-8ae5-562b37661624
ms.reviewer: bennyl
ms.suite: ems
ms.openlocfilehash: d9666c0a4fb3aad027ac1f85719bc533e919d75a
ms.sourcegitcommit: 49c3e41714a5a46ff2607cbced50a31ec90fc90c
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/22/2018
---
*Применяется к: Advanced Threat Analytics версии 1.9*



# <a name="tag-sensitive-accounts"></a>Пометка конфиденциальных учетных записей

Вы можете вручную пометить группы или учетные записи как конфиденциальные для повышения эффективности операций обнаружения. Важно убедиться в наличии обновления, так как некоторые операции обнаружения ATA, например обнаружение изменений привилегированной группы и путей бокового смещения, зависят от того, какие группы и учетные записи считаются конфиденциальными. Ранее служба ATA автоматически рассматривала сущность как *конфиденциальную*, если та входила в конкретный список групп. Теперь в качестве конфиденциальных можно вручную пометить других пользователей или группы, например членов совета директоров, руководителей, начальника отдела продаж и т. д., и ATA будет рассматривать их как конфиденциальные.

1.  В консоли ATA в строке меню щелкните значок шестеренки **Настройка**.

2.  В разделе **Обнаружение** выберите пункт **Теги сущности**.

    ![Теги сущности ATA](media/entity-tags.png)

3.  В разделе **Конфиденциально** введите имена **конфиденциальных учетных записей** и **конфиденциальных групп**, а затем щелкните значок **+**, чтобы добавить их.

    ![Пример конфиденциальной учетной записи ATA](media/sensitive-account-sample.png)

4. Нажмите кнопку **Сохранить**.

5. Перейдите на страницу профиля сущности, щелкнув имя сущности. Здесь можно увидеть, почему сущность считается конфиденциальной — благодаря членству в группе или пометке вручную как конфиденциальной.

     
## <a name="see-also"></a>См. также:
[Ознакомьтесь с форумом ATA.](https://social.technet.microsoft.com/Forums/security/home?forum=mata)