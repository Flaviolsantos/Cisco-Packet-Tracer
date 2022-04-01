DHCP to atribute IPs for the PCs inside the Network


```

ip dhcp excluded-address 10.0.1.1
ip dhcp excluded-address 10.1.1.1
ip dhcp excluded-address 10.2.1.1

ip dhcp pool V10
 network 10.0.1.0 255.255.255.0
 default-router 10.0.1.1
 option 150 ip 10.1.1.1
 dns-server 8.8.8.8
ip dhcp pool V20
 network 10.1.1.0 255.255.255.0
 default-router 10.1.1.1
 option 150 ip 10.1.1.1
 dns-server 8.8.8.8
ip dhcp pool V30
 network 10.2.1.0 255.255.255.0
 default-router 10.2.1.1
 option 150 ip 10.1.1.1
 dns-server 8.8.8.8
 
 ```
 
