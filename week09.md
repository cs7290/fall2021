
# Week 09

Geospatial data-viz with slippy maps

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

## Choropleth w/tooltip

* This assignment was due 6 Nov -- had a few perfect 10s
* Review the solution in detail -- those who want to resubmit will get half their missing points.

[assignment08_solution.md](./assignment08_solution.md)

## In-class Exercise -- D3 + Leaflet + Tooltip

Add a tooltip to [D3 + Leaflet](https://observablehq.com/@pbogden/d3-leaflet)

* Hint: Follow this closely -- [Plot Tooltip](https://observablehq.com/@mkfreeman/plot-tooltip)
* [D3 + Leaflet + Tooltip](https://observablehq.com/d/7111ad3d30aee012)

## Raster tiles

Tile providers

* [Raster Tiles](https://observablehq.com/@d3/raster-tiles?collection=@d3/d3-tile)
  * Uses [d3-tile](https://github.com/d3/d3-tile) with a list of map tile providers
* [Stamen maps](http://maps.stamen.com/#terrain/12/37.7706/-122.3782)
  * Has example maps, instructions for using tile URLs

## In-Class Exercise

Change tile source in Leaflet

* Use a tile source in [Raster Tiles](https://observablehq.com/@d3/raster-tiles?collection=@d3/d3-tile)
  * Extract the URLs to use with Leaflet

## Leaflet & OSM

* [OSM Data Viz](https://observablehq.com/@pbogden/osm-data-viz)
