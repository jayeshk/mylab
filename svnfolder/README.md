
This is a cordova plugin for [Skobbler](http://www.skobbler.com/) maps and navigation:

This plugin is wrapper on top of skobbler sdk and provides interface for maps and navigation.

## Installation
```
cordova plugin add cordova-skobblermap-plugin
```
## Usage

All plugin methods take 3 arguments - option, success callback, failure callback.

* In order to use GPS features, location usage key will be added in project configuration, while installing plugin 'location usage' discription can be set using key $LOCATION_USAGE_DESCRIPTION. 

### Setup maps with api key.

To set up maps first needs to obtain api key from [Skobbler developer site](http://developer.skobbler.com/getting-started/ios). This method will setup map and download required meta data. The SDK requires some meta files to be present in order to be able to render the map (in offline). Meta files may be downloaded on-demand from Skobbler servers while Map serviceing are intilizing. ( *alternate approch - in future meta files may be distributed prebundled in app)

If the application doesn't call the initialization method before using other framework API, it will give an error.


```javascript

Skobbler.setUpMaps({
		apiKey:'~~~REPLACE API KEY~~~',
		mapDetailLevel:'light',
	}, 
	function (success) {
		console.log(success)
	}, 
	function (error) {
		console.log(error)
		alert(JSON.stringify(error));
	}
);

```
*apiKey: (required) needs to obtain from skobbler site.

*mapDetailLevel: (optional) light, full 

### Show past journey.

Add drift points and users markers

```javascript

Skobbler.showJourneyHistory({
	startlat:52.451619,
	startlng:9.720195,
	endlat:53.542949,
	endlng:10.023525,
	users:[
		{'id':1,'lat':53.540349, 'lng':10.032340, 'caption':'john', 'pictureurl':'www.ex.com'}, {'id':2,'lat':53.537848, 'lng':10.030581, 'caption':'adam', 'pictureurl':'www.ex.com'}],
	driftpoints:
		[{'id':10,'lat':53.536551, 'lng':10.029918}, {'id':11,'lat':53.503106, 'lng':10.038644}]
	}, 
	function(success){}, 
	function(error){});

```

### Calculate route and show navigation between points.

Calculates route between two points and show map navigation.

```javascript

var navigationOptions = {
							route: {
                            mode: 2,
                            startCoordinate: { 'lat': 37.9667, 'lng': 23.7167 },
                            destinationCoordinate: { 'lat': 37.9677, 'lng': 23.7567 }
                         }
                        }
Skobbler.showNavigation(navigationOptions,function (success){ },function (error) { });


```
*mode: (optional) default is RouteCarEfficient, possible optionals as below - 

RouteCarShortest = 0,
RouteCarFastest = 1,
RouteCarEfficient = 2,
RoutePedestrian = 3,
RouteBicycleFastest = 4,
RouteBicycleShortest = 5,
RouteBicycleQuietest = 6,
RouteBusFastest = 7

*startCoordinate: (required)

*destinationCoordinate: (required)


### Add drift points and users (This method will be refactored as - 'showDriftAgreedOption' )

Add drift points and users markers 

```javascript

Skobbler.showUsersAndDriftPoints({
	startlat:52.451619,
	startlng:9.720195,
	endlat:53.542949,
	endlng:10.023525,
	users:[
		{'id':1,'lat':53.540349, 'lng':10.032340, 'caption':'john', 'pictureurl':'www.ex.com'}, {'id':2,'lat':53.537848, 'lng':10.030581, 'caption':'adam', 'pictureurl':'www.ex.com'}],
	driftpoints:
		[{'id':10,'lat':53.536551, 'lng':10.029918}, {'id':11,'lat':53.503106, 'lng':10.038644}]
	}, 
	function(success){}, 
	function(error){});

```


### Show user and drift points.

Show user and drift points and show agreed option.

```javascript
Skobbler.showNavigation({
	route:{
	mode:2,
	startCoordinate:{'lat':18.932839, 'lng':72.827866},
	destinationCoordinate:{'lat':18.921942, 'lng':72.834693},
	otherUserCoordinate:{'lat':18.9067661, 'lng':72.8125013, 'caption':'Markus'}
	}
}, function(s){
		//Show options
		Skobbler.showDriftAgreedOption({}, function(s){}, function(e){});
}, function(e){});

```

### Show free journey route.

Utility method to clear annotations from current maps, assumption is that map screen is present.

```javascript

Skobbler.showFreeJouneryRoute({
	startlat:52.451619,
	startlng:9.720195,
	endlat:53.542949,
	endlng:10.023525,
	users:[{'id':1,'lat':53.540349, 'lng':10.032340, 'caption':'john', 'pictureurl':'www.ex.com'}, {'id':2,'lat':53.537848, 'lng':10.030581, 'caption':'adam', 'pictureurl':'www.ex.com'}],
	driftpoints:[{'id':10,'lat':53.536551, 'lng':10.029918}, {'id':11,'lat':53.503106, 'lng':10.038644}]
	}, 
	function(s){}, 
	function(e){});

```

### Clear annotations.

Utility method to clear annotations from current maps, assumption is that map screen is present.

```javascript

Skobbler.clearAnnotations({}, 
	function(success){}, 
	function(error){});

```

### Query current status of metadata. 

Meta files required for map. See 'setUp' method. Utility method to check current meta files status, can be used to verify meta if files are loaded before using other map features.

```javascript

Skobbler.checkDataDownloadedStatus({}, 
	function(success){}, 
	function(error){});

```


## License

Android: MIT

iOS: MIT


