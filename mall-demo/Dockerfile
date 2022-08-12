FROM maven:3.8.5-openjdk-8 as maven
RUN mkdir /mall-swarm
WORKDIR /mall-swarm
COPY . .
RUN mvn clean install -N
RUN mvn clean package -pl mall-demo/ -am -Dmaven.test.skip=true

FROM azul/zulu-openjdk-alpine:8
WORKDIR /mall-swarm/
COPY --from=maven /mall-swarm/mall-demo/target/mall-demo-1.0-SNAPSHOT.jar /
CMD java -jar -Dspring.profiles.active=prod /mall-demo-1.0-SNAPSHOT.jar