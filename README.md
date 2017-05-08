# MOD-1023 #
Arduino library and demo sketch for the  <a href="http://www.embeddedadventures.com/bme280_AMS-IAQ_multi_sensor_mod-1023.html">BME280 & AMS iAQ Weather Multi-sensor</a>.
<br>
In order to access both sensors, the Arduino sketch should include both the <a href="https://github.com/embeddedadventures/BME280">BME280 library</a> and this (iAQ-MOD1023) library. Refer to the demo sketch for usage.


## Using the library ##

The iAQ-MOD1023 uses I2C to communicate with the iAQ sensor. The sensor is constantly performing measurements and will have data stored in its registers, as well information on the data's status.

Retrieve the data all at once by calling 

	readRegisters();

Call the following functions to get the appropriate values for each item

	getPrediction();	//CO2 prediction value
	getResistance();	//Sensor resistance
	getTVOC();			//total volatile organic compounds in the air (ppb)

Call one of the following functions to determine if the data retrieved is valid. 
	
	getStatus();
	getStatusByte();	//If you only want a byte

- 0x00/OK = the measurement data is valid
- 0x10/RUNIN = data not valid; sensor is still calibrating
- 0x01/BUSY = sensor is still performing measurements; data may not be valid
- 0x80/ERROR = if this happens frequently, the sensor element may be defective

## Tested with the following boards ##
- Arduino Uno/compatible
- ESP32 Module
	- IO21 - SDA
	- IO22 - SCL
- ESP8266 Module (<a href="http://www.embeddedadventures.com/esp8266_wifi_module_wrl-esp7.html">ESP7</a> and <a href="http://www.embeddedadventures.com/esp8266_wifi_module_wrl-esp12e.html">ESP12</a>)
	- IO5 - SDA
	- IO4 - SCL
- SAMD21-based Arduino board

## Contact ##
Questions/comments/concerns regarding the code? Raise it up as a <a href="https://github.com/embeddedadventures/MOD-1023/issues/new">new issue</a> and we will help as soon as possible. You may also contact support@embeddedadventures.com or drances@embeddedadventures.com . Thanks!

## To Do ##

