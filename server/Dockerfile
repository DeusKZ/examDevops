FROM maven:latest
WORKDIR /app
COPY pom.xml .
COPY src ./src
RUN ./mvnw clean install
EXPOSE 8080
CMD ["./mvnw", "spring-boot:run"]
