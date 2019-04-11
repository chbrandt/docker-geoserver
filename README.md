# docker-geoserver

This container is deploying [GeoServer] over [Apache Tomcat], through its
[Web Archive] package.
The image [here defined](./dockerfile/Dockerfile) inherits from [Tomcat-8 official image].

Currently, versions are:
* GeoServer: `2.14.3`
* Tomcat: `8.5.37`

---
Container settings:
* (from Tomcat) eposed port is `8080`
* [Geoserver data directory][2] is: `GEOSERVER_DATA_DIR='/var/lib/geoserver_data'`
* Geoserver is at Tomcat's root path (`/`)
* [Credentials are the default ones][1]:
  * username: `admin`
  * password: `geoserver`
---

[1]: https://docs.geoserver.org/latest/en/user/gettingstarted/web-admin-quickstart/index.html#logging-in
[2]: https://docs.geoserver.org/stable/en/user/datadirectory/setting.html

## How to run it

```bash
$ docker run -p 8080:8080 chbrandt/geoserver
```
Then go to your browser' <http://localhost:8080>.


[geoserver]: http://geoserver.org/
[apache tomcat]: http://tomcat.apache.org/
[web archive]: http://geoserver.org/release/stable/
[Tomcat-8 official image]: https://github.com/docker-library/tomcat/blob/master/8.5/jre8/Dockerfile
