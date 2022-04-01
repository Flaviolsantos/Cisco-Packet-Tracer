Since the SW1 have VTP the Vlans will be associated to the other Switches

Switch the int to Trunk mod

```
int rang f0/12-13
sw mod trunk

```

Since SW3 has an interface connected to the PC (on Vlan 10)

```
int f0/4
sw mod acc
sw acc vlan 10
```
