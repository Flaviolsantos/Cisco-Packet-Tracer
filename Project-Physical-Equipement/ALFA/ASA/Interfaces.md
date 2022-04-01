ASA Interfaces

```
interface GigabitEthernet1/1
nameif outside
security-level 0
ip address 172.16.1.1 255.2555.255.0
no shutdown

interface GigabitEthernet1/2
nameif inside
security-level 100
ip address 172.18.1.1 255.255.255.0
no shutdown

interface GigabitEthernet1/4
nameif dmz
security-level 50
ip address 172.17.1.1 255.255.255.0
no shutdown
```
