- By default there is no limit to the number of MAC addresses a switch can learn on an interface and all MAC addresses are allowed.
- Use the **switchport port-security** command to enable port-security.
- Using port secuirty, you can specify how many mac-address should the switch learn in the interface.
- You can speicify which mac address should the router accept.
```
Switch(config)#interface fa0/1
Switch(config-if)#switchport port-security mac-address aaaa.bbbb.cccc
```