Events Sent
===

The package and Property View can send following events to Creator Central application:

| Event | Description |
| -------- | -------- |
| setWidgetSettings | Store data persistently for the widget's instance. |
| getWidgetSettings | Request the persistent data for the widget's instance. |
| setPackageSettings | Store data persistently for the package's instance. |
| getPackageSettings | Request the persistent data for the package's instance. |
| sendLog | Request to save the debug log to logs file. |

The following events is additional to package:

| Event | Description |
| -------- | -------- |
| changeTitle | Change the title of an instance of a widget. |
| changeImage | Change the image displayed by an instance of a widget. |
| changeState | Apply the state to an instance of a widget. |
| sendToPropertyView | Send a payload to the property view |

The following events is additional to property view:

| Event | Description |
| -------- | -------- |
| sendToPackage | Send a payload to the package. |

## saveWidgetSettings

The package and property view can save data persistently for the widget's instance using the setWidgetSettings event. Note that the property view will automatically receive a **didReceiveWidgetSettings** event with the new settings. Similarly, the package will automatically receive a **didReceiveWidgetSettings** event with the new settings when the property view sends this event.

``` json
var json = {
    "event": "saveWidgetSettings",
    "context": uniqueValue,
    "payload": {<json data>}
};
```

| Members | Description |
| -------- | -------- |
| event | saveWidgetSettings. |
| context | A value to identify the instance's widget or Property View. This value is received by the Property View as a parameter of the connectCreatorCentral function. |
| payload | A JSON object which is persistently saved for the widget's instance. |

## requestWidgetSettings

The package and property view can request the persistent data stored for the widget's instance using the **requestWidgetSettings** event.

``` json
var json = {
    "event": "requestWidgetSettings",
    "context": uniqueIdentifier
};
```

| Members | Description |
| -------- | -------- |
| event | requestWidgetSettings. |
| context | A value to identify the instance's widget or Property View. This value is received by the Property View as a parameter of the connectCreatorCentral function. |

The package or property view will receive a **didReceiveWidgetSettings** containing the settings for this widget:
``` json
var json = {
    "widget": "com.avermedia.example.widget1",
    "event": "didReceiveWidgetSettings",
    "context": uniqueIdentifier,
    "payload": {
        "settings": {<json data>}
    }
};
```

| Members | Description |
| -------- | -------- |
| event | requestWidgetSettings. |
| context | A value to identify the instance's widget or Property View. This value is received by the Property View as a parameter of the connectCreatorCentral function. |


## setPackageSettings

The package and property view can use this event to save tokens that should be available to every widget in the package.

``` json
var json = {
    "event": "setPackageSettings",
    "context": uniqueIdentifier,
    "payload": {
        "settings": {<json data>}
    }
};
```

| Members | Description |
| -------- | -------- |
| event | requestWidgetSettings. |
| context | A value to identify the package or Property View. This value is received by the Property View as a parameter of the connectCreatorCentral function. |
| payload | A json object which is persistently saved and available to every widget in the package. |

## requestPackageSettings

The package and Property View can request the persistent data which available to every widget in the package using the **requestPackageSettings** event:

``` json
var json = {
    "event": "requestPackageSettings",
    "context": uniqueIdentifier
};
```

| Members | Description |
| -------- | -------- |
| event | requestPackageSettings |
| context | A value to identify the package or Property View. This value is received by the Property View as a parameter of the connectCreatorCentral function. |

The package or Property View will receive event **didReceivePackageSettings** containing the global settings:

``` json
var json = {
    "event": "didReceivePackageSettings",
    "payload": {
        settings: {<json data>}
    }
}
```

## sendLog

The package and Property View can use the **sendLog** event to write a debug message to the logs file:
``` json
var json = {
    "event": "sendLog",
    "payload": {
        "message": "Something need to be saved."
    }
};
```

| Members | Description |
| -------- | -------- |
| event | sendLog |
| payload | A json object |

The payload object contains the following members:

| Payload | Description |
| -------- | -------- |
| message | A string to write to the logs file. |

## changeTitle

The package can send a **changeTitle** event to the Creator Central application to change the title displayed on the display view of widget.

``` json 
var json = {
    "event": "changeTitle", 
    "context": uniqueIdentifier,
    "payload": {
        "title": "New Title",
        "state": zero-based integer
    }
};
```

| Members | Description |
| -------- | -------- |
| event | changeTitle |
| context | A value to identify the widget instance you want to modify |
| payload | A json object |

The payload object contains the following members:

| Payload | Description |
| -------- | -------- |
| title | The title to display. |
| state | A 0-based integer value representing the state of a widget with multiple states. |

## changeImage

The package can send a **changeImage** event to the Creator Central application to change the image displayed on the display view of widget.

``` json 
var json = {
    "event": "changeImage", 
    "context": uniqueIdentifier,
    "payload": {
        "image": <base64 encoded image>,
        "state": zero-based integer
    }
};
```

| Members | Description |
| -------- | -------- |
| event | changeImage |
| context | A value to identify the widget instance you want to modify |
| payload | A json object |

The payload object contains the following members:

| Payload | Description |
| -------- | -------- |
| image | The image to display encoded in base64 with the image format declared in the mime type. |
| state | A 0-based integer value representing the state of a widget with multiple states. |

## changeState

The package can change the state of a widget supporting multiple states:
``` json
var json = {
    "event": "changeState",
    "context": uniqueIdentifier,
    "payload": {
        "state": zero-based integer
    }
};
```

| Members | Description |
| -------- | -------- |
| event | changeState |
| context | A value to identify the widget instance you want to modify |
| payload | A json object |

The payload object contains the following members:

| Payload | Description |
| -------- | -------- |
| state | A 0-based integer value representing the state of a widget with multiple states. |

## sendToPackage

The property view can send a payload to the package using the **sendToPackage** event:
``` json
var json = {
    "widget": "com.avermedia.example.widget1",
    "event": "sendToPackage",
    "context": uniqueIdentifier,
    "payload": {<json data>}
};
```

| Members | Description |
| -------- | -------- |
| widget | The widget category |
| event | sendToPackage |
| context | A value to identify the widget instance. |
| payload | A json object |

The package will receive event **sendToPackage** containing the payload:
``` json
var json = {
    "widget": "com.avermedia.example.widget1",
    "event": "sendToPackage",
    "context": uniqueIdentifier,
    "payload": {<json data>}
};
```

## sendToPropertyView

The package can send a payload to the Property View using the **sendToPropertyView** event:
``` json
var json = {
    "widget": "com.avermedia.example.widget1",
    "event": "sendToPropertyView",
    "context": uniqueIdentifier,
    "payload": {<json data>}
};
```

| Members | Description |
| -------- | -------- |
| widget | The widget category |
| event | sendToPropertyView |
| context | A value to identify the widget instance. |
| payload | A json object |

The property view will receive event **sendToPropertyView** containing the payload:
``` json
var json = {
    "widget": "com.avermedia.example.widget1",
    "event": "sendToPropertyView",
    "context": uniqueIdentifier,
    "payload": {<json data>}
};
```