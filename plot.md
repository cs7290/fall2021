
# Plot

## Learning goals

* Why Plot?
* What makes it different?
* How to use it, including the documentation

## General

* The philosophy
  * Described in the [Observable Plot](https://observablehq.com/@observablehq/plot) notebook
  * Plot employs a layered grammar of graphics
    * inspired by Vega-Lite, ggplot2, Wilkinson’s Grammar of Graphics, and Bertin’s Semiology of Graphics.
  * Plot rejects a chart typology in favor of **marks**, **scales**, and **transforms**.
    * you won't see bar charts and scatterplots, but you will see marks such as bar and dot
  * Plot can be readily extended in JavaScript, whether to define a channel, a transform, or even a custom mark.
  * And Plot is compatible with Observable dataflow: use inputs to control charts, and views to read chart selections.
  * This last part is coming soon!
  * This discussion is 4 months old:  https://news.ycombinator.com/item?id=27036768
* Marks
  * [Plot: Marks](https://observablehq.com/@observablehq/plot-marks) -- notebook
  * [Plot Marks](https://github.com/observablehq/plot#marks) -- github
    * Note that you can scroll the major sections in the README.md file (upper left drop-down)
  * Marks are geometric shapes (e.g., bars, dots, lines)
  * In the notebook example, "fruit" is encoded as the y-position, "units" is encoded as the x-position
  * Under the hood, Plot automatically creates the scales as needed
  * In the example, Plot creates linear and ordinal scales for quantitative and categorical data, respectively
  * Marks expose a plot() method
    * How come transforms don't expose a run method of some kind that allows them to operate on data?
* Channels
  * channel == visual property that encodes abstract data
  * Bind columns of (abstract tabular) data to visual properties of marks
  * Channels can be column names for tabular data, or a function for processing data
  * Channel functions are passed a datum and its index
    * this is a convention, similar to Array methods (array.map and array.filter)
    * you can bypass channel functions and simply pass parallel arrays (specifying labels using scale.label)
    * or you can also use the default "xy" shorthand
  * Plot can specify channels either with a value (column name) or a function
    * Similar to the way D3's selection.attr accepts functions
    * But note that Plot channel functions should return abstract values, not visual ones
  * At the bottom of the notebook, there's an interesting discussion of transforms and fill channels for setting color
    * Shows how to set the "fill" of a mark to an abstract value instead of a literal color (that will get interpreted)
    * Then set the literal color using a scale
    * This final example is a lead into a discussion of scales
* For example, [Plot: Dot](https://observablehq.com/@observablehq/plot-dot)
  * Dots support stroke and fill "channels" in addition to position along x and y.
  * Dots also support an "r" channel allowing the size of dots to represent data. 
* Plot currently supports ~12 mark types: Area, Bar, Cell, Dot, Frame, Line, Link, Rect, Rule, Text, and Tick.
  * Mark types determine shape, which channels, options and scales are supported, if any.
  * Both bar and dot support x and y position.
  * bar and rect both generate a rectangle; the difference is in how the coordinates of the rectangle are specified.
  * For a bar, one side is a quantitative interval while the other is an ordinal (or categorical)
  * For a rect, both sides are quantitative intervals.
  * Hence a bar is used for a bar chart but a rect is needed for a histogram.
* Special marks can be used for annotation
  * [Plut.rule()](https://github.com/observablehq/plot#rule)
  * Plot.ruleX([0]) creates a rule at x = 0

## Navigating the documentation

* It's all about the API!
  * Is it a memorable API?
  * Who reads the API reference docs, anyway?
  * It's all about examples!
  * Actually, it's a combination of examples and API reference documentation.
* [Plot: Dot](https://observablehq.com/@observablehq/plot-dot)
  * This is a higher level of detail than [Plot: Mark](https://observablehq.com/@observablehq/plot-mark)
  * Note the distinction between Plot.plot(options) and Plot.dot(options).plot()
    * In Plot.plot(options), the options include "marks: Plot.dot()") 
  * If you simply invoke Plot.dot(...).plot() you get a plot minus some of the options
  * For example: what's with "r"?
    * It's used in the notebook demo, but it's not explained or hard to find.  What do you do?
    * That's when it's time to look at the API reference
    * [Plot.dot API reference](https://github.com/observablehq/plot/blob/main/README.md#dot) -- github
    * Does "r" seem kind of arbitrary?  Maybe, but it's actually consistent with the SVG specification.

## Coercion, anonymous functions, null, NaN, and other stuff

* [Plot: Dot](https://observablehq.com/@observablehq/plot-dot)
* Coercion -- convert null to NaN thereby avoiding coercion of null to zero
  * [?? nullish coalescing operator](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Nullish_coalescing_operator)
  * returns its right-hand side operand when its left-hand side operand is null or undefined
* Checking for nulls
  * javascript check for nulls
  * [How to check for null](https://stackoverflow.com/questions/6003884/how-do-i-check-for-null-values-in-javascript)
  * https://www.destroyallsoftware.com/talks/wat
* [isNaN()](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/isNaN) -- MDN
* [Plot: Dot](https://observablehq.com/@observablehq/plot-dot) demo
  * Note that the "cars" dataset contains nulls; these are converted to NaN to prevent coercion to zero.
  * EXERCISE: Find them, how many are there?
    * Checking for NaN in an array: `[NaN, 1, 2].filter(isNaN)`
    * Checking for null in an array: `[null, 1, 2].filter(d => d === null)`

# Wine demo

* [Wine Plot](https://observablehq.com/d/701ce33a3f1cbd6b)
