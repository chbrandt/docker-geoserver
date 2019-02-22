# docker-geoserver

This container is deploying [GeoServer] over [Apache Tomcat], through its
[Web Archive] package.

## Run it
```
$ docker run -dt -p 8080:8080 chbrandt/geoserver
```
The [credentials are the deafult ones](https://docs.geoserver.org/latest/en/user/gettingstarted/web-admin-quickstart/index.html#logging-in):
* username: `admin`
* password: `geoserver`

Currently, versions are:
* GeoServer: `2.14.2`
* Tomcat: `8.5.37`

[geoserver]: http://geoserver.org/
[apache tomcat]: http://tomcat.apache.org/
[web archive]: http://geoserver.org/release/stable/
