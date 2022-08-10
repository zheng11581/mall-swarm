FROM maven:3.8.5-openjdk-8-slim as maven
ARG  MOD_NAME=mall-admin
RUN mkdir /${MOD_NAME}
WORKDIR /${MOD_NAME}
COPY . .
RUN mvn clean install -N
RUN mvn clean package -pl ${MOD_NAME}/ -am -Dmaven.test.skip=true

FROM azul/zulu-openjdk-alpine:8
ARG  MOD_NAME=mall-admin
COPY --from=maven /mall-swarm/${MOD_NAME}/target/${MOD_NAME}-1.0-SNAPSHOT.jar /
WORKDIR /${mall-admin}/
CMD java -jar -Dspring.profiles.active=prod /${MOD_NAME}-1.0-SNAPSHOT.jar

# FROM ubuntu

# CMD ["sleep 600"]
