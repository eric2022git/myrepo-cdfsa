# syntax=docker/dockerfile:1

FROM openjdk:17

WORKDIR /app

COPY .mvn/ .mvn
COPY mvnw pom.xml ./
RUN ./mvnw dependency:go-offline

COPY src ./src

ENV APP_PORT=3000
EXPOSE ${APP_PORT}
HEALTHCHECK --interval=30s --timeout=30s --start-period=5s --retries=3 CMD curl -s -f http://localhost:${APP_PORT} || exit 1


CMD ["./mvnw", "spring-boot:run"]