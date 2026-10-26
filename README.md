# ESPHome-Garage-Presense-Hub
ESPHome based tracking hub for 2 cars and BLE devices (for example iTags attached to trash/recycle bins); intended for garage ceiling mount installations.<br/><br/>  
BOM: [DOIT ESP32 DEVKIT V1](https://www.espboards.dev/esp32/esp32doit-devkit-v1/), 2 x [HC-SR04 Ultrasonic modules](https://www.sparkfun.com/ultrasonic-distance-sensor-hc-sr04.html), 2 x cheap [iTag bluetooth trackers from AliExpress](https://www.aliexpress.us/item/3256808320686272.html) <br/><br/> 
The config.yaml includes a full pin schema for the HC-SR04 Ultrasonic modules, the distance in the lambdas must be updated to suit the use case and installation after measuring distance to the parked car. This config assumes ceiling mounting of the HC-SR04 Ultrasonic modules above the parked vehicle. These modules have a maximum reliable real-world accurate range of 1.85 meters after testing. <br/><br/> 
```
substitutions:
  ble_mac_1: XX:XX:XX:XX:XX:XX # Replace with real MAC address of BLE itag 
  ble_mac_2: XX:XX:XX:XX:XX:XX # Replace with real MAC address of BLE itag
  presence_timeout: 360s       # Replace with desired timeout interval; default 360s
  car_1_distance: 1.2          # This must be changed to distance in meters from car after installation and measurement, assumes ultrasonic sensor is ceiling mounted above vehicle
  car_2_distance: 1.2          # This must be changed to distance in meters from car after installation and measurement, assumes ultrasonic sensor is ceiling mounted above vehicle
  tz: America/New_York         # Replace with actual Time Zone using TZ data format
  ntp: 0.pool.ntp.org          # Optionally change the NTP server
```
Update this substitution block with install specific values.<br/><br/>
Nightly battery checks and logic to silence the iTag disconnect beeping (note: these iTags have numerous variants; some do not allow this disconnect beeping to be silenced).<br/><br/>   
Buttons are provided to manually start scans and check battery life if needed to debug. Battery levels checked on boot and then daily to maximize iTag battery life.<br/><br/>  
BLE presence timeout is 360s to match the specific iTags in use. There are MANY variants and this number likely will need to be adjusted depending on the iTag variant.<br/><br/>   
Real BLE MAC addresses are required for a fully working config. Encryption keys are optional but recommended.
