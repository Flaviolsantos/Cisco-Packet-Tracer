
NAT

ACLs

```
access-list 1 permit 10.0.0.0 0.0.0.3
access-list 1 permit 172.16.0.0 0.15.255.255
acess-list 1 permit 192.168.0.0 0.0.255.255
```
```
access-list 100 permit tcp any any eq www
access-list 100 permit tcp any any eq 443
access-list 100 permit ip any 1.1.0.0 0.0.0.3

```

NAT overload

```
ip nat inside source list 1 interface s0/0/0 overload
ip nat inside source static tcp 172.17.1.2 80 1.1.0.2 80 
ip nat inside source static tcp 172.17.1.2 443 1.1.0.2 443 
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
