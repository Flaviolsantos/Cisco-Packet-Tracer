ASA Interfaces

```
interface GigabitEthernet1/1
bridge-group 1
nameif outside
security-level 0
no shutdown

interface GigabitEthernet1/2
bridge-group 2
nameif inside
security-level 100
no shutdown

interface GigabitEthernet1/3
bridge-group 2
nameif phone
security-level 100
no shutdown

interface GigabitEthernet1/4
nameif dmz
security-level 50
ip address 172.17.1.1 255.255.255.0
no shutdown

interface GigabitEthernet1/5
bridge-group 1
nameif bridge
security-level 0
no shutdown

```

