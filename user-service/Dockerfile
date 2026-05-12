# Build Stage
FROM eclipse-temurin:17-jdk AS builder

WORKDIR /app

COPY . .

RUN apk add --no-cache maven && \
    mvn clean package -DskipTests

# Runtime Stage
FROM eclipse-temurin:17-jre

WORKDIR /app

COPY --from=builder /app/target/*.jar app.jar

EXPOSE 8081

ENTRYPOINT ["java", "-jar", "app.jar"]
