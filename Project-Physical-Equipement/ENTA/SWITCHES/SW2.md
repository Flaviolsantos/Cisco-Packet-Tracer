Since the SW1 have VTP the Vlans will be associated to the other Switches

Switch the int to Trunk mod

```
int rang f0/11-13
sw mod trunk

```

Channel Group with SW1

```
int rang f0/11-12
channel-protocol lacp
channel-group 1
```
