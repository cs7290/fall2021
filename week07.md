# Week 7

## Topics

* Event-driven UI elements
* d3-brush
* Customizing d3-brush

## Events and Event Listeners

* [Introduction to Events](https://developer.mozilla.org/en-US/docs/Learn/JavaScript/Building_blocks/Events) -- MDN
  * [A simple example](https://developer.mozilla.org/en-US/docs/Learn/JavaScript/Building_blocks/Events#a_simple_example)
  * This example uses vanilla JavaScript with a `<button>` element
  * It implements the [EventTarget](https://developer.mozilla.org/en-US/docs/Web/API/EventTarget) interface
* [Web Events](https://developer.mozilla.org/en-US/docs/Web/Events) -- MDN
  * JavaScript Events are "fired" to notify code of "interesting changes" that may affect code execution. 
  * These may be associated with user interactions (using a mouse or resizing a window) or other things.
  * The MDN reference (above) has an extensive list of Events
  * Each event is represented by an object that implements the [Event interface](https://developer.mozilla.org/en-US/docs/Web/API/Event)
  * DEMO -- Use `<a>` element's "click" listener to trigger an action
    * [Event Listeners](https://observablehq.com/@mbostock/event-listeners#)
    * In section "1. Hypertext Literal" change the `href` attribute from `href="#"` to `href="#click"`
      * This change makes it easier to see what happens when you click on a link
    * Every time you click a link in the list, you see the name change in the associated input element
    * No big surprise here.
* You can trigger the "click" event programmatically
  * DEMO -- programmatic UI events
    * Again in section "1. Hypertext Literal", add a unique id to each `<a>` tag
```
html `<ul>${names.map((name, i) => html`
  <li>My name is ${name}! <a id=${"my" + i} href="#click" onclick=${() => click(name)}>Pick me.</a></li>
`)}</ul>`
```
 * Note that we create the unique id by adding the index `i` (second argument) of the anonymous function call
 * Then run the next line and watch the appropriate name appear in the input element
 * `d3.select("#my0").node().dispatchEvent(new CustomEvent("click"))`
  * This demo shows how to trigger a UI event programmatically
    * that event causes the listener function to be invoked
    * that listener function then changes the value of an input element
    * Notice that if you change the event type from "click" to something else (say, "input"), then it stops working
    * That's because the listening element (an `<a>` tag) is listening for a "click" event
* DEMO -- MDN documentation has a mousemove event demo in vanilla JavaScript
  * [mousemove Event](https://developer.mozilla.org/en-US/docs/Web/API/Element/mousemove_event) -- MDN
  * the canvas drawing example shows how to create multiple event listeners
  * get the location of the mouse/touch event from the event object
  * use the locations to draw on a canvas element
* There are other ways to trigger events with vanilla JavaScript, but D3 and Observablehq make things simpler

## Views

* "In Observable, a *view* is a user interface element that directly controls a value in the notebook. 
* A view consists of two parts:
  * The *view*, which is typically an interactive DOM element.
  * The *value*, which is any JavaScript value.
* Reference: [Introduction to Views](https://observablehq.com/@observablehq/introduction-to-views) -- observablehq
  * This notebook has several examples
  * [A Brief Introduction to Viewov](https://observablehq.com/@observablehq/a-brief-introduction-to-viewof) discusses the *viewof* keyword in Observable
  * On the one hand, Observable [Inputs](https://observablehq.com/@observablehq/inputs) make it super easy to create views with standard UI elements
  * But views can be any kind of visual element
    * See [Introduction to views](https://observablehq.com/@observablehq/introduction-to-views)
    * This notebook shows how to create views that trigger reevaluation of any cell that references the views value
    * To trigger the re-evaluation of any cell that references a view’s value, the view must emit an input event.
* [*viewof stroke*](https://observablehq.com/@observablehq/introduction-to-views#viewof-stroke) recreate the canvas drawing demo
  * It's worth looking at this example in some detail
* [*viewof point*](https://observablehq.com/@observablehq/introduction-to-views#viewof-point) uses a map as an interactive view
  * the red dot confirms appropriate relocation of the mousedown or mousemove events
  * the location coordinates of the mouse on the canvas are convered to [longitude, latitude]
  * the geographic coordinates are made available as the value of the map
  * the geographic coordinates are then reprojected back onto the map as a red circle

## Exercise 1

Modify a viewof demo in [Introduction to Views](https://observablehq.com/@observablehq/introduction-to-views)

* EXERCISE: Change `viewof stroke` in [Introduction to Views](https://observablehq.com/@observablehq/introduction-to-views) so that it reports the mouse position as its value
* SOLUTION: [Solution to Exercise 1](./exercises07.md#exercise-1)

## d3-brush

* [d3-brush](https://observablehq.com/collection/@d3/d3-brush) -- collection
  * It's worth investigating some demo from this remarkable collection of notebooks

## Exercise 2

Turn a brush into a view

* EXERCISE: Turn [Empty Brush Selection](https://observablehq.com/@d3/empty-brush-selection) into a "view"
  * See: [Introduction to views](https://observablehq.com/@observablehq/introduction-to-views)
* SOLUTION: [Solution to Exercise 2](./exercises07.md#exercise-2)

## Exercise 3

Same as above, but without D3.

* EXERCISE: Repeat Exercise 1, but this time without using D3.
* SOLUTION: [Solution to Exercise 3](./exercises07.md#exercise-3)

## Mutable

* [mutable values](https://observablehq.com/@mbostock/mutable-values)
* This notebook has a brief demo of mutable reporting on internal cell state with a button click

## Exercise 4

Reporting events with a mutable

* EXERCISE: Use [mutable values](https://observablehq.com/@mbostock/mutable-values) to report event types and mouse location when clicking the button in the notebook.
* SOLUTION: [Solution to Exercise 4](./exercises07.md#exercise-4)

# Range Slider

* Range slider -- history and current state
  * [Input: Range](https://observablehq.com/@observablehq/input-range) -- current state
    * Based entirely on web standards
    * Built-in styling is browser-dependent
    * There is no easy way to combine minimum & maximum values in same slider
  * [Range slider](https://observablehq.com/@mootari/range-slider) -- min & max
    * Min & max values in a single slider
    * CSS styling mimics browser-dependent styles
    * Browser-independent appearance (so you won't want to combine this with other inputs)
  * Observable history
    * [Inputs](https://observablehq.com/@tmcw/inputs/2) by tmcw
    * [Inputs](https://observablehq.com/@jashkenas/inputs) by jashkenas

## Hover

* Detecting hover elements
  * We can detect hovered elements using the ":hover" selector
  * This allows us to detect hovered elements of the brush (note the order in which they're placed in the SVG)
  * Thing is, we want to change the color of elements underneath that we're using to visualize the slider"
    * So we do it with a little JavaScript
* What you need to know
  * [selection.call()](https://github.com/d3/d3-selection#selection_call) API reference -- github
  * [*this* keyword](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/this) -- MDN
  * [*this* values in Observable](https://observablehq.com/@tmcw/untitled/5)
    * What's "this"? -- it's used in the call to brushHandle()
  * [d3.arc](https://github.com/d3/d3-shape#arc) -- it's used for the brush handle
  * [d3-brush API reference](https://github.com/d3/d3-brush) -- github
    * The reference lays out the structure so you can "select" and modify it
    * [SVG layout of the brush](https://github.com/d3/d3-brush#_brush)

## Exercise 5

* EXERCISE: Report events hovered element when moving the mouse over the brush.
* SOLUTION: [Solution to Exercise 5](./exercises07.md#exercise-5)
