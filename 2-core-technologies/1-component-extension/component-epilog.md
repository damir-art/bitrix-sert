# component_epilog.php

Устанавливаем мета-данные. Использование функций даже при отключенном кеше.  
В файле component_epilog.php мы получаем массив arResult из кеша.  
component.php содержит функцию SetResultCacheKeys где указаны параметры, которые должны кешироваться.  
