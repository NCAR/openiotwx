# Assembling the Main Unit

Once you have made sure that the sensors are all functional and uploading data, assemble the station.


Print all components that are necessary. The microcontroller and primary wiring center are housed in the spherical housing.

Atmospheric sensors are housed in the radiation shield, UV in the 'UV tube' and 'UV cap', the rain gauge is removed from its original mount and transferred onto a threaded base, and the air quality sensor is housed in the 'AQ' system.

The Hydreon RG15 rain sensor is separated from its original base by removing the four attached Phillips head screws. From there connect a GPIO to Grove wire-set to the pins on the RG15 circuit. Red-5v Black-Ground Yellow-in White-out. 

As the RG15 relies on UART for communication, this connection will monopolize the microcontrollers port.

Because of this, the user must also attach a GPIO to qwiic connect setup on pins 21 and 25 of the microcontroller.That qwiic is then attached to a four way qwiic splitter. 

One is connected to the UV, another is attached to the Air Quality sensor (PMSA003I), another is attached to the BME680 atmospheric sensor. If the user wishes to attach more qwiic I2C sensors, they can either be daisy chained to these listed sensors or connected to another splitter. We have yet to reach an upper bound on these qwiic I2C connections.

First, wire up the entire system, connect it to a power source and wireless signal, and run diagnostics to make sure data is being received by other clients. Once that is complete, place each sensor in its respective housing and attach all components.

From there, all the user must do is mount in their preferred location. For the measurements to be usable on a scale outside of a personal use case (usable in climate models), this must be 1.5-2 meters off the ground, in a representative area compared to the surrounding environment, and isolated from buildings. 

![wiring](.././img/electronic_layout.png)
