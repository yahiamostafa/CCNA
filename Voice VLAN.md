- Usually, IP phones sit next to a computer on the same desk. They require the same UTP cables as computers and also use Ethernet. If we want to connect them to a switch, we have two options.
	1) Connect the two devices to two interfaces.
		-  You need to install a new cable from the switchport to the IP phone.
		-   You will lose a switchport for the IP phone.
	2) You can connect the ip phone into the switch and connect the computer to the ip phone.
		- most IP phones (including Cisco) have a three port switch inside of the IP phone:
			-   One port connects to the switch.
			-   One port connects to the computer.
			-   One (internal) port connects to the phone.
- The Voice VLAN is also known as the Auxiliary VLAN (AUX VLAN).
- The computer will be in a **data VLAN**, the IP phone will be in the **voice VLAN**.
- we have a **trunk** between our switch and IP phone. The port on the IP phone that connects to the computer is an access port. The IP phone will forward all traffic from the computer to the switch **untagged**, traffic from the IP phone itself will be **tagged**. The only two VLANs that are allowed though, are the access and voice VLAN.
- We configured the switch but how does the IP phone know which VLANs to use? Cisco IP phones use CDP (Cisco Discovery Protocol) for this. The IP Phone will learn through CDP which VLANs it should use.