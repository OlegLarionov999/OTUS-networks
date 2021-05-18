# Лабораторная работа 7. Развертывание коммутируемой сети с резервными каналами.
## Задачи:
### Часть 1. Создание сети и настройка основных параметров устройства.
- #### Шаг 1. Создайте сеть согласно топологии.
- #### Шаг 2. Выполните инициализацию и перезагрузку коммутаторов.
- #### Шаг 3. Настройте базовые параметры каждого коммутатора.
- #### Шаг 4. Проверьте связь.
### Часть 2. Определение корневого моста.
- #### Шаг 1. Отключите все порты на коммутаторах.
- #### Шаг 2. Настройте подключенные порты в качестве транковых.
- #### Шаг 3. Включите порты F0/2 и F0/4 на всех коммутаторах.
- #### Шаг 4. Отобразите данные протокола spanning-tree.
### Часть 3. Наблюдение за процессом выбора протоколом STP порта, исходя из стоимости портов
- #### Шаг 1. Определите коммутатор с заблокированным портом. 
- #### Шаг 2. Измените стоимость порта.
- #### Шаг 3. Просмотрите изменения протокола spanning-tree.
- #### Шаг 4. Удалите изменения стоимости порта.
### Часть 4. Наблюдение за процессом выбора протоколом STP порта, исходя из приоритета портов.

### Топология:
![](https://github.com/OlegLarionov999/Images/blob/main/lab06/Screenshot_4.png)
### Таблица адресации:
![](https://github.com/OlegLarionov999/Images/blob/main/lab06/Screenshot_1.png)
## Приступим к выполнению:
## Часть 1. Создание сети и настройка основных параметров устройства.
### Шаг 1. Создайте сеть согласно топологии.
![](https://github.com/OlegLarionov999/Images/blob/main/lab06/Screenshot_15.png)

### Шаг 2. Выполните инициализацию и перезагрузку коммутаторов.
![](https://github.com/OlegLarionov999/Images/blob/main/lab06/Screenshot_2.png)
![](https://github.com/OlegLarionov999/Images/blob/main/lab06/Screenshot_3.png)
![](https://github.com/OlegLarionov999/Images/blob/main/lab06/Screenshot_5.png)
![](https://github.com/OlegLarionov999/Images/blob/main/lab06/Screenshot_6.png)
![](https://github.com/OlegLarionov999/Images/blob/main/lab06/Screenshot_7.png)
![](https://github.com/OlegLarionov999/Images/blob/main/lab06/Screenshot_8.png)
![](https://github.com/OlegLarionov999/Images/blob/main/lab06/Screenshot_9.png)
![](https://github.com/OlegLarionov999/Images/blob/main/lab06/Screenshot_10.png)
![](https://github.com/OlegLarionov999/Images/blob/main/lab06/Screenshot_11.png)

### Шаг 3. Настройте базовые параметры каждого коммутатора.
- #### Отключите поиск DNS.

- #### Присвойте имена устройствам в соответствии с топологией.

- #### Назначьте class в качестве зашифрованного пароля доступа к привилегированному режиму.

- #### Назначьте cisco в качестве паролей консоли и VTY и активируйте вход для консоли и VTY каналов.

- #### Настройте logging synchronous для консольного канала.

- #### Настройте баннерное сообщение дня (MOTD) для предупреждения пользователей о запрете несанкционированного доступа.

- #### Задайте IP-адрес, указанный в таблице адресации для VLAN 1 на всех коммутаторах.

- #### Скопируйте текущую конфигурацию в файл загрузочной конфигурации.
![](https://github.com/OlegLarionov999/Images/blob/main/lab06/Screenshot_12.png)
![](https://github.com/OlegLarionov999/Images/blob/main/lab06/Screenshot_13.png)
![](https://github.com/OlegLarionov999/Images/blob/main/lab06/Screenshot_14.png)
![](https://github.com/OlegLarionov999/Images/blob/main/lab06/Screenshot_16.png)
![](https://github.com/OlegLarionov999/Images/blob/main/lab06/Screenshot_17.png)
![](https://github.com/OlegLarionov999/Images/blob/main/lab06/Screenshot_18.png)
![](https://github.com/OlegLarionov999/Images/blob/main/lab06/Screenshot_19.png)
![](https://github.com/OlegLarionov999/Images/blob/main/lab06/Screenshot_20.png)

### Шаг 4. Проверьте способность компьютеров обмениваться эхо-запросами.
- #### Успешно ли выполняется эхо-запрос от коммутатора S1 на коммутатор S2?
![](https://github.com/OlegLarionov999/Images/blob/main/lab06/Screenshot_21.png)

- #### Успешно ли выполняется эхо-запрос от коммутатора S1 на коммутатор S3?
![](https://github.com/OlegLarionov999/Images/blob/main/lab06/Screenshot_22.png)

- #### Успешно ли выполняется эхо-запрос от коммутатора S2 на коммутатор S3?
![](https://github.com/OlegLarionov999/Images/blob/main/lab06/Screenshot_23.png)

## Часть 2. Определение корневого моста. 

**Для каждого экземпляра протокола spanning-tree (коммутируемая сеть LAN или широковещательный домен) существует коммутатор, выделенный в качестве корневого моста. Корневой мост служит точкой привязки для всех расчётов протокола spanning-tree, позволяя определить избыточные пути, которые следует заблокировать. Процесс выбора определяет, какой из коммутаторов станет корневым мостом. Коммутатор с наименьшим значением идентификатора моста (BID) становится корневым мостом. Идентификатор BID состоит из значения приоритета моста, расширенного идентификатора системы и MAC-адреса коммутатора. Значение приоритета может находиться в диапазоне от 0 до 65535 с шагом 4096 По умолчанию используется значение 32768.**

### Шаг 1. Отключите все порты на коммутаторах.
![](https://github.com/OlegLarionov999/Images/blob/main/lab06/Screenshot_24.png)
![](https://github.com/OlegLarionov999/Images/blob/main/lab06/Screenshot_25.png)
![](https://github.com/OlegLarionov999/Images/blob/main/lab06/Screenshot_26.png)
![](https://github.com/OlegLarionov999/Images/blob/main/lab06/Screenshot_27.png)
![](https://github.com/OlegLarionov999/Images/blob/main/lab06/Screenshot_28.png)
![](https://github.com/OlegLarionov999/Images/blob/main/lab06/Screenshot_29.png)

### Шаг 2. Настройте подключенные порты в качестве транковых.
![](https://github.com/OlegLarionov999/Images/blob/main/lab06/Screenshot_30.png)
![](https://github.com/OlegLarionov999/Images/blob/main/lab06/Screenshot_31.png)
![](https://github.com/OlegLarionov999/Images/blob/main/lab06/Screenshot_32.png)

### Шаг 3. Включите порты F0/2 и F0/4 на всех коммутаторах.
![](https://github.com/OlegLarionov999/Images/blob/main/lab06/Screenshot_35.png)
![](https://github.com/OlegLarionov999/Images/blob/main/lab06/Screenshot_33.png)
![](https://github.com/OlegLarionov999/Images/blob/main/lab06/Screenshot_36.png)
![](https://github.com/OlegLarionov999/Images/blob/main/lab06/Screenshot_37.png)
![](https://github.com/OlegLarionov999/Images/blob/main/lab06/Screenshot_38.png)
![](https://github.com/OlegLarionov999/Images/blob/main/lab06/Screenshot_39.png)
![](https://github.com/OlegLarionov999/Images/blob/main/lab06/Screenshot_40.png)

### Шаг 4. Отобразите данные протокола spanning-tree.

**Введите команду show spanning-tree на всех трех коммутаторах. Приоритет идентификатора моста рассчитывается путем сложения значений приоритета и расширенного идентификатора системы. Расширенным идентификатором системы всегда является номер сети VLAN. В примере ниже все три коммутатора имеют равные значения приоритета идентификатора моста (32769 = 32768 + 1, где приоритет по умолчанию = 32768, номер сети VLAN = 1); следовательно, коммутатор с самым низким значением MAC-адреса становится корневым мостом (в примере — S2).**

![](https://github.com/OlegLarionov999/Images/blob/main/lab06/Screenshot_41.png)
![](https://github.com/OlegLarionov999/Images/blob/main/lab06/Screenshot_42.png)
![](https://github.com/OlegLarionov999/Images/blob/main/lab06/Screenshot_43.png)

**Примечание. Режим STP по умолчанию на коммутаторе 2960 — протокол STP для каждой сети VLAN(PVST).**

- #### В схему ниже запишите роль и состояние (Sts) активных портов на каждом коммутаторе в топологии.
![](https://github.com/OlegLarionov999/Images/blob/main/lab06/Screenshot_44.png)

- #### С учетом выходных данных, поступающих с коммутаторов, ответьте на следующие вопросы:
Какой коммутатор является корневым мостом?

Почему этот коммутатор был выбран протоколом spanning-tree в качестве корневого моста?

Какие порты на коммутаторе являются корневыми портами?

Какие порты на коммутаторе являются назначенными портами?

Какой порт отображается в качестве альтернативного и в настоящее время заблокирован?

Почему протокол spanning-tree выбрал этот порт в качестве невыделенного (заблокированного) порта?

## Часть 3. Наблюдение за процессом выбора протоколом STP порта, исходя из стоимости портов.
### Шаг 1. Определите коммутатор с заблокированным портом.

**При текущей конфигурации только один коммутатор может содержать заблокированный протоколом STP порт. Выполните команду show spanning-tree на обоих коммутаторах некорневого моста. В примере ниже протокол spanning-tree блокирует порт F0/4 на коммутаторе с самым высоким идентификатором BID (S1).**

![](https://github.com/OlegLarionov999/Images/blob/main/lab06/Screenshot_45.png)
![](https://github.com/OlegLarionov999/Images/blob/main/lab06/Screenshot_46.png)

### Шаг 2. Измените стоимость порта.
- #### Помимо заблокированного порта, единственным активным портом на этом коммутаторе является порт, выделенный в качестве порта корневого моста. Уменьшите стоимость этого порта корневого моста до 18, выполнив команду spanning-tree cost 18 режима конфигурации интерфейса.**
 ![](https://github.com/OlegLarionov999/Images/blob/main/lab06/Screenshot_47.png)
 
### Шаг 3. Просмотрите изменения протокола spanning-tree. 
- #### Повторно выполните команду show spanning-tree на обоих коммутаторах некорневого моста. Обратите внимание, что ранее заблокированный порт (S1 – F0/4) теперь является назначенным портом, и протокол spanning-tree теперь блокирует порт на другом коммутаторе некорневого моста (S3 – F0/4).
![](https://github.com/OlegLarionov999/Images/blob/main/lab06/Screenshot_48.png)
![](https://github.com/OlegLarionov999/Images/blob/main/lab06/Screenshot_49.png)

- #### Почему протокол spanning-tree заменяет ранее заблокированный порт на назначенный порт и блокирует порт, который был назначенным портом на другом коммутаторе?
 
### Шаг 4. Удалите изменения стоимости порта.
- #### Выполните команду no spanning-tree cost 18 режима конфигурации интерфейса, чтобы удалить запись стоимости, созданную ранее.
![](https://github.com/OlegLarionov999/Images/blob/main/lab06/Screenshot_50.png)

- #### Повторно выполните команду show spanning-tree, чтобы подтвердить, что протокол STP сбросил порт на коммутаторе некорневого моста, вернув исходные настройки порта. Протоколу STP требуется примерно 30 секунд, чтобы завершить процесс перевода порта.
![](https://github.com/OlegLarionov999/Images/blob/main/lab06/Screenshot_51.png)
![](https://github.com/OlegLarionov999/Images/blob/main/lab06/Screenshot_52.png)

## Часть 4. Наблюдение за процессом выбора протоколом STP порта, исходя из приоритета портов.

**Если стоимости портов равны, процесс сравнивает BID. Если BID равны, для определения корневого моста используются приоритеты портов. Значение приоритета по умолчанию — 128 STP объединяет приоритет порта с номером порта, чтобы разорвать связи. Наиболее низкие значения являются предпочтительными. В части 4 вам предстоит активировать избыточные пути до каждого из коммутаторов, чтобы просмотреть, каким образом протокол STP выбирает порт с учетом приоритета портов.** 
 
- #### Включите порты F0/1 и F0/3 на всех коммутаторах.  
![](https://github.com/OlegLarionov999/Images/blob/main/lab06/Screenshot_53.png)
![](https://github.com/OlegLarionov999/Images/blob/main/lab06/Screenshot_54.png)
![](https://github.com/OlegLarionov999/Images/blob/main/lab06/Screenshot_55.png)

- #### Подождите 30 секунд, чтобы протокол STP завершил процесс перевода порта, после чего выполните команду show spanning-tree на коммутаторах некорневого моста. Обратите внимание, что порт корневого моста переместился на порт с меньшим номером, связанный с коммутатором корневого моста, и заблокировал предыдущий порт корневого моста.
![](https://github.com/OlegLarionov999/Images/blob/main/lab06/Screenshot_56.png)
![](https://github.com/OlegLarionov999/Images/blob/main/lab06/Screenshot_57.png)
![](https://github.com/OlegLarionov999/Images/blob/main/lab06/Screenshot_58.png)

- #### Какой порт выбран протоколом STP в качестве порта корневого моста на каждом коммутаторе некорневого моста?
 
- #### Почему протокол STP выбрал эти порты в качестве портов корневого моста на этих коммутаторах? 
 
## Вопросы для повторения:
- #### Какое значение протокол STP использует первым после выбора корневого моста, чтобы определить выбор порта?

- #### Если первое значение на двух портах одинаково, какое следующее значение будет использовать протокол STP при выборе порта?

- #### Если оба значения на двух портах равны, каким будет следующее значение, которое использует протокол STP при выборе порта?
 
 
 
 
 
 
 
 
 
