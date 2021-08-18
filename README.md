
# CS 7290 -- Fall 2021

Cutting edge data viz with web technologies.

# Syllabus ideas

* [D3 gallery](https://observablehq.com/@d3/gallery) -- observable notebook
  * The gallery is organized as follows
    * animation
    * interaction
    * analysis
    * hierarchies
    * networks
    * bars
    * lines
    * areas
    * dots
    * radial
    * annotation
    * maps
    * essays
    * just for fun
* [Interactive Data Visualization for the Web](https://learning.oreilly.com/library/view/interactive-data-visualization/9781491921296/ch02.html#idm140093208128112) -- oreilly.com
  * Chapter 2: Introducing D3
    * What D3 is. What it isn't.
    * Lists a bunch of libraries (alternatives to D3 -- Leaflet, Highcharts, Google Charts, etc.) 
  * Chapter 3: (Web) Technology fundamentals
  * Chapter 4: Setup (unnecessary)
  * Chapter 5: Drawing with data
  * Chapter 6: Divs, attributes, making a bar chart
  * Chapter 7: Scales
  * Chapter 8: Axes
  * Chapter 9: Updates, transitions and motion
  * Chapter 10: Interactivity
  * Chapter 11: Using paths (line and area charts)
  * Chapter 12: Selections
  * Chapter 13: Layouts
  * Chapter 14: Geomapping
  * Chapter 15: Exports (unnecessary)
  * Chapter 16: Project walk through

# Calendar

1. 20 & 21 Sep
2. 27 & 28 Sep
3. 4 & 5 Oct
4. 11 & 12 Oct -- 11 Oct is a holiday (Indigenous People's Day)
5. 18 & 19 Oct
6. 25 & 26 Oct
7. 1 & 2 Nov 
8. 8 & 9 Nov 
9. 15 & 16 Nov 
10. Thanksgiving -- 22 & 23 Nov -- (no classes this week)
11. 29 & 30 Nov
12. 6 & 7 Dec
13. Final Exams -- 13 & 14 Dec

# D3 in action -- Elijah Meeks

* D3 fundamentals
  * Chapters 1-3 -- data binding, data loading, creating graphical elements, scales, color, CSS, SVG
  * Chapter 4 -- line charts, axes, box plots
  * Chapter 5 -- pie charts, violin plots, histograms, sankey diagrams, word clouds
* Complex data visualization
  * Chapter 6 -- hierarchical data viz: treemaps, dendrograms
  * Chapter 7 -- network data
  * Chapter 8 -- geodata
* Advanced techniques

# Overview

* Intro
  * Where innovation takes places
    * Data science (Python, R)
    * Data journalism (nytimes.com)
    * [AI](https://playground.tensorflow.org/)
    * ~~Business Intelligence (BI)~~
  * D3
    * SVG
    * Canvas
    * [D3 gallery](https://observablehq.com/@d3/gallery)
  * Slippy maps
    * https://leafletjs.com/
    * https://maplibre.org/
  * 3D
    * [three.js](https://threejs.org/)
    * [deck.gl](https://deck.gl/)
    * [scatter-gl](https://github.com/PAIR-code/scatter-gl)

# Topics

* InfoVis paper (Bostock, et al., 2021) http://vis.stanford.edu/files/2011-D3-InfoVis.pdf
* SVG, Canvas, WebGL

# Visualizing chaos

* [Lorenz system](https://en.wikipedia.org/wiki/Lorenz_system) -- wikipedia
  * Physical systems can be completely deterministic and yet still be inherently unpredictable...
  * even in the absence of quantum effects. (butterfly effect)
* [Lorenz attractor](https://observablehq.com/@mbostock/lorenz-attractor) -- mbostock notebook
  * Solving lorenz equations and visualizing phase space with canvas
* [de Jong attractor](https://observablehq.com/@mbostock/de-jong-attractor-ii) -- mbostock notebook
* [UTF-8](https://en.wikipedia.org/wiki/UTF-8) -- wikipedia
  * Variable-width character encoding (1 to 4 bytes) capable of encoding more than a million characters
  * The most common encoding for the WWW
  * For example: ρ
  * Unicode (Universal Coded Character Set) Transformation Format -- 8-bit
  * First 128 characters corrspond to ASCII (1 byte)
    * `wc` -- word count (word, line, character)
    * `od` -- octal dump
    * create a file with only a zero -- "0", it will have 2 bytes
    * first bit of ASCII leaves room for 128 additional characters, otherwise it's "0"
