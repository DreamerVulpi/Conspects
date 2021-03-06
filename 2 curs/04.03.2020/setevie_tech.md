#####04.03.2020

###Сетевые технологии

####Тема лекции №2: "..."
***

> Установить CISCO Packet Tracer

Физический уровень требует присутствия интерфейса - аппаратуры передачи данных.

Самая распространённая сеть - телефонные сети (1970е)

АТС - оборудования телефонных станций, которые осуществляли соединения между телефонами

Использовались линии связи. Практически были телефонными линиями с аналоговым оборудованием.

Существует 2 типа канала передачи данных:
+ Аналоговый канал
    * Понимают такой канал, у которого на входе/выходе имеется непрерывный сигнал который можно описать непрерывной функцией от времени.
    Информационной составляющей которые могут нести информацию. Мложет быть амплитуда, частота. При использовании необхродимо некоторое преобразование кодирования передаваемых данных этими сигналами. Такое преобразование называется аналоговой модуляцией или аналоговым кодированием. В его основе лежит изменение какой-либо характеристики синусоидального сигнала несущего в соответствии с последовательностью передаваемых данных.
+ Цифровой канал
    * Передаёт в цифровой/дискретной/импульсной форме а т.к любая сеть связывает цифровые компьютеры то нужно передавать цифровые данные.

Зависит от формы информации которую может передавать канал.

***Основные способы аналоговой***

* амплитудная модуляция
* частотная модуляция
* фазовые модуляция

**Почему используется синуидальный сигнал?**

Есть 3 параметра, при помощи которых можно..

При амплитудная модуляции изменяется только амплитуда синусоида. При передачи логической единицы будет сигнал синусоида, а при передачи логического нуля другой амплитуды.
Этот способ в чистом виде обладает низкой помехоустойчивостью и применяется достаточно редко.

Часто применяется при низкоскоростной передаче данных.

При фазовой модуляции сигналы передаются одинаковыми по величине, по частоте несущими но смещёнными друг относительно друга (по фазе).

Из комбинированных методов широко используется QM-квадратуры и амплитудной. Сочетающей амплитудную модуляцию и фазовую модуляцию. Итого 32 комбинации для передачи данных.
В различных модификациях используется несколько вариантов. Остальные являются запрещёнными/недопустимыми. Если информация приходит с запрещённым - ошибка.

Для того чтобы осуществить передачу данных по  телефонным линиям используется устройство с одной стороны осуществляет МОДуляцию а с другой ДЕМодуляцию. Получаем МОДЕМ.

Модем подключался к ПК через последовательный КОМ порт с разъёмом RC232. Какая бы скорость данных не была она была всегда ограниченна скоростью по последовательному КОМ порту. Т.е у ПК не было сетевых адаптеров. 

На первых модемах подключение к ПК проходило по последовательному КОМ 115.200 кбит/с.

Модемы классифицируются:
+ по области применения, 
+ функциональности 
+ типу используемого сигналу
+ поддержки протоколов эмуляции
+ по способу исправлеия ошибок
+ сжатия данных
+ конструктивному исполнению  

По области применения:
1) **Модемы для коммунитируемых линий.** Они предназначались для широкого круга пользователей в том числе для корпоративных организаций и наиболее распространены. Особенностью их было в том, что они должны были напрямую связываться с аппаратурой АТС, а она в свою очередь, работала в полосе 3.1 килогерца а значит сигналы других частот аппаратура АТС не пропустит.
    + **Модемы для выделенных каналов.** Инициировалась специалистами с телефонных станций. Создавалось постоянное соединение. Работал с тем же самым оборудованием АТС, но ему не требовалась линия АТС.
    + **Модемы для физических линий связи.** Т.к нет аппаратуры АТС. Линии связи не ограничены, но все эти линии связи должны были иметь максимальное ограничение по длине, по качеству экранирования от внешних помех и непосредственно качество изготовленных проводников.
    Узкополосные модемы для физических линий использует методы модуляции аналогично модему для коммунитируемых линий, но за счёт полосы пропускания скорости стали достигать >=128 кбит/с и модемы подключались к сетевой карте.
    + **Модемы короткого радиуса действия.** Используют цифровые сигналы используемые цифровые кодирования исключают постоянную составляющую.
    + **Модемы для цифровой передачи.** Модемы работающих на линиях Т1 и Т2 в которых могут передаваться одновременно трафик данных и голос и канал АСД1. Поддерживают функции канальных интерфейсов.
    + **Модемы для сотовой связи.** ...Позволяющие работать с достаточным уровнем качества...
    + **Модемы с пакетной передачей.** Используют одну и ту же полосу частот в которой организуется множественный доступ. С тем же контролем несущей. При этом скорость передачи оставалсь не высокой и не превосходило 64 кбит.с но расстояние между станциями могло составляет несколько километров. Всегда проходил через узел имеющий эти функции множественного доступа. Модемы для радиоканалов не могли обмениваться информацией.
    + **Модемы для локальных сетей.** Скорость 16мб/с. Расстояние составляло не более 300 метров. Используется различные методы псевдослучаная перестройка частоты или шокополостной. Каждый байт передавался в своём диапазоне частот.

***По методу передачи модемы различают:***
+ Синхронные
+ Асинхронные

Эти модемы на уровне подключаемого кабеля на нём уже работал стек протоколов IP. И этот канал эмулировался как сетевой ... и ему выдавался IP, mask, DNS и т.д.
Раньше модемы имели разные протоколы которые задавал производитель. Было стандартизовано. Все протоколы которые относятся к модемам имели литеру V.42 и имели цифровой код. Рекомендации выдавала служба ITU-T.

**Тип протоколов:**
1) Протокол, определяющий соединение модема с линией связи: V.2 и V.25.
2) Протокол, определяющие соединение модма с компьютером, необходимо было указать скорость с которой максимально возможно передавать данные, максимальня скорость модема, указать проверку чётности, разрядность.;
3) Протоколы модуляции: V.17; V.32; V.90; 
4) Протоколы коррекции ошибок.;
5) Протокол сжатия данных. (Для повышения скорость передачи данных);
6) Протокол согласования параметров связи;
7) Протоколы самодиагностики модемов. (которые проводили с сегодняшнего).

**Режимы передачи данных.**

Определяет тип режима передачи данных.
* Симплексные; -> simple 
* Полудуплексные; -> или <- **не может работать в обе сторонны одновременно.**
*  Думплексные (передача данных осуществляет по каналу передачи данных в обоих направлениях);
    + Симметричный;
    + Ассиметричный;

Могут передаваться в различных режимах. 4 режима

+ Асинхронный
+ Синхронный
+ Изозронный (изобары, процессы при определённой величине)
+ Плезеохронный ("почти" изохронный).

Бит чётности (паритета) - он показывает если количество единиц чётное - 1, иначе 0.
После бита чётности передаётся 100 бит. Старт бит кодируется логическим 0. А 100 бит логической единицей.
Между передачий 100 бита и 1 байт и старт бита другого бита может пройти любое время, и в это время всё время должны передаваться или запрещённые сигналы. Или заполняет запрещёнными символоми.

Асинхронный режим зависит от синхро-генераторов. Чем выше скорость передачи тем выше погрешность генераторов поэтому скорость ограничена 100 кБит/секунду. Если синхронизация качественная, то можно передавать поток данных без дополнительных данных, то такой уже называется синхронным.
Передача битов данных заканчивается выдачей в канал символов. При отсутствии данных для передачи передатчик должен передавать в канал символы синхрозации.

В случае изохорной передачи кадров данных проихсодит в заданные известные отправителю и получателю время. При этом данные будут передаваться с постоянно скоростью

Плезеохронная передача требует синхронизацию с источниками совпадающими частотами. Необходимо пространство передавать с запрещёнными символами или пропустить 1 такт передачи чтобы снова начать синхрозацию.

