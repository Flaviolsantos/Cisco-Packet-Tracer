NAT


ACLs (Access-Lists)

```
access-list 1 permit 10.0.0.0 0.255.255.255
access-list 1 permit 172.16.0.0 0.15.255.255
access-list 1 permit 192.168.0.0 0.0.255.255
```

```
access-list 2 permit 10.0.0.0 0.255.255.255
access-list 2 permit 172.16.0.0 0.15.255.255
access-list 2 permit 192.168.0.0 0.0.255.255
```

NAT Overload

```
ip nat inside source list 1 interface s0/0/0 overload
ip nat inside source list 2 interface s0/0/1 overload

```

NAT on Interfaces

```
int s0/0/0
ip nat outside
```

```
int s0/0/1
ip nat outside
```

```
int f0/0
ip nat inside
```

```
int f0/1
ip nat outside
```


