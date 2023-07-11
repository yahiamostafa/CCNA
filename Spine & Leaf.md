### Spine & Leaf Archetiture
- **Spine and Leaf Architecture** is a two-layer, full-mesh topology composed of a leaf layer and a spine layer, with the leaf and spine switches. It was originally implemented in data centers to overcome the limitations of the three-tier architecture, where we have more east-west traffic than north-south traffic flow.  East-west traffic flows are server-to-server communication within the same data center.
- **Spine Layer –** serves as the backbone of the network similar to the core layer in our three-tier design. It is where we can find the spine switches which can be a Layer 3 switch. Each Layer 3 port is connected to the underlying Layer 2 leaf switch.
- **Leaf Layer –** connects to end devices similar to the access layer in our three-tier design. It is where the leaf switches which connect to all spine switches reside.
---
### PROS
- **Improved Redundancy –** As opposed to our traditional three-tier architecture where access layer switches connect to only two uplink distribution switches, every leaf switch connects to every spine switch. And instead of Spanning Tree Protocol (STP), we implement Transparent Interconnection of Lots of Links (TRILL) and Shortest Path Bridging (SPB), which allows traffic flows across all available links, offering improved redundancy, but like STP, still prevent loops.
- **Increased Bandwidth –** By implementing TRILL and SPB, we have the ability to use multiple active links instead of one and it increases bandwidth. With STP, only one link is active and the other links are blocked.
- **Improved Scalability –** In the event of oversubscription, we can add a spine switch and connect it to every leaf switch. If the port density is a concern, we can add a leaf switch and connect it to every spine switch.
- **Lower Costs –** Fixed-configuration switches unlike modular switches, have a fixed number of ports and are usually not expandable. Many spine-leaf networks use fixed-configuration switches.
- **Low Latency and Congestion Avoidance –** With having only a maximum of two hops between any source and destination nodes, we make a more direct traffic path, which improves performance and reduces bottleneck. The only exception is when the destination is on the same leaf switch.
- **Energy Efficient –** Fixed-configuration switches require slightly lower power consumption.
---
### CONS
- **Amount of Cables –** We need to run more copper or fiber cables since each leaf must be connected to every spine device.
- **Limited Hosts –** The number of hosts that we can support can be limited. Spine port counts can restrict the number of leaf switch connections.