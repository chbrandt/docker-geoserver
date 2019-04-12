FROM tomcat:8

MAINTAINER "Carlos H. Brandt <carloshenriquebrandt.gmail>"

ARG GEOSERVER_VERSION='2.14.3'

# By default, the data store is in:
# * GEOSERVER_DATA_DIR: ${CATALINA_HOME}/webapps/{ROOT|geoserver}/data/
# We will change it.
# Main goal for changing it is to effectively separate it from the app/code itself,
# and also allow for clean binding to a docker volume.
# ---
# For WAR setups it is recommended an alternative method (not env-variables):
# https://docs.geoserver.org/latest/en/user/datadirectory/setting.html#web-archive
# -> we will use a simple/clean environment variable; seems to work just fine.
# ---
ENV GEOSERVER_DATA_DIR='/var/lib/geoserver_data'

# Lines below will install the GeoServer WAR package inside Tomcat ('webapps/').
# NOTICE that GeoServer will be at Tomcat's root path: "http://host:port/".
# (Tomcat, by default, exposes app through port 8080)
#
RUN export WEB_ARCHIVE_ZIP="geoserver-${GEOSERVER_VERSION}-war.zip" &&\
    wget -q "http://sourceforge.net/projects/geoserver/files/GeoServer/${GEOSERVER_VERSION}/${WEB_ARCHIVE_ZIP}" &&\
    unzip $WEB_ARCHIVE_ZIP -d ${CATALINA_HOME}/webapps/.  &&\
    rm $WEB_ARCHIVE_ZIP                                   &&\
    catalina.sh stop 2> /dev/null                         &&\
    cd ${CATALINA_HOME}/webapps                           &&\
    rm -rf ROOT*                                          &&\
    mv geoserver.war ROOT.war

# Let's put some plugins there...
# * vector tiles
RUN mkdir -p /tmp/geoserver/vt &&  \
    wget -O /tmp/geoserver/gs.zip \
      https://iweb.dl.sourceforge.net/project/geoserver/GeoServer/${GEOSERVER_VERSION}/extensions/geoserver-${GEOSERVER_VERSION}-vectortiles-plugin.zip && \
    cd /tmp/geoserver/vt && unzip ../gs.zip && \
    mv * ${CATALINA_HOME}/webapps/ROOT/WEB-INF/lib/. && \
    cd - && rm -rf /tmp/geoserver
