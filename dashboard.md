
# Dashboard

## Exercise #1

Get the bootstrap dashboard example running locally on your machine.

* Open a terminal from which you can run Python
* Download and unzip the zip file into a local directory [./bootstrap-5.1.3-examples](./bootstrap-5.1.3-examples)
* Create a local copy of the "index.html" file from "./bootstrap-5.1.3-examples/dashboard", call it "orig.html"
* Copy "bootstrap.min.css", "bootstrap.bundle.min.js", "dashboard.css" and "dashboard.js" to the local directory.
* Adjust the URLs in "index.html" to look for the local files.
* Start the dev server (from the directory with "orig.html"): `python -m http.server`
* Then browse to http://localhost:8000/orig.html

**Solution: http://localhost:8000/orig.html**

## Exercise #2: Embedded cells

Put the map and the table from
[NOAA weather data by major U.S. city](https://observablehq.com/@observablehq/noaa-weather-data-by-major-u-s-city)
into the dashboard example. Replace the chart with the map, and the hard-coded table with the table from the notebook.

* Create your own fork of https://observablehq.com/@observablehq/noaa-weather-data-by-major-u-s-city
* Copy "orig.html" to "second.html"
* Remove/replace the code you don't need, including:
  * Replace the `<canvas>` element with a `<div id="myChart"></div>` that will contain the chart
  * Replace the `<table>` element with a `<div id="myTable"></div>` that will contain the chart
  * Remove the `<script>` tags containing Chart.js and feather.min.js
  * Remove "dashboard.js", which is used only for the demo chart
  * The code should look like this...
  ```
  <div class="my-4 w-100" id="myChart">
  </div>

  <h2>Section title</h2>
  <div id="myTable" class="table-responsive">
  </div>
  ```
* Embed the cells you want in the appropriate elements in "second.html"
* Add the following
```
<script type="module">
// Load the Observable runtime and inspector.
import {Runtime, Inspector} from "https://cdn.jsdelivr.net/npm/@observablehq/runtime@4/dist/runtime.js";

// Your notebook, compiled as an ES module.
import notebook from "https://api.observablehq.com/d/72366cd25d762e7b.js?v=3";

// Load the notebook, observing its cells with a default Inspector
// that simply renders the value of each cell into the provided DOM node.
const main = new Runtime().module(notebook, name => {
  if (name === "viewof cityMap") return Inspector.into("#myChart")();
  if (name === "viewof citySelected") return  Inspector.into("#myTable")();
});
</script>
```
* Note: The map is drawn on a canvas element that extends wider than the page.
  The aspect ratio is set by specifying `mapWidth` and `mapHeight`.
  The absolute width of the canvas is the value of `width` as set by
  the [Observable standard library](https://github.com/observablehq/stdlib#width).
* Note: The table is doesn't fill the table div.

**Solution: http://localhost:8000/second.html**

## Exercise #3: Responsive table

Make the table responsive.

* In the notebook, you could create a cell that sets the class of the table
```
myclasses = d3.select(viewof citySelected).select('table').classed("table", true)
```
* Then in the "second.html" file, you'd need to add the following line when setting up the runtime.
```
if (name === "myclasses") return true;
```
* If you make these two changes and reload, you should see that the table is the correct width.

**Solution: http://localhost:8000/third.html**

## Exercise #4: Responsive chart

Make the chart (map) responsive.

* To make the map the correct size when the window loads, first get a reference to the main module...
```
const main = new Runtime().module(notebook, name => {
```
then override the width
```
main.redefine("width", document.getElementById("myChart").offsetWidth);
```
* To get the map to resize whenver the window changes size, create an event listener for "resize" events.
* Use [`window.onresize`](https://developer.mozilla.org/en-US/docs/Web/API/Window/resize_event).
* For a demo, add the following code, then open the dev console and change the window size...
```
let i = 0;
window.onresize = () => console.log("I've been resized " + i++);
```
* So, define a function that overrides `width` using the size of the container div:
```
const resetWidth = () => main.redefine("width", document.getElementById("myChart").offsetWidth);
```
* Then use `window.onresize` to set the width according to the layout...
```
resetWidth();
window.onresize = resetWidth;
```
**Solution:** http://localhost:8000/fourth.html

## Exercise #5: Search input

Add the search input to the navigation bar.

* This is a bit more complicated because Observable's [Input: Search](https://observablehq.com/@observablehq/input-search)
is a combination of HTML elements. The bootstrap template puts an input element in the header...
```
<input class="form-control form-control-dark w-100" type="text" placeholder="Search" aria-label="Search"> -->
```
* We replace it with a DIV container that includes some bootstrap form classes:
```
<!-- Put form control here -->
<div id="mySearch" class="form-control form-control-dark"></div>
```
* When we render the cells, add the cell name for the search input in the notebook
```
if (name === "viewof filteredCities") return  Inspector.into("#mySearch")();
```
* We can experiment with class labels and bootstrap styling in the dev console.  For example
```
document.getElementById("mySearch").getElementsByTagName("input")[0].classList.add("form-control");
```
  However, we can't simply add this line in the HTML file because the notebook loads asyncronously.
  You'll get an error that the "input" element is undefined.
* Therefore, to get the styling correct, we need to add some bootstrap classes in the observable notebook.
  This is complicated because the Observable styling and the bootstrap classes conflict with one another.
  As a result, you need several adjustments...
```
myclasses = {
  d3.select(viewof citySelected).select('table').classed("table", true);
  d3.select(viewof filteredCities).select('input')
    .classed("form-control", true).classed("w-100", true).classed('form-control-dark', true);
  d3.select(viewof filteredCities).style("--input-width", "100%");
}
```
