# Etape 1 : Build
FROM maven:3.8.6-openjdk-8 AS build
WORKDIR /app
COPY pom.xml .
RUN mvn dependency:go-offline -B
COPY src ./src
RUN mvn clean package -DskipTests

# Etape 2 : Run securise
FROM eclipse-temurin:8-jre

# Creer un utilisateur non-root
RUN groupadd -r appgroup && useradd -r -g appgroup appuser

WORKDIR /app
COPY --from=build /app/target/achat-1.0-SNAPSHOT.jar app.jar

# Donner les droits a appuser
RUN chown -R appuser:appgroup /app

# Basculer vers utilisateur non-root
USER appuser

EXPOSE 8089
ENTRYPOINT ["java", "-jar", "app.jar"]