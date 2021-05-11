# Лабораторная работа 6. Внедрение маршрутизации между виртуальными локальными сетями.
## Задачи:
### Часть 1. Создание сети и настройка основных параметров устройства.
- #### Шаг 1. Создайте сеть согласно топологии.
- #### Шаг 2. Настройте базовые параметры для маршрутизатора.
- #### Шаг 3. Настройте базовые параметры каждого коммутатора.
- #### Шаг 4. Настройте узлы ПК.
### Часть 2. Создание сетей VLAN и назначение портов коммутатора.
- #### Шаг 1. Создайте сети VLAN на коммутаторах.
- #### Шаг 2. Назначьте сети VLAN соответствующим интерфейсам коммутатора.
### Часть 3. Конфигурация магистрального канала стандарта 802.1Q между коммутаторами.
- #### Шаг 1. Вручную настройте магистральный интерфейс F0/1 на коммутаторах S1 и S2.
- #### Шаг 2. Вручную настройте магистральный интерфейс F0/5 на коммутаторе S1.
### Часть 4. Настройка маршрутизации между сетями VLAN.
- #### Шаг 1. Настройте маршрутизатор.
### Часть 5. Проверьте, работает ли маршрутизация между VLAN.
- #### Шаг 1. Выполните следующие тесты с PC-A. Все должно быть успешно.
- #### Шаг 2. Пройдите следующий тест с PC-B.

### Топология:
![](https://github.com/OlegLarionov999/Images/blob/main/lab05/Screenshot_1.png)
### Таблица адресации:
![](https://github.com/OlegLarionov999/Images/blob/main/lab05/Screenshot_2.png)
### Таблица VLAN:
![](https://github.com/OlegLarionov999/Images/blob/main/lab05/Screenshot_3.png)
## Приступим к выполнению:
## Часть 1. Создание сети и настройка основных параметров устройства.
### Шаг 1. Создайте сеть согласно топологии.
- #### Подключите устройства, как показано в топологии, и подсоедините необходимые кабели.
![](https://github.com/OlegLarionov999/Images/blob/main/lab05/Screenshot_4.png)

### Шаг 2. Настройте базовые параметры для маршрутизатора.
- #### Подключитесь к маршрутизатору с помощью консоли и активируйте привилегированный режим EXEC.

- #### Войдите в режим конфигурации.

- #### Назначьте маршрутизатору имя устройства.

- #### Назначьте маршрутизатору имя устройства.

- #### Назначьте class в качестве зашифрованного пароля привилегированного режима EXEC.

- #### Назначьте cisco в качестве пароля консоли и включите вход в систему по паролю.

- #### Установите cisco в качестве пароля виртуального терминала и активируйте вход.

- #### Зашифруйте открытые пароли.

- #### Создайте баннер с предупреждением о запрете несанкционированного доступа к устройству.

- #### Сохраните текущую конфигурацию в файл загрузочной конфигурации.

- #### Настройте на маршрутизаторе время.
![](https://github.com/OlegLarionov999/Images/blob/main/lab05/Screenshot_5.png)
![](https://github.com/OlegLarionov999/Images/blob/main/lab05/Screenshot_6.png)

### Шаг 3. Настройте базовые параметры каждого коммутатора.
- #### Присвойте коммутатору имя устройства.

- #### Отключите поиск DNS, чтобы предотвратить попытки маршрутизатора неверно преобразовывать введенные команды таким образом, как будто они являются именами узлов.

- #### Назначьте class в качестве зашифрованного пароля привилегированного режима EXEC.

- #### Назначьте cisco в качестве пароля консоли и включите вход в систему по паролю.

- #### Установите cisco в качестве пароля виртуального терминала и активируйте вход.

- #### Зашифруйте открытые пароли.

- #### Создайте баннер с предупреждением о запрете несанкционированного доступа к устройству.

- #### Настройте на коммутаторах время.

- #### Сохранение текущей конфигурации в качестве начальной.
![](https://github.com/OlegLarionov999/Images/blob/main/lab05/Screenshot_7.png)
![](https://github.com/OlegLarionov999/Images/blob/main/lab05/Screenshot_8.png)
![](https://github.com/OlegLarionov999/Images/blob/main/lab05/Screenshot_9.png)
![](https://github.com/OlegLarionov999/Images/blob/main/lab05/Screenshot_10.png)

### Шаг 4. Настройте узлы ПК.
- #### Адреса ПК можно посмотреть в таблице адресации.
![](https://github.com/OlegLarionov999/Images/blob/main/lab05/Screenshot_11.png)
![](https://github.com/OlegLarionov999/Images/blob/main/lab05/Screenshot_12.png)

## Часть 2. Создание сетей VLAN и назначение портов коммутатора.
### Шаг 1. Создайте сети VLAN на коммутаторах.
- #### Создайте и назовите необходимые VLAN на каждом коммутаторе из таблицы выше.
![](https://github.com/OlegLarionov999/Images/blob/main/lab05/Screenshot_13.png)
![](https://github.com/OlegLarionov999/Images/blob/main/lab05/Screenshot_14.png)
![](https://github.com/OlegLarionov999/Images/blob/main/lab05/Screenshot_15.png)
![](https://github.com/OlegLarionov999/Images/blob/main/lab05/Screenshot_16.png)

- #### Настройте интерфейс управления и шлюз по умолчанию на каждом коммутаторе, используя информацию об IP-адресе в таблице адресации.
![](https://github.com/OlegLarionov999/Images/blob/main/lab05/Screenshot_17.png)
![](https://github.com/OlegLarionov999/Images/blob/main/lab05/Screenshot_18.png)

- #### Назначьте все неиспользуемые порты коммутатора VLAN Parking_Lot, настройте их для статического режима доступа и административно деактивируйте их.
![](https://github.com/OlegLarionov999/Images/blob/main/lab05/Screenshot_19.png)
![](https://github.com/OlegLarionov999/Images/blob/main/lab05/Screenshot_20.png)
![](https://github.com/OlegLarionov999/Images/blob/main/lab05/Screenshot_21.png)
![](https://github.com/OlegLarionov999/Images/blob/main/lab05/Screenshot_22.png)
![](https://github.com/OlegLarionov999/Images/blob/main/lab05/Screenshot_23.png)
![](https://github.com/OlegLarionov999/Images/blob/main/lab05/Screenshot_24.png)
![](https://github.com/OlegLarionov999/Images/blob/main/lab05/Screenshot_25.png)
![](https://github.com/OlegLarionov999/Images/blob/main/lab05/Screenshot_26.png)

### Шаг 2. Назначьте сети VLAN соответствующим интерфейсам коммутатора.
- #### Назначьте используемые порты соответствующей VLAN (указанной в таблице VLAN выше) и настройте их для режима статического доступа.
![](https://github.com/OlegLarionov999/Images/blob/main/lab05/Screenshot_27.png)
![](https://github.com/OlegLarionov999/Images/blob/main/lab05/Screenshot_28.png)

- #### Убедитесь, что VLAN назначены на правильные интерфейсы.
![](https://github.com/OlegLarionov999/Images/blob/main/lab05/Screenshot_29.png)
![](https://github.com/OlegLarionov999/Images/blob/main/lab05/Screenshot_30.png)

## Часть 3. Конфигурация магистрального канала стандарта 802.1Q между коммутаторам.
### Шаг 1. Вручную настройте магистральный интерфейс F0/1 на коммутаторах S1 и S2.
- #### Настройка статического транкинга на интерфейсе F0/1 для обоих коммутаторов.

- #### Установите native VLAN 1000 на обоих коммутаторах.

- #### Укажите, что VLAN 10, 20, 30 и 1000 могут проходить по транку.
 ![](https://github.com/OlegLarionov999/Images/blob/main/lab05/Screenshot_31.png)
 ![](https://github.com/OlegLarionov999/Images/blob/main/lab05/Screenshot_32.png)
 ![](https://github.com/OlegLarionov999/Images/blob/main/lab05/Screenshot_33.png)
 ![](https://github.com/OlegLarionov999/Images/blob/main/lab05/Screenshot_34.png)
 
- #### Проверьте транки, native VLAN и разрешенные VLAN через транк.
![](https://github.com/OlegLarionov999/Images/blob/main/lab05/Screenshot_35.png)
![](https://github.com/OlegLarionov999/Images/blob/main/lab05/Screenshot_36.png)

#### Шаг 2. Вручную настройте магистральный интерфейс F0/5 на коммутаторе S1.
- #### Настройте интерфейс S1 F0/5 с теми же параметрами транка, что и F0/1. Это транк до маршрутизатора.
![](https://github.com/OlegLarionov999/Images/blob/main/lab05/Screenshot_37.png)

- #### Сохраните текущую конфигурацию в файл загрузочной конфигурации.

- #### Проверка транкинга. Что произойдет, если G0/0/1 на R1 будет отключен? - В таком случае не удастся установить соедиенение между f0/5 и g0/0/1. Поэтому поднимаем интерфейс g0/0/1 маршрутизатора. 
![](https://github.com/OlegLarionov999/Images/blob/main/lab05/Screenshot_40.png)
![](https://github.com/OlegLarionov999/Images/blob/main/lab05/Screenshot_41.png)
![](https://github.com/OlegLarionov999/Images/blob/main/lab05/Screenshot_38.png)
![](https://github.com/OlegLarionov999/Images/blob/main/lab05/Screenshot_39.png)
![](https://github.com/OlegLarionov999/Images/blob/main/lab05/Screenshot_42.png)
![](https://github.com/OlegLarionov999/Images/blob/main/lab05/Screenshot_43.png)
![](https://github.com/OlegLarionov999/Images/blob/main/lab05/Screenshot_44.png)

## Часть 4. Настройка маршрутизации между сетями VLAN.
### Шаг 1. Настройте маршрутизатор.
- #### При необходимости активируйте интерфейс G0/0/1 на маршрутизаторе.

- #### Настройте подинтерфейсы для каждой VLAN, как указано в таблице IP-адресации. Все подинтерфейсы используют инкапсуляцию 802.1Q. Убедитесь, что подинтерфейсу для native VLAN не назначен IP-адрес. Включите описание для каждого подинтерфейса.
![](https://github.com/OlegLarionov999/Images/blob/main/lab05/Screenshot_45.png)
![](https://github.com/OlegLarionov999/Images/blob/main/lab05/Screenshot_46.png)

- #### Убедитесь, что вспомогательные интерфейсы работают.
![](https://github.com/OlegLarionov999/Images/blob/main/lab05/Screenshot_47.png)
![](https://github.com/OlegLarionov999/Images/blob/main/lab05/Screenshot_48.png)
![](https://github.com/OlegLarionov999/Images/blob/main/lab05/Screenshot_49.png)

## Часть 5. Проверьте, работает ли маршрутизация между VLAN.
### Шаг 1. Выполните следующие тесты с PC-A. Все должно быть успешно.
- #### Отправьте эхо-запрос с PC-A на шлюз по умолчанию.
![](https://github.com/OlegLarionov999/Images/blob/main/lab05/Screenshot_50.png)

- #### Отправьте эхо-запрос с PC-A на PC-B.
![](https://github.com/OlegLarionov999/Images/blob/main/lab05/Screenshot_51.png)
 
- #### Отправьте команду ping с компьютера PC-A на коммутатор S2.
![](https://github.com/OlegLarionov999/Images/blob/main/lab05/Screenshot_52.png)

### Шаг 2. Пройдите следующий тест с PC-B.
- #### В окне командной строки на PC-B выполните команду tracert на адрес PC-A.
![](https://github.com/OlegLarionov999/Images/blob/main/lab05/Screenshot_53.png)

- #### Какие промежуточные IP-адреса отображаются в результатах?













