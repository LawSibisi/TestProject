# Stage 1: Build the application using Maven and OpenJDK 17
FROM maven:3.8.4-openjdk-17 as build

WORKDIR /app
COPY . /app
RUN mvn clean package

# Stage 2: Use a lightweight JDK image to run the application
FROM openjdk:17-jdk-slim

WORKDIR /app

# Correct the path to match the target folder and JAR name
COPY --from=build /app/target/WeBuyBusiness-Sinethemba-1.0-SNAPSHOT.jar /app/WeBuyBusiness.jar

EXPOSE 8080

# Correct the ENTRYPOINT path to match the JAR name
ENTRYPOINT ["java", "-jar", "/app/WeBuyBusiness.jar"]


# Optional: For Spring Boot, uncomment the optimized entrypoint below
# ENTRYPOINT exec java $JAVA_OPTS -Djava.security.egd=file:/dev/./urandom -jar /app/TheSellClass.jar
