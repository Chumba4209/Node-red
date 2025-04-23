**BMP180 Sensor to Node-RED Dashboard via MQTT**

This project enables you to collect temperature and pressure data from a BMP180 sensor using an ESP8266 (D1 Mini) microcontroller, transmit it via MQTT, and visualize it on a Node-RED dashboard. Configuration is made simple via a Wi-Fi Manager portal, eliminating the need to access the code directly.

**Hardware Requirements**
•	ESP8266 D1 Mini or equivalent microcontroller
•	BMP180 pressure and temperature sensor
•	0.96" OLED Display (I2C)
•	Micro USB cable for flashing and power

**Software Requirements**
•	Node-RED (installed on local machine or server)
•	Required Node-RED nodes:
o	@flowfuse/node-red-dashboard
o	node-red-dashboard
•	MQTT broker (can be local or public like HiveMQ)

**Setup Instructions**

**Step 1: Install Node-RED**
Follow the official guide to install Node-RED on your machine: https://nodered.org/docs/getting-started/

**Step 2: Install Required Node-RED Nodes**
In the Node-RED editor:
1.	Click on the top-right menu → Manage palette
2.	Under the Install tab, search for and install:
o	@flowfuse/node-red-dashboard
o	node-red-dashboard

**Step 3: Import Node-RED Flow**
Import the following .json file containing the pre-built Node-RED flow. 


**To import it:**
1.	In the Node-RED editor, click the menu → Import
2.	Paste the contents of the file or upload the file
3.	Click Import and Deploy
   
**Step 4: Set Up MQTT in Node-RED**
In the imported flow, double-click the MQTT node to configure the broker.
If using a public broker:
•	Broker: broker.hivemq.com
•	Port: 1883
If using a local broker (e.g., Mosquitto on your VM):
•	Enter the IP address of the machine hosting your broker
•	Ensure both your ESP8266 and the machine running the broker are on the same network

**Step 5: Flash Binary Firmware**
Flash your microcontroller on the Solution Builder with the binary/code.

**Step 6: Wi-Fi and MQTT Configuration via Config Portal**
When the ESP8266 boots up for the first time, it will:
1.	Display on the OLED:
2.	Booting...
3.	1. Open BMP180Config on WiFi
4.	2. Edit WiFi and MQTT credentials
5.	3. Save, then click reset
6.	Create an Access Point named BMP180ConfigAP
7.	Connect to this Wi-Fi from your phone/laptop
8.	A captive portal will open automatically (or go to 192.168.4.1)
9.	Enter your:
o	Wi-Fi SSID and Password
o	MQTT Server (e.g., broker.hivemq.com or your local IP)
10.	Click Save
    
**Step 7: Device Behavior after Reset**
•	If configured correctly:
o	The OLED will show Booting...
o	Then MQTT Connected
o	Then live sensor readings:
o	Temp: 25.3 ºC
o	Pressure: 1013.2 hPa
•	If MQTT fails to connect:
o	OLED will show MQTT Failed. Retrying...

**Step 8: View Data on Node-RED Dashboard**
To access your dashboard:
1.	Open your browser
2.	Visit your Node-RED URL and add ‘ui’’at the end (e.g., http://127.0.0.1:1880/ui)
3.	Your temperature and pressure readings should now appear in real-time


