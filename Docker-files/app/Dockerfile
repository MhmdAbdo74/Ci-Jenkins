FROM tomcat:8-jre11
LABEL "Project"="Vprofile"
LABEL "Author"="Imran"
#remove default app 
RUN rm -rf /usr/local/tomcat/webapps/*
#deploy artifact in apache tomcat 
COPY target/vprofile-v2.war /usr/local/tomcat/webapps/ROOT.war

EXPOSE 8080
CMD ["catalina.sh", "run"]
WORKDIR /usr/local/tomcat/
VOLUME /usr/local/tomcat/webapps