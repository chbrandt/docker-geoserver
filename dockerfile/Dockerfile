FROM tomcat:8

MAINTAINER "Carlos H. Brandt <carloshenriquebrandt at gmail>"

ARG GEOSERVER_VERSION='2.18.3'

ADD src /tmp/src

RUN WEB_ARCHIVE_ZIP="geoserver-${GEOSERVER_VERSION}-war.zip"        &&\
    ZIP_LOCAL_PATH="/tmp/src/${WEB_ARCHIVE_ZIP}"                    &&\
    if [ ! -f "$ZIP_LOCAL_PATH" ]; then                               \
      GS="GeoServer/${GEOSERVER_VERSION}/${WEB_ARCHIVE_ZIP}";         \
      wget -q "http://sourceforge.net/projects/geoserver/files/${GS}" \
           -O ${ZIP_LOCAL_PATH};                                      \
    fi;                                                              \
    unzip ${ZIP_LOCAL_PATH} -d ${CATALINA_HOME}/webapps/.           &&\
    rm $ZIP_LOCAL_PATH                                              &&\
    catalina.sh stop 2> /dev/null

RUN catalina.sh start                           &&\
    echo 'Initializing Service' && sleep 20     &&\
    catalina.sh stop

ENV GEOSERVER_DATA_DIR="${CATALINA_HOME}/webapps/geoserver/data"

ADD catalina_home/conf/web.xml ${CATALINA_HOME}/conf/web.xml
ADD geoserver_data_dir/security/rest.properties ${GEOSERVER_DATA_DIR}/security/rest.properties
ADD geoserver_data_dir/user_projections/epsg.properties.planets \
      ${GEOSERVER_DATA_DIR}/user_projections/epsg.properties.planets

RUN cat ${GEOSERVER_DATA_DIR}/user_projections/epsg.properties.planets \
      >> ${GEOSERVER_DATA_DIR}/user_projections/epsg.properties

EXPOSE 8080
