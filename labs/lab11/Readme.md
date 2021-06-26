# Лабораторная работа 12. Настройка и проверка расширенных списков контроля доступа.
## Задачи:
### Часть 1. Создание сети и настройка основных параметров устройства.
- #### Шаг 1. Создайте сеть согласно топологии.
- #### Шаг 2. Произведите базовую настройку маршрутизаторов.
- #### Шаг 3. Настройте базовые параметры каждого коммутатора.
### Часть 2. Настройка сетей VLAN на коммутаторах.
- #### Шаг 1. Создайте сети VLAN на коммутаторах.
- #### Шаг 2. Назначьте сети VLAN соответствующим интерфейсам коммутатора.
### Часть 3. Настройте транки (магистральные каналы).
- #### Шаг 1. Вручную настройте магистральный интерфейс F0/1.
- #### Шаг 2. Вручную настройте магистральный интерфейс F0/5 на коммутаторе S1.
### Часть 4. Настройте маршрутизацию.
- #### Шаг 1. Настройка маршрутизации между сетями VLAN на R1.
- #### Шаг 2. Настройка интерфейса R2 g0/0/1 с использованием адреса из таблицы и маршрута по умолчанию с адресом следующего перехода 10.20.0.1.
### Часть 5. Настройте удаленный доступ.
- #### Шаг 1. Настройте все сетевые устройства для базовой поддержки SSH.
- #### Шаг 2. Включите защищенные веб-службы с проверкой подлинности на R1.
### Часть 6. Проверка подключения.
- #### Шаг 1. Настройте узлы ПК.
- #### Шаг 2. Выполните следующие тесты. Эхозапрос должен пройти успешно.
### Часть 7. Настройка и проверка списков контроля доступа (ACL).
- #### Шаг 1. Проанализируйте требования к сети и политике безопасности для планирования реализации ACL.
- #### Шаг 2. Разработка и применение расширенных списков доступа, которые будут соответствовать требованиям политики безопасности.
- #### Шаг 3. Убедитесь, что политики безопасности применяются развернутыми списками доступа.

### Топология:
![](https://github.com/OlegLarionov999/Images/blob/main/lab11/Screenshot_1.png)
### Таблица адресации:
![](https://github.com/OlegLarionov999/Images/blob/main/lab11/Screenshot_2.png)
### Таблица VLAN:
![](https://github.com/OlegLarionov999/Images/blob/main/lab11/Screenshot_3.png)
![](https://github.com/OlegLarionov999/Images/blob/main/lab11/Screenshot_4.png)

## Приступим к выполнению:
## Часть 1. Создание сети и настройка основных параметров устройства.
### Шаг 1. Создайте сеть согласно топологии.
![](https://github.com/OlegLarionov999/Images/blob/main/lab11/Screenshot_41.png)

### Шаг 2. Произведите базовую настройку маршрутизаторов.
- #### Назначьте маршрутизатору имя устройства.

- #### Отключите поиск DNS, чтобы предотвратить попытки маршрутизатора неверно преобразовывать введенные команды таким образом, как будто они являются именами узлов.

- #### Назначьте class в качестве зашифрованного пароля привилегированного режима EXEC.

- #### Назначьте cisco в качестве пароля консоли и включите вход в систему по паролю.

- #### Назначьте cisco в качестве пароля VTY и включите вход в систему по паролю.

- #### Зашифруйте открытые пароли.

- #### Создайте баннер с предупреждением о запрете несанкционированного доступа к устройству.

- #### Сохраните текущую конфигурацию в файл загрузочной конфигурации.
![](https://github.com/OlegLarionov999/Images/blob/main/lab11/Screenshot_5.png)
![](https://github.com/OlegLarionov999/Images/blob/main/lab11/Screenshot_6.png)

### Шаг 3. Настройте базовые параметры каждого коммутатора.
- #### Присвойте коммутатору имя устройства.

- #### Отключите поиск DNS, чтобы предотвратить попытки маршрутизатора неверно преобразовывать введенные команды таким образом, как будто они являются именами узлов.

- #### Назначьте class в качестве зашифрованного пароля привилегированного режима EXEC.

- #### Назначьте cisco в качестве пароля консоли и включите вход в систему по паролю.

- #### Назначьте cisco в качестве пароля VTY и включите вход в систему по паролю.

- #### Зашифруйте открытые пароли.

- #### Создайте баннер с предупреждением о запрете несанкционированного доступа к устройству.

- #### Сохраните текущую конфигурацию в файл загрузочной конфигурации.
![](https://github.com/OlegLarionov999/Images/blob/main/lab11/Screenshot_7.png)
![](https://github.com/OlegLarionov999/Images/blob/main/lab11/Screenshot_8.png)

## Часть 2. Настройка сетей VLAN на коммутаторах.
### Шаг 1. Создайте сети VLAN на коммутаторах.
- #### Создайте необходимые VLAN и назовите их на каждом коммутаторе из приведенной выше таблицы.
![](https://github.com/OlegLarionov999/Images/blob/main/lab11/Screenshot_9.png)
![](https://github.com/OlegLarionov999/Images/blob/main/lab11/Screenshot_10.png)

- #### Настройте интерфейс управления и шлюз по умолчанию на каждом коммутаторе, используя информацию об IP-адресе в таблице адресации.
![](https://github.com/OlegLarionov999/Images/blob/main/lab11/Screenshot_11.png)
![](https://github.com/OlegLarionov999/Images/blob/main/lab11/Screenshot_12.png)

- #### Назначьте все неиспользуемые порты коммутатора VLAN Parking Lot, настройте их для статического режима доступа и административно деактивируйте их.
![](https://github.com/OlegLarionov999/Images/blob/main/lab11/Screenshot_13.png)
![](https://github.com/OlegLarionov999/Images/blob/main/lab11/Screenshot_14.png)
![](https://github.com/OlegLarionov999/Images/blob/main/lab11/Screenshot_15.png)
![](https://github.com/OlegLarionov999/Images/blob/main/lab11/Screenshot_16.png)
![](https://github.com/OlegLarionov999/Images/blob/main/lab11/Screenshot_17.png)
![](https://github.com/OlegLarionov999/Images/blob/main/lab11/Screenshot_18.png)
![](https://github.com/OlegLarionov999/Images/blob/main/lab11/Screenshot_19.png)

### Шаг 2. Назначьте сети VLAN соответствующим интерфейсам коммутатора.
- #### Назначьте используемые порты соответствующей VLAN (указанной в таблице VLAN выше) и настройте их для режима статического доступа.
![](https://github.com/OlegLarionov999/Images/blob/main/lab11/Screenshot_20.png)
![](https://github.com/OlegLarionov999/Images/blob/main/lab11/Screenshot_21.png)

- #### Выполните команду "show vlan brief", чтобы убедиться, что сети VLAN назначены правильным интерфейсам.
![](https://github.com/OlegLarionov999/Images/blob/main/lab11/Screenshot_22.png)
![](https://github.com/OlegLarionov999/Images/blob/main/lab11/Screenshot_23.png)

## Часть 3. Настройте транки (магистральные каналы).
### Шаг 1. Вручную настройте магистральный интерфейс F0/1.
- #### Измените режим порта коммутатора на интерфейсе F0/1, чтобы принудительно создать магистральную связь. Не забудьте сделать это на обоих коммутаторах.
![](https://github.com/OlegLarionov999/Images/blob/main/lab11/Screenshot_24.png)
![](https://github.com/OlegLarionov999/Images/blob/main/lab11/Screenshot_25.png)

- #### В рамках конфигурации транка установите для native vlan значение 1000 на обоих коммутаторах.

- #### При настройке двух интерфейсов для разных собственных VLAN сообщения об ошибках могут отображаться временно.

- #### В качестве другой части конфигурации транка укажите, что VLAN 10, 20, 30 и 1000 разрешены в транке.
![](https://github.com/OlegLarionov999/Images/blob/main/lab11/Screenshot_26.png)
![](https://github.com/OlegLarionov999/Images/blob/main/lab11/Screenshot_27.png)

- #### Выполните команду show interfaces trunk для проверки портов магистрали, собственной VLAN и разрешенных VLAN через магистраль.
![](https://github.com/OlegLarionov999/Images/blob/main/lab11/Screenshot_28.png)
![](https://github.com/OlegLarionov999/Images/blob/main/lab11/Screenshot_29.png)

### Шаг 2. Вручную настройте магистральный интерфейс F0/5 на коммутаторе S1.
- #### Настройте интерфейс S1 F0/5 с теми же параметрами транка, что и F0/1. Это транк до маршрутизатора.

- #### Сохраните текущую конфигурацию в файл загрузочной конфигурации.

- #### Используйте команду "show interfaces" trunk для проверки настроек транка.
![](https://github.com/OlegLarionov999/Images/blob/main/lab11/Screenshot_30.png)

## Часть 4. Настройте маршрутизацию.
### Шаг 1. Настройка маршрутизации между сетями VLAN на R1.
- #### Активируйте интерфейс G0/0/1 на маршрутизаторе.
![](https://github.com/OlegLarionov999/Images/blob/main/lab11/Screenshot_31.png)

- #### Настройте подинтерфейсы для каждой VLAN, как указано в таблице IP-адресации. Все подинтерфейсы используют инкапсуляцию 802.1Q. Убедитесь, что подинтерфейс для собственной VLAN не имеет назначенного IP-адреса. Включите описание для каждого подинтерфейса.
![](https://github.com/OlegLarionov999/Images/blob/main/lab11/Screenshot_32.png)
![](https://github.com/OlegLarionov999/Images/blob/main/lab11/Screenshot_33.png)
![](https://github.com/OlegLarionov999/Images/blob/main/lab11/Screenshot_34.png)
![](https://github.com/OlegLarionov999/Images/blob/main/lab11/Screenshot_35.png)

- #### Настройте интерфейс Loopback 1 на R1 с адресацией из приведенной выше таблицы.
![](https://github.com/OlegLarionov999/Images/blob/main/lab11/Screenshot_36.png)

- #### С помощью команды show ip interface brief проверьте конфигурацию подынтерфейса.
![](https://github.com/OlegLarionov999/Images/blob/main/lab11/Screenshot_37.png)

### Шаг 2. Настройка интерфейса R2 g0/0/1 с использованием адреса из таблицы и маршрута по умолчанию с адресом следующего перехода 10.20.0.1.
![](https://github.com/OlegLarionov999/Images/blob/main/lab11/Screenshot_38.png)

## Часть 5. Настройте удаленный доступ.
### Шаг 1. Настройте все сетевые устройства для базовой поддержки SSH.
- #### Создайте локального пользователя с именем пользователя SSHadmin и зашифрованным паролем $cisco123!

- #### Используйте ccna-lab.com в качестве доменного имени.

- #### Генерируйте криптоключи с помощью 1024 битного модуля.

- #### Настройте первые пять линий VTY на каждом устройстве, чтобы поддерживать только SSH-соединения и с локальной аутентификацией.
![](https://github.com/OlegLarionov999/Images/blob/main/lab11/Screenshot_39.png)
![](https://github.com/OlegLarionov999/Images/blob/main/lab11/Screenshot_40.png)
![](https://github.com/OlegLarionov999/Images/blob/main/lab11/Screenshot_42.png)
![](https://github.com/OlegLarionov999/Images/blob/main/lab11/Screenshot_43.png)

### Шаг 2. Включите защищенные веб-службы с проверкой подлинности на R1.
- #### Включите сервер HTTPS на R1. Данная команда недоступна в Packet Tracer.
![](https://github.com/OlegLarionov999/Images/blob/main/lab11/Screenshot_44.png)

- #### Настройте R1 для проверки подлинности пользователей, пытающихся подключиться к веб-серверу. 

## Часть 6. Проверка подключения.
### Шаг 1. Настройте узлы ПК. Адреса ПК можно посмотреть в таблице адресации.
![](https://github.com/OlegLarionov999/Images/blob/main/lab11/Screenshot_45.png)
![](https://github.com/OlegLarionov999/Images/blob/main/lab11/Screenshot_46.png)

### Шаг 2. Выполните следующие тесты. Эхозапрос должен пройти успешно.
![](https://github.com/OlegLarionov999/Images/blob/main/lab11/Screenshot_47.png)
![](https://github.com/OlegLarionov999/Images/blob/main/lab11/Screenshot_48.png)
![](https://github.com/OlegLarionov999/Images/blob/main/lab11/Screenshot_49.png)
![](https://github.com/OlegLarionov999/Images/blob/main/lab11/Screenshot_50.png)
![](https://github.com/OlegLarionov999/Images/blob/main/lab11/Screenshot_51.png)

## Часть 7. Настройка и проверка списков контроля доступа (ACL).
### Шаг 1. Проанализируйте требования к сети и политике безопасности для планирования реализации ACL.
При проверке базового подключения компания требует реализации следующих политик безопасности:

- #### Политика 1. Сеть Sales не может использовать SSH в сети Management (но в другие сети SSH разрешен).

- #### Политика 2. Сеть Sales не имеет доступа к IP-адресам в сети Management с помощью любого веб-протокола (HTTP/HTTPS). Сеть Sales также не имеет доступа к интерфейсам R1 с помощью любого веб-протокола. Разрешён весь другой веб-трафик (обратите внимание — Сеть Sales может получить доступ к интерфейсу Loopback 1 на R1).

**Так как в Cisco Packet Tracer не удалось включить сервер HTTPS на R1, то данную политику применять на R1 не стал.**

- #### Политика 3. Сеть Sales не может отправлять эхо-запросы ICMP в сети Operations или Management. Разрешены эхо-запросы ICMP к другим адресатам.

- #### Политика 4. Cеть Operations не может отправлять ICMP эхозапросы в сеть Sales. Разрешены эхо-запросы ICMP к другим адресатам.

### Шаг 2. Разработка и применение расширенных списков доступа, которые будут соответствовать требованиям политики безопасности.
![](https://github.com/OlegLarionov999/Images/blob/main/lab11/Screenshot_52.png)
![](https://github.com/OlegLarionov999/Images/blob/main/lab11/Screenshot_53.png)
![](https://github.com/OlegLarionov999/Images/blob/main/lab11/Screenshot_54.png)

### Шаг 3. Убедитесь, что политики безопасности применяются развернутыми списками доступа.
![](https://github.com/OlegLarionov999/Images/blob/main/lab11/Screenshot_55.png)
![](https://github.com/OlegLarionov999/Images/blob/main/lab11/Screenshot_56.png)
![](https://github.com/OlegLarionov999/Images/blob/main/lab11/Screenshot_57.png)






