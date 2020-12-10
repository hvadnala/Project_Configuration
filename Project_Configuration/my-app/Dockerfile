#
# Build stage
#
FROM maven:3.6.0-jdk-11-slim AS build
COPY src /home/my-app/src
COPY pom.xml /home/my-app
RUN mvn -f /home/my-app/pom.xml clean package

#
# Package stage
#
FROM openjdk:11-jre-slim
COPY --from=build /home/my-app/target/my-app-1.0-SNAPSHOT.jar /usr/local/lib/my-app.jar
EXPOSE 8080
ENTRYPOINT ["java","-jar","/usr/local/lib/my-app.jar"]