#####27.02.2020
###Организация инфокоммуниационных процессов и систем
####Тема лекции №2: *"???"*
***

*Как передать информацию между ПК через ip-адресацию?*

1) аналогия с фреймом, чтобы у каждого кусочка был адрес отправителя и адрес получателя;
2) контрольная сумма, проверка целостность кусочка.

**Switch смотрит на mac-адреса.** 

*Что нужно сделать чтобы связать frame и кусочек ip через switch?*

*Инкапсуляция* - одни данные(ip-пакет), вносим (оборачиваем) в другие данные(frame).

*Как отправить данные через ip-адресацию?*

######Переконвертировать IP и MAC-адрес.

AdressResolutionProtocol (ARP)

Что он делает?

Фактически он позволяет связать ip-адрес и mac-адрес.

У каждого устройства есть табличка. Она называется ARP table.

Mac Adress соответствует определённому IP адресу.

mac1 -> ip1

1) ARP Request (запрос).

    * ######Фактически спрашивает кто имеет определённый IP-адрес. И он отправляет всем на broadcast адрес запрос (frame).

    * ######Если ПК видит что в запросе его IP-ашник, то отвечает. (выдавая свой IP и MAC-адрес)
    
2) ...

###Протокол IP адресации

Что? Куда?

######Виды IP адресации

1) Ipv4;
2) Ipv6;

Разница в нумерации и количестве адресов.

#####1. Ipv4

Безклассовая адресация

Нужно понимать его начальный и конечный адрес.


IP-адрес содержит 32 бита информации.

Максимальное количество возможных значений из 32 бит = 2^32 степени.

Актет - 8 бита данных на каждое определённое значение.

Маска сети -

Минус безклассовой адресации - теряются 2 IP. (Адрес сети и конечный адрес сети (broadcast))

Чем отличается сеть и подсеть?

Это одно и тоже.

**Лайвхак**

Сделать отсечку между 1 и 0. Значение сети может принимать 

Как определить адрес сети? (первый адрес)

Заменить значение на 0. (network)

Перевод в 10 систему счисления.

Чтобы определить bc нужно последнею часть заменить на 1.

Перевести в 10 систему счисления.

Адреса зарерверизрованны.

192.168.0.1 /32

/32 - единоличый хост-адрес

***
192.168.0.1 /30

IP 11000000.10101000.00000000.00000001
mask 11111111.11111111.11111111.11111100
net 192.168.0.0
bc 192.168.0.3 //2+1 iphosts
 
iphost 192.168.0.1 //

192.168.0.2 //

***

192.168.0.4

IP 11000000.10101000.00000000.00000100
mask .11111100
net 192.168.0.4 // 4 = 000001
bc 192.168.0.7 //7 = ?

Можно создать 64 сети по 2 ПК => 128

Чтобы посчитать ПК в сети 2^(32 - CIDR)
    
Маршрутизатор - позволяет перенаправлять трафик из одной "зоны" в другую.

дефолтный роутер (дефолтный шлюз/надеждный шлюз) - ...