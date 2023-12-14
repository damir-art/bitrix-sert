# Компоненты
Компонент - это реализация определённой функции на сайте.
- Компонент - с помощью АПИ (одного или нескольких модулей) манипулирует данными (контроллер, логика).
- Шаблон компонента - выводит данные на страницу (представление).

Меню, список новостей, список товаров, добавлением товара в корзину, оформление заказа, отправка писем.

## Размещение компонента
- Создаём тестовую страницу test.php
- В визуальном редакторе перетаскиваем компонент меню

Код вызова компонента меню:

    <?php
      $APPLICATION->IncludeComponent(
        "bitrix:menu",
        "",
        Array(
          "ALLOW_MULTI_SELECT" => "N",
          "CHILD_MENU_TYPE" => "left",
          "DELAY" => "N",
          "MAX_LEVEL" => "1",
          "MENU_CACHE_GET_VARS" => array(""),
          "MENU_CACHE_TIME" => "3600",
          "MENU_CACHE_TYPE" => "N",
          "MENU_CACHE_USE_GROUPS" => "Y",
          "ROOT_MENU_TYPE" => "left",
          "USE_EXT" => "N"
        )
      );
    ?>

- `$APPLICATION->IncludeComponent()` - в метод IncludeComponent() объекта $APPLICATION передаются параметры:
  - имя компонента состоит из пространства имён и имени
  - шаблон компонента (если не задан то используется дефолтный по-умолчанию)
  - настройки компонента
  - четвертый используется для компонентов в составе комплексного

Компоненты располагаются в директории `bitrix/components/namespace`  
`bitrix/components/bitrix/` - располагаются типовые стандартные компоненты, здесь не рекомендуется вносить изменения в компоненты и их шаблоны

## Файловая структура компонента
Файловая структура компонента на примере меню: `/bitrix/components/bitrix/menu/`:
- images/
- lang/ - языковые файлы
- templates/ - шаблоны компонента
  - .default/ - шаблон подключается если имя не выбрано
  - имя шаблона:
    - lang/ - языковые файлы
    - .description.php - описание шаблона
    - script.js - скрипты шаблона (подключаются автоматически)
    - style.css - стили шаблона (подключаются автоматически)
    - template.php - основной файл отвечающий за вывод информации
- .description.php - название компонента, описание, размещение в дереве визуального редактора,
- .parameters.php - настройки компонента, формирование массива arParams[],
  - список параметров формируется в настройке компонента,
- логика комопнента class.php, component.php:
  - получение массива arParams[]
  - работа с АПИ модулей,
  - получение данных из модулей,
  - формирование массива arResult[]
- stub.php

## Схема работы компонента
В файле .parameters.php формируется массив arParams[].  
В логику компонента отправляется массив arParams[].  
В логике компонента происходит обработка входящих параметров arParams[].  
В логике компонента формируется массив arResult[].  
В template.php отправляется массив arResult().

arResult() - результат работы компонента.  
Папка templates может отсутствовать, если у компонента нет вывода.  
Могут присутстовать другие файлы и папки, например images/.

## templates
Из чего состоит папка templates шаблоны компонента.

templates/ - шаблоны компонента
- .default/
  - системный шаблон
  - подключается если имя шаблона не выбрано
- имя шаблона:
  - lang/ - языковые файлы
  - .description.php - описание шаблона
  - script.js - скрипты шаблона (подключаются автоматически)
  - style.css - стили шаблона (подключаются автоматически)
  - template.php - основной файл отвечающий за вывод информации

В template.php идёт работа с массивом arResult().  

## Устройство компонента
- .parameters.php
  - $arParams[]
- components.php - только для локиги
  - $arParams[]
  - $arResult[]
- template.php - только для представления
- HTML
- кеш

Свои компоненты рекомендуется создавать если стандартные нагружают систему, чтобы уменьшить нагрузку на сервер.