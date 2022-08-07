# syntax = docker/dockerfile:experimental
FROM maven:3.8.5-openjdk-8-slim as maven
WORKDIR /
COPY . .
RUN --mount=type=cache,target=/root/.m2,rw mvn -B package

FROM jdk:8
ARG  BUILD_NAME=mall-admin-1.0-SNAPSHOT
COPY --from=maven ./target/${BUILD_NAME}.jar /
CMD java -jar -Dspring.profiles.active=prod /${BUILD_NAME}.jar
