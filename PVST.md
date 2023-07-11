### Per VLAN Spanning-Tree
- The oldest version of spanning-tree is called **CST (Common Spanning-Tree)** and is defined in the 802.1D standard. It only calculates a **single spanning-tree for all VLANs.**
- It will calculate spanning-tree for each VLAN.
- We can make a switch the root by:
	-   `priority`: We can manually change the bridge priority. (Lowest is preferred).
	-   `root`: We can configure the switch as root. (Primary | Secondary).
