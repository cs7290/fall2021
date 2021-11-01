
# data join

* [data join](https://bost.ocks.org/mike/join/) -- bost.ocks.org
  * [General Update Pattern](https://observablehq.com/@d3/general-update-pattern) is deprecated -- notebook
  * But it's informative
* [*selection*.join](https://observablehq.com/@d3/selection-join) replaces the general pattern -- notebook
  * [d3-transition](https://observablehq.com/collection/@d3/d3-transition) -- notebook
    * A *transition* is similar to a *selection*
    * But it animates changes to the DOM.
    * It's more general than CSS [transition](https://developer.mozilla.org/en-US/docs/Web/CSS/transition)
    * Interpolation can be accomplished with a variety of [d3-ease](https://github.com/d3/d3-ease) interpolators
    * Don't miss: [Easing Animations](https://observablehq.com/@d3/easing-animations?collection=@d3/d3-transition)
  * [d3-transition](https://github.com/d3/d3-transition/blob/main/README.md) API reference -- github

### Random alphabet demo

To understand the links above, you should recognize how the code below works.

```
{
  while (true) {
    yield randomLetters()
    await Promises.tick(1000)
  }
}
```
* In a nutshell: the cell updates every second (1000 milliseconds) with the return value of `randomLetters()`
* You can copy and paste this cell into one of the Observable notebook links above (where `randomLetters` is defined).
* [Introduction to Promises](https://observablehq.com/@observablehq/introduction-to-promises) is a good reference.
* Note: The comment at the end regarding [*selection*.call()](https://github.com/d3/d3-selection/blob/main/README.md#selection_call) is a technique that enables method chaining.
