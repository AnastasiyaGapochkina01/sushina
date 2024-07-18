1) Получить информацию о HugePages из файла /proc/meminfo. (Там скорее всего будет по нулям и это норма)
2) Получить информацию о количестве ядер cpu из файла /proc/cpuinfo (строка cpu cores)
3) Получить id (3 поле в строке) пользователя www-data офильтровав содержимое файла /etc/passwd
4) Создать в директории inform_фамилия папку text_processing
5) В text_processing создать файл info.csv с таким содержимым
```
Name,Company,Price,Ganre,Multiplayer
Item1,Company1,60000$,Ganre1,Yes
Item2,Company2,70000$,Ganre2,Yes
Item3,Company3,90000$,Ganre1,Yes
Item4,Company4,90000$,Ganre1,Yes
Item5,Company5,110000$,Ganre1,Yes
Item6,Company6,410000$,Ganre2,Yes
```
6) Вывести первые две строки файла info.csv
7) Вывести стобец Price
8) Найти все строки, в которых встречается слово Ganre2
9) Найти все строки, в которых встречается слово Ganre2 и вывести для них столбец Price
10) Создать в text_processing файл coins с таким содержимым
```
metal	weight	date	country	description
gold     1    1986  USA                 American Eagle
gold     1    1908  Austria-Hungary     Franz Josef 100 Korona
silver  10    1981  USA                 ingot
gold     1    1984  Switzerland         ingot
gold     1    1979  RSA                 Krugerrand
gold     0.5  1981  RSA                 Krugerrand
gold     0.1  1986  PRC                 Panda
silver   1    1986  USA                 Liberty dollar
gold     0.25 1986  USA                 Liberty 5-dollar piece
silver   0.5  1986  USA                 Liberty 50-cent piece
silver   1    1987  USA                 Constitution dollar
gold     0.25 1987  USA                 Constitution 5-dollar piece
gold     1    1988  Canada              Maple Leaf
```
11) Вывести монеты, которые чеканили из золота (gold)
12) Вывести только названия стран, которые чеканили из золота (gold)
13) Вывести монеты, которые чеканили в USA
