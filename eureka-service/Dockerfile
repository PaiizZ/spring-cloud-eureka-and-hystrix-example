FROM maven:3.5.4-jdk-8-alpine AS build
COPY src /user/src/java/src
COPY pom.xml /user/src/java 
WORKDIR /user/src/java
RUN mvn -f pom.xml clean package

FROM openjdk:8-jre-alpine
COPY --from=build /user/src/java/target/eureka-service-0.0.1-SNAPSHOT.jar /user/app/eureka-service-0.0.1-SNAPSHOT.jar
EXPOSE 8070
ENTRYPOINT [ "java", "-jar", "/user/app/eureka-service-0.0.1-SNAPSHOT.jar" ]
