# Свойства страницы
Отложенные функции - установка занчений свойств, после их размещения в коде.

После создания страницы и заполнения мета-тегов, появится следующий код:

    <?php
    require($_SERVER["DOCUMENT_ROOT"]."/bitrix/header.php");
    $APPLICATION->SetPageProperty("title", "Название страницы");
    $APPLICATION->SetPageProperty("keywords", "ключаевые слова");
    $APPLICATION->SetPageProperty("description", "Описание страницы");
    $APPLICATION->SetTitle("otzyvy");
    ?>

    Text here...

    <?php require($_SERVER["DOCUMENT_ROOT"]."/bitrix/footer.php"); ?>

Где:
- `SetTitle()` - это H1
- `SetPageProperty()` - свойства страницы

Свойства страницы можно установить в `Настройки > Настрйоки продукта > Настройки модулей > Управление структурой > Типы свойств`:
- Добавим новое свойство страницы: `hidden`.

Посмотреть свойства: `Изменить страницу > Заголовок и свойства страницы`:
- Откроем страницу с отзывами,
- В свойство `hidden` запишем `Скрытое поле`.

Выведем все свойства на страницу:

    <?php
    require($_SERVER["DOCUMENT_ROOT"]."/bitrix/header.php");
    $APPLICATION->SetPageProperty("hidden", "Скрытое поле");
    $APPLICATION->SetPageProperty("title", "Название страницы");
    $APPLICATION->SetPageProperty("keywords", "ключевые слова");
    $APPLICATION->SetPageProperty("description", "Описание страницы");
    $APPLICATION->SetTitle("Отзывы");
    ?>

    <div>H1: <?php $APPLICATION->ShowTitle(false); ?></div>
    <div>hidden: <?php $APPLICATION->ShowProperty('hidden'); ?></div>
    <div>title: <?php $APPLICATION->ShowProperty('title'); ?></div>
    <div>keywords: <?php $APPLICATION->ShowProperty('keywords'); ?></div>
    <div>description: <?php $APPLICATION->ShowProperty('description'); ?></div>

    <?php require($_SERVER["DOCUMENT_ROOT"]."/bitrix/footer.php"); ?>

Переопределять свойства можно в коде даже после кода вывода значения.

Работает принцип наследования значений мета-тегов, если они не установлены на странице, то берутся значения родительского раздела из файла `.section.php`.
