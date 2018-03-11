# ESP32-8266-Sensor-Monitor
An ESP32/8266 is used to receive sensor data from clients and then log and display the results

A sensor monitor that receives and displays on a webpage client data, usually from an ESP configured as a sensor. The design does nto use units for any data, you decide on that. For example if the sensor uploads 70 (in deg-F) it will display 70, you then need to set the channel units to deg-F. The software preloads some fileds with °C which may be displayed on your browser as A°C to resolve this go back to the channel setup and delete the leading (escape character) A then the display will be correct. so a fil;ed contens for units that was showing 'A°C' becomes '°C'.

Download the files to your IDE location.Locate the files referenced in the Server and Clients, download those and place in your Libraries folderChoose an IP address for your Server e.g. 192.168.0.99

Edit the Server IP address accordingly.

Test the Server by complining and uploading to either an ESP8266 or ESP32, the code adapts accordingly with conditional compile statments. The address of the libraries is included.

Make sure you choose the correct board type!

Test the server by typing this in a browser address bar: http://sensorserver.local/sensor?Sensor=1&temperature=21.2&humidity=50.1&pressure=1001&spare=0&sensortype="Mine"

Or if your PC does not have 'Bonjour' installed, this is needed to resolve mult-cast DNS packets and resolves the address sesnorserver.local to the IP address, in which case enter in the browser address bar:http://192.168.0.99/sensor?Sensor=1&temperature=21.2&humidity=50.1&pressure=1001&spare=0&sensortype="Mine"

Setup:

1. Determine your Routers address typically http://192.168.0.1 or https://192.168.5.1

2. Choose an IP addrress on your network, I used IPAddress local_IP(192, 168, 0, 99); // Set your server's fixed IP address

3. Set the Gateway address to match your Routers. IPAddress gateway(192, 168, 0, 1);  // Set your network Gateway usually your Router base address

4. Set a sub-net mask IPAddress subnet(255, 255, 255, 0); 

5. Now set DOmain Name Server Address, again the address of your Router. IPAddress dns(192,168,0,1); // Set your network DNS usually your Router base address

6. Change these entries to match your ssid and password:

const char ssid_1[]     = "your_SSID1";

const char password_1[] = "your_PASSWORD_for SSID1";

For Client programming ensure they use the same fixed IP address, in this example 192.168.0.99.

For the Clients, wire your sensors accordingly and change the sensor pins in the Source code to match your pins.

Compile and uploadAdjust the names and types and units as desired.

To see the sensors use http://sensorserver.local/sensor or http://192.168.0.99/sensor

To test the server use http://sensorserver.local/ or http://192.168.0.99/

Upload the example icons to your SD Card using the ESP upload function.
