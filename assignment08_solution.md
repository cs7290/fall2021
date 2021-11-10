
# Assignment 08 solution

Add a tooltip to the Choropleth map that shows the data value as it follows the mouse

* Assignment: Answer Exercise 3, in [choropleth.md](./choropleth.md)
* Solution: [State Choropleth (w/Tooltip)](https://observablehq.com/d/a86a048022e9fe27)
  * The solution is worth working through step by step.
  * Shows how to use mutable to figure out what's going on
  * Get a little practice with the technologies reviewed in the Two-Circles demo.
* Alternative Solution: [State Choropleth + Tooltip)](https://observablehq.com/d/fa196553146ee703)
  * Uses hover method from [Plot Tooltip](https://observablehq.com/@mkfreeman/plot-tooltip)

## EXERCISE #3: Tooltip

Add a tooltip that shows the data value as it follows the mouse

#### Step 1 -- add a listener for `mousemove` events to the states

* Start with a clean fork of [State Choropleth](https://observablehq.com/@d3/state-choropleth)
* The event listener goes right after the data `join` that adds the "fill"ed states
  * `.on("mousemove", mousemoved)`
  * Note: that's **not** the "stroke"ed boundary path that has "fill" equal to "none"
* And add the callback function taht we'll be modifying below
  ```
  function mousemoved() {
  }
  ```

#### Step 2 -- add a mutable (for reporting only)

* We'll use the mutable only for reporting values from `mousedover`
  ```
  mutable z = 42
  ```
* We'll begin by verifying that we're getting the mouse position correctly
  * Modify `mousemoved`...
  ```
  function mousemoved(event) {
    mutable z = d3.pointer(event, svg.node())
  }
  ```
* Next, verify that we can access data for each state with the `this` object
  * Modify `mousemoved`...
  ```
  function mousemoved(event) {
    const pos = d3.pointer(event, svg.node());
    mutable z = d3.select(this).data()
  }
  ```
  * Inspect the value in the mutable -- it's an array with one element
  * The return value from `selection.data()` is an array of bound data values
  * In this case, that element is a GeoJSON object for the path element `this` associated with the hovered state
* Now verify that we have the data we need to create a tooltip
  * The mutable will show the state name, value and the mouse position...
  * Modify `mousemoved`...
  ```
  function mousemoved(event) {
    const pos = d3.pointer(event, svg.node());
    const d = d3.select(this).data()[0];
    const state = d.properties.name;
    const value = data.get(state);

    mutable z = [state, value, pos[0], pos[1]]
  }
  ```

### Step 3 -- Add the tooltip

* Now add the tooltip
  * We'll follow the approach taken in [Plot Tooltip](https://observablehq.com/@mkfreeman/plot-tooltip)
  * We'll just simplify it bit by simply appending a group `g` element on the SVG
  * We'll use everything the same styles, etc.
  ```
  const tip = svg.append("g")
      .attr("class", "hover")
      .style("pointer-events", "none")
      .style("text-anchor", "middle");
  ```
* Then, modify `mousemoved`
  * We'll define a `text` array with the state name and value.
  * We define `vertical_offset` just as in [Plot Tooltip](https://observablehq.com/@mkfreeman/plot-tooltip)
  * The insert that creates the data-dependent elements of the tooltip
  ```
  function mousemoved(event) {
    const pos = d3.pointer(event, svg.node());
    const d = d3.select(this).data()[0];
    const state = d.properties.name;
    const value = data.get(state);

    const text = [state, value];
    const vertical_offset = 15;
    tip.attr("transform", `translate(${pos[0]}, ${pos[1] + 7})`)
        .selectAll("text")
        .data(text)
        .join("text")
        .style("dominant-baseline", "ideographic")
        .text((d) => d)
        .attr("y", (d, i) => (i - (text.length - 1)) * 15 - vertical_offset)
        .style("font-weight", (d, i) => (i === 0 ? "bold" : "normal"));
  }
  ```
* In summary, we've made the following changes
  * Added an "mousemove" event listener to states,
  * Created a callback function `mousemoved`
  * Added a `mutable` for reporting values in `mousemoved`
  * Added a tooltip, `tip`, for the formatted text

### Step 4 -- Add a background for the tooltip

* We'll greatly simplify the approach in [Plot Tooltip](https://observablehq.com/@mkfreeman/plot-tooltip)
  * Add a group element that will contain the background
    * We'll `transform` this group in the same way as the tooltip text group
    * Put this before the tooltip text so it shows up underneath the text
  ```
  svg.append("g")
      .attr("class", "hover-background")
    .append("rect")
      .attr("fill", "white")
      .attr("stroke", "#d3d3d3")
      .style("pointer-events", "none");
  ```
* Then, in the callback, add data-dependent sizing that's computed from the text elements
  * Modify `mousedover` by adding
  ```
  const bbox = tip.node().getBBox();
  const side_padding = 10;
  const vertical_padding = 5;
  rect
      .attr("transform", `translate(${pos[0]}, ${pos[1] + 7})`)
    .select("rect")
      .attr("x", bbox.x - side_padding)
      .attr("y", bbox.y - vertical_padding)
      .attr("width", bbox.width + 2 * side_padding)
      .attr("height", bbox.height + 2 * vertical_padding);
  ```

### Step 5 -- Cleanup

* Remove the `mutable`
* Remove the `title` element from the states
* Add a listener for `mouseout` events that makes the hover elements transparent (hides them)
  ```
  .on("mouseout", () => svg.selectAll(".hover").attr("opacity", 1))
  ```
* Add a couple lines that makes the tooltip visible on mouseover
  * Modify `mousedover` by adding the line...
  ```
  svg.selectAll(".hover").style("opacity", 1);
  ```

## Alternative solution

* [State Choropleth + Tooltip](https://observablehq.com/d/fa196553146ee703)
* This fork of [State Choropleth](https://observablehq.com/@d3/state-choropleth) adds a tooltip using the hover method from [Plot Tooltip](https://observablehq.com/@mkfreeman/plot-tooltip)
