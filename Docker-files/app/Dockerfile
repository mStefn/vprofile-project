From openjdk:11 AS BUILD_IMAGE
LABEL "Poject"="Vprofile"
LABEL "Author"="Stefan"
RUN apt update && apt install maven -y
RUN git clone --branch docker https://github.com/mStefn/vprofile-project.git
RUN cd vprofile-project && mvn install   

From tomcat:9-jre11
RUN rm -rf /usr/local/tomcat/webapps/*
COPY --from=BUILD_IMAGE vprofile-project/target/vprofile-v2.war /usr/local/tomcat/webapps/ROOT.war

EXPOSE 8080
CMD ["catalina.sh", "run"]
