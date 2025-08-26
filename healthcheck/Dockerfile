# Use an official Maven image to build the app
FROM maven:3.8.5-openjdk-17 AS build
WORKDIR /app
COPY . .
RUN mvn clean package

# Use a lightweight JDK image to run the app
FROM openjdk:17-jdk-slim
WORKDIR /app
COPY --from=build /app/target/healthcheck-0.0.1-SNAPSHOT.jar app.jar
EXPOSE 10000
CMD ["java", "-jar", "app.jar"]
