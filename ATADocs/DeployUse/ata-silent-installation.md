---
title: "Автоматическая установка ATA | Microsoft Advanced Threat Analytics"
description: "Здесь описывается автоматическая установка ATA."
keywords: 
author: rkarlin
manager: stevenpo
ms.date: 04/28/2016
ms.topic: get-started-article
ms.prod: identity-ata
ms.service: advanced-threat-analytics
ms.technology: security
ms.assetid: b3cceb18-0f3c-42ac-8630-bdc6b310f1d6
ms.reviewer: bennyl
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: d6e7d7bef97bfc4ffde07959dd9256f0319d685f
ms.openlocfilehash: 2e51bc9cac43ff90000ca74cccd158e119cc6ec0


---

# Автоматическая установка ATA
Эта статья содержит указания по автоматической установке ATA.
## Необходимые компоненты

Для Microsoft ATA версии 1.6 требуется установить платформу Microsoft .NET Framework 4.6.1. 

При установке или обновлении ATA платформа .NET Framework 4.6.1 автоматически установится в составе развертывания Microsoft ATA.

> [!Note] 
> Для установки платформы .NET Framework 4.6.1 может потребоваться перезагрузка сервера. При установке шлюза ATA на контроллерах домена рекомендуется запланировать период обслуживания.
При использовании метода автоматической установки ATA установщик настраивается для автоматического перезапуска сервера в конце установки (при необходимости). Чтобы избежать перезагрузки сервера как части установки, используйте флаг `-NoRestart`. Если потребуется использовать флаг `-NoRestart` и выполнить перезапуск в рамках установки, установщик приостановит работу до перезапуска сервера. Чтобы отслеживать ход выполнения развертывания, проверяйте журналы установщика ATA, расположенные в каталоге **%AppData%\Local\Temp**.


## Установите центр ATA.

Для установки центра ATA используйте приведенную ниже команду.

**Синтаксис**

    “Microsoft ATA Center Setup.exe” [/quiet] [/NoRestart] [/Help] [--LicenseAccepted] [NetFrameworkCommandLineArguments=”/q”] [InstallationPath=“<InstallPath>”] [DatabaseDataPath= “<DBPath>”] [CenterIpAddress=<CenterIPAddress>] [CenterPort=<CenterPort>] [CenterCertificateThumbprint=“<CertThumbprint>”] 
    [ConsoleIpAddress=<ConsoleIPAddress>] [ConsoleCertificateThumbprint=”<CertThumbprint >”]
    
**Варианты установки**

|Имя|Синтаксис|Обязательно для автоматической установки?|Описание|
|-------------|----------|---------|---------|
|Quiet|/quiet|Да|Запускает установщик, не отображая пользовательский интерфейс и запросы.|
|NoRestart|/norestart|Нет|Предотвращает все попытки перезапуска. По умолчанию в пользовательском интерфейсе будет отображаться запрос перед перезапуском.|
|Справка|/help|Нет|Предоставляет справку и краткий справочник. Отображает правильное использование команды установки, включая все варианты и особенности использования.|
|NetFrameworkCommandLineArguments="/q"|NetFrameworkCommandLineArguments="/q"|Да|Задает параметры для установки платформы .NET Framework. Необходимо задать, чтобы применить автоматическую установку платформы .NET Framework.|
|LicenseAccepted|--LicenseAccepted|Да|Указывает, что лицензия прочитана и утверждена. Необходимо задать при автоматической установке.|

**Параметры установки**

|Имя|Синтаксис|Обязательно для автоматической установки?|Описание|
|-------------|----------|---------|---------|
|InstallationPath|InstallationPath=“<InstallPath>”|Нет|Задает путь для установки двоичных файлов ATA. По умолчанию задан путь C:\Program Files\Microsoft Advanced Threat Analytics\Center.|
|DatabaseDataPath|DatabaseDataPath=“<DBPath>”|Нет|Задает путь к папке данных базы данных ATA. По умолчанию задан путь C:\Program Files\Microsoft Advanced Threat Analytics\Center\MongoDB\bin\data.|
|CenterIpAddress|CenterIpAddress=<CenterIPAddress>|Да|Задает IP-адрес службы центра ATA.|
|CenterPort|CenterPort=<CenterPort>|Да|Задает сетевой порт службы центра ATA.|
|CenterCertificateThumbprint|CenterCertificateThumbprint=“<CertThumbprint>”|Нет|Задает отпечаток сертификата для службы центра ATA. Этот сертификат используется для безопасного обмена данными между центром ATA и шлюзом ATA. Если этот параметр не задан, при установке будет создан самозаверяющий сертификат.|
|ConsoleIpAddress|ConsoleIpAddress=<ConsoleIPAddress>|Да|Задает IP-адрес консоли ATA.|
|ConsoleCertificateThumbprint|ConsoleCertificateThumbprint=”<CertThumbprint >”|Нет|Задает отпечаток сертификата для консоли ATA. Этот сертификат используется для проверки удостоверения веб-сайта консоли ATA. Если этот параметр не задан, при установке будет создан самозаверяющий сертификат.|

**Примеры**. Установка центра ATA с использованием путей установки по умолчанию и одного IP-адреса.

    “Microsoft ATA Center Setup.exe” /quiet --LicenseAccepted NetFrameworkCommandLineArguments="/q" CenterIpAddress=192.168.0.10
    CenterPort=444 ConsoleIpAddress=192.168.0.10

Установка центра ATA с использованием путей установки по умолчанию, двух IP-адресов и отпечатков сертификатов, определяемых пользователем.

    “Microsoft ATA Center Setup.exe” /quiet --LicenseAccepted NetFrameworkCommandLineArguments ="/q" CenterIpAddress=192.168.0.10 CenterPort=443 CenterCertificateThumbprint= ‎"1E2079739F624148ABDF502BF9C799FCB8C7212F”
    ConsoleIpAddress=192.168.0.11  ConsoleCertificateThumbprint=”G9530253C976BFA9342FD1A716C0EC94207BFD5A”

## Обновите центр ATA.

Для обновления центра ATA используйте приведенную ниже команду.

**Синтаксис**

    Microsoft ATA Center Setup.exe” [/quiet] [-NoRestart] /Help] [NetFrameworkCommandLineArguments=”/q”]


**Варианты установки**

|Имя|Синтаксис|Обязательно для автоматической установки?|Описание|
|-------------|----------|---------|---------|
|Quiet|/quiet|Да|Запускает установщик, не отображая пользовательский интерфейс и запросы.|
|NoRestart|/norestart|Нет|Предотвращает все попытки перезапуска. По умолчанию в пользовательском интерфейсе будет отображаться запрос перед перезапуском.|
|Справка|/help|Нет|Предоставляет справку и краткий справочник. Отображает правильное использование команды установки, включая все варианты и особенности использования.|
|NetFrameworkCommandLineArguments="/q"|NetFrameworkCommandLineArguments="/q"|Да|Задает параметры для установки платформы .NET Framework. Необходимо задать, чтобы применить автоматическую установку платформы .NET Framework.|


При обновлении ATA установщик автоматически обнаруживает, что ATA уже установлена на сервере и что установка обновления не требуется.

**Примеры**. Автоматическое обновление центра ATA. В больших средах обновление центра ATA может занять некоторое время. Просматривайте журналы ATA, чтобы отслеживать ход выполнения обновления.

        “Microsoft ATA Center Setup.exe” /quiet NetFrameworkCommandLineArguments="/q"

## Автоматическое удаление центра ATA

Для автоматического удаления центра ATA используйте следующую команду: **Синтаксис**:

    Microsoft ATA Center Setup.exe [/quiet] [/Uninstall] [/NoRestart] [/Help]
     [--DeleteExistingDatabaseData]

**Варианты установки**

|Имя|Синтаксис|Обязательно для автоматического удаления?|Описание|
|-------------|----------|---------|---------|
|Quiet|/quiet|Да|Запускает программу удаления, не отображая пользовательский интерфейс и подсказки.|
|Удаление|/uninstall|Да|Запускает автоматическое удаление центра ATA с сервера.|
|NoRestart|/norestart|Нет|Предотвращает все попытки перезапуска. По умолчанию в пользовательском интерфейсе будет отображаться запрос перед перезапуском.|
|Справка|/help|Нет|Предоставляет справку и краткий справочник. Отображает правильное использование команды установки, включая все варианты и особенности использования.|

**Параметры установки**

|Имя|Синтаксис|Обязательно для автоматического удаления?|Описание|
|-------------|----------|---------|---------|
|DeleteExistingDatabaseData|DeleteExistingDatabaseData|Нет|Удаляет все файлы в имеющейся базе данных.|

**Примеры**. Автоматическое удаление центра ATA с сервера и всех имеющихся данных базы данных.


    “Microsoft ATA Center Setup.exe” /quiet /uninstall --DeleteExistingDatabaseData

## Автоматическая установка шлюза ATA
Для автоматической установки шлюза ATA используйте приведенную ниже команду.

**Синтаксис**

    Microsoft ATA Gateway Setup.exe [/quiet] [/NoRestart] [/Help] [NetFrameworkCommandLineArguments ="/q"] 
    [GatewayCertificateThumbprint=”<CertThumbprint >”] [ConsoleAccountName=”<AccountName>”] 
    [ConsoleAccountPassword=”<AccountPassword>”]

**Варианты установки**

|Имя|Синтаксис|Обязательно для автоматической установки?|Описание|
|-------------|----------|---------|---------|
|Quiet|/quiet|Да|Запускает установщик, не отображая пользовательский интерфейс и запросы.|
|NoRestart|/norestart|Нет|Предотвращает все попытки перезапуска. По умолчанию в пользовательском интерфейсе будет отображаться запрос перед перезапуском.|
|Справка|/help|Нет|Предоставляет справку и краткий справочник. Отображает правильное использование команды установки, включая все варианты и особенности использования.|
|NetFrameworkCommandLineArguments="/q"|NetFrameworkCommandLineArguments="/q"|Да|Задает параметры для установки платформы .NET Framework. Необходимо задать, чтобы применить автоматическую установку платформы .NET Framework.|
|LicenseAccepted|--LicenseAccepted|Да|Указывает, что лицензия прочитана и утверждена. Необходимо задать при автоматической установке.|

**Параметры установки**

|Имя|Синтаксис|Обязательно для автоматической установки?|Описание|
|-------------|----------|---------|---------|
|GatewayCertificateThumbprint|GatewayCertificateThumbprint=”<CertThumbprint >”|Нет|Задает отпечаток сертификата для службы центра ATA. Этот сертификат используется для безопасного обмена данными между центром ATA и шлюзом ATA. Если этот параметр не задан, при установке будет создан самозаверяющий сертификат.|
|ConsoleAccountName|ConsoleAccountName=”<AccountName>”|Да|Задает имя учетной записи пользователя (user@domain.com), используемой для регистрации шлюза ATA в центре ATA.|
|ConsoleAccountPassword|ConsoleAccountPassword=”<AccountPassword>”|Да|Задает пароль учетной записи пользователя (user@domain.com), используемой для регистрации шлюза ATA в центре ATA.|

**Примеры**. Автоматическая установка шлюза ATA и его регистрация в центре ATA с помощью указанных учетных данных.

    “Microsoft ATA Gateway Setup.exe” /quiet NetFrameworkCommandLineArguments="/q" 
    ConsoleAccountName=”user@contoso.com” ConsoleAccountPassword=“userpwd”
    

## Обновление шлюза ATA

Для автоматического обновления шлюза ATA используйте приведенную ниже команду.

**Синтаксис**

    Microsoft ATA Gateway Setup.exe [/quiet] [/NoRestart] /Help] [NetFrameworkCommandLineArguments="/q"]


**Варианты установки**

|Имя|Синтаксис|Обязательно для автоматической установки?|Описание|
|-------------|----------|---------|---------|
|Quiet|/quiet|Да|Запускает установщик, не отображая пользовательский интерфейс и запросы.|
|NoRestart|/norestart|Нет|Предотвращает все попытки перезапуска. По умолчанию в пользовательском интерфейсе будет отображаться запрос перед перезапуском.|
|Справка|/help|Нет|Предоставляет справку и краткий справочник. Отображает правильное использование команды установки, включая все варианты и особенности использования.|
|NetFrameworkCommandLineArguments="/q"|NetFrameworkCommandLineArguments="/q"|Да|Задает параметры для установки платформы .NET Framework. Необходимо задать, чтобы применить автоматическую установку платформы .NET Framework.|


**Примеры**. Автоматическое обновление шлюза ATA.

        Microsoft ATA Gateway Setup.exe /quiet NetFrameworkCommandLineArguments="/q"

## Автоматическое удаление шлюза ATA

Для автоматического удаления шлюза ATA используйте следующую команду: **Синтаксис**:

    Microsoft ATA Gateway Setup.exe [/quiet] [/Uninstall] [/NoRestart] [/Help]
    
**Варианты установки**

|Имя|Синтаксис|Обязательно для автоматического удаления?|Описание|
|-------------|----------|---------|---------|
|Quiet|/quiet|Да|Запускает программу удаления, не отображая пользовательский интерфейс и подсказки.|
|Удаление|/uninstall|Да|Запускает автоматическое удаление шлюза ATA с сервера.|
|NoRestart|/norestart|Нет|Предотвращает все попытки перезапуска. По умолчанию в пользовательском интерфейсе будет отображаться запрос перед перезапуском.|
|Справка|/help|Нет|Предоставляет справку и краткий справочник. Отображает правильное использование команды установки, включая все варианты и особенности использования.|

**Примеры**. Автоматическое удаление шлюза ATA с сервера.


    Microsoft ATA Gateway Setup.exe /quiet /uninstall
    









## См. также

- [Обязательно ознакомьтесь с форумом ATA.](https://social.technet.microsoft.com/Forums/security/home?forum=mata)
- [Настройка сбора данных о событиях](configure-event-collection.md)
- [Предварительные требования для ATA](/advanced-threat-analytics/plan-design/ata-prerequisites)


<!--HONumber=Jun16_HO4-->


