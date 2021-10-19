# Week 6

TODO: Copy solutions.md to the github site

TODO: Distinguish stakeholder who helps craft a story with target audience

## Logistics

* Suggestions in Observable, Links & Questions in Piazza (pls mark things as "resolved")
* Projects (set up teams and review proposals)
* Looking ahead: mapping (static and slippy), animation, d3-geo, 3-D

## Topics

* (Re)Introduce D3
* Data wrangling (D3 and vanilla JavaScript)
* Interaction with D3 & Plot

## D3

* [Learn D3](https://observablehq.com/@d3/learn-d3?collection=@d3/learn-d3) -- collection
* [Learn D3: By Example](https://observablehq.com/@d3/learn-d3-by-example?collection=@d3/learn-d3)
  * This notebook demonstrates chart reuse of [D3 Histogram](https://observablehq.com/@d3/histogram)
  * EXERCISE #1: In a new notebook, recreate the histogram (chart1) using Plot
    * [Solution](./solutions.md#exercise-1)
  * EXERCISE #2: Change the height to 200 (as in chart2) using Plot
    * [Solution](./solutions.md#exercise-2)
  * EXERCISE #3: Do the same thing with chart3 -- get it to run in your new notebook.
    * [Solution](./solutions.md#exercise-3--4)
  * EXERCISE #4: Stop the axes from jiggling.
    * [Solution](./solutions.md#exercise-3--4)
  * EXERCISE #5: Add tooltips to the chart you created in Exercise #2
    * [Solution](./solutions.md/exercise-5)
    * As we'll see, the code that's used to add tooltips was written with D3 (and vanilla JavaScript).
  * The histogram is one of many [D3 Charts](https://observablehq.com/collection/@d3/charts) (collection)
    * You'll notice that many of these D3 charts can be easily and simply recreated with Plot.
    * But D3 is about much more than charts.

## Data wrangling (with D3 & Observable)

* Why should you use D3 & Observable?
  * Because it's a natural environment for developing good habits. For example...
    * "A good rule of thumb is that a cell should either define a named value to be referenced by other cells."
    * The last few paragraphs of [Learn D3: Data](https://observablehq.com/@d3/learn-d3-data?collection=@d3/learn-d3) explain why.
    * "Implicit dependencies lead to nondeterministic behavior 😱 during development, and possible errors 💥"
    * For example, if one cell defines an array and a second cell modifies it in-place, other cells may see the array before or after the mutation. 
    * Make the dependency explicit: give the second cell a name and copy the array using `Array.from` or `array.map`. 
    * Or combine the two cells so that only the already-modified array is visible to other cells.
* [Learn D3: Data](https://observablehq.com/@d3/learn-d3-data?collection=@d3/learn-d3)
  * EXERCISE #6: Fix the next line so that you add the numbers, not the strings
    * ``"62.7" + "59.9" // 122.6? Nope!``
    * [Solution](./solutions.md#exercise-6)
* d3-fetch -- convenient parsing on top of the [Fetch API](https://developer.mozilla.org/en-US/docs/Web/API/Fetch_API)
* d3-dsv -- parsing & formatting text (includes `d3.csvParse()`)
* d3-time -- dealing with all the issues related to time
* d3-time-format -- parsing and formatting time (includes `d3.utcParse()`)
* [d3-array](https://github.com/d3/d3-array) API reference (includes `d3.extent()`) -- github
  * [d3-array](https://github.com/d3/d3-array) API reference has a list of valuable Array methods (vanilla JavaScript)
    * [`Array.from()`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/from)
    * [`Array.prototype.map()`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/map)
  * There's also `Object`
    * [`Object`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Object)
      * [`Object`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Object) has useful static methods
      * [`Object.keys(obj)`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Object/keys)
      * [`Object.entries(obj)`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Object/entries)
    * [`Object.values(obj)`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Object/values)
  * [d3-array](https://github.com/d3/d3-array) adds many additional useful methods (with examples)
    * [d3-array statistics](https://github.com/d3/d3-array#statistics)
      * [d3.extent](https://observablehq.com/@d3/d3-extent)
    * [d3-array search](https://github.com/d3/d3-array#search)
    * [d3-array transformations](https://github.com/d3/d3-array#transformations)
    * [d3-array sets](https://github.com/d3/d3-array#sets)
    * [d3-array bins](https://github.com/d3/d3-array#bins)

## In-class labs

* [Lab #1](./lab01.md)
* [Lab #2](./lab02.md)

## Case Study: Wrangling Wikipedia

* [wikipedia.md](./wikipedia.md)

## Scales

[D3 scales](https://github.com/d3/d3-scale) and 
[Plot Scales](https://observablehq.com/@observablehq/plot-scales) are very closely related.

* Remember this? [Introducing D3-Scale](https://medium.com/@mbostock/introducing-d3-scale-61980c51545f) by Mike Bostock
* [Learn D3: Scales](https://observablehq.com/@d3/learn-d3-scales?collection=@d3/learn-d3)
  * Look under the hood at the bar chart in this notebook
    * It's SVG with:
      * [Continuous scales](https://github.com/d3/d3-scale#continuous-scales)
      * [d3.scaleLinear](https://github.com/d3/d3-scale#linear-scales)
      * [d3.scaleBand](https://github.com/d3/d3-scale#band-scales)
        * This reference is particularly relevant to Plot (figure shows padding options)
      * [d3-axis](https://github.com/d3/d3-axis#d3-axis), including
        * [d3.axisTop](https://github.com/d3/d3-axis#axisTop)
        * [d3.axisLeft](https://github.com/d3/d3-axis#axisLeft)
  * Create a D3 scale from a Plot scale
    * Create a chart with Plot that has only a scale: `chart = Plot.plot({x: {domain: [0, 100]}, grid: true})`
    * Get the scale object: `plotScale = chart.scale("x")`
    * Inspect the scale object -- it has all the properties needed to create a D3 scale
      * Note: `plotScale.type == "linear"` evaluates to true, which means we're using a linear scale.
      * [d3.scaleLinear](https://observablehq.com/@d3/d3-scalelinear) is one of several continuous scales
      * [Continuous Scales](https://observablehq.com/@d3/continuous-scales)
        * Notice that there's a whole lot of SVG attribute setting under the hood to visualize the scales
        * D3 scales come with many instance methods (e.g., [`scale.ticks()`](https://observablehq.com/@d3/scale-ticks))
          * Notice what happens when you vary the argument
        * [https://observablehq.com/@d3/continuous-scales#powers)
          * Try following the directions, i.e., change the range and value for "ticks" as suggested
    * Create the consistent D3 scale...
```
scale = d3.scaleLinear(plotScale.domain, plotScale.range)
```
or
```
scale = d3.scaleLinear()
scale = scale.domain(plotScale.domain)
scale = scale.range(plotScale.range)
```
or
```
scale = d3.scaleLinear()
    .domain(plotScale.domain)
    .range(plotScale.range)
```
* Notice that we're using [method chaining](https://en.wikipedia.org/wiki/Method_chaining) in the last example.

## Plot

* [Zebras?](https://observablehq.com/d/06a69c8c091df4c8)
  * [Introduction to Zebras](https://observablehq.com/@nickslevine/introduction-to-zebras-a-data-analysis-library-for-javascr)
  * 3 plots: S&P 500, daily change, rolling (yearly) average of volatility (sdv)
  * grouping, piping, visualization (vega-lite)
* [Alphabet](https://observablehq.com/d/3658a2d7f26f0ce3)
* [Diamonds](https://observablehq.com/d/55be911c1c3ac463)
  * [Plot: Rect](https://observablehq.com/@observablehq/plot-rect) -- includes visualization of diamonds
* Tooltips and Legend with Plot ??
  * Data wrangling with D3
  * [Tooltips with Plot](https://observablehq.com/@mkfreeman/plot-tooltip)
  * [Plot Color Legend](https://observablehq.com/@ambassadors/plot-color-legend)
  * [Plot Early Bird](https://observablehq.com/@fil/plot-early-bird)

## Tooltips with Plot 

Looking under the hood at [Tooltips with Plot](https://observablehq.com/@mkfreeman/plot-tooltip)

* Noteworth items...
  * It works with any "Mark" in any chart created by Plot
  * Simply set a title attribute for any mark
  * Pass your chart to the [addTooltips()](https://observablehq.com/@mkfreeman/plot-tooltip#addTooltips) function.
* Under the hood...
  * There's not that much code -- about 150 lines, including spaces and comments
