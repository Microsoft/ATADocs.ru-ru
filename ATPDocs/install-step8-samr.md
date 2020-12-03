---
title: Настройка SAM-R для включения определения пути перемещения бокового смещения в защитнике Майкрософт для идентификации
description: В этой статье объясняется, как настроить защитник Майкрософт для удостоверений, чтобы выполнять удаленные вызовы к SAM.
ms.date: 10/26/2020
ms.topic: how-to
ms.openlocfilehash: 24c1d6baf99e3d65a96897d2d0b90ffe94ad42eb
ms.sourcegitcommit: cdb7ae4580851e25aae24d07e7d66a750aa54405
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/03/2020
ms.locfileid: "96543949"
---
# <a name="configure-product-long-to-make-remote-calls-to-sam"></a>Настройка [!INCLUDE [Product long](includes/product-long.md)] для выполнения удаленных вызовов SAM

[!INCLUDE [Product long](includes/product-long.md)]Обнаружение [пути перемещения бокового смещения](use-case-lateral-movement-path.md) зависит от запросов, которые указывают локальных администраторов на конкретных компьютерах. Эти запросы выполняются с помощью протокола SAM-R с использованием [!INCLUDE [Product short](includes/product-short.md)] учетной записи службы, созданной во время [!INCLUDE [Product short](includes/product-short.md)] установки на  [шаге 2. Подключитесь к AD](install-step2.md).

## <a name="configure-sam-r-required-permissions"></a>Настройка необходимых разрешений для SAM-R

Чтобы клиенты и серверы Windows позволяли вашей [!INCLUDE [Product short](includes/product-short.md)] учетной записи выполнять действия SAM-R, необходимо внести изменения в **Групповая политика** , чтобы добавить [!INCLUDE [Product short](includes/product-short.md)] учетную запись службы в дополнение к настроенным учетным записям, перечисленным в политике **сетевого доступа** . Не забудьте применить групповые политики ко всем компьютерам, **Кроме контроллеров домена**.

> [!Note]
> Перед применением новых политик, таких как эта, важно убедиться, что среда останется защищенной и никакие изменения не затронут совместимость приложений. Для этого активируйте предлагаемые изменения и проверьте их на совместимость в режиме аудита, прежде чем вносить их в рабочую среду.

1. Найдите политику.

   - Имя политики: сетевой доступ — ограничение клиентов, которые могут выполнять удаленные вызовы SAM
   - Расположение: конфигурация компьютера, параметры Windows, параметры безопасности, локальные политики, параметры безопасности

    ![Поиск политики](media/samr-policy-location.png)

1. Добавьте [!INCLUDE [Product short](includes/product-short.md)] службу в список утвержденных учетных записей, которые могут выполнять это действие в современных системах Windows.

    ![Добавление службы](media/samr-add-service.png)

3. **Служба AATP** ( [!INCLUDE [Product short](includes/product-short.md)] служба, созданная во время установки) теперь имеет права, необходимые для выполнения SAM-R в среде.

Дополнительные сведения о SAM-R и этой групповой политики см. в статье [Network access: Restrict clients allowed to make remote calls to SAM](/windows/security/threat-protection/security-policy-settings/network-access-restrict-clients-allowed-to-make-remote-sam-calls) (Сетевой доступ — ограничение клиентов, которые могут выполнять удаленные вызовы SAM).

## <a name="see-also"></a>См. также

- [Исследование атак с использованием пути перемещения бокового смещения с помощью [!INCLUDE [Product short](includes/product-short.md)]](use-case-lateral-movement-path.md)
- [Посетите форум по [!INCLUDE [Product short](includes/product-short.md)].](https://aka.ms/MDIcommunity)
