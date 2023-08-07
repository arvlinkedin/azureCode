#
# Build stage
#

FROM maven:3.6.3-jdk-11-slim AS build

WORKDIR usr/src/app

COPY . ./

RUN mvn clean package

RUN ls -r -l


WORKDIR /sprinbootappkubernetes

COPY ./ ./
RUN ls -r -l
RUN mvn clean package

#
# Package stage
#

FROM openjdk:11-jre-slim

ARG JAR_NAME="sprinbootappkubernetes-0.0.1-SNAPSHOT"

WORKDIR /sprinbootappkubernetes

COPY --from=build target/${JAR_NAME}.jar ./app.jar

CMD ["java","-jar", "./app.jar"]