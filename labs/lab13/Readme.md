# Лабораторная работа 14. Настройка протоколов CDP, LLDP и NTP.
## Задачи:
### Часть 1. Создание сети и настройка основных параметров устройства.
- #### Шаг 1. Создайте сеть согласно топологии.
- #### Шаг 2. Произведите базовую настройку маршрутизаторов.
- #### Шаг 3. Настройте базовые параметры каждого коммутатора.
### Часть 2. Обнаружение сетевых ресурсов с помощью протокола CDP.
### Часть 3. Обнаружение сетевых ресурсов с помощью протокола LLDP. 
### Часть 4. Настройка NTP.
- #### Шаг 1. Выведите на экран текущее время.
- #### Шаг 2. Установите время.
- #### Шаг 3. Настройте главный сервер NTP.
- #### Шаг 4. Настройте клиент NTP.
- #### Шаг 5. Проверьте настройку NTP.

### Топология:
![](https://github.com/OlegLarionov999/Images/blob/main/lab13/Screenshot_2.png)

### Таблица адресации:
![](https://github.com/OlegLarionov999/Images/blob/main/lab13/Screenshot_1.png)

## Приступим к выполнению:
## Часть 1. Создание сети и настройка основных параметров устройства.
### Шаг 1. Создайте сеть согласно топологии.
![](https://github.com/OlegLarionov999/Images/blob/main/lab13/Screenshot_3.png)

### Шаг 2. Произведите базовую настройку маршрутизаторов.
- #### Назначьте маршрутизатору имя устройства.

- #### Отключите поиск DNS, чтобы предотвратить попытки маршрутизатора неверно преобразовывать введенные команды таким образом, как будто они являются именами узлов.

- #### Назначьте class в качестве зашифрованного пароля привилегированного режима EXEC.

- #### Назначьте cisco в качестве пароля консоли и включите вход в систему по паролю.

- #### Назначьте cisco в качестве пароля VTY и включите вход в систему по паролю.

- #### Зашифруйте открытые пароли.

- #### Создайте баннер с предупреждением о запрете несанкционированного доступа к устройству.

- #### Настройка интерфейсов, перечисленных в таблице выше

- #### Сохраните текущую конфигурацию в файл загрузочной конфигурации.
![](https://github.com/OlegLarionov999/Images/blob/main/lab13/Screenshot_4.png)

### Шаг 3. Настройте базовые параметры каждого коммутатора.
- #### Присвойте коммутатору имя устройства.

- #### Отключите поиск DNS, чтобы предотвратить попытки маршрутизатора неверно преобразовывать введенные команды таким образом, как будто они являются именами узлов.

- #### Назначьте class в качестве зашифрованного пароля привилегированного режима EXEC.

- #### Назначьте cisco в качестве пароля консоли и включите вход в систему по паролю.

- #### Назначьте cisco в качестве пароля VTY и включите вход в систему по паролю.

- #### Зашифруйте открытые пароли.

- #### Создайте баннер, который предупреждает всех, кто обращается к устройству, видит баннерное сообщение «Только авторизованные пользователи!».

- #### Отключите неиспользуемые интерфейсы

- #### Сохраните текущую конфигурацию в файл загрузочной конфигурации.

**Для S1:**

![](https://github.com/OlegLarionov999/Images/blob/main/lab13/Screenshot_5.png)
![](https://github.com/OlegLarionov999/Images/blob/main/lab13/Screenshot_6.png)
![](https://github.com/OlegLarionov999/Images/blob/main/lab13/Screenshot_7.png)
![](https://github.com/OlegLarionov999/Images/blob/main/lab13/Screenshot_8.png)
![](https://github.com/OlegLarionov999/Images/blob/main/lab13/Screenshot_9.png)

**Для S2:**

![](https://github.com/OlegLarionov999/Images/blob/main/lab13/Screenshot_10.png)
![](https://github.com/OlegLarionov999/Images/blob/main/lab13/Screenshot_11.png)
![](https://github.com/OlegLarionov999/Images/blob/main/lab13/Screenshot_12.png)
![](https://github.com/OlegLarionov999/Images/blob/main/lab13/Screenshot_13.png)

## Часть 2. Обнаружение сетевых ресурсов с помощью протокола CDP. На устройствах Cisco протокол CDP включен по умолчанию. Воспользуйтесь CDP, чтобы обнаружить порты, к которым подключены кабели.
- #### На R1 используйте соответствующую команду "show cdp", чтобы определить, сколько интерфейсов включено CDP, сколько из них включено и сколько отключено.
![](https://github.com/OlegLarionov999/Images/blob/main/lab13/Screenshot_14.png)

- #### Вопрос: Сколько интерфейсов участвует в объявлениях CDP? Какие из них активны? - Всего в объявлениях CDP участвует 4 интерфейса. Из них активен только g0/0/1.

- #### На R1 используйте соответствующую команду show cdp, чтобы определить версию IOS, используемую на S1. Какая версия IOS используется на S1? - Версия 15.0(2)SE4.
![](https://github.com/OlegLarionov999/Images/blob/main/lab13/Screenshot_15.png)

- #### На S1 используйте соответствующую команду show cdp, чтобы определить, сколько пакетов CDP было выданных. Сколько пакетов имеет выход CDP с момента последнего сброса счетчика?
![](https://github.com/OlegLarionov999/Images/blob/main/lab13/Screenshot_16.png)

- #### Настройте SVI для VLAN 1 на S1 и S2, используя IP-адреса, указанные в таблице адресации выше. Настройте шлюз по умолчанию для каждого коммутатора на основе таблицы адресов. - Данные параметры настроил с самого начала, поэтому параметр "Entry address(es) сразу имеет значение 10.22.0.2 - это адрес S1. В противном случае он не был бы задан при выводе команды "show cdp entry S1" на R1.

- #### На R1 выполните команду show cdp entry S1 .
![](https://github.com/OlegLarionov999/Images/blob/main/lab13/Screenshot_15.png)

- #### Вопрос: Какие дополнительные сведения доступны теперь?

- #### Отключить CDP глобально на всех устройствах.
![](https://github.com/OlegLarionov999/Images/blob/main/lab13/Screenshot_17.png)
![](https://github.com/OlegLarionov999/Images/blob/main/lab13/Screenshot_18.png)
![](https://github.com/OlegLarionov999/Images/blob/main/lab13/Screenshot_19.png)

## Часть 3. Обнаружение сетевых ресурсов с помощью протокола LLDP. На устройствах Cisco протокол LLDP может быть включен по умолчанию. Воспользуйтесь LLDP, чтобы обнаружить порты, к которым подключены кабели.
- #### Введите соответствующую команду lldp, чтобы включить LLDP на всех устройствах в топологии.
![](https://github.com/OlegLarionov999/Images/blob/main/lab13/Screenshot_20.png)
![](https://github.com/OlegLarionov999/Images/blob/main/lab13/Screenshot_21.png)
![](https://github.com/OlegLarionov999/Images/blob/main/lab13/Screenshot_22.png)

- #### На S1 выполните соответствующую команду lldp, чтобы предоставить подробную информацию о S2. Команды "show lldp entry S2" Cisco Packet Tracer не видит, поэтому воспользуемся командой "show lldp neighbors detail" и найдем в выводе информацию о S2.
![](https://github.com/OlegLarionov999/Images/blob/main/lab13/Screenshot_23.png)
![](https://github.com/OlegLarionov999/Images/blob/main/lab13/Screenshot_24.png)

- #### Что такое chassis ID для коммутатора S2? - MAC-адрес интерфейса f0/1 на S2.

- #### Соединитесь через консоль на всех устройствах и используйте команды LLDP, необходимые для отображения топологии физической сети только из выходных данных команды show.
![](https://github.com/OlegLarionov999/Images/blob/main/lab13/Screenshot_25.png)
![](https://github.com/OlegLarionov999/Images/blob/main/lab13/Screenshot_26.png)
![](https://github.com/OlegLarionov999/Images/blob/main/lab13/Screenshot_27.png)

## Часть 4. Настройка NTP.

**В части 4 необходимо настроить маршрутизатор R1 в качестве сервера NTP, а маршрутизатор R2 в качестве клиента NTP маршрутизатора R1. Необходимо выполнить синхронизацию времени для Syslog и отладочных функций. Если время не синхронизировано, сложно определить, какое сетевое событие стало причиной данного сообщения.**

### Шаг 1. Выведите на экран текущее время. Введите команду show clock для отображения текущего времени на R1. Запишите отображаемые сведения о текущем времени в следующей таблице.
![](https://github.com/OlegLarionov999/Images/blob/main/lab13/Screenshot_28.png)
![](https://github.com/OlegLarionov999/Images/blob/main/lab13/Screenshot_29.png)

### Шаг 2. Установите время. С помощью команды clock set установите время на маршрутизаторе R1. Введенное время должно быть в формате UTC.
![](https://github.com/OlegLarionov999/Images/blob/main/lab13/Screenshot_30.png)

### Шаг 3. Настройте главный сервер NTP. Настройте R1 в качестве хозяина NTP с уровнем слоя 4.
![](https://github.com/OlegLarionov999/Images/blob/main/lab13/Screenshot_31.png)

### Шаг 4. Настройте клиент NTP.
- #### Выполните соответствующую команду на S1 и S2, чтобы просмотреть настроенное время. Запишите текущее время, в следующей таблице.
![](https://github.com/OlegLarionov999/Images/blob/main/lab13/Screenshot_32.png)
![](https://github.com/OlegLarionov999/Images/blob/main/lab13/Screenshot_33.png)
![](https://github.com/OlegLarionov999/Images/blob/main/lab13/Screenshot_34.png)

- #### Настройте S1 и S2 в качестве клиентов NTP. Используйте соответствующие команды NTP для получения времени от интерфейса G0/0/1 R1, а также для периодического обновления календаря или аппаратных часов коммутатора.
![](https://github.com/OlegLarionov999/Images/blob/main/lab13/Screenshot_35.png)
![](https://github.com/OlegLarionov999/Images/blob/main/lab13/Screenshot_36.png)

### Шаг 5. Проверьте настройку NTP.
- #### Используйте соответствующую команду show , чтобы убедиться, что S1 и S2 синхронизированы с R1. Примечание: Синхронизация метки времени на маршрутизаторе R2 с меткой времени на маршрутизаторе R1 может занять несколько минут.
![](https://github.com/OlegLarionov999/Images/blob/main/lab13/Screenshot_37.png)
![](https://github.com/OlegLarionov999/Images/blob/main/lab13/Screenshot_38.png)

- #### Выполните соответствующую команду на S1 и S2, чтобы просмотреть настроенное время и сравнить ранее записанное время.
![](https://github.com/OlegLarionov999/Images/blob/main/lab13/Screenshot_39.png)
![](https://github.com/OlegLarionov999/Images/blob/main/lab13/Screenshot_40.png)










