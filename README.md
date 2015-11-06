# Жуэль
Жуэль — простой и красивый плеер для веба.

[Страница проекта](http://ilyabirman.ru/projects/jouele/)

## Как установить
```html
<!-- Dependencies -->
<script src="http://code.jquery.com/jquery-1.11.3.min.js"></script>
<script src="dist/jquery.jplayer.min.js"></script>
<!-- Jouele -->
<script src="dist/jouele.js"></script>
<link href="dist/jouele.css" rel="stylesheet"/>
```

## Как использовать
Каждая ссылка с классом jouele превратится в плеер МП3-файла, на который она ведёт. Например:
```html
<a href="http://audio.ilyabirman.ru/Ilya%20Birman%20-%20News.mp3" class="jouele">Ilya Birman: News</a>
```
Обратитесь к файлу `index.html`, чтобы увидеть дополнительные примеры использования.

## Расширенные возможности

### data-атрибуты
Добавление некоторых data-атрибутов изменит поведение или внешний вид плеера.

```data-length (String)```

Указывает общую продолжительность трека, чтобы время показывалось сразу, а не после нажатия кнопки «плей».
Примеры для трека длительностью 2 минуты 47 секунд: `data-length="2:47"`, `data-length="167"`

```data-pause-on-space (Boolean)```

Определяет, нужно ли останавливать этот трек по нажатию пробела. По умолчанию `true`.

```data-scroll-on-space (Boolean)```

Определяет, нужно ли проскроллить страницу после нажатия пробела и остановки играющего трека. Работает только если `data-pause-on-space` установлен в `true`. По умолчанию `false`.

```data-hide-timeline-on-pause (Boolean)```

Определяет, нужно ли скрывать таймлайн трека, когда он не играет. По умолчанию `false`.

### Скин
Добавление класса `jouele-skin-dark` к ссылке, которая будет инициализирована Жуэлем, включает предустановленный «тёмный» скин. Например:
```html
<a href="http://audio.ilyabirman.ru/Ilya%20Birman%20-%20News.mp3" class="jouele jouele-skin-dark">Ilya Birman: News</a>
```

Разработчик может создать собственный скин, изучив CSS-файл `jouele.skin.css`.
Для подключения нового скина нужно следующее:
- Заменить в `jouele.skin.css` все селекторы `jouele-skin-dark` на новое название, сохранив паттерн `jouele-skin-` (например, `jouele-skin-blue`).
- Добавить в ссылку, которая будет инициализирована Жуэлем, класс `jouele-skin-{название_скина}`.
- Подключить на сайт исправленный файл `joule.skin.css` после `jouele.css`.

## Динамическая инициализация

```
$(selector).jouele()
```
Превращает ссылку `selector` в плеер. Возвращает jQuery-объект, к которому применялся метод — `$(selector)`.
Если всё прошло хорошо, то в этот же jQuery-объект `$(selector)` добавится дополнительная `data` с именем `jouele`, в которой будет лежать экземпляр плеера `Jouele` (с этим экземпляром и работает весь API, см. ниже). DOM-объект `selector` будет исключен из DOM при помощи jQuery.detach().
Добавленный в DOM блок плеера с классом `jouele` и уникальным id будет также иметь в своём `data.jouele` экземпляр плеера `Jouele`.

## API
Самый простой способ обратиться к API:
```javascript
$(".jouele").data("jouele") // Получить экземпляр Jouele
```

### Методы API

```
Jouele.play()
```
Начинает воспроизведение трека. Возвращает экземпляр плеера `Jouele`.

```
Jouele.pause()
```
Останавливает воспроизведение трека. Возвращает экземпляр плеера `Jouele`.

```
Jouele.destroy()
```
Уничтожает плеер, возвращая в DOM-дерево ссылку, из которой он был создан. Возвращает jQuery-объект ссылки.

### Свойства API

```
Jouele.$link (jQuery object)
```
Хранит jQuery-объект, из которого был создан плеер.

```
Jouele.isPlaying (Boolean)
```
Указывает, играет ли сейчас этот трек.

```
Jouele.isPlayed (Boolean)
```
Указывает, запускался ли этот трек.

```
Jouele.totalTime (Number)
```
Хранит длительность трека в виде количества секунд. Может быть дробным.

## Титры
Идея и разработка — [Илья Бирман](http://ilyabirman.ru)

Разработка — [Евгений Лазарев](http://www.eugene-lazarev.ru)

## Лицензия
MIT License
