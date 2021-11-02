
# Week 08

* Project kickoffs
* Data join, d3-geo
* Choropleth (adding interaction with D3)

## Project plans

* See [projects.md](../projects.md)

## data join

Introduction to data-join with [d3-selection](https://github.com/d3/d3-selection)

* [data-join.md](./data-join.md)

## Projects

* Update [projects](./projects.md) with project teams as the rest of the class does the exercises
* Exercises are based on the choropleth

## Choropleth

Introduction to [d3-geo](https://github.com/d3/d3-geo) and mapping with D3

* [d3-geo](https://observablehq.com/collection/@d3/d3-geo) -- the collection
* [choropleth.md](./choropleth.md)

## Exercises

Work with [State Choropleth](https://observablehq.com/@d3/state-choropleth)

* Exercise #1: Add a circle that follows the mouse
  * Use [d3.pointer](https://github.com/d3/d3-selection/blob/main/README.md#pointer)
    * `d3.pointer(event)` is part of [d3-selection](https://github.com/d3/d3-selection/blob/main/README.md)
  * Get hints from [Plot Tooltip](https://observablehq.com/@mkfreeman/plot-tooltip)
* Exercise #2: Update the styling to highlight the state that's being moused over
  * Again, get hints from here: [Plot Tooltip](https://observablehq.com/@mkfreeman/plot-tooltip)
  * [d3.select()](https://github.com/d3/d3-selection#select) -- tells you about `this`
* Exercise #3: Tooltip
  * Add a tooltip that shows the data value as it follows the mouse
  * Get hints from here: [Plot Tooltip](https://observablehq.com/@mkfreeman/plot-tooltip)
  * You'll need to add a text element, and get the data from the selected element
* Solutions are here: [choropleth.md](./choropleth.md)

## Topojson

We're using topojson data, which has various features in addition to being efficient

* [topojson](https://github.com/topojson/topojson) -- github
* [topojson.neighbors](https://github.com/topojson/topojson-client/blob/master/README.md#neighbors)
* [merging states](https://bl.ocks.org/mbostock/5416405) -- bl.ocks.org
  * [topojson.merge](https://github.com/topojson/topojson-client/blob/master/README.md#merge)
* [merging states II](https://bl.ocks.org/mbostock/5416440) -- bl.ocks.org
  * careful rendering of selected states
  * filter geojson objects
* Note that the topojson on [State Choropleth](https://observablehq.com/@d3/state-choropleth) is pre-projected
  * You can see this by examining the GeoJSON
  * This can be problematic depending on your application

## d3-geo

d3-geo includes a variety of geospatial tools

* This is where the [projections](https://github.com/d3/d3-geo#projections) live
  * There's also [projection.invert](https://github.com/d3/d3-geo#projection_invert) if the projection is invertible
  * [ZIP codes](https://observablehq.com/@pbogden/zip-codes) shows one way to use projection
* [d3-geo spherical math](https://github.com/d3/d3-geo#spherical-math) has other capabilities
  * d3.GeoAlbersUsa requires scale and translate
  * With the projection, you can do all sorts of things
  * For example: [d3.geoContains(object, point)](https://github.com/d3/d3-geo#geoContains)
* [My U.S. Map (SVG)](https://observablehq.com/@pbogden/my-u-s-map-svg?collection=@pbogden/mapping)
  * If you know the projection, you're in good shape
  * Unprojected GeoJSON with metadata -- this may be a bit easier to work with
  * [My U.S. Map (Canvas)](https://observablehq.com/@pbogden/my-u-s-map-canvas?collection=@pbogden/mapping)

## Shapefiles

You can stream shapefiles with the [shapefile](https://github.com/mbostock/shapefile) library

* [shapefile](https://github.com/mbostock/shapefile) -- github
* [streaming shapefiles](https://observablehq.com/@mbostock/streaming-shapefiles)

## d3-tile

With d3-tile, you can easily integrate a variety of map-tile services

* [d3-tile](https://observablehq.com/collection/@d3/d3-tile) -- the collection
* [DC schools](https://observablehq.com/collection/@pbogden/dc-schools)
  * This has a variety of selectable tile services

## Slippy Maps

There are many different slippy map libraries -- the most popular open source library is Leaflet.

* [Hello, Leaflet](https://observablehq.com/@mbostock/hello-leaflet)
  * [Leaflet](https://observablehq.com/@tmcw/leaflet)
  * [Leaflet tutorials](https://leafletjs.com/examples.html)
* [Hello, Mapbox GL](https://observablehq.com/@mbostock/hello-mapbox-gl)
  * [Using Mapbox GL JS](https://observablehq.com/@tmcw/using-mapbox-gl-js)
* [Hello, OpenLayers](https://observablehq.com/@mbostock/hello-openlayers)
  * [Hello, Openlayers Select](https://observablehq.com/@mbostock/hello-openlayers-select)
  * [OpenLayers Choropleth](https://observablehq.com/@pbogden/choropleth-with-openlayers?collection=@pbogden/openlayers)
  * [D3 + OpenLayers](https://observablehq.com/@pbogden/d3-openlayers?collection=@pbogden/openlayers)
* The original: [D3 + Leaflet](https://bost.ocks.org/mike/leaflet/) published in 2012 -- bost.ocks.org
  * [D3 & Leaflet](https://observablehq.com/@pbogden/d3-leaflet) -- my attempt to implement the original
  * Uses [d3-geo stream](https://github.com/d3/d3-geo#streams) to link between Leaflet & D3

## Assignment 06 solutions

EDA with D3 and Plot -- review the solutions

* [assignment06_solutions.md](./assignment06_solutions.md)

