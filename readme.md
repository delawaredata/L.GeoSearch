#Why did we fork this?
So far, we've changed the code to allow users to pick a different marker icon.

Add l.control.geosearch.js, one of the provider scripts and the css file to your HTML document. You can then settup the service with:


````
new L.Control.GeoSearch({
	provider: new L.GeoSearch.Provider.OpenStreetMap(),
	searchLabel: 'search for address...',  // Default
	notFoundMessage: 'Sorry, that address could not be found.',  // Default
	messageHideDelay: 3000,  // Default
	zoomLevel: 18,  // Default
	icon: new L.Icon.Default()  // Default
}).addTo(map);
````

To change the marker icon, simply pass a new L.Icon to the icon option. See the [Leaflet documentation](http://leafletjs.com/reference.html#icon) for more info about creating custom marker icons.

````
var myIcon = L.icon({....});

new L.Control.GeoSearch({
	provider: new L.GeoSearch.Provider.OpenStreetMap(),
	icon: myIcon
}).addTo(map);
````

Here are the future plans for this fork:
  - Add ability to use circle markers
  - Be able to limit search to a bounding box, which will be useful for smaller maps.

*Original Documentation Below*

#Leaflet.GeoSearch
Adds support for address lookup (a.k.a. geocoding / geoseaching) to Leaflet.

Check out the [demo](http://smeijer.github.com/GeoSearch/)

#About the control
The control uses so called providers to take care of building the correct service url and parsing the retrieved data into an uniformal format. Thanks to this split-up, it is pretty easy to write your own providers, so you can use your own geocoding service(s).

The control comes with an default set of three providers:

  - L.GeoSearch.Provider.Esri
  - L.GeoSearch.Provider.Google
  - L.GeoSearch.Provider.OpenStreetMap

Using these are pretty simple.

#Using the control

For example, to use the Esri provider:

````
new L.Control.GeoSearch({
    provider: new L.GeoSearch.Provider.Esri()
}).addTo(map);
````

Or if you prefer using Google

````
new L.Control.GeoSearch({
    provider: new L.GeoSearch.Provider.Google()
}).addTo(map);
````

Some people are really loving open source and by that openstreetmap

````
new L.Control.GeoSearch({
    provider: new L.GeoSearch.Provider.OpenStreetMap()
}).addTo(map);
````

I really can't make it any harder. Checkout the providers to see how easy it is to write your own.
