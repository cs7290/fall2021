
# Leaflet

### D3 + Leaflet + Tooltip

Add a tooltip to [D3 + Leaflet](https://observablehq.com/@pbogden/d3-leaflet)

* Solution: [D3 + Leaflet + Tooltip](https://observablehq.com/d/45bd10fffb0dadf7)
  * Uses toolip "hover" method from [Plot Tooltip](https://observablehq.com/@mkfreeman/plot-tooltip)
* Requires remarkably little change to [D3 + Leaflet](https://observablehq.com/@pbogden/d3-leaflet)
  * Compare fork to see what changed.

### D3 + Leaflet + Legend

Add a color legend to [D3 + Leaflet](https://observablehq.com/@pbogden/d3-leaflet)

* Solution: [D3 + Leaflet + Legend](https://observablehq.com/d/e2bdf94949131ab3)
  * This fork of [D3 + Leaflet](https://observablehq.com/@pbogden/d3-leaflet) requires little change.
  * It uses the color legend method from [Plot Color Legend](https://observablehq.com/@ambassadors/plot-color-legend).
  * Compare fork to see what changed.
* The scale...
  * I randomly choose between several categorical colors for each state. (`frac` property is set when creating `states`)
  * The state color is set on "mouseover" and "mouseout".
  * The scale is implemented with [`d3.scaleOrdinal()`](https://github.com/d3/d3-scale#ordinal-scales)
* The legend...
  * Color legends -- with D3
    * There are various kinds of color [D3 scales](https://github.com/d3/d3-scale)
    * And there are just as many [Color Legends](https://observablehq.com/@d3/color-legend)
    * Each of these color legends is a simple SVG.
  * Color legends -- with Plot
    * The recommendation for this exercise is to use the color legend from Observable Plot
    * Import `colorLegend` from [Plot Color Legend](https://observablehq.com/@ambassadors/plot-color-legend)
    ```
    import {colorLegend} from "@ambassadors/plot-color-legend"
    ```
    * The notebook has a categorical color scale (ordinal scale) that's appropriate for "colorLegend"
    * Use `colorLegend` without modification, along with some optional parameters
    * `colorLegend(colorScale)` -- on its own, this creates a nice SVG legend for categorical data
      * colorScale.domain()
      * colorScale.range()
    * You can experiment with optional parameters (but be careful to assure square color swatches)
      * `{width: 150 + 30, marginRight: 150}` -- width should equal marginRight + 30 to assure square swatches
      * If you set `colorScale.domain(['1', '2', '3', '4', 'this is a super long line'])`, then it doesn't fit
      * That's when you need a wider margin
* Leaflet integration
  * Add a "Custom Legend Control" as per [Leaflet Choropleth example](https://leafletjs.com/examples/choropleth/)
  * The custom legend tutorial adds and styles a div and appends the HTML for a legend.
  * This code will add a simple styled div element, without a legend
  ```
  var legend = L.control({position: 'bottomright'});

  legend.onAdd = function (map) {
      var div = L.DomUtil.create('div', 'info legend');

      div.style['width'] = "100px";
      div.style['height'] = "100px";
      div.style['box-shadow'] = "0 0 15px rgba(0,0,0,0.2)";
      div.style['border-radius'] = "5px";
      div.style['background'] = "crimson";
  
      return div;
  };
  
  legend.addTo(map);
  ```
  * We use D3 to append our SVG color legend to the div
  ```
  var legend = L.control({position: 'bottomright'});

  legend.onAdd = function (map) {
      var div = L.DomUtil.create('div', 'info legend');
      let mr = 30; // Hint: Keep width = 30 + marginRight for square swatches
      const myLegend = colorLegend(colorScale, {tickPadding: 10, width: mr + 30, marginRight: mr});

      div.style['width'] = "100px";
      div.style['height'] = "100px";
      div.style['box-shadow'] = "0 0 15px rgba(0,0,0,0.2)";
      div.style['border-radius'] = "5px";
      div.style['background'] = "crimson";
      myLegend.style.background = "rgba(255,255,255,0)";
      d3.select(div).append(() => myLegend);
      // div.appendChild(myLegend) // this works too, it's equivalent to the previous line (see MDN for appendChild)
  
      return div;
  };
  
  legend.addTo(map);
  ```
  * You can experiment with this to see how it affects the content of Leaflet's div

### Stamen tiles

Change the tile service in [D3 + Leaflet](https://observablehq.com/@pbogden/d3-leaflet) to use Stamen tiles.

* [D3 + Leaflet + Stamen](https://observablehq.com/d/8899743901e6b503)
  * Uses [map tiles from Stamen](http://maps.stamen.com/#watercolor/12/37.7706/-122.3782)
  * Requires manipulation of the URL string
* [TileLayer reference docs](https://leafletjs.com/reference.html#tilelayer) -- leafletjs.com
  * It's worth looking at this documentation
  * Describes configurable parameters in the URL

### OSM data viz

Show (on the map of [OSM data viz](https://observablehq.com/@pbogden/osm-data-viz)) only those features that have a name (i.e., non-zero d.properties.tags.name)

* To get this, you have to find the code that determines what is shown in the tooltip
* It's the callback: onEachFeature -- see GeoJSON on Leaflet
* Solution: [OSM data viz 2](https://observablehq.com/d/8e573cbd7bd7bbf6)
