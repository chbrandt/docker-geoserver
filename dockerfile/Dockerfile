FROM tomcat:8.5.49

MAINTAINER "Carlos H. Brandt <carloshenriquebrandt.gmail>"

ARG GEOSERVER_VERSION='2.16.1'

ENV GEOSERVER_DATADIR="${CATALINA_HOME}/webapps/geoserver/data"

ADD user_projections/epsg.properties /tmp/epsg.properties

# Lines below will install the GeoServer WAR package inside Tomcat ('webapps/').
# NOTICE that GeoServer will be at Tomcat's root path: "http://host:port/".
# (Tomcat, by default, exposes app through port 8080)
#
RUN WEB_ARCHIVE_ZIP="geoserver-${GEOSERVER_VERSION}-war.zip"            &&\
    _BLA_="http://sourceforge.net/projects/geoserver/files/GeoServer"   &&\
    wget -q "${_BLA_}/${GEOSERVER_VERSION}/${WEB_ARCHIVE_ZIP}"          &&\
    unzip $WEB_ARCHIVE_ZIP -d ${CATALINA_HOME}/webapps/.                &&\
    rm $WEB_ARCHIVE_ZIP                                                 &&\
    catalina.sh stop 2> /dev/null
