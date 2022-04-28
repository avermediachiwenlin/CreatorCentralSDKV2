Registration Flow
===


## Package Registration

When launching the Creator Central application spawns one instance of each package. The package will called as the follows:

- for Javascript packages, its connectCreatorCentral() is called with specific parameters.
- for compiled packages written for example in C++ or Objective-C, its main() function is called with specific parameters.

These parameters contain the port and unique identifier to use for communication with the Creator Central application.

## Javascript package Registration

For a Javascript plugin, you need to declare the following Javascript function:

```
function connectCreatorCentral(inPort, inPackageUUID, inRegisterEvent, inInfo)
```

This function is called when the package is loaded and should:

- create the WebSocket with the port passed in parameter:

```
websokcet = new WebSocket("ws://localhost:" + inPort);
```

- When the WebSocket is open, the plugin needs to register with JSON data:

```
websocket.onopen = function()
{
	var json = {
		"event": inRegisterEvent,
		"uuid": inPackageUUID
	};

	websocket.send(JSON.stringify(json));
}
```

- After performing these two steps, the package should receive the events through the function:

```
Websocket.onmessage = function(evt)
```

The ```inInfo``` parameter is described in the section [Info parameter](#infoparameter).



## Compiled package Registration

If your package is a compiled package(C++, Swift, C#, ...), the command-line tool will be executed with the following parameters:

| Parameters | Description | 
| -------- | -------- |
| -port | The string "-port" |
| port     | The port used to create the WebSocket. | 
| -packageUUID | The string "-packageUUID" |
| UUID | The unique identifier string to register the package once the WebSocket is opened. |
| -registerEvent | The string "-registerEvent" |
| event | The event type that should be used to register the package once the WebSocket is opened. |
| info | A json object containing Creator Central information |

The ```info``` json is described in the section [Info parameter](#infoparameter)

## Property View Registration

These parameters contain the port and unique identifier to use for communication with the Creator Central application. Your Javascript function would be as below:

```
Function connectCreatorCentral(inPort, inPropertyViewUUID, inInfo, inActionInfo)
```

| Members | Description | 
| -------- | -------- |
| inPort     | The port used to create the WebSocket. | 
| inPropertyViewUUID | The unique identifier string to register the property view once the WebSocket is opened. |
| inRegisterEvent | The event type that should be used to register the property view once the WebSocket is opened. |
| inInfo | A json object containing Creator Central information. (See blow [Info parameter](#infoparameter) |
| inWidgetInfo | A json object containing information about the widget.(see below [inWidgetInfo parameter](#widgetinfoparameter) |

This function is called when property view is displayed and should:
- create the WebSocket with the port passed in parameter:
```
Websocket = new WebSocket("ws://localhost:" + inPort);
```

- When the WebSocket is open, the Property View needs to be registered:
```
websokcet.onopen = function()
{
	var json = {
		"event": inRegisterEvent,
		"uuid": inPropertyViewUUID
	};

	websocket.send(JSON.stringify(json));
};
```

- After performing these two steps, the Property View should receive the events through the function:
```
Websocket.onmessage = function(evt)
```

The ```inInfo``` parameter is described in the section [Info parameter](#infoparameter).

<h2 id="infoparameter">Info parameter</h2>

The ```info``` parameter used in the registration flow is a json object like:

```
{
	// Now only provide the information of the application and the OS platform.
	"application": {
		"language": "en",
		"platform": "mac",
		"platformVersion": "11.0",
		"version": "1.1.0.75"
	}
}
```

| application | Description |
| - | - |
| language | In which language used by Creator Central now. Possible values are ```en```, ```ja```, ```zh_TW```, ```de```, ```ko```  |
| platform | On which platform the Creator Central is running. Possible values are ```win```and ```mac``` .
| platformVersion | The operation system version. |
| version | The Creator Central application version. | 

<h2 id="widgetinfoparameter"> Widget info parameter</h2>

The widgetInfo parameter is a json object contains the following information:

``` json
var json = {
    "widget": "com.avermedia.example.widget1",
    "context": uniqueIdentifier,
    "payload": {
        "settings"" {<json data>}
    }
};
```

| Members | Description | 
| -------- | -------- |
| widget | The widget's category |
| context | A value to identify the widget instance. |
| payload | A json object |

The payload contains:

| Members | Description | 
| -------- | -------- |
| settings | This json contains data that you can set and are stored persistently. |
