# Слайдер

- создаём инфоблок для слайдера
- там же создадим свойство ссылку, которое будет ссылаться на детальную страницу

В настройке инфоблока:
- не трокаем шаблоны ссылок
- отключаем индексирование разделов и элементов
- в свойствах создаем ссылку
- доступы чтение для всех

Вывод инфоблока осуществляется через компонент news.list, размещаем его на тестовой странице.

Настройка компонента:
- тип инфоблока контент
- инфоблок слайдер
- выделить свойство LINK
- сохранить
- сохранить

Копируем шаблон в local называем slider.  
В шаблоне в цикле `$arItem['PROPERTIES']['LINK']['VALUE'][]`

Код вызова компонента размещаем в шаблоне.  
Отредактируем форму редактирования добавления элемента инфоблока.
