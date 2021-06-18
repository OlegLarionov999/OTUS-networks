# Лабораторная работа 11. Настройка протокола OSPFv2 для одной области.
## Задачи:
### Часть 1. Создание сети и настройка основных параметров устройства.
- #### Шаг 1. Создайте сеть согласно топологии.
- #### Шаг 2. Произведите базовую настройку маршрутизаторов.
- #### Шаг 3. Настройте базовые параметры каждого коммутатора.
### Часть 2. Настройка и проверка базовой работы протокола OSPFv2 для одной области.
- #### Шаг 1. Настройте адреса интерфейса и базового OSPFv2 на каждом маршрутизаторе.
### Часть 3. Оптимизация и проверка конфигурации OSPFv2 для одной области.
- #### Шаг 1. Реализация различных оптимизаций на каждом маршрутизаторе.
- #### Шаг 2. Убедитесь, что оптимизация OSPFv2 реализовалась.

### Топология:
![](https://github.com/OlegLarionov999/Images/blob/main/lab10/Screenshot_1.png)
### Таблица адресации:
![](https://github.com/OlegLarionov999/Images/blob/main/lab10/Screenshot_2.png)
## Приступим к выполнению:
## Часть 1. Создание сети и настройка основных параметров устройства.
### Шаг 1. Создайте сеть согласно топологии.
![](https://github.com/OlegLarionov999/Images/blob/main/lab10/Screenshot_3.png)

### Шаг 2. Произведите базовую настройку маршрутизаторов.
- #### Назначьте маршрутизатору имя устройства.

- #### Отключите поиск DNS, чтобы предотвратить попытки маршрутизатора неверно преобразовывать введенные команды таким образом, как будто они являются именами узлов.

- #### Назначьте class в качестве зашифрованного пароля привилегированного режима EXEC.

- #### Назначьте cisco в качестве пароля консоли и включите вход в систему по паролю.

- #### Назначьте cisco в качестве пароля VTY и включите вход в систему по паролю.

- #### Зашифруйте открытые пароли.

- #### Создайте баннер с предупреждением о запрете несанкционированного доступа к устройству.

- #### Сохраните текущую конфигурацию в файл загрузочной конфигурации.
![](https://github.com/OlegLarionov999/Images/blob/main/lab10/Screenshot_4.png)
![](https://github.com/OlegLarionov999/Images/blob/main/lab10/Screenshot_5.png)
![](https://github.com/OlegLarionov999/Images/blob/main/lab10/Screenshot_6.png)

### Шаг 3. Настройте базовые параметры каждого коммутатора.
- #### Назначьте коммутатору имя устройства.

- #### Отключите поиск DNS, чтобы предотвратить попытки маршрутизатора неверно преобразовывать введенные команды таким образом, как будто они являются именами узлов.

- #### Назначьте class в качестве зашифрованного пароля привилегированного режима EXEC.

- #### Назначьте cisco в качестве пароля консоли и включите вход в систему по паролю.

- #### Назначьте cisco в качестве пароля VTY и включите вход в систему по паролю.

- #### Зашифруйте открытые пароли.

- #### Создайте баннер с предупреждением о запрете несанкционированного доступа к устройству.

- #### Сохраните текущую конфигурацию в файл загрузочной конфигурации.
![](https://github.com/OlegLarionov999/Images/blob/main/lab10/Screenshot_7.png)
![](https://github.com/OlegLarionov999/Images/blob/main/lab10/Screenshot_8.png)

## Часть 2. Настройка и проверка базовой работы протокола OSPFv2 для одной области.
### Шаг 1. Настройте адреса интерфейса и базового OSPFv2 на каждом маршрутизаторе.
- #### Настройте адреса интерфейсов на каждом маршрутизаторе, как показано в таблице адресации выше.
![](https://github.com/OlegLarionov999/Images/blob/main/lab10/Screenshot_9.png)
![](https://github.com/OlegLarionov999/Images/blob/main/lab10/Screenshot_10.png)
![](https://github.com/OlegLarionov999/Images/blob/main/lab10/Screenshot_11.png)
![](https://github.com/OlegLarionov999/Images/blob/main/lab10/Screenshot_12.png)

- #### Откройте окно конфигурации.

- #### Перейдите в режим конфигурации маршрутизатора OSPF, используя идентификатор процесса 56.

- #### Настройте статический идентификатор маршрутизатора для каждого маршрутизатора (1.1.1.1 для R1, 2.2.2.2 для R2).
![](https://github.com/OlegLarionov999/Images/blob/main/lab10/Screenshot_13.png)
![](https://github.com/OlegLarionov999/Images/blob/main/lab10/Screenshot_14.png)

- #### Настройте инструкцию сети для сети между R1 и R2, поместив ее в область 0.
![](https://github.com/OlegLarionov999/Images/blob/main/lab10/Screenshot_15.png)

- #### Только на R2 добавьте конфигурацию, необходимую для объявления сети Loopback 1 в область OSPF 0.
![](https://github.com/OlegLarionov999/Images/blob/main/lab10/Screenshot_16.png)

- #### Убедитесь, что OSPFv2 работает между маршрутизаторами. Выполните команду "show ip ospf neig", чтобы убедиться, что R1 и R2 сформировали смежность. 
![](https://github.com/OlegLarionov999/Images/blob/main/lab10/Screenshot_17.png)
![](https://github.com/OlegLarionov999/Images/blob/main/lab10/Screenshot_18.png)

**Вопрос: Какой маршрутизатор является DR? Какой маршрутизатор является BDR? Каковы критерии отбора? Designated Router - R2, Backup Designated Router - R1. OSPF выбрал DR и BDR автоматически так как маршрутизаторы соединены в сети Ethernet. В качестве DR был выбран роутер R2 за самый высокий идентификатор - 2.2.2.2.**

- #### На R1 выполните команду "show ip route ospf", чтобы убедиться, что сеть R2 Loopback1 присутствует в таблице маршрутизации. Обратите внимание, что поведение OSPF по умолчанию заключается в объявлении интерфейса обратной связи в качестве маршрута узла с использованием 32-битной маски.
![](https://github.com/OlegLarionov999/Images/blob/main/lab10/Screenshot_19.png)

- #### Запустите Ping до адреса интерфейса R2 Loopback 1 из R1. Выполнение команды ping должно быть успешным.
![](https://github.com/OlegLarionov999/Images/blob/main/lab10/Screenshot_20.png)

## Часть 3. Оптимизация и проверка конфигурации OSPFv2 для одной области.
### Шаг 1. Реализация различных оптимизаций на каждом маршрутизаторе.
- #### На R1 настройте приоритет OSPF интерфейса G0/0/1 на 50, чтобы убедиться, что R1 является назначенным маршрутизатором.
![](https://github.com/OlegLarionov999/Images/blob/main/lab10/Screenshot_21.png)
![](https://github.com/OlegLarionov999/Images/blob/main/lab10/Screenshot_22.png)
![](https://github.com/OlegLarionov999/Images/blob/main/lab10/Screenshot_23.png)

- #### Настройте таймеры OSPF на G0/0/1 каждого маршрутизатора для таймера приветствия, составляющего 30 секунд.
![](https://github.com/OlegLarionov999/Images/blob/main/lab10/Screenshot_24.png)
![](https://github.com/OlegLarionov999/Images/blob/main/lab10/Screenshot_25.png)

- #### На R1 настройте статический маршрут по умолчанию, который использует интерфейс Loopback 1 в качестве интерфейса выхода. Затем распространите маршрут по умолчанию в OSPF. Обратите внимание на сообщение консоли после установки маршрута по умолчанию.
![](https://github.com/OlegLarionov999/Images/blob/main/lab10/Screenshot_26.png)
![](https://github.com/OlegLarionov999/Images/blob/main/lab10/Screenshot_27.png)

- #### Добавьте конфигурацию, необходимую для OSPF для обработки R2 Loopback 1 как сети точка - точка. Это приводит к тому, что OSPF объявляет Loopback 1 использует маску подсети интерфейса.
![](https://github.com/OlegLarionov999/Images/blob/main/lab10/Screenshot_28.png)

- #### Только на R2 добавьте конфигурацию, необходимую для предотвращения отправки объявлений OSPF в сеть Loopback 1.
![](https://github.com/OlegLarionov999/Images/blob/main/lab10/Screenshot_29.png)
![](https://github.com/OlegLarionov999/Images/blob/main/lab10/Screenshot_30.png)

- #### Измените базовую пропускную способность для маршрутизаторов. После этой настройки перезапустите OSPF с помощью команды "clear ip ospf process". Обратите внимание на
сообщение консоли после установки новой опорной полосы пропускания.
![](https://github.com/OlegLarionov999/Images/blob/main/lab10/Screenshot_31.png)
![](https://github.com/OlegLarionov999/Images/blob/main/lab10/Screenshot_32.png)
![](https://github.com/OlegLarionov999/Images/blob/main/lab10/Screenshot_33.png)
![](https://github.com/OlegLarionov999/Images/blob/main/lab10/Screenshot_34.png)

### Шаг 2. Убедитесь, что оптимизация OSPFv2 реализовалась.
- #### Выполните команду "show ip ospf interface g0/0/1" на R1 и убедитесь, что приоритет интерфейса установлен равным 50, а временные интервалы — Hello 30, Dead 120, а тип сети по умолчанию — Broadcast.
![](https://github.com/OlegLarionov999/Images/blob/main/lab10/Screenshot_35.png)

- #### На R1 выполните команду "show ip route ospf", чтобы убедиться, что сеть R2 Loopback1 присутствует в таблице маршрутизации. Обратите внимание на разницу в метрике между этим выходным и предыдущим выходным. Также обратите внимание, что маска теперь составляет 24 бита, в отличие от 32 битов, ранее объявленных.
![](https://github.com/OlegLarionov999/Images/blob/main/lab10/Screenshot_36.png)
![](https://github.com/OlegLarionov999/Images/blob/main/lab10/Screenshot_38.png)

- #### Введите команду "show ip route ospf" на маршрутизаторе R2. Единственная информация о маршруте OSPF должна быть распространяемый по умолчанию маршрут R1.
![](https://github.com/OlegLarionov999/Images/blob/main/lab10/Screenshot_37.png)
![](https://github.com/OlegLarionov999/Images/blob/main/lab10/Screenshot_39.png)

- #### Запустите Ping до адреса интерфейса R1 Loopback 1 из R2. Выполнение команды ping должно быть успешным.
![](https://github.com/OlegLarionov999/Images/blob/main/lab10/Screenshot_40.png)




































