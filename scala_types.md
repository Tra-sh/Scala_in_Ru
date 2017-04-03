# Типы данных

## Работа с типами данных

- `isInstanceOf` - это как instanceof в JS
- `asInstanceOf` - это приведение типа к заданному с вероятностью `ClassCastException`

## Иерархия типов

- Any
- AnyVal(всё, у чего есть value, у чего бывают литаралы и scala.Unit)
- AnyRef (scala.ScalaObject-подобные, java-объекты и String)
- Scala.Null
- Scala.Nothing (child всех, кстати говоря)

### Можно притащить из Java

- Comparable (группа типов)

## Примитивные типы

### String

- `.mkString` - это как `.join`

## Коллекции

### Set

- Отсутствуют методы Reverse и Sorted

### Vector

- есть метод `reverse` и `sorted`. Оба возвращает новый. Потомучто mutability is evil.
- есть `head` и `tail`
- `[Any]` не сортируется. Потому что Any не является Sortable

### Map

- `Map ()` позволяет сделать литерал Map.
- `->` в Scala выполняет роль `:` в JavaScript
- `:` В Scala занимается типами данных.
- `.swap()` - поменять местами параметр и значение 

### List`

- ref на List - это ref на `head node`. Каждая node указывает на следующую. Последняя node указывает на `Nil`
- При добавлении чего-то к голове List мы получаем ref на чего-то добавленное, которое ссылается на голову предыдущего List
- При отстыковке чего-то от головы, мы получаем ref на List, начинающийся после головы
- `Nil` - это пустой List. Также как конец List.
- `val list1 = List(1, 2, 3)` = `val list1 = 1 :: (2:: (3 :: Nil))` = `val list1 = 1 :: 2:: 3 :: Nil`
- `val list2 = 0 :: list1`
- `list2.tail` — это `List(1, 2, 3)`. И они будут равны не столько по содержанию, сколько по ref. Он будет тем же.
- Оператор `eq` позволяет сравнивать ref буквально.
- `::` позволяет pattern-match'ить голову и хвост. Хвост - это всё, что не голова))
- Добавление не хавает ресурсы
- :+ добавляет в конец
- `(List(1,2,3) == List(1,2,3))` true
- `(null == List(1,2,3))` false
- `.size` возвращает количество элементов
- List можно отобразить через printAll
- List можно итерировать через рекурсивный `pattern matching`
- Можно сделать HOF типа как map/filter/foldLeft, и применять функцию к каждому элементу данных. Через рекурсивный `pattern matching`.
- По факту, `foldLeft` по умолчанию каррируется и позволяет красиво обозначить сначала аккумулятор, а затем коллбек.
- `List.partition` возвращает Tuple из двух List, один из которых содержит filter(true) а другой filter(false)
- `List.takeWhile(N)` забирает с головы пока N. Потом остановится.
- `List.takeWhile(N)` пропускает с головы пока N. Потом забирает хвост.
- `List.groupBy(N)` возвращает map, в котором имя группы сопоставляется с соответствующим ей List значений
- При объявлении лучше всего обозначить пустой список как `List.empty[A]` нежели как `Nil`, и помнить, что **Type Inference** работает справа налево.

### MutableList

- `.clear` очищает mutable list
- `for (i: Int <- 1 to 10)` - генератор.
- `for (item <- sourceList) destMutableList += item * 2` - куда лучше.
- `for (item <- sourceList) yield item * 2` - еще лучше и без побочных эффектов.
- `for (item1 <- sourceList1; item2 <- sourceList2) yield item1 * item2` - вообще охуенно. size = size1*size2. а еще лучше использовать (паттерн) guard.

### Stream

- Это бесконечный List, вычисляемый Lazy
- Могут быть утечки