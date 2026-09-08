SD-WAN Administration
docs.paloaltonetworks.com
Contact Information
Corporate Headquarters:
Palo Alto Networks
3000 Tannery Way
Santa Clara, CA 95054
www.paloaltonetworks.com/company/contact-support
About the Documentation
• For the most recent version of this guide or for access to related documentation, visit the Technical
Documentation portal docs.paloaltonetworks.com.
• To search for a specific topic, go to our search page docs.paloaltonetworks.com/search.html.
• Have feedback or questions for us? Leave a comment on any page in the portal, or write to us at
documentation@paloaltonetworks.com.
Copyright
Palo Alto Networks, Inc.
www.paloaltonetworks.com
© 2024-2025 Palo Alto Networks, Inc. Palo Alto Networks is a registered trademark of Palo
Alto Networks. A list of our trademarks can be found at www.paloaltonetworks.com/company/
trademarks.html. All other marks mentioned herein may be trademarks of their respective companies.
Last Revised
November 10, 2025
SD-WAN Administration 2 ©2026 Palo Alto Networks, Inc.
Table of Contents
SD-WAN Deployment Workflow.................................................................. 5
Set Up SD-WAN.............................................................................................................. 7
Configure SD-WAN......................................................................................................... 8
Configure Interfaces for SD-WAN.............................................................. 13
Define Link Tag for SD-WAN Application Steering......................................................... 14
Define Your ISP Connections and Link Types................................................................... 16
Configure Ethernet Interface for SD-WAN........................................................................ 24
Configure an Aggregate Ethernet Interface and Subinterfaces for Link
Redundancy.................................................................................................................................35
Segment SD-WAN Traffic using VLAN Tags..................................................................... 42
Enable SD-WAN with Auto VPN.................................................................49
Add SD-WAN Branch or Hub Firewall................................................................................ 50
Configure Certificate-based Authentication for Strong Security...................................65
Quickly Add Multiple SD-WAN Devices with Bulk Import.............................................70
Configure SD-WAN Devices in HA Mode..........................................................................75
Onboard PAN-OS Firewalls to Prisma Access for Cloud-based Security.................... 78
Plan Your Topology for SD-WAN with Auto VPN........................................................... 91
Create a Full Mesh VPN Cluster with DDNS Service....................................................106
Enable SD-WAN without Auto VPN........................................................111
Configure a Virtual SD-WAN Interface.............................................................................112
Create a Default Route to the SD-WAN Interface........................................................ 115
Manage SD-WAN Link Failovers........................................................................................ 117
Define Your Custom SD-WAN Application Thresholds.....................................117
Monitor SaaS Applications Using SD-WAN......................................................... 121
SD-WAN Traffic Distribution Profiles....................................................................134
Define Path Selection for SD-WAN Traffic..........................................................140
Recover Corrupted or Lost Data to Improve Reliability.................................... 144
SD-WAN Traffic Steering Using Policy Rules........................................ 149
Define Your Application-based Traffic Steering Policies.............................................. 150
Distribute Sessions Not Matching SD-WAN Policy Rules............................................156
Configure Direct Internet Access..............................................................159
Allow Direct Internet Access Traffic Failover to MPLS Link........................................160
Backhaul Your Internet Traffic to SD-WAN Hub........................................................... 161
Create a Static Route for SD-WAN..........................................................169
SD-WAN Administration 3 ©2026 Palo Alto Networks, Inc.
Table of Contents
Configure Advanced Routing for SD-WAN............................................ 171
Enable Segmentation with Multiple Virtual Routers for Overlapping
Subnets.............................................................................................................177
Configure Multiple Virtual Routers on SD-WAN Hub...................................................179
Configure Multiple Virtual Routers on SD-WAN Branch............................................. 182
Monitoring and Reporting...........................................................................187
Monitor SD-WAN Tasks....................................................................................................... 188
Monitor SD-WAN Application and Link Performance...................................................189
Baseline Your Prisma Access Hub Application and Link Performance.......................194
Monitor Prisma Access Hub Application and Link Performance.................................196
Generate an SD-WAN Report.............................................................................................200
Troubleshooting............................................................................................. 203
Troubleshoot App Performance..........................................................................................211
Troubleshoot Link Performance..........................................................................................216
Troubleshoot KeyID Mismatch............................................................................................221
Troubleshoot Pre-Shared Key Mismatch..........................................................................225
SD-WAN Administration 4 ©2026 Palo Alto Networks, Inc.
SD-WAN Deployment Workflow
Where Can I Use This? What Do I Need?
```
• NGFW (Managed by PAN-OS or
```
```
Panorama)
```
```
• NGFW (Managed by Strata Cloud
```
```
Manager)
```
Advanced SD-WAN for NGFW
One of these:
AIOps for NGFW Premium or Strata
Cloud Manager Pro
Strata Cloud Manager Essentials
```
(Supports only NGFWs)
```
```
(Panorama Only) Key SD-WAN deployment steps:
```
After you plan your SD-WAN configuration, install the SD-WAN plugin and set up the
Panorama™ management server to centrally manage the SD-WAN configuration of your hub and
branch firewalls. By leveraging Panorama, you reduce management requirements and operational
overhead for administering your SD-WAN deployment and can more easily monitor link health
and troubleshoot issues should they arise.
• Plan the SD-WAN architecture and install the necessary plugin. Acquire the Advanced SD-
```
WAN license and validate SD-WAN interface setup on vsys1 (for multi-vsys firewalls).
```
• Onboard firewalls to Panorama and define base templates and device groups: Configure
link tags, SD-WAN interface profiles, and traffic distribution/path quality profiles. Establish
```
required security zones (internal, branch, hub) and define SD-WAN policy rules.
```
• Configure the interfaces, SD-WAN policy rules, and SD-WAN link management profiles.
```
• Add firewalls as hub or branch devices and a VPN Cluster to define the topology (hub-and-
```
```
spoke or mesh).
```
```
(Strata Cloud Manager Only) Key SD-WAN deployment steps:
```
• Plan the SD-WAN architecture. You do not need to install any plugin if you are using the Strata
Cloud Manager. Acquire the Advanced SD-WAN license and validate SD-WAN interface setup
```
on vsys1 (for multi-vsys firewalls).
```
• Enable Cloud Management and onboard/activate firewalls and licenses using Strata Cloud
Manager.
• Organize firewalls into separate hubs and branch folders/snippets.
• The SD-WAN plugin will automatically create the zones.
• Configure the interfaces, SD-WAN policy rules, BGP distribution profiles, SD-WAN link
management profiles, and VPN Cluster.
5
SD-WAN Deployment Workflow
• If Panorama or Strata Cloud Manager is managing a multi-vsys firewall, all SD-WAN
enabled interfaces and configurations must be configured on vsys1.
• SD-WAN does not support an SD-WAN configuration across multiple virtual systems
of a multi-vsys firewall.
• You need an Advanced SD-WAN license to enable the SD-WAN feature in the Palo
Alto Networks firewalls.
• PAN-OS & Panorama
• Strata Cloud Manager
SD-WAN Administration 6 ©2026 Palo Alto Networks, Inc.
SD-WAN Deployment Workflow
Strata Cloud Manager
Contact your account team to enable Cloud Management for NGFWs using Strata
Cloud Manager.
Set Up SD-WAN
```
Set up a Software-Defined Wide Area Network (SD-WAN) on Strata Cloud Manager for your Palo
```
```
Alto Networks Next-Gen Firewalls (NGFW).
```
STEP 1 | Log in to Strata Cloud Manager.
STEP 2 | Onboard your SD-WAN firewalls to Strata Cloud Manager.
All newly added firewalls are added the All Firewalls folder by default.
STEP 3 | Activate the SD-WAN license on your firewall.
STEP 4 | Create the SD-WAN folders for hub and branch firewalls.
Separate folders for your hub and branch firewalls are required to containing all SD-WAN
configuration objects specific to hub and branch firewall deployments.
1. Select System Settings > Folder Management and Add Folder.
Add new folders for your hub and branch SD-WAN firewalls.
2. In Folder Management, locate your hub and branch firewalls and expand the Actions
menu to Move your firewalls.
For the Destination, select the hub or branch folder you created and Move.
```
STEP 5 | Create zone-internal, zone-to-branch, and zone-to-hub security zones (case sensitive). The
```
SD-WAN plugin will create these zones, but the best practice is to preprovision these zones
```
so they can be added to existing Security policy rules (prior to SD-WAN transition). Every
```
transport or interface participating in SD-WAN needs to be in the same security zone.
STEP 6 | Create link tags.
Create a link tag to identify one or more physical links that you want applications and services
to use in a specific ordering during SD-WAN traffic distribution and failover protection.
Grouping multiple physical links allows you to maximize the application service quality if the
physical link health deteriorates.
1. Select Configuration > NGFW and Prisma Access > Network Policies > SD-WAN Policy
> Link Tags and create your link tags at the All Firewalls Context Scope.
Palo Alto Networks recommends creating all link tags at the All Firewalls
folder level to ensure link tags are available to all SD-WAN firewalls regardless
of the folder they’re associated with.
2. Add Tag.
3. Enter a Name and select a Color to identify the link tag.
4. Save.
SD-WAN Administration 7 ©2026 Palo Alto Networks, Inc.
SD-WAN Deployment Workflow
Configure SD-WAN
Contact your account team to enable Cloud Management for NGFWs using Strata
Cloud Manager.
Configure the physical Ethernet interfaces and SD-WAN interface profile to enable SD-WAN
functionality and define the characteristics of the ISP connections the firewall monitors.
Additionally, you must create the SD-WAN VPN cluster to determine which branches
communicate with which hubs and to create a secure connection between the branch and hub
firewalls.
STEP 1 | Log in to Strata Cloud Manager.
STEP 2 | Set up SD-WAN.
STEP 3 | Configure a layer 3 interface.
Layer 3 interfaces are required for SD-WAN functionality. Repeat this step to configure as
many Layer 3 Ethernet interfaces on your SD-WAN firewall as needed.
You can configure up to four IP addresses for an SD-WAN enabled interface. The Auto VPN
workflows uses only the first IP address from the configured IPv4 address list to create the
VPN tunnel and ignores the remaining IPv4 addresses in the list.
STEP 4 | Configure a logical router and add the interfaces that you created in the previous step to the
logical router.
```
STEP 5 | (Optional) Configure a BGP redistribution profile.
```
STEP 6 | Configure an SD-WAN interface profile.
The SD-WAN interface profile defines the characteristics of the ISP connection, specifies
the speed of links and how frequently the firewall monitors the link, and specifies the link
SD-WAN Administration 8 ©2026 Palo Alto Networks, Inc.
SD-WAN Deployment Workflow
```
tag. When you specify the same Link Tag on multiple links, you’re grouping (bundling) those
```
physical links into a link bundle or fat pipe.
1. Select Configuration > NGFW and Prisma Access > Network Policies > SD-WAN Policy
> Profiles > SD-WAN Interface and select the hub or branch folder where want to
create the SD-WAN interface profile.
2. Add Profile.
3. Enter a descriptive Name for the profile.
4. Select the Link Tag the profile assigns to the interface.
5. Select the Link Type from the predefined list.
6. Specify the Maximum Download (Mbps) speed from the ISP.
7. Specify the Maximum Upload (Mbps) speed to the ISP.
8. Check (enable Eligible for Error Correction Profile Interface Selection to enable Forward
```
Error Correction (FEC) or packet duplication for interfaces.
```
If enabled, you must enable this setting for both sending and receiving firewalls.
9. VPN Data Tunnel Support determines whether the branch-to-hub traffic and return
traffic flows through a VPN tunnel for added security or flows outside of the VPN tunnel
to avoid encryption overhead. This setting is enabled by default.
• Keep enabled for public links that have direct internet connections or internet break
capabilities, such as cable modem, ADSL, and other internet connections.
• Disable for private link types such as MPLS, satellite, or microwave that doesn’t have
internet breakout capability. However, you must first ensure that the traffic can’t be
intercepted because it will be sent outside of the VPN tunnel.
• The branch might have DIA traffic that needs to fail over to the private MPLS link
connecting to the hub, and reach the internet from the hub. The VPN Data Tunnel
Support setting determines whether the private data flows through the VPN tunnel
```
or flows outside the tunnel, and the failed over traffic uses the other connection (that
```
```
the private data flow doesn’t use). The firewall uses zones to segment DIA failover
```
traffic from private MPLS traffic.
10. Set the VPN Failover Metric if DIA AnyPath is enabled a hub or branch firewall, to
prioritize the order in which a particular hub is selected for failover.
The lower the metric, the higher the priority of the interface to be selected during
failover. If multiple hub virtual interfaces have the same metric value, SD-WAN sends
new session traffic to them in round-robin fashion.
11. Select the Path Monitoring mode.
• Aggressive—Firewall sends probe packets to the opposite end of the SD-WAN link
at a constant frequency. Use this mode if you need fast detection and failover for
brownout and blackout conditions. Default for all link types except LTE and Satellite.
```
• Relaxed—Firewall waits for a number of seconds (Probe Idle Time) between sending
```
sets of probe packets, making path monitoring less frequent. When the probe idle
time expires, firewall sends probes for 7 seconds at the Probe Frequency configured.
```
Use this mode when you have low-bandwidth links, links that charge by usage (such
```
SD-WAN Administration 9 ©2026 Palo Alto Networks, Inc.
SD-WAN Deployment Workflow
```
as LTE), or when fast detection isn’t as important as preserving cost and bandwidth.
```
Default for LTE and Satellite link types.
12. Set the Probe Frequency (per second) to specify the number of times per second the
firewall sends a probe packet to the opposite end of the SD-WAN link. The default
setting provides subsecond detection of brownout and blackout conditions.
13. Set the Probe Idle Time (seconds) to specify how long the firewall waits between sets of
probe packets.
14. Set the Failback Hold Time (seconds) to specify how long the firewall waits for a
recovered link to remain qualified before the firewall reinstates the link after it has failed.
15. Save.
STEP 7 | Configure a VPN cluster for your hub and branch firewalls.
1. Select Configuration > NGFW and Prisma Access > Setup > Auto VPN and Add VPN
Cluster.
2. Check (enable) SD-WAN.
3. Add the hub firewalls to the VPN cluster.
1. Add Hub Devices to select one or more firewalls to Add as hubs.
Up to four hubs are supported for a VPN cluster.
2. Click the firewall in the Hub Devices list.
3. Set the hub firewall Priority.
Range is 1 to 4. The lower the priority value, the higher the priority and local
preference. A cluster supports a maximum of four hubs. An active/passive HA pair
```
counts as one hub. Multiple hubs can have the same priority; an HA pair must have
```
the same priority.
4. Select a Logical Router.
5. (Optional) Check (enable) DIA VPN and select a DIA VPN Link Tag.
6. Update.
7. Repeat this step for all hub firewalls that you add to the VPN cluster.
4. Add the branch firewalls to the VPN cluster.
1. Add Hub Devices to select one or more firewalls to Add as hubs.
2. Select a Logical Router.
3. (Optional) Select a BGP Redistribution Profile.
4. Update.
5. Repeat this step for all branch firewalls that you add to the VPN cluster.
STEP 8 | Create SD-WAN link management profiles.
SD-WAN Administration 10 ©2026 Palo Alto Networks, Inc.
SD-WAN Deployment Workflow
PAN-OS & Panorama
The following list is a preview of the configuration tasks you need to perform to prepare for
your SD-WAN deployment. The detailed steps for you to take to accomplish each task appear in
subsequent task topics.
STEP 1 | Onboard the firewall to the Panorama management server either manually or using ZTP.
Create basic device groups and templates.
STEP 2 | Create link tags. Link tags enable you to identify common link types and link it with the SD-
WAN interface profiles. They are free form entries that are referenced in multiple locations.
Be consistent and meaningful when creating the link tags.
STEP 3 | Create an SD-WAN interface profile to define the link type, link tag, upload and download
```
bandwidth speed of the link, and path monitoring link types (aggressive or relaxed).
```
```
STEP 4 | Enable SD-WAN in Ethernet, sub Ethernet, and Aggregated Ethernet Interfaces; then add
```
the next hop gateway and apply the SD-WAN interface profile.
STEP 5 | As part of your SD-WAN policy, you use SD-WAN traffic distribution profiles to assign
which traffic distribution method the path-selection algorithm uses for an application. The
path-selection algorithm uses the path metrics, thresholds, and sensitivities as defined in a
path quality profile.
```
STEP 6 | (Optional) Each SD-WAN path quality profile (PQP) consists of a set of ranked metrics and
```
thresholds that an application requires for optimal performance. There are predefined PQPs
or you can also create custom PQPs.
```
STEP 7 | Create zone-internal, zone-to-branch, and zone-to-hub security zones (case sensitive). The
```
SD-WAN plugin will create these zones, but the best practice is to preprovision these zones
```
so they can be added to existing Security policy rules (prior to SD-WAN transition). Every
```
transport or interface participating in SD-WAN needs to be in the same security zone.
STEP 8 | Define the SD-WAN policy rules. SD-WAN policies are similar to security policy rules. You
can also apply Path Quality Profiles and Traffic Distribution Profiles in the SD-WAN policy
rules.
1. After completing the above steps, follow this workflow to complete your SD-WAN deployment
using the SD-WAN plugin.
STEP 9 | Add the Palo Alto Networks firewall as an SD-WAN hub or a branch device to the SD-WAN
plugin.
```
STEP 10 | Create a VPN Cluster with the appropriate cluster type (hub and spoke or mesh) based
```
on your network topology requirement. Then add the branches and hubs to your selected
topology.
SD-WAN Administration 11 ©2026 Palo Alto Networks, Inc.
SD-WAN Deployment Workflow
SD-WAN Administration 12 ©2026 Palo Alto Networks, Inc.
Configure Interfaces for SD-WAN
Where Can I Use This? What Do I Need?
• NGFW Advanced SD-WAN for NGFW
Configuring physical Ethernet interfaces is essential for enabling SD-WAN functionality on your
Palo Alto Networks firewall. The physical interfaces serve as the connection points for your
WAN links, such as internet, MPLS, or LTE connections. When you configure these interfaces for
SD-WAN, you're defining the characteristics of each ISP connection, including link type, speed,
and monitoring parameters. This allows the firewall to accurately assess the performance and
availability of each link.
Physical interfaces are configured as Layer 3 interfaces and are essential components of the SD-
WAN setup. Physical interfaces form the foundation for establishing connections to different
ISP links and play a crucial role in implementing the SD-WAN architecture for optimizing traffic
routing across multiple WAN connections.
```
(Panorama) You configure these physical interfaces with IP addresses, add them to virtual routers
```
```
or logical routers (SD-WAN plugin 3.1.0 and later versions), and associate them with SD-WAN
```
interface profiles to enable SD-WAN functionality.
By setting up Layer 3 interfaces and associating them with SD-WAN interface profiles, you're
providing the firewall with the necessary information to make intelligent routing decisions. The
SD-WAN interface profile defines crucial parameters like Link Tag, which is used for grouping
interfaces into link bundles, and path monitoring settings that determine how quickly the firewall
can detect and respond to link degradation or failure.
These configured physical interfaces become the foundation upon which you build your SD-WAN
policy rules, allowing you to optimize traffic flow, implement failover strategies, and ensure that
your critical applications always have the best possible path to their destination.
13
Configure Interfaces for SD-WAN
Define Link Tag for SD-WAN Application Steering
Where Can I Use This? What Do I Need?
• NGFW Advanced SD-WAN for NGFW
Create a link tag to identify one or more physical links that you want applications and services
to use in a specific order during SD-WAN traffic distribution and failover protection. Grouping
multiple physical links allows you to maximize the application and service quality if the physical
link health deteriorates.
When planning how to group your links, consider the use or purpose of the links and group them
accordingly. For example, if you are configuring links intended for low-cost or non-business-
critical traffic, create a link tag and group these interfaces together to ensure that the intended
traffic flows primarily on these links, and not on more expensive links that may impact business-
critical applications or services.
STEP 1 | Log in to the Panorama Web Interface.
STEP 2 | Select Objects > Tags and select the appropriate device group from the Device Group
context drop-down.
STEP 3 | Add a new tag.
```
STEP 4 | Enter a descriptive Name for the tag. For example; Low Cost Paths, Expensive Paths, General
```
Access, Private HQ, or Backup.
```
STEP 5 | Enable (check) Shared to make the Link Tag available to all device groups on the Panorama®
```
management server and to the default vsys on a single vsys hub or branch, or to vsys1 on
any multi-vsys hub or branch that you push to.
By configuring a Shared Link Tag, Panorama is able to reference the Link Tags in the firewall
configuration validation and successfully commits and pushes the configuration to branches
and hubs. The commit fails if Panorama is unable to reference a Link Tag.
```
STEP 6 | (Optional) Select a Color for the tag.
```
STEP 7 | Enter helpful Comments about the tag. For example, Group two low cost broadband
links and a backup link for general access to the internet.
STEP 8 | Click OK to save your configuration changes.
STEP 9 | Commit and Commit and Push your configuration changes.
SD-WAN Administration 14 ©2026 Palo Alto Networks, Inc.
Configure Interfaces for SD-WAN
STEP 10 | Define your ISP connections and link types.
SD-WAN Administration 15 ©2026 Palo Alto Networks, Inc.
Configure Interfaces for SD-WAN
Define Your ISP Connections and Link Types
Where Can I Use This? What Do I Need?
```
• NGFW (Managed by PAN-OS or
```
```
Panorama)
```
```
• NGFW (Managed by Strata Cloud
```
```
Manager)
```
Advanced SD-WAN for NGFW
One of these:
AIOps for NGFW Premium or Strata
Cloud Manager Pro
Strata Cloud Manager Essentials
```
(Supports only NGFWs)
```
Create an SD-WAN interface profile to define the characteristics of ISP connections and to
specify the speed of links and how frequently the firewall monitors the link, and specify a link tag
for the link.
SD-WAN link tags group multiple links together that is called link bundling or scaling. Link tags are
used to identify common link types and links in SD-WAN interface profiles. They are free form
entries that are referenced in multiple locations. Be consistent and meaningful when creating the
link tags.
The tag enables you to control the order in which the interfaces are used and systematically
configure multiple interfaces with SD-WAN functionality.
```
When you specify the same Link Tag on multiple links, you are grouping (bundling) those physical
```
links into a link bundle or fat pipe. You must configure an SD-WAN interface profile and specify it
for an Ethernet interface enabled with SD-WAN before you can save the Ethernet interface.
Group links based on a Common Criterion. For example, group links by path preference
from most preferred to least preferred, or group links by cost.
SD-WAN interface profiles map tags to interfaces, and helps to set bandwidths and probe rates.
```
They also identify whether a transport is private (such as MPLS), or public (such as Ethernet,
```
```
ADSL, Cable).
```
• PAN-OS & Panorama
• Strata Cloud Manager
PAN-OS & Panorama
STEP 1 | Log in to the Panorama Web Interface.
STEP 2 | Select Network > Network Profiles > SD-WAN Interface Profile and select the appropriate
template from the Template context drop-down.
STEP 3 | Add an SD-WAN interface profile.
STEP 4 | Enter a user-friendly Name for the SD-WAN interface profile, which you’ll see in reporting,
troubleshooting, and statistics.
SD-WAN Administration 16 ©2026 Palo Alto Networks, Inc.
Configure Interfaces for SD-WAN
STEP 5 | Select the vsys Location if you have a multi-vsys Panorama™ management server. By
default, vsys1 is selected.
STEP 6 | Select the Link Tag that this profile will assign to the interface.
STEP 7 | Add a Description for the profile.
```
STEP 8 | Select the physical Link Type from the predefined list (ADSL/DSL, Cable modem, Ethernet,
```
Fiber, LTE/3G/4G/5G, MPLS, Microwave/Radio, Satellite, WiFi, Private Link1, Private
```
Link2, Private Link3, Private Link4, or Other). (Beginning with PAN-OS 11.0.4, SD-WAN
```
```
plugin 3.1.3 and later 3.1 releases) (PAN-OS 11.1.3, SD-WAN plugin 3.2.1 and later releases)
```
We support the additional point-to-point private link types such as, Private Link1, Private
Link2, Private Link3, and Private Link4. We do not support plain text traffic from SD-WAN
branch firewall to SD-WAN hub firewall for Private Link1, Private Link2, Private Link3, and
Private Link4 link types. When you configure any of the new private link types, ensure that
you have an SD-WAN policy rule on the hub that is configured only with public link type.
Because when the internet-bound traffic backhauls or fails to the hub from the branch, it
must match with this SD-WAN policy rule. Otherwise, the traffic gets dropped as these
SD-WAN Administration 17 ©2026 Palo Alto Networks, Inc.
Configure Interfaces for SD-WAN
```
private links (Private Link1, Private Link2, Private Link3, and Private Link4) are part of the
```
```
direct internet access (DIA) SD-WAN interface.
```
```
(For PAN-OS 11.0.4 and later releases, SD-WAN plugin 3.1.3 and later releases) To
```
enable the additional point-to-point private link types, you must ensure the following:
• Panorama Management Server should be running on PAN-OS 11.0.4
• Panorama managed devices must be running on PAN-OS 11.0.4
• SD-WAN plugin version must be 3.1.3
```
(For PAN-OS 11.1.3 and later releases, SD-WAN plugin 3.2.1 and later releases) To
```
enable the additional point-to-point private link types, you must ensure the following:
• Panorama Management Server should be running on PAN-OS 11.1.3
• Panorama managed devices must be running on PAN-OS 11.1.3
• SD-WAN plugin version must be 3.2.1
```
(For PAN-OS 11.2.0 and later releases, SD-WAN plugin 3.3.0 and later releases ) To
```
enable the additional point-to-point private link types, you must ensure the following:
• Panorama Management Server should be running on PAN-OS 11.2.0
• Panorama managed devices must be running on PAN-OS 11.2.0
• SD-WAN plugin version must be 3.3.0
The firewall can support any CPE device that terminates and hands off as an Ethernet
```
connection to the firewall; for example, WiFi access points, LTE modems, laser/microwave
```
CPEs all can terminate with an Ethernet handoff.
The following link types will form tunnels with only the same link type:
```
• Public (or Other) link types—Ethernet, ASDL/DSL, Cable modem, Fiber,
```
LTE/3G/4G/5G, WiFi, and Other.
Any public link type to any other public link type will create a tunnel successfully.
For example, Ethernet-to-Other and Other-to-Other link types will create the
tunnels successfully.
• Private and Point-to-Point link types—MPLS, Satellite, Private Link1, Private Link2,
Private Link3, Private Link4, and Microwave/Radio.
A private link type can create the tunnel only with the same private link type. For
example, MPLS-to-MPLS and satellite-to-satellite link types are valid and therefore
the tunnels will be created successfully, but MPLS-to-satellite won't create the
tunnel.
SD-WAN Administration 18 ©2026 Palo Alto Networks, Inc.
Configure Interfaces for SD-WAN
```
(SD-WAN plugin 2.0 and later versions) For existing PAN-OS deployments that have
```
zones defined on the interfaces that will be used to support SD-WAN, Panorama may
automatically configure the interface’s zone name to one of the predefined SD-WAN
zones under the following conditions:
1. The SD-WAN interface is configured as a point-to-point private Link Type (MPLS,
```
Satellite, or Microwave) in its Interface Profile.
```
2. The VPN Data Tunnel Support checkbox is disabled (unchecked) on the SD-WAN
Interface Profile. This instructs PAN-OS to forward traffic in clear text outside of
the SD-WAN VPN tunnel. Because Private Link1, Private Link2, Private Link3,
and Private Link4 link types don't support plain text traffic from SD-WAN branch
firewall to SD-WAN hub firewall, you must leave VPN Data Tunnel Support option
enabled when you configure these private link types.
```
(SD-WAN plugin 2.0 and later versions) On the Hub firewall, the zone name is configured
```
```
as “zone-to-branch” when condition a) is met. On the Branch firewall, the zone name is
```
```
configured as “zone-to-hub” when both condition a) and condition b) are met. Panorama
```
automates this step to simplify configuration to ensure proper communication between the
hub and branch firewalls. If you have preexisting firewall policies that reference the old zone
name, you must update the policies to reflect the new predefined SD-WAN zone name.
```
STEP 9 | Specify the Maximum Download (Mbps) speed from the ISP in megabits per second (range
```
```
is 0 to 100,000; default is 1gbps). You can enter a range using up to three decimal places, for
```
example, 10.456. Ask your ISP for the link speed or sample the link’s maximum speeds with a
tool such as speedtest.net and take an average of the maximums over a good length of time.
```
STEP 10 | Specify the Maximum Upload (Mbps) speed to the ISP in megabits per second (range is 0
```
```
to 100,000; default is 1gbps). You can enter a range using up to three decimal places, for
```
example, 10.456. Ask your ISP for the link speed or sample the link’s maximum speeds with a
tool such as speedtest.net and take an average of the maximums over a good length of time.
SD-WAN Administration 19 ©2026 Palo Alto Networks, Inc.
Configure Interfaces for SD-WAN
```
STEP 11 | Specify the Tunnel Maximum Download (Mbps) speed from the ISP in megabits per second
```
```
(range is 0 to 100,000; default is 1gbps). You can enter a range using up to three decimal
```
places, for example, 10.456. Ask your ISP for the link speed or sample the link’s maximum
speeds with a tool such as speedtest.net and take an average of the maximums over a good
length of time.
```
STEP 12 | Specify the Tunnel Maximum Upload (Mbps) speed to the ISP in megabits per second (range
```
```
is 0 to 100,000; default is 1gbps). You can enter a range using up to three decimal places, for
```
example, 10.456. Ask your ISP for the link speed or sample the link’s maximum speeds with a
tool such as speedtest.net and take an average of the maximums over a good length of time.
```
STEP 13 | (SD-WAN plugin 2.0 and later versions) Select Eligible for Error Correction Profile interface
```
```
selection to enable Forward Error Correction (FEC) or packet duplication for interfaces. You
```
```
must enable this on both the encoding and decoding firewalls; you must also create an error
```
correction profile to apply to the SD-WAN policy rule for specific applications.
```
STEP 14 | (PAN-OS 9.1.2 and later versions) VPN Data Tunnel Support determines whether the
```
```
branch-to-hub traffic and return traffic flows through a VPN tunnel for added security (the
```
```
default method) or flows outside of the VPN tunnel to avoid encryption overhead.
```
• Leave VPN Data Tunnel Support enabled for public link types that have direct internet
connections or internet breakout capability, such as cable modem, ADSL, and other internet
connections.
• You can disable VPN Data Tunnel Support for private link types such as MPLS, satellite,
or microwave that do not have internet breakout capability except Private Link1, Private
Link2, Private Link3, and Private Link4 link types. However, you must first ensure the
traffic cannot be intercepted because it will be sent outside of the VPN tunnel.
```
• (SD-WAN plugin 3.1.3 and later releases) Because Private Link1, Private Link2, Private
```
Link3, and Private Link4 link types don't support plain text traffic from SD-WAN branch
firewall to SD-WAN hub firewall, you must leave VPN Data Tunnel Support enabled when
you configure these private link types.
• The branch may have DIA traffic that needs to fail over to the private MPLS link connecting
to the hub, and reach the internet from the hub. The VPN Data Tunnel Support setting
determines whether the private data flows through the VPN tunnel or flows outside the
```
tunnel, and the failed over traffic uses the other connection (that the private data flow
```
```
doesn’t use). The firewall uses zones to segment DIA failover traffic from private MPLS
```
traffic.
```
STEP 15 | (PAN-OS 10.0.3 and later versions) If you configure DIA AnyPath, a principal virtual interface
```
can have multiple hub virtual interfaces, so you must prioritize the order in which a particular
hub is selected for failover. Specify such priority by setting the VPN Failover Metric for the
VPN tunnels bundled in the hub virtual interface where this profile is applied. The lower the
metric, the higher the priority of the interface to be selected during failover. If multiple hub
SD-WAN Administration 20 ©2026 Palo Alto Networks, Inc.
Configure Interfaces for SD-WAN
virtual interfaces have the same metric value, SD-WAN sends new session traffic to them in
round-robin fashion.
```
STEP 16 | (Optional) Select the Path Monitoring mode in which the firewall monitors the interfaces
```
where you apply this SD-WAN Interface Profile.
The firewall selects what it considers the best monitoring method based on Link Type.
```
Retain the default setting for the link type unless an interface (where you apply this
```
```
profile) has issues that require more aggressive or more relaxed path monitoring.
```
```
• Aggressive—(Default for all link types except LTE and Satellite) Firewall sends probe
```
packets to the opposite end of the SD-WAN link at a constant frequency. Use this mode if
you need fast detection and failover for brownout and blackout conditions.
```
• Relaxed—(Default for LTE and Satellite link types) Firewall waits for a number of seconds
```
```
(the Probe Idle Time) between sending sets of probe packets, making path monitoring less
```
frequent. When the probe idle time expires, firewall sends probes for seven seconds at the
Probe Frequency configured. Use this mode when you have low bandwidth links, links that
```
charge by usage (such as LTE), or when fast detection isn’t as important as preserving cost
```
and bandwidth.
```
STEP 17 | Set the Probe Frequency (per second), which is the number of times per second that the
```
```
firewall sends a probe packet to the opposite end of the SD-WAN link (range is 1 to 5;
```
```
default is 5). The default setting provides subsecond detection of brownout and blackout
```
conditions.
If you change the Probe Frequency for a Panorama template, you should also adjust
the Packet Loss percentage threshold in a Path Quality profile for a Panorama device
group.
```
STEP 18 | If you select Relaxed path monitoring, you can set the Probe Idle Time (seconds) that the
```
```
firewall waits between sets of probe packets (range is 1 to 60; default is 60).
```
SD-WAN Administration 21 ©2026 Palo Alto Networks, Inc.
Configure Interfaces for SD-WAN
```
STEP 19 | Enter the Failback Hold Time (seconds) that the firewall waits for a recovered link to remain
```
qualified before the firewall reinstates that link as the preferred link after it has failed over
```
(range is 20 to 120; default is 120).
```
STEP 20 | Click OK to save the profile.
STEP 21 | Commit and Commit and Push your configuration changes.
STEP 22 | Monitor your application and link path health metrics, and generate reports of your
application and link health performance. For more information, see monitoring and reporting.
Strata Cloud Manager
STEP 1 | Log in to Strata Cloud Manager.
STEP 2 | Select Configuration > NGFW and Prisma Access > Network Policies > SD-WAN Policy >
Profiles > SD-WAN Interfaceand select the hub or branch folder where want to create the
SD-WAN interface profile.
STEP 3 | Add Profile.
STEP 4 | Enter a descriptive Name for the profile.
STEP 5 | Select the Link Tag the profile assigns to the interface.
STEP 6 | Select the Link Type from the predefined list.
```
STEP 7 | Specify the Maximum Download (Mbps) speed from the ISP.
```
```
STEP 8 | Specify the Maximum Upload (Mbps) speed to the ISP.
```
```
STEP 9 | Check (enable Eligible for Error Correction Profile Interface Selection to enable Forward
```
```
Error Correction (FEC) or packet duplication for interfaces.
```
If enabled, you must enable this setting for both sending and receiving firewalls.
STEP 10 | VPN Data Tunnel Support determines whether the branch-to-hub traffic and return traffic
flows through a VPN tunnel for added security or flows outside of the VPN tunnel to avoid
encryption overhead. This setting is enabled by default.
• Keep enabled for public links that have direct internet connections or internet break
capabilities, such as cable modem, ADSL, and other internet connections.
• Disable for private link types such as MPLS, satellite, or microwave that doesn’t have
internet breakout capability. However, you must first ensure that the traffic can’t be
intercepted because it will be sent outside of the VPN tunnel.
• The branch might have DIA traffic that needs to fail over to the private MPLS link
connecting to the hub, and reach the internet from the hub. The VPN Data Tunnel Support
setting determines whether the private data flows through the VPN tunnel or flows outside
```
the tunnel, and the failed over traffic uses the other connection (that the private data flow
```
```
doesn’t use). The firewall uses zones to segment DIA failover traffic from private MPLS
```
traffic.
SD-WAN Administration 22 ©2026 Palo Alto Networks, Inc.
Configure Interfaces for SD-WAN
STEP 11 | Set the VPN Failover Metric if DIA AnyPath is enabled a hub or branch firewall, to prioritize
the order in which a particular hub is selected for failover.
The lower the metric, the higher the priority of the interface to be selected during failover. If
multiple hub virtual interfaces have the same metric value, SD-WAN sends new session traffic
to them in round-robin fashion.
STEP 12 | Select the Path Monitoring mode.
• Aggressive—Firewall sends probe packets to the opposite end of the SD-WAN link at a
constant frequency. Use this mode if you need fast detection and failover for brownout and
blackout conditions. Default for all link types except LTE and Satellite.
```
• Relaxed—Firewall waits for a number of seconds (Probe Idle Time) between sending sets
```
of probe packets, making path monitoring less frequent. When the probe idle time expires,
firewall sends probes for 7 seconds at the Probe Frequency configured. Use this mode
```
when you have low-bandwidth links, links that charge by usage (such as LTE), or when fast
```
detection isn’t as important as preserving cost and bandwidth. Default for LTE and Satellite
link types.
```
STEP 13 | Set the Probe Frequency (per second) to specify the number of times per second the firewall
```
sends a probe packet to the opposite end of the SD-WAN link. The default setting provides
subsecond detection of brownout and blackout conditions.
```
STEP 14 | Set the Probe Idle Time (seconds) to specify how long the firewall waits between sets of
```
probe packets.
```
STEP 15 | Set the Failback Hold Time (seconds) to specify how long the firewall waits for a recovered
```
link to remain qualified before the firewall reinstates the link after it has failed.
STEP 16 | Save.
SD-WAN Administration 23 ©2026 Palo Alto Networks, Inc.
Configure Interfaces for SD-WAN
Configure Ethernet Interface for SD-WAN
Where Can I Use This? What Do I Need?
```
• NGFW (Managed by PAN-OS or
```
```
Panorama)
```
```
• NGFW (Managed by Strata Cloud
```
```
Manager)
```
Advanced SD-WAN for NGFW
One of these:
AIOps for NGFW Premium or Strata
Cloud Manager Pro
Strata Cloud Manager Essentials
```
(Supports only NGFWs)
```
Enable SD-WAN functionality to configure a physical, Layer 3 Ethernet interface.
To configure a physical interface, you must assign it an:
```
• (Panorama) IPv4, or IPv6 address, or both
```
```
• (Strata Cloud Manager) IPv4 address
```
You must also assign the interface a fully qualified next-hop gateway and assign an SD-WAN
```
interface profile to the interface. SD-WAN supports only a Layer 3 interface type; it doesn't
```
support Layer 2 networks such as VPLS. The SD-WAN interface profile defines key characteristics
```
that the firewall uses to manage that specific physical link, such as the link type (ADSL, cable
```
```
modem, MPLS), maximum upload and download speeds, and path monitoring settings. By
```
associating an SD-WAN interface profile with a physical Ethernet interface, you're essentially
telling the firewall how to treat that specific connection within the SD-WAN environment. This
association allows the firewall to apply the appropriate settings for link management, failover
behavior, and traffic routing based on the profile's configuration.
```
(Panorama) After you create a VPN cluster and export your hub and branch information in the
```
CSV, an Auto VPN configuration in the SD-WAN plugin uses this information to generate a
configuration for the associated branches and hubs that includes the predefined SD-WAN zones
and creates secure VPN tunnels between SD-WAN branches and hubs. Auto VPN configuration
also generates the BGP configuration if you enter BGP information in the CSV or when you add
an SD-WAN branch or hub.
```
(Strata Cloud Manager) BGP routing is enabled and generated by default.
```
• PAN-OS & Panorama
• Strata Cloud Manager
PAN-OS & Panorama
STEP 1 | Log in to the Panorama Web Interface.
STEP 2 | Select Network > Interfaces > Ethernet, select the appropriate template from the Template
```
context drop-down, select a slot number, such as Slot1, and select an interface (for example,
```
```
ethernet1/1).
```
SD-WAN Administration 24 ©2026 Palo Alto Networks, Inc.
Configure Interfaces for SD-WAN
STEP 3 | Select the Interface Type as Layer3.
STEP 4 | On the Config tab, for a legacy routing engine, select a Virtual Router or create a new virtual
router.
```
(SD-WAN plugin 3.1.0 and later versions) For Advanced Routing Engine, select a Logical
```
Router or create a new logical router.
STEP 5 | Assign the Security Zone that is appropriate for the interface you’re configuring.
For example, if you’re creating an uplink to an ISP, you must know that the Ethernet interface
you chose is going to an untrusted zone.
STEP 6 | To enable SD-WAN on an IPv4 interface, select the IPv4 tab and Enable SD-WAN.
With SD-WAN plugin 3.2.0 and later releases, you can configure up to four IP addresses for
an SD-WAN enabled interface. The SD-WAN plugin uses only the first IP Address from the
configured IP address list to create the SD-WAN tunnel.
The SD-WAN considers only the first IP address for the Next Hop Gateway and ignores the
remaining IP addresses in the list.
```
(HA deployments only) If you wish to downgrade from SD-WAN plugin version 3.2.0 to
```
3.1.0 or earlier, remove the HA active/passive configurations on both the firewalls before
attempting a downgrade procedure, such as downgrading PAN-OS and SD-WAN plugin
versions.
STEP 7 | For an IPv4 interface, select Type of address:
• Static—In the IP field, Add an IPv4 address and prefix length for the interface. You can use a
defined variable, such as $uplink, with a range of addresses. Note that you can only add an
IPv4 address or a defined variable and not an address object for the IP field. Enter the fully
```
qualified IPv4 address of the Next Hop Gateway (the next hop from the IPv4 address you
```
```
just entered). The Next Hop Gateway must be on the same subnet as the IPv4 address. The
```
Next Hop Gateway is the IP address of the ISP’s default router that the ISP gave you when
SD-WAN Administration 25 ©2026 Palo Alto Networks, Inc.
Configure Interfaces for SD-WAN
you bought the service. It is the next hop IP address to which the firewall sends traffic to
reach the ISP’s network, and ultimately, the internet and the hub.
```
• (PAN-OS 9.1.2 and later releases, and SD-WAN Plugin 1.0.2 and later releases)
```
PPPoE—Enable PPPoE authentication for DSL links, enter the Username and Password, and
Confirm Password.
• DHCP Client—It’s critical that DHCP assigns a default gateway, also known as the next
hop gateway for the ISP connection. The ISP will provide all the necessary connectivity
information, such as dynamic IP address, DNS servers, and the default gateway.
Although DHCP Client is supported for a hub or branch interface, on a hub
interface it’s preferable for you to assign a Static address instead of DHCP Client.
Using DHCP on a hub requires the Palo Alto Networks DDNS service. Using a Static
address at the hub site creates a more stable environment because DDNS isn’t
involved when resolving the DHCP IP address changes, and because the DDNS
service can take a few minutes to register the new IP address when it changes. If
you have multiple branch sites connecting to a hub site, having stability is critical to
keeping the network up and running.
If you select DHCP Client, be sure to disable the option Automatically create
default route pointing to default gateway provided by server, which is enabled by
default.
SD-WAN Administration 26 ©2026 Palo Alto Networks, Inc.
Configure Interfaces for SD-WAN
SD-WAN Administration 27 ©2026 Palo Alto Networks, Inc.
Configure Interfaces for SD-WAN
```
STEP 8 | (SD-WAN plugin 3.2.0 and later versions) To enable SD-WAN on an IPv6 interface, select
```
the IPv6 tab, Enable IPv6 on the interface, and Enable SD-WAN.
```
STEP 9 | (SD-WAN plugin 3.2.0 and later versions) In the EUI-64 (default 64-bit Extended Unique
```
```
Identifier) field, enter the 64-bit EUI in hexadecimal format. If you leave this field blank, the
```
firewall uses the EUI-64 generated from the MAC address of the physical interface. If you
enable the Use interface ID as host portion option when adding an address, the firewall uses
the Interface ID as the host portion of that address.
SD-WAN Administration 28 ©2026 Palo Alto Networks, Inc.
Configure Interfaces for SD-WAN
```
STEP 10 | (SD-WAN plugin 3.2.0 and later versions) For an IPv6 interface, select the Type of address as
```
Static. Select the Address Assignment tab.
1. Add an IPv6 Address for the interface or select New Variable to create the variable. SD-
WAN supports one IPv6 address per physical interface.
2. Enable address on interface.
3. Use interface ID as host portion—See prior step for explanation.
4. Anycast—Select to make the IPv6 address (route) an Anycast address (route), which
means multiple locations can advertise the same prefix, and IPv6 sends the anycast
traffic to the node it considers the nearest, based on routing protocol costs and other
factors.
5. Next Hop Gateway—Enter the IPv6 address of the Next Hop Gateway (the next hop
```
from the IPv6 address you entered). The Next Hop Gateway must be on the same
```
subnet as the IPv6 address. The Next Hop Gateway is the IP address of the ISP’s default
router that the ISP gave you when you bought the service. It is the next hop IP address
to which the firewall sends traffic to reach the ISP’s network, and ultimately, the internet
and the hub.
6. Send Router Advertisement—Select to enable the firewall to send this address in Router
```
Advertisements (RAs), in which case you must also enable the global Enable Router
```
```
Advertisement option for the interface (on the Router Advertisement tab).
```
7. Valid Lifetime (sec)—Enter the valid lifetime (in seconds) that the firewall considers
```
the address valid. The valid lifetime must equal or exceed the Preferred Lifetime (sec)
```
```
(default is 2,592,000).
```
8. Preferred Lifetime (sec)—Enter the preferred lifetime (in seconds) that the valid address
is preferred, which means the firewall can use it to send and receive traffic. After
the preferred lifetime expires, the firewall can't use the address to establish new
SD-WAN Administration 29 ©2026 Palo Alto Networks, Inc.
Configure Interfaces for SD-WAN
connections, but any existing connections are valid until the valid lifetime expires
```
(default is 604,800).
```
9. On-link—Select if systems that have addresses within the prefix are reachable without a
router.
10. Autonomous—Select if systems can independently create an IP address by combining
the advertised prefix with an Interface ID.
11. Click OK.
```
STEP 11 | (SD-WAN plugin 3.2.0 and later versions) For a static IPv6 interface, configure address
```
resolution.
1. Select Address Resolution.
2. Enable Duplicate Address Detection (DAD) if you want the uniqueness of a potential
```
IPv6 address to be verified before it's assigned to the interface (default is enabled).
```
3. If you selected Enable Duplicate Address Detection, specify the number of DAD
```
Attempts within the neighbor solicitation (NS) interval before the attempt to identify
```
```
neighbors fails; range is 1 to 10; default is 1.
```
4. Enter the Reachable Time (sec), the length of time that the client assumes a neighbor is
```
reachable after receiving a Reachability Confirmation message; range is 10 to 36,000;
```
default is 30.
5. Enter the NS Interval (sec) (Neighbor Solicitation interval), the length of time between
```
Neighbor Solicitations; range is 1 to 3,600; default is 1
```
6. Enable NDP Monitoring to enable Neighbor Discovery Protocol monitoring. When
enabled, you can select the NDP icon in the Features column and view information such
as the IPv6 address of a neighbor the firewall has discovered, the corresponding MAC
```
address, User-ID, and status (on a best-case basis).
```
7. Click OK.
SD-WAN Administration 30 ©2026 Palo Alto Networks, Inc.
Configure Interfaces for SD-WAN
```
STEP 12 | (SD-WAN plugin 3.2.0 and later versions) If you want to enable the interface to send
```
```
IPv6 Router Advertisements (RAs) and optionally tune RA parameters, configure Router
```
Advertisement as documented in the PAN-OS Networking Administrator's Guide, Configure
Layer 3 Interfaces.
```
STEP 13 | On the SD-WAN tab, select an SD-WAN Interface Profile that you already created (or
```
```
create a new SD-WAN interface profile) to apply to this interface. The SD-WAN Interface
```
Profile has an associated link tag, so the interfaces where this profile is applied will have the
associated link tag. An interface can have only one link tag.
STEP 14 | Click OK to save the Ethernet interface.
STEP 15 | Commit and Commit and Push your configuration changes.
```
STEP 16 | (SD-WAN manual configuration only) Configure a Virtual SD-WAN Interface. Auto VPN
```
configuration will perform this task if you’re using Auto VPN.
Strata Cloud Manager
Layer 3 interfaces are required for SD-WAN functionality. Repeat this step to configure as many
Layer 3 Ethernet interfaces on your SD-WAN firewall as needed.
Configure a Layer 3 interface for your firewalls as part of the folder or snippet configuration, or
for a specific firewall.
STEP 1 | Log in to Strata Cloud Manager.
STEP 2 | Select Configuration > NGFW and Prisma Access > Device Settings > Interfaces > Ethernet
and select the Configuration Scope where you want to create the Layer 3 interface.
Select a firewall from your Folders or select Snippets to configure the Layer 3 interface in a
snippet.
If you select a folder or select a snippet, you create a Layer 3 interface variable that must be
assigned at the device level.
STEP 3 | Add the interface.
If you’re configuring a Layer 3 interface for a specific firewall, select the interface you
want to configure instead.
• Folders and Snippets—Add Interface and select Interface.
• Firewalls—Add and Add Interface.
SD-WAN Administration 31 ©2026 Palo Alto Networks, Inc.
Configure Interfaces for SD-WAN
STEP 4 | Configure the interface.
If you’re configuring an interface in the folder or snippet scope, the interface configuration is
pushed only to firewalls that have the corresponding interface slot available. For example, if
you configure Ethernet 1/5 in the folder scope and the firewall associated with the folder has
only four interface slots, then the configuration isn’t pushed to the firewall.
1. Select the interface Slot.
2. Select the Interface Name.
When you configure an interface for a specific firewall, the Interface Name is
fixed, such as ethernet1/1 if you select Slot 1. The fixed interface names are
dependent on the slot that you selected in the previous step.
3. (Folders and Snippets only) Select the Default Interface Assignment.
4. (Optional) Enter a Description.
5. For Interface Type, select Layer3.
6. (Folders and Snippets only; Optional) Assign the interface to a Logical Router.
See configure a logical router for more information.
7. (Folders and Snippets only; Recommended) Assign the interface to a Zone.
Create New to create a new zone. See zone protection and DoS protection for more
information.
SD-WAN Administration 32 ©2026 Palo Alto Networks, Inc.
Configure Interfaces for SD-WAN
STEP 5 | Configure interface IP settings.
1. Select the interface IP Type.
• Static IPv4 Address.
Add the IPv4 IP addresses for the interface.
You can configure up to four IP addresses when you're configuring a Layer 3 Ethernet
interface for the SD-WAN functionality. Whereas the Auto VPN workflows uses only the
first IP address from the configured IPv4 address list to create the VPN tunnel.
• Activate the DHCP Client on the interface.
See configure an interface as a DHCP client for more information on configuring the
interface as a DHCP client.
• Activate PPPoE and configure the connection settings.
```
Enable to activate the interface for Point-to-Point Protocol over Ethernet (PPPoE)
```
termination. This makes the interface a PPPoE termination point to support connectivity
```
in a Digital Subscriber Line (DSL) environment where there’s a DSL modem but no other
```
PPPoE device to terminate the connection.
```
STEP 6 | (Optional) Configure the interface link settings.
```
1. Expand the Advanced Settings.
2. Select the interface Link Speed.
Auto is selected by default and allows the firewall to determine the speed.
3. Select the interface Link Duplex transmission mode.
Auto is selected by default to allow the firewall to negotiate the transmission mode
automatically.
4. Select the interface Link State.
Auto detect is selected by default to allow the firewall to determine the link state.
SD-WAN Administration 33 ©2026 Palo Alto Networks, Inc.
Configure Interfaces for SD-WAN
STEP 7 | Assign the interfaces to the aggregate interface group.
1. Select Configuration > NGFW and Prisma Access > Device Settings > Interfaces >
Ethernet and select the appropriate Configuration Scope.
You can select a folder or firewall from the Config Tree or select Snippets to configure
the interface in a snippet.
STEP 8 | Save.
STEP 9 | Push Config to push your configuration changes.
SD-WAN Administration 34 ©2026 Palo Alto Networks, Inc.
Configure Interfaces for SD-WAN
Configure an Aggregate Ethernet Interface and
Subinterfaces for Link Redundancy
Where Can I Use This? What Do I Need?
• NGFW Advanced SD-WAN for NGFW
```
(SD-WAN plugin 2.1.0 and later versions) SD-WAN supports aggregated Ethernet (AE) interfaces
```
so that an SD-WAN firewall in a data center, for example, can have an aggregate interface group
```
(bundle) of physical Ethernet interfaces that provide link redundancy. SD-WAN supports AE
```
interfaces with or without subinterfaces. You can create an AE interface with subinterfaces that
you can tag for different ISP services in order to provide end-to-end traffic segmentation. Thus,
your ISP services can reach multiple labs or buildings without needing a dedicated pair of fibers
for each connection. A Layer 3 AE interface group connects to a router, as shown in the following
```
figure:
```
VM-Series firewalls do not support AE interfaces. An SD-WAN hub or branch firewall that
has an AE interface should not belong to the same VPN cluster as a VM-Series SD-WAN
hub or branch firewall because AE interfaces are not supported on VM-Series firewalls.
PPPoE is not supported on subinterfaces.
STEP 1 | Log in to the Panorama Web Interface.
SD-WAN Administration 35 ©2026 Palo Alto Networks, Inc.
Configure Interfaces for SD-WAN
```
STEP 2 | Define your ISP connections and link types for each ISP connection (subinterface) in the AE
```
interface group to define its link attributes.
STEP 3 | Create an AE interface group.
1. Select Network > Interfaces > Ethernet, select a Panorama Template, and Add
Aggregate Group.
2. For Interface Name, enter the number to identify the aggregate group; range is 1 to 16.
3. For Interface Type, select Layer3.
4. Click OK.
STEP 4 | Assign physical interfaces to the aggregate group.
1. Select Network > Interfaces > Ethernet and select the interface you want to assign to
the aggregate group.
2. Select the Interface Type as Aggregate Ethernet.
3. Select the Aggregate Group you created; for example, ae1.
4. On the Advanced tab, select the Link Speed, Link Duplex, and Link State.
5. Click OK.
6. Repeat this step for each interface you want to assign to the aggregate group.
SD-WAN Administration 36 ©2026 Palo Alto Networks, Inc.
Configure Interfaces for SD-WAN
STEP 5 | For the aggregate group, create a subinterface that uses a static IP address.
1. Select Network > Interfaces > Ethernet, highlight the aggregate interface, such as ae1,
and click Add Subinterface at the bottom of the screen.
2. For Interface Name, enter a number after the period, such as 107.
3. Enter the VLAN Tag to differentiate between the subinterfaces. For ease of use, make
the tag the same number as the subinterface ID.
4. To configure a static IPv4 address for the subinterface, select the IPv4 tab and Enable
SD-WAN.
5. Select the Type of address: Static.
6. Add the IP address (and subnet mask) of the subinterface.
7. Enter the IP address of the Next Hop Gateway.
8. (SD-WAN plugin 3.2.0 and later versions) To configure a static IPv6 address for the
subinterface, select the IPv6 tab, Enable IPv6 on the interface, and Enable SD-WAN.
SD-WAN Administration 37 ©2026 Palo Alto Networks, Inc.
Configure Interfaces for SD-WAN
9. (SD-WAN plugin 3.2.0 and later versions) In the EUI-64 (default 64-bit Extended Unique
```
Identifier) field, enter the 64-bit EUI in hexadecimal format. If you leave this field blank,
```
the firewall uses the EUI-64 generated from the MAC address of the physical interface.
If you enable the Use interface ID as host portion option when added an address, the
firewall uses the Interface ID as the host portion of that address.
10. (SD-WAN plugin 3.2.0 and later versions) SelectAddress Assignment and Add an IPv6
Address for the interface or select New Variable to create the variable.
11. (SD-WAN plugin 3.2.0 and later versions) Use interface ID as host portion; see prior
substep for EUI-64.
12. (SD-WAN plugin 3.2.0 and later versions) Select Anycast to make the IPv6 address
```
(route) an Anycast address (route), which means multiple locations can advertise the
```
SD-WAN Administration 38 ©2026 Palo Alto Networks, Inc.
Configure Interfaces for SD-WAN
same prefix, and IPv6 sends the anycast traffic to the node it considers the nearest,
based on routing protocol costs and other factors.
13. (SD-WAN plugin 3.2.0 and later versions) Enter the IPv6 address of the Next Hop
```
Gateway (the next hop from the IPv6 address you entered). The Next Hop Gateway
```
must be on the same subnet as the IPv6 address. The Next Hop Gateway is the IP
address of the ISP's default router that the ISP gave you when you bought the service. It
is the next hop IP address to which the firewall sends traffic to reach the ISP's network,
and ultimately, the internet and the hub.
14. (SD-WAN plugin 3.2.0 and later versions) Select Send Router Advertisement to enable
```
the firewall to send this address in Router Advertisements (RAs), in which case you must
```
```
also enable the global Enable Router Advertisement option for the interface (on the
```
```
Router Advertisement tab).
```
15. (SD-WAN plugin 3.2.0 and later versions) Enter the Valid Lifetime (sec) in seconds that
the firewall considers the address valid. The valid lifetime must equal or exceed the
```
Preferred Lifetime (sec) (default is 2,592,000).
```
16. (SD-WAN plugin 3.2.0 and later versions) Enter the Preferred Lifetime (sec) (in seconds)
that the valid address is preferred, which means the firewall can use it to send and
receive traffic. After the preferred lifetime expires, the firewall can't use the address to
establish new connections, but any existing connections are valid until the valid lifetime
```
expires (default is 604,800).
```
17. (SD-WAN plugin 3.2.0 and later versions) Select On-link if systems that have addresses
within the prefix are reachable without a router.
18. (SD-WAN plugin 3.2.0 and later versions) Select Autonomous if systems can
independently create an IP address by combining the advertised prefix with the Interface
ID.
19. Click OK.
SD-WAN Administration 39 ©2026 Palo Alto Networks, Inc.
Configure Interfaces for SD-WAN
STEP 6 | As an alternative to a static address, for the aggregate group, create a subinterface that uses
DHCP to get its address.
1. Select Network > Interfaces > Ethernet and in the Template field, select a Template
Stack.
2. Highlight the aggregate interface, such as ae1, and click Add Subinterface at the bottom
of the screen.
3. Highlight the subinterface and click Override at the bottom of the screen.
4. Highlight the subinterface and for Interface Name, enter a number after the period, such
as 1.
5. Enter the VLAN Tag to differentiate between the subinterfaces. For ease of use, make
the tag the same number as the subinterface ID.
6. Select the IPv4 tab and Enable SD-WAN.
```
(SD-WAN plugin 3.2.0 and later versions) A subinterface in an aggregated
```
interface group supports only an IPv4 address as a DHCP client, not an IPv6
address.
7. Select the Type of address: DHCP Client.
8. Select Enable.
9. Uncheck (do not select) Automatically create default route pointing to default gateway
provided by server.
10. Select the Advanced tab and DDNS tab.
11. Select Settings and Enable. The Hostname is automatically generated by the Panorama
SD-WAN plugin.
12. Select the Vendor as Palo Alto Networks DDNS.
13. Click OK.
SD-WAN Administration 40 ©2026 Palo Alto Networks, Inc.
Configure Interfaces for SD-WAN
STEP 7 | Apply an SD-WAN Interface Profile to the subinterface.
1. Highlight the subinterface you created and select the SD-WAN tab.
2. Select the SD-WAN Interface Profile you created for this link or create a new profile.
3. Click OK.
STEP 8 | Repeat the prior steps to create additional Layer3 subinterfaces for the aggregate interface
group and apply an SD-WAN Interface Profile to each subinterface.
STEP 9 | Commit.
SD-WAN Administration 41 ©2026 Palo Alto Networks, Inc.
Configure Interfaces for SD-WAN
Segment SD-WAN Traffic using VLAN Tags
Where Can I Use This? What Do I Need?
• NGFW
• SD-WAN plugin 2.1.0 and later versions
Advanced SD-WAN for NGFW
SD-WAN supports Layer 3 subinterfaces so that the firewall can segment traffic using VLAN tags.
The following task shows how to create a Layer3 subinterface that uses a static IP address and
how to create one that uses DHCP to get its address. It shows how to assign a VLAN tag to the
subinterface and enable SD-WAN on the subinterface. Create an SD-WAN interface profile to
```
define each ISP connection and assign the profile to the corresponding subinterface (a virtual SD-
```
```
WAN interface).
```
If you configure SD-WAN Layer 3 subinterfaces on VM-Series firewalls, the VMware
configuration must have respective portgroups attached to those interfaces that allow all
VLANs.
PPPoE is not supported on subinterfaces.
```
STEP 1 | Configure an SD-WAN interface profile for each ISP connection (subinterface) to define its
```
link attributes.
SD-WAN Administration 42 ©2026 Palo Alto Networks, Inc.
Configure Interfaces for SD-WAN
STEP 2 | Create a Layer 3 subinterface that uses a static IPv4 address.
1. Select Network > Interfaces > Ethernet and in the Template field select a template.
2. Select an interface.
3. For Interface Type, select Layer3 and click OK.
4. Highlight the interface and click Add Subinterface at the bottom of the screen.
5. After the Interface Name and period, enter the subinterface number.
6. Enter a Tag for the subinterface (range is 1 to 4,094). For ease of use, make the tag the
same number as the subinterface ID.
7. On the IPv4 tab, Enable SD-WAN.
8. Select the Type of address: Static.
9. Add the IP address and subnet mask.
10. Enter the IP address of the Next Hop Gateway.
11. Click OK.
```
STEP 3 | (SD-WAN plugin 3.2.0 and later versions) Create a Layer 3 subinterface that uses a static
```
IPv6 address.
1. Perform the first six substeps of the step to create a Layer 3 subinterface that uses a
static IPv4 address, because they are the same for an IPv6 address.
2. On the IPv6 tab, Enable IPv6 on the interface and Enable SD-WAN.
3. In the EUI-64 (default 64-bit Extended Unique Identifier) field, enter the 64-bit EUI in
hexadecimal format. If you leave this field blank, the firewall uses the EUI-64 generated
from the MAC address of the physical interface. If you enable the Use interface ID as
SD-WAN Administration 43 ©2026 Palo Alto Networks, Inc.
Configure Interfaces for SD-WAN
host portion option when adding an address, the firewall uses the Interface ID as the
host portion of that address.
4. Select the Type of address: Static.
5. Select Address Assignment.
6. Add an IPv6 Address for the interface or select New Variable to create the variable. SD-
WAN supports one IPv6 address per physical interface.
7. Enable address on interface.
SD-WAN Administration 44 ©2026 Palo Alto Networks, Inc.
Configure Interfaces for SD-WAN
8. Use interface ID as host portion—.See the third substep above for explanation.
9. Anycast—Select to make the IPv6 address (route) an Anycast address (route), which
means multiple locations can advertise the same prefix, and IPv6 sends the anycast
traffic to the node it considers the nearest, based on routing protocol costs and other
factors.
10. Next Hop Gateway—Enter the IPv6 address of the Next Hop Gateway (the next hop
```
from the IPv6 address you entered). The Next Hop Gateway must be on the same
```
subnet as the IPv6 address. The Next Hop Gateway is the IP address of the ISP’s default
router that the ISP gave you when you bought the service. It is the next hop IP address
to which the firewall sends traffic to reach the ISP’s network, and ultimately, the internet
and the hub.
11. Send Router Advertisement—Select to enable the firewall to send this address in Router
```
Advertisements (RAs), in which case you must also enable the global Enable Router
```
```
Advertisement option for the interface (on the Router Advertisement tab).
```
12. Valid Lifetime (sec)—Enter the valid lifetime (in seconds) that the firewall considers
```
the address valid. The valid lifetime must equal or exceed the Preferred Lifetime (sec)
```
```
(default is 2,592,000).
```
13. Preferred Lifetime (sec)—Enter the preferred lifetime (in seconds) that the valid address
is preferred, which means the firewall can use it to send and receive traffic. After
the preferred lifetime expires, the firewall can't use the address to establish new
connections, but any existing connections are valid until the valid lifetime expires
```
(default is 604,800).
```
14. On-link—Select if systems that have addresses within the prefix are reachable without a
router.
15. Autonomous—Select if systems can independently create an IP address by combining
the advertised prefix with an Interface ID.
16. Click OK.
SD-WAN Administration 45 ©2026 Palo Alto Networks, Inc.
Configure Interfaces for SD-WAN
STEP 4 | As an alternative to a static address, create a Layer 3 subinterface that uses DHCP to get its
IPv4 address.
1. Select Network > Interfaces > Ethernet and in the Template field, select a template
```
stack (not a template).
```
2. Select an interface.
3. For Interface Type, select Layer3 and click OK.
4. Highlight the interface and click Add Subinterfaces at the bottom of the screen.
5. Highlight the subinterface and click Override.
6. Highlight the subinterface and after the Interface Name and period, enter the
subinterface number.
7. Enter a Tag for the subinterface (range is 1 to 4,094). For ease of use, make the tag the
same number as the subinterface ID.
8. On the IPv4 tab, Enable SD-WAN.
9. Select Type of address: DHCP Client and Enable.
10. Uncheck (do not select) Automatically create default route pointing to default gateway
provided by server.
11. Select the Advanced tab and then the DDNS tab.
12. Select Settings and Enable. The Hostname is automatically generated by the Panorama
SD-WAN plugin.
13. Select the Vendor as Palo Alto Networks DDNS.
14. Click OK.
SD-WAN Administration 46 ©2026 Palo Alto Networks, Inc.
Configure Interfaces for SD-WAN
STEP 5 | Apply an SD-WAN Interface Profile to the subinterface.
1. Highlight the subinterface you created and select the SD-WAN tab.
2. Select the SD-WAN Interface Profile you created for this link or create a new profile.
3. Click OK.
STEP 6 | Repeat the prior steps to add more subinterfaces to the interface.
STEP 7 | Commit.
SD-WAN Administration 47 ©2026 Palo Alto Networks, Inc.
Configure Interfaces for SD-WAN
SD-WAN Administration 48 ©2026 Palo Alto Networks, Inc.
Enable SD-WAN with Auto VPN
Where Can I Use This? What Do I Need?
• NGFW Advanced SD-WAN for NGFW
Auto VPN enables you to create SD-WAN cluster to connect multiple LANs. Auto VPN is an
automated process for configuring the VPN tunnel that helps you to deploy and manage an
SD-WAN environment easily. With Auto VPN, SD-WAN creates the tunnels and adds the
corresponding interfaces automatically when you configure the SD-WAN. Auto VPN allows you
to quickly and easily build VPN tunnels for your network topology.
With Auto VPN, you can create:.
```
• (Panorama) either hub and spoke or mesh topology based on your network requirements
```
```
• (Strata Cloud Manager) hub and spoke topology based on your network requirements
```
Using Auto VPN will be beneficial to you when your topology has more branches. Without Auto
VPN, you will be required to configure each SD-WAN firewall manually along with the routing
configurations.
```
(Strata Cloud Manager) With Auto VPN, you can now create Cellular, Sub Interface, and
```
Aggregate Interface configurations.
With Auto VPN, you can create multiple VPN clusters easily as per your network topology
requirements. With Auto VPN, you can also add or delete the branch or hub firewalls from the
existing cluster easily. Without Auto VPN, you may have to perform these tasks manually and
there are chances for misconfiguration while updating the existing cluster configuration.
```
(Panorama) You can also add a single SD-WAN hub or branch firewall or use a CSV to bulk import
```
multiple SD-WAN hub and branch firewalls.
You will be able to select your preferred authentication type while creating the SD-WAN cluster.
```
• (Panorama) pre-shared key or certificate authentication type
```
```
• (Strata Cloud Manager) pre-shared key authentication type
```
49
Enable SD-WAN with Auto VPN
Add SD-WAN Branch or Hub Firewall
Where Can I Use This? What Do I Need?
• NGFW Advanced SD-WAN for NGFW
Add a SD-WAN hub or branch firewall to be managed by the Panorama® management server.
```
When adding your devices, you specify what type of device it is (branch or hub) and you give
```
each device its site name for easy identification. Before adding your devices, plan your SD-WAN
configuration to ensure that you have all the required IP addresses and you understand the SD-
WAN topology. This helps in reducing any configuration errors.
If you have preexisting zones for your Palo Alto Networks®firewalls, you will be mapping them to
the predefined zones used in SD-WAN.
If you want to have active/passive HA running on two branch firewalls or two hub
firewalls, don’t add those firewalls as SD-WAN devices at this time. You’ll add them as HA
peers separately when you configure SD-WAN devices in HA mode.
If you’re using BGP routing, you must add a Security policy rule to enable BGP from the
internal zone to the hub zone and from the hub zone to the internal zone. If you want to
use 4-byte ASNs, you must first enable 4-byte ASNs for the virtual router.
When viewing SD-WAN devices, if no data is present or the screen indicates that SD-
WAN is undefined, check in the Compatibility Matrix that the Panorama release you’re
using supports the SD-WAN plugin release you’re trying to use.
STEP 1 | Log in to the Panorama Web Interface.
STEP 2 | Select Panorama > SD-WAN > Devices and Add a new SD-WAN firewall.
STEP 3 | Select the managed firewall Name to add as an SD-WAN device. You must add your SD-
WAN firewalls as managed devices before you can add them as an SD-WAN device.
STEP 4 | Select the Type of SD-WAN device.
• Hub—A centralized firewall deployed at a primary office or location to which all branch
devices connect using a VPN connection. Traffic between branches passes through the hub
before continuing to the target branch, and connects branches to centralized resources at
the hub location. The hub device processes traffic enforces policy rules, and manages link
swapping at the primary office or location.
• Branch—A firewall deployed at a physical branch location that connects the hub using a
VPN connection and provides security at the branch level. The branch device processes
traffic enforces policy rules, and manages link swapping at the branch location.
```
STEP 5 | (Mandatory for HA Peers) (PAN-OS 12.1.2 and later releases, SD-WAN 3.4.0 and later
```
```
releases) Configure HA peers simultaneously from a single window while adding the SD-
```
WAN firewall branches and hubs, ensuring configuration consistency between the active and
passive devices.
SD-WAN Administration 50 ©2026 Palo Alto Networks, Inc.
Enable SD-WAN with Auto VPN
```
STEP 6 | (Optional) (PAN-OS 10.2.8 and later 10.2 versions, and SD-WAN plugin 3.0.7 and later 3.0
```
```
versions) (PAN-OS 11.1.3 and later versions, and SD-WAN plugin 3.2.1 and later versions)
```
Configure multiple virtual routers on the SD-WAN hub.
Select Enable Multi-VR Support to configure multiple virtual routers on the SD-WAN hub.
We have introduced support for multiple virtual routers on the SD-WAN hub that enable you
to have overlapping IP subnet addresses on branch devices connecting to the same SD-WAN
hub. When you select the Type of SD-WAN as hub, you will be able to configure multiple
virtual routers by selecting Enable Multi-VR Support.
STEP 7 | For routing between the SD-WAN hub and branches:
```
• (SD-WAN plugin 3.0.0 and earlier versions) select Virtual Router Name in the web
```
interface.
```
• (SD-WAN plugin 3.1.0 and later versions) select Router Name in the web interface.
```
By default, an sdwan-default virtual router is created and enables Panorama to
automatically push the router configurations.
```
(Advanced Routing enabled) (SD-WAN plugin 3.1 and later versions) If you have configured
```
advanced routing and the logical routers are created successfully, Router Name displays both
virtual and logical router names:
• If the virtual router and logical router names are the same, then the Router Name displays
the same name because advanced routing creates a logical router with the same name as
the virtual router, by default. It's important that the logical router name and virtual router
name are the same for the same template when using the advanced routing engine.
```
• If the virtual router and logical router names are different (which happens only when you
```
```
update the logical router name manually), then the router name displays both the virtual and
```
```
logical router names. You can select either virtual router (for legacy engine) or logical router
```
```
(for advanced routing engine) based on your requirement. If you haven't enabled Advanced
```
```
Routing, then you’ll have only virtual routers to select from the Router Name (for the legacy
```
```
engine).
```
If you Enable Multi-VR Support:
```
• (PAN-OS 10.2.8 and later 10.2 releases, and SD-WAN plugin 3.0.7 and later 3.0 releases)
```
Select DIA virtual router for the Virtual Router Name.
```
• (PAN-OS 11.1.3 and later releases, and SD-WAN plugin 3.2.1 and later releases) Select DIA
```
virtual router for the Router Name.
STEP 8 | Enter the SD-WAN Site name to identify the geographical location or purpose of the device.
The SD-WAN Site name supports all upper-case and lower-case alphanumerical and
special characters. Spaces aren’t supported in the Site name and result in monitoring
```
(Panorama > SD-WAN > Monitoring) data for that site not to be displayed.
```
```
All SD-WAN devices, including SD-WAN devices in a high availability (HA)
```
configuration, must have a unique Site name.
SD-WAN Administration 51 ©2026 Palo Alto Networks, Inc.
Enable SD-WAN with Auto VPN
```
STEP 9 | (PAN-OS 12.1.5 and later versions and plugin 3.4.1 and later versions) Enable the Capacity-
```
```
Setting to optimize memory usage and enter SD-WAN rules, virtual interfaces (VIFs), and VIF
```
members to adjust the capacity values to meet your deployment requirements.
Before you enable capacity settings from Panorama and perform a commit-all, verify
that the deviceconfig node exists on the target device. If it does not exist,
commit-all to that device fails. To avoid this issue, in Panorama go to Templates >
Device > Setup > Management, add or update the value of any field, and commit
before enabling capacity settings.
When you enable the capacity settings, the device automatically populates fields with default
values, which you can then modify to prioritize specific features, such as SD-WAN policies or
virtual interfaces, based on your preference.
1. Enter the maximum number of SD-WAN policies in the Max SD-WAN Policies.
2. Enter the maximum number of virtual interfaces in the Max Virtual Interfaces.
3. Enter a value for Max members per VIF to define the number of members allowed per
virtual interface.
Increasing the maximum members per VIF up to 16 requires a proportional
reduction in other capacity settings to maintain the total memory consumption
limit of the device.
4. Select the Error Correction to allow the device to recover lost or corrupted packets.
5. Click Validate Capacity to ensure the entered values are within the supported hardware
limits.
Once the configuration passes validation, push the settings to the firewall. You must manually
reboot the firewall for the new capacity settings to take effect.
```
STEP 10 | (PAN-OS 10.0.3 and later versions) Select the Link Tag you created for the hub virtual
```
```
interface (or branch virtual interface), which Auto VPN will assign to the virtual interface.
```
```
You’ll use this Link Tag in a Traffic Distribution profile to enable the hub (or branch) to
```
participate in DIA AnyPath.
```
STEP 11 | (PAN-OS 9.1.3 and later versions and SD-WAN plugin 1.0.3 and later versions) If you’re
```
adding a hub that is behind a device performing NAT for the hub, you must specify the IP
address or FQDN of the public-facing interface on that upstream NAT-performing device,
so that Auto VPN configuration can use that address as the tunnel endpoint of the hub. It’s
SD-WAN Administration 52 ©2026 Palo Alto Networks, Inc.
Enable SD-WAN with Auto VPN
```
the IP address that the branch office’s IKE and IPSec flows must be able to reach. (You must
```
```
have already configured an Ethernet interface for SD-WAN.)
```
1. On the Upstream NAT tab, enable Upstream NAT.
2. Add a SD-WAN interface; select an interface you already configured for SD-WAN.
3. Select IP Address or FQDN and enter the IPv4 address without a subnet mask (for
```
example, 192.168.3.4) or the FQDN of the upstream device, respectively.
```
4. Click OK.
Additionally, on the upstream device that is performing NAT you must set up
the inbound destination NAT with a one-to-one NAT policy, and you must not
configure port translation to the IKE or IPSec traffic flows.
If the IP address on the upstream device changes, you must configure the new IP
address and push it to the VPN cluster. You must use the CLI commands clear
vpn ipsec-sa, clear vpn ike-sa, and clear session all on
both the branch and hub. You must also clear session all on the virtual
router where you configured the NAT policy for the IP addresses.
Upstream NAT isn’t supported on Layer 2 interfaces.
```
STEP 12 | (Required for preexisting customers) Map your preexisting zones to predefined zones used
```
for SD-WAN.
When you map your existing zones to a SD-WAN zone, you must modify your security
policy rules and add the SD-WAN zones to the correct Source and Destination zones.
1. Select Zone Internet and Add the preexisting zones that will egress SD-WAN traffic to
the internet.
2. Select Zone to Hub and Add the preexisting zones that will egress SD-WAN traffic to
the hub.
3. Select Zone to Branch and Add the preexisting zones that will egress SD-WAN traffic to
the branch.
4. Select Zone Internal and Add the preexisting zones that will egress SD-WAN traffic to
an internal zone.
```
STEP 13 | (PAN-OS 10.0.3 and later versions) (Full Mesh Deployments Only) If you’re adding a branch
```
that is behind a device performing NAT for the branch, you must specify the IP address or
FQDN of the public-facing interface on that upstream NAT-performing device, or select
DDNS to indicate that the IP address for the interface on the NAT device is obtained from
the Palo Alto Networks DDNS service. Thus, Auto VPN configuration uses that public IP
address as the tunnel endpoint for the branch. It is the IP address that the branch office’s IKE
SD-WAN Administration 53 ©2026 Palo Alto Networks, Inc.
Enable SD-WAN with Auto VPN
```
and IPSec flows must be able to reach. (You must have already configured Ethernet interface
```
```
for SD-WAN.)
```
1. On the Upstream NAT tab, enable Upstream NAT.
2. Add a SD-WAN interface; select an interface you already configured for SD-WAN.
3. If you select the NAT IP Address Type to be Static IP, select IP Address or FQDN and
```
enter the IPv4 address without a subnet mask (for example, 192.168.3.4) or the FQDN
```
of the upstream device, respectively.
4. Alternatively, select the NAT IP Address Type to be DDNS.
5. Click OK.
Additionally, on the upstream device that is performing NAT you must set up
the inbound destination NAT with a one-to-one NAT policy, and you must not
configure port translation to the IKE or IPSec traffic flows.
If the IP address on the upstream device changes, you must configure the new IP
address and push it to the VPN cluster. You must use the CLI commands clear
ipsec, clear ike-sa, and clear session all on both the branch and
hub. You must also clear session all on the virtual router where you
configured the NAT policy for the IP addresses.
There is a second location in the web interface where you can configure
Upstream NAT for a branch, but the following location isn't preferred and you
shouldn't configure Upstream NAT for a branch in both places. The secondary,
non-preferred location to configure Upstream NAT is on Panorama at Network
> Interfaces > Ethernet, select a template in the Template field, select an
Ethernet interface, and select the SD-WAN tab. At this point you can Enable
Upstream NAT, and select a NAT IP Address Type. This second method takes
precedence. If Upstream NAT is first configured for the Ethernet interface on
Panorama through the template stack, then the SD-WAN plugin won’t change
the settings, even if you use different settings on the plugin device configuration
page. Only if there is no Upstream NAT configured on Panorama through the
template stack, then the plugin configuration for Upstream NAT takes effect.
Upstream NAT is not supported on Layer 2 interfaces.
```
STEP 14 | (PAN-OS 10.1.5-h1 and later 10.1 versions, and SD-WAN plugin 2.2.1 and later 2.2 versions)
```
```
(PAN-OS 10.2.1 and later versions, and SD-WAN plugin 3.0.1 and later versions) If your
```
```
application traffic is tagged with Type of Service (ToS) bits or Differentiated Services Code
```
```
Point (DSCP) markings, copy the ToS field from the inner header to the outer VPN header of
```
encapsulated packets going through the VPN tunnel to preserve QoS information.
1. Select the VPN Tunnel tab.
2. Select Copy ToS Header.
3. Click OK.
SD-WAN Administration 54 ©2026 Palo Alto Networks, Inc.
Enable SD-WAN with Auto VPN
```
STEP 15 | (Mandatory) (SD-WAN plugin 3.2.0 and later versions) Specify how to authenticate the peer.
```
Select the Authentication type: Pre Shared Key or Certificate. If you choose a pre-shared key,
the pre-shared key will be automatically generated.
• You must use a unique certificate for each device in the SD-WAN cluster.
• You can't change the authentication type after adding an SD-WAN device to the
VPN cluster.
```
• (HA deployments only) If you have set up a high availability (HA) pair in Panorama,
```
then both the active and passive firewalls must use the same certificate. During the
RMA process, you must configure the replacement firewall with the same certificate
as the active firewall. If the certificate of an active firewall is revoked and a new
certificate is pushed, then the passive firewall must also be updated with the new
certificate. That is, both active and passive firewalls must have the same certificate
configured in a high availability deployment.
SD-WAN Administration 55 ©2026 Palo Alto Networks, Inc.
Enable SD-WAN with Auto VPN
```
STEP 16 | (Only if enabling Certificate authentication type) (SD-WAN plugin 3.2.0 and later versions)
```
Configure certificate-based authentication.
1. Select a Local Certificate—one that is already on the Panorama, Import a certificate, or
Generate a new certificate.
• If you need to Import a certificate, then first Import a Certificate for IKEv2 Gateway
Authentication and then return to this task. We do not support SCEP-generated
certificates.
• If you want to Generate a new certificate, then first generate a certificate on the
Panorama and then return to this task. The generated certificate must be unique for
each SD-WAN device. That is, you can't generate a certificate and share it among
multiple SD-WAN devices.
Keep the following in mind while generating the branch and hub firewall certificates
that are used for SD-WAN tunnel authentication:
• Two different hub devices can use the same hub certificate.
• Two different branch devices can use the same branch certificate if the following
conditions are met:
• Branch devices are not part of the same VPN cluster.
• There is no common hub device between the VPN clusters that this branch
device would be part of.
```
• (HA deployments only) Two different branch devices can also have the same
```
branch certificates if they are configured as HA members.
• If you've a common hub device between the VPN clusters, then the branch devices
that are part of these VPN clusters should have unique certificates containing
with unique values for all its attributes. If you don't ensure the uniqueness of the
SD-WAN Administration 56 ©2026 Palo Alto Networks, Inc.
Enable SD-WAN with Auto VPN
```
certificate and its values, then commit will fail on the hub device (no commit failure
```
```
on Panorama).
```
```
Also ensure that the leaf certificates (branch and hub firewall certificates)
```
used for SD-WAN tunnel authentication are generated meeting the
following criteria:
• Key usage should have digital signatures.
• All certificates must be signed by the same root CA.
• The device certificate must be directly signed by the root CA.
• Certificate format should be PKCS12.
• The certificate attributes are used for determining the local ID and peer ID for IKE
gateways. Hence, the leaf certificates, that is, the branch and hub firewall certificates
that are used for SD-WAN tunnel authentication, must be generated with the
following three certificate attributes and each certificate attribute should be assigned
with three unique attribute values. Otherwise, a commit error will be thrown.
```
• FQDN (Host Name)
```
```
• IP address (IP)
```
```
• User FQDN (Alt Email)
```
It is mandatory to have unique Host Name, IP, and Alt Email certificate
attributes among all certificates. That is, none of the certificates should have
these attribute values in common.
In the below example, NewCertificate is generated with the total of nine mandatory
certificate attributes. The Host Name certificate attribute is configured with three
unique attribute values: pan-fw01.yourcompany.com, pan-fw02.yourcompany.com,
and pan-fw03.yourcompany.com. The IP certificate attribute is configured with three
unique attribute values: 192.0.2.0, 192.0.2.1, and 192.0.2.2. The Alt Email certificate
SD-WAN Administration 57 ©2026 Palo Alto Networks, Inc.
Enable SD-WAN with Auto VPN
attribute is configured with three unique attribute values: sales@yourcompany.com,
IT@yourcompany.com, and customercare@yourcompany.com.
2. (Optional) Choose a Certificate Profile. A certificate profile contains information about
how to authenticate the peer gateway.
3. (Optional) Enable strict validation of peer’s extended key use to control strictly how the
key can be used.
```
STEP 17 | (Optional) (SD-WAN plugin 3.1.0 and earlier versions) Configure Border Gateway Protocol
```
routing.
To automatically set up BGP routing between the VPN cluster members, enter the BGP
information below. If you want to manually configure BGP routing on each firewall or use
a separate Panorama template to configure BGP routing for more control, leave the BGP
information below blank.
Before implementing SD-WAN with BGP routing in an environment where BGP is
already in use, ensure that the BGP configuration generated by the SD-WAN plugin
doesn’t conflict with your preexisting BGP configuration. For example, you must use
the existing BGP AS number and router ID values for the corresponding SD-WAN
device values. If the BGP configuration generated by the plugin conflicts with your
preexisting BGP configuration, the preexisting BGP configuration takes precedence.
If you want the pushed configuration to take precedence, you must enable the force
template value when doing a Panorama push.
1. Select the BGP tab and enable BGP to configure BGP routing for SD-WAN traffic.
2. Enter the BGP Router ID, which must be unique among all routers.
3. Specify a static IPv4 Loopback Address for BGP peering. Auto VPN configuration
automatically creates a Loopback interface with the same IPv4 address that you specify.
SD-WAN Administration 58 ©2026 Palo Alto Networks, Inc.
Enable SD-WAN with Auto VPN
If you specify an existing loopback address, the commit will fail, so you should specify an
IPv4 address that is not already a loopback address.
4. Enter the AS Number. The autonomous system number specifies a commonly defined
routing policy rule to the internet. The AS number must be unique for every hub and
branch location.
5. (SD-WAN plugin 2.0.2 and later versions) Disable the Remove Private AS option (the
```
default is enabled) if you have endpoints that need to exchange routes with a hub or
```
branch firewall in an SD-WAN BGP topology and therefore you don’t want to remove
```
private AS numbers (64512 to 65534) from the AS_PATH attribute in BGP Updates. In
```
this case, you want to enable the private AS numbers to leave the SD-WAN private AS in
BGP Updates.
The Remove Private AS setting applies to all BGP peer groups on the branch or
hub firewall. If you need this setting to differ among BGP peer groups or peers,
you must configure the setting outside of the SD-WAN plugin.
If you change the Remove Private AS setting, commit to all SD-WAN cluster
nodes, and subsequently downgrade to an SD-WAN plugin version earlier than
2.0.2, then all configuration related to Remove Private AS must be done outside
of the SD-WAN plugin or directly on the firewalls.
6. Enter Prefix(es) to Redistribute. On a hub device, you must enter at least one prefix
```
to redistribute. Branch devices do not have this option; subnets connected to branch
```
locations are redistributed by default.
```
STEP 18 | (SD-WAN plugin 3.1.1 and later versions using the legacy routing engine) To configure BGP
```
to use IPv4, select IPv4 BGP. Whether your BGP environment is only IPv4 or dual stack
```
(IPv4 and IPv6), you must enable IPv4 BGP.
```
1. Enable IPv4 BGP support.
```
For an upgraded configuration (an already existing SD-WAN IPv4 configuration),
```
Enable IPv4 BGP support is selected by default. Otherwise, explicitly Enable
IPv4 BGP support.
2. Specify a static IPv4 Loopback Address for BGP peering. Auto VPN configuration
automatically creates a Loopback interface with the same IPv4 address that you specify.
If you specify an existing loopback address, the commit will fail, so you must specify an
IPv4 address that isn’t already a loopback address.
3. Disable the Remove Private AS option (the default is enabled) if you have endpoints
that need to exchange routes with a hub or branch firewall in an SD-WAN BGP topology
```
and therefore you don’t want to remove private AS numbers (64512 to 65534) from
```
SD-WAN Administration 59 ©2026 Palo Alto Networks, Inc.
Enable SD-WAN with Auto VPN
the AS_PATH attribute in BGP Updates. In this case, you want to enable the private AS
numbers to leave the SD-WAN private AS in BGP Updates.
The Remove Private AS setting applies to all BGP peer groups on the branch or
hub firewall. If you need this setting to differ among BGP peer groups or peers,
you must configure the setting outside of the SD-WAN plugin.
If you change the Remove Private AS setting, commit to all SD-WAN cluster
nodes, and later downgrade to a SD-WAN plugin version earlier than 2.0.2, then
you must perform all configuration related to Remove Private AS outside of the
SD-WAN plugin or directly on the firewalls.
4. Add the Prefix(es) to Redistribute. On a hub device, you must enter at least one prefix
to redistribute over the SD-WAN tunnel. Branch devices don't have this mandatory
configuration requirement because subnets connected to branch locations are
redistributed by default.
```
STEP 19 | (SD-WAN plugin 3.1.1 and later versions using the legacy routing engine) To configure BGP
```
to use IPv6, select IPv6 BGP.
1. Enable IPv6 BGP support.
2. Specify a static IPv6 Loopback Address for BGP peering. Auto VPN configuration
automatically creates a loopback interface with the same IPv6 address that you specify.
If you specify an existing loopback address, the commit will fail, so you must specify an
IPv6 address that isn't already a loopback address.
3. Add the Prefix(es) to Redistribute over the SD-WAN tunnel. On a hub device, you must
enter at least one prefix to redistribute over the SD-WAN tunnel. Branch devices don't
SD-WAN Administration 60 ©2026 Palo Alto Networks, Inc.
Enable SD-WAN with Auto VPN
have this mandatory configuration requirement because subnets connected to branch
locations are redistributed by default.
STEP 20 | Click OK.
```
STEP 21 | (SD-WAN plugin 1.0.1 and later versions) Select Group HA Peers at the bottom of the
```
```
screen to display branches (or hubs) that are HA peers together.
```
SD-WAN Administration 61 ©2026 Palo Alto Networks, Inc.
Enable SD-WAN with Auto VPN
```
STEP 22 | (PAN-OS 9.1.2 and later versions, and SD-WAN plugin 1.0.2 and later versions) Have
```
Panorama create and push to firewalls a Security policy rule that enables BGP to run
between branches and hubs.
1. (SD-WAN plugin 3.1.0 and earlier versions) Select BGP Policy at the bottom of the
screen and Add.
2. (SD-WAN plugin 3.1.1 and later versions) At the bottom of the screen, select IPv4 BGP
Policy or IPv6 BGP Policy and Add a policy rule.
3. Enter a Policy Name for the Security policy rule that Panorama will automatically create.
4. (SD-WAN plugin 3.2.0 and later versions) Select Type as Hub or Branch.
5. Select Device Groups to specify the device groups to which Panorama pushes the
Security policy rule.
6. Click OK.
```
STEP 23 | (Optional) (PAN-OS 11.1.8 and later versions, and SD-WAN plugin 3.2.4 and later versions)
```
Configure dedicated tunnel to Panorama.
When the SD-WAN overlay experiences issues, branch devices lose their connection to
Panorama. It requires manual intervention to fix the connection issue that leads to extended
outages, high operational costs, and business disruptions. A dedicated tunnel to Panorama
resolves this issue. You can now configure a dedicated tunnel to Panorama on both mesh and
hub and spoke topologies. Dedicated tunnels are created from every configured SD-WAN
device to Panorama which is deployed behind termination devices. The dedicated tunnel
creates a separate dedicated management paths that operate independently from the SD-
SD-WAN Administration 62 ©2026 Palo Alto Networks, Inc.
Enable SD-WAN with Auto VPN
WAN overlay. It ensures continuous management access even when the primary SD-WAN
overlay is compromised.
The dedicated tunnel provides multiple connectivity options through primary and secondary
termination devices. You can select either a hub or branch firewall that is part of your SD-
WAN deployment as the termination devices.
• Hub devices are ideal termination points due to their central role in the SD-WAN
architecture. They typically have more robust connectivity and resources to handle
additional tunnels.
• Branch devices can also serve as termination devices. Select branch devices as a
termination device when a branch location has reliable and robust internet connectivity.
Ensure that your termination devices meet the following criteria:
• Termination devices must have at least one SD-WAN-enabled interface with DIA access.
• The primary and secondary termination devices should not be the same device.
Follow these steps to establish dedicated tunnels from your SD-WAN devices to Panorama,
ensuring continued management connectivity even if the primary SD-WAN overlay network
experiences issues.
1. Select Panorama Connectivity at the bottom of the screen and enable Create Dedicated
IPSEC Tunnels.
2. Enter a nonoverlapping IP CIDR address range for VPN Address Pool. Ensure that this
range doesn't overlap with the existing SD-WAN overlay tunnel IP configuration. The
SD-WAN Administration 63 ©2026 Palo Alto Networks, Inc.
Enable SD-WAN with Auto VPN
SD-WAN plugin uses the first address of the VPN pool as the loopback address for
creating the dedicated tunnel.
3. Select the Primary Termination Device that is the main endpoint for tunnels from branch
devices to Panorama.
• Select the primary SD-WAN enabled interface for Preferred DIA.
```
• (Optional) Select the secondary SD-WAN enabled interface for Backup DIA.
```
4. Select the Secondary Termination Device that provides redundancy if the primary
termination device fails.
• Select the secondary device for Preferred DIA.
```
• (Optional) Select the secondary device for Backup DIA.
```
```
STEP 24 | (Mandatory when enabling dedicated tunnel to Panorama) (PAN-OS 11.1.8 and later
```
```
versions, and SD-WAN plugin 3.2.4 and later versions) (Only for dedicated tunnel creation)
```
Add NAT policy for the dedicated tunnels.
If you're creating dedicated tunnels to Panorama, then it is mandatory to create a NAT policy
```
(as SD-WAN does not create one) and push the policy rule to the device group first and then
```
to the template. Don’t push the device group and template at the same time.
1. Select Dedicated Tunnel NAT Policy at the bottom of the screen and Add.
2. Select the Hub or Branch in the device groups to create the NAT policy rules.
```
• (Recommended) If you select Branch, then the NAT policy rules are created for the
```
SD-WAN enabled interfaces in the selected branch device group.
• If you select Hub, then the NAT policies are created for the SD-WAN enabled
interfaces in the selected hub device group.
3. Select OK to save the NAT policy.
4. Commit the changes to Panorama.
STEP 25 | Select Push to Devices to push your configuration changes to your managed firewalls.
SD-WAN Administration 64 ©2026 Palo Alto Networks, Inc.
Enable SD-WAN with Auto VPN
Configure Certificate-based Authentication for Strong
Security
Where Can I Use This? What Do I Need?
• Prisma Access
• NGFW
• SD-WAN plugin 3.2.0 and later releases
Advanced SD-WAN for NGFW
You can authenticate an SD-WAN device using either of the following two authentication types:
```
• (Default authentication type) Pre-shared key
```
```
• (SD-WAN plugin 3.2.0 and later releases) Certificate
```
When you create a new SD-WAN cluster or refresh the key with an SD-WAN plugin version
earlier than 3.2.0, the SD-WAN plugin generates the pre-shared key automatically. In addition
to the pre-shared key authentication type, we provide certificate-based authentication with SD-
WAN plugin 3.2.0 and later releases for next-generation firewalls to fulfill your security needs.
Take your security to the next level with stronger authentication and validation for all SD-WAN
sites with certificate-based authentication.
We support certificate-based authentication on all software and hardware devices running legacy
or advanced routing engines that support SD-WAN.
Follow the steps mentioned in the upgrade and downgrade considerations before you upgrade or
downgrade your current SD-WAN plugin.
Use the following workflow to configure certificate-based authentication for your SD-WAN
```
device:
```
STEP 1 | Log in to the Panorama Web Interface.
SD-WAN Administration 65 ©2026 Palo Alto Networks, Inc.
Enable SD-WAN with Auto VPN
STEP 2 | Generate a certificate for SD-WAN devices on Panorama.
1. Select Panorama > Certificate Management > Certificates.
2. Create a self-signed root CA certificate or import a certificate from your enterprise CA.
Based on the root CA, generate devices certificate for an SD-WAN device. We do not
support SCEP-generated certificates.
The generated certificate must be unique for each SD-WAN device. That is, you can't
generate a certificate and share it among multiple SD-WAN devices.
Keep the following in mind while generating the branch and hub firewall certificates that
is used for SD-WAN tunnel authentication:
• Two different hub devices can use the same hub certificate.
• Two different branch devices can use the same branch certificates if the following
conditions are met:
• Branch devices are not part of the same VPN cluster
• There is no common hub device between the VPN clusters that these branch
devices would be part of
```
• (HA deployments only) Two different branch devices can also have the same branch
```
certificates if they are configured as HA members.
• If the hub device is common between VPN clusters, certificates for branch devices
part of these VPN clusters should have unique certificates with all attributes having
unique values. If you don't ensure the uniqueness of the certificate and its values,
```
then commit will fail on the hub device (no commit failure on Panorama).
```
```
Also ensure that the leaf certificates (branch and hub firewall certificates) used
```
for SD-WAN tunnel authentication are generated meeting the following criteria:
• Key usage should have digital signatures.
• All certificates must be signed by the same root CA.
• The device certificate must be directly signed by the root CA.
• Certificate format should be PKCS12.
The certificate attributes are used for determining the local ID and peer ID for IKE
gateways. Hence, the leaf certificates, that is, the branch and hub firewall certificates
that are used for SD-WAN tunnel authentication must be generated with the following
SD-WAN Administration 66 ©2026 Palo Alto Networks, Inc.
Enable SD-WAN with Auto VPN
three certificate attributes and each certificate attribute should be assigned with three
unique attribute values. Otherwise, a commit error will be thrown.
```
• FQDN (Host Name)
```
```
• IP address (IP)
```
```
• User FQDN (Alt Email)
```
It's mandatory to have unique Host Name, IP, and Alt Email certificate
attributes among all certificates. That is, none of the certificates should have
these attribute values in common.
In the below example, NewCertificate is generated with the total of nine mandatory
certificate attributes. The Host Name certificate attribute is configured with three
unique attribute values: pan-fw01.yourcompany.com, pan-fw02.yourcompany.com,
and pan-fw03.yourcompany.com. The IP certificate attribute is configured with three
unique attribute values: 192.0.2.0, 192.0.2.1, and 192.0.2.2. The Alt Email certificate
attribute is configured with three unique attribute values: sales@yourcompany.com,
IT@yourcompany.com, and customercare@yourcompany.com.
SD-WAN Administration 67 ©2026 Palo Alto Networks, Inc.
Enable SD-WAN with Auto VPN
```
STEP 3 | (Optional) Configure a Certificate Profile that includes the root CA and intermediate CA for
```
secure server communication.
1. Select Panorama > Certificate Management > Certificate Profile.
2. Configure a certificate profile.
If you configure an intermediate CA as part of the Certificate Profile, you must also
include the root CA.
This Certificate Profile defines how the SD-WAN hubs and the branches authenticate
mutually.
STEP 4 | Import the CA certificates to validate the identity of the SD-WAN devices.
1. Panorama > Certificate Management > Certificates
2. Import the CA certificate and the key pair on Panorama for each SD-WAN device in a
```
cluster or import multiple certificates using Multiple Certificates (.tar). Use CSV to bulk
```
import the certificates into the Panorama management server. The CSV allows you to
import multiple certificates at once, rather than adding each certificate manually.
3. Commit your changes. It's important to commit after importing the certificates for the
imported certificates to be available for further configuration.
STEP 5 | Configure a certificate-based authentication type while adding an SD-WAN hub or branch
firewall to be managed by the Panorama management server. When adding your devices,
```
you specify what type of device it is (branch or hub), an authentication type for the device,
```
and you give each device its site name for easy identification.
1. Select Panorama > SD-WAN > Devices to add an SD-WAN device (SD-WAN hub or
```
branch firewall) to be managed by the Panorama management server.
```
2. Select the VPN Tunnel tab and configure the authentication type. For certificate-
based authentication, select Certificate and configure the certificate-related fields. It's
mandatory to select an authentication type while adding an SD-WAN device.
STEP 6 | Configure certificate-based authentication when onboarding PAN-OS firewalls to Prisma
Access.
1. Select Panorama > SD-WAN > Devices to select the SD-WAN branch firewall to
connect to the Prisma Access hub and configure the connection.
2. Select Prisma Access Onboarding and Add a compute node to a Region. In the VPN
Tunnel, it's mandatory to select the authentication type to authenticate the CN
```
(Prisma Access hub). For certificate-based authentication, select Certificate as the
```
SD-WAN Administration 68 ©2026 Palo Alto Networks, Inc.
Enable SD-WAN with Auto VPN
Authentication type and configure the certificate-related fields. It's mandatory to select
an authentication type while onboarding PAN-OS firewalls to Prisma Access.
Ensure that you select the same authentication type for all the branch devices
and the Prisma Access hub that is added. A commit failure occurs on Panorama
if you try to use different authentication types for the branch and the Prisma
hub.
STEP 7 | Configure certificate-based authentication while planning your topology for SD-WAN with
Auto VPN.
1. Select Panorama > SD-WAN > VPN Clusters.
2. Select the VPN cluster Type.
3. Select the Authentication Type as Certificate. It's mandatory to specify the
authentication type to add a device in a VPN cluster. A VPN cluster should have the
same authentication type selected for all its devices. You can't change the authentication
type of an SD-WAN device that has been added to a VPN cluster already. If you want
to change, then remove the VPN cluster and its SD-WAN devices and configure it again
with the authentication type of your choice. By default, we support the pre-shared
```
key authentication type for the devices in a VPN cluster (if you have not selected the
```
```
certificate type manually).
```
STEP 8 | Commit your configuration changes.
STEP 9 | Select Push to Devices to push your configuration changes to your managed firewalls.
SD-WAN Administration 69 ©2026 Palo Alto Networks, Inc.
Enable SD-WAN with Auto VPN
Quickly Add Multiple SD-WAN Devices with Bulk
Import
Where Can I Use This? What Do I Need?
• NGFW Advanced SD-WAN for NGFW
Add multiple SD-WAN devices to quickly onboard branch and hub firewalls, rather than manually
adding each device one at a time. When adding your devices, you specify what type of device it is
```
(branch or hub) and you give each device its site name for easy identification. Before adding your
```
devices, plan your SD-WAN configuration to ensure you have all the required IP addresses and
that you understand the SD-WAN topology. This helps reduce any configuration errors.
If you want to have active/passive HA running on two branch firewalls or two hub
firewalls, don’t add those firewalls as SD-WAN devices in your CSV file. You’ll add them as
HA peers separately when you configure SD-WAN devices in HA mode.
If you’re using BGP routing, you must add a Security policy rule to allow BGP from the
internal zone to the hub zone and from the hub zone to the internal zone. If you want to
```
use 4-byte autonomous system numbers (ASNs), you must first enable 4-byte ASNs for
```
the virtual router.
If you have preexisting zones for your Palo Alto Networks firewalls, you’ll be mapping them to the
predefined zones used in SD-WAN.
STEP 1 | Log in to the Panorama Web Interface.
STEP 2 | Select Panorama > SD-WAN > Devices > Device CSV and Export an empty SD-WAN device
CSV. The CSV allows you to import multiple branch and hub devices at once, rather than
adding each device manually.
SD-WAN Administration 70 ©2026 Palo Alto Networks, Inc.
Enable SD-WAN with Auto VPN
STEP 3 | Populate the SD-WAN device CSV with the branch and hub information and save the CSV.
All fields are required unless noted otherwise. Enter the following for each hub and branch:
• device-serial—The serial number of the branch or hub firewall.
• type—Specify whether the device is a branch or a hub.
• site—Enter the SD-WAN device site name to help you identify the geographical location or
purpose of the device.
The SD-WAN Site name supports all upper-case and lower-case alphanumerical
and special characters. Spaces aren’t supported in the Site name and result in
```
monitoring (Panorama > SD-WAN > Monitoring) data for that site not to be
```
displayed.
```
All SD-WAN devices, including SD-WAN devices in a high availability (HA)
```
configuration, must have a unique Site name.
```
• (Required for pre-existing customers) (SD-WAN plugin 3.1.0 and earlier versions) Map your
```
pre-existing zones to predefined zones used for SD-WAN.
When you map your existing zones to an SD-WAN zone, you must modify your
security policy rules and add the SD-WAN zones to the correct Source and
Destination zones.
• zone-internet—Enter the names of pre-existing zones that SD-WAN traffic will egress to
reach the internet.
• zone-to-branch —Enter the names of pre-existing zones that SD-WAN traffic will egress
to reach a branch.
• zone-to-hub—Enter the names of pre-existing zones that SD-WAN traffic will egress to
reach a hub.
• zone-internal—Enter the names of pre-existing zones that SD-WAN traffic will egress to
reach an internal zone.
```
• (SD-WAN plugin 3.1.0 and earlier versions) vr-name—Enter the name of the virtual router
```
or logical router to use for routing between the SD-WAN hub and branches. By default,
SD-WAN Administration 71 ©2026 Palo Alto Networks, Inc.
Enable SD-WAN with Auto VPN
Panorama creates an sdwan-default virtual router and can automatically push router
configurations.
```
(SD-WAN plugin 3.1.0 version) Enter the logical router name if you have enabled advanced
```
routing.
```
• (SD-WAN plugin 3.2.0 and later versions) router-name—Enter the virtual router to use for
```
routing between the SD-WAN hub and branches. By default, Panorama creates an sdwan-
default virtual router and enables Panorama to automatically push router configurations.
• vif-link-tag—Specify a link tag to identify the hub when applications and services use this
link during SD-WAN traffic distribution and failover.
```
• (Optional) router-id—Specify the BGP router ID, which must be unique among all virtual or
```
logical routers.
Enter the Loopback Address as the router ID.
Before implementing SD-WAN with BGP routing in an environment where BGP is
already in use, ensure that the BGP configuration generated by the SD-WAN plugin
doesn’t conflict with your existing BGP configuration. For example, you must use
the existing BGP AS number and router ID values for the corresponding SD-WAN
device values.
```
• (Optional) as-number—Enter the ASN of the private AS to which the virtual router on the
```
hub or branch belongs. The SD-WAN plugin supports only private autonomous systems.
The ASN must be unique for every hub and branch. The 4-byte ASN range is 4,200,000,000
to 4,294,967,294 or 64512.64512 to 65535.65534. The 2-byte ASN range is 64512 to
65534.
Use a 4-byte private ASN.
Before implementing SD-WAN with BGP routing in an environment where BGP is
already in use, ensure that the BGP configuration generated by the SD-WAN plugin
doesn’t conflict with your existing BGP configuration. For example, you must use
the existing BGP AS number and router ID values for the corresponding SD-WAN
device values.
```
• (Optional) ipv4-bgp-enable—Specify yes or no to enable or disable BGP for IPv4 addresses.
```
```
• (Optional) loopback-address—Specify a static loopback IPv4 address for BGP peering. SD-
```
WAN plugin 3.1.1 and later 3.1 releases support an IPv6 loopback address for BGP peering.
```
• (Optional) remove-private-as—Specify no to disable the Remove Private AS option (default
```
```
is enabled) if you have endpoints that need to exchange routes with a hub or branch firewall
```
in an SD-WAN BGP topology and therefore you don’t want to remove private AS numbers
```
(64512 to 65534) from the AS_PATH attribute in BGP Updates.
```
This setting applies to all BGP peer groups on the branch or hub firewall. If you need this
setting to differ among BGP peer groups or peers, you must configure the setting outside of
the SD-WAN plugin.
```
• (Optional) prefix-redistribute—Enter IP prefixes that the branch informs the hub it can
```
```
reach. To add more than one prefix, separate prefixes with a space, an ampersand (&), and
```
SD-WAN Administration 72 ©2026 Palo Alto Networks, Inc.
Enable SD-WAN with Auto VPN
```
a space; for example, 192.2.10.0/24 & 192.168.40.0/24. By default, the branch firewall
```
advertises all locally connected internet prefixes to the hub.
```
Palo Alto Networks doesn’t redistribute the branch office default route(s) learned
```
from the ISP.
```
• (Optional) (SD-WAN plugin 3.2.0 and later versions) ipv6-bgp-enable—Specify yes/no to
```
enable/disable BGP for IPv6 addresses.
```
• (Optional) (SD-WAN plugin 3.2.0 and later versions) ipv6-loopback-address—Specify a
```
static loopback IPv6 address for BGP peering.
```
• (Optional) (SD-WAN plugin 3.2.0 and later versions) ipv6-prefix-redistribute—Enter IPv6
```
prefixes to redistribute to the hub router from the branch. By default, all locally connected
internet IPv6 prefixes are advertised to the hub location.
```
• (Optional) copy-tos-header—Specify yes/no to enable/disable this option to copy the Type
```
```
of Service (TOS) header from the inner IP header to the outer IP header of the encapsulated
```
packets in order to preserve the original TOS information.
```
• (SD-WAN plugin 3.2.0 and later versions) authentication-type—Specify the authentication
```
```
type that the device (hub or branch) supports: pre-shared key or certificate authentication.
```
```
• (Only for Certificate authentication type) (SD-WAN plugin 3.2.0 and later versions)
```
certificate-name—Enter a certificate name. The name is case-sensitive and can have up to
63 characters on the firewall or up to 31 characters on the Panorama. It must be unique and
use only letters, numbers, hyphens, and underscores.
For pre-shared key authentication type, this field should be left empty.
STEP 4 | Import the SD-WAN device CSV into Panorama.
Verify that there are no pending commits on Panorama or the import fails.
1. On Panorama, Select Panorama > SD-WAN > Devices > Device CSV and Import the
CSV you edited in the previous step.
2. Browse and select the SD-WAN device CSV.
3. Click OK to import the SD-WAN devices.
SD-WAN Administration 73 ©2026 Palo Alto Networks, Inc.
Enable SD-WAN with Auto VPN
STEP 5 | Verify that your SD-WAN devices were successfully added.
You will be able to view the certificate-related fields for SD-WAN plugin 3.2.0 and later
versions.
STEP 6 | Commit your configuration changes.
STEP 7 | Select Push to Devices to push your configuration changes to your managed firewalls.
SD-WAN Administration 74 ©2026 Palo Alto Networks, Inc.
Enable SD-WAN with Auto VPN
Configure SD-WAN Devices in HA Mode
Where Can I Use This? What Do I Need?
• NGFW Advanced SD-WAN for NGFW
```
You can configure two firewalls as a branch in active/passive HA mode (or two firewalls as a hub
```
```
in active/passive HA mode) to be part of your SD-WAN environment. In this case, Panorama™
```
needs to push the same configuration to the active peer and the passive peer, rather than treat
the two firewalls individually. To make that happen, you configure active/passive HA before
adding the devices for SD-WAN, so that Panorama is aware the devices are HA peers and pushes
```
the same configuration to them. (Only HA active/passive mode is supported.)
```
Read through the following procedure before you begin so you don’t Commit after adding
your HA peers as SD-WAN devices.
In HA, the firewall does not synchronize SD-WAN session distribution statistics. After
```
an HA failover, the session distribution statistics display only statistics of new sessions;
```
statistics of existing sessions are lost.
• Versions Earlier Than 3.4.0
• 3.4.0 and Later
Versions Earlier Than 3.4.0
STEP 1 | Before you enable SD-WAN on your HA peers, configure active/passive HA on two firewall
models that support SD-WAN.
STEP 2 | Add the HA peers as SD-WAN devices, but don’t perform the last step to Commit.
STEP 3 | In Panorama, select Panorama > Managed Devices > Summary.
STEP 4 | At the bottom of the screen, select Group HA Peers. Confirm that under the Status display,
the HA Status column includes the two firewalls, one active and one passive. Panorama is
aware of the HA status and will push the same SD-WAN configuration to the two HA peers
when you commit.
STEP 5 | Commit and Commit and Push.
3.4.0 and Later
```
(PAN-OS 12.1.2 and later releases, SD-WAN 3.4.0 and later releases) (Mandatory for HA peers)
```
```
Configure high availability (HA) devices in SD-WAN with consistent configuration and ease of
```
management.
```
In a SD-WAN infrastructure, managing high availability (HA) device configurations has been a
```
challenging and error-prone process. To simplify the HA firewalls, we provide a single-window
SD-WAN Administration 75 ©2026 Palo Alto Networks, Inc.
Enable SD-WAN with Auto VPN
configuration that automatically synchronizes settings between active and passive devices,
thereby reducing the potential for configuration mismatches.
When you upgrade SD-WAN plugin from an earlier version to 3.4.0, the configuration
```
between HA peers will be synchronized automatically (if the devices were already added
```
```
before upgrade).
```
STEP 1 | Log in to the Panorama web interface.
STEP 2 | Navigate to Panorama > SD-WAN > Devices and select the active device in the HA pair.
STEP 3 | Enable Add HA Peer. When enabled, the SD-WAN plugin will automatically discover the HA
peer and populates the HA Peer Name.
• You can’t add HA firewall pairs individually. Configure both active and passive
firewalls together by enabling the Add HA Peer option.
• Configuration changes synchronize automatically between HA peer devices.
```
• (For Prisma® Access devices only) Note the following before Prisma® Access
```
```
configuration:
```
• Prisma Access interfaces added on active devices don’t appear in passive device
configuration leading to configuration inconsistency between HA peers.
• Adding Prisma Access configuration to passive devices results in an error.
Therefore, you must only add the Prisma Access configuration on the active
device.
• Empty Prisma Access configuration on passive device does not impact active
device configuration. Active device Prisma Access configuration remains
preserved despite passive being unconfigured.
SD-WAN Administration 76 ©2026 Palo Alto Networks, Inc.
Enable SD-WAN with Auto VPN
```
STEP 4 | (Mandatory) Enter the HA Peer Site name for the HA peer device (or secondary device) to
```
identify the geographical location or purpose of the device.
• It's mandatory to specify the site name for the HA peer device configuration.
• The HA Peer Site name supports all upper-case and lower-case alphanumerical and
special characters. Site names can’t contain spaces.
STEP 5 | Select OK.
If there is a mismatch between the active and passive Panorama configurations, a warning
symbol appears next to the device name in the SD-WAN devices list. In this case, perform the
following steps:
• Select the Warning icon to view a more detailed warning message.
• Review the configuration differences.
• Select Add HA Peer to synchronize configurations.
• Delete the passive device and add it again by enabling Add HA Peer on the active device.
Generally, a warning message appears when the firewall was configured and added separately
before converting to a HA pair. You will also encounter the warning when active and passive
firewalls have different configurations.
STEP 6 | Commit and Commit and Push.
SD-WAN Administration 77 ©2026 Palo Alto Networks, Inc.
Enable SD-WAN with Auto VPN
Onboard PAN-OS Firewalls to Prisma Access for Cloud-
based Security
Where Can I Use This? What Do I Need?
• Prisma Access
• NGFW
• SD-WAN plugin 2.2 and later versions
Advanced SD-WAN for NGFW
SD-WAN plugin 2.2 and later versions provides Prisma Access hub support, in which PAN-OS
```
firewalls connecting to Prisma Access compute nodes (CNs) achieve cloud-based security in an
```
SD-WAN hub-and-spoke topology. In this topology, the SD-WAN hubs are Prisma Access CNs
```
(IPSec Termination Nodes) and the SD-WAN branches are PAN-OS firewalls. A maximum of four
```
```
hubs (any combination of PAN-OS hubs participating in DIA AnyPath and Prisma Access hubs) are
```
supported. SD-WAN automatically creates IKE and IPSec tunnels that connect the branch to the
hub. Review the system requirements for SD-WAN and Prisma Access.
It's important to configure Prisma Access first, and then configure SD-WAN.
• If you're starting a brand new Prisma Access configuration, read the Prisma Access
Administrator’s Guide and complete Phase 1 and then Phase 2 configuration steps.
• If you already have Prisma Access running, ensure Phase 1 is complete, and then
complete Phase 2.
The following flowchart shows the order of the two configuration phases and basic steps within
each phase. The full Prisma Access prerequisites with links and the configuration steps for SD-
WAN follow the flowchart.
PHASE 1—PRISMA ACCESS PHASE 2—SD-WAN
```
(COMPLETE PHASE 1 FIRST) (BEGIN ONLY AFTER
```
```
COMPLETING PHASE 1)
```
1. Set up the infrastructure subnet,
infrastructure BGP AS, template stack and
device group for a tenant.
2. Set up template stacks, templates, device
groups, trust and untrust zones, and
bandwidth allocation for specific regions.
3. Ensure your Prisma Access deployment is
licensed for remote networks.
4. Ensure your deployment allocates
bandwidth per compute location, instead
of by location.
1. Configure a branch firewall with an
interface that has SD-WAN enabled.
2. Log in to the Panorama web interface.
3. Specify the BGP local address pool for
loopback addresses.
4. Select the SD-WAN branch firewall to
connect to the Prisma Access hub and
configure the connection.
5. Commit and Push the configuration to the
cloud.
6. Verify that onboarding is complete.
SD-WAN Administration 78 ©2026 Palo Alto Networks, Inc.
Enable SD-WAN with Auto VPN
PHASE 1—PRISMA ACCESS PHASE 2—SD-WAN
```
(COMPLETE PHASE 1 FIRST) (BEGIN ONLY AFTER
```
```
COMPLETING PHASE 1)
```
5. Ensure you have assigned bandwidth to
the compute location that corresponds to
the location to which you want to onboard.
6. Perform a local commit and push to the
Prisma Access cloud.
7. Synchronize the branch firewall to Prisma
Access.
8. Commit to Panorama.
9. Push to Devices.
10.View the new interface that was created.
11.Verify the IPSec tunnel is up.
12.Verify the IKE gateway is up.
13.Create an SD-WAN policy rule to generate
monitoring data.
14.Commit and Commit and Push to branch
firewalls.
15.Monitor Prisma Access hub application and
link performance.
Before you connect SD-WAN to Prisma Access, you must have a branch firewall with an interface
that has SD-WAN enabled. Additionally, ensure you have performed the following Prisma Access
```
prerequisites for one or more tenants; these are the Phase 1 steps:
```
1. For Panorama > Cloud Services > Configuration, set up the infrastructure subnet,
infrastructure BGP AS, template stack and device group for a tenant on the Service Setup
page.
2. On the Remote Networks page, set up template stacks, templates, device groups, trust and
untrust zones, and bandwidth allocation for specific regions.
3. Ensure your Prisma Access deployment is licensed for remote networks by selecting Panorama
> Licenses and checking your license information.
• Licenses available after November 17, 2020 show the amount of licensed bandwidth you
have for remote networks in the Net Capacity area.
• Licenses available before November 17, 2020 show the available remote network
bandwidth in the GlobalProtect Cloud Service for Remote Networks area under Total
Mbps.
4. Ensure your deployment allocates bandwidth per compute location, instead of by location.
5. Ensure you have assigned bandwidth to the compute location that corresponds to the location
to which you want to onboard. Prisma Access allocates one IPSec termination node per 500
Mbps of bandwidth you allocate to a region.
6. Perform a local commit and push to the Prisma Access cloud.
After you have performed the preceding steps for Phase 1 with Prisma Access, perform the
following Phase 2 steps for SD-WAN.
STEP 1 | Log in to the Panorama Web Interface.
SD-WAN Administration 79 ©2026 Palo Alto Networks, Inc.
Enable SD-WAN with Auto VPN
STEP 2 | Specify the BGP local address pool for loopback addresses.
1. Select Panorama > SD-WAN > VPN Clusters.
2. At the bottom of the screen, select BGP Prisma Address Pool.
3. Add an unused private subnet (prefix and netmask) for the local BGP addresses for
Prisma Access.
4. Click OK.
5. Commit.
Do not simply change an existing address pool if Prisma Access is already
onboarded. If you need to change an address pool, perform the following steps
during a maintenance window to update the SD-WAN branch and the Prisma
Access CN with your address pool changes:
1. Use Panorama to access an SD-WAN branch and delete the existing
```
onboarding that the address pool change will impact; then do a local Commit.
```
2. Update the VPN address pool, and then do a local Commit.
3. Perform the Prisma Access onboarding again, and then do a local Commit
and Push.
SD-WAN Administration 80 ©2026 Palo Alto Networks, Inc.
Enable SD-WAN with Auto VPN
STEP 3 | Select the SD-WAN branch firewall to connect to the Prisma Access hub and configure the
connection.
1. Select Panorama > SD-WAN > Devices.
2. Select the branch firewall on which you enabled SD-WAN, whose name then populates
the Name field.
3. Select the Type of device as Branch.
4. Select the Router Name.
5. Enter the Site.
All SD-WAN devices must have a unique Site name.
6. Select Prisma Access Onboarding and Add.
7. Select a local, SD-WAN-enabled Interface on the firewall to connect to the Prisma
Access hub.
8. Select a Prisma Access Tenant (select default for a single tenant environment).
All SD-WAN interfaces on a branch firewall must use the same Prisma Access tenant.
9. Enter a helpful Comment.
SD-WAN Administration 81 ©2026 Palo Alto Networks, Inc.
Enable SD-WAN with Auto VPN
10. Add a compute node to a Region by selecting the region where the CN (Prisma Access
```
hub) is located.
```
There can be multiple regions per interface.
11. (PAN-OS 11.2.11 and later versions, and SD-WAN plugin 3.3.4 and later versions)
Select the Hybrid SASE Failover checkbox. Enabling this checkbox activates the Hybrid
SASE Failover functionality for your selected branch. This feature requires at least two
branches with it enabled to function correctly.
By default, this is disabled.
12. Select an IPSec Termination Node (GP gateway) from the list of nodes; the list is based
on the nodes that Prisma Access spun up for the region earlier. You are choosing the hub
SD-WAN Administration 82 ©2026 Palo Alto Networks, Inc.
Enable SD-WAN with Auto VPN
to which this branch connects. SD-WAN Auto VPN configuration builds IKE and IPSec
relationships and tunnels with this node.
13. Enable BGP for communication between the branch and hub (Enable is the default).
14. Advertise Default Route to allow the Prisma Access hub’s default route to be advertised
to the branch firewall.
15. Summarize Mobile User Routes before advertising to have the Prisma Access hub
advertise summarized mobile user IP subnet routes, thereby reducing the number of
advertisements to the branches.
16. Don’t Advertise Prisma Access Routes to prevent the IPSec Termination Node/hub from
advertising its Prisma Access routes to the SD-WAN branches.
17. Enter the Secret for authentication of BGP communications and Confirm Secret.
18. (SD-WAN plugin 3.2.0 and later versions) Configure the VPN tunnel parameters and
authentication type to authenticate the PAN-OS firewall and Prisma Access hub.
1. (Optional) If you want to preserve the Type of Service (ToS) information in the
encapsulated packets, select Copy TOS Header.
```
If there are multiple sessions inside the tunnel (each with a different ToS
```
```
value), copying the ToS header can cause the IPSec packets to arrive out of
```
order.
2. Select the Authentication: Pre Shared Key or Certificate.
Ensure that you select the same authentication type for all the branch
devices and the Prisma Access device that is added.
The pre-shared key is automatically generated if selected as an authentication type
for a region.
19. (SD-WAN plugin 3.2.0 and later versions) Select Certificate to configure certificate-
based authentication.
20. (SD-WAN plugin 3.2.0 and later releases) (Only if enabling Certificate authentication
```
type) The certificate must be present on the Panorama before performing Prisma Access
```
SD-WAN Administration 83 ©2026 Palo Alto Networks, Inc.
Enable SD-WAN with Auto VPN
Onboarding of the SD-WAN branch firewall. We do not support SCEP-generated
certificate. Select a Local Certificate—one that is already on the Panorama.
Ensure the following for the certificate that you have in the Panorama for the successful
Prisma Access onboarding process:
• The certificate must be unique for each SD-WAN device. That is, you can't share the
certificate among multiple SD-WAN devices.
Keep the following in mind while generating the branch and hub firewall certificates
that is used for SD-WAN tunnel authentication:
• Two different hub devices can use the same hub certificate.
• Two different branch devices can use the same branch certificates if the following
conditions are met:
• Branch devices are not part of the same VPN cluster
• There is no common hub device between the VPN clusters that these branch
devices would be part of
```
• (HA deployments only) Two different branch devices can also have the same
```
branch certificates if they are configured as HA members.
• If the hub device is common between VPN clusters, certificates for branch devices
part of these VPN clusters should have unique certificates with all attributes
having unique values. If you don't ensure the uniqueness of the certificate and its
```
values, then commit will fail on the hub device (no commit failure on Panorama).
```
```
Also ensure that the leaf certificates (branch and hub firewall certificates)
```
used for SD-WAN tunnel authentication are generated meeting the following
```
criteria:
```
• Key usage should have digital signatures
• All certificates must be signed by the same root CA
• The device certificate must be directly signed by the root CA
• Certificate format should be PKCS12
• The certificate attributes are used for determining the local ID and peer ID for IKE
gateways. Hence, the leaf certificates, that is, the branch and hub firewall certificates
that is used for SD-WAN tunnel authentication must be generated with the following
three certificate attributes and each certificate attribute should be assigned with
three unique attribute values. Otherwise, a commit error will be thrown.
```
• FQDN (Host Name)
```
```
• IP address (IP)
```
```
• User FQDN (Alt Email)
```
It's mandatory to have unique Host Name, IP, and Alt Email certificate
attributes among all certificates. That is, none of the certificates should have
these attribute values in common.
In the below example, NewCertificate is generated with the total of nine mandatory
certificate attributes. The Host Name certificate attribute is configured with three
SD-WAN Administration 84 ©2026 Palo Alto Networks, Inc.
Enable SD-WAN with Auto VPN
unique attribute values: pan-fw01.yourcompany.com, pan-fw02.yourcompany.com,
and pan-fw03.yourcompany.com. The IP certificate attribute is configured with three
unique attribute values: 192.0.2.0, 192.0.2.1, and 192.0.2.2. The Alt Email certificate
attribute is configured with three unique attribute values: sales@yourcompany.com,
IT@yourcompany.com, and customercare@yourcompany.com.
21. (SD-WAN plugin 3.2.0 and later versions) (Optional) (Only if enabling Certificate
```
authentication type) Choose a Certificate Profile. A Certificate Profile contains
```
information about how to authenticate the peer gateway.
22. (SD-WAN plugin 3.2.0 and later versions) (Optional) Enable strict validation of peer’s
extended key use to control strictly how the key can be used.
23. Select a Link Tag for the hub.
When you want to enable ECMP for a Prisma Access hub, onboard more than
```
one branch interface to the same compute node (CN) and use the same Link Tag
```
on those branch interfaces.
24. Click OK. The display will include a Peer AS number and the Tunnel Monitor IP address
provided by Prisma Access.
SD-WAN Administration 85 ©2026 Palo Alto Networks, Inc.
Enable SD-WAN with Auto VPN
STEP 4 | Commit and Push the configuration to the cloud, where Prisma Access spins up the correct
number of IPSec Termination Nodes based on requested bandwidth.
When more than one IPSec tunnel is going to the same CN, the Prisma Access
configuration has ECMP enabled with symmetric return, as shown in this Prisma
Access example:
SD-WAN Administration 86 ©2026 Palo Alto Networks, Inc.
Enable SD-WAN with Auto VPN
STEP 5 | Verify that onboarding is complete.
1. Select Panorama > Cloud Services > Status and verify that the Remote Networks
Deployment Status displays success.
2. Select the Remote Networks Deployment Status details.
3. Confirm that the Prisma Access node completion displays 100%.
SD-WAN Administration 87 ©2026 Palo Alto Networks, Inc.
Enable SD-WAN with Auto VPN
```
STEP 6 | Synchronize the branch firewall to Prisma Access to retrieve the service IP address(es) of the
```
CNs.
1. Select Panorama > SD-WAN > Devices.
2. Select the SD-WAN branch device.
3. Select Prisma Access Onboarding and Sync To Prisma (and respond to message to
```
continue). Repeat for each branch device.
```
After the sync to Prisma is successful, you will see the Prisma Access
configuration parameters on the SD-WAN branch firewall. If not, wait for
approximately 15 minutes and repeat the Sync to Prisma. If necessary, go to
```
the Prisma Access plugin and verify that the CN onboarding has finished (you
```
```
can see the CN with the bandwidth and IP addresses assigned). After that
```
verification, retry Sync To Prisma.
STEP 7 | Commit to Panorama.
STEP 8 | Push to Devices to push to the local branch firewall. Edit Selections to select the Push Scope
Selection. Select the correct Template and Device Group.
STEP 9 | On the branch firewall, select Network > Interfaces > SD-WAN and see the new interface
that was created with the Link Tag you created, assigned to the Security Zone named zone-
to-pa-hub, and with the IPSec tunnel connecting to the CN.
STEP 10 | Select Network > IPSec Tunnels and verify the IPSec tunnel is up.
STEP 11 | Select Network > Network Profiles > IKE Gateways and verify the IKE gateway is up.
SD-WAN Administration 88 ©2026 Palo Alto Networks, Inc.
Enable SD-WAN with Auto VPN
STEP 12 | Create an SD-WAN policy rule to generate monitoring data.
This step is required to baseline Prisma Access Hub latency, jitter, and packet loss data for
accurate traffic distribution. SD-WAN monitoring data is generated from traffic that matches
your SD-WAN policy rules.
1. Define path selection for SD-WAN traffic using traffic distribution profile.
2. Define your custom SD-WAN application thresholds (using path quality profiles) with
high latency, jitter, and packet loss thresholds.
A Path Quality profile is required to create an SD-WAN policy rule. Creating a Path
Quality profile with high thresholds allows you to baseline latency, jitter, and packet loss
for the Prisma Access hub without causing app to swap to a different link.
3. Configure an SD-WAN policy rule.
STEP 13 | Commit and Commit and Push to branch firewalls.
```
STEP 14 | (Only if enabling Pre Shared Key authentication type) Refresh the Prisma IKE pre-shared key.
```
If you need to change the current Prisma IKE key that is used to secure the IPSec
connection between the branch and the Prisma hub, perform this step to randomly
generate a new key for the tunnel and update both sides of the tunnel. Perform this
step when the hub and branch are not busy.
Do not create an IKE gateway manually with a name beginning with “gw_” because
such names are reserved for Prisma IKE creation during onboarding. This step to
refresh the Prisma IKE pre-shared key refreshes all such named IKE gateways if there
are any apart from those created by Prisma Access.
1. Select Panorama > SD-WAN > Devices and select a device.
2. At the bottom of the screen, select Refresh Prisma IKE Key.
3. A message appears notifying you that Refreshing the IKE key will update
all SD-WAN tunnels between the branch and the Prisma Access hub
and will require a simultaneous configuration push to all branch
and Prisma Access hub devices. Best practice recommendation is
to perform the refresh during a maintenance window as traffic
can be affected. Do you wish to continue? Select Yes if you wish to
continue.
SD-WAN Administration 89 ©2026 Palo Alto Networks, Inc.
Enable SD-WAN with Auto VPN
STEP 15 | Commit and Commit and Push to branch firewalls.
STEP 16 | Monitor Prisma Access Hub Application and Link Performance to understand the baseline
latency, jitter, and packet loss for the links to Prisma Access.
This step is required to gather accurate latency, jitter, and packet loss data to fine-tune your
Prisma Access hub path quality profiles.
SD-WAN Administration 90 ©2026 Palo Alto Networks, Inc.
Enable SD-WAN with Auto VPN
Plan Your Topology for SD-WAN with Auto VPN
Where Can I Use This? What Do I Need?
```
• NGFW (Managed by PAN-OS or
```
```
Panorama)
```
```
• NGFW (Managed by Strata Cloud
```
```
Manager)
```
Advanced SD-WAN for NGFW
One of these:
AIOps for NGFW Premium or Strata
Cloud Manager Pro
Strata Cloud Manager Essentials
```
(Supports only NGFWs)
```
In your SD-WAN configuration, you must configure one or more VPN clusters to determine which
branches communicate with which hubs and creates a secure connection between the branch and
hub devices. VPN clusters are logical groupings of devices, so consider things such as geographical
location or function when logically grouping your devices.
PAN-OS 10.0.2 and earlier releases support only the hub-spoke SD-WAN VPN topology.
SD-WAN full mesh VPN topology is supported in PAN-OS 10.0.3 and later releases.
PAN-OS®10.0.3 and later releases support both hub-spoke and full mesh SD-WAN VPN
topologies. In a hub-spoke topology, a centralized firewall hub at a primary office or location acts
as the gateway between branch devices. The hub-to-branch connection is a VPN tunnel. In this
configuration, traffic between branches must pass through the hub.
```
The first time you configure a virtual SD-WAN interface with direct internet access (DIA) links
```
for an SD-WAN hub or branch firewall, a VPN cluster called autogen_hubs_cluster is
automatically created and the SD-WAN firewall is automatically added to the VPN cluster. This
allows the Panorama® management server to monitor SD-WAN application and link performance
for devices that are protected by the SD-WAN firewall and accessing resources outside of your
corporate network. Additionally, any SD-WAN firewall with DIA links that you configure in the
future are automatically added to the autogen_hubs_cluster VPN cluster containing all hubs
and branches with DIA links to enable Panorama to monitor application and link performance.
The autogen_hubs_cluster is purely for monitoring application and link health, and not to
create VPN tunnels between the hubs and branches with DIA links. If you need to connect hubs
and branches with VPN tunnels, you must create a new VPN cluster and add all the required hubs
and branches to that cluster.
When you select the Pre-shared key as an Authentication Type, a strong, random IKE pre-shared
key is created for all hubs and branches in the VPN cluster to secure the VPN tunnels, and each
firewall has a master key that encrypts the pre-shared key.
The SD-WAN plugin generates the pre-shared key and encrypts it with the master key of
Panorama. When you push the SD-WAN plugin configuration to the firewall, the firewall
must have the same master key to decrypt the pre-shared key shared by the SD-WAN
plugin. That is, the master key must match between the Panorama and its managed
firewalls. Otherwise, the push will fail on the SD-WAN firewalls.
SD-WAN Administration 91 ©2026 Palo Alto Networks, Inc.
Enable SD-WAN with Auto VPN
The system secures the pre-shared key, even from the administrator. Beginning with PAN-OS
9.1.2, you can refresh the IKE pre-shared key, which Panorama sends to all members of the
cluster.
Refresh the pre-shared key when cluster members aren't busy.
```
(SD-WAN 3.2.0 and later versions)When you select Certificate as the Authentication Type,
```
then the hubs and branches in the SD-WAN VPN cluster is based on the certificate-based
authentication.
After the SD-WAN Plugin is upgraded to 2.1.0, the hub and branch firewalls in a single VPN
```
cluster must all run either PAN-OS 10.0.4 (or a later 10.0 release) or 10.1.0, not a combination of
```
the two releases.
When viewing VPN clusters, if no data is present or the screen indicates that SD-WAN
is undefined, check in the Compatibility Matrix that the Panorama release you're using
supports the SD-WAN plugin release you're trying to use.
SD-WAN plugin 3.2.0 and later versions support IPv6 interfaces and IPv6 tunnels. Whether an
```
IPv4 or IPv6 IPSec tunnel is formed between two Ethernet ports (or subinterface or AE interface)
```
```
(DIA link) depends on whether the Ethernet interface (or subinterface or AE interface) has an
```
IPv4 or IPv6 address. If both of the interfaces have an IPv4 address, an IPv4 tunnel is brought up.
If both of the interfaces have an IPv6 address, an IPv6 tunnel is brought up. In the case of dual
stack, an IPv4 tunnel is brought up.
The tunnel interface IP address comes from the VPN pool. You can create an IPv6 address pool
independent of an IPv4 address pool. If both IPv4 and IPv6 addresses are configured, the tunnel
interface is assigned an IPv4 address only, as shown in the following table. If the IPv4 VPN
address pool is exhausted and an IPv6 address pool exists, the tunnel interface is assigned an IPv6
address. If only IPv4 is configured, the tunnel will use an IPv4 address. If only IPv6 is configured,
the tunnel will use an IPv6 address.
VPN Pool Configured
IPv4 Yes Yes No
IPv6 Yes No Yes
Tunnel Interface IP IPv4 Only IPv4 Only IPv6 Only
• PAN-OS & Panorama
• Strata Cloud Manager
PAN-OS & Panorama
STEP 1 | Plan your branch and hub VPN topology to determine which branches communicate with
each of your hubs. For more information, see plan your SD-WAN configuration.
STEP 2 | Log in to the Panorama Web Interface.
SD-WAN Administration 92 ©2026 Palo Alto Networks, Inc.
Enable SD-WAN with Auto VPN
```
STEP 3 | (PAN-OS 9.1.2 and later versions, and SD-WAN plugin 1.0.2 and later versions) Specify IP
```
address ranges for the IPSec VPN tunnels that Auto VPN configuration creates.
Auto VPN configuration creates a VPN tunnel between a hub and branches and
assigns IP addresses to the tunnel endpoints. Enter subnet ranges that you want Auto
VPN to use as VPN tunnel addresses. You can enter up to 20 IP prefix/netmask ranges.
Auto VPN draws from that pool for VPN tunnel addresses, drawing from the largest
```
range (for the address family) first, and then drawing from the next largest range when
```
necessary. You must configure at least one range for the pool. If you don’t perform this
step before pushing the configuration to a hub or branch, the Commit and Push will
fail.
If you upgrade from an earlier SD-WAN Plugin release, you must check that your
ranges are still correct. If they aren't, enter new ranges. After you Commit, all tunnels
are dropped and new tunnels are used, so perform this task during a time you have low
traffic.
1. Select Panorama > SD-WAN > VPN Clusters.
2. At the bottom of the screen, select VPN Address Pool.
3. Select IPv4 or IPv6 and Add an address pool with one or more (up to 20) Member IP
address and netmask ranges, for example, 192.168.0.0/16 or 2001::/16, respectively.
4. Click OK.
SD-WAN Administration 93 ©2026 Palo Alto Networks, Inc.
Enable SD-WAN with Auto VPN
```
(SD-WAN plugin 2.2.0 and later versions) Don't simply change an existing
```
address pool if Prisma Access is onboarded. If you need to change an address
pool, perform the following steps during a maintenance window to update the
branch and the Panorama CN with your address pool changes:
1. Use Panorama to access an SD-WAN branch and delete the existing
```
onboarding that the address pool change will impact; then do a local Commit.
```
2. Update the VPN address pool, and then do a local Commit.
3. Perform the Panorama onboarding again, and then do a local Commit and
Push.
STEP 4 | Configure the VPN cluster. Repeat this step to create VPN clusters as needed.
1. Select Panorama > SD-WAN > VPN Clusters and Add a VPN cluster.
2. Enter a descriptive name for the VPN cluster.
Underscores and spaces are not supported in the VPN cluster name and result in
```
monitoring (Panorama > SD-WAN > Monitoring) data for the cluster not to be
```
displayed. Choose the name of the VPN cluster carefully so you do not need to
change the name in the future. SD-WAN monitoring data is generated based on
the old cluster name and cannot be reconciled to a new cluster name, and will
cause issues with the number of reported clusters when monitoring your VPN
clusters or generating reports.
3. Select the VPN cluster Type.
Only Hub-Spoke VPN cluster type is supported in PAN-OS 10.0.2 and earlier
11.0 versions. Beginning with PAN-OS 10.0.3, you can Create a Full Mesh
VPN Cluster with DDNS Service.
4. (SD-WAN plugin 3.2.0 and later versions) Select the Authentication type: Pre Shared
Key or Certificate. It's mandatory to specify the authentication type to add a device in a
VPN cluster. A VPN cluster should have the same authentication type selected for all its
devices.
When you select the authentication type for a VPN cluster, only the branches and hubs
```
that are configured with the same authentication type (as the VPN cluster) can be added
```
to the VPN cluster. For example, when you select certificate as the authentication type
SD-WAN Administration 94 ©2026 Palo Alto Networks, Inc.
Enable SD-WAN with Auto VPN
for a VPN cluster, then all the hubs and branches that are added to the cluster should be
configured with certificate as the authentication type.
You can't modify the authentication type or VPN cluster name of a VPN cluster that
has been configured already. To make a change, remove the VPN cluster and its SD-
WAN devices and configure it again using the new authentication type or VPN cluster
name. By default, we support the pre-shared authentication type for the devices in a
```
VPN cluster (if the certificate method is not selected manually).
```
• One you've configured the VPN cluster, you cannot change the cluster name
```
or its authentication type (both cluster and device level).
```
• You cannot have different authentication types within a single VPN cluster.
That is, a VPN cluster authentication type must match with all the SD-WAN
devices in the VPN cluster. Any difference would result in a commit failure.
• You can have different VPN clusters with different authentication types
configured.
• In a VPN cluster, you cannot have SD-WAN devices with different
authentication types selected. If an SD-WAN hub is part of two VPN clusters,
then the two clusters should be configured with the same authentication
type.
If you want to change the authentication type to Certificate for an existing VPN cluster,
delete the VPN cluster and create it again with the authentication type of your choice.
After creating a VPN cluster with certificate authentication type, if you want to
downgrade to an PAN-OS or SD-WAN plugin version that does not support certificate
authentication type, follow these steps:
• Delete the existing VPN cluster. SD-WAN device authentication will automatically
change to pre-shared key on downgrade.
• Downgrade to the PAN-OS or SD-WAN plugin version of your preference. See the
system requirements for SD-WAN for the minimum PAN-OS and SD-WAN plugin
versions required for configuring the certificate authentication type.
Follow the steps mentioned in the Upgrade and Downgrade Considerations before you
upgrade or downgrade your current SD-WAN plugin.
5. (PAN-OS 11.1.8 and later 11.1 versions, SD-WAN plugin 3.2.3 and later 3.2 versions)
```
(PAN-OS 11.2.5 and later 11.2 versions, SD-WAN plugin 3.3.3 and later 3.3 versions)
```
As quantum computing technology advances, traditional encryption methods used in
VPNs and other secure communications become increasingly vulnerable to attacks. In
Advanced NGFW SD-WAN, we have introduced post-quantum VPN to address this
emerging threat with quantum-resistant encryption methods to protect your SD-WAN
overlay.
```
Post-Quantum pre-shared key (PQ PPK) is one of the key components of post-quantum
```
VPN that enhances the security of your IPSec tunnels by adding an additional layer of
quantum-resistant encryption. The SD-WAN plugin allows you to enable post-quantum
VPN features for your VPN clusters and manage the associated settings. When enabled,
the plugin automatically generates and manages strong PQ PPKs for your IPSec tunnels.
SD-WAN Administration 95 ©2026 Palo Alto Networks, Inc.
Enable SD-WAN with Auto VPN
The SD-WAN plugin configures IKE and IPSec Crypto profiles to use quantum-safe
algorithms when post-quantum VPN is enabled.
Select PQ PPK to enable PQ PPK for your SD-WAN overlay.
A warning appears:
Select OK to enable post-quantum VPN for the VPN cluster. The SD-WAN plugin will
automatically generate 10 strong PQ PPKs to use with the IPSec tunnels. The SD-WAN
SD-WAN Administration 96 ©2026 Palo Alto Networks, Inc.
Enable SD-WAN with Auto VPN
plugin will configure the IPSec tunnels to use PQ PPK with the negotiation mode set to
preferred.
• PQ PPK isn’t supported on the PA-220 firewall.
• PQ PPK is supported only with Pre Shared Key authentication type.
• When multiple VPN clusters with PQ PPK share a hub firewall, then the
shared hub firewall cannot simultaneously support some clusters with PQ
PPK enabled and others using standard PSK authentication. That is, all VPN
clusters connected to a shared hub firewall must either use PSK or use PQ
PPK.
• Existing VPN clusters won’t have post-quantum VPN configured by default.
This approach ensures there is no disruption to existing IPSec connectivity.
However, you have the flexibility to manually enable post-quantum VPN
for an existing cluster if desired. When you do so, the IPSec tunnels won’t
be immediately affected. Instead, the post-quantum capabilities will be
negotiated when the keys expire or when the tunnel is renegotiated.
This gradual adoption strategy enables you to implement quantum-safe
encryption at your own pace, balancing security enhancements with
operational stability.
If you want to refresh the PQ PPK list, use the Refresh PQPPK List in the VPN cluster
configuration. It regenerates the new post-quantum pre-shared keys and updates the
keys on all SD-WAN devices within the selected VPN cluster.
```
(HA deployments only) For Panorama in HA configuration, all PQ PPK information is
```
synchronized between the active and passive peers, ensuring seamless failover. Similarly,
for HA active/passive firewalls, the PQ PPK list and all pre-shared keys, including post-
quantum key information, are synchronized between the devices. This synchronization
ensures that the PQ PPK configuration remains consistent and operational across the
SD-WAN Administration 97 ©2026 Palo Alto Networks, Inc.
Enable SD-WAN with Auto VPN
HA pair, maintaining the quantum-safe encryption capabilities of your SD-WAN overlay
even during failover events.
6. Add one or more branch devices that you determined need to communicate with each
other.
```
• (SD-WAN plugin 1.0.1 and later versions) Select Group HA Peers to display the
```
branch devices that are HA peers together.
• Select the branch devices to add to the cluster.
```
When configuring VPN clusters with high availability (HA) branch firewalls,
```
```
both HA peers (active and passive) must be included. If you select one HA
```
peer firewall for a branch, you're required to also select its corresponding HA
peer. This ensures that both the active and passive HA peers are part of the
VPN cluster configuration.
• Click OK.
7. Add one or more hub devices that you determined need to communicate with the
branch devices.
SD-WAN hubs in an HA configuration are considered as a single SD-WAN hub firewall.
```
MPLS and satellite link types will form tunnels with only the same link type; for
```
example, MPLS-to-MPLS and satellite-to-satellite. Tunnels won’t be created
between an MPLS link and an Ethernet link, for example.
For the SD-WAN versions earlier than 3.1.3, you can add up to four SD-WAN hub
firewalls to a VPN cluster.
```
(SD-WAN plugin 3.2.1 and later versions) You can add up to 16 SD-WAN hub firewalls
```
to a VPN cluster. Only four of the 16 hubs can have the same hub priority within a VPN
SD-WAN Administration 98 ©2026 Palo Alto Networks, Inc.
Enable SD-WAN with Auto VPN
cluster due to ECMP. Any attempt to configure the same priority for more than four SD-
WAN hubs would result in a commit error.
```
• (SD-WAN plugin 1.0.1 and later versions) Select Group HA Peers to display the hub
```
devices that are HA peers together.
• Select the hubs to add to the cluster and click OK.
```
When configuring VPN clusters with high availability (HA) hub firewalls, both
```
```
HA peers (active and passive) must be included. If you select one HA peer
```
firewall for a hub, you're required to also select its corresponding HA peer.
This ensures that both the active and passive HA peers are part of the VPN
cluster configuration.
• For any new or previously existing VPN cluster that has more than one hub, you
```
must prioritize the hubs to determine a) that traffic be is sent to a particular hub,
```
```
and b) the subsequent hub failover order. The hub failover priority range is 1 to 4.
```
If you upgrade, the default priority is set to 4. The plugin internally translates the
hub failover priority to a BGP local preference number as shown in the following
table. The lower the priority value, the higher the priority and local preference. A
cluster supports a maximum of four hubs for the SD-WAN versions earlier than 3.1.3.
With SD-WAN plugin 3.2.1 and later versions, you can add up to 16 SD-WAN hub
firewalls to a VPN cluster. An active/passive HA pair counts as one hub. Multiple hubs
```
can have the same priority; an HA pair must have the same priority. Panorama uses
```
the branch’s BGP template to push the local preference of the hubs to the branches in
the cluster.
Hub Failover Priority Local Preference
1 250
2 200
3 150
SD-WAN Administration 99 ©2026 Palo Alto Networks, Inc.
Enable SD-WAN with Auto VPN
Hub Failover Priority Local Preference
4 100
If multiple hubs have the same priority, Panorama enables ECMP in two
places on each branch firewall to determine how branches select the path.
```
ECMP is enabled for the virtual router (Network > Virtual Routers > ECMP)
```
```
and ECMP Multiple AS Support is enabled for BGP (Network > Virtual
```
```
Routers > BGP > Advanced). If all hubs in the cluster have a unique priority,
```
ECMP is disabled on the branches. If a hub priority configuration changes,
Panorama reevaluates whether to enable or disable ECMP.
• If you selected Group HA Peers, select the pair and click in the Hub Failover
```
Priority field; enter a single Priority (range is 1 to 4), which applies to both hubs in
```
the HA pair, and click OK.
The Hub Failover Priority for HA Peers window appears only for
configured HA pairs. If you add a new HA pair, you must configure the
Hub Failover Priority for each of the two new peers independently.
You will get an error message if you assign different priorities to hubs that
are ungrouped HA peers and then you select Group HA Peers and Submit.
• For hubs that are not HA pairs, select a hub and click in the Hub Failover Priority
```
field; enter a priority (range is 1 to 4).
```
SD-WAN Administration 100 ©2026 Palo Alto Networks, Inc.
Enable SD-WAN with Auto VPN
8. Click OK to save the VPN cluster.
```
STEP 5 | (PAN-OS 9.1.2 and later versions, and SD-WAN plugin 1.0.2 and later versions) Advertise
```
additional prefixes at the branch to the hub.
```
The firewall automatically redistributes (advertises) all non-public, connected routes
```
from the branch to the hub. You can also redistribute any additional prefixes from the
```
branch to the hub. The Prefix(es) to Redistribute field accepts a list of prefixes, rather
```
than just a single prefix.
1. Select Panorama > SD-WAN > Devices and select a branch firewall.
2. Select BGP and Add one or more IP addresses with netmask to Prefix(es) to
Redistribute.
3. Click OK.
STEP 6 | Commit and Commit to Panorama.
```
STEP 7 | (SD-WAN plugin 2.0.1 and later 2.0 versions) If your hub firewalls in a hub-spoke VPN
```
cluster have DHCP or PPPoE interfaces, you must use DDNS. Select Network > Interfaces >
Ethernet and in the Template field, select Template-stack for a hub.
```
STEP 8 | (SD-WAN plugin 2.0.1 and later 2.0 versions) Select the interfaces whose IP address
```
indicates Dynamic-DHCP Client or PPPOE, click Override on the bottom of the screen,
and click OK to close.
SD-WAN Administration 101 ©2026 Palo Alto Networks, Inc.
Enable SD-WAN with Auto VPN
```
STEP 9 | (SD-WAN plugin 2.0.1 and later 2.0 versions) Verify on Panorama that the DDNS settings
```
were configured.
1. Select Network > Interfaces > Ethernet and select the same interface again.
2. Select Advanced > DDNS.
3. See that the DDNS settings were automatically configured with a Hostname and the
Vendor set to Palo Alto Networks DDNS.
4. Click OK.
```
STEP 10 | (SD-WAN plugin 2.0.1 and later 2.0 versions) Commit and Commit to Panorama.
```
```
STEP 11 | Push the configuration to the hub(s).
```
When Panorama creates virtual SD-WAN interfaces for hubs, Panorama doesn't
necessarily create the interfaces using contiguous interface numbers. It might
randomly skip an interface number, for example, sdwan.921, sdwan.922, sdwan.924,
sdwan.925. Despite the discontiguous numbering, Panorama creates the correct
number of SD-WAN interfaces. Use the operational CLI command show interface
sdwan? to see the SD-WAN interfaces.
1. Select Commit and Push to Devices.
2. Edit Selections on the lower left side of the screen.
3. Deselect Filter Selected.
4. Click on Deselect All.
5. Select your hub Device Group. Select Include Device and Network Templates at the
bottom of the screen. You must push to hubs before pushing to branches.
Most branches have dynamic IP addresses through their service providers, so branches
must initiate the IKE/IPSec connection because the hub doesn’t have the branches’ IP
address. To ensure that the hub is ready to receive the IKE/IPSec connections, the hub’s
SD-WAN Administration 102 ©2026 Palo Alto Networks, Inc.
Enable SD-WAN with Auto VPN
configuration must be committed and pushed before the branch’s configuration. Thus,
when the branch configurations are pushed and the branches initiate the connection to
the hub, the hub is ready.
6. Select the Templates tab and Deselect All.
7. The Push Scope is the Device Group. Push the configuration to the hub(s).
```
STEP 12 | Push the configuration to the branch(es) by repeating the prior step, but selecting your
```
branch Device Group.
SD-WAN Administration 103 ©2026 Palo Alto Networks, Inc.
Enable SD-WAN with Auto VPN
```
STEP 13 | (PAN-OS 9.1.2 and later versions, and SD-WAN plugin 1.0.2 and later versions) Refresh the
```
IKE pre-shared key.
If you need to change the current IKE key that is used to secure the IPSec connections
between VPN cluster devices, perform this step to randomly generate a new key for
the cluster.
Perform this step when cluster members aren't busy.
1. Select Panorama > SD-WAN > VPN Clusters and select a cluster.
2. At the bottom of the screen, select Refresh IKE Key.
3. A message appears notifying you that Refreshing the IKE key will generate
```
a new security association (SA) for every SD-WAN firewall in the
```
VPN cluster. This may cause a service disruption. Do you wish to
continue? Yes | No Select Yes if you wish to continue.
4. Commit.
```
After you Refresh IKE Key, you must commit to the entire cluster; a partial
```
commit will bring down tunnels.
5. Push to Devices.
Strata Cloud Manager
The SD-WAN interface profile defines the characteristics of the ISP connection, specifies the
speed of links and how frequently the firewall monitors the link, and specifies the link tag. When
```
you specify the same Link Tag on multiple links, you’re grouping (bundling) those physical links
```
into a link bundle or fat pipe.
STEP 1 | Log in to Strata Cloud Manager.
STEP 2 | Select Configuration > NGFW and Prisma Access > Setup > Auto VPN and Add VPN
Cluster.
```
STEP 3 | Check (enable) SD-WAN.
```
SD-WAN Administration 104 ©2026 Palo Alto Networks, Inc.
Enable SD-WAN with Auto VPN
STEP 4 | Add the hub firewalls to the VPN cluster.
1. Add Hub Devices to select one or more firewalls to Add as hubs.
Up to four hubs are supported for a VPN cluster.
2. Click the firewall in the Hub Devices list.
3. Set the hub firewall Priority.
Range is 1 to 4. The lower the priority value, the higher the priority and local preference.
A cluster supports a maximum of four hubs. An active/passive HA pair counts as one hub.
```
Multiple hubs can have the same priority; an HA pair must have the same priority.
```
4. Select a Logical Router.
5. (Optional) Check (enable) DIA VPN and select a DIA VPN Link Tag.
6. Update.
7. Repeat this step for all hub firewalls that you add to the VPN cluster.
STEP 5 | Add the branch firewalls to the VPN cluster.
1. Add Hub Devices to select one or more firewalls to Add as hubs.
2. Select a Logical Router.
3. (Optional) Select a BGP Redistribution Profile.
4. Update.
5. Repeat this step for all branch firewalls that you add to the VPN cluster.
SD-WAN Administration 105 ©2026 Palo Alto Networks, Inc.
Enable SD-WAN with Auto VPN
Create a Full Mesh VPN Cluster with DDNS Service
Where Can I Use This? What Do I Need?
```
• NGFW (Managed by PAN-OS 10.0.3 or a
```
```
later PAN-OS release)
```
• SD-WAN plugin 2.0.1 or a later SD-WAN
release
Advanced SD-WAN for NGFW
Beginning with PAN-OS 10.0.3, SD-WAN supports a full mesh topology, in addition to the hub-
spoke topology. The mesh can consist of branches with or without hubs. Use full mesh when
the branches need to communicate with each other directly. Examples of use cases for full mesh
include retailers that have branches and hubs, and enterprises that operate with or without hubs.
Some firewall interfaces use DHCP to get their IP address. Branch offices often use a consumer-
grade internet service and receive a dynamic IP address, which of course can change. For this
```
reason, the firewalls require Dynamic DNS (DDNS) so that a DDNS service can detect the public-
```
facing IP address of the firewall interface that is running SD-WAN. When you push the DDNS
setting to all firewalls, that notifies each firewall to register its external interface IP address with
the Palo Alto Networks DDNS cloud service so that the IP address is converted to an FQDN.
```
DDNS is also required because the CPE device from the ISP may be performing source NAT. (The
```
```
dynamic IP address may or may not be source-NAT translated). The DDNS service allows the
```
firewall to register the public-facing IP address with the DDNS server. When you have devices
connect for branch-to-branch mesh, Auto VPN contacts the DDNS service for those firewalls
to pull their public IP addresses that are registered in the DDNS cloud and uses those public IP
addresses to create the IKE peering and the VPN tunnels. If the CPE device is performing source
NAT, when you add an SD-WAN branch device to be managed by Panorama, you will enable
Upstream NAT and the NAT IP Address Type will be DDNS.
For the CPE device or upstream routing device using source NAT, you are responsible for
```
creating the one-to-one destination NAT rule (with no port translation) on that device to
```
translate the external IP address back to the private IP address assigned to the firewall’s
interface. This translation allows the IKE and IPSec protocols to come back into the
```
firewall. (Palo Alto Networks doesn’t have access rights to the upstream CPE or upstream
```
```
router that is performing source NAT.)
```
SD-WAN full mesh with DDNS service requires the following:
• ZTP plugin 1.0.1 or a later 1.0 release that is downloaded, installed, and configured in order
to leverage the DDNS that is associated with ZTP. Panorama must be ZTP-registered and
communicating with the ZTP Service.
• Applications and Threats Content Release Version 8354 or a later version
• All firewalls participating in full mesh DDNS must be registered under the same Customer
```
Support Portal (CSP) account.
```
SD-WAN Administration 106 ©2026 Palo Alto Networks, Inc.
Enable SD-WAN with Auto VPN
• All firewalls participating in full mesh DDNS must have the latest device certificate installed.
Properly authenticating the firewalls, Panorama, and the cloud services are important security
procedures that require the device certificate, and the CSP and ZTP services.
• If you have a firewall or other network device that controls outgoing traffic positioned in front
of the Palo Alto Networks firewall, you must change the configuration on that device to allow
traffic from the DDNS-enabled interfaces to the following FQDNs:
```
• https://myip.ngfw-ztp.paloaltonetworks.com/ (to reach whatsmyIP service)
```
```
• https://ngfw-ztp.paloaltonetworks.com/ (to reach DDNS registration service)
```
STEP 1 | Install the latest device certificate for Panorama and for all managed firewalls that are hubs
or branches.
STEP 2 | Install ZTP Plugin 1.0.1 to set up Zero Touch Provisioning.
1. In the Panorama Administrator’s Guide, read the ZTP Overview.
2. Install the ZTP Plugin.
3. Configure the ZTP Installer Administrator Account.
4. Select Panorama > Zero Touch Provisioning > Setup and edit the General settings to
enable Dynamic IP Registration.
5. Click OK. The General settings indicate On ZTP Service with a Tenant ID number.
6. Select ZTP Service Status and confirm that the firewall Serial Number is listed.
STEP 3 | If you haven’t already done so, install the SD-WAN plugin 2.0.1 or a 2.0 release.
STEP 4 | Commit on Panorama.
STEP 5 | Log in to the Panorama Web Interface.
SD-WAN Administration 107 ©2026 Palo Alto Networks, Inc.
Enable SD-WAN with Auto VPN
STEP 6 | Create the VPN Address Pool while planning your topology for SD-WAN with Auto VPN.
STEP 7 | Create the full mesh VPN cluster.
1. Select Panorama > SD-WAN > VPN Clusters.
2. Select the Type to be Mesh.
3. Add the Branches that need to communicate with each other.
4. (Optional) Add one or more Hubs if you also want a hub in the mesh.
5. Click OK.
STEP 8 | Commit and Commit to Panorama. If your firewalls have static IP addresses, you are done. If
your branch or hub firewalls in a VPN mesh have DHCP or PPPoE interfaces, you must use
DDNS, so continue this procedure as follows.
STEP 9 | Select Network > Interfaces > Ethernet and in the Template field, select Template-stack for
a particular branch.
STEP 10 | Select the interface whose IP address indicates Dynamic-DHCP Client or PPPOE, click
Override on the bottom of the screen, and click OK to close.
SD-WAN Administration 108 ©2026 Palo Alto Networks, Inc.
Enable SD-WAN with Auto VPN
STEP 11 | Verify on Panorama that the DDNS settings were configured.
1. Select Network > Interfaces > Ethernet and select the same interface again.
2. Select Advanced > DDNS.
3. See that the DDNS settings were automatically configured with a Hostname based on
the interface name, and the Vendor set to Palo Alto Networks DDNS. For example,
on the Ethernet1/2 interface, the resulting Hostname is 0102.
4. Click OK.
STEP 12 | If the VPN cluster includes any hubs that have a DHCP or PPPoE interface, repeat Steps 9
through 11, but in the Template field, select Template-stack for a particular hub.
Even if your hub is not in a full mesh cluster, but is in a hub-spoke cluster, if the hub
uses DHCP or PPPOE to get its IP address for an SD-WAN interface, you must perform
the Override steps to enable DDNS.
STEP 13 | Commit to Panorama and Push to Devices.
SD-WAN Administration 109 ©2026 Palo Alto Networks, Inc.
Enable SD-WAN with Auto VPN
STEP 14 | Verify on the branch firewall that the branch is configured with DDNS.
1. Log into the branch firewall.
2. Select Network > Interfaces > Ethernet and for the Ethernet interface that you
configured, scroll over the DDNS Info icon in the Features column to see the
Vendor, Hostname, IP address, and other DDNS information.
STEP 15 | On another branch in the cluster, view that the Peer Address of the interface is a system-
generated FQDN for the DDNS registration.
1. Log onto another branch and select Network > Network Profiles > IKE Gateways.
2. See that the Peer Address is a secure name, not easily
```
referenced and showing no company information; for example
```
0101.8ced8460fcc5177cd3665ce41b6345323a15a612b8e52ec1d9ec057a582cb4.t13855f6c9a92d
STEP 16 | View FQDNs of branches and hubs and update DDNS information.
1. Access the CLI.
2. View FQDNs (generated by DDNS) for other branches and hubs: show dns-proxy
fqdn all
3. Update the DDNS addresses: request system fqdn refresh
SD-WAN Administration 110 ©2026 Palo Alto Networks, Inc.
Enable SD-WAN without Auto
VPN
Where Can I Use This? What Do I Need?
• NGFW Advanced SD-WAN for NGFW
Add a single SD-WAN hub or branch firewall or use a CSV to bulk import multiple SD-WAN hub
and branch firewalls with pre-shared key or certificate authentication type.
You can also configure SD-WAN without using the SD-WAN plugin by following one of these
```
ways:
```
• Configure using a network template from the Panorama management server, or
• Configure SD-WAN directly on each firewall
While configuring SD-WAN without Auto VPN, it's mandatory to define the virtual interface and
bundle the correct physical interface under these virtual interfaces on which SD-WAN is enabled.
The tunnels between a site and hub should be part of the same virtual interface. It is also required
```
to configure the routing protocol (or static route) for route exchange.
```
If you use Auto VPN configuration through Panorama, it creates the SD-WAN interfaces for you,
in which case you don't have to create and configure a virtual SD-WAN interface. If you are not
using Auto VPN configuration through Panorama, then you can configure SD-WAN manually as
```
follows:
```
1. Create the DIA SD-WAN virtual interface (VIF) on both hub and branch firewalls and configure
the SD-WAN-enabled interface as a member of DIA VIF.
2. Configure the default route using DIA SD-WAN VIF for internet traffic.
3. Configure IPSec tunnel between the hub and branch firewalls using the physical interface on
which SD-WAN is enabled as the IKE gateway.
4. Create the SD-WAN VIF (branch VIF on the hub and hub VIF on the branch) and configure the
IPSec tunnel that goes to the same destination as a part of the same VIF.
5. Configure routing between hub and branch to exchange the routing information.
111
Enable SD-WAN without Auto VPN
Configure a Virtual SD-WAN Interface
Where Can I Use This? What Do I Need?
• NGFW Advanced SD-WAN for NGFW
If you use Auto VPN configuration through Panorama, it creates the SD-WAN interfaces for you,
in which case you don’t create and configure a virtual SD-WAN interface.
If you aren’t using Auto VPN configuration with Panorama, create and configure a virtual SD-
WAN interface to specify one or more physical, SD-WAN-capable ethernet interfaces that go to
the same destination, such as to a specific hub or to the internet. In fact, all links in a virtual SD-
```
WAN interface must be the same type: all VPN tunnel links or all direct internet access (DIA) links.
```
The first figure illustrates an example of an SD-WAN interface named SDWAN.901 that bundles
```
two physical interfaces, which use different carriers: Ethernet1/1 (the cable modem link) and
```
```
Ethernet1/2 (the fiber service link). Both links are a VPN tunnel from the branch to the hub.
```
```
In this figure, both links in the SD-WAN interface happen to use the same link tag (Cheap
```
```
Broadband), but links in an SD-WAN interface can have different link tags.
```
In the following figure, SD-WAN.902 bundles Ethernet1/1 and Ethernet1/2 links, which are both
DIA links from the branch to the internet:
STEP 1 | Log in to the Panorama Web Interface.
SD-WAN Administration 112 ©2026 Palo Alto Networks, Inc.
Enable SD-WAN without Auto VPN
STEP 2 | Select Network > Interfaces > SD-WAN and select the appropriate template from the
Template context drop-down.
```
STEP 3 | Add a logical SD-WAN interface by entering a number (in the range 1 to 9,999) after the
```
sdwan. prefix.
Auto VPN configuration creates SD-WAN interfaces numbered .901, .902, and so
on. Hence, if you want to create the SD-WAN interfaces manually, don't use the
sdwan.90x format for an SD-WAN interface name.
```
(SD-WAN plugin 3.2.0 and later versions) Similarly, Auto VPN configuration creates an
```
SD-WAN interface numbered .9016 for an IPv6 interface, so don't use sdwan.9016 for
an SD-WAN interface name.
STEP 4 | Enter a descriptive Comment.
Add a helpful comment, such as Branch to internet or Branch to western
USA hub if you are on the Branch template. Your comment makes troubleshooting
easier rather than trying to decipher auto-generated names in logs and reports.
STEP 5 | Select the Protocol to indicate the type of virtual SD-WAN interface:
• ipv4 indicates an IPv4 DIA virtual interface.
```
• (SD-WAN plugin 3.2.0 and later versions) ipv6 indicates an IPv6 DIA virtual interface.
```
• none indicates a VPN tunnel virtual interface.
STEP 6 | On the Config tab, assign the SD-WAN interface to a Virtual Router.
STEP 7 | Assign the SD-WAN interface to a Security Zone.
The virtual SD-WAN interface and all of its interface members must be in the same Security
zone, thus ensuring the same Security policy rules apply to all paths from the branch to the
same destination.
STEP 8 | On the Advanced tab, Add Interfaces, which are members that go to the same destination,
```
by selecting one or more Layer 3 Ethernet interfaces (for DIA) or one more virtual VPN
```
```
tunnel interfaces (for hub). If you enter more than one interface, they must all be the same
```
```
type (either VPN tunnel or DIA).
```
The firewall virtual router uses this virtual SD-WAN interface to route SD-WAN traffic
to a DIA or a hub location. During routing, the route table determines which virtual
```
SD-WAN interface (egress interface) the packet will exit based on the destination IP
```
address in the packet. Then the SD-WAN path health and Traffic Distribution profiles
```
in the SD-WAN policy rule that the packet matches determine which path to use (and
```
```
the order in which to consider new paths if a path deteriorates.)
```
SD-WAN Administration 113 ©2026 Palo Alto Networks, Inc.
Enable SD-WAN without Auto VPN
STEP 9 | Click OK to save your configuration change.
STEP 10 | Commit and Commit and Push your configuration changes.
SD-WAN Administration 114 ©2026 Palo Alto Networks, Inc.
Enable SD-WAN without Auto VPN
Create a Default Route to the SD-WAN Interface
Where Can I Use This? What Do I Need?
• NGFW Advanced SD-WAN for NGFW
Auto VPN creates a virtual SD-WAN interface named sdwan.901 for IPv4 DIA and a virtual SD-
WAN interface named sdwan.9016 for IPv6 DIA. It creates a virtual SD-WAN interface named
```
sdwan.90x (where the x starts from 2) for VPN tunnels. Auto VPN also creates its own default
```
```
route that uses the sdwan.901 (IPv4) and sdwan.9016 (IPv6) interface as its egress interface and
```
```
uses a low metric, so that the sdwan.901 (IPv4) interface and sdwan.9016 (IPv6) interface are
```
preferred over the default route you created. SD-WAN plugin 3.2.0 and later versions support
IPv6 interfaces and IPv6 tunnels.
When you configure Auto VPN using Panorama™, it creates the default route configuration, in
which case you don’t have to create and configure the default route. For all other cases, use the
following workflow to create a default route pointing to the SD-WAN DIA virtual interface that
was created earlier.
STEP 1 | Log in to the Panorama Web Interface.
STEP 2 | Select the Template you are working on.
STEP 3 | Select Network > Virtual Routers and select a virtual router, such as sd-wan.
```
STEP 4 | (SD-WAN plugin 3.1.0 and earlier versions) Select Static Routes and Add a static route by
```
Name.
```
STEP 5 | (SD-WAN plugin 3.1.0 and earlier versions ) For Destination, enter 0.0.0.0/0.
```
```
STEP 6 | (SD-WAN plugin 3.2.0 and later versions) Select Static Routes.
```
```
STEP 7 | (SD-WAN plugin 3.2.0 and later versions) Select IPv4 or IPv6 and Add a static route by
```
Name.
```
STEP 8 | (SD-WAN plugin 3.2.0 and later versions) For an IPv4 Destination, enter 0.0.0.0/0. For an
```
IPv6 Destination, enter ::/0.
STEP 9 | For egress Interface, select one of the logical SD-WAN interfaces you created to bring up
the firewall.
The egress interface you select can be any logical SD-WAN interface except
sdwan.901, sdwan.902, or sdwan.9016.
STEP 10 | For Next Hop, select None.
STEP 11 | For Metric, enter a value greater than 50, so that this default route is not preferred over the
default route that Auto VPN creates with a low metric.
STEP 12 | Click OK.
SD-WAN Administration 115 ©2026 Palo Alto Networks, Inc.
Enable SD-WAN without Auto VPN
STEP 13 | Select Commit and Commit and Push your configuration changes.
STEP 14 | Commit your changes.
STEP 15 | Repeat this task for other templates on firewalls that use a service route to access Panorama.
SD-WAN Administration 116 ©2026 Palo Alto Networks, Inc.
Enable SD-WAN without Auto VPN
Manage SD-WAN Link Failovers
Where Can I Use This? What Do I Need?
• NGFW Advanced SD-WAN for NGFW
Use SD-WAN link Management Profiles to define an SD-WAN traffic routing across gateways in
your SD-WAN network. With SD-WAN link Management Profiles, the SD-WAN traffic is routed
based on the availability or performance of the gateways. This optimizes the performance of your
SD-WAN network and adds reliability against the network failures.
Create and configure a path quality profile, SaaS quality profile, traffic distribution profile, and
error correction profile to manage SD-WAN link failovers.
```
• SD-WAN path quality profiles (PQPs)—Each SD-WAN path quality profile (PQP) is comprised
```
of a set of ranked metrics and thresholds that an application requires for optimal performance.
• SaaS quality profile—The SaaS quality profile allows you to specify the SaaS application to
monitor using an adaptive learning algorithm that monitors the application activity, or by
specifying a SaaS application using the application IP address, FQDN, or URL.
```
• SD-WAN traffic distribution profiles (TDPs)—As part of your SD-WAN policy, you use
```
SD-WAN traffic distribution profiles to assign which traffic distribution method the path-
selection algorithm uses for an application. The path-selection algorithm uses the path metrics,
thresholds, and sensitivities as defined in a path quality profile.
```
• Error correction profile—SD-WAN uses forward error correction (FEC) and packet duplication
```
```
(PD) to improve the performance and reliability of IP network. Forward Error Correction (FEC)
```
is used to recover the lost packets by sending extra packets for every group of four packets.
Packet duplication duplicates packets through secondary links to reduce packet loss if one link
goes down.
Define Your Custom SD-WAN Application Thresholds
Where Can I Use This? What Do I Need?
```
• NGFW (Managed by PAN-OS or
```
```
Panorama)
```
```
• NGFW (Managed by Strata Cloud
```
```
Manager)
```
Advanced SD-WAN for NGFW
One of these:
AIOps for NGFW Premium or Strata
Cloud Manager Pro
Strata Cloud Manager Essentials
```
(Supports only NGFWs)
```
Create a Path Quality profile for each set of business-critical and latency-sensitive applications,
application filters, application groups, services, service objects and service group objects that has
```
unique network quality (health) requirements based on latency, jitter, and packet loss percentage.
```
Applications and services can share a Path Quality profile. Specify the maximum threshold for
SD-WAN Administration 117 ©2026 Palo Alto Networks, Inc.
Enable SD-WAN without Auto VPN
each parameter, above which the firewall considers the path deteriorated enough to select a
better path.
As an alternative to creating a Path Quality profile, you can use any of the predefined Path
Quality profiles, such as general-business, voip-video, file-sharing, audio-streaming, photo-video,
and remote-access, and more. The predefined profiles are set up to optimize the latency, jitter,
packet loss, and bandwidth thresholds for the type of applications and services suggested by the
name of the profile.
The predefined Path Quality profiles for a device group are based on the default Probe
Frequency settings in the SD-WAN Interface profile template. If you change the default
Probe Frequency setting, you must adjust the Packet Loss percentage threshold in the
Path Quality profile for the firewalls in a Device Group that are affected by the template
where you changed the Interface profile.
The firewall treats the latency, jitter, and packet loss thresholds as OR conditions, meaning if any
```
one of the thresholds is exceeded, the firewall selects the new best (preferred) path. Any path
```
that has latency, jitter, and packet loss less than or equal to all three thresholds is considered
qualified and the firewall selected the path based on the associated Traffic Distribution profile.
By default, the firewall measures latency and jitter every 200ms and takes an average of the last
three measurements to measure path quality in a sliding window. You can modify this behavior
by selecting aggressive or relaxed path monitoring when you define your ISP connections and link
types.
If a path fails over because it exceeded the configured packet loss threshold, the firewall still
sends probing packets on the failed path and calculates its packet loss percentage as the path
recovers. It can take approximately three minutes for the packet loss percentage on a recovered
path to fall below the packet loss threshold configured in the Path Quality profile. For example,
suppose an SD-WAN policy rule for an application has a Path Quality profile that specifies a
packet loss threshold of 1% and a Traffic Distribution profile that specifies Top Down distribution
```
with tag 1 (applied to tunnel.1) first on the list and tag 2 (applied to tunnel.2) next on the list.
```
When tunnel.1 exceeds 1% packet loss, the data packets fail over to tunnel.2. After tunnel.1
```
recovers to 0% packet loss (based on probing packets), it can take up to three minutes for the
```
monitored packet loss rate for tunnel.1 to drop below 1%, at which time the firewall then selects
tunnel.1 as the best path again.
```
The sensitivity setting indicates which parameter (latency, jitter, or packet loss) is more important
```
```
(preferred) for the applications to which the profile applies. When the firewall evaluates link
```
quality, it considers a parameter with a high setting first. For example, when the firewall compares
```
two links, suppose one link has 100ms latency and 20ms jitter; the other link has 300ms latency
```
and 10 ms jitter. If the sensitivity for latency is high, the firewall chooses the first link. If the
sensitivity for jitter is high, the firewall chooses the second link. If the parameters have the same
```
sensitivity (by default the parameters are set to medium), the firewall evaluates packet loss first,
```
then latency, and jitter last.
As the SD-WAN Traffic Distribution Profiles concept states, the new path selection occurs in
```
less than one second if you leave path monitoring and probe frequency with default settings;
```
otherwise, new path selection could take more than one second. To achieve subsecond failover
based on packet loss, you must set the latency sensitivity to high and the latency threshold to no
more than 250ms.
SD-WAN Administration 118 ©2026 Palo Alto Networks, Inc.
Enable SD-WAN without Auto VPN
Reference the Path Quality profile in an SD-WAN policy rule to control the threshold at which the
firewall replaces a deteriorating path with a new path for matching application packets.
• PAN-OS & Panorama
• Strata Cloud Manager
PAN-OS & Panorama
STEP 1 | Log in to the Panorama Web Interface.
STEP 2 | Select a Device Group.
STEP 3 | Select Objects > SD-WAN Link Management > Path Quality Profile.
STEP 4 | Add a Path Quality profile by Name using a maximum of 31 alphanumeric characters.
STEP 5 | For Latency, double-click the Threshold value and enter the number of milliseconds allowed
for a packet to leave the firewall, arrive at the opposite end of the SD-WAN tunnel, and a
```
response packet to return to the firewall before the threshold is exceeded (range is 10 to
```
```
2,000; default is 100).
```
```
STEP 6 | For Latency, select the Sensitivity (low, medium, or high). Default is medium.
```
Click the arrow at the end of the Threshold column to sort thresholds in ascending or
descending numerical order.
```
STEP 7 | For Jitter, double-click the Threshold value and enter the number of milliseconds (range is 10
```
```
to 1,000; default is 100).
```
```
STEP 8 | For Jitter, select the Sensitivity (low, medium, or high). Default is medium.
```
STEP 9 | For Packet Loss, double-click the Threshold value and enter the percentage of packets lost
```
on the link before the threshold is exceeded (range is 1 to 100.0; default is 1).
```
Setting the Sensitivity for Packet Loss has no effect, so leave the default setting.
If you change the Probe Frequency in an SD-WAN Interface profile for a Panorama
template, you should also adjust the Packet Loss threshold for a Panorama device
group.
SD-WAN Administration 119 ©2026 Palo Alto Networks, Inc.
Enable SD-WAN without Auto VPN
STEP 10 | For Bandwidth, double-click the Threshold value and enter the bandwidth utilization
```
percentage at which the path is considered degraded (range: 1–100%; default 100%).
```
```
STEP 11 | For Bandwidth, select the Sensitivity (low, medium, or high). Default is medium.
```
STEP 12 | Click OK.
STEP 13 | Commit and Commit and Push your configuration changes.
STEP 14 | Commit your changes.
STEP 15 | Repeat this task for every Device Group.
Strata Cloud Manager
STEP 1 | Log in to Strata Cloud Manager.
STEP 2 | Select Configuration > NGFW and Prisma Access and in the Overview, select the branch
folder for which you want to create your SD-WAN Link Management profiles.
To make the Error Correction profile available to all SD-WAN firewalls regardless of folder
association, select All Firewalls.
```
STEP 3 | (Optional) Create a custom Path Quality profile.
```
Create a custom Path Quality profile for each set of business-critical and latency-sensitive
applications, application filters, application groups, services, service objects and service group
```
objects that has unique network quality (health) requirements based on latency, jitter, and
```
packet loss percentage specific to your business needs. Applications and services can share a
Path Quality profile.
The firewall treats the latency, jitter, and packet loss thresholds as OR conditions, meaning
```
if any one of the thresholds is exceeded, the firewall selects the new best (preferred) path.
```
Any path that has latency, jitter, and packet loss less than or equal to all three thresholds
is considered qualified and the firewall selected the path based on the associated Traffic
Distribution profile.
As an alternative to creating a Path Quality profile, you can use any of the predefined Path
Quality profiles, such as general-business, voip-video, file-sharing, audio-streaming, photo-
video, and remote-access, and more. The predefined profiles are set up to optimize the
SD-WAN Administration 120 ©2026 Palo Alto Networks, Inc.
Enable SD-WAN without Auto VPN
latency, jitter, and packet loss thresholds for the type of applications and services suggested by
the name of the profile.
1. Select Network Policies > SD-WAN Policy > Profiles > Path Quality and select the
branch folder for which you want to create the Path Quality profile.
2. Add Path Quality Profile.
3. Enter a descriptive Name.
Up to 31 alphanumeric characters are supported.
4. Configure the Latency settings.
The latency settings specify the number of milliseconds allowed for a packet to leave
the firewall, arrive at the opposite end of the SD-WAN tunnel, and a response packet to
return to the firewall before the threshold is exceeded.
1. Specify the latency Threshold in milliseconds.
Range is 10 to 3000. Default is 100.
2. Specify the latency threshold Sensitivity.
```
You can select Low, Medium (default), or High sensitivity.
```
5. Configure the Jitter settings.
The jitter settings specify the number of milliseconds allowed for packet disruptions to
impact data packet arrival. High jitter may cause packets to be received out of order or
to be discarded.
1. Specify the jitter Threshold in milliseconds.
Range is 10 to 2000. Default is 100.
2. Specify the latency threshold Sensitivity.
```
You can select Low, Medium (default), or High sensitivity.
```
6. Configure the Packet Loss settings.
The packet loss settings specify the percentage of packets lost on the link before the
threshold is exceeded.
Range is 1 to 100. Default is 1.
7. Save.
Monitor SaaS Applications Using SD-WAN
Where Can I Use This? What Do I Need?
• NGFW Advanced SD-WAN for NGFW
SD-WAN SaaS monitoring enables you to monitor and maintain healthy connections to your
critical SaaS applications at branch locations. Configure SaaS Quality profiles and associate them
with SD-WAN policy rules that monitor the key health metrics such as latency, jitter, and packet
loss for your essential SaaS applications. By creating a SaaS Quality profile, you can specify how
your SD-WAN solution monitors and manages traffic to specific SaaS applications, ensuring
SD-WAN Administration 121 ©2026 Palo Alto Networks, Inc.
Enable SD-WAN without Auto VPN
optimal path selection based on real-time network conditions. It allows you to define monitoring
parameters for up to four static IP addresses, or one FQDN, or URL per profile.
```
Configure a SaaS Quality profile to monitor direct internet access (DIA) links between a SaaS
```
```
application and your branch firewall. The SaaS Quality Profile (SQP) is used to measure the
```
```
path health of Direct Internet Access (DIA) applications and can use either an active or passive
```
approach. The active method is a one-sided health measurement that sends a probe from the
firewall and it measures bi-directional health to a static IP address or a monitored URL. The
passive method doesn’t send any probes. SaaS applications will not have a destination side PAN-
OS firewall frontending the traffic, so the SD-WAN VPN tunnel health probes are not used with
these monitoring types.
```
With direct internet access (DIA) links, you can ensure application usability and swap links
```
when performance thresholds are exceeded that provides reliability on business-critical SaaS
applications at branch firewall locations. With SD-WAN SaaS monitoring, you can proactively
manage link health, automatically switch to better-performing links for new sessions, and maintain
optimal application performance. This granular control over SaaS traffic routing enhances your
ability to deliver consistent, high-quality user experiences across your distributed network.
SaaS application path monitoring is supported only for SD-WAN enabled PAN-OS
firewalls. SaaS application path monitoring is not supported for Prisma Access hubs.
Monitor SaaS Applications with SaaS Quality Profile
Where Can I Use This? What Do I Need?
```
• NGFW (Managed by PAN-OS or
```
```
Panorama)
```
```
• NGFW (Managed by Strata Cloud
```
```
Manager)
```
Advanced SD-WAN for NGFW
One of these:
AIOps for NGFW Premium or Strata
Cloud Manager Pro
Strata Cloud Manager Essentials
```
(Supports only NGFWs)
```
```
If your branch firewall has a Direct Internet Access (DIA) link to a Software-as-a-Service (SaaS)
```
application, create a SaaS Quality profile to specify how one or more SaaS applications should be
monitored. SaaS Quality profiles are associated with an SD-WAN policy rule to determine how
the branch firewall determines the path quality thresholds for latency, jitter, and packet loss and
selects the preferred path for an outgoing packet.
The SaaS Quality profile supports up to four static IP addresses, or one fully qualified domain
```
name (FQDN) or URL per SaaS Quality profile. When multiple static IP addresses are configured,
```
the branch firewall monitors one IP address at a time in a cascading order based on how the IP
addresses are ordered in the SaaS Quality profile. For example, if you add IP1, IP2, IP3, and IP4,
the branch firewall monitors IP1 to determine if the path quality thresholds have been exceeded,
then continues to IP2, and so forth.
• PAN-OS & Panorama
• Strata Cloud Manager
SD-WAN Administration 122 ©2026 Palo Alto Networks, Inc.
Enable SD-WAN without Auto VPN
PAN-OS & Panorama
SD-WAN monitoring and reporting data displays the SaaS application and SaaS
application IP, FQDN, or URL as it is currently configured in the SaaS Quality profile
associated with an SD-WAN policy rule regardless of the time filter applied when viewing
your SD-WAN monitoring data.
For example, three days ago you initially configured the IP address of your SaaS
application as 192.168.10.50 in a SaaS Quality profile and had traffic match the SD-
WAN policy rule to which the SaaS Quality profile is associated. Today, you reconfigured
this existing SaaS Quality profile and changed the SaaS application IP address to
192.168.10.20. When you go review the SD-WAN monitoring data, all existing
monitoring data for this SaaS application display the IP address 192.168.10.20.
STEP 1 | Log in to the Panorama web interface.
STEP 2 | Select Objects > SD-WAN Link Management > SaaS Quality Profile and specify the Device
Group containing your SD-WAN configuration.
STEP 3 | Add a new SaaS quality profile.
STEP 4 | Enter a descriptive Name for the SaaS Quality profile.
```
STEP 5 | (Optional) Enable (check) Shared to make the SaaS Quality profile shared across all device
```
groups.
```
STEP 6 | (Optional) Enable (check) Disable override to disable overriding the SaaS Quality profile
```
configuration on the local firewall.
Disable override can only be enabled if Shared is disabled in the previous step.
STEP 7 | Configure the SaaS Monitoring Mode.
• Automatically monitor the SaaS application path health.
Enabled by default, Adaptive monitoring allows the branch firewall to passively monitor
the SaaS application session for send and receive activity to determine if the path quality
SD-WAN Administration 123 ©2026 Palo Alto Networks, Inc.
Enable SD-WAN without Auto VPN
thresholds have been exceeded. The SaaS application path health quality is automatically
determined without any additional health checks on the SD-WAN interface.
Adaptive SaaS monitoring is supported only for TCP SaaS applications.
• Configure the Static IP address for the SaaS application.
Create a SaaS Quality profile per critical SaaS application that you need monitored.
If a SaaS application has multiple IP addresses, configure a SaaS Quality profile with
the multiple static IP addresses for that SaaS application.
SaaS monitoring is resource-intensive and may impact firewall performance if
monitoring a large number of SaaS applications. It is a best practice to only monitor
those business-critical SaaS applications that need good usability.
1. Select IP Address/Object > Static IP Address and Add an IP address.
2. Enter the IP address of the SaaS application or select a configured address object.
3. Enter the Probe Interval by which the branch firewall probes the SaaS application path
for health information.
4. Click OK to save your configuration changes.
```
• Configure the fully qualified domain name (FQDN) for the SaaS application.
```
1. Configure a FQDN address object for the SaaS application.
2. Select IP Address/Object > FQDN and Add the FQDN.
3. Select the FQDN address object for the SaaS application.
4. Enter the Probe Interval by which the branch firewall probes the SaaS application path
for health information.
5. Click OK to save your configuration changes.
SD-WAN Administration 124 ©2026 Palo Alto Networks, Inc.
Enable SD-WAN without Auto VPN
• Configure the URL for the SaaS application.
URL monitoring is only supported for traffic over ports 80, 443, 8080, 8081, and
143.
1. Select HTTP/HTTPS.
2. Enter the Monitored URL of the SaaS application.
3. Enter the Probe Interval by which the branch firewall probes the SaaS application path
for health information.
The minimum probe interval supported for a SaaS application HTTP/HTTPS is 3 seconds.
4. Click OK to save your configuration changes.
STEP 8 | Select Commit and Commit and Push your configuration changes.
Strata Cloud Manager
STEP 1 | Log in to Strata Cloud Manager.
STEP 2 | Select Configuration > NGFW and Prisma Access and in the Overview, select the branch
folder for which you want to create your SD-WAN Link Management profiles.
To make the Error Correction profile available to all SD-WAN firewalls regardless of folder
association, select All Firewalls.
STEP 3 | Create a SaaS Quality profile.
The SaaS Quality profile specifies how one or more software-as-a-service applications
```
should be monitored if your branch firewall has a Direct Internet Access (DIA) link to a SaaS
```
SD-WAN Administration 125 ©2026 Palo Alto Networks, Inc.
Enable SD-WAN without Auto VPN
application. The SaaS Quality profile is associated with an SD-WAN policy rule to determine
how the branch firewall determines the path quality thresholds for latency, jitter, and packet
loss and selects the preferred path for an outgoing packet.
1. Select Network Policies > SD-WAN Policy > Profiles > SaaS Quality.
2. Add Profile.
3. Enter a descriptive Name.
4. Configure the SaaS Quality profile.
The following SaaS Monitoring Mode types are supported. Only a single SaaS
Monitoring Mode type is supported for a SaaS Quality profile.
• Adaptive—Passively monitor the SaaS application session for send and receive activity
to determine if the predefined path quality thresholds have been exceeded.
• Static IP Address—Add up to four static IP addresses to monitor and specify the
Probe Interval by which the branch firewall probes the SaaS application path for
health information.
• FQDN—Add one Fully Qualified Domain Name and specify the Probe Interval by
which the branch firewall probes the SaaS application path for health information.
• HTTP/HTTPS—Add a URL and specify the Probe Interval by which the branch
firewall probes the SaaS application path for health information.
5. Save.
Monitor SaaS Application at Branch using SD-WAN
Where Can I Use This? What Do I Need?
• NGFW Advanced SD-WAN for NGFW
If your organization is leveraging a business-critical SaaS application at a branch firewall location,
you can configure a SaaS Quality profile and associate it with a SD-WAN policy rule to monitor
the latency, jitter, and packet loss health metrics of the critical SaaS application and swap links
```
from an SD-WAN branch firewall to a SaaS application on a Direct Internet Access (DIA) link to
```
ensure application usability.
If the business-critical SaaS application DIA link health metric thresholds are exceeded, the link
is swapped to the next DIA link configured in the Traffic Distribution profile for all new sessions.
The existing session on the degraded DIA link is not swapped over to the next DIA link.
STEP 1 | Set up your SD-WAN deployment.
1. Install the SD-WAN plugin.
2. Set up Panorama and firewalls for SD-WAN.
3. Add SD-WAN Devices to Panorama.
4. (High availability configurations only) Configure SD-WAN devices in HA mode.
5. Plan your topology for SD-WAN with Auto VPN.
SD-WAN Administration 126 ©2026 Palo Alto Networks, Inc.
Enable SD-WAN without Auto VPN
STEP 2 | Define a link tag to group the SaaS application DIA links.
Create multiple Link Tags for your DIA links in order to apply different SD-WAN monitoring
settings for each SaaS application DIA link based on the link type.
Additionally, you can create a single Link Tag for multiple DIA links to group the links into a
single link bundle. Creating a single Link Tag for multiple DIA links allows you to aggregate
bandwidth between bundled links and allow the firewall to distribute sessions between
multiple links.
STEP 3 | Configure an SD-WAN interface profile to define the characteristics of your ISP connection
and specify the speed of the DIA link, how frequently the branch firewall monitors the link,
and select the Link Tag to specify to which link the SD-WAN Interface profile applies.
If you created multiple Link Tags, you must configure an SD-WAN Interface profile for each
Link Tag.
If you created a link bundle by assigning multiple DIA links to a single Link Tag, specifying that
link tag applies the SD-WAN Interface profile settings to all DIA links in the bundle.
STEP 4 | Configure a physical Ethernet interface for each SaaS application DIA link.
All physical Ethernet interfaces for DIA links must be Layer3.
STEP 5 | Configure a Virtual SD-WAN Interface that groups all physical Ethernet interfaces for the
SaaS application DIA links into a single interface group.
The firewall virtual router uses this virtual SD-WAN interface to route SD-WAN traffic to a
DIA location. The SD-WAN path health and Traffic Distribution profiles in the SD-WAN policy
rule then determine which path to use and the order in which to consider new paths if a path
health deteriorates.
```
STEP 6 | Define your custom SD-WAN application thresholds (using path quality profiles) to configure
```
the latency, jitter, and packet loss thresholds and sensitivity in order to specify when the
branch firewall should swap to the next DIA link.
STEP 7 | Create a SaaS quality profile to specify your SaaS application and the frequency the DIA link
is monitored.
STEP 8 | Create a traffic distribution profile to specify the order the branch firewall swaps to DIA links
in the event of link health degradation.
STEP 9 | Configure an SD-WAN policy rule to specify the SaaS application and link health metrics, and
determine how the firewall selects the preferred link for the critical SaaS application traffic.
In the Application tab, add the SaaS application you are monitoring to the SD-WAN
policy rule to ensure the SaaS monitoring settings are applied only to the desired SaaS
application.
SD-WAN Administration 127 ©2026 Palo Alto Networks, Inc.
Enable SD-WAN without Auto VPN
Configure Hub Failover from Branch to Same SaaS Application Destination
Where Can I Use This? What Do I Need?
• NGFW Advanced SD-WAN for NGFW
If your organization is leveraging a SaaS application at a branch firewall location but the branch
firewall has no healthy DIA links to swap to, you can configure the hub firewall as a failover
alternative to maintain a healthy connection to your SaaS application.
If the SaaS application DIA link health metric thresholds are exceeded and the branch firewall has
no healthy DIA links available, the link is swapped to the next hub firewall for all new sessions.
The existing session on the degraded DIA link is not swapped over to the hub firewall.
For example, say your branch and hub firewalls are located in the same region and access a SaaS
application using the same destination IP. You can configure the hub firewall to act as a failover
in the event there are no healthy DIA links from the branch firewall to the SaaS application by
configuring an identically named SaaS Quality profile on both the branch and hub firewalls to
automatically failover to the hub firewall if no healthy DIA links are available from the branch
firewall. This allows you to maintain a health path for your SaaS application and maintain accurate
end-to-end SaaS application monitoring data without congesting your network bandwidth.
STEP 1 | Set up your SD-WAN deployment.
1. Install the SD-WAN plugin.
2. Set up Panorama and firewalls for SD-WAN.
3. Add SD-WAN Devices to Panorama.
4. (High availability configurations only) Configure SD-WAN devices in HA mode.
5. Plan your topology for SD-WAN with Auto VPN.
STEP 2 | Define a link tag to group the SaaS application DIA links.
Create multiple Link Tags for your DIA links in order to apply different SD-WAN monitoring
settings for each SaaS application DIA link based on the link type.
Additionally, you can create a single Link Tag for multiple DIA links to group the links into a
single link bundle.
STEP 3 | Configure an SD-WAN interface profile to define the characteristics of your ISP connection
and specify the speed of the DIA link, how frequently the branch firewall monitors the link,
and select the Link Tag to specify to which link the SD-WAN Interface profile applies.
If you created multiple Link Tags, you must configure an SD-WAN Interface profile for each
Link Tag.
If you created a link bundle by assigning multiple DIA links to a single Link Tag, specifying that
link tag applies the SD-WAN Interface profile settings to all DIA links in the bundle.
STEP 4 | Configure a physical Ethernet interface for each SaaS application DIA link.
All physical Ethernet interfaces for DIA links must be Layer3.
SD-WAN Administration 128 ©2026 Palo Alto Networks, Inc.
Enable SD-WAN without Auto VPN
STEP 5 | Configure a virtual SD-WAN interface that groups all physical Ethernet interfaces for the
SaaS application DIA links into a single interface group.
The firewall virtual router uses this virtual SD-WAN interface to route SD-WAN traffic to a
DIA location. The SD-WAN path health and Traffic Distribution profiles in the SD-WAN policy
rule then determine which path to use and the order in which to consider new paths if a path
health deteriorates.
STEP 6 | Create identically named SaaS quality profiles for both the hub and branch firewalls.
Two identically named SaaS Quality profiles must be configured on the hub and branch
firewalls to successfully leverage the hub firewall as an alternative failover. The easiest
way to accomplish this is to create a single SaaS Quality profile in the Shared device group.
SD-WAN Administration 129 ©2026 Palo Alto Networks, Inc.
Enable SD-WAN without Auto VPN
Alternatively, you can create two SaaS Quality profiles with identical names in different device
groups and push them to your hub and branch firewalls.
1. Select Objects > SD-WAN Link Management > SaaS Quality Profile, and from the
Device Group drop-down select Shared.
2. Add a new SaaS Quality profile.
3. Enter a descriptive Name for the SaaS Quality profile.
4. Enable (check) Shared to make the SaaS Quality profile shared across all device groups.
This is required to make the SaaS Quality profile available to all device groups your
branch and hub firewalls belong to.
5. Enable (check) Disable override to disable overriding the SaaS Quality profile
configuration on the local firewall.
6. Configure the SaaS Monitoring Mode using one of the following methods.
• Configure the Static IP address for the SaaS application.
Create a SaaS Quality profile per SaaS application. If a SaaS application has
multiple IP addresses, configure a SaaS Quality profile with the multiple static
IP addresses for that SaaS application.
1. Select IP Address/Object > Static IP Address and Add an IP address.
2. Enter the IP address of the SaaS application or select a configured address object.
3. Enter the Probe Interval by which the branch firewall probes the SaaS application
path for health information.
4. Click OK to save your configuration changes.
```
• Configure the fully qualified domain name (FQDN) for the SaaS application.
```
1. Configure a FQDN address object for the SaaS application.
2. Select IP Address/Object > FQDN and Add the FQDN.
3. Select the FQDN address object for the SaaS application.
4. Enter the Probe Interval by which the branch firewall probes the SaaS application
path for health information.
5. Click OK to save your configuration changes.
• Configure the URL for the SaaS application.
URL monitoring is only supported for traffic over ports 80, 443, 8080, 8081,
and 143.
1. Select HTTP/HTTPS.
2. Enter the Monitored URL of the SaaS application.
3. Enter the Probe Interval by which the branch firewall probes the SaaS application
path for health information.
4. Click OK to save your configuration changes.
STEP 7 | Create a traffic distribution profile to specify the order the branch firewall swaps from DIA
links to VPN links to the hub firewall in the event of link health degradation.
SD-WAN Administration 130 ©2026 Palo Alto Networks, Inc.
Enable SD-WAN without Auto VPN
STEP 8 | Configure an SD-WAN policy rule to specify the SaaS application and link health metrics, and
determine how the firewall selects the preferred link for the critical SaaS application traffic.
In the Application tab, add the SaaS application you are monitoring to the SD-WAN
policy rule to ensure the SaaS monitoring settings are applied only to the desired SaaS
application.
Configure Hub Failover from Branch to Different SaaS Application Destination
Where Can I Use This? What Do I Need?
• NGFW Advanced SD-WAN for NGFW
If your organization is leveraging a SaaS application at a branch firewall location but the branch
firewall has no healthy DIA links to swap to, you can configure the hub firewall as a failover
alternative to maintain a healthy connection to your SaaS application using a SaaS Quality profile
pointing to a different SaaS application destination.
If the SaaS application DIA link health metric thresholds are exceeded and the branch firewall has
no healthy DIA links available, the link is swapped to the next hub firewall for all new sessions.
The existing session on the degraded DIA link is not swapped over to the hub firewall.
For example, say your branch and hub firewalls are located on opposite sides of the country and
access a SaaS cloud application deployed in a cloud provider such as GCP. You can configure
the hub firewall to act as a failover in the event there are no healthy DIA links from the branch
firewall to the SaaS application. To accomplish this, configure an identically named SaaS Quality
profile on both the branch and hub firewalls to automatically failover to the hub firewall if no
healthy DIA links are available from the branch firewall. The SaaS Quality profile configured on
the hub firewall to points to the on-ramp location closest to the hub to take advantage of local
resources closest to it. This allows you flexibility in specifying healthy failover paths and the
ability to maintain accurate end-to-end SaaS application monitoring data without congesting your
network bandwidth.
STEP 1 | Set up your SD-WAN deployment.
1. Install the SD-WAN plugin.
2. Set up Panorama and firewalls for SD-WAN.
3. Add SD-WAN Devices to Panorama.
4. (High availability configurations only) Configure SD-WAN devices in HA mode.
5. Plan your topology for SD-WAN with Auto VPN.
STEP 2 | Define a link tag to group the SaaS application DIA links.
Create multiple Link Tags for your DIA links in order to apply different SD-WAN monitoring
settings for each SaaS application DIA link based on the link type.
Additionally, you can create a single Link Tag for multiple DIA links to group the links into a
single link bundle.
SD-WAN Administration 131 ©2026 Palo Alto Networks, Inc.
Enable SD-WAN without Auto VPN
STEP 3 | Configure an SD-WAN interface profile to define the characteristics of your ISP connection
and specify the speed of the DIA link, how frequently the branch firewall monitors the link,
and select the Link Tag to specify to which link the SD-WAN Interface profile applies.
If you created multiple Link Tags, you must configure an SD-WAN Interface profile for each
Link Tag.
If you created a link bundle by assigning multiple DIA links to a single Link Tag, specifying that
link tag applies the SD-WAN Interface profile settings to all DIA links in the bundle.
STEP 4 | Configure a physical Ethernet interface for each SaaS application DIA link.
All physical Ethernet interfaces for DIA links must be Layer3.
STEP 5 | Configure a Virtual SD-WAN Interface that groups all physical Ethernet interfaces for the
SaaS application DIA links into a single interface group.
The firewall virtual router uses this virtual SD-WAN interface to route SD-WAN traffic to a
DIA location. The SD-WAN path health and Traffic Distribution profiles in the SD-WAN policy
rule then determine which path to use and the order in which to consider new paths if a path
health deteriorates.
STEP 6 | Create identically named SaaS quality profiles for both the hub and branch firewalls.
Two identically named SaaS Quality profiles must be configured on the hub and branch
firewalls to successfully leverage the hub firewall as an alternative failover. Create two SaaS
SD-WAN Administration 132 ©2026 Palo Alto Networks, Inc.
Enable SD-WAN without Auto VPN
Quality profiles with identical names each pointing to a different SaaS application destination
in different device groups and push them to your hub and branch firewalls.
1. Select Objects > SD-WAN Link Management > SaaS Quality Profile, and select the
target device group containing the branch firewall from the Device Group drop-down.
2. Add a new SaaS Quality profile.
3. Enter a descriptive Name for the SaaS Quality profile.
4. Enable (check) Disable override to disable overriding the SaaS Quality profile
configuration on the local firewall.
5. Configure the SaaS Monitoring Mode using one of the following methods.
• Configure the Static IP address for the SaaS application.
Create a SaaS Quality profile per SaaS application. If a SaaS application has
multiple IP addresses, configure a SaaS Quality profile with the multiple static
IP addresses for that SaaS application.
1. Select IP Address/Object > Static IP Address and Add an IP address.
2. Enter the IP address of the SaaS application or select a configured address object.
3. Enter the Probe Interval by which the branch firewall probes the SaaS application
path for health information.
4. Click OK to save your configuration changes.
```
• Configure the fully qualified domain name (FQDN) for the SaaS application.
```
1. Configure a FQDN address object for the SaaS application.
2. Select IP Address/Object > FQDN and Add the FQDN.
3. Select the FQDN address object for the SaaS application.
4. Enter the Probe Interval by which the branch firewall probes the SaaS application
path for health information.
5. Click OK to save your configuration changes.
• Configure the URL for the SaaS application.
URL monitoring is only supported for traffic over ports 80, 443, 8080, 8081,
and 143.
1. Select HTTP/HTTPS.
2. Enter the Monitored URL of the SaaS application.
3. Enter the Probe Interval by which the branch firewall probes the SaaS application
path for health information.
4. Click OK to save your configuration changes.
6. Select Objects > SD-WAN Link Management > SaaS Quality Profile, and select the
target device group containing the hub firewall from the Device Group drop-down.
7. Repeat Steps 6.2 through 6.5 to create an identically named SaaS Quality profile for a
SaaS application at a different destination.
SD-WAN Administration 133 ©2026 Palo Alto Networks, Inc.
Enable SD-WAN without Auto VPN
This step is required to make in identically named SaaS Quality profile in the device
group your hub firewall belongs to.
STEP 7 | Create a traffic distribution profile to specify the order the branch firewall swaps from DIA
links to VPN links to the hub firewall in the event of link health degradation.
STEP 8 | Configure an SD-WAN policy rule to specify the SaaS application and link health metrics, and
determine how the firewall selects the preferred link for the critical SaaS application traffic.
In the Application tab, add the SaaS application you are monitoring to the SD-WAN
policy rule to ensure the SaaS monitoring settings are applied only to the desired SaaS
application.
SD-WAN Traffic Distribution Profiles
Where Can I Use This? What Do I Need?
• NGFW Advanced SD-WAN for NGFW
One of these:
AIOps for NGFW Premium or Strata
Cloud Manager Pro
Strata Cloud Manager Essentials
```
(Supports only NGFWs)
```
In an SD-WAN topology, the firewall detects a brownout, a blackout, and path deterioration per
application and selects a new path to ensure you experience the best performance for your critical
business applications. Having multiple ISP links allows you to scale your traffic capacity and
reduce costs. The new path selection occurs in less than one second if you leave path monitoring
```
and probe frequency with default settings; otherwise, new path selection could take more than
```
one second.
To implement such path selection, the firewall uses SD-WAN policy rules, which reference a
Traffic Distribution profile that specifies how to select paths for session load distribution and for
failover to a better path when path quality for an application deteriorates.
```
Decide which traffic distribution method an application or service (that matches an SD-WAN
```
```
policy rule) should use:
```
• Best Available Path—Select this method if cost is not a factor and you will allow applications
to use any path out of the branch. The firewall uses path quality metrics to distribute traffic
and to fail over to one of the links belonging to a Link Tag in the list, thus providing the best
application experience to users.
• Top-Down Priority—If you have expensive or low-capacity links that you want used only as
a last resort or as a backup link, use the Top-Down Priority method and place the tags that
include those links last in the list of Link Tags in the profile. The firewall uses the top Link Tag
in the list first to determine the links on which to session load traffic and on which to fail over.
If none of the links in the top Link Tag are qualified based on the Path Quality profile, the
firewall selects a link from the second Link Tag in the list. If none of the links in the second Link
SD-WAN Administration 134 ©2026 Palo Alto Networks, Inc.
Enable SD-WAN without Auto VPN
Tag are qualified, the process continues as necessary until the firewall finds a qualified link in
the last Link Tag. If all associated links are overloaded and no link meets quality thresholds, the
firewall uses the Best Available Path method to select a link on which to forward traffic. At the
start of a failover event, the firewall starts at the top of the Top-Down Priority list of Link Tags
to find a link to which it fails over.
```
• Weighted Session Distribution—Select this method if you want to manually load traffic (that
```
```
matches the rule) onto your ISP and WAN links and you don’t require failover during brownout
```
conditions. You manually specify the link’s load when you apply a static percentage of new
sessions that the interfaces grouped with a single Link Tag will get. The firewall distributes
new sessions using round robin among the links having the specified Link Tags, until the link
assigned the lowest percentage reaches that percentage of sessions. The firewall then uses the
```
remaining link(s) in the same manner. You might select this method for applications that aren’t
```
sensitive to latency and that require a lot of the link’s bandwidth capacity, such as large branch
backups and large file transfers.
If the link experiences brownout, the firewall doesn’t redirect the matching traffic to a
different link.
In the event of a failing path condition, the traffic distribution method you choose for
```
application(s) in an SD-WAN policy rule, along with the Link Tags on groups of links, determine if
```
```
and how the firewall selects a new path (performs link failover) as follows:
```
Path Condition Top-Down Priority Best Available Path Weighted Session
Distribution
Session on existing
path failed a path
health threshold
```
(brownout)
```
Affected session fails
```
over to better path (if
```
```
available)
```
Affected session fails
```
over to better path (if
```
```
available)
```
Affected sessions
don’t fail over
Top-Down or Best
Available Path
```
recovered: existing
```
path is still qualified
```
(good)
```
Affected session fails
back to previous path
Affected session
stays on existing
path, doesn’t fail back
Affected sessions
don’t fail over
Top-Down or Best
Available Path
```
recovered: existing
```
path fails a health
check
All sessions fail back
to previous path
Selective sessions fail
back to previous path
until affected existing
path recovers
Affected sessions
don’t fail over
Existing path is down
```
(blackout)
```
All sessions fail over
to next path on list
All sessions fail over
to next best path
All sessions fail over
to other tags based
on weight settings
Brownout with no
```
qualified (better) path
```
Take best available
path
Take best available
path
Take best available
path
SD-WAN Administration 135 ©2026 Palo Alto Networks, Inc.
Enable SD-WAN without Auto VPN
Additionally, the firewall automatically performs session load sharing among interface members of
a single Link Tag. After those interfaces approach their maximum Mbps, new sessions flow over to
```
interfaces having a different Link Tag (based on the traffic distribution method) if those interfaces
```
have better health metrics.
Path Condition Top-Down Priority Best Available Path Weighted Session
Distribution
Multiple links with
the same SD-WAN
Tag
Share session load
equally among links
within SD-WAN Tag
Share session load
based on best path
within SD-WAN Tag
Share session load
based on % weight
assigned to SD-WAN
Tag
Multiple links with
different SD-WAN
Tags
Share session load
based on list priority,
```
load link(s) in first SD-
```
WAN Tag first.
Share session load
based on best path
from all SD-WAN
Tags
Share session load
based on % weight
assigned to SD-WAN
Tags
The following figure illustrates an example of a Traffic Distribution profile that uses the Top-
Down Priority method. The #1, #2, and #3 are the order of Link Tags of links the firewall
examines, if necessary, to find a healthy path to complete an application session failover. For each
separate failover event that arises, the firewall starts at the beginning of the Top-Down list of Link
Tags.
SD-WAN Administration 136 ©2026 Palo Alto Networks, Inc.
Enable SD-WAN without Auto VPN
1. In this Top-Down Priority example, packets from a branch carrying a specific application (for
```
example, office365-enterprise-access) arrive at the firewall. The firewall uses the route table
```
to determine the next hop to the destination and the outgoing interface, which is the virtual
SD-WAN interface tunnel named sdwan.901. The Security policy rule allows the packets. The
```
packets then match an SD-WAN policy rule (named Office365 to Hub1) that specifies the
```
destination zone for the hub. The firewall uses the SD-WAN policy rule’s Path Quality profile,
Traffic Distribution profile, and that profile’s Link Tags to determine which interface member
```
(link) from sdwan.901 to use. The Traffic Distribution profile lists three Link Tags in this order:
```
```
#1 Cheap Broadband, #2 HQ Backhaul, and #3 Backup (which is the order of Link Tags the
```
```
firewall examines links to find a link to which it can fail over).
```
2. Assuming all paths are qualified (by the Path Quality profile), the firewall distributes the
packets to one of the physical links tagged with first Link Tag in the Traffic Distribution profile
```
list: Cheap Broadband. The sdwan.901 tunnel has two member interfaces (two carriers): the
```
cable modem VPN tunnel and the fiber service VPN tunnel. The firewall first examines a link by
round-robin, and chooses the first link it finds that is qualified, for example, the cable modem
link.
3. If the first Cheap Broadband link (cable modem) isn’t a qualified link, the firewall selects the
```
second Cheap Broadband link (fiber service).
```
4. If the second Cheap Broadband link (fiber service) isn’t a qualified link, the firewall selects the
link tagged with the #2 link tag HQ Backhaul, which is a more expensive MPLS link to the same
hub.
5. If the MPLS link isn’t a qualified link, the firewall selects the link tagged with the #3 link tag
Backup, which is an even more expensive 5G LTE link to the same hub.
6. If the firewall doesn’t find a qualified link to fail over to, it uses the Best Available method to
select a link.
7. Upon the start of a new failover event, the firewall starts at the top of the Top-Down list of
Link Tags to find a link to which it will fail over.
Keep in mind that SD-WAN traffic distribution is one of the later steps in the packet flow logic.
Let’s zoom out to see a broader view of the packet flow.
SD-WAN Administration 137 ©2026 Palo Alto Networks, Inc.
Enable SD-WAN without Auto VPN
Packet flow details for the figure are as follows:
1. When a session for an application arrives at the firewall, the firewall performs session lookup
to determine if the session is an existing session or new session.
2. A new session goes through session setup:
1. Forwarding lookup—The firewall gets the egress zone, egress interface, and virtual system
from the Layer 3 route table or Layer 2 Forwarding Database lookup, etc. For applications
that match an SD-WAN policy rule, the firewall uses the virtual SD-WAN interface as the
egress interface.
2. NAT Policy lookup—If session matches a NAT rule, firewall does another forwarding lookup
```
to determine the final (translated) egress interface and zone.
```
3. Security Policy lookup—If a Security Policy rule allows the session, the session is created and
installed in the session table. The firewall then performs additional classification using App-
ID™ and User-ID™.
3. Content Inspection—The firewall performs Threat Inspection (Anti-Spyware for IPS
```
[Vulnerability Protection], Antivirus, URL Filtering, WildFire®, etc.) on payload and headers as
```
needed.
4. The Forwarding/Egress stage performs path selection and forwards the packets. This stage is
where SD-WAN path selection occurs.
1. Packet Forwarding Process—The firewall uses the ingress interface to determine the
```
forwarding domain; performs routing, switching, or virtual wire forwarding.
```
2. SD-WAN path selection occurs when the application matches an SD-WAN policy rule; the
```
Path Quality profile determines path qualification; the Traffic Distribution profile determines
```
SD-WAN Administration 138 ©2026 Palo Alto Networks, Inc.
Enable SD-WAN without Auto VPN
the method of path selection and the order in which paths are considered during the
selection.
3. IPSec/SSL-VPN tunnel encryption occurs if needed.
4. Packet Egress Process - QoS shaping, DSCP rewrite, and IP fragmentation are applied (if
```
needed).
```
5. Transmit Packet—The firewall forwards the packet over the selected egress interface.
Now we zoom back in to examine the SD-WAN path selection logic in more detail.
1. The firewall consults the route table during Forwarding lookup; based on the destination
IP address matching a Layer 3 prefix, the firewall determines the egress SD-WAN virtual
interface. The packet is either going directly to the public internet or going back to the hub
through a secure VPN link.
2. The firewall monitors each path by performing health checks that run over a VPN tunnel. Each
DIA circuit has a VPN tunnel that monitors health information.
3. The application in the SD-WAN policy rule is associated with a Path Quality profile, and
the firewall compares the path’s actual average latency, jitter, and packet loss values to the
threshold values.
4. Any path that has a higher latency, jitter, or packet loss value than the threshold is not
selected.
5. All qualifying paths in the virtual SD-WAN interface are then subjected to the Traffic
```
Distribution profile’s method and path priority (ordering) logic. SD-WAN link tags group ISP
```
services together, and the order of these tags in the Traffic Distribution profile prioritizes the
paths during path selection.
6. Thus, the path quality profile and the traffic distribution profile together determine the next
best path to use and the firewall forwards the traffic out that link.
SD-WAN Administration 139 ©2026 Palo Alto Networks, Inc.
Enable SD-WAN without Auto VPN
Define Path Selection for SD-WAN Traffic
Where Can I Use This? What Do I Need?
```
• NGFW (Managed by PAN-OS or
```
```
Panorama)
```
```
• NGFW (Managed by Strata Cloud
```
```
Manager)
```
Advanced SD-WAN for NGFW
One of these:
AIOps for NGFW Premium or Strata
Cloud Manager Pro
Strata Cloud Manager Essentials
```
(Supports only NGFWs)
```
SD-WAN Traffic Distribution Profiles are a crucial component in optimizing application
performance across your SD-WAN deployment. These profiles enable you to define path
selection strategies for your network traffic, ensuring that critical business applications receive
the best possible service quality. A Traffic Distribution Profile determines how the firewall selects
paths for session load distribution and failover when path quality deteriorates for an application.
This profile works with SD-WAN policy rules to provide granular control over traffic routing
decisions.
When traffic matches an SD-WAN policy rule, the firewall uses the associated Traffic Distribution
Profile to determine how to distribute the traffic across available links. The profile's distribution
method, combined with real-time path quality measurements, guides the firewall in selecting the
optimal path for each session. For example, in a top-down priority configuration, the firewall first
attempts to use links associated with the topmost Link Tag in the list. If those links don't meet
the quality thresholds defined in the Path Quality Profile, it moves to the next Link Tag in the list,
continuing until it finds a qualified link.
Based on your SD-WAN configuration plan, create the SD-WAN traffic distribution profiles you
need based on how you want the applications in your SD-WAN policy rules to be session loaded
and to fail over.
• PAN-OS and Panorama
• Strata Cloud Manager
PAN-OS & Panorama
STEP 1 | Log in to the Panorama Web Interface.
STEP 2 | Ensure you already configured the Link Tags in an SD-WAN interface profile and committed
and pushed them. The Link Tags must be pushed to your hubs and branches in order for
Panorama™ to successfully associate the Link Tags you specify in this Traffic Distribution
profile to an SD-WAN interface profile.
STEP 3 | Select a Device Group.
SD-WAN Administration 140 ©2026 Palo Alto Networks, Inc.
Enable SD-WAN without Auto VPN
STEP 4 | Create a Traffic Distribution profile.
1. Select Objects > SD-WAN Link Management > Traffic Distribution Profile.
2. Add a Traffic Distribution profile by Name using a maximum of 31 alphanumeric
characters.
3. Select Shared only if you want to use this traffic distribution profile across all Device
```
Groups (both hubs and branches).
```
4. Select one traffic distribution method and add a maximum of four Link Tags that use this
method for this profile.
• Best Available Path—Add one or more Link Tags. During the initial packet exchanges,
before App-ID has classified the application in the packet, the firewall uses the path
```
in the tag that has the best health metrics (based on the order of tags). After the
```
```
firewall identifies the application, it compares the health (path quality) of the path it
```
```
was using to the health of the first path (interface) in the first Link Tag. If the original
```
```
path’s health is better, it remains the selected path; otherwise, the firewall replaces
```
the original path. The firewall repeats this process until it has evaluated all the paths
in the Link Tag. The final path is the path the firewall selects when a packet arrives
that meets the match criteria.
When a link becomes unqualified and must fail over to the next best path,
the firewall can migrate a maximum of 1,000 sessions per minute from the
unqualified link to the next best path. For example, suppose tunnel.901
```
has 3,000 sessions; 2,000 of those sessions match SD-WAN policy rule A
```
```
and 1,000 sessions match SD-WAN policy rule B (both rules have a traffic
```
```
distribution policy configured with Best Path Available). If tunnel.901
```
becomes unqualified, it takes three minutes to migrate the 3,000 sessions
from the unqualified link to the next best path.
• Top Down Priority—Add one or more Link Tags. The firewall distributes new sessions
```
(that meet the match criteria) to links using the top-to-bottom order of the Link
```
Tags you added. The firewall examines the first tag configured for this profile, and
examines the paths that use that tag, selecting the first path it finds that is qualified
```
(that is at or below the Path Quality thresholds for this rule). If no qualified path is
```
found from that Link Tag, firewall examines the paths that use the next Link Tag. If
the firewall finds no path after examining all paths in all of the Link Tags, the firewall
SD-WAN Administration 141 ©2026 Palo Alto Networks, Inc.
Enable SD-WAN without Auto VPN
uses the Best Available Path method. The first path selected is the preferred path
until one of the Path Quality thresholds for that path is exceeded, at which point the
firewall again starts at the top of the Link Tag list to find the new preferred path.
If you have only one link at the hub, that link supports all of the virtual
interfaces and DIA traffic. If you want to use the link types in a specific
order, you must apply a Traffic Distribution profile to the hub that specifies
Top Down Priority, and then order the Link Tags to specify the preferred
order. If you apply a Traffic Distribution profile that instead specifies Best
Available Path, the firewall will use the link, regardless of cost, to choose
the best performing path to the branch. In summary, Link Tags in a Traffic
Distribution profile, the Link Tag applied to a hub virtual interface, and a
VPN Failover Metric in an SD-WAN Interface Profile work only when the
Traffic Distribution profile specifies Top Down Priority.
• Weighted Session Distribution—Add one or more Link Tags and then enter the
Weight percentage for each Link Tag so that the weights total 100%. The firewall
performs session load distribution between Link Tags until their percentage
maximums are reached. If there is more than one path in the Link Tag, the firewall
distributes equally using round-robin until the path health metrics are reached, and
```
then distributes sessions to the other member(s) that are not at the limit.
```
If multiple physical interfaces have the same tag, the firewall distributes
```
matching sessions evenly among them. If all paths fail a health (path quality)
```
threshold, the firewall selects the path that has the best health statistics. If no
```
SD-WAN links are available (perhaps due to a blackout), the firewall uses static
```
or dynamic routing to route the matching packets.
If a packet is routed to a virtual SD-WAN interface, but the firewall cannot
find a preferred path for the session based on the SD-WAN policy’s Traffic
Distribution profile, the firewall implicitly uses the Best Available Path method
to find the preferred path. The firewall distributes any application sessions that
don’t match an SD-WAN policy rule based on the firewall’s implicit, final rule,
which distributes the sessions in round-robin order among all available links,
regardless of the Traffic Distribution profile.
If you prefer to control how the firewall distributes unmatched sessions, create
a final catch-all rule to distribute unmatched sessions to specific links in the
order you specify.
5. (Optional) After adding Link Tags, use the Move Up or Move Down arrows to change
the order of tags in the list, so they reflect the order in which you want the firewall to
use links for this profile and for the selected applications in the SD-WAN policy rule.
6. Click OK.
STEP 5 | Commit and Commit and Push your configuration changes.
STEP 6 | Commit your changes.
Strata Cloud Manager
SD-WAN Administration 142 ©2026 Palo Alto Networks, Inc.
Enable SD-WAN without Auto VPN
STEP 1 | Log in to Strata Cloud Manager.
STEP 2 | Select Configuration > NGFW and Prisma Access and in the Overview, select the branch
folder for which you want to create your SD-WAN Link Management profiles.
To make the Error Correction profile available to all SD-WAN firewalls regardless of folder
association, select All Firewalls.
STEP 3 | Create a Traffic Distribution profile.
The Traffic Distribution profile specifies how the firewall selects paths for session load
distribution and for path failover when the firewall detects a brownout, blackout, or path
deterioration for an application. Before you can configure a Traffic Distribution profile, you
must create all your link tags so the firewall can know which paths to fail over to.
1. Select Network Policies > SD-WAN Policy > Profiles > Traffic Distribution.
2. Add Profile.
3. Enter a descriptive Name.
4. Select the Traffic Distribution method the firewall uses to determine which path to fail
over to.
Only a single Traffic Distribution method is supported for a Traffic Distribution profile.
• Best Available Path—Select this method if cost isn’t a factor and you allow
applications to use any path out of the branch. The firewall uses the predefined Path
Quality metrics to distribute traffic and to fail over to one of the links belonging to a
Link Tag in the list, thus providing the best application experience to users.
• Top Down Priority—Select this method if you have expensive or low-capacity
links that you want used only as a last resort or as a backup link. When using this
method, order your Link Tags so that the paths you want used as a last resort are at
the bottom of the Link Tag list. The firewall uses the top Link Tag in the list first to
determine the links on which to session load traffic and on which to fail over. If none
of the links in the top Link Tag are qualified based on the predefined Path Quality
profile, the firewall selects a link from the second Link Tag in the list. If none of the
links in the second Link Tag are qualified, the process continues as necessary until the
firewall finds a qualified link in the last Link Tag. If all associated links are overloaded
and no link meets quality thresholds, the firewall uses the Best Available Path method
to select a link on which to forward traffic. At the start of a failover event, the firewall
starts at the top of the Top-Down Priority list of Link Tags to find a link to which it
fails over.
• Weighted Session Distribution—Select this method if you want to manually load
```
traffic (that matches the rule) onto your ISP and WAN links and you don’t require
```
failover during brownout conditions. You manually specify the link load when you
apply a static percentage of new sessions that the interfaces grouped with a single
Link Tag will get. The firewall distributes new sessions using round-robin among the
links having the specified Link Tags, until the link assigned the lowest percentage
reaches that percentage of sessions. The firewall then uses one or more remaining
links in the same manner. You might select this method for applications that aren’t
SD-WAN Administration 143 ©2026 Palo Alto Networks, Inc.
Enable SD-WAN without Auto VPN
sensitive to latency and that require much of the link’s bandwidth capacity, such as
large branch backups and large file transfers.
5. Add Link Tags .
When adding and ordering your Link Tags, be sure consider the Traffic Distribution
method you selected to ensure the firewall selects the appropriate path.
6. Save.
Recover Corrupted or Lost Data to Improve Reliability
Where Can I Use This? What Do I Need?
```
• NGFW (Managed by PAN-OS or
```
```
Panorama)
```
```
• NGFW (Managed by Strata Cloud
```
```
Manager)
```
Advanced SD-WAN for NGFW
One of these:
AIOps for NGFW Premium or Strata
Cloud Manager Pro
Strata Cloud Manager Essentials
```
(Supports only NGFWs)
```
```
Forward error correction (FEC) is a method of correcting certain data transmission errors that
```
occur over noisy communication lines, thereby improving data reliability without requiring
retransmission. FEC is helpful for applications that are sensitive to packet loss or corruption,
such as audio, VoIP, and video conferencing. With FEC, the receiving firewall can recover lost or
corrupted packets by employing parity bits that the sending encoder embeds in an application
flow. Repairing the flow avoids the need for SD-WAN data to fail over to another path or for
TCP to resend packets. FEC can also help with UDP applications by recovering the lost or corrupt
packets, since UDP does not retransmit packets.
SD-WAN FEC supports branch and hub firewalls acting as encoders and decoders. The FEC
mechanism has the encoder add redundant bits to a bitstream, and the decoder uses that
information to correct received data if necessary, before sending it to the destination.
SD-WAN also supports packet duplication as an alternative method of error correction. Packet
duplication performs a complete duplication of an application session from one tunnel to a second
tunnel. Packet duplication requires more resources than FEC and should be used only for critical
applications that have low tolerance for dropped packets.
Modern applications that have their own embedded recovery mechanisms may not need
FEC or packet duplication. Apply FEC or packet duplication only to applications that
```
can really benefit from such a mechanism; otherwise, much additional bandwidth and
```
CPU overhead are introduced without any benefit. Neither FEC nor packet duplication is
helpful if your SD-WAN problem is congestion.
```
Neither FEC nor packet duplication should be used on DIA links; they are only for VPN tunnel
```
links between branches and hubs.
FEC and packet duplication is supported only for SD-WAN enabled PAN-OS firewalls. FEC
and packet duplication is not supported for Prisma Access Hubs.
SD-WAN Administration 144 ©2026 Palo Alto Networks, Inc.
Enable SD-WAN without Auto VPN
```
To configure FEC or packet duplication on the encoder (the side that initiates FEC or packet
```
```
duplication):
```
• Create an SD-WAN Interface Profile that specifies Eligible for Error Correction Profile
interface selection and apply the profile to one or more interfaces.
• Create an Error Correction Profile to implement FEC or packet duplication.
• Apply the Error Correction Profile to an SD-WAN policy rule and specify a single application to
which the rule applies.
```
• Push the configuration to encoders. (The decoder [the receiving side] requires no specific
```
```
configuration for FEC or packet duplication; the mechanisms are enabled by default on the
```
```
decoder as long as the encoder initiates the error correction.)
```
FEC and packet duplication support an MTU of 1,340 bytes. A packet larger than that will
not go through the FEC or packet duplication process.
• PAN-OS & Panorama
• Strata Cloud Manager
PAN-OS & Panorama
FEC and packet duplication functionality require Panorama to run PAN-OS 10.0.2 or a later
release and SD-WAN plugin 2.0 or a later release that is compatible with the PAN-OS release.
The encoder and decoder must both be running PAN-OS 10.0.2 or a later release. If one branch
or hub is running an older software release than what is required, traffic with an FEC or packet
duplication header is dropped at that firewall.
Beginning with PAN-OS 10.0.3, FEC and packet duplication are supported in a full mesh topology,
in addition to the hub-spoke topology already supported.
STEP 1 | Log in to the Panorama Web Interface.
STEP 2 | Define your ISP connections and link types, where you select Eligible for Error Correction
Profile interface selection to indicate that the firewall can automatically use the interfaces
SD-WAN Administration 145 ©2026 Palo Alto Networks, Inc.
Enable SD-WAN without Auto VPN
```
(where the SD-WAN Interface Profile is applied) for error correction. Whether this option
```
defaults to selected or not depends on the Link Type you select for the profile.
You can have Eligible for Error Correction Profile interface selection unchecked in a
profile and apply the profile to an expensive 5G LTE link, for example, so that costly
error correction is never performed on that link.
STEP 3 | Configure a physical Ethernet interface for SD-WAN and apply the SD-WAN Interface
Profile that you created to an Ethernet interface.
STEP 4 | Create an Error Correction Profile for FEC or packet duplication.
1. Select Objects > SD-WAN Link Management > Error Correction Profile.
2. Add an Error Correction profile and enter a descriptive Name of up to 31 alphanumeric
```
characters; for example, EC_VOIP.
```
3. Select Shared to make the Error Correction profile available to all device groups on
Panorama and to the default vsys on a single-vsys hub or branch, or to vsys1 on a multi-
vsys hub or branch to which you push this configuration.
4. Specify the Activate when packet loss exceeds (%) setting—When packet loss exceeds
this percentage, FEC or packet duplication is activated for the configured applications in
```
the SD-WAN policy rule where this Error Correction profile is applied. Range is 1 to 99;
```
the default is 2.
5. Select Forward Error Correction or Packet Duplication to indicate which error
correction method the firewall uses when an SD-WAN policy rule references this SD-
```
WAN Interface Profile; the default is Forward Error Correction. If you select Packet
```
```
Duplication, SD-WAN selects an interface over which to send duplicate packets. (SD-
```
WAN selects one of the interfaces you configured with Eligible for Error Correction
```
Profile interface selection in the prior step.)
```
6. (Forward Error Correction only) Select the Packet Loss Correction Ratio: 10% (20:2),
```
20% (20:4), 30% (20:6), 40% (20:8), or 50% (20:10)—Ratio of parity bits to data packets;
```
SD-WAN Administration 146 ©2026 Palo Alto Networks, Inc.
Enable SD-WAN without Auto VPN
```
the default is 10% (20:2). The higher the ratio of parity bits to data packets that the
```
```
sending firewall (encoder) sends, the higher the probability that the receiving firewall
```
```
(decoder) can repair packet loss. However, a higher ratio requires more redundancy and
```
therefore more bandwidth overhead, which is a tradeoff for achieving error correction.
The parity ratio applies to the encoding firewall’s outgoing traffic. For example, if the hub
firewall parity ratio is 50% and the branch firewall parity ratio is 20%, the hub firewall
will receive 20% and the branch firewall will receive 50%.
7. Specify the Recovery Duration (ms)—Maximum number of milliseconds that the
```
receiving firewall (decoder) can spend performing packet recovery on lost data packets
```
```
using the parity packets it received (range is 1 to 5,000; default is 1,000). The firewall
```
immediately sends data packets it receives to the destination. During the Recovery
Duration, the decoder performs packet recovery for any lost data packets. When the
recovery duration expires, all the parity packets are released. You configure the recovery
duration in the Error Correction Profile for the encoder, which sends the Recovery
Duration value to the decoder. A Recovery Duration setting on the decoder has no
impact.
Start by using the default Recovery Duration setting and adjust it if necessary,
based on your testing with normal and intermittent brown-outs.
8. Click OK.
STEP 5 | Configure an SD-WAN policy rule, reference the Error Correction Profile you created in the
rule, and specify a critical application to which the rule applies.
Specify only one application in the SD-WAN policy rule when configuring FEC or
packet duplication. You should not combine multiple applications in a single policy rule
for FEC or packet duplication.
STEP 6 | Commit and Commit and Push your configuration changes to the encoding firewalls
```
(branches and hubs).
```
Strata Cloud Manager
STEP 1 | Log in to Strata Cloud Manager.
SD-WAN Administration 147 ©2026 Palo Alto Networks, Inc.
Enable SD-WAN without Auto VPN
STEP 2 | Select Configuration > NGFW and Prisma Access and in the Overview, select the branch
folder for which you want to create your SD-WAN Link Management profiles.
To make the Error Correction profile available to all SD-WAN firewalls regardless of folder
association, select All Firewalls.
STEP 3 | Create an Error Correction profile.
```
SD-WAN supports Forward Error Correction (FEC) to correct certain data transmission
```
errors that occur over noisy communication lines to improve data reliability without requiring
retransmission or Packet Duplication to duplicate application sessions from one tunnel to
another.
1. Select Network Policies > SD-WAN Policy > Profiles > Error Correction.
To make the Error Correction profile available to all SD-WAN firewalls regardless of
folder association, select All Firewalls.
2. Add Profile.
3. Enter a descriptive Name.
4. Specify the Activation Threshold (Packet Loss %) to set the packet loss percentage that
must be exceeded before error correction is activated.
5. Select the error correction Mode.
Only a single error correction Mode can be selected for an Error Correction profile.
6. (Forward Error Correction only) Select the Packet Loss Correction Ratio to specify the
ratio of parity bits to data packets.
The higher the ratio of parity bits to data packets that the sending firewall sends, the
higher the probability that the receiving firewall can repair packet loss. However, a
higher ratio requires more redundancy and therefore more bandwidth overhead, which
is a tradeoff for achieving error correction. The parity ratio applies to the receiving
firewall’s outgoing traffic.
```
Also specify the Recovery Duration (ms) to set the maximum number of milliseconds
```
that the receiving firewall can spend performing packet recovery on last data packets
using the parity packets it received.
7. Save.
SD-WAN Administration 148 ©2026 Palo Alto Networks, Inc.
SD-WAN Traffic Steering Using
Policy Rules
Where Can I Use This? What Do I Need?
• NGFW Advanced SD-WAN for NGFW
One of these:
AIOps for NGFW Premium or Strata
Cloud Manager Pro
Strata Cloud Manager Essentials
```
(Supports only NGFWs)
```
You need to create an SD-WAN policy to shape the traffic that egresses the SD-WAN firewall.
You may want to create different SD-WAN policy rules depending on the traffic types and link
```
types that you have. Each SD-WAN policy has a traffic distribution policy (TDP) and path qualify
```
```
profile (PQP) attached to it. PQP contains thresholds for latency, jitter, and packet loss. When one
```
of the thresholds is exceeded, the firewall selects a new path for the applications based on the
link tags added under the traffic distribution policy. As a best practice, leveraging the predefined
PQP can help you get started quickly without having to figure out the correct latency, jitter, and
packet loss thresholds for each application you need to manage.
Palo Alto Networks has created the SD-WAN predefined path quality profiles by testing
multiple applications from each application category in a controlled environment. The latency,
jitter, and packet loss conditions were adjusted independently to see where the application’s
user experience dropped below acceptable levels and the results were compiled with other
applications from the same category to determine an acceptable starting point. If needed, you
can tune the values provided by the predefined PQPs as you gain more experience on how the
application responds to the threshold values, and path failover can be accelerated or postponed
to achieve the desired user experience. As a best practice, make a copy of the predefined profile
and adjust the latency, jitter, and packet loss values as needed. In general, raising the values delays
SD-WAN path failover and lowering them accelerates path failover.
149
SD-WAN Traffic Steering Using Policy Rules
Define Your Application-based Traffic Steering Policies
Where Can I Use This? What Do I Need?
```
• NGFW (Managed by PAN-OS or
```
```
Panorama)
```
```
• NGFW (Managed by Strata Cloud
```
```
Manager)
```
Advanced SD-WAN for NGFW
One of these:
AIOps for NGFW Premium or Strata
Cloud Manager Pro
Strata Cloud Manager Essentials
```
(Supports only NGFWs)
```
```
An SD-WAN policy rule specifies application(s) and/or service(s) and a traffic distribution profile
```
to determine how the firewall selects the preferred path for an incoming packet that doesn’t
belong to an existing session and that matches all other criteria, such as source and destination
zones, source and destination IP addresses, and source user. The SD-WAN policy rule also
specifies a path quality profile of thresholds for latency, jitter, and packet loss. When one of the
```
thresholds is exceeded, the firewall selects a new path for the application(s) and/or service(s).
```
When monitoring your SD-WAN traffic, traffic originating from a source behind the hub device is
evaluated against the SD-WAN policies pushed to the hub device as it enters the hub device, and
because the path selection decision has already been made, the branch device does not evaluate
the traffic against its SD-WAN policies as it passes through the branch device to the final target
device. Conversely, traffic originating from a source behind the branch device is evaluated against
the SD-WAN policies pushed to the branch device and not by hub device. The logs from both the
hub and branch are aggregated, and for the same traffic, two session entries are displayed but
only the SD-WAN device that originally evaluated the traffic contains the SD-WAN details.
• PAN-OS & Panorama
• Strata Cloud Manager
PAN-OS & Panorama
STEP 1 | Log in to the Panorama Web Interface.
STEP 2 | Select Policies > SD-WAN and select the appropriate device group from the Device Group
context drop-down.
STEP 3 | Add an SD-WAN policy rule.
STEP 4 | On the General tab, enter a descriptive Name for the rule.
STEP 5 | On the Source tab, configure the source parameters of the policy rule.
1. Add the Source Zone or select Any source zone
2. Add one or more source addresses, set an external dynamic list (EDL), or select Any
Source Address.
3. Add one or more source users or select any Source User.
SD-WAN Administration 150 ©2026 Palo Alto Networks, Inc.
SD-WAN Traffic Steering Using Policy Rules
STEP 6 | On the Destination tab, configure the destination parameters of the policy rule.
1. Add the Destination Zone or select Any destination zone.
2. Add one or more destination addresses, set an EDL, or select Any Destination Address.
STEP 7 | On the Application/Service tab, attach your SD-WAN Link Management profiles and specify
your applications and services.
```
(SD-WAN plugin 2.0 and later versions) PAN-OS 10.0.2 supports associating only a
```
SaaS Quality Profile or an Error Correction but not both. If you associate one of these
profiles with an SD-WAN policy rule, you cannot associate the other.
For example, if you associate a SaaS Quality profile with an SD-WAN policy rule, you
are unable to associate an Error Correction profile with the same SD-WAN policy rule.
1. Select the Path Quality or define your custom SD-WAN application thresholds (using
```
path quality profiles).
```
2. (SD-WAN plugin 2.0 and later versions) Select the SaaS Quality Profile or create a SaaS
```
quality profile if the branch firewall has a Direct Internet Access (DIA) link to a SaaS
```
```
application. The default is None (disabled).
```
3. (SD-WAN plugin 2.0 and later versions) Select the Error Correction Profile or create an
```
error correction profile to apply forward error correction (FEC) or packet duplication to
```
```
the applications that match the SD-WAN policy rule. The default is None (disabled).
```
4. Add Applications and select one or more applications from the list or select Any
applications. All applications you select are subject to the health thresholds specified in
the Path Quality profile you selected. If a packet matches one of these applications and
```
that application exceeds one of the health thresholds in the Path Quality profile (and the
```
```
packet matches the remaining rule criteria), the firewall selects a new preferred path.
```
Add only business-critical applications and applications that are sensitive to
path conditions for their usability.
```
(SD-WAN plugin 2.0 and later versions) If you associate a SaaS Quality Profile
```
in Adaptive mode with the SD-WAN policy, add the specific SaaS applications
you want to monitor. Using adaptive monitoring for all applications that match
the SD-WAN policy rule may impact the performance of the SD-WAN firewall.
```
(SD-WAN plugin 2.0 and later versions) If you associate a SaaS Quality Profile
```
with a specified SaaS application, add the SaaS application to the SD-WAN
rule to ensure the SaaS monitoring settings are applied only to the desired SaaS
application.
5. Add Services and select one or more services from the list or select Any services. All
services you select are subject to the health thresholds specified in the Path Quality
profile you selected. If a packet matches one of these services and that service exceeds
SD-WAN Administration 151 ©2026 Palo Alto Networks, Inc.
SD-WAN Traffic Steering Using Policy Rules
```
one of the health thresholds in the Path Quality profile (and the packet matches the
```
```
remaining rule criteria), the firewall selects a new preferred path.
```
Add only business-critical services and services that are sensitive to path
conditions for their usability.
STEP 8 | On the Path Selection tab, select a Traffic Distribution profile or create a traffic distribution
```
profile. When an incoming packet (unassociated with a session) matches all the match criteria
```
in the rule, the firewall uses this Traffic Distribution profile to select a new preferred path.
SD-WAN Administration 152 ©2026 Palo Alto Networks, Inc.
SD-WAN Traffic Steering Using Policy Rules
STEP 9 | On the Target tab, use one of the following methods to specify the target firewalls in the
device group to which Panorama pushes the SD-WAN policy rule:
```
• Select Any (target to all devices) (the default) to push the rule to all devices. Alternatively,
```
select Devices or Tags to specify the devices to which Panorama pushes the SD-WAN
policy rule.
• On the Devices tab, select one or more filters to restrict the selections that appear in the
```
Name field; then select one or more devices to which Panorama pushes the rule, as in this
```
```
example:
```
```
• On the Tags tab, Add one or more Tags and select the tag(s) to specify that Panorama push
```
the rule to devices that are tagged with the selected tags, as in this example:
• If you specified Devices or Tags, you can select Target to all but these specified devices
and tags to have Panorama push the SD-WAN policy rule to all devices except for the
specified devices or tagged devices.
STEP 10 | Click OK.
SD-WAN Administration 153 ©2026 Palo Alto Networks, Inc.
SD-WAN Traffic Steering Using Policy Rules
STEP 11 | Commit and Commit and Push your configuration changes.
In an SD-WAN policy rule, you also specify the devices to which you want Panorama to push
the rule.
```
STEP 12 | (Best Practice) Create a catch-all SD-WAN policy rule to distribute unmatched sessions so
```
that you can control which links any unmatched sessions use and view unmatched sessions
in logging and reports in the SD-WAN plugin.
If you don’t create a catch-all rule to distribute unmatched sessions, the firewall
distributes them in round-robin order among all available links because there is
no traffic distribution profile for unmatched sessions. Round-robin distribution
of unmatched sessions can increase your costs unexpectedly and result in loss of
application visibility.
STEP 13 | After configuring your SD-WAN policy rules, Create a Security Policy Rule to allow traffic
```
(for example, bgp as an Application) from branches to the internet, from branches to hubs,
```
and from hubs to branches.
```
STEP 14 | (Optional) Configure QoS for critical applications.
```
If the SD-WAN applications need guaranteed bandwidth capacities or if you do not
want other applications taking bandwidth from critical business applications, create
QoS rules to control the bandwidth properly.
STEP 15 | To automatically set up BGP routing between VPN cluster members, in the SD-WAN plugin,
Configure BGP routing between branches and hubs to dynamically route traffic that will be
subject to the SD-WAN failover and load sharing.
Alternatively, if you want to manually configure BGP routing on each firewall or use a separate
```
Panorama template to configure BGP routing (for more control), leave the BGP information in
```
the plugin blank. Instead, configure BGP routing.
STEP 16 | Configure NAT for public-facing virtual SD-WAN interfaces.
Strata Cloud Manager
An SD-WAN policy rule specifies applications and services, and a traffic distribution profile to
determine how the firewall selects the preferred path for an incoming packet that doesn’t belong
to an existing session and that matches all other criteria, such as source and destination zones,
source and destination IP addresses, and source user. The SD-WAN policy rule also specifies a
path quality profile of thresholds for latency, jitter, and packet loss. When one of the thresholds is
exceeded, the firewall selects a new path for one or more applications, services, or both.
STEP 1 | Log in to Strata Cloud Manager.
STEP 2 | Create SD-WAN link management profiles.
STEP 3 | Select Configuration > NGFW and Prisma Access > Network Policies > SD-WAN Policy and
select the branch folder for which you want to create the SD-WAN policy rule.
SD-WAN Administration 154 ©2026 Palo Alto Networks, Inc.
SD-WAN Traffic Steering Using Policy Rules
STEP 4 | Add Rule and select whether to create a Pre Rule or Post Rules.
A pre-rule is a policy rule that always comes before any policy rules configured locally on the
firewall. A post-rule is a policy rule that always comes after any policy rules configured locally
on the firewall.
STEP 5 | Configure the policy rule Source match criteria.
If you’re adding a zone, Select one or more of the predefined zones you created when setting
up SD-WAN.
Additionally, you can configure any Addresses or Users as needed.
STEP 6 | Configure the policy rule Destination match criteria.
If you’re adding a zone, Select one or more of the predefined zones you created when setting
up SD-WAN.
Additionally, you can configure any Addresses or Users as needed.
STEP 7 | Configure the Application/Service to specify which applications or services the SD-WAN
policy rule applies to and to associate your link Management Profiles.
1. For Application, select Any or Select applications, application groups, or application
filters.
2. For Service, select Application Default, Any or Select any custom services you’ve
configured.
3. Select a predefined Path Quality Profile to specify the latency, jitter, and packet loss
parameters indicate path health.
4. (Optional) Select a SaaS Quality Profile you created when you created your SD-WAN
link Management Profiles to specifies how software-as-a-service applications are
```
monitored if your branch firewall has a Direct internet Access (DIA) link to a SaaS
```
application.
STEP 8 | Configure the corrective Action the firewall takes when a link health is degraded and failover
is required.
1. Select a Traffic Distribution Profile to specify how the firewall selects paths for session
load distribution and for path failover when the firewall detects a brownout, blackout, or
path deterioration for an application.
2. Select an Error Correction Profile to specify the corrective action the firewall takes
when certain data transmission errors occur over noisy communication lines to improve
data reliability without requiring retransmission or Packet Duplication to duplicate
application sessions from one tunnel to another.
STEP 9 | Save.
STEP 10 | Push Config to push your configuration changes.
SD-WAN Administration 155 ©2026 Palo Alto Networks, Inc.
SD-WAN Traffic Steering Using Policy Rules
Distribute Sessions Not Matching SD-WAN Policy Rules
Where Can I Use This? What Do I Need?
• NGFW Advanced SD-WAN for NGFW
The firewall attempts to match sessions that arrive at an SD-WAN virtual interface to an SD-
```
WAN policy rule; the firewall examines the SD-WAN policy rules in order from the top down, just
```
as it does for Security policy rules.
• If there is an SD-WAN rule match, the firewall executes the path monitoring and traffic
distribution for that SD-WAN policy rule.
• If there is no match to any SD-WAN policy rule in the list, the session matches an implied
SD-WAN policy rule at the end of the list that uses the round-robin method to distribute
unmatched sessions among all links in one SD-WAN interface, which is based on the route
lookup.
Furthermore, if there is no SD-WAN policy rule for a specific application, the firewall doesn’t track
that application’s performance in the SD-WAN-specific visibility tools such as logging and reports
in the SD-WAN plugin.
To illustrate the implied policy rule:
• Suppose the firewall has three SD-WAN policy rules: one rule specifies five voice applications,
one rule specifies six video conferencing applications, and one rule specifies ten SaaS
applications.
• A session, for example, a video application session, arrives at the firewall and doesn’t match
any of the SD-WAN policy rules. Because the session didn’t match a rule, the firewall has no
path quality profile or traffic distribution profile to apply to the session.
• Therefore, firewall matches the video application to the implied rule and distributes each video
session among all of the available SD-WAN link tags and their associated links on the firewall,
which could be two broadband links, an MPLS link, and an LTE link. Session 1 goes to one
member of the broadband interface, session 2 goes to another member of the broadband
interface, session 3 goes to MPLS, session 4 goes to LTE, session 5 goes to the first member of
the broadband interface, session 6 goes to the second member of the broadband interface, and
the round-robin distribution continues.
You may not want to let your unmatched sessions resort to matching the implied SD-WAN rule
because you have no control over that session distribution. Instead, we recommend you create a
catch-all SD-WAN policy rule and place it last in the list of SD-WAN policy rules. A catch-all SD-
WAN policy rule lets you:
• Control which links the unmatched sessions use.
```
• View all of the applications on the firewall (including unmatched application sessions) in logging
```
and reports in the SD-WAN plugin.
STEP 1 | Log in to the Panorama Web Interface.
SD-WAN Administration 156 ©2026 Palo Alto Networks, Inc.
SD-WAN Traffic Steering Using Policy Rules
```
STEP 2 | Define your custom SD-WAN application thresholds (using path quality profiles) that sets
```
very high latency, jitter, and packet loss thresholds that will never be exceeded. For example,
2,000ms latency, 1,000ms jitter, and 99% packet loss.
STEP 3 | Create a traffic distribution profile that specifies the SD-WAN link tags you want to use,
in the order in which you want the links associated with those link tags to be used by
unmatched sessions.
```
If you don’t want unmatched applications to use a specific path (physical interface)
```
at all, omit the tag that includes that link from the list of link tags in the traffic
distribution profile. For example, if you don’t want an unmatched application such as
movie streaming to use the expensive LTE link, omit the link tag for the LTE link from
the list of link tags in the traffic distribution profile.
STEP 4 | Add a catch-all SD-WAN policy rule and on the Application/Service tab, specify the Path
Quality Profile that you created.
STEP 5 | Select Any for the Applications and Service.
STEP 6 | On the Path Selection tab, select the Traffic Distribution Profile you created.
STEP 7 | Move the rule down to the last position in the list of SD-WAN policy rules.
STEP 8 | Commit and Commit and Push your configuration changes.
STEP 9 | Commit your changes.
SD-WAN Administration 157 ©2026 Palo Alto Networks, Inc.
SD-WAN Traffic Steering Using Policy Rules
SD-WAN Administration 158 ©2026 Palo Alto Networks, Inc.
Configure Direct Internet Access
Where Can I Use This? What Do I Need?
• NGFW Advanced SD-WAN for NGFW
The traditional WAN solution backhauls all the internet traffic to the data centers that results in
```
packet latency, drops, and jitter. Direct Internet Access (DIA) is one of the solutions where the
```
internet-bound traffic from the branch can be routed directly to the internet. This reduces the
```
latency of tunneling Internet-bound traffic to the data center (or central location).
```
Implementing DIA provides the following advantages:
• Provides DIA to the users at the remote locations
• Minimizes bandwidth consumption
• Reduces latency and jitter
• Cost efficient by offloading internet traffic from the private network
Although SD-WAN is designed to support both public DIA and private traffic flows efficiently
and apply security at each egress location, some use cases still require the redirection of all traffic
```
(both DIA and private) to the hub for central logging and security enforcement. This usecase is
```
generally implemented with one or more private WAN links and no public ISP circuits.
The important things to note with this use case include the following.
• SD-WAN’s DIA AnyPath must be implemented to redirect the branch’s DIA traffic through the
WAN link.
• You must permit the branch to redirect its DIA traffic to the hub by enabling the Allow DIA VPN
option in the Panorama SD-WAN plugin’s VPN Cluster hub configuration and this setting is
enabled/disabled per hub.
```
• As all traffic is redirected through the WAN link(s), SaaS quality profiles are not needed on the
```
```
branch office, and are only configured on the Hub SD-WAN firewall (if needed).
```
• Security policies are used at either the branch or hub locations to permit or deny branch traffic.
It is more efficient to block unwanted applications at the branch before it sends it over the
WAN link.
• QoS can also be used as an SD-WAN overlay to regulate the amount of traffic the branch is
permitted to redirect to the hub. Additional information on configuring QoS with SD-WAN can
be found in the Implementing QoS with SD-WAN technical paper.
159
Configure Direct Internet Access
Allow Direct Internet Access Traffic Failover to MPLS
Link
Where Can I Use This? What Do I Need?
• NGFW Advanced SD-WAN for NGFW
At an SD-WAN branch office, the firewall performs split tunneling so that any applications
```
having a public IP address take the Direct Internet Access (DIA) interface to the internet, and
```
applications having private IP addresses that belong to the hub take the VPN interface. The
firewall automatically fails over DIA applications to the MPLS private connection to the hub when
necessary, so that the traffic destined for the internet takes an alternative path through the hub to
reach the internet. To allow this to work, you must do the following:
STEP 1 | Create an MPLS link between your branch and hub. When you define your ISP connections
and link types, the link type must be MPLS for both the hub and branch.
```
STEP 2 | (PAN-OS 9.1.2 and later versions) If you want the private traffic to go through the VPN
```
tunnel, enable VPN Data Tunnel Support in the SD-WAN interface profile. If you disable
VPN Data Tunnel Support, the private data will go outside of the VPN tunnel.
STEP 3 | Configure an SD-WAN policy rule for specific applications, define your custom SD-WAN
```
application thresholds (using path quality profiles), and define path selection for SD-WAN
```
```
traffic (using traffic distribution profiles) that specifies the Top Down Priority method. The
```
Traffic Distribution profile must also specify an MPLS link as one of the failover options
```
(identified by a tag). Verify that the applications in the SD-WAN policy rule reference the
```
correct Path Quality and Traffic Distribution profiles, and that the Traffic Distribution profile
specifies Top Down Priority.
After the VPN Data Tunnel Support is enabled on both the hub and branch and the MPLS
link is operational, the firewall automatically uses the MPLS connection to fail over DIA traffic
when necessary.
STEP 4 | In the hub configuration, ensure the hub has a path to the internet and routing is properly set
up for the hub traffic to reach the internet.
The firewall uses the DIA virtual interface and the VPN virtual interface to ensure that the
```
public internet traffic is kept separate from your private traffic in the same path; that is, the
```
internet traffic and private traffic do not go through the same VPN tunnel. Full segmentation
with proper zoning is in full effect.
SD-WAN Administration 160 ©2026 Palo Alto Networks, Inc.
Configure Direct Internet Access
Backhaul Your Internet Traffic to SD-WAN Hub
Where Can I Use This? What Do I Need?
• NGFW Advanced SD-WAN for NGFW
```
When your SD-WAN direct internet access (DIA) links from an ISP experience a blackout or
```
brownout, you need those links to fail over to another link to ensure business continuity. DIA links
can fail over to an MPLS link, but you may not have an MPLS link. DIA links must be able to fail
```
over to another link that has a direct path or indirect path (through a hub) to the internet; the DIA
```
traffic can take any path available to get to the internet and isn’t restricted to DIA. DIA AnyPath
supports a DIA link failing over to a private VPN tunnel going to a hub firewall to then reach the
internet.
DIA AnyPath requires PAN-OS 10.0.3 or a later PAN-OS release and the compatible SD-WAN
Plugin release, which is shown in the SD-WAN table in the Panorama Plugins section of the
Compatibility Matrix.
```
There are several use cases for wanting an internet link to fail over to a VPN tunnel (DIA
```
```
AnyPath):
```
• You want to transition away from an expensive MPLS link to one or more public internet
connections, usually from different vendors.
• You have multiple hubs in a VPN cluster to allow a waterfall-type of failover from the primary
hub to a succession of backup hubs.
• In a split tunneling scenario, you want only a particular bandwidth-intensive application to
go directly to the internet through the branch’s DIA link instead of going back to the data
center hub through the VPN tunnel, thus saving WAN bandwidth costs. In the event of a DIA
brownout or blackout, this application traffic fails over to the data center hub to reach the
```
internet; and if necessary can subsequently fail over to a second hub to reach the internet.
```
• In a different split tunneling scenario, you want most of your internet traffic to go out the DIA
link rather than backhaul the traffic to the data center for internet breakout. However, you
```
want specific applications (that may need additional scanning or logging by another security
```
```
device) to go back to the data center. You create an SD-WAN policy rule to direct those
```
applications to a primary path to the hub, rather than the normal DIA link as determined by
the default route in the firewall’s route table. In the event of a brownout or blackout, those
applications fail over to take the branch’s DIA interface.
DIA AnyPath introduces the concept of a principal virtual interface, which can include both
```
DIA links and nested hub virtual interfaces and branch virtual interfaces (VPN tunnels) that each
```
```
include their own links. The principal virtual interface can have a maximum of nine DIA (Ethernet)
```
interfaces, hub virtual interfaces, and branch virtual interfaces. You assign a Link Tag to a hub
when you add the hub device to Panorama. Assuming you use the SD-WAN plugin, Auto VPN
assigns that Link Tag to the hub virtual interface, which allows you to specify the tag in a Traffic
Distribution profile to control the failover order among virtual interfaces.
A principal virtual interface is referred to as a DIA-VIF in CLI commands.
SD-WAN Administration 161 ©2026 Palo Alto Networks, Inc.
Configure Direct Internet Access
A principal virtual interface can have interface members that belong to different Security
zones. However, the best practice is to have all member interfaces in the principal virtual
interface belong to the same Security zone. Another best practice is to have at least one
member interface in the principal virtual interface be of the link type Ethernet, Cable
mode, ADSL, Fiber, LTE, or WiFi.
The following topology example shows Branch1 with two ISP connections and an MPLS link.
Branch1 also has a Hub1 virtual interface with three VPN tunnels connecting to Hub1, and a
Hub2 virtual interface of three VPN tunnels connecting to Hub2. Branch1 also has a branch2
virtual interface with three VPN tunnels connecting to Branch2 and a branch3 virtual interface
with three VPN tunnels connecting to Branch3. The goal of DIA AnyPath is to configure the order
in which DIA can fail over to VPN tunnels to reach the internet directly or indirectly and thus
maintain business continuity.
When you configure a principal virtual interface, it automatically becomes the default route so
that internet traffic is routed properly to any of the members of the principal virtual interface
```
(both DIA links and VPN tunnels). The path selection is based on SD-WAN Path Quality profiles
```
and Traffic Distribution profiles, which you would set to use the Top Down Priority distribution
method to control the failover order. In the example topology, a Traffic Distribution profile can list
the tag for the principal virtual interface first, then the tag for the Hub1 virtual interface, and then
the tag for the Hub2 virtual interface.
Zooming in to a deeper level of failover priority, a hub virtual interface has multiple tunnel
members, so you need a way to prioritize the failover order of the members, such as prioritizing
that a broadband VPN tunnel be used before an LTE VPN tunnel. You specify the priority
SD-WAN Administration 162 ©2026 Palo Alto Networks, Inc.
Configure Direct Internet Access
using the VPN Failover Metric in the SD-WAN Interface Profile that you apply to the Ethernet
interface. The lower the metric value, the higher the priority for the tunnel to be selected upon
failover. In the topology example, in the Hub1 virtual interface, a lower VPN Failover Metric for
t11 than for t12 causes internet traffic to fail over to t11 before t12. If multiple tunnels in a virtual
interface have the same metric, SD-WAN sends new session traffic to the tunnels in round-robin
fashion.
STEP 1 | Log in to the Panorama Web Interface.
SD-WAN Administration 163 ©2026 Palo Alto Networks, Inc.
Configure Direct Internet Access
STEP 2 | Specify the failover priority for a VPN tunnel bundled in a hub virtual interface or branch
virtual interface.
1. Select or define your ISP connections and link types.
Best Practice is to configure at least one interface with the link type of Ethernet,
Cable modem, ADSL, Fiber, LTE, or WiFi.
2. You must enable VPN Data Tunnel Support.
3. Specify the VPN Failover Metric for a VPN tunnel; range is 1 to 65,535; default is 10.
```
The lower the metric value, the higher the priority of VPN tunnel (link) where you apply
```
this profile.
```
For example, set the metric to a low value and apply the profile to a broadband interface;
```
then create a different profile that sets a high metric to apply to an expensive LTE
interface to ensure it is used only after broadband has failed over.
If you have only one link at the hub, that link supports all of the virtual interfaces
and DIA traffic. If you want to use the link types in a specific order, you must
apply a Traffic Distribution profile to the hub that specifies Top Down Priority,
and then order the Link Tags to specify the preferred order. If you apply a Traffic
Distribution profile that instead specifies Best Available Path, the firewall
will use the link, regardless of cost, to choose the best performing path to the
branch. In summary, Link Tags in a Traffic Distribution profile. the Link Tag
```
applied to a hub virtual interface (Step 6 in this task), and a VPN Failover Metric
```
work only when the Traffic Distribution profile specifies Top Down Priority.
4. Click OK.
STEP 3 | Configure a physical Ethernet interface for SD-WAN and on the SD-WAN tab, apply the SD-
WAN Interface Profile you created in the prior step.
Best Practice is to have all interfaces in the principal virtual interface belong to the
same Security zone.
SD-WAN Administration 164 ©2026 Palo Alto Networks, Inc.
Configure Direct Internet Access
STEP 4 | Repeat Steps 2 and 3 to configure additional SD-WAN Interface Profiles with a different
VPN failover metric and apply the profiles to different Ethernet interfaces to determine the
order in which failover occurs to the links.
STEP 5 | Define a link tag for a hub virtual interface.
STEP 6 | Add the Link Tag to a hub that you want to participate in DIA AnyPath.
1. In Panorama > SD-WAN > Devices, add an SD-WAN device to add a hub to be managed
by Panorama.
2. Select the hub.
3. Select the Link Tag that you created in the prior step, which Auto VPN applies to the
whole hub virtual interface, not an individual link. Thus, you can reference this Link Tag
in the Traffic Distribution Profile to indicate the hub virtual interface for the failover
order for DIA AnyPath. On the branch device, Auto VPN uses this tag to populate the
Link Tag field on the SD-WAN virtual interface that terminates on the hub device.
4. Click OK.
STEP 7 | Repeat Steps 5 and 6 to create a Link Tag for each hub virtual interface and add the tag to
each hub that will participate in DIA AnyPath. Do the same for any branch virtual interface.
STEP 8 | Create a Traffic Distribution Profile to implement DIA AnyPath.
1. Define path selection for SD-WAN traffic using traffic distribution profile.
2. Select Top Down Priority.
3. Add the Link Tags so they appear in the order that you want their associated links used
for failover.
For example, if your use case is for certain applications to use DIA first, list the DIA tag
first, then a hub virtual interface tag, then a second hub virtual interface tag. If your use
case is for certain applications to first go to the hub and then the internet, list a hub
virtual interface first, then perhaps a second hub virtual interface, and list a DIA tag last.
If you have full mesh with no hub, use the DIA tag and branch virtual interface tags in the
order you want.
SD-WAN Administration 165 ©2026 Palo Alto Networks, Inc.
Configure Direct Internet Access
STEP 9 | Create identically named SaaS Quality Profiles for both the hub and branch firewalls.
Two identically named SaaS Quality profiles must be configured on the hub and branch
firewalls to successfully leverage the hub firewall as an alternative failover.
The easiest way to configure failover to a hub firewall with the same SaaS application
destination is to create a single SaaS Quality profile in the Shared device group. Alternatively,
you can create two SaaS Quality profiles with identical names in different device groups and
push them to your hub and branch firewalls.
To failover to a hub firewall with different SaaS application destinations, create two SaaS
Quality profiles with identical names each pointing to a different SaaS application destination
in different device groups and push them to your hub and branch firewalls.
You must also create an SD-WAN policy rule that references this SaaS Quality profile
in order to allow the hub to advertise link quality statistics for the SaaS Quality profile
to the branch. Doing so will provide end-to-end SaaS monitoring through the hub.
Without this SD-WAN policy rule, you would have only the link measurements from
the branch to the hub, but not from the hub to the SaaS application.
STEP 10 | Allow the hubs to participate in DIA AnyPath.
1. Create a VPN cluster and select a hub.
2. Select Allow DIA VPN for the hub. A maximum of four hubs (any combination of PAN-
```
OS hubs participating in DIA AnyPath and Prisma Access hubs (SD-WAN plugin 2.2 and
```
```
later versions)) are supported. If they are HA hubs, a total of eight hubs are supported. If
```
you Allow DIA VPN for one HA peer in a pair, you must also enable it for the other HA
peer.
SD-WAN Administration 166 ©2026 Palo Alto Networks, Inc.
Configure Direct Internet Access
```
STEP 11 | Create an SD-WAN policy rule for specific application(s) to use DIA AnyPath.
```
1. Configure an SD-WAN policy rule.
2. On the Application/Service tab, specify the applications and services for which you want
to implement DIA AnyPath.
3. Associate the SaaS Quality Profile you created in the previous step.
If you are configuring a SaaS Quality profile with different SaaS application destination,
you must associate the SaaS Quality profile with the SD-WAN policy rule in each branch
and hub device group.
4. On the Path Selection tab, select the Traffic Distribution Profile you created for the
applications.
STEP 12 | Route new sessions that don’t match any SD-WAN policy rule and sessions that arrive during
a Panorama or firewall configuration change.
1. Create an appropriate Path Quality profile and Traffic Distribution profile to handle such
sessions.
2. Configure an SD-WAN policy rule that is a catch-all rule for these sessions.
3. Place the rule last in the list.
STEP 13 | Commit and Push to Devices.
STEP 14 | Create a Security Policy Rule to allow DIA traffic to the Destination Zones named zone-
internet and zone-to-hub and specify the Applications subject to the rule. Commit and
push to the branches.
STEP 15 | Use the following CLI commands to monitor DIA information:
1. show sdwan connection <dia-vif-name>
2. show sdwan path-monitor stats dia-vif all
3. show sdwan path-monitor dia-anypath
4. show sdwan path-monitor dia-anypath packet-buffer all
5. show sdwan path-monitor stats conn-idx <IDX>
SD-WAN Administration 167 ©2026 Palo Alto Networks, Inc.
Configure Direct Internet Access
SD-WAN Administration 168 ©2026 Palo Alto Networks, Inc.
Create a Static Route for SD-WAN
Where Can I Use This? What Do I Need?
• NGFW Advanced SD-WAN for NGFW
```
In addition to (or as an alternative to) BGP routing, you can create static routes to route your SD-
```
WAN traffic.
You can configure static routes either using Panorama™ or directly on the firewall hub or branch.
If you are going to use Panorama, you should be familiar with the process to configure a template
or template stack variable. You will create a variable to use as the destination in your static route,
```
as shown in the following procedure. (You can also create a variable for the next hop.) You will
```
```
push a static route (that goes to the hub) to the branch. You will push a static route (that goes to
```
```
the branch) to the hub.
```
STEP 1 | Log in to the Panorama Web Interface.
STEP 2 | Configure a Template or Template Stack Variable and enter the variable Name
in the following format: $peerhostname_clustername.customname. For example,
```
$branchsanjose_clusterca.10 or $DIA_cluster2.location3. After the dollar sign ($), the
```
elements in the variable are:
• peerhostname—Hostname of the destination hub or branch to which the static route goes.
For a static route to the internet, the peerhostname must be DIA. An alternative to the
peer’s hostname is to use the peer’s serial number. If the peer is part of an HA pair, you can
use the hostname or serial number of either one of the two HA firewalls.
• clustername—Name of the VPN cluster to which the destination hub or branch belongs.
```
• customname—Text string of your choice; you cannot use a period (.) in the customname.
```
You can have more than one static route going to the same peer, which means the variables
```
will have the same peerhostname and clustername; you differentiate the variables by using a
```
different customname.
STEP 3 | Select the variable Type to be IP Netmask and enter the destination IP address with a slash
and netmask length, such as 192.168.2.1/24.
```
(SD-WAN plugin 3.2.0 and later versions) For IPv6, enter the IPv6 address with a slash and
```
prefix length, such as 2001:DB8::/32.
STEP 4 | Click OK to save the variable.
STEP 5 | Select Network > Virtual Routers and select a virtual router.
STEP 6 | Select Static Routes.
```
STEP 7 | Select IPv4 or IPv6 (SD-WAN plugin 3.2.0 and later versions) and Add a Name for the static
```
route.
169
Create a Static Route for SD-WAN
STEP 8 | For Destination, select the variable you created.
STEP 9 | For Interface, select from the dropdown list, which includes only interfaces from the
```
template; for example, Ethernet1/1, Tunnel.x, or sdwan.xx.
```
```
STEP 10 | For Next Hop, select IP Address or IPv6 Address (SD-WAN plugin 3.2.0 and later versions)
```
```
and enter the IP address or variable of the next hop for the static route (the hub or branch to
```
```
which the static route goes).
```
STEP 11 | Click OK.
STEP 12 | Commit and Commit and Push your changes.
Auto VPN configuration replaces the sdwan keyword in the Interface field of the static route
with the egress virtual SD-WAN interface that it determines based on the Destination variable.
Thus, the static route in the routing table indicates that traffic going to the peer host in the
identified VPN cluster will egress the virtual SD-WAN interface to reach the specified next
hop.
STEP 13 | Configure a static route for the return traffic.
SD-WAN Administration 170 ©2026 Palo Alto Networks, Inc.
Configure Advanced Routing for
SD-WAN
Where Can I Use This? What Do I Need?
• NGFW
• SD-WAN plugin version 3.1.0 or above
Advanced SD-WAN for NGFW
Advanced Routing Engine allows the firewall to scale and provide stable, high-performing, and
highly available routing functions to large data centers, ISPs, enterprises, and cloud users. The
Advanced Routing Engine relies on industry-standard configuration methodology, which facilitates
```
the administrator tasks. It allows the creation of profiles that are used for different functions (such
```
```
as, filtering, redistribution, and metric changes), all of which can be used across logical routers.
```
These profiles provide finer granularity to filter routes for each dynamic routing protocol and
improve route redistribution across multiple protocols.
Although conceptually equivalent, the advanced routing engine uses logical routers rather than
virtual routers to instantiate routing domains.
```
Unlike virtual routers, logical routers are not created by default; you must create one
```
before configuring the routing functions.
You can use an advanced routing engine or a legacy engine based on your network requirements:
• When you enable Advanced Routing, logical routers are created and advanced routing engine
is used for routing.
• When you disable Advanced Routing, virtual routers are created and legacy engine is used for
routing.
```
The advanced route engine supports multiple logical routers (known as a virtual router on the
```
```
legacy route engine). The advanced route engine has more convenient menu options and there
```
```
are more BGP settings that you can easily configure in a profile (authentication, timers, address
```
```
family, or redistribution profile) that applies to a BGP peer group or peer, for example.
```
The Advanced Routing Engine supports static routes, MP-BGP, OSPFv2, OSPFv3, RIPv2, Protocol
```
Independent Multicast Sparse Mode (PIM-SM), PIM Source-Specific Multicast (SSM), BFD,
```
redistribution, route filtering into the RIB, access lists, prefix lists, and route maps.
You’ll need the following to configure advanced routing engine on SD-WAN:
Platform Firewalls running PAN-OS
Release
SD-WAN Plugin
PanoramaTM 11.0 or later 3.1.0 or later
171
Configure Advanced Routing for SD-WAN
SD-WAN plugin creates logical router or virtual router based on the value of the advanced routing
```
option. When Advanced Routing is enabled, a logical router is created; Otherwise, virtual router is
```
created.
When you enable advanced routing in template stack and perform a Panorama commit and push
to the firewall, SD-WAN plugin runs the migration script to create the SD-WAN related objects
```
(static, interfaces, redistribution profile, BGP) in Logical Router. The migration script creates the
```
logical router name same as the virtual router name for the same template. Hence the hubs and
branches have always the same router name.
After migration, Panorama does not allow you to delete the migrated virtual routers.
The SD-WAN plugin 3.1.0 and later versions can concurrently manage firewalls using the
Advanced Routing Engine and firewalls using the legacy routing engine. The benefit is that you
can migrate select managed firewalls to the new Advanced Routing Engine while still maintaining
your current legacy routing engine configuration on others.
```
(SD-WAN plugin 3.1.0 and later versions) While the SD-WAN plugin manages a firewall regardless
```
of the routing engine, only one routing engine configuration can be in effect at a time on a
managed firewall. You can use the Advanced Routing option to enable or disable the advanced
```
routing engine. Each time you change the engine that the firewall uses (you enable or disable
```
```
Advanced Routing to access the advanced engine or legacy engine, respectively), you must
```
commit the configuration and reboot the firewall for the changes to take effect.
Before you switch to the advanced route engine, make a backup of your current
configuration. Similarly, if you configure Panorama with a template stack that enables or
disables Advanced Routing, after you commit and push the template stack to devices, you
must reboot the devices in the template stack for the change to take effect.
When configuring Panorama, create device groups and template stack for devices that
```
all use the same Advanced Routing setting (all enabled or all disabled). Panorama won’t
```
push configurations with Advanced Routing enabled to smaller firewalls that don’t support
Advanced Routing. For those firewalls, Panorama will push a legacy configuration if one is
present.
Ensure that you downgrade to an appropriate SD-WAN plugin and PAN-OS version, and
disable Advanced Routing if you plan to use a virtual router. Use a separate template where the
```
Advanced Routing is disabled (in this case, virtual routers are created) when downgrading the SD-
```
WAN plugin.
If you have configured Advanced Routing and want to switch to a virtual router, then disable
Advanced Routing to return to the previously saved virtual router configuration. Commit and push
any changes made to the firewall after disabling advanced routing before attempting a downgrade
procedure, such as downgrading PAN-OS and SD-WAN plugin versions.
If you enable Advanced Routing, SD-WAN interfaces must be configured in the same logical
```
router; they cannot be split among logical routers.
```
STEP 1 | Log in to the Panorama Web Interface.
STEP 2 | Upgrade Panorama to 11.1 or later versions and install the SD-WAN plugin 3.1.0 or later
versions.
SD-WAN Administration 172 ©2026 Palo Alto Networks, Inc.
Configure Advanced Routing for SD-WAN
STEP 3 | Add your hub and branch firewalls as managed devices to the PanoramaTM management
server.
STEP 4 | Make a backup of your current configuration before you enable Advanced Routing.
STEP 5 | In the Device section, select appropriate template stack from the Template context drop-
down.
SD-WAN Administration 173 ©2026 Palo Alto Networks, Inc.
Configure Advanced Routing for SD-WAN
STEP 6 | Enable advanced routing engine.
1. Select Device > Setup > Management and edit the General Settings.
2. Enable Advanced Routing. SD-WAN plugin will create logical router or virtual router
based on the value of the advanced routing option. When Advanced Routing is enabled,
a logical router is created. Otherwise, virtual router is created.
3. Click OK.
4. A warning message about the migration appears; click Yes to proceed.
On clicking Yes, a built-in migration script will migrate your existing configuration to the
advanced routing engine. If you select Skip, an empty configuration is created for the
advanced routing engine.
The Migration Configuration displays the color codes that indicate the migration status.
SD-WAN Administration 174 ©2026 Palo Alto Networks, Inc.
Configure Advanced Routing for SD-WAN
In the Virtual Router, review the STATUS of templates in template stacks. The STATUS
should be green for successful migration. Otherwise, take necessary action for any
templates that did not pass the migration.
The successful migration automatically converts each virtual router to a corresponding
logical router. It is mandatory to commit the configuration and restart the firewall for the
changes to take effect.
5. Commit.
6. Select Device > Setup > Operations and Reboot Device.
STEP 7 | Select Commit > Commit to Panorama and commit your changes.
SD-WAN Administration 175 ©2026 Palo Alto Networks, Inc.
Configure Advanced Routing for SD-WAN
STEP 8 | Commit and push your configuration changes to your managed firewalls. Push to Devices to
view the logical routers added in the selected SD-WAN firewalls.
1. Select Commit > Push to Devices and Edit Selections.
2. Select Templates and choose the templates stack and template from the list.
3. Enable Force Template Values to overwrite local configuration with the updated template
values. Before you use this option, check for overridden values on the firewalls to ensure
your commit does not result in any unexpected network outages or issues caused by
replacing those overridden values.
4. Click OK and Push to devices.
STEP 9 | Log back into the firewall.
STEP 10 | Select Network.
Notice the menu items, which are more industry-standard and more detailed than the single
```
item (Virtual Routers) on the legacy menu. Routing includes Logical Routers and Routing
```
Profiles, which include BGP, BFD, OSPF, OSPFv3, RIPv2, Filters, and Multicast.
STEP 11 | You must enable Advanced Routing for each template stack individually when you have
more than one template stack in your configuration. Repeat Steps 5 through 10 for other
template stacks on firewalls that you intend to update for advanced routing.
According to our design requirement, the logical router name must be the same as
the virtual router name for the same template when using the advanced routing
engine. This means that hubs and branches have always the same router name. When
manually creating logical routers rather than using a migration script, you must make
sure the logical router name and virtual router name are the same.
STEP 12 | Select virtual or logical router in your SD-WAN deployment.
```
Select Panorama > SD-WAN > Devices, to add an SD-WAN device (SD-WAN hub or branch
```
```
firewall) to be managed by the Panorama management server.
```
In addition to existing configuration options for adding an SD-WAN device, you can now select
```
a logical router (for advanced routing engine) or virtual router (for legacy engine) for a Router
```
Name. It is important that the logical router name and the virtual router name are same for the
same template when using the advanced routing engine.
```
Select the Router Name (logical or virtual router) to use for routing between the SD-WAN hub
```
and branches:
• If the virtual router and logical router names are the same, then the Router Name displays
one name.
• If virtual router and logical router names are different, then the Router Name displays both
```
virtual and logical router name. You can select either virtual router (for legacy engine) or
```
```
logical router (for advanced routing engine) based on your requirement.
```
SD-WAN Administration 176 ©2026 Palo Alto Networks, Inc.
Enable Segmentation with
Multiple Virtual Routers for
Overlapping Subnets
Where Can I Use This? What Do I Need?
• NGFW Advanced SD-WAN for NGFW
The multiple virtual router support on SD-WAN enables you to segment your network into
multiple virtual routing domains on a single Palo Alto Networks Next-Generation Firewall. This
capability allows you to create isolated network environments, each with its own routing table,
interfaces, and policy rules. With multiple virtual router support, you can efficiently manage
complex network architectures, improve security through network isolation, and simplify
your overall network design. This feature is useful for service providers, large enterprises, and
organizations with strict compliance requirements that need to maintain separation between
different departments, customers, or applications. With multiple virtual router support, you can
optimize your network resources, reduce hardware costs, and gain greater flexibility in managing
diverse network segments all within a single physical appliance. With this feature, you can expand
your network, enhance security, and easily manage your network while meeting the demands of
today's complex networking environments.
Multiple virtual routers offer several key benefits for your network. By implementing multiple
virtual routers, you can:
• segment your network into isolated routing domains on a single physical firewall. This allows
you to create separate network environments for different departments, customers, or
applications.
• improve security through network isolation. You can prevent unauthorized access between
segments by controlling the traffic between virtual routers.
• manage complex network architectures with flexibility. You can have separate routing tables,
interfaces, and policy rules for each virtual router.
• optimize network resources and reduce hardware costs by consolidating multiple logical
networks onto a single physical appliance.
• expand your network by adding new network segments without requiring additional physical
firewalls.
• enable multitenant environments where each tenant can have their own isolated network
space for service providers and large enterprises.
Overall, virtual routers give you more granular control over your network design and traffic flow
while improving security, efficiency, and manageability.
```
(SD-WAN plugin 3.0.7 and later versions) (SD-WAN plugin 3.2.1 and later versions) You can
```
configure multiple virtual routers on SD-WAN hub firewalls.
177
Enable Segmentation with Multiple Virtual Routers for Overlapping Subnets
Beginning with SD-WAN plugin 3.3.1 release, you can also configure multiple virtual routers on
SD-WAN branch firewalls.
SD-WAN Administration 178 ©2026 Palo Alto Networks, Inc.
Enable Segmentation with Multiple Virtual Routers for Overlapping Subnets
Configure Multiple Virtual Routers on SD-WAN Hub
Where Can I Use This? What Do I Need?
```
• NGFW (Managed by PAN-OS 10.2.8 and
```
later 10.2 releases and SD-WAN plugin
```
3.0.7 and later 3.0 releases)
```
```
• NGFW (Managed by PAN-OS 11.1.3 and
```
later releases, and SD-WAN plugin 3.2.1
```
and later releases)
```
Advanced SD-WAN for NGFW
We have introduced support for multiple virtual routers on the SD-WAN hub that enable you to
have overlapping IP subnet addresses on branch devices connecting to the same SD-WAN hub.
With this feature you can have multiple logical routing domains with overlapping subnets. When
you enable this feature, the SD-WAN hub supports overlapping subnets only if the overlapping
subnets are in different virtual routers.
By default, multiple virtual routers on an SD-WAN hub is disabled.
The following figure illustrates an SD-WAN hub with two virtual routers. By enabling multiple
virtual routers support on the SD-WAN hub, the four branches connecting to the same SD-WAN
hub can have overlapping IP subnets or belong to different entities and function independently
because their traffic goes to different virtual routers.
Multiple virtual router feature is supported on both SD-WAN hub firewall as well as Prisma
Access hub. You can onboard Prisma Access as a hub from the branch, when the branch is
connected to an on-premises hub where the multiple virtual router feature is enabled.
```
Configure multiple virtual routers while adding an SD-WAN hub firewall (Panorama > SD-WAN >
```
```
Devices).
```
Importing multiple virtual routers related configuration using a CSV file while importing the SD-
WAN device is not supported.
```
(PAN-OS 11.1.3 and later releases, and SD-WAN plugin 3.2.1 and later releases) We support
```
advanced routing when the multiple virtual routers on SD-WAN hub is enabled.
STEP 1 | Log in to the Panorama Web Interface.
SD-WAN Administration 179 ©2026 Palo Alto Networks, Inc.
Enable Segmentation with Multiple Virtual Routers for Overlapping Subnets
STEP 2 | Select Panorama > SD-WAN > Devices and Add a new SD-WAN firewall.
While creating a hub template, add all the virtual routers participating in the SD-WAN hub
where the multiple virtual router will be enabled. You must do this before adding the SD-WAN
device using the SD-WAN plugin. While creating the hub template, ensure that the virtual
router name on the branch matches with one of the virtual routers on the hub.
STEP 3 | To configure multiple virtual routers on the SD-WAN hub:
• Select the Type of SD-WAN device as Hub.
• Select Enable Multi-VR Support.
The virtual router selected for the Virtual Router Name is used as the hub direct internet
```
access (DIA) virtual router and considered as the default virtual router. The configuration
```
specified under the BGP tab must be specific to the DIA virtual router.
• We don't support FEC and packet duplication when multiple virtual router feature
is enabled on the SD-WAN hub.
• The multiple virtual router feature on SD-WAN hub is supported only in a hub-
```
spoke topology (and not supported in a full mesh topology).
```
• To process internet traffic on the SD-WAN hub, SD-WAN policy must ensure that
the MPLS tag is selected only when the MPLS link has internet access and NAT.
```
• PAN-OS does not support forwarding traffic in clear text (when the VPN Data
```
```
Tunnel Support is disabled on the SD-WAN Interface Profile) outside of the SD-
```
WAN VPN tunnel when multiple virtual routers support on the SD-WAN hub
feature is enabled.
The number of virtual routers supported on the Palo Alto Networks firewalls are as follows:
Palo Alto Networks Firewall Maximum Virtual Routers
Supported
Maximum SD-WAN Hub
Virtual Routers Supported
PA-3400 11 10
PA-5220 and PA-5410 20 20
PA-5250 and PA-5430 125 50
PA-5420 50 20
PA-5260, PA-5280, PA-5400,
PA-5440, PA-5445, and
PA-7000.
225 50
SD-WAN Administration 180 ©2026 Palo Alto Networks, Inc.
Enable Segmentation with Multiple Virtual Routers for Overlapping Subnets
```
STEP 4 | (Optional) Configure virtual routers.
```
1. Select the Virtual Routers tab to configure multiple virtual routers for the SD-WAN hub.
2. BGP routing uses IPv4 by default and hence Enable IPv4 BGP Support is enabled and
you can't change this configuration.
3. Enter the name of the Virtual Router.
4. Select an already created Zone in the hub template (Network > Zones) that is
appropriate for the virtual router that you are configuring.
If you configure the same zone for two or more virtual routers in the Multi-
VR Configuration, ensure that the virtual routers are not configured with the
overlapping subnets.
5. (Optional) Enter the virtual Router ID, which must be unique among all routers.
6. Specify a static IPv4 Loopback Address for BGP peering. Auto VPN configuration
automatically creates a loopback interface with the same IPv4 address that you specify.
If you specify an existing loopback address, the commit will fail, so you should specify an
IPv4 address that is not already a loopback address.
7. Enter the AS Number. The autonomous system number specifies a commonly defined
routing policy to the internet. The AS number must be unique for every hub and branch
location.
8. Disable the Remove Private AS option (the default is enabled) if you have endpoints
that need to exchange routes with a hub or branch firewall in an SD-WAN BGP topology
```
and therefore you don’t want to remove private AS numbers (64512 to 65534) from
```
the AS_PATH attribute in BGP Updates. In this case, you want to allow the private AS
numbers to leave the SD-WAN private AS in BGP Updates.
The Remove Private AS setting applies to all BGP peer groups on the branch or
hub firewall. If you need this setting to differ among BGP peer groups or peers,
you must configure the setting outside of the SD-WAN plugin.
If you change the Remove Private AS setting, commit to all SD-WAN cluster
nodes, and subsequently downgrade to an SD-WAN plugin version earlier than
2.0.2, then all configuration related to Remove Private AS must be done outside
of the SD-WAN plugin or directly on the firewalls.
9. Enter Prefix(es) to Redistribute. On a hub device, you must enter at least one prefix to
redistribute.
10. Click OK
11. Click Add at the bottom of the Virtual Routers tab to add more virtual routers.
SD-WAN Administration 181 ©2026 Palo Alto Networks, Inc.
Enable Segmentation with Multiple Virtual Routers for Overlapping Subnets
Configure Multiple Virtual Routers on SD-WAN Branch
Where Can I Use This? What Do I Need?
```
• NGFW (Managed by PAN-OS 11.2.3 and
```
later releases, and SD-WAN plugin 3.3.1
```
and later releases)
```
Advanced SD-WAN for NGFW
We have introduced support for multiple virtual routers on the SD-WAN branches to have
overlapping IP subnet addresses on both hub and branch devices. With this feature you can have
multiple logical routing domains with overlapping subnets.
Ensure the following before you enable the multiple virtual routers on the SD-WAN branch
```
devices:
```
• The hub device to which the branches are connected must have the multiple virtual router
support.
• The hub devices to which the branches are connected must have all the virtual routers that are
present in the branch devices.
• In a VPN cluster, for the branches to have the multiple virtual router support, you must enable
the multiple virtual router support on all the hubs first.
The following figure illustrates three SD-WAN branches with each configured with one or more
virtual routers. By enabling multiple virtual routers support on the SD-WAN branches, the three
branches connecting to the same SD-WAN hub can have overlapping IP subnets or belong to
different entities and function independently because their traffic goes to different virtual routers.
SD-WAN Administration 182 ©2026 Palo Alto Networks, Inc.
Enable Segmentation with Multiple Virtual Routers for Overlapping Subnets
STEP 1 | Log in to the Panorama Web Interface.
STEP 2 | Select Panorama > SD-WAN > Devices and Add a new SD-WAN firewall.
SD-WAN Administration 183 ©2026 Palo Alto Networks, Inc.
Enable Segmentation with Multiple Virtual Routers for Overlapping Subnets
STEP 3 | To configure multiple virtual routers on the SD-WAN branch device:
• Select the Type of SD-WAN device as Branch.
• Select Enable Multi-VR Support.
The virtual router selected for the Virtual Router Name is used as the branch direct internet
```
access (DIA) virtual router and considered as the default virtual router. The configuration
```
specified under the BGP tab must be specific to the DIA virtual router.
• We don't support FEC and packet duplication when multiple virtual router feature
is enabled on the SD-WAN branch.
• The multiple virtual router feature on SD-WAN branch is supported only in a hub-
```
spoke topology (and not supported in a full mesh topology).
```
• To process internet traffic on the SD-WAN branch, SD-WAN policy must ensure
that the MPLS tag is selected only when the MPLS link has internet access and
NAT.
```
• PAN-OS does not support forwarding traffic in cleartext (when the VPN Data
```
```
Tunnel Support is disabled on the SD-WAN Interface Profile) outside of the SD-
```
WAN VPN tunnel when multiple virtual routers support on the SD-WAN branch
feature is enabled.
A maximum of 20 virtual routers are supported on the SD-WAN branch device. However, the
number of virtual routers supported on the SD-WAN branch varies by the platform:
Palo Alto Networks Firewall Maximum Virtual Routers
Supported
Maximum SD-WAN Branch
Virtual Routers Supported
PA-460 5 5
PA-450 5 5
PA-445 3 3
PA-440 3 3
PA-415 3 3
PA-1420 10 10
PA-1410 10 10
PA-850 5 5
PA-820 5 5
PA-3200 10 10
SD-WAN Administration 184 ©2026 Palo Alto Networks, Inc.
Enable Segmentation with Multiple Virtual Routers for Overlapping Subnets
```
STEP 4 | (Optional) Configure virtual routers.
```
1. Select the Virtual Routers tab to configure multiple virtual routers for the SD-WAN
branch.
2. BGP routing uses IPv4 by default and hence Enable IPv4 BGP Support is enabled and
you can't change this configuration.
3. Enter the name of the Virtual Router.
4. Select a unique zone for the virtual router.
```
In a VPN cluster with multiple virtual router configuration, each device (branch or hub)
```
with virtual router that is participating in the multiple virtual router configuration must
have a unique zone.
5. (Optional) Enter the virtual Router ID, which must be unique among all routers.
6. Specify a static IPv4 Loopback Address for BGP peering. Auto VPN configuration
automatically creates a loopback interface with the same IPv4 address that you specify.
If you specify an existing loopback address, the commit will fail, so you should specify an
IPv4 address that is not already a loopback address.
7. Enter the AS Number. The autonomous system number specifies a commonly defined
routing policy to the internet. The AS number must be unique for every hub and branch
location.
8. Disable the Remove Private AS option (the default is enabled) if you have endpoints
that need to exchange routes with a hub or branch firewall in an SD-WAN BGP topology
```
and therefore you don’t want to remove private AS numbers (64512 to 65534) from
```
the AS_PATH attribute in BGP Updates. In this case, you want to allow the private AS
numbers to leave the SD-WAN private AS in BGP Updates.
The Remove Private AS setting applies to all BGP peer groups on the branch or
hub firewall. If you need this setting to differ among BGP peer groups or peers,
you must configure the setting outside of the SD-WAN plugin.
If you change the Remove Private AS setting, commit to all SD-WAN cluster
nodes, and subsequently downgrade to an SD-WAN plugin version earlier than
2.0.2, then all configuration related to Remove Private AS must be done outside
of the SD-WAN plugin or directly on the firewalls.
9. Enter Prefix(es) to Redistribute. On a hub device, you must enter at least one prefix to
redistribute.
10. Click OK
11. Click Add at the bottom of the Virtual Routers tab to add more virtual routers.
SD-WAN Administration 185 ©2026 Palo Alto Networks, Inc.
Enable Segmentation with Multiple Virtual Routers for Overlapping Subnets
SD-WAN Administration 186 ©2026 Palo Alto Networks, Inc.
Monitoring and Reporting
Where Can I Use This? What Do I Need?
• NGFW Advanced SD-WAN for NGFW
Monitor and generate reports of the application and link health status in your VPN clusters to
identify and resolve issues. In order for the Panorama® management server to display SD-WAN
application and link health information, you must enable the SD-WAN firewalls to push device
monitoring data to Panorama and configure log forwarding to Panorama when you add your SD-
WAN firewalls as managed devices. If you have not configured your SD-WAN firewalls to forward
logs to Panorama, the SD-WAN Monitoring displays no application or link health information.
In order for Panorama to gather SD-WAN monitoring data, you must push the SD-WAN
configuration from Panorama to your SD-WAN firewalls. If no SD-WAN monitoring data
is displayed, verify that you successfully pushed the SD-WAN configuration.
187
Monitoring and Reporting
Monitor SD-WAN Tasks
Monitor commits, pushes, and other SD-WAN tasks executed from the Panorama® management
server to gain insight and detailed information regarding the specific task.
If a task succeeds with warnings or fails, you can view detailed warnings and description to better
understand how to resolve the misconfiguration. Additionally, you can view the last push state
details to review detailed information as to what caused the task warnings or errors.
STEP 1 | Log in to the Panorama web interface.
STEP 2 | After editing the SD-WAN configuration, Commit your changes to view the job status.
The job status window displays the operation performed, the result, and any details and
warnings related to the job status.
STEP 3 | View the last push details for jobs that succeed with warnings or failed.
1. Click Tasks (
```
) at the bottom of the web interface to open the Task Manager.
```
2. Click the job Type for the SD-WAN task.
3. Click the job Status to view the last push state details for the task.
4. Review the last push state details to identify and resolve the configuration issues.
SD-WAN Administration 188 ©2026 Palo Alto Networks, Inc.
Monitoring and Reporting
Monitor SD-WAN Application and Link Performance
Where Can I Use This? What Do I Need?
• NGFW Advanced SD-WAN for NGFW
Monitor the application and link performance in your VPN clusters to troubleshoot issues by
viewing summary information across all VPN clusters and then successively drilling down to
isolate the issues to affected sites, applications, and links. Visibility on SD-WAN traffic is shown
on the SD-WAN firewall receiving the traffic. For example, for traffic from the hub firewall to
the branch firewall, the SD-WAN monitoring data is reflected on the branch firewall. The landing
dashboard displays:
• App Performance
• Impacted—One or more applications in the VPN cluster for which none of the paths have
jitter, latency, or packet loss performance that meet the specified thresholds in the Path
Quality Profile in the list of paths from which the firewall can choose.
• OK—Number of VPN clusters, hubs, and branches that are experiencing no jitter, latency, or
packet loss performance issues.
• Link Performance
• Error—One or more sites in the VPN cluster have connectivity issues such as when a tunnel
```
or a virtual interface (VIF) is down.
```
• Warning—Number of VPN clusters, hubs, and branches that have links with bandwidth
```
(supported in PAN-OS 11.1.5 and later with SD-WAN plugin 3.2.2 and later versions), jitter,
```
latency, or packet loss performance measurements that exceed the moving seven-day
average value of the metric.
• OK—Number of VPN clusters, hubs, and branches that are experiencing no bandwidth
```
(supported in PAN-OS 11.1.5 and later with SD-WAN plugin 3.2.2 and later versions), jitter,
```
latency, or packet loss performance issues.
Beginning with PAN-OS 11.1.5, SD-WAN plugin 3.2.2 and later versions support 'bandwidth'
which is the primary measure of the link performance.
```
(SD-WAN plugin 2.0 and later versions) If a hub or branch firewall have an SD-WAN policy rule
```
configured with Forward Error Correction, an Error Correction Initiated message
is displayed to notify you that the hub or branch firewall detected and corrected errors in
transmitted data for an application.
```
(SD-WAN plugin 2.0 and later versions) SD-WAN hubs display Error Correction
```
Initiated only if traffic originated from the SD-WAN hub to the SD-WAN branch and
matched an SD-WAN policy rule with an error correction profile attached.
From the landing dashboard, narrow the view to impacted applications or links that have the
Error or Warning status. Then select an affected site to view site-level details. From the site, view
application-level or link-level details.
SD-WAN Administration 189 ©2026 Palo Alto Networks, Inc.
Monitoring and Reporting
```
(SD-WAN plugin 2.2 and later versions) See Monitor Prisma Access Hub Application and Link
```
Performance to monitor application and link performance for Prisma Access hubs.
If no data is present or the screen indicates that SD-WAN is undefined, check in the
Compatibility Matrix that the Panorama release you are using supports the SD-WAN
plugin release you are trying to use.
STEP 1 | Log in to the Panorama Web Interface.
STEP 2 | Select Panorama > SD-WAN > Monitoring to view at-a-glance health status summaries of
your VPN clusters, hubs, and branches.
STEP 3 | Click an App Performance or Link Performance summary that indicates Impacted, Error,
or Warning counts to view a detailed list of sites and their status based on bandwidth
SD-WAN Administration 190 ©2026 Palo Alto Networks, Inc.
Monitoring and Reporting
```
(supported in PAN-OS 11.1.5 and later with SD-WAN plugin 3.2.2 and later versions),
```
latency, jitter, packet loss, and bandwidth.
To understand how the SD-WAN path measurements are calculated, refer SD-WAN path
selection primer.
STEP 4 | Click a site that displays Warning or Error to see one VPN cluster. The site data display App
Performance and Link Performance, including the impacted applications. Additionally, use
SD-WAN Administration 191 ©2026 Palo Alto Networks, Inc.
Monitoring and Reporting
the Sites filter to view VPN clusters based on link notifications, latency deviations, jitter
deviations, packet loss deviations, or impacted applications.
```
(PAN-OS 11.1.5 and later with SD-WAN plugin 3.2.2 and later versions) You can now view the
```
new link performance parameter, maximum upload/download speed for the selected site in a
VPN cluster.
```
Click each Link to view the baseline bandwidth (supported in PAN-OS 11.1.5 and later with
```
```
SD-WAN plugin 3.2.2 and later versions), jitter, packet loss, and latency measured for the
```
tunnel.
```
(PAN-OS 11.1.5 and later with SD-WAN plugin 3.2.2 and later versions) The Bandwidth graph
```
shows the rolling maximum upload and download speeds for the physical and tunnel links.
```
• For the physical link, the graph displays the SD-WAN interface profile configuration (if
```
```
configured) as the maximum value. Otherwise, the graph displays the maximum Tx and Rx
```
value the physical link has seen so far as the maximum value.
• For the tunnel links, the graph displays the maximum Tx and Rx value the tunnel has seen so
far as the maximum value.
```
(SD-WAN plugin 2.0 and later versions) For SaaS applications over a Direct Internet Access
```
```
(DIA) link, the SaaS Monitoring column indicates whether the app is created in a SaaS Quality
```
profile and associated with one or more SD-WAN policy rules.
• Disabled—The app is not a SaaS application configured in a SaaS Quality profile.
• Enabled—The app is a SaaS application configured in a SaaS Quality profile and is
associated with one or more SD-WAN policies.
```
(SD-WAN plugin 2.0 and later versions) If you associated an error correction profile with an
```
SD-WAN policy rule for an application, the Error Correction Applied columns displays if and
what type of error correction was applied. Additionally, you can view the Error Corrected
Sessions/Impacted Sessions/Total Sessions to understand how many sessions were error
SD-WAN Administration 192 ©2026 Palo Alto Networks, Inc.
Monitoring and Reporting
corrected by the branch or hub firewall out of the total number of sessions for the specified
timeframe.
Click PDF/CSV to export the detailed health information for the applications and links in the
Site in PDF or CSV format.
STEP 5 | Click the branch or hub that has an application that needs attention.
STEP 6 | Click an impacted application to view application-level or link-level details.
For example, view the link characteristics for an application to understand the latency, jitter
and packet loss for the application over the specified link. Additionally, you can view when
error correction was applied for the link.
SD-WAN Administration 193 ©2026 Palo Alto Networks, Inc.
Monitoring and Reporting
Baseline Your Prisma Access Hub Application and Link
Performance
Where Can I Use This? What Do I Need?
• Prisma Access
• NGFW
• SD-WAN plugin 2.2 and later versions
Advanced SD-WAN for NGFW
Before you configure SD-WAN link management profiles, Palo Alto Networks recommends
you baseline your Prisma Access Hub application and link performance to better understand
the normal payload activity for your Prisma Access Hub to avoid unnecessary link swapping for
applications and traffic that do not require it.
STEP 1 | Log in to the Panorama Web Interface.
STEP 2 | Onboard PAN-OS firewalls to Prisma Access for cloud-based security.
STEP 3 | Select Panorama > SD-WAN > Monitoring and modify the SD-WAN monitoring time range.
The longer the time frame you use to baseline your Prisma Access Hub app and link
performance, the more accurate the baseline will be. At a minimum, use three days worth of
app and link performance to baseline the latency, jitter, and packet loss data you use to create
your SD-WAN link management profiles.
Palo Alto Networks recommends assessing seven days of app and link performance
data to baseline the latency, jitter, and packet loss for the Prisma Access Hub.
STEP 4 | Filter the SD-WAN monitoring to display only your Prisma Access Hub-Spoke VPN clusters.
1. Click an App Performance or Link Performance summary that indicates Impacted, Error,
or Warning counts to view a detailed list of sites and their status based on latency, jitter,
and packet loss.
2. In the VPN Cluster filter, select Prisma Access Hub-Spoke.
3. Click a Site to view in-depth health details for the Prisma Access Hub.
SD-WAN Administration 194 ©2026 Palo Alto Networks, Inc.
Monitoring and Reporting
STEP 5 | Review the link characteristics for a Prisma Access Hub application.
1. Click an application in the App Performance section to view the Traffic Characteristics
and the links used for the applications traffic.
2. Click each Link to view the baseline latency, jitter, and packet loss measured for the
application across the link.
Repeat this for all links until you gather sufficient baseline data to modify your Prisma
Access Hub path quality profile.
STEP 6 | Modify your Prisma Access Hub path quality profile based on the latency, jitter, and packet
loss baselines you gathered.
STEP 7 | Continue configuring SD-WAN as needed.
STEP 8 | Monitor Prisma Access hub application and link performance to further fine-tune your SD-
WAN link management profiles.
SD-WAN Administration 195 ©2026 Palo Alto Networks, Inc.
Monitoring and Reporting
Monitor Prisma Access Hub Application and Link
Performance
Where Can I Use This? What Do I Need?
• Prisma Access
• NGFW
Advanced SD-WAN for NGFW
```
Monitor the application and link performance for your Prisma Access Hub (SD-WAN plugin 2.2
```
```
and later versions) to troubleshoot issues by viewing summary information across all VPN clusters
```
and then successively drilling down to isolate the issues to affected sites, applications, and links.
Visibility on SD-WAN traffic is shown on the Prisma Access deployment or SD-WAN firewall
receiving the traffic. For example, for traffic from the hub firewall to the branch firewall, the SD-
WAN monitoring data is reflected on the branch firewall. The landing dashboard displays:
• App Performance
• Impacted—One or more applications in the VPN cluster for which none of the paths have
jitter, latency, or packet loss performance that meet the specified thresholds in the Path
Quality Profile in the list of paths from which the firewall can choose.
• OK—Number of VPN clusters, hubs, and branches that are experiencing no jitter, latency, or
packet loss performance issues.
• Link Performance
• Error—One or more sites in the VPN cluster have connectivity issues such as when a tunnel
```
or a virtual interface (VIF) is down.
```
• Warning—Number of VPN clusters, hubs, and branches that have links with jitter, latency, or
packet loss performance measurements that exceed the moving seven-day average value of
the metric.
• OK—Number of VPN clusters, hubs, and branches that are experiencing no jitter, latency, or
packet loss performance issues.
From the landing dashboard, narrow the view to impacted applications or links that have the
Error or Warning status. Then select an affected site to view site-level details. From the site, view
application-level or link-level details.
See Monitor SD-WAN Application Link Performance to monitor application and link performance
across all your SD-WAN sites.
If no data is present or the screen indicates that SD-WAN is undefined, check in the
Compatibility Matrix that the Panorama release you are using supports the SD-WAN
plugin release you are trying to use.
STEP 1 | Log in to the Panorama Web Interface.
SD-WAN Administration 196 ©2026 Palo Alto Networks, Inc.
Monitoring and Reporting
STEP 2 | Select Panorama > SD-WAN > Monitoring to view at-a-glance health status summaries of
your VPN clusters, hubs, and branches.
STEP 3 | Filter the SD-WAN monitoring to display only your Prisma Access Hub-Spoke VPN clusters.
1. Click an App Performance or Link Performance summary that indicates Impacted, Error,
or Warning counts to view a detailed list of sites and their status based on latency, jitter,
and packet loss.
2. In the VPN Cluster filter, select Prisma Access Hub-Spoke.
3. Click a Site to view in-depth health details for the Prisma Access Hub.
SD-WAN Administration 197 ©2026 Palo Alto Networks, Inc.
Monitoring and Reporting
STEP 4 | Review the Prisma Access Hub in-depth health details.
The site data displays the Prisma Access Onboarding details, as well App Performance and Link
Performance including the impacted applications.
```
For SaaS applications over a Direct Internet Access (DIA) link, the SaaS Monitoring column
```
indicates whether the app is created in a SaaS Quality profile and associated with one or more
SD-WAN policy rules.
• Disabled—The app is not a SaaS application configured in a SaaS Quality profile.
• Enabled—The app is a SaaS application configured in a SaaS Quality profile and is
associated with one or more SD-WAN policies.
If you associated an error correction profile with an SD-WAN policy rule for an application, the
Error Correction Applied columns displays if and what type of error correction was applied.
Additionally, you can view the Error Corrected Sessions/Impacted Sessions/Total Sessions to
understand how many sessions were error corrected by the branch or hub firewall out of the
total number of sessions for the specified timeframe.
Click PDF/CSV to export the detailed health information for the applications and links in the
Site in PDF or CSV format
SD-WAN Administration 198 ©2026 Palo Alto Networks, Inc.
Monitoring and Reporting
STEP 5 | Click an impacted application to view application-level or link-level details.
For example, view the link characteristics for an application to understand the latency, jitter
and packet loss for the application over the specified link. Additionally, you can view when
error correction was applied for the link.
SD-WAN Administration 199 ©2026 Palo Alto Networks, Inc.
Monitoring and Reporting
Generate an SD-WAN Report
Where Can I Use This? What Do I Need?
• NGFW Advanced SD-WAN for NGFW
Configure and generate an SD-WAN report detailing the top applications or links with the highest
frequency of path quality degradation. The order application or links appear in a report is based
```
on the amount of data impacted; the more data is impacted, the higher the application or link
```
appears in the report. SD-WAN reports are generated as needed and cannot be scheduled.
Use the SD-WAN reports to verify the correct application or link throughput, or ensure that
application or link impact is not noticed by users. For example, if your ISP guaranteed a certain
amount of throughput on a link, generate a Link Performance report for that link to verify that the
guaranteed bandwidth is honored.
From the Panorama® management server, you can only generate reports for applications or links
across all SD-WAN enabled firewalls. To generate a report for applications or links processed by
an individual firewall, you must create and generate the report locally on the firewall.
If no data is present or the screen indicates that SD-WAN is undefined, check in the
Compatibility Matrix that the Panorama release you are using supports the SD-WAN
plugin release you are trying to use.
STEP 1 | Log in to the Panorama web interface.
STEP 2 | Select Panorama > SD-WAN > Reports and Add a new report.
SD-WAN Administration 200 ©2026 Palo Alto Networks, Inc.
Monitoring and Reporting
STEP 3 | Configure the SD-WAN report parameters.
1. Enter a descriptive Name for the report.
2. Choose the Report Type to generate:
• Select App Performance to generate a report detailing only application health
performance.
• Select Link Performance to generate a report detailing only the link health
performance.
3. Select the VPN Cluster for which to generate the report. By default, all is selected.
4. Select a Site within the selected VPN cluster for which to generate the report. By
default, all is selected.
If you selected all Clusters then this field is grayed out and a Site cannot be selected.
5. (App Performance only) Select the Application for which to generate the report.
If you selected all Clusters and Sites then this field is grayed out and an individual
application cannot be selected.
6. (Link Performance only) Select the Link Tag for which to generate the report. Selecting a
link tag generates a report for all links in grouped using the tag in the cluster or site. By
default, all is selected.
7. (Link Performance only) Select the Link Type for which to generate the report. Selecting
a link type generates a report for all links of the specified type in the cluster or site. By
default, all is selected.
8. Select the Top N applications or links to include in the report. This setting determines
the number of applications or links experiencing health degradation to include in the
report. By default, the report includes the top 5 applications or links experiencing health
degradation.
9. Specify the Time Period within which to generate the report. By default, None is
selected and queries the entire health status history of the applications or links.
STEP 4 | Click Run Now to generate the report.
STEP 5 | View the generated report and Export XML to export the report in XML format to your local
device. When ready, click Close.
STEP 6 | In the Reports pop-up, click OK to save your configured report.
SD-WAN Administration 201 ©2026 Palo Alto Networks, Inc.
Monitoring and Reporting
STEP 7 | Commit > Commit to Panorama and Commit your changes.
SD-WAN Administration 202 ©2026 Palo Alto Networks, Inc.
Troubleshooting
Where Can I Use This? What Do I Need?
• NGFW Advanced SD-WAN for NGFW
Use the Panorama® management server command-line interface to view SD-WAN information
and perform operations.
Use the following CLI commands to view and clear SD-WAN information and view SD-WAN
global counters. You can also view VPN tunnel information, BGP information, and SD-WAN
interface information.
If You Want to ... Use ...
View or Clear SD-WAN Information
• View path names and IDs for an SD-WAN
interface, their state, local and peer IP
addresses, and tunnel interface number.
> show sdwan connection all | <s
dwan-interface>
• View the number and percentage of
sessions distributed to each tunnel member
of a virtual SD-WAN interface.
> show sdwan session distributi
on policy-name <sdwan-policy-na
me>
• View the names of SD-WAN policy rules
that send traffic to the specified virtual
SD-WAN interface. Additionally, view the
traffic distribution method, configured
latency, jitter, and packet loss thresholds,
link tags identified for the rule, and
member tunnel interfaces.
> show sdwan rule vif sdwan.x
203
Troubleshooting
If You Want to ... Use ...
• View SD-WAN events such as the path
selection and path quality measurements.
For PAN-0S 10.0.0 and
10.0.1, when you make an SD-
WAN configuration change
```
(such as a Path Quality profile
```
```
change) that results in a
```
different SD-WAN path being
selected, the Traffic log does
not count or log the path
change.
> show sdwan event
• Clear SD-WAN events.
> clear sdwan event
• View latency, jitter, and packet loss on
```
a virtual SD-WAN interface (specify
```
```
interface number or name).
```
Latency, jitter, and packet loss
measurements are taken and averaged
over a three time frames time frame. Each
time frame has a health version, which
increments when a health parameter value
```
(that exceeds the threshold) changes. In
```
addition to the real time measurement,
there is a current use measurement, which
displays the value of the parameter the last
time the real-time value change exceeded
the threshold.
> show sdwan path-monitor stats
vif <sdwan.x>
> show sdwan path-monitor stats
vif <sdwan-interface-name>
• View the name of the SD-WAN policy rule
that the specified session matches, the
source and destination tunnel interfaces,
the configured latency, jitter, and packet
> show sdwan session path-select
session-id <session-id>
SD-WAN Administration 204 ©2026 Palo Alto Networks, Inc.
Troubleshooting
If You Want to ... Use ...
loss percentage for the rule, and the traffic
distribution method.
For PAN-0S 10.0.0 and
10.0.1, when you make an SD-
WAN configuration change
```
(such as a Path Quality profile
```
```
change) that results in a
```
different SD-WAN path being
selected, the Traffic log does
not count or log the path
change.
• View monitoring mode for the virtual SD-
```
WAN link (Aggressive or Relaxed) and
```
update intervals.
> show sdwan path-monitor parame
ter path-name <sdwan-path-name>
• View monitoring mode for the virtual SD-
```
WAN interface (Aggressive or Relaxed),
```
update intervals, and probe statistics.
> show sdwan path-monitor parame
ter vif <sdwan.x>
View Global Counters to troubleshoot SD-WAN
• On a branch, verify that the number of SD-
WAN probe Request packets transmitted
equals the number of probe Reply packets
received.
On a branch firewall, most SD-WAN
tunnels are the initiator, which means the
tunnel will have SD-WAN path-monitor
probing enabled.
> show counter global filter del
ta yes
flow_sdwan_prob_req_tx
flow_sdwan_prob_reply_rx
• On a hub, verify that the number of SD-
WAN probe Request packets received
equals the number of probe Reply packets
transmitted.
On a hub firewall, most SD-WAN tunnels
are the responder, which means the tunnel
will have SD-WAN path-monitor probing
disabled.
> show counter global filter del
ta yes
flow_sdwan_prob_req_rx
flow_sdwan_prob_reply_tx
View VPN Tunnel Information
• View all tunnels created on the firewall.
> show vpn flow
SD-WAN Administration 205 ©2026 Palo Alto Networks, Inc.
Troubleshooting
If You Want to ... Use ...
• View details of individual tunnels identified
by name. > show vpn flow name <name>
• View details of individual tunnels identified
by ID. > show vpn flow tunnel-id <tunne
l-id>
• View IKE Phase 1 and Phase 2 details for
all tunnels. > show vpn ike-sa
```
• View IKEv2 security associations (SAs)
```
and IKEv2 IPSec child SAs of a specific
gateway.
> show vpn ike-sa gateway <gate
way>
• View tunnel details.
> show vpn tunnel
View BGP Information
• View the BGP summary for a virtual router.
> show routing protocol bgp sum
mary virtual-router <virtual-rou
ter>
• View the BGP peer summary.
> show routing protocol bgp peer
peer-name <peer-name> virtual-r
outer <virtual-router>
• View a summary of local RIB.
> show routing protocol bgp loc
-rib
View SD-WAN Interface Information among RIB and FIB
• View the new SD-WAN egress interface.
> show routing route
• View SD-WAN interfaces in forwarding
information base. > show routing fib
SD-WAN Administration 206 ©2026 Palo Alto Networks, Inc.
Troubleshooting
If You Want to ... Use ...
• Verify panorama is in FIPS-CC mode.
> debug plugins sd_wan export-mo
ngo-collections deletepass
> debug plugins sd_wan export-mo
ngo-collections export
Initiate IKE/IPSec Negotiation
• Initiate an IKE negotiation with the
designated gateway. > test vpn ike-sa gateway <gate
way>
• Initiate an IPSec negotiation for the
designated tunnel. > test vpn ipsec-sa tunnel <tun
nel>
View Capacity Settings
```
(PAN-OS 12.1.5 and later versions and plugin 3.4.1 and later versions)
```
• View the Capacity Setting related numbers
for the firewall.
```
(Panorama Only)
```
> show plugins sd_wan devices <d
evice number> capacity-setting
• View the Capacity Setting related numbers
for the firewall. > debug sdwand capacity show
```
Autonomous Digital Experience Management (ADEM) Commands
```
```
(PAN-OS 11.1.9 or later 11.1 version, SD-WAN 3.2.2 and later versionwith ADEM 1.0.1 or
```
```
later version)(PAN-OS 11.2.6 or later 11.2 version, SD-WAN 3.2.2 and later version with
```
```
ADEM 1.0.1 or later version)
```
The ADEM plugin is incompatible with PAN-OS version 12.1.2, which means that
upgrading to PAN-OS 12.1.2 will prevent installation of the plugin and disable the
ability to monitor remote sites on next-generation firewalls using ADEM functionality.
View the following ADEM connection status
with SD-WAN plugin:
• PAN-OS connection to ADEM portal
• device certificate validity
• number of applications enabled for testing
>show plugins adem status
SD-WAN Administration 207 ©2026 Palo Alto Networks, Inc.
Troubleshooting
If You Want to ... Use ...
View all the configured applications tests for
an SD-WAN branch. >show plugins adem applications
View the current logging level for ADEM
agent. >show plugins adem log-level
View the last set of data sent to the ADEM
portal. The result will be displayed in the
JASON format.
Run request plugins
adem enable-message-
history command before show
plugins adem message.
>show plugins adem message
View all the valid path where the ADEM agent
has run probes. >show plugins adem paths
View all the SD-WAN tunnel where ADEM
agent has run probes. >show plugins adem vpns
Enable the message history for ADEM probes.
>request plugins adem enable-mes
sage-history
Disable the message history for ADEM
probes. >request plugins adem disable-me
ssage-history
Disable application tests on the SD-WAN
branch. >request plugins adem disable-t
ests
```
Enable ADEM probes (if disabled manually).
```
>request plugins adem enable-te
sts
Run an on-demand path test for an
application over the desired path. >request plugins adem run-applic
ation-path application app_name
path path_name
SD-WAN Administration 208 ©2026 Palo Alto Networks, Inc.
Troubleshooting
If You Want to ... Use ...
Get the application name by running show
plugins adem applications command.
Get the path name by running show
plugins adem paths command.
Run an on-demand ping test for an application
over the desired path. >request plugins adem run-appli
cation-ping application app_nam
e path path_name protocol <icmp|
tcp>
Get the application name by running show
plugins adem applications command.
Get the path name by running show
plugins adem paths command.
Run an on-demand cURL test for an
application over the desired path. >request plugins adem run-curl
application app_name path path_
name
Get the application name by running show
plugins adem applications command.
Get the path name by running show
plugins adem paths command.
Run an on-demand overlay ping test for an
SD-WAN tunnel. >request plugins adem run-vpn-ov
erlay-ping tunnel tunnel_name
Get the tunnel name by running show
plugins adem vpns command.
Run on-demand underlay ping test for an SD-
WAN tunnel. >request plugins adem run-vpn-un
derlay-ping tunnel tunnel_name
Get the tunnel name by running show
plugins adem vpns command.
Run on-demand underlay path test for an SD-
WAN tunnel. >request plugins adem run-vpn-un
derlay-path tunnel tunnel_name
Get the tunnel name by running show
plugins adem vpns command.
SD-WAN Administration 209 ©2026 Palo Alto Networks, Inc.
Troubleshooting
If You Want to ... Use ...
Configure the ADEM agent logging levels:
• Debug—Logs debugging issues.
• Error—Log only errors.
• Fatal—Logs only fatal errors.
```
• Information—Logs agent activity (default).
```
• Verbose—Logs additional debug messages
with detailed information.
• Warning—Logs only warnings and errors.
>request plugins adem set-log-le
vel level log_level
View the ADEM log file information. SD-WAN
retains the last seven days ADEM log files.
Along with other SD-WAN log
files, ADEM log files also are
deleted when you perform a PAN-
OS upgrade or degrade.
>tail follow yes plugins-log <pl
ugin-adem-timestamp.log>
For example:
>tail follow yes plugins-log plu
gin-adem-20250131.log
The timestamp must be in yyyymmdd format.
SD-WAN Administration 210 ©2026 Palo Alto Networks, Inc.
Troubleshooting
Troubleshoot App Performance
Where Can I Use This? What Do I Need?
• NGFW Advanced SD-WAN for NGFW
Understanding what is causing degraded performance for your apps and services is integral to
ensuring the user experience is not impacted. Understanding why your VPN clusters are impacted
and app traffic failed over to different links helps in fine tuning your SD-WAN configuration.
STEP 1 | Log in to the Panorama Web Interface.
STEP 2 | Select Panorama > SD-WAN > Monitoring and view the Impacted VPN clusters.
STEP 3 | Filter the VPN clusters based on your preferred metric from the Site drop-down and select
time frame. In this example, we are viewing All Sites containing impacted VPN clusters in the
last 12 hours.
SD-WAN Administration 211 ©2026 Palo Alto Networks, Inc.
Troubleshooting
STEP 4 | In the Sites column, select the impacted hub or branch firewall to view the impacted apps
and the corresponding link performance.
SD-WAN Administration 212 ©2026 Palo Alto Networks, Inc.
Troubleshooting
STEP 5 | In the App Performance section, click an app to view detailed Traffic Characteristic
```
information about the app traffic such as the internet service(s) and links used:
```
• Review the pie chart to understand the breakdown of app traffic across the your internet
services.
• Review the linegraph to understand how many bytes of data were transferred over each
internet service over time.
• Review the Links Used section to understand which links the app traffic used and to
understand how many of the bytes were impacted out of the total bytes in the selected
time frame.
SD-WAN Administration 213 ©2026 Palo Alto Networks, Inc.
Troubleshooting
STEP 6 | Investigate which health metric caused the app to swap links.
The dotted line indicates the seven day average for the health metric.
1. In the Links Used section of the Traffic Characteristics tab, click an ethernet Link to
```
view detailed Link Characteristics (latency, jitter, and packet loss) over the time frame
```
specified in Step 2 to investigate what health metric caused the app to swap links.
2. In the Traffic Characteristics tab, select another link to view the Link Characteristics
for secondary app link to better understand what caused the VPN cluster to become
impacted.
SD-WAN Administration 214 ©2026 Palo Alto Networks, Inc.
Troubleshooting
STEP 7 | After you have identified why the app traffic is impacted, consider the following to resolve
the issue:
• Consider adding additional links to the traffic distribution profile. By adding additional links
for app traffic to fail over to, you help ensure that the app traffic and user experience are
not impacted by links with degraded health.
• Reconfigure the health thresholds in your path quality profile. It may be that the health
thresholds are too strict, resulting in unnecessary link failover. For example, if you have an
app that can experience up to 18% packet loss before user experience is impacted, having
a 10% packet loss threshold would result in the app failing over to a different link without a
need to.
```
• Consult your internet service provider (ISP) to determine if there are impacts to your
```
network outside of your control that they can resolve.
SD-WAN Administration 215 ©2026 Palo Alto Networks, Inc.
Troubleshooting
Troubleshoot Link Performance
Where Can I Use This? What Do I Need?
• NGFW Advanced SD-WAN for NGFW
Understanding what is causing degraded link performance is integral for ensuring the user
experience when using apps and services is not impacted. Understanding why your VPN clusters
have links that are impacted helps in fine tuning your SD-WAN configuration to ensure that the
user experiences when using apps and services are not affected by links with degraded health.
STEP 1 | Log in to the Panorama Web Interface.
STEP 2 | Select Panorama > SD-WAN > Monitoring and view the Impacted VPN clusters.
STEP 3 | Filter the VPN clusters based on your preferred metric from the Site drop-down and select
time frame. In the Sites column, select the impacted hub or branch firewall to view the
impacted apps and the corresponding link performance.
In this example, we are viewing All Sites containing impacted VPN clusters in the last 24 hours.
SD-WAN Administration 216 ©2026 Palo Alto Networks, Inc.
Troubleshooting
STEP 4 | In the Sites column, select the impacted hub or branch firewall to view the impacted apps
and the corresponding link performance.
SD-WAN Administration 217 ©2026 Palo Alto Networks, Inc.
Troubleshooting
STEP 5 | In the App Performance section, click an app to view detailed Traffic Characteristic
```
information about the app traffic such as the internet service(s) and links used:
```
• Review the pie chart to understand the breakdown of app traffic across the your internet
services.
• Review the linegraph to understand how many bytes of data were transferred over each
internet service over time.
• Review the Links Used section to understand which links the app traffic used and to
understand how many of the bytes were impacted out of the total bytes in the selected
time frame.
STEP 6 | Investigate which health metric caused the app to swap links.
The dotted line indicates the threshold you configure when you define your custom SD-WAN
```
application thresholds (using path quality profiles).
```
1. In the Links Used section of the Traffic Characteristics tab, click an ethernet Link to
```
view detailed Link Characteristics (latency, jitter, and packet loss) over the time frame
```
specified in Step 2 to investigate what health metric caused the app to swap links. In this
example, we are viewing ethernet 1/1 and can see that the percentage of packets lost
SD-WAN Administration 218 ©2026 Palo Alto Networks, Inc.
Troubleshooting
regularly exceeded the configured threshold in the Path Quality Profile for the app and
can conclude that this is the reason the app traffic failed over to the next best link.
2. In the Traffic Characteristics tab, select another link to view the Link Characteristics. In
this example, we are viewing ethernet 1/4 and can see that after the app traffic failed
SD-WAN Administration 219 ©2026 Palo Alto Networks, Inc.
Troubleshooting
over, ethernet 1/4 experienced jitter for the app that exceeded the configured threshold.
This forced the app traffic to fail over back to ethernet 1/1.
Since both links had health metrics that were exceeded, the app traffic had no healthy
link to fail over to resulting in the VPN cluster becoming impacted.
STEP 7 | After you have identified why the app traffic is impacted, consider the following to resolve
the issue:
• Consider adding additional links to the traffic distribution profile. By adding additional links
for app traffic to fail over to, you help ensure that the app traffic and user experience are
not impacted by links with degraded health.
• Reconfigure the health thresholds in your path quality profile. It may be that the health
thresholds are too strict, resulting in unnecessary link fail over. For example, if you have an
app that can experience up to 18% packet loss before user experience is impacted, having
a 10% packet loss threshold would result in the app failing over to a different link without a
need to.
```
• Consult your internet service providor (ISP) to determine if there are impacts to your
```
network outside of your control that they can resolve.
SD-WAN Administration 220 ©2026 Palo Alto Networks, Inc.
Troubleshooting
Troubleshoot KeyID Mismatch
Where Can I Use This? What Do I Need?
• NGFW Advanced SD-WAN for NGFW
You may encounter a keyID mismatch error in your SD-WAN deployments like, hub and spoke or
full mesh deployments. This error commonly occurs when you replace a HA pair in the SD-WAN
cluster, upgrade a HA pair, or clear the SD-WAN plugin cache:
• For deployments earlier to SD-WAN plugin version 2.2.5, 3.0.8, 3.1.3, 3.2.1, or 3.3.0, this issue
```
is seen after the RMA process (that is, after replacing a faulty firewall).
```
• For the newer SD-WAN plugin versions, this issue is seen when replacing one of the HA pairs
with a serial number that’s lower than either of the pairs prior to replacement.
• For the same plugin versions, this issue is seen when clearing the SD-WAN plugin cache. It is
```
not recommended to clear the SD-WAN cache; however, if the cache is cleared, a commit and
```
push to all members of the cluster is mandatory.
Now, let us understand why the keyID error occurs in these cases. When you commit and push to
a few of the SD-WAN devices in the SD-WAN cluster after making these changes, the SD-WAN
device will fail to establish all the SD-WAN tunnels throwing the keyID mismatch error. The SD-
WAN firewall logs the keyID mismatch error in an IKE or system log file.
The SD-WAN firewall uses the following mechanism to generate the keyID and other attributes of
the SD-WAN tunnel:
```
(For versions earlier to SD-WAN plugin 2.2.5, 3.0.8, 3.1.3, 3.2.1, and 3.3.0) During
```
autoprovisioning, the SD-WAN hub firewall uses the serial number of the branch firewall in the
VPN cluster to generate IKE gateway name, IPSec tunnel name, and keyID values. Similarly, the
branch firewall uses the serial number of the hub firewall to generate the IKE gateway name,
IPSec tunnel name, and keyID values.
```
(For SD-WAN plugin 2.2.5, 3.0.8, 3.1.3, 3.2.1, and 3.3.0 versions) The SD-WAN firewall uses the
```
lower serial number among the HA pair to generate the IKE gateway name, IPSec tunnel name,
and keyID values.
Any changes to the firewall's serial number in the VPN cluster will impact the SD-WAN tunnel
establishment, as the firewall's serial number is associated with the keyID and other attributes of
the SD-WAN tunnel.
Consider an example hub and spoke topology, where a hub site is connected with a HA branch
site. Let's see how the hub uses the branch firewall's serial number and the branch uses the
connected hub's serial number in its SD-WAN tunnel attributes. Note the following hub and
branch firewall states that show the usage of serial numbers in the tunnel names.
```
Hub (in working state):
```
admin@SDWAN-hub> show system state | match info.serial
sys.s1.info.serial: 007251000362133
admin@SDWAN-hub> show vpn flow
SD-WAN Administration 221 ©2026 Palo Alto Networks, Inc.
Troubleshooting
total tunnels configured: 3
filter - type IPSec, state any
total IPSec tunnel configured: 3
total IPSec tunnel shown: 3
id name state monitor local-ip
peer-ip tunnel-i/f mode
-- -------------- ----- ------- --------
------- ---------- ----
1 tl_0101_007251000362138_0101 active up 192.0.2.2
172.16.20.2 tunnel.912 tunnel
4 tl_0101_007251000362138_0102 active up 192.0.2.2
172.16.40.2 tunnel.913 tunnel
admin@SDWAN-hub# show template network ike | match "local-id\|peer-
id"
set network ike gateway gw_0101_007251000362138_0101 local-id id
00725100036213801010072510003621330101
set network ike gateway gw_0101_007251000362138_0101 peer-id id
00725100036213801010072510003621330101
set network ike gateway gw_0101_007251000362138_0102 local-id id
00725100036213801020072510003621330101
set network ike gateway gw_0101_007251000362138_0102 peer-id id
00725100036213801020072510003621330101
```
Branch (in working state):
```
```
admin@SDWAN-branch(active)> show system state | match info.serial
```
sys.s1.info.serial: 007251000362138
peer.sys.s1.info.serial: 007251000362134
```
admin@SDWAN-branch(active)> show vpn flow
```
total tunnels configured: 2
filter - type IPSec, state any
total IPSec tunnel configured: 2
total IPSec tunnel shown: 2
id name state monitor local-ip
peer-ip tunnel-i/f mode
-- -------------- --- ------- --------
------- ----------- ----
1 tl_0101_007251000362133_0101 active up 198.51.100.1
192.0.2.2 tunnel.900 tunnel
4 tl_0102_007251000362133_0101 active up 198.51.100.8
192.0.2.2 tunnel.901 tunnel
In the above example, the hub firewall references the serial of the active branch
device in its tunnel name convention. Similarly, the branch firewall references the
serial of the hub device in the tunnel name. Further, the keyID configuration on
each peer is derived from the respective serial numbers. For example, the CLI output
from the hub firewall above shows the local and peer keyID for the tunnel gateway
SD-WAN Administration 222 ©2026 Palo Alto Networks, Inc.
Troubleshooting
gw_0101_007251000362138_0101 as: 00725100036213801010072510003621330101 and
00725100036213801010072510003621330101 respectively.
Now, consider that the SD-WAN plugin managing the hub and spoke topology is upgraded
to version 3.0.8. This results in a recalculation of the serial numbers and redetermining the
lower of the two serials for the HA peer: that is, the serial number of the passive branch device
```
(007251000362134) will be used for the IKE gateway name, IPSec tunnel name as well as the
```
keyID. After the upgrade, if a commit push was executed only to the hub device, then the new
```
tunnel parameters, including a new keyID will be generated; but since there was no simultaneous
```
commit and push to the branch and as the branch firewall is still using the old keyID, it will lead to
a keyID mismatch.
After upgrade, the tunnel configurations and hub tunnel attribute have changed as follows.
```
Branch (in broken state):
```
admin@SDWAN-hub> show vpn flow
total tunnels configured: 3
filter - type IPSec, state any
total IPSec tunnel configured: 3
total IPSec tunnel shown: 3
id name state monitor local-ip
peer-ip tunnel-i/f mode
-- -------------- ----- ------- --------
------- ---------- ----
1 tl_0101_007251000362134_0101 inactiv down 192.0.2.2
172.16.20.2 tunnel.912 tunnel
4 tl_0101_007251000362134_0102 inactiv down 192.0.2.2
172.16.40.2 tunnel.913 tunnel
admin@SDWAN-hub# show template network ike | match "local-id\|peer-
id"
set network ike gateway gw_0101_007251000362134_0101 local-id id
00725100036213401010072510003621330101
set network ike gateway gw_0101_007251000362134_0101 peer-id id
00725100036213401010072510003621330101
set network ike gateway gw_0101_007251000362134_0102 local-id id
00725100036213401020072510003621330101
set network ike gateway gw_0101_007251000362134_0102 peer-id id
00725100036213401020072510003621330101
Following is the sample IKE log of the hub firewall with keyID mismatch error.
```
2025-01-21 19:54:41.680 -0800 [PERR]: { 1: }:
```
198.51.100.1[500] - 192.0.2.2[500]:0x556c1e76bde0 received ID_I
```
(type keyid [00725100036213801010072510003621330101]) does not match
```
peers id
```
2025-01-21 19:54:41.680 -0800 [INFO]: { 1: }:
```
```
192.0.2.2[500] - 198.51.100.1[500]:(nil) closing IKEv2 SA
```
```
gw_0101_007251000362134_0101:74, code 13
```
SD-WAN Administration 223 ©2026 Palo Alto Networks, Inc.
Troubleshooting
```
2025-01-21 19:54:41.680 -0800 [PNTF]: { 1: }: ====>
```
```
IKEv2 IKE SA NEGOTIATION FAILED AS RESPONDER, non-rekey; gateway
```
gw_0101_007251000362134_0101 <====
While the hub firewall is using the new keyID, the branch firewall is still using the old keyID,
which resulted in the keyID mismatch.
To avoid keyID mismatch error, ensure the following:
• If the devices in the SD-WAN cluster have direct reachability to Panorama outside of the SD-
WAN tunnels, commit and push to all devices in the cluster. This ensures that every device has
the matching keyID parameters.
• In both the hub-and-spoke and full mesh topologies, override the gateway configuration on
```
one of the branch (or hub) devices and set the correct keyID values to match the values of
```
the corresponding peer followed by a commit. After reestablishing connectivity to Panorama,
revert the IKE gateway changes by selecting revert after enabling the IKE gateway name
```
(Network > Network Profiles > IKE Gateways). Do not commit after reverting. Instead, commit
```
and push from Panorama and ensure that Merge with Device Candidate Config is selected in
the Push Selection Scope.
The local identification and peer identification may not always be the same value.
Therefore, when setting the local and peer identification, be sure to copy the values
exactly. Copy the local identification value from one gateway and then on the
```
corresponding overriden gateway, paste this value into the peer identification field;
```
similarly, copy the peer identification value from the gateway and paste it into the
local identification field on the corresponding overriden gateway.
SD-WAN Administration 224 ©2026 Palo Alto Networks, Inc.
Troubleshooting
Troubleshoot Pre-Shared Key Mismatch
Where Can I Use This? What Do I Need?
• NGFW Advanced SD-WAN for NGFW
You may encounter a pre-shared key mismatch error in an SD-WAN cluster after a commit and
push operation from the Panorama. When this error occurs, you may view entries similar to the
following in the ikemgr.log file:
```
2025-01-22 17:26:22.700 -0800 [PERR]: { 1: }: 192.168.20.2[500] -
```
172.16.20.2[500]:0x7fa610013da0 authentication failure
```
2025-01-22 17:26:22.700 -0800 [INFO]: { 1: }: 192.168.20.2[500] -
```
172.16.20.2[500]:0x7fa610013da0 authentication result: failure
```
2025-01-22 17:26:22.703 -0800 [PERR]: { 4: }: 192.168.20.2[500] -
```
172.16.40.2[500]:0x7fa6100249f0 authentication failure
```
2025-01-22 17:26:22.703 -0800 [INFO]: { 4: }: 192.168.20.2[500] -
```
172.16.40.2[500]:0x7fa6100249f0 authentication result: failure
```
Additionally, you can view the following error description in the tunnel responder (hub firewall)
```
system logs:
```
We recommend you to look into the IKE and system logs of tunnel peer (the responder)
```
while troubleshooting the pre-shared key mismatch error. Because the tunnel or gateway
marked as passive won’t provide relevant troubleshooting logs.
The pre-shared key mismatch error occurs between the SD-WAN tunnel peers in either of the
following cases:
```
• (Versions earlier to SD-WAN plugin 2.2.6 and 3.0.7) When a name of an SD-WAN cluster is
```
changed, a new pre-shared key will be generated along with the tunnel IP addresses. When
you commit and push the changes to one or some of the cluster devices, then the new keys will
be applied to only those devices. The remaining devices in the SD-WAN cluster will maintain
the old key.
```
(SD-WAN plugin 2.2.6 and later releases, SD-WAN plugin 3.0.7 and later releases) You
```
can’t rename the SD-WAN cluster name. Therefore, there is no relationship between
the pre-shared key and cluster name.
```
• (Versions earlier to SD-WAN plugin 2.2.3, 3.0.4, and 3.1.0) In case of Panorama failover, if you
```
choose to commit and push the configuration changes to selective firewalls rather than to all
the firewalls in an SD-WAN cluster, it will lead to a pre-shared key mismatch. Because the pre-
shared key isn’t synchronized between the Panorama and the firewalls.
SD-WAN Administration 225 ©2026 Palo Alto Networks, Inc.
Troubleshooting
```
• (All SD-WAN plugin versions) If the IKE key is refreshed (Panorama > SD-WAN4 > VPN
```
```
Clusters) for the SD-WAN plugin, a new pre-shared key is generated. Hence, if a commit-push
```
isn’t sent to all members in the cluster after key refresh that will lead to a key mismatch, which
in turn, takes down the tunnels between the applicable tunnel peers.
The IKE key specifies the pre-shared key that is used for authentication. Refreshing the
IKE key is recommended only if it is needed. Because refreshing the IKE key will update
all the SD-WAN tunnels in the VPN cluster. It also requires simultaneous configuration
push to all branch and hub devices. The IKE key and KeyID are different attributes
altogether.
Perform the following if you encounter a pre-shared key mismatch error:
• If the SD-WAN devices have out-of-band access directly to Panorama outside of the SD-WAN
tunnels, then execute a commit and push to all the devices in the VPN cluster. This ensures
that all devices in the VPN cluster are configured with the same pre-shared key.
SD-WAN Administration 226 ©2026 Palo Alto Networks, Inc.
Troubleshooting
• Override the IKE gateway for a specific tunnel peer between the target devices by manually
entering a temporary pre-shared key that matches on both sides.
To override the gateway:
• Log in to the managed device.
• Navigate to Network > Network Profiles > IKE Gateways.
• Manually enter the temporary pre-shared key that matches on both sides.
• Override and commit the changes locally.
Commit the changes locally. Once the tunnel recovers, revert the change without committing it
locally.
Once the tunnel recovers, revert the changes:
```
• Navigate to the same gateway (Network > Network Profiles > IKE Gateways) and revert.
```
Enable Merge with Device Candidate Config in the Push Selection Scope, commit, and push
from Panorama.
SD-WAN Administration 227 ©2026 Palo Alto Networks, Inc.
Troubleshooting
SD-WAN Administration 228 ©2026 Palo Alto Networks, Inc.