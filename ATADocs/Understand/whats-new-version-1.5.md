---
title: "Новые возможности ATA версии 1.5 | Microsoft ATA"
description: "В этой статье перечислены новые возможности и известные проблемы в ATA версии 1.5."
keywords: 
author: rkarlin
manager: mbaldwin
ms.date: 04/28/2016
ms.topic: article
ms.prod: 
ms.service: advanced-threat-analytics
ms.technology: 
ms.assetid: a0d64aff-ca9e-4300-b3f8-eb3c8b8ae045
ms.reviewer: bennyl
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: f13750f9cdff98aadcd59346bfbbb73c2f3a26f0
ms.openlocfilehash: c6e39cf057ed5e2a86acb8c41301252ed8339922


---

# Новые возможности ATA версии 1.5
В этих заметках о выпуске содержатся сведения об известных проблемах в текущей версии решения Advanced Threat Analytics.

## Что нового в обновлении ATA 1.5
Обновление до версии ATA 1.5 привносит следующие улучшения:

-   сокращение времени обнаружения;

-   улучшенный алгоритм автоматического обнаружения устройств NAT (преобразование сетевых адресов);

-   улучшенный процесс разрешения имен для устройств, не присоединенных к домену;

-   поддержка переноса данных во время обновления продукта;

-   более быстрая реакция пользовательского интерфейса на подозрительные действия, в которых задействованы тысячи сущностей;

-   улучшенное автоматическое разрешение для оповещений системы мониторинга;

-   дополнительные счетчики производительности для улучшения процессов мониторинга и устранения неполадок.

## Известные проблемы
В этой версии существуют следующие проблемы.

### Сбой установки нового шлюза ATA
После обновления развертывания ATA до версии 1.5 возникает ошибка при установке нового шлюза ATA: Microsoft Advanced Threat Analytics Gateway is not installed (Шлюз Microsoft Advanced Threat Analytics не установлен).

![Ошибка шлюза ATA](media/ata-install-error.png)

<b>Решение.</b> Отправьте сообщение по адресу <ataeval@microsoft.com> с просьбой сообщить о вариантах решения проблемы.
### Развертывание
Папка, указанная в параметрах "Путь к данным базы данных" и "Путь к журналу базы данных", должна быть пустой (никаких файлов или подпапок).
Если она не пустая, развертывание не выполнится.

### Установка из ZIP-файла
Перед установкой шлюза ATA извлеките файлы из ZIP-файла в локальный каталог и установите шлюз из него. Не устанавливайте шлюз ATA непосредственно из ZIP-файла, иначе произойдет сбой установки.

### Конфигурация
Когда конфигурация шлюза ATA настроена, при первом запуске шлюза ATA надпись "Не синхронизировано" будет отображаться до тех пор, пока служба полностью не запустится. При первом запуске службы это может занять до 10 минут.

### Программное обеспечение для записи сетевого трафика
Единственное программное обеспечение для записи сетевого трафика, которое поддерживается в шлюзе ATA и которое можно установить, — это [Microsoft Network Monitor 3.4](http://www.microsoft.com/download/details.aspx?id=4865). Не устанавливайте Microsoft Message Analyzer или другие программы для записи сетевого трафика. Установка другого программного обеспечения приведет к неправильной работе шлюза ATA.

### Установка исправлений на узел виртуализации
Не устанавливайте исправление KB3047154 на узел виртуализации. Это может привести к неправильному зеркальному отображению портов.

## См. также

[Руководство по миграции на обновленную версию ATA 1.5](ata-update-1.5-migration-guide.md)

[Руководство по миграции на обновленную версию ATA 1.6](ata-update-1.6-migration-guide.md)

[Обязательно ознакомьтесь с форумом ATA.](https://social.technet.microsoft.com/Forums/security/home?forum=mata)



<!--HONumber=Jul16_HO4-->

