- We use subnetting inorder not to use the classeful networks A, B, C.
- If we need to craete more subnets we can borrow bits from the host bits.
`Example :`
If we have a class C and we need to have 4 subnets, so we will borrow two bits from the host side.
subnet mask `11111111.11111111.11111111.11000000`

subnet number | network address| first usable ip| last usable ip | broadcast address
---|---|---|---|---
1 | 192.168.1.0|192.168.1.1|192.168.1.62|192.168.1.63
2|192.168.1.64|192.168.1.65|192.168.1.126|192.168.1.127
3|192.168.1.128|192.168.1.129|192.168.1.190|192.168.1.191
4|192.168.1.192|192.168.1.193|192.168.1.254|192.168.1.255
	


