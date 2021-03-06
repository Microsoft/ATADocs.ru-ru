---
title: Новые возможности Advanced Threat Analytics версии 1,6
description: В этой статье перечислены новые возможности и известные проблемы в ATA версии 1.6.
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 01/23/2017
ms.topic: conceptual
ms.prod: advanced-threat-analytics
ms.technology: ''
ms.assetid: 27b139e5-12b9-4953-8f53-eb58e8ce0038
ms.reviewer: bennyl
ms.suite: ems
ms.openlocfilehash: 73c8157b582f4f3eed0550a0d59ca76eae45ce92
ms.sourcegitcommit: 5bf0c6a204b71126306a0c64108eaf9cb7fc042f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/18/2021
ms.locfileid: "101097289"
---
# <a name="whats-new-in-ata-version-16"></a>Новые возможности ATA версии 1.6

В этих заметках о выпуске содержатся сведения об известных проблемах в текущей версии решения Advanced Threat Analytics.

## <a name="whats-new-in-the-ata-16-update"></a>Новые возможности в обновлении ATA 1.6

При обновлении ATA до версии 1.6 появляются следующие улучшения:

- Новые обнаружения

- улучшения имеющихся обнаружений.
- Упрощенный шлюз ATA.
- Автоматическое обновление
- Улучшение производительности центра ATA
- более низкие требования к хранению;
- поддержка IBM QRadar;

### <a name="new-detections"></a>Новые обнаружения

- **Вредоносный запрос конфиденциальных сведений для защиты данных.**  
API защиты данных (DPAPI) — это служба защиты данных на основе пароля. Эта служба защиты используется различными приложениями, которые хранят секреты пользователя, такие как пароли веб-сайтов и учетные данные файлового ресурса. Для решения проблемы при потере пароля пользователи могут расшифровывать защищенные данные с помощью ключа восстановления. При этом пароль не используется. В среде домена злоумышленники могут удаленно похищать ключи восстановления и использовать их для расшифровки защищенных данных на всех компьютерах, присоединенных к домену.

- **Перечисление сеансов NET.**  
Разведка — ключевой этап в цепочке продвинутой атаки. Контроллеры домена выполняют функции файловых серверов для распространения объектов групповой политики с использованием протокола SMB. На этапе разведки злоумышленники могут запрашивать в контроллере домена все активные сеансы SMB на сервере. Таким образом они получают доступ ко всем пользователям и IP-адресам, связанным с этими сеансами SMB. При перечислении сеансов SMB злоумышленники используют конфиденциальные учетные записи, за счет чего они могут осуществлять боковое смещение в сети.

- **Вредоносные запросы на репликацию.**  
В среде Active Directory между контроллерами домена регулярно выполняется репликация. Злоумышленник может подделать запрос на репликацию Active Directory (иногда путем олицетворения контроллера домена). Таким образом он может получить данные, хранящиеся в Active Directory, включая хэши паролей, без использования более продвинутых методов, например теневого копирования томов.

- **Обнаружение уязвимости MS11-013.**  
В Kerberos есть уязвимость, благодаря которой можно повысить привилегии. Она позволяет подделать определенные характеристики билета службы Kerberos. Воспользовавшись этой уязвимостью, пользователь-злоумышленник может получить маркер с повышенными привилегиями на контроллере домена.

- **Внедрение нестандартных протоколов.**  
Обычно запросы на аутентификацию (Kerberos или NTLM) выполняются с использованием набора стандартных протоколов и методов. Однако для успешной аутентификации запрос должен удовлетворять только определенным требованиям. Злоумышленники могут внедрить эти протоколы в среду, немного изменив их. По этим изменениям можно определить попытку атаки злоумышленника (Pass-The-Hash, атака методом подбора и т. д.).

### <a name="improvements-to-existing-detections"></a>улучшения имеющихся обнаружений.

В ATA 1.6 реализована улучшенная логика обнаружения, благодаря которой сокращается количество ложно-положительных и ложно-отрицательных результатов для имеющихся обнаружений, например при атаках Golden Ticket, атаках с использованием учетной записи honeytoken, атаках методом подбора и атаках с удаленным выполнением.

### <a name="the-ata-lightweight-gateway"></a>Упрощенный шлюз ATA.

В этой версии ATA появился новый вариант развертывания шлюза ATA, позволяющий установить шлюз ATA непосредственно на контроллере домена. При этом шлюз ATA не выполняет второстепенных функций. Кроме того, теперь можно воспользоваться динамическим управлением ресурсами на основе ресурсов, доступных на контроллере домена, при котором обеспечивается непрерывная работа имеющихся операций контроллера домена. Упрощенный шлюз ATA позволяет снизить затраты на развертывание ATA. В то же время упрощается развертывание на сайтах филиалов с ограниченными аппаратными ресурсами, на которых невозможно настроить зеркальное отображение портов.
Дополнительные сведения об упрощенном шлюзе ATA см. в статье [Архитектура ATA](ata-architecture.md#ata-gateway-and-ata-lightweight-gateway).

Дополнительные сведения о рекомендациях для развертывания и выборе подходящего типа шлюза см. в статье [Планирование производительности ATA](ata-capacity-planning.md#choosing-the-right-gateway-type-for-your-deployment).

### <a name="automatic-updates"></a>Автоматическое обновление

Начиная с версии 1.6, центр ATA можно обновить с помощью Центра обновления Майкрософт. Кроме того, теперь шлюзы ATA можно автоматически обновить с использованием стандартного коммуникационного канала в центре ATA.

### <a name="improved-ata-center-performance"></a>Улучшение производительности центра ATA

Благодаря сниженной нагрузке на базу данных и более эффективному способу выполнения обнаружения в этой версии в одном центре ATA можно выполнять мониторинг множества контроллеров домена.

### <a name="lower-storage-requirements"></a>более низкие требования к хранению;

Для работы с базой данных ATA 1.6 необходимо существенно меньше места — всего лишь 20 % дискового пространства по сравнению с предыдущими версиями.

### <a name="support-for-ibm-qradar"></a>поддержка IBM QRadar;

Теперь ATA может получать события не только из поддерживаемых решений SIEM, но и из решения SIEM QRadar от IBM.

## <a name="known-issues"></a>Известные проблемы

В этой версии существуют следующие проблемы.

### <a name="failure-to-recognize-new-path-in-manually-moved-databases"></a>Сбой распознавания нового пути в базах данных, перемещенных вручную

В средах, в которых путь к базе данных перемещается вручную, развертывание ATA не использует новый путь к базе данных для обновления. Ручное перемещение пути к базе данных может вызвать следующие проблемы.

- ATA может использовать все свободное место на системном диске центра ATA. При этом не выполняется цикличное удаление старых сетевых операций.

- Обновление ATA до версии 1.6 может привести к сбою проверки готовности перед обновлением, как показано на рисунке ниже.

    ![Сбой проверки готовности](media/ata_failed_readinesschecks.png)

    > [!IMPORTANT]
    > Перед обновлением ATA до версии 1.6 обновите следующий раздел реестра, указав правильный путь к базе данных: `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft Advanced Threat Analytics\Center\DatabaseDataPath`.

### <a name="migration-failure-when-updating-from-ata-15"></a>Сбой миграции при обновлении ATA 1.5

При обновлении ATA до версии 1.6 может произойти сбой и отобразится следующее сообщение об ошибке с кодом:

![Ошибка при обновлении ATA до версии 1.6](http://i.imgur.com/QrLSApr.png)

Если вы видите эту ошибку, просмотрите журнал развертывания в разделе: **C:\Users \<User> \AppData\Local\Temp** и найдите следующее исключение:

```
System.Reflection.TargetInvocationException: Exception has been thrown by the target of an invocation. ---> MongoDB.Driver.MongoWriteException: A write operation resulted in an error. E11000 duplicate key error index: ATA.UniqueEntityProfile.$_id_ dup key: { : "<guid>" } ---> MongoDB.Driver.MongoBulkWriteException`1: A bulk write operation resulted in one or more errors.  E11000 duplicate key error index: ATA.UniqueEntityProfile.$_id_ dup key: { : " <guid> " }
```

Вы можете также увидеть следующую ошибку:

```
System.ArgumentNullException: Value cannot be null.
```

Если вы видите одну из этих ошибок, запустите следующий обходной путь:

**Обходной путь**.

1. Переместите папку data_old во временную папку (которая обычно находится в каталоге %ProgramFiles%\Microsoft Advanced Threat Analytics\Center\MongoDB\bin).
1. Удалите центр ATA 1.5 и все данные базы данных.
![Удаление ATA 1.5](http://i.imgur.com/x4nJycx.png)
1. Повторно установите центр ATA версии 1.5. Используйте ту же конфигурацию, что и при предыдущей установке ATA 1.5 (сертификаты, IP-адреса, путь к базе данных и т. д.).
1. Остановите работу этих служб в следующем порядке:
    1. центр Microsoft Advanced Threat Analytics;
    2. MongoDB
1. Замените файлы базы данных MongoDB файлами в папке "data_old".
1. Запустите эти службы в следующем порядке:
    1. MongoDB
    2. центр Microsoft Advanced Threat Analytics;
1. Просмотрите журналы, чтобы убедиться, что продукт работает без ошибок.
1. [Скачайте](/samples/browse/?redirectedfrom=TechNet-Gallery "Скачать") средство "RemoveDuplicateProfiles.exe" и скопируйте его в основной путь установки (%ProgramFiles%\Microsoft Advanced Threat analytics\center.).
1. Из командной строки с повышенными привилегиями запустите файл `RemoveDuplicateProfiles.exe` и дождитесь его успешного выполнения.
1. Отсюда: `…\Microsoft Advanced Threat Analytics\Center\MongoDB\bin` Каталог: **Mongo ATA** введите следующую команду:

```dos
db.SuspiciousActivities.remove({ "_t" : "RemoteExecutionSuspiciousActivity", "DetailsRecords" : { "$elemMatch" : { "ReturnCode" : null } } }, { "_id" : 1 });
```

![Обходной путь обновления](http://i.imgur.com/Nj99X2f.png)

Он должен возвращать, `WriteResult({ "nRemoved" : XX })` где "XX" — количество подозрительных действий, которые были удалены. Если число больше 0, выйдите из командной строки и продолжите процесс обновления.

### <a name="net-framework-461-requires-restarting-the-server"></a>NET Framework 4.6.1 требует перезапуска сервера

![Перезапуск .NET Framework](media/ata-net-framework-restart.png)

### <a name="historical-network-activities-no-longer-migrated"></a>Сетевые операции в журнале не переносятся

В этой версии ATA предусмотрен улучшенный механизм обнаружения, который обеспечивает более точное обнаружение и позволяет сократить количество ложно-положительных результатов, особенно в случае атаки Pass-the-Hash.
Новый усовершенствованный механизм обнаружения использует внутреннюю технологию обнаружения, благодаря чему можно выявлять проблемы без обращения к сетевым операциям в журнале. Таким образом производительность центра ATA существенно повышается. Это также означает, что при обновлении не нужно переносить сетевые операции в журнале.
При обновлении ATA данные экспортируются в `<Center Installation Path>\Migration` в качестве JSON-файла (если они понадобятся для изучения в будущем).

## <a name="see-also"></a>См. также

Посетите [форум ATA.](https://social.technet.microsoft.com/Forums/security/home?forum=mata) 
 [Обновление ATA до версии 1,6 — руководством по миграции](ata-update-1.6-migration-guide.md)