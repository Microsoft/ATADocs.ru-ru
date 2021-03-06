---
title: Обновление датчиков Microsoft Defender для удостоверений
description: В этой статье показано, как выполнить и отложить обновления датчиков в Microsoft Defender для удостоверений.
ms.date: 10/27/2020
ms.topic: how-to
ms.openlocfilehash: 3d77e5ebd6fdec2647f08aa32c1e2076a1487293
ms.sourcegitcommit: a892419a5cb95412e4643c35a9a72092421628ec
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/16/2021
ms.locfileid: "100534418"
---
# <a name="update-microsoft-defender-for-identity-sensors"></a>Обновление датчиков Microsoft Defender для удостоверений

Чтобы обеспечить наилучшую защиту для вашей организации, своевременно обновляйте датчики [!INCLUDE [Product long](includes/product-long.md)].

Как правило, [!INCLUDE [Product long](includes/product-long.md)] обновляется несколько раз в месяц, предоставляя новые типы обнаружения, новые функции и улучшения производительности. Обычно эти обновления включают соответствующие незначительные обновления датчиков. Датчики [!INCLUDE [Product short](includes/product-short.md)] и соответствующие обновления никогда не имеют разрешений на запись в контроллеры домена. Пакеты обновления датчиков влияют только на датчики [!INCLUDE [Product short](includes/product-short.md)] и их функции обнаружения.

## <a name="defender-for-identity-sensor-update-types"></a>Типы обновления датчиков Defender для удостоверений

Датчики [!INCLUDE [Product short](includes/product-short.md)] поддерживают два типа обновлений.

- Обновления дополнительной версии
  - Часто
  - Установка MSI и внесение изменений в реестр не требуется
  - Перезапущены: службы датчика [!INCLUDE [Product short](includes/product-short.md)]
  - Не запущены: службы контроллера домена и операционная система сервера

- Обновления основной версии
  - Редко
  - Содержат значительные изменения
  - Перезапущены: службы датчика [!INCLUDE [Product short](includes/product-short.md)]
  - Возможно потребуется перезагрузка сервера: службы контроллера домена и операционная система сервера

> [!NOTE]
>
> - Управляйте автоматической перезагрузкой датчика (для **основных** обновлений) на странице настройки на портале [!INCLUDE [Product short](includes/product-short.md)].
> - Датчик [!INCLUDE [Product short](includes/product-short.md)] всегда резервирует не менее 15 % памяти и ресурсов ЦП, доступных на контроллере домена, на котором он установлен. Если [!INCLUDE [Product short](includes/product-short.md)] потребляет слишком много памяти, служба автоматически останавливается и перезапускается службой обновления датчиков [!INCLUDE [Product short](includes/product-short.md)].

## <a name="delayed-sensor-update"></a>Отложенное обновление датчиков

Учитывая высокую скорость разработки и выпуска обновлений [!INCLUDE [Product short](includes/product-short.md)], вы можете определить набор датчиков в качестве круга отложенного обновления. Это обеспечит поэтапное обновление датчиков. [!INCLUDE [Product short](includes/product-short.md)] позволяет выбрать способ обновления датчиков и настроить для каждого датчика **отложенное обновление**.

Если отложенное обновление не настроено, датчики будут обновляться автоматически при каждом обновлении [!INCLUDE [Product short](includes/product-short.md)]. Для датчиков с настроенным **отложенным обновлением** задержка составляет 72 ч после официального выпуска каждого обновления службы.

Функция **отложенного обновления** позволяет добавить определенные датчики в круг автоматического обновления, когда все обновления выполняются автоматически. Для остальных датчиков можно установить задержку, чтобы вы могли удостовериться в том, что автоматическое обновление выбранных датчиков выполнено успешно.

> [!NOTE]
> В случае возникновения ошибок и неудачного обновления датчика, создайте запрос в службу поддержки. Чтобы дополнительно усилить защиту прокси-сервера, разрешив ему обмениваться данными только с экземпляром, обратитесь к разделу [Настройка прокси-сервера](configure-proxy.md).
Между датчиками и облачной службой Azure используется строгая взаимная проверка подлинности на основе сертификатов.

Каждое обновление протестировано и проверено для всех поддерживаемых операционных систем и оказывает минимальное воздействие на сеть и работу организации.

Настройка отложенного обновления датчика

1. На портале [!INCLUDE [Product short](includes/product-short.md)] щелкните значок параметров и выберите пункт **Конфигурация**.
1. Щелкните вкладку **Обновления**.
1. В строке таблицы рядом с каждым нужным датчиком передвиньте ползунок **Отложенное обновление** в положение **Включено**.
1. Нажмите кнопку **Сохранить**.

## <a name="sensor-update-process"></a>Процесс обновления датчика

Каждые несколько минут датчики [!INCLUDE [Product short](includes/product-short.md)] проверяют наличие новой версии. После обновления облачного экземпляра [!INCLUDE [Product short](includes/product-short.md)] до новой версии служба датчиков [!INCLUDE [Product short](includes/product-short.md)] запускает процесс обновления.

1. Облачный экземпляр [!INCLUDE [Product short](includes/product-short.md)] обновляется до последней версии.
1. Служба обновления датчиков [!INCLUDE [Product short](includes/product-short.md)] определяет, что появилась обновленная версия.
1. Для датчиков без заданного **отложенного обновления** запускается процесс обновления.
    1. Служба обновления датчиков [!INCLUDE [Product short](includes/product-short.md)] получает обновленную версию из облачной службы (в формате CAB-файла).
    1. Служба обновления датчиков [!INCLUDE [Product short](includes/product-short.md)] проверяет сигнатуру файла.
    1. Служба обновления датчиков [!INCLUDE [Product short](includes/product-short.md)] извлекает CAB-файл в новую папку в каталоге установки датчика. По умолчанию это *C:\Program Files\Azure Advanced Threat Protection Sensor\<version number>* .
    1. Служба датчиков [!INCLUDE [Product short](includes/product-short.md)] указывает на новые файлы, извлеченные из CAB-файла.
    1. Служба обновления датчиков [!INCLUDE [Product short](includes/product-short.md)] перезапускает службу датчиков [!INCLUDE [Product short](includes/product-short.md)].
        > [!NOTE]
        > Незначительные обновления датчика выполняются без установки MSI, изменения значений реестра или других системных файлов. Даже перезапуск с ожиданием не влияет на процесс обновления датчика.
    1. Датчики запускаются с обновленной версией.
    1. Датчик получает разрешение от облачной службы Azure. Вы можете проверить состояние датчиков на странице **Обновления**.
    1. Следующий датчик начинает процесс обновления.

1. Через 72 часа после обновления облачной службы [!INCLUDE [Product short](includes/product-short.md)] для датчиков с настроенной **задержкой** обновление запускается так же, как и для датчиков, обновляемых автоматически.

![Обновление датчиков](media/sensor-update.png)

Если обновление датчиков не удается завершить, создается оповещение о работоспособности, которое отправляется в виде уведомления.

![Сбой обновления датчиков](media/sensor-outdated.png)

## <a name="see-also"></a>См. также

- [Настройка пересылки событий](configure-event-forwarding.md)
- [Предварительные требования для работы с [!INCLUDE [Product short](includes/product-short.md)]](prerequisites.md)
- [Посетите форум по [!INCLUDE [Product short](includes/product-short.md)].](https://aka.ms/MDIcommunity)
