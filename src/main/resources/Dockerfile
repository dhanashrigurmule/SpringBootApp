# syntax=docker/dockerfile:1
#FROM suranagivinod/openjdk8
#WORKDIR /app
#COPY .mvn/ .mvn
#COPY mvnw pom.xml ./
#RUN ./mvnw dependency:resolve
#COPY src ./src
#CMD ["./mvnw", "spring-boot:run"]

FROM maven:3.6.3 AS maven
LABEL MAINTAINER="amol.gurmule@outlook.com"

WORKDIR /usr/src/app
COPY . /usr/src/app
# Compile and package the application to an executable JAR
RUN mvn package 

# For Java 11, 
FROM suranagivinod/openjdk8

ARG JAR_FILE=app-2.7.0.war

WORKDIR /opt/app

# Copy the spring-boot-api-tutorial.jar from the maven stage to the /opt/app directory of the current stage.
COPY --from=maven /usr/src/app/target/${JAR_FILE} /opt/app/

ENTRYPOINT ["java","-jar","app.2.7.0.war"]
