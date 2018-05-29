# owf-lib-viz-fullpagejs-story

Open Water Foundation library to visualize a story using [fullpage.js](https://alvarotrigo.com/fullPage/) JavaScript library.

## Repository Contents:
```
├── owf-viz-fullpagejs-story....Repository folder.
│   ├── build-util/.............Folder contains scripts to view website locally and deploy to web.
│   ├── site-basic-example/.....A basic FullPage example - can stand alone as website.
│   |   ├── css/................CSS files for website.
│   |   ├── images/.............Images used in the webiste.
│   |   ├── js/.................Javascript files for the website.
│   |   ├── index.html..........Landing page for visualization.
```

## Design
The main functionality of this page is built using features provided by the [fullpage.js](https://alvarotrigo.com/fullPage/) Javascript Library.
Some of the layout is managed using the grid system provided by the [bootstrap](https://getbootstrap.com/) Javascript Library.  

Examples are limited to only using the basic scrollable features of this library.
There are several [extensions](https://alvarotrigo.com/fullPage/extensions/) available that provide features such as
[horizontal scrolling](https://alvarotrigo.com/fullPage/extensions/scroll-horizontally.html) and
[parallax effect](https://alvarotrigo.com/fullPage/extensions/parallax.html).
However, the extensions for the fullpage.js library require purchase.
The basic scrollable page is often sufficient to implement a story and the extensions can be added
later if additional functionality is needed.

## Navbar

If desired a nav-bar can easily be configured using [bootstrap.js](https://getbootstrap.com/docs/4.0/components/navbar/#nav).    
To make use of the visual scrolling features provided by fullpage.js, the links specified in the
nav-bar must correspond to the anchor names configured by the `anchors` variable for the full page object.
This can be found in the script tags at the bottom of `index.html`.

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

The setup for fullpage.js is easy to implement in `index.html`. Begin with a containing div `id='fullpage'`,
and then each different section for the webpage is contained in separate divs all with `class='section'`,
for example:  

```html
<div id="fullpage">
  <div class="section"></div>
  <div class="section"></div>
  <div class="section"></div>
</div>
```

#### JavaScript

Once the html has been added to the page, the fullpage object can be configured to implement scrolling features.
The simplest way to implement fullpage is to allow all defaults with no configurations:

```javascript
$(document).ready(function(){
  #('#fullpage').fullpage();
})
```
There are many different ways to configure the page. An example can be seen in the
[site-folder](https://github.com/OpenWaterFoundation/owf-lib-viz-fullpagejs-story/tree/master/site-basic-example#fullpagejs-configuration).  
See more configuration options at [fullpage options](https://github.com/alvarotrigo/fullPage.js#options)

## Bootstrap

For convenience and simplicity, the example sites implement the use of the
[bootsrap](https://getbootstrap.com/) JavaScript library to organize the contents in each section.  
In general, these examples utilize the [grid system](https://getbootstrap.com/docs/4.0/layout/grid/)
that bootstrap provides to help automatically size width of divs.
Other bootstrap classes are used for [centering text](https://getbootstrap.com/docs/4.0/utilities/text/).  
To see an example of how bootstrap can be used to configure different sections on a
page see [site-basic-example](https://github.com/OpenWaterFoundation/owf-lib-viz-fullpagejs-story/tree/master/site-basic-example#bootstrap-example).

## Resources

* [fullPage.js](https://alvarotrigo.com/fullPage/)
* [bootstrap](https://getbootstrap.com/)
