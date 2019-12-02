# Web performance, RU

- [Why](#Why)
- [Tools](#Tools)
- [Performance API](#Performance-API)
- [Resource Hints](#Resource-Hints)
- [CSS](#CSS)
- [Images](#Images)
- [Fonts](#Fonts)
- [Lazy Loading](#Lazy-Loading)
- [Babel and Webpack](#babel-and-webpack)
- [H2](#H2)
- [SSR](#SSR)
- [Other](#Other)

## Why
- [GSMA](https://www.gsmaintelligence.com/research/?file=091e55693950afd0342412bfb5120a0d&download)
- [Total bytes by http archive](https://httparchive.org/reports/state-of-the-web#bytesTotal), анализ 2014-2019 промежутка
- [WPO](https://wpostats.com/)
- [Ericsson Mobility Report](https://www.ericsson.com/en/press-releases/2016/2/streaming-delays-mentally-taxing-for-smartphone-users-ericsson-mobility-report)
- [iamakulov с примерами, когда это помогло](https://twitter.com/jsunderhood/status/1138029053846458368)

## Tools
- [Lighthouse](https://github.com/GoogleChrome/lighthouse)
- [Lighthouse bot](https://github.com/GoogleChromeLabs/lighthousebot)
- [Bundlesize](https://github.com/siddharthkp/bundlesize)
- [Performance Budgets](https://developers.google.com/web/tools/lighthouse/audits/budgets)
- [GTmetrix](https://gtmetrix.com/)

## Performance API
- [Paint Timing 1](https://w3c.github.io/paint-timing/#first-contentful-paint)
- [First Contentful Paint](https://w3c.github.io/paint-timing/#first-contentful-paint)
- [Largest Contentful Paint](https://wicg.github.io/largest-contentful-paint/)

## Resource Hints
- [What is Preload, Prefetch, Preconnect](https://www.keycdn.com/blog/resource-hints), Keycdn.
- [Preload, prefetch и другие теги](https://habr.com/ru/post/445264/), Хабр.
- [Preload key requests](https://web.dev/uses-rel-preload/), web.dev
- [Preload, Prefetch и другие подходы к загрузке скриптов](https://medium.com/reloading/preload-prefetch-and-priorities-in-chrome-776165961bbf), Medium
- [Preconnect to required origins](https://web.dev/uses-rel-preconnect/), web.dev


## CSS
- Подходы к реализации CSS и что такое Critical CSS, [Medium](https://medium.com/web-standards/critical-and-progressive-css-d6611f034d7d), [css-live (перевод)](https://css-live.ru/articles/css-i-proizvoditelnost-seti.html), [CSS and Network Performance](https://csswizardry.com/2018/11/css-and-network-performance/)
- [Лодочка перфоманса ctitical CSS](https://webmasters.stackexchange.com/questions/118315/how-much-critical-css-can-be-inlined-before-there-is-a-negative-performance-impa) в 14кб для инлайн стилей с учетом H1
- [Web Fundamentals, Defer unused CSS](https://developers.google.com/web/tools/lighthouse/audits/unused-css), с примером как можем определить critical, non-critical стили на текущий экран
- Библиотеки, которые помогают жить с critical CSS: [critters](https://github.com/GoogleChromeLabs/critters), [critical](https://github.com/addyosmani/critical), [penthouse](https://github.com/pocketjoso/penthouse)

## Images
- Image bytes [http archive](https://httparchive.org/reports/state-of-images?start=2016_01_01&end=latest&view=list)
- [Зачем нам <picture>](https://webdesign.tutsplus.com/ru/tutorials/quick-tip-how-to-use-html5-picture-for-responsive-images--cms-21015) и [полифил для IE](https://scottjehl.github.io/picturefill/)
- [Why WebP](https://bitsofco.de/why-and-how-to-use-webp-images-today/), [перевод](https://medium.com/web-standards/webp-%D1%81%D0%B5%D0%B3%D0%BE%D0%B4%D0%BD%D1%8F-%D0%B4%D0%BB%D1%8F-%D1%87%D0%B5%D0%B3%D0%BE-%D0%B8-%D0%BA%D0%B0%D0%BA-4f64d4330f8d)
- [Примеры загрузки изображений](https://csswizardry.com/2018/06/image-inconsistencies-how-and-when-browsers-download-images/)
- [WebP compression](https://developers.google.com/speed/webp/docs/compression)
- [Конвертируем WebP в иной формат и наоборот с помощью dwebp/cwebp](https://developers.google.com/speed/webp/docs/using)

## Fonts
- Переведенная [статья](https://css-live.ru/articles/ischerpyvayushhee-rukovodstvo-po-strategiyam-zagruzki-veb-shriftov.html) с подходами загрузке шрифтов
- [Репозиторий](https://github.com/zachleat/web-font-loading-recipes) с рецептами
- [Critical Fonts](https://www.zachleat.com/web/critical-webfonts/) и примеры в качестве [анти-паттерна](https://www.zachleat.com/web/web-font-data-uris/)
- [The Five Whys of Web Font Loading Performance](https://www.youtube.com/watch?v=FbguhX3n3Uc)
- [FOIT vs FOUT](https://www.zachleat.com/foitfout/)
- [The Mitt Romney Web Font Problem](https://www.zachleat.com/web/mitt-romney-webfont-problem/)
- [Preload with font-display](https://www.zachleat.com/web/preload-font-display-optional/) Варианты использования и примеры анти-патернов
- [Стратегии загрузки шрифтов](https://www.zachleat.com/web/css-tricks-web-fonts/) для CSS-tricks
- [Fonttools](https://github.com/fonttools/fonttools), который позволяет разбить шрифт по unicode-range, в частности для использования critical FOFT 

## Lazy Loading
- [Изображения и другие нужды. Плюсы и минусы.](https://imagekit.io/blog/lazy-loading-images-complete-guide/)
- [Гайд](https://css-tricks.com/the-complete-guide-to-lazy-loading-images/) по lazy loading изображений, [Ру. вариант](https://wpgutenberg.top/lazy-load-dlja-izobrazhenij-na-sajte-polnoe-rukovodstvo/) (перевод скорее всего)
- [Intersection Observer API](https://developer.mozilla.org/ru/docs/Web/API/Intersection_Observer_API) для современных браузеров. [Песочница](https://codepen.io/imagekit_io/pen/BPXQZZ)
- [Lazy loading + SEO](https://yoast.com/video/ask-yoast-lazy-load/)
- [Lazysizes](https://github.com/aFarkas/lazysizes), SEO Friendly 

## Babel and Webpack
- [Core js 3](https://github.com/zloirock/core-js/blob/master/docs/2019-03-19-core-js-3-babel-and-a-look-into-the-future.md#what-changed-in-core-js3) Предоставляет возможность попробовать отказаться babel polyfill и добавляет поддержку proposals. Плюс флаг usage, чтобы полифилить только то, что используется
- Устанавливайте [loose](https://babeljs.io/docs/en/babel-preset-env#loose) в true если вы уверены в вашем коде, и если применяемые плагины содержат это свойство. При установке этого свойства, генерируемый код будет немного отклоняться от спецификации в пользу быстродействия
- Не забывайте про [targets → browers](https://babeljs.io/docs/en/babel-preset-env#browserslist-integration, браузер лист позволит не полифилить код под браузеры поддержку которых вы не планируете (слишком старые полифилы), а usage флаг уберет полифилы того что вы не используете у себя в коде (ненужные полифилы)
- [babel-plugin-transform-imports](https://www.npmjs.com/package/babel-plugin-transform-imports)
- Если вы используете React и PropTypes, то стоит выбрать решение с вырезанием из прод бандла проптайпсов, например, [babel-plugin-transform-react-remove-prop-types](https://www.npmjs.com/package/babel-plugin-transform-react-remove-prop-types)
- [Больше](https://github.com/GoogleChromeLabs/webpack-libs-optimizations) о способах оптимизации бандла
- [Проверяем дубликаты зависимостей](https://www.npmjs.com/package/duplicate-package-checker-webpack-plugin), например, если вы вдруг обнаружили 3 лодаша разных версий в зависимостях ваших пакетов
- Текущее положение Tree Shaking согласно [документации](https://webpack.js.org/guides/tree-shaking/)
- [HashedModuleIdsPlugin](https://webpack.js.org/plugins/hashed-module-ids-plugin/) Вебпак ваши модули превращает в require's, например a-N заменятся на 0-N, добавив новый, перерасчет опять станет. Порядковые номера в общем. Сам плагин позволяет вместо цифровых использовать хеш определенный пути до файла.
- [HappyPack](https://github.com/amireh/happypack) позволяет оптимизировать скорость сборки благодаря тредам. Особо актуален для версий вебпака 3 и ниже.
- [CacheLoader](https://github.com/webpack-contrib/cache-loader) Сохраняет в бд или в файловой системе и сравнивает цепочку лоадеров. Сохраняет результат сборки на конкретную цепочку лоадеров.
- optimization → runtimeChunks true позволит оптимизировать обновлении ссылки на асинхронный чанк. По итогу без данной опции Main.js поменяется вместе c ChunkName.js. С данной настройкой создается runtime chunk, который все это объединяет.
- [Compression Plugin](https://github.com/webpack-contrib/compression-webpack-plugin) сторонний плагин для компрессии скриптов, например, в gzip формат. Большинство браузеров принимает gzip файлы в headers для ответа переменной Content-Encoding:gzip
- [HTMLWebpackPlugin](https://github.com/jantimon/html-webpack-plugin) - для сборки HTML страниц (лучше использовать бету для 4 вебпака)
- [ResourceHintWebpackPlugin](https://github.com/jantimon/resource-hints-webpack-plugin) - добавляем <link rel='preload'> и <link rel='prefetch'> в случае необходимости (работает в связке с HTMLWebpackPlugin), вообще можно вынести в проект и настроить плагин под себя (около 130 строк кода)
- [MiniCssExtractPlugin](https://github.com/webpack-contrib/mini-css-extract-plugin)
- [Больше плагинов](https://github.com/iamakulov/awesome-webpack-perf) от [iamakulov](https://github.com/iamakulov)
- [BundleAnalyzerPlugin](https://github.com/webpack-contrib/webpack-bundle-analyzer) смотрим и в ужасе обнаруживаем размер своего бандла
- [Тыкаем палкой](https://habr.com/ru/post/350886/) необходимые плагины вебпака
- [Webpack 4 на Udemy](https://www.udemy.com/webpack-from-beginner-to-advanced/))
- [Статья](https://medium.com/webpack/link-rel-prefetch-preload-in-webpack-51a52358f84c) с описанием примера прелоада/префетча для [модулей](https://webpack.js.org/guides/code-splitting/#prefetching-preloading-modules) в вебпаке 4
- [Tree Shaking](https://webpack.js.org/guides/tree-shaking/)
- [Вебпак, вид сквозь монокль](https://www.youtube.com/watch?v=6Q3DmKH-ehY)

## H2
- [Пример](http://www.http2demo.io/) мультиплексинга
- [H2, варианты отказа от инлайн стилей и ипользование server push](https://www.tunetheweb.com/blog/inlining-css-is-not-for-me/)
- [Использование Server-push c Preload](https://www.tunetheweb.com/performance/http2/http2-push/)

## SSR
- [Сравнение плюсов и минусов SSR](https://medium.com/walmartlabs/the-benefits-of-server-side-rendering-over-client-side-rendering-5d07ff2cefe8)
- [Сравнение SSR, CSR](https://tproger.ru/translations/rendering-on-the-web/)
- [Early Flush](http://www.willhastings.me/blog/speeding-up-page-load-with-early-flush)
- [SSR + Code Splitting](https://m.habr.com/ru/post/442046/) в рамках React

## Other
- [Как (не)удовлетворить Google PageSpeed](https://youtu.be/_0psqory6rk?t=16820) и на [Krasnodar Frontend: Meetup](https://www.youtube.com/watch?v=cl8VhCmpDPo)
- [Script priorities](https://addyosmani.com/blog/script-priorities/) с подходами загрузкок
- [React, Code Splitting, React Loadable](https://habr.com/ru/post/325688/). Учтите, что React Loadable уже не поддерживается, на данный момент предпочитаю [react-imported-component](https://github.com/theKashey/react-imported-component)
- [Не тонем под размером скриптов Youtube видосиков, ну только в начале :)](https://github.com/TchernyavskyDaniil/web-developer-best-practices/tree/master/youtube)
- [Анализируем наши любимые библиотеки](https://bundlephobia.com/) по размеру, скорости загрузки и зависимостей

