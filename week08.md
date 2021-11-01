
# Week 08

* Project kickoffs
* Data join, d3-geo
* Choropleth (adding interaction with D3)

## data join

Introduction to data-join with [d3-selection](https://github.com/d3/d3-selection)

* [data-join.md](./data-join.md)

## Projects

* Update [projects](./projects.md) with project teams as the rest of the class does the exercises
* Exercises are based on the choropleth

## Choropleth

Introduction to [d3-geo](https://github.com/d3/d3-geo) and mapping with D3

* [choropleth.md](./choropleth.md)

## Exercises

Work with [State Choropleth](https://observablehq.com/@d3/state-choropleth)

* Exercise #1: Add a circle that follows the mouse
  * Use [d3.pointer](https://github.com/d3/d3-selection/blob/main/README.md#pointer)
    * `d3.pointer(event)` is part of [d3-selection](https://github.com/d3/d3-selection/blob/main/README.md)
  * Get hints from [Plot Tooltip](https://observablehq.com/@mkfreeman/plot-tooltip)
* Exercise #2: Update the styling to highlight the state that's being moused over
  * Again, get hints from here: [Plot Tooltip](https://observablehq.com/@mkfreeman/plot-tooltip)
  * [d3.select()](https://github.com/d3/d3-selection#select) -- tells you about `this`
* Exercise #3: Tooltip
  * Add a tooltip that shows the data value as it follows the mouse
  * Get hints from here: [Plot Tooltip](https://observablehq.com/@mkfreeman/plot-tooltip)
  * You'll need to add a text element, and get the data from the selected element

## Assignment 06 solutions

EDA with D3 and Plot -- review the solutions

* [assignment06_solutions.md](./assignment06_solutions.md)
