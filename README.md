# Center for Spatial Research Mapping Engine Project

### Overall Structure
The final process for producing maps would look like this:
* Use Leaflet to create a map in our HTML + CSS + Javascript
* Get base *vector* tiles from OSM through Leaflet and Tangram (Mapzen)
* Get base *raster* tiles from our own server through Leaflet
* Get any other data from our own server (from our postGIS database) through Leaflet

The c4sr mapping engine could consist of the following elements:
* Routing engine: providing route data without having to deal with rate limits
* Raster tiling server: providing raster tiles and eliminating the need for Mapbox storing and serving
* PostGIS database: serving our own datasets in map-ready formats (geoJSON?)
* Vector map templates: using open source data
* [Updated Map Server](http://www.axismaps.com/blog/): This might be the overall configuration, apart from the routing engine... (Test this one first).
* [Map Server](http://www.axismaps.com/blog/2012/01/dont-panic-an-absolute-beginners-guide-to-building-a-map-server/): This might be the overall configuration, apart from the routing engine... (Old version).

#### Routing Engine
An internal server that can provide us with routing information. Specially useful when working with large transportation datasets like the NYC Taxicab data or Citibike data. Given a specific transportation network the routing engine will give us the ideal route for any pair of origin and destination.
* References:
  * [Valhalla - Mapzen](https://github.com/valhalla): Open source routing engine and libraries
  * [Example with Docker](https://github.com/stuartlynn/valhalla-docker)

#### Raster tile server
See the overall tutorials at the top... this might be the easiest solution. Also, we might want to build the tiles first and then upload them to the server. Or upload them to the postgis database and have Mapnik render them (don't know if this is correct).
* References:
  * [Creating your own tiles](https://wiki.openstreetmap.org/wiki/Creating_your_own_tiles): Maybe this is the best starting point?
  * [Hosting Rasters as a Tile Server](https://gis.stackexchange.com/questions/144821/hosting-rasters-as-a-tile-server): Using Tilemill to create the tiles and then uploading them to a server?
  * [Mapnik???](https://github.com/klokantech/tileserver-mapnik)
  * [Docker??](http://osm2vectortiles.org/docs/serve-raster-tiles-docker/)
  * [Mapbox Studio Classic](https://github.com/mapbox/mapbox-studio-classic): Could Mapbox Studio Classic work as a replacement for Tilemill in terms of generating tiles?

#### Vector Tile Templates
This could help with creating templates and serving *vector* tiles with OSM data as basemaps for our projects.
* References:
  * [Tangram - Mapzen](https://mapzen.com/projects/tangram/)
  * [Terrain - Updated](https://mapzen.com/blog/elevation/)
  * [Terrain](https://libraries.io/github/mapzen/terrarium)
  * [Terrain](https://mapzen.com/blog/mapping-mountains/)

#### Other
* [How to display tiles in projections other than Web-Mercator](http://vis4.net/blog/posts/no-more-mercator-tiles/)
* Other mapping javascript libraries:
  * [Leaflet](http://leafletjs.com/): The classic.
  * [Polymaps](http://polymaps.org/)
  * [Open Layers](http://openlayers.org/)
  * [Modest Maps](http://modestmaps.com/): Minimal and "hackable"?

 #### Working sites:
 *  https://tangrams.github.io/explorer/#9.9/3.4973/-76.3896/kind/major_road
 *  https://mapzen.com/documentation/tangram/Raster-Overview/
 *  https://www.openstreetmap.org/node/274021463
 *  https://wiki.openstreetmap.org/wiki/Key:place
 *  https://tangrams.github.io/tangram-sandbox/tangram.html?styles/press#7/3.447/-76.540
 *  https://github.com/tangrams/tangram-sandbox/blob/gh-pages/styles/press.yaml
 *  https://wiki.openstreetmap.org/wiki/Zoomlevel
 *  https://mapzen.com/documentation/tangram/Filters-Overview/
 *  