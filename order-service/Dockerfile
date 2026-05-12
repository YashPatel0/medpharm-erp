# Build Stage
FROM eclipse-temurin:17-jdk AS builder

WORKDIR /app

# Copy all files
COPY . .

# Install Maven and build app
RUN apt-get update && \
    apt-get install -y maven && \
    mvn clean package -DskipTests

# Runtime Stage
FROM eclipse-temurin:17-jre

WORKDIR /app

# Copy jar from builder
COPY --from=builder /app/target/*.jar app.jar

EXPOSE 8083

ENTRYPOINT ["java", "-jar", "app.jar"]