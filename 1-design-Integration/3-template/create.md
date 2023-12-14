# Создание шаблона
Настройки > Настройки продукта > Сайты > Шаблоны сайтов > Добавить шаблон

- ID - inner
- Название - Внутренние страницы
- Описание - Шаблон внутренних страниц
- Кликаем по ссылке `#WORK_AREA#` (создадутся пустые файлы header.php, footer.php)
- Сохранить

Папка `inner` создастся в папке `/bitrix/templates/` перенесите `/local/templates/`.

Папка `inner` содержит:
- .styles.php
- description.php
- footer.php
- header.php
- styles.css
- template_styles.css

Переносим верстку:
- Переносим в header.php верхнюю часть сайта,
- Переносим в footer.php нижнюю часть сайта,
- Переносим стили в template_styles.css,
- Переносим папку со скриптами
- Переносим папку с изображениями

## Создание шаблона главной страницы
Настройки > Настройки продукта > Сайты > Шаблоны сайтов > Добавить шаблон

- ID - main
- Название - Главная страница
- Описание - Шаблон главной страницы
- Кликаем по ссылке `#WORK_AREA#` (создадутся пустые файлы header.php, footer.php)
- Сохранить

Чтобы не переносить все стили, скрипты и изображения, можно взять их из шаблона внутренних страниц и перенести в папку `.default`, также файл template_styles.css. И поменять пути покдлючения файлов на .default

Теперь путь до template_styles.css нужно прописать в header.

    <?php
    // Проверка константы B_PROLOG_INCLUDED
    if (!defined("B_PROLOG_INCLUDED") || B_PROLOG_INCLUDED !== true) {
      die();
    }
    ?>
    <!DOCTYPE HTML>
    <html lang="en-US">
    <head>
      <title><?php $APPLICATION->ShowTitle(); ?></title>
      <link rel="stylesheet" href="/local/templates/.default/template_styles.css" />
      <script type="text/javascript" src="/local/templates/.default/js/jquery-1.8.2.min.js"></script>
      <script type="text/javascript" src="/local/templates/.default/js/slides.min.jquery.js"></script>
      <script type="text/javascript" src="/local/templates/.default/js/jquery.carouFredSel-6.1.0-packed.js"></script>
      <script type="text/javascript" src="/local/templates/.default/js/functions.js"></script>
      <link rel="shortcut icon" type="image/x-icon" href="<?=SITE_DIR?>favicon.ico" />
      <?php $APPLICATION->ShowHead(); ?>
    </head>
    <body>
      <div id="panel">
        <?php $APPLICATION->ShowPanel(); ?>
      </div>

В /index.php оставляем только подключения header.php и footer.php  
В header.php помещаем весь код главной или всё до футера.

## Подключаем главную и внутренню в админке
Подключаем шаблоны главной и внутренних в админке.
- Настройки > Настройки продукта > Сайты > Список сайтов > s1 > Шаблон сайта
- Главная > Для папки или файла > /index.php
- Внутренняя > Без условия
