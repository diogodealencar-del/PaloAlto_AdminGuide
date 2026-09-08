

## HOW TO CONFIGURE ISP REDUNDANCY AND LOAD
## BALANCING
- ISP Load Balancing is used when more than one internet provider is connected to the firewall. Policy-Based Forwarding (PBF) is used
to forward traffic based on the source subnet.
- ISP Redundancy is used when one service provider is down and all traffic needs to be routed to the remaining service provider.

Normally, the firewall uses the destination IP address in a packet to determine the outgoing interface. The firewall uses the routing
table associated with the virtual router to which the interface is connected to perform the route lookup. Policy-Based Forwarding
(PBF) allows the user to override the routing table, and specify the outgoing or egress interface based on specific parameters such
as source or destination IP address, or type of traffic.

The following topology includes:
Two internal subnets
## • Subnet1: 192.168.1.0/24
## • Subnet2: 172.16.1.0/24
Two ISP gateways
## • ISP1: 10.30.6.254
## • ISP2: 10.30.1.254


Two important items to remember:
- PBF rules are applied either on the first packet (SYN) or the first response to the first packet (SYN/ACK). Application-specific rules
are not recommended for use with PBF.
- Address translation (NAT) rules are not applied unless a security rule matched the connection, which is why security rules need to
be in place for the address translation to work.


## Configuring Redundancy
Primary ISP configuration:
- Create a PBF rule that forwards traffic to the default gateway.
- Attach a tunnel monitoring profile and set the action as "disable on failure."


## Monitoring Profile:


This configuration forces all traffic coming from the 192.168.1.0/24 subnet to egress out of Ethernet 1/3.
A Monitor Profile is set up to monitor an IP address. In the test config, monitor profile "multiple isp" is used to monitor a public DNS
## 8.8.8.8.

When the monitor can no longer reach this IP address, the defined action (fail-over), takes place. The PBF rule is disabled and the
firewall falls back to the static route created in  the virtual router, as shown below. Path monitoring verifies connectivity to an IP
address so the firewall can direct traffic through an alternate route. The firewall uses ICMP pings as heartbeats to verify that the
specified IP address is reachable.

A monitoring profile allows specifying the threshold number of heartbeats to determine whether the IP address is reachable. When
the  monitored  IP  address  is  unreachable,  the  user  can  either  disable  the  PBF  rule  or  specify  a  fail-over  or  wait-recover  action.
Disabling the PBF rule allows the virtual router to take over the routing decisions.

Secondary ISP configuration
- Create a static route with a normal metric



## Configuring Load Sharing

Example 1: Load balancing with no backup
In this case, PBF is used to force traffic from different subnets through the respective ISP.  In this scenario, all traffic from subnet
192.168.1.0/24 is forwarded out of Ethernet 1/3, and subnet 172.16.1.0/24 is forced out of Ethernet 1/4.

## Rules:
o Rule 1: Subnet 192.168.1.0/24 going to 0.0.0.0/0 next hop is ISP 1
o Rule 2: Subnet 172.16.1.0/24 going to 0.0.0.0/0 next hop is ISP 2




Example 2: Load balancing and redundancy
In this case, PBF is used to forward traffic out of a particular interface based on the source
A backup is configured if the ISP goes down.


## Rules:
o Rule 1: Subnet 192.168.0.0/24 going to 0.0.0.0/0 next hop is ISP 1
o Rule 2: Subnet 172.16.0.0/24 going to 0.0.0.0/0 next hop is ISP 2
o Backup for Rule 1: Subnet 192.168.0.0/24 going to 0.0.0.0/0 next hop is ISP 2
o Backup for Rule 2: Subnet 172.16.0.0/24 going to 0.0.0.0/0 next hop is ISP 1

Rule 1 and Rule 2 perform the same action as Example 1.
The backup rules allow traffic to go through the ISP that has connectivity in case either were to fail.

If VPNs are configured (IPSec or GlobalProtect), refer to the following documents for information on how to configure the VPNs:
