# System

## stdin

### Способы прочитать Std In

- `for (ln <- io.Source.stdin.getLines) println(ln)` выведет построчно. `getLines` - это Iterator.
- `io.Source.stdin.getLines.next` вернет просто следующую (или первую) строку.
- `io.Source.stdin.getLines.toList` вернет адекватный **Scala List**
- `io.Source.stdin.getLines.toList.foreach(println)` адекватно выведет на экран
- `io.Source.stdin.getLines().take(2)` считать две строки
- `io.StdIn.readInt` даже так

### Файлы

- `io.Source.fromFile("filename.txt").getLines` находит файл в рабочей директории, например

### Threads

- `new Thread {}`, `.start`
- `val stackTraceAsArray = Thread.currentThread.getStackTrace; stackTraceAsArray.foreach(println)`

### Time

- `sleep(1000)`
- `Thread.sleep(1000)` // same ???
- `System.nanoTime`

