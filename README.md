# MMM-UKLiveBusStopInfo
Additional Module for MagicMirror²  https://github.com/MichMich/MagicMirror

# Module: UKLiveBusStopInfo
Magic Mirror Module for UK bus information. Returns real-time info about a SPECIFIC bus stop.

## Using the module

To use this module, add it to the modules array in the `config/config.js` file:

```javascript
modules: [
    {
		module: 'MMM-UKLiveBusStopInfo',
		position: 'bottom_left',
		config: {
			atcocode: 	'490015165B', 		// ATCO code for specific bus stop
			app_id: 	'', 				        // TransportAPI App ID
			app_key: 	'', 	              // TransportAPI App Key
			limit: 		5  					        // Optional - Maximum results to display.
      showRealTime: false,          // Optional - show realtime departure info
      showDelay: false              // Optional - show delay in minutes based on Real Time info vs Time table
		}
	},
]
```
There are 3 MANDATORY fields - `atcocode`, `app_id` and `app_key`. All the others are used to limit the amount of info you get back, especially useful for busy bus stops that serve multiple routes.

**PLEASE NOTE** The TransportAPI provides a sample key in their documentation that I previously referenced here. This is being removed very soon, so you *MUST* register to get this module to work!

The following is taken from the TransportAPI documentation [here](https://developer.transportapi.com/docs?raml=https://transportapi.com/v3/raml/transportapi.raml##request_uk_bus_stop_atcocode_live_json)

|Option|Required Settings Description|
|---|---|
|`atcocode`|String. The bus stop you require information about.<br><br>This value is **REQUIRED** <br/>**Example**: 490015165A <br />|
|`api_id`|String. Your TransportAPI app_id [Get yours here](https://developer.transportapi.com/signup).<br><br>This value is **REQUIRED**  <br/>**Example**: 03zf7118 <br />|
|`app_key`|String. Your TransportAPI app_key [Get yours here](https://developer.transportapi.com/signup).<br><br>This value is **REQUIRED** <br/>**Example**: z9307fd87b0000c107e098d5effedc97 <br />|

|Option|Optional Settings Description|
|---|---|
|`showRealTime`| Boolean. Show realtime departure info. <br><br>**Default:** false|
|`showDelay`| Boolean. Show delay in minutes based on Real Time info vs Time table. <br><br>**Default:** false|
|`limit`|Integer. Number of departures to return.<br><br>**Default:** 10|
|`nextBuses`|String. Set this to 'no' if you want to disable expensive calls to NextBuses.<br><br>**Default:** 'Yes'|

To find the ATCOCode of a bus stop look at the OpenStreetMap.org transport layer and query the bus stop you are interested in.

## Transport API

To setup an account for the App_id & app_key sign up for an account here: http://www.transportapi.com/

## Troubleshooting

If there are issue getting data out of the module I'm ALWAYS going to ask the following:

1. Do you have an account set up at Transportapi.com?
2. Do you have an app_id and app_key set up?
3. Do you know the ATCOCode for the bus stop??
4. If you use the live api documentation [here](https://developer.transportapi.com/docs?raml=https://transportapi.com/v3/raml/transportapi.raml##uk_bus_stop_atcocode_live_json) and put in the info you want to use does it respond without an error?
5. Is the info in your config the same as that you’ve used successfully in the live api docs?
