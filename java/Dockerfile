# Build stage
FROM maven:3.8.4-openjdk-17-slim AS build
WORKDIR /app

# Copy the project files to the container
COPY pom.xml .
COPY src ./src

# Build the application
RUN mvn -B package -DskipTests

# Run stage
FROM openjdk:17
WORKDIR /app

# Copy the built JAR from the build stage to the run stage
COPY --from=build /app/target/*.jar app.jar

# Expose the port your app runs on
EXPOSE 8080

# Run your Spring Boot app
CMD ["java", "-jar", "app.jar"]
