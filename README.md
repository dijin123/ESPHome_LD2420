# 8266 Mini D1 and ESPHome - LD2420
The ld2420 sensor platform allows you to use the HLK-LD2420 motion and presence sensor. 

![image](https://github.com/user-attachments/assets/639262a7-4158-4e50-a289-b5b6e71808b0)

# Code for ESPHome:
```
esphome:
  name: motiondetector1
  friendly_name: MotionDetector1

esp8266:
  board: esp01_1m

logger:

api:
  encryption:
    key: "##########"

ota:
  - platform: esphome
    password: "#############"

wifi:
  ssid: !secret wifi_ssid
  password: !secret wifi_password
  
ap:
    ssid: "Motiondetector1 Fallback Hotspot"
    password: "##########"

captive_portal:

web_server:
  port: 80

uart:
  id: ld2420_radar
  tx_pin: GPIO14
  rx_pin: GPIO4
  baud_rate: 115200
  parity: NONE
  stop_bits: 1
  
 
ld2420:
  
 
text_sensor:
  - platform: ld2420
    fw_version:
      name: LD2420 Firmware
 
sensor:
  - platform: ld2420
    moving_distance:
      name : Moving Distance
 
binary_sensor:
  - platform: ld2420
    has_target:
      name: Presence
 
select:
  - platform: ld2420
    operating_mode:
      name: Operating Mode
 
number:
  - platform: ld2420
    presence_timeout:
      name: Detection Presence Timeout
    min_gate_distance:
      name: Detection Gate Minimum
    max_gate_distance:
      name: Detection Gate Maximum
    gate_select:
      name: Select Gate to Set
    still_threshold:
      name: Set Still Threshold Value
    move_threshold:
      name: Set Move Threshold Value
        
button:
  - platform: ld2420
    apply_config:
      name: Apply Config
    factory_reset:
      name: Factory Reset
    restart_module:
      name: Restart Module
    revert_config:
      name: Undo Edits
```
