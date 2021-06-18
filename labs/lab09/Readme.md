# Лабораторная работа 10. Конфигурация безопасности коммутатора.
## Задачи:
### Часть 1. Настройка основного сетевого устройства.
- #### Шаг 1. Создайте сеть.
- #### Шаг 2. Настройте маршрутизатор R1.
- #### Шаг 3. Настройка и проверка основных параметров коммутатора.
### Часть 2. Настройка сетей VLAN на коммутаторах.
- #### Шаг 1. Сконфигруриуйте VLAN 10.
- #### Шаг 2. Сконфигруриуйте SVI для VLAN 10.
- #### Шаг 3. Настройте VLAN 333 с именем Native на S1 и S2.
- #### Шаг 4. Настройте VLAN 999 с именем ParkingLot на S1 и S2.
### Часть 3. Настройки безопасности коммутатора.
- #### Шаг 1. Релизация магистральных соединений 802.1Q.
- #### Шаг 2. Настройка портов доступа.
- #### Шаг 3. Безопасность неиспользуемых портов коммутатора.
- #### Шаг 4. Документирование и реализация функций безопасности порта.
- #### Шаг 5. Реализовать безопасность DHCP snooping.
- #### Шаг 6. Реализация PortFast и BPDU Guard.
- #### Шаг 7. Проверьте наличие сквозного подключения.

### Топология:
![](https://github.com/OlegLarionov999/Images/blob/main/lab09/Screenshot_1.png)
### Таблица адресации:
![](https://github.com/OlegLarionov999/Images/blob/main/lab09/Screenshot_2.png)
## Приступим к выполнению:
## Часть 1. Настройка основного сетевого устройства.
### Шаг 1. Создайте сеть.
- #### Создайте сеть согласно топологии.
![](https://github.com/OlegLarionov999/Images/blob/main/lab09/Screenshot_5.png)

- #### Инициализация устройств.

### Шаг 2. Настройте маршрутизатор R1.
- #### Загрузите следующий конфигурационный скрипт на R1.
![](https://github.com/OlegLarionov999/Images/blob/main/lab09/Screenshot_3.png)
![](https://github.com/OlegLarionov999/Images/blob/main/lab09/Screenshot_4.png)
![](https://github.com/OlegLarionov999/Images/blob/main/lab09/Screenshot_6.png)

- #### Проверьте текущую конфигурацию на R1, используя команду "show ip interface brief".
![](https://github.com/OlegLarionov999/Images/blob/main/lab09/Screenshot_7.png)

- #### Убедитесь, что IP-адресация и интерфейсы находятся в состоянии up / up (при необходимости устраните неполадки).

### Шаг 3. Настройка и проверка основных параметров коммутатора.
- #### Настройте имя хоста для коммутаторов S1 и S2.

- #### Откройте окно конфигурации.

- #### Запретите нежелательный поиск в DNS.

- #### Настройте описания интерфейса для портов, которые используются в S1 и S2.
![](https://github.com/OlegLarionov999/Images/blob/main/lab09/Screenshot_8.png)
![](https://github.com/OlegLarionov999/Images/blob/main/lab09/Screenshot_9.png)

- #### Установите для шлюза по умолчанию для VLAN управления значение 192.168.10.1 на обоих коммутаторах.
![](https://github.com/OlegLarionov999/Images/blob/main/lab09/Screenshot_10.png)
![](https://github.com/OlegLarionov999/Images/blob/main/lab09/Screenshot_11.png)

## Часть 2. Настройка сетей VLAN на коммутаторах.
### Шаг 1. Сконфигруриуйте VLAN 10.
- #### Добавьте VLAN 10 на S1 и S2 и назовите VLAN - Management.
![](https://github.com/OlegLarionov999/Images/blob/main/lab09/Screenshot_12.png)
![](https://github.com/OlegLarionov999/Images/blob/main/lab09/Screenshot_13.png)

### Шаг 2. Сконфигруриуйте SVI для VLAN 10.
- #### Настройте IP-адрес в соответствии с таблицей адресации для SVI для VLAN 10 на S1 и S2. 
![](https://github.com/OlegLarionov999/Images/blob/main/lab09/Screenshot_14.png)
![](https://github.com/OlegLarionov999/Images/blob/main/lab09/Screenshot_15.png)

- #### Включите интерфейсы SVI и предоставьте описание для интерфейса.

### Шаг 3. Настройте VLAN 333 с именем Native на S1 и S2.

### Шаг 4. Настройте VLAN 999 с именем ParkingLot на S1 и S2.
![](https://github.com/OlegLarionov999/Images/blob/main/lab09/Screenshot_16.png)
![](https://github.com/OlegLarionov999/Images/blob/main/lab09/Screenshot_17.png)

## Часть 3. Настройки безопасности коммутатора.
### Шаг 1. Релизация магистральных соединений 802.1Q.
- #### Настройте все магистральные порты Fa0/1 на обоих коммутаторах для использования VLAN 333 в качестве native VLAN.
![](https://github.com/OlegLarionov999/Images/blob/main/lab09/Screenshot_18.png)
![](https://github.com/OlegLarionov999/Images/blob/main/lab09/Screenshot_19.png)

- #### Убедитесь, что режим транкинга успешно настроен на всех коммутаторах.
![](https://github.com/OlegLarionov999/Images/blob/main/lab09/Screenshot_20.png)
![](https://github.com/OlegLarionov999/Images/blob/main/lab09/Screenshot_21.png)

- #### Отключить согласование DTP F0/1 на S1 и S2.
![](https://github.com/OlegLarionov999/Images/blob/main/lab09/Screenshot_22.png)
![](https://github.com/OlegLarionov999/Images/blob/main/lab09/Screenshot_23.png)

- #### Проверьте с помощью команды "show interfaces".
![](https://github.com/OlegLarionov999/Images/blob/main/lab09/Screenshot_24.png)
![](https://github.com/OlegLarionov999/Images/blob/main/lab09/Screenshot_25.png)

### Шаг 2. Настройка портов доступа.
- #### На S1 настройте F0/5 и F0/6 в качестве портов доступа и свяжите их с VLAN 10.
![](https://github.com/OlegLarionov999/Images/blob/main/lab09/Screenshot_26.png)

- #### На S2 настройте порт доступа Fa0/18 и свяжите его с VLAN 10.
![](https://github.com/OlegLarionov999/Images/blob/main/lab09/Screenshot_27.png)

### Шаг 3. Безопасность неиспользуемых портов коммутатора.
- #### На S1 и S2 переместите неиспользуемые порты из VLAN 1 в VLAN 999 и отключите неиспользуемые порты.
![](https://github.com/OlegLarionov999/Images/blob/main/lab09/Screenshot_28.png)
![](https://github.com/OlegLarionov999/Images/blob/main/lab09/Screenshot_29.png)
![](https://github.com/OlegLarionov999/Images/blob/main/lab09/Screenshot_30.png)
![](https://github.com/OlegLarionov999/Images/blob/main/lab09/Screenshot_31.png)

- #### Убедитесь, что неиспользуемые порты отключены и связаны с VLAN 999, введя команду "show int st".
![](https://github.com/OlegLarionov999/Images/blob/main/lab09/Screenshot_32.png)
![](https://github.com/OlegLarionov999/Images/blob/main/lab09/Screenshot_33.png)
![](https://github.com/OlegLarionov999/Images/blob/main/lab09/Screenshot_34.png)
![](https://github.com/OlegLarionov999/Images/blob/main/lab09/Screenshot_35.png)

### Шаг 4. Документирование и реализация функций безопасности порта.
- #### Интерфейсы F0/6 на S1 и F0/18 на S2 настроены как порты доступа. На этом шаге вы также настроите безопасность портов на этих двух портах доступа.

- #### На S1, введите команду "show port-security interface f0/6" для отображения настроек по умолчанию безопасности порта для интерфейса F0/6. Запишите свои ответы ниже.
![](https://github.com/OlegLarionov999/Images/blob/main/lab09/Screenshot_36.png)
![](https://github.com/OlegLarionov999/Images/blob/main/lab09/Screenshot_37.png)

- #### На S1 включите защиту порта на F0 / 6 со следующими настройками: Максимальное количество записей MAC-адресов: 3; Режим безопасности: restrict; Aging time: 60 мин; Aging type: неактивный.
![](https://github.com/OlegLarionov999/Images/blob/main/lab09/Screenshot_38.png)

- #### Проверьте безопасность порта на S1 F0/6.
![](https://github.com/OlegLarionov999/Images/blob/main/lab09/Screenshot_39.png)
![](https://github.com/OlegLarionov999/Images/blob/main/lab09/Screenshot_40.png)

- #### Включите безопасность порта для F0 / 18 на S2. Настройте каждый активный порт доступа таким образом, чтобы он автоматически добавлял адреса МАС, изученные на этом порту, в текущую конфигурацию.
![](https://github.com/OlegLarionov999/Images/blob/main/lab09/Screenshot_41.png)

- #### Настройте следующие параметры безопасности порта на S2 F / 18: Максимальное количество записей MAC-адресов: 2; Тип безопасности: Protect; Aging time: 60 мин.
![](https://github.com/OlegLarionov999/Images/blob/main/lab09/Screenshot_42.png)

- #### Проверка функции безопасности портов на S2 F0/18.
![](https://github.com/OlegLarionov999/Images/blob/main/lab09/Screenshot_43.png)
![](https://github.com/OlegLarionov999/Images/blob/main/lab09/Screenshot_44.png)

### Шаг 5. Реализовать безопасность DHCP snooping.
- #### На S2 включите DHCP snooping и настройте DHCP snooping во VLAN 10.
![](https://github.com/OlegLarionov999/Images/blob/main/lab09/Screenshot_45.png)

- #### Настройте магистральные порты на S2 как доверенные порты.
![](https://github.com/OlegLarionov999/Images/blob/main/lab09/Screenshot_46.png)

- #### Ограничьте ненадежный порт Fa0/18 на S2 пятью DHCP-пакетами в секунду.
![](https://github.com/OlegLarionov999/Images/blob/main/lab09/Screenshot_47.png)

- #### Проверка DHCP Snooping на S2.
![](https://github.com/OlegLarionov999/Images/blob/main/lab09/Screenshot_48.png)

- #### В командной строке на PC-B освободите, а затем обновите IP-адрес.
![](https://github.com/OlegLarionov999/Images/blob/main/lab09/Screenshot_49.png)
![](https://github.com/OlegLarionov999/Images/blob/main/lab09/Screenshot_50.png)

- #### Проверьте привязку отслеживания DHCP с помощью команды show ip dhcp snooping binding.
![](https://github.com/OlegLarionov999/Images/blob/main/lab09/Screenshot_51.png)
### Шаг 6. Реализация PortFast и BPDU Guard.
- #### Настройте PortFast на всех портах доступа, которые используются на обоих коммутаторах.
![](https://github.com/OlegLarionov999/Images/blob/main/lab09/Screenshot_52.png)
![](https://github.com/OlegLarionov999/Images/blob/main/lab09/Screenshot_53.png)

- #### Включите защиту BPDU на портах доступа VLAN 10 S1 и S2, подключенных к PC-A и PC-B.
![](https://github.com/OlegLarionov999/Images/blob/main/lab09/Screenshot_54.png)
![](https://github.com/OlegLarionov999/Images/blob/main/lab09/Screenshot_55.png)

- #### Убедитесь, что защита BPDU и PortFast включены на соответствующих портах.
![](https://github.com/OlegLarionov999/Images/blob/main/lab09/Screenshot_56.png)
![](https://github.com/OlegLarionov999/Images/blob/main/lab09/Screenshot_57.png)

### Шаг 7. Проверьте наличие сквозного подключения.
- #### Проверьте PING свзяь между всеми устройствами в таблице IP-адресации. В случае сбоя проверки связи может потребоваться отключить брандмауэр на хостах.
![](https://github.com/OlegLarionov999/Images/blob/main/lab09/Screenshot_58.png)
![](https://github.com/OlegLarionov999/Images/blob/main/lab09/Screenshot_59.png)









