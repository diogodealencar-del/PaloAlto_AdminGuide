

## PAN-OS SD-WAN
## Auto Provisioning Primer
## Palo Alto Networks, Inc.
www.paloaltonetworks.com
© 2022  Palo Alto Networks, Inc. Palo Alto Networks is a registered trademark of Palo Alto Networks. A list of
our trademarks can be found at  https://www.paloaltonetworks.com/company/trademarks.html. All other
marks mentioned herein may be trademarks of their respective companies.
## Revision Date: March 28, 2022

Table of Contents
## Simplifying Deployment Through Automation3
SD-WAN Deployment Overview3
SD-WAN Plugin Devices5
SD-WAN Plugin VPN Clusters7
SD-WAN Plugin Auto Configuration9
## Interface Management Profile10
## Monitor Profile10
IKE Crypto Profile11
IPSec Crypto Profile11
IKE Gateways12
IPSec VPN Tunnels15
## Security Zones17
SD-WAN Interfaces17
## Virtual Router20
## Static Routes21
BGP Dynamic Routing23
Enabling BGP Protocol24
Auto Configured BGP Peer Group and Members26
Auto Configured BGP Export and Import Rules29
Auto Configured BGP Redistribution Rules33
## Summary37
PAN-OS SD-WAN Auto Provisioning Primer© 2022 Palo Alto Networks, Inc.
## 2

## Simplifying Deployment Through Automation
PAN-OS SD-WAN is a flexible software defined WAN solution that supports hub spoke, full mesh, and hybrid
SASE topologies.  To help customers quickly roll out SD-WAN, Panorama’s SD-WAN plugin automates
firewall configuration and enables the necessary features to create a robust and redundant network
between SD-WAN locations.
This paper discusses the deployment steps involved with a new SD-WAN implementation, how the
SD-WAN plugin configures each firewall, and which features are automatically enabled.
SD-WAN Deployment Overview
The following configuration steps are required to onboard the firewalls and to get them ready for SD-WAN
deployment.  The first six steps are prerequisites to rolling out SD-WAN and are fully covered in theSD-WAN
Administration Guideso they are not covered in thispaper.  Please reference those guides for additional
information if needed.
SD-WAN prerequisites include:
1.Plan your deployment
2.Register and license the new firewalls (excludes ZTP)
3.Add firewalls to Panorama
4.Create Panorama device groups (DG) and templates
5.Create the Link Tag(s)
6.Create the virtual routers (optional)
The SD-WAN configuration steps for a greenfield deployment include:
7.Enable SD-WAN on firewall interface(s)
8.Group interfaces to create Link Bundle (optional)
9.Add firewalls to SD-WAN device list
10.Create SD-WAN VPN cluster
11.Create SD-WAN profiles and policies
12.Set up security policies
Steps 9 and 10 are covered thoroughly in this paper as this is where the majority of the automated SD-WAN
configuration is performed.  Panorama’s SD-WAN plugin is used to create the SD-WAN network topology
between all SD-WAN locations and to perform monitoring and reporting functions.
© 2022 Palo Alto Networks, Inc.PAN-OS SD-WAN Auto Provisioning Primer
## 3

The four SD-WAN plugin components include:
1.Devices
2.VPN Clusters
3.Monitoring
4.Reporting
The configuration items that are automatically created by the SD-WAN plugin include the following items
and are discussed in detail in the subsequent sections.
## ●
SD-WAN related profiles
## ●
IKE gateways, IPSec VPN tunnels, pre-shared keys
## ●
Virtual router and SD-WAN interfaces
## ●
Static routes, BGP, and redistribution profiles
Throughout this document, the following hub spoke topology is used to demonstrate the SD-WAN plugin
activity.  Two branches named us1-gcp and us2-gcp connect to a single hub named us3hub-gcp and each
site has two ISP circuits and one MPLS WAN connection.
PAN-OS SD-WAN Auto Provisioning Primer© 2022 Palo Alto Networks, Inc.
## 4

SD-WAN Plugin Devices
The SD-WAN plugin’s Devices component is used to declare the role of the firewall and set up the routing
features.  The firewall’s role can be either a Hub or a Branch and the configuration items automatically
created depend on the declaration.
Branch firewalls can connect to hub and/or branch firewalls and initiate the path health checks to the hub.
Hub firewalls are devices located at the headquarters or data center locations and act as centralized
termination points for branch VPN tunnels.  Hub firewalls do not initiate the health checks to the branches.
The following illustration shows an example of the us3hub-gcp hub firewall and its device configuration.
Name- The name of the firewall to declare a Hub orBranch role.  The name entered is used in device
lists to simplify onboarding and is displayed in various reports and troubleshooting screens.
Type- The Hub or Branch role to assign to the firewall.Depending on the type assigned, the
SD-WAN plugin creates the necessary IPsec tunnels, enables health check functions, configures BGP
routing, and places the virtual interfaces (VIFs) in the proper SD-WAN zones.
Virtual Router Name- The virtual router (VR) to assignto SD-WAN.  All available VRs defined on the
device are displayed in the dropdown list and only one VR can be assigned to the SD-WAN overlay.
Site- A free form field used to provide a descriptivename for the site.  A best practice is to provide a
descriptive name to help identify the site in the visualization screens and for simplifying
© 2022 Palo Alto Networks, Inc.PAN-OS SD-WAN Auto Provisioning Primer
## 5

troubleshooting.  Avoid using spaces or special characters in site names as this may impact how the
data is displayed in the SD-WAN Monitoring functions.
Link Tag (Hub only)- The link tag that is assignedto a hub firewall and is used by DIA AnyPath to
failover branch internet traffic to a hub location.
Zone Selection- Provides a way for existing PAN-OScustomers to map an existing zone to one of
the four predefined SD-WAN zones to allow the SD-WAN interfaces to be properly configured for
egress traffic.  For new customers that do not have pre-existing security zones, this configuration
step can be omitted and they can use the predefined SD-WAN zones for both SD-WAN traffic
handling and security policies.
BGP- Provides BGP configuration information to theSD-WAN plugin to automatically configure
routing between all firewall devices belonging to the same VPN Cluster.  The mandatory information
to configure BGP includes:
## ●
Router ID- The router ID specified in IPv4 format
## .
## ●
Loopback IP- The loopback IP address that is usedfor BGP peering between SD-WAN
firewalls.  The router ID can be used as the loopback IP.
## ●
AS Number- A private BGP ASN from either a 2 byteor 4 byte range.  A valid private ASN falls
into the following ranges: 2 byte (54512 - 65534), 4 byte (4200000000 - 4294967294).
## ●
Prefixes- IP prefixes (networks) that are redistributedfrom the firewall to all other locations.
For hub firewalls, prefixes are required.  For branch firewalls, all connected routes are
PAN-OS SD-WAN Auto Provisioning Primer© 2022 Palo Alto Networks, Inc.
## 6

automatically redistributed to all other locations.  Additional non-connected prefixes can be
added to branch firewalls if needed using the Prefixes field.
The BGP configuration options provided in the SD-WAN plugin Devices screen are sufficient to
create the BGP routing between all locations.  A separate Panorama template or device group is not
required to complete the BGP configuration.
Upstream NAT- Provides the upstream NAT IP addressinformation (static IP or DDNS) for the
SD-WAN plugin to properly configure IKE and IPSec VPN tunnels between the SD-WAN sites.  This is
optional and is only required for firewalls that have another device ahead of it performing NAT
address translation.
Prisma Access Onboarding (Branch)- Provides the abilityto connect the branch firewall to a Prisma
Access hub (IPSec Termination Node) to create a hybrid SASE topology.  Please reference the
“Onboard PAN-OS Firewalls to Prisma Access” for moreinformation.
SD-WAN Plugin VPN Clusters
The SD-WAN plugin’s VPN Clusters component is used to create the SD-WAN network topology and Hub-
Spoke, Mesh (branch-to-branch), and hybrid deployments are supported.  The VPN Clusters component
makes it easy to roll out dozens to hundreds of SD-WAN sites through an intuitive user interface and
automates many network configuration items behind the scenes.
© 2022 Palo Alto Networks, Inc.PAN-OS SD-WAN Auto Provisioning Primer
## 7

Name- The name of the VPN cluster.  This is a freeform field and spaces are not permitted.  The best
practice is to give the VPN cluster a descriptive name to make it more intuitive when using the
visualization, reporting, and troubleshooting components.  The SD-WAN plugin can create and
manage multiple VPN clusters for larger SD-WAN deployments.
Type- The network topology type declared for theVPN cluster.  Either Hub-Spoke or full Mesh
(branch-to-branch) topologies are supported.  Hubs are optional for the full mesh branch-to-branch
network topology and if added, the topology becomes a hybrid where the branches are connected
to both the hub locations as well as to every other branch.
Branches- Add “branch” firewall devices to the VPNcluster.  When the firewalls were onboarded
with the SD-WAN plugin’s Devices component, they were given a device type - either branch or hub.
The plugin displays all the “branch” devices to simplify the VPN cluster creation.  In the example
above, two branch locations connect to a single hub location in a hub spoke topology.
Hubs- Add “hub” firewall devices to the VPN cluster.All firewalls onboarded with the SD-WAN
plugin’s Devices component using a type of “hub” will be displayed in the list.  A maximum of four
hubs are supported to provide a waterfall failover topology for the branch locations.  Hubs can
belong to more than one VPN cluster.
HA Status- Shows the HA state of the HA Active/Passivefirewall members.  A location that
deploys two SD-WAN firewalls in an HA A/P pair must add both firewalls to the VPN cluster
using the plugin.  You can optionally “Group HA Peers” to simplify the management and
display of the firewall pair.
Hub Failover Priority- Assigns a failover priorityto the hub to provide a waterfall failover
capability for the branch locations. The hub failover is activated when multiple hubs are
advertising the same hub networks (prefixes) to the branches to provide redundancy.  A
priority of “1” is the highest priority and the valid priority range is 1 to 4.  The hub failover
priority instructs the plugin to modify the branch firewalls’ BGP import rule Local Preference
setting to control the failover order to each of the connected hubs.  When the highest priority
hub is not available, the branch forwards its hub traffic through the second priority hub, and
so on down the list until the lowest priority firewall is reached.
Allow DIA VPN- Controls the ability to permit ordeny the branch firewalls’ ability to fail its
DIA traffic (internet) over to hub location.  Enabling the checkbox permits the branches to
send their internet traffic through the hub to get a better Internet user experience if their
local ISP circuits are congested or down.
Tip:If the hub locations have plenty of bandwidthand can be used as an alternate DIA
path, enabling this option provides the best redundancy for the branches.  For hub locations
PAN-OS SD-WAN Auto Provisioning Primer© 2022 Palo Alto Networks, Inc.
## 8

that do not have sufficient bandwidth, disable this option as the additional branch traffic can
negatively impact the hub’s internet circuits.
When the firewall devices have been added and the VPN clusters configured, Panorama creates the
configuration for the branch and hub firewalls automatically.  To bring the SD-WAN topology up, perform a
Panorama commit and push the configuration to the firewall devices in the cluster.
SD-WAN Plugin Auto Configuration
The Panorama SD-WAN plugin greatly reduces the time and configuration complexity that is involved in
deploying a redundant and highly reliable SD-WAN network across many locations.  The items that are
automatically configured by the SD-WAN plugin include the following:
## ●
## Interface Management Profile
## ●
## Monitor Profile
## ●
IKE Crypto Profile
## ●
IPSec Crypto Profile
## ●
IKE Gateways
## ●
IPSec VPN Tunnels
## ●
## Security Zones
## ●
SD-WAN Interfaces
## ●
## Virtual Router
## ●
## Static Routes
## ●
BGP Dynamic Routing
Administrators can verify the auto created items on their SD-WAN enabled firewalls by changing the device
context within Panorama and drilling down on each firewall’s SD-WAN configuration.  The illustration below
shows how to select the firewall in the VPN cluster to view.
© 2022 Palo Alto Networks, Inc.PAN-OS SD-WAN Auto Provisioning Primer
## 9

## Interface Management Profile
A new Interface Management Profile named “check_ping” is automatically created on the firewall and
enabled with the new “Ping” network service.  This profile is applied to all SD-WAN VPN tunnels configured
on the firewall and allows the virtual interface to participate in the SD-WAN ICMP health checks.
## Monitor Profile
A new Monitor Profile named “sdwan default” is created on the firewall and enabled with the Wait Recover
action and the default values for a 3 second interval and threshold of 5 are applied.  The monitor profile is
applied to all SD-WAN VPN tunnels to control the tunnel monitoring activity to detect tunnel failures.
PAN-OS SD-WAN Auto Provisioning Primer© 2022 Palo Alto Networks, Inc.
## 10

IKE Crypto Profile
A new IKE Crypto Profile named “sdwan default” is created on the firewall and enabled for strong security
with DH Group 20, AES-256-CBC encryption, and SHA384 authentication.  The pre-shared key lifetime is set
to renew every 8 hours and all IKE gateway peering between the SD-WAN locations use this profile.
IPSec Crypto Profile
A new IPSec Crypto Profile named “sdwan default” is created on the firewall and enabled for strong security
with AES-256-GCM encryption, DH Group 20 with a 1 hour lifetime, and SHA256 authentication.  All SD-WAN
IPSec tunnels use this profile to secure communications between SD-WAN locations.
© 2022 Palo Alto Networks, Inc.PAN-OS SD-WAN Auto Provisioning Primer
## 11

IKE Gateways
The Panorama SD-WAN plugin automatically configures an IKE Gateway on all firewall interfaces that are
enabled for SD-WAN and assigned an SD-WAN interface profile.  The interface profile’s link type can provide
additional input to determine the IKE gateway creation.  For example, an IKE gateway is created between all
public link types on the hub and branch firewalls in a hub spoke topology or between all branch firewalls in
a mesh topology.  IKE gateways are also created between private WAN link types such as MPLS to MPLS and
satellite to satellite circuits.
The illustration below shows an example of the IKE Gateway created on the us3hub-gcp hub firewall.  In
addition, the SD-WAN plugin adds a comment to show where the IKE gateway is applied.  In this example,
this IKE gateway is used for the us2-gcp branch 2 connection and the firewall belongs in the Cluster-US VPN
cluster.
PAN-OS SD-WAN Auto Provisioning Primer© 2022 Palo Alto Networks, Inc.
## 12

The SD-WAN plugin uses the following naming convention for IKE gateways:
gw_0101_007058044445587_0104
gw- Identifies the gateway as an SD-WAN provisionedgateway.
0101- The local firewall’s source interface participatingin the SD-WAN IKE peering - 0101 is Eth1/1.
007058044445587- The serial number of the peer firewallparticipating in the IKE relationship.
0104- The peer firewall’s local interface used inthe SD-WAN IKE peering activity - 0104 is Eth1/4.
SD-WAN IKE Gateway peering is performed with the following default configuration:
Version- Configured for “IKEv2 only mode” to supportstrong security and efficient peering.
Address type- Configured for the IPv4 address family.
© 2022 Palo Alto Networks, Inc.PAN-OS SD-WAN Auto Provisioning Primer
## 13

Interface- Auto populated by the SD-WAN plugin for interfaces that have SD-WAN enabled.
Local IP Address- Auto populated by the SD-WAN pluginand the IP address is extracted from the
SD-WAN interface.
Peer IP Address Type- Configured according to thefirewall’s SD-WAN device type. Hubs are set
with a Dynamic peer type and allow the branch to initiate the VPN Phase 1 activity.  Branches are set
with the hub’s IP address or another branch’s IP address information (mesh topology).
Authentication- Configured for “Pre-shared Key”.
Pre-shared Key- Automatically populated with a random32 character key generated by a complex
algorithm.  The key is stored in a secured area of the operating system that is not accessible and key
lifetimes are set relatively short to ensure keys are rotated regularly.  Administrators can manually
refresh IKE keys at any time using the “Refresh Ike Key” function in the VPN Clusters plugin option.
Local and Peer Identification- Configured to useKEYID authentication, which is generated from
the device serial number in binary format.
Comment- Auto populated with the name and serialnumber of the remote firewall the IKE gateway
is terminated on.  The VPN cluster information is also shown.
The SD-WAN plugin also configures IKE Gateway options in the Advanced Options tab as follows:
PAN-OS SD-WAN Auto Provisioning Primer© 2022 Palo Alto Networks, Inc.
## 14

Common Options- Items configured depend on the SD-WAN device type.
## ●
Hub devices have both “Enable Passive Mode” and “Enable NAT Traversal” enabled.
## ●
Branch devices have “Enable NAT Traversal” enabled.  The “Enable Passive Mode” is never
selected for a branch firewall as it has to initiate the IKE Phase 1 activity to the peer.
IKEv2 IKE Crypto Profile- The ”sdwan-default” profileis automatically selected for the SD-WAN IKE
gateway and the “Strict Cookie Validation” checkbox is disabled.
IKEv2 Liveness Check- Configured with a 5 secondinterval.
IPSec VPN Tunnels
The SD-WAN plugin automatically configures the IPSec VPN tunnels based on the IKE gateways
provisioned.  The plugin also creates the required number of IPSec tunnels to create a mesh between the
ISP circuits defined on both firewalls.  In this paper’s hub spoke example, the us1-gcp branch firewall had
two ISP circuits and the us3hub-gcp hub firewall had two ISP circuits, so a total of four VPN tunnels would
be created between the two SD-WAN firewalls’ ISP interfaces.
© 2022 Palo Alto Networks, Inc.PAN-OS SD-WAN Auto Provisioning Primer
## 15

The SD-WAN plugin uses the following naming convention for SD-WAN IPSec tunnels:
tl_0101_007058044445578_0104
tl- Identifies the virtual interface as an SD-WANprovisioned IPSec tunnel.
0101- The local firewall’s source interface thatoriginated the IPSec tunnel - 0101 is Eth1/1.
007058044445578- The serial number of the peer firewallthe IPSec tunnel terminates to.
0104- The peer firewall’s local interface used toterminate the IPSec tunnel - 0104 is Eth1/4.
SD-WAN IPSec VPN tunnel is created with the following default configuration:
Tunnel Interface- The tunnel interface is automaticallyprovisioned by the SD-WAN plugin starting
with “tunnel.900” and increases upward for each new tunnel added.
TIP:If there are existing IPSec tunnels that arenumbered above 900, they need to be
renumbered below 900 before enabling PAN-OS SD-WAN on the firewall.
Type- Configured for “Auto Key”.
Address Type- Configured for the IPv4 address family.
IKE Gateway- Automatically populated with the IKEgateway the SD-WAN plugin created.  See the
IKE Gatewayssection for more details.
IPSec Crypto Profile- Automatically configured withthe “sdwan-default” IPSec crypto profile the
SD-WAN plugin created.  The “Show Advanced Options” and “Enable Replay Protection” options are
enabled with an Anti Replay WIndow size of 1024.
Tunnel Monitor- Automatically enabled and the “DestinationIP” is populated with an IP address
from the “VPN Address Pool'' defined in the SD-WAN Plugin’s VPN Cluster configuration.
PAN-OS SD-WAN Auto Provisioning Primer© 2022 Palo Alto Networks, Inc.
## 16

The Monitoring Profile is automatically configured to use the “sdwan-default” monitoring profile
created by the SD-WAN plugin.
Comment- Auto populated with the name and serialnumber of the remote firewall the IPSec
tunnel is terminated on.  The VPN cluster information is also shown.
## Security Zones
The SD-WAN plugin automatically creates the necessary security zones it needs to deploy SD-WAN.  The
zones created include:
zone-internal- Used by the loopback interface specifiedin the Devices configuration when the
SD-WAN firewall was on-boarded to Panorama.  The loopback interface is used to set up BGP
peering between the VPN cluster’s SD-WAN firewalls.
zone-to-branch- Used by the SD-WAN virtual interfaces(VIFs) defined on the hub or branch firewall
that are destined to go to a branch location.  When this zone is created on the hub firewall, all VIFs
going to branch locations are placed in this zone.  When this zone is created on the branch firewall,
all VIFs going to another branch location in a branch-to-branch mesh topology are placed in this
zone.
zone-to hub- Used by the SD-WAN virtual interfaces(VIFs) defined on the branch firewall that are
destined to go to a hub location.
zone-to-internet- Used by interfaces that go to thepublic internet.  By default, this zone doesn’t
have any interfaces.
zone-to-pa-hub- Used by branch firewalls that areconnected to a Prisma Access Hub (IPSec
Termination Node).  The VIF that connects to the Prisma Access Hub is placed into this zone.
SD-WAN Interfaces
The SD-WAN plugin automatically creates the interface types it needs to fully activate SD-WAN on the
branch and hub firewalls.  The three different interfaces types created include:
loopback.901- A loopback interface created for BGPpeering between the firewalls belonging to the
same VPN cluster.  This loopback interface is added to zone-internal automatically and only one
loopback interface is required per firewall.
© 2022 Palo Alto Networks, Inc.PAN-OS SD-WAN Auto Provisioning Primer
## 17

tunnel.9xx- The IPSec tunnel interfaces created toconnect the SD-WAN firewalls together.  The
number of tunnels created by the SD-WAN plugin depends on the VPN cluster type (Hub-Spoke or
Mesh), the number of branches and hubs in the VPN cluster, and the number of SD-WAN enabled
interfaces (ISP circuits) at each location.  The tunnel numbering starts from tunnel.900 and increases
upward for each tunnel added and the numbering doesn’t have to be sequential.  The illustration
below shows the us2-gcp branch firewall’s VPN tunnels that were automatically created by the
SD-WAN plugin.  The comment field contains important information showing where the VPN tunnel
is terminating and in this example, it’s the us3hub-gcp hub firewall.
sd-wan.9xx- The SD-WAN virtual interfaces (VIFs)created to group IPSec tunnels or DIA Ethernet
interfaces together.  All IPSec tunnels going to the same destination are grouped together in the
same VIF interface.
PAN-OS SD-WAN Auto Provisioning Primer© 2022 Palo Alto Networks, Inc.
## 18

TIP:By default, the DIA interfaces are always grouped into the sdwan.901 interface while IPSec
tunnels are grouped into sdwan.902 or higher VIF interfaces.
To illustrate this concept, the example below shows the us1-gcp branch firewall’s sdwan.904 VIF
grouping five IPSec tunnels together.  The VPN tunnels range from tunnel.901 - tunnel.905 and they
all go to the us3hub-gcp hub firewall.  The us1-gcp branch firewall also groups three Ethernet
interfaces, ranging from Ethernet1/1 - Ethernet1/3, together into the sdwan-901 VIF to service DIA
internet traffic.
In this example, the branch firewall is configured with DIA AnyPath to allow the branch office to
redirect its internet traffic to the hub location to obtain a better path if its ISP circuits degrade or go
down.  To support DIA AnyPath, the sdwan-904 VIF is also placed in the DIA VIF and the path
selection order is controlled by the Traffic Distribution Profile.
© 2022 Palo Alto Networks, Inc.PAN-OS SD-WAN Auto Provisioning Primer
## 19

## Virtual Router
PAN-OS SD-WAN supports one virtual router (VR) for SD-WAN routing and both static routes and BGP are
used to forward traffic to the internet and to the other SD-WAN locations. The option to disable the BGP
configuration and use only static routes to customize routing for special use cases is also supported, but this
paper concentrates on the BGP routing option that is configured by the SD-WAN plugin.
Panorama templates are used to configure and push the SD-WAN virtual router and its Ethernet interfaces
to each firewall defined in the VPN cluster.  Afterwards, the SD-WAN plugin is used to add the SD-WAN
virtual interfaces to the VR to complete the SD-WAN configuration.
The illustrations below show two views of the same SD-WAN VR called “DemoRouter” and how the SD-WAN
plugin automatically configures and adds the necessary SD-WAN virtual interfaces to the VR.
## ●
The first illustration is from the Panorama template and shows how the VR is configured with the
physical Ethernet interfaces used by each firewall.
## ●
The second illustration is from the local firewall and shows how the VR is configured with the
SD-WAN virtual interfaces and the physical Ethernet interfaces.
The Panorama template configures each firewall’s SD-WAN VR to include the physical Ethernet interfaces
the firewall uses for SD-WAN.You can also use theVR to support other interfaces that you don't use for
SD-WAN.The following illustration shows an exampleof the “DemoRouter” VR used in each of the firewalls
showcased in this paper.  The SD-WAN interfaces are Ethernet1/1 - Ethernet1/3 and the remaining interfaces
are used for other purposes.
PAN-OS SD-WAN Auto Provisioning Primer© 2022 Palo Alto Networks, Inc.
## 20

The next illustration shows the branch firewall’s VR configuration after Panorama pushed the SD-WAN
configuration to each firewall.  When viewed from the local firewall’s perspective, the VR shows all SD-WAN
interfaces, both physical and virtual, as well as any other interfaces required to support the local functions
that are assigned to the “DemoRouter” VR.
## Static Routes
The SD-WAN plugin creates static routes to enable the SD-WAN network and the number of static routes depends on the
VPN cluster type (Hub-Spoke or Mesh) and the number of SD-WAN firewalls added to the VPN cluster.
For hub spoke topologies, the  SD-WAN plugin  creates a minimum of two static routes.  In our hub spoke example with one
hub and two branch locations, the SD-WAN plugin creates three static routes on the hub firewall and two static routes on
each of the branch firewalls.  The types of static routes that are automatically created include:
## ●
A default route used to process local DIA traffic and DIA AnyPath failover traffic (if configured)
## ●
One or more static routes used to establish BGP peering with other SD-WAN firewalls (hub or branches)
© 2022 Palo Alto Networks, Inc.PAN-OS SD-WAN Auto Provisioning Primer
## 21

The following two illustrations show the static routes that were automatically created on the us3hub-gcp hub firewall and
one of the branch firewalls.
Hub Firewall- The hub firewall has three static routeswith the first one assigned to the default route (0.0.0.0/0)
using the sdwan.901 interface and a metric of 5.  The second and third static routes are created for each of the
connected branches using the corresponding sdwan.904 and sdwan.905 VIF interfaces, and the destination network
is the branch’s loopback address that is used for BGP peering.  A metric of 10 is assigned to the branch static routes.
Branch Firewall- The branch firewall has two staticroutes with the first one assigned to the default route (0.0.0.0/0)
using the sdwan.901 interface and a metric of 5.  The second static route is assigned to the hub and points to the
hub’s loopback address as the destination.  The hub static route uses the sdwan.904 VIF interface and it is assigned a
metric of 10.
PAN-OS SD-WAN Auto Provisioning Primer© 2022 Palo Alto Networks, Inc.
## 22

BGP Dynamic Routing
The SD-WAN plugin automatically configures BGP routing on each firewall that belongs to the same VPN
cluster.  When the firewall is on-boarded to Panorama and added as an SD-WAN device, the option to
enable and configure the BGP parameters is provided.  When Panorama creates the SD-WAN configuration,
the BGP parameters entered for each firewall are used to configure the firewall’s virtual router and to ensure
BGP peering, routing, and filtering is configured automatically.
This greatly reduces the time and resources needed to deploy PAN-OS SD-WAN, but it also hides a lot of the
routing and SD-WAN configuration - which can make the deployment harder to understand or
troubleshoot if you do not know where the automatic configurations were made..
Warning:The hub spoke network topology introducedin the SD-WAN Deployment Overview
section is referenced frequently in this section.  Please familiarize yourself with the topology
beforehand.
The following illustration recaps the firewalls used to form the hub spoke topology referenced in all example
configurations.  All three devices (one hub and two branches) are members of the “Cluster-US” VPN cluster.
Hub- The hub firewall is named us3hub-gcp and isconfigured to allow DIA AnyPath to failover
internet traffic from the branch firewalls to the hub.  As there is only one hub defined in the VPN
cluster, the Hub Failover Priority doesn’t come into play, so setting any priority level is fine.
Branches- The branch firewalls are named us1-gcpand us2-gcp and connect to the hub named
us3hub-gcp.
© 2022 Palo Alto Networks, Inc.PAN-OS SD-WAN Auto Provisioning Primer
## 23

The following illustration shows the SD-WAN Devices summary screen which lists the hub and both
branches along with their routing and zone information and it’s a fast way to validate the BGP peering
information for the VPN cluster’s firewalls.
As shown in the previous sections, the SD-WAN plugin also configures the static routes and creates the
SD-WAN VIFs to support the DIA traffic and the connections between the hub and two branches.
To set up the VPN cluster’s BGP routing protocol, the SD-WAN plugin automatically configures the
following BGP components.
## ●
Enables BGP routing protocol
## ●
Configures BGP peer group and members
## ●
Configures BGP export and import rules
## ●
Configures BGP redistribution rules
The PAN-OS SD-WAN plugin uses many of the BGP protocol’s default settings and this document points
out the important BGP settings that are required for a successful PAN-OS SD-WAN deployment.  If there is
no mention of a BGP parameter, the default value is used.
Enabling BGP Protocol
For each firewall in the VPN cluster, the SD-WAN plugin enables and configures BGP automatically and no
additional Panorama templates are required to get basic routing set up for SD-WAN.  For advanced
networks and routing requirements, additional Panorama templates can be used to add more functionality.
Warning:Templates that contain overlapping BGP routingobjects are overwritten by the
SD-WAN plugin’s BGP configuration.  For example, if a non-SD-WAN template was used to assign
the ASN to the BGP router and it is a different value from the ASN defined on the SD-WAN plugin’s
Devices setting, it is overwritten when a Panorama push is performed.
PAN-OS SD-WAN Auto Provisioning Primer© 2022 Palo Alto Networks, Inc.
## 24

General Tab:The SD-WAN plugin configures the BGPGeneral Tab with the following settings:
BGP FeatureHub FirewallBranch Firewall
BGPEnabledEnabled
Router IDRetrieved from DevicesRetrieved from Devices
AS NumberRetrieved from DevicesRetrieved from Devices
Install RouteEnabledEnabled
Reject Default RouteEnabledEnabled
Aggregate MEDEnabledEnabled
Deterministic MED ComparisonEnabledEnabled
The following illustration shows the branch firewall’s BGP General configuration and the options that are
enabled.
© 2022 Palo Alto Networks, Inc.PAN-OS SD-WAN Auto Provisioning Primer
## 25

TIP:For existing PAN-OS networks where BGP is already configured, care must be taken
when enabling SD-WAN.  The same Router ID and AS Numbers that you’re already using should be
used for SD-WAN when configuring the firewall in the SD-WAN plugin’s Devices component.
Otherwise, the SD-WAN plugin’s BGP settings override the existing BGP information on the firewall.
For the BGP Advanced tab, the PAN-OS BGP protocol’s default values are used.
Auto Configured BGP Peer Group and Members
The SD-WAN plugin generates the peer group and adds the necessary peers to the configuration based on
the SD-WAN topology selected and the number of SD-WAN devices in the VPN cluster.  The SD-WAN plugin
automatically names the peer group using the serial number of the firewall and any pre-existing BGP peers
are placed in order after the SD-WAN peers.  The following syntax is used in the auto configured peer
groups.
branch_”serial-number-of-peer-device”
TIP:Automatically generated names have a maximumlength.  If the combined name of
“branch_name + serial_number” exceeds the maximum characters, the SD-WAN plugin truncates
the serial number and only uses the last 4 digits.
The illustration below shows an example of the peer groups created on the us3hub-gcp hub firewall and
there are two branch peer groups configured - one for each branch the hub is connected to.
PAN-OS SD-WAN Auto Provisioning Primer© 2022 Palo Alto Networks, Inc.
## 26

Within each peer group, the SD-WAN plugin adds the peer for the firewall to exchange BGP information
with.  The peer name uses the BGP peer’s serial number and the syntax is shown below..
branch_”serial-number-of-peer-device”
Peer Group/Peer Tab:The SD-WAN plugin configuresthe BGP Peer Group and its BGP Peer with the
following settings:
BGP FeatureHub FirewallBranch Firewall
Peer Group NameAuto generatedAuto generated
Peer GroupEnabledEnabled
Remove Private ASEnabledEnabled
Peer NameAuto generatedAuto generated
PeerEnabledEnabled
Peer ASRetrieved from DevicesRetrieved from Devices
Address FamilyIPv4/UnicastIPv4/Unicast
Local Address InterfaceSD-WAN loopback.901SD-WAN loopback.901
Peer Address (IP)Retrieved from DevicesRetrieved from Devices
## Multi Hop6464
The illustrations below show an example of the hub’s peer group and peer created on the us3hub-gcp hub
firewall to connect to the “us2-gcp” branch firewall.
© 2022 Palo Alto Networks, Inc.PAN-OS SD-WAN Auto Provisioning Primer
## 27

As mentioned, the SD-WAN plugin reuses many of the BGP protocol’s default settings to simplify
deployment.  The Multi Hop setting is increased to 64 to account for longer paths with additional hops.
TIP:As a reference, the SD-WAN Interfaces summaryscreen also provides a list of the SD-WAN VIFs
going to each destination and verifies the destination firewall in the comment column.  In the illustration
below, we can see the two branch firewalls the hub is connected to and the corresponding SD-WAN VIF
interfaces and its VPN tunnel VIFs used.
PAN-OS SD-WAN Auto Provisioning Primer© 2022 Palo Alto Networks, Inc.
## 28

Auto Configured BGP Export and Import Rules
To provide the proper exchange of network information from each firewall to its BGP peer, the SD-WAN
plugin automatically creates export and/or import rules on each firewall depending on its role.  Hub firewalls
are configured with an export rule and branch firewalls are configured with an import and export rule.
## Hub Export Rule
The export rule created on the hub firewall is named “default” and includes all branch devices from the VPN
cluster that the hub belongs to.  The illustration below shows the export rule created for the us3hub-gcp
hub firewall in our SD-WAN example topology.
© 2022 Palo Alto Networks, Inc.PAN-OS SD-WAN Auto Provisioning Primer
## 29

The export rule configures a match requirement that matches on a specific community string to correctly
propagate the BGP routes to its SD-WAN peers.  Each SD-WAN peer is assigned a unique community string
which is created from the loopback.901 interface’s IP address, and the action is configured to “Allow” the
export.
## Creating Community Strings
The SD-WAN plugin creates each firewall’s community string from its 32bit IPv4 loopback IP address and it
is displayed as two 16 bit numbers, commonly known as “new format”.
PAN-OS SD-WAN Auto Provisioning Primer© 2022 Palo Alto Networks, Inc.
## 30

## (0 - 65535):(0-65535)
For example, if the loopback IP address is 1.2.3.4, the SD-WAN plugin performs the following translation to
create the community string in decimal representation form.
IPv4 loopback address:1.2.3.4is translated to Hex
Hex representation:0x0102:0x0304is translated to Decimal
Decimal representation:258:772
Branch Import and Export Rules
Branch firewalls are configured with both an import and an export rule to control failover and how its routes
are propagated to its peers.  The import rule controls how the branch fails over between the multiple hubs
defined in the VPN cluster.  A maximum of four hubs can be defined and the Hub Failover Priority creates a
waterfall failover capability between the hubs.  Reference the VPN Cluster section for more information.
The SD-WAN plugin converts the Hub Failover Priority into a BGP local preference value and configures the
branch firewall’s BGP settings accordingly.  When routes are imported from the hubs, the corresponding
local preference is applied to ensure proper failover priority, and the firewall with the highest BGP local
preference value is the preferred hub.
The following translation is applied between the Hub Failover Priority and the BGP local preference value.
Hub Failover PriorityBGP Local Preference
## 1250
## 2200
## 3150
## 4100
TIP:The import rule only applies if the same route(s)are advertised from multiple hub
locations, as “more specific” routes alway win regardless of the local preference applied.
For example, the routes for 10.10.100.0/24 - 10.10.150.0/24 are advertised from two different hub
locations as the hubs are designed to back each other up.  The hub firewall assigned with the Hub
© 2022 Palo Alto Networks, Inc.PAN-OS SD-WAN Auto Provisioning Primer
## 31

Failover Priority of “1” and local preference of “250” becomes the preferred hub location over the hub
firewall assigned with a Hub Failover Priority of “2” and a local preference of “200”.
The SD-WAN plugin names the import rule using the following syntax:
LPREF_”serial-number-of-hub-device”
The following illustration shows the us2-gcp branch firewall’s BGP import rule and the match is performed
on the “us3hub-gcp” hub firewall to apply its corresponding BGP local preference value of “250”.
PAN-OS SD-WAN Auto Provisioning Primer© 2022 Palo Alto Networks, Inc.
## 32

The SD-WAN plugin also creates a BGP export rule on the branch firewall that controls the networks
advertised to its peers.  Like the hub’s export rule, the branch’s export rule is also named “default” and it
matches on a specific community string for the peer firewall and the “Allow” action enables BGP to export
the networks.  The number of export rules created for the branch firewall depends on the VPN cluster
topology and the number of hub and branch members.
Auto Configured BGP Redistribution Rules
The SD-WAN plugin automatically creates BGP redistribution rules on the hub and branch firewalls to
control the exchange of route information between the VPN cluster firewalls.  The number of redistribution
rules created depends on the SD-WAN firewall role - either a hub or a branch.
## Hub Redistribution Rule
The hub firewall is configured with a BGP redistribution rule that includes all networks defined on the hub’s
Devices “Prefix(es) to Redistribute” configuration.  The illustration below shows the network prefixes that are
redistributed from the hub to the branches.
The SD-WAN plugin also appends the unique community string to the redistribution rule that matches the
export rule and this completes the configuration to allow the firewall to propagate its network prefixes to
the corresponding peer firewalls.  The illustration below shows the us3hub-gcp hub firewall’s BGP
redistribution rule and it also highlights the “Allow Redistribute Default Route” checkbox’s disabled setting,
which gives the SD-WAN plugin control to configure the default route using the sdwan-901 VIF.
© 2022 Palo Alto Networks, Inc.PAN-OS SD-WAN Auto Provisioning Primer
## 33

The illustration below show the us3hub-gcp hub firewall’s 192.168.0.0/16 redistribution rule in greater detail
and the auto generated community string that matches the hub’s BGP export rule.
## Branch Redistribution Rules
The branch firewalls are configured with two BGP redistribution rules.  The first rule is designed to advertise
the branch firewall’s connected routes to all other peer locations.  The following illustration shows the
PAN-OS SD-WAN Auto Provisioning Primer© 2022 Palo Alto Networks, Inc.
## 34

us2-gcp branch firewall’s “connected” redistribution profile created by the SD-WAN plugin.  A default priority
of “10” is assigned.
The next two illustrations show how the SD-WAN plugin applies the redistribution profile to the branch
firewall’s BGP Redistribution Rule tab and how the auto generated community strings are matched with
the export rule.
© 2022 Palo Alto Networks, Inc.PAN-OS SD-WAN Auto Provisioning Primer
## 35

The second redistribution rule, named “rd_bgp_block”, is designed to exclude the branch firewall’s SD-WAN
interfaces from being advertised to the other sites.  The SD-WAN plugin assigns this rule a priority of “1” to
give it priority over the previous redistribution rule and ensure it’s evaluated first.
The illustration below shows rd_bgp_block redistribution profile with the “No Redist” option selected to
block the redistribution.  All Ethernet interfaces that are enabled with SD-WAN are added to the profile
automatically by the SD-WAN plugin.
PAN-OS SD-WAN Auto Provisioning Primer© 2022 Palo Alto Networks, Inc.
## 36

The SD-WAN plugin adds the rd_bgp_block redistribution profile to the branch firewall’s BGP redistribution
rules to complete the configuration.
TIP:If changes are made to the SD-WAN plugin’s Devicesor VPN Clusters components,
Panorama performs a template commit to all firewall members in the VPN cluster.
## Summary
This paper shows the power of the Panorama SD-WAN plugin and how it greatly simplifies the
configuration of many SD-WAN components on both the hub and branch firewalls.  By auto configuring
many tedious and complex settings, the plugin helps to eliminate configuration error and makes easy work
of rolling out a new SD-WAN topology.
For more information on SD-WAN concepts, administration guides, and technical papers, please visit the
following links:
## ●
PAN-OS Administration Guide
## ●
PAN-OS SD-WAN TechDocs
## ●
Panorama TechDocs
© 2022 Palo Alto Networks, Inc.PAN-OS SD-WAN Auto Provisioning Primer
## 37