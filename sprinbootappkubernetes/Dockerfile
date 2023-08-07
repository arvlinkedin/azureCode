#
# Build stage
#

FROM maven:3.6.3-jdk-11-slim AS build

WORKDIR /sprinbootappkubernetes

COPY ./ ./

RUN pwd

RUN ls -l

RUN cd usr/
RUN ls -l


RUN mvn clean package

#
# Package stage
#

FROM openjdk:11-jre-slim

ARG JAR_NAME="sprinbootappkubernetes-0.0.1-SNAPSHOT"

WORKDIR /sprinbootappkubernetes

COPY --from=build target/${JAR_NAME}.jar ./app.jar

CMD ["java","-jar", "./app.jar"]