
# Scatter-GL

* [scatter-gl](https://github.com/PAIR-code/scatter-gl) -- github

## Install

* Note the CDN install for a web page
* Get the version number and dependency in `package.json` -- 0.0.11 for scatter-gl and 0.125 for three.js
  * See the recommendation on [Observable talk](https://talk.observablehq.com/t/help-loading-library-scattergl/2730)
* The issue: [Introduction to require](https://observablehq.com/@observablehq/require) -- observable
  * Links to good resources at the bottom of this notebook
  * See especially "Requiring stubborn add-ons"
* The solution: [ScatterGL npm](https://observablehq.com/d/b768018727ec3939)
  * QUESTION: What can you say about performance from this demo?

## Exercise #1 -- Scatter-GL Penguins

Visualize the [Palmer Penguins](https://github.com/allisonhorst/palmerpenguins#palmerpenguins-) with Scatter-GL.

### Solution

* Load the library
```
ScatterGL = {
  const { ScatterGL } = await require.alias({
    THREE: "three@0.125/build/three.min.js"
  })("scatter-gl@0.0.11");
  return ScatterGL;
}
```
* Load the data
```
penguins = d3.csv("https://raw.githubusercontent.com/allisonhorst/palmerpenguins/master/inst/extdata/penguins.csv", 
  d3.autoType);
```
* Render the data
```
{
  const div = DOM.element("div");
  div.style.height = "500px";
  yield div;

  // Notice the data are scaled so each axes have approximately equal range
  const data = penguins.map(d => [d.bill_length_mm / 2, d.bill_depth_mm, d.flipper_length_mm / 5]);
  const dataset = new ScatterGL.Dataset(data);
  const scatterGL = new ScatterGL(div);
  scatterGL.render(dataset);
}
```

## Exercise #2 -- Colorful Penguins

Color the penguins by Species

