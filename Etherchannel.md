- EtherChannel is a technology that lets you bundle multiple physical links into a single logical link.
- Spanning-Tree will not remove any link because they are considered as one virtual link.
- You can assign up to 16 physical interfaces to an EtherChannel but o**nly 8 interfaces** will be active at a time.
- If you want to configure an EtherChannel then we have three options:
	-   **PAgP (Cisco proprietary)**
	-   **LACP (IEEE standard)**
	-   **Manual**
- If you are going to create an EtherChannel you need to make sure that all interfaces have the same configuration:
	-   Duplex.
	-   Speed.
	-   Native and allowed VLANs.
	-   Switchport mode (access or trunk).
---
### Port Aggregation Protocol PAgP
-   **Desirable:** The interface will actively ask the other side to become an EtherChannel.
-   **Auto:** The interface will wait passively for the other side to ask to become an EtherChannel.
- If you want to make any changes like configuring the EtherChannel as a trunk, you need to do this under the port-channel interface and the switch automatically adds the commands to the physical interfaces as well.
---
### Link Aggregation Control Protocol LACP
-   **Active**: The interface will actively ask the other side to become an EtherChannel.
-   **Passive:** The interface waits passively for the other side to ask to become an EtherChannel.
- --
### Manual
- Instead of PAgP or LACP, we can also manually enable the Etherchannel.
```
SW1(config)#interface range GigabitEthernet 0/1 - 2
SW1(config-if-range)#channel-group 1 mode on
```
---
### Load Balancing
- There are plenty of options to choose from, including combinations of source and/or destination MAC or IP addresses.