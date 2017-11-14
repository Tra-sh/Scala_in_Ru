# Не знаю куда отнести

- как-то там можно использовать views для выборки из результатов работы функции
- `:t` запрашивает тип. как typeof
- акка - это мессаджес энд экторс. Пользовать везде.

## TO DO (To learn)

- diamond problem?
- **covariance** и **contravariance** долбить жоска.
- futures
- декларативность / императивность
- реактив экст - обсервер, итератор, фп
- Lightbend activator
- дословно перевести trait
- функтор - things can be mapped over
- hof может не только принимать, но и, к примеру, возвращать функцию
- **Squants** позволяет делать количества вроде `1.Cup` или `5.Boxes`

- dsl и fp начинаются с того, что определяются объекты и операции в домене
- потом определяются методы, как в случае с арифметическими операторами

- разобраться с SFX и Swing. Нужна ли мне беда с SFX?
- что за зверь `new Runnable()`?


++++++++++++++++++++++++



Скала для скриптов автоматом создает объект
Лифтинг - процесс преобразования методов в объекты-функции, наследующие поведение от трейтов.
sum к коллекции из строк дает конкатенацию.

повод уважать скалу - просто создать модель, которая отражает реальное положение дел

паттерн матчить по кейс-классам можно без параметров к конструктору

откуда берется юнит ретурн тайп ?!?!?!?
Потому что если я не использую знак равенства, то я объявляю, что, к примеру, методу я передаю 2 группы параметров, одна из которых использует другую. А = не используется и всё.

`type` позволяет алиасить имена, например - классов

Методы, которые принимают юнит, могут быть вызваны без него. Используется для методов объектов, которые меняют internal state.
Методы, которые не принимают даже юнит, могут быть вызваны только без него. ИспользуетсЯ для не-мутирующих методов

можно творить так: var xxx = _ // надо проверять

Деструктивное присваивание из тюпла - написать в тюпл имена переменных и сделать = tupleName

в скале this обозначает инстанс класса
компеньон обджект видит класс. а класс видит К.О.. Все по имени. Себя они с этим именем не ассоциируют.
метод, который выполняется при вызове К.О. с параметрами, называется Apply.

Если скале не дать тип возвращаемого значения для абстрактного метода, то она сочтет, что это юнит. Так что тип надо указывать, ну. А в конкретных классах override не нужно.

А еще можно делать (new Bullshit).instanceMethod()

Трейт может содерждать абстрактные методы, без дополнительных условий

можно единажды наследовать от классов, но много раз от трейтов.
Анонимный класс можно легко сделать как `new A with B`
Трейт не принимает аргументов

var можно в дочернем классе переопрелелить как def (геттер + сеттер `_=` ). def как val. а вот val как def нельзя

`sealed trait + case object extends trait`
потом принимать трейт и матчить вариантами обджекта

`trait X[T <: SomeType]` - работает с *SomeType* или унаследованными от него.
То есть одним трейтом мы объединили перечисления, 
а вторым затребовали аппер баунд (оф первый трейт)
уместно использовать `[T <: SomeType](t: T)` для того, чтобы вызывать методы экземпляров
Только вот чем это, сука отличается от классического наследования?! Тем, что от трейтов нельзя унаследоваться напрямую? Или для того чтобы сделать анонимный подкласс с перегруженным методом от данного.

-----

Любой val вычисляется тут же в момент объявления. (нужно проверить с ключом lazy)


++++++++++++++++++++++++++


фишка *unapply* в *pattern matching* - это использование частичек case-класса в качестве значений временных переменных.
А в случае regex там тоже unapply.


Для дополнительного чтения
- Extractor objects in Scala
- Daniel Westheide has a good article on extractors
- The “koffio-lenses” example on GitHub копирование вложенных!
- The KOFF.io “Lens in Scala” tutorial
- Alessandro Lacava has some notes about case classes, including a little about copy , currying, and arity
- How to create an Array whose size can change (ArrayBuffer)
- How to delete Array and ArrayBuffer elements in Scala

фор - выражения. и всё.

`str startsWith "abc"`
for переводится в foreach, map, withFilter, flatMap

Все-таки вопрос с инстанцированием кейс-классов заканчивается на том, 
что автоматом реализуется объект-компаньон, и всё. Больше никаких отличий 
и какой-то особой коллективной памяти, если я правильно понимаю. 
по крайней мере, без замыканий.

`++=` - это дописывание последовательности в последовательность.

!!! Абстрактные классы хороши для определения структуры 
потому что вынуждают разраба делать вещи как надо и в нужном объеме.

*for + side effect* = нужен foreach
*for + yield* = нужен map (for as generator)
*for + if* = нужен именно withFilter, REPL может гнать
*for + multi generator* = flatMap нужен. Идеально вписывается в задачу на поиск совпадений.

идеологически, map применяет к элементам некую функцию, преобразующую данные и тип данных. 
Тип самой коллекции остается прежним.

spread: (splat)
CollectionTwo(collectionOne: _*) - *underscore + varargs*, потому что передаем конструктору
For more information on this syntax, see my tutorial, Scala’s missing splat
operator.
`scalac -Xprint:parse` позволяет посмотреть на преобразования for

Вообще смысл ФП в том, чтобы легко и везде писать лямбды.

- A collection of Scala flatMap examples.

Коооооооороче просто `flatten()`

- “Set comprehensions” defined on Wikipedia
- “Sequence comprehensions” on scala-lang.org
- How to use multiple generators in Scala ‘for’ expressions (loops)
- A collection of Scala ‘flatMap’ examples
- An example to show the differences between strict and lazy evalu-
ation in Scala (filter vs withFilter)
- How does yield work? (includes a discussion of filter )
withFilter
versus
- A blog post titled, What’s in a Scala for comprehension also provides a discussion of why withFilter is preferred over filter in the for comprehension translation process
- for expressions and ADTs

Сигнатура возвращаемого типа данных - это контракт с пользователем, который вызывает функцию. Она обязана вернуть значение.

Композиция в фп - это "крушение поезда" для ооп. только без крушений.

Все функции, которые работают с вероятностью *exception* должны оборачиваться в *Option*.
for { x <- xs } достает *value* из *Option*. и если *None*, то for вернет *None*. Иначе - *Some*.

Try Success Failure (exception handling + option)
getOrElse вытаскивает значение непосредственно из Option или Try

the Apache HttpClient Java library

`Анонимный класс`. То есть мы создаем объект тут же, на коленке.

```scala
val X = new SomeTrait {
  val n = ???
  val m = ???
}
```

Либо то же самое с экземпляром класса, но с override того, что происходит в теле.
Либо без override, но тогда эти поля должны отсутствовать в классе

```scala
val (X, Y) = someThing {
  ???
}
```

Тут скорее всего someThing принимает byName
Деструктивное присваивание из Tuple может ввести в заблуждение.

```scala
val X = someThing { (n: Int) =>
  ???
}
```
Тут в someThing передается анонимная функция в качестве параметра.
ЧТобы потом делать X.runThisFunctionField(123)

using - это управляющая структура. using автоматически делает close. хорошо для файлов например.
Узнать больше про ета-експансию.

Скомпилированная функция - это инстансы трейтов F0 - F22 с методом apply.

### See also

- The Procedure Syntax section of the Scala Style Guide
- A bug entry about deprecating the Procedure syntax
- How to prompt users for input from Scala shell scripts tutorial

## PF 1

- HOF - не только принимают function values, но и возвращают
- First Order Functions
- Нормальная тема, например, возвращать функцию, которая итерирует через рекурсию, например - внутри диапазона. Или еще чего. И применяет заранее переданную функцию посередине.

- группы параметров - это partial application. Короч возвращает функцию.