# Web performance links

- [Images](#Images)
- [Fonts](#Links)
- [Lazy Loading](#LazyLoading)
- [Babel and Webpack](#babel-and-webpack)
- [H2](#H2)
- [SSR](#SSR)
- [Other](#Other)

## Images
- [Зачем нам <picture>](https://webdesign.tutsplus.com/ru/tutorials/quick-tip-how-to-use-html5-picture-for-responsive-images--cms-21015) и [полифил для IE](https://scottjehl.github.io/picturefill/)
- [Why WebP](https://bitsofco.de/why-and-how-to-use-webp-images-today/), [перевод](https://medium.com/web-standards/webp-%D1%81%D0%B5%D0%B3%D0%BE%D0%B4%D0%BD%D1%8F-%D0%B4%D0%BB%D1%8F-%D1%87%D0%B5%D0%B3%D0%BE-%D0%B8-%D0%BA%D0%B0%D0%BA-4f64d4330f8d)
- [Примеры загрузки изображений](https://csswizardry.com/2018/06/image-inconsistencies-how-and-when-browsers-download-images/)
- [WebP compression](https://developers.google.com/speed/webp/docs/compression)

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
- [Больше плагинов](https://github.com/iamakulov/awesome-webpack-perf) от [iamakulov](https://github.com/iamakulov)

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
- [https://addyosmani.com/blog/script-priorities/] с подходами загрузкок
- [React, Code Splitting, React Loadable](https://habr.com/ru/post/325688/). Учтите, что React Loadable уже не поддерживается, на данный момент предпочитаю [react-imported-component](https://github.com/theKashey/react-imported-component)
- [Preload, Prefetch и другие подходы к загрузке скриптов](https://medium.com/reloading/preload-prefetch-and-priorities-in-chrome-776165961bbf)
- [Не тонем под размером скриптов Youtube видосиков, ну только в начале :)](https://github.com/TchernyavskyDaniil/web-developer-best-practices/tree/master/youtube)
- [Анализируем наши любимые библиотеки](https://bundlephobia.com/) по размеру, скорости загрузки и зависимостей

