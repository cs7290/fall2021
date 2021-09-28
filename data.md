
# Data

Learning goals 

* Introduce the various ways to get (CORS-enabled) data in/out of observable notebooks
* d3.json (the easy way) vs fetch (the hard way) vs XMLHttpRequest (the IE way...yuck!)
* Start thinking about potential data sources for term project

## Reference

* [Introduction to Data](https://observablehq.com/@observablehq/introduction-to-data) -- mbostock notebook
  * [Introduction to Promises](https://observablehq.com/@observablehq/introduction-to-promises)
  * [d3.autoType](https://observablehq.com/@d3/d3-autotype)
  * [check for date](https://stackoverflow.com/questions/643782/how-to-check-whether-an-object-is-a-date)
  * [Introduction to Imports](https://observablehq.com/@observablehq/introduction-to-imports)

## Data sources

* [Working with the census API](https://observablehq.com/@mbostock/working-with-the-census-api) -- mbostock notebook
* [Map](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Map) -- MDN

## CORS

* [Same Origin Policy (SOP)](https://en.wikipedia.org/wiki/Same-origin_policy)
  * Web browsers restrict the ability for a script in a one web page to access data from a second web page.
  * Under the SOP, both web pages must have the same origin (combination of URI scheme, hostname, port)
  * The SOP exists because it has important security implications.
  * The issue: browser requests for web content include authentication credentials (cookies)
    * These cookies maintain your "user session"
    * For example, when you're logged into gmail or a banking site, you only need to log in once.
  * The problem occurs if you're logged into your bank site, and then you accidentally click on evil.com
    * In that case, evil.com could send a request to your bank site using your credentials.
    * The thing is, many sites have open data in which case the SOP is overly restrictive.
* Cross-Origin Resource Sharing (CORS) comes to the rescue.
  * CORS is a networking mechanism that allows websites to share open data.
  * The [CORS](https://developer.mozilla.org/en-US/docs/Web/HTTP/CORS) reference at MDN is fairly complex (confusing?).
  * It talks about HTTP headers, and distinguishes the servers associated with same-origin and cross-origin requests
  * Basically, a website that wants to share its data openly, without authentication, just needs to say so explicitly.
  * If it doesn't, then the browser will block access.
  * The [UC Irvine ML Repository](https://archive.ics.uci.edu/ml/index.php) is not CORS-enabled, even though they serve open data. In that case, if your file isn't too big, you'll need to download the data locally and then upload it to your Observable notebook.
 s a file attachment.
 * [CORS tutorial](https://www.html5rocks.com/en/tutorials/cors//)
* Checking for CORS
  * The following URL throws a fetch error if you try to load the data in  Observable
  * `curl -I https://archive.ics.uci.edu/ml/machine-learning-databases/iris/iris.data` -- no headers
  * Whereas the following request includes a CORS header: "Access-Control-Allow-Origin: *"
  * `curl -I https://earthquake.usgs.gov/earthquakes/feed/v1.0/summary/4.5_hour.geojson` -- CORS enabled
