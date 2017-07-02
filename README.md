## Performance Optimization

This is a project for Udacity performance optimization course. Instructions for the project and files before performance optimization can be found on [Udacity github repository](https://github.com/udacity/frontend-nanodegree-mobile-portfolio) 

Changes done by me to achieve better webpage performance:

#### Part 1: Optimize PageSpeed Insights score for index.html

1. Size of images optimized.

2. All styles inlined in `<head>`.

3. Fonts served locally.

4. Critical rendering path blocking scripts loaded asynchronously by adding `async` attribute.

#### Part 2: Optimize Frames per Second in pizza.html

1. Critical rendering path analyzed, forced layout reflows found and removed.

  function changePizzaSizes(size) {
      for (var i = 0; i < document.querySelectorAll(".randomPizzaContainer").length; i++) {
        var dx = determineDx(document.querySelectorAll(".randomPizzaContainer")[i], size);
       var newwidth = (document.querySelectorAll(".randomPizzaContainer")[i].offsetWidth + dx) + 'px';
       document.querySelectorAll(".randomPizzaContainer")[i].style.width = newwidth;
       }
    }

  function changePizzaSizes(size) {
      for (var i = 0; i < document.querySelectorAll(".randomPizzaContainer").length; i++) {
        var dx = determineDx(document.querySelectorAll(".randomPizzaContainer")[i], size);
 -      var newwidth = (document.querySelectorAll(".randomPizzaContainer")[i].offsetWidth + dx) + 'px';
 -      document.querySelectorAll(".randomPizzaContainer")[i].style.width = newwidth;
 +    }
 +    for (var j = 0; j < document.querySelectorAll(".randomPizzaContainer").length; j++) {
 +      var newwidth = (document.querySelectorAll(".randomPizzaContainer")[j].offsetWidth + dx) + 'px';
 +      document.querySelectorAll(".randomPizzaContainer")[j].style.width = newwidth;
      }
    }

2. Performance increased with hardware accelerated CSS - the GPU triggered by including the `transform: translateZ(0)`; declaration for `.mover` class in `pizza.html`. 

3. `backface-visibility: hidden` property (which can make a huge difference in no so powerful equipments as it enables hardware acceleration) added for `.mover` class in `pizza.html`.

