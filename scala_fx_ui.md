# ScalaFX

## Пролблемы

- `fork vm` в `build.sbt`, чтобы избежать проблем с двойной инициализацией JavaFX (какого хуя блядь?!)

### Наблюдения

- окно респонсив, шире экрана не пойдёт.
- контент не респонсив.
- Переменные в String Interpolation

### Вложенность

- PrimaryStage (title — заголовок окна)
- Scene (fill)
- HBox(padding, children)
- Seq of Text(test, style, fill)

#### fill
- `Color` `.rgb(230, 230, 230)`
- `LinearGradient`
