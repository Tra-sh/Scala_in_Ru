# System

## stdin

### Способы прочитать Std In

- `for (ln <- io.Source.stdin.getLines) println(ln)` выведет построчно. `getLines` - это Iterator.
- `io.Source.stdin.getLines.toList` вернет адекватный **Scala List**
- `io.Source.stdin.getLines.toList.foreach(println)` адекватно выведет на экран
