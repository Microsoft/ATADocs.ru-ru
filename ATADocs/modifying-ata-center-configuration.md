---
title: "Изменение конфигурации центра Advanced Threat Analytics | Документация Майкрософт"
description: "Описывается изменение IP-адреса, порта, URL-адреса консоли и сертификата центра ATA."
keywords: 
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 6/23/2017
ms.topic: article
ms.prod: 
ms.service: advanced-threat-analytics
ms.technology: 
ms.assetid: 93b27f15-f7e5-49bb-870a-d81d09dfe9fc
ms.reviewer: bennyl
ms.suite: ems
ms.openlocfilehash: 1e9fa2d104c52087746e7c03fea27e3cb596adf0
ms.sourcegitcommit: 470675730967e0c36ebc90fc399baa64e7901f6b
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/30/2017
---
*Применяется к Advanced Threat Analytics версии 1.8*



# Изменение конфигурации центра ATA
<a id="modifying-the-ata-center-configuration" class="xliff"></a>


После первоначального развертывания необходимо аккуратно внести изменения в центр ATA. При обновлении IP-адреса, порта, URL-адреса консоли или сертификата используйте описанную ниже процедуру.

## IP-адрес центра ATA
<a id="the-ata-center-ip-address" class="xliff"></a>

Шлюзы ATA локально хранят IP-адрес центра ATA, к которому они подключаются. Шлюзы регулярно подключаются к центру ATA и подтягивают изменения конфигурации. Способ подключения шлюзов ATA к центру ATA следует изменять в два этапа.

-   Первый этап — изменение IP-адреса и порта, которые должна будет использовать служба центра ATA. На этом этапе центр ATA по-прежнему ведет прослушивание исходного IP-адреса. Когда шлюз ATA в следующий раз будет синхронизировать свою конфигурацию, он будет иметь два IP-адреса для центра ATA. Пока шлюз ATA может подключаться с помощью исходного IP-адреса, новый IP-адрес и порт использоваться не будут.

-   Второй этап — по завершении синхронизации обновленной конфигурации на всех шлюзах АТА вы сможете активировать новый IP-адрес и порт, которые прослушивает центр АТА. После активации нового IP-адреса служба центра ATA будет привязана к нему. Шлюзы ATA не смогут подключиться к исходному адресу и теперь будут пытаться подключиться к новому IP-адресу центра ATA. После подключения к центру ATA с помощью нового IP-адреса шлюз ATA подтянет последнюю конфигурацию и будет использовать один IP-адрес для центра ATA. (Пока вы снова не измените IP-адрес).

> [!NOTE]
> -   Если на первом этапе шлюз ATA работал в автономном режиме и не получил обновленную конфигурацию, вам нужно будет вручную обновить файл конфигурации JSON на шлюзе ATA.
> -   Если на сервере центра ATA установлен новый IP-адрес, можно выбрать его из списка IP-адресов при внесении изменений. Если по какой-то причине невозможно установить IP-адрес на сервере центра ATA, вы можете выбрать пользовательский IP-адрес и добавить его вручную. Вы не сможете активировать новый IP-адрес, пока IP-адрес не будет установлен на сервере.
> -   Если необходимо развернуть новый шлюз ATA после активации нового IP-адреса, необходимо загрузить пакет установки шлюза ATA еще раз.

## URL-адрес консоли
<a id="the-console-url" class="xliff"></a>

URL-адрес используется в следующих сценариях:

-   Установка шлюзов ATA. При установке шлюза ATA он регистрирует себя с помощью центра ATA. Такой процесс регистрации требует подключения к консоли АТА. Если указать FQDN в качестве URL-адреса консоли ATA, необходимо убедиться, что шлюз ATA может разрешить FQDN для IP-адреса, к которому привязана консоль ATA.

-   Оповещения. Когда АТА отправляет оповещение с помощью системы SIEM или электронной почты, такое оповещение содержит ссылку на подозрительное действие. Часть ссылки содержит параметр URL-адреса консоли ATA.

-   Если сертификат установлен из вашего внутреннего центра сертификации (ЦС), рекомендуется сделать так, чтобы URL-адрес соответствовал имени субъекта в сертификате: тогда пользователи не будут получать предупреждение при подключении к консоли ATA.

-   Использование FQDN в качестве URL-адреса консоли ATA позволяет изменять IP-адрес, используемый консолью ATA, без отправки оповещений, как это было ранее, и без необходимости повторно скачивать пакет шлюза ATA. Необходимо обновить DNS с помощью нового IP-адреса.

> [!NOTE]
> После изменения URL-адреса консоли АТА и перед установкой новых шлюзов ATA необходимо скачать пакет установки шлюза ATA.

## Сертификат центра ATA
<a id="the-ata-center-certificate" class="xliff"></a>
Если срок действия вашего сертификата скоро истечет и вам нужно продлить или заменить его после того, как вы установили новый сертификат в хранилище локального компьютера на сервере центра ATA, сделать это можно в два этапа:

-   Первый этап: обновление сертификата, который должен использоваться центром ATA. На этом этапе служба центра ATA по-прежнему привязана к исходному сертификату. В процессе синхронизации конфигураций у шлюзов ATA будет два потенциальных сертификата, действительных для взаимной проверки подлинности. Пока шлюз ATA может подключаться с помощью исходного сертификата, новый сертификат использоваться не будет.

-   Второй этап: когда на всех шлюзах ATA завершится синхронизация обновленной конфигурации, вы сможете активировать новый сертификат, к которому привязана служба центра АТА. При активации нового сертификата служба центра ATA будет привязана к нему. Шлюзы ATA не смогут взаимно проверить подлинность службы центра ATA должным образом и попытаются проверить подлинность второго сертификата. После подключения к службе центра ATA шлюз АТА подтянет последнюю конфигурацию и будет использовать один сертификат для центра ATA (Пока вы снова не измените IP-адрес).

> [!NOTE]
> -   Если на первом этапе шлюз ATA работал в автономном режиме и не получил обновленную конфигурацию, вам нужно будет вручную обновить файл конфигурации JSON на шлюзе ATA.
> -   Используемый вами сертификат должен быть доверенным сертификатом шлюзов ATA.
> -   Сертификат используется также для консоли ATA, поэтому он должен соответствовать адресу консоли ATA, чтобы не появлялись предупреждения браузера.
> -   Если необходимо развернуть новый шлюз ATA после активации нового сертификата, необходимо скачать пакет установки шлюза ATA еще раз.

## Изменение конфигурации центра ATA
<a id="changing-the-ata-center-configuration" class="xliff"></a>

1.  Откройте консоль ATA.

2.  На панели инструментов щелкните значок параметров и выберите пункт **Конфигурация**.

    ![Значок параметров конфигурации ATA](media/ATA-config-icon.png)

3.  Выберите **Center** (Центр).

  ![Изменение конфигурации ATA](media/change-center-config.png)

4.  В поле **URL-адрес** выберите **Добавить пользовательское DNS-имя или IP-адрес**, а затем укажите новое DNS-имя или IP-адрес, либо в поле **Сертификат** выберите новый сертификат.

5.  Нажмите кнопку **Сохранить**.

6.  Вы увидите уведомление о том, сколько шлюзов ATA синхронизировано с последней конфигурацией.

    >[!IMPORTANT]
    >Перед активацией новой конфигурации убедитесь, что все шлюзы ATA синхронизируются с последней конфигурацией. Если сделать это до синхронизации шлюзов ATA, работа шлюза ATA может быть нарушена. Если любой из шлюзов ATA не синхронизирован, при нажатии кнопки "Активировать" возникнет следующая ошибка:


7.  Когда все шлюзы ATA будут синхронизированы, нажмите кнопку **Активировать**, чтобы активировать новый IP-адрес или сертификат.

    > [!NOTE]
    > Если вы ввели пользовательский IP-адрес, вы не сможете нажать кнопку **Активировать**, пока IP-адрес не будет установлен в центре ATA.

8.  Убедитесь, что после активации изменений все шлюзы ATA смогут синхронизировать свои конфигурации. На панели уведомлений будет видно, сколько шлюзов ATA успешно синхронизировали свои конфигурации.




## См. также
<a id="see-also" class="xliff"></a>
- [Работа с консолью ATA](working-with-ata-console.md)
- [Ознакомьтесь с форумом ATA.](https://aka.ms/ata-forum)