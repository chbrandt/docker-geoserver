# Data ingestion

Note:
> To ingest planetary data into GeoServer it must first be converted to
> EPSG:4326. This is because GeoServer is designed to work with EPSG data
> coded data, and EPSG:4326 (aka, WGS84) is common ground for degree
> coded data. Using such coordinates reference system simply makes life easier
> by following this _everywhere_ standard.

Steps to follow:

1. Run docker-geoserver
1. Download data (e.g, raster);
1. Convert data CRS to EPSG:4326;
1. Share data with your GeoServer instance;
1. Ingest data to GeoServer,
  * use the web/gui interface or
  * use the REST API


### Run GeoServer

```bash
$ docker run -dt --name geoserver \
             -v /path/to/data:/data -p 8080:8080 \
             chbrandt/geoserver
```


### Download data

For example, download the Margs-Viking global map from USGS/Astropedia,
https://astrogeology.usgs.gov/search/map/Mars/Viking/Color/Mars_Viking_ClrMosaic_global_925m.


### Convert CRS

Using `rasterio.warp` (eg, https://rasterio.readthedocs.io/en/latest/topics/reproject.html)
convert it to EPSG:4326.
Eg, `Mars_Viking_ClrMosaic_global_925m.tif` --> `Mars_Viking_ClrMosaic_global_925m.epsg4326.tif`.


### Share data

Move `Mars_Viking_ClrMosaic_global_925m.epsg4326.tif` to `/path/to/data`
(where docker-geoserver and the host share files).


### Ingest data (raster)

#### Using the Web/GUI interface

1. Create a new Workspace (eg, `mars`) if there is none already;
1. Create a new _Store_ for this raster (GeoTIFF);
  * Fill _Data Source name_
  * Indicate file: `/data/Mars_Viking_ClrMosaic_global_925m.epsg4326.tif`
1. Publish (`Mars_Viking_ClrMosaic_global_925m.epsg4326`)
