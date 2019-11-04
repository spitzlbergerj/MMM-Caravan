# MMM-CaravanPiClimate - a MagicMirror<sup>2</sup> Module

This [MagicMirror<sup>2</sup>](https://github.com/MichMich/MagicMirror/) module is used in the [CaravanPi](https://github.com/spitzlbergerj/CaravanPi) project to display data of a BME280 climate sensor. CaravanPi is a project based on a Raspberry Pi for a smart caravan.

In the CaravanPi project Magic Mirror is used as a display module. The screen is usually not mounted behind a mirror, but can also be used as a TV in the caravan. For the Caravan Pi project there are further modules for Magic Mirror:

[MMM-CaravanPiPosition - Module for displaying level information](https://github.com/spitzlbergerj/MMM-CaravanPiPosition)
[MMM-CaravanPiGasWeight - Module for indicating the filling of a gas bottle via a scale](https://github.com/spitzlbergerj/MMM-CaravanPiGasWeight)
[MMM-CaravanPiTemperature - Module for displaying temperature values e.g. in the refrigerator](https://github.com/spitzlbergerj/MMM-CaravanPiTemperature)
[MMM-CaravanPiClimate - Module for displaying climate values](https://github.com/spitzlbergerj/MMM-CaravanPiClimate)

## Screendumps

<img src="https://github.com/spitzlbergerj/MMM-CaravanPiClimate/blob/master/images/MMM-CaravanPiClimate-Screendump-Boxlines.jpg">

## Using the module

To use this module, add the following configuration block to the modules array in the `config/config.js` file:
```js
var config = {
    modules: [
        {
            module: 'MMM-CaravanPiClimate',
            config: {
                // See below for configurable options
            }
        }
    ]
}
```

## Configuration options

| Option           | Description
|----------------- |-----------
| `option1`        | *Required* DESCRIPTION HERE
| `option2`        | *Optional* DESCRIPTION HERE TOO <br><br>**Type:** `int`(milliseconds) <br>Default 60000 milliseconds (1 minute)
