1) Из файла /etc/mtab получить режим монтирования cgroup2 (rw или ro)
2) Получить список пользователей из /etc/passwd (только имена)
3) Выполнить команду ps aux - список процессов - и найти процесс ssh
4) Из файла /etc/os-release получить значение PRETTY_NAME
5) Выполнить команду printenv и получить из ее вывода значение HOME
6) Создать файл sample.xml с содержимым
```
<root>
  <person>
    <name>John Doe</name>
    <age>30</age>
    <email>john.doe@example.com</email>
  </person>
  <person>
    <name>Jane Smith</name>
    <age>25</age>
    <email>jane.smith@example.com</email>
  </person>
  <book>
    <title>The Adventure Begins</title>
    <author>Robert Johnson</author>
    <year>2022</year>
  </book>
</root>
```
и получить из него все email.
7) Выполнить команду ls -l /etc и отфильтровать вывод так, чтобы получить только директории/файлы с rc в имени
8) Создать файл access.log с содержимым
```
02.01.2024 05:33:50 localhost ssh: denied wrong password from 156.78.198.42
02.01.2024 06:28:29 localhost ssh: successfully authenticated from 108.117.162.5
02.01.2024 07:27:32 localhost ssh: successfully logged out from 254.199.78.117
02.01.2024 11:24:56 localhost ssh: connection dropped by timeout from 227.65.89.157
02.01.2024 11:59:29 localhost ssh: denied wrong password from 252.175.99.156
02.01.2024 12:17:44 localhost ssh: connection dropped by timeout from 50.26.154.246
```
9) Найти в файле access.log строки, содержащие denied wrong password
10) Для всех найденных строк из п9 вывести только ip-адрес
11) Получить из файла /etc/fstab только UUID
