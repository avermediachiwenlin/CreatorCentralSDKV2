Package Configuration
===


## PackageConfig.json Example

Here is an example of PackageConfig.json file. Developers should modify the fields for your Package/Widget.

``` json 
{
    "Widgets": [
        {
            "Name": "AX Lighting Toggle",
            "Icon": "widgetIcon",
            "States": [
                {
                    "Image": "onImage"
                },
                {
                    "Image": "offImage"
                }
            ], 
            "Layouts": [
                {
                    "width": 1,
                    "height": 1
                },
                {
                    "width": 2,
                    "height": 1
                }
            ],
            "Tooltip": "This widget can toggle the lighting state of AX devices.", 
            "Category": "com.avermedia.widget.lighting.toogle",
            "PropertyViewPath": "property/lightingToggle.html"
        }
    ], 
    
    "Author": "AVerMedia", 
    "Description": "", 
    "Name": "AX Lighting", 
    "Category": "com.avermedia.package.axlighting",
    "Icon": "images/packageIcon", 
    "URL": "https://www.avermedia.com/gaming/creatorcentral", 
    "Version": "1.0.0",
    "Runtime": [
        "mac": {
            "type": "web",
            "target": "index.html",
            "MinimumVersion": "11.0"
        },
        "win": {
            "type": "web",
            "target": "index.html",
            "MinimumVersion": "11.0"
        }
    },
    "Creator Central": { 
        "MinimumVersion" : "1.1",
        "SDKVersion": 2
    }
}
```


## Members

### Main

| Members        | Type     | Description|
| - | - | - |
| Widgets        | Required | An array of widgets in this Package. One Package can have one or multiple widgets. For example, the Stream Live package can contain 3 widgets: Set Current Scene, Set Current Source, and Start to Record|
| Author         | Required | The author of the Package. This string will be displayed to the user in Creator Central Widget Store.|
| Description    | Required | Provides a general description of what the package does. This string will be displayed to the user in Creator Central Widget Store.|
| Name           | Required | The name of the package. This string will be displayed to the user in the Widget List and Creator Central Widget Store both.|
| Icon           | Required | The relative path to a PNG image. This image will be displayed to the user in the Widget List and Creator Central Widget Store both.|
| URL            | Optional | A site to provide more information about the package.|
| Version        | Required | Package's semantic version (1.0.0)|
| Runtime        | Required | The relative path to the HTML/binary file containing the package code.|
| CreatorCentral | Required | Minimal supported Creator Central App version and SDK version  of this Package|


### Widgets

| Member   | Type     | Description |
| -------- | -------- | ----------- |
| Icon     | Required | The relative path to a PNG image. This image will be displayed to the user in the Widget List. |
| Name     | Required | The name of the widget. This string will be displayed to the user in the Widget List. |
| States   | Required | Each widget can have one or more states. For example, the Mute widget may have two states, mute and unmute. Ask the action to change its state by sending a changeState event. |
| Layouts   | Optional | Specifies an array of layouts. Each widget can have one or more layouts. For example, the Clock widget can have two different layouts. One is analog and another is digital. |
| Tooltip  | Optional | The string is displayed as a tooltip when the user leaves the mouse over your widget in the Widget List. |
| Category | Required | The unique identifier must be contained only lowercase alphanumeric characters(a-z, 0-9), hyphen(-), and period(.). We strongly suggest to name your identifier in **reverse-DNS** format. For example, a **Hello World** widget made by AVerMedia(avermedia.com). We will use **com.avermedia.helloworld** as the unique identifier.  |
| PropertyViewPath | Optional | The relative path to the Property View HTML file. If missing, the widget will have an empty Property View. |


### States

| Member | Type     | Description                      |
| ------ | -------- | -------------------------------- |
| Image  | Required | The default image for the state. |


### Layouts

| Member | Type     | Description                 |     |
| ------ | -------- | --------------------------- | --- |
| Width  | Required | The width of display view.  |     |
| Height | Required | The height of display view. |     | 

### Runtime

| Member         | Type     | Description                                                            |
| -------------- | -------- | ---------------------------------------------------------------------- |
| mac / win      | Required | The name of the platform, mac or win                                   |
| Type           | Required | The type of the package executable, web or bin                         |
| Target         | Required | The relative path to the HTML/binary file containing the package code. |
| MinimumVersion | Required | The minimum version of platform.                                       |

### CreatorCentral

| Member         | Type     | Description                             |
| -------------- | -------- | --------------------------------------- |
| MinimumVersion | Required | The minimum version of Creator Central. |
| SDKVersion     | Required | The current SDK version is 2.           |

