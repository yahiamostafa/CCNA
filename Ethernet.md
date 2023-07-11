- Ethernet is not a single protocol but an entire collection of different standards. These standards come from the IEEE and all of them start with 802.3 in their name.

Bandwidth | Common Name | Informal Name 
---------|-------|---
10Mbps | Ethernet | 10BASE-T
100Mbps| Fast Ethernet | 100BASE-T
1000Mpbs | Gigabit Etherent | 1000BASE-T
10Gbps | 10 Gigabit Ethernet | 10GBASE-T	


-- -
- For Physical layer there are two cables we can use:
	- UTP.
	- Glass Fiber.
- **UTP**
	- UTP cables use copper to transmit an eletrical signal. The advantage of UTP is that it’s cheap and easy to work with. One of the disadvantages is that you can only use it up to 100 meter.
	- To use an electrical signal to transmit data, we need two things:
		-   An electrical circuit.
		-   Something to communicate a 1 or 0 to the other side.
	- One issue with electricity when sending it through a wire is that we get EMI (electromagnetic interference). Twisting the cables helps to cancel most of the EMI between the wire pairs. This is also known as crosstalk.
	- To create the electrical circuit, we use two wires inside the UTP cable to create a loop, which allows electricity to flow
	- ##### Straight Through Cable
		- 10BASE-T and 100BASE-T both use only two wire pairs in a UTP cable, one for transmission and the other for receiving.
		- We call this the straight through cable, the wires on both ends are connected one-to-one.
	- ##### Crossover Cable
		- What if we want to connect two switches to each other? If both of them transmit on pins 3 and 6, we get a collision on the wire.
	- Modern switches don’t care if you use a straight-through or crossover cable, they use something called auto-mdix to figure out what cable you used and use the correct wires automatically.
	- ##### Cable Selection
		- Something to keep in mind is that computers, printers, routers, access points and such use pin 1 and 2 to transmit their data. Switches use pin 3 and 6 to transmit data.
		- We use starigh through with diferent devices except for computer and router.
		- We use cross over with similar devices.
	- ##### 1000BASE-T (Gigabit Cabling)
		- It uses the four pairs in transimission and receiving.
- ##### Fiber Cabling
	- Instead of an electrical signal, we transmit light from one end to another through glass or plastic. One of the advantages is that there is less signal loss over long distances.
- ##### Duplex
	- Half duplex means that we can’t send and receive at the same time. When one computer is transmitting, everyone else has to wait. When nobody is transmitting, we can take a shot and transmit a frame.
	- When two computers decide the “line is free” and start transmitting, we still get a collision.  To solve this issue, we have a protocol called CSMA/CD:
		- Carrier sense means we can “listen” on the cable to hear if anything is going on, in other words, if another computer is sending data at this moment. Multi-access means everyone can access our physical medium but it has to be clear…no other computer should be sending at that moment.
****
### Datalink layer
- One of the great things about Ethernet is that although we have different standards, they all use a common Ethernet frame.


 ![[Pasted image 20220824170211.png]]
-   Preamble: this is a 7-byte pattern of ones and zeroes and is used for synchronization.
-   SFD: the “start frame delimiter” marks the end of the preamble and tells the receiver that the next fields will be the actual Ethernet frame, starting with the destination field.
-   Destination: this is the destination MAC address of the receiver.
-   Source: the source MAC address of the device that sent the frame.
-   Type: this tells us what is carried inside the Ethernet frame. An IPv4 packet, IPv6 packet or something else.
-   Data: this carries the actual data that we are trying to transmit, for example an IPv4 packet.
-   FCS: the frame check sequence helps the receiver to figure out if the frame is correct or corrupt.
- **MAC  Address**
	- Ethernet addresses are called MAC (Media Access Control) addresses. Each network device has a unique MAC address. When we send an Ethernet frame, we add our own MAC address as the source and the receiver MAC address as the destination.