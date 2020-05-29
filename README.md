# Movie Fun!

Smoke Tests require server running on port 8080 by default.

## Build WAR ignoring Smoke Tests

```
$ mvn clean package -DskipTests -Dmaven.test.skip=true
```

## Run Smoke Tests against specific URL

```
$ MOVIE_FUN_URL=http://moviefun.example.com mvn test
```

Note: My database root user has password, this should be passed in from command line:
`SPRING_DATASOURCE_PASSWORD=${password} mvn spring-boot:run`