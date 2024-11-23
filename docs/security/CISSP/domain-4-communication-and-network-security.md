
# IPv4

| Classes | Subnet Mask      | Networks    |
| ------- | ---------------- | ----------- |
| A       | 255.0.0.0/8      | 2^7=128     |
| B       | 255.255.0.0/16   | 2^14=~16000 |
| C       | 255.255.255.0/24 | ~2 mln      |
**Reserved**
0.0.0.0/8
127.0.0.0/8
169.254.0.0/16
[RFC1918](https://www.rfc-editor.org/rfc/rfc1918.html)
	10.0.0.0
	172.16.0.0
	192.168.0.0

## NAT (Network Address Translation)
**DNAT**: multiple private IPs translated in 1 public IP
**Static NAT**: 1 private IP for 1 public IP
**PAT**: each private IP is assigned to a router port on the same public IP
Port Forwarding
[SNAT and DNAT](https://www.youtube.com/watch?v=wg8Hosr20yw)


# Remote Access
## Conditional Access
## MFA
## Least Privilege

## [802.1x](https://www.youtube.com/watch?v=dwPipQscMjM)
Port based authentication
### Patch management: 
Clients (remote endpoints) and VPNs should also part of periodic reviews and patches

# Virtual Private Cloud
Network security groups
Subnets
Internet gateway
NAT gateway: logical software instance to separate subnets communications
Network Peering

# Wireless Network Security
PSK pre-shared key
Enterprise mode (802.1X authn)

**Wi-Fi Protection Access**
WEP  - RC4 - Vulnerable
WPA  - TKIP - Vulnerable
WPA2 802.11i - CCMP/AES - strong
WPA3 - CCMP/AES, SAE - very strong

[Extensible Authentication Protocol](https://en.wikipedia.org/wiki/Extensible_Authentication_Protocol) (**EAP**)
framework to adapt to multiple authn methods ([TLS](https://en.wikipedia.org/wiki/Extensible_Authentication_Protocol#EAP_Transport_Layer_Security_(EAP-TLS)), Tunnelled TLS, LEAP...)

# Cellular
GSM
UTMS
HSPA+
4G (LTE)
5G 

SIM cards (Subscriber Identity Module)
ESN: electronic Serial Number

# Satellite
GPS ~27 satellites. each country or Region has its own satellite network.
Mix of wired and wireless transmissions

## Microsegmentation
[VXLAN](https://en.wikipedia.org/wiki/Virtual_Extensible_LAN): encapsulation of LAN ethernet frames in UDP datagrams to route them through phisically  separated LANs
Containerization
Multi Protocol Label Switching ([MPLS](https://en.wikipedia.org/wiki/Multiprotocol_Label_Switching))

## Edge Network
DMZ
CDN
- edge computing devices
