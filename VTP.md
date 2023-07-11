### VLAN Trunking Protocol
- Let’s say you have a network with 20 switches and 50 VLANs. Normally you would have to configure each switch separately and create those VLANs on each and every switch. That’s a time consuming task so there is something to help us called **VTP** (VLAN Trunking Protocol). VTP will let you create VLANs on one switch and all the other switches will synchronize themselves.
- We have one VTP server which is the switch where you create / modify or delete VLANs.
- The other switches are VTP clients.
- The VTP configuration has a revision number which will increase when you make a change.
- Every time you make a change on the VTP server this will be synchronized to the VTP clients.
- you can have multiple VTP servers since it also functions as a VTP client so you can make changes on multiple switches in your network.
- To simplify:
	1.  VTP adds / modifies / deletes VLANs.
	2.  For every change the revision number will increase.
	3.  The latest advertisement will be sent to all VTP clients.
	4.  VTP clients will synchronize themselves with the latest information.
- Besides the VTP server and VTP client there’s also a VTP transparent.
- Our VTP Transparent will forward advertisements but will **not synchronize** itself.
- Let’s say you create VLAN 20 on our VTP server, this is what will happen:
	1.  You create VLAN 20 on the VTP server.
	2.  The revision number will increase.
	3.  The VTP server will forward the latest advertisement which will reach the VTP transparent switch.
	4.  The VTP transparent will not synchronize itself but will forward the advertisement to the VTP client.
	5.  The VTP client will synchronize itself with the latest information.
- Should you use VTP? It might sound useful but VTP has a big security risk…the problem with VTP is that a VTP server is also a VTP Client and any VTP client will synchronize itself with the highest revision number.
- You have a network with a single VTP server and a couple of VTP client switches, everything is working fine but one day you want to test some stuff and decide to take one of the VTP clients out of the network and put it in a lab environment.
	1.  You take the VTP client switch out of the network.
	2.  You configure it so it’s no longer a VTP Client but a VTP server.
	3.  You play around with VTP, create some VLANs, modify some.
	4.  Every time you make a change the revision number increases.
	5.  You are done playing…you delete all VLANs.
	6.  You configure the switch from VTP Server to VTP Client.
	7.  You connect your switch to your production network.
- A VTP client can **overwrite** a VTP server if the revision number is higher because a VTP server is also a VTP client.