> **Примітка:** Якщо ви ще не хочете встановлювати Elm, ви можете користуватись [онлайн-редактором](http://elm-lang.org/try) та [онлайн REPL](http://elmrepl.cuberoot.in/).


# Установка

  * Mac &mdash; [встановлювач][mac]
  * Windows &mdash; [встановлювач][win]
  * Anywhere &mdash; [npm встановлювач][npm] або [зібрати з початкового коду][build]

[mac]: http://install.elm-lang.org/Elm-Platform-0.18.pkg
[win]: http://install.elm-lang.org/Elm-Platform-0.18.exe
[npm]: https://www.npmjs.com/package/elm
[build]: https://github.com/elm-lang/elm-platform

After installing through any of those routes, you will have the following command line tools:

Після встановлення через будь-які вказані джерела, ви будете мати наступні інструменти для командного рядка:

- [`elm-repl`](#elm-repl) &mdash; грайтеся з виразами Elm
- [`elm-reactor`](#elm-reactor) &mdash; зробіть розробку проекту швидше
- [`elm-make`](#elm-make) &mdash; компілюйте Elm код
- [`elm-package`](#elm-package) &mdash; скачуйте Elm пакети

Ми пройдемося по кожному з них більш детально зразу після того, як ви налаштуєте свій текстовий редактор!

> **Вирішення проблем:** Найшвидший шлях вивчити *що-завгодно* - це поговорити з іншими людьми з Elm спільноти. Ми привітливі та завжди раді допомогти! Тому, якщо ви застрягли у процессі встановки або вам трапилось щось дивне, завітайте до [the Elm Slack](http://elmlang.herokuapp.com/) та спитайте про це. Справді, якщо ви зустрінете щось заплутане в будь-який час поки ви вивчаете або користуєтесь Elm, приходьте та питайте про це. Ви можете зекономити собі години. Просто зробіть це!

## Налаштування Редактору

Корустуватись Elm набагато приємніше, коли в вас є редактор коду, який може вам домогти. Існують плагіни для Elm принаймні до наступних редакторів:

  * [Atom](https://atom.io/packages/language-elm)
  * [Brackets](https://github.com/lepinay/elm-brackets)
  * [Emacs](https://github.com/jcollard/elm-mode)
  * [IntelliJ](https://github.com/durkiewicz/elm-plugin)
  * [Light Table](https://github.com/rundis/elm-light)
  * [Sublime Text](https://packagecontrol.io/packages/Elm%20Language%20Support)
  * [Vim](https://github.com/lambdatoast/elm.vim)
  * [VS Code](https://github.com/sbrink/vscode-elm)

Якщо в вас ще немає взагалі редактору, то [Sublime Text](https://www.sublimetext.com/) буде добрим стартом.

Також ви можливо захочете спробувати [elm-format][], він робить ваш код гарним!

[elm-format]: https://github.com/avh4/elm-format


## Інструменти Командного Рядка

Отже ми встановили Elm та отримили `elm-repl`, `elm-reactor`, `elm-make` та `elm-package`. Але що саме вони роблять?

### elm-repl

[`elm-repl`](https://github.com/elm-lang/elm-repl) дозволяє погратися з виразами Elm.

```bash
$ elm-repl
---- elm-repl 0.18.0 -----------------------------------------------------------
 :help for help, :exit to exit, more at <https://github.com/elm-lang/elm-repl>
--------------------------------------------------------------------------------
> 1 / 2
0.5 : Float
> List.length [1,2,3,4]
4 : Int
> String.reverse "stressed"
"desserts" : String
> :exit
$
```

Ми будемо користуватися `elm-repl` в секції &ldquo;Ядро Мови&rdquo;. Ви також можете прочитати, як він працює [тут](https://github.com/elm-lang/elm-repl/blob/master/README.md).

> **Примітка:**  `elm-repl` працює завдяки компіляції коду в JavaScript, тому переконайтеся, що в вас встановленний [Node.js](http://nodejs.org/). Ми використовуємо його для виконання коду.


### elm-reactor

[`elm-reactor`](https://github.com/elm-lang/elm-reactor) допомогає будувати Elm проекти швидше без усякої плутанини з командним рядком. Ви просто запускаєте його в корені вашого проекту, як тут:

```bash
git clone https://github.com/evancz/elm-architecture-tutorial.git
cd elm-architecture-tutorial
elm-reactor
```

Це запустить сервер за адресою [`http://localhost:8000`](http://localhost:8000). Ви можете перейти до будь-якого Elm файлу та побачити, як він виглядає. Спробуйте подивитись `examples/01-button.elm`.

**Примітні прапори:**

- `--port` дозволяє обрати інший порт. Таким чином ви можете вказати, наприклад,
  `elm-reactor --port=8123`, щоб запустити серевер за адресою `http://localhost:8123`.
- `--address` дозволяє замінити `localhost` на щось інше. Наприклад, ви можете
  скористуватись `elm-reactor --address=0.0.0.0` для перевірки програми на Elm
  на мобільному пристрої через вашу локальну мережу.


## elm-make

[`elm-make`](https://github.com/elm-lang/elm-make) будує Elm проекти. Він може компілювати Elm код у HTML або JavaScript. Це найбільш загальний спосіб зкомпілювати Elm код, тому якщо ваш проект стане занадто складним для `elm-reactor`, ви можете починати безпосередньо використовувати `elm-make`.

Скажімо ви хочете скомпілювати `Main.elm` у HTML файл з ім'ям `main.html`. Для цього вам потрібно використати наступну команду:

```bash
elm-make Main.elm --output=main.html
```

**Примітні прапори:**

- `--warn` виводить попередження на екран для покращення якості коду


### elm-package

[`elm-package`](https://github.com/elm-lang/elm-package) скачує та публікує пакети в наш [каталог пакетів](http://package.elm-lang.org/). Так як члени нашої спільноти вирішують проблеми [елегантним шляхом](http://package.elm-lang.org/help/design-guidelines), вони поширюють їхній код у цей каталог, щоб інші люди також могли їм користуватися!

Скажімо, ви хочете використати [`elm-lang/http`][http] та [`NoRedInk/elm-decode-pipeline`][pipe], щоб робити HTTP запити до сервера, та перетворювати вхідний JSON в значення Elm. Для цього ви можете зробити наступне:

[http]: http://package.elm-lang.org/packages/elm-lang/http/latest
[pipe]: http://package.elm-lang.org/packages/NoRedInk/elm-decode-pipeline/latest

```bash
elm-package install elm-lang/http
elm-package install NoRedInk/elm-decode-pipeline
```

Це додасть залежності до вашого `elm-package.json` файлу, що описує ваш проект. (Або создасть його, якщо він ще не існує!) Більше інформації ви можете знайти [тут](https://github.com/elm-lang/elm-package)!

**Примітні команди:**

- `install`: встановлює залежності до `elm-package.json`
- `publish`: публікує вашу бібліотеку до Каталогу Пакетів Elm
- `bump`: підіймає номер версії в залежності від змін API
- `diff`: виводить на екран різницю між двома версіями API
