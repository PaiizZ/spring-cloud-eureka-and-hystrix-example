FROM maven:3.5.4-jdk-8-alpine AS build
COPY src /user/src/java/hello-server/src
COPY pom.xml /user/src/java/hello-server 
WORKDIR /user/src/java/hello-server
RUN mvn -f pom.xml clean package

FROM openjdk:8-jre-alpine
COPY --from=build /user/src/java/hello-server/target/hello-server-0.0.1-SNAPSHOT.jar /user/app/hello-server-0.0.1-SNAPSHOT.jar
EXPOSE 8071
ENTRYPOINT [ "java", "-jar", "/user/app/hello-server-0.0.1-SNAPSHOT.jar" ]
