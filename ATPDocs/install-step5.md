---
title: Общие сведения о настройке параметров датчика удостоверений в защитнике Майкрософт
description: Шаг 5. Установка защитника Майкрософт для идентификации помогает настроить параметры защитника для автономного датчика удостоверений.
ms.date: 09/15/2019
ms.topic: how-to
ms.openlocfilehash: 42dc42caad1b76cf706cf85d34fd60f5c7a52756
ms.sourcegitcommit: a892419a5cb95412e4643c35a9a72092421628ec
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/16/2021
ms.locfileid: "100534027"
---
# <a name="configure-microsoft-defender-for-identity-sensor-settings"></a>Настройка параметров датчика удостоверений в защитнике Майкрософт

В этой статье вы узнаете, как правильно настроить [!INCLUDE [Product long](includes/product-long.md)] параметры датчика для начала просмотра данных. Вам потребуется дополнительная настройка и интеграция, чтобы воспользоваться всеми [!INCLUDE [Product short](includes/product-short.md)] возможностями.

## <a name="prerequisites"></a>Предварительные условия

- [Экземпляр [!INCLUDE [Product short](includes/product-short.md)]](install-step1.md), [подключенный к Active Directory](install-step2.md).
- Скачанная копия [пакета установки датчика [!INCLUDE [Product short](includes/product-short.md)]](install-step3.md) и ключ доступа.

## <a name="configure-sensor-settings"></a>Настройка параметров датчика

После [!INCLUDE [Product short](includes/product-short.md)] установки датчика выполните следующие действия, чтобы настроить [!INCLUDE [Product short](includes/product-short.md)] параметры датчика.

1. Нажмите кнопку **запустить** , чтобы открыть браузер и войти на [!INCLUDE [Product short](includes/product-short.md)] портал.

1. На [!INCLUDE [Product short](includes/product-short.md)] портале перейдите в раздел **Конфигурация** и в разделе **система** выберите **датчики**.

    ![Страница датчиков](media/sensor-config.png)

1. Выберите датчик, который требуется настроить, а затем введите указанные ниже сведения.

    ![Настройка параметров датчика](media/sensor-config-2.png)

    - **Описание**: введите описание [!INCLUDE [Product short](includes/product-short.md)] датчика (необязательно).
    - **Контроллеры домена (FQDN)** (требуется для [!INCLUDE [Product short](includes/product-short.md)] автономного датчика, это невозможно изменить для [!INCLUDE [Product short](includes/product-short.md)] датчика). Введите полное доменное имя контроллера домена и щелкните знак "плюс", чтобы добавить его в список. Например, **dc01.contoso.com**.

    Сведения ниже относятся к серверам, которые указываются в списке **Контроллеры домена**.
    - Все контроллеры домена, трафик которых отслеживается через зеркальное отображение портов, [!INCLUDE [Product short](includes/product-short.md)] должны быть перечислены в списке **контроллеры домена** . Если контроллер домена не указан в списке **Контроллеры домена**, обнаружение подозрительных действий может выполняться не так, как ожидается.
    - По крайней мере один контроллер домена из списка должен быть глобальным каталогом. Это позволяет [!INCLUDE [Product short](includes/product-short.md)] разрешать объекты компьютеров и пользователей в других доменах леса.

    - **Сетевые адаптеры для записи** (обязательно)

    - Для [!INCLUDE [Product short](includes/product-short.md)] датчиков все сетевые адаптеры, используемые для связи с другими компьютерами в Организации.
    - Для [!INCLUDE [Product short](includes/product-short.md)] автономного датчика на выделенном сервере выберите Сетевые адаптеры, настроенные в качестве зеркального порта назначения. Они будут получать зеркально отображенный трафик контроллера домена.

1. Нажмите кнопку **Сохранить**.

## <a name="validate-installations"></a>Проверка установки

Чтобы проверить [!INCLUDE [Product short](includes/product-short.md)] успешность развертывания датчика, проверьте следующее:

1. Проверьте, что служба **Датчик Azure Advanced Threat Protection** запущена. После сохранения [!INCLUDE [Product short](includes/product-short.md)] параметров датчика может потребоваться несколько секунд для запуска службы.

1. Если служба не запускается, просмотрите файл Microsoft.Tri.sensor-Errors.log, расположенный в папке по умолчанию с путем %programfiles%\Azure Advanced Threat Protection sensor\Version X\Logs.

    >[!NOTE]
    > Версия [!INCLUDE [Product short](includes/product-short.md)] обновлений часто для проверки последней версии на [!INCLUDE [Product short](includes/product-short.md)] портале перейдите в раздел **Конфигурация** и затем **о программе**.

1. Перейдите к [!INCLUDE [Product short](includes/product-short.md)] URL-адресу экземпляра. На [!INCLUDE [Product short](includes/product-short.md)] портале Найдите что-нибудь на панели поиска, например пользователя или группы в домене.

1. Проверьте [!INCLUDE [Product short](includes/product-short.md)] подключение на любом устройстве домена, выполнив следующие действия.
    1. Откройте командную строку.
    1. Введите `nslookup`.
    1. Введите на **сервере** полное доменное имя или IP-адрес контроллера домена, на котором [!INCLUDE [Product short](includes/product-short.md)] установлен датчик. Например, `server contosodc.contoso.azure`
        - Обязательно замените ContosoDC. contoso. Azure и contoso. Azure полным доменным [!INCLUDE [Product short](includes/product-short.md)] именем датчика и имени домена соответственно.
    1. Введите `ls -d contoso.azure`.
    1. Повторите шаги 3 и 4 для каждого датчика, который нужно протестировать.
    1. В [!INCLUDE [Product short](includes/product-short.md)] консоли откройте профиль сущности для компьютера, с которого выполнялась проверка подключения.
    1. Проверьте связанные логические действия и убедитесь в наличии соединения.

    > [!NOTE]
    >Если контроллер домена, который вы хотите проверить, является вашим первым развернутым датчиком, подождите не менее 15 минут, чтобы серверная часть базы данных завершила первоначальное развертывание необходимых микрослужб до того, как вы предпримете попытку проверить связанные логические действия для такого контроллера домена.

## <a name="next-steps"></a>Дальнейшие шаги

- [Настройка прокси-сервера](configure-proxy.md)
- [Расширенная политика аудита](configure-windows-event-collection.md)
- [Настройка [!INCLUDE [Product short](includes/product-short.md)] для выполнения удаленных вызовов SAM](install-step8-samr.md)

## <a name="join-the-community"></a>Присоединяйтесь к сообществу!

У вас есть дополнительные вопросы или вы хотите обсудить с другими пользователями особенности использования [!INCLUDE [Product short](includes/product-short.md)] или вопросы, связанные с безопасностью? Присоединяйтесь к [сообществу [!INCLUDE [Product short](includes/product-short.md)]](https://aka.ms/MDIcommunity).
