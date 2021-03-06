---
title: Изменение конфигурации Advanced Threat Analytics — пароль для подключения к домену
description: Процедура изменения пароля для подключения к домену на шлюзе ATA.
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 3/21/2018
ms.topic: conceptual
ms.prod: advanced-threat-analytics
ms.technology: ''
ms.assetid: 4a25561b-a5ed-44aa-9b72-366976b3c72a
ms.reviewer: bennyl
ms.suite: ems
ms.openlocfilehash: d310ec8659fcb2fa2a128f24b9b243939dc438eb
ms.sourcegitcommit: e844155ea57f73dfe2b47f4c5c1c7f5292ccbf1e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2020
ms.locfileid: "94690386"
---
# <a name="change-ata-configuration---domain-connectivity-password"></a>Изменение конфигурации ATA. Пароль для подключения к домену

[!INCLUDE [Banner for top of topics](includes/banner.md)]

## <a name="change-the-domain-connectivity-password"></a>Изменение пароля для подключения к домену

Изменяя пароль для подключения к домену, указывайте правильный пароль. Если указать неправильный пароль, служба ATA на шлюзах ATA перестанет работать.

В таком случае откройте на шлюзе ATA файл Microsoft.Tri.Gateway-Errors.log и найдите в нем следующие ошибки: `The supplied credential is invalid.`.

Чтобы исправить эту ошибку, в центре ATA измените пароль для подключения к домену, как описано ниже.

1. Откройте в центре ATA консоль ATA.

1. На панели инструментов щелкните значок параметров и выберите пункт **Конфигурация**.

    ![Значок параметров конфигурации ATA](media/ATA-config-icon.png)

1. Выберите **Directory Services** (Службы каталогов).

    ![Изменение пароля для шлюзов ATA (рисунок)](media/ATA-GW-change-DC-password.png)

1. В разделе **Password** (Пароль) измените пароль.

    Если у центра ATA есть подключение к домену, то, чтобы проверить учетные данные, нажмите кнопку **Проверить подключение**.

1. Выберите команду **Сохранить**.

1. После изменения пароля убедитесь, что служба шлюза ATA работает на всех шлюзах ATA.



## <a name="see-also"></a>См. также
- [Работа с консолью ATA](working-with-ata-console.md)
- [Обязательно ознакомьтесь с форумом ATA.](https://social.technet.microsoft.com/Forums/security/home?forum=mata)
