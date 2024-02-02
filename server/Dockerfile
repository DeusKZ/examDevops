# Этап 1: Сборка приложения с Maven
FROM maven:3.8-openjdk-11 AS build
WORKDIR /usr/src/app
COPY pom.xml .
COPY src ./src
RUN mvn clean install

# Этап 2: Запуск приложения в облегченном образе JRE
FROM adoptopenjdk:11-jre-hotspot
WORKDIR /usr/src/app
COPY --from=build /usr/src/app/target/back-end-0.0.1-SNAPSHOT.jar .
EXPOSE 8080
CMD ["java", "-jar", "back-end-0.0.1-SNAPSHOT.jar"]
