##Клиент-серверные базы данных
###Лекция №1.
***
Postres - хорошая БД

В 1970 году кем-то было придумано правило ACID, по которому работают все современные БД.
Все операции в БД выполняются в рамках транкзации. Если вы явно не открываете.

A - **Атамарность**, если в ходе заполнения запросов один из запросов не будет выполнен, то все данные откатываются назад.
```
Пример: Перевод денег
************************************
Поиск -> Проверка -> Списание
Update...
Select...
Delete...
Commit... - конец транзакции
roll back... - Если на одно из этапов будет ошибка/пропажа электричества, то данные откатываются назад.
```
C - **Согласованность**, гарантирует нам, что те данные, которые будут записаны в БД будут соответствовать структуре БД.
В реляционной теории такого сделать нельзя.

I - **Изолированность**, момент когда данные из одной транзакции не видны другой транзакции.

D - **Сохранность**, данные которые записываются на ЖД и остаются навсегдаю

Поэтому в СУБД используется принцип двойной записи.

Все транзакции записываются в лог транзакций.

Все операции которые делает пользователь записываются в журнал транзакций: Дата, время, номер транзакции и контрольная сумма.

Как работает журнал (Алгоритм):
1) Данные попадают в КЭШ Озу, 
2) При достижении крит.отметки передаются в ЖД. 
3) Помечается контрольная точка.

Чтобы решить проблему с несколькими запросами одновременно был придумал MVCC - Multi Version Cession Control.

***Литература***
* MySql Оптимизация производительности - Шварц & Зайцев;

*Слайды презентации будут в личном кабинете mirea*

|xmin|xmam|id|t1|t2|
|------|------|------|------|------|
|100|0|1|100|5|
|101|0|2|150|10|
|102|0|3|250|20|

Внутреннее представление таблицы, поля xmin и xmax скрыты от нас. В полях xmin 

Предположим, что мы начинаем транкзакцию под идентификатором 103. На момент её начала нам видны записи под номерами 100, 101, 102.

|xmin|xmam|id|t1|t2|
|------|------|------|------|------|
|100|0|1|100|5|
|101|0|2|150|10|
|102|0|3|250|20|

```
Update test SET t1=200 Where id=2;
```
В рамках транкзакции 103 мы изменили запись, где id = 2.

|xmin|xmam|id|t1|t2|
|------|------|------|------|------|
|100|0|1|100|5|
|101|**103**|2|150|10|
|**103**|**0**|**2**|**200**|**10**|

Начинаем транкзакцию 104. Нам видны записи 100-103
Добавляем новую запись
```
Insert Into test Values(300, 30);
```
|xmin|xmam|id|t1|t2|
|------|------|------|------|------|
|100|0|1|100|5|
|101|0|2|150|10|
|102|0|3|250|20|
|103|0|2|200|10|
|**104**|**0**|**4**|**300**|**30**|

***Хорошим тоном являются короткие запросы!***

Начинаем транкзакцию 105. Нам видны записи 100-104
Удаляем запись
```
Delete from test where = 1;
```

|xmin|xmam|id|t1|t2|
|------|------|------|------|------|
|**100**|**105**|**1**|**100**|**5**|
|101|0|2|150|10|
|102|0|3|250|20|
|103|0|2|200|10|
|104|0|4|300|30|


**Проблемы MVCC**
* Что делать с реализованными кортежами?;
    * Post - инструмент vacuum;
    * MySQL & Oracle - БОЛЕЕ долгие транкзакции;
* Мы заранее не знаем номера окончания транкзакции;

**4 уровня изоляции транкзакции**

Насколько данные изолированы от запросов из вне, пока не работаете
1) Read Uncommitted;
2) Read Committed;
3) Repeatable Read;
4) Serializable; 

Чем выше уровень тем выше скорость, но данные могут быть противоречивые.

Потерянное обновление - происходит в случае перезатирания изменений другой транкзакцией до завершения транкзакции, которая не завершена.


В СУБД потерянное обновление - НЕВОЗМОЖНО.

Курсовая работа
* Выполнение задания;