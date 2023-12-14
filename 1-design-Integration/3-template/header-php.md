# header.php
Открываем файл header.php у стандартной темы Битрикс, копируем API оттуда.

В начале файла:

    // Проверка константы B_PROLOG_INCLUDED
    if (!defined("B_PROLOG_INCLUDED") || B_PROLOG_INCLUDED !== true) {
      die();
    }

    // Подключаем языковые файлы
    IncludeTemplateLangFile(__FILE__);

Перед `</head>`:

      // Показать название страницы
      <title><?php $APPLICATION->ShowTitle(); ?></title>

      // Подключает основные поля тега head: мета-теги content-type, robots, keywords, description; стили CSS; скрипты
      <?php $APPLICATION->ShowHead(); ?>
    </head>

- `SITE_TEMPLATE_PATH` - URL от корня сайта до папки текущего шаблона, для пользовательских стилей, скриптов, изображений

Подключение административной панели управления:

    <body>
      <div id="panel">
        <?php $APPLICATION->ShowPanel(); ?>
      </div>

Общий код:

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
      <script type="text/javascript" src="<?php echo SITE_TEMPLATE_PATH; ?>/js/jquery-1.8.2.min.js"></script>
      <script type="text/javascript" src="<?php echo SITE_TEMPLATE_PATH; ?>/js/slides.min.jquery.js"></script>
      <script type="text/javascript" src="<?php echo SITE_TEMPLATE_PATH; ?>/js/jquery.carouFredSel-6.1.0-packed.js"></script>
      <script type="text/javascript" src="<?php echo SITE_TEMPLATE_PATH; ?>/js/functions.js"></script>
      <link rel="shortcut icon" type="image/x-icon" href="<?=SITE_DIR?>favicon.ico" />
      <?php $APPLICATION->ShowHead(); ?>
    </head>
    <body>
      <div id="panel">
        <?php $APPLICATION->ShowPanel(); ?>
      </div>
