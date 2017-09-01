---
title: "Автоматическая установка Advanced Threat Analytics | Документация Майкрософт"
description: "Здесь описывается автоматическая установка ATA."
keywords: 
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 08/29/2017
ms.topic: get-started-article
ms.prod: 
ms.service: advanced-threat-analytics
ms.technology: 
ms.assetid: b3cceb18-0f3c-42ac-8630-bdc6b310f1d6
ms.reviewer: bennyl
ms.suite: ems
ms.openlocfilehash: c38db312ea877b63580d745153aa58ea34a160a6
ms.sourcegitcommit: 9ce330726e5de8c05eae6a20d3e6c1d8bef3cd0e
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/29/2017
---
*Применяется к Advanced Threat Analytics версии 1.8*


# <a name="ata-silent-installation"></a>Автоматическая установка ATA
Эта статья содержит указания по автоматической установке ATA.

## <a name="prerequisites"></a>Предварительные требования

Для ATA версии 1.8 требуется установить платформу Microsoft .NET Framework 4.6.1. 

При установке или обновлении ATA платформа .NET Framework 4.6.1 автоматически установится в составе развертывания Microsoft ATA.

> [!Note] 
> Для установки платформы .NET Framework 4.6.1 может потребоваться перезагрузка сервера. При установке шлюза ATA на контроллерах домена рекомендуется запланировать период обслуживания.
При использовании метода автоматической установки ATA установщик настраивается для автоматического перезапуска сервера в конце установки (при необходимости). Из-за ошибки в установщике Windows флаг norestart не позволяет гарантированно запретить перезагрузку сервера, поэтому автоматическую установку следует проводить только в периоды обслуживания.

Чтобы отслеживать ход выполнения развертывания, проверяйте журналы установщика ATA, расположенные в каталоге **%AppData%\Local\Temp**.


## <a name="install-the-ata-center"></a>Установите центр ATA.

Для установки центра ATA используйте приведенную ниже команду.

**Синтаксис**

    "Microsoft ATA Center Setup.exe" [/quiet] [/Help] [--LicenseAccepted] [NetFrameworkCommandLineArguments="/q"] [InstallationPath="<InstallPath>"] [DatabaseDataPath= "<DBPath>"] [CenterIpAddress=<CenterIPAddress>] [CenterPort=<CenterPort>] [CenterCertificateThumbprint="<CertThumbprint>"] 
    [ConsoleIpAddress=<ConsoleIPAddress>] [ConsoleCertificateThumbprint="<CertThumbprint >"]
    
**Варианты установки**

> [!div class="mx-tableFixed"]
|Имя|Синтаксис|Обязательно для автоматической установки?|Описание|
|-------------|----------|---------|---------|
|Quiet|/quiet|да|Запускает установщик, не отображая пользовательский интерфейс и запросы.|
|Справка|/help|Нет|Предоставляет справку и краткий справочник. Отображает правильное использование команды установки, включая все варианты и особенности использования.|
|NetFrameworkCommandLineArguments="/q"|NetFrameworkCommandLineArguments="/q"|да|Задает параметры для установки платформы .NET Framework. Необходимо задать, чтобы применить автоматическую установку платформы .NET Framework.|
|LicenseAccepted|--LicenseAccepted|да|Указывает, что лицензия прочитана и утверждена. Необходимо задать при автоматической установке.|

**Параметры установки**

> [!div class="mx-tableFixed"]
|Имя|Синтаксис|Обязательно для автоматической установки?|Описание|
|-------------|----------|---------|---------|
|InstallationPath|InstallationPath="<InstallPath>"|Нет|Задает путь для установки двоичных файлов ATA. По умолчанию задан путь C:\Program Files\Microsoft Advanced Threat Analytics\Center.|
|DatabaseDataPath|DatabaseDataPath= "<DBPath>"|Нет|Задает путь к папке данных базы данных ATA. По умолчанию задан путь C:\Program Files\Microsoft Advanced Threat Analytics\Center\MongoDB\bin\data.|
|CenterIpAddress|CenterIpAddress=<CenterIPAddress>|да|Задает IP-адрес службы центра ATA.|
|CenterPort|CenterPort=<CenterPort>|да|Задает сетевой порт службы центра ATA.|
|CenterCertificateThumbprint|CenterCertificateThumbprint="<CertThumbprint>"|Нет|Задает отпечаток сертификата для службы центра ATA. Этот сертификат используется для безопасного обмена данными между центром ATA и шлюзом ATA. Если этот параметр не задан, при установке будет создан самозаверяющий сертификат.|
|ConsoleIpAddress|ConsoleIpAddress=<ConsoleIPAddress>|да|Задает IP-адрес консоли ATA.|
|ConsoleCertificateThumbprint|ConsoleCertificateThumbprint="<CertThumbprint >"|Нет|Задает отпечаток сертификата для консоли ATA. Этот сертификат используется для проверки удостоверения веб-сайта консоли ATA. Если этот параметр не задан, при установке будет создан самозаверяющий сертификат.|

**Примеры**. Установка центра ATA с использованием путей установки по умолчанию и одного IP-адреса.

    "Microsoft ATA Center Setup.exe" /quiet --LicenseAccepted NetFrameworkCommandLineArguments="/q" CenterIpAddress=192.168.0.10
    CenterPort=444 ConsoleIpAddress=192.168.0.10

Установка центра ATA с использованием путей установки по умолчанию, двух IP-адресов и отпечатков сертификатов, определяемых пользователем.

    "Microsoft ATA Center Setup.exe" /quiet --LicenseAccepted NetFrameworkCommandLineArguments ="/q" CenterIpAddress=192.168.0.10 CenterPort=443 CenterCertificateThumbprint= ‎"1E2079739F624148ABDF502BF9C799FCB8C7212F"
    ConsoleIpAddress=192.168.0.11  ConsoleCertificateThumbprint="G9530253C976BFA9342FD1A716C0EC94207BFD5A"

## <a name="update-the-ata-center"></a>Обновите центр ATA.

Для обновления центра ATA используйте приведенную ниже команду.

**Синтаксис**

    "Microsoft ATA Center Setup.exe" [/quiet] [/Help] [NetFrameworkCommandLineArguments="/q"]


**Варианты установки**

> [!div class="mx-tableFixed"]
|Имя|Синтаксис|Обязательно для автоматической установки?|Описание|
|-------------|----------|---------|---------|
|Quiet|/quiet|да|Запускает установщик, не отображая пользовательский интерфейс и запросы.|
|Справка|/help|Нет|Предоставляет справку и краткий справочник. Отображает правильное использование команды установки, включая все варианты и особенности использования.|
|NetFrameworkCommandLineArguments="/q"|NetFrameworkCommandLineArguments="/q"|да|Задает параметры для установки платформы .NET Framework. Необходимо задать, чтобы применить автоматическую установку платформы .NET Framework.|


При обновлении ATA установщик автоматически обнаруживает, что ATA уже установлена на сервере и что установка обновления не требуется.

**Примеры**. Автоматическое обновление центра ATA. В больших средах обновление центра ATA может занять некоторое время. Просматривайте журналы ATA, чтобы отслеживать ход выполнения обновления.

        "Microsoft ATA Center Setup.exe" /quiet NetFrameworkCommandLineArguments="/q"

## <a name="uninstall-the-ata-center-silently"></a>Автоматическое удаление центра ATA

Для автоматического удаления центра ATA используйте следующую команду: **Синтаксис**:

    Microsoft ATA Center Setup.exe [/quiet] [/Uninstall] [/Help]
     [--DeleteExistingDatabaseData]

**Варианты установки**

> [!div class="mx-tableFixed"]
|Имя|Синтаксис|Обязательно для автоматического удаления?|Описание|
|-------------|----------|---------|---------|
|Quiet|/quiet|да|Запускает программу удаления, не отображая пользовательский интерфейс и подсказки.|
|Удаление|/uninstall|да|Запускает автоматическое удаление центра ATA с сервера.|
|Справка|/help|Нет|Предоставляет справку и краткий справочник. Отображает правильное использование команды установки, включая все варианты и особенности использования.|

**Параметры установки**

> [!div class="mx-tableFixed"]
|Имя|Синтаксис|Обязательно для автоматического удаления?|Описание|
|-------------|----------|---------|---------|
|DeleteExistingDatabaseData|DeleteExistingDatabaseData|Нет|Удаляет все файлы в имеющейся базе данных.|

**Примеры**. Автоматическое удаление центра ATA с сервера и всех имеющихся данных базы данных.


    "Microsoft ATA Center Setup.exe" /quiet /uninstall --DeleteExistingDatabaseData

## <a name="ata-gateway-silent-installation"></a>Автоматическая установка шлюза ATA

> [!NOTE]
> При автоматическом развертывании упрощенного шлюза ATA с помощью System Center Configuration Manager или другой системы развертывания программного обеспечения рекомендуется создать два пакета развертывания:</br>Net Framework 4.6.1, включая перезагрузку контроллера домена;</br>шлюз ATA. </br>Сделайте пакет шлюза ATA зависимым от развертывания пакета .NET Framework. </br>Получите [пакет автономного развертывания .NET Framework 4.6.1](https://www.microsoft.com/download/details.aspx?id=49982). 


Для автоматической установки шлюза ATA используйте приведенную ниже команду.

**Синтаксис**

    Microsoft ATA Gateway Setup.exe [/quiet] [/Help] [NetFrameworkCommandLineArguments ="/q"] 
    [ConsoleAccountName="<AccountName>"] 
    [ConsoleAccountPassword="<AccountPassword>"]

> [!NOTE]
> Если вы работаете на присоединенном к домену компьютере и выполнили вход с помощью имени пользователя и пароля администратора ATA, указывать здесь учетные данные не требуется.


**Варианты установки**

> [!div class="mx-tableFixed"]
|Имя|Синтаксис|Обязательно для автоматической установки?|Описание|
|-------------|----------|---------|---------|
|Quiet|/quiet|да|Запускает установщик, не отображая пользовательский интерфейс и запросы.|
|Справка|/help|Нет|Предоставляет справку и краткий справочник. Отображает правильное использование команды установки, включая все варианты и особенности использования.|
|NetFrameworkCommandLineArguments="/q"|NetFrameworkCommandLineArguments="/q"|да|Задает параметры для установки платформы .NET Framework. Необходимо задать, чтобы применить автоматическую установку платформы .NET Framework.|

**Параметры установки**

> [!div class="mx-tableFixed"]
|Имя|Синтаксис|Обязательно для автоматической установки?|Описание|
|-------------|----------|---------|---------|
|ConsoleAccountName|ConsoleAccountName="<AccountName>"|Да|Задает имя учетной записи пользователя (user@domain.com), используемой для регистрации шлюза ATA в центре ATA.|
|ConsoleAccountPassword|ConsoleAccountPassword="<AccountPassword>"|Да|Задает пароль учетной записи пользователя (user@domain.com), используемой для регистрации шлюза ATA в центре ATA.|

**Примеры**. Чтобы автоматически установить шлюз ATA, выполните вход в присоединенный к домену компьютер с помощью учетных данных администратора ATA. При этом во время установки вводить учетные данные не потребуется. В противном случае необходимо выполнить регистрацию в центре ATA с помощью указанных учетных данных.

    "Microsoft ATA Gateway Setup.exe" /quiet NetFrameworkCommandLineArguments="/q" 
    ConsoleAccountName="user@contoso.com" ConsoleAccountPassword="userpwd"
    

## <a name="update-the-ata-gateway"></a>Обновление шлюза ATA

Для автоматического обновления шлюза ATA используйте приведенную ниже команду.

**Синтаксис**

    Microsoft ATA Gateway Setup.exe [/quiet] [/Help] [NetFrameworkCommandLineArguments="/q"]


**Варианты установки**

> [!div class="mx-tableFixed"]
|Имя|Синтаксис|Обязательно для автоматической установки?|Описание|
|-------------|----------|---------|---------|
|Quiet|/quiet|да|Запускает установщик, не отображая пользовательский интерфейс и запросы.|
|Справка|/help|Нет|Предоставляет справку и краткий справочник. Отображает правильное использование команды установки, включая все варианты и особенности использования.|
|NetFrameworkCommandLineArguments="/q"|NetFrameworkCommandLineArguments="/q"|да|Задает параметры для установки платформы .NET Framework. Необходимо задать, чтобы применить автоматическую установку платформы .NET Framework.|


**Примеры**. Автоматическое обновление шлюза ATA.

        Microsoft ATA Gateway Setup.exe /quiet NetFrameworkCommandLineArguments="/q"

## <a name="uninstall-the-ata-gateway-silently"></a>Автоматическое удаление шлюза ATA

Для автоматического удаления шлюза ATA используйте следующую команду: **Синтаксис**:

    Microsoft ATA Gateway Setup.exe [/quiet] [/Uninstall] [/Help]
    
**Варианты установки**

> [!div class="mx-tableFixed"]
|Имя|Синтаксис|Обязательно для автоматического удаления?|Описание|
|-------------|----------|---------|---------|
|Quiet|/quiet|да|Запускает программу удаления, не отображая пользовательский интерфейс и подсказки.|
|Удаление|/uninstall|да|Запускает автоматическое удаление шлюза ATA с сервера.|
|Справка|/help|Нет|Предоставляет справку и краткий справочник. Отображает правильное использование команды установки, включая все варианты и особенности использования.|

**Примеры**. Автоматическое удаление шлюза ATA с сервера.


    Microsoft ATA Gateway Setup.exe /quiet /uninstall
    









## <a name="see-also"></a>См. также

- [Ознакомьтесь с форумом ATA.](https://social.technet.microsoft.com/Forums/security/home?forum=mata)
- [Настройка сбора данных о событиях](configure-event-collection.md)
- [Предварительные требования ATA](ata-prerequisites.md)