<<<<<<< HEAD
=======

>>>>>>> d9237ecdf2f635d4651b45025ddc8d247bc630bb
# Week 09

Geospatial data-viz with slippy maps

<<<<<<< HEAD
* D3 & SVG basics
* Leaflet extensions/customization
* OSM data viz 

=======
>>>>>>> d9237ecdf2f635d4651b45025ddc8d247bc630bb
## Applications

Believe it or not, there's more to it than than sliders and tooltips.

* Hurricane flooding (0:11 - 3:11) -- "no so old stuff"
* [Cloud Contours](https://observablehq.com/@d3/cloud-contours?collection=@d3/d3-contour)

## Two Circles

Back to the basics -- looking at simple SVG interactions in detail (no copy and paste).

[Two Circles](https://observablehq.com/d/e9929ab1f12864d8) -- Created to address some things from the last couple assignments

* SVG element layering
* event capture and bubbling
* [.stopPropagation](https://developer.mozilla.org/en-US/docs/Web/API/Event/stopPropagation)
* [d3.transition](https://github.com/d3/d3-transition) and [d3.ease](https://github.com/d3/d3-ease)

## In-class Exercise

Practice with D3 data join

* EXERCISE: Recreate the circles and the functionality entirely with D3
* SOLUTION: [Two Circles with D3](./two_circles.md)
  * Hint: [*selection*.join](https://observablehq.com/@d3/selection-join)

## Min & Max Range Slider

Quick overview of the range-slider (from brush) solution (assignment due last week)

* NO DETAIL YET.
* [assignment07_solution.md](./assignment07_solution.md)

<<<<<<< HEAD
**STOPPED HERE ON MONDAY**

=======
>>>>>>> d9237ecdf2f635d4651b45025ddc8d247bc630bb
## Choropleth w/tooltip

* This assignment was due 6 Nov -- had a few perfect 10s
* Review the solution in detail -- those who want to resubmit will get half their missing points.

[assignment08_solution.md](./assignment08_solution.md)

## In-class Exercise -- D3 + Leaflet + Tooltip

Add a tooltip to [D3 + Leaflet](https://observablehq.com/@pbogden/d3-leaflet)

* Hint: Follow this closely -- [Plot Tooltip](https://observablehq.com/@mkfreeman/plot-tooltip)
<<<<<<< HEAD
* It should be really easy.
* Solution: [leaflet.md](./leaflet.md)

## In-class Exercise -- D3 + Leaflet + Legend

* Add a Legend to [D3 + Leaflet](https://observablehq.com/@pbogden/d3-leaflet)
* Hint: follow this closely -- [Plot Color Legend](https://observablehq.com/@ambassadors/plot-color-legend)
  * Maybe avoid doing this as an in-class exercise.
* Solution: [leaflet.md](./leaflet.md)
=======
* [D3 + Leaflet + Tooltip](https://observablehq.com/d/7111ad3d30aee012)
>>>>>>> d9237ecdf2f635d4651b45025ddc8d247bc630bb

## Raster tiles

Tile providers

* [Raster Tiles](https://observablehq.com/@d3/raster-tiles?collection=@d3/d3-tile)
<<<<<<< HEAD
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
  * Queryies the API using a library that returns [GeoJSON](https://geojson.org/)
  * If you return everything, then make sure to use a very small domain
  * You can filter your query using the Overpass query language
  * [Overpass API by example](https://wiki.openstreetmap.org/wiki/Overpass_API/Overpass_API_by_Example)
=======
  * Uses [d3-tile](https://github.com/d3/d3-tile) with a list of map tile providers
* [Stamen maps](http://maps.stamen.com/#terrain/12/37.7706/-122.3782)
  * Has example maps, instructions for using tile URLs

## In-Class Exercise

Change tile source in Leaflet

* Use a tile source in [Raster Tiles](https://observablehq.com/@d3/raster-tiles?collection=@d3/d3-tile)
  * Extract the URLs to use with Leaflet

## Leaflet & OSM

* [OSM Data Viz](https://observablehq.com/@pbogden/osm-data-viz)
>>>>>>> d9237ecdf2f635d4651b45025ddc8d247bc630bb
