- Portfast does two things for us:
	• Interfaces with portfast enabled that come up will go to forwarding mode immediately, the interface will skip the listening and learning state.  
	• A switch will never generate a topology change notification for an interface that has portfast enabled.
- It’s a good idea to enable portfast on interfaces that are connected to hosts because these interfaces are likely to go up and down all the time. Don’t enable portfast on an interface to another hub or switch.