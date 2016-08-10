# osul/fcrepo:4.5.1
FROM tomcat:7-jre8
MAINTAINER Corey Hinshaw <hinshaw.25@osu.edu>

ENV FEDORA_VERSION 4.5.1
ENV FEDORA_TAG 4.5.1

# Install Fedora
RUN mkdir -p /mnt/ingest \
  && mkdir -p /mnt/fcrepo4-data \
  && sed -i '$i<role rolename="fedoraUser"/>$i<role rolename="fedoraAdmin"/>$i<role rolename="manager-gui"/>$i<user username="testuser" password="password1" roles="fedoraUser"/>$i<user username="adminuser" password="password2" roles="fedoraUser"/>$i<user username="fedoraAdmin" password="secret3" roles="fedoraAdmin"/>$i<user username="fedora" password="fedora" roles="manager-gui"/>' $CATALINA_HOME/conf/tomcat-users.xml \
  && echo 'fcrepo.home=/mnt/fcrepo4-data' >> $CATALINA_HOME/conf/catalina.properties \
  && curl -fSL https://github.com/fcrepo4-exts/fcrepo-webapp-plus/releases/download/fcrepo-webapp-plus-$FEDORA_TAG/fcrepo-webapp-plus-$FEDORA_VERSION.war -o fcrepo.war \
  && cp fcrepo.war $CATALINA_HOME/webapps/fcrepo.war

VOLUME /mnt/ingest
VOLUME /mnt/fcrepo4-data
