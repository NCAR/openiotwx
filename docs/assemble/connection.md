# Power and Internet connection

## Power Options

To power your device, you have two primary options - a solar panel and battery or Power over Ethernet (PoE).

For a solar panel and battery, we are fans of [Voltaic](https://voltaicsystems.com/) because of their fairly high quality to price. 
That being said, there are many companies out there and if you can find a good deal, take it. The power source is only critical insofar as it exists, and the specific method shouldn't change anything.

For PoE we suggest integrating via an m5 microcontroller integration. What PoE does is both data transfer as well as internet, so it covers both realms.

## Internet Options

The methodology we have developed for remote stations is threefold.

If there is service via a cellular network i.e T-mobile, Verizon, AT&T, etc. 
purchase a sim card with a long lifespan and a relatively small amount of data (we use 200mb for a year).
Additionally purchase a USB modem.
With these two options you can run a miniaturized wireless network that integrates perfectly with the ESP32 microcontroller and data protocol.

If there isn't cell service, you can either store data locally and retrieve it - cheaper and more time-consuming - or set up a satellite network
 - significantly more expensive but easier.

### Note

 All of these options are listed within materials for you to choose what works best for you. If you choose PoE there are a few changes to the config.json - noted in the installation section.
