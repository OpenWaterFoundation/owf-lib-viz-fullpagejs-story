# owf-lib-viz-fullpagejs-story
Open Water Foundation library to visualize a story using [fullpage.js](https://alvarotrigo.com/fullPage/) JavaScript library

## Design
The main functionality of this page is built using features provided by the [fullpage.js](https://alvarotrigo.com/fullPage/) Javascript Library. Some of the layout is managed using the grid system provided by the [bootstrap](https://getbootstrap.com/) Javascript Library.  

Currently, we are limited to only using the basic scrollable features of this library. There are several [extensions](https://alvarotrigo.com/fullPage/extensions/) available, that provide features such as horizontal scrolling and parallax effect. However, the extensions for the fullpage.js library require purchase. For the most part, a scrollable page is sufficient enough to accomplish what is needed, and the extensions can be added later, if necessary.

## Navbar

At the top of `index.html` there is code for the navigation bar. This nav-bar is created using [bootstrap.js](https://getbootstrap.com/docs/4.0/components/navbar/#nav).  
To make use of the visual scrolling features provided by fullpage.js, the links specified in the nav-bar must correspond to the anchor names configured by the `anchors` variable for the full page object. This can be found in the script tags at the bottom of `index.html`.

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
The following example demonstrates placing an iframe containing a visualization next to a text description to go along with it. Everything is contained in a row element, the visualization is set to take up 8 width and the text is of width 4 to fill the remaining space in the grid:
```html
<div class="row">
  <div class="col-lg-8">
    <iframe data-src="http://viz.openwaterfoundation.org/co/owf-viz-co-snodas-gapminder/" scrolling="no" frameborder="0"></iframe>
  </div>
  <div class="col-lg-4">
     <h2>Gapminder</h2>
      <p>This visualization has been developed
      to illustrate how snowpack changes in water supply basins throughout Colorado in a
      water year.
      The goal is to quickly gain an understanding of both the absolute and relative magnitude of water supply throughout Colorado.
      The visualization illustrates how conditions in local and major basins vary in time and compare to each other.
      The basins correspond to those used by the National Weather Service (NWS) River Forecast Centers (RFCs) and Northern Water.
      ABRFC = Arkansas Basin,
      CBRFC= Colorado Basin,
      MBRFC = South Platte (Missouri) Basin,
      NCWCD = Northern Water collection basins,
      WGRFC = Rio Grande Basin (West Gulf RFC).
      See also the map interface to SNODAS data
      hosted by the Open Water Foundation (in process of moving to a State of Colorado server) - use this to learn more about
      locations of the basins.
      </p>
  </div>
```

## Resources

* [fullPage.js](https://alvarotrigo.com/fullPage/)
* [bootstrap](https://getbootstrap.com/)
