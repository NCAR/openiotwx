# Power and Internet connection

## Power Options

To power your device, you have two primary options - a solar panel and battery or Power over Ethernet (PoE).

For a solar panel and battery, we are fans of [Voltaic](https://voltaicsystems.com/) because of their fairly high quality to price. 
That being said, there are many companies out there and if you can find a good deal, take it. The power source is only critical insofar as it exists, and the specific method shouldn't change anything.

For PoE we suggest integrating via an m5 microcontroller integration. What PoE does is both data transfer as well as internet, so it covers both realms.

## Internet Options

The methodology we have in use for remote stations is three pronged.

1. If there is service via a cellular network i.e T-mobile, Verizon, AT&T, etc. purchase a sim card with a long lifespan and a relatively small amount of data (we use 200mb for a year).Additionally purchase a USB modem. With these two options you can run a miniaturized wireless network that integrates perfectly with the ESP32 microcontroller and the MQTTdata protocol.
2. If there isn't cell service and funds are tight you can either store data locally and retrieve it - time-consuming
3. If there isn't cell service and there are available monies, set up a satellite network - significantly more expensive but easier.
