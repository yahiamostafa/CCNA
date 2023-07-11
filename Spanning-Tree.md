- Spanning-tree is a protocol that runs on our switches that helps us to solve loops.
- We use redundent links for redundency (Inorder not to have a single point of failure).
- We don't hava a TTL in Ethernet Frames.
- Spanning-tree will help us to create a **loop-free topology** by blocking certain interfaces.
- our switches will send a special frame to each other called a **BPDU (Bridge Protocol Data Unit)**.
- In this BPDU there are two pieces of information that spanning-tree requires:
	- **Priority**.
	- **MAC Address**.
- The **MAC address** and the **priority** together make up the **bridge ID**.
---
### Spanning-Tree Election Process
- First of all spanning tree will **elect a root bridge**; this root-bridge will be the one that has the best “bridge ID”.
- The switch with the **lowest bridge ID** is the best one.
- By default the priority is **32768** but we can change this value if we want.
- The ports on our root bridge are always **designated** which means they are in a **forwarding** state.
- all our **“non-root” bridges**  will have to find the **shortest path to our root bridge**! The shortest path to the root bridge is called the **“root port”**.
- We will block the ports (their router has the highest bridge-id).
- On each segment there can be only one designated port or we’ll end up with a loop.