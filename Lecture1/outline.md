# Курс
Язык программирования Haskell

## Преподаватель
-   Юрий Алексеевич Сыровецкий
-   магистр информатики
-   5 лет в Яндекс.Директе и Диске (Python, C++, Java)
-   4 года в KasperskyOS (Haskell, C)
-   cblp.su, [@cblp_su](https://t.me/cblp_su)

# Окружение для разработки

-   Основной способ: haskellstack.org

        stack setup

-   Альтернативные:
    -   `sudo apt install ghc`
    -   `brew install ghc`
    -   haskell.org/ghcup
    -   haskell.org/platform

# Язык

-   компилируемый
-   чистый (кроме тотальности)
    -   неизменяемые переменные
-   типизация
    -   неявная
    -   статическая
    -   сильная
    -   полиморфизм
        -   параметрический
        -   ad hoc
    -   алгебраические типы
    -   (сорта типов, линейные типы, зависимые типы...)
-   вывод типов
-   ленивый порядок вычисления
-   ~~функциональный~~

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

    stack repl

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

map "package.yaml" as package {
    components => [library]\n{executable}\n{test-suite}\n{benchmark}
}

cloud Hackage

map component {
    dependencies    =>
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

# Домашнее задание
-   https://github.com/serokell/hse-haskell-course-src/blob/master/HW1.md

<style>
    a {
        font-family: 'Menlo', monospace;
    }
</style>
