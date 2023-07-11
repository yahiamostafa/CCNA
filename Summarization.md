`Example`
Let’s say we want to create the most optimal summary for the following 4 networks:
-   192.168.0.0 / 24 subnet mask 255.255.255.0
-   192.168.1.0 / 24 subnet mask 255.255.255.0
-   192.168.2.0 / 24 subnet mask 255.255.255.0
-   192.168.3.0 / 24 subnet mask 255.255.255.0

`Solution`
The first and the second octet are the same, and the first 6 bits in the third octet are the same.

`192.168.0.0/22`
****

`Advantages`

-   **Saves memory**: routing tables will be smaller which reduces memory requirements.
-   **Saves bandwidth**: there are less routes to advertise so we save some bandwidth.
-   **Saves CPU cycles**: less packets to process and smaller routing tables to work on.
-   **Stability**: Prevents routing table instability due to flapping networks.


`Drawbacks`

- **Forwarding traffic for unused networks**: a router will drop traffic when it doesn’t have a matching destination in its routing table. When we use summarization, it’s possible that the summary route covers networks that are not in use. The router that has a summary route will forward them to the router that has advertised the summary route.
- **Sub-optimal routing**: routers prefer the path with the longest prefix match. When you use summaries, it’s possible that your router prefers another path where it has learned a more specific network from. The summary route also has a single metric.