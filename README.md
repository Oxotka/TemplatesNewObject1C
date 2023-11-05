# Шаблоны новых объектов 1С для 1С:Бухгалтерия

Используется для создания новых объектов в конфигурации, чтобы не забыть, что нужно сделать.
Сделано на примере 1С:Бухгалтерия предприятия, в других конфигурациях могут быть похожие объекты.

# Константы

1. Новую константу следует включить в план обмена "[МиграцияПриложений](https://its.1c.ru/db/smtl/content/22218931/hdoc)", при это авторегистрация должна быть выключена.

2. Для работы в распределенной информационной базе константу следует включить в соответствующие подписки и планы обменов. Названия обычно заканчиваются на "РегистрацияКонстанты", например, АвтономнаяРаботаРегистрацияКонстанты.
Для Бухгалтерии предприятия это:
Константы:
- **АвтономнаяРаботаРегистрацияКонстанты**
- **ПолныйРегистрацияКонстанты**
- **ПоОрганизацииРегистрацияКонстанты**

Планы Обменов:
- **АвтономнаяРабота**
- **Полный**
- **ПоОрганизации**

![NewConstant](img/NewConstant.png)

# Документы

## Основные свойства

1. **Имя**. Имя дается в единственном числе, например ЗаказПокупателя, ПеремещениеТоваров, Анкета.

<details>
<summary>Подробнее в стандарте Имена объектов метаданных в конфигурациях</summary>

Ссылка на стандарт - [Имена объектов метаданных в конфигурациях](https://its.1c.ru/db/v8std/content/550/hdoc)

Имена документов, напротив, даются в единственном числе. Например: ЗаказПокупателя, ПеремещениеТоваров, Анкета.

При этом следует избегать в именах документов слов, от удаления которых смысл не меняется, например: «Документ…».

При выборе имени документа следует различать два случая:

1. В первую очередь, следует стараться отразить в имени документа суть процесса, который отражается в системе этим документом. При этом само имя должно быть максимально лаконичным, рекомендуется избегать слов «Накладная…», «Акт…» и т.п.

Например, в системе автоматизирован процесс «Сверка взаиморасчетов», который завершается подписанием сторонами, участвующими в сверке, печатного документа «Акт сверки  товаров».  Поскольку в данном случае в системе документом фиксируется именно процесс, то документ называется СверкаВзаиморасчетов.

2. Если документ не отражает какой-либо процесс в системе, а предназначен только для получения соответствующей печатной формы, то допустимо образовывать имя документа от имени печатной формы. В этом случае допустимо использовать слова «Накладная», «Акт» и т.п. в имени документа. Как правило, у такого документа нет статусов, по нему не вводятся на основании другие документы, а сам процесс получения печатной формы может быть автоматизирован другими документами.

Например, для получения печатной формы «Товарно транспортная накладная» (ТТН) в системе имеется документ, который содержит реквизиты, специфичные для данного печатного документа. При этом поскольку весь процесс формирования ТТН связан с другими документами («Реализация  товаров и  услуг», «Перемещение товаров»), то документ целесообразно назвать от имени печатной формы: ТоварноТранспортнаяНакладная.
</details>

2. **Синоним**. Синоним объекта должен быть определен так, чтобы осмысленно, лаконично описывать объект. Заполняется обязательно

<details>
<summary>Подробнее в стандарте Имя, синоним, комментарий</summary>

Ссылка на стандарт - [Имя, синоним, комментарий](https://its.1c.ru/db/v8std/content/474/hdoc)

1.1. Синоним объекта должен быть определен так, чтобы осмысленно, лаконично описывать объект. Заполняется обязательно.

Данное требование продиктовано тем, что синонимы непосредственно участвуют в формировании пользовательского интерфейса (отображаются в формах, отчетах, командном интерфейсе и т.д.) и поэтому должны корректно и одинаково во всех местах пользовательского интерфейса идентифицировать ту сущность, к которой они относятся. Помимо объектов метаданных, требование распостраняется также и на реквизиты объектов метаданных, табличные части, реквизиты табличных частей, измерения регистров, ресурсы и другие объекты конфигурации, у которых имеется синоним.

1.2. Не рекомендуется в синонимах объектов использовать сокращения. Исключением являются только общеупотребительные и соответствующие целевой аудитории сокращения (например, Сумма (регл.) ) и аббревиатуры (например, НДС или МСФО).
</details>

3. **Комментарий**. Не заполняется

4. **Представление объекта**. Заполняется в единственном числе, например, Заказ покупателя или Реализация услуг. Представления объекта не задается, если совпадает с синонимом. Слова типа «Поступление», «Реализация», «Инвентаризация» используются без изменения и для объекта, и для списка

5. **Представление списка**. Заполняется во множественном числе, например, Заказы покупателя. Представления списка не задается, если совпадает с синонимом. Слова типа «Поступление», «Реализация», «Инвентаризация» используются без изменения и для объекта, и для списка

Длина свойства, которое отображается в командном интерфейсе (Представление списка или синоним) должна быть не более 38 символов. Идеально, если они уместятся в 30 символов

## Нумерация

1. Для установки нумерации необходимо установить свойства документа:
**Тип номера** - Строка
**Длина номера** - 11
**Допустимая длина номера** - Переменная
**Периодичность** - В пределах года
**Контроль уникальности** - Да
**Автонумерация** - Да

2. Для установки номера документ нужно включить в один из наборов подписок, например для Бухгалтерии предприятия:

- Если у документа есть реквизиты **Организация** и **ПодразделениеОрганизация**, то включить в подписки:
**ПередЗаписьюДокументаПроверкаНомераПоДатеОрганизацииПодразделению**
**УстановитьПрефиксИнформационнойБазыОрганизацииПодразделенияНомеруДокумента**

- Если у документа есть реквизит **Организация**, но нет реквизита **ПодразделениеОрганизации**, то включить в подписки:
**ПередЗаписьюДокументаПроверкаНомераПоДатеИОрганизации**
**УстановитьПрефиксИнформационнойБазыИОрганизацииНомеруДокумента**

- Если у документа нет реквизита **Организация**, то включить в подписки:
**ПередЗаписьюДокументаПроверкаНомераПоДате**
**УстановитьПрефиксИнформационнойБазыНомеруДокумента**

![NewDocument](img/NewDocument.png)

## Реквизиты документа

1. **Значение заполнения**. Заполняется значением по умолчанию, например, Курс = 1 или ВидОперации = Основной вид операции
2. **Заполнять из данных заполнения**. **Да**, если требуется заполнить реквизит при создании нового документа из формы списка с установленными отборами
3. **Проверка заполнения**. **Выдавать ошибку**, если хотя бы в одном сценарии требуется обязательное заполнение реквизита.

<details>
<summary>Подробнее в стандарте Подсказка и проверка заполнения</summary>

Ссылка на стандарт - [Подсказка и проверка заполнения](https://its.1c.ru/db/v8std/content/478/hdoc)
2.1. Свойство «Проверка заполнения». Для всех типизированных объектов метаданных, а также для стандартных реквизитов и табличных частей, которые в соответствии с логикой объекта являются обязательными к заполнению, свойство "Проверка заполнения" должно быть установлено в "Выдавать ошибку".

В ряде случаев проведение документа с незаполненными реквизитами и табличными частями не имеет смысла с точки зрения отражения документа в учете. Например, документ Заказ клиента является запросом клиента на поставку определенного количества товара. Из определения понятно, что методически заказ с незаполненным клиентом и незаполненной табличной частью Товары не имеет смысла, поэтому у реквизита Клиент и табличной части Товары свойство "Проверка заполнения" должно быть установлено в "Выдавать ошибку".

2.2. При установке свойства «Проверка заполнения» следует исходить из того, что все ограничения и проверки должны быть (насколько это возможно полно) описаны в метаданных конфигурации. Поэтому если хотя бы один из сценариев работы с объектом требует обязательного заполнения реквизита, то свойство «Проверка заполнения» устанавливается в «Выдавать ошибку». Если в других сценариях работы заполнять реквизит не обязательно, то такие случаи должны быть предусмотрены в [обработчике события модуля объекта ОбработкаПроверкиЗаполнения](https://its.1c.ru/db/v8std#content:463:hdoc).

При этом не следует придерживаться обратной схемы, когда свойство «Проверка заполнения» установлено в «Не проверять», а в обработчике ОбработкаПроверкиЗаполнения дописаны какие-либо проверки заполнения. Такая схема затрудняет анализ логики работы конфигурации.

2.3. Если проверка заполнения реквизита зависит от тех или иных условий, рекомендуется управлять автопометкой незаполненного значения с помощью условного оформления форм объектов. Убирать ее в случае, если при данном состоянии объекта заполнение реквизита проверять не требуется.

</details>

4. **Связи параметров выбора**. Заполняется, если значение реквизита зависит от значений других реквизитов документа, например: для ДоговорКонтрагента задаются связи: Отбор.Владелец(Контрагент), Отбор.Организация(Организация)

5. **Параметры выбора**. Заполняется, если значение ограничено заранее известными условиями отбора, например, если ДоговорКонтрагента можно выбрать только вида СПоставщиком – вид договора задается в параметрах выбора.
Для счетов учета устанавливается Отбор.ЗапретитьИспользоватьВПроводках(Ложь)


# Справочники

# Регистры сведений

# Регистры накопления

# Отчеты

# Журналы документов
