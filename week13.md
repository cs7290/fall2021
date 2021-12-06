
# Week 13

* 3D
* WebGL vs SVG
* scatter-gl

## Scatterplot tour with penguins

* [Scatterplot Tour](https://observablehq.com/@d3/scatterplot-tour)
* Scatterplot tour using the [Palmer Penguins](https://github.com/allisonhorst/palmerpenguins#palmerpenguins-)
  * [Solution](https://observablehq.com/d/e6569c4e3860e806)
  * Only two cells needed to change.
  * [Detail instructions](./zoom.md)

**Picking up from week 11**

## WebGL

Demos above allowed us to start seeing the 
[performance](https://developer.mozilla.org/en-US/docs/Web/Performance) limitations of 
[DOM manipulation](https://developer.mozilla.org/en-US/docs/Learn/JavaScript/Client-side_web_APIs/Manipulating_documents).

* [WebGL API](https://developer.mozilla.org/en-US/docs/Web/API/WebGL_API) -- MDN
  * WebGL is a JavaScript API for rendering high-performance interactive 3D and 2D graphics.
  * It uses HTML5 `<canvas>` elements -- without plugins -- in any compatible web browser.
  * In particular, the user's device must have supporting hardware (Graphical Processing Unit = GPU).
  * WebGL closely conforms to [OpenGL ES 2.0](https://en.wikipedia.org/wiki/OpenGL_ES)
  * WebGL programs consist of control code (JavaScript) and special effects code (shader code) executed on a GPU. 
  * WebGL elements can be mixed with other HTML elements.
* [WebGL Tutorial](https://developer.mozilla.org/en-US/docs/Web/API/WebGL_API/Tutorial) -- MDN
  * The tutorial has some good background links, including this one on OpenGL...
  * [An Introduction to OpenGL](https://duriansoftware.com/joe/an-intro-to-modern-opengl.-table-of-contents)
* For example
  * [LiquidFun](https://observablehq.com/@mbostock/liquidfun?collection=@observablehq/webgl) -- mbostock notebook
  * [LiquidFun](http://google.github.io/liquidfun/) -- google.github.io

## Intro tutorials

* [MDN WebGL Demo #2](https://observablehq.com/@tmcw/mdn-webgl-demo-2?collection=@observablehq/webgl) -- tmcw notebook
* [Hello, Fragment Shader](https://observablehq.com/@mbostock/hello-fragment-shader) -- mbostock notebook
* [Hello, WebGL](https://bl.ocks.org/mbostock/5440492) -- mbostock block (circa 2013)
  * This introductory tutorial demonstrates how to use the WebGL API.
  * Notice the amount of work you need to do simply for setup.

## Three.js

Three.js makes WebGL usable.

* [Three.js](https://threejs.org/)
* [Hello, Three.js!](https://observablehq.com/@mbostock/hello-three-js)

## Deck.gl

Deck.gl is a relative newcomer.

* [Deck.gl](http://deck.gl)
* [Deck.gl](https://github.com/visgl/deck.gl) -- github
* [Degk.gl tutorials](https://observablehq.com/@pessimistress/deck-gl-tutorial) -- observable notebooks

## Scatter-GL

Scatter-GL is an interactive 3D / 2D webgl-accelerated scatter plot point renderer.

* It's the core functionality behind Google's [Embedding projector](http://projector.tensorflow.org/)
* It's built with [Three.js](https://threejs.org/)
* [scatter-gl](https://github.com/PAIR-code/scatter-gl#scattergl) -- github
  * To run the demo
  ```
  cd ~/Sites/scatter-gl
  yarn
  yarn demo
  ```
  Browse to http://localhost:8080

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
    * Load the library
    ```
    ScatterGL = {
      const { ScatterGL } = await require.alias({
        THREE: "three@0.125/build/three.min.js"
      })("scatter-gl@0.0.10");
      return ScatterGL;
    }
    ```
    * Render some dots
    ```
    {
      const points = Array(100)
        .fill()
        .map(e => [Math.random() * 100, Math.random() * 100, Math.random() * 100]);
      const containerElement = DOM.element('div');
      containerElement.style.height = "500px";
      yield containerElement;
      const dataset = new ScatterGL.Dataset(points);
      const scatterGL = new ScatterGL(containerElement);
      scatterGL.render(dataset);
    }
    ```
  * QUESTION #1: What can you say about performance from this demo?
  * QUESTION #2: What happens when you run the render cell many times in rapid succession?
    * Hint: [How to dispose of objects](https://threejs.org/docs/#manual/en/introduction/How-to-dispose-of-objects)
    * Compare with [Hello, Three.js!](https://observablehq.com/@mbostock/hello-three-js)

## In-Class Exercise -- Scatter-GL penguins

Visualize the [Palmer Penguins](https://github.com/allisonhorst/palmerpenguins#palmerpenguins-) with Scatter-GL (use default colors).

* [Solution](./scattergl.md)

## In Class Exercise -- Colorful penguins

Color the penguins by species

* [Solution](./scattergl.md#exercise-2----colorful-penguins)

## In Class Exercise -- Hover color

Get the color to turn black on hover

* [Solution](./scattergl.md#exercise-3----change-color-on-hover)
