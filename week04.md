# Week 4

## Topics

* Animation (Assignment 03 solution)
* Telling a story (projects)
* [Plot](./plot2.md) and Dashboard (continued from [week03.md](./week03.md))

## Animation

* [America's Cup](https://archive.nytimes.com/www.nytimes.com/interactive/2013/09/25/sports/americas-cup-course.html)
  * America's cup animation -- discuss how it works
  * View source -- shows that it uses an early version of D3 to animate an SVG (not canvas)
* Visualizing chaos (SVG vs 2d Canvas vs WebGL)
  * [Lorenz Attractor](https://observablehq.com/@mbostock/lorenz-attractor)
  * [Lorenz Attractor II](https://observablehq.com/@mbostock/lorenz-attractor-ii)
  * [Lorenz Attractor III](https://observablehq.com/@mbostock/lorenz-attractor-iii)
* Canvas
  * Animation with [Canvas](https://developer.mozilla.org/en-US/docs/Web/API/CanvasRenderingContext2D) has been around for a while. It's fairly verbose with "vanilla" JavaScript.
  * Introduction to [Canvas](https://developer.mozilla.org/en-US/docs/Web/API/Canvas_API) -- MDN
  * [Advanced Animations](https://developer.mozilla.org/en-US/docs/Web/API/Canvas_API/Tutorial/Advanced_animations) -- MDN
  * [window.RequestAnimationFrame()](https://developer.mozilla.org/en-US/docs/Web/API/window/requestAnimationFrame) -- MDN
  * [WebGL](https://developer.mozilla.org/en-US/docs/Web/API/WebGL_API/Tutorial/Getting_started_with_WebGL) is more difficult still
* Animation is easier with Observable
  * [Animation Loops](https://observablehq.com/@mbostock/animation-loops)
  * [Introduction to Generators](https://observablehq.com/@observablehq/introduction-to-generators)
* You can dig into the details, but it starts becoming subtle
  * [Pause a generator](https://observablehq.com/@mbostock/pause-a-generator)
    * technique for pausing a generator (in Observable)
    * uses "this" from the standard library to access the previous value
    * [standard library](https://github.com/observablehq/stdlib)
  * Vanilla generators aren't any easier
    * [Generator](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Generator) -- MDN
      * The MDN reference shows how Generators work with vanilla JavaScript
      * Note how IE doesn't support generators
    * [yield](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/yield) -- MDN 
      * Also has a nice example of vanilla JavaScript

## Assignment03 solutions

* [Assignment03 solutions](./assignment03_solutions.md)
* [My solution](https://observablehq.com/d/00e2a852f2a4fd14) (after completing the exercise below)

## Exercise

* [Introduction to Mutable State](https://observablehq.com/@observablehq/introduction-to-mutable-state)
* Look the cell called "mutableWalls"
* Reproduce this cell with an SVG
* [the solution](https://observablehq.com/d/67483f66e715c57a)

**STOPPED HERE**

## Projects

Telling a story with data

* Dashboards vs insights
* Single-family: http://pbogden.com/single
* Engaging stakeholders -- some options...
  * Update on [stinky](https://github.com/ds5110/stinky)
  * Update on [Service-Learning](https://communityengagement.northeastern.edu/programs/service-learning/)
  * Update on [observable-jupyter](https://github.com/thomasballinger/observable-jupyter)

## Dashboards

* [Plot II](./plot2.md)
* See [week03.md](./week03.md)

## Plot tooltips

* Learning goals
  * Show how D3 is used to add CSS styles to Plots elements
* [Plot tooltip](https://observablehq.com/@mkfreeman/plot-tooltip) -- Mike Freeman
  * add a "title" attribute to any mark
  * addTooltips() is a function takes a chart as its first argument
  * Adds <style> to the chart to the chart to the chart to the chart (right before returning the chart)
* [Plot animation](https://observablehq.com/@mkfreeman/plot-animation)
