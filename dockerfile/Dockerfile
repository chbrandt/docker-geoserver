FROM tomcat:8

MAINTAINER "Carlos H. Brandt <carloshenriquebrandt.gmail>"

ARG GEOSERVER_VERSION='2.14.2'

RUN export WEB_ARCHIVE_ZIP="geoserver-${GEOSERVER_VERSION}-war.zip" &&\
    wget -q "http://sourceforge.net/projects/geoserver/files/GeoServer/${GEOSERVER_VERSION}/${WEB_ARCHIVE_ZIP}" &&\
    unzip $WEB_ARCHIVE_ZIP -d ${CATALINA_HOME}/webapps/. &&\
    rm $WEB_ARCHIVE_ZIP &&\
    catalina.sh stop 2> /dev/null &&\
    cd ${CATALINA_HOME}/webapps &&\
    rm -rf ROOT* &&\
    mv geoserver.war ROOT.war

ENV DEBIAN_FRONTEND=noninteractive
RUN apt-get update &&\
    apt-get install -y vim curl &&\
    apt-get clean
