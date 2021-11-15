
# Week 10

Geospatial data-viz with OpenStreetMap

## Project check in

* Review project status with each group

## In-class Exercise -- D3 + Leaflet + Tooltip

Review the solution in class...??? (It was an exercise, but we didn't finish)

Add a tooltip to [D3 + Leaflet](https://observablehq.com/@pbogden/d3-leaflet)

* Hint: Follow this closely -- [Plot Tooltip](https://observablehq.com/@mkfreeman/plot-tooltip)
* It should be really easy.
* Solution: [leaflet.md](./leaflet.md)

## In-class Exercise -- D3 + Leaflet + Legend

* Add a Legend to [D3 + Leaflet](https://observablehq.com/@pbogden/d3-leaflet)
* Hint: follow this closely -- [Plot Color Legend](https://observablehq.com/@ambassadors/plot-color-legend)
* Hint: look also at the [Leaflet Choropleth](https://leafletjs.com/examples/choropleth/) tutorial
  * Maybe avoid doing this as an in-class exercise.
* Solution: [leaflet.md](./leaflet.md)

## Raster tiles

Tile providers

* [Raster Tiles](https://observablehq.com/@d3/raster-tiles?collection=@d3/d3-tile)
  * Uses [d3-tile](https://github.com/d3/d3-tile)
  * Includes a list of map tile providers
  * It's worth understanding how this works, because you can use it to modify the URLs for Leaflet
* [Stamen maps](http://maps.stamen.com/#terrain/12/37.7706/-122.3782)
  * Has example maps and instructions for using tile URLs, including attribution
  * Be careful about violating licenses and usage policies when using tile sources.
* [TileLayer reference docs](https://leafletjs.com/reference.html#tilelayer) -- leafletjs.com
  * It's worth looking at this documentation
  * Describes configurable parameters in the URL

## In-class Exercise -- D3 + Leaflet + Stamen

* Use Stamen tiles in [D3 + Leaflet](https://observablehq.com/@pbogden/d3-leaflet)
* Solution: [leaflet.md](./leaflet.md)

## Leaflet & OSM

* [OpenStreetMap export GUI](https://www.openstreetmap.org/export#map=15/43.6500/-70.2430)
  * Introduction to OpenStreetMap
* [OSM Data Viz](https://observablehq.com/@pbogden/osm-data-viz)
  * This notebook performs several pre-packaged queries.
  * Queryies the Overpass API using a library that returns [GeoJSON](https://geojson.org/)
  * If you return everything (i.e., if you don't filter your query), then make sure to use a very small domain
  * You can filter your query using the Overpass query language
  * [Overpass API by example](https://wiki.openstreetmap.org/wiki/Overpass_API/Overpass_API_by_Example)

## In-class Exercise -- Investigate OSM data

* Show (on the map) only those features that have a name (i.e., non-zero d.properties.tags.name)
  * To get this, you have to find the code that determines what is shown in the tooltip
  * It's the callback: `onEachFeature` -- see [GeoJSON on Leaflet](https://leafletjs.com/examples/geojson/)
