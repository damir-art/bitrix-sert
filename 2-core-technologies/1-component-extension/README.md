# Расширение возможностей типовых компонентов

Расширяем функционал типового компонента с помощью:
- result_modifier.php - создаётся в папке шаблона компонента, должен присутствовать пролог как у template.php
- component_epilog.php - создаётся в папке шаблона компонента, должен присутствовать пролог как у template.php
- .parameters.php - дополняет визуальные параметры компонента

component_epilog.php - подключается после исполнения шаблона.  
Шаблон подключается в component.php с помощью функции: `includeComponentTemplate()`.  
После него идет код где можно переопределить функции используемые в component_epilog.php

Если очистить кеш то все файлы подключатся в одно и тоже время.  
Если обновить страницу с кешем обновится время у component_epilog.php, этот файл не кешируется.

## Итог
- result_modifier.php - дополняет $arResult, кешируется как и шаблон.
- template.php - шаблон, получаем верстку HTML, которая кешируется.
- component_epilog.php - подключается после исполнения шаблона, расширяет функции компонента, не кешируется.

## Устройство компонента часть вторая (см img/1.png)
- .parameters.php
  - $arParams[] - попадает в components.php
- component.php - только для логики
  - $arParams[] - попадает в result_modifier.php
  - $arResult[] - попадает в result_modifier.php
- result_modifier.php
  - $arParams[] - попадает в template.php
  - $arResult[] - попадает в template.php
- template.php - только для представления
  - $arParams[] - попадает в кеш
  - $arResult[] - попадает в кеш
  - HTML        - попадает в кеш
- КЕШ - отправляется клиенту в виде HTML
  - $arParams[] - попадает в component_epilog.php
  - $arResult[] - попадает в component_epilog.php
- component_epilog.php

$arResult[] в component_epilog.php содержит меньше данных чем в result_modifier.php, чтобы уменьшить объем массива попадаемогов кеш  
Для дополнения $arResult[] доступного в component_epilog.php используется API функция SetResultCacheKeys() в result_modifier.php  
component_epilog.php подключается после исполнения шаблона, после него могут следовать вызовы API находящиеся в component.php  
`component_epilog.php` вызывается на каждом хите, не размещайте в нем тяжелый код.
