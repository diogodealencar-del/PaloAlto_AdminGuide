

## PAN-OS SD-WAN
Routing Considerations for
Multiple VPN Clusters
## Palo Alto Networks, Inc.
www.paloaltonetworks.com
© 2022  Palo Alto Networks, Inc. Palo Alto Networks is a registered trademark of Palo Alto Networks. A list of
our trademarks can be found at  https://www.paloaltonetworks.com/company/trademarks.html. All other
marks mentioned herein may be trademarks of their respective companies.
## Revision Date: June 14, 2022

Table of Contents
Leveraging BGP for Flexible Routing3
The Need for Multiple VPN Clusters3
Intra-VPN Cluster Communications5
Expanding the Hub Spoke Example6
Alternate Designs for Multiple VPN Cluster Topologies8
ECMP and Symmetric Return8
Full Mesh with Merged VPN Clusters10
Full Mesh with All Branch Cluster12
Data Center Interconnect (DCI)13
Hub Firewall BGP Import Rule Manipulation15
## Configuration Example16
## Summary19
Routing Considerations for Multiple VPN Clusters© 2022 Palo Alto Networks, Inc.
## 2

Leveraging BGP for Flexible Routing
When designing advanced SD-WAN topologies, there may be a need to configure additional BGP features
to allow inter-VPN cluster communications to support branch communications between VPN clusters.  By
default, PAN-OS SD-WAN’s plugin automatically configures BGP routing for intra-VPN cluster
communications, and this greatly simplifies rollout for both hub spoke and full mesh topologies.  This paper
discusses alternate concepts for inter-VPN cluster communications to help network/security architects
design and implement SD-WAN networks spanning multiple geographies.
The Need for Multiple VPN Clusters
Configuring PAN-OS SD-WAN to operate in a multi-region deployment is one of the more common use
cases where two VPN clusters are used.  In this use case, two VPN clusters are deployed in different
geolocations and are used to provide backup from one region to the other by having the data center (DC)
hubs represented in each VPN cluster - one as a primary hub and one as a backup hub.
For example, an enterprise has two VPN clusters configured to support two georegions called United States
West and United States East.  One DC is in Denver and the other is in New York City.
© 2022 Palo Alto Networks, Inc.Routing Considerations for Multiple VPN Clusters
## 3

Two VPN clusters are created to support the hub and branch locations and the hub spoke topology is
deployed to allow each VPN cluster’s branches to be directly connected to the primary and backup hubs.
VPN ClusterBranch LocationsPrimary Hub LocationBackup Hub Location
United States EastAll branches east of the
North Dakota and Texas
east state lines
New York City data
center
Denver data center
United States WestAll branches west of the
Minnesota and
Louisiana west state
lines
Denver data centerNew York City data
center
Sample topology for United States West VPN cluster.
Routing Considerations for Multiple VPN Clusters© 2022 Palo Alto Networks, Inc.
## 4

Sample topology for United States East VPN cluster.
Intra-VPN Cluster Communications
By default, the PAN-OS SD-WAN plugin automatically creates the IKE peers, VPN tunnels and virtual
interfaces (VIFs), and configures BGP to allow communications between all locations within the cluster.  The
default BGP configuration creates the following routing capabilities:
## ●
All branches in the cluster have the same priority for each of the DC hubs.
## ●
The hub firewall sets the local preference on the branch firewalls to set the hub priority as the
primary or backup hub.  The hub priority is configured with the Panorama SD-WAN plugin’s VPN
Clusters “Hub Failover Priority” option.  The primary hub is set at priority = 1 and the backup hub is
set at priority = 2.
## ●
Routes advertised by the hub firewall are influenced by the local preference to create a “waterfall
failover” capability between the primary and secondary hubs.  The local preference value is created
from the Hub Failover Priority setting from the VPN cluster configuration.
## ●
The hub advertises a summary route to the connected branches.
## ●
The hub firewall does not advertise the routes it learns from one branch to another branch.
## ●
All intra-VPN cluster branch communication must go through the hub and if the primary hub goes
offline, the backup hub takes over.
© 2022 Palo Alto Networks, Inc.Routing Considerations for Multiple VPN Clusters
## 5

Once Panorama pushes the hub spoke configuration to the branch and hub firewalls and a commit is
performed, the hub spoke topology is fully operational.
Tip:For more information on what is automaticallyconfigured by the PAN-OS SD-WAN
plugin, please reference thePAN-OS SD-WAN Auto ProvisioningPrimer.
Expanding the Hub Spoke Example
In specific use cases, a branch office in the United States West cluster may need to communicate directly
with one of the branches in the United States East cluster, bypassing the need to go through the two hub
firewalls.  This is known as inter-VPN cluster communications.
Due to how each VPN cluster’s hub firewalls have programmed the local preference settings for their native
branch locations, the paths the branch traffic takes can encounter an asymmetry  problem.  The following
example illustrates this concept:
1.Branch-West in the United States West VPN cluster needs to communicate directly with Branch-East
in the United States East VPN cluster.
2.Based on the hub priority configured for each VPN cluster, the traffic originating from Branch-West
goes to the Hub-Denver firewall because it is programmed as the branch’s primary hub (priority = 1
configured in the VPN Cluster).  The Denver hub forwards Branch-West’s traffic to the Branch-East
firewall.
Routing Considerations for Multiple VPN Clusters© 2022 Palo Alto Networks, Inc.
## 6

3.Traffic arrives at the Branch-East firewall, but it doesn’t know about Branch-West’s subnet prefixes as
the hubs do not advertise the routes learned from each branch to other branches in the VPN cluster.
4.The return traffic from Branch-East is routed to the Hub-NYC firewall based on the branch’s BGP
configuration.  Branch-East has the Hub-NYC’s summary route in its route table and is told that its
primary hub is the Hub-NYC firewall (priority = 1 setting in the VPN cluster).
5.Routing C2S traffic through one hub firewall and S2C traffic through the other hub firewall creates an
“asymmetric flow” between the two hub firewalls and the traffic is dropped by the Hub-NYC firewall.
The reason Hub-NYC drops the traffic is because it is not the “session owner” and it doesn’t have the
session information necessary to match the return traffic.  Hub-Denver has this information as it
created the session.
The reason for the asymmetry is due to the default routing configuration created by the SD-WAN plugin,
which advertises the hub’s summary route and hub priority to each of the branch firewalls through the local
preference setting.
© 2022 Palo Alto Networks, Inc.Routing Considerations for Multiple VPN Clusters
## 7

Alternate Designs for Multiple VPN Cluster Topologies
To support a variety of advanced topologies, PAN-OS SD-WAN provides several other design mechanisms to
give network/security administrators the tools they need.  By understanding the advantages and
disadvantages of each alternate solution discussed in this paper, you can design an advanced SD-WAN
topology that meets your multiple VPN cluster requirements.
ECMP and Symmetric Return
To control how return traffic is sent back to the source, ECMP and symmetric return can be enabled on the
hub firewalls to ensure S2C flows take the same path back to the branch.  This design “flattens out” the hub
topology and allows both hubs to be used equally by the branches by removing the waterfall failover
capability between the Hub-Denver and Hub-NYC firewalls.  To achieve this, the hub priority is configured to
the same priority value on both hub firewalls in the VPN Cluster configuration.
The following diagram shows the new hub topology and its relationship to the branches defined in the VPN
cluster.  Both United States West and United States East VPN clusters now have two active hubs to use for
communicating the branch to branch traffic.  ECMP enables equal paths to both hubs and the symmetric
return keeps the C2S and S2C flows going through the same hub firewall.
Routing Considerations for Multiple VPN Clusters© 2022 Palo Alto Networks, Inc.
## 8

Considerations to understand before selecting this design include:
1.Do all branch locations need to communicate with all other branch and hub locations?
a.If the answer is “yes”, enabling ECMP and symmetric return is a good option and doesn’t
require a full mesh topology.
b.A full mesh topology can also be implemented, but this solution requires more firewall
resources to bring up the additional IKE peers, IPSec tunnels, and to perform health checks
between all locations.
2.Are the DC hub locations advertising the same or different subnet prefixes?
a.If the DC hubs are advertising the same prefixes, the hub priority needs to be set to the same
value in the VPN cluster.  This allows any hub to be used between the two VPN clusters.  To
balance traffic between the branch firewall and the hubs, a DIA AnyPath setting using either
source or destination prefixes can be used to split the traffic between the two hubs.  For more
information on how PAN-OS SD-WAN selects the best path, reference thePAN-OS SD-WAN
## Path Selection Primerdocument.
b.If the DC hubs are advertising different prefixes, the hub priority still needs to be set to the
same value in the VPN cluster, but the priority plays a smaller role in this use case as the more
specific route is used by the branch.
3.Do the branch firewalls have enough resources to support a full mesh topology?
a.If the answer is “yes”, changing the topology from a hub spoke to full mesh can simplify the
routing requirements.  This option also removes the extra hop to the hub firewall and reduces
latency by allowing the branches to talk to each other directly.  If your applications require the
lowest latency possible, this may be your best option.
b.If the branch firewalls do not have enough resources to support the number of devices in the
full mesh VPN cluster, you need to keep the topology as hub spoke or upgrade the firewalls to
a higher capacity model.
Tip:Depending on the firewall model and availableresources, a full mesh design can
negatively impact firewall performance, so understanding the capacity of your firewalls is an
important factor. Take inventory of all firewalls in the VPN cluster(s) and see how much available CPU
resources are available before switching to a full mesh topology.  As a general guideline, If the
firewalls are under 50% utilization, you can safely enable full mesh.
## Design Advantages - Configuration Simplicity
## ●
There are no other manual routing changes that need to be made outside of the SD-WAN plugin’s
default router settings.
## ●
Each Hub firewall is configured with ECMP and Symmetric Return on the SD-WAN virtual router to
achieve the results.
## ●
DIA AnyPath can be used to control path selection for each branch location to balance traffic loads to
each hub.
## ●
Hubs can be reused in other VPN clusters in either hub spoke or full mesh topologies.
© 2022 Palo Alto Networks, Inc.Routing Considerations for Multiple VPN Clusters
## 9

Design Disadvantages - Requires an Extra Hop
## ●
Inter-VPN cluster traffic between branch locations still needs to go through the hub.  The extra hop
added by the hub may increase latency, impact latency-sensitive applications, and decrease
performance and usability.
## ●
Additional SD-WAN policies may be needed on the hub firewalls if you need granular control of the
traffic type and applications allowed to traverse the hub.
Full Mesh with Merged VPN Clusters
A single VPN cluster can greatly simplify the network and routing requirements.  This alternate solution
merges two VPN clusters into a single cluster and configures the hubs in a waterfall failover topology for
redundancy.
Considerations to understand before selecting this design include:
1.Do all branch locations need to communicate with all other branch and hub locations?
a.If the answer is “yes”, switching the SD-WAN topology from hub spoke to full mesh to support
direct branch-to-branch communications is the simplest solution.  In this example, the full
mesh design allows all branches to communicate with each other and to both hubs in the
VPN cluster.  The firewall’s route table determines the egress VIF interface to the destination
and the SD-WAN algorithms select the best path within the VIF.
Routing Considerations for Multiple VPN Clusters© 2022 Palo Alto Networks, Inc.
## 10

b.All routing is configured through the PAN-OS SD-WAN plugin and manual routing
configuration outside of the SD-WAN plugin is minimal or eliminated.
2.Are the DC hub locations advertising the same or different subnet prefixes?
a.If the DC hubs are advertising the same prefixes, the hub priority needs to be considered and
one hub is configured as “preferred” over the other.  To balance traffic between the branch
firewall and the hubs, a DIA AnyPath setting using either source or destination prefixes can
be used to split the traffic between the two hubs.
b.If the DC hubs are advertising different prefixes, the hub priority still needs to be set to
different values in the VPN cluster, but the priority plays a smaller role in this use case as the
more specific route is used by the branch.
3.Do the branch firewalls have enough resources to support a full mesh topology?
a.If the answer is “yes”, changing the topology from a hub spoke to full mesh can simplify the
routing requirements.  This option also removes the extra hop to the hub firewall and reduces
latency by allowing the branches to communicate directly.  If your applications require the
lowest latency possible, this may be the best option.
b.If the branch firewalls do not have enough resources to support the number of devices in the
full mesh VPN cluster, this alternate solution won’t work.
Tip:Review and determine if your multiple VPN clusterdesign can benefit from a single VPN
cluster using a full mesh topology for the branch and hubs.  Firewall capacity and sizing must be
part of your decision as a full mesh design can negatively impact firewall performance.
Take inventory of all firewalls in the VPN cluster(s) and see how much available CPU resources are
available before switching to a full mesh topology.  As a general guideline, If the firewalls are under
50% utilization, you can safely enable full mesh.
The number of devices in the full mesh topology must also be considered as each branch connects
to all other branches in the cluster using a fully meshed VPN tunnel (MxN) design and this can
quickly increase the number of IPSec tunnels configured on each firewall.  Understand the IKE, IPSec
tunnel, and SD-WAN VIF capacity limits beforehand.
If your full mesh design pushes the firewall capacity toward its upper limits (for example, past 75%), it
may be better to use multiple VPN clusters as this design permits growth and the addition of more
branch locations.  Alternatively, the firewalls can be upgraded to a higher capacity model to support
the single full mesh design.
## Design Advantages - Configuration Simplicity
## ●
There are no other manual routing changes that need to be made outside of the SD-WAN plugin’s
default router settings.
## ●
Branch firewalls can communicate directly with any other branch and reduce additional latency
caused by going through the hub firewall.
## ●
Branch firewalls can failover to hub firewalls if branch-to-branch communications are lost.
## ●
DIA AnyPath can be used to control path selection for each location.
© 2022 Palo Alto Networks, Inc.Routing Considerations for Multiple VPN Clusters
## 11

## ●
Hubs can be reused in other VPN clusters in either hub spoke or full mesh topologies.
Design Disadvantages - Resources and Troubleshooting
## ●
Branch firewalls may not have enough free resources to bring up a full mesh topology.  Full mesh
adds additional CPU load to refresh the IKE keys and needs more data plane resources to support
the additional IPSec tunnels.
## ●
Full mesh topologies are more complex as they add many IPSec tunnels and SD-WAN VIFs.  This can
create additional troubleshooting overhead and prolong network issues if they’re not diagnosed
quickly.
## ●
SNMP and trap monitoring needs to be reviewed and filtered to reduce complexity.
Full Mesh with All Branch Cluster
This alternative design is a variation of the previous full mesh design.  The hub firewalls are added to the
VPN cluster as a branch instead of a hub and this allows a full mesh topology to be created with only branch
locations and no DC hubs.  This design allows every firewall to communicate with any other firewall defined
in the VPN cluster directly and simplifies the routing configuration by making every remote connection a
single hop.
Considerations to understand before selecting this design include:
1.Do all branch locations need to communicate with all other branch and hub locations?
Routing Considerations for Multiple VPN Clusters© 2022 Palo Alto Networks, Inc.
## 12

a.If the answer is “yes”, switching the SD-WAN topology from hub spoke to full mesh with an
“all branch” solution simplifies the design and routing requirements.  Full mesh allows all
firewalls in each location to communicate with each other directly.
b.All routing is configured through the PAN-OS SD-WAN plugin and manual routing
configuration outside of the SD-WAN plugin are minimal or eliminated.
2.Are the DC hub locations advertising the same or different subnet prefixes?
a.If the DC hubs are advertising the same prefixes, this causes an issue with “overlapping
subnets” being advertised from two “branch” locations and this alternate solution won’t work.
b.If the DC hubs are advertising different prefixes, the solution properly routes all
communications between locations as a single hop.
3.Do the firewalls have enough resources to support a full mesh topology?
a.If the answer is “yes”, changing the topology from a hub spoke to full mesh with “all
branches” can simplify the routing requirements and reduce additional hops.
b.If the branch firewalls do not have enough resources to support the number of devices in the
full mesh VPN cluster, this alternate solution won’t work.
c.See the previoustipson full mesh considerationsbefore finalizing your decision.
## Design Advantages - Configuration Simplicity
## ●
There are no other manual routing changes that need to be made outside of the SD-WAN plugin’s
default router settings.
## ●
Branch firewalls can communicate with any other branch directly and reduce added latency going
through the hub firewall.
## ●
DIA AnyPath can be used to control path selection for each location.
Design Disadvantages - Resources and Troubleshooting
## ●
Branch firewalls may not have enough free resources to bring up a full mesh topology.  Full mesh
adds additional CPU load to refresh the IKE keys and needs more data plane resources to support
the additional IPSec tunnels.
## ●
Full mesh topologies are more complex as they add many IPSec tunnels and SD-WAN VIFs.  This can
create additional troubleshooting overhead and prolong network issues if they’re not diagnosed
quickly.
## ●
SNMP and trap monitoring needs to be reviewed and filtered to reduce complexity.
Data Center Interconnect (DCI)
The DCI alternative connects the hub firewalls together using an existing network that is designed to
connect two or more data centers together to share resources across the organization.  This route can be
configured on the hub firewalls independently of the SD-WAN routing functions and it can leverage any of
the DC technologies such as ECMP, LAG interfaces, NAT, and more.
© 2022 Palo Alto Networks, Inc.Routing Considerations for Multiple VPN Clusters
## 13

Considerations to understand before selecting this design include:
1.Do all branch locations need to communicate with all other branch and hub locations?
a.If the answer is “No” and only some branches need this requirement, the DCI connection may
offer a simpler solution.
b.The VPN cluster routes are automatically configured by the PAN-OS SD-WAN plugin and
routing between the hubs is configured outside of the plugin.  This allows you to configure
the network to direct traffic from one hub to another over the DCI connection using any
supported network protocols and features.  VPN connections are optional and if they’re not
needed, crypto overhead can be eliminated.
c.The DCI connection can be any DC-to-DC network fabric ranging from a dedicated circuit,
MPLS, layer 2 connection, or an IPSec tunnel over the same circuits used by PAN-OS SD-WAN.
2.Are the DC hub locations advertising the same or different subnet prefixes?
a.If the DC hubs are advertising the same prefixes, this causes an issue with “overlapping
subnets” being advertised from two hub locations and this alternate solution won’t work.
b.If the DC hubs are advertising different prefixes, the solution properly routes all
communications between the hubs.
## Design Advantages - Configuration Simplicity
## ●
Minimal route configuration on the hub firewalls and peer routers outside of the SD-WAN plugin.
## ●
Leverages any existing DIA capabilities for redundancy and failover between data centers.
Routing Considerations for Multiple VPN Clusters© 2022 Palo Alto Networks, Inc.
## 14

## ●
DIA AnyPath can be used to control path selection for each location.
## ●
Hubs can be reused in other VPN clusters in either hub spoke or full mesh topologies.
Design Disadvantages - Added Configuration and Hops
## ●
If granular control is required to manage inter-VPN cluster communications, additional router
configuration is required to permit/deny each branch from traversing the DCI connection.  If
branches are added or removed frequently, this can add to management overhead.
## ●
Extra hops are added to branch-to-branch communications, latency may increase and application
usability can falter.
## ●
There is a potential for asymmetric routing if the hub router configurations are not programmed
correctly.
Hub Firewall BGP Import Rule Manipulation
This alternate solution provides granular control to permit or deny branch communication between VPN
clusters.  It uses BGP import filters to perform prefix filtering on the hub firewall and can be more complex
than some of the other alternatives discussed.  The benefit is the freedom to manually configure and
manipulate the branch communications of specific firewalls to allow them to communicate with branch
locations in another VPN cluster.
© 2022 Palo Alto Networks, Inc.Routing Considerations for Multiple VPN Clusters
## 15

Considerations to understand before selecting this design include:
1.Do all branch locations need to communicate with all other branch and hub locations?
a.If the answer is “No” and only some branches need this requirement, this alternate solution
can be a good solution for a limited number of branches.
b.The majority of the routing configuration for the branch to hub VPN cluster communications
are automatically handled by the PAN-OS SD-WAN plugin.
c.The hub BGP import rules are only configured on the primary hub of one VPN cluster to
permit a branch’s routes to be exchanged with another branch belonging to another VPN
cluster.
## Design Advantages - Centralized Route Configuration
## ●
This alternate solution minimizes the number of firewalls that need to be configured and only
requires route changes on the primary hub firewall on one VPN cluster.
## ●
Reducing changes to a single hub firewall minimizes the chance of network disruptions if
configuration errors are made.
## ●
DIA AnyPath can be used to control path selection for each location.
## ●
Hubs can be reused in other VPN clusters in either hub spoke or full mesh topologies.
Design Disadvantages - Added Configuration and Hops
## ●
This alternate solution requires manual configuration for each branch that requires inter-VPN cluster
communications, making scalability more difficult.  If network growth is stable and there are not a
lot of changes at the branch locations, this may not be an issue.
## Configuration Example
The following example shows how the hub’s BGP import rules are configured to allow two specific branches
to exchange route information.  This allows the branch to learn the subnet prefixes of its peers to properly
route traffic.
1.Decide which VPN cluster to modify and identify the Primary Hub that its branches attach to.
a.In this example, we select the United States West VPN cluster and modifications are made on
the Hub-Denver firewall.
2.Open Panorama and select the primary hub device
a.In this example, the Hub-Denver firewall is selected.
3.Using a separate template outside of the SD-WAN plugin, create a routing enhancement on the hub
device’s virtual router:
a.Under the BGP protocol, create a “dummy” peer group for Branch-West as shown in the
illustration below.  Enter the name of the branch that the import rule applies to.
b.Use the BGP peer group defaults and leave all other BGP configuration items unconfigured
as they are not used for the dummy peer group.
Routing Considerations for Multiple VPN Clusters© 2022 Palo Alto Networks, Inc.
## 16

4.After the dummy peer group is created, create an Import Rule and add the dummy peer group you
created in the previous step to the “Used By” configuration as shown below.
© 2022 Palo Alto Networks, Inc.Routing Considerations for Multiple VPN Clusters
## 17

5.Using the import rule’s Match tab, configure the “Community Regular Expression” to match on the
branch’s community string.
a.In this example, the community match expression for Branch-West’s community string is
## “^44032:3$”.
b.Leave all other match criteria at the default blank values as shown in the illustration below.
6.On the import rule’s Action tab, configure the Community type to “Overwrite” and set the overwrite
value to the primary hub’s community value.
a.In this example, the community type overwrite value to the Hub-Denver’s community string
is “44032:1”.
b.Set the action to “Allow” and ensure the dampening, next hop, and origin fields are set to the
default value of “None” as shown in the illustration below.
Routing Considerations for Multiple VPN Clusters© 2022 Palo Alto Networks, Inc.
## 18

7.Commit and push the configuration to the primary hub.  In this example, the configuration is pushed
to the Hub-Denver firewall.
8.Review the route table to ensure that the branch subnet prefixes are exchanged properly and test
connectivity between the two branches.
## Summary
This paper exposes some of the challenges with multiple VPN Cluster network designs and shows five
design alternatives that can solve the asymmetric routing issue when branch offices try to communicate
between two VPN clusters.  By fully understanding your network’s requirements and firewall resources, any
one of these solutions can help you create a flexible SD-WAN design for inter-VPN cluster communications.
For more information on PAN-OS SD-WAN concepts, please visit the following links:
## ●
PAN-OS Administration Guide
## ●
PAN-OS SD-WAN TechDocs
## ●
Panorama TechDocs
© 2022 Palo Alto Networks, Inc.Routing Considerations for Multiple VPN Clusters
## 19