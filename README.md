# docker-geoserver

This container is deploying [GeoServer] over [Apache Tomcat], through its
[Web Archive] package.

Currently, versions are:
* GeoServer: `2.14.2`
* Tomcat: `8.5.37`

## Run it

The minimal command-line to run the container is:
```
$ docker run -p 8080:8080 chbrandt/geoserver
```
After a couple of seconds, geoserver will be available at your browser's `http://localhost:8080`.

The [credentials are the deafult ones](https://docs.geoserver.org/latest/en/user/gettingstarted/web-admin-quickstart/index.html#logging-in):
* username: `admin`
* password: `geoserver`

[geoserver]: http://geoserver.org/
[apache tomcat]: http://tomcat.apache.org/
[web archive]: http://geoserver.org/release/stable/
