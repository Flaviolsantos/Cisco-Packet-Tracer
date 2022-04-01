
NAT

ACLs

```
access-list 1 permit 10.0.0.0 0.0.0.3
access-list 1 permit 172.16.0.0 0.15.255.255
acess-list 1 permit 192.168.0.0 0.0.255.255
```

NAT overload

```
ip nat inside source list 1 interface s0/0/0 overload
```

NAT on Interfaces

```
int s0/0/0
ip nat outside
```

```
int f0/0
ip nat inside
```
