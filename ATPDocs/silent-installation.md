---
title: Автоматическая установка защитника Майкрософт для идентификации
description: В этом разделе описано, как автоматически установить защитник Майкрософт для идентификации.
ms.date: 10/27/2020
ms.topic: how-to
ms.openlocfilehash: 056451d5f0881360643bfc453366a8ccdb0ddccc
ms.sourcegitcommit: 3a478353118670b8124bc62d33751d8ba6af109d
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/23/2020
ms.locfileid: "97746882"
---
# <a name="product-long-switches-and-silent-installation"></a>[!INCLUDE [Product long](includes/product-long.md)] параметры и автоматическая установка

Эта статья содержит инструкции и инструкции по [!INCLUDE [Product long](includes/product-long.md)] параметрам и автоматической установке.

## <a name="prerequisites"></a>Предварительные требования

[!INCLUDE [Product short](includes/product-short.md)] требуется установка платформы Microsoft .NET Framework 4,7 или более поздней версии.

При установке [!INCLUDE [Product short](includes/product-short.md)] .NET framework 4,7 автоматически устанавливается в составе развертывания, [!INCLUDE [Product short](includes/product-short.md)] если не установлена платформа .net Framework 4,7 или более поздняя версия.

> [!NOTE]
> Для установки платформы .NET Framework 4.7 может потребоваться перезагрузка сервера. При установке [!INCLUDE [Product short](includes/product-short.md)] датчика на контроллерах домена рассмотрите возможность планирования периода обслуживания для контроллеров домена.

[!INCLUDE [Product short](includes/product-short.md)]При использовании автоматической установки установщик настроен на автоматический перезапуск сервера в конце установки (при необходимости). Автоматическую установку следует выполнять только в течение периода обслуживания. Из-за ошибки в установщике Windows флаг *norestart* не позволяет гарантированно запретить перезагрузку сервера.

Чтобы отслеживать ход развертывания, отслеживайте [!INCLUDE [Product short](includes/product-short.md)] журналы установщика, которые находятся в папке `%AppData%\Local\Temp` .

## <a name="product-short-sensor-silent-installation"></a>[!INCLUDE [Product short](includes/product-short.md)] Автоматическая установка датчика

> [!NOTE]
> При автоматическом развертывании [!INCLUDE [Product short](includes/product-short.md)] датчика с помощью System Center Configuration Manager или другой системы развертывания программного обеспечения рекомендуется создать два пакета развертывания:</br>– .NET Framework 4.7 или более поздняя версия (может включать перезагрузку контроллера домена);</br>- [!INCLUDE [Product short](includes/product-short.md)] датчика. </br>Сделайте [!INCLUDE [Product short](includes/product-short.md)] пакет датчика зависимым от развертывания пакета .NET Framework. </br>Получите [пакет автономного развертывания .NET Framework 4.7](https://support.microsoft.com/help/3186497/the-net-framework-4-7-offline-installer-for-windows).

Чтобы выполнить полностью автоматическую установку датчика, используйте следующую команду [!INCLUDE [Product short](includes/product-short.md)] :

**Синтаксис cmd.exe**:

```dos
"Azure ATP sensor Setup.exe" /quiet NetFrameworkCommandLineArguments="/q" AccessKey="<Access Key>"
```

**Синтаксис PowerShell**:

```powershell
.\"Azure ATP sensor Setup.exe" /quiet NetFrameworkCommandLineArguments="/q" AccessKey="<Access Key>"
```

> [!NOTE]
> При использовании синтаксиса PowerShell пропуск префикса **./** приводит к ошибке, препятствующей автоматической установке.

> [!NOTE]
> Скопируйте ключ доступа из [!INCLUDE [Product short](includes/product-short.md)] раздела **конфигурации** портала на странице **датчиков** .

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
> |InstallationPath|InstallationPath=""|Нет|Задает путь для установки [!INCLUDE [Product short](includes/product-short.md)] двоичных файлов датчика. Путь по умолчанию: %programfiles%\Azure Advanced Threat Protection sensor
> |AccessKey|AccessKey="\*\*"|Да|Задает ключ доступа, используемый для регистрации [!INCLUDE [Product short](includes/product-short.md)] датчика в [!INCLUDE [Product short](includes/product-short.md)] экземпляре.|

**Примеры**:

Используйте следующую команду, чтобы автоматически установить [!INCLUDE [Product short](includes/product-short.md)] датчик:

```dos
"Azure ATP sensor Setup.exe" /quiet NetFrameworkCommandLineArguments="/q" AccessKey="mmAOkLYCzfH8L/zUIsH24BIJBevlAWu7wUcSfIkRJufpuEojaDHYdjrNs0P3zpD+/bObKfLS0puD7biT5KDf3g=="
```

## <a name="proxy-authentication"></a>Проверка подлинности прокси-сервера

Для выполнения проверки подлинности на прокси-сервере используйте следующие команды:

**Синтаксис**

> [!div class="mx-tableFixed"]
>
> |Имя|Синтаксис|Обязательно для автоматической установки?|Описание:|
> |-------------|----------|---------|---------|
> |ProxyUrl|ProxyUrl="http\://proxy.contoso.com:8080"|Нет|Определяет URL-адрес и номер порта прокси-сервера для датчика [!INCLUDE [Product short](includes/product-short.md)].|
> |ProxyUserName|ProxyUserName="Contoso\ProxyUser"|Нет|Если служба прокси-сервера требует проверки подлинности, укажите имя пользователя в формате "ДОМЕН\пользователь".|
> |ProxyUserPassword|ProxyUserPassword="P@ssw0rd"|Нет|Указывает пароль для имени пользователя прокси-сервера. * Датчик [!INCLUDE [Product short](includes/product-short.md)] шифрует учетные данные и сохраняет их локально.|

## <a name="update-the-product-short-sensor"></a>Обновление [!INCLUDE [Product short](includes/product-short.md)] датчика

Используйте следующую команду для автоматического обновления [!INCLUDE [Product short](includes/product-short.md)] датчика:

**Синтаксис**

```dos
"Azure ATP sensor Setup.exe" [/quiet] [/Help] [NetFrameworkCommandLineArguments="/q"]
```

**Варианты установки**

> [!div class="mx-tableFixed"]
>
> |Имя|Синтаксис|Обязательно для автоматической установки?|Описание:|
> |-------------|----------|---------|---------|
> |Quiet|/quiet|Да|Запускает установщик, не отображая пользовательский интерфейс и запросы.|
> |Справка|/help|Нет|Предоставляет справку и краткий справочник. Отображает правильное использование команды установки, включая все варианты и особенности использования.|
> |NetFrameworkCommandLineArguments="/q"|NetFrameworkCommandLineArguments="/q"|Да|Задает параметры для установки платформы .NET Framework. Необходимо задать, чтобы применить автоматическую установку платформы .NET Framework.|

**Примеры.**

[!INCLUDE [Product short](includes/product-short.md)]Автоматическое обновление датчика:

```dos
"Azure ATP sensor Setup.exe" /quiet NetFrameworkCommandLineArguments="/q"
```

<a name="silently-uninstall-sensor"></a>

## <a name="uninstall-the-product-short-sensor-silently"></a>Автоматическое удаление [!INCLUDE [Product short](includes/product-short.md)] датчика

Чтобы выполнить автоматическое удаление датчика, используйте следующую команду [!INCLUDE [Product short](includes/product-short.md)] :

**Синтаксис**

```dos
"Azure ATP sensor Setup.exe" [/quiet] [/Uninstall] [/Help]
```

**Варианты установки**

> [!div class="mx-tableFixed"]
>
> |Имя|Синтаксис|Обязательно для автоматического удаления?|Описание:|
> |-------------|----------|---------|---------|
> |Quiet|/quiet|Да|Запускает программу удаления, не отображая пользовательский интерфейс и подсказки.|
> |Удаление|/uninstall|Да|Запускает автоматическое удаление [!INCLUDE [Product short](includes/product-short.md)] датчика с сервера.|
> |Справка|/help|Нет|Предоставляет справку и краткий справочник. Отображает правильное использование команды установки, включая все варианты и особенности использования.|

**Примеры.**

Чтобы автоматически удалить [!INCLUDE [Product short](includes/product-short.md)] датчик с сервера, выполните следующие действия.

```dos
"Azure ATP sensor Setup.exe" /quiet /uninstall
```

## <a name="see-also"></a>См. также

- [Предварительные требования для работы с [!INCLUDE [Product short](includes/product-short.md)]](prerequisites.md)
- [Установка [!INCLUDE [Product short](includes/product-short.md)] датчика](install-step4.md)
- [Настройка [!INCLUDE [Product short](includes/product-short.md)] датчика](install-step5.md)
- [Посетите форум по [!INCLUDE [Product short](includes/product-short.md)].](https://aka.ms/MDIcommunity)
