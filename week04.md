# Week 4

## Topics

* Animation (Assignment 03 solution)
* Telling a story (projects)
* Dashboards with [Plot](./plot2.md)

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

The purpose of the projects -- tell a story with data

* Dashboards vs Insights
  * [Four Ways to Slice Obama's Budget](https://archive.nytimes.com/www.nytimes.com/interactive/2012/02/13/us/politics/2013-budget-proposal-graphic.html)
* What is data visualization anyway?
  * Case study: NYTimes article on the America's Cup
  * Case study: http://pbogden.com/single
  * Case study: Myth debunked
* Engaging stakeholders for your project -- some options...
  * Update on [stinky](https://github.com/ds5110/stinky)
    * Smell data
    * Meteorological data
  * Update on [Service-Learning](https://communityengagement.northeastern.edu/programs/service-learning/)
  * Update on [observable-jupyter](https://github.com/thomasballinger/observable-jupyter)
    * [robservable gallery](https://juba.github.io/robservable/articles/gallery.html)
  * Do you have an idea for a project?
    * Think about it...

## Animation

[animation.md](./animation.md) -- additional (advanced) comments about animation and Observable.

## viewof

* [Introduction to views](https://observablehq.com/@observablehq/introduction-to-views)
  * In Observable, a view is a user interface element that directly controls a value in the notebook
  * A view consists of 2 parts:
    * the view itself, which is typically an interactive DOM element
    * the value, which is any JavaScript value
  * HTML input elements work by default as views for two reasons:
    * they have a value property
    * they emit input events when you interact with them
    * [Input event](https://developer.mozilla.org/en-US/docs/Web/API/HTMLElement/input_event) -- MDN
      * this reference has a nice example that shows how it works in vanilla javascript
      * it's fairly cumbersome, but it works
  * [Observable Inputs](https://observablehq.com/@observablehq/inputs) are more convenient than native HTML
    * Plus, you can create custom inputs
    * For example, the map that behaves like an input element when you click on it
      * It dispatches an "input" event when you do that (you can see it in the code)
    * The silly emoticon is also an input element, and counter
* [A Brief Introduction to viewof](https://observablehq.com/@observablehq/a-brief-introduction-to-viewof)
  * This notebook provides a look under the hood of "viewof"
  * It discusses the extra logic for dealing with "idiosyncrasies"

## Dashboard

* [Dashboard](https://observablehq.com/@mbostock/dashboard)
  * Shows how to create a Dashboard with imported cells
  * How do you create an interactive Dashboard (i.e., dashboard with interactive charts)?
  * [Earthquake Dashboard](https://observablehq.com/@pbogden/earthquake-dashboard)
* [Responsive design](https://developer.mozilla.org/en-US/docs/Learn/CSS/CSS_layout/Responsive_Design)
  * describes this evolution of web page layouts to accommodate mobile devices
  * explains the purpose of `<meta name="viewport" content="width=device-width,initial-scale=1">`
  * introduces [CSS Grid Layout](https://developer.mozilla.org/en-US/docs/Learn/CSS/CSS_layout/Grids)
  * [CSS Grid Layout](https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_Grid_Layout)
    * `python -m http.server`
    * browse to http://localhost:8000/index3.html
* With Observable Dashboard
  * How do you set the width?
  * How do you set the height?

## Exercise

* Start with https://observablehq.com/@mbostock/dashboard
* Replace on of the charts with https://observablehq.com/@d3/world-airports
* [Solution](./solution.md)

## Interactive Plot in a Dashboard

* [Plot Early Bird](https://observablehq.com/@fil/plot-early-bird)
* [Plot.brush()](https://observablehq.com/@fil/plot-brush-71)
  * [My Plot.brush()](https://observablehq.com/d/e92ee4710f38237f)
* [My Dashboard with Plot.brush()](https://observablehq.com/d/0c28e2b73ff337d2)
  * note the use of "viewof"

## Observable Plot (Take 2)

* Learning goals
  * Practice with the Plot API 
  * Show how D3 is used to add CSS styles to Plots elements
  * Explore where Plot is going
* [Plot II](./plot2.md)
* [Plot tooltip](https://observablehq.com/@mkfreeman/plot-tooltip) -- Mike Freeman
  * add a "title" attribute to any mark
  * addTooltips() is a function takes a chart as its first argument
  * Adds <style> to the chart to the chart to the chart to the chart (right before returning the chart)
* [Plot animation](https://observablehq.com/@mkfreeman/plot-animation)
