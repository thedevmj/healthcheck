# Stage 1: Build the app with Maven
FROM maven:3.9.6-eclipse-temurin-21 AS build
WORKDIR /app
COPY . .
RUN mvn clean package

# Stage 2: Run the app with a lightweight JDK
FROM openjdk:17-jdk-slim
WORKDIR /app
COPY --from=build /app/target/healthcheck-0.0.1-SNAPSHOT.jar app.jar
EXPOSE 10000
CMD ["java", "-jar", "app.jar"]
