---
title: Отслеживание контроллеров домена и датчиков, установленных на контроллерах домена, с помощью Расширенной защиты от угроз Azure | Документация Майкрософт
description: Сведения об отслеживании датчиков Azure ATP и покрытия датчиков с помощью Azure ATP
keywords: ''
author: mlottner
ms.author: mlottner
manager: barbkess
ms.date: 02/13/2019
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: azure-advanced-threat-protection
ms.technology: ''
ms.assetid: 92decce8-b3ae-4d32-8407-a95314a66863
ms.reviewer: itargoet
ms.suite: ems
ms.openlocfilehash: b371cb5f2bfeef9ddc14ee11623b609c3f49dbfb
ms.sourcegitcommit: 5d3607b3a2c9d1a35dd36287f4a5fc68fca67eb0
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/18/2019
ms.locfileid: "56334431"
---
# <a name="monitoring-your-domain-controller-coverage"></a>Мониторинг покрытия контроллеров домена

Как только первый датчик Azure ATP будет установлен и настроен в любом контроллере домена в сети, Azure ATP начнет наблюдение за средой для контроллеров домена. 

Во время установки рекомендуется выбрать по крайней мере один контроллер домена датчика Azure ATP в качестве потенциального синхронизатора домена в каждом домене. Одна из задач датчика синхронизатора домена — обеспечение активного поиска этих контроллеров домена конкретным датчиком. Контроллеры домена можно переводить в состояние потенциального синхронизатора домена (и выводить из него) после первоначальной настройки. Если контроллер домена выбран как кандидат для синхронизации домена, в контроллерах домена выполняется только пассивный мониторинг сетевой активности. Дополнительные сведения о настройке датчика Azure и установке его в качестве **потенциального синхронизатора домена** см. в разделе [Конфигурация датчика Azure ATP](install-atp-step5.md) 

После установки и настройки датчика Azure ATP на контроллере домена в сети датчик начинает взаимодействовать со службой Azure ATP на постоянной основе, отправляя сведения о состоянии, работоспособности и версии датчика и собранные события и изменения Active Directory.  

### <a name="domain-controller-status"></a>Состояние контроллера домена

Azure ATP осуществляет постоянный мониторинг среды для выявления неотслеживаемых контроллеров домена, добавленных в среду, и сообщает о них, чтобы помочь вам в управлении полным покрытием вашей среды. 

1. Чтобы проверить состояние обнаруженных отслеживаемых и неотслеживаемых контроллеров домена, перейдите в область **Конфигурация** портала Azure ATP и в разделе **Система** выберите **Датчики**.
   
     ![Мониторинг состояния датчиков Azure ATP](media/atp-sensors-status-monitoring.png)

2. Текущие отслеживаемые и неотслеживаемые контроллеры домена отображаются в верхней части экрана. Для загрузки подробных сведений о состоянии мониторинга контроллеров домена выберите **Загрузить сведения**. 

В загруженном Excel-файле покрытия контроллеров домена содержатся следующие сведения обо всех контроллерах домена в вашей организации:

|Название|Описание|
|----|----|
|Hostname|Имя компьютера|
|Имя домена|Имя домена|
|Под наблюдением|Состояние мониторинга Azure ATP|
|Тип датчика|Датчик Azure ATP или автономный датчик Azure ATP|
|Подразделение|Расположение в Active Directory |
|Версия операционной системы| Обнаруженная версия операционной системы|
|IP-адрес|Обнаруженный IP-адрес| 


> [!NOTE]
> Изменения на страницах конфигурации портала Azure ATP могут вносить только администраторы Azure ATP.


## <a name="see-also"></a>См. также

- [Архитектура Azure ATP](atp-architecture.md)
- [Настройка датчиков Azure ATP](install-atp-step5.md)
- [Поддержка нескольких лесов](atp-multi-forest.md)
- [Загляните на форум Azure ATP!](https://aka.ms/azureatpcommunity)