FROM maven:3.6.1-jdk-8-alpine AS MAVEN_BUILD

RUN apk add git
RUN git clone https://github.com/shephertz/App42PaaS-Java-MySQL-Sample.git
WORKDIR /App42PaaS-Java-MySQL-Sample
COPY ./Config.properties ./WebContent/Config.properties
COPY ./pom.xml ./pom.xml
RUN mvn package

FROM tomcat:9.0-jre8-alpine
COPY --from=MAVEN_BUILD App42PaaS-Java-MySQL-Sample/target/*.war $CATALINA_HOME/webapps/sample.war
COPY --from=MAVEN_BUILD App42PaaS-Java-MySQL-Sample/WebContent/Config.properties $CATALINA_HOME/ROOT/Config.properties
CMD ["catalina.sh", "run"]