Mostly talk about and link CHORDS.
Mention personal server creation, installation of client, broker

There are many ways you can approach collecting, visualizing, analyzing, and utilizing, the data
from your station/s. Because Open IoTwx relies on an MQTT protocol, it must send its data to a broker.

Each station is, in the IoT view, a client. Whatever platform you choose to interact with the data from
 your station on is also a client. To go between clients, a broker is required. In our opinion, 
 [CHORDS](https://earthcubeprojects-chords.github.io/chords-docs/whatis/), is your best option for
 doing that. CHORDS serves as the broker, essentially an intersection that your data gets sent to and
 away from, as well as, if you want, the client. CHORDS allows for data visualization, download (in many 
 formats), and more. Your data can be sent to the Open IoTwx client, and be published with the other
 open-data stations, or put onto your own server, where you have complete autonomy over the data
 that you collect. It is completely your choice.

 Follow the steps on CHORDS if you wish to use it as a service. Their documentation is quite 
 user-friendly.

 While Open IoTwx is in favor of public data, in the same way we believe in open software and 
 knowledge in general, we understand that many communities have had data systematically 
 used against them, and thus want control over it. Any Open IoTwx users (you) should feel no obligation
 to share data unless they want to.
