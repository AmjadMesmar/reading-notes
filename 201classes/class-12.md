
# Article Summaries

## Article 1: EASILY CREATE STUNNING ANIMATED CHARTS WITH CHART.JS

- Charts are far better for displaying data visually than tables and have the added benefit that no one is ever going to press-gang them into use as a layout tool. They’re easier to look at and convey data quickly but they’re not always easy to create.

- A great way to get started with charts is with ***Chart.js***, a JavaScript plugin that uses HTML5’s canvas element to draw the graph onto the page. It’s a well documented plugin that makes using all kinds of bar charts, line charts, pie charts and more, incredibly easy.

## Setting up

- The first thing we need to do is download Chart.js. Copy the Chart.min.js out of the unzipped folder and into the directory you’ll be working in. Then create a new html page and import the script:

![Charts](Images201/charts.png)

## Drawing a line chart

- To draw a line chart, the first thing we need to do is create a canvas element in our HTML in which Chart.js can draw our chart. So add this to the body of our HTML page:

![Charts](Images201/charts2.png)

Next, we need to write a script that will retrieve the context of the canvas, so add this to the foot of your body element:

![Charts](Images201/charts3.png)

- (We can actually pass some options to the chart via the Line method, but we’re going to stick to the data for now to keep it simple.)

Inside the same script tags we need to create our data, in this instance it’s an object that contains labels for the base of our chart and datasets to describe the values on the chart. Add this immediately above the line that begins ‘var buyers=’:

![Charts](Images201/charts4.png)

If you test your file in a browser you’ll now see a cool animated line graph.

## Article 2: Basic usage of canvas

- At first sight a <***canvas***> looks like the <***img***> element, with the only clear difference being that it doesn't have the src and alt attributes. Indeed, the <***canvas***> element has only two attributes, width and height. These are both optional and can also be set using DOM properties. When no width and height attributes are specified, the canvas will initially be 300 pixels wide and 150 pixels high. The element can be sized arbitrarily by CSS, but during rendering the image is scaled to fit its layout size: if the CSS sizing doesn't respect the ratio of the initial canvas, it will appear distorted.

**References:**

- EASILY CREATE STUNNING ANIMATED CHARTS WITH CHART.JS [Read the full article here](https://www.webdesignerdepot.com/2013/11/easily-create-stunning-animated-charts-with-chart-js/)

- Basic usage of canvas [Read the full article here](https://developer.mozilla.org/en-US/docs/Web/API/Canvas_API/Tutorial/Basic_usage/)

- EASILY CREATE STUNNING ANIMATED CHARTS WITH CHART.JS [Read the full article here](https://www.webdesignerdepot.com/2013/11/easily-create-stunning-animated-charts-with-chart-js/)

- EASILY CREATE STUNNING ANIMATED CHARTS WITH CHART.JS [Read the full article here](https://www.webdesignerdepot.com/2013/11/easily-create-stunning-animated-charts-with-chart-js/)

- EASILY CREATE STUNNING ANIMATED CHARTS WITH CHART.JS [Read the full article here](https://www.webdesignerdepot.com/2013/11/easily-create-stunning-animated-charts-with-chart-js/)

## [Main page](https://amjadmesmar.github.io/reading-notes/)