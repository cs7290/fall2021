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
