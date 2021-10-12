
# Plot II

Week 5 -- In-depth look at Plot

## Learning goals

* Core concepts
* When to use examples vs API documentation
* Interaction with Plot -- [My Dashboard with Plot.brush()](https://observablehq.com/d/0c28e2b73ff337d2)

## Design concepts

Goal: Memorable API

* Marks -- an array of marks to render, each mark has its own data and options
* Scales
* Transforms -- mechanism for transforming data as part of plot specification

## Core concepts

The API reference is organized according to the design elements -- use the dropdown table of contents!!

* [API reference](https://github.com/observablehq/plot/blob/main/README.md)
* [Plot.plot(option)](https://github.com/observablehq/plot/blob/main/README.md#plotplotoptions)
  * ``Plot.plot(options)`` has options
  * Mark options
    * a ``marks`` option in ``Plot.plot()`` specifies an array of marks to render
    * Each mark may be an array of marks -- nesting enables composition
    * ``marks`` may be a function that returns an SVG element
    * ``marks`` may be null or undefined, in which case it's ignored
    * ``marks`` are drawn in z order, last on top
    * When drawing a single mark, you can call ``mark.plot(options)`` as shorthand
  * There are other options
* [Plot: Marks](https://observablehq.com/@observablehq/plot-marks)
  * area, bar, cell, dot, frame, line, link, rect, rule, text, tick -- and Plot.marks()
* [Plot: Scales](https://observablehq.com/@observablehq/plot-scales)
  * scale options are determined by the corresponding top-level plot option, one of: x, y, r, color, opacity
  * known scale names: x, y, fx, fy, r, color, or opacity
  * Scales map an abstract value a visual value such as x- or y-position or color.
  * Scales define a plot’s coordinate system.
* [Plot: Transforms](https://observablehq.com/@observablehq/plot-transforms)
  * filter, sort, reverse -- all marks support these basic transforms
  * transform -- a custom transform function
  * group, bin, map, stack, select -- built-in options transforms
  * [map](https://github.com/observablehq/plot/blob/main/README.md#map) API reference -- github
    * These map methods are suppported:
    * *cumsum* -- a cumulative sum (*cumsum* is a string)
    * a function to be passed an array of values, returning new values -- IMPORTANT: the function is passed an array
    * an object that implements the map method -- this could be an array because arrays implement the map method
    * You need to read the API docs in this case because all 3 methods do **not** have examples
    * [Plot: Map examples](https://observablehq.com/@observablehq/plot-map)
* [Plot: Facets](https://observablehq.com/@observablehq/plot-facets)

## Tutorials

* [Plot Explorations: Penguins](https://observablehq.com/@observablehq/plot-exploration-penguins)
* [Plot Explorations: Weather](https://observablehq.com/@observablehq/plot-exploration-weather)

## Learning Plot

* Plot.plot(options)
  * Plot.mark(data, options)
  * Plot.marks(...marks)
* Plot.scales
* See the other parts of the [Observable Plot API menu](https://github.com/observablehq/plot/blob/main/README.md)

## Discussion

* [Awesome Plot](https://observablehq.com/@observablehq/awesome-plot) -- links to other notebooks about extensibility
* [SVG](https://developer.mozilla.org/en-US/docs/Web/SVG/Element/svg) -- mentions embedding SVG in SVG
* [Plot vs Vega-Lite](https://observablehq.com/@observablehq/plot-vega-lite)
* [Plot issues](https://github.com/observablehq/plot/issues) -- github
* [D3 API Reference](https://github.com/d3/d3/blob/main/API.md)

## Penguin tutorial -- solutions

* data columns: species, island, bill_length, bill_depth, flipper_length, body_mass, sex
0. 1-D distribution -- dot plot
```
Plot.dot(data, {x: "bill_length"}).plot() // it works, but circles overlap
```
```
Plot.dot(data, {x: "bill_length", fill: "black", fillOpacity: .2}).plot() // opacity helps with overlapping dots
```
1. 2-D scatterplot distinguishing species
```
Plot.dot(data, {x: "bill_length", y: "body_mass"}).plot() // color distinguishes species
```
2. Scatterplot with "fill" to distinguish "species"
```
Plot.dot(data, {x: "bill_length", y: "body_mass", fill: "species"}).plot() // color distinguishes species
```
3. Faceting creates small multiples (trellis chart) that distinguish sex (while fill distinguishes "species")
```
Plot.dot(data, {x: "bill_length", y: "body_mass", fill: "species"})
  .plot({facet: {data: data, x: 'sex'}, grid: true, marks: [ Plot.frame() ]})
```
* faceting allows for one more dimension -- potentially confusing
* [Plot facets](https://observablehq.com/@observablehq/plot-facets)
4. Faceting (by islands)
```
Plot.barY(data, Plot.groupX({y: "count"}, {x: "species", fill: "species"})) // bar chart
  .plot({ facet: { data, x: "island" }, // implement for each facet
          marks: [ Plot.frame(), ]
  })
```
or equivalently (everything in Plot.plot())...
```
Plot.plot({ facet: { data, x: "island" }, // implement for each facet
            marks: [ Plot.frame(), 
                     Plot.barY(data, Plot.groupX({y: "count"}, {x: "species", fill: "species"})) // bar chart
            ]
  })
```
or same information, different marks...
```
Plot.dot(data, Plot.group({r: "count"}, {x: "island", y: "species", stroke: "species" })).plot({
  r: {
    range: [0, 50] // adjusts the radius scale to make the marks more visible
  },
  marginLeft: 80,
  height: 300
})
```
these same marks can be used without formatting...
```
Plot.dot(data, Plot.group({r: "count"}, {x: "island", y: "species", stroke: "species" })).plot()
```
or equivalently
```
Plot.plot({marks: [ Plot.dot(data, Plot.group({r: "count"}, {x: "island", y: "species", stroke: "species"})) ] })
```
6. Distribution of weights
```
Plot.rectY(data, Plot.binX({y: "count"}, {x: "body_mass", thresholds: 20}))
  .plot()
```
7. Distribution of weight, sex, species
```
Plot.rectY(data, Plot.stackY(Plot.binX({y: "count"}, {x: "body_mass", fill: "species", thresholds: 20}))).plot({
  facet: {
    data,
    x: "sex",
    y: "species" // toggle this line to see effect!
  },
  marks: [
    Plot.frame(),
//    Plot.tickX(data, Plot.groupZ({x: "median"}, {  // Toggle tickX to get the solution to 8 (i.e., adding statistics)
//      x: "body_mass",
//      stroke: "#333", // applies statistic to "stroke" in this case
//      strokeWidth: 2
    }))
  ]
})
```
8. Adding statistic with [groupZ transform](https://github.com/observablehq/plot#plotgroupzoutputs-options)
  * [Group](https://github.com/observablehq/plot#group) -- Like Bin, aggregates ordinal or categorical data 
    * The only difference from Bin: Group is for discrete data
  * [Map](https://github.com/observablehq/plot#map) -- another transform
    * Groups data into series and then applies a mapping function to each series’ values
    * Say to normalize them relative to some basis or to apply a moving average.
9. Several things going on in the last question -- hard to interpret plot without a legend.

## Weather tutorial -- solutions

* data columns: date (daily), precipitation, temp_min, temp_max, wind, weather (categorical)

1. High temperature time series
```
Plot.line(data, {x: 'date', y: 'temp_max').plot()
```
* High & low temperature time series
```
Plot.plot({
  marks: [
    Plot.line(data, {x: 'date', y: 'temp_max', stroke: 'red'}),
    Plot.line(data, {x: 'date', y: 'temp_min', stroke: 'blue'})
  ]
});
```
2. Smoothed high & low temperature time series -- pass all Plot.line options through Plot.windowY()
```
Plot.plot({
  marks: [
    Plot.line(data, Plot.windowY(28, {x: "date", y: "temp_max", stroke: "red"})),
    Plot.line(data, Plot.windowY(28, {x: "date", y: "temp_min", stroke: "blue"})),
  ]
});
```
* or you can add "k" as an option...
```
Plot.plot({
  marks: [
    Plot.line(data, Plot.windowY({x: "date", y: "temp_max", k: 28, stroke: "red"})),
    Plot.line(data, Plot.windowY({x: "date", y: "temp_min", k: 28, stroke: "blue"})),
  ]
});
```
3. Area between high and low temperatures -- Plot.area needs y1 & y2
```
Plot.plot({
  marks: [
    Plot.areaY(data, Plot.windowY({x: "date", y1: "temp_max", y2: "temp_min", k: 28, fill: "#ccc"})),
    Plot.line(data, Plot.windowY({x: 'date', y: 'temp_max', k: 28, stroke: 'red'})),
    Plot.line(data, Plot.windowY({x: 'date', y: 'temp_min', k: 28, stroke: 'blue'})),
    ]
})
```
4. Daily average temperature computed from max & min
```
Plot.plot({
  marks: [
    Plot.areaY(data, Plot.windowY({x: "date", y1: "temp_max", y2: "temp_min", k: 28, fill: "#ccc"})),
    Plot.line(data, Plot.windowY({x: 'date', y: (d) => (d.temp_max + d.temp_min) / 2, k: 28, stroke: 'black'})),
  ]
})
```
5. Monthly precipitation -- bin avaraging uses "thresholds" and "d3.timeMonth" for time intervals
  * This solution requires a good understanding of the way D3 handles time
  * You need to look at the [d3-time](https://github.com/d3/d3-time) API reference docs
  * The next few lines pull out the elements
```
Plot.rectY(data, Plot.binX({ y: "sum" }, {
  x: "date",
  y: "precipitation",
  thresholds: d3.timeMonth,
})).plot()
```
6. Calendar view of precipitation -- facet by year
  * This solution requires a good understanding of [Plot faceting](https://observablehq.com/@observablehq/plot-facets)
  * Note how the facet are created in the facet options with the anonymous function that uses `date.getUTCFullYear()`
  * It would be hard to get this from the [Facet options](https://github.com/observablehq/plot/blob/main/README.md#facet-options) API reference
  * But the reference links to the examples, which are helpful
  * The final penguin example in [Plot: Facets](https://observablehq.com/@observablehq/plot-facets) is noteworthy
  * The penguin example explains facet filtering, and shows how it can be avoided with array.slice()
  * This is subtle, and would be hard to figure out with out examples
```
Plot.plot({
  color: {
    scheme: "blues"
  },
  facet: {
    data: data,
    y: d => d.date.getUTCFullYear(),
  },
  marks: [
    Plot.frame({stroke: "#ccc"}),
    Plot.cell(data, {
      x: d => d3.utcWeek.count(d3.utcYear(d.date), d.date),
      y: d => d.date.getUTCDay(),
      fill: "precipitation",
      title: "precipitation",
    })
  ]
})
```
7. Weather emoji
  * The final example goes one step further with a fancy application of Plot.text
  * [Plot: text](https://observablehq.com/@observablehq/plot-text) notebook has some good use cases
8. Scale options -- not in the weather tutorial
  * You can use scale options to customize the X & Y axes
  * [scale options](https://github.com/observablehq/plot/blob/main/README.md#scale-options)
  * The options are based on [d3-scale](https://github.com/d3/d3-scale) "microlibrary"
  * Experiment with choice of "ticks"
```
Plot.plot({marks: [ Plot.dot(data, {x: 'date', y: 'precipitation'}) ],
           x: {domain: [new Date(2000, 0), new Date(2022, 0)], ticks: 10},
           grid: true})
```

