---
title: Расширенная защита от угроз Azure в Microsoft Cloud App Security | Документация Майкрософт
description: Обзор возможностей Azure ATP в Microsoft Cloud App Security.
keywords: ''
author: mlottner
ms.author: mlottner
manager: rkarlin
ms.date: 06/18/2019
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.service: azure-advanced-threat-protection
ms.assetid: 5169dffc-75c4-4eb0-b997-b5359cecda97
ms.reviewer: itargoet
ms.suite: ems
ms.openlocfilehash: 1e64ccfd3f559f59b0091e49a51e2016ef3f8745
ms.sourcegitcommit: 87756e27894570997b7039d128f223de0664639f
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/18/2019
ms.locfileid: "67193499"
---
# <a name="using-azure-atp-with-microsoft-cloud-app-security"></a>Использование Azure ATP с Microsoft Cloud App Security 


Эта статья призвана помочь вам узнать о возможностях расширенного изучения и переходить по ним при использовании портала Microsoft Cloud App Security с Azure ATP. 

Получая доступ к Azure ATP с помощью портала Microsoft Cloud App Security при использовании имеющихся локальных обнаружений и анализов аномального поведения, вы получаете дополнительную возможность выявлять утечку конфиденциальных данных в предприятии и отправлять оповещения об этом, а также отфильтровывать действия и создавать ценные политики. Это гибридное предложение анализирует действия и оповещения на основе анализа поведения пользователей и сущностей, чтобы выявить схемы опасного поведения, и предоставляет оценку приоритета для изучения, чтобы оптимизировать реагирование на инциденты для скомпрометированных удостоверений. 

В этой статье рассматриваются следующие темы:

> [!div class="checklist"]
> * обзор службы;
> * новые способы доступа к Azure ATP;
> * лицензирование необходимых компонентов;
> * где найти отслеживаемые действия Azure ATP в Cloud App Security.

## <a name="service-overview"></a>Обзор службы

При интеграции с Azure ATP на портале Cloud App Security предоставляются оповещения и рекомендации от:
- Решение Microsoft Cloud App Security, идентифицирующее атаки при работе в облаке, поддерживает не только продукты Майкрософт, но и сторонние приложения.
- Решение "Расширенная защита от угроз Azure", использующее машинное обучение и поведенческую аналитику для обнаружения атак в локальных сетях.
- Защита идентификации Azure Active Directory позволяет выявить и предотвратить риски идентификации, связанные с пользователями и их учетными данными, при работе в облачных приложениях.

## <a name="access-azure-atp"></a>Доступ к Azure ATP

Продолжайте использовать Azure ATP на портале Azure ATP или просматривайте оповещения Azure ATP и оценку удостоверений на портале Microsoft Cloud App Security. В любом рабочем процессе задачи установки и настройки Azure ATP по-прежнему обрабатываются на портале Azure ATP. 

## <a name="prerequisites"></a>Предварительные условия

Чтобы получить все возможности изучения поведения пользователей в гибридной среде, вам понадобится следующее:
- Действительная лицензия Microsoft Cloud App Security
- Действующая лицензия на Azure ATP, подключенную к вашему экземпляру Active Directory.
 
>[!NOTE]
>Если у вас нет подписки на Cloud App Security, вы по-прежнему сможете использовать портал Cloud App Security для изучения оповещений Azure ATP и выполнять подробный обзор поведения пользователей и их локальных управляемых действий, но не получите связанные аналитические сведения из облачных приложений.

Сведения о том, как быстро включить Azure ATP в Cloud App Security, см. в статье об [интеграции Azure ATP](https://docs.microsoft.com/cloud-app-security/aatp-integration/enable-azure-advanced-threat-protection).  
 
## <a name="azure-atp-in-cloud-app-security"></a>Azure ATP в Cloud App Security 

Основы использования портала Cloud App Security см. в [кратком руководстве по Cloud App Security](https://docs.microsoft.com/cloud-app-security/getting-started-with-cloud-app-security). 

Получайте доступ к данным и новым гибридным возможностям Azure ATP в оповещениях, действиях и на страницах пользователей Cloud App Security. 

## <a name="alerts"></a>Предупреждения

Оповещения Azure ATP отображаются в очереди **Оповещения** Cloud App Security. Дополнительные параметры фильтрации оповещений доступны только при просмотре оповещений в Cloud App Security. Оповещения Azure ATP отфильтровываются с помощью фильтра приложений, установленного для Azure ATP. 


## <a name="activities"></a>Действия

Оповещения Azure ATP отображаются в **журнале действий** Cloud App Security. Дополнительные параметры и возможности фильтрации действий доступны только при просмотре оповещений в Cloud App Security. Дополнительные сведения о фильтрации и создании новых политик действий см. в статье о [действиях Azure ATP с использованием Microsoft Cloud App Security](https://docs.microsoft.com/azure-advanced-threat-protection/atp-activities-filtering-mcas).  

## <a name="user-pages"></a>Страницы пользователя 

Страницы пользователя содержат [оценку приоритета для изучения](https://docs.microsoft.com/cloud-app-security/tutorial-ueba) по каждому пользователю и журнал всех действий. 

Чтобы получить доступ к странице системного пользователя:
1. Откройте **Оповещения** в главном меню.
1. Выберите и отфильтруйте очередь оповещений для конкретного пользователя с помощью поля **Имя пользователя**.

 или

1. Из меню **Исследовать** выберите **Журнал действий**. 
1. Отфильтруйте очередь журнала действий по пользователям. 

    ![Журнал действий](media/atp-mcas-activity-filter.png)

## <a name="next-steps"></a>Дальнейшие шаги

Дополнительные сведения о фильтрации и создании новых политик действий см. в статье о [действиях Azure ATP с использованием Microsoft Cloud App Security](https://docs.microsoft.com/azure-advanced-threat-protection/atp-activities-filtering-mcas). 
  
## <a name="join-the-community"></a>Присоединяйтесь к сообществу!

Возникли дополнительные вопросы или желание обсудить с другими пользователями службу Azure ATP и связанные с ней вопросы безопасности? Присоединяйтесь к [сообществу Azure ATP](https://techcommunity.microsoft.com/t5/Azure-Advanced-Threat-Protection/bd-p/AzureAdvancedThreatProtection)!




