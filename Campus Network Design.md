#### What is a “campus” network anyway?
- A campus network is an enterprise network (hundreds or thousands of users) where we have one or more LANs in one or multiple buildings. Everything is geographically close to each other so we typically use Ethernet (and Wireless) for connectivity. Typically the company owns everything on the campus…hardware, cabling, etc.
- To support this many users we require a lot of switchports which means a lot of switches. We need a physical design to connect these switches to each other and also a good logical design to make it work.
---
### The Three Layers
- **Core Layer –** It serves as the backbone of the network and interconnects distribution switches. These devices should be high-speed and able to forward packets as quickly as possible.
- **Distribution Layer –** Distribution switches aggregate traffic from the access layer switches before it is transmitted to the core layer. Routing, filtering, and QoS features are usually managed here.
- **Access Layer –** Access switches connect end devices to the network. It could be anything from your computer, IP phone, printer, surveillance camera, etc.
---
### Collpased Core Design
- Collapsed Core Architecture is a campus network design wherein we combine the core and distribution layers. We do not use a separate set of core switches in addition to the distribution switches. The core and distribution functions are implemented by a single device.
- Core layers are responsible for forwarding large amounts of packets both reliably and quickly. The distribution layer, on the other hand, is routing and filtering, and the communication point between the access layer and the core. This design is often deployed in small and medium campus networks.
- **Advantages**
	- **Lower Costs –** the company or organization can save money by reducing the number of hardware, including the running of copper or fiber to link these devices.
	- **Simplified Network –** configuring and managing these devices are less complex, with only two layers requiring communication.
- **Disadvantages**
	- **Less scalable –** Fewer devices mean we’re also limiting scalability, especially in a rapidly growing network where we connect more and more end-users. By Cisco’s definition, a small network provides services for up to 200 devices while a medium-size network provides services for 200 to 1000 devices.
	- **Resiliency –** We said earlier that the core switch should be high-speed and able to forward packets as quickly as possible. But in a collapsed core design, the collapsed core switches are also performing other functions of the distribution switch, which results in higher utilization. This can lead to degraded services.
	- **Redundancy –** With fewer devices needed to run the network, there is a lower redundancy to cover the failures of individual components.
- 