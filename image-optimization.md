# Оптимизация изображений для WEB

https://miro.com/app/board/uXjVN8bnvyw=/?share_link_id=255145644498 - борда на которой собраны матерьялы по теме

## Какие вопросы бро?

### Что такое изображения?

Бля википедя "ахуенная" 🤷‍♂️

> Цифровое изображение — двумерное изображение, представленное в цифровом виде. В зависимости от способа описания, изображение может быть растровым или векторным.

лучше и не скажешь.

Два новых понятия в студию "Растр" и "Вектор"

Растровое изображение - представление двух типов данных: положение и цвет пикселя. Графическая матрица пикселей 🤯
Векторное изображение - набор простых геометрических фигур точка линия и (сплайны, кривые Безье, круги, окружности, эллипсы, многоугольники) тд... представленных в математических формулах и параметров к ним

Изображения бывают в разных форматах:

- для растровых изображений различие между форматами заложено в том как хранятся значения пикселей.
- векторные изображения обычно представлены в текстовом виде (ну или в текстовом + заархивированном 🍌)

**К растру у нас относится**: gif, jpg, png, webp, avif

**К вектору**: svg

#### Разберем по форматам чо к чему?

![image history](image-history.png?raw=true "image history")

_GIF_ - как завещали старшие кто не знает что такое гифки тот лох. В целом если ты не знаешь что такое гифки "Вон из профессии" но это так лирика.
Довольно древний формат разработан еще в 1987 году. Деды помнят и нам велели...🐷 Ограничен 256 цветами, но может играть анимацию и поддерживает прозрачность (за что мы его и любим💞). Формат файла поддерживает LZV компрессию, но в текущих реалиях гифки "все равно 🤷‍♂️" весят довольно много и в вебе используют ограниченно.

_JPG_ - 👑 король картинок где не важен (🤮) прозрачный фон, отлично сжимается. Сейчас его постепенно вытесняет WEBP, но за частую больше 80% картинок в этом формате.

![shakal](shakal.png?raw=true "shakal")

_PNG_ - когда браузеры начали поддерживать PNG это был прорыв. И прорыв жопы дизайнеров + тогдашних верстальщиков (http://chikuyonok.ru/2009/10/decor/) эх было время. И бордер радиус еще не был придуман. Хорошо жметься, но требует больше затрат по процу. Поддерживает прозрачность. В вебе юзаеться на равне с _jpeg_, хорошим тоном считается использовать его там где по дизайну задуман прозрачный фон.

_WEBP_ - производная JPG и PNG, придумано гуглом, взяли лучшее от обоих форматов https://developers.google.com/speed/webp но есть проблемы с поддержкой в старых Safari

_AVIF_ - примдуман Alliance for Open Media https://aomediacodec.github.io/av1-avif/, в процессе создания туда запускал руки Netflix. Появился относительно недавно 2019 год. Лучшая компрессия из всех. Поддерживается Chrome + FF. Есть поддержка анимации. Должен прийти на смену webp.

изощренные виды _HEIF/HEIC_, _JPEG XL_

_SVG_ - разработан относительно недавно 2001 год, текстовый, отлично жмется zip. В вебе используется для сервисных изображений (иконки, логотипы). свг хорош тем что его не пожрет шакал и он очень мало весит.

### Как и зачем изображения можно оптимизировать?

Под оптимизацией мы подразумеваем компрессию. Уменьшение размера файла без потери информации (в идеале 🤷‍♂️). Изображения в среднем занимают 50% (per bites) любой страницы в интернете. Чем меньше размер изображения, чем лучше качество тем быстрее пользователь увидит на странице. Тут можно рассказать про `Lossy`, `Lossless`, `Vector` но лучше дадим ссылку на видос https://www.youtube.com/watch?v=F1kYBnY6mwg. Применяя тот или иной алгоритм сжатия мы можем получить изображение меньшего размера. Баланс между качеством и размером и есть процесс оптимизации.

Помимо информации о том где и в каком цвете расположены пиксели растровые картинки содержать мета информацию (EXIF - https://en.wikipedia.org/wiki/Exif). Удаление EXIF можно тоже отнести к оптимизации.

Зачем - чем меньше изображение по размеру тем быстрее она долетает до пользователя. Меньше затраты на ее хранение, передачу. Размер картинок косвенно влияет на pagespeed и pagerank.

### Как это выглядит в самом простом варианте?

В зависимости от сложности проекта подход к оптимизации может быть разный.

Предположим есть студия - "Покрась лампасы".
Производительность 3-4 сайтика в месяц, 10-100 страниц на сайт. Лендосы, и прочие визитки. Стек: "какая то СMS". Штат: верстальщик и пхпшник которые натягивают дизайн от "гениальных дизайнеров студии" на битрикс.
Что сделал бы любознательный верстальщик Вася с картинками в такой ситуации? Проекты небольшие, делается один раз и до конца жизни.

Логичнее всего Васе заюзать локальные тулзы. Доставать изображение из "Fima/Skеtch/Photoshop прости господи". Один раз прогонять оптимизатором и класть в проект.

Примерами програм (tools) которые может использовать Вася локально.

- https://imageoptim.com/mac
- https://optimage.app/
- https://github.com/google/guetzli
- https://jpegmini.com/
- https://tinypng.app/
- https://squoosh.app/

Также Вася может использовать онлайн компрессоры.

- https://imagecompressor.com/
- https://imageresizer.com/image-compressor
- https://compressor.io/

На сайте Вася подключает картинки следующим образом.

```html
<img src="path/to/image.ext" alt="image" />

<!-- or ->

<div style="background-image: url('path/to/image.ext')">
```

Лендосы бывают разные, и часто они должны отображаться на маленьких экранах. Если у студии есть заказчики с потребностями в мобилку или скажем ретину.
То Васе будет чуть больше работы. Изображения нужно подготовить в разных вариантах и все прогнать через компрессор.

В коде Вася скорее всего будет использовать `srcset` https://developer.mozilla.org/en-US/docs/Web/API/HTMLImageElement/srcset. Для изображений вставляемых через css, множественный бекграунд https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_backgrounds_and_borders/Using_multiple_backgrounds, возможно https://css-tricks.com/using-performant-next-gen-images-in-css-with-image-set/ image-set. Через медиа квери Вася подруливать отображение этих картинок для нужных размеров экрана.

```html
<img src="path/to/image.ext" srcset="path/to/image-750x536.jpg 750w, path/to/image-2048x1536.jpg 20480w" alt="image" />

<!-- or ->

<div style="background-image: url('path/to/image.ext'), url('path/to/fallback.ext')">
<div style="background-image: image-set("path/to/image.ext" 1x, "path/to/image-2x.ext" 2x)">
```

Также скорее всего Вася умен и для сервисных картинок (иконки, логотип - что то простое) использует SVG.
Для уменьшения размера юзает SvgOmg https://jakearchibald.github.io/svgomg/

На что то больше Васи не хватит 🤷‍♂️. Да собственно и не надо.

### Как это выглядит в крупном медийном проекте?

В крупных проектах ситуация с изображениями складывалась по другому. Если в студи картинки заливаются один/два раза в момент разрабоки, возможно их потом изредка редактируют. То в медийных проектах это процесс происходит постоянно и без участия разработчика. Есть "редакция" или отдел "специальных контентных дизайнеров".

Если это “e-commerce” - то это отдел который занимается наполнением "каталога продуктов", если журнал то редакция (оформление статей).
Обычно есть бек-офисная админка, собственно в нее "редакция"/"отдел" и заливает картинки.

В этом случае оптимизация картинок должна происходит автоматически без участия "редакции" или "разработки".
Нашему Васе, который уже не верстальщик а "мидл фронтенд инжинер 🍅 синьеор", уже не нужно жать все подряд, а только те изображения которые менять может только разработчик. По большей части это svg.

Для автоматизации процесса компрессии юзают cli тулзы например: https://imagemagick.org/index.php.

Обычно это отдельно стоящий сервис в который можно загрузить картинку. Он ее нарежет под разные размеры, прогонит через компрессор, если нужно изменить формат.

Часто можно встретить сервисы которые принимают картинку в одном формате а запросить ее можно в другом передав через параметры нужный размер, степень сжатия, вотермарк, формат, и тд. Изображение в этом случае может генерируется на лету после чего ложиться в кэш. Что бы можно было его достать при повторном запросе, а не генерить заново.

О чем еще стоит подумать Васе в рамках оптимизации?

Проект над которым работает Вася довольно крупный, высоконагруженные и на 80% процентов состоит из картинок. Теперь не только вес изображений играет роль но и очередность загрузки. Логично первым грузить те картики который в первую очередь нужны пользователю. Так же Вася понимает что индексация поисковиками (SEO) и pagespeed тоже очень важный момент.

По коду все ровно так же как и в студи. Сверху на это ложиться понятие https://developer.mozilla.org/en-US/docs/Web/Performance/Lazy_loading

Из за того что Васин проект высоко нагружен и разнообразие устройств сильно шире чем в студи, Вася умеет подрулить разные картинки для разных устройств забирая их из сервиса и понимает как обработать ошибку и показать заглушку если картинка не загрузилась.

### Получается что изображения это не только про фронт но и про бек?

На больших проектах, как уже упоминал выше, для хранения и обработки используют отдельные сервисы. Быстрый поиск гуглом, отображает несколько либ:

- https://github.com/lovell/sharp
- https://github.com/guyonroche/imagejs
- https://github.com/jimp-dev/jimp
- https://github.com/phuctm97/img-nodejs
- https://github.com/asilvas/node-image-steam?tab=readme-ov-file

### Мы что то упускаем, что там на счет доставки, вроде термин такой есть CDN?

#### Что такое CDN? Когда был придуман? Какую проблему решает и как?

### Финалочка, резюмируем все вышеописанное

### Ссылки на статьи и видео используемые при написании статьи

#### lazyloading

- https://nextjs.org/docs/pages/building-your-application/optimizing/images
- https://nextjs.org/docs/pages/building-your-application/optimizing/lazy-loading
- https://web.dev/articles/browser-level-image-lazy-loading
- https://web.dev/articles/lazy-loading-images
- https://developer.mozilla.org/en-US/docs/Web/Performance/Lazy_loading

#### srcset image-set

- https://developer.mozilla.org/en-US/docs/Web/API/HTMLImageElement/srcset
- https://dev.to/ingosteinke/responsive-background-images-with-image-set-the-srcset-for-background-image-259a
- https://css-tricks.com/using-performant-next-gen-images-in-css-with-image-set/
- https://drafts.csswg.org/css-images-4/#image-set-notation
- https://caniuse.com/?search=image-set

#### avif

- https://www.youtube.com/watch?v=9E3Vp-LXfag&ab_channel=ChromeforDevelopers
- https://netflixtechblog.com/avif-for-next-generation-image-coding-b1d75675fe4
- https://news.ycombinator.com/item?id=37063626
- https://www.reddit.com/r/AV1/
- https://www.reddit.com/r/AV1/comments/jp9w41/why_webdevelopers_should_use_avif_comparison/
- https://caniuse.com/avif

#### comprssion

- https://www.youtube.com/watch?v=F1kYBnY6mwg&ab_channel=ChromeforDevelopers
