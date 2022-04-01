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

Router Alfa

```
int S0/0/0
ip add 1.1.0.2 255.255.255.252
no shutdown

```
Router BETA
```
int S0/0/0
ip add 2.1.0.2 255.255.255.252
no shutdown

```
