FROM openjdk:8-jdk

MAINTAINER "Carlos H. Brandt <carloshenriquebrandt.gmail>"

ARG GEOSERVER_VERSION='2.16.1'

ARG GEOSERVER_HOME="/usr/share/geoserver-${GEOSERVER_VERSION}"
ENV GEOSERVER_HOME=$GEOSERVER_HOME

ARG GEOSERVER_DATA_DIR='/var/lib/geoserver_data'
ENV GEOSERVER_DATA_DIR=$GEOSERVER_DATA_DIR

# Lines below will install the GeoServer WAR package inside Tomcat ('webapps/').
# NOTICE that GeoServer will be at Tomcat's root path: "http://host:port/".
# (Tomcat, by default, exposes app through port 8080)
#
RUN mkdir -p $GEOSERVER_HOME $GEOSERVER_DATA_DIR                        &&\
    BINARY_ZIP="geoserver-${GEOSERVER_VERSION}-bin.zip"                 &&\
    _BLA_="http://sourceforge.net/projects/geoserver/files/GeoServer"   &&\
    wget -q "${_BLA_}/${GEOSERVER_VERSION}/${BINARY_ZIP}"               &&\
    unzip $BINARY_ZIP -d ${GEOSERVER_HOME}/..                           &&\
    rm $BINARY_ZIP                                                      &&\
    [ "$(ls -A $GEOSERVER_DATA_DIR)" ] || \
      cp -R ${GEOSERVER_HOME}/data_dir/* ${GEOSERVER_DATA_DIR}/.

ADD user_projections/epsg.properties ${GEOSERVER_DATA_DIR}/user_projections/epsg.properties

EXPOSE 8080

ENTRYPOINT ${GEOSERVER_HOME}/bin/startup.sh
