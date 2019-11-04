# MMM-CaravanPiClimate - a MagicMirror<sup>2</sup> Module

This [MagicMirror<sup>2</sup>](https://github.com/MichMich/MagicMirror/) module is used in the [CaravanPi](https://github.com/spitzlbergerj/CaravanPi) project to display data of a BME280 climate sensor. CaravanPi is a project based on a Raspberry Pi for a smart caravan.

In the CaravanPi project Magic Mirror is used as a display module. The screen is usually not mounted behind a mirror, but can also be used as a TV in the caravan. For the Caravan Pi project there are further modules for Magic Mirror:

[MMM-CaravanPiPosition - Module for displaying level information](https://github.com/spitzlbergerj/MMM-CaravanPiPosition)
[MMM-CaravanPiGasWeight - Module for indicating the filling of a gas bottle via a scale](https://github.com/spitzlbergerj/MMM-CaravanPiGasWeight)
[MMM-CaravanPiTemperature - Module for displaying temperature values e.g. in the refrigerator](https://github.com/spitzlbergerj/MMM-CaravanPiTemperature)
[MMM-CaravanPiClimate - Module for displaying climate values](https://github.com/spitzlbergerj/MMM-CaravanPiClimate)

## Screendumps
modus: Boxlines
<img src="https://raw.githubusercontent.com/spitzlbergerj/MMM-CaravanPiClimate/master/img/MMM-CaravanPiClimate-Screendump-Boxlines.jpg">

## Installation
In your terminal, go to your MagicMirror's Module folder:
````
cd ~/MagicMirror/modules
````

Clone this repository:
````
git clone https://github.com/spitzlbergerj/MMM-CaravanPiClimate
````

Configure the module in your `config.js` file as followed.

## Using the module

To use this module, add it to the modules array in the `config/config.js` file:
````javascript
modules: [
{
	module: 'MMM-CaravanPiClimate',
	header: 'Klimawerte',
	position: 'top_left', // This can be any of the regions.
	config: {
        valueDir: "/home/pi/CaravanPi/values",
        updateInterval: 100000, // milliseconds
        tempUnit: " °C",
        humUnit: " %",
        pressUnit: " hPa",
        tempPrecision: 2,
        humPrecision: 2,
        pressPrecision: 2,
        showDate: true,
        sensors: [
            {
                name: "Innenraum",
                file: "BME280-96-118",
            },
            {
                name: "Außenbereich",
                file: "BME280-96-119",
            },
        ],
        localeStr: 'de-DE',
        style: "lines",
    }
}
]
````

## Configuration options

The following properties can be configured:

<table width="100%">
	<thead>
		<tr>
			<th>Option</th>
			<th width="100%">Description</th>
		</tr>
	</thead>
	<tbody>
		<tr>
			<td><code>valueDir</code></td>
			<td><b>Optional</b></code> - The IP address of your HomeMatic central control unit.
				<br/>If not set, the default is: <code>homematic-ccu2</code></td>
		</tr>
		<tr>
			<td><code>updateInterval</code></td>
			<td><b>Optional</b></code> - The update interval in milliseconds.<br/>
				If not set, the default is: <code>300000</code> (5 minutes)</td>
		</tr>
		<tr>
			<td><code>tempUnit</code></td>
			<td><b>Optional</b></code> - determines whether the set target temperature is to be displayed in brackets. Possible values: <code>true</code> or <code>false</code> Default is <code>true</code></td>
		</tr>
        <tr>
			<td><code>humUnit</code></td>
			<td><b>Optional</b></code> - determines whether the set target temperature is to be displayed in brackets. Possible values: <code>true</code> or <code>false</code> Default is <code>true</code></td>
		</tr>
        		<tr>
			<td><code>pressUnit</code></td>
			<td><b>Optional</b></code> - determines whether the set target temperature is to be displayed in brackets. Possible values: <code>true</code> or <code>false</code> Default is <code>true</code></td>
		</tr>
        		<tr>
			<td><code>tempPrecision</code></td>
			<td><b>Optional</b></code> - Decimal places for temperature values. Default is <code>2</code></td>
		</tr>
        		<tr>
			<td><code>humPrecision</code></td>
			<td><b>Optional</b></code> - Decimal places for humidity values. Default is <code>2</code></td>
		</tr>
        		<tr>
			<td><code>pressPrecision</code></td>
			<td><b>Optional</b></code> - Decimal places for press values. Default is <code>2</code></td>
		</tr>
        		<tr>
			<td><code>showDate</code></td>
			<td><b>Optional</b></code> - determines whether the set target temperature is to be displayed in brackets. Possible values: <code>true</code> or <code>false</code> Default is <code>true</code></td>
		</tr>
		<tr>
			<td><code>localeStr</code></td>
			<td><b>Optional</b></code> - String for country-specific formatting of numbers. Possible values: see <a href="https://tools.ietf.org/html/rfc5646">Tags for Identifying Languages</a> Default is <code>'de-DE'</code></td>
		</tr>
		<tr>
			<td><code>sensors</code></td>
			<td><b>Required</b> - Add all your sensors that should appear in the MagicMirror. Each sensor must include the following properties:
				<table width="100%">
					<thead>
						<tr>
							<th>Option</th>
							<th width="100%">Description</th>
						</tr>
					</thead>
					<tbody>
						<tr>
							<td><code>name</code></td>
							<td>The unique <code>ise_id</code> to identify the device. All ids can be extracted by calling the following URL of the installed XML-API addon: <code>http://ccu2IP/xmlapiURL/devicelist.cgi</code></td>
						</tr>
						<tr>
							<td><code>file</code></td>
							<td>The label for the device (i.e.: Living Room). If not present or empty, the internal device name is shown instead.</td>
						</tr>
						<tr>
							<td><code>showSetTemperature</code></td>
							<td>Whether to show or to hide the target temperature. Default is <code>false</code></td>
						</tr>
						<tr>
							<td><code>showCurrentMode</code></td>
							<td>Whether to show or to hide the current state (i.e.: Heater off). Default is <code>true</code></td>
						</tr>	
						<tr>
							<td><code>showFaultReporting</code></td>
							<td>Whether to show or to hide any faults of the device (i.e.: Low battery warning). Default is <code>true</code></td>
						</tr>	
						<tr>
							<td><code>showHumidity</code> (only available for wall thermostats)</td>
							<td>Whether to show or to hide the humidity. Default is <code>true</code></td>
						</tr>	
						<tr>
							<td><code>precisionTemp</code></td>
							<td>Decimal places for temperature values. Default is <code>2</code></td>
						</tr>	
						<tr>
							<td><code>precisionHum</code></td>
							<td>Decimal places for humidity values. Default is <code>0</code></td>
						</tr>	
						<tr>
							<td><code>warnTempHigh</code></td>
							<td>Determines whether a warning is displayed when the temperature threshold <code>tempThresholdHigh</code> is exceeded (or equal) by displaying the value in <code>warnColor</code>. Default is <code>'false'</code></td>
						</tr>	
						<tr>
							<td><code>warnTempLow</code></td>
							<td>Determines whether a warning is displayed when the temperature falls below or is equal the threshold <code>tempThresholdLow</code> by displaying the value in <code>warnColor</code>. Default is <code>'false'</code></td>
						</tr>	
						<tr>
							<td><code>warnHumHigh</code></td>
							<td>Determines whether a warning is displayed when the humidity threshold <code>humThresholdHigh</code> is exceeded (or equal) by displaying the value in <code>warnColor</code>. Default is <code>'false'</code></td>
						</tr>	
						<tr>
							<td><code>warnHumLow</code></td>
							<td>Determines whether a warning is displayed when the humidity falls below or is equal the threshold <code>humThresholdLow</code> by displaying the value in <code>warnColor</code>. Default is <code>'false'</code></td>
						</tr>	
						<tr>
							<td><code>tempThresholdLow</code></td>
							<td>Temperature lower threshold. Default is <code>5</code></td>
						</tr>	
						<tr>
							<td><code>tempThresholdHigh</code></td>
							<td>Temperature upper threshold. Default is <code>24</code></td>
						</tr>	
						<tr>
							<td><code>humThresholdLow</code></td>
							<td>Humidity lower threshold. Default is <code>35</code></td>
						</tr>	
						<tr>
							<td><code>humThresholdHigh</code></td>
							<td>Humidity upper threshold. Default is <code>60</code></td>
						</tr>	
						</tbody>
				</table>
			</td>
		</tr>
	</tbody>
</table>
