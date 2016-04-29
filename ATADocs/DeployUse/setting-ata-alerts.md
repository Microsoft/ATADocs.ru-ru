---
# required metadata

title: Настройка оповещений ATA | Microsoft Advanced Threat Analytics
description: В этой статье описано, как настроить получение оповещений ATA о подозрительной активности (по электронной почте или с помощью пересылки событий ATA) 
keywords:
author: rkarlin
manager: stevenpo
ms.date: 04/28/2016
ms.topic: article
ms.prod: identity-ata
ms.service: advanced-threat-analytics
ms.technology: security
ms.assetid: 14cb7513-5dc8-49cb-b3e0-94f469c443dd

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: bennyl
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# Настройка оповещений ATA
Существует три способа получения оповещений ATA о подозрительной активности: по электронной почте, при помощи пересылки событий ATA и пересылки событий на сервер SIEM или сервер системного журнала. Можно выбрать как один, так и несколько способов, а также настроить для них некоторые дополнительные параметры.

> [!NOTE]
> -   В уведомлении по электронной почте содержится ссылка, с помощью которой пользователь сможет перейти непосредственно на страницу с подробными сведениями об обнаруженной подозрительной активности. Имя узла, содержащееся в ссылке, соответствует параметрам URL-адреса консоли ATA на странице центра ATA. По умолчанию URL-адрес консоли ATA — это IP-адрес, выбранный при установке центра ATA.  При настройке оповещений по электронной почте в качестве URL-адреса консоли ATA рекомендуется использовать полное доменное имя.
> -   Оповещения о работоспособности системы отправляются только по электронной почте.
> -   Оповещения отправляются из центра ATA на сервер SMTP и сервер системного журнала.
> -   Электронные оповещения ATA о подозрительной активности отправляются только в случае ее обнаружения.

## Настройка параметров языка оповещений и частоты их получения
Параметр **Язык** можно настроить как для уведомлений по электронной почте, так и для уведомлений, отправляемых на сервер системного журнала.

Параметр **Частота** можно настроить только для уведомлений, отправляемых на сервер системного журнала.

1.  Откройте консоль ATA.

2.  На панели инструментов щелкните значок параметров и выберите пункт **Конфигурация**.

    ![Значок параметров конфигурации ATA](media/ATA-config-icon.JPG)

3.  Выберите пункт **Оповещения**.

4.  В поле **Язык** выберите язык для оповещений.

5.  В поле **Частота** выберите значение **Низкая периодичность**, если хотите получать краткие оповещения только после обнаружения новой подозрительной активности. Если вы хотите получать детальные оповещения о новой обнаруженной подозрительной активности или изменении уже существующей, выберите значение **Высокая периодичность**.

    ![Изображение настройки уровня детализации оповещений](media/ATA-alerts-verbosity-language.png)

6.  Нажмите кнопку **Сохранить**.

## Настройка оповещений по электронной почте
Вы можете настроить получение оповещений ATA в случае обнаружения подозрительной активности. Если вы настроили получение оповещений по электронной почте, для них можно настроить некоторые дополнительные параметры.

1.  На рабочем столе сервера центра ATA щелкните значок **Управление Microsoft Advanced Threat Analytics**.

2.  Введите имя пользователя и пароль, а затем нажмите кнопку **Войти**.

3.  На панели инструментов щелкните значок параметров и выберите пункт **Конфигурация**.

    ![Значок параметров конфигурации ATA](media/ATA-config-icon.JPG)

4.  Выберите пункт **Оповещения**.

5.  Выберите параметр **Почта**, чтобы активировать получение оповещений по электронной почте, и введите следующие сведения:

    |Поле|Описание|Значение|
    |---------|---------------|---------|
    |Конечная точка сервера SMTP (обязательно)|Введите полное доменное имя сервера SMTP.|Пример.<br />smtp.contoso.com|
    |SSL|Если серверу SMTP требуется SSL, активируйте его. **Примечание**. После включения SSL необходимо также изменить номер порта.|По умолчанию отключено|
    |Проверка подлинности|Активируйте, если для сервера SMTP требуется проверка подлинности. **Примечание**. При включении проверки подлинности необходимо предоставить имя пользователя и пароль учетной записи электронной почты, которая имеет разрешение на подключение к серверу SMTP.|По умолчанию отключено|
    |Отправитель (обязательно)|Введите адрес электронной почты отправителя.|Пример.<br />ATA@contoso.com|
    |Получатель (обязательно)|Введите адреса электронной почты пользователей или почтовой группы, которые должны получать оповещения при обнаружении ATA подозрительной активности. **Примечание**. Необходимо ввести один адрес электронной почты за раз и щелкнуть знак "плюс".|Пример.<br />securityteam@contoso.com|

## Настройка пересылки событий ATA на сервер SIEM
Можно настроить отправку оповещений ATA о подозрительной активности на сервер системного журнала. Если вы настроили такой способ получения оповещений, для них можно настроить некоторые дополнительные параметры.

1.  Перед настройкой оповещений системного журнала обратитесь к администратору системы SIEM, чтобы получить следующие сведения:

    -   полное доменное имя или IP-адрес сервера SIEM;

    -   порт, который прослушивает сервер SIEM;

    -   тип транспортного протокола, который следует использовать (UDP, TCP или защищенный TCP);

    -   формат, в котором необходимо отправлять данные (RFC 3164 или RFC 5424).

2.  На рабочем столе сервера центра ATA щелкните значок **Управление Microsoft Advanced Threat Analytics**.

3.  Введите имя пользователя и пароль, а затем нажмите кнопку **Войти**.

4.  На панели инструментов щелкните значок параметров и выберите пункт **Конфигурация**.

    ![Значок параметров конфигурации ATA](media/ATA-config-icon.JPG)

5.  Выберите пункт **Оповещения**.

6.  Выберите параметр **Системный журнал**, чтобы активировать отправку оповещений о подозрительной активности на сервер системного журнала, и введите следующие сведения:

    |Поле|Описание|
    |---------|---------------|
    |Конечная точка сервера системного журнала|Полное доменное имя сервера системного журнала|
    |Транспорт|UDC, TCP или защищенный TCP|
    |Формат|Для отправки событий ATA на сервер SIEM используются форматы RFC 5424 или RFC 3164.|

## См. также
[Для получения поддержки посетите наш форум.](https://social.technet.microsoft.com/Forums/security/en-US/home?forum=mata)


<!--HONumber=Apr16_HO2-->

