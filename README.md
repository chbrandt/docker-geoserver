# docker-geoserver

This container is deploying [GeoServer] over [Apache Tomcat], through its
[Web Archive] package.
The image [here defined](./dockerfile/Dockerfile) inherits from [Tomcat-8](https://github.com/docker-library/tomcat/blob/master/8.5/jre8/Dockerfile).

Currently, versions are:
* GeoServer: `2.14.3`
* Tomcat: `8.5.37`

## How to use it

This container exposes port `8080`, and Geoserver is available at the root path.
```bash
$ docker run -p 8080:8080 chbrandt/geoserver
```
Then go to your browser' <http://localhost:8080>.

[Credentials are the default ones][1]:
* username: `admin`
* password: `geoserver`

[1]: https://docs.geoserver.org/latest/en/user/gettingstarted/web-admin-quickstart/index.html#logging-in

[geoserver]: http://geoserver.org/
[apache tomcat]: http://tomcat.apache.org/
[web archive]: http://geoserver.org/release/stable/
