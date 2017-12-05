D3 Tutorial
================
Joyce Robbins
2017-12-05

-   [Setup](#setup)
-   [HTML](#html)
-   [D3 (+ text)](#d3-text)
-   [SVG](#svg)
-   [D3 (+ SVG) in the console](#d3-svg-in-the-console)
-   [D3 (+ SVG) in the .html file](#d3-svg-in-the-.html-file)
-   [References](#references)

### Setup

1.  If you don't have it already, download the Chrome browser.

### HTML

1.  #### Create an .html file and view it with Chrome Developer Tools

    1.  Create a text file in RStudio\* (File, New File, Text File) (\*or whatever text editor you are using)
    2.  Here is the structure of a simple .html document, which consists of a "head" and a "body". Type it in and save the file as "myfile.html" (Read more [here](https://designshack.net/articles/html/what-is-html-the-anatomy-of-an-html5-document/) on the structure of an HTML5 document.)

            <!DOCTYPE html>
            <html lang="en">
            <head>
                <meta charset="utf-8">
                <title></title>
            </head>
            <body>
            </body>
            </html>

    3.  Add a title (doesn't appear on the web page itself) to the *head* section and various elements to the *body*, such as headers and at least three paragraph elements, such as:

            <h3>This is an h3 header.</h3> 
            <p>This is a paragraph.</p> 
            <p>This is another paragraph.</p>
            <p>This is a third paragraph.</p>

    4.  Open it in Chrome on half the screen, and keep RStudio (or whatever text editor you're using) open on the other half of the screen.

    5.  Make a change to the .html file, save it and refresh the file in the browser to see it. (Keyboard shortcuts such as cmd-s and cmd-r are helpful.)

    6.  In Chrome, **View Developer Developer Tools** to view *DOM elements.*

### D3 (+ text)

1.  #### Select an element with `d3.select` and remove it

    1.  To use D3 we need to access a D3 library, which takes the form of a file ending in .js. We can either download it or link to it online. We'll do the latter by adding the following line immediately after the `<title>...</title>` line in the head section of our html file:
        `<script src="https://d3js.org/d3.v4.min.js"></script>`
        (Source: <https://www.d3js.org>)
    2.  Save the file, go back to Chrome, refresh the page and click on "Console" next to the "Elements" tab.
    3.  Type the following in the console:
        `> d3.select("p").remove()`
        What happened?
    4.  Refresh the page. What happened?

2.  #### Select an element with `d3.select` and style it

    1.  Try the following (or variations thereof):

            > d3.select("p").style("color", "blue")
            > d3.select("p").style("background-color", "yellow")
            > d3.select("p").style("font-size", "24px")
            > d3.select("p").style("font-weight", "bold")

        (Refresh)

3.  #### Select multiple elements with `d3.selectAll` and style them:

    `> d3.selectAll("p").style("color", "purple")`

4.  #### Assign a selection to a variable and style it

    1.  Type the following in the console:
        (Note: `var` is JavaScript, not D3 per se).

            > var columbia = d3.selectAll("p")
            > columbia.style("background-color", "green")

    2.  Make other changes using "columbia" instead of `d3.selectAll("p")`.

5.  #### Chaining

    Combine multiple style instructions on the same line:

    `> columbia.style("color", "red").style("font-size", "30px")`

6.  #### Add an element with `d3.append`

    1.  Type the following in the console:

            > var nyc = d3.select("body")
            > nyc.append("h1")
            > d3.select("h1").text("This is an h1 header.")

    2.  Click the *Elements* tab and observe what has changed in the DOM.
    3.  Refresh the browser and inspect the DOM once again.

### SVG

1.  #### Create an SVG element in `myfile.html`

    1.  Add the following immediately after the `<body>` tag.
        `<svg width = "500" height = "400"></svg>`
    2.  Save and refresh in the browser... what happened?

2.  #### Add shapes to the SVG element (inbetween the `<svg>` and `</svg>` tags

    1.  Add a rectangle (that fills the "canvas"): `<rect x="0" y = "0" width = "500" height = "400" fill = "aquamarine"></rect>`
    2.  Add other shapes, such as: `<circle cx="150" cy="150" r="50" fill="blue"></circle>`
    3.  See here for inspiration: <https://developer.mozilla.org/en-US/docs/Web/SVG/Tutorial/Basic_Shapes>
    4.  Style your shapes with inline CSS: <https://developer.mozilla.org/en-US/docs/Web/SVG/Tutorial/Fills_and_Strokes>
    5.  Create an original piece of art!
    6.  Advanced svg: <https://developer.mozilla.org/en-US/docs/Web/SVG/Tutorial/Paths>

### D3 (+ SVG) in the console

1.  #### Select and modify shapes

    We will now use `d3.select` and `d3.selectAll` to select shapes through the JavaScript console and modify them, as we did previously with HTML elements. Try the following (or variations thereof):

        > d3.selectAll("circle").attr("fill", "red");
        > d3.selectAll("circle").attr("cx", "20");
        > d3.selectAll("circle").attr("r", "100");
        > d3.selectAll("circle").attr("fill", "white");
        > d3.selectAll("circle").attr("stroke", "blue");

2.  #### Add shapes with `.append`

    1.  Add a rectangle as follows:

            > d3.select("svg").append("rect").attr("x", "10").attr("y", "10")
            .attr("width", "100").attr("height", "200").attr("fill", "pink");

        Alternate method:
        Add `<script src="https://d3js.org/d3-selection-multi.v1.min.js"></script>` immediately after the `<body>` tag and then do the following:

            > d3.select("svg").append("rect").attrs({ x: 10, y: 10, width: 80, height: 80, fill: 'red' })

    2.  Click the *Elements* tab to observe changes in the DOM.

3.  #### Add transitions with `.transition()` and `.duration()`

    1.  Movement

            > d3.select("circle").transition().duration(5000).attr("cx", "400");
            > d3.select("circle").transition().duration(5000).attr("cy", "400");
            > d3.select("circle").transition().duration(5000).attr("cx", "100");
            > d3.select("circle").transition().duration(5000).attr("cy", "100");

    2.  Change size

            > d3.select("circle").transition().duration(5000).attr("r", "30");

    3.  Change fill color

            > d3.select("circle").transition().duration(5000).attr("fill", "purple");

    4.  Combine multiple attributes with chaining, such as:

            > d3.select("circle").transition().duration(5000).attr("fill", "white").attr("cx","250").attr("cy","250").attr("r","25");

### D3 (+ SVG) in the .html file

1.  #### Create transitions that happen when the web page is loaded

    1.  Add the following to `myfile.html` at the *end* of the body section (right before `</body>`):

            <script type = "text/javascript">
            d3.select("circle").transition().duration("5000").
            attr("cx", "300").attr("cy","300").attr("fill","green");
            </script>

    2.  Save it and refresh in the browser.
    3.  Add additional transitions.

### References

These authors are absolutely the best teachers for complete beginners, *however*, free versions of their materials are only available for the previous version of D3 (version 3):

#### Curran Kelleher

(free) <https://github.com/curran/screencasts/tree/gh-pages/introToD3>

(paid): <https://www.manning.com/livevideo/d3-js-in-motion>

#### Scott Murray

(free): <http://alignedleft.com/tutorials/d3>

(paid): <http://alignedleft.com/work/d3-book-2e>
