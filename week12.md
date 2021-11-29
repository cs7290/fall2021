
# Week 12

* Design and publish
* CSS frameworks
* Advanced embedding

## Site design -- examples

* [Tegan](https://tegan-ayers.github.io/)
  * custom -- very clean, well documented
* [Vanessa](https://vcchatman.github.io/dataviz-fall21-solo-portfolio/)
  * bootstrap
* [Chih-Ming](https://davyaco.github.io/CS7290CMS/)
  * bootstrap theme

## bootstrap

* It's been around for a while (they're on version 5.1)
  * For simple apps, the default build may be all you need.
  * As with most CSS frameworks, it can be customized.
  * The examples are good...
* [Bootstrap examples](https://getbootstrap.com/docs/5.1/examples/) -- getbootstrap.com
  * You can serve examples locally with a dev server, for example: `python -m http.server`
    * Then browse to http://localhost:8000
    * Then navigate to any of the example directories
    * For example, navbar components are here: http://localhost:8000/bootstrap-5.1.3-examples/navbars/
* The framework organizes things into components
  * Some require JavaScript
  * You can load the CSS and JS locally or from the cloud

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

## Advanced embedding

You're familiar with embedding an entire notebook, or a subset of a notebook...

* [Introduction to Embedding](https://observablehq.com/@observablehq/introduction-to-embedding)

You can also integrate individual cells from a notebook into elements of a web page that's styled with bootstrap,
which provides much more design flexibility...

* [Advanced Downloading and Embedding](https://observablehq.com/@observablehq/downloading-and-embedding-notebooks)

The section on "Rendering cells" shows how to insert a cell into a container element.

## Exercise #2 -- Embedded cells

Put the map and the table from
[NOAA weather data by major U.S. city](https://observablehq.com/@observablehq/noaa-weather-data-by-major-u-s-city)
into the bootstrap dashboard example. 

* Replace the chart with the map, and the hard-coded table with the table from the notebook.
* Create your own fork of https://observablehq.com/@observablehq/noaa-weather-data-by-major-u-s-city
  * Evidently, this is necessary for a CORS-enabled notebook API.
  * You can verify the problem in the development console.
* [Solution: Exercise 2](./dashboard.md/#exercise-2-embedded-cells)

**Solution:** http://localhost:8000/second.html

## Responsive design

* [Responsive design](https://developer.mozilla.org/en-US/docs/Learn/CSS/CSS_layout/Responsive_Design) -- MDN
  * The references discusses issues related to cross-browser and multiple device support.
  * Responsive design can be a challenge when dealing with CSS.
* [Responsive tables with bootstrap](https://getbootstrap.com/docs/5.1/content/tables/)
  * [CSS width](https://developer.mozilla.org/en-US/docs/Web/CSS/width)
  * To fit the container, use "width: 100%;
  * To opt in to the bootstrap styling of tables, use `class="table"`

## Exercise #3: Responsive table

Make the table responsive.

* [Solution](./dashboard.md/#exercise-3-responsive-table)

**Solution:** http://localhost:8000/third.html

## Responsive charts

* [Responsive images](https://developer.mozilla.org/en-US/docs/Learn/CSS/CSS_layout/Responsive_Design#responsive_images)
  * SVG and canvas elements can maintain a constant apect ratio, but need appropriate CSS styling
  * Bootstrap handles this with the `img-fluid` class
  * This class needs to be set on the `canvas` or `svg`
  * You an also set the appropriate class in the original notebook.
  * **However**, if you take this approach, interaction with the map won't work.
* **The best way:** Set `width` by overriding cell values
  * See [Advanced Downloading and Embedding](https://observablehq.com/@observablehq/downloading-and-embedding-notebooks)
  * We want to specify the width [width](https://github.com/observablehq/stdlib#width) in the notebook
  * We want to set width to equal the width of the containing element.
  * We'll use the `<div>`'s [offsetWidth](https://developer.mozilla.org/en-US/docs/Web/API/HTMLElement/offsetWidth)
  * Then use: `main.redefine("data", newData);` in our case `main.redefine("width", div.offsetWidth)`

## Exercise #4: Responsive chart

Make the chart (map) responsive.

* [Solution](./dashboard.md#exercise-4-responsive-chart)

**Solution:** http://localhost:8000/
