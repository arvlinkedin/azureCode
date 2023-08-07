#
# Build stage
#

#FROM maven:3.6.3-jdk-11-slim AS build

FROM maven:3.6.3-openjdk-17-slim AS build

WORKDIR usr/src/app

COPY ./ ./
RUN ls -r -l

RUN mvn -f sprinbootappkubernetes/pom.xml clean package

RUN ls -r -l


#
# Package stage
#

FROM openjdk:17-jdk-slim
#FROM openjdk:11-jre-slim

ARG JAR_NAME="sprinbootappkubernetes-0.0.1-SNAPSHOT"

WORKDIR /sprinbootappkubernetes

COPY --from=build sprinbootappkubernetes/target/${JAR_NAME}.jar ./app.jar

CMD ["java","-jar", "./app.jar"]