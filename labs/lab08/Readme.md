# Лабораторная работа 9. Настройка DHCPv6.
## Задачи:
### Часть 1. Создание сети и настройка основных параметров устройства.
- #### Шаг 1. Создайте сеть согласно топологии.
- #### Шаг 2. Настройте базовые параметры каждого коммутатора.
- #### Шаг 3. Произведите базовую настройку маршрутизаторов.
- #### Шаг 4. Настройка интерфейсов и маршрутизации для обоих маршрутизаторов.
### Часть 2. Проверка назначения адреса SLAAC от R1.
- #### Шаг 1. В части 2 вы убедитесь, что узел PC-A получает адрес IPv6 с помощью метода SLAAC.
### Часть 3. Настройка и проверка сервера DHCPv6 на R1.
- #### Шаг 1. Более подробно изучите конфигурацию PC-A.
- #### Шаг 2. Настройте R1 для предоставления DHCPv6 без состояния для PC-A.
### Часть 4. Настройка сервера DHCPv6 с сохранением состояния на R1.
- #### Шаг 1. В части 4 настраивается R1 для ответа на запросы DHCPv6 от локальной сети на R2.
### Часть 5. Настройка и проверка ретрансляции DHCPv6 на R2.
- #### Шаг 1. Включите PC-B и проверьте адрес SLAAC, который он генерирует.
- #### Шаг 2. Настройте R2 в качестве агента DHCP-ретрансляции для локальной сети на G0/0/1.
- #### Шаг 3. Попытка получить адрес IPv6 из DHCPv6 на PC-B.

### Топология:
![](https://github.com/OlegLarionov999/Images/blob/main/lab08/Screenshot_1.png)
### Таблица адресации:
![](https://github.com/OlegLarionov999/Images/blob/main/lab08/Screenshot_2.png)
## Приступим к выполнению:
## Часть 1. Создание сети и настройка основных параметров устройства.
### Шаг 1. Создайте сеть согласно топологии.
- #### Подключите устройства, как показано в топологии, и подсоедините необходимые кабели.
![](https://github.com/OlegLarionov999/Images/blob/main/lab08/Screenshot_3.png)

### Шаг 2. Настройте базовые параметры каждого коммутатора(необязательно).
- #### Присвойте коммутатору имя устройства.

- #### Отключите поиск DNS, чтобы предотвратить попытки маршрутизатора неверно преобразовывать введенные команды таким образом, как будто они являются именами узлов.

- #### Назначьте class в качестве зашифрованного пароля привилегированного режима EXEC.

- #### Назначьте cisco в качестве пароля консоли и включите вход в систему по паролю.

- #### Назначьте cisco в качестве пароля VTY и включите вход в систему по паролю.

- #### Зашифруйте открытые пароли.

- #### Создайте баннер с предупреждением о запрете несанкционированного доступа к устройству.

- #### Отключите все неиспользуемые порты.

- #### Сохраните текущую конфигурацию в файл загрузочной конфигурации.

### Шаг 3. Произведите базовую настройку маршрутизаторов.
- #### Назначьте маршрутизатору имя устройства.

- #### Отключите поиск DNS, чтобы предотвратить попытки маршрутизатора неверно преобразовывать введенные команды таким образом, как будто они являются именами узлов.

- #### Назначьте class в качестве зашифрованного пароля привилегированного режима EXEC.

- #### Назначьте cisco в качестве пароля консоли и включите вход в систему по паролю.

- #### Назначьте cisco в качестве пароля VTY и включите вход в систему по паролю.

- #### Зашифруйте открытые пароли.

- #### Создайте баннер с предупреждением о запрете несанкционированного доступа к устройству.

- #### Активация IPv6-маршрутизации.

- #### Сохраните текущую конфигурацию в файл загрузочной конфигурации.
![](https://github.com/OlegLarionov999/Images/blob/main/lab08/Screenshot_4.png)
![](https://github.com/OlegLarionov999/Images/blob/main/lab08/Screenshot_5.png)

### Шаг 4. Настройка интерфейсов и маршрутизации для обоих маршрутизаторов.
- #### Настройте интерфейсы G0/0/0 и G0/1 на R1 и R2 с адресами IPv6, указанными в таблице выше.
![](https://github.com/OlegLarionov999/Images/blob/main/lab08/Screenshot_6.png)
![](https://github.com/OlegLarionov999/Images/blob/main/lab08/Screenshot_7.png)

- #### Настройте маршрут по умолчанию на каждом маршрутизаторе, который указывает на IP-адрес G0/0/0 на другом маршрутизаторе.
![](https://github.com/OlegLarionov999/Images/blob/main/lab08/Screenshot_8.png)
![](https://github.com/OlegLarionov999/Images/blob/main/lab08/Screenshot_9.png)
![](https://github.com/OlegLarionov999/Images/blob/main/lab08/Screenshot_10.png)
![](https://github.com/OlegLarionov999/Images/blob/main/lab08/Screenshot_11.png)

- #### Убедитесь, что маршрутизация работает с помощью пинга адреса G0/0/1 R2 из R1.
![](https://github.com/OlegLarionov999/Images/blob/main/lab08/Screenshot_12.png)

- #### Сохраните текущую конфигурацию в файл загрузочной конфигурации.
![](https://github.com/OlegLarionov999/Images/blob/main/lab08/Screenshot_13.png)

## Часть 2. Проверка назначения адреса SLAAC от R1.

**В части 2 вы убедитесь, что узел PC-A получает адрес IPv6 с помощью метода SLAAC.**

### Шаг 1. Включите PC-A и убедитесь, что сетевой адаптер настроен для автоматической настройки IPv6. Через несколько минут результаты команды ipconfig должны показать, что PC-A присвоил себе адрес из сети 2001:db8:1::/64.
![](https://github.com/OlegLarionov999/Images/blob/main/lab08/Screenshot_15.png)
![](https://github.com/OlegLarionov999/Images/blob/main/lab08/Screenshot_16.png)

- #### Откуда взялась часть адреса с идентификатором хоста?

**Индентификатор хоста в данном случае генерируется с помощью технологии EUI-64 - хост создает идентификатор интерфейса, используя свой 48-битный MAC-адрес и вставляет шестнадцатеричное значение fffe в середине адреса.**

## Часть 3. Настройка и проверка сервера DHCPv6 на R1. 

**В части 3 выполняется настройка и проверка состояния DHCP-сервера на R1. Цель состоит в том, чтобы предоставить PC-A информацию о DNS-сервере и домене.**

### Шаг 1. Более подробно изучите конфигурацию PC-A.
- #### Выполните команду ipconfig /all на PC-A и посмотрите на результат.
![](https://github.com/OlegLarionov999/Images/blob/main/lab08/Screenshot_17.png)

- #### Обратите внимание, что основной DNS-суффикс отсутствует. Также обратите внимание, что предоставленные адреса DNS-сервера являются адресами «локального сайта anycast», а не одноадресные адреса, как ожидалось.

### Шаг 2. Настройте R1 для предоставления DHCPv6 без состояния для PC-A.
- #### Создайте пул DHCP IPv6 на R1 с именем R1-STATELESS. В составе этого пула назначьте адрес DNS-сервера как 2001:db8:acad: :1, а имя домена — как stateless.com.
![](https://github.com/OlegLarionov999/Images/blob/main/lab08/Screenshot_18.png)

- #### Настройте интерфейс G0/0/1 на R1, чтобы предоставить флаг конфигурации OTHER для локальной сети R1 и укажите только что созданный пул DHCP в качестве ресурса DHCP для этого интерфейса.
![](https://github.com/OlegLarionov999/Images/blob/main/lab08/Screenshot_19.png)

- #### Сохраните текущую конфигурацию в файл загрузочной конфигурации.

- #### Перезапустите PC-A.

- #### Проверьте вывод ipconfig /all и обратите внимание на изменения.
![](https://github.com/OlegLarionov999/Images/blob/main/lab08/Screenshot_20.png)

- #### Тестирование подключения с помощью пинга IP-адреса интерфейса G0/1 R2.
![](https://github.com/OlegLarionov999/Images/blob/main/lab08/Screenshot_21.png)

## Часть 4. Настройка сервера DHCPv6 с сохранением состояния на R1.
### Шаг 1. В части 4 настраивается R1 для ответа на запросы DHCPv6 от локальной сети на R2.
- #### Создайте пул DHCPv6 на R1 для сети 2001:db8:acad:3:aaa::/80. Это предоставит адреса локальной сети, подключенной к интерфейсу G0/0/1 на R2. В составе пула задайте DNS сервер 2001:db8:acad: :254 и задайте доменное имя STATEFUL.com.
![](https://github.com/OlegLarionov999/Images/blob/main/lab08/Screenshot_22.png)

- #### Назначьте только что созданный пул DHCPv6 интерфейсу g0/0/0 на R1.
![](https://github.com/OlegLarionov999/Images/blob/main/lab08/Screenshot_23.png)

## Часть 5. Настройка и проверка ретрансляции DHCPv6 на R2.

**В части 5 необходимо настроить и проверить ретрансляцию DHCPv6 на R2, позволяя PC-B получать адрес IPv6.**

### Шаг 1. Включите PC-B и проверьте адрес SLAAC, который он генерирует. Обратите внимание на вывод, что используется префикс 2001:db8:acad:3::.
![](https://github.com/OlegLarionov999/Images/blob/main/lab08/Screenshot_24.png)

### Шаг 2. Настройте R2 в качестве агента DHCP-ретрансляции для локальной сети на G0/0/1.
- #### Настройте команду ipv6 dhcp relay на интерфейсе R2 G0/0/1, указав адрес назначения интерфейса G0/0/0 на R1. Также настройте команду managed-config-flag.

**Cisco Packet Tracer не поддерживает данную команду.**

![](https://github.com/OlegLarionov999/Images/blob/main/lab08/Screenshot_25.png)

- #### Сохраните конфигурацию.

### Шаг 3. Попытка получить адрес IPv6 из DHCPv6 на PC-B.
- #### Перезапустите PC-B.

- #### Откройте командную строку на PC-B и выполните команду ipconfig /all и проверьте выходные данные, чтобы увидеть результаты операции ретрансляции DHCPv6.

**Данный пункт не имеет смысла т.к. не выполнен Шаг 2.**

- #### Проверьте подключение с помощью пинга IP-адреса интерфейса R0 G0/0/1.
![](https://github.com/OlegLarionov999/Images/blob/main/lab08/Screenshot_26.png)
































