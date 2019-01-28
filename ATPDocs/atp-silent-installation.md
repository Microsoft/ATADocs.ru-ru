---
title: Автоматическая установка Azure Advanced Threat Protection | Документы Майкрософт
description: Сведения об автоматической установке Azure ATP.
keywords: ''
author: mlottner
ms.author: mlottner
manager: mbaldwin
ms.date: 12/05/2018
ms.topic: conceptual
ms.prod: ''
ms.service: azure-advanced-threat-protection
ms.technology: ''
ms.assetid: 24eca4c6-c949-42ea-97b9-41ef0fb611f1
ms.reviewer: itargoet
ms.suite: ems
ms.openlocfilehash: 9bd886f4c8929af85a3f77e25052ff0fbc7a4c56
ms.sourcegitcommit: f37127601166216e57e56611f85dd783c291114c
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/24/2019
ms.locfileid: "54840681"
---
# <a name="azure-atp-switches-and-silent-installation"></a>Коммутаторы и автоматическая установка Azure ATP
Эта статья содержит рекомендации и инструкции по использованию коммутаторов Azure ATP и выполнению автоматической установки.

## <a name="prerequisites"></a>Предварительные условия

Для Azure ATP требуется установить платформу Microsoft .NET Framework 4.7. 

При установке Azure ATP платформа .NET Framework 4.7 автоматически устанавливается в составе развертывания Azure ATP.

> [!IMPORTANT] 
> У вас должна быть установлена последняя версия .NET Framework. Если установлена предыдущая версия .NET, автоматическая установка Azure ATP зациклится и не будет выполнена. 

> [!NOTE] 
> Для установки платформы .NET Framework 4.7 может потребоваться перезагрузка сервера. При установке датчика Azure ATP на контроллерах домена рекомендуется запланировать период обслуживания контроллеров.
При использовании автоматической установки Azure ATP установщик настраивается для автоматического перезапуска сервера в конце установки (при необходимости). Автоматическую установку следует выполнять только в течение периода обслуживания. Из-за ошибки в установщике Windows флаг *norestart* не позволяет гарантированно запретить перезагрузку сервера.

Чтобы отслеживать ход выполнения развертывания, проверяйте журналы установщика Azure ATP, расположенные в каталоге **%AppData%\Local\Temp**.


## <a name="azure-atp-sensor-silent-installation"></a>Автоматическая установка датчика Azure ATP

> [!NOTE]
> При автоматическом развертывании датчика Azure ATP с помощью System Center Configuration Manager или другой системы развертывания программного обеспечения рекомендуется создать два пакета развертывания:</br>Net Framework 4.7, включая перезагрузку контроллера домена;</br>датчик Azure ATP. </br>Сделайте пакет датчика Azure ATP зависимым от развертывания пакета .NET Framework. </br>Получите [пакет автономного развертывания .NET Framework 4.7](https://support.microsoft.com/help/3186497/the-net-framework-4-7-offline-installer-for-windows). 


Для полного автоматического удаления датчика Azure ATP используйте следующую команду:


**Синтаксис**

    Azure ATP sensor Setup.exe /AccessKey=<Access Key> /quiet NetFrameworkCommandLineArguments ="/q" 


> [!NOTE]
> Скопируйте ключ доступа с портала Azure ATP, выбрав раздел **Конфигурация**, а затем **Датчик**.


**Варианты установки**

> [!div class="mx-tableFixed"]
> 
> |Название|Синтаксис|Обязательно для автоматической установки?|Описание|
> |-------------|----------|---------|---------|
> |Quiet|/quiet|Да|Запускает установщик, не отображая пользовательский интерфейс и запросы.|
> |Справка|/help|Нет|Предоставляет справку и краткий справочник. Отображает правильное использование команды установки, включая все варианты и особенности использования.|
> |NetFrameworkCommandLineArguments="/q"|NetFrameworkCommandLineArguments="/q"|Да|Задает параметры для установки платформы .NET Framework. Необходимо задать, чтобы применить автоматическую установку платформы .NET Framework.|

**Параметры установки**

> [!div class="mx-tableFixed"]
> 
> |Название|Синтаксис|Обязательно для автоматической установки?|Описание|
> |-------------|----------|---------|---------|
> |AccessKey|AccessKey="\*\*"|Да|Задает ключ доступа, используемый для регистрации датчика Azure ATP в экземпляре Azure ATP.|

**Примеры.** Для автоматической установки датчика Azure ATP используйте приведенную ниже команду.

    "Azure ATP sensor Setup.exe" /quiet NetFrameworkCommandLineArguments="/q" 
    AccessKey="3WlO0uKW7lY6Lk0+dfkfkJQ0qZV6aSq5WxLf71+fuBhggCl/BMs9JxfAwi7oy9vYGviazUS1EPpzte7z8s4grw==" 


## <a name="update-the-azure-atp-sensor"></a>Обновление датчика Azure ATP

Для автоматического обновления датчика Azure ATP используйте приведенную ниже команду.

**Синтаксис**

    Azure ATP sensor Setup.exe [/quiet] [/Help] [NetFrameworkCommandLineArguments="/q"]


**Варианты установки**

> [!div class="mx-tableFixed"]
> 
> |Название|Синтаксис|Обязательно для автоматической установки?|Описание|
> |-------------|----------|---------|---------|
> |Quiet|/quiet|Да|Запускает установщик, не отображая пользовательский интерфейс и запросы.|
> |Справка|/help|Нет|Предоставляет справку и краткий справочник. Отображает правильное использование команды установки, включая все варианты и особенности использования.|
> |NetFrameworkCommandLineArguments="/q"|NetFrameworkCommandLineArguments="/q"|Да|Задает параметры для установки платформы .NET Framework. Необходимо задать, чтобы применить автоматическую установку платформы .NET Framework.|


**Примеры.** Автоматическое обновление датчика Azure ATP:

    Azure ATP sensor Setup.exe /quiet NetFrameworkCommandLineArguments="/q"

## <a name="uninstall-the-azure-atp-sensor-silently"></a>Автоматическое удаление датчика Azure ATP

Для автоматического удаления датчика Azure ATP используйте следующую команду: **Синтаксис**

    Azure ATP sensor Setup.exe [/quiet] [/Uninstall] [/Help]

**Варианты установки**

> [!div class="mx-tableFixed"]
> 
> |Название|Синтаксис|Обязательно для автоматического удаления?|Описание|
> |-------------|----------|---------|---------|
> |Quiet|/quiet|Да|Запускает программу удаления, не отображая пользовательский интерфейс и подсказки.|
> |Удаление|/uninstall|Да|Запускает автоматическое удаление датчика Azure ATP с сервера.|
> |Справка|/help|Нет|Предоставляет справку и краткий справочник. Отображает правильное использование команды установки, включая все варианты и особенности использования.|

**Примеры.** Автоматическое удаление датчика Azure ATP с сервера:


    Azure ATP sensor Setup.exe /quiet /uninstall




## <a name="see-also"></a>См. также

- [Предварительные требования к Azure ATP](atp-prerequisites.md)
- [Установка датчика Azure ATP](install-atp-step4.md)
- [Настройка датчика Azure ATP](install-atp-step5.md)
- [Загляните на форум Azure ATP!](https://aka.ms/azureatpcommunity)
