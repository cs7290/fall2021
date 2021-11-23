
# Zoom

* [Scatterplot Tour](https://observablehq.com/@d3/scatterplot-tour)

## Exercise

Modify the scatterplot tour to use the [Palmer Penguins](https://github.com/allisonhorst/palmerpenguins#palmerpenguins-)

* [Solution](https://observablehq.com/d/e6569c4e3860e806)
  * Only two cells needed to change.
* First, read the data and make it conform to the data model for the visualization
  * The easiest way to do it is to add an index for each species.
  * You then need to return two dimensions in the data
  * You don't necessarily need to remove the "NA"s from the data
  ```
  data = {
    const url = "https://raw.githubusercontent.com/allisonhorst/palmerpenguins/master/inst/extdata/penguins.csv"
    const data = await d3.csv(url, d3.autoType);
    const species = Array.from(new Set(data.map(d => d.species)));
  
    return data.map(d => [d.bill_length_mm, d.bill_depth_mm, species.indexOf(d.species)]);
  }
  ```
  * This will zoom to the species, but the initial "Overview" won't include any of the data.
    * That's because the original dataset was created with parameters that included the origin.
* Second, set the intial zoom according to the data parameters (not the identity)
  * You can pull out the "overview" zoom and computed it from the data
  * The "transforms" cell changes to the following
  ```
  transforms = {
    const [x0, x1] = d3.extent(data, d => d[0]).map(x);
    const [y1, y0] = d3.extent(data, d => d[1]).map(y);
    const k = 0.9 * Math.min(width / (x1 - x0), height / (y1 - y0));
    const tx = (width - k * (x0 + x1)) / 2;
    const ty = (height - k * (y0 + y1)) / 2;
    const overview = ["Overview", d3.zoomIdentity.translate(tx, ty).scale(k)];
  
    return [overview].concat(d3.groups(data, d => d[2]).map(([key, data]) => {
      const [x0, x1] = d3.extent(data, d => d[0]).map(x);
      const [y1, y0] = d3.extent(data, d => d[1]).map(y);
      const k = 0.9 * Math.min(width / (x1 - x0), height / (y1 - y0));
      const tx = (width - k * (x0 + x1)) / 2;
      const ty = (height - k * (y0 + y1)) / 2;
      return [`Cluster ${key}`, d3.zoomIdentity.translate(tx, ty).scale(k)];
    }))
  }
  ```
