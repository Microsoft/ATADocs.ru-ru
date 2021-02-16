---
title: Поддержка нескольких лесов удостоверений в защитнике Майкрософт
description: Поддержка нескольких лесов Active Directory в защитнике Майкрософт для идентификации.
ms.date: 10/26/2020
ms.topic: conceptual
ms.openlocfilehash: c0a5c135d73ecbcdd23b6ed2ea8a12a212a0f23d
ms.sourcegitcommit: a892419a5cb95412e4643c35a9a72092421628ec
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/16/2021
ms.locfileid: "100533670"
---
# <a name="microsoft-defender-for-identity-multi-forest-support"></a>Поддержка нескольких лесов удостоверений в защитнике Майкрософт

## <a name="multi-forest-support-set-up"></a>Настройка поддержки нескольких лесов

[!INCLUDE [Product long](includes/product-long.md)] поддерживает Организации с несколькими лесами, обеспечивая возможность легко отслеживать пользователей активности и профилей в лесах.

В организациях, как правило, есть несколько лесов Active Directory. Все они используются для разных целей, например для поддержки устаревшей инфраструктуры сделок слияния и поглощения, географического распределения и границ безопасности (красный лес). Вы можете защитить несколько лесов с помощью [!INCLUDE [Product short](includes/product-short.md)] , обеспечивая возможность отслеживать и исследовать всю сеть с помощью одной панели прозрачности.

Поддержка нескольких лесов Active Directory обеспечивает следующие возможности:

- просматривать и анализировать действия, выполняемые пользователями в нескольких лесах, в едином представлении;
- более эффективное обнаружение ложных срабатываний и сокращение их числа благодаря расширенной интеграции Active Directory и сопоставлению учетных записей;
- расширенный контроль и упрощенное развертывание; Улучшены оповещения о работоспособности и отчеты о покрытии, когда все контроллеры домена отслеживаются из одной [!INCLUDE [Product short](includes/product-short.md)] консоли.

## <a name="defender-for-identity-detection-activity-across-multiple-forests"></a>Защитник для действия обнаружения удостоверений в нескольких лесах

Для обнаружения действий между лесами [!INCLUDE [Product short](includes/product-short.md)] датчики запрашивают контроллеры домена в удаленных лесах, чтобы создать профили для всех участвующих сущностей (включая пользователей и компьютеры из удаленных лесов).

- [!INCLUDE [Product short](includes/product-short.md)] датчики можно установить на контроллерах домена во всех лесах, даже в лесах без доверия.
- Добавьте дополнительные учетные данные на странице службы каталогов для поддержки недоверенных лесов в вашей среде.
  - Для поддержки всех лесов с двусторонним доверием требуются только один учетные данные.
  - Дополнительные учетные данные требуются только для каждого леса с доверием без доверия Kerberos или без доверия.
  - Ограничение по умолчанию — 10 недоверенных лесов на [!INCLUDE [Product short](includes/product-short.md)] экземпляр. Если в вашей организации больше 10 лесов, обратитесь в службу поддержки.

![[!INCLUDE [Product short](includes/product-short.md)]: этап 1 приветствия](media/directory-services-add-no-trust-forests.png)

### <a name="requirements"></a>Требования

- Пользователь, настраиваемый в [!INCLUDE [Product short](includes/product-short.md)] консоли в разделе **службы каталогов** , должен быть доверенным во всех остальных лесах и должен иметь по крайней мере разрешение только на чтение для выполнения запросов LDAP на контроллерах домена.
- Если [!INCLUDE [Product short](includes/product-short.md)] автономные датчики установлены на автономных компьютерах, а не непосредственно на контроллерах домена, убедитесь, что компьютерам разрешено взаимодействовать со всеми контроллерами домена удаленного леса с помощью протокола LDAP.

- [!INCLUDE [Product short](includes/product-short.md)]Чтобы взаимодействовать с [!INCLUDE [Product short](includes/product-short.md)] датчиками и [!INCLUDE [Product short](includes/product-short.md)] автономными датчиками, откройте следующие порты на каждом компьютере, на котором [!INCLUDE [Product short](includes/product-short.md)] установлен датчик:

  |Протокол|Транспорт|Port|В/Из|Direction|
  |----|----|----|----|----|
  |**Интернет-порты**||||
  |SSL (*.atp.azure.com)|TCP|443|Облачная служба [!INCLUDE [Product short](includes/product-short.md)]|Исходящее|
  |**Внутренние порты**||||
  |LDAP|TCP и UDP|389|Контроллеры домена|Исходящее|
  |Защищенный LDAP (LDAPS)|TCP|636|Контроллеры домена|Исходящее|
  |LDAP для глобального каталога|TCP|3268|Контроллеры домена|Исходящее|
  |LDAPS для глобального каталога|TCP|3269|Контроллеры домена|Исходящее|

## <a name="multi-forest-support-network-traffic-impact"></a>Влияние поддержки нескольких лесов на трафик

При [!INCLUDE [Product short](includes/product-short.md)] сопоставлении лесов используется процесс, который влияет на следующее:

- После [!INCLUDE [Product short](includes/product-short.md)] запуска датчика он запрашивает удаленные Active Directoryные леса и получает список пользователей и данные компьютера для создания профиля.
- Каждые 5 минут каждый [!INCLUDE [Product short](includes/product-short.md)] датчик запрашивает один контроллер домена из каждого домена из каждого леса, чтобы сопоставлять все леса в сети.
- Каждый [!INCLUDE [Product short](includes/product-short.md)] датчик сопоставляет леса с помощью объекта "трустеддомаин" в Active Directory, войдя в систему и проверяя тип доверия.
- Вы также можете увидеть нерегламентированный трафик, когда [!INCLUDE [Product short](includes/product-short.md)] датчик обнаруживает действия между лесами. В этом случае [!INCLUDE [Product short](includes/product-short.md)] датчики отправляют запрос LDAP на соответствующие контроллеры домена для получения сведений о сущности.

## <a name="known-limitations"></a>Известные ограничения

- Интерактивные входы, выполняемые пользователями в одном лесу для доступа к ресурсам в другом лесу, не отображаются на [!INCLUDE [Product short](includes/product-short.md)] панели мониторинга.

## <a name="see-also"></a>См. также

- [Средство определения размера [!INCLUDE [Product short](includes/product-short.md)]](https://aka.ms/aatpsizingtool)
- [Архитектура [!INCLUDE [Product short](includes/product-short.md)]](architecture.md)
- [Установка [!INCLUDE [Product short](includes/product-short.md)]](install-step1.md)
- [Посетите форум по [!INCLUDE [Product short](includes/product-short.md)].](https://aka.ms/MDIcommunity)
