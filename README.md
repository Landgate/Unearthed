Unearthed
=========

Resources for developers in the Unearthed Hackathon.

## layers.json
Contains the list of layers in *Locate*, along with their layerIds, layerKeys, datasourceIds, URIs for their datasources, and some additional useful metadata.

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

For easier viewing of layers.json try the [JSONView](https://chrome.google.com/webstore/detail/jsonview/chklaanhfefbnpoihckbnefhakgolnmc?hl=en) Chrome extension or the free online [JSON Visualisation](http://chris.photobooks.com/json/default.htm) tool.

> **Coming Soon:** We're hard at work on a brand new search and discovery tool! We'll intergrate all of this information and more in a single easy to use web interface with handy tools for developers.

## Accessing Data

### Spatial whatnow?
New to working with spatial? [GIS for Dummies](http://wiki.openstreetmap.org/wiki/GIS_for_Dummies_(written_by_a_dummy)) is a useful little primer.

### I just need to be able to see it on a map
If you simply need to be able to generate a visual representation of the data (e.g. display it on a map, generate a once-off JPEG) you have three options:

- WMS (Web Mapping Service)
- WMTS (Web Map Tile Service)
- Google Maps JavaScript API

[OpenLayers](http://openlayers.org/), [Leaflet](http://leafletjs.com/), [MapBox JS](https://www.mapbox.com/mapbox.js), [Google Maps JavaScript API](https://developers.google.com/maps/documentation/javascript/tutorial)
[QGIS](http://www.qgis.org/en/site/)
[SLIP Code Samples](https://github.com/Landgate/slip-code-samples)


### I need to be able to retrieve and run queries against the raw data

[Google Maps Engine API](https://developers.google.com/maps-engine/)
[WFS]()

[SLIP Code Samples](https://github.com/Landgate/slip-code-samples) (Details..., [GeoJSON](http://openlayers.org/dev/examples/?q=geojson))
[GME API & WFS Tutorial](https://github.com/Landgate/slip-developer-documentation/wiki/Tutorial-%231%3A-The-GME-API-%26-WFS)


## My own data...
[CartoDB](http://cartodb.com/)
[TileMill](https://www.mapbox.com/tilemill/)


### I **really** need an offline copy


On-demand or in the Unearthed data dump


## Tools
[Postman](http://www.getpostman.com/)

GitHub GeoJSON view

QGIS





### WMS & WMTS
WMS and WMTS access to *Locate* only require the mapId.

> ***Locate's* mapID:** 09372590152434720789-00913315481290556980

**[WMS Capabilities](https://mapsengine.google.com/09372590152434720789-00913315481290556980-4/wms/?REQUEST=GetCapabilities&VERSION=1.3.0)** | **[WMTS Capabilities](https://mapsengine.google.com/09372590152434720789-00913315481290556980-4/wmts/?REQUEST=GetCapabilities&VERSION=1.0&SERVICE=WMTS)**


### The GME API & WFS
Accessing data via the Google Maps Engine API or WFS is at the datasource-level and requires a datasource assetId to be provided.

> **GME API:** https://www.googleapis.com/mapsengine/v1/tables/{assetId}/features?version=published&key={your-api-key}

> **WFS:** https://clients6.google.com/mapsengine/wfs_experimental/wfs/{assetId}/?REQUEST=GetCapabilities&SERVICE=WFS2.0&assetVersion=published

### Google Maps JavaScript API
The Google Maps JavaScript API has two ways of accessing data in Google Maps Engine:

1. Via the layerId (recommended), or
2. By supplying a mapId and a layerKey.

> ***Locate's* mapID:** 09372590152434720789-00913315481290556980
