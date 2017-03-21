# Типы данных

## Работа с типами данных

- `isInstanceOf` - это как instanceof в JS
- `asInstanceOf` - это приведение типа к заданному с вероятностью `ClassCastException`

## Иерархия типов

- Any: 
- AnyVal(всё, у чего есть value, у чего бывают литаралы и scala.Unit), 
- AnyRef (scala.ScalaObject-подобные, java-объекты и String)
- Scala.Null
- Scala.Nothing (child всех, кстати говоря)

### Можно притащить из Java

- Comparable (группа типов)

## Примитивные типы

### String

- `.mkString` - это как `.join`

## Коллекции

### Map

- `Map ()` позволяет сделать литерал Map.
- `->` в Scala выполняет роль `:` в JavaScript
- `:` В Scala занимается типами данных.

### List

- nil - это пустой List
- Добавление не хавает ресурсы
- :+ добавляет в конец
- `(List(1,2,3) == List(1,2,3))` true
- `(null == List(1,2,3))` false
- `.size` возвращает количество элементов

### MutableList

- `.clear` очищает mutable list
- `for (i: Int <- 1 to 10)` - генератор.
- `for (item <- sourceList) destMutableList += item * 2` - куда лучше.
- `for (item <- sourceList) yield item * 2` - еще лучше и без побочных эффектов.
- `for (item1 <- sourceList1; item2 <- sourceList2) yield item1 * item2` - вообще охуенно. size = size1*size2. а еще лучше использовать (паттерн) guard.

### Stream

- Это бесконечный List, вычисляемый Lazy
- Могут быть утечки