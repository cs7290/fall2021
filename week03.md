# Week 3

## Learning goals

* Styling data visualizations with CSS and D3
* Plot
* Dashboard

Note: We didn't get to Dashboards this week.

## Questions

* Ask questions
* Piazza is coming alive -- this is good!
* Asking questions can be difficult, it takes practice
    * Questions and answers are rated and ranked in stackoverflow
    * Major awards for general questions that indicate we may be going too fast and/or something isn't clear
* If possible, include a link to a notebook
    * Make it clear in the notebook where to find the issue, especially if the notebook is not throwing an error

## Clean code

* Clean code
  * It's requires discipline
  * It becomes worthwhile during development/debugging
  * It can be documentation -- clean code is self-documenting code
* Examples
  * It's the approach we're taking, and it makes amazing things possible
  * Copy-paste can work
  * Copy-paste is bad when with it's unclear what's going on with the code
* Beware of side effects
  * This can make it nearly impossible to copy/paste code
  * CSS is powerful but, as we'll see, it's a side effect

## Observable Plot

* Learning goals
  * Quick Plot for tabular data with sensible defaults (e.g., in Python: Seaborn)
  * Customizable (e.g., in Python: Seaborn is built with Matplotlib)
  * Memorable API designed with extensibility in mind (In Python, um, is that Seaborn or Matplotlib or...?)
* [Observable Plot](https://observablehq.com/@observablehq/plot) -- mbostock notebook
* [Plot vs D3 with Mike Bostock & Shirley Wu](https://www.youtube.com/watch?v=nCBog6EPvSo)
* [Observable Plot (Jupyter)](https://observablehq.com/@pbogden/observable-plot-jupyter) -- my notebook

## Assignment02 -- Plot

* Review some of the homework submissions
* [Wine Plot](https://observablehq.com/d/701ce33a3f1cbd6b)
  * Demonstrates various things about Observable Plot [./plot.md](./plot.md)
  * Show how to get data from UC Irvine Archive (CORS)
  * Data for mini project -- mention Census API
* [data.md](./data.md) -- introduction to data, await, fetch, Census, APIs, CORS
* [Plot Early Bird](https://observablehq.com/@fil/plot-early-bird)
  * Try working with Plot's experimental "BRUSH"
* Other reading (entirely optional)
  * [Plot for D3 users](https://observablehq.com/@observablehq/plot-for-d3-users) (Toph Tucker) -- notebook
    * Interesting perspective on Plot -- the philosophy, current set of capabilities, and future
    * Item 2: Scales are inferred (and there are other sensible defaults too)
    * Item 6: Seaborn-style faceting is super easy
    * Item 7: Interactivity is possible using Observable's runtime, and they're working on extensions
    * Item 8: Many plugins with new functionality already exist, or are on the way

## Interactive Plot

* [Interactive Plot](https://observablehq.com/d/42f366e930b89e5c) -- my notebook

## The DOM (an introduction)

* Basic HTML page
  * [createElement](https://developer.mozilla.org/en-US/docs/Web/API/Document/createElement#basic_example) -- MDN
    * This MDN reference compares basic HTML with same content created dynamically with JavaScript (good demo)
    * Make sure to mention that we're not going to get super into the weeds of Web technologies
    * MDN is a great resource -- bottom of the page has browser compatibility
    * Google "javascript map mdn" and look at the compatibility
    * ES6 -- [ECMAScript](https://en.wikipedia.org/wiki/ECMAScript) -- wikipedia
  * Markdown -- it gets formatted automatically by github, giving you its CSS with Jeckyl
* [Introduction to the DOM](https://developer.mozilla.org/en-US/docs/Web/API/Document_Object_Model/Introduction) -- MDN
* In Observable
  * Looking under the hood -- create an observable notebook and inspect the header
  * The page content is in an `<iframe>`, which has its own "#document" (root node)
  * There's a lot going on, but you can still "inspect" the value that gets returned from each cell.
  * In some cases, it's just some text in a `<div>` element, in other cases it can be an `<svg>`
  * That's enough "looking under the hood" for now.
  * In this course, we don't need to pay attention to these details -- this is just FYI.
  * All you need for now is a general understanding of the DOM and how it relates to a simple web page.
  * For our visualizations, we're going to be working with various DOM elements, such as SVG and canvas.

## d3-selection

* [Introduction to HTML](https://observablehq.com/@observablehq/introduction-to-html)
  * [Observable standard library](https://observablehq.com/@observablehq/stdlib)
    * Review the methods available on the standard library
  * Shows how to create HTML elements and insert them in the DOM
    * For example, next few links from MDN show how to do it with HTML and vanilla JavaScript
    * [createElement](https://developer.mozilla.org/en-US/docs/Web/API/Document/createElement)
      * Basic example in this link shows how to do it with HTML and how to do it with JavaScript
      * [basic example](https://developer.mozilla.org/en-US/docs/Web/API/Document/createElement#basic_example)
      * [div](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/div)
* [SVG circle](https://developer.mozilla.org/en-US/docs/Web/SVG/Element/circle) -- MDN
* [d3-selection](https://github.com/d3/d3-selection) -- github
  * Some fairly advanced D3 in the notebook above -- let's do something simple
  * [d3-create](https://github.com/d3/d3-selection#create) -- github
  * [d3.selection.select()](https://github.com/d3/d3-selection#select) -- github
  * [d3.selection.selectAll()](https://github.com/d3/d3-selection#select) -- github
    * you can select by tag name, class, attribute, etc.
    * the "selectors" are the same as used in CSS and vanilla JavaScript
    * [CSS selectors](https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_Selectors) -- MDN
    * [CSS selectors](https://www.w3schools.com/cssref/css_selectors.asp) -- W3schools
      * this pages has a table that's pretty good
  * [d3-selection.append()](https://github.com/d3/d3-selection#create) -- github
  * [d3-selection.append()](https://github.com/d3/d3-selection#create) -- github
  * [d3-selection.node()](https://github.com/d3/d3-selection#selection_node) -- github
  * [d3.selection.data(data)](https://github.com/d3/d3-selection#selection_data) -- github
    * If "data" **is** specified, binds the specified array of data with the selected elements
    * If "data" is **not** specified, this method returns the array of data for the selected elements.
  * In the old days, [jQuery](https://jquery.com/) provided a some of this functionality
```
{
  // Create a square <svg> 128px by 128px.
  const svg = d3.create("svg").attr("width", 128).attr("height", 128);

  // Add a circle
  const circle = svg.append("circle")
      .attr("r", 128);

  // Return the SVG to the notebook so it gets added to the DOM
  return svg.node();
}
```

## EXERCISE: SVG circle

* Center the circle in the SVG
* Add a slider that moves the circle from left to right across the page
* The Solution -- [Exercise: SVG circle](https://observablehq.com/d/991595f4b70d9f06)

## d3-array

* Arrays have .map() and .filter() functions
  * [Array.map()](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/map)
  * [Array.filter()](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/filter)
* [d3-array API reference](https://github.com/d3/d3-array) -- github
  * includes a list of built-in array methods -- you do NOT need D3 for these
  * [API reference](https://github.com/d3/d3-array#api-reference) is complementary and begins here
* [Installing](https://github.com/d3/d3-array#installing)
  * There are various ways to include d3-array methods in your web page
  * D3 (and d3-array and d3-selection) are part of Observable notebooks

## Styling with CSS-like syntax

* Learning goals
  * Introduction and practice with d3-selection and d3-array
  * Styling nodes in an SVG using the CSS or the "style" attribute
  * Setting attribute
* Styling without D3 (the hard way)
  * [document.getElementsByClassName](https://developer.mozilla.org/en-US/docs/Web/API/Document/getElementsByClassName)
  * [document.getElementsById](https://developer.mozilla.org/en-US/docs/Web/API/Document/getElementById)
  * [SFO post mentions CORS and Illustrator](https://stackoverflow.com/questions/2753732/how-to-access-svg-elements-with-javascript)
  * [iframe.contentDocument](https://developer.mozilla.org/en-US/docs/Web/API/HTMLIFrameElement/contentDocument)
  * [Scripting (SVG)](https://developer.mozilla.org/en-US/docs/Web/SVG/Scripting) -- mdn
* With D3
  * First you need to know about d3-selection -- the API reference is quite good -- go through it with in detail
  * [d3-selection](https://github.com/d3/d3-selection) -- github
* Many charts and libraries can be styled with a little CSS-like syntax
* DEMO
  * Start with this...
```
{
  // Create a square <svg> 128px by 128px.
  const svg = d3.create("svg").attr("width", 128).attr("height", 128);

  // Add a circle
  const circle = svg.append("circle")
      .attr("r", 128);

  // Return the SVG to the notebook so it gets added to the DOM
  return svg.node();
}
```
  * Add styling with an SVG attribute to the circle created above
    * `.attr('fill', 'steelblue')`
  * Show how you can add a `<style>` to the observable notebook -- this styles every circle (CSS dominates)
    * html`<style>circle {fill: crimson;}</style>`
  * Show how you can add a `<style>` directly to the SVG element using d3-select
    * `.style('fill', 'steelblue')`
    * This dominates again

## EXERCISE: Styling World Airports

Use D3 to style World Airports

* Start with [World Airports](https://observablehq.com/@d3/world-airports)
  * Create a new notebook
  * Import the necessary stuff -- `import {map, data} from "@d3/world-airports"`
  * Demo how to select all the circle nodes with D3 --`d3.select(map).selectAll("circle").nodes()`
  * Typically, data are "bound" to elements with D3
    * d3.select(map).selectAll("circle").data()`
  * Demo data-dependent operations -- with D3 selections, they're array-like
    * `d3.select(map).selectAll("circle").filter(d => d.longitude > 0).remove()`
  * [Styling Airports](https://observablehq.com/d/30583a87bf4e560d)

## Fine-tuning the SVG

* There was a question in Piazza about rotating the labels in a Plot chart.
* I don't think you can do this within Plot -- maybe, but I doubt it
* You can do it the hard way if all you're doing is fine-tuning
* The only reason I'm showing you this is because...
  * Shows how to use D3
  * Shows how you can customize CSS
  * Demonstrates things than you *can* do if you really want to
* First go here and we'll modify a chart https://observablehq.com/@observablehq/plot-marks
  * Name the SVG, to "a" then the single line of SVG chained methods should do it
  * You can look under the hood with the developer console.
```
a = Plot.dot(sales, {x: d => d.units, y: d => d.fruit}).plot({x: {label: "units →"}})
d3.select(a).selectAll("g[text-anchor='middle']")
  .selectAll("text")
  .attr('transform', 'rotate(-45)translate(-10)');
```

## EXERCISE -- earthquakes with style

Style the [earthquakes](https://observablehq.com/@pbogden/earthquakes)

* Create a new notebook -- import only what you need
* Make the earthquakes pretty
* Give them magnitude-dependent size
