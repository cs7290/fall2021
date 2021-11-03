
# Choropleth

* [Choropleth](https://observablehq.com/@d3/choropleth)
  * This is county-level choropleth
  * Note about tooltips: This choropleth has a built-in SVG tooltip
    * implemented with [SVG `<title>` element](https://developer.mozilla.org/en-US/docs/Web/SVG/Element/title)
    * [Observable Plot](https://github.com/observablehq/plot/blob/main/README.md) implements tooltips the same way
      * each mark has an optional "title" channel -- if you provide a value, it'll show up as an SVG `<title>`
      * the other channels: "fill", "fillOpacity", "stroke", "strokeOpacity", "strokeWidth"
    * Note: SVG `<title>` is *not* the same as the [HTML document `<title>`](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/title)
* [My Zoom to Bounding Box](https://observablehq.com/@pbogden/my-zoom-to-bounding-box)
  * Adds pan and zoom capabilities to the county-level choropleth
    * also adds clickable [d3-transitions](https://github.com/d3/d3-transition) for zooming in/out on a state
  * I created this because zooming a county-level SVG can have performance issues
* [State Choropleth](https://observablehq.com/@d3/state-choropleth)
  * we're going to customize this below
  * topojson has 2-character ID and state name
* TODO: discuss color scale

## EXERCISE #1: Circle

Add a circle that follows the mouse to [State Choropleth](https://observablehq.com/@d3/state-choropleth)

* Hints:
  * Use [d3.pointer](https://github.com/d3/d3-selection/blob/main/README.md#pointer)
    * `d3.pointer(event)` is part of [d3-selection](https://github.com/d3/d3-selection/blob/main/README.md)
  * For more hints, look at the implementation of [Plot Tooltip](https://observablehq.com/@mkfreeman/plot-tooltip)
* SOLUTION
  * [State Choropleth (w/tooltip)](https://observablehq.com/d/a86a048022e9fe27)
  * First: add a circle that will follow the mouse
    * `const circle = svg.append("circle").attr("r", 10)`
    * That line should appear **after** the code that draws the states and state boundaries
      * Otherwise it will appear underneath those elements
    * When you add the line, you should see 1/4 of the circle in the upper left corner, where `x = y = 0`
      * That's because we have yet to set the values for `cx` and `cy`
  * Second, declare `function mousemoved(event) {}`, which will determine the circle position based on the mouse event
    ```
    function mousemoved(event) {
      const pointer = d3.pointer(event, svg.node());
      circle.attr("cx", pointer[0])
        .attr('cy', pointer[1])
      // mutable z = pointer  // use this to inspect the mouse location (add a `mutable z` cell to the notebook)
    }
    ```
    * You can place this anywhere inside the cell.
      * Arbitrary placement in the cell is due to [Hoisting](https://developer.mozilla.org/en-US/docs/Glossary/Hoisting)  in JavaScript.
  * Third, add an event listener to the SVG
    * Add `svg.on("mousemove", mousemoved)` somewhere in the cell.
    * You can do it by changing
    ```
    const svg = d3.create("svg")
      .attr("viewBox", [0, 0, 975, 610]);
    ````
    to
    ```
    const svg = d3.create("svg")
      .attr("viewBox", [0, 0, 975, 610])
      .on('mousemove', mousemoved);
    ```
    * Note: the technique for getting the circle to follow the mouse on the map
in [Introduction to Views](https://observablehq.com/@observablehq/introduction-to-views#viewof-point) 
is significantly more subtle 
       * That example uses [layerX and layerY](https://developer.mozilla.org/en-US/docs/Web/API/UIEvent/layerX), which is **non-standard**!!
  * When you add an event listener for `mousemove`
    * If you add it to the states, then you can use it below for data-dependent styling or a tooltip
      * To put it on states, move the line: `.on("mousemove", mousemoved)` after: `.join("path")`
  * **TODO** Show what happens when you change the location of `.on("mousemove", mousemoved)`
    * If you put it on the main SVG, then the circle goes anywhere
    * If you put it on the "g" with the legend, it only moves if you mouse over the legend
    * If you put it on the states, then it won't move outside the states

## EXERCISE #2: Styling

Update the styling to highlight the state that's being moused over

* Again, get hints from here: [Plot Tooltip](https://observablehq.com/@mkfreeman/plot-tooltip)
* [d3.select()](https://github.com/d3/d3-selection#select) -- tells you about `this`
  * You'll use `this` to select a state
  * You can also use `this` to get the data value that's bound to the state
* If you change the implementation to
```
  const states = svg.append("g")
    .selectAll("path")
    .data(topojson.feature(us, us.objects.states).features)
    .join("path")
      .attr("fill", d => color(data.get(d.properties.name)))
      .attr("d", path)
      .on("mousemove", mousemoved)
      .on("mouseout", mousedout)
    .append("title")
      .text(d => `${d.properties.name}
${format(data.get(d.properties.name))}`);
```
* Then update `function mousemoved()` to include the following...
```
    d3.select(this).attr('fill', 'crimson')
```
* And add `function mousedout()` as follows (using `this` to get the bound datum)
```
  function mousedout(event) {
    const d = d3.select(this).data()[0];
    d3.select(this).attr('fill', color(data.get(d.properties.name)));
  }
```
* If the circle is still there, then you'll have to add `.attr("pointer-events", "none")`
  * Otherwise the circle will be underneath the mouse, and the states' `<path>` elements will never detect mouse events

## EXERCISE #3: Tooltip

Add a tooltip that shows the data value as it follows the mouse

