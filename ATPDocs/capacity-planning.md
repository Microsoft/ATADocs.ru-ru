---
title: Планирование развертывания в защитнике Майкрософт
description: Помогает спланировать развертывание и решить, сколько защитника Майкрософт для серверов удостоверений потребуется для поддержки сети.
ms.date: 10/26/2020
ms.topic: how-to
ms.openlocfilehash: 8266742f2766977685d465b3634c7a71a51af682
ms.sourcegitcommit: a892419a5cb95412e4643c35a9a72092421628ec
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/16/2021
ms.locfileid: "100533908"
---
# <a name="plan-capacity-for-microsoft-defender-for-identity"></a>Планирование производительности защитника Майкрософт для идентификации

В этом руководство вы определите, сколько [!INCLUDE [Product long](includes/product-long.md)] датчиков вам нужно.

## <a name="prerequisites"></a>Предварительные условия

- Загрузите [ [!INCLUDE [Product short](includes/product-short.md)] средство изменения размера](https://aka.ms/aatpsizingtool).
- Знакомство со статьей [Архитектура [!INCLUDE [Product short](includes/product-short.md)]](architecture.md).
- Знакомство со статьей [Предварительные требования [!INCLUDE [Product short](includes/product-short.md)]](prerequisites.md).

## <a name="use-the-sizing-tool"></a>Использование средства изменения размера

Рекомендуемый и самый простой способ определить емкость [!INCLUDE [Product short](includes/product-short.md)] развертывания — использовать [!INCLUDE [Product short](includes/product-short.md)] средство изменения размера. Если не удается использовать это средство, вы можете собрать информацию о трафике вручную. Дополнительные сведения о методе сбора информации вручную см. в разделе [Средство оценки трафика контроллера домена](#manual-sizing) этой статьи.

1. Запустите [!INCLUDE [Product short](includes/product-short.md)] средство изменения размера **TriSizingTool.exe** из скачанного ZIP-файла.
1. Когда средство завершит работу, откройте файл Excel с результатами.
1. В файле Excel найдите и щелкните лист **Azure ATP Summary** (Сводка Azure ATP). Другие листы не понадобятся, так как они используются при планировании ресурсов ATA.
    ![Пример средства планирования емкости](media/capacity-tool.png)

1. В файле Excel с результатами найдите поле **Busy Packets/sec** (Кол-во занятых пакетов/с) в таблице датчика Azure ATP и запишите его значение.
1. Сопоставьте поле " **занятых пакетов/с** " с полем " **пакетов в секунду** " в разделе " [ [!INCLUDE [Product short](includes/product-short.md)] таблица датчиков](#sizing) " этой статьи. Воспользуйтесь информацией из этих полей, чтобы определить объем памяти и ресурсы ЦП, которые требуются для работы датчика.

<a name="sizing"></a>

## <a name="defender-for-identity-sensor-sizing"></a>Защитник для изменения размера датчика удостоверений

[!INCLUDE [Product short](includes/product-short.md)]Датчик может поддерживать мониторинг контроллера домена в зависимости от объема сетевого трафика, создаваемого контроллером домена. В следующей таблице приводятся приблизительные данные. Окончательный объем, анализируемый датчиком, зависит от объема и распределения трафика.

Следующие значения емкости для ЦП и ОЗУ имеют отношение к **потреблению самого датчика**, а не к емкости контроллеров доменов.

|Пакетов в секунду|ЦП (ядра)\*|Память\*\* (ГБ)|
|----|----|-----|
|0–1 тыс.|0,25|2,50|
|1–5 тыс.|0,75|6,00|
|5–10 тыс.|1,00|6,50|
|10–20 тыс.|2,00|9,00|
|20–50 тыс.|3,50|9,50|
|50–75 тыс. |3,50|9,50|
|75–100 тыс.|3,50|9,50|

\* Здесь указаны физические ядра, а не ядра с поддержкой технологии Hyper-Threading.  
\*\* Оперативная память (ОЗУ)

При определении размера, учитывайте следующие моменты:

- Общее количество ядер, которые будет использовать служба датчика.  
Рекомендуем не использовать ядра с поддержкой технологии Hyper-Threading. Работа с ядрами с технологией Hyper-Threading может привести к [!INCLUDE [Product short](includes/product-short.md)] проблемам с работоспособностью датчика.
- Общий объем памяти, который будет использовать служба датчика.
- Если контроллер домена не содержит ресурсы, необходимые для [!INCLUDE [Product short](includes/product-short.md)] датчика, это не повлияет на производительность контроллера домена. Однако [!INCLUDE [Product short](includes/product-short.md)] датчик может работать не так, как ожидалось.
- При запуске в качестве виртуальной машины всю память нужно выделить для виртуальной машины на постоянной основе.
- Для оптимальной производительности задайте для **параметра питания** датчик значение [!INCLUDE [Product short](includes/product-short.md)] **Высокая производительность**.
- Для этой задачи необходимо не менее 2 ядер и
- Требуется не менее 6 ГБ свободного пространства на жестком диске, рекомендуется 10 ГБ, включая пространство, необходимое для [!INCLUDE [Product short](includes/product-short.md)] двоичных файлов и журналов.

### <a name="dynamic-memory"></a>Динамическая память

> [!NOTE]
> При запуске в качестве виртуальной машины всю память нужно выделить для виртуальной машины на постоянной основе.

|Платформа запуска виртуальной машины|Описание:|
|------------|-------------|
|Hyper-V|Убедитесь, что для виртуальной машины отключена функция **Включить динамическую память**.|
|VMWare|Убедитесь, что настроенный объем памяти и объем зарезервированной памяти одинаковы, или выберите параметр **Reserve all guest memory (All locked)** (Зарезервировать всю память гостевой ОС (все заблокированные)) в настройках виртуальной машины.|
|Другой узел виртуализации|Сведения о том, как обеспечить полное выделение памяти для виртуальной машины на постоянной основе, см. в документации, предоставленной поставщиком. |

<a name="manual-sizing"></a>

## <a name="domain-controller-traffic-estimation"></a>Оценка трафика контроллера домена

Если по каким-либо причинам вы не можете использовать [!INCLUDE [Product short](includes/product-short.md)] средство изменения размера, вручную Соберите данные счетчика пакетов/с на всех контроллерах домена. Рекомендуем собирать данные за 24 часа с коротким интервалом (примерно 5 секунд). Затем для каждого контроллера домена вычислите ежедневное среднее значение и среднее значение самого занятого периода (15 минут). В следующих разделах представлены инструкции по сбору числа пакетов в секунду с одного контроллера домена.

Существуют различные инструменты, с помощью которых можно определить среднее число пакетов в секунду, отправляемых с контроллеров домена. Если у вас нет таких инструментов, эти сведения можно отследить с помощью системного монитора.

Чтобы определить количество пакетов в секунду, выполните на каждом контроллере домена указанные ниже действия:

1. Откройте системный монитор.

    ![Изображение системного монитора](media/traffic-estimation-1.png)

1. Разверните узел **Группы сборщиков данных**.

    ![Изображение узла "Группы сборщиков данных"](media/traffic-estimation-2.png)

1. Щелкните правой кнопкой мыши узел **Задано пользователем** и последовательно выберите **Создать** &gt; **Группа сборщиков данных**.

    ![Изображение окна создания группы сборщиков данных](media/traffic-estimation-3.png)

1. Введите имя группы сборщиков данных и установите переключатель **Создать вручную (для опытных)** .

1. В разделе **Какой тип данных вы хотите использовать?** выберите **Создать журналы данных и Счетчик производительности**.

    ![Изображение окна выбора типа данных для новой группы сборщиков данных](media/traffic-estimation-5.png)

1. В разделе **Какие счетчики производительности следует записывать в журнал?** нажмите кнопку **Добавить**.

1. Разверните узел **Сетевой адаптер**, выберите пункт **Пакетов/с** и выберите подходящий экземпляр. Если вы не уверены, выберите значение **&lt;Все экземпляры&gt;** и нажмите кнопку **Добавить**, а затем — **ОК**.

    > [!NOTE]
    > Чтобы увидеть имя адаптера и сведения о конфигурации, выполните в командной строке команду `ipconfig /all`.

    ![Изображение окна добавления счетчиков производительности](media/traffic-estimation-7.png)

1. Установите для параметра **Интервал выборки** значение **5 секунд**.

1. Задайте папку для хранения данных.

1. В разделе **Create the data collector set** (Создать группу сборщиков данных) выберите **Запустить группу сборщиков данных сейчас** и нажмите кнопку **Готово**.

    После этого отобразится созданная группа сборщиков данных с зеленым треугольником, который указывает на то, что она активна.

1. Через 24 часа остановите группу сборщиков данных, щелкнув ее правой кнопкой мыши и выбрав пункт **Остановить**.

    ![Изображения остановки группы сборщиков данных](media/traffic-estimation-12.png)

1. В проводнике перейдите к папке, в которой сохранен BLG-файл, и дважды щелкните его, чтобы открыть в системном мониторе.

1. Выберите счетчик пакетов в секунду и запишите приведенные в нем среднее и максимальные значения.

    ![Изображения счетчика пакетов в секунду](media/traffic-estimation-14.png)

## <a name="next-steps"></a>Дальнейшие шаги

В этом руководство вы определили, сколько [!INCLUDE [Product short](includes/product-short.md)] датчиков вам нужно. Вы также можете определить размер датчиков. Перейдите к [!INCLUDE [Product short](includes/product-short.md)] краткому руководству по созданию экземпляра.

> [!div class="nextstepaction"]
> [Создание [!INCLUDE [Product short](includes/product-short.md)] экземпляра](install-step1.md)

## <a name="join-the-community"></a>Присоединяйтесь к сообществу!

У вас есть дополнительные вопросы или вы хотите обсудить с другими пользователями особенности использования [!INCLUDE [Product short](includes/product-short.md)] или вопросы, связанные с безопасностью? Присоединяйтесь к [сообществу [!INCLUDE [Product short](includes/product-short.md)]](https://aka.ms/MDIcommunity).
