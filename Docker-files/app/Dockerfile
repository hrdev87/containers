FROM openjdk:11 AS BUILD_IMAGE
RUN apt update && apt install maven -y
RUN git clone https://github.com/hrdev87/containers.git
RUN cd containers && git checkout docker && mvn install


FROM tomcat:9-jre11
LABEL "Project"="containers"
LABEL "Author"="Hamidreza"
RUN rm -rf /usr/local/tomcat/webapps/*
COPY --from=BUILD_IMAGE containers/target/vprofile-v2.war /usr/local/tomcat/webapps/ROOT.war

EXPOSE 8080
CMD ["catalina.sh", "run"]