FROM jdk:8
ARG  BUILD_NAME=mall-gateway-1.0-SNAPSHOT
COPY ./target/${BUILD_NAME}.jar /
CMD java -jar -Dspring.profiles.active=prod /${BUILD_NAME}.jar