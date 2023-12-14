# Отладка
Способы отладки применяемые при разрботке сайта.

Для чего нужна отладка:
- понимание того с какими данными работают компоненты
- возможность отслеживать изменения данных
- обнаружение причин ошибок в работе сайта

Что проверять отладкой:
- $arParams - набор параметров, определяет с какими данными работает компонент.
- $arResult - результат работы компонента, сформированный параметрами запроса и базой данных.

Схема:
- $arParams
- component.php <--> БД
- $arResult
- result_modifier.php
- template.php
- отображение

Что выведет print_r($arParams) и print_r($arResult).  
Можно использовать print_r(), var_dump(), var_export().  
result_modifier.php модифицирует данные работы комопнента.  
Где размещать функции: php_interface/init.php, php_interface/include/dump.php (пользовательский файл)  
Показывать отладочную информацию можно для определённого пользователя, по айпи или по параметрам в строке URL.