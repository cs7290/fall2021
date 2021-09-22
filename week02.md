
# Week 2

## General

* There's a wide range of backgrounds in the class -- it's expected and good to see.
* Grading will be based on how much you learn, not on how your background compares with others.
* There's a lot of information. We're diving right in. There's no wading involved.
* So ask questions!! There will be major awards for both asking and answering (in Piazza and in class)
* As for Major Awards -- I'm keeping track, it'll be part of the class-participation score.
* Make use of office hours!  If office hours aren't convenient for you, just make an appointment.

## Overview

A list of notebooks so far (like book chapters, except there's no book)...

* Last week
  * [JavaScript for Python Programmers](https://observablehq.com/@ballingt/javascript-for-python-programmers)
    * [Introduction to Code](https://observablehq.com/@observablehq/introduction-to-code)
  * [Observable for Jupyter Users](https://observablehq.com/@observablehq/observable-for-jupyter-users)
    * [Observable's not JavaScript](https://observablehq.com/@observablehq/observables-not-javascript)
* This week
  * [Introduction to Data](https://observablehq.com/@observablehq/introduction-to-data)
  * [Observable Inputs](https://observablehq.com/collection/@observablehq/inputs) -- the collection
    * [Observable Inputs](https://observablehq.com/@observablehq/inputs)
    * [Hello, Inputs!](https://observablehq.com/@observablehq/hello-inputs)
    * [Input Table ](https://observablehq.com/@observablehq/input-table)
  * [Introduction to Imports](https://observablehq.com/@observablehq/introduction-to-imports)
  * [Introduction to HTML](https://observablehq.com/@observablehq/introduction-to-html)
  * [Observable Plot](https://observablehq.com/@observablehq/plot) -- mbostock notebook
  * [Introduction to Embedding](https://observablehq.com/@observablehq/introduction-to-embedding) -- notebook

## JavaScript for Python Programmers

* [JavaScript for Python Programmers](https://observablehq.com/@ballingt/javascript-for-python-programmers)
  * This was required reading -- Review it briefly.
  * Let's skim through it and see if there are any questions.
  * We won't go into great detail.
  * This is something you should keep handy and look at periodically.
* [Introduction to Code](https://observablehq.com/@observablehq/introduction-to-code)
  * This is an alternative with much of the same information, not Python-centric

## Observable for Jupyter Users

* Assigment #1 had two notebooks for required reading:
  * [JavaScript for Python Programmers](https://observablehq.com/@ballingt/javascript-for-python-programmers)
    * In principle, we could have a quiz on this required reading from the assignment.
  * [Observable for Jupyter Users](https://observablehq.com/@observablehq/observable-for-jupyter-users)
    * This was required reading -- Review it briefly in class
    * In principle, we could have a quiz on this required reading from the assignment.
    * If we were to have a quiz, this is what some of the questions would look like...
* Demo quiz questions
  * Question 1: In Jupyter notebooks, it's implicit that the "repr()" -- printable reprepresentation --
of the last expression gets printed below the cell. What's implicit from an Observable notebook cell?
  * Multiple choice answers
    * The value of the last expression gets printed.
    * A string equivalent of the last expression is printed below the cell.
    * A string equivalent of the last expression is printed above the cell.
      * This is only true if you return a string.
    * Undefined.
      * THIS IS THE CORRECT ANSWER -- You must explicitly return values
    * None of the above
  * Question 2: How many types of cells are there
    * 1 -- THIS USED TO BE THE CORRECT ANSWER -- JavaScript -- that's what it says in the reading, but it's out of date
    * 2
    * 3
    * 4 -- THIS IS SORT OF THE CORRECT ANSWER -- that's how many there are now (if you create a new cell)
      * The two sort-of-answers are reconciled by understanding the role of the standard library
      * This would have been a trick question in a quiz, and students would have been justified in objecting;-)
      * [Observable standard library](https://observablehq.com/@observablehq/stdlib)
  * Question 3: Multi-line code cells are surrounded by...
    * white space
    * square brackets
    * curly brackets -- THIS IS THE CORRECT ANSWER
    * parentheses
  * Question 4: If you create two cells named "a" and run them in sequence then
    * The first cell in the sequence wins and determines the value of "a"
    * The second cell in the sequence wins and determines the value of "a"
    * None of the above -- THIS IS THE CORRECT ANSWER -- you'll create a runtime error
  * Question 5: When you press "Cmd-Enter", Observable cells run as follows:
    * All cells run from top to bottom
    * Only the individual cell runs
    * All cells above the current cell run first, then the current cell runs
    * None of the above -- THIS IS THE CORRECT ANSWER
      * The current cell will run along with any cells that depend on the return value will also run.
      * The cells run in execution order.
      * [How Observable Runs](https://observablehq.com/@observablehq/how-observable-runs)

## Introduction to Data

* Learning goals
  * Introduce various ways to get data in/out of observable notebooks
  * d3.json (the easy way) vs fetch (the hard/modern way) vs XMLHttpRequest (yuck!)
  * start thinking about potential data sources for term project
* We didn't spend much time on this in class
* [Introduction to Data](https://observablehq.com/@observablehq/introduction-to-data)
* Related references
  * [Introduction to Promises](https://observablehq.com/@observablehq/introduction-to-promises)
  * [d3.autoType](https://observablehq.com/@d3/d3-autotype)
  * [check for date](https://stackoverflow.com/questions/643782/how-to-check-whether-an-object-is-a-date)
  * CORS
  * [Introduction to Imports](https://observablehq.com/@observablehq/introduction-to-imports)
  * [Working with the census API](https://observablehq.com/@mbostock/working-with-the-census-api) -- mbostock notebook

## Observable Inputs

* Learning goals
  * Lightweight interface elements in Observable (the easy way)
  * Extensible and memorable API
  * The hard way
* References
  * [Interactive Plot](https://observablehq.com/d/42f366e930b89e5c) -- my notebook
  * [Observable Plot (Jupyter)](https://observablehq.com/@pbogden/observable-plot-jupyter) -- my notebook

## EXERCISES (in-class)

* **EXERCISE 1** -- Put the earthquake data into a table
* **EXERCISE 2** -- Add an Input with maximum-magnitude filter
  * Note: Did this together at the end of Monday's class
  * [the shared notebook](https://observablehq.com/d/606ead110ea0ca44)
  * STOPPED HERE ON MONDAY
  * **Solution** -- [Earthquakes in a table on a map in a Plot](https://observablehq.com/d/9d469ee38387512e)

## HTML and CSS

* [html.md](./html.md) -- This is the minimal answer to last week's assignment
* Basic HTML page (not covered in class)
  * [createElement](https://developer.mozilla.org/en-US/docs/Web/API/Document/createElement#basic_example) -- MDN
    * This MDN reference compares basic HTML with same content created dynamically with JavaScript (good demo)
    * Note: Our goal is not to get super into the weeds of Web technologies
    * MDN is a great resource (bottom of the page has browser compatibility)
    * Google "javascript map mdn" and look at the compatibility
    * ES6 -- [ECMAScript](https://en.wikipedia.org/wiki/ECMAScript) -- wikipedia
* Note: On Github, markdown gets formatted automatically into a web page, giving you CSS with Jekyll

## Observable Plot

* Learning goals
  * Quick Plot for tabular data with sensible defaults (e.g., in Python: Seaborn)
  * Customizable (e.g., in Python: Seaborn is built with Matplotlib)
  * Memorable API designed with extensibility in mind (e.g., in Python: Um, wait. Is that Seaborn or Matplotlib?)
* [Observable Plot](https://observablehq.com/@observablehq/plot) -- mbostock notebook

## EXERCISES (in-class)

* Recall array methods we used last time (and will be using a lot in the future)
  * If we do this: `let a = [];
  * Then this evaluates to true: `a instanceof Array`
  * [Object prototypes](https://developer.mozilla.org/en-US/docs/Learn/JavaScript/Objects/Object_prototypes)
    * Prototypes are the mechanism by which JavaScript objects inherit features from one another.
  * [Array.filter](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/filter)
    * All Array instances have a filter method
  * [Array.map](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/map)
    * All Array instances have a map method
* **EXERCISE 3** -- Put the data on a map by replacing the airports (recall observable inputs)
  * [Earthquakes in a Table](https://observablehq.com/d/996a2e0e5a633b85)
  * [Introduction to Imports](https://observablehq.com/@observablehq/introduction-to-imports)
    * See the section: "Rewrite" Code Using import - with
  * [World Airports](https://observablehq.com/@d3/world-airports)
* **EXERCISE 4** -- Visualize the earthquakes with Observable Plot
  * Start with -- [Earthquakes in a table](https://observablehq.com/d/9d469ee38387512e)
  * **Solution** -- [Earthquakes in a table on a map in a Plot](https://observablehq.com/d/9d469ee38387512e)
    * This notebook has solutions to all 4 exercises.
