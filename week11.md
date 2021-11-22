
# Week 11

* Licenses
* d3-zoom & zoom transitions (SVG vs Canvas)
* WebGL scatterplots (SVG vs WebGL)

# Licenses

* [Introduction to Licenses](https://observablehq.com/@observablehq/licenses)
  * Permissive -- others can reuse, provided they provide attribution
  * Copyleft -- others can reuse, and must return any modifications or extensions
  * Creative Commons -- permissive reuse of content
  * Attribution Share Alike is the content analog of Copyleft
* Forked notebooks retain licensing of the original
* D3 team has added the ISC license to their notebooks

## d3-zoom & d3-drag

* [d3-zoom](https://github.com/d3/d3-zoom#d3-zoom) -- github API reference
  * [zoom events](https://github.com/d3/d3-zoom#api-reference) (quite a few are involved)
  * `d3.zoom()` creates a "zoom behavior"
  * [`zoom(selection)`](https://github.com/d3/d3-zoom#_zoom) binds the necessary event listeners
  * [`d3.zoomTransform(node)`](https://github.com/d3/d3-zoom#_zoom) returns the transform for the specified node
    * The transform represents a 2-D [transformation matrix](https://en.wikipedia.org/wiki/Transformation_matrix)
    * The zoom behavior stores the zoom state on the element to which the zoom behavior was applied.
    * That's so the zoom behavior can be applied to many elements, and each one can be zoomed independently.
* [d3-drag](https://github.com/d3/d3-drag) -- github API reference
  * [Drag and Zoom](https://observablehq.com/@d3/drag-zoom?collection=@d3/d3-zoom)
  * You can get all the behavior of a slippy map

## Compare performance of SVG and Canvas

* [Zoom SVG (rescaled)](https://observablehq.com/@d3/zoom-svg-rescaled)
  * SVG -- individual elements can be selected, each one is attached to the DOM
  * If you inspect the SVG, you'll see that each "circle" elements gets its own "translate", "r" remaining constant
* [Zoom Canvas (rescaled)](https://observablehq.com/@d3/zoom-canvas-rescaled)
  * If you look at the code, the canvas is redrawn with each zoom event
  * Canvas -- there is only one element attached to the DOM, pixels are manipulated directly
* QUESTION: Experiment with these demos. What can you say about relative performance?

## d3-zoom

* [Scatterplot Tour](https://observablehq.com/@d3/scatterplot-tour)
* Note: To improve rendering performance, the circles are drawn as zero-length strokes with round caps.
* QUESTION: At what point (i.e., for how many elements) does performance start degrading?

## In-class Exercise

Modify the [Scatterplot Tour](https://observablehq.com/@d3/scatterplot-tour)
to use the [Palmer Penguins](https://github.com/allisonhorst/palmerpenguins#palmerpenguins-)
  * [solution](./zoom.md)

