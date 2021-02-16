---
title: Оценка уровня безопасности удостоверений в защитнике Майкрософт
description: В этой статье приводятся общие сведения о защитнике Майкрософт для отчетов об оценке уровня безопасности удостоверений.
ms.date: 10/26/2020
ms.topic: how-to
ms.openlocfilehash: 3b3f20ac50e3b5b687dd6ece8b421c84288a3126
ms.sourcegitcommit: a892419a5cb95412e4643c35a9a72092421628ec
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/16/2021
ms.locfileid: "100533857"
---
# <a name="microsoft-defender-for-identitys-identity-security-posture-assessments"></a>Оценка уровня безопасности удостоверений в защитнике Майкрософт

Как правило, организации всех размеров имеют ограниченную видимость относительно того, могут ли их локальные приложения и службы представлять уязвимость для организации. Проблема ограниченной видимости особенно актуальна для неподдерживаемых или устаревших компонентов.

Хотя компания может постоянно вкладывать значительное время и усилия в усиление безопасности удостоверений и инфраструктуры идентификации (например, Active Directory, Active Directory Connect), легко можно остаться в неведении о простейших неверных настройках и использовании устаревших версий компонентов, что представляет одну из самых крупных угроз для организации. Исследование безопасности Майкрософт показывает, что большинство атак с удостоверениями используют распространенные неправильные настройки в Active Directory, и указывает на то, что устаревшие компоненты (например, протокол NTLMv1) продолжают использоваться для взлома удостоверений и успешного проникновения в организации. Чтобы бороться с этой эффективностью, [!INCLUDE [Product long](includes/product-long.md)] теперь предлагает возможность профилактической оценки безопасности идентификации, которая позволяет обнаруживать и предлагать действия по улучшению в локальных конфигурациях Active Directory.

## <a name="what-do-defender-for-identity-identity-security-posture-assessments-provide"></a>Что обеспечивает защитник для оценки уровня безопасности удостоверений идентификации?

- Используются обнаружения и контекстные данные по известным уязвимым компонентам и неправильным настройкам, а также предлагаются соответствующие пути исправления.
- [!INCLUDE [Product short](includes/product-short.md)] обнаруживает не только подозрительные действия, но и активно отслеживает локальные удостоверения и инфраструктуру идентификации для слабых участков, используя имеющийся [!INCLUDE [Product short](includes/product-short.md)] датчик.
- Создаются точные отчеты об оценке текущей системы безопасности организации, что позволяет быстро вести реагирование и мониторинг в непрерывном цикле.

## <a name="how-do-i-get-started"></a>С чего начать?

### <a name="access"></a>Access

[!INCLUDE [Product short](includes/product-short.md)] Оценка безопасности доступна с помощью портала Microsoft Cloud App Security после включения [!INCLUDE [Product short](includes/product-short.md)] интеграции. Сведения о том, как интегрировать [!INCLUDE [Product short](includes/product-short.md)] в Cloud App Security, см. в разделе [ [!INCLUDE [Product short](includes/product-short.md)] Интеграция](/cloud-app-security/aatp-integration).

### <a name="licensing"></a>Лицензирование

Для доступа к [!INCLUDE [Product short](includes/product-short.md)] отчетам оценки безопасности в Cloud App Security не требуется лицензия Cloud App Security, [!INCLUDE [Product short](includes/product-short.md)] требуется только лицензия.

## <a name="access-defender-for-identity-using-cloud-app-security"></a>Доступ к защитнику для удостоверения с помощью Cloud App Security

Основы использования портала Cloud App Security см. в [кратком руководстве по Cloud App Security](/cloud-app-security/getting-started-with-cloud-app-security).

**Оценки состояния безопасности удостоверений**

[!INCLUDE [Product short](includes/product-short.md)] предлагает следующие средства оценки уровня безопасности для идентификации. Каждая оценка — это скачиваемый отчет с инструкциями по использованию и инструментами для создания плана действий, позволяющего исправить или устранить проблему.

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
    ![Доступ [! ВКЛЮЧИТЬ [продукт Short] (включая/Product-Short. md)] отчеты об уровне безопасности удостоверений в Cloud App Security](media/cas-isp-report-1.png)
1. Выберите **Исследовать** в меню слева, а затем в раскрывающемся меню выберите **Уровень безопасности удостоверений**.
1. В открывшемся списке **Отчеты об оценке безопасности** выберите оценку уровня безопасности удостоверений, которую вы хотите просмотреть.

## <a name="next-steps"></a>Дальнейшие шаги

- [Дополнительные сведения об использовании Cloud App Security с [!INCLUDE [Product short](includes/product-short.md)]](activities-filtering-mcas.md)
- [Посетите форум по [!INCLUDE [Product short](includes/product-short.md)].](https://aka.ms/MDIcommunity)
