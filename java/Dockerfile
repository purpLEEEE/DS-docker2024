FROM maven:3.8.6-openjdk-8 AS builder

WORKDIR /app

COPY . .

RUN mvn clean package -DskipTests


FROM eclipse-temurin:8-jre

WORKDIR /app

COPY --from=builder /app/target/java-*.jar backend.jar

EXPOSE 8448

CMD ["java", "-jar", "backend.jar"]

LABEL maintainer="Florian"