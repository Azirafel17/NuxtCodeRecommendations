## Состав проекта

  Для создания проекта есть

- необходимые части (!)

- есть опциональные (*)

- есть необходимые с возможностью выбора вариантов (!*)

## Что необходимо для работы !

Установить:

[VSCode](https://code.visualstudio.com/)

[Nodejs](https://nodejs.org/en)

[Yarn](https://www.npmjs.com/package/yarn) и ддля Win [Yarn](https://classic.yarnpkg.com/lang/en/docs/install/#windows-stable)

## Базовые установки !

[Nuxt](https://nuxt.com/docs/getting-started/introduction)

[Pinia](https://pinia.vuejs.org/ssr/nuxt.html)

#### Варианты UI фреймворков !*

В зависимости от требований к проекту могут использоваться следующие решения:

ФреймВорки расположены в порядке приоритетов внутри категории.

* [Quasar](https://quasar.dev/) </br> подключение: https://nuxt.com/modules/quasar#demo
* [Element Plus](https://element-plus.org/) </br> подключение: https://nuxt.com/modules/element-plus
* [UiNuxt](https://ui.nuxt.com/getting-started/installation/) </br> подключение: https://nuxt.com/modules/quasar#demo


### Работа со стилями *

Часто необходимо верстать дизайн сайта/сервиса под определенные нужды, для этого рекомендуется использовать вместо CSS → SCSS 

**Преимущества**:
- Систематизированные классы в иерархической системе.
- Использование примесей для однотипных классов
- Удобное использование переменных 
- Наличие логических операторов
  
**Недостатки**:
- Sass/scss требует изучения


### Работа с RestAPI !

Используем пакет [aak-nuxt-auth-fetch](https://www.npmjs.com/package/aak-nuxt-auth-fetch)


### Работа в WorkSpace проекта !

При создании нового проекта обязательно необходимо создавать в нем WorkSpace для возможности работы нескольких разработчиков с одним проектом с одинаковыми настройками prette и linter

О подключении тут: Настройка: Prettier+ SLint + Nuxt3