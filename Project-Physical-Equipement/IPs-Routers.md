IPs Defined on the Routers


Router ENTA

```
int S0/0/0
ip add 1.1.0.1 255.255.255.252
no shutdown

```
```
int S0/0/1
ip add 2.1.0.1 255.255.255.252
no shutdown

```

```
int g0/0
no shutdown

interface GigabitEthernet0/0.10
encapsulation dot1Q 10
ip address 10.0.1.1 255.255.255.0
ip nat inside
ip virtual-reassembly
no shutdown

intnterface GigabitEthernet0/0.20
encapsulation dot1Q 20
ip address 10.1.1.1 255.255.255.0
ip nat inside
ip virtual-reassembly
no shutdown

ininterface GigabitEthernet0/0.30
encapsulation dot1Q 30
ip address 10.2.1.1 255.255.255.0i
p nat inside
ip virtual-reassembly in
no shutdown

inf g0/1
no shutdown

```


Router Alfa
```
int S0/0/0
ip add 1.1.0.2 255.255.255.252
no shutdown

int f0/0
no shutdown

```
Router BETA
```
int S0/0/0
ip add 2.1.0.2 255.255.255.252
no shutdown

int f0/0
no shutdown

```
