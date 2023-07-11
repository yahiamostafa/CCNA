- The firewall is the barrier between a **trusted and untrusted network**, often used between your LAN and WAN.
---
### Stateful Filtering
- Firewalls, like routers can use access-lists to check for the source and/or destination address or port numbers.
- Most routers however, don’t spend much time at filtering…when they receive a packet, they check if it matches an entry in the access-list and if so, they permit or drop the packet.
- No matter if they receive a single packet or thousands, each packet is treated individually and we don’t keep track of packets we have seen before or not. This is called **stateless filtering** (Routers).
- Firewalls, on the other hand, use stateful filtering.
- They keep track of all incoming and outgoing connections. Here are some examples:
	- A web server is sitting behind a firewall, it’s a busy server that accepts an average of 20 new TCP connections per second from different IP addresses. The firewall keeps track of all connections, once it sees a source IP address that is requesting more than 10 new TCP connections per second, it will drop all traffic from this source IP address, preventing a DoS (Denial of Service).
- --
### Packet Inspection
- Most firewalls support some form of (deep) packet inspection. Simple access-lists only check source/destination addresses and ports, that’s layer 3 and 4 of the OSI model. Packet inspection means we can inspect up to layer 7 of the OSI model. This means we can look at application data and even the payload.
- Here are some examples:
	- Your firewall can check the payload to block any packets that contains known worms or viruses.
	- You can check the URL itself.
- --
### Security Zones
- Cisco routers, by default, will permit and forward all packets they receive, if they have a matching route in their routing table. If you want to restrict this, you have to configure some access-lists. This can become an administrative nightmare if you have a lot of interfaces and/or access-list rules.