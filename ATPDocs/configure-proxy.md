---
title: "Настройка прокси-сервера или брандмауэра для взаимодействия Azure ATP с датчиком | Документы Майкрософт"
description: "Сведения о настройке брандмауэра или прокси-сервера для взаимодействия облачной службы Azure ATP и датчиков Azure ATP"
keywords: 
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 3/3/2018
ms.topic: get-started-article
ms.prod: 
ms.service: azure-advanced-threat-protection
ms.technology: 
ms.assetid: 9c173d28-a944-491a-92c1-9690eb06b151
ms.reviewer: itargoet
ms.suite: ems
ms.openlocfilehash: f077bbd9990affbb6c552c5ad8875fdfebbd70f2
ms.sourcegitcommit: 84556e94a3efdf20ca1ebf89a481550d7f8f0f69
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/08/2018
---
*Применяется к: Azure Advanced Threat Protection*



# <a name="configure-your-proxy-to-allow-communication-between-azure-atp-sensors-and-the-azure-atp-cloud-service"></a>Настройка прокси-сервера для взаимодействия датчиков Azure ATP и облачной службы Azure ATP

Чтобы контроллеры домена могли обмениваться данными с облачной службой, откройте порт 443 *.atp.azure.com в брандмауэре или на прокси-сервере. Конфигурация должна быть указана на уровне компьютера (учетной записи компьютера), а не на уровне учетной записи пользователя. Можно проверить конфигурацию, выполнив следующие действия.
 
1.  Убедитесь, что **текущий пользователь** имеет доступ к конечной точке процессора, использующей IE. Для этого перейдите с контроллера домена по следующему URL-адресу: https://triprd1wcuse1sensorapi.eastus.cloudapp.azure.com (для США). Должна появиться ошибка 503:

 ![служба недоступна](./media/service-unavailable.png)
 
2.  Если сообщение об ошибке 503 не отображается, проверьте конфигурацию прокси-сервера и повторите попытку.

3.  Если конфигурация прокси-сервера работает для **CURRENT_USER** (то есть отображается ошибка 503), проверьте, включены ли параметры прокси-сервера WinInet для учетной записи **LOCAL_SYSTEM** (используемой службой обновления датчика), выполнив следующую команду в командной строке с повышенными привилегиями:
 
    reg compare "HKCU\SOFTWARE\Microsoft\Windows\CurrentVersion\Internet Settings\Connections" "HKU\S-1-5-18\Software\Microsoft\Windows\CurrentVersion\Internet Settings\Connections" /v DefaultConnectionSettings

Если появляется ошибка "Ошибка: не удается найти указанный раздел или параметр в реестре", значит, на уровне **LOCAL_SYSTEM** не настроено ни одного прокси-сервера.
 
 ![ошибка локальной системы прокси-сервера](./media/proxy-local-system-error.png)

Если выводится результат "Результат сравнения: не совпадают", значит, прокси-сервер задан для **LOCAL_SYSTEM**, но не совпадает с прокси для **CURRENT_USER**:
 
  ![результат сравнения прокси-сервера](./media/proxy-result-compared.png)

5.  Если для **LOCAL_SYSTEM** отсутствуют правильные параметры прокси-сервера (прокси не настроен или отличается от **CURRENT_USER**), возможно, потребуется скопировать параметры прокси-сервера из **CURRENT_USER** в **LOCAL_SYSTEM**. Не забудьте создать резервную копию раздела реестра перед внесением в него изменений:

 Раздел текущего пользователя: HKCU\SOFTWARE\Microsoft\Windows\CurrentVersion\Internet Settings\Connections\DefaultConnectionSettings Раздел локальной системы: HKU\S-1-5-18\Software\Microsoft\Windows\CurrentVersion\Internet Settings\Connections\DefaultConnectionSettings

 
6.  Выполните шаги 4 и 5 для учетной записи **Local_Service** (она совпадает с **Local_System**, но вместо S-1-5-18 должно быть указано S-1-5-19.



## <a name="see-also"></a>См. также
- [Настройка пересылки событий](configure-event-forwarding.md)
- [Обязательно ознакомьтесь с форумом ATP](https://aka.ms/azureatpcommunity)