
# HTML

Learning goals

* Minimal HTML page
* Valid HTML
* Running things locally
* CSS
* Embedding Observable notebooks
* Tachyons

# Hello, world!

Here's the "Hello, World!" from https://pages.github.com/

```
<!DOCTYPE html>
<html>
<body>
<h1>Hello World</h1>
<p>I'm hosted with GitHub Pages.</p>
</body>
</html>
```

It's not a "valid" HTML file in that it doesn't pass the test at https://validator.w3.org/.
This file passes the test...

```
<!DOCTYPE html>
<html lang=en>
<meta charset=utf-8>
<title>hello</title>
<body>
<h1>Hello World</h1>
<p>I'm hosted with GitHub Pages.</p>
</body>
</html>
```

The next file just generates a warning -- recommends adding a "lang" attribute to the "html" start tag.
Notice that some of the tags aren't completed explicitly -- it's automatic.

```
<!DOCTYPE html>
<meta charset=utf-8>
<title>hello</title>
<body>
<h1>Hello World</h1>
<p>I'm hosted with GitHub Pages.
```

You can serve any these files locally one line of Python...

```
python -m http.server
```
Then browse to http://localhost:8000 or http://127.0.0.1:8000

* http://localhost:8000/index.html -- the minimal page

# Observable embedding

Embedding charts from an Observable notebook is remarkably easy.

* http://localhost:8000/index2.html -- epicyclic gearing (embedded)
* [Introduction to Embedding](https://observablehq.com/@observablehq/introduction-to-embedding)
* [Epicyclic Gearing](https://observablehq.com/@mbostock/epicyclic-gearing)

```
<!DOCTYPE html>
<meta charset=utf-8>
<title>hello</title>
<body>
<h1>Hello World</h1>
<iframe width="100%" height="716" frameborder="0"
  src="https://observablehq.com/embed/@mbostock/epicyclic-gearing?cells=graphic"></iframe>
```

The iframe above doesn't validate, but it works.

```
<!DOCTYPE html>
<meta charset=utf-8>
<title>hello</title>
<body>
<h1>Hello World</h1>
<iframe width="100%" height="716" frameborder="0"
  src="https://observablehq.com/embed/@mbostock/epicyclic-gearing?cells=graphic"></iframe>
```

## CSS

What is CSS?

* http://localhost:8000/index3.html -- grid demo -- a little CSS
* [CSS](https://developer.mozilla.org/en-US/docs/Web/CSS)
* [Getting started](https://developer.mozilla.org/en-US/docs/Learn/CSS/First_steps/Getting_started)
* [CSS Grid Layout](https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_Grid_Layout) -- MDN

CSS is hard! Why do I want to know about CSS?

* [Advanced Embedding](https://observablehq.com/@observablehq/downloading-and-embedding-notebooks)
* [tachyons](http://tachyons.io/)
* [github primer](https://primer.style/css/)

What's tacyons?

* http://localhost:8000/index4.html -- tachyons demo
* http://tachyons.io/ -- tachyons
* http://tachyons.io/components/#nav -- nav components
