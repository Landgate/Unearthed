Unearthed
=========

Resources for developers in the Unearthed Hackathon from Landgate's SLIP data platform. This new release of the SLIP platform is currently in beta and is the product of a partnership between Landgate and Google built on the Google Maps Engine cloud-based service.

## Resources Map Service
Landgate have prepared a map service containing *more than [blah]* resource and environment-related datasets from a range of Government agencies. *list them?*

The data are available to inspect and query in the [SLIP Resources Map Viewer](https://mapsengine.google.com/09372590152434720789-11493353092997567468-4/mapview/?authuser=0).

### layers.json
This JSON dump contains the list of layers in the map service, along with their layerIds, layerKeys, datasourceIds, URIs for their datasources, and some additional useful metadata.

```javascript
{
  layerId: /* A globally unique ID used to refer to this layer */
  layerKey: /* The layer key - For the GMaps JS Lib. Not unique. */
  name: /* The layer name */
  description: /* The layer description */
  bbox: /* An array of four numbers (west, south, east, north) which define 
    the rectangular bounding box covered by the layer as latitude and longitude in decimal degrees */
  datasourceType: /* The type of layer - one of "table" or "image" */
  datasources: /* The path to the GME API resource of the more specific version of this asset. 
    Used for querying features and only applies to datasourceType "image". */
}
```

For easier viewing of layers.json use the [JSONView](https://chrome.google.com/webstore/detail/jsonview/chklaanhfefbnpoihckbnefhakgolnmc?hl=en) Chrome extension or the free online [JSON Visualisation](http://chris.photobooks.com/json/default.htm) tool.

> **Coming Soon:** We're hard at work on a brand new search and discovery tool! We'll intergrate all of this information and more in a single easy to use web interface with handy tools for developers.

## **Locate** Map Service
We also have our **Locate** map service available for use. For more information check out [its GitHub page](https://github.com/Landgate/Locate).


## Accessing Data
This section will serve as a brief introduction to develop off the SLIP platform. More detailed information, step-by-step guides, tutorials, code samples, and much more are available on our *[SLIP Developer Documentation wiki](https://github.com/Landgate/slip-developer-documentation/wiki)*.

### Spatial whatnow?
New to working with spatial data? We can highly recommend a read through of [GIS for Dummies](http://wiki.openstreetmap.org/wiki/GIS_for_Dummies_(written_by_a_dummy)).

### I just need to be able to see something on a map
If you simply need to be able to generate a visual representation of the data (e.g. display it on a map, generate a once-off JPEG) you have three API options:

- WMS (Web Mapping Service)
- WMTS (Web Map Tile Service)
- Google Maps JavaScript API

To consume these APIs you'll want a client library to do the heavy lifting for you. Fortunately you're spoilt for choice!

[OpenLayers](http://openlayers.org/), [OpenLayers 3](http://ol3js.org/) (still in beta), [Leaflet](http://leafletjs.com/), amd [MapBox JS](https://www.mapbox.com/mapbox.js) can all be used to easily consume WMS and WMTS APIs.

The [Google Maps JavaScript API](https://developers.google.com/maps/documentation/javascript/tutorial) has connectors specifically for Google Maps Engine. *inc Dynamic*

Code samples are available for all of these libraries over on our [SLIP Code Samples](https://github.com/Landgate/slip-code-samples) page. Check them out!

For quick and dirty mashups and visualisations in a desktop environment you can't go past [QGIS](http://www.qgis.org/en/site/).

For non-client facing calls you can either build the URL string yourself or use tools like [OWSLib (Python)](https://pypi.python.org/pypi/OWSLib) or [GeoTools (Java)](http://geotools.org/).


### I need to be able to retrieve and run queries against the raw data
If your focus is actually getting at the raw data itself, running queries against it, and analysing it then the [Google Maps Engine API](https://developers.google.com/maps-engine/) is your friend.

> *Note:* WFS access is available if needs be, but it's still an experimental service. See our [WFS page](https://github.com/Landgate/slip-developer-documentation/wiki/WFS) for more information.

The GME API is a RESTful API that speaks and consumes JSON. Our [Getting Started](https://github.com/Landgate/slip-developer-documentation/wiki/Getting-Started) documentation and [GME API Tutorial](https://github.com/Landgate/slip-developer-documentation/wiki/Tutorial-%231%3A-The-GME-API-%26-WFS) have more information on working with the GME API. We've also got a few [code samples](https://github.com/Landgate/slip-code-samples) demonstrating more advanced uses of the GME API.

> *Note:* You can also map the GeoJSON data that the GME API returns. [OpenLayers](http://openlayers.org/dev/examples/?q=geojson) and [Leaflet](http://leafletjs.com/examples/geojson.html) support GeoJSON natively and GitHub itself [will render GeoJSON files](https://help.github.com/articles/mapping-geojson-files-on-github).

If commandline is more your thing there's work underway to support the GME API within the [GDAL](http://www.gdal.org/). See the [GMEDriver documentation](http://trac.osgeo.org/gdal/wiki/GMEDriver) for more information.



On-demand or in the Unearthed data dump


## Tools
### APIs
For playing with APIs we recommend use of the [Postman](http://www.getpostman.com/) HTTP Client. It makes exploring and testing APIs a breeze.

### Desktop Apps
If you need to manipulate, convert, and analyse spatial data [QGIS](http://www.qgis.org/en/site/) is the best open source Geographic Information System.

### Make your own maps
If you have data you need to map you're spoilt for choice these days:

**SLIP GME?**
* [Google Maps Engine](http://mapsengine.google.com) (a free version of the same platform SLIP is built on [subject to [these limits](https://support.google.com/mapsengine/answer/3342103?hl=en)].
* [CartoDB](http://cartodb.com/)
* [TileMill](https://www.mapbox.com/tilemill/)
* [MangoMap](http://mangomap.com/)

### Help
[gis.stackexchange.com](http://gis.stackexchange.com/) is your friend.


### WMS & WMTS
WMS and WMTS access to *Locate* only require the mapId.

> ***Locate's* mapId:** 09372590152434720789-00913315481290556980
> Resources mapId:** 09372590152434720789-11493353092997567468

**[WMS Capabilities](https://mapsengine.google.com/09372590152434720789-00913315481290556980-4/wms/?REQUEST=GetCapabilities&VERSION=1.3.0)** | **[WMTS Capabilities](https://mapsengine.google.com/09372590152434720789-00913315481290556980-4/wmts/?REQUEST=GetCapabilities&VERSION=1.0&SERVICE=WMTS)**


### The GME API & WFS
Accessing data via the Google Maps Engine API or WFS is at the datasource-level and requires a datasource assetId to be provided (see ```layers.json```).

> **GME API:** https://www.googleapis.com/mapsengine/v1/tables/{assetId}/features?version=published&key={your-api-key}

> **WFS:** https://clients6.google.com/mapsengine/wfs_experimental/wfs/{assetId}/?REQUEST=GetCapabilities&SERVICE=WFS2.0&assetVersion=published

### Google Maps JavaScript API
The Google Maps JavaScript API has two ways of accessing data in Google Maps Engine:

1. Via the layerId (recommended - see ```layers.json```), or
2. By supplying a mapId and a layerKey.

> ***Locate's* mapID:** 09372590152434720789-00913315481290556980
> Resources mapId:** 09372590152434720789-11493353092997567468
