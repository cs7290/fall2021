
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

## In-Class Exercise -- Scatterplot tour with penguins

Modify the [Scatterplot Tour](https://observablehq.com/@d3/scatterplot-tour)
to use the [Palmer Penguins](https://github.com/allisonhorst/palmerpenguins#palmerpenguins-)
  * [solution](./zoom.md)

## 3-D

* [Crater shading](https://observablehq.com/@visionscarto/crater-shading?collection=@visionscarto/30daymapchallenge)

## WebGL

Demos above allowed us to start seeing the 
[performance](https://developer.mozilla.org/en-US/docs/Web/Performance) limitations of 
[DOM manipulation](https://developer.mozilla.org/en-US/docs/Learn/JavaScript/Client-side_web_APIs/Manipulating_documents).

* [WebGL API](https://developer.mozilla.org/en-US/docs/Web/API/WebGL_API) -- MDN
  * WebGL is a JavaScript API for rendering high-performance interactive 3D and 2D graphics.
  * It uses HTML5 `<canvas>` elements without plugins in any compatible web browser.
  * Note: the user's device must have supporting hardware (Graphical Processing Unit; GPU).
  * WebGL closely conforms to [OpenGL ES 2.0](https://en.wikipedia.org/wiki/OpenGL_ES)
  * WebGL programs consist of control code (JavaScript) and special effects code (shader code) executed on a GPU. 
  * WebGL elements can be mixed with other HTML elements.
* [WebGL Tutorial](https://developer.mozilla.org/en-US/docs/Web/API/WebGL_API/Tutorial) -- MDN
  * The tutorial has some good background links, including this one on OpenGL...
  * [An Introduction to OpenGL](https://duriansoftware.com/joe/an-intro-to-modern-opengl.-table-of-contents)

## Demos

* [LiquidFun](https://observablehq.com/@mbostock/liquidfun?collection=@observablehq/webgl) -- mbostock notebook
  * [LiquidFun](http://google.github.io/liquidfun/) -- google.github.io

## Intro tutorials

* [MDN WebGL Demo #2](https://observablehq.com/@tmcw/mdn-webgl-demo-2?collection=@observablehq/webgl) -- tmcw notebook
* [Hello, Fragment Shader](https://observablehq.com/@mbostock/hello-fragment-shader) -- mbostock notebook
* [Hello, WebGL](https://bl.ocks.org/mbostock/5440492) -- mbostock block (circa 2013)
  * This introductory tutorial demonstrates how to use the WebGL API.
  * Notice the amount of work you need to do simply for setup.

## Scatter-GL demo

* [scatter-gl](https://github.com/PAIR-code/scatter-gl#scattergl) -- github
  * To run the demo
  ```
  cd ~/Sites/scatter-gl
  yarn
  yarn demo
  ```
  Browse to http://localhost:8080
* [Embedding projector](http://projector.tensorflow.org/)

## Scatter-GL in Observable

Installation...

* Note the CDN install for a web page
* For Observable...
  * Get the version number and dependency in `package.json` -- 0.0.11 for scatter-gl and 0.125 for three.js
    * See the issue raised on [Observable talk](https://talk.observablehq.com/t/help-loading-library-scattergl/2730)
  * The issue: [Introduction to require](https://observablehq.com/@observablehq/require) -- observable
    * Links to good resources at the bottom of this notebook
    * See especially "Requiring stubborn add-ons"
  * The solution: [ScatterGL npm](https://observablehq.com/d/b768018727ec3939)
    * QUESTION: What can you say about performance from this demo?

## In-Class Exercise -- Scatter-GL penguins

Visualize the [Palmer Penguins](https://github.com/allisonhorst/palmerpenguins#palmerpenguins-) with Scatter-GL (use default colors).

* [Solution](./scattergl.md)

## In Class Exercise -- Colorful penguins

Color the penguins by species

* [Solution](./scattergl.md#exercise-2----colorful-penguins)

## In Class Exercise -- Hover color

Get the color to turn black on hover

* [Solution](./scattergl.md#exercise-3----change-color-on-hover)
