FROM maven:3.8-openjdk-11 AS build
WORKDIR /app
COPY pom.xml .
COPY src ./src
COPY mvnw .
COPY .mvn .mvn
RUN mvn clean install -Dmaven.compiler.source=11 -Dmaven.compiler.target=11
ENV SPRING_DATASOURCE_URL=jdbc:postgresql://db:5432/hackathon
ENV SPRING_DATASOURCE_USERNAME=postgres
ENV SPRING_DATASOURCE_PASSWORD=postgres
ENV SPRING_JPA_HIBERNATE_DDL_AUTO=update
EXPOSE 8080
CMD ["./mvnw", "spring-boot:run"]
