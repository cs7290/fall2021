# Exercises 07

## Exercise 1

Modifying a view in [Introduction to Views](https://observablehq.com/@observablehq/introduction-to-views)

* EXERCISE: Change `viewof stroke` in [Introduction to Views](https://observablehq.com/@observablehq/introduction-to-views) so that it reports the mouse position as its value
* SOLUTION
  * Put the next line right above this line: `canvas.dispatchEvent(new CustomEvent("input"));`
  * `canvas.value = [event.type, event.layerX, event.layerY]`

## Exercise 2

Turn a brush into a view

* EXERCISE: Turn [Empty Brush Selection](https://observablehq.com/@d3/empty-brush-selection) into a "view"
  * See: [Introduction to views](https://observablehq.com/@observablehq/introduction-to-views)
* SOLUTION:
  * Change `chart` to `viewof chart`
  * In `function brushed()` on the last line, add:
    * `svg.property("value", selection).dispatch("input");`
    * Note: you can do this as a copy and paste, without really understanding what's going on. Hence the next exercise.

## Exercise 3

Same as above, but without D3.

* EXERCISE: Repeat Exercise 1, but this time without using D3.
* SOLUTION:
  * Instead of this line:
    * `svg.property("value", selection).dispatch("input");`
  * Use the following 2 lines:
    * `svg.node().value = selection;`
    * `svg.node().dispatchEvent(new CustomEvent("input"));`

## Exercise 4

Report events with a mutable

* EXERCISE: Use [mutable values](https://observablehq.com/@mbostock/mutable-values) to report event types and mouse location when clicking the button in the [mutable values](https://observablehq.com/@mbostock/mutable-values) notebook.
* SOLUTION:
  * Add a mutable: `mutable z = 42`
  * Then modify the `button.onclick` line to
  * `button.onclick = (event) => { ++mutable x; mutable z = [event.type, event.clientX, event.clientY] }`

## Exercise 5

Report [mouse events](https://developer.mozilla.org/en-US/docs/Web/API/Element#mouse_events) and "[:hover](https://developer.mozilla.org/en-US/docs/Web/CSS/:hover)"ed element with a mutable.

* EXERCISE: Use [mutable values](https://observablehq.com/@mbostock/mutable-values) to report event types 
and the element being hovered over when you're moving the mouse over the brush.
for [Empty Brush Selection](https://observablehq.com/@d3/empty-brush-selection?collection=@d3/d3-brush)
* SOLUTION:
  * Add a mutable cell, e.g.: `mutable z = 42`
  * Change: 
```
  const circle = svg.append("g")
      .attr("fill-opacity", 0.2)
    .selectAll("circle")
    .data(Float64Array.from({length: 800}, Math.random))
    .join("circle")
      .attr("transform", d => `translate(${x(d)},${y()})`)
      .attr("r", 3.5);
```
to
```
  const g = svg.append("g")

  g.call(brush)
      .call(brush.move, [0.3, 0.5].map(x));

  g.on('mousemove', mousemoved)

  function mousemoved(event) {
    mutable z = ['MOUSEMOVE', event.type, d3.select(this).select(":hover").attr('class')];
  }
```
* The following elements should be selectable with ":hover"
  * `.overlay`
  * `.handle--custom`
  * `.selection`

## Exercise 6

Custom brush styling.

* EXERCISE: Adapt the [Empty Brush Selection](https://observablehq.com/@d3/empty-brush-selection) so that it looks like a 2-handle range slider.
  * Hint: First remove the data and axes, then add the blue & gray slider channels.
  * Note: This is worth doing in class -- debugging errors encountered in the solution could be informative.
* SOLUTION:
  * Remove the `circle` (i.e., random data visualization) and axes
  * Add slider channels (gray and blue parts)
```
  // Add the background slider channel (the gray/unselected part)
  const strokeWidth = 1;
  g.insert('rect', '.overlay')   // Add the slider channel
      .attr("x", margin.left)
      .attr("y", margin.top + radius / 2 + strokeWidth)
      .attr("height", radius - 2 * strokeWidth)
      .attr("width", width - margin.right - margin.left)
      .attr("rx", radius / 2)
      .attr("fill", "#ddd")
      .attr("stroke", "#aaa")  // default gray stroke
      .attr("stroke-width", strokeWidth)

  // Add the "selected" slider channel (blue part)
  const channel = g.insert('rect', '.overlay')
    .attr('class', 'custom-channel')
    .attr("x", margin.left)
    .attr("y", margin.top + radius / 2)
    .attr("height", radius)
    .attr("width", width - margin.right - margin.left)
    .attr("rx", radius / 2)
    .attr("fill", 'steelblue')
```
    * NOTE: You can change the size of the blue part pretty easily (something to do with the brush)
  * Set the size of the blue part of the channel according to the brush selection
    * In `function brushed`, add this line:
```
    channel.attr('x', selection[0]).attr('width', selection[1] - selection[0]);
```
    * Note: this will throw an error because "channel" is not defined.
      * ReferenceError: Cannot access 'channel' before initialization
      * The error points to this line: `.call(brush.move, [0.3, 0.5].map(x));`
      * That's because this line invokes `function brush`, which references "channel"
      * Fix it by moving the line above below the splot where "channel" is defined.
  * The rest of the styling can be done for homework.
```
