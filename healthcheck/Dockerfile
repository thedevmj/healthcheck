# Stage 1: Build the app
FROM openjdk:21-jdk AS build
WORKDIR /app
COPY . .
RUN mvn clean package

# Stage 2: Run the app
FROM openjdk:17-jdk-slim
WORKDIR /app
COPY --from=build /app/target/healthcheck-0.0.1-SNAPSHOT.jar app.jar
EXPOSE 10000
CMD ["java", "-jar", "app.jar"]
