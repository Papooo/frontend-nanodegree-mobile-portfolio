## Performance Optimization

This is a project for Udacity performance optimization course. Instructions for the project and files before performance optimization can be found on [Udacity github repository](https://github.com/udacity/frontend-nanodegree-mobile-portfolio) 

Changes done by me to achieve better webpage performance:

#### Part 1: Optimize PageSpeed Insights score for index.html

* Size of images optimized.

* All styles inlined in `<head>`.

* Fonts served locally.

* Critical rendering path blocking scripts loaded asynchronously by adding `async` attribute.

#### Part 2: Optimize Frames per Second in pizza.html

* Critical rendering path analyzed, forced layout reflows found and removed.

* Faster web API calls used - `document.getElementById()` and `document.getElementByClassName()` instead of `document.querySelector()` and `document.querySelectorAll()`

* Local variables outside the loop created when possible, so the DOM is not explicitly touched in every iteration.

* Instead of static 200, number of pizzas needed to fill the screen calculated dynamically, based on browser window resolution.
     
* Performance increased with hardware accelerated CSS - the GPU triggered by including the `transform: translateZ(0)`; declaration for `.mover` class in `pizza.html`. 

* `backface-visibility: hidden` property (which can make a huge difference in no so powerful equipments as it enables hardware acceleration) added for `.mover` class in `pizza.html`.

