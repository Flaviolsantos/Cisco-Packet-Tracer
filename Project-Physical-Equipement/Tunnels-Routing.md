On router ENTA i used 2 different protocols:
-EIGRP (used on Tunnels)
-OSPF (used on internet network)




ENTA

For the internel network

```
router ospf 100
passive-interface FastEthernet0/0
passive-interface FastEthernet0/1
network 10.0.1.0 0.0.0.255 area 0
network 10.1.1.0 0.0.0.255 area 0
network 10.2.1.0 0.0.0.255 area 0

```


Tunnels (without encyption)

Tunnel 1 (the tunnel between ENTA and ALFA)

```
int tun1
 ip address 192.168.1.1 255.255.255.252
 tunnel source Serial0/0/0
 tunnel destination 1.1.0.2

```

Tunnel 2 (the tunnel between ENTA and BETA)

```
int tun2
 ip address 192.168.1.5 255.255.255.252
 tunnel source Serial0/0/1
 tunnel destination 2.1.0.2

```

Routing on Tunnels

For Tunnel 1
```
router eigrp 100
no auto-summary
redistribute static 
passive-interface f0/0
passive-interface f0/1
passive-interface s0/0/0
passive-interface s0/0/1
network 192.168.1.0 0.0.0.3

```

For Tunnel 2

```
router eigrp 100
no auto-summary
redistribute static 
passive-interface f0/0
passive-interface f0/1
passive-interface s0/0/0
passive-interface s0/0/1
network 192.168.1.4 0.0.0.3

```


Tunnel Encryption

Tunnel Encriptado

ROUTER ENTA -> ALFA

```
crypto map OMAPA 10 ipsec-isakmp
    set peer 1.1.0.2
    match address 100
access-list 100 permit gre host 1.1.0.2 host 1.1.0.1
```
```
int s0/0/0
crypto map OMAPA
```


KEY -> ```crypto isakmp key Passw0rd address 1.1.0.2```



```crypto ipsec transform-set TRANS ah-sha-hmac esp-aes 256 esp-sha-hmac```

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





ROUTER ENTA -> BETA
```
crypto map MAP 10 ipsec-isakmp
    set peer 2.1.0.2
    match address 100
access-list 100 permit gre host 2.1.0.2 host 2.1.0.1
```
```
int s0/0/1
crypto map MAP
```
   
KEY  `crypto isakmp key Passw0rd address 2.1.0.2`


`crypto ipsec transform-set TRANSF ah-sha-hmac esp-aes 256 esp-sha-hmac`

```
crypto map MAP 10 ipsec-isakmp
set transform-set TRANSF
```


```
crypto isakmp policy 10
encryption aes 256
authentication pre-share
group 5
lifetime 3600
```


To Check if the Tunel is Encrypted :
```
show crypto isakmp sa
show crypto ipsec sa
```

