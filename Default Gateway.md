- When one host wants to send something to another host then it will check if the destination is inside or outside its own network. When the destination is in the same network then it will ARP.
- The host check if the destination is in the same network by checking the subnet mask.
`Example`
- We only have network `192.168.1.0` with subnet mask `255.255.255.0`.
- let’s say that `192.168.1.1` wants to send an IP packet to `192.168.1.2`.
- The subnet mask tells us which part of the IP address is the network and host part.
- network address for `192.168.1.1` is `192.168.1.0` which is the same for `192.168.1.2`.
- Two hosts are in the same network.
- Else we will send this to the default gateway.
---
`Example`
Host 1 with ip `192.168.1.1` in the network `192.168.1.0/24` to host 2 with ip `192.168.2.2`.

![[Pasted image 20220829171457.png]]

**At Host 1**
1) First it will check if the other host local or remote.
2) The Destination is remote.
3) H1 will now build an Ethernet frame, enters its own source MAC address and it will check if it has the MAC address of the default gateway.
4) It'll check the ARP table.

**At Router 1**
1) is check if the FCS (Frame Check Sequence) of the Ethernet frame is correct or not.
2) If the FCS is correct, we will process the frame if:
	-   The destination MAC address is the address of the interface of the router.
	-   The destination MAC address is a broadcast address of the subnet that the router interface is connected to.
	-   The destination MAC address is a multicast address that the router listens to.
3) The router will now look at the IP packet, and the first thing it does is check if the header checksum is OK.
4) we continue by looking at the destination IP address.
5) **R1** will do a recursive lookup it will enter the routing table to know how to reach the destination, it will enter it again to know how to reach the next hop.
6) It will decrement the **TTL** by one.
7) It will calculate the **Header Checksum** again.
8) Once this is done, R1 checks its ARP table to see if there is an entry for the next hop.
9) R1 builds a new Ethernet frame with its own MAC address of the GigabitEthernet 0/2 interface and R2 as the destination.
---
Let’s summarize this process.

- **The host has a simple decision to make:**
	-   Is the destination on the local subnet?
	    -   Check ARP table for destination IP address, if empty, send an ARP request.
	-   Is the destination on a remote subnet?
	    -   Check ARP table for default gateway IP address, if empty, send an ARP request.

- **The router has to perform a number of tasks:**
	-   When it receives an Ethernet frame, check if the FCS (Frame Check Sequence) is correct. If not, drop the frame.
	-   Check if the destination address of the frame is:
	    -   destined to our MAC address
	    -   destined to a broadcast address of the subnet our interface is in.
	    -   destined to a multicast address that we listen to.
	-   De-encapsulate the IP packet from the frame, discard the Ethernet frame.
	-   Look for a match in the routing table for the destination IP address, figure out what the outgoing interface and optionally, the next hop IP address is.
	-   Decrease the TTL (Time to Live) field in the IP header, recalculate the header checksum.
	-   Encapsulate the IP packet in a new Ethernet frame.
	-   Check the ARP table for the destination IP address or next hop IP address.
	-   Transmit the frame.
