---
title: Предварительные требования для работы с Microsoft Defender для удостоверений
description: Описание требований для успешного развертывания Microsoft Defender для удостоверений в среде
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 11/24/2020
ms.topic: overview
ms.collection: M365-security-compliance
ms.service: azure-advanced-threat-protection
ms.reviewer: itargoet
ms.suite: ems
ms.openlocfilehash: 23078e7e4281629f378e27281a21124d959f0902
ms.sourcegitcommit: 24530d8fac3b63dee766b124b6a5549c1b9ef808
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/24/2020
ms.locfileid: "96028674"
---
# <a name="product-long-prerequisites"></a>Предварительные требования для работы с [!INCLUDE [Product long](includes/product-long.md)]

В этой статье описываются требования для успешного развертывания [!INCLUDE [Product long](includes/product-long.md)] в среде.

>[!NOTE]
> Дополнительные сведения о планировании ресурсов и производительности см. в статье [Планирование ресурсов [!INCLUDE [Product short](includes/product-short.md)]](capacity-planning.md).

[!INCLUDE [Product short](includes/product-short.md)] состоит из облачной службы [!INCLUDE [Product short](includes/product-short.md)], которая, в свою очередь, состоит из портала [!INCLUDE [Product short](includes/product-short.md)] и датчика [!INCLUDE [Product short](includes/product-short.md)]. Дополнительные сведения о каждом компоненте [!INCLUDE [Product short](includes/product-short.md)] см. в статье [Архитектура [!INCLUDE [Product short](includes/product-short.md)]](architecture.md).

[!INCLUDE [Product short](includes/product-short.md)] защищает локальных и синхронизированных пользователей ваших служб Azure Active Directory. См. подробнее о среде, состоящей только из пользователей AAD в руководстве по [обеспечению защиты удостоверений AAD](/azure/active-directory/identity-protection/overview).

Чтобы создать экземпляр [!INCLUDE [Product short](includes/product-short.md)], требуется клиент AAD, для которого определен как минимум один глобальный администратор или администратор безопасности. Каждый экземпляр [!INCLUDE [Product short](includes/product-short.md)] поддерживает границу леса Active Directory и режим работы леса (FFL) для Windows 2003 и более поздних версий.

Требования в этом руководстве разделены на разделы, в которых описывается все необходимое для успешного развертывания [!INCLUDE [Product short](includes/product-short.md)].

[Перед началом работы](#before-you-start). В этом разделе перечислены сведения, которые необходимо собрать, а также учетные записи и сетевые объекты, которые нужно создать перед установкой.

[Портал [!INCLUDE [Product short](includes/product-short.md)]](#azure-atp-portal-requirements). В этом разделе описываются требования к браузеру для работы с порталом [!INCLUDE [Product short](includes/product-short.md)].

[Датчик [!INCLUDE [Product short](includes/product-short.md)]](#azure-atp-sensor-requirements). В этом разделе перечислены требования к программному и аппаратному обеспечению для датчиков [!INCLUDE [Product short](includes/product-short.md)].

[Автономный датчик [!INCLUDE [Product short](includes/product-short.md)]](#azure-atp-standalone-sensor-requirements). Автономный датчик [!INCLUDE [Product short](includes/product-short.md)] устанавливается на выделенных серверах. Чтобы этот датчик получал сетевой трафик, нужно настроить зеркальное отображение портов на контроллере домена.

> [!NOTE]
> Автономные датчики [!INCLUDE [Product short](includes/product-short.md)] не поддерживают сбор записей журнала трассировки событий Windows (ETW), которые предоставляют данные для нескольких обнаружений. Для полного охвата среды рекомендуется развернуть датчик [!INCLUDE [Product short](includes/product-short.md)].

## <a name="before-you-start"></a>Прежде чем начать

В этом разделе перечислены сведения, которые вам необходимо собрать, а также сведения об учетных записях и сетевых объектах, которые должны быть у вас перед установкой [!INCLUDE [Product short](includes/product-short.md)].

- Получите лицензию на Enterprise Mobility + Security 5 (EMS E5) непосредственно на [портале Microsoft 365](https://www.microsoft.com/cloud-platform/enterprise-mobility-security-pricing) или используйте модель лицензирования Cloud Solution Partner (партнер по облачным решениям, CSP). Доступны также отдельные лицензии на [!INCLUDE [Product short](includes/product-short.md)].

- Убедитесь, что контроллеры домена, на которых вы планируете устанавливать датчики [!INCLUDE [Product short](includes/product-short.md)], подключены через Интернет к облачной службе [!INCLUDE [Product short](includes/product-short.md)]. Датчик [!INCLUDE [Product short](includes/product-short.md)] поддерживает работу с прокси-сервером. Дополнительные сведения о конфигурации прокси-сервера см. в статье [Конфигурация прокси-сервера для [!INCLUDE [Product short](includes/product-short.md)]](configure-proxy.md).

- По крайней мере одна из следующих учетных записей служб каталогов с доступом на чтение ко всем объектам в отслеживаемых доменах:
  - **Стандартная** учетная запись пользователя AD и пароль. Требуется для датчиков под управлением Windows Server 2008 R2 с пакетом обновления 1 (SP1).
  - **Групповая управляемая учетная запись службы** (gMSA). Требуется Windows Server 2012 или более поздней версии.  
  Все датчики должны иметь разрешения на получение пароля учетной записи gMSA.  
  См. сведения об учетных записях gMSA в руководстве по [использованию групповых управляемых учетных записей](/windows-server/security/group-managed-service-accounts/getting-started-with-group-managed-service-accounts#BKMK_CreateGMSA).

    В следующей таблице показаны учетные записи пользователей AD, которые могут использоваться с определенными версиями сервера:

    |Тип учетной записи|Windows Server 2008 R2 с пакетом обновления 1 (SP1)|Windows Server 2012 или более поздней версии|
    |---|---|---|
    |**Стандартная** учетная запись пользователя AD|Да|Да|
    |Учетная запись **gMSA**|Нет|Да|

    > [!NOTE]
    >
    > - Для компьютеров с датчиками под управлением Windows Server 2012 и более поздних версий рекомендуется использовать учетную запись **gMSA** для повышения уровня безопасности и включения автоматического управления паролями.
    > - Если у вас есть датчики под управлением Windows Server 2008 и Windows Server 2012 или более поздней версии, рекомендуется использовать не только учетную запись **gMSA**, но и по крайней мере одну **стандартную** учетную запись пользователя AD.
    > - Если для различных подразделений в домене были установлены настраиваемые списки управления доступом, убедитесь, что у выбранного пользователя есть разрешение на чтение данных подразделений.

- При выполнении Wireshark в автономном датчике [!INCLUDE [Product short](includes/product-short.md)] необходимо перезапустить службу датчика [!INCLUDE [Product short](includes/product-short.md)] после остановки записи Wireshark. Если не перезапустить службу датчика, датчик перестанет записывать трафик.

- При попытке установить датчик [!INCLUDE [Product short](includes/product-short.md)] на компьютере, настроенном с функцией объединения сетевых карт, возникнет ошибка установки. Чтобы установить датчик [!INCLUDE [Product short](includes/product-short.md)] на компьютере с функцией объединения сетевых карт, ознакомьтесь с разделом [Проблема [!INCLUDE [Product short](includes/product-short.md)] при работе с функцией объединения сетевых карт](troubleshooting-known-issues.md#nic-teaming).

- Рекомендация по контейнеру **Удаленные объекты**: в контейнере удаленных объектов у пользователя должно быть разрешение только на чтение. Разрешения только для чтения в этом контейнере позволяют [!INCLUDE [Product short](includes/product-short.md)] обнаруживать удаление пользователей из вашего каталога Active Directory. Дополнительные сведения о настройке разрешений только для чтения в контейнере удаленных объектов см. в разделе **Changing permissions on a deleted object container** (Изменение разрешений для контейнера удаленных объектов) статьи [View or Set Permissions on a Directory Object](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc816824(v=ws.10)) (Просмотр или установка разрешений для объекта каталога).

- **Токен-приманка** (необязательно): Учетная запись пользователя, не совершавшего операции в сети. Эта учетная запись будет настроена как пользователь Honeytoken [!INCLUDE [Product short](includes/product-short.md)]. Дополнительные сведения об использовании токенов-приманок: [Настройка учетных записей Honeytoken и исключений из обнаружения](install-step7.md).

- Необязательно: При развертывании автономного датчика следует пересылать [события Windows](configure-windows-event-collection.md#configure-event-collection) в [!INCLUDE [Product short](includes/product-short.md)], чтобы [!INCLUDE [Product short](includes/product-short.md)] мог дополнительно улучшить обнаружение угроз, связанных с проверкой подлинности, добавлением к конфиденциальным группам и подозрительным созданием служб.  Датчик [!INCLUDE [Product short](includes/product-short.md)] получает эти события автоматически. В автономном датчике [!INCLUDE [Product short](includes/product-short.md)] эти события можно получать из системы SIEM или настроив пересылку событий Windows с контроллера домена. Собранные события предоставляют [!INCLUDE [Product short](includes/product-short.md)] дополнительные данные, которые невозможно получить через сетевой трафик контроллера домена.

<a name="azure-atp-portal-requirements"></a>

## <a name="product-short-portal-requirements"></a>Требования для работы с порталом [!INCLUDE [Product short](includes/product-short.md)]

Доступ к порталу [!INCLUDE [Product short](includes/product-short.md)] осуществляется через браузер. Поддерживаются следующие браузеры и параметры:

- Браузер с поддержкой TLS 1.2, например:
  - Microsoft Edge
  - Internet Explorer 11 и более поздних версий;
  - Google Chrome 30.0 и более поздних версий.
- минимальное разрешение экрана —1700 пикселей.
- Открытый порт брандмауэра или прокси-сервера — чтобы контроллеры домена могли обмениваться данными с облачной службой [!INCLUDE [Product short](includes/product-short.md)], откройте порт 443 для *.atp.azure.com в брандмауэре или на прокси-сервере.

    > [!NOTE]
    > Также можно использовать тег службы Azure (**AzureAdvancedThreatProtection**) для включения доступа к [!INCLUDE [Product short](includes/product-short.md)]. Дополнительные сведения о тегах службы: статья [Теги службы виртуальной сети](/azure/virtual-network/service-tags-overview) или [загружаемый файл тегов службы](https://www.microsoft.com/download/details.aspx?id=56519).

 ![[!INCLUDE [Product short](includes/product-short.md)]: схема архитектуры](media/architecture-topology.png)

> [!NOTE]
> По умолчанию [!INCLUDE [Product short](includes/product-short.md)] поддерживает до 200 датчиков. Чтобы установить дополнительные датчики, обратитесь в службу поддержки [!INCLUDE [Product short](includes/product-short.md)].

## <a name="product-short-network-name-resolution-nnr-requirements"></a>Требования к разрешению сетевых имен (NNR) [!INCLUDE [Product short](includes/product-short.md)]

Разрешение сетевых имен (NNR) — главный компонент [!INCLUDE [Product short](includes/product-short.md)]. Чтобы разрешить IP-адреса для имен компьютеров, датчики [!INCLUDE [Product short](includes/product-short.md)] запрашивают IP-адрес, используя один из следующих методов:

- NTLM через RPC (TCP-порт 135)
- NetBIOS (UDP-порт 137)
- RDP (TCP-порт 3389), только первый пакет **приветствия клиента**.
- Запросы к DNS-серверу с помощью обратного поиска IP-адреса в DNS (UDP 53).

Для работы первых трех методов необходимо открыть соответствующие порты для входящего трафика с датчиков [!INCLUDE [Product short](includes/product-short.md)] на устройства в сети. Дополнительные сведения о [!INCLUDE [Product short](includes/product-short.md)] и NNR см. в разделе [Политика NNR в [!INCLUDE [Product short](includes/product-short.md)]](nnr-policy.md).

Для получения наилучших результатов рекомендуется использовать все методы. Если это невозможно, следует использовать поиск в DNS и по крайней мере один из других методов.

<a name="azure-atp-sensor-requirements"></a>

## <a name="product-short-sensor-requirements"></a>Требования к датчику [!INCLUDE [Product short](includes/product-short.md)]

В этом разделе перечислены требования для датчика [!INCLUDE [Product short](includes/product-short.md)].

### <a name="general"></a>Общие сведения

Датчик \* поддерживает установку на контроллере домена под управлением Windows Server 2008 R2 с пакетом обновления 1 (SP1) (за исключением Server Core), Windows Server 2012, Windows Server 2012 R2, Windows Server 2016 (в том числе Server Core, но не Nano Server), Windows Server 2019[!INCLUDE [Product short](includes/product-short.md)] (в том числе Server Core, но не Nano Server).

| Версия операционной системы   | Сервер с возможностями рабочего стола | Основные серверные компоненты | Nano Server    |
| -------------------------- | ------------------------------ | ----------- | -------------- |
| Windows Server 2008 R2 с пакетом обновления 1 (SP1) | &#10004;                       | &#10060;    | Неприменимо |
| Windows Server 2012        | &#10004;                       | &#10004;    | Неприменимо |
| Windows Server 2012 R2     | &#10004;                       | &#10004;    | Неприменимо |
| Windows Server 2016        | &#10004;                       | &#10004;    | &#10060;       |
| Windows Server 2019\*      | &#10004;                       | &#10004;    | &#10060;       |

\* Требуется [KB4487044](https://support.microsoft.com/help/4487044/windows-10-update-kb4487044) или накопительный пакет обновления более поздней версии. Датчики, установленные в Server 2019 без этого обновления будут автоматически остановлены, если версия файла *ntdsai.dll* в системном каталоге старше версии *10.0.17763.316*.

Контроллер домена можно использовать в качестве контроллера домена только для чтения.

Чтобы контроллеры домена могли обмениваться данными с облачной службой, откройте порт 443 для \*.atp.azure.com в брандмауэре или на прокси-сервере.

Во время установки будет установлена платформа .NET Framework 4.7, если эта платформа или ее более поздняя версия отсутствует. При этом может потребоваться перезагрузка контроллера домена. Перезагрузка также может произойти, если она уже запланирована.

> [!NOTE]
> Требуется не менее 5 ГБ дискового пространства; рекомендуется 10 ГБ. Сюда входит пространство, необходимое для двоичных файлов [!INCLUDE [Product short](includes/product-short.md)], журналов [!INCLUDE [Product short](includes/product-short.md)] и журналов производительности.

### <a name="server-specifications"></a>Спецификации сервера

Для датчика [!INCLUDE [Product short](includes/product-short.md)] на контроллере домена требуется минимум 2 ядра и 6 ГБ ОЗУ.
Для обеспечения оптимальной производительности задайте в **параметре электропитания** компьютера, на котором работает датчик [!INCLUDE [Product short](includes/product-short.md)], значение **Высокая производительность**.

Датчик [!INCLUDE [Product short](includes/product-short.md)] можно развернуть на контроллерах домена с различной нагрузкой и различных размеров в зависимости от объема входящего и исходящего трафика, а также установленных ресурсов.

В операционных системах Windows 2008 R2 и 2012 датчик [!INCLUDE [Product short](includes/product-short.md)] не поддерживается в [многопроцессорном групповом режиме](/windows/win32/procthread/processor-groups). Дополнительные сведения о многопроцессорном групповом режиме см. в статье об [устранении неполадок](troubleshooting-known-issues.md#multi-processor-group-mode).

>[!NOTE]
> При запуске в качестве динамической памяти виртуальной машины или любой другой памяти функция воздушного шага не поддерживается.

Дополнительные сведения о требованиях к оборудованию для датчика [!INCLUDE [Product short](includes/product-short.md)] см. в статье [Планирование ресурсов [!INCLUDE [Product short](includes/product-short.md)]](capacity-planning.md).

### <a name="time-synchronization"></a>Синхронизация времени

Время серверов и контроллеров домена, на которых установлен датчик, должно быть синхронизировано в пределах пяти минут.

### <a name="network-adapters"></a>Сетевые адаптеры

Датчик [!INCLUDE [Product short](includes/product-short.md)] отслеживает локальный трафик всех сетевых адаптеров контроллера домена.  
После развертывания используйте портал [!INCLUDE [Product short](includes/product-short.md)], чтобы изменить параметры отслеживания сетевых адаптеров.

Датчик не поддерживается в контроллерах доменов под управлением Windows 2008 R2 с включенным группированием сетевых адаптеров Broadcom.

### <a name="ports"></a>Порты

В следующей таблице перечислены порты, необходимые для работы датчика [!INCLUDE [Product short](includes/product-short.md)].

|Протокол|Транспорт|Port|От|Кому|
|------------|-------------|--------|-----------|
|**Интернет-порты**|||||
|SSL (*.atp.azure.com)|TCP|443|Датчик [!INCLUDE [Product short](includes/product-short.md)]|Облачная служба [!INCLUDE [Product short](includes/product-short.md)]|
|SSL (localhost)|TCP|444|Датчик [!INCLUDE [Product short](includes/product-short.md)]|localhost|
|**Внутренние порты**|||||
|DNS|TCP и UDP|53|Датчик [!INCLUDE [Product short](includes/product-short.md)]|DNS-серверы|
|Netlogon (SMB, CIFS, SAM-R)|TCP/UDP|445|Датчик [!INCLUDE [Product short](includes/product-short.md)]|Все устройства в сети|
|RADIUS|UDP|1813|RADIUS|Датчик [!INCLUDE [Product short](includes/product-short.md)]|
|**Порты NNR**\*|||||
|HTML через RPC|TCP|Порт 135|[!INCLUDE [Product short](includes/product-short.md)]s|Все устройства в сети|
|NetBIOS|UDP|137|[!INCLUDE [Product short](includes/product-short.md)]s|Все устройства в сети|
|RDP|TCP|3389 (только первый пакет приветствия клиента)|[!INCLUDE [Product short](includes/product-short.md)]s|Все устройства в сети|

\* Один из этих портов является обязательным, но рекомендуем открыть их все.

### <a name="windows-event-logs"></a>Журналы событий Windows

Обнаружение [!INCLUDE [Product short](includes/product-short.md)] основано на определенных [журналах событий Windows](configure-windows-event-collection.md#configure-event-collection), анализируемых датчиком и получаемых с контроллеров домена. Чтобы проводить аудит и включать в журнал событий Windows нужные события, контроллерам домена требуются точные параметры расширенной политики аудита. Дополнительные сведения о настройке правильных политик см. в статье о [проверке расширенной политики аудита](configure-windows-event-collection.md). Чтобы [обеспечить аудит события Windows 8004](configure-windows-event-collection.md#configure-audit-policies) в соответствии с требованиями службы, проверьте [параметры аудита NTLM](/archive/blogs/askds/ntlm-blocking-and-you-application-analysis-and-auditing-methodologies-in-windows-7).

> [!NOTE]
> С помощью учетной записи пользователя службы каталогов датчик запрашивает конечные точки в организации для обнаружения локальных администраторов, использующих SAM-R (вход в сеть), чтобы построить [график путей бокового смещения](use-case-lateral-movement-path.md). Дополнительные сведения см. в разделе [Настройка необходимых разрешений для SAM-R](install-step8-samr.md).

<a name="azure-atp-standalone-sensor-requirements"></a>

## <a name="product-short-standalone-sensor-requirements"></a>Требования к автономному датчику [!INCLUDE [Product short](includes/product-short.md)]

В этом разделе перечислены требования к автономному датчику [!INCLUDE [Product short](includes/product-short.md)].

> [!NOTE]
> Автономные датчики [!INCLUDE [Product short](includes/product-short.md)] не поддерживают сбор записей журнала трассировки событий Windows (ETW), которые предоставляют данные для нескольких обнаружений. Для полного охвата среды рекомендуется развернуть датчик [!INCLUDE [Product short](includes/product-short.md)].

### <a name="general"></a>Общие сведения

Автономный датчик [!INCLUDE [Product short](includes/product-short.md)] поддерживает установку на сервере под управлением Windows Server 2012 R2 или Windows Server 2016 (включая Server Core).
Автономный датчик [!INCLUDE [Product short](includes/product-short.md)] можно установить на сервер, который входит в домен или рабочую группу.
Автономный датчик [!INCLUDE [Product short](includes/product-short.md)] можно использовать для отслеживания контроллеров домена с режимом работы домена Windows 2003 и более поздних версий.

Чтобы автономные датчики могли обмениваться данными с облачной службой, откройте порт 443 *.atp.azure.com в брандмауэре или на прокси-сервере.

Сведения об использовании виртуальных машин с автономным датчиком [!INCLUDE [Product short](includes/product-short.md)] см. в статье [Настройка зеркального отображения портов](configure-port-mirroring.md).

> [!NOTE]
> Требуется не менее 5 ГБ дискового пространства; рекомендуется 10 ГБ. Сюда входит пространство, необходимое для двоичных файлов [!INCLUDE [Product short](includes/product-short.md)], журналов [!INCLUDE [Product short](includes/product-short.md)] и журналов производительности.

### <a name="server-specifications"></a>Спецификации сервера

Для обеспечения оптимальной производительности задайте в **параметре электропитания** компьютера, на котором работает автономный датчик [!INCLUDE [Product short](includes/product-short.md)], значение **Высокая производительность**.

Автономные датчики [!INCLUDE [Product short](includes/product-short.md)] поддерживают отслеживание нескольких контроллеров домена в зависимости от объема сетевого трафика, передаваемого между контроллерами домена.

>[!NOTE]
> При запуске в качестве динамической памяти виртуальной машины или любой другой памяти функция воздушного шага не поддерживается.

Дополнительные сведения о требованиях к оборудованию для автономного датчика [!INCLUDE [Product short](includes/product-short.md)] см. в статье [Планирование ресурсов [!INCLUDE [Product short](includes/product-short.md)]](capacity-planning.md).

### <a name="time-synchronization"></a>Синхронизация времени

Время серверов и контроллеров домена, на которых установлен датчик, должно быть синхронизировано в пределах пяти минут.

### <a name="network-adapters"></a>Сетевые адаптеры

Для автономного датчика [!INCLUDE [Product short](includes/product-short.md)] требуется по крайней мере один адаптер управления и по крайней мере один адаптер записи.

- **Адаптер управления** — будет использоваться для связи в корпоративной сети. Датчик будет использовать этот адаптер для отправки запроса к контроллеру домена для защиты и разрешения учетных записей компьютера.

    При настройке этого адаптера следует настроить следующие параметры:

    - статический IP-адрес, включая шлюз по умолчанию;

    - предпочитаемый и альтернативный DNS-серверы.

    - **DNS-суффикс этого подключения** должен быть DNS-именем домена для каждого отслеживаемого домена.

        ![Настройка DNS-суффикса в дополнительных параметрах TCP/IP](media/dns-suffix.png)

        > [!NOTE]
        > Если автономный датчик [!INCLUDE [Product short](includes/product-short.md)] является членом домена, эту настройку можно выполнять автоматически.

- **Адаптер записи** — используется для записи входящего и исходящего трафика контроллеров домена.

    > [!IMPORTANT]
    >
    > - Следует настроить зеркальное отображение портов адаптера записи в качестве целевого размещения сетевого трафика контроллера домена. Дополнительные сведения см. в статье [Настройка зеркального отображения портов](configure-port-mirroring.md). Как правило, чтобы настроить зеркальное отображение портов, следует привлечь специалистов по обслуживанию сети или группу виртуализации.
    > - Для конкретной среды следует настроить статический немаршрутизируемый IP-адрес (с маской /32) без адресов DNS-сервера и шлюза датчика по умолчанию. Например, 10.10.0.10/32. Это гарантирует, что сетевой адаптер записи может записать максимальное количество трафика, а также что сетевой адаптер управления используется для отправки и получения требуемого сетевого трафика.

### <a name="ports"></a>Порты

В следующей таблице перечислены порты, которые необходимо настроить на адаптере управления для работы автономного датчика [!INCLUDE [Product short](includes/product-short.md)].

|Протокол|Транспорт|Port|От|Кому|
|------------|-------------|--------|-----------|
|**Интернет-порты**||||
|SSL (*.atp.azure.com)|TCP|443|Датчик [!INCLUDE [Product short](includes/product-short.md)]|Облачная служба [!INCLUDE [Product short](includes/product-short.md)]|
|SSL (localhost)|TCP|444|Датчик [!INCLUDE [Product short](includes/product-short.md)]|localhost|
|**Внутренние порты**||||
|LDAP|TCP и UDP|389|Датчик [!INCLUDE [Product short](includes/product-short.md)]|Контроллеры домена|
|Защищенный LDAP (LDAPS)|TCP|636|Датчик [!INCLUDE [Product short](includes/product-short.md)]|Контроллеры домена|
|LDAP для глобального каталога|TCP|3268|Датчик [!INCLUDE [Product short](includes/product-short.md)]|Контроллеры домена|
|LDAPS для глобального каталога|TCP|3269|Датчик [!INCLUDE [Product short](includes/product-short.md)]|Контроллеры домена|
|Kerberos|TCP и UDP|88|Датчик [!INCLUDE [Product short](includes/product-short.md)]|Контроллеры домена|
|Netlogon (SMB, CIFS, SAM-R)|TCP и UDP|445|Датчик [!INCLUDE [Product short](includes/product-short.md)]|Все устройства в сети|
|Служба времени Windows|UDP|123|Датчик [!INCLUDE [Product short](includes/product-short.md)]|Контроллеры домена|
|DNS|TCP и UDP|53|Датчик [!INCLUDE [Product short](includes/product-short.md)]|DNS-серверы|
|Syslog (необязательно)|TCP/UDP|514, в зависимости от конфигурации|Сервер SIEM|Датчик [!INCLUDE [Product short](includes/product-short.md)]|
|RADIUS|UDP|1813|RADIUS|Датчик [!INCLUDE [Product short](includes/product-short.md)]|
|**Порты NNR** \*|||||
|HTML через RPC|TCP|135|[!INCLUDE [Product short](includes/product-short.md)]s|Все устройства в сети|
|NetBIOS|UDP|137|[!INCLUDE [Product short](includes/product-short.md)]s|Все устройства в сети|
|RDP|TCP|3389 (только первый пакет приветствия клиента)|[!INCLUDE [Product short](includes/product-short.md)]s|Все устройства в сети|

\* Один из этих портов является обязательным, но рекомендуем открыть их все.

> [!NOTE]
>
> - С помощью учетной записи пользователя службы каталогов датчик запрашивает конечные точки в организации для обнаружения локальных администраторов, использующих SAM-R (вход в сеть), чтобы построить [график путей бокового смещения](use-case-lateral-movement-path.md). Дополнительные сведения см. в разделе [Настройка необходимых разрешений для SAM-R](install-step8-samr.md).

## <a name="see-also"></a>См. также

- [Средство определения размера [!INCLUDE [Product short](includes/product-short.md)]](https://aka.ms/aatpsizingtool)
- [Архитектура [!INCLUDE [Product short](includes/product-short.md)]](architecture.md)
- [Установка [!INCLUDE [Product short](includes/product-short.md)]](install-step1.md)
- [Разрешение сетевых имен (NNR)](nnr-policy.md)
- [Посетите форум по [!INCLUDE [Product short](includes/product-short.md)].](https://aka.ms/MDIcommunity)
