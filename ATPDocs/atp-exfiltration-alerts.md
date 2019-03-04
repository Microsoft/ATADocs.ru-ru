---
title: Руководство по оповещениям о краже данных в Azure ATP | Документация Майкрософт
d|Description: This article explains the Azure ATP alerts issued when attacks typically part of exfiltration phase efforts are detected against your organization.
keywords: ''
author: mlottner
ms.author: mlottner
manager: barbkess
ms.date: 02/11/2019
ms.topic: tutorial
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: azure-advanced-threat-protection
ms.technology: ''
ms.assetid: 452d951c-5f49-4a21-ae10-9fb38c3de302
ms.reviewer: itargoet
ms.suite: ems
ms.openlocfilehash: 94e73ecb2980c851aec6ff391c49fff88e4961c8
ms.sourcegitcommit: c48db18274edb2284e281960c6262d97f96e01d2
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/14/2019
ms.locfileid: "56263647"
---
# <a name="tutorial-exfiltration-alerts"></a>Руководство. Предупреждения о краже данных  

Как правило, атаки изначально направлены на доступные объекты, например пользователей с низким уровнем прав, а затем быстро распространяются по горизонтали, пока злоумышленник не получит доступ к ценным ресурсам, например важным учетным записям, в том числе с правами администратора домена, или конфиденциальным данным. Azure ATP позволяет устанавливать источники таких современных угроз, прослеживая всю цепочку атаки, и классифицировать их по следующим этапам:

1. [Разведывательная атака](atp-reconnaissance-alerts.md)
2. [Компрометация учетных данных](atp-compromised-credentials-alerts.md)
3. [Боковое смещение](atp-lateral-movement-alerts.md)
4. [Полное управление доменом](atp-domain-dominance-alerts.md)
5. **Кража данных**

Дополнительные сведения о структуре и общих компонентах всех оповещений системы безопасности Azure ATP см. в разделе [Основные сведения об оповещениях безопасности](understanding-security-alerts.md).

Следующие оповещения помогают выявлять и устранять последствия подозрительных действий этапа **Кража данных**, обнаруженных Azure ATP в вашей сети. В этом руководстве вы узнаете, как распознавать, классифицировать, предотвращать и устранять последствия следующих атак:

> [!div class="checklist"]
> * Подозрительный обмен данными через DNS (внешний код 2031)
> * Кража данных по SMB (внешний код 2030)

## <a name="suspicious-communication-over-dns-external-id-2031"></a>Подозрительный обмен данными через DNS (внешний код 2031) 

*Предыдущее название*. Подозрительный обмен данными через DNS

**Описание**

В большинстве организаций протокол DNS не отслеживается, и в нем редко блокируется выполнение вредоносных действий. Это позволяет злоумышленнику на скомпрометированном компьютере пользоваться протоколом DNS в своих целях. Вредоносный обмен данными по протоколу DNS может быть использован для организации утечки данных, отправки команд и управления, а также для обхода ограничений корпоративной сети.

**TP, B-TP или FP?**
 
В некоторых организациях протокол DNS правомерно используется для обычного обмена информацией. Определение состояния оповещения системы безопасности

1. Проверьте, принадлежит ли зарегистрированный домен запросов надежному источнику, например вашему поставщику системы антивирусной защиты.  
    - Это действие можно отнести к категории **B-TP**, если домен является известным и надежным, а DNS-запросы разрешены. *Закройте* оповещение системы безопасности и исключите домен из будущих обнаружений.  
    - Если зарегистрированный домен не является надежным, определите процесс создания запроса на компьютере-источнике. Для выполнения этой задачи можно использовать [Монитор процессов](https://docs.microsoft.com/sysinternals/downloads/procmon).

**Определение области бреши в системе безопасности**

1. На конечном компьютере, который должен быть DNS-сервером, проверьте подозрительные записи домена.
    - С каким IP-адресом он связан?
    - Кто является владельцем домена?
    - Где находится IP-адрес?
1. Исследуйте [исходный и конечный компьютеры](investigate-a-computer.md).

**Предлагаемое исправление и шаги по профилактике**

1. Уменьшите влияние исходного компьютера.
    - Найдите средство, инициировавшее атаку, и удалите его.
    - Найдите пользователей, выполнивших вход в систему во время вредоносной активности, так как они также могут быть скомпрометированы. Сбросьте их пароли и включите многофакторную проверку подлинности.
2. Если по результатам анализа зарегистрированный домен запросов не является надежным, рекомендуется заблокировать целевой домен, чтобы исключить любой дальнейший обмен данными.

> [!NOTE]
> В оповещениях системы безопасности типа *Подозрительный обмен данными через DNS* перечисляются подозрительные домены. Новые домены, а также домены, которые были недавно добавлены и еще не известны и не распознаны в Azure ATP, но при этом являются частью организации с соответствующими подтверждениями, могут быть закрыты.

## <a name="data-exfiltration-over-smb-external-id-2030"></a>Кража данных по SMB (внешний код 2030)

**Описание**. На контроллерах домена хранятся наиболее важные данные организации. Для большинства злоумышленников одной из приоритетных задач является получение доступа к контроллеру домена для кражи наиболее важных данных. Например, утечка файла Ntds.dit, который хранится на контроллере домена, позволяет злоумышленнику создать поддельный билет на получение билетов (TGT) Kerberos, обеспечивающий доступ к любому ресурсу. Поддельные TGT-билеты Kerberos позволяют злоумышленнику задать произвольное истечение срока действия билета. Оповещение **Кража данных по SMB** Azure ATP активируется при наблюдаемой подозрительной передаче данных с отслеживаемых контроллеров домена.

**TP, B-TP или FP**
1. Должны ли эти пользователи копировать эти файлы на этот компьютер?  
    - Если ответ на приведенный выше вопрос — **да**, **закройте** оповещение как действие **B-TP** и исключите компьютер.

**Определение области бреши в системе безопасности**
1. Исследуйте [пользователя-источник](investigate-a-user.md).  
2. Исследуйте [исходный и конечный компьютеры](investigate-a-computer.md) операций копирования. 

**Предлагаемое исправление и шаги по профилактике**
1. Сбросьте пароли пользователей-источников и включите многофакторную идентификацию.
2. Уменьшите влияние исходного компьютера.
    - Найдите средство, инициировавшее атаку, и удалите его.
    - Найдите скопированные файлы и удалите их. 
    <br>Проверьте наличие других действий с этими файлами. Были ли они перенесены в другое место? Были ли они перемещены за пределы сети организации? 
    - Найдите пользователей, выполнивших вход в систему во время вредоносной активности, так как они также могут быть скомпрометированы. Сбросьте их пароли и включите многофакторную проверку подлинности.
3. Если один из этих файлов — **ntds.dit**:
    - Несколько раз меняйте пароль билета на получение билетов Kerberos (KRBTGT), как описано в записи блога о [скриптах для сброса пароля к учетной записи KRBTGT, доступных клиентам](https://cloudblogs.microsoft.com/microsoftsecure/2015/02/11/krbtgt-account-password-reset-scripts-now-available-for-customers/) с помощью [средства сброса пароля или ключей к учетной записи KRBTGT](https://gallery.technet.microsoft.com/Reset-the-krbtgt-account-581a9e51). 
    - Учтите, что такой сброс приведет к тому, что все билеты Kerberos в этом домене станут недействительными. Это означает, что работа **всех** служб будет нарушена и они не будут работать до обновления или, в некоторых случаях, до перезапуска службы.

    - **Будьте очень осмотрительны при выполнении двойного сброса KRBTGT. Двойной сброс KRBTGT влияет на все компьютеры, серверы и пользователей в среде.**

   - Закройте все существующие сеансы подключения к контроллерам домена. 

## <a name="see-also"></a>См. также

- [Проверка компьютера](investigate-a-computer.md)
- [Работа с оповещениями системы безопасности](working-with-suspicious-activities.md)
- [Работа с путями бокового смещения](use-case-lateral-movement-path.md)
- [Оповещения о разведывательных атаках](atp-reconnaissance-alerts.md)
- [Оповещения о компрометации учетных данных](atp-compromised-credentials-alerts.md)
- [Оповещения об атаках бокового смещения](atp-lateral-movement-alerts.md)
- [Оповещения о захвате управления доменом](atp-domain-dominance-alerts.md)
- [Загляните на форум Azure ATP!](https://aka.ms/azureatpcommunity)