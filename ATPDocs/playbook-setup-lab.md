---
title: Руководство по настройке лаборатории оповещений безопасности Azure ATP
description: В этом руководстве показано, как настроить тестовую лабораторию Azure ATP, чтобы имитировать угрозы, которые должно обнаружить решение Azure ATP.
ms.service: azure-advanced-threat-protection
ms.topic: how-to
author: shsagir
ms.author: shsagir
ms.date: 02/28/2019
ms.reviewer: itargoet
ms.openlocfilehash: 5b7bc09b0327260504900c6a0b075b243c02f70e
ms.sourcegitcommit: 0c356b0860ae8663254e0cf6f04001bcc91ce207
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/21/2020
ms.locfileid: "90828729"
---
# <a name="tutorial-setup-an-atp-security-alert-lab"></a>Учебник. Настройка лаборатории оповещений системы безопасности ATP 

 В лаборатории оповещений системы безопасности Azure ATP можно продемонстрировать возможности **Azure ATP**в определении и обнаружении подозрительных действий и потенциальных атак для сети. В этом первом руководстве из четырех в этой серии приводятся сведения о создании лабораторной среды для тестирования *дискретных* обнаружений Azure ATP. Лаборатория оповещений системы безопасности в первую очередь использует возможности Azure ATP *по работе с сигнатурами*. Эта лаборатория не охватывает обнаружения на основе поведения пользователей или сущностей с использованием расширенных возможностей машинного обучения, так как для их применения изучаемый период с реальным сетевым трафиком должен составлять до 30 дней. Дополнительные сведения по каждому руководству из этой серии о лаборатории для оповещений системы безопасности ATP см. в [этой статье](playbook-lab-overview.md). 


Изучив данный учебник, вы научитесь: 

> [!div class="checklist"]
> * Настроите сервер и компьютеры лаборатории.
> * Настроите Active Directory с пользователями и группами.
> * Установите и настроите Azure ATP.
> * Установите локальные политики для серверов и компьютеров.
> * Сымитируете сценарий управления службы технической поддержки с использованием запланированной задачи.

## <a name="prerequisites"></a>Предварительные требования

1. [Контроллер домена и две рабочие станции в лаборатории](#servers-and-computers).
   - Выполните [расконсервацию Active Directory (AD) для добавления пользователей](#bkmk_hydrate).
1. [Экземпляр Azure ATP](install-step1.md), [подключенный к Active Directory](install-step2.md).
1. [Скачайте](install-step3.md) и [установите последнюю версию датчика Azure ATP](install-step4.md) на контроллере домена в лаборатории.
1. Ознакомьтесь [со сведениями о рабочих станциях с привилегированным доступом](/windows-server/identity/securing-privileged-access/privileged-access-workstations) и [политикой SAMR](/windows/security/threat-protection/security-policy-settings/network-access-restrict-clients-allowed-to-make-remote-sam-calls).

## <a name="recommendations"></a>Рекомендации

Рекомендуем как можно точнее следовать инструкции при настройке лаборатории. Чем точнее параметры настроенной лаборатории совпадают с указанными в инструкции, тем проще будет выполнить процедуры тестирования Azure ATP. После завершения настройки лаборатории вы будете готовы к выполнению действий с использованием предлагаемых средств изучения атак и просмотру обнаружений этих действий с помощью Azure ATP.

Структура вашей лаборатории должна быть максимально приближенной к приведенной ниже схеме:

![Структура тестовой лаборатории Azure ATP](media/playbook-atp-setup-lab.png)

### <a name="servers-and-computers"></a>Серверы и компьютеры

В приведенной ниже таблице подробно описаны компьютеры и необходимые конфигурации. IP-адреса предоставляются только для справочных целей, чтобы помочь вам разобраться.

В примерах для этих руководств используется следующее NetBIOS-имя для леса: **CONTOSO.AZURE**.

|  Полное доменное имя. | OS | IP-адрес | Назначение |
|------|-------|---------|--------------|
| ContosoDC.contoso.azure | Windows Server 2012 R2 | 10.0.24.4 | Контроллер домена с установленным локально датчиком Azure ATP |
| VictimPC.contoso.azure | Windows 10 | 10.0.24.5 |Компьютер атакуемого |
| AdminPC.contoso.azure | Windows 10  | 10.0.24.6 | Компьютер администратора домена (иногда называется "Защищенная рабочая станция администратора" или "Привилегированная рабочая станция администратора") |

### <a name="active-directory-users-and-groups"></a>Пользователи и группы в Active Directory

В этой лаборатории находятся три основных пользователя и одна учетная запись службы. Учетная запись службы предназначена для Azure ATP. Она используется как для целей синхронизации LDAP, так и для SAMR.

Кроме того, там находится группа безопасности Helpdesk, членом которой является пользователь Ron HelpDesk. Эта группа безопасности представляет собой имитацию службы технической поддержки. Группа безопасности соединена с объектом групповой политики, который предоставляет нашим членам службы технической поддержки права локального администратора на соответствующих компьютерах. Эта конфигурация используется для имитации реалистичной административной модели в рабочей среде.

| Полное имя    | Учетная запись диспетчера учетных записей безопасности |Назначение|
|--------------|------------|--------------------------------------------------------------------------------------------------|
| Jeff Leatherman  | JeffL  | В ближайшее время станет жертвой весьма эффективной фишинговой атаки  |
| Ron HelpDesk  | RonHD  |Команда ИТ-специалистов Contoso полагается на этого пользователя для устранения различных проблем. Он является членом группы безопасности Helpdesk. |
| Samira Abbasi | SamiraA  | В Contoso этот пользователь является администратором домена. |
| Служба Azure ATP | AATPService | Учетная запись службы Azure ATP |

## <a name="azure-atp-base-lab-environment"></a>Базовая лабораторная среда Azure ATP

Чтобы настроить базовую лабораторию, мы добавим пользователей и группы в Active Directory, изменим политику SAM и добавим привилегированную группу в Azure ATP.

### <a name="hydrate-active-directory-users-on-contosodc"></a><a name="bkmk_hydrate"></a> Расконсервация службы Active Directory для добавления в нее пользователей ContosoDC

Чтобы упростить лабораторию, мы автоматизировали процесс создания фиктивных пользователей и групп в Active Directory. Этот сценарий будет выполнен как предварительное условие для этого руководства. Вы можете использовать готовый сценарий или изменить его для расконсервации среды Active Directory в вашей лаборатории. Если вы не хотите использовать сценарий, выполните эту операцию вручную.

Чтобы добавить пользователей в Active Directory, выполните следующий сценарий от имени администратора домена в ContosoDC:

``` PowerShell

# Store the user passwords as variables
$SamiraASecurePass = ConvertTo-SecureString -String 'NinjaCat123' -AsPlainText -Force
$ronHdSecurePass = ConvertTo-SecureString -String 'FightingTiger$' -AsPlainText -Force
$jefflSecurePass = ConvertTo-SecureString -String 'Password$fun' -AsPlainText -Force
$AATPService = ConvertTo-SecureString -String 'Password123!@#' -AsPlainText -Force

# Create new AD user SamiraA and add her to the domain admins group
New-ADUser -Name SamiraA -DisplayName "Samira Abbasi" -PasswordNeverExpires $true -AccountPassword $samiraASecurePass -Enabled $true
Add-ADGroupMember -Identity "Domain Admins" -Members SamiraA

# Create new AD user RonHD, create new Helpdesk SG, add RonHD to the Helpdesk SG
New-ADUser -Name RonHD -DisplayName "Ron Helpdesk" -PasswordNeverExpires $true -AccountPassword $ronHdSecurePass -Enabled $true
New-ADGroup -Name Helpdesk -GroupScope Global -GroupCategory Security
Add-ADGroupMember -Identity "Helpdesk" -Members "RonHD"

# Create new AD user JeffL
New-ADUser -Name JeffL -DisplayName "Jeff Leatherman" -PasswordNeverExpires $true -AccountPassword $jefflSecurePass -Enabled $true

# Take note of the "AATPService" user below which will be our service account for Azure ATP.
# Create new AD user Azure ATP Service

New-ADUser -Name AatpService -DisplayName "Azure ATP/ATA Service" -PasswordNeverExpires $true -AccountPassword $AATPService -Enabled $true

```

### <a name="configure-sam-r-capabilities-from-contosodc"></a>Настройка возможностей SAM-R из ContosoDC

Чтобы служба Azure ATP правильно выполняла перечисление SAM-R и создавала пути бокового смещения, вам нужно изменить политику SAM.

1. Найдите свою политику SAM в разделе **политики \> Параметры Windows настройки \> безопасности \> Локальные политики \> Параметры безопасности \> "сетевой доступ: разрешить клиентам выполнять удаленные вызовы SAM"**_

    ![Измените групповую политику, разрешив Azure ATP использовать возможности пути бокового смещения.](media/playbook-labsetup-localgrouppolicies3.png)

1. Добавьте учетную запись службы Azure ATP (AATPService) в список утвержденных учетных записей, которые могут выполнять это действие в современных системах Windows.

    ![Добавление службы](media/samr-add-service.png)

### <a name="add-sensitive-group-to-azure-atp"></a>Добавление привилегированной группы в Azure ATP

Добавление группы безопасности Helpdesk в качестве **привилегированной группы** позволит вам использовать функцию графика бокового смещения в службе Azure ATP. Рекомендуем помечать тегами привилегированных пользователей и группы, которые не обязательно являются администраторами домена, но имеют привилегии на использование многочисленных ресурсов.

1. На портале Azure ATP в строке меню щелкните значок шестеренки **Настройка**.

1. В разделе **Обнаружение** щелкните **теги сущностей**.

    ![Теги сущностей Azure ATP](media/entity-tags.png)

1. В разделе **Конфиденциально** введите имя Helpdesk для **конфиденциальных групп**,а затем щелкните значок **+**, чтобы добавить их.

    ![Отметьте Helpdesk в качестве привилегированной группы Azure ATP, чтобы включить графики бокового смещения и отчеты для этой группы.](media/playbook-labsetup-helpdesksensitivegroup.png)

1. Выберите команду **Сохранить**.

### <a name="azure-atp-lab-base-setup-checklist"></a>Контрольный список для настройки базовой лаборатории Azure ATP

На этом этапе у вас должна быть настроена базовая лаборатория Azure ATP. Кроме того, должна быть подготовлена служба Azure ATP и добавлены пользователи. Просмотрите контрольный список, чтобы убедиться, что настройка базовой лаборатории завершена.  

| Шаг    | Действие | Состояние |
|--------------|------------|------------------|
| 1  | Установка датчика Azure ATP на компьютере ContosoDC (этап подготовки)| - [ ] |
| 2  | Создание пользователей и групп в Active Directory  | - [ ] |
| 3  | Настройка учетной записи службы Azure ATP для SAMR должным образом | - [ ] |
| 4  | Добавление группы безопасности Helpdesk в качестве **привилегированной группы** в Azure ATP| - [ ] |

## <a name="set-up-the-lab-workstations"></a>Настройка рабочих станций лаборатории

Настроив базовую лабораторию Azure ATP, вы можете приступить к настройке рабочей станции, чтобы подготовиться к ознакомлению со следующими руководствами из этой серии. Мы выполним расконсервацию компьютеров VictimPC и AdminPC, чтобы эта лаборатория выглядела активной.

### <a name="victimpc-local-policies"></a>Локальные политики VictimPC

Следующим шагом является завершение настройки локальной политики. На компьютере **VictimPC** в качестве членов группы локальных администраторов добавлены пользователь JeffL и группа безопасности Helpdesk. Как и во многих организациях, JeffL является администратором на собственном устройстве (**VictimPC**).

Настройте локальные политики от имени локального администратора, запустив автоматизированный сценарий PowerShell:

``` PowerShell
# Add JeffL to local Administrators group on VictimPC
Add-LocalGroupMember -Group "Administrators" -Member "Contoso\JeffL"
# Add Helpdesk to local Administrators group on VictimPC
Add-LocalGroupMember -Group "Administrators" -Member "Contoso\Helpdesk"
```

Проверьте группу администраторов на компьютере **VictimPC** и убедитесь, что в нее в качестве членов входят, по меньшей мере, Helpdesk и JeffL:

![Helpdesk и JeffV в качестве членов в группе локальных администраторов для VictimPC](media/playbook-labsetup-localgrouppolicies2.png)

### <a name="simulate-helpdesk-support-on-victimpc"></a><a name="helpdesk-simulation"></a> Имитация работы службы технической поддержки на компьютере VictimPC

Для имитации рабочей управляемой сети создайте запланированную задачу на компьютере **VictimPC**, чтобы запустить процесс cmd.exe от имени пользователя **RonHD**.

1. Из **консоли PowerShell с повышенными привилегиями** выполните на VictimPC следующую команду:

    ``` PowerShell
    $action = New-ScheduledTaskAction -Execute 'cmd.exe'
    $trigger = New-ScheduledTaskTrigger -AtLogOn
    $runAs = 'Contoso\RonHD'
    $ronHHDPass = 'FightingTiger$'
    Register-ScheduledTask -TaskName "RonHD Cmd.exe - AATP SA Playbook" -Trigger $trigger -User $runAs -Password $ronHHDPass -Action $action
    ```

1. Войдите в систему компьютера от имени пользователя **JeffL**. Процесс cmd.exe запускается в контексте пользователя RonHD после входа в систему, имитируя службу технической поддержки, управляющую компьютером.

### <a name="turn-off-antivirus-on-victimpc"></a>Отключение антивирусной программы на компьютере VictimPC

В целях тестирования отключите все антивирусные решения, работающие в лабораторной среде. Так во время выполнения этих упражнений мы сможем сосредоточиться на Azure ATP, а не на методах уклонения от вирусов.

Вы не сможете скачать некоторые средства из следующего раздела, если сначала не отключите антивирусные решения. Кроме того, если антивирусная программа будет включена после установки средств для атаки, вам нужно будет отключить ее и снова скачать средства.

### <a name="stage-common-hacker-tools"></a>Установка общих средств для взлома

> [!WARNING]
> Приведенные ниже средства представлены только для научных целей. Корпорация Майкрософт **не** является владельцем этих средств, не может дать и не дает гарантий относительно их поведения. Эти средства следует запускать **только** в тестовой лабораторной среде.

Для запуска сборника схем оповещений системы безопасности Azure ATP необходимы следующие средства.

| Инструмент | URL-адрес |
|----|-----|
| Mimikatz | [Mimikatz на сайте GitHub](https://github.com/gentilkiwi/mimikatz) |
| PowerSploit | [PowerSploit на сайте GitHub](https://github.com/PowerShellMafia/PowerSploit) |
| PsExec | [Microsoft Docs](/sysinternals/downloads/psexec) |
| NetSess | [Средства JoeWare](https://www.joeware.net/freetools) |

Мы благодарим авторов этих средств исследования за то, что они дали пользователям возможность лучше понять риск и влияние кибератак.

### <a name="adminpc-local-policies"></a>Локальные политики AdminPC

Необходимо добавить **Helpdesk** в группу локальных администраторов на компьютере **AdminPC**. Затем удалите администраторов домена из группы локальных администраторов. Этот шаг гарантирует, что Samira, администратор домена, не является администратором AdminPC. Это лучшая методика в области учетных данных. Выполните этот шаг вручную или используйте предоставленный сценарий PowerShell.

1. Добавьте **Helpdesk** на компьютер **AdminPC** и *удалите* администраторов домена из группы локальных администраторов, запустив следующий сценарий PowerShell:

    ``` PowerShell
   # Add Helpdesk to local Administrators group
   Add-LocalGroupMember -Group "Administrators" -Member "Contoso\Helpdesk"
   # Remove Domain Admins from local Administrators group
   Remove-LocalGroupMember -Group "Administrators" -Member "Domain Admins"

   ```

1. После запуска сценария **Helpdesk** переместится в локальный список в разделе **Администраторы** > **Члены группы** на компьютере **AdminPC**.
![Helpdesk в группе локальных администраторов для AdminPC](media/playbook-labsetup-localgrouppolicies1.png)

### <a name="simulate-domain-activities-from-adminpc"></a>Имитация действий домена из AdminPC

Действия домена должен имитировать пользователь SamiraA. Этот шаг можно выполнить вручную или же использовать предоставленный сценарий PowerShell. Сценарий PowerShell обращается к контроллеру домена каждые 5 минут и выполняет имитацию действия сети от имени пользователя Samira.

Выполните приведенный ниже сценарий в командной строке PowerShell на компьютере AdminPC от имени **SamiraA**.

```PowerShell

while ($true)
{
    Invoke-Expression "dir \\ContosoDC\c$"
    Start-Sleep -Seconds 300
}

```

### <a name="workstation-setup-checklist"></a>Контрольный список настройки рабочей станции

Просмотрите контрольный список, чтобы убедиться, что настройка базовой рабочей станции завершена.

| Шаг    | Действие | Состояние |
|--------------|------------|------------------|
| 1  | Добавление JeffL и Helpdesk в качестве локальных администраторов на компьютер VictimPC | - [ ] |
| 2  | Создание запланированной задачи, выполняющейся от имени пользователя RonHD на компьютере VictimPC | - [ ] |
| 3  | Отключение антивирусного решения на компьютере VictimPC | - [ ] |
| 4  | Установка средств для взлома на компьютере VictimPC| - [ ] |
| 5  | Добавление Helpdesk и удаление администраторов домена из группы локальных администраторов на компьютере AdminPC| - [ ] |
| 6  | Выполнение сценария PowerShell от имени пользователя Samira для имитации действий домена | - [ ] |

## <a name="mission-accomplished"></a>Миссия выполнена!

Ваша лаборатория Azure ATP готова к использованию. Методы, использованные для этой настройки, были выбраны с учетом необходимости управления ресурсами (*чем-то* или *кем-то*), для чего требуются права локального администратора. Помимо приведенных выше, в лаборатории возможны и другие способы имитации рабочего процесса управления:

- Вход и выход из системы VictimPC с использованием учетной записи RonHD.
- Добавление другой версии запланированной задачи.
- Сеанс RDP.
- Выполнение команды runas в командной строке.

 Для достижения наилучших результатов выберите способ имитирования, который вы сможете автоматизировать в своей лаборатории для обеспечения согласованности.


## <a name="next-steps"></a>Дальнейшие действия

Протестируйте свою лабораторную среду Azure ATP с использованием сборника схем оповещений системы безопасности Azure ATP для каждого этапа кибератаки, начиная с этапа разведки.  

> [!div class="nextstepaction"]
> [Руководство. Сборник схем рекогносцировки](playbook-reconnaissance.md)


## <a name="join-the-community"></a>Присоединяйтесь к сообществу!

Возникли дополнительные вопросы или желание обсудить с другими пользователями службу Azure ATP и связанные с ней вопросы безопасности? Присоединяйтесь к [сообществу Azure ATP](https://techcommunity.microsoft.com/t5/Azure-Advanced-Threat-Protection/bd-p/AzureAdvancedThreatProtection)!