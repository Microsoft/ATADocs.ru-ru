---
title: Автоматическая установка Расширенной защиты от угроз Azure
description: Сведения об автоматической установке Azure ATP.
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 11/26/2019
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.service: azure-advanced-threat-protection
ms.assetid: 24eca4c6-c949-42ea-97b9-41ef0fb611f1
ms.reviewer: itargoet
ms.suite: ems
ms.openlocfilehash: 307c1c5e078eba9180956bca5e64b6034c1b1075
ms.sourcegitcommit: 71181a243e60d29a2345620735f9c91ab2b5d689
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/21/2020
ms.locfileid: "85123484"
---
# <a name="azure-atp-switches-and-silent-installation"></a>Коммутаторы и автоматическая установка Azure ATP
Эта статья содержит рекомендации и инструкции по использованию коммутаторов Azure ATP и выполнению автоматической установки.

## <a name="prerequisites"></a>Предварительные условия

Azure ATP требует установки Microsoft .NET Framework 4.7 или более поздней версии.

При развертывании Azure ATP выполняется автоматическая установка .NET Framework 4.7, если эта платформа или ее более поздняя версия не установлена.

> [!IMPORTANT]
> У вас должна быть установлена последняя версия .NET Framework. Если установлена предыдущая версия .NET, автоматическая установка Azure ATP зациклится и не будет выполнена.

> [!NOTE]
> Для установки платформы .NET Framework 4.7 может потребоваться перезагрузка сервера. При установке датчика Azure ATP на контроллерах домена рекомендуется запланировать период обслуживания контроллеров.
При использовании автоматической установки Azure ATP установщик настраивается для автоматического перезапуска сервера в конце установки (при необходимости). Автоматическую установку следует выполнять только в течение периода обслуживания. Из-за ошибки в установщике Windows флаг *norestart* не позволяет гарантированно запретить перезагрузку сервера.

Чтобы отслеживать ход выполнения развертывания, проверяйте журналы установщика Azure ATP, расположенные в каталоге **%AppData%\Local\Temp**.

## <a name="azure-atp-sensor-silent-installation"></a>Автоматическая установка датчика Azure ATP

> [!NOTE]
> При автоматическом развертывании датчика Azure ATP с помощью System Center Configuration Manager или другой системы развертывания программного обеспечения рекомендуется создать два пакета развертывания:</br>– .NET Framework 4.7 или более поздняя версия (может включать перезагрузку контроллера домена);</br>– датчик Azure ATP. </br>Сделайте пакет датчика Azure ATP зависимым от развертывания пакета .NET Framework. </br>Получите [пакет автономного развертывания .NET Framework 4.7](https://support.microsoft.com/help/3186497/the-net-framework-4-7-offline-installer-for-windows).

Для полного автоматического удаления датчика Azure ATP используйте следующую команду:

**Синтаксис cmd.exe**:

    "Azure ATP sensor Setup.exe" /quiet NetFrameworkCommandLineArguments="/q" AccessKey="<Access Key>"

**Синтаксис PowerShell**:

    ./"Azure ATP sensor Setup.exe" /quiet NetFrameworkCommandLineArguments="/q" AccessKey="<Access Key>"

> [!NOTE]
> При использовании синтаксиса PowerShell пропуск префикса **./** приводит к ошибке, препятствующей автоматической установке.

> [!NOTE]
> Скопируйте ключ доступа с портала Azure ATP в разделе **Конфигурация** на странице **Датчик**.


**Варианты установки**

> [!div class="mx-tableFixed"]
>
> |Имя|Синтаксис|Обязательно для автоматической установки?|Описание:|
> |-------------|----------|---------|---------|
> |Quiet|/quiet|Да|Запускает установщик, не отображая пользовательский интерфейс и запросы.|
> |Справка|/help|Нет|Предоставляет справку и краткий справочник. Отображает правильное использование команды установки, включая все варианты и особенности использования.|
> |NetFrameworkCommandLineArguments="/q"|NetFrameworkCommandLineArguments="/q"|Да|Задает параметры для установки платформы .NET Framework. Необходимо задать, чтобы применить автоматическую установку платформы .NET Framework.|

**Параметры установки**

> [!div class="mx-tableFixed"]
>
> |Имя|Синтаксис|Обязательно для автоматической установки?|Описание:|
> |-------------|----------|---------|---------|
> |InstallationPath|InstallationPath=""|Нет|Задает путь для установки двоичных файлов датчика AATP. Путь по умолчанию: %programfiles%\Azure Advanced Threat Protection sensor
> |AccessKey|AccessKey="\*\*"|Да|Задает ключ доступа, используемый для регистрации датчика Azure ATP в экземпляре Azure ATP.|

**Примеры.** Для автоматической установки датчика Azure ATP используйте приведенную ниже команду.

    "Azure ATP sensor Setup.exe" /quiet NetFrameworkCommandLineArguments="/q" AccessKey="mmAOkLYCzfH8L/zUIsH24BIJBevlAWu7wUcSfIkRJufpuEojaDHYdjrNs0P3zpD+/bObKfLS0puD7biT5KDf3g=="

## <a name="proxy-authentication"></a>Проверка подлинности прокси-сервера

Для выполнения проверки подлинности на прокси-сервере используйте следующие команды:

**Синтаксис**


> [!div class="mx-tableFixed"]
>
> |Имя|Синтаксис|Обязательно для автоматической установки?|Описание:|
> |-------------|----------|---------|---------|
> |ProxyUrl|ProxyUrl="http\://proxy.contoso.com:8080"|Нет|Указывает URL-адрес и номер порта прокси-сервера для датчика Azure ATP.|
> |ProxyUserName|ProxyUserName="Contoso\ProxyUser"|Нет|Если служба прокси-сервера требует проверки подлинности, укажите имя пользователя в формате "ДОМЕН\пользователь".|
> |ProxyUserPassword|ProxyUserPassword="P@ssw0rd"|Нет|Указывает пароль для имени пользователя прокси-сервера. * Учетные данные шифруются и хранятся локально датчиком Azure ATP.|

## <a name="update-the-azure-atp-sensor"></a>Обновление датчика Azure ATP

Для автоматического обновления датчика Azure ATP используйте приведенную ниже команду.

**Синтаксис**

    Azure ATP sensor Setup.exe [/quiet] [/Help] [NetFrameworkCommandLineArguments="/q"]


**Варианты установки**

> [!div class="mx-tableFixed"]
>
> |Имя|Синтаксис|Обязательно для автоматической установки?|Описание:|
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
> |Имя|Синтаксис|Обязательно для автоматического удаления?|Описание:|
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
