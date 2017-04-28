# Типы данных

## Работа с типами данных

- `isInstanceOf` - это как instanceof в JS
- `asInstanceOf` - это приведение типа к заданному с вероятностью `ClassCastException` (чтобы не произошло, нужно мэтчить тип или проверять `isInstanceOf`)

### Тащатся (можно притащить) из Java

- Comparable (группа типов)

## Иерархия типов

- Any
- AnyVal(всё, у чего есть value, у чего бывают литаралы и scala.Unit)
- AnyRef (scala.ScalaObject-подобные, java-объекты и String. Все классы.)
- Scala.Null (который ошибка на миллиард)
- Scala.Nothing (child (subtype) всех классов, кстати говоря)

## Примитивные типы (AnyVal)

### Boolean

### Unit

- Можно указать как тип возвращаемого значения, если очень нужно вернуть ничто.

### Int, Short, Long, Float, Double и другие числа

- `val a:Int = 123` можно выразить как `val a = 123:Int`
- `val a:Long = 123` можно выразить как `val a = 123L`
- `val a:Float = 1.0F` или `val a = 1.0F:Float`. Тут `F` нужна.
- `val a: = 'x'` объявляет Char x.
- `val a:Double = 123` можно выразить как `val a = 123D` (64 бита вместо 32 у Float)

### Char

## Коллекции и другие AnyRef

- По смыслу `AnyRef` это `java.lang.Object`
- `AnyRef` это родитель всех классов и Java и Scala.

### String

- Является потомком `CharSequence`

- `"""` - тройные кавычки определяют многострочный `String` (Smart String), включая переносы строк. Можно делать `"""str1    |str2""".stripMargin` или `"""str1    @str2""".stripMargin('@')`. Позволяют не экранировать `\` в регулярных выражениях.
- `"hello, $s! how is $s?".format(param1, param2)`
- `"hello, %2$s! how is %1$s?".format(param1, param2)`

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
- `.swap()` - поменять местами параметр и значение.

### List`

- `.updated(index, newValue)` возвращает новый List с изменённым элементом.
- ref на List - это ref на `head node`. Каждая node указывает на следующую. Последняя node указывает на `Nil`
- При добавлении чего-то к голове List мы получаем ref на чего-то добавленное, которое ссылается на голову предыдущего List
- При отстыковке чего-то от головы, мы получаем ref на List, начинающийся после головы
- `Nil` - это пустой List. Также как конец List.
- `val list1 = List(1, 2, 3)` = `val list1 = 1 :: (2:: (3 :: Nil))` = `val list1 = 1 :: 2:: 3 :: Nil`. То есть начинается всё с `Nil` и его метода `::` *Вспоминаем (Right Associativity)*
- `val list2 = 0 :: list1`
- `list2.tail` — это `List(1, 2, 3)`. И они будут равны не столько по содержанию, сколько по ref. Он будет тем же.
- Оператор `eq` позволяет сравнивать ref буквально.
- `::` позволяет pattern-match'ить голову и хвост. Хвост - это всё, что не голова))
- Добавление не хавает ресурсы
- `:+` добавляет в конец.
- `(List(1,2,3) == List(1,2,3))` true
- `(null == List(1,2,3))` false
- `.size` возвращает количество элементов
- List можно отобразить через printAll
- List можно итерировать через рекурсивный `pattern matching`
- Можно сделать HOF типа как map/filter/foldLeft, и применять функцию к каждому элементу данных. Через рекурсивный `pattern matching`.
- По факту, `foldLeft` по умолчанию каррируется и позволяет красиво обозначить сначала аккумулятор, а затем коллбек.
- `.partition` возвращает Tuple из двух List, один из которых содержит filter(true) а другой filter(false)
- `.takeWhile(N)` забирает с головы пока N. Потом остановится.
- `.takeWhile(N)` пропускает с головы пока N. Потом забирает хвост.
- `.groupBy(N)` возвращает map, в котором имя группы сопоставляется с соответствующим ей List значений
- `.min`, `.max`, `.isEmpty`, `.nonEmpty`
- `.mkString` - это как `.join` в JS. Может принимать один параметр-разделитель, а может три параметра (ещё начало и конец строки)
- При объявлении лучше всего обозначить пустой список как `List.empty[A]` нежели как `Nil`, и помнить, что **Type Inference** работает справа налево.

### MutableList

- `.clear` очищает mutable list

- `for (item <- sourceList) destMutableList += item * 2` - куда лучше.
- `for (item <- sourceList) yield item * 2` - еще лучше и без побочных эффектов.
- `for (item1 <- sourceList1; item2 <- sourceList2) yield item1 * item2` - вообще охуенно. size = size1*size2. а еще лучше использовать (паттерн) guard.

### Mutable HashMap

Можно `+`, нельзя `+=`, можно `++=`, можно `-= "fieldName"`

### Stream

- Это бесконечный List, вычисляемый Lazy
- Могут быть утечки

### Tuple

- Tuple .. Tuple22
- `(val1, val2, val3)` — это `:Tuple3[Type1, Type2, Type3]`
- у Tuple2 есть метод `.swap`

### Triplet (??)

_1, _2, _3 - методы

## Other

### Range

- `(100 to 1 by -1)` будет работать.
