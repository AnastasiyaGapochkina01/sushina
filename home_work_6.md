# Часть 1: Справка
1) Установка из репозиториев с помощью пакетного менеджера
```
# обновляем информацию о досутпных пакетах (может, выпустили новую верисю?), но не обновляем само ПО
sudo apt update
# устанавливаем пакет (вместо <package-name> подставить имя пакета, например nginx)
sudo apt install <package-name>
```
2) Установка пакетов (.deb)
```
# скачиваем пакет с помощью утилиты wget, например
wget http://ftp.uk.debian.org/debian/pool/main/f/fcheck/fcheck_2.7.59-25_all.deb
# в выводе ls должны увидеть fcheck_2.7.59-25_all.deb
ls
# устанавливаем с помощью dpkg и ключа -i (install)
sudo dpkg -i fcheck_2.7.59-25_all.deb
# смотрим внимательно на "выхлоп" консоли, могут быть ошибки, связаныне с неустановленными зависимостями. Тогда их нужно доставлять вручную
# после установки можно выполнить поиск, куда установщик положил исполняемый файл
whereis fcheck
```
3) Сборка из исходников.

Алгоритм:
- поиск исходников. например php53 можно взять по ссылке
https://sourceforge.net/projects/mapn/files/source/php/php-5.3.6.tar.gz/download?use_mirror=master
- распаковка архива с исходным кодом
```
tar -xzvf php-5.3.6.tar.gz -C /src/php53
```
- создание MAKEFILE (инструкции, как компилировать ПО). Скрипт configure может использоваться и с ключами
```
./configure
# или например так, если надо включить модуль fpm, задать пользователя и группу (и еще много других параметров)
./configure --enable-ftp \
--disable-cgi \
--enable-fpm \
--with-fpm-user=www-data \
--with-fpm-group=www-data
```
- сборка
```
make
```
- установка (метод "в лоб")
```
make install
```
# Часть 2: Сборка из исходников
1) По инструкции https://docs.docker.com/engine/install/debian/#install-using-the-repository установить докер
2) Установить git
```
sudo apt install git -y
```
3) Склонировать репозиторий с файлами docker, поднять контейнер по инструкции ниже
```
git clone git@github.com:AnastasiyaGapochkina01/06_home_work.git
cd 06_home_work
sudo docker compose up -d --build
sudo docker exec -it old-debian bash
```
4) После того, как выполнил ```sudo docker exec -it old-debian bash``` ты попал в контейнер и все выполняешь в нем
- перейти в директорию /usr/src/php
- выполнить
```
export gnuArch="$(dpkg-architecture --query DEB_BUILD_GNU_TYPE)"
export debMultiarch="$(dpkg-architecture --query DEB_BUILD_MULTIARCH)"
```
- запустить конфигуратор
```
./configure \
    --host="${gnuArch}" \
    --with-libdir="/lib/${debMultiarch}/" \
    --with-config-file-path="${PHP_INI_DIR}" \
    --with-config-file-scan-dir="${PHP_INI_DIR}/conf.d" \
    --disable-cgi \
    --enable-ftp \
    --enable-mbstring \
    --enable-mysqlnd \
    --enable-fpm \
    --with-fpm-user=www-data \
    --with-fpm-group=www-data \
    --with-mhash \
    --with-pdo-sqlite=/usr \
    --with-sqlite3=/usr \
    --with-curl=/usr/local \
    --with-openssl=/usr/local/ssl \
    --with-readline \
    --with-recode \
    --with-zlib
```
- запустить сборку
```
make
```
она свалится с ошибкой
```
collect2: error: ld returned 1 exit status
Makefile:260: recipe for target 'sapi/fpm/php-fpm' failed
make: *** [sapi/fpm/php-fpm] Error 1
```
нужно установить libcurl4-gnutls-dev с помощью apt/apt-get и снова запустить make
- запустить ```make install```
- проверить, что php установился
# Часть 3: Установка из пакета (тоже выполнять в контейнере)
1) С помощью apt установить gnupg2 и lsb-release. Пакетный менеджер выругается, что не будут установлены зависимости, надо выполнить
```
apt-get -f install
```
и повторить команду установки
2) Скачать пакет
```
wget http://ftp.de.debian.org/debian/pool/main/m/memstat/memstat_1.1+b1_amd64.deb
```
3) Установить пакет командой ```dpkg```
4) Проверить, выполнив ```memstat```
# Часть 4: Установка через apt с добавлением репозитория
1) Скачать пакет
```
wget https://repo.percona.com/apt/percona-release_latest.$(lsb_release -sc)_all.deb
```
2) Установить
```
dpkg -i percona-release_latest.$(lsb_release -sc)_all.deb
```
посмотреть в /etc/apt/sources.list.d - там появится файл с репозиторием percona
3) Обновить индекс
```
apt update
```
4) Установить percona
```
apt install percona-server-server-5.7
```
5) Проверить ```mysql -V```
