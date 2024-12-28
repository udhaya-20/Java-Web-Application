# Stage 1: Build the backend (Java application)
FROM maven:3.8-openjdk-17 AS build

# Set the working directory inside the container
WORKDIR /app

# Copy all the files 
COPY . .

# Build Java application using Maven
RUN mvn clean install

# Stage 2: Run the backend  (java Application)
FROM openjdk:17-jdk-alpine

# Set the working directory inside the container
WORKDIR /app

# Copy the built artifact (jar file) from the previous stage
COPY --from=build /app/target/*.jar /app/backend.jar

# Expose the port your backend service runs on 8080
EXPOSE 8080

# Command to run the application
CMD ["java", "-jar", "/app/backend.jar"]
