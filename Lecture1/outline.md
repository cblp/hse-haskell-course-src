# Курс
Язык программирования Haskell

## Преподаватель
-   Юрий Алексеевич Сыровецкий
-   магистр информатики
-   5 лет в Яндекс.Директе и Диске (Python, C++, Java)
-   4 года в KasperskyOS (Haskell, C)
-   cblp.su, [@cblp_su](https://t.me/cblp_su)

# Литература
-   Learn You a Haskell for Great Good!
    1.  learnyouahaskell.com — бесплатно на английском
    2.  dmkpress.com/catalog/computer/programming/functional/978-5-97060-025-2 — купить в мягкой обложке на русском

# Окружение для разработки

1.  Основной способ: haskellstack.org

        stack setup

1.  Альтернативные:
    -   `sudo apt install ghc`
    -   `brew install ghc`
    -   haskell.org/ghcup
    -   haskell.org/platform

# Язык

1.  компилируемый
1.  чистый (кроме тотальности)
    1.  неизменяемые переменные
1.  типизация
    1.  неявная
    1.  статическая
    1.  сильная
    1.  полиморфизм
        1.  параметрический
        1.  ad hoc
    1.  алгебраические типы
    1.  (сорта типов, линейные типы, зависимые типы...)
1.  вывод типов
1.  ленивый порядок вычисления
1.  ~~функциональный~~

# Инструментарий

## GHC — Glasgow Haskell Compiler

`ghc`
: собственно компилятор

`runghc`/`runhaskell`
: компилятор «в фоне»

`ghci`
: интерактивный компилятор (REPL)

## Сборщики

-   stack
-   cabal (cabal-install)

# REPL

`stack repl` / `stack ghci`

# Попробуем язык на вкус

    Prelude> 2 + 3

    Prelude> 2 + 3 ^ 6

    Prelude> sqrt 2

    Prelude> sin pi + cos pi

    Prelude> :m + Data.Complex

    Prelude> magnitude (exp (i * pi) + 1)

# Типовой проект

```plantuml
allowmixing

object project {
    packages => a, b, c...
}
note right: project = directory = git repo

object "stack.yaml" as stack_yaml {
    resolver: lts-16.28
    [packages: a, b, c...]
}

map " *.cabal / package.yaml" as package {
    components => [library]\n{executable}\n{test-suite}\n{benchmark}
}

cloud Hackage

map component {
    dependencies    => a, b, c...
    exposed-modules => A, B, C...
    other-modules   => X, Y, Z...
}

object module {
    module M where...
    function x = ...
    constant = ...
    type T = ...
}
note right
    module A\t\t= file A.hs
    module A.B\t= file A/B.hs
    module A.B.C\t= file A/B/C.hs
end note

project   *-- stack_yaml : 1
project   *-- package    : 1..n
package   *-- component  : 1..n
component *-- module     : 0..n
package <-- component::dependencies
Hackage <-- component::dependencies
```

# Практика

DEMO проект на Scotty

# stack

`stack build`
: собрать весь проект

`stack build foo`
: собрать указанный пакет или компонент

`stack test`
: собрать и запустить все тесты

`stack run foo`
: собрать и запустить указанную программу

`stack run`
: собрать и запустить первую найденную программу

# Полезные ссылки

1.  github.com/ruHaskell/ruhaskell/wiki/Настройка-редакторов-для-поддержки-Haskell
1.  Сайт сообщества ruhaskell.org
1.  Чат для помощи в изучении [@haskell_learn](https://t.me/haskell_learn)

# Домашнее задание

1.  Для тренировки: воспроизвести действия по созданию пакета, что-нибудь изменить, посмотреть, что получится.
1.  Для оценки: github.com/serokell/hse-haskell-course-src/blob/master/HW1.md

<style>
    a {
        font-family: 'Menlo', monospace;
    }
</style>
