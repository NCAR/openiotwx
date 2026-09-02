# Platform

openIoTwx is an open source community committed to increasing access to weather
observation hardware, software, and data. This is achieved through our portable, 
modular, and affordable platform. openIoTwx can be installed with up to 7 
sensors or "nodes." These nodes include, but are not limited to: temperature, relative 
humidity, pressure, volatile organic compounds (VOCs), digital rain sensors, sky 
cameras, wind speed and direction, soil moisture, and globe temperature (for estimating 
mean radiant temperature). The platform is 
small enough to mount anywhere using low cost commercial off-the-shelf materials and 
3D printed parts.


Any of these nodes can be attached to the body using universal one inch screw-in 
connectors. This approach allows for any 1" PVC pipe or other threaded connector to be 
used as a base for the station. This specification was chosen due to how commonly 
available it is to find components that fit. The body of the station has threaded 
connectors. Depending on the housing used, there are between three and five ports. 

Users are provided with a starter set of screw in adaptors for an initial 
set of sensors such as the RG15 digital rain sensor, 
air quality monitor, and radiation shields. We also provide screw-in connectors with a 
cap so that users can cap off connectors not in use and deploy. This prevents water and 
dust from getting into the electronics. Should a user want to attach a new sensor, they 
can modify the 3D design files (provided in the print section) for whatever their 
needs demand.

## Wind Speed and Direction

Wind measurements are collected with an RS485/Modbus anemometer (WS302). Because the
core microcontroller communicates over I2C/Qwiic, an RS485-to-UART interface is required
to bring the sensor's Modbus responses onto the station. Once connected, wind speed and
direction are validated, converted into usable units, and added to the station's
transmitted payload alongside the other sensor readings. See
[Materials](../getting-started/materials.md) for parts (pricing/links TBD) and
[Flash](../installation/core_install.md) for the library needed to read the sensor.

## Soil Moisture

A soil moisture node can be added to the station for agricultural and ecological
sensing applications. Like the other nodes, it is read by the microcontroller and
published in the same MQTT payload as the rest of the station's measurements. Parts
are listed under [Materials](../getting-started/materials.md) (pricing/links TBD).

## Globe Thermometer and Mean Radiant Temperature (MRT)

A 3D-printed globe thermometer houses a second temperature sensor and estimates the
Mean Radiant Temperature (MRT) using the globe temperature, air temperature, and wind
speed. MRT is a key input for outdoor heat-exposure studies, since it captures the
radiant heat load a person or object experiences beyond what air temperature alone
reports.

MRT is estimated as:

```
T_MRT = [ (T_g + 273.15)^4 + (1.1e8 * v_a^0.6 / (e_g * D^0.4)) * (T_g - T_a) ]^(1/4) - 273.15
```

Where:

* `T_g` — globe temperature (°C)
* `T_a` — air temperature (°C)
* `v_a` — wind speed (m/s)
* `e_g` — globe emissivity
* `D` — globe diameter (m)

The globe housing print files and assembly steps are in progress; see
[Print](../print.md) and [Assemble](../assemble/core.md) for status.

