### Virtual Private Network
- VPNs (Virtual Private Network) help by establishing a secure connection over an insecure network, such as the internet.
- This is a great alternative to private WAN connections since Internet access is usually cheaper and it’s available pretty much everywhere.
---
### VPN Types:
- ####  Site-to-site VPN
	- With the site-to-site VPN, we have a network device at each site, between these two network devices we build a VPN tunnel. Each end of the VPN tunnel will encrypt the original IP packet, adds a VPN header, a new IP header and then forwards the encrypted packet to the other end of the tunnel.
	![[Pasted image 20220904171927.png]]
	- Here’s what happens in the picture above:
		-   H1 sends an IP packet with source 192.168.1.1 and destination 192.168.2.2.
		-   R1 encrypts the IP packet, adds a VPN header and creates a new IP header with its own public IP address as the source and 2.2.2.2 as the destination.
		-   R1 sends the new packet to R2.
		-   R2 receives the packet, checks if the packet really came from R1, decrypts it and forwards it to H2.
		-   H2 receives the original IP packet.
	- Another advantage of (VPN) tunnels is that it allows LANs with private IP addresses to communicate with each other.
- #### Client-to-site VPN
	- The client-to-site VPN is also called the remote user VPN.
	- The user installs a VPN client on his/her computer, laptop, smartphone or tablet. The VPN tunnel is established between the user’s device and the remote network device.
- --
### VPN Protocols
- #### IPSec
	- The IP protocol itself doesn’t have any security features at all, which is why IPSec was created. IPSec is not a protocol but it’s a **framework** and offers confidentiality, integrity, authentication and anti-replay features on **layer three** of the OSI model.
	- You can use IPSec for:
		-   Creating a site-to-site VPN tunnel.
		-   Creating a client-to-site (remote user) VPN tunnel.
		-   Between two servers to authenticate and/or encrypt traffic.
- #### SSL VPN
	- SSL (Secure Sockets Layer)  is a protocol that is normally used to encrypt traffic between a web browser and web server. When you surf the web using HTTP, everything is clear text. For secure connections, we use **HTTPS**. We can use the same technology for VPNs.
	- One of the advantages of SSL VPN is that since it uses HTTPS, you can use it pretty much everywhere. Most public wifi hotspots do permit HTTPS traffic while some might block other traffic like IPSec.
	- Another reason why SSL VPN is popular is that you **don’t always have to use a software client**.