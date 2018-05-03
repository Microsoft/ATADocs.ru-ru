---
title: Устранение известных неполадок Azure ATP | Документация Майкрософт
description: В этой статье описываются способы устранения неполадок в службе Azure ATP.
keywords: ''
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 4/10/2018
ms.topic: article
ms.prod: ''
ms.service: azure-advanced-threat-protection
ms.technology: ''
ms.assetid: 23386e36-2756-4291-923f-fa8607b5518a
ms.reviewer: itargoet
ms.suite: ems
ms.openlocfilehash: 2112e9fea1f316ff12d87b3a477b78bff4457a5f
ms.sourcegitcommit: e0209c6db649a1ced8303bb1692596b9a19db60d
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
*Применяется к: Azure Advanced Threat Protection*


# <a name="troubleshooting-azure-atp-known-issues"></a>Устранение известных неполадок Azure ATP 


## <a name="deployment-log-location"></a>Расположение журнала развертывания
 
Журналы развертывания Azure ATP расположены во временном каталоге пользователя, установившего продукт. Их можно найти по следующему пути в месте установки по умолчанию: C:\Users\Administrator\AppData\Local\Temp (or one directory above %temp%).

## <a name="azure-atp-sensor-nic-teaming-issue"></a>Проблема с датчиком ATP на компьютере с функцией объединения сетевых карт

При попытке установить датчик ATP на компьютере, настроенном с функцией объединения сетевых карт, возникает ошибка установки. Чтобы установить датчик ATP на компьютере с функцией объединения сетевых карт, следуйте приведенным ниже инструкциям.

Если вы еще не установили датчик, сделайте следующее:

1.  Скачать Npcap из [https://nmap.org/npcap/](https://nmap.org/npcap/).
2.  Удалите библиотеку WinPcap, если она установлена.
3.  Установите Npcap со следующими параметрами: loopback_support=no, winpcap_mode=yes.
4.  Установите пакет датчика.

Если вы уже установили датчик, сделайте следующее:

1.  Скачать Npcap из [https://nmap.org/npcap/](https://nmap.org/npcap/).
2.  Удалите датчик.
3.  Удалите WinPcap.
4.  Установите Npcap со следующими параметрами: loopback_support=no, winpcap_mode=yes.
5.  Переустановите пакет датчика.

## <a name="windows-defender-atp-integration-issue"></a>Проблема интеграции ATP в Защитнике Windows

Azure Advanced Threat Protection позволяет интегрировать Azure ATP с ATP в Защитнике Windows. Сейчас интеграция доступна только клиентам закрытой предварительной версии ATP в Защитнике Windows. 

## <a name="vmware-virtual-machine-sensor-issue"></a>Проблема с датчиком виртуальной машины VMware

Если на виртуальных машинах VMware установлен датчик Azure ATP, может появиться предупреждение системы мониторинга **Some network traffic is not being analyzed** (Часть сетевого трафика не анализируется). Это происходит из-за несоответствия конфигураций в VMware.

Чтобы решить эту проблему, выполните указанные ниже действия.

Задайте в конфигурации сетевого адаптера виртуальной машины значения **0** или **Отключено** для следующих параметров: TsoEnable, LargeSendOffload, TSO Offload, Giant TSO Offload.
> [!NOTE]
> Для датчиков Azure ATP в конфигурации сетевого адаптера нужно отключить только параметр **IPv4 TSO Offload**.

 ![Проблема с датчиком VMware](./media/vm-sensor-issue.png)

## <a name="see-also"></a>См. также
- [Предварительные требования к Azure ATP](atp-prerequisites.md)
- [Планирование производительности Azure ATP](atp-capacity-planning.md)
- [Настройка сбора данных о событиях](configure-event-collection.md)
- [Настройка пересылки событий Windows](configure-event-forwarding.md#configuring-windows-event-forwarding)
- [Обязательно ознакомьтесь с форумом ATP](https://aka.ms/azureatpcommunity)