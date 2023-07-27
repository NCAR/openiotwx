# Testing your Station before deployment 

Before you place all of your sensors into their various housing, it is important to test whether or not you are receiving data.

Here are the steps to do that most effectively:

1. Configure your wifi modem (if you are using a sim card setup)
2. Plug the modem into your power source and check whether or not you have a signal.
3. Unplug the modem and plug in your microcontroller, without any sensors attached. When connected to power, but not to sensors, it will blink red. 
4. Unplug the microcontroller from the power source and attach your cables. Make sure all Grove and Qwiic connectors are properly pushed into place as this can cause issues down the line.
5. Without plugging in the modem, connect your microcontroller, with sensors attached, to the power source. If it flashes blue, you're clear to proceed.
6. Unplug the microcontroller, plug in the modem, wait a few seconds for your modem to connect, and plug in your microcontroller.
7. Wait a few minutes and then check your data portal to see if you are receiving data. If so, you are good assemble the station.

![full assembly](.././img/full_station.png){style="display: block; margin: 0 auto; width: 250px;"}

