---
title: Advanced Threat Analytics в защитнике Майкрософт для перемещения удостоверений
description: Узнайте, как переместить существующую установку Advanced Threat Analytics в защитник Майкрософт для идентификации.
ms.date: 10/26/2020
ms.topic: how-to
ms.openlocfilehash: 45b9004bc439a28e144686e3147b94b6019a7a0f
ms.sourcegitcommit: a892419a5cb95412e4643c35a9a72092421628ec
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/16/2021
ms.locfileid: "100533806"
---
# <a name="advanced-threat-analytics-ata-to-microsoft-defender-for-identity"></a>Advanced Threat Analytics (ATA) в защитнике Майкрософт для идентификации

> [!NOTE]
> Окончательная версия ATA доступна в [целом](https://support.microsoft.com/help/4568997/update-3-for-microsoft-advanced-threat-analytics-1-9). Поддержка ATA будет завершаться 12 января 2021. Расширенная поддержка будет продолжена до 2026 января. Дополнительные сведения см. в [нашем блоге](https://techcommunity.microsoft.com/t5/microsoft-security-and/end-of-mainstream-support-for-advanced-threat-analytics-january/ba-p/1539181).

Воспользуйтесь этим руководством, чтобы перейти с существующей установки ATA на службу ( [!INCLUDE [Product long](includes/product-long.md)] ). В этом руководство описаны [!INCLUDE [Product short](includes/product-short.md)] необходимые условия и требования, а также сведения о планировании и завершении перемещения. Также включены этапы проверки и советы по использованию новейших решений для защиты от угроз и безопасности [!INCLUDE [Product short](includes/product-short.md)] после установки.

Дополнительные сведения о различиях между ATA и [!INCLUDE [Product short](includes/product-short.md)] см. в [ [!INCLUDE [Product short](includes/product-short.md)] часто задаваемых вопросах](technical-faq.yml).

В руководстве описаны следующие действия:

> [!div class="checklist"]
>
> - Проверка и подтверждение [!INCLUDE [Product short](includes/product-short.md)] предварительных требований к службе
> - Документирование существующей конфигурации ATA
> - Планирование перехода
> - Настройка и настройка [!INCLUDE [Product short](includes/product-short.md)]  службы
> - Выполнение проверок после перехода
> - Вывод ATA из эксплуатации после перехода

> [!NOTE]
> Переход с [!INCLUDE [Product short](includes/product-short.md)] ATA возможен с любой версии ATA. Однако, поскольку данные не могут быть перемещены из ATA в [!INCLUDE [Product short](includes/product-short.md)] , рекомендуется хранить данные центра ATA и предупреждения, необходимые для текущего исследования, пока все оповещения ATA не будут закрыты или исправлены.

## <a name="prerequisites"></a>Предварительные условия

- Для создания экземпляра требуется клиент Azure Active Directory по крайней мере с одним администратором глобального/безопасности [!INCLUDE [Product short](includes/product-short.md)] . Каждый экземпляр [!INCLUDE [Product short](includes/product-short.md)] поддерживает границу леса Active Directory и режим работы леса (FFL) для Windows 2003 и более поздних версий.

- [!INCLUDE [Product short](includes/product-short.md)] требуется платформа .NET Framework 4,7 или более поздней версии, и может потребоваться контроллер домена (перезапуск), если текущая версия .NET Framework не 4,7 или более поздняя.

- Убедитесь, что контроллеры домена соответствуют всем требованиям [ [!INCLUDE [Product short](includes/product-short.md)] к датчикам](prerequisites.md#azure-atp-sensor-requirements) и ваша среда соответствует всем [ [!INCLUDE [Product short](includes/product-short.md)] требованиям](prerequisites.md).

- Убедитесь, что все контроллеры домена, которые планируется использовать, имеют достаточный доступ к службе через Интернет [!INCLUDE [Product short](includes/product-short.md)] . Проверьте и убедитесь, что контроллеры домена соответствуют [ [!INCLUDE [Product short](includes/product-short.md)] требованиям конфигурации прокси-сервера](configure-proxy.md).

> [!NOTE]
> Это руководством по миграции предназначено [!INCLUDE [Product short](includes/product-short.md)] только для датчиков.

## <a name="plan"></a>План

Перед началом перехода подготовьте следующую информацию:

1. Данные учетной записи вашей [службы каталогов](install-step2.md).
1. [Параметры](setting-syslog.md) уведомлений системного журнала.
1. [Параметры уведомлений](notifications.md) по электронной почте.
1. Членство в группах ролей ATA
1. Интеграция VPN
1. Исключения оповещений
    - Исключения передаются из ATA в [!INCLUDE [Product short](includes/product-short.md)] , поэтому сведения о каждом исключении необходимы для [репликации исключений в [!INCLUDE [Product short](includes/product-short.md)] ](excluding-entities-from-detections.md).
1. Данные учетных записей HoneyToken.
    - Если у вас еще нет выделенных учетных записей HoneyToken, Узнайте больше о [хонэйтокенс в [!INCLUDE [Product short](includes/product-short.md)] ](install-step7.md) и создайте новые учетные записи, которые будут использоваться для этой цели.
1. Полный список всех объектов (компьютеров, групп, пользователей), которые вы хотите вручную пометить как конфиденциальные.
    - Дополнительные сведения о важности [конфиденциальных сущностей](sensitive-accounts.md) см. в статье [!INCLUDE [Product short](includes/product-short.md)] .
1. [Сведения](reports.md) о планировании отчетов (список отчетов и запланированное время).

> [!NOTE]
> Не удаляйте центр ATA, пока не будут удалены все шлюзы ATA. Если удалить центр ATA с еще работающими шлюзами ATA, то ваша организация останется без защиты от угроз.

## <a name="move"></a>Переместить

Выполните переход на [!INCLUDE [Product short](includes/product-short.md)] два простых шага.

### <a name="step-1-create-and-install-defender-for-identity-instance-and-sensors"></a>Шаг 1. Создание и Установка защитника для экземпляра удостоверения и датчиков

1. [Создание нового [!INCLUDE [Product short](includes/product-short.md)] экземпляра](install-step1.md)

1. Удалите упрощенный шлюз ATA на всех контроллерах домена.

1. Установите [!INCLUDE [Product short](includes/product-short.md)] датчик на всех контроллерах домена:
    - [Скачайте [!INCLUDE [Product short](includes/product-short.md)] файлы датчиков](install-step3.md).
    - [Получите [!INCLUDE [Product short](includes/product-short.md)] Ключ доступа](install-step3.md#download-the-setup-package).
    - [Установите [!INCLUDE [Product short](includes/product-short.md)] датчики на контроллерах домена](install-step4.md).

### <a name="step-2-configure-and-validate-defender-for-identity-instance"></a>Шаг 2. Настройка и проверка защитника для экземпляра Identity

- [Настройте датчик](install-step5.md)

> [!NOTE]
> Некоторые задачи в следующем списке невозможно завершить перед установкой [!INCLUDE [Product short](includes/product-short.md)] датчиков, а затем выполнить начальную синхронизацию, например выбрать сущности для постановки тегов, **учитывающих** ручную маркировку. Запланируйте до двух часов времени на выполнение начальной синхронизации.

#### <a name="configuration"></a>Конфигурация

Войдите на [!INCLUDE [Product short](includes/product-short.md)] портал и выполните следующие задачи настройки.

| Шаг    | Действие | Состояние |
|--------------|------------|------------------|
| 1  | Установка [отложенных обновлений на выбранных контроллерах домена](sensor-update.md) | - [ ] |
| 2  | Данные учетных записей [службы каталогов](install-step2.md)| - [ ] |
| 3  | Настройка [уведомлений системного журнала](setting-syslog.md) | - [ ] |
| 4  | Сведения об [интеграции VPN](install-step6-vpn.md)| - [ ] |
| 5  | Настройка [интеграции WDATP](integrate-mde.md)| - [ ] |
| 6  | Настройка учетных записей [HoneyTokens](install-step7.md)| - [ ] |
| 7  | Указание [конфиденциальных объектов](sensitive-accounts.md)| - [ ] |
| 8  | Создание [исключений для оповещений безопасности](excluding-entities-from-detections.md)| - [ ] |
| 9 | [Включение уведомлений по электронной почте](notifications.md) | - [ ] |
| 10  | [Настройка расписания отчетов](reports.md) (список отчетов и запланированное время)| - [ ] |
| 11  | Настройка [разрешений на основе ролей](role-groups.md) | - [ ] |
| 12  | [Настройка уведомлений SIEM (IP-адрес)](configure-event-collection.md#siemsyslog)| - [ ] |

#### <a name="validation"></a>Проверка

На [!INCLUDE [Product short](includes/product-short.md)] портале:

- Просмотрите все [оповещения о работоспособности](health-center.md) на предмет возможных проблем со службой.
- Проверьте [!INCLUDE [Product short](includes/product-short.md)] [журналы ошибок датчика](troubleshooting-using-logs.md) на наличие необычных ошибок.

## <a name="after-the-move"></a>После перехода

В этом разделе руководства описаны действия, которые можно выполнить после завершения перехода.

> [!NOTE]
> Импорт существующих предупреждений системы безопасности из ATA в [!INCLUDE [Product short](includes/product-short.md)] не поддерживается. Обязательно запишите все существующие оповещения ATA или устраните соответствующие проблемы, прежде чем выводить центр ATA из эксплуатации.

- **Выведите центр ATA из эксплуатации**  
  - Для доступа к данным центра ATA после перехода рекомендуется некоторое время сохранять его данные в работе. После вывода центра ATA из эксплуатации количество ресурсов обычно можно уменьшить, особенно если они являются виртуальными машинами.

- **Создайте резервную копию Mongo DB**  
  - Если вы хотите сохранить данные ATA на неопределенный срок, [выполните резервное копирование Mongo DB](/advanced-threat-analytics/ata-database-management#backing-up-the-ata-database).

## <a name="mission-accomplished"></a>Все готово

Поздравляем! Переход с ATA на [!INCLUDE [Product short](includes/product-short.md)] завершен.

## <a name="next-steps"></a>Дальнейшие шаги

Дополнительные сведения о [[!INCLUDE [Product short](includes/product-short.md)]](what-is.md) функциях, функциях и [оповещениях системы безопасности](understanding-security-alerts.md).

## <a name="join-the-community"></a>Присоединяйтесь к сообществу!

У вас есть дополнительные вопросы или вы хотите обсудить с другими пользователями особенности использования [!INCLUDE [Product short](includes/product-short.md)] или вопросы, связанные с безопасностью? Присоединяйтесь к [сообществу [!INCLUDE [Product short](includes/product-short.md)]](https://techcommunity.microsoft.com/t5/Azure-Advanced-Threat-Protection/bd-p/AzureAdvancedThreatProtection).
