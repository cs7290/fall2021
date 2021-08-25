
# CS 7290 -- Fall 2021

# Overview

* Intro
  * The modern browser
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
