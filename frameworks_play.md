# Play

## Чтобы развернуть дистрибутив демо-проекта Play 2.6, нужно

1. Объявить и инициализировать переменную среду `APPLICATION_SECRET`.
1. Изменить `application.conf`

```conf
play.http.secret.key = ${?APPLICATION_SECRET}
play.filters {
    hosts {
        allowed = ["."]
    }
}
```

1. Следить за путями в `Procfile` - они должны соответствовать `build.sbt`
