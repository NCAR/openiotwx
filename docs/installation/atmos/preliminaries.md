# Atmos Node

!!! note "Phasellus posuere in sem ut cursus"

    Lorem ipsum dolor sit amet, consectetur adipiscing elit. Nulla et euismod
    nulla. Curabitur feugiat, tortor non consequat finibus, justo purus auctor
    massa, nec semper lorem quam in massa.

The Atmos node is comprised of two sensors and two 3d-printed housing
units. The first sensor houses the atmospheric conditions for air
temperature, humidity and barometric pressure. It can be fitted with the
[Seeedstudio BME280 Grove](https://www.seeedstudio.com/Grove-BME280-Environmental-Sensor-Temperature-Humidity-Barometer.html)
environmental sensor, or if you would like to obtain aggregate VOC
measurements, you can fit the housing with the
[BME680 Grove](https://www.seeedstudio.com/Grove-Temperature-Humidity-Pressure-and-Gas-Sensor-for-Arduino-BME680.html)
sensor. The code is designed to work with both sensors (but not
simultaneously). These parts can be found in the
[parts list](https://drive.google.com/file/d/1lAb784yfsxWOiH-yVCXQ3Ii0yEgUmtUQ/view?usp=sharing).

### Radiation Shield

<img width="360" alt="atmos node"
src="https://github.com/NCAR/iotwx-manual/blob/main/img/atmos-node.jpg"/>

The radiation shield sensor captures the following measurements:
temperature, humidity, barometric pressure, and optionally VOC (if using
the BME680 sensor).

**PRINTING**

* the radiation shield design 3d print files can be found in the
  [`/build/stl/atmos`](https://github.com/NCAR/iotwx-manual/tree/master/build/stl/atmos) page. If you need to
  print, you will need to follow the instructions there to print the
  housing.

**FLASHING**

* the code to flash the node can be found in the
  [esp32-atomlite-arduino-atmos-node repository](https://github.com/NCAR/esp32-atomlite-arduino-atmos-node).
  You will to follow the instructions there to understand the Arduino
  flashing requirements and procedures.

### UV

Because the UV measurement is part of the Atmos node, the code already
includes the capability to capture and transmit measurements. It is
integrated in to the
[esp32-atomlite-arduino-atmos-node repository](https://github.com/NCAR/esp32-atomlite-arduino-atmos-node)
and hence no other changes or files are necessary to flash once that
file has been uploaded to the microcontroller.
