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

Report events with a mutable

* EXERCISE: Use [mutable values](https://observablehq.com/@mbostock/mutable-values) to report event types and mouse location when clicking the button in the [mutable values](https://observablehq.com/@mbostock/mutable-values) notebook.
* SOLUTION: [Solution to Exercise 4](./exercises07.md#exercise-4)

**STOPPED HERE ON MONDAY**

## Range Slider

Range slider -- history and current state

* Observable inputs -- the history
  * [Inputs](https://observablehq.com/@jashkenas/inputs) by jashkenas
  * [Inputs](https://observablehq.com/@tmcw/inputs/2) by tmcw (adds a "cautious" option)
* [Input: Range](https://observablehq.com/@observablehq/input-range) -- current state
  * Good: Input elements based entirely on web standards
  * Not so good: Built-in styling is browser-dependent
  * Not so good: There is no easy way to adjust both the minimum & maximum values in a single input element
* [Range slider](https://observablehq.com/@mootari/range-slider) -- min & max
  * Good: Adjustable min & max of range in a single slider with optional styling
  * Not so good: CSS styling mimics browser-dependent styles and behavior
  * Not so good: Customizing CSS is a huge challenge
  * Not so good: You need to do more work if you want to mimic browser-dependent styling of built-in input elements
* QUESTION: Could you customize [Empty Brush Selection](https://observablehq.com/@d3/empty-brush-selection)
and turn it into a 2-handle range slider?
  * What sort of interactive functionality would you need?  HINT: See Exercise 5 (below)
  * How would you style it? How hard would it be?  HINT: See Exercise 6 (below)

## :hover

* [:hover](https://developer.mozilla.org/en-US/docs/Web/CSS/:hover) -- MDN
  * The :hover CSS pseudo-class matches when the user interacts with an element with a pointing device, 
  * But a `:hover` event does not necessarily activate the element.
* [The `<style>` element](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/style)
  * In-line styles take precedence over external CSS style sheets
  * `style` attributes override even in-line styles.
* [Multiple style elements](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/style#multiple_style_elements)
  * Multiple `<style>` and `<link>` elements are applied to the DOM in the order they are included in the document.
  * This example shows how conflicting styles are resolved (last one wins)
* Look at the styling and behavior or [Input: Range](https://observablehq.com/@observablehq/input-range)
  * Color changes during hover and selection.
  * Need to distinguish the handle and the channel
* Styling hovered elements
  * We can select hovered elements using the CSS ":hover" selector
  * This allows us to identify hovered elements of the brush
  * Note the order in which they're placed in the SVG.
  * Thing is, we want to change the color of elements underneath that we're using to visualize the slider"
    * So we do it with a little JavaScript
* [d3-brush events](https://github.com/d3/d3-brush#brush_on) -- github
  * There are several types of "brush events"
  * Listeners for these events are registered when you invoke `selection.call(brush, callback)`
* [*brush(group)*](https://github.com/d3/d3-brush#_brush) API reference describes what happens.
  * IMPORTANT: the brush creates the SVG elements necessary for display and to receive input events for interaction.
  * The SVG elements can be modified, removed, styled, etc.
  * As you can see from [Empty Brush Selection](https://observablehq.com/@d3/empty-brush-selection), "mousemove" add "mouseout" are being used to change the pointer style

## Empty Brush Selection

How it works

* [D3 api reference](https://github.com/d3/d3/blob/main/API.md)
  * Lays out the D3 hierarchy and links to the detailed API reference docs
  * Come here if you want to find out what's going on
* [d3.create("svg")](https://github.com/d3/d3-selection/blob/v3.0.0/README.md#create)
  * It's part of [d3-selection](https://github.com/d3/d3-selection)
* [d3.brushX](https://github.com/d3/d3-brush/blob/v3.0.0/README.md#brushX)
  * [brush(group)](https://github.com/d3/d3-brush/blob/v3.0.0/README.md#_brush)
    * applies brush to the specified group
  * [brush.on(typenames, listener)](https://github.com/d3/d3-brush/blob/v3.0.0/README.md#brush_on)
    * sets the event listener(s) for the specified typename(s) and returns the brush.
* [d3-selection](https://observablehq.com/@d3/d3-selection-2-0?collection=@d3/d3-selection)
  * [selection.append()](https://github.com/d3/d3-selection#selection_append)
  * [selection.data()](https://github.com/d3/d3-selection#selection_data)
    * Binds the specified array of data with the selected elements
    * Returns a new selection that represents the update selection
  * [selection.join()](https://github.com/d3/d3-selection#selection_join)
    * This is the essence of the D in D3 -- Data-Driven Documents
    * [Joining Data](https://github.com/d3/d3-selection#joining-data)
    * [selection.join notebook](https://observablehq.com/@d3/selection-join)
  * [selection.call()](https://github.com/d3/d3-selection#selection_call)
  * [*this* keyword](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/this) -- MDN 
  * [*this* values in Observable](https://observablehq.com/@tmcw/untitled/5)
    * What's "this"? -- it's used in the call to brushHandle()
  * [d3.arc](https://github.com/d3/d3-shape#arc) -- it's used for the brush handle
  * [d3-brush API reference](https://github.com/d3/d3-brush) -- github
    * The reference lays out the structure so you can "select" and modify it
    * [SVG layout of the brush](https://github.com/d3/d3-brush#_brush)
    * There are several elements involved in event detection:
      * `.overlay`
      * `.handle--custom`
      * `.selection`
  * Bubbling and capture of events
    * [Introduction to Events](https://developer.mozilla.org/en-US/docs/Learn/JavaScript/Building_blocks/Events)
    * Q: Why do I care? A: Becuase event bubbling in the DOM means that some DOM elements won't know about events.
    * And sometimes events can be prevented from bubbling all the way up to the DOM
  * [Event Bubble and Capture](https://developer.mozilla.org/en-US/docs/Learn/JavaScript/Building_blocks/Events#event_bubbling_and_capture) -- MDN
    * Nice example showing what happens during capturing and bubbling phases of a click event.
    * Also shows the hierarchy of nested div elements with hover-dependent fill
* [User Manual](https://observablehq.com/@observablehq/user-manual) -- collection of good stuff

## Exercise 5

Report mouse events and `hover:`ed elements.

* EXERCISE: Adapt the [Empty Brush Selection](https://observablehq.com/@d3/empty-brush-selection) to
report [mouse events](https://developer.mozilla.org/en-US/docs/Web/API/Element#mouse_events) 
and "[:hover](https://developer.mozilla.org/en-US/docs/Web/CSS/:hover)"ed element with a mutable.
Report event types and identify the specific element being hovered.
* SOLUTION: [Solution to Exercise 5](./exercises07.md#exercise-5)

## Exercise 6

Custom brush styling.

* EXERCISE: Adapt the [Empty Brush Selection](https://observablehq.com/@d3/empty-brush-selection) so that it looks like a 2-handle range slider.
  * Hint: First remove the data and axes, then add the blue & gray slider channels.
  * Note: This is worth doing in class -- debugging errors encountered in the solution could be informative.
* SOLUTION: [Solution to Exercise 6](./exercises07.md#exercise-6)
