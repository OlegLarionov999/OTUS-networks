# Лабораторная работа 1. Базовая настройка коммутатора.
## Задачи:
### Часть 1. Проверка конфигурации коммутатора по умолчанию.
### Часть 2. Создание сети и настройка основных параметров устройства.
- #### Настройка базовых параметров коммутатора.
- #### Настройка IP-адреса для ПК.
### Часть 3. Проверка сетевых подключений.
- #### Отобразите конфигурацию устройства.
- #### Протестируйте сквозное соединение, отправив эхо-запрос.
- #### Протестируйте возможности удаленного управления с помощью Telnet.
### Топология:
![](https://github.com/OlegLarionov999/Images/blob/main/Screenshot_2.png)

## Приступим к выполнению:
## Часть 1. Создание сети и проверка настроек коммутатора по умолчанию.
### Шаг 1. Создание сети согласно топологии:
- #### Подключаем консольный кабель к порту "RS 232" PC-A, другой его конец подключаем к порту "console" коммутатора S1:
![](https://github.com/OlegLarionov999/Images/blob/main/Screenshot_3.png)
- #### Затем устанавливаем консольное подключение к коммутатору, запустив терминал с рабочего стола PC-A:
![](https://github.com/OlegLarionov999/Images/blob/main/Screenshot_4.png)
![](https://github.com/OlegLarionov999/Images/blob/main/Screenshot_5.png)
- #### Подключиться через Telnet или SSH не получится, пока для интерфейса VLAN коммутатора не будет назначен IP-адрес. Для первоначальной настройки всегда придется использовать порт "Console".

### Шаг 2. Проверка настроек коммутатора по умолчанию.
- #### Командой "enable" попадаем в привилегированный режим настройки коммутатора EXEC. Появившаяся "#" вместо ">" рядом с именем устройства означает, что мы перешли из пользовательского режима в привилегированный.
![](https://github.com/OlegLarionov999/Images/blob/main/Screenshot_6.png)

- #### Введя команду "show running-config" в режиме EXEC видим, что на коммутаторе находится пустой файл конфигурации по умолчанию:
![](https://github.com/OlegLarionov999/Images/blob/main/Screenshot_7.png)
![](https://github.com/OlegLarionov999/Images/blob/main/Screenshot_8.png)
![](https://github.com/OlegLarionov999/Images/blob/main/Screenshot_9.png)

- #### Изучив файл текущей конфигурации коммутатора "running-configuration", можно заметить, что у коммутатора cisco 2960 есть 24 интерфейса FastEthernet, 2 интерфейса GigabitEthernet, а диапазон значений, отображаемых в vty-линиях 0-15, т.е. возможно не более 16 одновременных подключений по виртуальному интерфейсу.

- #### Для того, чтобы изучить файл загрузочной конфигурации "startup-configuration" введем команду "show startup-config", находясь в пользовательском режиме EXEC:
![](https://github.com/OlegLarionov999/Images/blob/main/Screenshot_10.png)

**Сообщение startup-config is not present означает, что мы не сохранили текущую конфигурацию "running-config" в файл загрузочной конфигурации "startup-config", т.е. файл загрузочной конфигурации на коммутаторе пока отсутствует**

- #### Для того, чтобы изучить характеристики виртуального интерфейса коммутатора (SVI) введем команду "show running-config" из привилегированного режима EXEC. Спустившись до параметров конфигурации сети VLAN 1, видим, что виртуальному интерфейсу SVI не назначен IP-адрес. Судя по записи "shutdown", данный интерфейс выключен.
![](https://github.com/OlegLarionov999/Images/blob/main/Screenshot_11.png) 

**Что бы узнать, какой MAC-адрес имеет интерфейс SVI в сети VLAN 1, нужно выполнить команду "show interfaces vlan 1" в привилегированном режиме EXEC. В данном случае видим, что MAC-адрес это 000c.857b.539b т.е. 00.0c.85.7b.53.9b.**

![](https://github.com/OlegLarionov999/Images/blob/main/Screenshot_12.png)

- #### Изучить IP-свойства интерфейса SVI сети VLAN 1 можно, выполнив команду show "ip interface vlan 1". Мы видим, что виртуальный интерфейс SVI не поднят, IP-адрес не назначен, т.е. данный интерфейс административно отключен.
![](https://github.com/OlegLarionov999/Images/blob/main/Screenshot_13.png)

- #### Теперь подсоединим кабель Ethernet компьютера PC-A к порту 6 на коммутаторе. Так как PC-A и коммутатор S1 находятся на разных уровнях модели OSI, будем использовать кабель "Straight through cable". Дождавшись согласования параметров скорости и дуплекса между коммутатором и ПК, увидим, что на концах изображенного кабеля появились зеленые стрелки.
![](https://github.com/OlegLarionov999/Images/blob/main/Screenshot_14.png)

**В терминале настройки коммутатора появились данные о том, что интерфейс FastEthernet0/6 коммутатора теперь поднят, так же теперь активирован протокол удаленного подключения по данному интерфейсу**

![](https://github.com/OlegLarionov999/Images/blob/main/Screenshot_15.png)

- #### Изучив сведения о версии ОС Cisco IOS на коммутаторе, делаем вывод, что ее версия "15.0(2)SE4", а файл образа системы называется "2960-lanbasek9-mz.150-2.SE4" с расширением .bin. Для того чтобы увидеть эти сведения, выполним команду "show flash" в режиме EXEC. 
![](https://github.com/OlegLarionov999/Images/blob/main/Screenshot_17.png)

**Базовый MAC-адрес, назначенный ethernet интерфейсам это 00:17:59:A7:51:80.**

![](https://github.com/OlegLarionov999/Images/blob/main/Screenshot_16.png)

- #### Изучим свойства по умолчанию интерфейса FastEthernet 0/6, который используется компьютером PC-A. Интерфейс включен. Т.к. мы соединили кабелем данный интерфейс с интерфейсом PC-A, то в эмуляторе Cisco packet tracer он поднялся автоматически. MAC-адрес интерфейса ethernet 0/6 это 00.e0.a3.52.54.06. Так же видно, что соединение "Full duplex" со скоростью 100 Mb/sec.
![](https://github.com/OlegLarionov999/Images/blob/main/Screenshot_18.png)

**В ситуации, когда мы будем работать с реальным оборудованием, интерфейс ethernet, к которому будет подключен наш ПК, нужно будет поднять самим. Для этого следует перейти в режим конфигурирования конкретного интерфейса(enable->configure terminal->interface f0/6) и выполнить команду "no shutdown". После этого интерфейс будет включен.**

![](https://github.com/OlegLarionov999/Images/blob/main/Screenshot_19.png)

- #### Изучить параметры сети VLAN можно, выполнив команду "show vlan brief" в режиме EXEC. Имя, присвоенное сети VLAN 1 по умолчанию - "default". В сети VLAN 1 по умолчанию расположены все порты коммутатора. Сеть VLAN 1 активна. По умолчанию VLAN принадлежит типу "default VLAN" - в нем находятся все порты коммутатора перед началом конфигурирования. В данном случае все порты находятся в одной локальной сети.
![](https://github.com/OlegLarionov999/Images/blob/main/Screenshot_20.png)

-#### Изучим флеш-память, выполнив команду "show flash" или "dir flash" в режиме EXEC. Имя образа Cisco IOS - "2960-lanbasek9-mz.150-2.SE4.bin".
![](https://github.com/OlegLarionov999/Images/blob/main/Screenshot_21.png)

## Часть 2. Настройка базовых параметров сетевых устройств.
### Шаг 1. Настройка базовых параметров коммутатора.
- #### В режиме глобальной конфигурации настроим базовые параметры коммутатора. Сохраним текущую конфигурацию в память.
![](https://github.com/OlegLarionov999/Images/blob/main/Screenshot_22.png)

- #### Назначим IP-адрес и маску виртуальному интерфейсу SVI сети VLAN 1 коммутатора для возможности удаленного управления через Telnet или SSH.
![](https://github.com/OlegLarionov999/Images/blob/main/Screenshot_23.png)

- #### Так же поставим пароль на консольный порт удаленного подключения к коммутатору. Чтобы консольные сообщения не прерывали выполнение команд, используем параметр logging synchronous.
![](https://github.com/OlegLarionov999/Images/blob/main/Screenshot_24.png)

- #### То же самое сделаем и с каналами виртуального соединения vty чтобы в последствии подключаться через Telnet. Команда login нужна что бы порт выводил приглашение для аутентификации.
![](https://github.com/OlegLarionov999/Images/blob/main/Screenshot_25.png)

### Шаг 2. Настройка IP-адреса на компьютере PC-A.
- #### Назначим PC-A IP-адрес и маску:
![](https://github.com/OlegLarionov999/Images/blob/main/Screenshot_26.png)
![](https://github.com/OlegLarionov999/Images/blob/main/Screenshot_27.png)

## Часть 3. Проверка сетевых подключений.
### Шаг 1. Отобразим конфигурацию коммутатора.
- #### Выполняем команду "show running-config" в режиме EXEC. Файл конфигурации представлен [тут.](https://github.com/OlegLarionov999/OTUS-networks/blob/main/labs/lab00/show%20run)

- #### Проверим параметры VLAN. Для начала "поднимем" виртуальный интерфейс SVI сети VLAN 1.
![](https://github.com/OlegLarionov999/Images/blob/main/Screenshot_28.png)

**Теперь, выполнив команду "show interface vlan 1" в режиме EXEC, изучим параметры сети VLAN 1. Пропускная способность SVI интерфейса равна 100000 Kbit. Сам VLAN 1 и канальный протокол находятся в активном состоянии.** 

![](https://github.com/OlegLarionov999/Images/blob/main/Screenshot_29.png)

### Шаг 2. Протестируем сквозное соединение, отправив эхо-запрос из терминала PC-A с помощью утилиты ping.
- #### На IP-адрес самого PC-A (192.168.1.2):
![](https://github.com/OlegLarionov999/Images/blob/main/Screenshot_30.png)

- #### На административный адрес интерфейса SVI коммутатора S1 (192.168.1.1):
![](https://github.com/OlegLarionov999/Images/blob/main/Screenshot_31.png)

### Шаг 3. Проверка удаленного управления коммутатором с помощью Telnet.
- #### Для начала зададим, по какому транспортному протоколу будет осуществляться подключение к терминальными линиям. Для этого в настройках конфигурирования терминальных линий vty введем команду "transport input telnet":
![](https://github.com/OlegLarionov999/Images/blob/main/Screenshot_32.png)

- #### Так как IP-адрес SVI мы прописали ранее, остается только подключиться через консоль PC-A к нашему коммутатору по Telnet. Для этого в консоли PC-A прописываем "telnet 192.168.1.1". 
![](https://github.com/OlegLarionov999/Images/blob/main/Screenshot_33.png)

**Подключение прошло успешно! Теперь, введя все требуемые пароли для входа в привилегированный режим, сохраним конфигурацию и завершим сеанс Telnet командой "exit"**

![](https://github.com/OlegLarionov999/Images/blob/main/Screenshot_34.png) 
