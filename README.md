# yii2-fias-extended

Решил для удобства вшить wertex/yii2-fias в установленый yii2  
wertex/yii2-fias это форк [ejen/yii2-fias](ejen/yii2-fias)

# Установка
```
git clone https://github.com/wertex/yii2-fias-extended.git
composer update
```

# DBF
Для работы с файлами DBF я использовал dll [отсюда](https://github.com/nufue/pecl-dbase-windows)

# Применение миграций
```
php yii migrate --migrationPath=@vendor/wertex/yii2-fias/console/migrations
```
# Настройка консольного приложения
Для выполнения консольных комманд уже прописана следующая настройка в конфиге консольного приложения (console.php):
```php
    ...
    'controllerMap' => [
        'fias' => [
            'class' => 'ejen\fias\console\controllers\FiasController',
        ]
    ],
    ...
```
# Консольные команды
## Импорт dbf файла в базу данных
Качаем по [ссылке](http://fias.nalog.ru/Updates.aspx) **fias_dbf.rar**
Вытаскиваем **только нужные файлы** вашего региона (так будет быстрее, чем ждать разархивации всей информации)
Кладем файлы в корень проекта в папку **data**.  
Выполняем консольные команды по очереди:
```
php yii fias/import-dbf data\ADDROB66.DBF --region=66
php yii fias/import-dbf data\HOUSE66.DBF
```
Опция region является не обязательной и позволяет импортировать записи относящиеся только к конкретному региону(в случае импорта ADDROBJ.DBF)
