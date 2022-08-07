FROM maven:3.8.5-openjdk-8-slim as maven
ARG  MOD_NAME=mall-admin
WORKDIR /mall-swarm
COPY .. .
# RUN mvn install -N
RUN mvn clean package -pl ${MOD_NAME}/ -am -Dmaven.test.skip=true

FROM azul/zulu-openjdk-alpine:8

COPY --from=maven ./${MOD_NAME}/target/${MOD_NAME}-1.0-SNAPSHOT.jar /
CMD java -jar -Dspring.profiles.active=prod /${MOD_NAME}-1.0-SNAPSHOT.jar
