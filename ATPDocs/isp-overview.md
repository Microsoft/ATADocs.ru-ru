---
title: Оценка состояния безопасности удостоверений Расширенной защиты от угроз Azure
description: В этой статье представлен обзор отчетов об оценке состояния безопасности удостоверений Azure ATP.
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 09/16/2019
ms.topic: how-to
ms.collection: M365-security-compliance
ms.service: azure-advanced-threat-protection
ms.assetid: 71b15bd9-3183-4e24-b18a-705023ccc313
ms.reviewer: itargoet
ms.suite: ems
ms.openlocfilehash: eaef6571a11852e66634e9043daa25ec8fdbe2ef
ms.sourcegitcommit: c7c0a4c9f7507f3e8e0f219798ed7d347c03e792
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/22/2020
ms.locfileid: "90910196"
---
# <a name="azure-atps-identity-security-posture-assessments"></a>Оценки состояния безопасности удостоверений Azure ATP

[!INCLUDE [Rebranding notice](includes/rebranding.md)]

Как правило, организации всех размеров имеют ограниченную видимость относительно того, могут ли их локальные приложения и службы представлять уязвимость для организации. Проблема ограниченной видимости особенно актуальна для неподдерживаемых или устаревших компонентов.

Хотя компания может постоянно вкладывать значительное время и усилия в усиление безопасности удостоверений и инфраструктуры идентификации (например, Active Directory, Active Directory Connect), легко можно остаться в неведении о простейших неверных настройках и использовании устаревших версий компонентов, что представляет одну из самых крупных угроз для организации. Исследование безопасности Майкрософт показывает, что большинство атак с удостоверениями используют распространенные неправильные настройки в Active Directory, и указывает на то, что устаревшие компоненты (например, протокол NTLMv1) продолжают использоваться для взлома удостоверений и успешного проникновения в организации. Для эффективной борьбы с этим Azure ATP теперь предлагает возможность профилактической оценки безопасности удостоверений, которая позволяет обнаруживать проблемы и предлагать действия по улучшению в локальных конфигурациях Active Directory.

## <a name="what-do-azure-atp-identity-security-posture-assessments-provide"></a>Как проводятся оценки состояния безопасности удостоверений Azure ATP?

- Используются обнаружения и контекстные данные по известным уязвимым компонентам и неправильным настройкам, а также предлагаются соответствующие пути исправления.
- Azure ATP не только обнаруживает подозрительные действия, но и активно проверяет локальные удостоверения и инфраструктуру идентификации на наличие слабых участков, используя имеющийся датчик Azure ATP.
- Создаются точные отчеты об оценке текущей системы безопасности организации, что позволяет быстро вести реагирование и мониторинг в непрерывном цикле.

## <a name="how-do-i-get-started"></a>С чего начать?

### <a name="access"></a>Access

Оценка безопасности Azure ATP доступна на портале Microsoft Cloud App Security после включения интеграции с Azure ATP. Сведения о том, как интегрировать Azure ATP с Cloud App Security, см. в статье об [интеграции Azure ATP](/cloud-app-security/aatp-integration).

### <a name="licensing"></a>Лицензирование

Для доступа к отчетам оценки безопасности Azure ATP в Cloud App Security не требуется лицензия на Cloud App Security; нужна только лицензия Azure ATP.

## <a name="access-azure-atp-using-cloud-app-security"></a>Доступ к Azure ATP через Cloud App Security

Основы использования портала Cloud App Security см. в [кратком руководстве по Cloud App Security](/cloud-app-security/getting-started-with-cloud-app-security).

**Оценки состояния безопасности удостоверений**

Оценки состояния безопасности удостоверений в Azure ATP включает следующие возможности. Каждая оценка — это скачиваемый отчет с инструкциями по использованию и инструментами для создания плана действий, позволяющего исправить или устранить проблему.

**Отчеты об оценке**

- [Служба очереди печати принтера на контроллерах домена](cas-isp-print-spooler.md)
- [Неактивные сущности в конфиденциальных группах](cas-isp-dormant-entities.md)
- [Раскрытие сущностями учетных данных в виде открытого текста](cas-isp-clear-text.md)
- [Использование Microsoft LAPS](cas-isp-laps.md)
- [Использование устаревших протоколов](cas-isp-legacy-protocols.md)
- [Пути бокового смещения с максимальным риском](cas-isp-riskiest-lmp.md)
- [Неотслеживаемые контроллеры домена](cas-isp-unmonitored-domain-controller.md)
- [Небезопасные атрибуты учетной записи](cas-isp-unsecure-account-attributes.md)
- [Незащищенное делегирование Kerberos](cas-isp-unconstrained-kerberos.md)
- [Небезопасные атрибуты журнала ИД безопасности](cas-isp-unsecure-sid-history-attribute.md)
- [Использование ненадежного шифра](cas-isp-weak-cipher.md)

Для доступа к оценкам состояния безопасности удостоверений выполните следующие действия.

1. Откройте портал **Microsoft Cloud App Security**.
    ![Доступ к отчетам по безопасности удостоверений Azure ATP в Cloud App Security](media/atp-cas-isp-report-1.png)
1. Выберите **Исследовать** в меню слева, а затем в раскрывающемся меню выберите **Уровень безопасности удостоверений**.
1. В открывшемся списке **Отчеты об оценке безопасности** выберите оценку уровня безопасности удостоверений, которую вы хотите просмотреть.

## <a name="next-steps"></a>Дальнейшие шаги

- [Дополнительные сведения об использовании Cloud App Security с Azure ATP](activities-filtering-mcas.md)
- [Загляните на форум Azure ATP!](https://aka.ms/azureatpcommunity)