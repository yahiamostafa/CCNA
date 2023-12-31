### Rapid Spanning-Tree Protocol RSTP
- Rapid spanning-tree only has three port states:
	- Discarding {Blocking, Lisetning}.
	- Learning
	- Forwarding
- There are a backup port which is used to accelarate the convergence process after any network topology change.
- Ports can have the following options in RSTP:
	-   Unknown
	-   Alternate / Backup port.
	-   Root port.
	-   Designated port.
- This new BPDU is called a **version 2 BPDU.**
- all switches generate BPDUs **every two seconds (hello time).** This is the default hello time but you can change it.
- BPDUs are now used as a **keepalive mechanism** similar to what routing protocols like OSPF or EIGRP use. If a switch **misses** **three BPDUs** from a neighbor switch it will assume connectivity to this switch has been lost and it will remove all MAC addresses immediately.
- Rapid spanning **doesn’t use timers** to decide whether an interface can move to the forwarding state or not. It will use a **negotiation mechanism** for this.