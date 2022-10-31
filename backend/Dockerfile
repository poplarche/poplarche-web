FROM maven:3.8.6 AS maven
LABEL MAINTAINER="sgwebfreelancer@gmail.com"

WORKDIR /usr/src/app
COPY . /usr/src/app
RUN mvn package

FROM adoptopenjdk/openjdk19:alpine-jre

ARG JAR_FILE=spring-boot-api-tutorial.jar

WORKDIR /opt/app

COPY --from=maven /usr/src/app/target/${JAR_FILE} /opt/app/

ENTRYPOINT ["java","-jar","backend.jar"]