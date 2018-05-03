# owf-lib-viz-fullpagejs-story
Open Water Foundation library to visualize a story using [fullpage.js](https://alvarotrigo.com/fullPage/) JavaScript library

## Design
The main functionality of this page is built using features provided in [fullpage.js](https://alvarotrigo.com/fullPage/) Javascript Library. Some of the layout is created using the grid system of [bootstrap](https://getbootstrap.com/) Javascript Library.  
Currently, we are limited to only using the basic scrollable features of this library. There are several [extensions](https://alvarotrigo.com/fullPage/extensions/) available, but these require the payment of a fee. For the most part, a scrollable page is sufficient enough to accomplish what we need, and the extensions can be added later, if necessary.

## Navbar

At the top of `index.html` there is code for the navigation bar. This nav-bar is created using [bootstrap.js](https://getbootstrap.com/docs/4.0/components/navbar/#nav).  
The links used in the nav-bar must correspond to the configuration of the `anchors` variable for the full page object, found in the script tags at the bottom of `index.html`.

Example:
```JavaScript
$("#fullpage").fullpage({
  anchors:['sectionTitle1', 'sectionTitle2', 'sectionTitle3']
})
```

```html
<ul class="navbar-nav">
  <li class="nav-item">
    <a class="nav-link js-scroll-trigger" href="#sectionTitle1">Section 1</a>
  </li>
  <li class="nav-item">
    <a class="nav-link js-scroll-trigger" href="#sectionTitle2">Section 2</a>
  </li>
  <li class="nav-item">
    <a class="nav-link js-scroll-trigger" href="#sectionTitle3">Section 3</a>
  </li>
</ul>
```

## Full Page
#### Html
The set up for fullpage.js is easy to implement in `index.html`. Begin with a containing div `id='fullpage'`, and then each different section for the webpage is contained in separate divs all with `class='section'`.
Example:  
```html
<div id="fullpage">
  <div class="section"></div>
  <div class="section"></div>
  <div class="section"></div>
</div>
```

#### JavaScript
Once the html has been added to the page, you can configure the fullpage object to implement scrolling features.
The simplest way to implement fullpage is to allow all defaults with no configurations:
```javascript
$(document).ready(function(){
  #('#fullpage').fullpage();
})
```
The current configurations are as follows:
```javascript
$(document).ready(function() {
  $('#fullpage').fullpage({
    //assigns links to different sections
    anchors:['top','section-one','gapminder', 'colorado-river', 'section-two', 'copyright'],
    //sets background colors to different sections
    sectionsColor:['#9DB66B','','','','','#5A5A5A'],
    //initializes bullet scrolling on right side of page
    navigation:true,
    navigationPosition:'right',
    navigationTooltips:['OWF Visualizations','Section 1','Gapminder', 'Colorado River', 'Section 2', 'Copyright']
  });
});
```
See more configuration options at [fullpage options](https://github.com/alvarotrigo/fullPage.js#options)

## Bootstrap
For convenience and simplicity this page implements the use of the [bootsrap](https://getbootstrap.com/) JavaScript library to organize the contents in each section.  
in general, this page utilizes the [grid system](https://getbootstrap.com/docs/4.0/layout/grid/) that bootstrap provides to help automatically size width of divs.
Other bootstrap classes are used for [centering text](https://getbootstrap.com/docs/4.0/utilities/text/).

## Resources

* [fullPage.js](https://alvarotrigo.com/fullPage/)
* [bootstrap](https://getbootstrap.com/)
