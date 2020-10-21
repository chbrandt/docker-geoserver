## References

1. GeoServer REST API: https://docs.geoserver.org/stable/en/user/rest/index.html
2. GeoServer REST API reference: https://docs.geoserver.org/stable/en/user/rest/api/index.html

## Notes

###### Configuration reload
* https://gis.stackexchange.com/questions/7754/geoserver-configuration-reload
* https://docs.geoserver.org/stable/en/user/rest/api/reload.html

```
curl -u admin:password -XPOST http://localhost:8080/geoserver/rest/reload`
```

###### Run behind a proxy
* https://docs.huihoo.com/geoserver/1.6.0/Configure%20GeoServer%20to%20run%20with%20a%20proxy.html

"
(...) You can now configure GeoServer to have the capabilities document properly report a proxy. We'd like to get this so it is easier to configure, but figured it's better to have the option at all. To configure a proxy, add this line to your web.xml:
```
<context-param>
  <param-name>PROXY_BASE_URL</param-name>
  <param-value>http://wms.externalhost.com/</param-value>
</context-param>
```
Where the value is the url to have GeoServer report in the capabilities document.
"

