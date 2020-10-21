# docker-geoserver

This dockerfile set up [GeoServer] on top of [Apache Tomcat], using the
[Web Archive] distribution package.

The image available at [chbrandt/geoserver] provides the following versions:
* GeoServer: `2.17.3`
* Tomcat: `8`

## Build your image

If you want to create an image for a particular version of GeoServer you can
give `docker build` an argument specifying the version accordingly.

For example, to build an image for GeoServer `2.15.3`:
```bash
$ cd dockerfile/
$ docker build --build-arg GEOSERVER_VERSION=2.15.3 -t my_geoserver .
```

---
Container settings:
* Exposed port is `8080` (Tomcat's default)
* [Credentials are the default ones][1]:
  * username: `admin`
  * password: `geoserver`
* [Geoserver data directory][2] is:
  * `GEOSERVER_DATA_DIR='/var/lib/geoserver_data'`
---

[1]: https://docs.geoserver.org/latest/en/user/gettingstarted/web-admin-quickstart/index.html#logging-in
[2]: https://docs.geoserver.org/stable/en/user/datadirectory/setting.html

## How to run it

```bash
$ docker run -p 8080:8080 chbrandt/geoserver
```
Then go to your browser' <http://localhost:8080/geoserver>.

## Relocating the data directory

By default, the data is stored under `data/` in the root of GeoServer installation,
in a Tomcat/WAR setup it is at `${CATALINA_HOME}/webapps/geoserver/data/`.

To change it one can define an environment variable '`GEOSERVER_DATA_DIR`'
defining the path to use instead. E.g.,
```
$ docker run -e GEOSERVER_DATA_DIR='/var/lib/geoserver_data' \
  -p 8080:8080 chbrandt/geoserver
```

See GeoServer' [docs on _data-directory_][datadirectory]


[geoserver]: http://geoserver.org/
[apache tomcat]: http://tomcat.apache.org/
[web archive]: http://geoserver.org/release/stable/
[Tomcat-8 official image]: https://github.com/docker-library/tomcat/blob/master/8.5/jre8/Dockerfile
[chbrandt/geoserver]: https://hub.docker.com/repository/docker/chbrandt/geoserver
[2.16 nightly build]: https://build.geoserver.org/geoserver/2.16.x/
[datadirectory]: https://docs.geoserver.org/latest/en/user/datadirectory/setting.html#web-archive
