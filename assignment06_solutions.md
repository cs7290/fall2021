
# Assignment 06 Solutions

The assignment had 3 parts...

* Part 1: Finish [lab02](https://github.com/cs7290/fall2021/blob/main/lab02.md) from week 6 (EDA of pet adoptions)
  * Lab2 is all about EDA and data wrangling with Plot and D3. We started in class.
* Part 2: Let me know about term project
* Part 3: Add a mini-project porfolio piece to your gh-pages site (assignment 5 = assignment 4 w/extended deadline)

# Lab 2

EDA with pet adoption data

* To access the data, use `import {petAdoptions} from "7ffd902947c09896"`
* [Poor Dogs](https://observablehq.com/d/9bb9f29652b5d52e) -- my notebook with solutions
* The answers are also below.

## Exercise 0: How much data?

Q: How much data is there (e.g., # of rows, and why)?

A: 3 years of data for 50 states + DC (3 * 51 = 153 rows) and 31 named columns.

* How do you figure this out quickly?
  * [Inputs.table](https://observablehq.com/@observablehq/input-table) is a quick way to get some basic information.
  * `Inputs.table(petAdoptions)`
    * It shows all the fairly long headers
    * There's a "state" column, so we infer that 153 is a multiple of 51 (50 states and DC)
* How many years?
  * `new Set(petAdoptions.map(d => d.year))`
  * this gives us the unique "year"s, and indeed there are 3 years, which explains the 153 rows (3 * 51)
* How many columns?
  * there are two ways to get list of column names with 31 elements (strings)
  * `Object.keys(petAdoptions[0])` -- vanilla JavaScript
  * `petAdoptions.columns` -- this is created when Observable parses the file attachment
  * when we load a CSV with `FileAttachment().csv()`, it parses using [d3-dsv](https://github.com/d3/d3-dsv)
  * the API reference [d3-csv](https://github.com/d3/d3-dsv) tells you about the `columns` property

## Exercise 1: Total canine adoptions

Q: Get the total number of canine adoptions by year (consider using d3.group)

* Use [d3.group()](https://github.com/d3/d3-array#transformations) -- API docs
    * [d3-group](https://observablehq.com/@d3/d3-group) -- notebook
    * Groups the specified iterable
    * Returns an [InternMap](https://observablehq.com/@mbostock/internmap) from key to array of values
* `grp = d3.group(petAdoptions, d => d.year) // Group by year`
* `Array.from(d3.group(petAdoptions, d => d.year)) // Turn the InternMap into an Array`
* `d3.groups(petAdoptions, d => d.year) // With d3.groups (plural) you get the Array (above) directly`
* Compute the total dog adoptions by year (inspect `dogAdoptions` for the answer to this exercise)
  * we group by year with `d3.groups()`, which produces an Array with one element for each year
  * we then compute computing the sum for each year with `Array.map()`
```
dogAdoptions = d3.groups(petAdoptions, d => d.year) // group by year
  .map(g => ({year: g[0], adoptions: d3.sum(g[1], d => d.adoption_canine)}) ) // compute sum for each year
```
* With [Plot: Group](https://observablehq.com/@observablehq/plot-group)
  * Plot’s group transforms let you derive summary values for each group.
  * The `groupX()` transform groups data by "x" (year in this case)
  * Since we want total adoptions by year, we use "sum" to get the total adoptions for each year
  * This grouping can be used to produce a "y" channel, which we then plot using the "barY" mark
```
Plot.barY(petAdoptions, Plot.groupX({y: "sum"}, {x: "year", y: "adoption_canine"}))
  .plot({marginLeft: 60})
```
* To add tooltips:
  * First `import {addTooltips} from "@mkfreeman/plot-tooltip"`
  * Then `toolTip = d => d[0].year + "\n" + d3.format(",")(d3.sum(d, d => d.adoption_canine)) + " dogs adopted"`
  * And finally:
```
addTooltips(
Plot.barY(petAdoptions, Plot.groupX({y: "sum", title: toolTip}, {x: "year", y: "adoption_canine"}))
  .plot({marginLeft: 60})
  )
```


## Exercise 2. Format the result

Q: Use the result from the previous step to print (with commas for thousands) the total number for all years.

A: [d3.format()](https://github.com/d3/d3-format) makes this pretty easy

* ``md`Total dog adoptions (all years): ${d3.format(",")(d3.sum(dogAdoptions, d => d.adoptions))}``
* `d3.format` encoding is also part of Plot as you can see in the next chart
* Define `toolTip = d => d[0].year + "\n" + d3.format(",")(d3.sum(d, d => d.adoption_canine)) + " dogs adopted"`
* Then use the following
```
addTooltips(
Plot.barY(petAdoptions, Plot.groupX({y: "sum", title: toolTip}, 
                                    {x: "year", y: "adoption_canine", fill: "crimson"}))
  .plot({marginLeft: 60})
  )
```

## Exercise 3. Grouped bar chart

Q: Create a grouped bar chart -- bar chart shows each year, grouped by state

A: The solution below uses all sorts of Plot options...
```
Plot.plot({
  y: {tickFormat: "s"},
  color: {scheme: "Category10", domain: [...new Set(petAdoptions.map(d => d.year))]},
  facet: {data: petAdoptions, x: "state", frame: true, label: "Dogs Killed"},
  marginTop: 50,
  marks: [
    Plot.barY(petAdoptions, {
      x: "year",
      y: "shelter_euthanasia_canine",
      title: "shelter_euthanasia_canine",
      fill: "year",
      sort: {fx: "y", reduce: "sum", limit: 6, reverse: true}
    }),
    Plot.frame(),
    Plot.ruleY([0])
  ]
})
```
## `d3.group`, `d3.rollup` and `d3.index`

* Verification is always a good idea! 
* You can verify the calculations in Plot with [d3-array](https://github.com/d3/d3-array/blob/main/README.md)
  * They use similar syntax
* [d3.group](https://github.com/d3/d3-array/blob/main/README.md#group) for grouping
  * The arguments are (data, ...keys)
* [d3.rollup](https://github.com/d3/d3-array/blob/main/README.md#rollup) for grouped calculations
  * The arguments are (data, reducer, ...keys)
* [d3.group, d3.rollup, d3.index](https://observablehq.com/@d3/d3-group) -- notebook
  * Each of these valuable grouping tools is part of [d3-array](https://github.com/d3/d3-array)
* [d3.group](https://github.com/d3/d3-array/blob/main/README.md#group) is part of [d3.array](https://github.com/d3/d3-array/blob/main/README.md)
  * the documentation provides a simple example of groups using one key, and nested groups with multiple keys
  * with petAdoptions, the syntax is: `d3.group(petAdoptions, d -> d.state, d -> d.year)`
  * Use [d3.groups](https://github.com/d3/d3-array/blob/main/README.md#groups) to get an array
  * `d3.group(petAdoptions, d => d.state, d => d.year, d => d.shelter_euthanasia_canine)`
* [d3.rollup](https://github.com/d3/d3-array/blob/main/README.md#rollup) is also part of [d3.array](https://github.com/d3/d3-array/blob/main/README.md)
  * like d3-group, except you can operate on the group with a "reducer" function
  * `d3.rollup(petAdoptions, g => d3.sum(g, d => d.shelter_euthanasia_canine), d => d.state, d => d.year)`
  * Use [d3.rollups](https://github.com/d3/d3-array/blob/main/README.md#rollups) to get an array
  * `d3.rollups(petAdoptions, g => d3.sum(g, d => d.shelter_euthanasia_canine), d => d.state, d => d.year)`
* You can convert a Map to an array to a [Array.from()](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/from) (vanilla JavaScript)
* [d3.index](https://github.com/d3/d3-array/blob/main/README.md#index) (not using it here)
  * Equivalent to group but returns a unique value per compound key
  * Throws an error if the key is not unique.
