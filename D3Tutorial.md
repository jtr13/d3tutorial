D3 Tutorial
================
Joyce Robbins
2017-12-03

-   [Setup](#setup)
-   [HTML](#html)
-   [D3 (text only... no graphics)](#d3-text-only...-no-graphics)
-   [SVG](#svg)
-   [References](#references)

### Setup

1.  If you don't have it already, download the Chrome browser.

### HTML

1.  #### Create an .html file and view it with Chrome Developer Tools

    1.  Create a text file in RStudio\* (File, New File, Text File) (\* or whatever text editor you are using)
    2.  Here is the structure of a simple .html document, which consists of a "head" and a "body". Type it in and save the file as "myfile.html"

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

### D3 (text only... no graphics)

1.  #### Select an element with `d3.select` and remove it

    1.  To use D3 we need to access a D3 library, which takes the form of a file ending in .js. We can either download it or link to it online. We'll do the latter by adding the following line immediately after the title line in the head section of our html file:
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

    2.  Check the *Elements* tab and observe what has changed.

### SVG

1.  #### Create an SVG element in `myfile.html`

    1.  Add the following immediately after the `<body>` tag.
        `<svg width = "500" height = "500"></svg>`
    2.  Save and refresh in the browser... what happened?

2.  #### Add shapes to the SVG element (inbetween the `<svg>` and `</svg>` tags

    1.  Add a rectangle (that fills the "canvas"): `<rect x="0" y = "0" width = "500" hieght = "500" fill = "aquamarine"></rect>`
    2.  Add other shapes, such as: `<circle cx="150" cy="150" r="50" fill="blue"></circle>`
    3.  See here for inspiration: <https://developer.mozilla.org/en-US/docs/Web/SVG/Tutorial/Basic_Shapes>
    4.  Style your shapes with inline CSS: <https://developer.mozilla.org/en-US/docs/Web/SVG/Tutorial/Fills_and_Strokes>
    5.  Create an original piece of art!
    6.  Advanced svg: <https://developer.mozilla.org/en-US/docs/Web/SVG/Tutorial/Paths>

### References

Best for complete beginners:

Scott Murray

-   Curran Kelleher
