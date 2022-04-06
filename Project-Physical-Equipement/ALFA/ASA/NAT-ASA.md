
NAT

```
object network OUTSIDE
subnet 172.16.1.0 255.255.255.0
nat (inside, outside) dynamic interface


object network INSIDE
subnet 172.18.1.0 255.255.255.0
nat (inside, outside) dynamic interface

object network DMZ
subnet 172.17.1.0 255.255.255.0
nat (dmz, outside) dynamic interface

object network PHONE
subnet 172.18.1.0 255.255.255.0
nat (phone, outside) dynamic interface

object network BRIDGE
subnet 172.16.1.0 255.255.255.0
nat (bridge, outside) dynamic interface


object network SITE
host 172.17.1.254
nat (dmz, outside) static 172.17.1.254

```

