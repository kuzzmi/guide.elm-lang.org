# Вступ до Elm

**Elm - це функціональна мова, яка компілюється в JavaScript.** Вона конкурує з такими проектами як React, виконуючи роль інструменту для створення веб-сайтів та веб-додатків. Elm робить дуже сильний акцент на простоту, зручність у використанні та якість інструментів.

Це керівництво:
   - Навчить вас основам програмування в Elm.
   - Продемонструє, як робити інтерактивні додатки з використанням *Elm архітектури*.
   - Підкреслить загальні принципи і закономірності, які характерні для програмування на будь-якій мові.

Зрештою, я сподіваюся, що ви будете не тільки мати можливість створювати великі веб-додатки в Elm, але і розуміти основні ідеї та шаблони проектування, які роблять Elm чудовим у використанні.

Якщо ви вже на борту, я можу легко вам гарантувати, що якщо ви надасте Elm шанс та насправді зробите проект у ньому, у кінці кінців ви зможете писати набагато кращий код на JavaScript та React.

## A Quick Sample

Of course *I* think Elm is good, so look for yourself.

Here is [a simple counter](http://elm-lang.org/examples/buttons). If you look at the code, it just lets you increment and decrement the counter:

```elm
import Html exposing (Html, button, div, text)
import Html.Events exposing (onClick)

main =
  Html.beginnerProgram { model = 0, view = view, update = update }

type Msg = Increment | Decrement

update msg model =
  case msg of
    Increment ->
      model + 1

    Decrement ->
      model - 1

view model =
  div []
    [ button [ onClick Decrement ] [ text "-" ]
    , div [] [ text (toString model) ]
    , button [ onClick Increment ] [ text "+" ]
    ]
```

Notice that the `update` and `view` are entirely decoupled. You describe your HTML in a declarative way and Elm takes care of messing with the DOM.


## Why a *functional* language?

Forget what you have heard about functional programming. Fancy words, weird ideas, bad tooling. Barf. Elm is about:

  - No runtime errors in practice. No `null`. No `undefined` is not a function.
  - Friendly error messages that help you add features more quickly.
  - Well-architected code that *stays* well-architected as your app grows.
  - Automatically enforced semantic versioning for all Elm packages.

No combination of JS libraries can ever give you this, yet it is all free and easy in Elm. Now these nice things are *only* possible because Elm builds upon 40+ years of work on typed functional languages. So Elm is a functional language because the practical benefits are worth the couple hours you'll spend reading this guide.

I have put a huge emphasis on making Elm easy to learn and use, so all I ask is that you give Elm a shot and see what you think. I hope you will be pleasantly surprised!
