---
title: Настройка пересылки событий Windows в Advanced Threat Analytics
description: Описываются параметры настройки пересылки событий Windows в ATA.
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 3/21/2018
ms.topic: conceptual
ms.prod: advanced-threat-analytics
ms.technology: ''
ms.assetid: 3f0498f9-061d-40e6-ae07-98b8dcad9b20
ms.reviewer: bennyl
ms.suite: ems
ms.openlocfilehash: f833b799f14dec5b1ae1a7cf18bd9813f9912cd9
ms.sourcegitcommit: e844155ea57f73dfe2b47f4c5c1c7f5292ccbf1e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2020
ms.locfileid: "94690845"
---
# <a name="configuring-windows-event-forwarding"></a>Настройка пересылки событий Windows

[!INCLUDE [Banner for top of topics](includes/banner.md)]

> [!NOTE]
> В версии ATA 1.8 и более поздних настройка сбора событий для упрощенных шлюзов ATA больше не требуется. Упрощенный шлюз ATA теперь может считывать события локально — настраивать переадресацию событий не требуется.

Чтобы улучшить возможности обнаружения, ATA требуется доступ к следующим событиям Windows: 4776, 4732, 4733, 4728, 4729, 4756, 4757, 7045. Они могут автоматически считываться упрощенным шлюзом ATA или, если упрощенный шлюз ATA не развернут, передаваться в шлюз ATA путем настройки прослушивания событий SIEM в шлюзе ATA или пересылки событий Windows.

> [!NOTE]
> При использовании основных серверных компонентов можно использовать [wecutil](/windows-server/administration/windows-commands/wecutil) для создания подписок на события, которые пересылаются с удаленных компьютеров, и управления этими подписками.

### <a name="wef-configuration-for-ata-gateways-with-port-mirroring"></a>Настройка пересылки событий Windows для шлюза ATA с зеркалированием портов

После настройки зеркалирования портов от контроллеров домена на шлюз ATA выполните следующие инструкции, чтобы настроить пересылку событий Windows с помощью конфигурации "инициировано источником". Это один из возможных способов пересылки событий Windows. 

**Шаг 1. Добавление учетной записи сетевой службы в группу читателей журнала событий для домена** 

В этом сценарии предполагается, что шлюз ATA входит в домен.

1. Откройте раздел "Пользователи и компьютеры Active Directory", перейдите в папку **Builtin** и дважды щелкните группу **Читатели журнала событий**. 
1. Выберите пункт **Участники**.
1. Если в этом списке нет элемента **Сетевая служба**, нажмите кнопку **Добавить** и введите имя **Сетевая служба** в поле **Введите имена выбираемых объектов**. Щелкните **Проверить имена** и дважды нажмите **ОК**. 

После добавления **сетевой службы** в группу **Читатели журнала событий** перезагрузите контроллеры домена, чтобы изменения вступили в силу.

**Шаг 2. Создание на контроллерах домена политики для изменения параметра "Настроить конечный диспетчер подписки"** 
> [!Note] 
> Вы можете настроить групповую политику для этих параметров, а затем применять ее к каждому контроллеру домена, контролируемому шлюзом ATA. Описанные ниже действия изменяют локальную политику контроллера домена.  

1. Выполните следующую команду на каждом контроллере домена: *winrm quickconfig*.
1. В командной строке введите *gpedit.msc*.
1. Раскройте элементы **Конфигурация компьютера > Административные шаблоны > Компоненты Windows > Пересылка событий**.

    ![Изображения редактора локальной групповой политики](media/wef%201%20local%20group%20policy%20editor.png)

1. Дважды щелкните **Настроить конечный диспетчер подписки**.
   
   1.  Выберите значение **Включено**.
   2.  В разделе **Параметры** щелкните **Показать**.

   3.  В поле **SubscriptionManagers** введите следующее значение и нажмите кнопку **ОК**: *Server=http://<fqdnATAGateway>:5985/wsman/SubscriptionManager/WEC,Refresh=10* 
      
        *(Например: Server=`http://atagateway9.contoso.com:5985/wsman/SubscriptionManager/WEC,Refresh=10`)*
      
        ![Изображение настройки целевой подписки](media/wef%202%20config%20target%20sub%20manager.png)
      
   4.  Нажмите кнопку **ОК**.
   5.  В командной строке с повышенными привилегиями введите команду *gpupdate /force*. 

**Шаг 3. Выполнение действий на сервере шлюза ATA** 

1. Откройте командную строку с повышенными привилегиями и введите *wecutil qc*
1. Откройте средство **просмотра событий**. 
1. Щелкните правой кнопкой мыши **Подписки** и выберите **Создать подписки**. 

    1. Введите имя и описание для подписки. 
    2. В параметре **Журнал на конечном компьютере** должно быть выбрано значение **Пересланные события**. Чтобы шлюз ATA мог прочитать события, для журнала назначения следует указать **Перенаправленные события**. 
    3. Выберите **Инициировано исходным компьютером** и нажмите **Выбор групп компьютеров**.
        1. Щелкните **Добавить компьютер в домен**.
        2. Введите имя контроллера домена в поле **Введите имена выбираемых объектов**. Щелкните **Проверить имена** и нажмите кнопку **ОК**.  
          ![Изображение средства просмотра событий](media/wef3%20event%20viewer.png)  
        3. Нажмите кнопку **ОК**.
    4. Щелкните **Выбрать события**.
        1. Щелкните **По журналу** и выберите **Журнал безопасности**.
        2. В поле **Включить/исключить идентификаторы событий** введите номер события и нажмите кнопку **OK**. Например, введите 4776, как в следующем примере.

        ![Изображение фильтра запросов](media/wef%204%20query%20filter.png)

    5. Щелкните созданную подписку правой кнопкой мыши и выберите **Состояние выполнения**, чтобы проверить, есть ли проблемы с состоянием. 
    6. Через несколько минут убедитесь в том, что события, для которых настроена пересылка, отображаются в списке пересланных событий в шлюзе ATA.


Дополнительные сведения см. на странице [Настройка компьютеров для пересылки и сбора событий](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc748890(v=ws.11))

## <a name="see-also"></a>См. также
- [Установка ATA](install-ata-step1.md)
- [Обязательно ознакомьтесь с форумом ATA.](https://social.technet.microsoft.com/Forums/security/home?forum=mata)