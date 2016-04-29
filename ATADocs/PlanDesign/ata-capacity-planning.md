---
# required metadata

title: Планирование производительности ATA | Microsoft Advanced Threat Analytics
description: В этой статье содержатся сведения, которые помогут определить, сколько серверов ATA потребуются для поддержки вашей сети
keywords:
author: rkarlin
manager: stevenpo
ms.date: 04/28/2016
ms.topic: get-started-article
ms.prod: identity-ata
ms.service: advanced-threat-analytics
ms.technology: security
ms.assetid: 279d79f2-962c-4c6f-9702-29744a5d50e2

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: bennyl
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# Планирование производительности ATA
В этой статье содержатся сведения, которые помогут определить, сколько серверов ATA потребуются для поддержки вашей сети.

## Определение размера и количества ресурсов для центра ATA
Чтобы проанализировать поведение пользователя, центру ATA требуются данные минимум за 30 дней. Ниже указаны сведения о пространстве на диске, которое необходимо базе данных ATA для одного контроллера домена. Чтобы вычислить весь объем пространства, необходимый для базы данных ATA, при наличии нескольких контроллеров домена, необходимо суммировать требуемый объем места на диске для каждого контроллера домена.

|Пакетов в секунду&#42;|Число ядер ЦП&#42;&#42;|Память (ГБ)|Объем хранилища ОС (ГБ)|Объем хранилища базы данных в день (ГБ)|Объем хранилища базы данных в месяц (ГБ)|Операции ввода-вывода в секунду&#42;&#42;&#42;|
|---------------------------|-------------------------|---------------|-------------------|---------------------------------|-----------------------------------|-----------------------------------|
|1000|4|48|200|1,5|45|30 (100)
|10 000|4|48|200|15|450|200 (300)
|40 000|8|64|200|60|1800|500 (1000)
|100 000|12|96|200|150|4500|1000 (1500)
|200 000|16|128|200|300|9000|2000 (2500)
&#42; Ежедневное среднее количество пакетов в секунду, отправляемых контроллерами домена, которые отслеживают шлюзы ATA.

&#42;&#42; Сюда относятся физические ядра, а не ядра с поддержкой технологии Hyper-Threading.

&#42;&#42;&#42; Средние значения (пиковые значения).
> [!NOTE]
> -   Совокупное максимальное количество обрабатываемых центром ATA кадров в секунду из всех отслеживаемых контроллеров домена составляет 200 000.
> -   При крупном развертывании (начиная с примерно 100 000 пакетов в секунду) требуется, чтобы журнал базы данных и сама база данных находились на разных дисках.
> -   Указанные в таблице объемы памяти — это фактические значения. Всегда учитывайте будущий рост нагрузки и помните, что на диске базы данных должно быть по крайней мере 20 % свободного пространства.
> -   Если на диске базы данных остается менее 20 % (100 ГБ) свободного пространства, самые старые данные за 24 часа будут удалены. Это будет происходить, пока на диске останется только 5 % или 50 ГБ свободного пространства (для хранения данных за 2 дня). Затем сбор данных будет остановлен.
> -  При выполнении действий чтения и записи задержка хранилища должна быть менее 10 мс.
> -  Соотношение между количеством операций чтения и записи должно составлять примерно 1:3 при обработке меньше 100 000 пакетов в секунду и 1:6 при обработке свыше 100 000 пакетов в секунду.

## Определение размера шлюза ATA
Шлюз ATA может поддерживать мониторинг нескольких контроллеров домена, что зависит от объема сетевого трафика отслеживаемых контроллеров домена.

|Пакетов в секунду&#42;|Число ядер ЦП&#42;&#42;|Память (ГБ)|Объем хранилища ОС (ГБ)|
|---------------------------|-------------------------|---------------|-------------------|
|10 000|4|12|80|
|20 000|8|24|100|
|40 000|16|64|200|
&#42; Общее количество пакетов в секунду, отправляемых всеми контроллерами домена, которые отслеживает конкретный шлюз ATA.

&#42; Общий объем зеркально отображенного трафика контроллера домена не может превышать емкость сетевого адаптера в шлюзе ATA.

&#42;&#42; Технология Hyper-Threading должна быть отключена.

## Оценка трафика контроллера домена
Существуют различные инструменты, с помощью которых можно определить среднее число пакетов в секунду, отправляемых с контроллеров домена. Если у вас нет таких инструментов, эти сведения можно отследить с помощью системного монитора.

Чтобы определить число пакетов в секунду, сделайте для каждого контроллера домена следующее:

1.  Откройте системный монитор.

    ![Изображение системного монитора](media/ATA-traffic-estimation-1.png)

2.  Разверните узел **Группы сборщиков данных**.

    ![Изображение узла "Группы сборщиков данных"](media/ATA-traffic-estimation-2.png)

3.  Щелкните правой кнопкой мыши узел **Задано пользователем** и последовательно выберите **Создать** &gt; **Группа сборщиков данных**.

    ![Изображение окна создания группы сборщиков данных](media/ATA-traffic-estimation-3.png)

4.  Введите имя группы сборщиков данных и установите переключатель **Создать вручную (для опытных)**.

5.  В разделе **Какой тип данных вы хотите использовать?** установите переключатель **Создать журналы данных и счетчик производительности**.

    ![Изображение окна выбора типа данных для новой группы сборщиков данных](media/ATA-traffic-estimation-5.png)

6.  В разделе **Данные каких счетчиков производительности следует записывать в журнал?** выберите команду **Добавить**.

7.  Разверните узел **Сетевой адаптер**, выберите пункт **Пакетов/с** и выберите подходящий экземпляр. Если вы не уверены, выберите значение **&lt;Все экземпляры&gt;** и нажмите кнопку **Добавить**, а затем — **ОК**.

    > [!NOTE]
    > Чтобы увидеть имя адаптера и сведения о конфигурации, введите в командной строке команду `ipconfig /all`.

    ![Изображение окна добавления счетчиков производительности](media/ATA-traffic-estimation-7.png)

8.  Установите для параметра **Интервал выборки** значение **1 секунда**.

9. Задайте папку для хранения данных.

10. В разделе **Создать группу сборщиков данных** установите переключатель **Запустить группу сборщиков данных сейчас** и нажмите кнопку **Готово**.

    После этого отобразится новая группа сборщиков данных с зеленым треугольником, который указывает на то, что она активна.

11. Через 24 часа остановите группу сборщиков данных, щелкнув ее правой кнопкой мыши и выбрав **Остановить**.

    ![Изображения остановки группы сборщиков данных](media/ATA-traffic-estimation-12.png)

12. В проводнике перейдите к папке, в которой сохранен BLG-файл, и дважды щелкните его, чтобы открыть в системном мониторе.

13. Выберите счетчик пакетов в секунду и запишите приведенные в нем среднее и максимальные значения.

    ![Изображения счетчика пакетов в секунду](media/ATA-traffic-estimation-14.png)

## См. также
- [Предварительные требования для ATA](ata-prerequisites.md)
- [Архитектура ATA](/advanced-threat-analytics/Understand/ata-architecture)
- [Для получения поддержки посетите наш форум.](https://social.technet.microsoft.com/Forums/security/en-US/home?forum=mata)


<!--HONumber=Apr16_HO2-->

