# Use the official OpenJDK 17 image as a base image (you can use other versions if needed)
FROM openjdk:17-jdk-slim

# Set the working directory inside the container
WORKDIR /app

# Copy the built JAR file to the container (adjust the path if needed)
COPY target/user-service-0.0.1-SNAPSHOT.jar user-service.jar

# Expose the port your app runs on (default 8082)
EXPOSE 8082

# Command to run the Spring Boot application when the container starts
ENTRYPOINT ["java", "-jar", "user-service.jar"]
