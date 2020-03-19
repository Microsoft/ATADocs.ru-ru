---
title: Фильтрация действий и политики Расширенной защиты от угроз Azure в Microsoft Cloud App Security
description: Общие сведения о фильтрации действий и политиках Azure ATP в Microsoft Cloud App Security.
keywords: ''
author: shsagir
ms.author: shsagir
manager: rkarlin
ms.date: 07/01/2019
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.service: azure-advanced-threat-protection
ms.assetid: 397e5a77-2bc7-454c-9fe5-649ebaab16b3
ms.reviewer: itargoet
ms.suite: ems
ms.openlocfilehash: bffad5454cbc1f9216333f44af9a7cfd39ce5433
ms.sourcegitcommit: 11fff9d4ebf1c50b04f7789a22c80cdbc3e4416a
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/15/2020
ms.locfileid: "79414477"
---
# <a name="use-activity-filters-and-create-action-policies-with-azure-atp-in-microsoft-cloud-app-security"></a>Фильтрация действий и создание политик действий с помощью Azure ATP в Microsoft Cloud App Security 

Эта статья призвана помочь вам понять, как фильтровать действия Azure ATP и создавать для них политики с помощью Microsoft Cloud App Security. 

Дополнительные сведения о том, как выполнить интеграцию, см. в статье об [интеграции Azure ATP в Cloud App Security](https://docs.microsoft.com/cloud-app-security/aatp-integration/enable-azure-advanced-threat-protection).  

Использование Azure ATP с Microsoft Cloud App Security позволяет анализировать действия и получать оповещения на основе User and Entity Behavior Analytics (UEBA) — аналитики поведения пользователей и сущностей. С таким решением вы можете обнаруживать в своей компании самые рискованные действия, использовать комплексную оценку приоритета для изучения, а также фильтровать действия и настраивать политики действий. 

## <a name="prerequisites"></a>Предварительные условия

Чтобы получить все возможности изучения поведения пользователей в гибридной среде, вам понадобится следующее:
- Действительная лицензия для Microsoft Cloud App Security
- Действующая лицензия на Azure ATP, подключенную к вашему экземпляру Active Directory.

>[!NOTE]
>Если у вас нет подписки на Cloud App Security, вы все еще можете изучать оповещения Azure ATP и выполнять подробный обзор поведения пользователей и их локальных управляемых действий на портале Cloud App Security, тем не менее аналитические сведения, связанные с облачными приложениями, останутся недоступными.

## <a name="filter-azure-atp-activities-in-cloud-app-security"></a>Фильтрация действий Azure ATP в Cloud App Security  
 
Доступ к действиям Azure ATP можно получить из основного меню **Исследовать** Cloud App Security, выбрав подменю **Журнал действий**, или из меню **Оповещения**, где действия можно посмотреть по состоянию, категории, уровню серьезности, приложению, имени пользователя или политике.  

Чтобы получить доступ к действиям Azure ATP по пользователям:

1. Отфильтруйте очередь **Оповещения** с использованием поля "Имя пользователя". 
    ![Очередь "Оповещения"](media/atp-mcas-alerts-queue.png)
1. Щелкните имя пользователя для какого-либо оповещения в полученном списке, чтобы открыть **страницу пользователя**, поведение которого нужно изучить. 
    
1. Отфильтруйте действия пользователя, используя доступные поля, или добавьте новое правило фильтра с помощью кнопки +.
    ![Очередь "Оповещения"](media/atp-mcas-activity-filter.png)

## <a name="create-activity-policies-in-cloud-app-security"></a>Создание политик действий в Cloud App Security

Отфильтровав действия и определив, какие политики действий вы хотите реализовать, а также что сейчас не соответствует требованиям вашей организации, используйте функцию **Создать политику действия** в меню фильтра, чтобы мгновенно создать настраиваемую политику для пользователя, устройства или клиента. 

Чтобы создать политику действия:

1. На любой странице **Журнала действий** примените фильтр (например, приложение, имя пользователя, тип действия и т. д.). 
    - Для фильтрации действий из Azure ATP выберите **Active Directory** в фильтре приложений. 
    ![Создание политики действия](media/atp-mcas-create-new-policy.png)
1. Нажмите кнопку **Новая политика из поиска**.    
1. Добавьте **имя политики**. 
    ![Создание политики действия — шаг 2](media/atp-mcas-create-policy.png)
1. Добавьте **описание** политики.  
1. Назначьте **серьезность** политики.
1. Выберите **категорию** политики.
1. Выберите или измените фильтры, чтобы создать и назначить политику.
1. Уточните или добавьте фильтры. 
1. Сохраните и примените новую политику.  


## <a name="next-steps"></a>Дальнейшие шаги

Узнайте больше об оценке приоритета для изучения и дополнительных возможностях функций [Microsoft Cloud App Security](https://docs.microsoft.com/cloud-app-security/).
  
## <a name="join-the-community"></a>Присоединяйтесь к сообществу!

Возникли дополнительные вопросы или желание обсудить с другими пользователями службу Azure ATP и связанные с ней вопросы безопасности? Присоединяйтесь к [сообществу Azure ATP](https://techcommunity.microsoft.com/t5/Azure-Advanced-Threat-Protection/bd-p/AzureAdvancedThreatProtection)!




