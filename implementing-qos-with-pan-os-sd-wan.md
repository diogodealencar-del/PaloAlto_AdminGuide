

Implementing QoS with
## PAN-OS SD-WAN
## Palo Alto Networks, Inc.
www.paloaltonetworks.com
© 2022  Palo Alto Networks, Inc. Palo Alto Networks is a registered trademark of Palo Alto Networks. A list of
our trademarks can be found at  https://www.paloaltonetworks.com/company/trademarks.html. All other
marks mentioned herein may be trademarks of their respective companies.
## Revision Date: January 5, 2022

Table of Contents
Is QoS Still Required with SD-WAN3
QoS and SD-WAN Considerations3
QoS Configuration Options4
SD-WAN Considerations6
SD-WAN Use Case Examples8
Example 1 - Two Class QoS Policy Use Case10
Example 2 - Four Class QoS Use Case13
Example 3 - Eight Class QoS Use Case19
More Food for Thought21
QoS and SD-WAN Reference Material23
Implementing QoS with PAN-OS SD-WAN© 2022 Palo Alto Networks, Inc.
## 2

Is QoS Still Required with SD-WAN
Palo Alto Networks’ PAN-OS SD-WAN solution provides a rich set of features to help network
administrators ensure the best application user experience.  To do this, PAN-OS SD-WAN is
constantly analyzing the paths between the SD-WAN enabled firewalls and to internet
applications to ensure the best path is being used.  When SD-WAN detects that an application’s
path is degraded, it will attempt to find a better path and will automatically switch paths for all
new application sessions.
However, there can be network conditions that still cause an application to perform below
expectations even with SD-WAN’s automatic path selection.  An example is when all links are
heavily oversubscribed and congested and the path selection criteria thresholds are exceeded on
every link.  When networks are congested, latency, jitter, and packet loss rise as there isn’t enough
free bandwidth on any link to ensure good application performance and usability.
To provide critical business applications with the bandwidth they need at all times, PAN-OS
Quality of Service (QoS) can be overlaid on top of SD-WAN’s path selection capabilities to improve
the application experience.  In addition to preserving bandwidth for critical business applications
and prioritizing its traffic through the firewall, QoS can also be used to influence SD-WAN’s path
failover behavior and this concept is discussed in the use case examples.
QoS and SD-WAN Considerations
This paper illustrates several use cases on how to configure PAN-OS QoS in SD-WAN enabled
networks.  Things to consider before designing the QoS solution include the following:
1)If no QoS policies are specified, the firewall treats all traffic as Class 4 which is often
described as a “best effort” QoS class.
-PAN-OS firewalls apply QoS on the egress interface and QoS policies need to be
applied to the correct interface to take effect.
-QoS policies use application classification to perform policy matches and apply a QoS
class when matched.  Bandwidth and prioritization are applied through QoS profiles.
-All examples use two interfaces: Eth1/1 as the Untrust zone and Eth1/2 as Trust zone.
-IPSec tunnels terminated on Eth1/1 are in a VPN zone.  A QoS policy applied to this
interface guarantees traffic on the IPSec tunnels going to an external destination.  A
QoS profile is created and applied to the QoS settings on Eth1/1 for the “tunneled”
traffic. Conversely, if there is a need to limit downloaded traffic from the internet, a
QoS profile is created and applied to the QoS setting on Eth1/2 for the “clear text”
© 2022 Palo Alto Networks, Inc.Implementing QoS with PAN-OS SD-WAN
## 3

traffic.  Clear text traffic is traffic that is not inside of a VPN tunnel.  This concept is
shown in the following illustration.
2)Traffic must match the classification criteria set in the QoS Policy to get tagged with
DSCP/TOS and class for proper handling.
3)QoS comes into play when the firewall is experiencing high utilization on the links that are
connected to the QoS enabled interfaces.
4)If Max Egress is not defined on the interface it defaults to 5000 Mbps.  Note that this default
maximum can be platform specific.
5)For SD-WAN, there are multiple VPN tunnels terminating on a single physical interface - as
there is one VPN tunnel per service provider originating from the firewall going to each
destination SD-WAN firewall.  For SD-WAN use cases, the Max Egress value is not set on the
physical interface directly.  Instead, QoS is applied through a QoS Profile and applied to the
IPSec tunnel to provide better control for each application’s required bandwidth limits.
QoS Configuration Options
To achieve the desired QoS results, the following QoS features can be set to control priority and
bandwidth allocation for critical applications.
QoS Class- A QoS class is used to determine the priorityand bandwidth for traffic matching a
QoS policy.  There are eight classes numbered 1 - 8 and class 4 is used to classify traffic that doesn’t
match another QoS class.  QoS classes are configured in QoS profiles and assigned to a QoS policy
that is applied to the “egress” interface.
Implementing QoS with PAN-OS SD-WAN© 2022 Palo Alto Networks, Inc.
## 4

Class Priority- For each QoS class, a priority of real-time, high, medium, or low can be assigned.
The maximum and guaranteed bandwidth for matched application traffic can also be set for a
class.  QoS priority queuing and bandwidth management determines the order of traffic and how
traffic is handled upon entering or leaving the firewall when congestion occurs.
Guaranteed Egress- The amount of bandwidth guaranteedfor matched application traffic.
When the egress guaranteed bandwidth is exceeded, the firewall passes traffic on a “best-effort”
basis.  Bandwidth that is guaranteed but unused remains available for all traffic.  Bandwidth can
be guaranteed for a single QoS class, for all or some clear text traffic, and for all or some tunneled
traffic.
Egress Max- The overall bandwidth allocation formatched application traffic. The firewall drops
traffic that exceeds the egress max limit set.  The maximum bandwidth limit can be set for a QoS
class, for all or some clear text traffic, for all or some tunneled traffic, and for all traffic egressing
the QoS interface.
Tip: Not Setting Egress Max or Guaranteed Egress
When entering values for each class’ Egress Max or Guaranteed Egress in the QoS profile, it
is important to set bandwidth capacities based on real production traffic patterns for the
circuit that QoS is being applied on.  It is also important to take into consideration the type
of circuit being used too.
For example, if the circuit is capable of bursting over its capacity level, a better option is to
leave the Egress Max or Guaranteed Egress per QoS profile empty, to allow the circuit’s
burst capabilities to be used.  Remember that interfaces without these settings show an
Egress Max value of 5000 Mbps in the QoS statistics.  One expectation to this is when
utilizing percentage-based values for bandwidth per class, and is addressed further down
in the doc.
Percentage vs Mbps- Egress Guaranteed can be setusing Mbps or a percentage of the Egress
Max’s total bandwidth value set in the QoS profile.  If the bandwidth required by each class should
always be defined as a portion of the profile’s Egress Max value, using the percentage bandwidth
type eliminates the need to adjust the bandwidth maximums when link capacities are upgraded
or downgraded.  Using the Mbps bandwidth type allows a specific amount of bandwidth to be
locked to a class even if the link’s egress max changes.
© 2022 Palo Alto Networks, Inc.Implementing QoS with PAN-OS SD-WAN
## 5

SD-WAN Considerations
Using QoS overlays in an SD-WAN environment requires a combination of QoS options as well as
tuning the SD-WAN path quality and traffic distribution profiles for the corresponding
applications.  The examples illustrate how QoS and SD-WAN policies work together to provide a
better user experience and how QoS policies can control when and if an application should
failover to a better path.
One way to think about how QoS overlays work with SD-WAN path failover is through their inverse
relationship.  When a link is congested, if an application is given a higher priority and more
guaranteed bandwidth through a QoS policy, it reduces the chance of having the application
failover to another path as dictated by the SD-WAN policy.
As not all applications behave the same when they are switched from one ISP circuit to another,
the quality methodology used to ensure the best user experience may require some
experimentation.  For example, a traditional TCP application may crash/hang when its session is
switched from a poor performing ISP link to a better performing ISP link.  This is especially true if
outbound NAT is applied as switching ISP links causes the source IP address to change mid
session.  However, modern “internet based” applications that are transaction based vs. session
based may function flawlessly when switched between ISP links, even when its source IP address
changes mid stream.
Implementing QoS with PAN-OS SD-WAN© 2022 Palo Alto Networks, Inc.
## 6

To extract the best user experience, the QoS bandwidth and SD-WAN path monitoring thresholds
should be configured after understanding how traffic is traversing the ISP circuits.  Real world data
should be used whenever possible to properly model the SD-WAN environment as this allows
accurate QoS and SD-WAN path monitoring profiles to be configured.
If link congestion was an issue before deploying SD-WAN, chances are higher bandwidth circuits
are required and/or QoS policies should be strictly enforced for business critical applications.
Deploying SD-WAN by itself may simply cause the applications to flip back and forth between the
congested links and may degrade the user experience.
Tip:When QoS policies are overlaid on top of SD-WAN,use SD-WAN policies to
control and optimize the traffic flow for qualified business applications and utilize QoS to
control max egress for non-essential and non-business critical traffic.  This ensures more
bandwidth for the critical business applications and reduces the need to flip the
applications between ISP links.  The non critical applications with less guaranteed
bandwidth leverages SD-WAN to find a better performing path.
© 2022 Palo Alto Networks, Inc.Implementing QoS with PAN-OS SD-WAN
## 7

SD-WAN Use Case Examples
In each example, the same topology and bandwidth usage assumptions are used to illustrate the
QoS application.
1)Two Internet circuits, each with 100 Mbps upload and download speeds, are used at each
location. These capacity limits must be considered when configuring the QoS profiles and
policies.
2)A full mesh SD-WAN topology with three locations comprising two branches and one data
center (DC) is used. In a full mesh topology, eight tunnels per device are automatically
configured by the SD-WAN plugin with four tunnels terminated on each of the firewall’s ISP
interfaces.
In the diagram, note that Branch office #1 has two ISPs and multiple VPN tunnels are
created for each of its ISP connections to the other two sites.  As the Branch Office #2 and
DC Headquarter locations also have two ISP providers, there is a 2 X 2 configuration
Implementing QoS with PAN-OS SD-WAN© 2022 Palo Alto Networks, Inc.
## 8

between each site’s ISP providers which results in four VPN tunnels being created between
the source and destination ISP interfaces.  This “full mesh” configuration ensures that there
is always a backup path between the two ISP providers at each location.
To simplify routing, all VPN tunnels from the source location to the destination location are
placed into an SD-WAN Virtual Interface (VIF).  When traffic needs to egress from the local
site to one of the other sites, the route table performs a destination address lookup and
determines which egress SD-WAN VIF the traffic needs to be forwarded to.
The exact tunnel chosen within the SD-WAN VIF is determined by three decision points:
## ●
The traffic distribution profile’s interface tag order.
## ●
The path quality measurements for the tunnels.
## ●
The latency, jitter, and packet loss thresholds set in the SD-WAN policy’s path quality
profile for the matching application.
In general, the healthiest tunnel that matches the traffic distribution profile’s tag order is
selected.  Once that path’s quality degrades and the path quality thresholds no longer
meet the application’s needs, a better performing tunnel is selected (if one exists) and all
new sessions are forward over the new tunnel.  This offloads congestion on the original
tunnel and allows it to return to normal conditions to service additional traffic loads.
3)An assumption is that all eight tunnels are utilized equally and this assigns approximately
25 Mbps of bandwidth per tunnel interface - based on a total of 200 Mbps of available
bandwidth between the two internet circuits with a theoretical max bandwidth of 100
Mbps each.  However, this rarely happens as the SD-WAN health probes on each link helps
to identify the best path.  In addition, the branch to branch traffic loads tend to be less than
traffic from branch to DC headquarters.
4)SD-WAN policies are used to control and optimize the traffic flow for qualified applications
and QoS policies are used to control max egress for non-essential and non-business critical
traffic.
Tip:A best practice recommendation is to have realworld traffic flow data from a
netflow collector, or similar device, that can provide accurate baselining for traffic flows over
each internet circuit
© 2022 Palo Alto Networks, Inc.Implementing QoS with PAN-OS SD-WAN
## 9

Example 1 - Two Class QoS Policy Use Case
In the first example, QoS policies are used to classify all nonessential traffic to Class 8 with a
“priority low” setting and configured limits for guaranteed and egress maximums.  The QoS policy
leaves all other traffic as default with the rest of the available bandwidth and no Egress Max.  The
QoS policies and profiles are applied between all locations.
## Configuration Steps
1)Set up a QoS profile as shown in the illustration below:
a)Class 8 = low priority, 15 Mbps Egress Max, 0 Egress Guaranteed
b)Class 4 = high priority, no Egress Max limit, 85 Mbps Egress Guaranteed
c)Remember that all non-matching applications are automatically assigned to Class 4
Implementing QoS with PAN-OS SD-WAN© 2022 Palo Alto Networks, Inc.
## 10

As all non-matching traffic is automatically treated as Class 4, the policy example shown
below achieves the same QoS results as the policy above.
2)Apply QoS on the proper interface and remember that QoS is applied on the egress
interface, so traffic flow direction is an important consideration.  Also, no Egress Max is
configured on the interface itself as these values are controlled from the QoS profile.
© 2022 Palo Alto Networks, Inc.Implementing QoS with PAN-OS SD-WAN
## 11

3)Add QoS policies with the necessary match criteria for the applications.  In this example, a
policy for all non-business critical applications is applied to Class 8.
Implementing QoS with PAN-OS SD-WAN© 2022 Palo Alto Networks, Inc.
## 12

Example 2 - Four Class QoS Use Case
In the second example, four QoS classes are used to guarantee bandwidth and priority for real
time, high, and medium priority traffic with no max egress set.  Low priority traffic has its max
egress set to control the amount of bandwidth it can use.
QoS policies are used to control application bandwidth and priority between the two branches
and the DC headquarter location.  SD-WAN policies and traffic distribution profiles are used to
handle failover between the two links originating from the branch.
## Configuration Steps
1)Set up a QoS profile with four classes, each with a different priority for real-time, high,
medium and low priority traffic.
a)Class 1 = real-time priority, no Egress Max limit, 45 Mbps Egress Guaranteed
b)Class 2 = high priority, no Egress Max limit, 20 Mbps Egress Guaranteed
c)Class 4 = medium priority, 30 Mbps Egress Max, 30 Mbps Egress Guaranteed
d)Class 8 = low priority, 5 Mbps Egress Max, 0 Mbps Egress Guaranteed
In this example, the guaranteed egress applied to each class totalled up to 95% of max
theoretical total for the link between all four classes.
© 2022 Palo Alto Networks, Inc.Implementing QoS with PAN-OS SD-WAN
## 13

When link congestion occurs, the application traffic matched to the higher priority classes
take precedence (on best effort), while low priority application traffic has its capacity limited
by the max egress limit defined.  This ensures higher priority traffic getting more
bandwidth and lessening the chance of the SD-WAN’s path quality profile thresholds being
triggered.
If the application(s) mapped to the QoS class generate more traffic than the max
bandwidth allocated, congestion arises as the QoS class is now oversubscribed.  Latency,
jitter, and/or packet loss can rise on the link and the path quality profile assigned to the
matching application(s) in the SD-WAN policy are triggered.  This will instruct SD-WAN to
find a better path (if one exists) and select it based on the traffic distribution profile’s path
order.
Implementing QoS with PAN-OS SD-WAN© 2022 Palo Alto Networks, Inc.
## 14

2)Apply the QoS profile to the ethernet interfaces where the SD-WAN tunnels are terminated.
Remember that QoS is applied on the egress interface so traffic flow direction is important
to consider.  Also, no Egress Max is configured on the interface itself as these values are
controlled from the QoS profile.
3)Add QoS policies with the necessary match criteria for the applications to properly line up
with the QoS classes created.  Also, when QoS is combined with SD-WAN, consideration
should be given to the priority of when QoS is applied over SD-WAN’s traffic redirection
profile.
For example, if the preference is to use QoS policies to guarantee bandwidth for critical
applications on each circuit so they don’t have to failover to another path, more bandwidth
can be allocated to these applications and force other non-critical applications to failover
with lower bandwidth limits.  This strategy may be less disruptive to critical applications
depending on how the application reacts to switching links.
In the following QoS policy example, critical marketing and finance applications going to
the DC hub are mapped to Class 2 with high priority and a guaranteed bandwidth of 20
Mbps.  This ensures that these applications are given enough bandwidth to operate before
failing over when the link becomes congested.
© 2022 Palo Alto Networks, Inc.Implementing QoS with PAN-OS SD-WAN
## 15

If less bandwidth is allocated to a specific class, congestion builds on those links when it
gets busy and latency, jitter, and packet loss rises.  When this happens, SD-WAN’s health
probes detect this condition and triggers the SD-WAN path monitoring profile’s thresholds
and instructs the firewall to switch the impacted application to a better performing link (if
one exists).
In the following SD-WAN policy example, the marketing applications are using SD-WAN’s
predefined “general-business” path quality profile thresholds to determine if a better link
should be taken.
Implementing QoS with PAN-OS SD-WAN© 2022 Palo Alto Networks, Inc.
## 16

Tip:As a best practice, leveraging PAN-OS’s predefined path quality profiles can
help administrators get started quickly without having to figure out the correct
latency, jitter, and packet loss thresholds for each application they need to maximize
usability for.
Palo Alto Networks created the SD-WAN predefined path quality profiles by testing
multiple applications from each application category in a controlled environment.  The
latency, jitter, and packet loss conditions were adjusted independently to see where the
application’s user experience dropped below acceptable levels and the results were
compiled with other applications from the same category to determine an acceptable
starting point.
If needed, the predefined category thresholds can be tuned afterwards when more
application testing has been performed in the environment.  Path failover can be
accelerated or postponed to achieve the desired user experience.  Simply make a copy of
the predefined profile and adjust the latency, jitter, and packet loss values as needed.  In
general, raising the values delay SD-WAN path failover and lowering them accelerate path
failover.
If you don’t know which category an application falls under, use thePalo Alto Networks
Applipedia serviceto identify the application andits category, and then use the
corresponding predefined path quality profile in the SD-WAN policy.
In this example, applications matching the SD-WAN policy uses a “Top Down Priority” traffic
distribution profile that prioritizes the ISP A Fiber service over the ISP B Broadband service
and when the path quality profile’s thresholds are exceeded, the matching applications will
switch from ISP A to ISP B’s paths.
© 2022 Palo Alto Networks, Inc.Implementing QoS with PAN-OS SD-WAN
## 17

Tip:If there are multiple ISP links that you wouldlike to bundle together to take
advantage of the aggregate bandwidth they provide, assign the same Link Tag for each ISP
service’s interface profile and PAN-OS automatically groups the links together to form one
big virtual link (pipe).  Application traffic is automatically distributed to all links in the
bundle and when congestion is encountered on one link, the best link in the bundle is used
for new sessions.  When all links in the bundle are not meeting the path quality profile’s
thresholds, the next tag in the top down priority list is selected if it can provide a better
path.
Implementing QoS with PAN-OS SD-WAN© 2022 Palo Alto Networks, Inc.
## 18

Tip:If there are circuit types that should not be used for routine path failover, such as
expensive 5G LTE links, set the “VPN Failover Metric” in the SD-WAN Interface Profile
accordingly.  The lower the metric value, the higher the priority of the tunnel to be chosen
for failover.
With the QoS policy overlay guaranteeing bandwidth for these applications, there is less chance of
path failover when ISP A’s link is heavily used.  Understanding how QoS classes work in relation to
SD-WAN’s path quality profile thresholds and traffic distribution profiles will help network
administrators decide how to best configure the SD-WAN architecture to ensure the best
application usability experience.
Example 3 - Eight Class QoS Use Case
In the third example, granular application quality is controlled using eight QoS classes.  The
configuration provides egress guarantees for real time, high and medium priority applications but
it doesn’t limit the egress maximum for these classes.  An egress maximum limit is set on the low
priority class to restrict matching applications on the amount of bandwidth they can use and this
reserves more bandwidth for the other higher priority classes.
Bandwidth is assigned using a percentage of the Egress Max’s total bandwidth.  QoS policies are
used to control application bandwidth and priority between the two branches and the DC
headquarter locations.  SD-WAN policies, path quality profiles, and traffic distribution profiles are
configured to handle failover between the two links originating from the branch.
Tip:In general, the desired QoS and SD-WAN failovercombinations can be achieved
with fewer classes.  The eight class QoS example should only be used if it’s absolutely
necessary as it adds complexity.
## Configuration Steps
1)Set up a QoS profile with eight classes, each with different two priorities for the same class.
a)Class 1 = real-time priority, no Egress Max limit, 25% Egress Guarantee
b)Class 2 = real-time priority, no Egress Max limit, 5% Egress Guarantee
c)Class 3 = high priority, no Egress Max limit, 20% Egress Guarantee
d)Class 4 = medium priority, no Egress Max limit, 20% Egress Guarantee
e)Class 5 = high priority, no Egress Max limit, 5% Egress Guarantee
f)Class 6 = high priority, no Egress Max limit, 5% Egress Guarantee
© 2022 Palo Alto Networks, Inc.Implementing QoS with PAN-OS SD-WAN
## 19

g)Class 7 = medium priority, no Egress Max limit, 0% Egress Guarantee
h)Class 8 = low priority, 15% Egress Max limit, 10% Egress Guarantee
In this example, the guaranteed egress percentage applied to each class totalled up to 90%
of max theoretical total for the link between all eight classes.
When link congestion occurs, the application traffic matched to the higher priority classes
take precedence (on best effort).  This example used additional classes to provide more
granularity with application matching and additional levels of bandwidth control to allow
applications from different app categories to have their bandwidth guarantees.
The SD-WAN policy’s application matching should go hand-in-hand with the applications
defined in the QoS policies to ensure the best control over when an application should
failover to a better link.  Separate traffic distribution profiles can be created and assigned to
the granular SD-WAN policies to set up different path selection order if needed.  For
Implementing QoS with PAN-OS SD-WAN© 2022 Palo Alto Networks, Inc.
## 20

example, one high priority class may take a top down approach while another high priority
class can take a “Best Available Path” approach.
The low priority application traffic has its capacity limited by the max egress percentage
limit defined.  This ensures higher priority traffic getting more bandwidth and lowering the
chance of the SD-WAN’s path quality profile thresholds being triggered.
2)Apply the QoS profile to the ethernet interfaces where the SD-WAN tunnels are terminated.
Remember that QoS is applied on the egress interface so traffic flow direction is important
to consider.  Also, no Egress Max is configured on the interface itself as these values are
controlled from the QoS profile.
3)Add QoS policies with the necessary match criteria for the applications to properly line up
with the QoS classes created.  Also, when QoS is combined with SD-WAN, consideration
should be given to the priority of when QoS is applied over SD-WAN’s traffic redirection
profile.
See example 2 for more details on how QoS and SD-WAN policies work together.
More Food for Thought
This paper illustrates how QoS can be used with SD-WAN policies to further raise application
usability to ensure the best possible user experience for critical applications.  There are other
strategies outside of this paper that can be considered as well.  For example:
© 2022 Palo Alto Networks, Inc.Implementing QoS with PAN-OS SD-WAN
## 21

1)Isolate critical applications onto the most reliable link(s).  If the site has multiple links with
different quality/bandwidth characteristics (such as fiber, DSL, satellite), a “top down
priority” traffic distribution profile can be created with the best performing links on top and
the lower quality/bandwidth links towards the bottom.  Assign the traffic distribution profile
to the critical applications to guarantee them the best paths first.  Similarly, create a traffic
distribution profile with the lower bandwidth/quality links as the primary link for the
non-critical applications and assign it to the SD-WAN policy that matches with these
applications.  Keeping the critical applications on the best performing links and the other
non-critical applications on the lower quality links help isolate the traffic classes better and
give more options on how bandwidth is used.
2)Don’t let low priority non-critical applications take over in a failover situation.  Create a
traffic distribution profile that restricts the links lower priority applications can use and
don’t let them failover to links that critical applications use.  For example, if there are high
bandwidth consuming applications that are non business related, create a traffic
distribution profile with only one link tag to prohibit path changes.  When that link is
congested or down, the matched traffic cannot failover to another path and impact critical
business applications.  This strategy allows the non-critical applications to operate only if
specific links are available.
3)Sacrifice non business low priority applications when there is insufficient bandwidth.  Tune
the SD-WAN path quality profile thresholds to a higher value and assign the profile to the
SD-WAN policy that controls the low priority applications.  This strategy keeps the low
priority applications on the congested link longer (or indefinitely) and allows the critical
applications to find a better performing path (if one exists) and failover.
4)Leverage QoS to control the class priority and the amount of bandwidth non business
applications can use on both the primary and failover links.  Never let these applications
overly consume bandwidth and cause issues for critical business applications.
Using a combination of strategies mentioned above and understanding QoS’s role within an
SD-WAN topology allows network administrators to create robust networks that maximize the
application user experience.
In addition, don’t forget to use the Panorama SD-WAN monitoring tool and related SD-WAN CLI
commands to better understand how the applications and links are performing.  If the critical
applications are frequently failing over between multiple paths, determine if this is caused by
congestion and oversubscribed bandwidth onevery linkor if this is isolated to one application or
link.  If it’s the latter, tune the QoS and SD-WAN profiles to lessen the impact.  If it’s the former, add
more bandwidth, apply aggressive QoS policies to control non essential applications, or set up
security policies to block some of the non business applications.
Implementing QoS with PAN-OS SD-WAN© 2022 Palo Alto Networks, Inc.
## 22

QoS and SD-WAN Reference Material
## ●
PAN-OS Quality of Service Admin Guide
## ●
Getting Started: Quality of Service
## ●
## PAN-OS SD-WAN
© 2022 Palo Alto Networks, Inc.Implementing QoS with PAN-OS SD-WAN
## 23