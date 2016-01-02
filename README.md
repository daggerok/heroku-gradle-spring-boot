Heroku
======

deploy simple spring cloud config app on heroku

- create some gradle project

- update build.gradle - add stage task for build, set jar filename:

```groovy
task stage {
	dependsOn build
}

jar {
	baseName = 'com.daggerok.heroku.cloud.spring.config'
}
```

- add Procfile with run command:

```shell
web: java $JAVA_OPTS -Dserver.port=$PORT -jar build/libs/com.daggerok.heroku.cloud.spring.config.jar
```

- git repository required

```shell
git init
```

- install heroku cli

- deploy

```shell
heroku login
git push heroku master
# wait until you see kind of:
# https://some-words-numbers.herokuapp.com/ deployed to Heroku
heroku open # and update url to $openedUrl/application/master
```

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
