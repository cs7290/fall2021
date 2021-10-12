# Week 5

Only 1 class this week -- Indigenous People's Day

## Topics

* Plot (mission & extensibility)
* How to use documentation
* Extending Plot

## Grades (so far)

* Done through assignment 3
* If you didn't ace assignment 03, then look at Canvas comments and resubmit
* Really great when there's feedback on the challenges -- also great when there's experimenting

## Mini-Projects (one more week)

* Assignment 04 deadline extended
  * intermediate progress recorded, 
  * and points added
* Mini-projects can be project proposals
* Project proposals need stakeholders
  * Stakeholders
  * What are they? 
  * What's a good stakeholder? One who describes a problem/story vs how to solve/tell it

## Why Observable Plot?

Another plotting package?!?

* [Introducing Observable Plot](https://observablehq.com/@observablehq/introducing-observable-plot)
  * Mission: help everyone make sense of the world with data. 
  * To succeed, we need to make visualization easier and faster, both to learn and to practice.  Less chore, more joy. 
  * We believe people will be more successful finding and communicating insights if they can “use vision to think” instead of wrestling with the intricacies of programming.
  * With its concise and (hopefully) memorable API, Observable Plot lets you try out ideas quickly. 
  * Yet Plot is still powerful and expressive when you need it. 
  * Plot is designed to be extended.
  * [Towards reusable charts](https://bost.ocks.org/mike/chart/)
  * [Let's make a D3 plugin](https://medium.com/@mbostock/let-s-make-a-d3-plugin-c8e697599f48)
* And Vega-Lite!?
  * [Plot and Vega-Lite](https://observablehq.com/@observablehq/plot-vega-lite)
  * Look at the table comparing the two.
  * [Python Data Viz](https://www.anaconda.com/blog/python-data-visualization-2018-why-so-many-libraries) why so many libraries?
* And Plotly?
  * [Plotly.js graphing library](https://plotly.com/javascript/)
  * [Encapsulating D3 in Plotly Dash](https://dash.plotly.com/d3-react-components)
* And D3!?
  * Plot is built with D3.
  * D3 is recommended for it's low-level approach for bespoke explanatory visualizations
    * and as a foundation for higher-level exploratory visualization tools
  * [Introducing D3-scale](https://medium.com/@mbostock/introducing-d3-scale-61980c51545f)
    * D3 espouses abstractions that are useful for any visualization application and rejects the tyranny of charts.
    * [Diamonds](https://observablehq.com/d/55be911c1c3ac463) with Plot
* And if you want to contribute to Plot's evolution?
  * [Github issues](https://github.com/observablehq/plot/issues)
  * [Awesome Plot](https://observablehq.com/@observablehq/awesome-plot) -- more links about extensibility
  * [Extending Plot](#extending-plot) (links to a section below)

## Plot II

* [plot2.md](./plot2.md) -- Beyond copy and paste
* Discusses how to use the Plot documentation

## How to use the documentation (JavaScript)

JavaScript ([ECMAScript](https://en.wikipedia.org/wiki/ECMAScript)) is a rapidly evolving language, with
new syntax arriving all the time. Stackoverflow is not always helpful.

### Case Study: Object initializers

There are several ways to initialize an object in JavaScript

* [Object Initializers](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Object_initializer)
  * [New notation in ES6 (ECMAScript 2015)](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Object_initializer#new_notations_in_ecmascript_2015)
* Try this in an Observable cell (it's concise, and new in ES6)...
```javascript
let a = 1, b = 2, c = 3;
return {a, b, c}; // What does this return?
```
* And this (it's useful for setting default values, also new in ES6)...
```javascript
let object = {b: 10};
let {a = 1, b = 2, c = 3} = object
return [a, b, c]; // What does this return?
```
### Case Study: var, let and const
* [var](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/var) -- MDN
  * The var statement declares a function-scoped or globally-scoped variable, optionally initializing it to a value.
```javascript
var x = 1;

if (x === 1) {
  var x = 2;

  console.log(x); // Expected output: ??
}

console.log(x); // expected output: ??
```
* [let](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/let) -- MDN
  * The let statement declares a block-scoped local variable, optionally initializing it to a value.
```javascript
let x = 1;

if (x === 1) {
  let x = 2;

  console.log(x); // Expected output: ??
}

console.log(x); // Expected output: ??
```
* [const](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/const)
  * Constants are block-scoped, much like variables declared using the let keyword.
  * The value of a constant can't be changed through reassignment, and it can't be redeclared.
```javascript
const number = 42;

try {
  number = 99;
} catch (err) {
  console.log(err); // Expected output: ??
}

console.log(number); // Expected output: ??
```
How about...
```javascript
const { bar } = foo; // where foo = { bar:10, baz:12 };
console.log(bar); // Expected output?
```

## Extending Plot

* Customizing and extending Plot
  * Why would you want to do such a thing? 
  * If it helps you tell a story or saves you time, you might. 
  * Case Study: SVG button
* [Plot and D3](https://observablehq.com/d/1efb997caa8bf6fe) -- Adding a Legend
  * [SVG](https://developer.mozilla.org/en-US/docs/Web/SVG/Element/svg) -- mentions embedding SVG in SVG
  * D3 comes in handy, and it's under the hood.
  * [D3 API Reference](https://github.com/d3/d3/blob/main/API.md)
