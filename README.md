Udactiy Website Optimization Project
====================================

## Introduction

This is the website optimization project that is part of Udactiy's Front-end Web Developer Nanodegree.

* As part of the project, we were given an established repository for a website designed by one of the course developers.
* It was our responsibility to optmize the files in the repository so that the homepage of the website has a pageSpeed Insights score of 90 or higher on mobile and desktop formats. 
* We were also required to optimize Cam's Pizzeria so that the page scrolls within 60 frame per second. 
* Lastly, we were required to optmize the feature on the Cam's Pizzeria page that renders small, medium, and large size pizzas. The requirement is that these pizza images have to render in 5 milliseconds or less. 

## Files

The files that were optimized in this project are as follows:

Grunt was used to minify these files:
* index.html,
* pizza.html,
* css/print.css,
* js/perfmatters.js
* views/css/bootstrap-grid.css,
* views/js/main.js

The optimization changes were made to these files:
* index.html,
* css/style.css,
* views/js/main.js

The images were compressed using compressjpeg.com and compresspng.com, these images were compressed:
* pizza.png,
* profilepic.jpg,
* pizzeria.jpg

## Getting Started

To checkout the project:

1. Go to the GitHub repository which is located [https://github.com/hernanal/frontend-nanodegree-mobile-portfolio](here).
2. On the left, a little ways down the page, find the drop down button that says "Branch". Select the gh-pages branch.
3. Click the button that says "clone or download" and download the zip file.
4. Find the zip file on your local machine and extract all the files.
5. Find the index.html in the root directory and open it.
6. If you just want to view the website you can follow this [https://hernanal.github.io/frontend-nanodegree-mobile-portfolio/](link).

## Specific optimizations

* Optimizations made to index.html are as follows:

** Smaller image of pizzeria was added to increase pageSpeed insights score.
** Media attribute was added to print.css to prevent it from blocking page rendering since it is only utilized when printing.
** Async tag was added to analytics.js to prevent it from blocking parsing of the html.
** style.css was inlined into index.html to prevent it from blocking rendering of the page.
** profilepic.jpg was compressed to increase the pageSpeed insights score.
** The smaller pizzeria image was compressed to further increase pageSpeed insights score. 


* Optimizations made to views/js/main.js are as follows:

** All querySelectorAll instances were replaced with getElementsByClassName because it is a more performant way of gathering elements. This was done per the advise of one of the instructors in the webcasts. 
** All querySelector instances were replaced with getElementsById because it is more performant.
** After the first timeline recording of the scrolling on Cam's Pizzeria it was determined that the updatePositions function was the source of a Forced Syncronous Layout(FSL) because layout was being triggered before the style was being set. Variables, len and scroll, were created outside of the for loop to assist in solving this bottleneck. Lines 517 and 518.
** The sliding pizzas that move in the background when the page is scrolled were reduced from 200 to 30. This greatly improved the speed of the page and there was no noticable change to the background.

* The last part of the project required us to optimize the pizza resizing feature on Cam's Pizzeria site. 
** A recording of the timeline showed a FSL within the function determineDx. To solve this bottleneck, the determineDx function was removed because further inspection revealed that it was essentially useless. Lines 426-448.
** The code from the sizeSwitcher function that was inside of the determineDx function was modified and moved into changePizzaSizes function. Lines 452-464.  
** The randomPizzas variable was added outside of the for loop to reduce the repetitiveness that existed inside the function. Line 465.
** The for loop was modified so that it only batches the style changes to the pizza's width. 

After all of these changes the average average scripting time for the last 10 frames is around 0.68 milliseconds, which is significantly below the 10-12 milliseconds required to render at 60 frames per second. 

The average time to resize pizzas is around 3.12 milliseconds, which is below the minimum requirement of 5 milliseconds to be performant. 

The pageSpeed insights scores for the mobile and desktop formats are 95/100 and 91/100 respectively. Both above the minimum requirement of 90/100. 

## References

[http://stackoverflow.com/questions/14377590/queryselector-and-queryselectorall-vs-getelementsbyclassname-and-getelementbyid](querySelector and querySelectorAll vs getElementById and getElementsByClassName in JavaScript)

[https://developer.chrome.com/devtools/docs/device-mode](Device mode and Mobile Emulation)

[https://developer.chrome.com/devtools/docs/timeline](Performance profiling with the Timeline)

[https://developer.chrome.com/devtools/docs/timeline#timeline-event-reference](Timeline event reference)

[https://developers.google.com/web/fundamentals/performance/optimizing-content-efficiency/optimize-encoding-and-transfer#minification-preprocessing--context-specific-optimizations](Data compression 101)

[https://developers.google.com/web/fundamentals/performance/optimizing-content-efficiency/http-caching](HTTP caching)

[https://developers.google.com/web/fundamentals/performance/critical-rendering-path/render-blocking-css](Render blocking CSS)

[https://developers.google.com/web/fundamentals/performance/critical-rendering-path/adding-interactivity-with-javascript](Adding interactivity with JavaScript)

[https://developers.google.com/web/fundamentals/performance/critical-rendering-path/optimizing-critical-rendering-path](Optimizing the critical rendering path)

[https://developers.google.com/web/fundamentals/performance/critical-rendering-path/analyzing-crp#performance-patterns](Analyzing critical rendering path performance)

[http://gent.ilcore.com/2011/03/how-not-to-trigger-layout-in-webkit.html](How to NOT to trigger a layout in WebKit)





