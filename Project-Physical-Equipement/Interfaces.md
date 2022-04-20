Router Enta
```
int s0/0/0
no shutdown

int s0/0/1 
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

router ALFA
```
int s0/1/1
no shutdown

int f0/0
no shutdown
```
router BETA
```
int s0/1/1
no shutdown

int f0/0
no shutdown
```


SW 1
```
int f0/11
no shutdown

int f0/12
no shutdown

int f0/15
no shutdown

```
SW 2

```
int f0/11
no shutdown

int f0/12
no shutdown

int f0/13
no shutdown

```
SW3 
```
int f0/11
no shutdown

int f0/12
no shutdown

int f0/13
no shutdown

int f0/4
no shutdown
```

SW4

```
int f0/11
no shutdown

int f0/12
no shutdown

int f0/13
no shutdown

int f0/4
no shutdown

int f0/5
no shutdown
```
