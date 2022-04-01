VLANS

```
VTP domain enta.pt

vlan 10 
name V10

vlan 20 
name V20

vlan 30 
name V30
```

Then Switch all the int connected to Trunk mode

```
int rang f0/11-13
sw mod trunk
```

Since there is 2 Connections between SW1 and SW2 it will be done an channel group to connect them

```
int rang f0/11-12
channel-protocol lacp
channel-group 1

```


