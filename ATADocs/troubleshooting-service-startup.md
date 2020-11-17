---
title: Устранение неполадок при запуске службы Advanced Threat Analytics
description: В этой статье описываются способы устранения неполадок при запуске службы ATA
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 3/21/2018
ms.topic: conceptual
ms.prod: advanced-threat-analytics
ms.technology: ''
ms.assetid: 5a65285c-d1de-4025-9bb4-ef9c20b13cfa
ms.reviewer: bennyl
ms.suite: ems
ms.openlocfilehash: 3f23eb1aa2adc49b3913ab1e4218653a5b8c874d
ms.sourcegitcommit: e844155ea57f73dfe2b47f4c5c1c7f5292ccbf1e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2020
ms.locfileid: "94689927"
---
# <a name="troubleshooting-service-startup"></a>Устранение неполадок при запуске службы

[!INCLUDE [Banner for top of topics](includes/banner.md)]

## <a name="troubleshooting-ata-center-service-startup"></a>Устранение неполадок при запуске службы центра ATA

Если центр ATA не запускается, выполните описанную ниже процедуру устранения неполадок:

1. Выполните следующую команду Windows PowerShell: `Get-Service Pla | Select Status`,
   чтобы убедиться в том, что служба счетчиков производительности запущена. Если она не запущена, это неполадка платформы и эту службу необходимо снова запустить.
1. Если он был запущен, попробуйте перезапустить его и проверьте, разрешает ли он проблему:  `Restart-Service Pla`
1. Попробуйте создать новый сборщик данных вручную (достаточно любого сборщика, например, для сбора данных по ЦП компьютера).
Если он запускается, скорее всего, платформа исправна. В противном случае имеется неполадка платформы.

1. Попробуйте повторно создать сборщик данных ATA вручную, выполнив следующие команды в командной строке с повышенными привилегиями:

```dos
sc stop ATACenter
logman stop "Microsoft ATA Center"
logman export "Microsoft ATA Center" -xml c:\center.xml
logman delete "Microsoft ATA Center"
logman import "Microsoft ATA Center" -xml c:\center.xml
logman start "Microsoft ATA Center"
sc start ATACenter
```

## <a name="troubleshooting-ata-lightweight-gateway-startup"></a>Устранение неполадок при запуске упрощенного шлюза ATA

**Симптом**

Шлюз ATA не запускается, и выводится следующее сообщение об ошибке:<br></br>
*System.Net.Http.HttpRequestException: Код состояния ответа не указывает на успешное выполнение: 500 (внутренняя ошибка сервера)*

**Описание**

Это происходит, поскольку в ходе процесса установки упрощенного шлюза служба ATA выделяет пороговое значение ЦП, позволяющее упрощенному шлюзу использовать ЦП с буфером 15 %. Если пороговое значение было задано независимо с помощью раздела реестра, этот конфликт будет препятствовать запуску упрощенного шлюза. 

**Решение**

1. В разделах реестра, если имеется значение DWORD с именем **Отключить счетчики производительности** , убедитесь, что оно равно **0**.

```
HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\PerfOS\Performance\
HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\PerfProc\Performance
```

1. Затем перезапустите службу Pla. Упрощенный шлюз ATA автоматически обнаружит изменение и перезапустит службу.

## <a name="see-also"></a>См. также:

- [Предварительные требования ATA](ata-prerequisites.md)
- [Планирование производительности ATA](ata-capacity-planning.md)
- [Настройка сбора данных о событиях](configure-event-collection.md)
- [Настройка пересылки событий Windows](configure-event-collection.md)
- [Обязательно ознакомьтесь с форумом ATA.](https://social.technet.microsoft.com/Forums/security/home?forum=mata)
