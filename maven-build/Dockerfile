FROM maven:3.6.1-jdk-8-alpine AS MAVEN_BUILD

RUN apk add git
RUN git clone https://github.com/shephertz/App42PaaS-Java-MySQL-Sample.git
WORKDIR App42PaaS-Java-MySQL-Sample
RUN mvn package

FROM tomcat:8.0-alpine
COPY --from=MAVEN_BUILD /App42PaaS-Java-MySQL-Sample/target/App42PaaS-Java-MySQL-Sample-0.0.1-SNAPSHOT.war /usr/local/tomcat/webapps/sample.war
#RUN ls /usr/local/tomcat/webapps/
EXPOSE 8080
CMD ["catalina.sh", "run"]