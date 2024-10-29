# Часть 1
1) В домашней директории создать папку text_processing
2) В папке text_processing создать файл info.csv с таким содержимым
```
Name:Company:Price:Ganre:Multiplayer
Item1:Company1:60000$:Ganre1:Yes
Item2:Company2:70000$:Ganre2:Yes
Item3:Company3:90000$:Ganre1:Yes
Item4:Company4:90000$:Ganre1:No
Item5:Company5:110000$:Ganre1:Yes
Item6:Company6:410000$:Ganre2:Yes
Item7:Company1:60000$:Ganre1:Yes
Item8:Company4:40000$:Ganre2:No
Item9:Company3:90000$:Ganre1:Yes
```
3)) В файле info.csv найти строки, которые содержат слово No
4) В файле info.csv найти все строки, в которых встречается слово Ganre2
5) В файле info.csv найти все строки, в которых встречается слово Ganre2 и вывести только 3 поле
6) Создать файл metrics с содержимым
```
metric_name:metric_type:interval
cache_disk_use:gauge:1
cache_use:gauge:0
key_buffer_bytes_used:byte:3
table.rows.read:count:10
disk_use:gauge:10
data_size:gauge:1
rows_deleted:count:1
bytes_received:byte:1
```
7) В файле metrics найти все строки, в которых встречается слово gauge и вывести только первое поле
8) В файле metrics найти все строки, в которых встречается слово byte и вывести только 3 поле
9) В файле metrics найти все строки, в которых встречается слово disk и вывести только 2 поле
10) В файле metrics найти все строки, которые *начинаются* с cache
11) В файле info.csv найти все строки, которые содержат слово Company4
12) Отфильровать вывод команды lscpu так, чтобы получить значение CPU MHz
13) Отфильровать вывод команды lscpu так, чтобы получить значение Hypervisor vendor
14) Отфильтровать вывод команды lsblk так, чтобы получить имена разделов
15) Отфильтровать вывод команды free -h так, чтобы получить размер Swap
16) Выполнить команду lsmod и в выводе найти строку, которая содержит информацию о модуле floppy и вывести второй столбец
17) В директории text_processing создать файл logs с содержимым
```
# Cron logs
Oct 20 06:24:01 server1 CRON[1349677]: (user1) CMD (   /usr/bin/python3 /home/user1/update.py)
Oct 20 06:25:01 server3 CRON[1349678]: (user2) CMD (   /usr/bin/python3 /home/user2/report.py)
Oct 20 06:26:01 server2 CRON[1349679]: (root) CMD (   /usr/bin/cleanup.sh)
Oct 20 06:27:01 server3 CRON[1349680]: (user3) CMD (   /usr/bin/backup.sh)
Oct 20 06:28:01 server1 CRON[1349681]: (user4) CMD (   /usr/bin/monitor.sh)

# Error logs
Oct 20 06:30:00 server1 sshd[12345]: Failed password for invalid user admin from 192.168.0.10 port 22 ssh2
Oct 20 06:31:00 server3 sshd[12346]: Failed password for invalid user guest from 192.168.0.11 port 22 ssh2
Oct 20 06:32:00 server1 sshd[12347]: Accepted password for user2 from 192.168.0.12 port 22 ssh2
Oct 20 06:33:00 server1 sshd[12348]: Failed password for invalid user test from 192.168.0.13 port 22 ssh2

# Warning logs
Oct 20 06:35:00 server1 kernel: [123456] Warning! CPU temperature is high.
Oct 21 09:10:00 server2 kernel: [123458] Warning! High CPU usage detected on process ID 5678.
Oct 21 09:11:00 server2 systemd[1]: Warning! Service myservice.service is taking too long to start.
Oct 21 09:12:00 server2 sshd[23461]: Warning! Multiple failed login attempts from 192.168.0.25.
Oct 21 09:13:00 server2 application[34571]: Warning! Disk space on /home is below 10% remaining.

# Info logs
Oct 21 09:02:00 server2 application[34569]: INFO User1 logged in successfully.
Oct 21 09:03:00 server2 application[34570]: INFO User3 logged out.
Oct 21 09:14:00 server2 application[34572]: INFO User4 logged in successfully from 192.168.0.26.
Oct 21 09:15:00 server2 application[34573]: INFO Backup completed successfully at /backup/user4_backup.tar.gz.
Oct 21 09:16:00 server2 systemd[1]: INFO Service myservice.service started successfully.
Oct 21 09:17:00 server2 sshd[23462]: INFO User1 logged out from session on terminal pts/0.
```
18) В файле logs.txt найти все записи, которые содержат application
19) В файле logs найти записи о запусках cron на сервере server3 и вывести команду, которая запускалась (это то, что в скобках в конце)

<img width="928" alt="image" src="https://github.com/user-attachments/assets/c61ff7c3-5346-45ff-a45e-c6511dde87a1">

20) В файле logs найти запись о сервисе myservice
21) В файле logs найти все записи, содержащие ssh и вывести для них название сервера (третье поле)

<img width="714" alt="image" src="https://github.com/user-attachments/assets/b13e56a0-1b74-438f-b910-55b9d4e1e4fa">

22) В файле logs найти все записи, содержащие kernel и вывести для них шестое поле
23) В файле logs найти все записи, содержащие "Failed password" и вывести только ip

<img width="699" alt="image" src="https://github.com/user-attachments/assets/da09364f-353d-4bd5-8563-423402547b1b">

24) В файле logs.txt найти записи, содержащие "Accepted password" и вывести имя пользователя и ip

<img width="688" alt="image" src="https://github.com/user-attachments/assets/1d36804e-31b3-4257-9b1d-97c0130a3acc">

25) В файле logs.txt найти записи, содержащие "Disk space" и вывести название сервера

# Часть 2
1) Создать группы: developers, designers и managers
2) Создать пользователей user-tech-1, user-tech-2, user-tech-3, user-tech-4, user-tech-5, user-tech-6
3) Пользователей user-tech-2, user-tech-3 и user-tech-6 добавить в группу developers
4) Пользователей user-tech-1 и user-tech-4 добавить в группу designers
5) Пользователя user-tech-5 добавить в группу managers
6) Создать пользователя admin, задав ему при создании uid=6666, добавить в группу sudo
7) Вывести на экран состав групп developers, designers и managers
8) Задать пароли для всех пользователей
9) Создать папку project, в ней папки code, psd и docs
10) Создать файл server.go и положить его в папку code
11) Создать файл maket1 и положить его в папку psd
12) Создать файл license и положить его в папку docs
13) Дать права на папки группам
- developers на code
- designers на psd
- managers на docs
14) Владельцем директорий code, psd и docs сделать пользователя admin

# Часть 3
1) Вывести список всех процессов
2) В списке процессов найти php-fpm (если установлен; если нет - взять apache)
3) Вывести для процесса php-fpm параметры php-fpm (если установлен; если нет - взять apache)
- pid
- ppid
- stat
- comm
4) Отобразить процессы пользователя www-data
5) В директории proc найти папку, соответствующую процессу php-fpm (если установлен; если нет - взять apache)
6) Вывести какой сейчас load avergage на сервере
