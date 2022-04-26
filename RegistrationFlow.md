Registration Flow
===


## Package Registration

When launching the Creator Central application spawns one instance of each package. The package will called as the follows:

- for JavaScript packages, its connectCreatorCentral() is called with specific parameters.
- for compiled packages written for example in C++ or Objective-C, its main() function is called with specific parameters.

These parameters contain the port and unique identifier to use for communication with the Creator Central application.

| Parameters | Description | 
| -------- | -------- |
| port     | The port used to create the WebSocket. | 
| uuid | The unique identifier string to register the package once the WebSocket is opened. |
| event | The event type that should be used to register the package once the WebSocket is opened. |
| info | A json object containing Creator Central information |

## Property View Registration

These parameters contain the port and unique identifier to use for communication with the Creator Central application.

| Parameters | Description | 
| -------- | -------- |
| port     | The port used to create the WebSocket. | 
| uuid | The unique identifier string to register the property view once the WebSocket is opened. |
| event | The event type that should be used to register the property view once the WebSocket is opened. |
| info | A json object containing Creator Central information |
| widgetInfo | A json object containing information about the widget. |

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

