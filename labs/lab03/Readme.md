# Лабораторная работа 4. Настройка IPv6-адресов на сетевых устройствах.
## Задачи:
### Часть 1. Настройка топологии и конфигурация основных параметров маршрутизатора и коммутатора.
- #### Настройка маршрутизатора.
- #### Настройка коммутатора.
### Часть 2. Ручная настройка IPv6-адресов.
- #### Назначение IPv6-адресов интерфейсам Ethernet на R1.
- #### Активация IPv6-маршрутизации на R1.
- #### Назначение IPv6-адреса интерфейсу управления (SVI) на S1.
- #### Назначение компьютерам статических IPv6-адресов.
### Часть 3. Проверка сквозного подключения.

### Топология:
![](https://github.com/OlegLarionov999/Images/blob/main/dtRUW_Y21ZA.jpg)

## Приступим к выполнению:
## Часть 1. Настройка топологии и конфигурация основных параметров маршрутизатора и коммутатора.
### Шаг 1. Настройка маршрутизатора.
![](https://github.com/OlegLarionov999/Images/blob/main/1.png)
![](https://github.com/OlegLarionov999/Images/blob/main/3.png)
![](https://github.com/OlegLarionov999/Images/blob/main/2.png)
![](https://github.com/OlegLarionov999/Images/blob/main/5.png)
![](https://github.com/OlegLarionov999/Images/blob/main/4.png)
![](https://github.com/OlegLarionov999/Images/blob/main/6.png)
![](https://github.com/OlegLarionov999/Images/blob/main/7.png)

### Шаг 2. Настройка коммутатора.
![](https://github.com/OlegLarionov999/Images/blob/main/8.png)

- #### Шаблон по умолчанию менеджера базы данных 2960 Switch Database Manager (SDM) не поддерживает IPv6. Включим IPv6-адресацию, выполнив команду "sdm prefer dual-ipv4-and-ipv6 default". Теперь менеджер базы данных коммутатора использует шаблон "dual-ipv4-and-ipv6". После перезагрузки коммутатора будет использоваться новый шаблон. Мы можем его изучить, выполнив команду "show sdm prefer" в режиме EXEC.
![](https://github.com/OlegLarionov999/Images/blob/main/9.png)
![](https://github.com/OlegLarionov999/Images/blob/main/10.png)

## Часть 2. Ручная настройка IPv6-адресов.
### Шаг 1. Назначение IPv6-адресов интерфейсам Ethernet на R1.
- #### Назначим глобальные индивидуальные IPv6-адреса, указанные в таблице адресации обоим интерфейсам Ethernet на R1.
![](https://github.com/OlegLarionov999/Images/blob/main/11.png)
![](https://github.com/OlegLarionov999/Images/blob/main/12.png)

- #### Выполнив команду "show ipv6 interface brief", проверим, назначен ли каждому интерфейсу корректный индивидуальный IPv6-адрес. 
![](https://github.com/OlegLarionov999/Images/blob/main/13.png)

- #### Для обеспечения соответствия локальных адресов канала индивидуальному адресу, вручную введем локальные адреса канала на каждом интерфейсе Ethernet на R1.
![](https://github.com/OlegLarionov999/Images/blob/main/14.png)

- #### Используя команду "show ipv6 interface brief", убедимся, что локальный адрес связи изменен на fe80::1. 
![](https://github.com/OlegLarionov999/Images/blob/main/15.png)

**Какие группы многоадресной рассылки назначены интерфейсу G0/0?**

![](https://github.com/OlegLarionov999/Images/blob/main/19.png)

**FF02::1 - группа многоадресной рассылки для всех узлов**
**FF02::2 - группа многоадресной рассылки для всех маршрутизаторов**
**FF02::1:FF00:1 - групповой адрес запрашиваемого узла**

### Шаг 2. Активация IPv6-маршрутизации на R1.
- #### Чтобы получить данные IPv6-адреса, назначенные интерфейсу PC-B, выполним команду "ipconfig" в командной строке PC-B.  
![](https://github.com/OlegLarionov999/Images/blob/main/17.png)

- #### Активируем IPv6-маршрутизацию на R1 с помощью команды "ipv6 unicast routing". Это позволит компьютерам получать IP-адреса и данные шлюза по умолчанию с помощью функции SLAAC (Автоконфиигурация без сохранения состояния адреса).
![](https://github.com/OlegLarionov999/Images/blob/main/18.png)

- #### Теперь, когда R1 входит в группу многоадресной рассылки всех маршрутизаторов, еще раз введем команду "ipconfig" на PC-B чтобы проверить данные IPv6-адреса. PC-B получил глобальный префикс маршрутизации и идентификатор подсети, которые мы настроили на R1 благодаря технологии SLAAC. Устройства получают необходимую информацию для настройки GUA из сообщений ICMPv6 RA(Router Advertisement) локального маршрутизатора.
![](https://github.com/OlegLarionov999/Images/blob/main/20.png)

### Шаг 3. Назначение IPv6-адреса интерфейсу управления (SVI) на S1.
- #### Назначим адрес IPv6 для S1. Также назначим интерфейсу управления (SVI) локальный адрес канала.
![](https://github.com/OlegLarionov999/Images/blob/main/21.png)

- #### Проверим правильность назначения IPv6-адресов интерфейсу управления с помощью команды "show ipv6 interface vlan 1"
![](https://github.com/OlegLarionov999/Images/blob/main/22.png)

### Шаг 4. Назначение компьютерам статических IPv6-адресов.
- #### Назначим адреса IPv6 в окне "IP Configuration" для каждого ПК.
![](https://github.com/OlegLarionov999/Images/blob/main/23.png)
![](https://github.com/OlegLarionov999/Images/blob/main/24.png)

- #### Убедимся, что каждый ПК имеет два глобальных адреса IPv6: один статический и один SLAAC.

### Часть 3. Проверка сквозного подключения. 
- #### С PC-A отправьте эхо-запрос на FE80::1. Это локальный адрес канала, назначенный G0/1 на R1.
![](https://github.com/OlegLarionov999/Images/blob/main/25.png)

- #### Отправьте эхо-запрос на интерфейс управления S1 с PC-A.
![](https://github.com/OlegLarionov999/Images/blob/main/26.png)

- #### Введите команду tracert на PC-A, чтобы проверить наличие сквозного подключения к PC-B.
![](https://github.com/OlegLarionov999/Images/blob/main/27.png)

- #### С PC-B отправьте эхо-запрос на PC-A.
![](https://github.com/OlegLarionov999/Images/blob/main/28.png)

- #### С PC-B отправьте эхо-запрос на локальный адрес канала G0/0 на R1.
![](https://github.com/OlegLarionov999/Images/blob/main/29.png)
