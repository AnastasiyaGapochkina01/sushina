1) Создать директорию home_work2 в домашней директории
2) В home_work2 создать директорию devops-project
3) В devops-project создать директории frontend, backend и storage
4) В директории storage с помощью команды cat создать файл data.csv с таким содержимым
```
Name Department Phone
J.Smith development +19873456
S.Grows security -
E.Bett-Rikards development +13456239
S.Brown qa +19746293
E.Green manager +16734567
```
5) В директории frontend создать файл index.html с таким содержимым
```
<!DOCTYPE html>
<html>
<body>

<h1>Frontend</h1>
</body>
</html>
```
6) В devops-project с помощью команды echo создать файл proxy.conf с содержимым
```
# TODO: nginx conf
```
7) В директории backend создать файл app с таким содержимым
```
package main

import "fmt"

func main() {
    fmt.Println("Hello, World!")
}
```
8) В директории home_work2 создать директорию backups
9) Скопировать директории frontend, backend и storage в backups с новыми именами: frontend_bk, backend_bk и storage_bk
10) Удалить из devops-project директорию storage и затем "восстановить" ее из директории backups/storage_bk
11) В директории frontend создать 5 файлов с любым содержимым:
- checkout.html
- footer.html
- logo.png
- promo
- style.css
12) Скопировать все файлы из директории frontend в frontend_bk
13) Переименовать файл logo.png в logo
14) Создать в frontend директорию styles и переместить туда style.css
15) Посмотреть первые шесть записей любого лога из /var/log
16) Посмотреть последние двадцать записей любого лога из /var/log
17) Посмотреть содержимое файла /proc/meminfo
18) Посмотреть содержимое файла /proc/cpuinfo
19) Вывести 4 и 5 строки из файла /etc/group
20) Посмотреть содержимое файла /etc/network/interfaces
