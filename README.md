# **BMP180 Sensor to Node-RED Dashboard via MQTT**

This project enables you to collect temperature and pressure data from a BMP180 sensor using an ESP8266 (D1 Mini) microcontroller, transmit it via MQTT, and visualize it on a Node-RED dashboard. Configuration is made simple via a Wi-Fi Manager portal, eliminating the need to access the code directly.

**Hardware Requirements**
- ESP8266 D1 Mini or equivalent microcontroller
- BMP180 pressure and temperature sensor
- 0.96" OLED Display (I2C)
- Micro USB cable for flashing and power

**Software Requirements**
- Node-RED (installed on local machine or server)
-	Required Node-RED nodes:
>	@flowfuse/node-red-dashboard
>	node-red-dashboard
-	MQTT broker (can be local or public like HiveMQ)

**Setup Instructions**

**Step 1: Install Node-RED**

Follow the official guide to install Node-RED on your machine: https://nodered.org/docs/getting-started/

**Step 2: Install Required Node-RED Nodes**

In the Node-RED editor:
1.	Click on the top-right menu → Manage palette
2.	Under the Install tab, search for and install:
>	@flowfuse/node-red-dashboard
>	node-red-dashboard

**Step 3: Import Node-RED Flow**

Import the flows.json file containing the pre-built Node-RED flow from the following link: 
*https://github.com/Chumba4209/Node-red/blob/main/flows.json*
Open the link and copy the json file.

**To import it:**
1.	In the Node-RED editor, click the menu → Import
2.	Paste the contents of the file or upload the file
3.	Click Import and Deploy
   
**Step 4: Set Up MQTT in Node-RED**
In the imported flow, double-click the MQTT node to configure the broker.
If using a public broker:
-	Broker: broker.hivemq.com
-	Port: 1883
If using a local broker (e.g., Mosquitto on your VM):
-	Enter the IP address of the machine hosting your broker
-	Ensure both your ESP8266 and the machine running the broker are on the same network

**Step 5: Flash Binary Firmware**
Flash your microcontroller on the Solution Builder with the binary/code.

**Step 6: Wi-Fi and MQTT Configuration via Config Portal**
When the ESP8266 boots up for the first time, it will:
1.	Display on the OLED:

![image](https://github.com/user-attachments/assets/59f382f3-7a57-42ea-b4de-82e1c4392545)

NOTE: Incase the display is not working or you do not have a display, check your WiFi port and see if the BMP180ConfigAP is visible and click it.

![image](https://github.com/user-attachments/assets/c08e7291-1119-4002-a537-a5981bf3b3d3)


7.	An Access Point named BMP180ConfigAP is created
8.	Connect to this Wi-Fi from your phone/laptop

![image](https://github.com/user-attachments/assets/df61bae1-eac3-42a4-bd35-697c9698a150)

   
10.	A captive portal will open automatically (or go to 192.168.4.1)
    
11.	Enter your:
>	Wi-Fi SSID and Password
>	MQTT Server (e.g., broker.hivemq.com or your local IP)

![image](https://github.com/user-attachments/assets/0c394739-977e-418c-a64d-e7cab8df8f82)


12.	Click Save
    
**Step 7: Device Behavior after Reset**

-	If configured correctly:
1.	The OLED will show *Booting...*
2.	Then *MQTT Connected*
-	Then live sensor readings:

![image](https://github.com/user-attachments/assets/990dad40-5c29-48cf-89e8-2f7e780a53fa)

-	If MQTT fails to connect:
  >	OLED will show MQTT Failed. Retrying...

NOTE: If you do not have a display or if your display is not working, open your node red and check the debug page to see if data is being sent by your microcontroller

![image](https://github.com/user-attachments/assets/384959f8-fb94-445a-b337-7965fc5df101)


**Step 8: View Data on Node-RED Dashboard**
To access your dashboard:
1.	Open your browser
2.	Visit your Node-RED URL and add ‘ui’’at the end (e.g., http://127.0.0.1:1880/ui)
3.	Your temperature and pressure readings should now appear in real-time


