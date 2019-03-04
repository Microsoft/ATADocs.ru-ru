---
title: Оповещения системы безопасности этапа разведывательной атаки в Azure ATP | Документация Майкрософт
d|Description: This article explains the Azure ATP alerts issued when attacks typically part of reconnaissance phase efforts are detected against your organization.
keywords: ''
author: mlottner
ms.author: mlottner
manager: barbkess
ms.date: 02/24/2019
ms.topic: tutorial
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: azure-advanced-threat-protection
ms.technology: ''
ms.assetid: e9cf68d2-36bd-4b0d-b36e-7cf7ded2618e
ms.reviewer: itargoet
ms.suite: ems
ms.openlocfilehash: 36f7d273273e11d57c681e75cc762e853a127616
ms.sourcegitcommit: 5e954f2f0cc14e42d68d2575dd1c2ed9eaabe891
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/25/2019
ms.locfileid: "56754418"
---
# <a name="tutorial-reconnaissance-alerts"></a>Руководство. Предупреждения о разведывательных атаках  

Как правило, атаки изначально направлены на доступные объекты, например пользователей с низким уровнем прав, а затем быстро распространяются по горизонтали, пока злоумышленник не получит доступ к ценным ресурсам, например важным учетным записям, в том числе с правами администратора домена, или конфиденциальным данным. Azure ATP позволяет устанавливать источники таких современных угроз, прослеживая всю цепочку атаки, и классифицировать их по следующим этапам:

1. **Разведывательная атака**
2. [Компрометация учетных данных](atp-compromised-credentials-alerts.md)
3. [Боковое смещение](atp-lateral-movement-alerts.md)
4. [Полное управление доменом](atp-domain-dominance-alerts.md)
5. [Кража данных](atp-exfiltration-alerts.md) 

Дополнительные сведения о структуре и общих компонентах всех оповещений системы безопасности Azure ATP см. в разделе [Основные сведения об оповещениях безопасности](understanding-security-alerts.md).

Следующие оповещения помогают выявлять и устранять последствия подозрительных действий этапа **Разведывательная атака**, обнаруженных Azure ATP в вашей сети.

В этом руководстве вы узнаете, как распознавать, классифицировать, предотвращать и устранять последствия следующих атак:

> [!div class="checklist"]
> * Разведывательная атака путем перечисления учетных записей (внешний код 2003)
> * Рекогносцировка путем сетевого сопоставления (DNS) (внешний код 2007)
> * Разведывательная атака, направленная на субъект безопасности (LDAP) (внешний код 2038) — предварительная версия
> * Разведывательная атака с использованием пользователя и IP-адреса (SMB) (внешний код 2012)
> * Разведывательная атака с использованием пользователей и членства в группах (SAMR) (внешний код 2021)
> * 

## <a name="account-enumeration-reconnaissance-external-id-2003"></a>Разведывательная атака путем перечисления учетных записей (внешний код 2003) 


*Предыдущее название.* Разведывательная атака с использованием перечисления учетных записей.

**Описание**

В разведывательной атаке путем перечисления учетных записей злоумышленник использует словарь с тысячами имен пользователей или такие средства, как KrbGuess, чтобы попытаться угадать имена пользователей в вашем домене.

**Kerberos.** Он создает запросы Kerberos с различными именами, пытаясь найти имя, которое будет допустимым в домене. Если имя пользователя угадано верно, злоумышленник получит ошибку Kerberos **Требуется предварительная проверка подлинности**, а не **Неизвестный субъект безопасности**.

**NTLM.** Он создает запросы проверки подлинности NTLM, используя словарь имен, чтобы найти имя, которое будет допустимым в домене. Если имя пользователя успешно угадано, злоумышленник получает ошибку NTLM **WrongPassword (0xc000006a)**, вместо **NoSuchUser (0xc0000064)**.

При таком обнаружении Azure ATP может определить, откуда пришла атака перечисления учетных записей, сколько всего было попыток угадывания и сколько было успешных совпадений. Если неизвестных пользователей слишком много, Azure ATP распознает это как подозрительное действие.

**TP, B-TP или FP**

Некоторые серверы и приложения запрашивают контроллеры домена, чтобы определить, существуют ли учетные записи, в рамках правомерных сценариев использования.

Чтобы определить, относится ли запрос к категории **TP**, **B-TP** или **FP**, щелкните оповещение, чтобы открыть страницу сведений:

1. Проверьте, должен ли компьютер-источник выполнять запросы этого типа. Примерами **B-TP** в этом случае могут быть серверы Microsoft Exchange или система отдела кадров.

2. Проверьте домены учетных записей.
   - Отображаются ли дополнительные пользователи, принадлежащие к другому домену? 
     <br>Неверная конфигурация сервера, например настройки Exchange, Skype или ADSF, может привести к появлению дополнительных пользователей, принадлежащих к другим доменам.
   - Проверьте конфигурацию проблемной службы, чтобы исправить неправильные настройки.

     Если ответ на вопросы выше — **да**, это действие **B-TP**. *Закройте* оповещение системы безопасности.<br>

В качестве следующего этапа проанализируйте компьютер-источник. 

1. Запущен ли на компьютере-источнике сценарий или приложение, которые могут выполнять такие действия?  
   - Является ли сценарий старым сценарием, который выполняется со старыми учетными данными? <br>Если да, остановите и измените или удалите сценарий. 
   - Является ли приложение административным приложением или сценарием или приложением (сценарием) безопасности, которое должно выполняться в среде?
 
     Если вы ответили **да** на предыдущий вопрос, *закройте* оповещение системы безопасности и исключите этот компьютер. Вероятно, это действие **B-TP**.

Теперь проанализируйте учетные записи.<br>
<br>Известно, что злоумышленники используют словарь случайных имен учетных записей, чтобы найти имена существующих учетных записей в организации.

1. Несуществующие учетные записи выглядят знакомыми?  
   - Если несуществующие учетные записи выглядят знакомыми, возможно, это отключенные учетные записи сотрудников, уволившихся из компании.
   - Найдите приложение или сценарий, которые проверяют, какие учетные записи все еще существуют в Active Directory.

     Если вы ответили **да** на один из этих вопросов, *закройте* оповещение системы безопасности: вероятно, это действие **B-TP**.

2. Если какая-либо попытка угадывания совпадает с существующими именами учетных записей, злоумышленник знает о существовании учетных записей в вашей среде и может попытаться использовать атаку методом подбора, чтобы получить доступ к домену с помощью обнаруженных имен пользователей. 
    - Проверьте угаданные имена учетных записей на предмет других подозрительных действий. 
    - Проверьте, не являются ли совпавшие учетные записи конфиденциальными.

### <a name="understand-the-scope-of-the-breach"></a>Определение области бреши в системе безопасности

1. Исследуйте исходный компьютер.
2. Если какая-либо попытка угадывания совпадает с существующими именами учетных записей, злоумышленник знает о существовании учетных записей в вашей среде и может попытаться использовать атаку методом подбора, чтобы получить доступ к домену с помощью обнаруженных имен пользователей. Исследуйте существующие учетные записи с помощью [руководства по анализу пользователей](investigate-a-user.md). 

### <a name="suggested-remediation-and-steps-for-prevention"></a>Предлагаемое исправление и шаги по профилактике

1. Уменьшите влияние [компьютера](investigate-a-computer.md)-источника. 
    1. Найдите средство, инициировавшее атаку, и удалите его.
    2. Найдите пользователей, выполнивших вход в систему во время вредоносной активности, так как эти пользователи также могут быть скомпрометированы. 
    3. Сбросьте их пароли и включите многофакторную проверку подлинности.
2. Настройте принудительное применение [длинных и сложных паролей](https://docs.microsoft.com/windows/device-security/security-policy-settings/password-policy) в организации. Длинные сложные пароли обеспечивают необходимый первый уровень защиты от атак методом подбора. Атаки методом подбора, как правило, являются следующим этапом в процессе кибератаки, который следует за перечислением. 

## <a name="network-mapping-reconnaissance-dns-external-id-2007"></a>Рекогносцировка путем сетевого сопоставления (DNS) (внешний код 2007) 

*Предыдущее название.* Разведывательная атака с использованием DNS.

**Описание**

На DNS-сервере содержится схема всех компьютеров, IP-адресов и служб в сети. Эта информация используется злоумышленниками для определения структуры сети и выявления подходящих компьютеров для проведения последующих этапов атаки. 
 
Протокол DNS предполагает несколько типов запросов. Это оповещение системы безопасности Azure ATP обнаруживает подозрительные запросы, которые направляют запросы AXFR (на передачу) от серверов, не использующих DNS, или чрезмерно большое количество запросов.

**Период обучения**

Период обучения этого оповещения составляет восемь дней от начала наблюдения за контроллерами домена. 

**TP, B-TP или FP**

1. Проверьте, является ли компьютер-источник DNS-сервером.

    - Если компьютер-источник **является** DNS-сервером, закройте оповещение системы безопасности как действие **FP**. 
    - Для предотвращения будущих **ложных срабатываний** убедитесь, что UDP-порт 53 между датчиком Azure ATP и компьютером-источником **открыт**.

Сканеры безопасности и правомерные приложения могут создавать запросы DNS. 

1. Проверьте, должен ли компьютер-источник создавать действия такого типа.

    - Если компьютер-источник закономерно создает такие действия, **закройте** оповещение системы безопасности как действие **B-TP** и исключите компьютер.

**Определение области бреши в системе безопасности**

1. Исследуйте [компьютер-источник](investigate-a-computer.md). 

**Предлагаемое исправление и шаги по профилактике**

**Исправление:**
- Уменьшите влияние исходного компьютера. 
    - Найдите средство, инициировавшее атаку, и удалите его.
    - Найдите пользователей, выполнивших вход в систему во время вредоносной активности, так как эти пользователи также могут быть скомпрометированы. Сбросьте их пароли и включите многофакторную проверку подлинности.

**Предотвращение:**<br>
Очень важно предотвратить будущие атаки с помощью запросов AXFR путем защиты внутреннего DNS-сервера.

- Чтобы защитить внутренний DNS-сервер от разведывательных атак с использованием DNS, отключите передачу зоны или [ограничьте ее](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/ee649273(v=ws.10)) только определенными IP-адресами. Настройка передачи зоны — одна из задач контрольного списка при [защите DNS-серверов от внутренних и внешних атак](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/ee649273(v=ws.10)).

## <a name="security-principal-reconnaissance-ldap-external-id-2038---preview"></a>Разведывательная атака, направленная на субъект безопасности (LDAP) (внешний код 2038) — предварительная версия

**Описание**: разведывательная атака, направленная на субъект безопасности, используется злоумышленниками для получения важной информации об окружении домена. Такая информация помогает злоумышленникам определить структуру домена и привилегированные учетные записи, которые они в дальнейшем могут использовать для реализации цепочки атаки. Протокол LDAP — это один из самых популярных методов отправки запросов в Active Directory (в том числе и среди злоумышленников).  Разведывательная атака с использованием LDAP, направленная на субъект безопасности, часто используется на первом этапе атаки типа Kerberoasting. Атаки типа Kerberoasting выполняются для получения целевого списка с именами субъектов безопасности (SPN), для которых злоумышленники затем пытаются получить билеты от сервера предоставления билетов (TGS).

Чтобы разрешить Azure ATP определить полномочных пользователей и собрать о них точные данные, в первые 10 дней после развертывания Azure ATP оповещения такого типа не срабатывают. После завершения первоначального этапа обучения Azure ATP оповещения будут генерироваться на компьютерах, которые выполняют подозрительные запросы перечисления с помощью LDAP или запросы привилегированным группам с использованием методов, не зарегистрированных ранее.  

**Период обучения**: 10 дней на каждый компьютер с даты первого события, зарегистрированного на компьютере. 

**TP, B-TP или FP**
1.  Щелкните имя исходного компьютера и перейдите на страницу его профиля. 
    1. Ожидаемое ли это поведение для такого исходного компьютера? 
    2. Если это известный компьютер и такое поведение для него ожидаемо, **закройте** оповещение системы безопасности и исключите компьютер как действие **B-TP**. 

**Определение области бреши в системе безопасности**

1.  Проверьте выполненные запросы (например, от администраторов домена или всех пользователей в домене) и определите, были ли они выполнены успешно. Изучите результаты поиска по каждой уязвимой группе на наличие подозрительных действий, совершенных с группой или участниками такой группы.
2. Исследуйте [компьютер-источник](investigate-a-computer.md). 
    - С помощью запросов LDAP проверьте, выполнялись ли действия доступа к ресурсам с использованием каких-либо уязвимых имен участников безопасности.

**Предлагаемое исправление и шаги по профилактике**

1.  Уменьшите влияние исходного компьютера.
    1. Найдите средство, инициировавшее атаку, и удалите его.
    2. Запущено ли на компьютере средство проверки, которое выполняет различные запросы LDAP?
    3. Найдите пользователей, вошедших в систему во время выполнения подозрительного действия, так как они также могут быть скомпрометированы. Сбросьте их пароли и включите многофакторную проверку подлинности.
2.  Сбросьте пароль, если был осуществлен доступ к ресурсу имени субъекта-службы, который используется с учетной записью пользователя, а не компьютера.

## <a name="user-and-ip-address-reconnaissance-smb-external-id-2012"></a>Разведывательная атака с использованием пользователя и IP-адреса (SMB) (внешний код 2012) 

*Предыдущее название.* Разведывательная атака с использованием перечисления сеансов SMB

### <a name="description"></a>Описание

Перечисление, использующее протокол SMB, позволяет злоумышленникам узнать, в какие системы пользователи недавно выполнили вход. Получив эти сведения, злоумышленники могут перемещаться по сети, чтобы далее получить доступ к определенной конфиденциальной учетной записи.

Если перечисление сеансов SMB выполняется для контроллера домена, для такого обнаружения активируется оповещение. 

**TP, B-TP или FP**

Сканеры и приложения безопасности могут законным образом отправлять запросы к контроллерам домена для открытых сеансов SMB.

1. Должен ли компьютер-источник создавать действия этого типа?
2. Проверьте, запущен ли на исходном компьютере какой-либо сканер безопасности.  
    Если ответ — да, возможно, это действие B-TP. *Закройте* оповещение системы безопасности и исключите компьютер.
3. Проверьте пользователей, выполнивших операцию.
   Должны ли эти пользователи выполнять эти действия?  
    Если ответ — "да", *закройте* оповещение системы безопасности как действие B-TP.

**Определение области бреши в системе безопасности**

1. Исследуйте исходный компьютер.  
2. На странице оповещений проверьте наличие любых пользователей, подвергшихся атаке. Для дальнейшего анализа каждого такого пользователя проверьте его профиль. Рекомендуется начать анализ с конфиденциальных и приоритетных пользователей.

**Предлагаемое исправление и шаги по профилактике**

Используйте [средство Net Cease](https://gallery.technet.microsoft.com/Net-Cease-Blocking-Net-1e8dcb5b) для усиления защиты среды против этой атаки.

## <a name="user-and-group-membership-reconnaissance-samr-external-id-2021"></a>Разведывательная атака с использованием пользователей и членства в группах (SAMR) (внешний код 2021) 


*Предыдущее название.* разведывательная атака с использованием запросов к службам каталогов; 

**Описание**. Рекогносцировка с использованием пользователей и членства в группах применяется злоумышленниками для сопоставления структуры каталогов и привилегированных учетных записей для дальнейших этапов атаки. Одним из методов, используемых для запроса каталога для такого сопоставления, является удаленный протокол диспетчера учетной записи безопасности (SAM-R).  
При таком обнаружении в течение первого месяца после развертывания Azure ATP оповещения будут отсутствовать (период обучения). Во время периода обучения Azure ATP определяет, какие запросы SAM-R соответствуют каждому компьютеру. Это могут быть групповые или отдельные запросы конфиденциальной учетной записи. 

**Период обучения**

Четыре недели на контроллер домена, начиная с первой сетевой активности SAMR для конкретного контроллера домена.

**TP, B-TP или FP** 

1. Щелкните имя компьютера-источника, чтобы перейти на страницу профиля.        
   - Должен ли компьютер-источник выполнять действия этого типа?
     - Если ответ — "да", *закройте* оповещение системы безопасности как действие **B-TP** и исключите этот компьютер. 
   - Проверьте пользователя/пользователей, выполнивших операцию.
     - Эти пользователи постоянно входят на компьютер-источник или они являются администраторами, которые могут выполнять такие действия?   
     - Проверьте профиль пользователя и его соответствующие действия. Проанализируйте обычное поведение пользователей и выполните поиск других подозрительных действий с помощью [руководства по анализу](investigate-a-user.md). 
    
     Если вы ответили **да** на предыдущий вопрос, *закройте* оповещение как действие **B-TP**. 
  
**Определение области бреши в системе безопасности**

1. Просмотрите выполненные запросы (например, администраторов предприятия или администраторов), а также как они завершились — успешно или сбоем.
2. Исследуйте каждого обнаруженного пользователя с помощью руководства для исследования.
3. Исследуйте исходный компьютер.  
  
**Предлагаемое исправление и шаги по профилактике**

1. Уменьшите влияние исходного компьютера.
2. Найдите и удалите средство, инициировавшее атаку.
3. Найдите пользователей, выполнивших вход в систему во время вредоносной активности, так как они также могут быть скомпрометированы. Сбросьте их пароли и включите многофакторную проверку подлинности.
4. Сбросьте пароль исходного пользователя и включите многофакторную проверку подлинности.
5. Настройте управление доступом к сети и ограничьте число клиентов, которые могут выполнять удаленные вызовы групповой политики SAM.

> [!NOTE]
> Чтобы отключить оповещение системы безопасности Azure ATP, обратитесь в службу поддержки.

> [!div class="nextstepaction"]
> [Руководство по оповещениям о компрометации учетных данных](atp-compromised-credentials-alerts.md)

## <a name="see-also"></a>См. также

- [Проверка компьютера](investigate-a-computer.md)
- [Проверка пользователя](investigate-a-user.md)
- [Работа с оповещениями системы безопасности](working-with-suspicious-activities.md)
- [Оповещения о компрометации учетных данных](atp-compromised-credentials-alerts.md)
- [Оповещения об атаках бокового смещения](atp-lateral-movement-alerts.md)
- [Оповещения о захвате управления доменом](atp-domain-dominance-alerts.md)
- [Оповещения о краже данных](atp-exfiltration-alerts.md)
- [Справочник по журналу Azure ATP SIEM](cef-format-sa.md)
- [Работа с путями бокового смещения](use-case-lateral-movement-path.md)
- [Загляните на форум Azure ATP!](https://aka.ms/azureatpcommunity)