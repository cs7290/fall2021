
# Week 1 -- Day 2

## Logistics

* Office hours: 
  * Fridays, 2-4pm (Eastern Time)
  * Just about anytime by appointment
* Term Projects -- options to think about, but it's still early
  * [Project: "stinky"](https://github.com/ds5110/stinky) -- data from two DS 5110 project teams this past summer
  * S-L (discussions in progress -- stay tuned)
  * Public APIs (see the "APIs" section of [Introduction to Data](https://observablehq.com/@observablehq/introduction-to-data)

## Assignment for next week

* There's some coding and some reading
* Check [assignment01.md](./assignment01.md) for both
* Check Canvas for submission instructions

## In-class demo: collaboration with Observablehq

* Learning goals:
  * Get hands-on experience with Observable
  * Test the collaborative capabilities (including sharing and active coding with up to 5 people)
  * Introduction to D3 -- demonstrate how easy it can be (e.g., downloading USGS earthquake data)
* [My demo notebook](https://observablehq.com/d/4af7054abad3a547)
* `d3 = require("d3@6")`
* Notebook owner can share with up to 4 people
* Try 2 interactive cells -- show how cells execute reactively (like a spreadsheet, not top down like Jupyter)
  * y = 2 * x
    * has an error until "x" is defined
  * x = 3
    * error goes away as soon as you run this cell
* It's JavaScript inside a cell
  * Use curly braces with multiple lines
  * Cells have a (return) value
  * Name the cell if you want the return value to be accessible elsewhere (other cells or other notebooks)
  * The return value that can be a DOM element or a value or any other JavaScript object
* Try reading some data
  * Just as easy as "pd.read_csv(url)"
  * More flexible with `d3 = require("d3@6")`
  * Example: data = await d3.json("https://earthquake.usgs.gov/earthquakes/feed/v1.0/summary/4.5_hour.geojson")
  * "data" can be inspected interactively
* Discuss the resemblance to Jupyter/Colab
  * Point out the differences

## Learning goals for today

* Introduction to Observable notebooks (above)
* Discuss Python & Python Data Viz in relation to JavaScript/D3/Observable
* Demo: reuse an Observable chart (i.e., same chart, new data) -- Note: we didn't get enough time for this
* Data access and processing with HTML5/D3/Observable (Note: we didn't have time to get to this)

## Looking ahead

Aspirational goals for the next couple/several weeks (subject to change)

* Next week
  * Observable fundamentals
    * [Introduction to Data](https://observablehq.com/@observablehq/introduction-to-html)
    * [Introduction to Code](https://observablehq.com/@observablehq/introduction-to-code)
    * [Introduction to HTML](https://observablehq.com/@observablehq/introduction-to-html)
  * Basic charts -- [Observable Plot](https://observablehq.com/@observablehq/plot)
  * UI components
    * [Observable inputs](https://observablehq.com/@observablehq/inputs)
    * [Introduction to views](https://observablehq.com/@observablehq/introduction-to-views)
* Week following
  * [Dashboard](https://observablehq.com/@mbostock/dashboard)
  * Interactive charts
  * [Advanced embedding & downloading](https://observablehq.com/@observablehq/downloading-and-embedding-notebooks)
* Small Project #1: Dashboard with Observable Plot

## Python & JavaScript

* Programming languages
  * [The 10 most popular programming languages to learn in 2020](https://www.northeastern.edu/graduate/blog/most-popular-programming-languages/) -- Northeastern's perspective
  * Python and JavaScript top the list.
  * For data visualization, Python & JavaScript are increasingly interconnected.

## Python Data Viz and JavaScript/D3

* [Why so many libraries](https://www.anaconda.com/blog/python-data-visualization-2018-why-so-many-libraries) -- VanderPlas
  * Interesting Python/SciPy guru's perspective on Python Data Viz
  * Common theme: web technologies & modern browsers (Chrome, Firefox, etc.)
* Both languages have interactive tools
  * Python: Jupyter -- data science notebooks have been around for a while
    * Google Colab -- Jupyter in the cloud, with some nice enhancements
  * JavaScript: Observable (observablehq.com) -- relatively new
  * Browser-based notebooks: under the hood...
    * HTML5 APIs enable access to data and hardware (GPUs) native in *all* modern browsers (cross-platform)
    * web standards for styling, file formats, rendering (CSS, SVG, Canvas, WebGL), computation and animation.
    * JavaScript is the increasingly powerful language that ties it all together.
    * Jupyter is constrained by server side (kernel) communications, latencies, etc. -- it suffers as a result
    * Observable is entirely in the browser, so performance is top notch and possibilities are endless

A little more insight on the JavaScript-Python connection...

## Why so many libraries in Python?

* Common themes in the VanderPlas chart: desktop vs browser, OpenGL vs WebGL, static vs interactive, 2D vs 3D, etc.
* Of note: JavaScript and D3.js dominate a large chunk of the Python landscape.
* Another consideration is that many of the Python libraries are "charting programs"...

> *"If we endeavor to develop a charting instead of a graphing program, we will accomplish two things. First, we inevitably will offer fewer charts than people want. Second, our package will have no deep structure. Our computer program will be unnecessarily complex, because we will fail to reuse objects or routines that function similarly in different charts. And we will have no way to add new charts to our system without generating complex new code. Elegant design requires us to think about a theory of graphics, not charts."* Leland Wilson in [Grammar of Graphics](https://books.google.com/books?id=_kRX4LoFfGQC) (2005).

### Looking to the future

The future in Python, according to VanderPlas:

* [Part II](https://www.anaconda.com/blog/python-data-visualization-2018-moving-toward-convergence) -- convergence
* [Part III](https://www.anaconda.com/blog/python-data-visualization-2018-moving-toward-convergence) -- the future
* [Panel](https://panel.holoviz.org/)
  * A common framework for the variety of Python libraries that conform to a community standard
  * Example: [Gapminder dashboard](https://gapminders.pyviz.demo.anaconda.com/gapminders)
  * Example: [Attractor demos](https://attractors.pyviz.demo.anaconda.com/attractors_panel)

### Bostock's attractors

Relatively lightweight, relatively fast, relatively compact and extensible, remarkable indeed...

* [Clifford attractor](https://observablehq.com/@mbostock/clifford-attractor)
* [Clifford attractor II](https://observablehq.com/@mbostock/clifford-attractor-ii)
* This barely scratches the surface of what can be accomplished with web technologies, made easy by Observable

### Advanced visualization

The first release of D3.js was in 2011, and Mike Bostock described his philosophy in 2015:

> "*D3 espouses abstractions that are useful for any visualization application and rejects the tyranny of charts."* Mike Bostock in [Introducing D3 Scale](https://medium.com/@mbostock/introducing-d3-scale-61980c51545f) (Dec 2015).

By any measure it's safe to say that D3 has achieved Mike Bostock's vision of *a standard library of data visualization: not just a tool you use directly to visualize data by writing code, but also a suite of tools that underpin more powerful software.*

Bostock's latest creation is: [Observable notebook](https://observablehq.com/). He described the vision in 2018:

* [A better way to code](https://medium.com/@mbostock/a-better-way-to-code-2b1d2876a3a0)

Observable notebooks are already transformative, and they're getting better all the time.

# Live coding demo: Airports & Earthquakes

Goal: reuse a d3 chart -- import the chart, but override the original dataset with our own

* [World Airports('https://observablehq.com/@d3/world-airports')
* Learning goals
  * Dissect the elements of a Bostock gem
    * It's concise, but still fairly complex -- don't be intimidated, you don't need to create this from scratch
    * Note the data model -- it be investigated in the notebook
    * Note the data source -- a File attachment
    * Note the required libraries -- D3.js and topojson.js
  * Show how easy it is to reuse the map

## EXERCISE #1 (in class)

Import the map and the data into a new notebook

* Learning Goal: Prepare to reuse the map using imports
* [Introduction to imports](https://observablehq.com/@observablehq/introduction-to-imports)
* Inspect the data -- this shows you the data model that the map is expecting

## Get the earthquake data

* [Introduction to data](https://observablehq.com/@observablehq/introduction-to-data)
* The hard way
  * [fetch](https://developer.mozilla.org/en-US/docs/Web/API/fetch) -- MDN
    * [response](https://developer.mozilla.org/en-US/docs/Web/API/Response) -- MDN
    * [promise](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Promise) -- MDN
      * What's a promise? * It's a proxy for a value that's not necessarily known when the promise is created
      * Why do we need them?  * Because the web is asynchronous and unreliable
* The easy way
  * [d3-fetch](https://github.com/d3/d3-fetch)
    * d3.json(url)
    * Many other file formats can be "fetch"ed and parsed as well -- CSV, TSV, text, XML, images, and SVG

## EXERCISE #2

Use d3.json() to load the earthquake data into the notebook you just created

* [USGS GeoJSON API](https://earthquake.usgs.gov/earthquakes/feed/v1.0/geojson.php)
* Compare the earthquake data model to the airports data model
* Q: How many magnitude 4.5+ earthquakes were there in the last month?

## EXERCISE #3

Modify the earthquake data to conform to the airports data model

* Look at the example in [d3.dsv() API reference documentation](https://github.com/d3/d3-fetch#dsv)

## My Earthquakes

This is the hard way, i.e., without D3

* [Earthquakes](https://observablehq.com/@pbogden/earthquakes)
  * Different projection
  * With styling (CSS)

## References and resources

The list below supplements the readings in [assignment 01](./assignment01.md).

### Tutorials

* [Observable tutorials](https://observablehq.com/tutorials)
  * [Notebooks & Cells](https://observablehq.com/@observablehq/notebooks-cells) -- observable video
  * Other tutorials are good too

### Observable references

* [Introduction to Observable](https://observablehq.com/collection/@observablehq/introduction) -- collection
* [A Taste of Observable](https://observablehq.com/@observablehq/a-taste-of-observable)
* [Introduction to data](https://observablehq.com/@observablehq/introduction-to-data)
  * [Public APIs](https://github.com/public-apis/public-apis) -- think about these for the term project

### Debugging & problem solving

* MDN (Mozilla Developers Network)
  * [The DOM (Document Object Model)](https://developer.mozilla.org/en-US/docs/Web/API/Document_Object_Model) -- MDN
  * EXERCISE: Remove the heading from [my page](https://pbogden.github.io/with_style.html)
    * `document.getElementById`
  * EXERCISE: Remove the Google logo from google.com -- without removing the rest of the content
* [stackoverflow.com](http://stackoverflow.com)
* [w3school](http://w3schools.com)
