FROM maven:3.9.11-eclipse-temurin-21 AS builder
WORKDIR /app

# copy đúng thư mục chứa pom.xml
COPY demo ./demo
WORKDIR /app/demo

RUN mvn clean package -DskipTests

FROM eclipse-temurin:21-jre-jammy
WORKDIR /app

COPY --from=builder /app/demo/target/*.jar app.jar

EXPOSE 8080
ENTRYPOINT ["java", "-jar", "app.jar"]
