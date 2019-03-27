---
lastChanged: 14.09.2018
translatedFrom: de
translatedWarning: Если вы хотите отредактировать этот документ, удалите поле «translationFrom», в противном случае этот документ будет снова автоматически переведен
editLink: https://github.com/ioBroker/ioBroker.docs/edit/master/docs/ru/basics/README.md
title: основы
hash: 46Emgb6RhhtKOmznvzllM65gAhQS1y+ya+CTcZGe9ME=
---
# Основы
?> ***Это подстановочный знак*** . <br><br> Помогите с ioBroker и расширьте эту статью. Пожалуйста, обратите внимание на [Руководство по стилю ioBroker](community/styleguidedoc), чтобы изменения могли быть легко приняты.

@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@, из-за того,

После прочтения основ пользователь должен уметь понимать и назначать различные термины, относящиеся к ioBroker.

Цель короткая и четкая, с 2-4 строками, если необходимо, позже все перестраивается как страница с длинным скроллером.

Основные статьи должны ссылаться на соответствующие подробные описания.
@@@

## Определение терминов
Чтобы упростить начало работы и понять дальнейшую помощь, вот наиболее важные термины, которые объясняются в ioBroker и вокруг него.

* `Host`: устройство, на котором установлен ioBroker
* `Adapter`: модуль или плагин для ioBroker, например, для связи с оборудованием
    - не может быть запущено
    - Может быть только один адаптер на хост
* `Instanz`: исполняемая копия адаптера
    - выполняет код, предоставленный адаптером
    - можно запустить и остановить
    - может иметь настройки
    - адаптер должен быть установлен, чтобы иметь экземпляры адаптера
* `Objekt`: Поле, в котором могут храниться данные
    - Большинство экземпляров создают `channel`
    - `channel` - это объект, который действует как папка
* `Aufzählung`: содержит, например, список комнат
* `Log`: протокол о накопленных ошибках
    - фильтруется по степени серьезности события, экземпляра и т. д.
* `Ereignisse`: Список всех изменений объектов