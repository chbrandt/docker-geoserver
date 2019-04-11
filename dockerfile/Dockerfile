FROM tomcat:8

MAINTAINER "Carlos H. Brandt <carloshenriquebrandt.gmail>"

ARG GEOSERVER_VERSION='2.14.3'

ENV GEOSERVER_DATA_DIR='/var/lib/geoserver_data'

RUN export WEB_ARCHIVE_ZIP="geoserver-${GEOSERVER_VERSION}-war.zip" &&\
    wget -q "http://sourceforge.net/projects/geoserver/files/GeoServer/${GEOSERVER_VERSION}/${WEB_ARCHIVE_ZIP}" &&\
    unzip $WEB_ARCHIVE_ZIP -d ${CATALINA_HOME}/webapps/. &&\
    rm $WEB_ARCHIVE_ZIP &&\
    catalina.sh stop 2> /dev/null &&\
    cd ${CATALINA_HOME}/webapps &&\
    rm -rf ROOT* &&\
    mv geoserver.war ROOT.war
