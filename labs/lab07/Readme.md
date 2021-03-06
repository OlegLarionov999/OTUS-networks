# Лабораторная работа 8. Реализация DHCPv4.
## Задачи:
### Часть 1. Создание сети и настройка основных параметров устройства.
- #### Шаг 1. Создание схемы адресации.
- #### Шаг 2. Создайте сеть согласно топологии.
- #### Шаг 3. Произведите базовую настройку маршрутизаторов.
- #### Шаг 4. Настройка маршрутизации между сетями VLAN на маршрутизаторе R1.
- #### Шаг 5. Настройте G0/1 на R2, затем G0/0/0 и статическую маршрутизацию для обоих маршрутизаторов.
- #### Шаг 6. Настройте базовые параметры каждого коммутатора.
- #### Шаг 7. Создайте сети VLAN на коммутаторе S1.
- #### Шаг 8. Назначьте сети VLAN соответствующим интерфейсам коммутатора.
- #### Шаг 9. Вручную настройте интерфейс S1 F0/5 в качестве транка 802.1Q.
### Часть 2. Настройка и проверка двух серверов DHCPv4 на R1.
- #### Шаг 1. Настройте R1 с пулами DHCPv4 для двух поддерживаемых подсетей. Ниже приведен только пул DHCP для подсети A
- #### Шаг 2. Сохраните конфигурацию.
- #### Шаг 3. Проверка конфигурации сервера DHCPv4.
- #### Шаг 4. Попытка получить IP-адрес от DHCP на PC-A.
### Часть 3. Настройка и проверка DHCP-ретрансляции на R2.
- #### Шаг 1. Настройка R2 в качестве агента DHCP-ретрансляции для локальной сети на G0/0/1.
- #### Шаг 2. Попытка получить IP-адрес от DHCP на PC-B.

### Топология:
![](https://github.com/OlegLarionov999/Images/blob/main/lab07/Screenshot_2.png)
### Таблица адресации:
![](https://github.com/OlegLarionov999/Images/blob/main/lab07/Screenshot_1.png)
### Таблица VLAN:
![](https://github.com/OlegLarionov999/Images/blob/main/lab07/Screenshot_3.png)
## Приступим к выполнению:
## Часть 1. Создание сети и настройка основных параметров устройства.
### Шаг 1. Создание схемы адресации (Подсети сети 192.168.1.0/24 в соответствии со следующими требованиями).
- #### Одна подсеть «Подсеть A», поддерживающая 58 хостов (клиентская VLAN на R1). Запишите первый IP-адрес в таблице адресации для R1 G0/0/1.100.

- #### Одна подсеть «Подсеть B», поддерживающая 28 хостов (управляющая VLAN на R1). Запишите первый IP-адрес в таблице адресации для R1 G0/0/1.200. Запишите второй IP-адрес в таблице адресов для S1 VLAN 200 и введите соответствующий шлюз по умолчанию.

- #### Одна подсеть «Подсеть C», поддерживающая 12 узлов (клиентская сеть на R2). Запишите первый IP-адрес в таблице адресации для R2 G0/0/1. Запишите второй IP-адрес в таблице адресов для S2 VLAN 1 и введите соответствующий шлюз по умолчанию.
![](https://github.com/OlegLarionov999/Images/blob/main/lab07/Screenshot_5.png)
![](https://github.com/OlegLarionov999/Images/blob/main/lab07/Screenshot_4.png)

### Шаг 2. Создайте сеть согласно топологии.
- #### Подключите устройства, как показано в топологии, и подсоедините необходимые кабели.
![](https://github.com/OlegLarionov999/Images/blob/main/lab07/Screenshot_6.png)

### Шаг 3. Произведите базовую настройку маршрутизаторов.
- #### Назначьте маршрутизатору имя устройства.

- #### Откройте окно конфигурации.

- #### Отключите поиск DNS, чтобы предотвратить попытки маршрутизатора неверно преобразовывать введенные команды таким образом, как будто они являются именами узлов.

- #### Назначьте class в качестве зашифрованного пароля привилегированного режима EXEC.

- #### Назначьте cisco в качестве пароля консоли и включите вход в систему по паролю.

- #### Назначьте cisco в качестве пароля VTY и включите вход в систему по паролю.

- #### Зашифруйте открытые пароли.

- #### Создайте баннер с предупреждением о запрете несанкционированного доступа к устройству.

- #### Сохраните текущую конфигурацию в файл загрузочной конфигурации.

- #### Установите часы на маршрутизаторе на сегодняшнее время и дату.
![](https://github.com/OlegLarionov999/Images/blob/main/lab07/Screenshot_7.png)
![](https://github.com/OlegLarionov999/Images/blob/main/lab07/Screenshot_8.png)
![](https://github.com/OlegLarionov999/Images/blob/main/lab07/Screenshot_9.png)
![](https://github.com/OlegLarionov999/Images/blob/main/lab07/Screenshot_10.png)

### Шаг 4. Настройка маршрутизации между сетями VLAN на маршрутизаторе R1.
- #### Активируйте интерфейс G0/0/1 на маршрутизаторе.
![](https://github.com/OlegLarionov999/Images/blob/main/lab07/Screenshot_11.png)

- #### Настройте подинтерфейсы для каждой VLAN в соответствии с требованиями таблицы IP-адресации. Все субинтерфейсы используют инкапсуляцию 802.1Q и назначаются первый полезный адрес из вычисленного пула IP-адресов. Убедитесь, что подинтерфейсу для native VLAN не назначен IP-адрес. Включите описание для каждого подинтерфейса.
![](https://github.com/OlegLarionov999/Images/blob/main/lab07/Screenshot_12.png)
![](https://github.com/OlegLarionov999/Images/blob/main/lab07/Screenshot_13.png)

- #### Убедитесь, что вспомогательные интерфейсы работают.
![](https://github.com/OlegLarionov999/Images/blob/main/lab07/Screenshot_14.png)

### Шаг 5. Настройте G0/1 на R2, затем G0/0/0 и статическую маршрутизацию для обоих маршрутизаторов.
- #### Настройте G0/0/1 на R2 с первым IP-адресом подсети C, рассчитанным ранее.

- #### Настройте интерфейс G0/0/0 для каждого маршрутизатора на основе приведенной выше таблицы IP-адресации.
![](https://github.com/OlegLarionov999/Images/blob/main/lab07/Screenshot_16.png)
![](https://github.com/OlegLarionov999/Images/blob/main/lab07/Screenshot_15.png)

- #### Настройте маршрут по умолчанию на каждом маршрутизаторе, указываемом на IP-адрес G0/0/0 на другом маршрутизаторе.
![](https://github.com/OlegLarionov999/Images/blob/main/lab07/Screenshot_17.png)
![](https://github.com/OlegLarionov999/Images/blob/main/lab07/Screenshot_18.png)
![](https://github.com/OlegLarionov999/Images/blob/main/lab07/Screenshot_19.png)
![](https://github.com/OlegLarionov999/Images/blob/main/lab07/Screenshot_20.png)

- #### Убедитесь, что статическая маршрутизация работает с помощью пинга до адреса G0/0/1 R2 от R1.
![](https://github.com/OlegLarionov999/Images/blob/main/lab07/Screenshot_21.png)

- #### Сохраните текущую конфигурацию в файл загрузочной конфигурации.
![](https://github.com/OlegLarionov999/Images/blob/main/lab07/Screenshot_22.png)
![](https://github.com/OlegLarionov999/Images/blob/main/lab07/Screenshot_23.png)

### Шаг 6. Настройте базовые параметры каждого коммутатора.
- #### Присвойте коммутатору имя устройства.

- #### Отключите поиск DNS, чтобы предотвратить попытки маршрутизатора неверно преобразовывать введенные команды таким образом, как будто они являются именами узлов.

- #### Назначьте class в качестве зашифрованного пароля привилегированного режима EXEC.

- #### Назначьте cisco в качестве пароля консоли и включите вход в систему по паролю.

- #### Назначьте cisco в качестве пароля VTY и включите вход в систему по паролю.

- #### Зашифруйте открытые пароли.

- #### Создайте баннер с предупреждением о запрете несанкционированного доступа к устройству.

- #### Сохраните текущую конфигурацию в файл загрузочной конфигурации.

- #### Установите часы на маршрутизаторе на сегодняшнее время и дату.

- #### Скопируйте текущую конфигурацию в файл загрузочной конфигурации.
![](https://github.com/OlegLarionov999/Images/blob/main/lab07/Screenshot_24.png)
![](https://github.com/OlegLarionov999/Images/blob/main/lab07/Screenshot_25.png)

### Шаг 7. Создайте сети VLAN на коммутаторе S1.
- #### Создайте необходимые VLAN на коммутаторе 1 и присвойте им имена из приведенной выше таблицы.
![](https://github.com/OlegLarionov999/Images/blob/main/lab07/Screenshot_26.png)

- #### Настройте и активируйте интерфейс управления на S1 (VLAN 200), используя второй IP-адрес из подсети, рассчитанный ранее. Кроме того установите шлюз по умолчанию на S1.
![](https://github.com/OlegLarionov999/Images/blob/main/lab07/Screenshot_27.png)

- #### Настройте и активируйте интерфейс управления на S2 (VLAN 1), используя второй IP-адрес из подсети, рассчитанный ранее. Кроме того, установите шлюз по умолчанию на S2.
![](https://github.com/OlegLarionov999/Images/blob/main/lab07/Screenshot_28.png)

- #### Назначьте все неиспользуемые порты S1 VLAN Parking_Lot, настройте их для статического режима доступа и административно деактивируйте их. На S2 административно деактивируйте все неиспользуемые порты.

**Для S1:**

![](https://github.com/OlegLarionov999/Images/blob/main/lab07/Screenshot_29.png)
![](https://github.com/OlegLarionov999/Images/blob/main/lab07/Screenshot_30.png)
![](https://github.com/OlegLarionov999/Images/blob/main/lab07/Screenshot_31.png)

**Для S2:**
![](https://github.com/OlegLarionov999/Images/blob/main/lab07/Screenshot_32.png)
![](https://github.com/OlegLarionov999/Images/blob/main/lab07/Screenshot_33.png)
![](https://github.com/OlegLarionov999/Images/blob/main/lab07/Screenshot_34.png)
![](https://github.com/OlegLarionov999/Images/blob/main/lab07/Screenshot_35.png)


### Шаг 8. Назначьте сети VLAN соответствующим интерфейсам коммутатора.
- #### Назначьте используемые порты соответствующей VLAN (указанной в таблице VLAN выше) и настройте их для режима статического доступа.
![](https://github.com/OlegLarionov999/Images/blob/main/lab07/Screenshot_36.png)

- #### Убедитесь, что VLAN назначены на правильные интерфейсы.
![](https://github.com/OlegLarionov999/Images/blob/main/lab07/Screenshot_37.png)

- #### Почему интерфейс F0/5 указан в VLAN 1?

**Интерфейс F0/5 послужит нам магистральным каналом от коммутатора S1 к роутеру R1.**

### Шаг 9. Вручную настройте интерфейс S1 F0/5 в качестве транка 802.1Q.
- #### Измените режим порта коммутатора, чтобы принудительно создать магистральный канал.
![](https://github.com/OlegLarionov999/Images/blob/main/lab07/Screenshot_38.png)

- #### В рамках конфигурации транка установите для native VLAN значение 1000.
![](https://github.com/OlegLarionov999/Images/blob/main/lab07/Screenshot_39.png)

- #### В качестве другой части конфигурации магистрали укажите, что VLAN 100, 200 и 1000 могут проходить по транку.
![](https://github.com/OlegLarionov999/Images/blob/main/lab07/Screenshot_40.png)

- #### Сохраните текущую конфигурацию в файл загрузочной конфигурации.
![](https://github.com/OlegLarionov999/Images/blob/main/lab07/Screenshot_46.png)
![](https://github.com/OlegLarionov999/Images/blob/main/lab07/Screenshot_47.png)

- #### Проверьте состояние транка.
![](https://github.com/OlegLarionov999/Images/blob/main/lab07/Screenshot_44.png)
![](https://github.com/OlegLarionov999/Images/blob/main/lab07/Screenshot_45.png)

- #### Какой IP-адрес был бы у ПК, если бы он был подключен к сети с помощью DHCP?

**Чтобы DHCP-сервер мог назначать адреса, нужно сначала выделить пулы для каждого из VLAN и исключить адреса, назначенные нами статически, прописав при этом шлюз по умолчанию при конфигурации каждого пула IP-адресов. Таким образов, при подключении PC к VLAN, для которого IP-адреса назначает DHCP, для конечного узла будет определен первый свободный IP-адрес из пула, предназначенного для VLAN, в котором находится наш PC. Исключенные из пула DHCP-сервера адреса назначаться не будут.**

## Часть 2. Настройка и проверка двух серверов DHCPv4 на R1.
### Шаг 1. Настройте R1 с пулами DHCPv4 для двух поддерживаемых подсетей. Ниже приведен только пул DHCP для подсети A.
- #### Исключите первые пять используемых адресов из каждого пула адресов.
![](https://github.com/OlegLarionov999/Images/blob/main/lab07/Screenshot_48.png)
![](https://github.com/OlegLarionov999/Images/blob/main/lab07/Screenshot_49.png)

- #### Создайте пул DHCP (используйте уникальное имя для каждого пула).
![](https://github.com/OlegLarionov999/Images/blob/main/lab07/Screenshot_50.png)

- #### Укажите сеть, поддерживающую этот DHCP-сервер.
![](https://github.com/OlegLarionov999/Images/blob/main/lab07/Screenshot_51.png)

- #### В качестве имени домена укажите CCNA-lab.com.
![](https://github.com/OlegLarionov999/Images/blob/main/lab07/Screenshot_53.png)

- #### Настройте соответствующий шлюз по умолчанию для каждого пула DHCP.
![](https://github.com/OlegLarionov999/Images/blob/main/lab07/Screenshot_52.png)

- #### Настройте время аренды на 2 дня 12 часов и 30 минут.
![](https://github.com/OlegLarionov999/Images/blob/main/lab07/Screenshot_54.png)

- #### Затем настройте второй пул DHCPv4, используя имя пула R2_Client_LAN и вычислите сеть, маршрутизатор по умолчанию, и используйте то же имя домена и время аренды, что и предыдущий пул DHCP.
![](https://github.com/OlegLarionov999/Images/blob/main/lab07/Screenshot_55.png)
![](https://github.com/OlegLarionov999/Images/blob/main/lab07/Screenshot_74.png)

### Шаг 2. Сохраните конфигурацию.
- #### Сохраните текущую конфигурацию в файл загрузочной конфигурации.
![](https://github.com/OlegLarionov999/Images/blob/main/lab07/Screenshot_56.png)

### Шаг 3. Проверка конфигурации сервера DHCPv4.
- #### Чтобы просмотреть сведения о пуле, выполните команду show ip dhcp pool.
![](https://github.com/OlegLarionov999/Images/blob/main/lab07/Screenshot_58.png)

- #### Выполните команду show ip dhcp bindings для проверки установленных назначений адресов DHCP.
![](https://github.com/OlegLarionov999/Images/blob/main/lab07/Screenshot_60.png)
![](https://github.com/OlegLarionov999/Images/blob/main/lab07/Screenshot_61.png)

- #### Выполните команду show ip dhcp server statistics для проверки сообщений DHCP.
![](https://github.com/OlegLarionov999/Images/blob/main/lab07/Screenshot_62.png)

### Шаг 4. Попытка получить IP-адрес от DHCP на PC-A.
- #### Из командной строки компьютера PC-A выполните команду ipconfig /all.
![](https://github.com/OlegLarionov999/Images/blob/main/lab07/Screenshot_63.png)

- #### После завершения процесса обновления выполните команду ipconfig для просмотра новой информации об IP-адресе.
![](https://github.com/OlegLarionov999/Images/blob/main/lab07/Screenshot_64.png)
![](https://github.com/OlegLarionov999/Images/blob/main/lab07/Screenshot_65.png)

- #### Проверьте подключение с помощью пинга IP-адреса интерфейса R0 G0/0/1.
![](https://github.com/OlegLarionov999/Images/blob/main/lab07/Screenshot_66.png)

## Часть 3. Настройка и проверка DHCP-ретрансляции на R2. В части 3 настраивается R2 для ретрансляции DHCP-запросов из локальной сети на интерфейсе G0/0/1 на DHCP-сервер (R1).
### Шаг 1. Настройка R2 в качестве агента DHCP-ретрансляции для локальной сети на G0/0/1.
- #### Настройте команду ip helper-address на G0/0/1, указав IP-адрес G0/0/0 R1.
![](https://github.com/OlegLarionov999/Images/blob/main/lab07/Screenshot_67.png)

- #### Сохраните конфигурацию.
![](https://github.com/OlegLarionov999/Images/blob/main/lab07/Screenshot_68.png)

### Шаг 2. Попытка получить IP-адрес от DHCP на PC-B.
- #### Из командной строки компьютера PC-B выполните команду ipconfig /all.
![](https://github.com/OlegLarionov999/Images/blob/main/lab07/Screenshot_69.png)

- #### После завершения процесса обновления выполните команду ipconfig для просмотра новой информации об IP-адресе.
![](https://github.com/OlegLarionov999/Images/blob/main/lab07/Screenshot_70.png)
![](https://github.com/OlegLarionov999/Images/blob/main/lab07/Screenshot_71.png)

- #### Проверьте подключение с помощью пинга IP-адреса интерфейса R1 G0/0/1.
![](https://github.com/OlegLarionov999/Images/blob/main/lab07/Screenshot_72.png)

- #### Выполните show ip dhcp binding для R1 для проверки назначений адресов в DHCP.
![](https://github.com/OlegLarionov999/Images/blob/main/lab07/Screenshot_73.png)

- #### Выполните команду show ip dhcp server statistics для проверки сообщений DHCP.

**Кажется, такой команды в Packet Tracer нет.**

![](https://github.com/OlegLarionov999/Images/blob/main/lab07/Screenshot_62.png)
