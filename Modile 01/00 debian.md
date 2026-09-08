
#### Часть 3. Основные настройки системы

Следуйте инструкциям на экране. Все шаги интуитивно понятны.

1.  **Выбор языка**:
    *   Выберите язык, который будет использоваться в процессе установки и в системе. Рекомендуется выбрать `English` для избежания проблем с путями в консоли.

2.  **Выбор местоположения**:
    *   Укажите вашу страну или регион (например, `Hong Kong` или `other` -> `Asia` -> `Russia`).

3.  **Настройка клавиатуры**:
    *   Выберите раскладку клавиатуры. Для русскоязычных пользователей можно выбрать `American English` для системы, а русскую раскладку добавить позже.

4.  **Настройка сети**:
    *   Введите **Имя компьютера** (hostname), например, `debian-workstation`.
    *   Поле **Доменное имя** можно оставить пустым.

5.  **Настройка пользователей и паролей**:
    *   **Пароль суперпользователя (root)**: Установите надежный пароль для учетной записи `root`. **Запомните его!**.
    *   **Создание обычного пользователя**: Введите ваше полное имя, имя пользователя (логин) и пароль для ежедневной работы. Этот пользователь сможет выполнять административные задачи через `sudo`.

---

#### Часть 4. Разметка диска

Этот этап критически важен.

1.  **Метод разметки**:
    *   Вам будет предложено выбрать метод разметки диска. Для новичков рекомендуется выбрать **`Guided - use entire disk`** (Использовать весь диск). Выберите диск, на который будет установлена система.

2.  **Схема разделов**:
    *   Затем выберите схему разделов. Рекомендуемый для начинающих вариант — **`All files in one partition (recommended for new users)`** (Все файлы в одном разделе). Более опытные пользователи могут выбрать разделение `/home` для сохранения личных данных при переустановке системы.

3.  **Подтверждение изменений**:
    *   Установщик покажет, какие изменения будут внесены на диск. Подтвердите действие, выбрав **`Yes`** и нажав `Continue`.

---

#### Часть 5. Выбор программного обеспечения (Ключевой этап для GUI)

1.  **Настройка менеджера пакетов**:
    *   На вопрос о сканировании дополнительных установочных носителей ответьте **`No`**.
    *   На вопрос об использовании сетевого зеркала для обновлений ответьте **`Yes`** (рекомендуется) или **`No`** (если хотите настроить источники позже).

2.  **Выбор компонентов для установки (Software selection)**:
    *   Это самый важный экран для нашей задачи. С помощью клавиши **`Space`** отметьте нужные пункты:
        *   **`Debian desktop environment`** — **Обязательно отметьте!** Это установит базовую графическую оболочку (обычно GNOME по умолчанию).
        *   **`... GNOME`** / **`... KDE Plasma`** / **`... Xfce`** — Можно выбрать конкретную среду рабочего стола, если она доступна. По умолчанию установится GNOME.
        *   **`SSH server`** — **Рекомендуется отметить**, это позволит подключаться к серверу удаленно.
        *   **`standard system utilities`** — Базовый набор утилит, рекомендуется оставить отмеченным.
    *   После выбора перейдите на кнопку **`Continue`** и нажмите `Enter`.

3.  **Установка**:
    *   Начнется процесс копирования и установки выбранных пакетов. Это может занять некоторое время в зависимости от скорости интернета.

---

#### Часть 6. Завершение установки

1.  **Установка загрузчика GRUB**:
    *   На вопрос об установке загрузчика GRUB ответьте **`Yes`**.
    *   Выберите диск для установки загрузчика (обычно это `/dev/sda` или аналогичный).

2.  **Перезагрузка**:
    *   После завершения установки появится сообщение. Извлеките установочный носитель (USB-флешку или отключите ISO в настройках виртуальной машины) и нажмите **`Continue`** для перезагрузки.

---

#### Часть 7. Первый запуск и проверка

1.  **Вход в систему**:
    *   После перезагрузки вы увидите графический экран входа (дисплейный менеджер). Войдите под созданным вами обычным пользователем, используя его пароль.

2.  **Проверка работы**:
    *   Убедитесь, что графический интерфейс работает корректно, открыв меню приложений или терминал.

---

Полученная система готова к дальнейшей настройке и использованию в качестве рабочей станции.

Установки Zabix 

Устиановка MySQL для сервера Zabbix
```
apt update

apt install default-mysql-server
```

Установка Zabbix server на виртуальныю машину


Действия производяться согласно описанию приведенному на страницы.

```
https://www.zabbix.com/download?zabbix=6.4&os_distribution=debian&os_version=11&components=server_frontend_agent&db=mysql&ws=apache
```
Запуск и настройка Zabbix

```
http://ip или имя сервера/zabbix/
```
```
Login:   Admin
Password: zabbix
```

 Альтернативные варианты установки ( Не использовать не курсе)

Установка и запуск сервера

 Установка SQL сервера
Для установки будем использовать MySQL
```
# apt install mysql-server
```
 Настройка кодировки UTF-8
```
# nano /etc/mysql/conf.d/utf8.cnf
```
```
[mysqld]
collation_server=utf8_general_ci
character_set_server=utf8
init_connect='SET collation_connection = utf8_general_ci'
init_connect='SET NAMES utf8'
skip-character-set-client-handshake
```
 Управление параметрами сервера

```
# nano /etc/mysql/conf.d/my-custom-settings.cnf
```
```
[mysqld]
sql_mode=""
innodb_strict_mode=OFF
```
```
[mysqld]
sql_mode=""
innodb_strict_mode=OFF
```
Смена пароля пользователя root

Подключение

В интерактивном режиме
```
# mysql -u root -p

Welcome to the MySQL monitor.  Commands end with ; or \g.
```
MariaDB

```
MariaDB [(none)]> ALTER USER root@localhost IDENTIFIED VIA mysql_native_password;

MariaDB [(none)]> SET PASSWORD = PASSWORD('12345678');

# service mysql restart
```
Выход
```
mysql> exit
```

Управление базами данных и пользователями

Просмотр списка баз данных и подключение к базе данных
```
mysql> show databases;
mysql> use mysql;
```

Установка из репозитория Debian
```
# apt install zabbix-server-mysql   #2m

# less /usr/share/doc/zabbix-server-mysql/README.Debian

# nano zabbix.sql
```
```
#drop database zabbix;
create database zabbix character set utf8 collate utf8_bin;

#debian11
#grant all privileges on zabbix.* to zabbix@localhost identified by 'zabbix';

#ubuntu20
#create  USER zabbix@localhost identified by 'zabbix';
#grant all privileges on zabbix.* to zabbix@localhost;
```
```
# mysql < zabbix.sql
```
```
# cat /usr/share/zabbix-server-mysql/{schema,images,data}.sql.gz | mysql -uzabbix -pzabbix zabbix  
```
```
# nano /etc/zabbix/zabbix_server.conf.d/<Название вашего конфига>.conf
```
```
DBHost=localhost
DBName=zabbix
DBUser=zabbix
DBPassword=zabbix
```
Перезапуск служб
```
# systemctl enable zabbix-server

# service zabbix-server start
```
Установка и запуск web интерфейса

Установка и запуск сервера Apache

Debian/Ubuntu

```
# apt install apache2
```

Базовая конфигурация
Управление кодировкой
```
# nano /etc/apache2/sites-available/000-default.conf
...
        AddDefaultCharset utf-8
...
```

Установка компоненов zabbix web
```
# apt install zabbix-frontend-php php-mysql

# less /usr/share/doc/zabbix-frontend-php/README.Debian
```
```
# nano /etc/apache2/conf-available/zabbix-frontend-php.conf
```
```
php_value date.timezone Europe/Moscow

php_value date.timezone Europe/Moscow
```



