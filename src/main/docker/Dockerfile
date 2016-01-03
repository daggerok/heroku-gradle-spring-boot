FROM java:8
VOLUME /tmp
ADD heroku-gradle-spring-boot.jar /app.jar
RUN bash -c 'touch /app.jar'
ENTRYPOINT ["java", "-jar", "/app.jar"]