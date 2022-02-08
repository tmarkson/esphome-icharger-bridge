# esphome-icharger-bridge

Connect Junsi iCharger to WiFi using [ESPHome](https://esphome.io/).

The iCharger series of battery chargers implements a Modbus on some models. This is TTL level, making it easy to interface with a microcontroller, such as ESP8266 and ESP32.

Use this device with [Home Assistant](https://www.home-assistant.io/) for bonus points. 

### Reasons
- track capacity and cycles remotely.
- log data over time, such as cell resistance.
- see errors when they happen, not the next day.
- good introduction to Esphome since the hardware is simple.

### Usage
1. Configure iCharger to output Modbus instead of USB communication. See [manual](https://github.com/tmarkson/esphome-icharger-bridge/blob/main/media/iCharger_MODBUS_Protocol.pdf).

1. Connect ESP device to iCharger using the wiring below.
1. Install esphome on your PC, or use it within another framework such as Home Assistant.
1. Upload the firmware using your configuration. `esphome run ./esphome-icharger-bridge.yaml`
1. Connect to the device. `esphome logs ./esphome-icharger-bridge.yaml`
1. Optional: Connect to the device via browser by going to ![http://esphome-icharger-bridge/](http://esphome-icharger-bridge/)
1. Optional: Add integration to Home Assistant via ESPHome using 

### Wiring
The ESP device can connect with any 2 GPIO pins.

The below connections use hardware UART ports to allow faster baud rates and less CPU wait time.

| iCharger      | ESP device    | Power supply  |
| ------------- |---------------|---------------|
| GND           | GND           | GND           |
| J1 SIGNAL     | GPIO3 (RX)    | -             |
| J2 SIGNAL     | GPIO1 (TX)    | -             |
| 5V            | -             | 5V INPUT      |
| -             | VCC           | 3.3V OUTPUT   |


<img src="https://github.com/tmarkson/esphome-icharger-bridge/blob/main/media/wiring.png" alt="connections image" width="400"/><br />
Credit: Junsi Modbus protocol manual

<img src="https://s3.amazonaws.com/assets.flitetest.com/article_images/full/icharger10-jpg_1364406006.jpg" alt="image. J1 and J2 port for Modbus" width="400"/><br />
Credit: [FliteTest](https://s3.amazonaws.com/assets.flitetest.com/article_images/full/icharger10-jpg_1364406006.jpg)


### Suggestions
- implement the `web_server` component to view the data without an external framework.
- use with Home Assistant for logging over time.
- submit pull requests with improvements. Such as test sensors to decode the status and error codes.
- submit issues with questions.

### Tested Devices
- Junsi iCharger 4010 Duo. [Product link](http://www.jun-si.com/EnProductShow.asp?ID=102).
