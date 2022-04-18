Routing and Tunnel

```
interface Tunnel2
 ip address 192.168.1.6 255.255.255.252
 tunnel source Serial0/1/1
 tunnel destination 2.1.0.1
```


```
router eigrp 200
no auto-summary
passive-interface FastEthernet0/0
passive-interface Serial0/1/1
network 172.16.1.0 0.0.0.255
network 172.17.1.0 0.0.0.255
network 172.18.1.0 0.0.0.255
network 192.168.1.4 0.0.0.3
```



Tunnel Encriptado


```
crypto map MAP 10 ipsec-isakmp
    set peer 2.1.0.1
    match address 100
access-list 100 permit gre host 2.1.0.1 host 2.1.0.2



int s0/1/1
crypto map MAP


crypto isakmp key Passw0rd address 2.1.0.1


crypto ipsec transform-set TRANSF ah-sha-hmac esp-aes 256 esp-sha-hmac


crypto map MAP 10 ipsec-isakmp
set transform-set TRANSF


crypto isakmp policy 10
encryption aes 256
authentication pre-share
group 5
lifetime 3600
```


ACLS and NAT

```
access-list 1 permit 172.16.1.0 0.0.0.255
access-list 1 permit 172.17.1.0 0.0.0.255
access-list 1 permit 172.18.1.0 0.0.0.255
access-list 100 permit tcp any any eq www
access-list 100 permit tcp any any eq 443
access-list 100 permit ip any 2.1.0.0 0.0.0.3
```
```
ip nat inside source list 1 interface s0/1/1 overload
ip nat inside source static tcp 172.17.1.2 80 2.1.0.2 80 
ip nat inside source static tcp 172.17.1.2 443 2.1.0.2 443 
```

NAT on Interfaces

```
interface Serial0/1/1
 ip address 2.2.0.2 255.255.255.252
 ip nat outside
 ip virtual-reassembly in
```

```
interface FastEthernet0/0
 ip address 172.16.2.3 255.255.255.0
 ip nat inside
 ip virtual-reassembly in
```
