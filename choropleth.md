
# Choropleth

* [Choropleth](https://observablehq.com/@d3/choropleth)
  * Note: This choropleth has a tooltip, implemented using the built-in [SVG `<title>` element](https://developer.mozilla.org/en-US/docs/Web/SVG/Element/title)
  * That's also the way [Observable Plot](https://github.com/observablehq/plot/blob/main/README.md) implements tooltips for marks
    * each mark has an optional "title" channel
    * the other channels: "fill", "fillOpacity", "stroke", "strokeOpacity", "strokeWidth"
  * Note: the SVG `<title>` is *not* the same as the [HTML document `<title>`](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/title)
* [My Zoom to Bounding Box](https://observablehq.com/@pbogden/my-zoom-to-bounding-box)
  * Adds pan and zoom capabilities with clickable [d3-transitions](https://github.com/d3/d3-transition)
  * I created this because zooming an SVG with every county had performance issues
* [State Choropleth](https://observablehq.com/@d3/state-choropleth)
  * topojson has 2-character ID and state name
* TODO: discuss color scale

## EXERCISE #1: Circle

Add a circle that follows the mouse

* Use [d3.pointer](https://github.com/d3/d3-selection/blob/main/README.md#pointer)
  * `d3.pointer(event)` is part of [d3-selection](https://github.com/d3/d3-selection/blob/main/README.md)
  * Get hints from [Plot Tooltip](https://observablehq.com/@mkfreeman/plot-tooltip)
* First, add an event listener to the SVG
  * immediately following the line: `  const svg = d3.create("svg")`
  * add the line: `     .on("mousemove", mousemoved)`
  * then declare `function mousemoved(event) {}`
  * Note: [Hoisting](https://developer.mozilla.org/en-US/docs/Glossary/Hoisting) means we can add the function declaration anywhere inside the cell.
  * Note: the technique in [Introduction to Views](https://observablehq.com/@observablehq/introduction-to-views#viewof-point) is significantly more subtle
     * And it uses [layerX](https://developer.mozilla.org/en-US/docs/Web/API/UIEvent/layerX), which is **non-standard**!!
* Second: add a circle that will follow the mouse
  * Put the following line **after** states, so that it shows up on top
  * `const circle = svg.append("circle").attr("r", 10).attr("fill", "red").attr('pointer-events', "none");`
* Third: create the callback function...
```
  function mousemoved(event) {
    const pointer = d3.pointer(event, svg.node());
    circle.attr("cx", pointer[0])
      .attr('cy', pointer[1])
    // mutable z = pointer  // use this to inspect the mouse location
  }
```
* When you add an event listener for `mousemove`
  * If you put it on the states, then you can use it for data-dependent styling or tooltip
  * To put it on states, then after: `    .join("path")`
  * add the line: `     .on("mousemove", mousemoved)`
* **TODO** Show what happens when you change the location of `.on("mousemove", mousemoved)`
  * If you put it on the main SVG, then the circle goes anywhere
  * If you put it on the "g" with the legend, it doesn't work unless you mouse over the legend
  * If you put it on the states, then it won't extend outside the states

## EXERCISE #2: Styling

Update the styling to highlight the state that's being moused over

