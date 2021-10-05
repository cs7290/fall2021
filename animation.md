
# Animation

Among other things, Observable greatly simplifies animation because...

[Observable's not JavaScript](https://observablehq.com/@observablehq/observables-not-javascript)

* As we start working with animations, this notebook may be helpful, especially if you like to look under the hood.
  * The notebook may be hard to read at first, but it will become more readable with time.
  * The notebok has more detail than we need for animations.
  * If you're confused, then ask questions. 
  * It's **not** required reading.
* There are several terms that you should know. 
  * These terms may be new if you're new to JavaScript or asynchronous operations; the concepts exist in Python.
  * [await](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/await)
    * The await operator is used to wait for a Promise.
  * [Promise](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Promise)
    * A `Promise` object represents the eventual completion (or failure) of an asynchronous operation and its resulting value.
    * A promise is a proxy for a value not necessarily known when the promise is created.
    * A promise is said to be "settled" if it is either "fulfilled" or "rejected", but not "pending". 
    * You will also see the term "resolved" used with promises.
    * A "resolved" promise is settled or “locked-in” to match the state of another promise. 
  * [yield](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/yield)
    * The yield keyword is used to pause and resume a generator function (function*).
    * A [function* declaration](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/function*) defines a generator function, which returns a Generator object.
  * [Generator](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Generator)
    * A Generator object is returned by a generator function.
    * A Generator object conforms to both the ["iterable" protocol](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Iteration_protocols#the_iterable_protocol) and the ["iterator" protocol](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Iteration_protocols#the_iterator_protocol)
    * [Iterable examples](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Iteration_protocols#iterable_examples)
      * String, Array, TypedArray, Map, and Set are all built-in iterables. 
      * Each of their prototype objects implements a so-called [@@iterator method](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/@@iterator)
      * The iterator method is part of the iterable protocol ("@@" has special meaning)
      * [@@iterator](https://262.ecma-international.org/6.0/#sec-well-known-symbols) is a "well-known symbol"
      * [Stackoverflow exchange is helpful](https://stackoverflow.com/questions/29492333/what-does-at-at-mean-in-es6-javascript)
      * In JavaScript, get the iterator using "Symbol.iterator"
      * The iterator method defines how to iterate synchronously over a sequence of values.

## Observable cells...

* ...are separate scripts
* ...run in topological order
* ...re-run when any referenced cell changes
* ...need curly braces, `{...}` when they involve statements, and they must then return (or yield) a value
* ...and...
  * ...can be views
  * ...can be mutables
  * ...can be imported from other notebooks

## Observable cells implicitly await Promises

You can define a cell whose value is a promise
```
hello = new Promise(resolve => {
  setTimeout(() => {
    resolve("hello there");
  }, 5000);
})
```
* If you reference such a cell, you don’t need to await; the referencing cell won’t run until the value resolves.
* [setTimeout()](https://developer.mozilla.org/en-US/docs/Web/API/setTimeout) method sets a timer and executes a function once the timer expires
* the time to wait is in milliseconds
```
hello.split(/\s+/g) // implicit await
```

## Observable cells implicitly iterate over generators

* If a cell yields, any referencing cell will see the most-recently yielded value.
* yields occur no more than once every animation frame (typically 60 times/second)
* For this reason, generators are handy for animation in Observable.
* If you yield a DOM element, it will be added to the DOM before the generator resumes.

## The old days...

* ...there were no Promises (IE doesn't support them)
* ...there were only old-fashioned passed-in callbacks
* ...several asynchronous operations in a row would lead to the classic "callback pyramid of doom."
* Promises come with some nice [guarantees](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Using_promises#guarantees).
  * One of the great things about using promises is chaining.
  * With modern functions, we attach callbacks to the returned promises instead, enabling a promise chain.
    * Asynchronous programming allows the browser to do multiple things at the same time, for example:
    * Download files and perform complex calculations and respond fluidly to user interaction
  * [Introduction to Promises](https://observablehq.com/@observablehq/introduction-to-promises)
* Things have gotten even better in the last few years
  * Asynchronous iteration came to the browser with the 2018 version of the JavaScript specification.
  * Asynchronous iteration extends one step bayond asynchronous programming
  * Asynchronous iteration allows you to step through multiple asynchronous tasks.
  * The animation at end of the next notebook is an example -- 4 awaits in a sequence.
  * [Introduction to asynchronous iteration](https://observablehq.com/@observablehq/introduction-to-asynchronous-iteration)
