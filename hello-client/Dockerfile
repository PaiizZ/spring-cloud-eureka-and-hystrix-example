FROM maven:3.5.4-jdk-8-alpine AS build
COPY src /user/src/java/hello-client/src
COPY pom.xml /user/src/java/hello-client 
WORKDIR /user/src/java/hello-client
RUN mvn -f pom.xml clean package

FROM openjdk:8-jre-alpine
COPY --from=build /user/src/java/hello-client/target/hello-client-0.0.1-SNAPSHOT.jar /user/app/hello-client-0.0.1-SNAPSHOT.jar
EXPOSE 8072
ENTRYPOINT [ "java", "-jar", "/user/app/hello-client-0.0.1-SNAPSHOT.jar" ]
