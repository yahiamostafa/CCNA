### Access List
- Access-lists work on the network (layer 3) and the transport (layer 4) layer and can be used for two different things:
	- **Filtering**.
		- is used to permit or deny traffic reaching certain parts of our network. Without filtering traffic can go anywhere.
	- **Classification**.
		- does not drop IP packets like filtering does but we use it to “select” traffic.
		- We can use ACLs to select which data should be encrypted during using a **VPN**.
	- You can apply **ACLs** in three spots:
		- **Inbound.**
		- **Outbound**.
		- **VTY** for telent and ssh.
- There are two types of **ACLs**
	- **Standard**.
	- **Extended**.
---
#### Standard Access List
- Standard access-list is implemented using source IP address only.
- These are the Access-list which are made using the source IP address only.
`Router(config)# access-list $access_list_number [permit/deny] ip`
- Keep in mind at the bottom of the access-list is a “deny any”.
- In a standard access list, the whole network or sub-network is denied.
- Standard access-list uses the range 1-99 and extended range 1300-1999.
---
#### Extended Access List
- These are the ACL that uses both source and destination IP addresses and also the port numbers to distinguish IP traffic.
- In this type of ACL, we can also mention which IP traffic should be allowed or denied.
- These use range 100-199 and 2000-2699.
`Router(config)# access-list 100 permit tcp 1.1.1.0 0.0.0.255 host 2.2.2.2 eq 80`
- We will only permit tcp packets from network `1.1.1.0/24`  forwarded to the host `2.2.2.2` on port `80` which is **HTTP**.
- Keep in mind at the bottom of the access-list is a “deny any”.
- --
#### Time-Based Access List
- Time-based access-list are type of access-list which allow network access on the basis of time period.
- It is useful when you want to place restrictions on outbound or inbound traffic on the basis of particular time of the day or particular days of a week.
- It best works with NTP (Network Time Protocol) synchronisation but can work with router clock.
- -- 
#### Refelxive Access List
- Reflexive Access-list is an access-list that allows only the replies of the packets of the sessions initiated within the network (from the outside network).
- When a session is initiated within the network and goes outside the network through the router (operating reflexive Access-list), reflexive Access-list are triggered. Therefore, it creates a temporary entry for the traffic which is initiated within the network and allows only those traffic from the outside network which is a part of the session (traffic generated within the network). This temporary entry is removed when the session ends.