On this Router used only 1 Protocol for Routing (EIGRP)


Tunnel (not encypted)

Tunnel 1 -> this is the tunnel associated with ENTA 

```
interface Tunnel1
 ip address 192.168.1.2 255.255.255.252
 tunnel source Serial0/1/1
 tunnel destination 1.1.0.1
 no shutdown
```

Routing 

```
ip route 172.17.11.0 255.255.255.0 172.16.1.2 
ip route 172.18.11.0 255.255.255.0 172.16.1.2 


router eigrp 100
no auto-summary
passive-interface FastEthernet0/0
passive-interface Serial0/1/1
network 192.168.1.0 0.0.0.3
network 172.16.0.0 0.0.0.255
network 172.17.0.0 0.0.0.255
network 172.18.0.0 0.0.0.255
 ```
 
 
 Tunnel Encryption
 
```
crypto map OMAPA 10 ipsec-isakmp
    set peer 1.1.0.1
    match address 101
access-list 101 permit gre host 1.1.0.1 host 1.1.0.2
```
```
int s0/0/0
crypto map OMAPA
```
```
crypto isakmp key Passw0rd address 1.1.0.1
```

```
crypto ipsec transform-set TRANS ah-sha-hmac esp-aes 256 esp-sha-hmac
```


```
crypto map OMAPA 10 ipsec-isakmp
set transform-set TRANS
```


```
crypto isakmp policy 10
encryption aes 256
authentication pre-share
group 5
lifetime 3600
```


NAT and ACLs



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


```
ip nat inside source list 1 interface s0/1/1 overload
ip nat inside source static tcp 172.17.1.2 80 1.1.0.2 80 
ip nat inside source static tcp 172.17.1.2 443 1.1.0.2 443 
```

NAT on Interfaces

```
interface Serial0/1/1
 ip address 1.1.0.2 255.255.255.252
 ip nat outside
 ip virtual-reassembly in
 no shutdown
```

```
interface FastEthernet0/0
 ip address 172.16.1.1 255.255.255.0
 ip nat inside
 ip virtual-reassembly in
 no shutdown
```
