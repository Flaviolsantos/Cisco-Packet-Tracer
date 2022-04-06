Acess-lists

```
access-list OUTSIDE extended permit ip any any
access-list INSIDE extended permit ip any any
access-list DMZ extended permit ip any any
access-list PHONE extended permit ip any any
access-list BROADCAST extended permit ip any any
```

Attach the ACLs to the interfaces

```
access-group OUTSIDE in interface outside
access-group DMZ in interface dmz
access-group INSIDE in interface inside
access-group PHONE in interface phone
access-group BROADCAST in interface broadcast
```
