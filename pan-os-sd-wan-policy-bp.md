

## PAN-OS SD-WAN
## Policy Best Practice
## Palo Alto Networks, Inc.
www.paloaltonetworks.com
© 2022  Palo Alto Networks, Inc. Palo Alto Networks is a registered trademark of Palo Alto Networks. A list of
our trademarks can be found at  https://www.paloaltonetworks.com/company/trademarks.html. All other
marks mentioned herein may be trademarks of their respective companies.
## Revision Date: May 12, 2022

Table of Contents
Ensuring Rapid and Reliable Path Selection4
Designing an SD-WAN Best Practice Network4
The Role App-ID Plays5
A Word on Predefined Path Quality Profiles5
Identifying the Application Category6
Testing and Tuning Path Quality Profile Thresholds7
## Best Practice Strategies12
## Internal Traffic Strategy12
## External Traffic Strategy13
## Weighted Session Distribution Strategy14
Dealing with Packet Loss14
Catch-All SD-WAN Policy16
## Best Practice Examples17
## Best Practice Example Topology17
## Internal Application Examples18
## Corporate Email Application18
## Corporate Voice Application19
## Mobile Conferencing Application22
## Database Application23
## Custom Business Applications25
Exceptions to the Rule29
## External Application Examples34
## Cloud Email Service34
Voice SaaS Service36
Video Conferencing SaaS Application38
PAN-OS SD-WAN Policy Best Practice© 2022 Palo Alto Networks, Inc.
## 2

## Public Cloud Custom Application41
## Other External Application Considerations44
## Redirecting Traffic Through Hub44
Backhauling All Traffic to Hub45
## Summary45
© 2022 Palo Alto Networks, Inc.PAN-OS SD-WAN Policy Best Practice
## 3

Ensuring Rapid and Reliable Path Selection
PAN-OS SD-WAN is a flexible software defined WAN solution that is tightly integrated with the PAN-OS
NGFW security platform to provide rapid path selection and ensure the highest application usability
possible.  To accomplish this, administrators must fully understand how the path selection mechanisms
operate and what role Quality of Service (QoS) can play in addition to creating the most effective SD-WAN
policies.
This paper discusses topics that should be considered when designing the SD-WAN policies to help you
create a robust network that implements Palo Alto Networks best practices.  Before proceeding, you must
have a good understanding and working knowledge of PAN-OS SD-WAN profiles, policies, and PAN-OS
security components.
For more technical information on QoS, SD-WAN path selection, and how the PAN-OS SD-WAN plugin
automates configuration, please refer to the following papers on thePAN-OS SD-WAN Expert’s Corner:
## ●
Implementing QoS with PAN-OS SD-WAN
## ●
PAN-OS SD-WAN Path Selection Primer
## ●
PAN-OS SD-WAN Auto Provisioning Primer
## ●
PAN-OS SD-WAN Administrator’s Guide
Familiarizing yourself with the PAN-OS SD-WAN Administrator’s Guide and the PAN-OS SD-WAN Path
Selection Primer is highly recommended.  The best practice examples provided are based on customer
deployment experiences and tests performed by Palo Alto Networks’ test team and professional service
engineers.
Designing an SD-WAN Best Practice Network
Creating a best practice SD-WAN network topology relies heavily on how you configure the SD-WAN
profiles, policies, and apply them to critical business applications versus non-critical applications to take
advantage of available bandwidth and to provide intelligent path selection.  There are several traffic
distribution strategies that can be applied to internal traffic (branch to hub or to another branch) and to
external traffic going to the public internet.
Before diving into the best practice strategies, a review of several core SD-WAN concepts helps ground the
examples used in the remainder of this paper.
PAN-OS SD-WAN Policy Best Practice© 2022 Palo Alto Networks, Inc.
## 4

The Role App-ID Plays
As the purpose of implementing SD-WAN is to provide users with the best possible application experience,
it makes sense that application identification (App-ID) is a core component of PAN-OS SD-WAN.  The
firewall uses PAN-OS application decoders to identify an application and its sub functions, and this process
can take multiple packet exchanges to accurately identify the application.  For more information on App-ID,
please reference thePAN-OS Administrator's Guide'sApp-IDchapter.
Application traffic is matched against the SD-WAN policy list starting from the top.  An application match
triggers the SD-WAN policy and its profiles to determine when to take another path and the order of the
paths to use.  The first time the user initiates the application, a full application decoder event takes place.
Once the application is identified, it is cached against the user’s device in the firewall’s App Cache memory
and leveraged by SD-WAN for all subsequent sessions.  The App Cache reduces additional App-ID workload
and allows all subsequent sessions to be matched and analyzed for SD-WAN path selection on the first
packet.
When a new session enters the firewall, the App Cache is checked to see if the application already exists.  If
found, the App-ID from cache is used and no further App-ID processing is required.  If not, the App-ID
engine uses one or multiple packets to decode and identify the application.  If the application is not known
yet, the SD-WAN policy engine cannot perform an application match and the default SD-WAN policy that
matches “unknown” applications is used to forward the first session.  The firewall performs a route lookup
using the Forwarding Information Base (FIB) and selects the SD-WAN egress interface from which to
forward the traffic.
Although this default behavior works for the majority of SD-WAN use cases, you may have an application
that must egress out of the best SD-WAN path based on the first packet of a new session.  In these
situations, the service ports and IP addresses can be used for application identification and custom
application objects can be created and used in the SD-WAN policy to accomplish this.
A Word on Predefined Path Quality Profiles
The examples listed in this paper revolve around the predefined Path Quality Profiles (PQP) that are
provided in PAN-OS SD-WAN.  As a best practice, leveraging the predefined PQP can help you get started
quickly without having to figure out the correct latency, jitter, and packet loss thresholds for each
application you need to manage.
Palo Alto Networks created the SD-WAN predefined path quality profiles by testing multiple applications
from each application category in a controlled environment.  The latency, jitter, and packet loss conditions
were adjusted independently to see where the application’s user experience dropped below acceptable
levels and the results were compiled with other applications from the same category to determine an
acceptable starting point.
If needed, you can tune the values provided by the predefined PQPs as you gain more experience on how
the application responds to the threshold values, and path failover can be accelerated or postponed to
achieve the desired user experience.  As a best practice, make a copy of the predefined profile and adjust
© 2022 Palo Alto Networks, Inc.PAN-OS SD-WAN Policy Best Practice
## 5

the latency, jitter, and packet loss values as needed.  In general, raising the values delays SD-WAN path
failover and lowering them accelerates path failover.
Identifying the Application Category
If you don’t know which category an application falls under, use either thePalo Alto Networks Applipedia
serviceor the PAN-OSObjects > Applicationsto identifythe application and its category, and then use the
corresponding predefined PQP in the SD-WAN policy.  The predefined SD-WAN path quality profile
categories are modeled after the App-ID subcategories to make identification easy.
For example, if you need to create an SD-WAN policy that manages “hotmail” but you’re not sure which
predefined PQP to use, perform a search for the “hotmail” application on Applipedia and reference the
subcategory returned.  In this example, the “email” subcategory is returned.
PAN-OS SD-WAN Policy Best Practice© 2022 Palo Alto Networks, Inc.
## 6

By opening the predefined PQP for “email”, you can verify the three thresholds and sensitivity settings
provided by Palo Alto Networks as a starting point.
Testing and Tuning Path Quality Profile Thresholds
As there are many applications that can fall under the same application subcategory, the predefined
settings may not be the optimal threshold and sensitivity values for your application.  A best practice is to
test your critical applications in a controlled lab environment to see how they respond to latency, jitter, and
packet loss.  This helps identify when an application’s behavior becomes unacceptable and if the predefined
path quality profile’s settings should be used in your production network or if they need to be tuned to
achieve the best results.
© 2022 Palo Alto Networks, Inc.PAN-OS SD-WAN Policy Best Practice
## 7

An easy way to test your application is to leverage open source tools that can introduce latency, jitter, and
packet loss into the internet connection.  For example, Linux’s tc command can be used as shown in this
example:
jitter-test.sh
## #!/bin/bash
# set delay 100ms delay and 10ms jitter
sudo tc qdisc add dev eth0 root netem delay 100ms 10ms
sleep 90
sudo tc qdisc del dev eth0 root netem
#set 40% packet losudo ss
sudo tc qdisc add dev eth0 root netem loss 40%
sleep 90
sudo tc qdisc del dev eth0 root netem
Start the test with the predefined threshold values and either lower or raise the values depending on how
the application responds.  Test one threshold at a time to identify when the application response becomes
unacceptable.   For example, your application testing may follow this process flow:
1.Set the noise generator to match the predefined PQP’s latency value.  Set the jitter and packet loss
settings to the off setting.  This allows you to test one parameter at a time.
2.Run the application and see how it responds with the amount of latency being introduced.  If the
application is behaving fine and the response is acceptable, try raising the amount of latency
introduced on the network until you reach the point where it becomes unacceptable.  If the
predefined latency value breaks the application right away, try lowering the amount of latency
introduced until you find the point where the application starts to become usable.
3.Use the Panorama SD-WAN Monitoring and/or PAN-OS traffic logs to verify the application behavior
and path selection activity.  The illustration below shows the FTP application’s impacted activity
(Bytes Impacted/Total Bytes).
PAN-OS SD-WAN Policy Best Practice© 2022 Palo Alto Networks, Inc.
## 8

The following illustration shows the impacted interfaces for the FTP application.  Take note of the
latency, jitter, and packet loss baseline values provided - as shown by the dash line “-----”.  The
baseline values are measured from the SD-WAN healthcheck probes’ sliding window measurement
and represents a starting point to reference how the network is performing.
© 2022 Palo Alto Networks, Inc.PAN-OS SD-WAN Policy Best Practice
## 9

This next illustration shows the branch office’s traffic log for the FTP application with a non-zero “App
Flap Count”.  The non-zero app flap count tracks the number of times the application switched to a
better performing path.  The SD-WAN widget shows the reason why the application switched paths,
and in this example, we can see that the FTP application switched paths twice due to the latency
threshold being exceeded in the “ftp2hub-branchpolicy-1” SD-WAN policy.
PAN-OS SD-WAN Policy Best Practice© 2022 Palo Alto Networks, Inc.
## 10

4.Once you find the ideal latency value, write it down as this becomes your new latency threshold in
your path quality profile.
5.Repeat steps 1 through 4 for the jitter setting with the latency and packet loss generation turned off.
6.Repeat steps 1 through 4 for the packet loss setting with the latency and jitter generation turned off.
7.Experiment with the “sensitivity” setting on the PQP to see if the application behaves differently with
the priorities for latency, jitter, or packet loss being higher or lower.
If the test results differ significantly from the predefined PQP thresholds, create a new PQP and apply the
new thresholds to obtain better control over the application’s path selection.  This process can also be used
to create PQPs for custom applications where there are no matching predefined profiles.
© 2022 Palo Alto Networks, Inc.PAN-OS SD-WAN Policy Best Practice
## 11

TIP:If you don’t have a noise generator, you can still use the predefined PQP to perform the
test, but it involves more trial and error as you have no control over the network conditions.  Start off
with higher PQP values and test the application’s tolerance to the PQP thresholds.  If these values
are set too low, the application flips back and forth between multiple paths frequently while the
usability remains unaffected.  If it’s set too high, the application’s usability suffers and the application
doesn’t failover to a better performing path until network conditions get much worse.  Use the traffic
logs to filter on the application and monitor the path selection behavior against the application’s
usability to better understand how to tune the PQP settings.
Also remember that many modern cloud applications are tolerant to latency and jitter and can
recover lost packets without greatly impacting the user’s experience.  Only use aggressive thresholds
for applications that really need them to prevent unnecessary path switching.
## Best Practice Strategies
The PAN-OS SD-WAN best practice examples provided in this section follow several strategies that have
been utilized in customer and lab environments to obtain the best path selection behavior for a group of
commonly used enterprise applications.  The application groups selected for illustration include:
## ●
## Email
## ●
## Voice
## ●
## Conferencing
## ●
## Database
## ●
## Customer Business Critical Applications
Two core SD-WAN strategies are used to control internal and external bound application traffic and are
applicable to many enterprise SD-WAN networks.
## Internal Traffic Strategy
Internal bound traffic stays within the company and can originate from the branch going to the hub, from
the branch to another branch, or from the hub to a branch.  Most enterprise networks have one or more
private WAN links (such as MPLS, fiber, satellite, etc.) connecting the locations together and the cost of
operation may not be a primary concern.
For these deployments, the general strategy is to configure the SD-WAN policies with:
## ●
Traffic Distribution Profile:Best Available Path
## ●
Connection Type:SD-WAN interface with VPN Data Tunnel Support enabled
## ●
Path Monitoring:Aggressive with 5 probes per second
PAN-OS SD-WAN Policy Best Practice© 2022 Palo Alto Networks, Inc.
## 12

The SD-WAN tunnels provide seamless application failover between the source and destination firewalls
and with the default path monitoring frequency, the average path selection failover time is approximately
600ms.  Private links also have no next hop IP address changes (as switching between DIA ISP connections
have with different source NAT’d IP addresses), so there are no session disruptions when failing over.
The internal strategy works best when you have multiple circuits with roughly the same bandwidth capacity
for each.  For example, WAN 1 has 200 Mbps capacity and WAN 2 has 150 Mbps.  If the WAN link’s capacity
varies by a large margin, trying to load traffic to the best path with one link having a much higher capacity,
and typically lower latency, with another circuit with a much lower capacity and higher latency doesn’t work
as well.  For example, WAN 1 has 200 Mbps (MPLS) and WAN 2 has 20 Mbps (satellite).
If packet loss is an issue between two SD-WAN firewalls, Forward Error Correction (FEC) or Packet
Duplication (PD) can be enabled to perform packet recovery.
## External Traffic Strategy
External bound traffic is sent outside of the company and originates from the branch or hub going to the
internet through the DIA virtual interfaces (VIF). Most enterprise networks have multiple ISP circuits (such as
broadband, fiber, DSL, etc.) to support path failover and link bundling for this use case.
For these deployments, the general strategy is to configure the SD-WAN policies with:
## ●
Traffic Distribution Profile:Top Down Priority
## ●
Connection Type:SD-WAN interface with VPN Data Tunnel Support enabled
## ●
Path Monitoring:Aggressive with 5 probes per second
With DIA internet circuits, source NAT is typically applied on each ISP link and this can affect how
application failover behavior works.  New sessions are moved to a better performing path, while existing
sessions remain on the current path.  This ensures that traditional TCP applications are not broken when
switching from one ISP to another and taking on a new source NAT IP address mid session.  With the
default path monitoring frequency, the average path selection failover time is approximately 600ms.
Existing sessions that remain on the current path should begin to improve as the new sessions are moved
to another path and congestion is reduced.  With lower congestion, latency and jitter conditions should also
improve.  If packet loss is causing the application to perform poorly, remaining on the current path despite
having new sessions moving to another path may not improve the application.  TCP applications can also
heal from lost or corrupt packets by requesting retransmissions of the impacted packet, but this results in
additional delay and lowers application usability.
The external strategy works best for the majority of internet applications.  Some considerations that you
should be aware of include:
## ●
When a new ISP path is selected due to a circuit failure or brown out condition, the next hop IP
address changes.
## ●
Authentication applications (such as SAML, ADFS, etc) perform better with the Top Down Priority
traffic distribution method.
© 2022 Palo Alto Networks, Inc.PAN-OS SD-WAN Policy Best Practice
## 13

## ●
Applications that create multiple sessions may not behave consistently if the sessions are distributed
between two ISP paths with different source NAT IP addresses.
## ●
SaaS Quality Profiles should be configured for critical SaaS applications to monitor the path health.
The “Adaptive” monitoring mode is preferred for TCP applications as it doesn’t add bandwidth
overhead.
## ●
Forward Error Correction and Packet Duplication are not applied to internet bound traffic because
there is no PAN-OS SD-WAN NGFW on the receiving side.
## Weighted Session Distribution Strategy
A third less used strategy may be useful with specific applications if you need to manually control how
sessions are distributed between the SD-WAN paths.  Weighted session distribution allocates traffic based
on a percentage value assigned to the Link Tag and there is no link failover if the current path encounters
high latency, jitter, or packet loss.  This strategy can be useful to control bandwidth use for metered circuits
(such as LTE) or to control heavy bandwidth applications by keeping them on a specific path and not
allowing them to dominate other paths.
Please reference theSD-WAN Administrator’s Guideand thePAN-OS SD-WAN Path Selection Primerfor
more information on the supported traffic distribution methods.
Dealing with Packet Loss
Packet loss can affect applications in different ways depending on the application protocol.  For example,
TCP applications have the ability to detect packet loss and corruption and can retransmit packets when
needed, whereas UDP applications do not retransmit packets and rely on best effort.  The application itself
may also have packet loss and corruption detection and healing capabilities to lessen the effect of packet
loss, but this is not universal across all modern applications and relies on the application vendor.
PAN-OS SD-WAN provides two mechanisms to deal with packet loss and each has its own benefits and
drawbacks, so understanding how they work can help you decide if they are needed for your internal
applications.  Key considerations for enabling Forward Error Correction (FEC) or Packet Duplication (PD)
include the following:
1.FEC and PD are applied to an SD-WAN VPN connection and not to a public DIA internet connection.
Both solutions require a PAN-OS SD-WAN firewall on both sides of the VPN connection to encode
and decode packet loss repair information.
2.FEC and PD introduce overhead and should only be applied to applications that really need them.
Modern applications may already have packet loss recovery capabilities and duplicating recovery
using the firewall may not improve the user experience further.
3.The firewall CPU and memory resources are used for both recovery methods and implementing FEC
or PD on every internal application can impact other functions.
4.FEC allows you to adjust the ratio of “repair packets to data packets” to control how much overhead
is desired or needed.  The higher the packet loss correction ratio, the better chance of lost packet
recovery and the more bandwidth and CPU resources used.
PAN-OS SD-WAN Policy Best Practice© 2022 Palo Alto Networks, Inc.
## 14

5.PD duplicates every original source packet and sends it on a separate path so it has the best repair
outcome, but introduces the highest bandwidth overhead.
6.Not every VPN tunnel should be used for packet loss recovery.  For example, you may want to
exclude expensive LTE links or low bandwidth satellite links from being used and this can be done
through the SD-WAN Interface Profile’s “Eligible for Error Correction Profile interface selection”
option.  The illustration below shows how the LTE circuit can be excluded from the error correction
profile’s path selection by unchecking the eligibility box on the SD-WAN Interface Profile.
7.PAN-OS SD-WAN’s health probes are used to measure packet loss on the VPN tunnel, and default to
Aggressive mode with a probe frequency of five per second.  Depending on how packet loss is
occuring on the network, there can be variations between the actual number of data packets lost
and the packet loss detection accuracy.  For example, if 95 data packets are being sent per second
and combined with a probe frequency of five per second, a total of one hundred packets per second
© 2022 Palo Alto Networks, Inc.PAN-OS SD-WAN Policy Best Practice
## 15

is seen on the network.  Assuming that the traffic load is consistent and probes are being introduced
evenly, there is one health probe for every nineteen data packets. If a bad network connection drops
ten packets sequentially between the health probes, the firewall does not detect any packet loss as
no health probes were dropped.  If the bad network connection is causing ad hoc packet drops and
impacts both data and probe packets, the firewall detects the packet loss.  Attention must be given
to how the packet loss (%) threshold is applied to the Error Correction and Path Quality profiles and a
lower value may be needed to trigger the policy correctly.
8.FEC and PD require the correct MTU size to be configured on the network.  It does not support an
MTU greater than 1,340 bytes as extra bytes are required to encode the recovery information.
For more information on FEC and PD and how to configure an Error Correction Profile, reference the
SD-WAN Administrator’s Guide.
Catch-All SD-WAN Policy
A catch-all policy should be placed at the bottom of the SD-WAN policy list to match and process any
applications that did not match a more specific policy.  This allows PAN-OS to log and report on the
SD-WAN activity for unmatched applications as well as giving you control over the default behavior.  If you
do not add a specific catch-all policy, PAN-OS distributes the application sessions in round robin fashion
between all available links that satisfy the routing and egress interface selection and this may or may not
meet your needs - especially if expensive or low bandwidth circuits are being used.
There are two catch-all strategies to consider:
1.Use a single catch-all policy for both internal and external traffic and apply a top down traffic
distribution method to control the path selection order.  This method is often preferred when
expensive links (such as LTE) or low bandwidth links (such as satellite) are used.
2.Use multiple catch-all policies to handle internal and external traffic differently.  Internal traffic can
use the Best Available Path traffic distribution method while the external traffic can use the Top
Down Priority method.  The SD-WAN policy’s destination classification can be used to match on
internal vs external traffic to implement the correct traffic distribution policy.
TIP:Best practice is to create your own SD-WAN catch-allpolicy to gain full control and
visibility of how unmatched applications are handled.
PAN-OS SD-WAN Policy Best Practice© 2022 Palo Alto Networks, Inc.
## 16

## Best Practice Examples
## Best Practice Example Topology
To illustrate the different best practice approaches, the examples shown in this paper use a hub spoke
topology.  Two branches named us1-gcp and us2-gcp connect to a single hub named us3hub-gcp and each
site has two ISP circuits and one MPLS WAN connection.
ISP-100M = 100Mbps
ISP-200M = 200Mbps
MPLS = 200 Mbps
The best practice examples highlight the internal vs external bound applications and provide the packet
quality and traffic distribution profiles configured in the corresponding SD-WAN policy that match the
application categories.
As customer networks can differ significantly depending on the type of circuits installed (e.g. cable modem
vs satellite), quality of the last mile connections (copper DSL vs fiber), number of hops to the internet
provider, and so forth, the examples shown use the predefined SD-WAN path quality profiles to illustrate the
SD-WAN policy.
© 2022 Palo Alto Networks, Inc.PAN-OS SD-WAN Policy Best Practice
## 17

## Internal Application Examples
Most enterprises have the following critical application groups that require good usability characteristics as
they are used by many employees.  Having these applications falter due to degraded networks can severely
impact productivity and cause many IT helpdesk events that SD-WAN can help mitigate.
## Corporate Email Application
In this example, the company is hosting its own mail server.  The Microsoft Exchange email application
relies on a mail server infrastructure that is hosted in the corporate data center (DC) and the MS Outlook
clients on each user’s device interact with the Exchange servers on a continuous basis.  Disruption of the
corporate email platform can impact critical decisions and sales, so IT ranks the application as a high priority
business application that is critical to everyone’s productivity.
The MPLS circuit is very stable and has a great SLA that has proven itself over time, but the company has
outgrown the circuit’s 200Mbps capacity as it has increased the number of business applications needed to
grow its business in the last two years.  The IT budget has not kept pace with the growth of the company’s
activity and the rapid hiring pace has made things worse in terms of having adequate bandwidth between
the branch locations and the DC.  The IT team needs a lower cost alternative to supplement the MPLS
circuit and the decision was made to deploy PAN-OS SD-WAN on the company’s PAN-OS firewalls deployed
at each location.
Eventually, the decision may be made to completely remove MPLS, but the network team would like to see
how SD-WAN performs with cost effective internet circuits before migrating off the MPLS circuit entirely.  In
order to create a robust WAN network, the firewall administrator designs and implements the following
best practice SD-WAN policy for the email application.
Application:MS Exchange, MS Outlook
Application Group:Email
SD-WAN Policy:EmailOptimized
Flow:Branch to DC hub
Source Zone:L3-trust
Destination Zone:Zone-to-hub (PAN-OS default zone)
Path Quality Profile:Email
Traffic Distribution Profile:BestAvailable
PAN-OS SD-WAN Policy Best Practice© 2022 Palo Alto Networks, Inc.
## 18

## Corporate Voice Application
In this example, the company has not fully transitioned to a cloud voice system and still hosts its own voice
servers in each location.  The systems rely on a series of voice protocols to allow the handsets and PBX
components to communicate with each other across the branch and hub locations.  Protocols that are
required by the voice system include H.323, H.245, Real Time Protocol (RTP), and Real Time Control Protocol
(RTCP).  The voice system is categorized as a mission critical application and any disruptions are not
tolerated by the users as they rely on this technology to not only communicate internally, but to their
customer base as well.
In order to create a robust voice network, the firewall administrator designs and implements the following
best practice SD-WAN policy for the voice applications.
Application:H.323, H.245 and RTP, RTCP
Application Group:Voip-video and Audio-streaming
SD-WAN Policy:VoIPOptimized and AudioOptimized
Flow:Branch to DC hub
Source Zone:L3-trust
© 2022 Palo Alto Networks, Inc.PAN-OS SD-WAN Policy Best Practice
## 19

Destination Zone:Zone-to-hub (PAN-OS default zone)
Path Quality Profile:VoIP-video and Audio-streaming
Traffic Distribution Profile:BestAvailable
The voice system applications require two separate SD-WAN policies as the family of protocols react
differently to the latency, jitter, and packet loss.  The predefined packet quality profile for voip-audio is
assigned to the H.323 and H245 applications and the audio-streaming profile is assigned to control RTP and
RTCP.  As this is internal traffic between the branch and DC hub locations, the traffic distribution profile uses
the “Best Available Path” distribution method.
The VoIPOptimized SD-WAN policy is configured as follows.
PAN-OS SD-WAN Policy Best Practice© 2022 Palo Alto Networks, Inc.
## 20

The AudioOptimized SD-WAN policy is configured as follows.
© 2022 Palo Alto Networks, Inc.PAN-OS SD-WAN Policy Best Practice
## 21

## Mobile Conferencing Application
In this example, a financial firm is using portable video conferencing carts between their branch and hub
locations to allow employees to host high quality conferencing meetings between large groups of people.
Employees have the choice of using their cloud conferencing application installed on their corporate
laptops or reserving a high quality mobile conferencing cart that’s better suited for team collaboration in
large conference rooms.
The mobile conferencing carts provide 4K video with HD audio and eliminate the need for deploying a high
quality conferencing system in every conference room to reduce costs.  Network applications  required by
the system include H.323 and/or Session Initiation Protocol (SIP), Simple Certificate Enrollment Protocol
(SCEP), web proxy support for Basic, Digest and NTLM.  The network team tested each application by
simulating the amount of latency, jitter, and packet loss each application can withstand before making the
video conferencing application unusable.  The critical applications that impacted usability include the H.323
and SIP protocols while the SCEP and web proxy applications were quite robust under high latency and
jitter environments.
With these test results, the administrator creates an SD-WAN policy to ensure high usability for the
video/audio protocols.  As this is internal traffic between the branch and DC hub locations, the traffic
distribution profile uses the “Best Available Path” distribution method.
Application:H.323, SIP
Application Group:Voip-video
SD-WAN Policy:ConferencingOptimized
Flow:Branch to DC hub
Source Zone:L3-trust
Destination Zone:Zone-to-hub (PAN-OS default zone)
Path Quality Profile:VoIP-video
PAN-OS SD-WAN Policy Best Practice© 2022 Palo Alto Networks, Inc.
## 22

Traffic Distribution Profile:BestAvailable
## Database Application
In this example, a manufacturing company uses several inventory applications throughout its
manufacturing plants and the database is housed at the headquarter data center.  Each manufacturing
location (branch) must have a fully redundant and robust connection with the servers that host the
application.  The manufacturing application is a TCP application and uses Oracle as the database platform.
© 2022 Palo Alto Networks, Inc.PAN-OS SD-WAN Policy Best Practice
## 23

The IT team has categorized the manufacturing applications as a critical business process and the following
SD-WAN policy is created to ensure optimum usability.  Although the Oracle database application requires
separate security policies for logging, SQL, reporting, and other management functions, the SD-WAN policy
uses the “database” application subcategory to classify the Oracle functions.  As this is internal traffic
between the branch and DC hub locations, the traffic distribution profile uses the “Best Available Path”
distribution method.
Application:Oracle
Application Group:Database
SD-WAN Policy:DatabaseOptimized
Flow:Branch to DC hub
Source Zone:L3-trust
Destination Zone:Zone-to-hub (PAN-OS default zone)
Path Quality Profile:General-business
Traffic Distribution Profile:BestAvailable
PAN-OS SD-WAN Policy Best Practice© 2022 Palo Alto Networks, Inc.
## 24

## Custom Business Applications
If you have applications that do not fall into the Palo Alto Networks App-ID categories, such as custom
finance, HR, or manufacturing applications, create a custom application to allow the firewall to perform a
classification match in the SD-WAN policy.  As stated earlier, another reason to create custom applications
for SD-WAN is to allow the firewall to make path selection decisions based on the application’s first packet
versus using the App-ID decoder to identify the application.  When the App-ID decoder is used, the first
session may take several packet exchanges to be fully recognized and this can affect how the path selection
is made for the first session.  After the first session is identified by App-ID, the application cache is used to
identify subsequent sessions for path selection.
TIP:Taking the time to create a custom applicationobject for SD-WAN is a recommended
best practice.  The application object can also be used for other purposes, such as a security policy or
a policy-based routing policy.
To better understand how custom applications are created, follow the instructions provided by the PAN-OS
Administrator’s Guide toCreate a Custom Application.Another resource includes the Palo Alto Networks
YouTube channel where multiple tutorials are posted for creating custom application objects:How to
Configure a Custom App-ID.
Once the custom application is created, it can be selected from the SD-WAN policy’s application selection
screen.
© 2022 Palo Alto Networks, Inc.PAN-OS SD-WAN Policy Best Practice
## 25

TIP:Custom applications are not overwritten or updated by the regular content updates.
In this example, the IT team created a custom application to handle the iperf application that is used to test
one of their custom applications located in the data center’s hub location.  The custom application matches
on TCP destination port 8889.
Application:Custom iperf TCP application (iperf-tcp8889)
Application Group:General-business
SD-WAN Policy:Iperf-tcp8889
Flow:Branch to DC hub
Source Zone:L3-trust
Destination Zone:Zone-to-hub (PAN-OS default zone)
Path Quality Profile:iperf-TCP
Traffic Distribution Profile:BestAvailable
The illustration below shows an SD-WAN policy with a custom application named “iperf-tcp8889” and a
custom PQP named “iperf-TCP”.  When the firewall performs the SD-WAN rule application match, it
matches on the TCP session’s first packet with destination port TCP-8889 and applies the associated path
quality profile.
TIP:Optionally, you can also use source and/or destinationIP addresses to further lock in the
application match for custom applications.  For example, if the custom application is hosted by a few
servers, you can create an address object using the server IP addresses or an FQDN representing all
the servers.
PAN-OS SD-WAN Policy Best Practice© 2022 Palo Alto Networks, Inc.
## 26

The following two illustrations show how the administrator further restricted their test application to a
specific server using an FQDN address object and further tightened the match by only allowing the rule to
match on TCP port 8889.  The application port number can be configured in the SD-WAN rule or the
custom application object and these examples show how it can be done in both places.
The illustrations below show the iperf-tcp8889 custom application’s configuration and how a match is
performed using the capabilities provided by the Application object.
© 2022 Palo Alto Networks, Inc.PAN-OS SD-WAN Policy Best Practice
## 27

The networking team also helped identify the best PQP thresholds for the custom application by setting up
a Linux host that allowed them to fully test the acceptable levels for latency, jitter, and packet loss.  These
thresholds were used to create the “iperf-TCP” path quality profile and allow the company to ensure the
best user experience.  As this is internal traffic between the branch and DC hub locations, the traffic
distribution profile uses the “Best Available Path” distribution method.
PAN-OS SD-WAN Policy Best Practice© 2022 Palo Alto Networks, Inc.
## 28

Exceptions to the Rule
Depending on the type and capacity of your ISP circuits, there can be exceptions to using the “Best
Available Path” traffic distribution method.  Scenarios where a “Top Down Priority” traffic distribution profile
may be better suited include the following use cases.
1.The branch office is using ISP circuits that vary greatly in speed/capacity.  For example:
a.ISP circuit 1 (primary):Fiber connection with 500 Mbps capacity
b.ISP circuit 2 (secondary):DSL connection with 50 Mbps capacity
In this use case, it may be better to use the top down distribution profile and only failover business
applications to the secondary circuit if the primary is degraded or completely down.  This can help
reduce the amount of path selection performed by the firewall as the secondary link is much smaller
than the primary and may be easily pushed to full capacity with just a few large sessions.
The following illustration shows the top down traffic distribution profile and the SD-WAN interface
profile used for this use case exception.  When the PQP’s thresholds are exceeded, the application
matching the SD-WAN policy is  allowed to failover from the primary to the secondary ISP circuit.
© 2022 Palo Alto Networks, Inc.PAN-OS SD-WAN Policy Best Practice
## 29

2.The branch office uses a primary ISP circuit and a backup ISP circuit that is very expensive to operate.
For example:
a.ISP circuit 1 (primary):Broadband with 300 Mbps down/100 Mbps up capacity
b.ISP circuit 2 (backup):5G LTE connection with 200 Mbps capacity
For this use case, the LTE backup connection is only used when absolutely necessary as it’s much
more expensive to operate.  A top down distribution profile allows the primary circuit to be used for
all applications and when the critical business applications are impacted, only they are allowed to
failover to the secondary LTE circuit.  Non-critical applications remain on the primary circuit.
TIP:Creating one distribution profile for criticalapplications and one for non-critical
applications  gives you the flexibility to control how the applications failover or stay on the
impacted link.
PAN-OS SD-WAN Policy Best Practice© 2022 Palo Alto Networks, Inc.
## 30

The following illustrations show the two traffic distribution profiles used to control how critical vs
non-critical applications failover.  Notice the critical application’s profile has two link tags to permit
failover and the profile for the non-critical applications only has one link tag which enforces the no
failover objective.
The following illustration shows the SD-WAN interface profile used for this use case exception.
An alternate traffic distribution profile which can accomplish the same results is to use the
“Weighted Session Distribution” for the non-critical applications and allocate all other traffic to the
primary link.  The weighted session distribution method allocates sessions to the link tags using a
© 2022 Palo Alto Networks, Inc.PAN-OS SD-WAN Policy Best Practice
## 31

percentage value and sessions do not failover to a better performing path when the path is
impacted.
In the following illustration, you can see 100% of the traffic allocated to the “ISP 1 Broadband” link tag
and 0% allocated to the “ISP 2 5G LTE” link tag.   Assigning this profile to the SD-WAN policy that
matches the non-critical applications ensures no failover to the expensive LTE circuit.
3.The branch office uses an application that must be honored with a strict SLA, forcing a private WAN
connection to be preferred over public internet VPN connections that cannot be guaranteed.  For
this use case, many customers retain their MPLS circuits and use them as the primary path for SLA
intensive applications while cheaper public internet circuits are added to scale the bandwidth
demands for other applications.
Two traffic distribution profiles are created to allow the SD-WAN policy to treat each application type
appropriately.  In the illustrations below, the “Strict SLA Apps” profile uses a top down priority
approach and lists the MPLS circuit as the preferred path to honor the SLA it provides and fails the
critical apps over to the non SLA circuits if the MPLS becomes impacted.  Similarly, the “Non SLA
Apps” profile lists the ISP 1 Broadband circuit as the preferred path for other applications and fails
over to MPLS and then finally to the expensive ISP 2 5G LTE circuit.
PAN-OS SD-WAN Policy Best Practice© 2022 Palo Alto Networks, Inc.
## 32

4.The branch office uses an application that may interfere with other critical business applications and
cause frequent path changes between the ISP circuits.  For example, a branch office uses a cloud
storage platform to backup its security video feeds and with the high resolution of the 4K cameras,
the total bandwidth used by multiple cameras can quickly consume over 40% of their total internet
bandwidth.  The network administrator would like to put this application on the secondary ISP link
so it doesn’t interfere with the other core business applications that are placed on the primary ISP
link.  The core business applications’ performance is critical to productivity so they must be treated
as a higher priority than the video backup application, and if the backup process fails, the backup
application keeps retrying and no data is lost.
When the ISP circuits experience poor performance, the video backup application remains on the
secondary ISP circuit without the ability to failover to the primary ISP circuit, but the core business
applications are permitted to use both ISP circuits.
As shown in the following illustrations, two traffic distribution profiles can be created to accomplish
this.  The “Core Business Apps” profile uses the best available path distribution method to allow the
core business applications to use the best performing link from the two ISP circuits.  The “Video
Backup App” profile limits the backup application to just the secondary ISP link with the top down
priority and doesn’t allow it to failover when the link degrades.
© 2022 Palo Alto Networks, Inc.PAN-OS SD-WAN Policy Best Practice
## 33

## External Application Examples
Many enterprises use cloud based applications and services that fall into the same critical application
groups as the internal application examples.  The following examples illustrate the PQP and traffic
distribution profiles that are used as a best practice to keep the applications running smoothly.
## Cloud Email Service
In this example, the company uses Google Mail for its enterprise mail application and users access the
application through their favorite web browser or the GMail app on both corporate provided laptops and
their own mobile devices.  Disruption of the Google mail application can impact critical business functions
so IT ranks the cloud application as a high priority business application that is critical to everyone’s
productivity.
The company uses two ISP circuits at each branch location as shown in the Best Practice Example Topology
above.  IT allows the GMail application to failover to the DC hub location if the branch DIA circuits are
impacted and the failover traffic takes the MPLS path between the branch and hub locations.  The
administrator also configured a SaaS Quality Profile to measure the GMail application’s performance from
the branch office firewall to the destination application server and has set the monitoring mode to
“Adaptive”.  This allows the firewall to use the GMail traffic to determine the latency, jitter, and packet loss
and does not require the firewall to send a health probe to a specified location (IP address).
The following profile and SD-WAN policy are used to ensure the best usability for the GMail application.
Application:Gmail-enterprise
Application Group:Email
SD-WAN Policy:GMailOptimized
Flow:Branch or Hub to Internet
PAN-OS SD-WAN Policy Best Practice© 2022 Palo Alto Networks, Inc.
## 34

Source Zone:L3-trust
Destination Zone:L3-untrust
Path Quality Profile:Email
SaaS Quality ProfileGMailSaaS
Traffic Distribution Profile:TopDown
In order to leverage the hub location as a failover option for the branch’s GMail application, two identically
named SaaS quality profiles must be created on the branch and hub firewalls.  This allows PAN-OS to add
the measurements from the branch to the hub and from the hub to the SaaS application together to obtain
an end-to-end path measurement for GMail.  The easiest way to accomplish this is to create a single SaaS
Quality Profile in the Shared device group using Panorama.
© 2022 Palo Alto Networks, Inc.PAN-OS SD-WAN Policy Best Practice
## 35

As the GMail application is permitted to failover from the branch to the DC Hub if the performance is better going over the
MPLS WAN connection, the SD-WAN Hub firewall must be configured to “Allow DIA VPN” to permit application failover
from the branch location.
Voice SaaS Service
In this example, the company uses the RingCentral SaaS application for all of its phone service and each
employee has an application on their computer and mobile devices to make and receive calls.
The company uses two ISP circuits at each branch location as shown in the Best Practice Example Topology
above.  IT has decided to only allow the phone application to failover between the branch’s two ISP circuits
and the ability to failover to a hub location is not be permitted as the bandwidth capacity at the hub
location is averaging over 80% utilization during business hours.
PAN-OS SD-WAN Policy Best Practice© 2022 Palo Alto Networks, Inc.
## 36

The administrator also configured a SaaS Quality Profile to measure the RingCentral application’s
performance from the branch office firewall to the destination IP addresses that RingCentral gave them for
each of their branch locations.  In this example, the SaaS application uses the “Static IP Address” monitoring
mode and three IP addresses are monitored per branch location.
In order to create a robust voice user experience, the administrator designs and implements the following
best practice SD-WAN policy for the RingCentral voice service.
Application:RingCentral
Application Group:Voip-video
SD-WAN Policy:VoIPOptimized
Flow:Branch or Hub to Internet
Source Zone:L3-trust
Destination Zone:L3-untrust
Path Quality Profile:VoIP-video
SaaS Quality Profile:Us1-gcp-ringcentral
Traffic Distribution Profile:TopDown
© 2022 Palo Alto Networks, Inc.PAN-OS SD-WAN Policy Best Practice
## 37

Video Conferencing SaaS Application
In this example, the company is using Zoom to conduct video conferencing between their employees and
customers.
The company uses two ISP circuits at each branch location as shown in the Best Practice Example Topology
above.  The Zoom application is permitted to use the branch’s two ISP circuits, but the ability to failover to
the hub location is not permitted as the administrator at the central location doesn’t want branch traffic
traversing their internet links.
To provide an alternate backup path for the branch’s mission critical business applications, an LTE
connection is provided at the branch location and it is only used if the primary and secondary ISP circuits
PAN-OS SD-WAN Policy Best Practice© 2022 Palo Alto Networks, Inc.
## 38

are heavily impacted.  Not all applications are allowed to use the LTE backup circuit and the administrator
uses the traffic distribution profile to control access to the expensive service.
For the SaaS Quality Profile, the administrator is using the FQDN for the Zoom service to ensure the path
from the branch to the Zoom cloud service is being measured for latency, jitter, and packet loss.  The
administrator creates the following SD-WAN policy and profiles to ensure high usability for the Zoom
conferencing application.
Application:Zoom
Application Group:Internet-conferencing
SD-WAN Policy:ConferencingOptimized
Flow:Branch or Hub to Internet
Source Zone:L3-trust
Destination Zone:L3-untrust
Path Quality Profile:Internet-conferencing
SaaS Quality Profile:ZoomSaaS
Traffic Distribution Profile:TopDown
© 2022 Palo Alto Networks, Inc.PAN-OS SD-WAN Policy Best Practice
## 39

As there are multiple Panorama administrators across the company, the hub location’s administrator
configured the VPN Cluster to prevent any “accidental” configuration to the traffic distribution profiles that
may allow traffic to failover to their location.  By unchecking the “Allow DIA VPN” option on their hub
firewall, no branches in the VPN cluster are permitted to redirect traffic to their location.
PAN-OS SD-WAN Policy Best Practice© 2022 Palo Alto Networks, Inc.
## 40

## Public Cloud Custom Application
In this example, the company is moving a custom warehouse application from their on-prem data center to
the public cloud.  The warehouse application is secured with TLSv1.2 and uses the company’s certificate
generated by their certificate authority, so it can be accessed directly from the warehouse devices without
an additional VPN tunnel.
Several branch offices are located in remote rural locations where high quality internet connectivity may not
be possible and the network administrator has seen instances where packet loss can contribute to
application performance issues.  The packet loss isn’t a regular occurrence, but when it does happen it’s
enough to cause the application to slow down and this results in users calling the helpdesk complaining of
application slowness and freezing.
There are two SD-WAN deployment options that be used, and the IT team considers both:
1.As the custom application is natively secured through an SSL connection, users can access the
application through the SD-WAN DIA interfaces without the need for an additional VPN tunnel.  This
option treats the custom application just like any other public cloud application and both ISP circuits
can be used to access the application on the public cloud VPC housing the virtual server.  A PAN-OS
SD-WAN firewall is only required at the branch office with this option.  Without a PAN-OS SD-WAN
firewall on both ends of the connection, PAN-OS packet loss recovery techniques cannot be used.
2.With instances of packet loss in a few of the rural branch locations, being able to use PAN-OS
SD-WAN’s packet loss recovery capability would provide the best user experience and ensure
productivity.  This deployment option treats the cloud application as a “Cloud Hub” application and
requires an additional SD-WAN firewall to be deployed at the public cloud edge.  The two SD-WAN
firewalls create a VPN mesh between themselves and enable the ability to turn on Forward Error
© 2022 Palo Alto Networks, Inc.PAN-OS SD-WAN Policy Best Practice
## 41

Correction or Packet Duplication through the VPN tunnel.  This helps recover lost packets and
improve usability.
The team decides to go with option 2, so this custom DIA application resembles an internal application and
a PAN-OS VM-Series firewall is deployed at the cloud edge to support SD-WAN.  The traffic distribution
profile uses a top down approach and places the ISP circuit that typically experiences packet loss as the
secondary path to limit its impact on the warehouse application.
Like the internal custom application example, if you have applications that do not fall into the Palo Alto
Networks App-ID categories, you must create a custom application object to allow the firewall to perform a
classification match in the SD-WAN policy.
TIP:To better understand how custom applicationsare created, follow the instructions
provided by the PAN-OS Administrator’s Guide forCreatea Custom Application.  Another resource
includes Palo Alto Networks YouTube channel where multiple tutorials are posted:How to Configure
a Custom App-ID.
Once the custom application is created, it can be selected from the SD-WAN policy’s application selection
screen and custom applications are not overwritten or updated by the regular content updates.
In this example, the security team created a custom application for their “home grown” warehouse
application which matches on TCP destination port 8280.  In addition, the warehouse devices that use the
application operate from a secure VLAN and have a dedicated source IP address range at each branch.  For
this example, the branch device range is 10.200.21.0/24, and the security administrator took all of this
information into consideration when creating the custom App-ID.
The following SD-WAN policy and profiles were created to support this use case and ensure the best user
experience.
Application:Cloud-warehouse (tcp8280)
Application Group:General-business
SD-WAN Policy:Cloud-warehouse
Flow:Branch to Hub (cloud hub)
Source Zone:L3-trust
## Source Address:10.200.21.0/24
Destination Zone:Zone-to-hub (PAN-OS default zone)
Path Quality Profile:General-business
Error Correction Profile:FEC-warehouse
Traffic Distribution Profile:TopDown
PAN-OS SD-WAN Policy Best Practice© 2022 Palo Alto Networks, Inc.
## 42

The IT team selected Forward Error Correction as the packet loss recovery mechanism after analyzing the
packet loss data from their SIM’s historical information.  Packet loss was not consistent and was not high
enough to justify the overhead that Packet Duplication introduced (replicating every packet on another
link).
After experimenting with the FEC packet loss
correction ratio, the team decided to increase the
ratio from the default value of 10% to 20% to obtain a
higher recovery rate.  As the warehouse application
is not bandwidth intensive, the 20% ratio offered a
good balance between recovery and additional
bandwidth overhead needed by the extra parity
packets.
© 2022 Palo Alto Networks, Inc.PAN-OS SD-WAN Policy Best Practice
## 43

## Other External Application Considerations
Other external use cases that may require additional configuration that goes beyond the packet quality and
traffic distribution profiles include the following.
## Redirecting Traffic Through Hub
As shown in the cloud email example, branch DIA traffic can be configured to failover to a hub location if all
paths are impacted at the branch location.  This capability is very useful for locations that only have one ISP
circuit to the internet with a private WAN circuit (such as MPLS) connecting back to the hub location.  Items
to note include the items listed below and you can reference theDIA AnyPathfeature for more information.
1.The hub location must account for the additional bandwidth to support the branch’s redirected
traffic.  Regional internet issues can impact multiple branch offices and dramatically increase the
bandwidth consumption at the hub location.
2.A branch’s DIA failover traffic to the hub location is not granted by default.  You must permit the
branch locations to failover to the hub by enabling the “Allow DIA VPN” option in the Panorama
SD-WAN plugin’s VPN Cluster hub configuration.  Failover is enabled/disabled for each hub in the
VPN cluster and this gives complete control to the hub administrators.
3.QoS can also be used as an SD-WAN overlay to regulate the amount of traffic the branch is permitted
to redirect to the hub.  Additional information on configuring QoS with SD-WAN can be found in the
Implementing QoS with PAN-OS SD-WANtechnical paper.
4.By default, PAN-OS SD-WAN health probes are measured between the VPN tunnel endpoints.
Additional SaaS Quality Profiles are needed to measure the path health between the firewall and the
target specified in the profile.  Understand the benefits of the adaptive and active probing method
(IP address, http/https) as they each have their benefits and drawbacks.  Reference theSD-WAN
administrator guidefor more information on SaaS QualityProfiles.
5.End-to-end path measurements originating from the branch, going through the hub, and out to the
internet require two identically named SaaS quality profiles to be created - one on the branch and
one on the hub.  This allows PAN-OS to aggregate the VPN and SaaS measurementsto obtain the
end-to-end measurement and greatly reduces the amount of health probes sent from the branch
firewall.
6.SD-WAN and security policies can be used to permit or deny specific DIA traffic through the hub.  For
example, if you wish to only permit business related applications and block non-business
applications, you can create SD-WAN policies to only redirect those applications and overlay them
with security policies for additional enforcement.  For example, allowing a SaaS application’s video
conferencing component but blocking file transfers.
7.Traffic egressing out of the hub location inherits the source NAT IP address of the hub and not the
branch and the SaaS application’s return traffic should go back through the hub location and be
redirected to the branch.  The hub firewall uses symmetric return to send the traffic through the
same VPN tunnel if it’s not impacted.
8.Troubleshooting may require both the branch and hub traffic logs, packet traces, debug commands,
etc., to fully understand the flow.
PAN-OS SD-WAN Policy Best Practice© 2022 Palo Alto Networks, Inc.
## 44

Backhauling All Traffic to Hub
Although PAN-OS SD-WAN is designed to support both public DIA and private traffic flows efficiently and
apply security at each egress location, some use cases still require the redirection of all traffic (both DIA and
private) to the hub for central logging and security enforcement.  This use case is generally implemented
with one or more private WAN links and no public ISP circuits.  The important things to note with this use
case include the following.
1.PAN-OS SD-WAN’sDIA AnyPathmust be implemented toredirect the branch’s DIA traffic through
the WAN link.
2.You must permit the branch to redirect its DIA traffic to the hub by enabling the “Allow DIA VPN”
option in the Panorama SD-WAN plugin’s VPN Cluster hub configuration and this setting is
enabled/disabled per hub.
3.As all traffic is redirected through the WAN link(s), SaaS quality profiles are not needed on the branch
office, and are only configured on the Hub SD-WAN firewall (if needed).
4.Security policies are used at either the branch or hub locations to permit or deny branch traffic.  It is
more efficient to block unwanted applications at the branch before it sends it over the WAN link.
5.QoS can also be used as an SD-WAN overlay to regulate the amount of traffic the branch is permitted
to redirect to the hub.  Additional information on configuring QoS with SD-WAN can be found in the
Implementing QoS with PAN-OS SD-WANtechnical paper.
## Summary
This paper exposed many best practice recommendations for creating SD-WAN policy and profiles
to ensure the highest levels of application usability for all application types.  Multiple customer use
cases were shown in the examples throughout this paper to give you an idea of PAN-OS SD-WAN’s
flexibility when it comes to controlling “when and how” an application should seek a better
performing path.
For more information on PAN-OS SD-WAN concepts, please visit the following links:
## ●
PAN-OS Administration Guide
## ●
PAN-OS SD-WAN TechDocs
## ●
Panorama TechDocs
© 2022 Palo Alto Networks, Inc.PAN-OS SD-WAN Policy Best Practice
## 45