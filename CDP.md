### Cisco Discovery Protocol
- CDP is a Cisco protocol that runs on all Cisco devices that helps us discover Cisco devices on the network.
- CDP is Cisco proprietary, runs on the data-link layer and is enabled by default.
- **CDPV2:** Is the most recent release of the protocol and provides more intelligent device tracking features like instances of mismatch native VLAN IDs on 802.1Q trunks, and mismatch in duplex states between connecting devices.
---
#### How CDP works ?
-   All Cisco devices transmit CDP packets periodically (default time interval value is 60 seconds though this is adjustable). These packets advertise a time-to-live (TTL) value in seconds, which indicates the number of seconds that the packet must be retained before it can be discarded (default value is 180 seconds).
- CDP packets are sent with a time-to-live value that is nonzero after an interface is enabled and With a time-to-live value of zero immediately before an interface is down. This provides quick state discovery.
---
#### Notes for CDP
- CDP only works on directly connected interfaces.
- CDP messages are generated every 60 second, hold-down timer is 180 seconds.
- Messages are destined to L2 multicast address 01:00:0C:CC:CC:CC.
- Device that receives CDP messages on an interface from other devices the information is stored in a table that can be viewed using the **_show cdp neighbors_** command.
- CDP table information is refreshed each time an announcement is received from neighbor, and the holdtime for that entry is reinitialized.
- The holdtime specifies the lifetime of an entry in the table - if no announcements are received from a device for a period in excess of the holdtime, the device information is discarded and wiped out.