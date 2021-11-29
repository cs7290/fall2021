
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

## Exercise #2 -- Embedded cells

Put the map and the table from
[NOAA weather data by major U.S. city](https://observablehq.com/@observablehq/noaa-weather-data-by-major-u-s-city)
into the dashboard example. Replace the chart with the map, and the hard-coded table with the table from the notebook.

* Create your own fork of https://observablehq.com/@observablehq/noaa-weather-data-by-major-u-s-city
* Copy "orig.html" to "second.html"
* Remove the code you don't need, including:
  * Replace the `<canvas>` element with a `<div id="myChart">` that will contain the chart
  * Replace the `<table>` element with a `<div id="myTable">` that will contain the chart
  * The `<script>` tags containing Chart.js and feather.min.js
  * "dashboard.js", which is used only for the demo chart
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

