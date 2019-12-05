FROM tomcat:8.5.49

MAINTAINER "Carlos H. Brandt <carloshenriquebrandt.gmail>"

ARG GEOSERVER_VERSION='2.16.1'

# Lines below will install the GeoServer WAR package inside Tomcat ('webapps/').
# NOTICE that GeoServer will be at Tomcat's root path: "http://host:port/".
# (Tomcat, by default, exposes app through port 8080)
#
RUN export WEB_ARCHIVE_ZIP="geoserver-${GEOSERVER_VERSION}-war.zip" &&\
    wget -q "http://sourceforge.net/projects/geoserver/files/GeoServer/${GEOSERVER_VERSION}/${WEB_ARCHIVE_ZIP}" &&\
    unzip $WEB_ARCHIVE_ZIP -d ${CATALINA_HOME}/webapps/.  &&\
    rm $WEB_ARCHIVE_ZIP                                   &&\
    catalina.sh stop 2> /dev/null
