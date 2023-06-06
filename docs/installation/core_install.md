# Flashing Microcontrollers

Each station node is build atop a microcontroller, where each
microcontroller is connected to one or more sensors either directly or
by hubs -- [Grove hubs](https://www.seeedstudio.com/Grove-I2C-Hub.html) or [Qwiic hubs](https://www.seeedstudio.com/Grove-Qwiic-Hub-p-4531.html). 

IotWx is designed to be used with the [m5Stack Atom Lite](https://m5stack.com/collections/m5-core/products/atom-lite-esp32-development-kit)
ESP32-Pico based microcontroller, but it is possible to connect other microcontroller devices with small modifications to the codebase, though technically _any_ ESP32 chip with enough memory would work.

## Core IoTwx library installation

There are two nodes that the core Arduino code has been developed for.
Before compiling the microcode onto the Arduino, you will also need to
install the core IoTwx shared library which controls many of the
communications and initialization functions of each node.


!!! info  "IoTwx Core Library"

    The core library can found at the following repository. It should be
    installed in your `Arduino/libraries` directory and once installed, you
    may use it by the `#include "IoTwx.h"` directive.


    * [https://github.com/NCAR/esp32-atomlite-arduino-iotwx](https://github.com/NCAR/esp32-atomlite-arduino-iotwx)



## Preparing Your System

First, download Arduino 1.8 - this is an old release but in order to use the correct data format, SPIFFS, you must use Arduino 1.8. Download Arduino 1.8.19 following this [link](https://www.arduino.cc/en/Main/Software). If this is changed in Arduino IDE, IoTWX will adapt accordingly. 

There are a few other steps you will need to complete:

Next, download the following packages. The easiest way to do this is to follow the github links and click download as zip. 
From there, in the ‘manage libraries’ functionality of Arduino, you can add a library from a .ZIP. Do this with all packages.


* install the required ESP32 Pico / M5 Stack Atom lite boards; a comprehensive instruction set is [here](https://docs.m5stack.com/#/en/arduino/arduino_development)
* install the [arduino-esp32fs-plugin](https://github.com/me-no-dev/arduino-esp32fs-plugin) that will allow SPIFFS file uploads to ESP32 boards
* install the following libraries through the Arduino IDE:
    * MQTT library from 256dpi [https://github.com/256dpi/arduino-mqtt](https://github.com/256dpi/arduino-mqtt)
    * SeeedStudio VEML6070 library [https://github.com/Seeed-Studio/Seeed_VEML6070](https://github.com/Seeed-Studio/Seeed_VEML6070)
    * SeeedStudio BME280 library [https://github.com/Seeed-Studio/Grove_BME280](https://github.com/Seeed-Studio/Grove_BME280)
    * SeeedStudio BME680 library [https://github.com/Seeed-Studio/Seeed_BME680](https://github.com/Seeed-Studio/Seeed_BME680)
    * ArduinoJson library [https://github.com/bblanchon/ArduinoJson](https://github.com/bblanchon/ArduinoJson)
    * FastLED library [https://github.com/FastLED/FastLED](https://github.com/FastLED/FastLED)
    * NTPClient library [https://github.com/arduino-libraries/NTPClient](https://github.com/arduino-libraries/NTPClient)

## Editing and Flashing Configuration Files

Your microcontroller must contain a configuration file to operate.  The file contains information about WiFi connections, MQTT (the way your station will send data) connections and some other relevant information.


The microntroller uses an [ESP32 SPIFFS filesystem](https://docs.espressif.com/projects/esp-idf/en/latest/esp32/api-reference/storage/spiffs.html) to store the configuration. 
In the folder that you will flash onto your mictrocontroller, you will find a `/data` folder which contains a `config.json` file.


### Understanding the `config.json` file

The typical config file  looks like this:

```json
{    
    "iotwx_local_config":"1",
    "iotwx_id":"m5atom/esp32/aaffbbcc",
    "iotwx_mq_ip":"",
    "iotwx_mq_port":"1883",
    "iotwx_publish_interval":"1",
    "iotwx_reset_interval":"360",
    "iotwx_sensor":"grove/i2c",
    "iotwx_timezone":"21600",
    "iotwx_wifi_pwd":"",
    "iotwx_wifi_ssid":"",
    "iotwx_topic":"measurements/iotwx",
    "iotwx_max_frequency":"240"
}
```

Much of this information is unnecessary for the functioning of your station. It is all quite 
interesting if you are using this project academically but, if not, the only things you will need 
to edit are "iotwx_wifi_pwd", "iotwx_wifi_ssid", and "iotwx_topic" (if you want to publish somewhere
other than the main measurement hub).


The details of each key are described below.

| key | value / description |
|:--:|:---|
| `iotwx_local_config` | always set to "1" |
| `iotwx_id` |  contains a _unique_ identifier for you station as a whole -- that is to say, if you have multiple nodes on the same _physical station_, they would share the same `iotwx_id`.  This identifier is also used in the data portal. (e.g. `"iotwx-co-bb83"`) |
| `iotwx_mq_ip` |  the ip address (e.g. `"172.88.0.13"`) of the MQTT broker you will be using.  At the moment only one such broker is allowed. You may use the FQDN (`"mymqttsite.wx"`) but the IP address uses less power by reducing the time WiFi is on to do DNS lookups. |
| `iotwx_mq_port` |  the port number of the broker, which is typically `"1883"` for non-SSL and `"8883"` for SSL. |
| `iotwx_publish_interval` |  the interval you wish your station to transmit in _minutes_.  Note this is relevant primarily for the Atmos node which continuously transmits at the specified interval. Hydro and Aero nodes only transmit when there is data to transmit. |
| `iotwx_reset_interval`| the number of minutes between system resets.  The nodes are designed to reset every 6 hours or twice daily.  Reset is instantaneous and the system is restored to full functionality in 90 seconds after the Bluetooth acquisition phase. (e.g. `"1"` for 1 minute) |
| `iotwx_sensor` | the sensor string for the node and may vary based on the node.  Typically do not change this value from what is contained in the default for your node. |
| `iotwx_timezone` | the GMT offset in seconds of the station timezone. (e.g. `"21600"`)|
| `iotwx_wifi_pwd` and `iotwx_wifi_ssid` | are the corresponding wifi password and ssid of the network your node will connect to.  Note, it is not necessary (but would be unusual) for all nodes to connect to the same WiFi network. (e.g. `"your_wifi"` and `"your_password"`)|
| `iotwx_topic` | the MQTT topic your node will publish to.  It is not necessary for all nodes to publish to the same topic, but if you are using the CHORDS MQTT Orchestrator ([GitHub - NCAR/chords-mqtt-orchestrator](https://github.com/NCAR/chords-mqtt-orchestrator)), then you will need to adjust it accordingly to route your messages where they belong.  The current default is `"iotwx/net"`. |
| `iotwx_max_frequency` | is the CPU frequency (in Mhz) you wish your node to run  on.  The m5Stack Atom Lite can be run at frequencies up to 240, but has only been tested down 40 Mhz. Varying the value has power-saving benefits, where we have seen 20-50% reduction in power consumption of a node. |
