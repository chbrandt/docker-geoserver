FROM tomcat:8

MAINTAINER "Carlos H. Brandt <carloshenriquebrandt.gmail>"

ARG GEOSERVER_VERSION='2.14.3'

ENV GEOSERVER_DATA_DIR='/var/lib/geoserver_data'

# Lines below will install the GeoServer WAR package inside Tomcat ('webapps/').
# NOTICE that GeoServer will be at Tomcat's root path: "http://host:port/".
#
RUN export WEB_ARCHIVE_ZIP="geoserver-${GEOSERVER_VERSION}-war.zip" &&\
    wget -q "http://sourceforge.net/projects/geoserver/files/GeoServer/${GEOSERVER_VERSION}/${WEB_ARCHIVE_ZIP}" &&\
    unzip $WEB_ARCHIVE_ZIP -d ${CATALINA_HOME}/webapps/.  &&\
    rm $WEB_ARCHIVE_ZIP                                   &&\
    catalina.sh stop 2> /dev/null                         &&\
    cd ${CATALINA_HOME}/webapps                           &&\
    rm -rf ROOT*                                          &&\
    mv geoserver.war ROOT.war

# We may want to modify the data store path, for the time being the default is:
#ENV GEOSERVER_DATA_DIR=${CATALINA_HOME}/webapps/ROOT/data/
# For WAR setups it is actually recommended an alternative method:
# https://docs.geoserver.org/latest/en/user/datadirectory/setting.html#web-archive
