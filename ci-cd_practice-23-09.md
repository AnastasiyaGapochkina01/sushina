Написать пайплайн для создания бэкапов базы данных mariadb. Пайплайн должен включать
- сжатие дампа в файл `.*sql.gz`; в имени файла обязательно должен присутствовать timestamp
- проверку валидности бэкапа, например так

```bash
BEGIN=$(head -n 1 dump.sql | grep '^-- MySQL dump' | wc -l)
END=$(tail -n 1 dump.sql | grep '^-- Dump completed' | wc -l)

if [ "$BEGIN" -eq 1 ] && [ "$END" -eq 1 ]; then
  echo "Success"
else
  echo "Error"
fi

```
- копирование файла бэкапа на удаленный сервер в папку `/opt/backups`
- запуск пайплайна по расписанию
- оповещение о результатах выполнения pipeline в Telegram
