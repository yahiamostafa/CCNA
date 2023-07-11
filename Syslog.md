- By default, these syslog messages are only outputted to the console. This is because the **logging console** command is enabled by default. If you log in through telnet or SSH, you won’t see any syslog messages. You can enable this with the **terminal monitor** command.
- You can see the syslog history by using **show logging** command.
- it will store up to 8192 bytes of syslog messages in its RAM. When you reboot your router or switch, the history will be gone. It is possible to increase the size of the logging buffer.
- ```R1(config)#logging buffered 16384``` This reserves up to 16384 bytes of RAM for syslog messages.
---
### Syslog server
- A local history is nice but it is stored in RAM. If you reboot the router or switch, it will be gone. What if the router crashed and you want to see if it logged anything before it went down? If you have dozens of routers and switches, logging into each device one-by-one to look for syslog messages is also not the best way to spend your time.
- In production networks, we use a central server called a syslog server. Syslog is a protocol, a standard and you can configure your routers and switches to forward syslog messages to the syslog server like this:  ```R1(config)#logging 192.168.1.2```
---
### Syslog Message Format
```
R1#
*Feb 14 09:40:10.326: %LINEPROTO-5-UPDOWN: Line protocol on Interface GigabitEthernet0/1, changed state to up
```
- Above we can see that the line protocol of interface GigabitEthernet0/1 went up but there’s a bit more info than just that. Let me break down how Cisco IOS formats these log messages:
	-   **timestamp**: Feb 14 0:40:10.326
	-   **facility**: %LINEPROTO
	-   **severity level**: 5
	-   **mnemonic**: UPDOWN
	-   **description**: Line protocol on Interface GigabitEthernet0/1, changed state to up
- The syslog is basically the process that generated the syslog message. If you look at some of the syslog messages above, you can see %LINEPROTO which keeps track of line protocols, %SYS for general system messages and %LINK for interfaces that went up or down.
---
### Syslog Severity Leve
- Let’s take a closer look at the severity levels. There are different severity levels for logging information. An interface that goes down is probably more important to know than a message that tells us we exited the global configuration. In total there are 8 severity levels:
	0. Emergency  
	1. Alert  
	2. Critical  
	3. Error  
	4. Warning  
	5. Notice  
	6. Informational  
	7. Debug
-  the lower the number, the more important the syslog message is. Alert and emergency are used when something bad is going on, like when your router runs out of memory and a process crashes. The critical, error and warning messages are used for important events like interfaces that go down. Here’s an example: