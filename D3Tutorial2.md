D3 Tutorial
================
Joyce Robbins
2017-12-05

-   [D3 (+SVG) in the .html file](#d3-svg-in-the-.html-file)

### D3 (+SVG) in the .html file

1.  Let's create a new file:

        <!DOCTYPE HTML>
        <html lang="en">
        <head>
            <meta charset="utf-8">
            <title>This is my second html file.</title>
            <script src="https://d3js.org/d3.v4.min.js"></script>
        </head>
        <body>
            <svg width = "600" height = "600">
                <rect x = "0" y = "0" width = "600" height = "600" fill = "#FFDFED"></rect>
            </svg>
        </body>
        </html>

2.  Add a circle with D3, by adding the following after the `<svg></svg>` section:

            <script>
          var mysvg = d3.select("svg")
          mysvg.append("circle")
            .attr("cx", 100)
            .attr("cy", 200)
            .attr("r", 50)
            .attr("fill", "red");
            </script>

3.  Add another circle after the first one.

          mysvg.append("circle")
            .attr("cx", 200)
            .attr("cy", 300)
            .attr("r", 25)
            .attr("fill", "blue");

4.  And a third one of your choosing.
5.  Save an extra copy of the file and erase the circles. We're going to add them in a different way. Use this script instead:

            <script>
        var data = [1, 2, 3];
        var mysvg = d3.select("svg")
        mysvg.selectAll("circle")
          .data(data)
          .enter().append("circle")
          .attr("cx", function(d) { return d*50 + 100; })
          .attr("cy", "200")
          .attr("r", function(d) { return d*5; })
          .attr("fill", "green");
            </script>
