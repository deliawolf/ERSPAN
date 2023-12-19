# ERSPAN

Encapsulated Remote Switched Port Analyzer Network

The Cisco ERSPAN mirrors traffic on one or more “source” ports and delivers the mirrored traffic to one or more “destination” ports on another switch. The traffic is encapsulated in Generic Routing Encapsulation (GRE) and is, therefore, routable across a Layer 3 network between the “source” switch and the “destination” switch.

Configure source
```
Configuration on Switch A (Source)
SwitchA(config)# monitor session 1 type erspan-source
SwitchA(config-mon-erspan-src)# source vlan 10
SwitchA(config-mon-erspan-src)# destination
SwitchA(config-mon-erspan-src-dst)# erspan-id 101
SwitchA(config-mon-erspan-src-dst)# ip address 192.0.2.2
SwitchA(config-mon-erspan-src-dst)# origin ip address 192.0.2.1
SwitchA(config-mon-erspan-src-dst)# exit
SwitchA(config-mon-erspan-src)# no shutdown
Configuration on Switch B (Destination)
```
Configure destination
```
SwitchB(config)# monitor session 1 type erspan-destination
SwitchB(config-mon-erspan-dst)# destination interface fastEthernet 0/2
SwitchB(config-mon-erspan-dst)# source
SwitchB(config-mon-erspan-dst-src)# erspan-id 101
SwitchB(config-mon-erspan-dst-src)# ip address 192.0.2.2
SwitchB(config-mon-erspan-dst-src)# exit
SwitchB(config-mon-erspan-dst)# no shutdown
```
Validate the config
```
Switch-1# show monitor session 1
```
