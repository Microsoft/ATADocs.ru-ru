---
title: Переход с Advanced Threat Analytics на Расширенную защиту от угроз Azure
description: Узнайте, как перевести существующую установку Advanced Threat Analytics на Azure ATP.
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 10/16/2019
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.service: azure-advanced-threat-protection
ms.assetid: e734e382-c4b1-43ca-9a8d-96c91daf2578
ms.reviewer: itargoet
ms.suite: ems
ms.openlocfilehash: eb37bf60d0de0ee09afa74e6a23c54ca40ee32c3
ms.sourcegitcommit: fbb0768c392f9bccdd7e4adf0e9a0303c8d1922c
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2020
ms.locfileid: "84774627"
---
# <a name="advanced-threat-analytics-ata-to-azure-advanced-threat-protection-azure-atp"></a>Переход с Advanced Threat Analytics (ATA) на Расширенную защиту от угроз Azure (Azure ATP)

Это руководство поможет вам перейти с существующей установки ATA на службу "Расширенная защита от угроз Azure" (Azure ATP). В нем приведены предварительные и основные требования к Azure ATP и подробно описано планирование и выполнение перехода. Кроме того, здесь приведены необходимые действия по проверке, а также советы по использованию новейших решений безопасности и защиты от угроз в сочетании с Azure ATP после установки службы.

Дополнительные сведения о различиях между ATA и Azure ATP см. в статье [Часто задаваемые вопросы об Azure ATP](https://docs.microsoft.com/azure-advanced-threat-protection/atp-technical-faq#what-is-azure-atp).

В руководстве описаны следующие действия:

> [!div class="checklist"]
>
> - Просмотр и проверка предварительных требований для службы Azure ATP
> - Документирование существующей конфигурации ATA
> - Планирование перехода
> - Установка и настройка службы Azure ATP
> - Выполнение проверок после перехода
> - Вывод ATA из эксплуатации после перехода

> [!NOTE]
> Переход на Azure ATP возможен с любой версии ATA. Однако поскольку перенести данные из ATA в Azure ATP невозможно, рекомендуется не удалять ваши данные и оповещения центра ATA, необходимые для текущего анализа, пока не будут закрыты все оповещения или устранены соответствующие проблемы.

## <a name="prerequisites"></a>Предварительные условия

- Для создания экземпляра Azure ATP требуется клиент Azure Active Directory с хотя бы одним глобальным администратором или администратором безопасности. Каждый экземпляр Azure ATP поддерживает границу леса Active Directory и режим работы леса (FFL) для Windows 2003 и более поздних версий.

- Azure ATP требует наличия .NET Framework 4.7 или более поздней версии и может потребовать контроллер домена (с перезагрузкой), если вы используете .NET Framework версии ниже 4.7.

- Убедитесь, что контроллеры домена отвечают всем [требованиям датчиков Azure ATP](https://docs.microsoft.com/azure-advanced-threat-protection/atp-prerequisites#azure-atp-sensor-requirements) и ваша среда удовлетворяет всем [требованиям Azure ATP](https://docs.microsoft.com/azure-advanced-threat-protection/atp-prerequisites).

- Все контроллеры домена, которые вы планируете использовать, должны иметь необходимое подключение к Интернету для работы со службой Azure ATP. Проверьте и подтвердите соответствие контроллеров домена [требованиям конфигурации прокси-сервера Azure ATP](https://docs.microsoft.com/azure-advanced-threat-protection/configure-proxy).

> [!NOTE]
> Это руководство по миграции предназначено только для датчиков Azure ATP. Дополнительные сведения см. в разделе [Выбор правильного типа датчика для развертывания](https://docs.microsoft.com/azure-advanced-threat-protection/atp-capacity-planning#choosing-the-right-sensor-type-for-your-deployment).

## <a name="plan"></a>План

Перед началом перехода подготовьте следующую информацию:

1. Данные учетной записи вашей [службы каталогов](https://docs.microsoft.com/azure-advanced-threat-protection/install-atp-step2).
1. [Параметры](https://docs.microsoft.com/azure-advanced-threat-protection/setting-syslog) уведомлений системного журнала.
1. [Параметры уведомлений](https://docs.microsoft.com/azure-advanced-threat-protection/notifications) по электронной почте.
1. Членство в группах ролей ATA
1. Интеграция VPN
1. Исключения оповещений
    - Исключения не переносятся из ATA в Azure ATP, поэтому необходимы сведения о каждом исключении для [репликации исключений в Azure ATP](https://docs.microsoft.com/azure-advanced-threat-protection/excluding-entities-from-detections).
1. Данные учетных записей HoneyToken.
    - Если у вас нет выделенных учетных записей HoneyToken, то прочтите о [HoneyToken в Azure ATP](https://docs.microsoft.com/azure-advanced-threat-protection/install-atp-step7) и создайте новые учетные записи для текущей задачи.
1. Полный список всех объектов (компьютеров, групп, пользователей), которые вы хотите вручную пометить как конфиденциальные.
    - См. дополнительные сведения о важности [конфиденциальных объектов](https://docs.microsoft.com/azure-advanced-threat-protection/sensitive-accounts) в Azure ATP.
1. [Сведения](https://docs.microsoft.com/azure-advanced-threat-protection/reports) о планировании отчетов (список отчетов и запланированное время).
1. Наименование и данные каждого упрощенного шлюза ATA, являющегося потенциальным синхронизатором домена Azure ATP.
    - См. дополнительные сведения о важности [потенциальных синхронизаторов домена](https://docs.microsoft.com/azure-advanced-threat-protection/install-atp-step5#configure-sensor-settings) в Azure ATP.

> [!NOTE]
> Не удаляйте центр ATA, пока не будут удалены все шлюзы ATA. Если удалить центр ATA с еще работающими шлюзами ATA, то ваша организация останется без защиты от угроз.

## <a name="move"></a>Переместить

Выполните переход на Azure ATP в два простых шага:

### <a name="step-1-create-and-install-azure-atp-instance-and-sensors"></a>Шаг 1. Создание и установка экземпляра и датчиков Azure ATP

1. [Создайте экземпляр Azure ATP.](https://docs.microsoft.com/azure-advanced-threat-protection/install-atp-step1)

2. Удалите упрощенный шлюз ATA на всех контроллерах домена.

3. Установите датчик Azure ATP на всех контроллерах домена:
    - [Скачайте файлы датчика Azure ATP](https://docs.microsoft.com/azure-advanced-threat-protection/install-atp-step3).
    - [Получите ключ доступа Azure ATP](https://docs.microsoft.com/azure-advanced-threat-protection/install-atp-step3#download-the-setup-package).
    - [Установите датчики Azure ATP на контроллерах домена](https://docs.microsoft.com/azure-advanced-threat-protection/install-atp-step4).

### <a name="step-2-configure-and-validate-azure-atp-instance"></a>Шаг 2. Настройка и проверка экземпляра Azure ATP

- [Настройте датчик](https://docs.microsoft.com/azure-advanced-threat-protection/install-atp-step5)

> [!NOTE]
> Некоторые задачи в следующем списке невозможно выполнить до установки датчиков Azure ATP и последующей начальной синхронизации, например, невозможно выбрать объекты и пометить их как **конфиденциальные** вручную. Запланируйте до двух часов времени на выполнение начальной синхронизации.

#### <a name="configuration"></a>Конфигурация

Войдите на портал Azure ATP и выполните следующие задачи по настройке.

| Шаг    | Действие | Состояние |
|--------------|------------|------------------|
| 1  | Установка [отложенных обновлений на выбранных контроллерах домена](https://docs.microsoft.com/azure-advanced-threat-protection/sensor-update) | — [ ] |
| 2  | Данные учетных записей [службы каталогов](https://docs.microsoft.com/azure-advanced-threat-protection/install-atp-step2)| — [ ] |
| 3  | Настройка [потенциальных синхронизаторов домена](https://docs.microsoft.com/azure-advanced-threat-protection/install-atp-step5#configure-sensor-settings) | — [ ] |
| 4  | Настройка [уведомлений системного журнала](https://docs.microsoft.com/azure-advanced-threat-protection/setting-syslog) | — [ ] |
| 5  | Сведения об [интеграции VPN](https://docs.microsoft.com/azure-advanced-threat-protection/install-atp-step6-vpn)| — [ ] |
| 6  | Настройка [интеграции WDATP](https://docs.microsoft.com/azure-advanced-threat-protection/integrate-wd-atp)| — [ ] |
| 7  | Настройка учетных записей [HoneyTokens](https://docs.microsoft.com/azure-advanced-threat-protection/install-atp-step7)| — [ ] |
| 8  | Указание [конфиденциальных объектов](https://docs.microsoft.com/azure-advanced-threat-protection/sensitive-accounts)| — [ ] |
| 9  | Создание [исключений для оповещений безопасности](https://docs.microsoft.com/azure-advanced-threat-protection/excluding-entities-from-detections)| — [ ] |
| 10 | [Включение уведомлений по электронной почте](https://docs.microsoft.com/azure-advanced-threat-protection/notifications) | — [ ] |
| 11  | [Настройка расписания отчетов](https://docs.microsoft.com/azure-advanced-threat-protection/reports) (список отчетов и запланированное время)| — [ ] |
| 12  | Настройка [разрешений на основе ролей](https://docs.microsoft.com/azure-advanced-threat-protection/atp-role-groups) | — [ ] |
| 12  | [Настройка уведомлений SIEM (IP-адрес)](https://docs.microsoft.com/azure-advanced-threat-protection/configure-event-collection#siemsyslog)| — [ ] |

#### <a name="validation"></a>Проверка

На портале Azure ATP:

- Просмотрите все [оповещения о работоспособности](https://docs.microsoft.com/azure-advanced-threat-protection/atp-health-center) на предмет возможных проблем со службой.
- Проверьте [журналы ошибок датчика](https://docs.microsoft.com/azure-advanced-threat-protection/troubleshooting-atp-using-logs) Azure ATP на наличие необычных ошибок.

## <a name="after-the-move"></a>После перехода

В этом разделе руководства описаны действия, которые можно выполнить после завершения перехода.

> [!NOTE]
> Импорт существующих оповещений системы безопасности из ATA в ATP не поддерживается. Обязательно запишите все существующие оповещения ATA или устраните соответствующие проблемы, прежде чем выводить центр ATA из эксплуатации.

- **Выведите центр ATA из эксплуатации**  
  - Для доступа к данным центра ATA после перехода рекомендуется некоторое время сохранять его данные в работе. После вывода центра ATA из эксплуатации количество ресурсов обычно можно уменьшить, особенно если они являются виртуальными машинами.

- **Создайте резервную копию Mongo DB**  
  - Если вы хотите сохранить данные ATA на неопределенный срок, [выполните резервное копирование Mongo DB](https://docs.microsoft.com/advanced-threat-analytics/ata-database-management#backing-up-the-ata-database).

## <a name="mission-accomplished"></a>Все готово

Поздравляем! Переход с ATA на Azure ATP завершен.

## <a name="next-steps"></a>Дальнейшие шаги

См. дополнительные сведения о возможностях, функциях и [оповещениях системы безопасности](https://docs.microsoft.com/azure-advanced-threat-protection/understanding-security-alerts)[Azure ATP](https://docs.microsoft.com/azure-advanced-threat-protection/what-is-atp).

## <a name="join-the-community"></a>Присоединяйтесь к сообществу!

Возникли дополнительные вопросы или желание обсудить с другими пользователями службу Azure ATP и связанные с ней вопросы безопасности? Присоединяйтесь к [сообществу Azure ATP](https://techcommunity.microsoft.com/t5/Azure-Advanced-Threat-Protection/bd-p/AzureAdvancedThreatProtection)!
