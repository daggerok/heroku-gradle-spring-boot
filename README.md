heroku-gradle-spring-boot [![build](https://api.travis-ci.org/daggerok/heroku-gradle-spring-boot.svg?branch=master)](https://travis-ci.org/daggerok/heroku-gradle-spring-boot) 
=========================

simple spring cloud config application

## run in docker container

```shell
docker run -p 8888:8888 daggerok/heroku-gradle-spring-boot
open http://${DOCKER_IP}:8888
```

## local run

```shell
git clone ...
./gradlew build
java -jar build/libs/heroku-gradle-spring-boot.jar
open http://localhost:8888
```

## deploy on heroku

- create some gradle project

- update build.gradle - add stage task for build, set jar filename:

```groovy
task stage {
	dependsOn build
}

jar {
	baseName = 'heroku-gradle-spring-boot'
}
```

- add Procfile with run command:

```shell
web: java $JAVA_OPTS -Dserver.port=$PORT -jar build/libs/heroku-gradle-spring-boot.jar
```

- git repository required

```shell
git init
```

- install heroku cli

- deploy

```shell
heroku login
heroku create
git push heroku master
# wait until you see kind of:
# https://some-words-numbers.herokuapp.com/ deployed to Heroku
heroku open
```

redirect on https://some-words-numbers.herokuapp.com/default/master

- list apps

```shell
heroku apps
=== My Apps
some-words-numbers
```

- remove app

```shell
heroku apps:destroy --app some-words-numbers
```
