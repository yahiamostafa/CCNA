### Router on a Stick
- We use a router on a stick for inter-vlan routing.
- the link between the router and switch will be a trunk.
- It’s possible to create **sub-interfaces** on a router.
- These are virtual interfaces and on each sub-interface we can configure an IP address.

`Senario`
- We will create sub interfaces on the router.
- We will assign to each router a vlan to be tagged on this sub-interface.
- The router will check the routing table and it will send the packet through the sub-interface.

`Drawbaks`
- You are using one interface and the traffic flow up and down which may cause a congestion.
- Single Point of failure.

`Advantages`
- Cheap compared to Layer-3 Switch.

- ----------
### SVI (Switch Virtual Interface)
- This switch has routing capabilities.
- I can configure something called a **SVI (Switch Virtual Interface)** for each VLAN and put an IP address on it.
- This IP address can be used for computers as their default gateway.
- To create a **SVI** there are some requirements to have:
	- The VLAN has to **exist** in the VLAN database and it should be **active**.
	- At least one access or trunk port should use this VLAN actively and it should be in spanning-tree forwarding mode.
- the VLAN has to be active somehow or your SVI will go down.
---
### Routed Ports on a Multilayer Switch
- A router port is not associated with a particular VLAN, as is an access port or SVI.