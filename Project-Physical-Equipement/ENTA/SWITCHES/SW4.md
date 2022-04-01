Since the SW1 have VTP the Vlans will be associated to the other Switches

Switch the int to Trunk mod

```
int rang f0/12-13
sw mod trunk

```


Since SW4 has a IP phone and a PC connected to him its needed to associate with there Vlans

```
int f0/4
sw mod acc
sw acc vlan 30
```

```
int f0/5
switchport mode access
switchport voice vlan 20
mls qos trust cos
```
