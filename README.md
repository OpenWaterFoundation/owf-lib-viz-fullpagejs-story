# owf-lib-viz-fullpagejs-story

Open Water Foundation library to visualize a story using [fullpage.js](https://alvarotrigo.com/fullPage/) JavaScript library.

See the visualization [deployed on OWF website](http://viz.openwaterfoundation.org/co/owf-lib-viz-fullpagejs-story/site-basic-example).

* [Repository Contents](#repository-contents)
* [Design](#design)
* [Navbar](#navbar)
* [Full Page](#full-page)
* [Bootstrap](#bootstrap)
* [Resources](#resources)
* [Leaflet](#leaflet)

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

## Leaflet

These examples utilize the [Leaflet](https://leafletjs.com/) javascript library to add maps to the story. 
The code necessary to create a single leaflet map can be quite lengthy, which can clutter up the index.html file. 

#### Separate Javascript Files
One technique to handle this issue is to move the javascript code for each map into their own separate javascript 
files, and then including them in index.html.

#### Using Closures
Another issue that can be ran into is confusion among variable names. Often when working with leaflet maps the code 
to build each separate map can look very similar and the variable names used might end up being the same, which can 
confuse the javascript namespace. Wrapping your code in a closer can combat this issue.  
Below is an example of closure syntax:
```javascript
(function(){
  //encapsulated code
})();
```

#### Example
See the following example on how to put it all together:
```html
<!-- index.html -->
<div id='mapbox1' class='map-right'></div>
<!-- javascript file must come AFTER declaring the map div id -->
<script src='js/leaflet-map.js'></script>
```
```javascript
//leaflet.map.js
(function(){
    // Leaflet MapBox of IPPs by Basin and Cost
	var map = L.map('mapbox1').setView([40.112, -104.828], 9);

	L.tileLayer('https://api.mapbox.com/styles/v1/mapbox/outdoors-v9/tiles/256/{z}/{x}/{y}?access_token=' +
				'pk.eyJ1Ijoia3Jpc3RpbnN3YWltIiwiYSI6ImNpc3Rjcnl3bDAzYWMycHBlM2phbDJuMHoifQ.vrDCYwkTZsrA_0FffnzvBw', 
	{
		maxZoom: 18,
		attribution: 'Created by the <a href="http://openwaterfoundation.org">Open Water Foundation. </a>' + 
		'Map data &copy; <a href="http://openstreetmap.org">OpenStreetMap</a> contributors, ' +
			'<a href="http://creativecommons.org/licenses/by-sa/2.0/">CC-BY-SA</a>, ' +
			'Imagery © <a href="http://mapbox.com">Mapbox</a>',
		id: 'mapbox.outdoors'
	}).addTo(map);
  
  //Additional leaflet code
  
})();
```

## Resources

* [fullPage.js](https://alvarotrigo.com/fullPage/)
* [bootstrap](https://getbootstrap.com/)
* [leaflet.js](https://leafletjs.com/)
* [JuxtaposeJS](https://juxtapose.knightlab.com/)
* [ArcGIS](https://www.arcgis.com/index.html)
