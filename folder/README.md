
This is a cordova plugin for [Skobbler](http://www.skobbler.com/) maps and navigation:

This plugin is wrapper on top of skobbler sdk and provides interface for maps and navigation.

## Installation
```
cordova plugin add cordova-skobblermap-plugin
```

## Usage

All plugin methods takes 3 arguments - option, success callback, failure callback.

### Setup maps with api key.

To set up maps first needs to obtain api key from Skobbler developer site [http://developer.skobbler.com/getting-started/ios] to use maps. 


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


### Calculate route and show navigation between points.

Calculates route between two points and show map navigation.

```javascript

Skobbler.showNavigation({
	route:{
		mode:2,
		startCoordinate:{'lat':37.9667, 'lng':23.7167},
		destinationCoordinate:{'lat':37.9677, 'lng':23.7567}
		}
	}, 
	function(success){}, 
	function(error){}
);

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


## License

Android: MIT

iOS: MIT
