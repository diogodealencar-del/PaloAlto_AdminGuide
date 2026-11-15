

## Security Policy Best Practices
docs.paloaltonetworks.com

## Contact Information
## Corporate Headquarters:
## Palo Alto Networks
## 3000 Tannery Way
Santa Clara, CA 95054
www.paloaltonetworks.com/company/contact-support
About the Documentation
•For the most recent version of this guide or for access to related documentation, visit the Technical
Documentation portal docs.paloaltonetworks.com.
•To search for a specific topic, go to our search page docs.paloaltonetworks.com/search.html.
•Have  feedback  or  questions  for  us?  Leave  a  comment  on  any  page  in  the  portal,  or  write  to  us  at
documentation@paloaltonetworks.com.
## Copyright
## Palo Alto Networks, Inc.
www.paloaltonetworks.com
## ©
2022-2024   Palo   Alto   Networks,   Inc.   Palo   Alto   Networks   is   a   registered   trademark   of   Palo
Alto  Networks.  A  list  of  our  trademarks  can  be  found  at  www.paloaltonetworks.com/company/
trademarks.html. All other marks mentioned herein may be trademarks of their respective companies.
## Last Revised
## January 22, 2024
## Security Policy Best Practices2
## ©
## 2026 Palo Alto Networks, Inc.

## Security Policy Best Practices
Security policy determines what traffic you allow on your network and how to treat that traffic.
Security policy best practices limit the traffic you allow to only sanctioned traffic required for
your business and tolerated traffic for your employees. This reduces the attack surface and helps
safeguard your network and your business assets. The viewpoint of this document is what to do
for best network security whether your business is security-first or mission-critical availability
first.
Security policy best practices follow the principle of least privilege, which means that only people
who need access to specific applications, data, and infrastructure are granted access, and that
traffic is decrypted, inspected, and logged appropriately to protect assets, intellectual property,
and other things that are critical to your business. All other access increases risk without achieving
business goals.
This book contains streamlined, step-by-step best practices for how to:
•Plan Security policy
•Deploy Security policy
•Maintain Security policy
Steps that require configuration or for which there is in-depth conceptual information include
links to the appropriate documentation for details. Learn about features, capabilities, and
operation of Palo Alto Networks products in product administrator’s guides, release notes,
upgrade guides, interconnect guides, etc., which are available on technical documentation home
page:
## •PAN-OS
•Panorama
•Panorama Managed Prisma Access and Strata Cloud Manager Managed Prisma Access
(including GlobalProtect App documentation)
•Prisma SD-WAN
•Cloud Delivered Security Services
•Cloud Identity Engine
•GlobalProtect
•VM-Series
•CN-Series
•Cortex Help Center
•Firewall and appliance hardware guides
Refer to the Palo Alto Networks series of best practices books for best practices advice on
subjects such as decryption, DoS and Zone Protection (including Packet Buffer Protection), and
much more.
## 3

## Security Policy Best Practices
## Plan Security Policy Best Practices
Before you create best practice Security policy rules, make sure you understand best practices
for planning a secure network, especially Zero Trust Network Access (ZTNA) principles. Security
policy defines the traffic you allow and block. However, it takes a comprehensive set of tools and
services to completely protect your network, including tools that provide:
•Visibility, such as decryption, App-ID, User-ID, and Device-ID.
•Advanced Threat Prevention, such as vulnerability protection, antivirus, anti-spyware, file
blocking, sandboxing, Data Loss Prevention (DLP), DNS Security, and more.
•IoT security to control unmanaged devices and SaaS security to control SaaS applications (next-
generation CASB).
Ensure that you have the appropriate toolset to safeguard your network and to use in and with
Security policy.
STEP 1 |You can’t defend against threats that you can’t see. Decrypt all the traffic you can, in
accordance with legal compliance, local regulations, privacy regulations, and business
considerations to gain visibility into traffic so you can inspect it and prevent threats. For SSL
Forward Proxy (outbound) decryption, implement User-ID and URL Filtering first so you can
target decryption effectively. Some traffic can’t be decrypted due to technical reasons such
as pinned certificates, client authentication, and embedded certificates in IoT devices.
If you don’t decrypt traffic, the firewall can’t granularly identify applications. For example,
the firewall can see that the container application is facebook, but can’t see the functional
application, so you don’t know and can’t control if the user is uploading, downloading, posting,
etc. on Facebook. The firewall also can’t see and inspect the payload, so you don’t have the
visibility to defend against malicious content. To get the most from your other subscriptions
and to achieve the best protection, you must decrypt traffic to gain visibility into that traffic.
Decryption doesn’t require a license, but for decrypting outbound traffic, add an Advanced
URL Filtering license so that you can take a granular approach to decryption and easily choose
which types of traffic to decrypt and not to decrypt. URL Filtering enables you to exclude
categories that you shouldn’t decrypt for legal, personal information, regulatory, or other
reasons. URL Filtering also enables you to block user access to malicious websites.
In addition, decrypt inbound traffic to protect critical servers and decrypt SSH Proxy traffic to
prevent malicious management traffic.
Follow decryption best practices to prepare for, roll out, and maintain decryption.
STEP 2 |View the planning and deployment processes through a lens of least privilege access and
## Zero Trust Network Access.
Understand who needs to use which applications to access which data and which
infrastructure. This enables you to construct Security policy rules that allow only the people
who need access for business purposes access to only the necessary data and infrastructure
while blocking all other access.
Use the attributes available in Security policy to define least privilege access: users, devices,
applications, source and destination, service, and URL (for outbound traffic, with decryption
## Security Policy Best Practices4
## ©
## 2026 Palo Alto Networks, Inc.

## Security Policy Best Practices
enabled so that the firewall has visibility into each functional application, not just the container
application).
STEP 3 |Get the appropriate subscriptions for your business to achieve the best threat prevention
and security posture.
Advanced URL Filtering—Cloud-delivered service that enables safe website access, protects
users from dangerous sites, and helps prevent credential phishing attacks.
Advanced Threat Prevention or active legacy threat protection—Cloud-delivered Advanced
Threat Prevention uses inline deep learning and machine learning models for real-time
enforcement of evasive and day-one command-and-control (C2) threats, and includes all
features of standard Threat Prevention. Standard Threat Prevention protects against C2,
malware, and vulnerability exploits.
Air-gapped environments cannot use Advanced Threat Prevention because it’s a
cloud service and requires a cloud connection.
Follow best practices for Threats Content Updates to ensure that you have the
latest protections.
DNS Security—(Must purchase an Advanced Threat Prevention or have an active legacy
Threat Prevention license and a DNS Security license to activate) Cloud-delivered service
that identifies and blocks threats in DNS traffic and prevents connecting to malicious DNS
sites and is constantly updated to prevent new types of DNS-based attacks.
Enterprise Data Loss Prevention (DLP)—Cloud-delivered service that protects data across
all enterprise networks, clouds, and users, and enables compliance with data safety
regulations.
Strata Logging Service—Cloud-based log storage that scales with your log volume and
ingests logs from next-generation firewalls, Panorama, Prisma Access, and Cortex XDR.
Most Cortex applications use Strata Logging Service to access, analyze, and report on your
logged network data.
WildFire—Cloud-based or private analysis environment that identifies both known and
unknown (new) malware and generates signatures the firewall uses to identify and block
malicious traffic.
SaaS Security—Cloud-delivered service that secures your sanctioned SaaS applications with
licenses that can be standalone or bundled:
•The Data Security license includes SaaS Security API and Enterprise DLP.
•The SaaS Security Inline add-on license works with Strata Logging Service to discover
and control all the SaaS applications on your network, including Shadow IT applications,
and enables SaaS Policy Recommendation to the firewall administrator.
•Enterprise DLP to protect against data loss in SaaS applications.
IoT Security—Discovers and secures IoT devices on your network and enables automatic
IoT Policy Rule Recommendations to the firewall administrator. Follow IoT Security best
practices for planning, deployment, and monitoring.
GlobalProtect—Provides capabilities beyond the free VPN features, including the
GlobalProtect mobile app, HIP checks, clientless VPN, and more.
## Security Policy Best Practices5
## ©
## 2026 Palo Alto Networks, Inc.

## Security Policy Best Practices
STEP 4 |Review your network segmentation plan.
For Panorama Managed Prisma Access, there are effectively only two zones, trust and untrust,
and you map all Panorama zones to the Prisma Access trust or Prisma Access untrust zone.
On Panorama and firewalls, if a zone isn’t granular enough and includes devices, users, and
applications that require different security treatment, consider rearchitecting your zones
to segment the network in a more granular way. Place users, applications, and devices that
require similar treatment in the same zone. Small zones are easier to defend than large zones.
In some cloud environments, the architecture might limit the number of zones you can
configure.
Follow DoS and Zone Protection Best Practices to prevent flood attacks and safeguard the
devices in each zone and your firewall buffers.
For Strata Cloud Manager Managed Prisma Access, base microsegmentation on identity.
STEP 5 |Define which applications you need to allow for business purposes (sanctioned applications)
and which applications to allow for other purposes (tolerated applications).
Use App-ID in Security policy (no subscription required) to identify both container applications
and their functional applications (e.g., not just “facebook” but “facebook-post”, “facebook-
download”, etc.). If you use SaaS Security, use the App-ID Cloud Engine (ACE) to identify cloud
applications (requires SaaS Security subscription).
The firewall allows applications you specify in Security policy rules whose Action is Allow and
blocks applications specified in rules whose Action denies, drops, or resets traffic, based on
the rule’s criteria. Traffic must meet all of a rule’s criteria to match the rule. If an application
matches no rule, the two default rules at the bottom of the Security policy rulebase control the
traffic. Interzonal (source and destination are in different zones) traffic is denied by default.
Intrazonal (source and destination are in the same zone) traffic is allowed by default.
Communicate access policy so employees understand why they may not be able to access
certain applications.
STEP 6 |Identify all users. Control who has access to which applications and devices in Security policy
to ensure that consistent policy follows each user everywhere in the network.
User-ID (no subscription required) combines user information from multiple sources to identify
all users on your network. To help ensure that user identification is consistent and to scale
across your network, use the Cloud Identity Engine (CIE) (no subscription required) as an
aggregated single source for User-ID. CIE gathers and synchronizes user data from sources
across your network. All firewalls pull exactly the same user information from CIE, whether
## Security Policy Best Practices6
## ©
## 2026 Palo Alto Networks, Inc.

## Security Policy Best Practices
they’re on a campus or in the cloud. CIE also provides authentication in conjunction with most
major identity providers (IdPs) such as Okta, Azure AD, PingID, etc.
In PAN-OS 10.2 and earlier, CIE provides Directory Synchronization (DSS) and Cloud
Authentication (CAS) services. Starting with PAN-OS 11.0, you can also use CIE as
redistribution points.
When configuring user groups, think about who needs to access the same resources in the
same way for the same business purposes and follow best practices for user group mapping
and best practices for dynamic user groups (DUGs).
Use GlobalProtect VPN in Always On mode for highest security and reliable user identification
if possible. Use GlobalProtect for remote access and with internal gateways to gather User-ID
information no matter where your users are located.
STEP 7 |Plan to attach the appropriate Security profiles or Security profile group to every Security
policy rule that allows traffic. (If a rule blocks traffic, the firewall doesn’t inspect the blocked
traffic.)
Security profile groups are groups of profiles tuned for a particular purpose that you apply to
Security policy rules instead of applying each profile individually. This saves time and helps
prevent accidental misconfiguration.
STEP 8 |Plan how to store logs (in Strata Logging Service, on Log Collectors, etc.) and which
administrators to notify for different types and severities of log events. Plan for enough log
storage capacity to enable investigation into events after they occur.
STEP 9 |Use a single management pane such as Panorama or Strata Cloud Manager Managed Prisma
Access to manage your deployment for easier, more consistent security.
STEP 10 |Follow Administrative Access Best Practices to ensure least privilege access for Panorama
and firewall administrators.
STEP 11 |Day 1 Configurations, which are available on the Customer Support Portal (Tools > Run Day
1 Configuration) and require support login, are templates that provide a use-case agnostic
configuration model to start your path to least privilege access. Day 1 Configurations
help you implement basic network security best practices right away, including for critical
elements such as Dynamic Updates, Security profiles, logging, and more.
## Security Policy Best Practices7
## ©
## 2026 Palo Alto Networks, Inc.

## Security Policy Best Practices
## Deploy Security Policy Best Practices
Deploying Security policy best practices includes:
•Security Policy Rule Best Practices—Focuses on every aspect of Security policy rule
construction, from who can access what applications and resources in which way to applying
threat profiles that help safeguard traffic from malware.
•Security Policy Rulebase Best Practices—Focuses on the sequence of Security policy rules in
the rulebase and how that affects the traffic you allow and block.
•Policy Optimizer Best Practices—Focuses on using Policy Optimizer to tighten and maintain the
rulebase.
•App-ID Cloud Engine Best Practices—Focuses on how to use cloud App-IDs in Security policy
and how to automate adding new cloud App-IDs to the rulebase. (The App-ID Cloud Engine
requires a SaaS Security Inline subscription.)
•Policy Recommendation Best Practices—Focuses on SaaS Policy Recommendation and
IoT Policy Recommendation. (SaaS Policy Recommendation requires a SaaS Security Inline
subscription and IoT Policy Recommendation requires an IoT Security subscription.)
While planning and deploying, keep these principles in mind:
The principle of least privilege access; limit access to only the right people using only the right
applications, from only the right sources to the right destinations.
Follow Decryption Best Practices. Decrypt as much traffic as your business considerations,
local and privacy regulations, and legal compliance allow to gain maximum visibility into
traffic so that you can inspect and control it. For SSL Forward Proxy (outbound) decryption,
implement User-ID and URL Filtering first so you can target decryption effectively.
For outbound decryption, get an Advanced URL Filtering license so that when
decryption exposes a malicious website, URL Filtering can block access to it.
Some traffic cannot be decrypted for technical reasons due to pinned certificates,
client authentication, embedded certificates in IoT devices, etc.
Inspect all traffic in both directions for threats. Trust nothing implicitly.
Automate as much as possible to help ensure that Security policy stays up to date using
dynamic address groups (DAGs), external dynamic lists (EDLs), and VM monitoring features.
Use auto-tagging to automate security actions for users and devices based on log events. Auto-
tagging enables you to automate the actions to take when a log event happens, for example,
quarantining a potentially infected device or forcing a user to use MFA authentication.
## Security Policy Best Practices8
## ©
## 2026 Palo Alto Networks, Inc.

## Security Policy Best Practices
Avoid configuration bloat:
•Reuse objects such as Security profiles and profile groups, tags, application groups,
application filters, user groups, and address groups. On Panorama, use shared objects to
avoid configuring the same objects for multiple device groups.
•Before you add a new policy rule to the rulebase, check existing rules to see if you can add
new applications, users, or devices to existing rules instead of creating multiple similar rules.
See if an existing rule is the same except for one of the following objects: source zone,
destination zone, source IP address, destination IP address, application, service port, or user.
If only one of those objects is different, add the new object to the existing rule instead of
creating a new rule.
For example, you want to allow a new accounting application. When you look at the existing
rulebase, you find a rule for a different accounting application that allows access from the
same source to the same destination, for the same user groups, using the application’s
default port. Instead of writing a new rule for the new application, simply add the new
application to the existing rule.
This method also works well for consolidating existing rules.
•For outbound traffic, create one rule based on URL categories for multiple applications that
require the same security treatment. For example, to allow all low-risk financial services
traffic (assuming you want to inspect and log the traffic the same way), create an allow rule
that specifies both the financial-services and low-risk URL categories.
•Use Policy Optimizer to remove unused rules.
Use Panorama or Strata Cloud Manager Managed Prisma Access to manage firewall
deployments so that you can use device groups to apply consistent Security policy to single or
groups of firewalls.
Use pre-rules and post-rules appropriately:
•Pre-rules—Firewalls evaluate pre-rules before locally-defined rules and post-rules. (Locally-
defined rules on individual firewalls apply only to those firewalls.) Place policies that apply
to all firewall deployments in the pre-rules, such as allowing DNS and other critical services
and using the pre-defined threat EDLs to block known malicious and high-risk IP addresses.
•Post-rules—Firewalls evaluate these rules after pre-rules and locally-defined rules.
In Panorama Security policy rules, use the Target tab to exclude specific firewalls
or device group subsets from the rule (Target to all but these specified devices).
This enables you to create one broad rule higher in the hierarchy instead of creating
multiple similar rules lower in the hierarchy to make the exception.
Application override policy is not the same as layer 7 Security policy. Don’t use it unless you
must because Application Override removes many security controls that are inherent to the
Palo Alto Networks platform. Application Override doesn’t enable you to inspect layer 7 traffic,
use Security profiles to protect traffic against threats, or use App-ID, so it increases risk. In
most cases, it’s better to create a Custom Application or use a custom service timeout than to
use Application Override.
Review your existing rulebase. If you have Application Override rules for traffic other than
SMB or SIP, convert the rule to an App-ID based rule so that you can decrypt and inspect the
## Security Policy Best Practices9
## ©
## 2026 Palo Alto Networks, Inc.

## Security Policy Best Practices
traffic at layer 7 and prevent threats. If the rule is for SMB or SIP traffic, ensure that it follows
the principle of least privilege access and is as restrictive as possible.
## Security Policy Rule Best Practices
This section covers Security policy rule construction, from who can access what applications and
resources in which way to applying threat profiles that help safeguard traffic from malware.
Security policy rules define traffic matching criteria, including applications, users, devices, source
and destination, URLs, and services (ports). Combining matching criteria adds more granular
context to a rule, narrows the scope of the rule, and reduces the attack surface. The matching
criteria enable you to define the exact traffic you want to control with the rule and to adhere to
Zero Trust Network Access (ZTNA) principles.
Security policy rules also define actions to take on traffic that matches a rule’s criteria, including
whether to allow or deny the traffic, logging and log forwarding, threat inspection, and scheduling.
Create Security policy rules that are as specific as possible to apply the principle of least privilege
access and to segment the network.
•Critical Concepts for Security Policy—How Security policy rules work.
•Rule Name, Description, Audit Comments, and Tags—Best practices for managing Security
policy rules.
•Sources and Destinations—Best practices for applying the principle of least privilege access to
lock down traffic sources and destinations.
•Applications and Services—Best practices for adding applications to rules.
•Website Access (URL Filtering)—Best practices for how to allow user access to external
websites.
•Policy Actions and Other Settings—Best practices for how to allow or deny traffic and for
applying QoS.
•Logging and Log Forwarding—Best practices for logging traffic and forwarding logs for long-
term storage and analysis.
•Security Profiles—Best practices for applying Security profiles to Security policy rules.
Critical Concepts for Security Policy
To create effective Security policy, it helps to understand critical concepts about what Security
policy rules do, how they work in the Security policy rulebase, how traffic matches rules, and best
practices for rule construction.
•Decrypt all the traffic that local regulations, compliance, business requirements, and privacy
considerations allow. For SSL Forward Proxy (outbound) decryption, implement User-ID
and URL Filtering first so you can target decryption effectively. Decrypting traffic provides
visibility so the firewall can identify functional applications (for example, not just facebook but
facebook-post, facebook-download, facebook-file-sharing, etc.), identify websites, and apply
threat profiles to inspect and prevent threats in the traffic. Decrypting traffic enables you to
get the most protection and prevention from your threat subscriptions.
•Allow vs. block rules—Security policy on Palo Alto Networks firewalls is based on explicitly
allowing traffic in policy rules and denying all traffic that you don’t explicitly allow (allow
list). Traffic that you don’t explicitly allow is implicitly denied. The goal is to allow only
## Security Policy Best Practices10
## ©
## 2026 Palo Alto Networks, Inc.

## Security Policy Best Practices
the applications, users, and devices that you want on your network and let the firewall
automatically block what you don’t want.
As you move toward allow list based Security policy, use block rules to prevent access to risky
IP addresses, websites, and applications. Create and test block rules based on the pre-defined
External Dynamic Lists (EDLs) to block bulletproof IP addresses, high-risk IP addresses, and
known malicious IP addresses lurking within otherwise benign application categories and to
prevent authenticating to a malicious URL or domain. Use Advanced URL Filtering to block
access to risky websites.
Be particularly careful with file sharing applications because bad actors can use them
to exfiltrate data. Block most file sharing applications. For file sharing applications that
you need for business purposes, allow access only to users who need those applications
for business purposes.
For the tightest security, allow only applications used for business purposes. However,
most enterprises need to allow some non-business applications for employees (tolerated
applications). Consider which tolerated applications to allow and ask yourself if those
applications pose any threat to the organization, such as the ability to upload or download data.
Decrypt and inspect as much traffic as you can for threats.
•Security policy rules are specific. If traffic doesn't match every criteria specified in a Security
policy rule, the traffic does not match the rule. For example, if a rule specifies a particular user,
an application, and a source and destination, the traffic must match all of those criteria to
match the rule. If the user, source, and destination match but the application does not match,
then the traffic doesn’t match the rule.
•Security policy rules segment your network by defining who has access to which applications
and infrastructure. Rules segment the network by defining the source, destination, user, device,
service, and URL.
•Security policy rules apply all attached Threat Prevention profiles to traffic that matches the
rules.
•Security policy rules are in an ordered rulebase (you choose the order of the rules). Firewalls
compare traffic to Security policy rules starting with the first rule in the Security policy
rulebase and move through to the last rule in the rulebase. When traffic matches a rule’s
criteria, the firewall takes the rule’s Action on the traffic, and doesn't compare the traffic to any
other rules. If no rule matches the traffic, the firewall drops the traffic (implicit deny).
•Place more specific, granular Security policy rules above general rules in the rulebase to avoid
shadowing a rule. Shadowing is when a broad rule that includes the same matching criteria as
a more specific rule is placed higher in the rulebase than the specific rule. In that case, traffic
intended to match the specific rule instead matches the general rule first.
•If traffic matches no other rules, two default Security policy rules at the bottom of the rulebase
automatically drop all traffic between different zones (interzone-default) and automatically
allow all traffic between the same zone (intrazone-default). You can modify the interzone-
default and intrazone-default rules to log traffic, apply threat inspection, etc. If you add a rule
that denies all traffic earlier in the rulebase (local firewall rules or Panorama pre- and post-
rules), no traffic matches the default rules.
## Security Policy Best Practices11
## ©
## 2026 Palo Alto Networks, Inc.

## Security Policy Best Practices
•Apply the principle of least privilege access to Security policy rule construction (be granular,
precise):
•Control which administrators have access to administer which portions of which firewall and
Panorama devices. Follow best practices for securing administrative access.
•Identify all users (no unknown users should be on your network), identify the applications
you want to allow on your network, and know your infrastructure (resources that users
and applications access). Map who needs access to which applications and resources for
business purposes so that your Security policy rules allow no unnecessary access. Allow
access to business resources and sanctioned applications only to users who need access for
business purposes, and allow only the minimum required access.
•Allow access to non-business applications that you tolerate for the benefit of your
employees.
•In most cases, use allow rules instead of block rules—it’s more accurate and easier to define
what you want to allow on your network and implicitly deny the rest than it is to explicitly
block the ever-increasing number of applications that you don’t want on your network.
•Optimize the rulebase to edit rules with unused applications and to remove or disable rules
that aren’t used.
Rule Name, Description, Audit Comments, and Tags
The Name, Description, Audit Comments, and Tags fields make it easier to manage and navigate
your Security policy rulebase and to understand what each rule does. They also help new and
experienced administrators understand when to add a new application, user, or user group to an
existing rule and when to create a new rule.
STEP 1 |Name—Identifies what each rule does.
Develop a standard naming convention which uses terms that make it easy to search the
rulebase. Names that clearly show administrators what each rule does make it easier to
understand the traffic that each rule controls and makes searching for any particular rule easier
and more intuitive.
STEP 2 |Description—Describes the purpose of the rule so that anyone examining the rulebase can
understand why the rule was created and the intended result.
To ensure all policies have a description in PAN-OS and Panorama Managed Prisma Access,
enable Require description on policies in Panorama > Setup > Management > Policy Rulebase
Settings (Device > Setup > Management > Policy Rulebase Settings on individual firewalls).
For existing rules without a description, add one next time you edit the rule.
In Strata Cloud Manager Managed Prisma Access, ensure that administrators enter a
description.
STEP 3 |Tags—High-level descriptors to describe flow-based components, application-based policy,
internal services, particular user groups—whatever makes sense for your business.
Tags organize policies into groups, which enables you to filter and search for policies based on
tags.
For example, if you create a Tag called disabled and apply it to all disabled rules, you can
filter the rulebase and see all disabled rules based on that tag. Using the same tag, you can
## Security Policy Best Practices12
## ©
## 2026 Palo Alto Networks, Inc.

## Security Policy Best Practices
search the rulebase for rules that are labeled disabled but have been reactivated by filtering
for the disabled tag and disabled eq no.
To ensure that all policies have a tag in PAN-OS and Panorama Managed Prisma Access,
enable Require Tag on policies in Panorama > Setup > Management > Policy Rulebase
Settings (Device > Setup > Management > Policy Rulebase Settings on individual firewalls).
For existing rules without a tag, add one next time you edit the rule.
STEP 4 |Prevent administrators from committing policies if they have no tags or description.
In PAN-OS and Panorama Managed Prisma Access, enable Fail commit if policies have no
tags or description in Panorama > Setup > Management > Policy Rulebase Settings (Device >
Setup > Management > Policy Rulebase Settings on individual firewalls). For existing rules, the
commit fails if you don’t add a tag and description the next time you edit the rule.
STEP 5 |Audit Comments—Tracks changes to rules and why changes were made so that you have a
history of rule changes and rationales for the changes. This is especially useful to document
rules that are only used in case of disaster recovery or on a limited basis.
In PAN-OS and Panorama Managed Prisma Access, ensure that all policies include audit
comments, enable Require audit comment on policies in Panorama > Setup > Management
> Policy Rulebase Settings (Device > Setup > Management > Policy Rulebase Settings on
individual firewalls) and specify an audit comment format. For existing rules without audit
comments, you must add them next time you edit the rule.
Audit comments stay with the rule permanently. Click Audit Comment Archive in the rule to
view the history, which can’t be deleted.
Sources and Destinations
Controlling traffic sources and destinations is about following the principle of least privilege
access. Create Security policy rules that specify the exact source and destination for application
traffic that you want to match the rule. Allowing traffic on the rule from sources and destinations
that applications don’t require for business purposes increases the attack surface, which increases
risk. Strictly limiting sources and destinations to those required for business purposes reduces the
attack surfaces and decreases risk.
Granular source and destination control helps you implement least privilege access:
•Sources—Zones, addresses, users, and devices, 5G Security, subscribers, equipment, and
network slice.
•Destinations—Zones, addresses, and devices.
As much as possible, use address group and user group objects instead of individual addresses and
users to reduce the number of source and destination objects. This simplifies policy and makes it
easier to understand. Limit the total number of source and destination objects for rulebase clarity.
## Security Policy Best Practices13
## ©
## 2026 Palo Alto Networks, Inc.

## Security Policy Best Practices
STEP 1 |In PAN-OS, specify source and destination zones as narrowly as possible to prevent
unnecessary access to data and applications.
Dedicating zones for particular purposes, such as a zone for all web servers, makes it easier to
create granular policy because all of the servers in the zone usually require the same security
policy.
Panorama Managed Prisma Access uses two zones, trust and untrust. Map Panorama
zones to the Prisma Access trust or Prisma Access untrust zone.
Strata Cloud Manager Managed Prisma Access uses three zones: trust, untrust, and
clientless VPN, which is mapped to the trust zone by default. In many third-party SD-
WAN integrations, in the Log Viewer, the source zone uses the name of the remote
network.
STEP 2 |Specify source and destination addresses as narrowly as possible to prevent unnecessary
access to data and applications. Use address groups instead of individual addresses as much
as possible to simplify policy. If the rule is for all of the devices in a zone, for inbound traffic
specify the destination address as any and for outbound traffic specify the source address as
any.
•Use FQDN address objects to reference internal systems so that when system IP addresses
change, the change doesn’t affect policy.
•Use Dynamic Address Groups (DAGs) in policy to adapt automatically to changes in server
roles or in security posture based on log events and auto-tagging. Think about how to group
servers and develop a tagging strategy that makes sense for your business.
When a specified log event occurs, the firewall moves IP addresses from one DAG to
another DAG based on auto-tagging. DAGs are updated automatically and don’t require
a commit action. This enables you to take automated security actions such as moving a
potentially infected server or endpoint from a DAG in a policy rule that allows access to
critical resources to a DAG in a policy rule that blocks that access (quarantining a device).
•In data center environments with automation, use DAGs to control access for VMs as the
data center spins up and spins down virtualized servers. Dynamically register tags using the
native XML API or the VM Monitoring agent on the firewall.
•In data center environments, segmentation combined with automation might make it
difficult to manage individual IP addresses. As a last resort if the environment is too difficult
to manage, use subnets, but this is a less secure method.
•Use Palo Alto Networks predefined External Dynamic Lists (EDLs) as the source or
destination to block traffic to and from high-risk, bulletproof, and other malicious IP
addresses.
•If compliance, business policy, or other reasons require you to block geographic regions,
specify the region or regions as the address. (For inbound traffic, specify the geographical
region as the source and any as the destination. For outbound traffic, specify any as the
source and the geographical region as the destination.)
## Security Policy Best Practices14
## ©
## 2026 Palo Alto Networks, Inc.

## Security Policy Best Practices
STEP 3 |Specify source users with User-ID so that Security policy is valid for both on-premises and
remote access. Consistent user identification is critical to ensure consistent policy regardless
of user location and method of connectivity.
•Create user groups based on the context what does the user need to do for business purposes
—what are the common access requirements? This viewpoint groups users by resources they
need to access and applications they need to use so you can create logical groups and apply
policy to them.
Have the network security team work with the team that controls user groups to
help ensure that the groupings make sense for security controls.
Specify individual users in policy only when you can’t use groups. For example, your CEO
and few other C-suite executives might require various access privileges that other users
and groups should not have.
•If your deployment allows it, use the Cloud Identity Engine (CIE) to:
•Aggregate all User-ID sources across your network, both cloud and on-premises.
•Synchronize the directory sources.
•Provide consistent User-ID information across the network.
Consistent User-ID enables policy to follow users everywhere in the network.
CIE provides authentication via integration with Identity Providers such as Okta,
Azure AD, and many others.
•GlobalProtect is the User-ID mapping source with the most accurate and comprehensive
user information and greatest accuracy (there are also many other possible User-ID
mapping sources).
•Use Dynamic User Groups (DUGs) in policy to automatically remediate anomalous user
behavior and malicious activity based on log events and auto-tagging. DUGs work similarly
to DAGs. Think about what activities warrant quarantining or restricted access and develop
a tagging strategy that makes sense for your business.
Also use DUGs to allow periodic access to user groups. For example, a DUG can allow
access for quarterly auditors (as defined by a user group for auditors) during audits and
block access at all other times.
•In Security policy rule configuration, in addition to specifying particular users and groups,
you can specify whether the rule applies to any user, pre-logon users, known-user
(authenticated), or unknown (not authenticated) users:
•Use any for rules that apply to all network users, for example, access to basic services
such as DNS, NTP, OCSP, etc.
•Allow no unknown users on your network. Create a rule to block unknown users.
Alternatively, use unknown for guest access providing that you allow no access to your
corporate network.
•Remote Access VPN with Pre-Logon is specific to GlobalProtect users. It establishes a
VPN tunnel before the user logs in to the device to authenticate the endpoint and enable
access to specific services such as DHCP, DNS, etc., and requires installing machine
certificates on each endpoint. Policy rules that allow pre-logon user access must allow
## Security Policy Best Practices15
## ©
## 2026 Palo Alto Networks, Inc.

## Security Policy Best Practices
access only to services for machine authentication and necessary network services. Deny
all other access for pre-logon users.
The overarching principle is least privilege access. Allow access only to users and
groups that require access to applications and resources for business purposes.
•Follow User-ID best practices.
STEP 4 |In Security policy rules that govern IoT devices (IoT Security requires a subscription), specify
IoT devices using Device-ID (PAN-OS 10.0 and later).
Device objects define the Device-IDs of IoT devices and identify source devices in the same
way User-ID identifies source users. Device objects have six metrics to use as match criteria. A
device must match all of the configured metrics to match a Device-ID. In most cases, defining
one or two metrics is sufficient. The more metrics you define, the greater the chances that
the filter is too specific and won’t match the devices you want to match. Understand what
information devices send to the firewall to know which metrics to configure to define the
device object (not all devices transmit all metrics). The following operational commands show
the information that IoT devices send to the firewall:
•> show iot ip-device-mapping-mp all—View all IP address-to-device mappings
on the firewall.
•> show iot ip-device-mapping-mp ip <ip-address>—View the IP address-to-
device mapping for a specified IP address.
Follow IoT Security best practices.
Applications and Services
By default, an implicit deny rule at the bottom of the Security policy rulebase blocks applications
that you don’t explicitly allow in a Security policy rule. To enforce least privilege access, refine
Security policy rules until they specify only the exact applications you want to allow for business
purposes (sanctioned applications) and for your employees (tolerated applications). Application-
based rules provide granular control of who uses each functional application and how they use it,
so you can create precise Security policy rules as you move toward a Zero Trust Network Access
environment. Port-based rules allow any application on the open port; avoid them.
You must enable decryption for the firewall to see the functional application instead
of just the “-base” application. Seeing the functional application enables you to control
applications granularly. For example, instead of seeing just the container application
“facebook”, the firewall can see “facebook-posting”, “facebook-downloading”, “facebook-
file-sharing”, etc. This enables you to configure Security policy based on least privilege
access; instead of giving all employees access to all facebook functional applications, you
can restrict or block access to specific functional applications for appropriate users.
When you add a container application to a rule, all of its functional applications are added
to the rule implicitly. Specify the exact functional applications you want to allow to gain
more granular control of the applications you allow and who you allow to use them.
How you apply best practices advice for applications depends on whether your environment is
new, existing, or a migration. Many of the recommendations reflect the final best practices state.
In some cases, we provide transition advice or advice about different environments. However,
every environment is unique. The goal is to understand what applications traverse your network,
## Security Policy Best Practices16
## ©
## 2026 Palo Alto Networks, Inc.

## Security Policy Best Practices
what sanctioned and tolerated applications you want to traverse your network, and to use that
information to transition safely to a Security policy rulebase that allows only the applications you
sanction for business purposes and tolerate for employee access.
Security Policy Rulebase Best Practices covers where to position rules in the Security
policy rulebase.
1.Use application groups as much as possible to simplify and tighten Security policy rule creation
and reduce the size of the rulebase.
Application groups are user-defined sets of applications that require similar security treatment.
Adding an application group to a Security policy rule enables you to control multiple
applications with one rule instead of creating a separate rule for each application. If you
need to add an application to the group or make any other changes, you only have to make
the change once instead of making the change in every rule because when you update an
application group, the rules that reference it are automatically updated.
2.Whether you are adding applications to an application group or to an individual Security policy
rule, specify the exact functional applications you want unless you’re using a group to block
a container application (which blocks all of its functional applications) or you want to allow
access to all of a container application’s functional applications.
3.Application dependencies occur when an application needs other applications (dependent
applications) to work properly. Application dependencies only matter for applications that you
allow, not for applications that you block. There are two types of dependent applications:
•Explicit applications, which the firewall shows you when you add an application to the
rule and which you add manually so that the application works properly. For example, the
facebook-chat application depends on adding the facebook-base and mqtt-base applications
manually.
•Implicit applications, which the firewall automatically allows to support the specified
application and which you don’t need to explicitly add to a rule. For example, in addition
to the explicit applications required for facebook-chat to work properly, when you add
facebook-chat to a rule the firewall automatically allows the applications jabber and web-
## Security Policy Best Practices17
## ©
## 2026 Palo Alto Networks, Inc.

## Security Policy Best Practices
browsing. (Unless you explicitly add them to a rule, jabber and web-browsing aren’t allowed
for all traffic, just for the facebook-chat traffic.)
Be aware of which applications you allow implicitly when you allow an application.
You can see an application’s dependencies in several ways:
•The Applications object provides a searchable database of applications. Select an
application to see its explicit application dependencies (Depends on) and its implicit
application dependencies (Implicitly Uses).
•Palo Alto Networks applipedia is a searchable database of content-delivered App-IDs.
Search and select an application to see its explicit application dependencies (Depends on
Applications) and its implicit application dependencies (Implicit use Applications).
•When you add an application to a Security policy rule, the firewall shows you the explicit
dependent applications but not the implicit dependent applications.
•Commit Validate to see application dependencies based on the entire Security policy
rulebase instead of on just one rule.
Each network environment and business is different, so how to handle applications
dependencies is not a one-size-fits-all recommendation. There are two ways to approach
application dependencies, depending on your business and security requirements:
•Focus on availability—Add all of the dependent applications shown in a Security policy rule
to the rule to ensure that the application functions properly. For example, for the rule that
controls facebook-chat, add facebook-base and mqtt-base to the rule.
However, this might result in some common dependent applications, such as ssl, being
added to many rules instead of just to one rule, which adds clutter to the rulebase. (Even
if the rulebase already allows ssl, ssl appears as a dependent application for many other
applications.) A good way to mitigate this is to use Policy Optimizer to remove duplicate
occurrences of dependent applications.
•Focus on security—To allow as few applications as possible, run a Commit Validate to see
all of the application dependencies in the Security policy rulebase. Add the dependencies
you need based on the Commit Validate output. Consider creating application groups for
different sets of application dependencies (e.g., VMware dependencies, software update
dependencies, etc.) that contain all of the dependent applications you want to allow so that
you can control access based on users.
4.In new and existing deployments, block known malicious and risky traffic immediately.
•Block potentially malicious traffic based on trusted threat intelligence sources, including
Palo Alto Networks built-in External Dynamic Lists (EDLs), which require an Advanced
Threat Prevention or Threat Prevention subscription and block bulletproof IP addresses,
high-risk IP addresses, known malicious IP addresses, and IP addresses known as Tor exit
nodes.
•Block encrypted DNS to maintain visibility into the traffic and to inspect the traffic for
threats using Threat profiles. Attackers use DNS for many types of attacks, so you must
inspect DNS traffic. Block both DNS-over-HTTPS (DoH) and DNS-over-TLS (DoT), and use
## Security Policy Best Practices18
## ©
## 2026 Palo Alto Networks, Inc.

## Security Policy Best Practices
the Palo Alto Networks DNS Service. If you can’t block encrypted DNS immediately, gain
visibility into the traffic and transition to blocking DoH and (DoT) traffic.
Because of App-ID’s granularity, you can allow regular DNS traffic in one rule and
block DoT and DoH traffic in another rule because each has a different App-ID that
you can specify in a Security policy rule.
•Bad actors often use file sharing applications to exfiltrate data. Block most file sharing
applications and allow access to business file sharing applications only to users who need
those applications for business purposes. An easy way to accomplish this is to create a
rule that specifies the users and has an application filter that includes the subcategory file-
sharing and/or the tag Uploading.
Constructing allow-list based Security policy implicitly blocks most unwanted applications,
so you don’t need many block rules. Base what you block on your business requirements by
allowing only the application traffic that you want on your network and by thinking about who
needs to use each application.
5.Set the Service to application-default in most cases. Because App-ID is based on signatures
instead of port and protocol (which can be spoofed), App-ID is very accurate, so you don’t need
to specify the port. Using application default prevents any application except the legitimate
application from using the port and stops evasive applications from using non-standard ports.
If in the future the default port for the application changes, application-default automatically
applies the new port so you don’t have to reconfigure service port settings.
Only specify service ports if you have a custom application, special architectural requirements,
or if your company security requirements demand it.
6.For internal applications and applications for which there is no App-ID, create custom
applications to gain layer 7 visibility into traffic. Don’t use Application Override policy because
it bypasses layer 7 processing and threat inspection. The use cases for Application Override are
unusual situations with SMB or SIP traffic.
7.Use application filters to discover traffic on your network and to handle new applications.
Application filters are dynamic sets of applications. Applications match application filters based
on attributes that you define, such as category, subcategory, risk, tags (pre-defined tags or
custom tags), and characteristics. The firewall automatically adds new applications to a filter
when they match the filter criteria. Security policy rules with an application filter automatically
control new applications that match the filter.
Application filters are looser controls than application groups. You control exactly which
applications are in an application group. The attributes you define control which applications
are in an application filter, which can lead to broader membership and allowing more
## Security Policy Best Practices19
## ©
## 2026 Palo Alto Networks, Inc.

## Security Policy Best Practices
applications than you need to allow. That’s why they’re best for discovering traffic so that you
can control it.
Use cases include:
•In new deployments where you’re not yet familiar with the traffic, use application filters to
analyze different categories and subcategories of traffic so you can discover which of those
types of applications are on your network.
You can create application filters to discover traffic of different types in mature
deployments as well.
•Filtering the rulebase for new applications. Create a filter that matches new applications and
place the rule near the top of the rulebase. Use Policy Optimizer to gain visibility into the
applications and control them.
Content updates control new applications. When an Applications content update is
released, the new applications are seen as new until the next Applications content
update is released. Releases normally occur on or around the third Tuesday of each
month. After the next set of new applications are released, the previous set of new
applications is no longer seen as new, and the application filter no longer matches
them. Follow Best Practices for Applications and Threats Content Updates and
decide how to handle the new applications before the next Applications content
update .
•In migration scenarios, use application filters to block or allow broad ranges of specific
application types and then use Policy Optimizer to narrow them down to only the
applications you want on the network. Application filters also enable you to ensure that
certain types of new applications are allowed automatically when they match a filter.
•Future-proof rules by handling new applications automatically when they match a filter. This
is useful both in the application discovery phase in migrations and new deployments, and in
mature environments.
For example, create an allow rule with an application filter based on the Palo Alto Networks
tag. This ensures that you allow all current Palo Alto Networks applications and all future
Palo Alto Networks applications.
Another example is creating a rule that filters for new content-delivered App-IDs to safely
handle them until you can examine them more closely.
8.Application definitions are not static. Applications content updates can change an application’s
definition and therefore how the rules treat the application. Follow best practices for
Applications Content Updates to ensure that you have the time to make any necessary
changes due to the update.
Website Access (URL Filtering)
Advanced URL Filtering requires a license. Use Advanced URL Filtering with PAN-OS, Prisma
Access (usually included with the Prisma Access license), and Cloud NGFW for AWS.
URL Filtering based on website categories simplifies outbound Security policy and protects
you from malicious websites. Each URL category defines a group of sites that have the same
type of content, for example, health-and-medicine, games, or hacking sites. There are also
three categories that define the relative risk level of sites within a particular category: low-risk,
## Security Policy Best Practices20
## ©
## 2026 Palo Alto Networks, Inc.

## Security Policy Best Practices
medium-risk, and high-risk. Combining a category with a risk level enables you to create Security
policy rules that block or allow traffic based on risk within a URL category.
You must enable decryption to take advantage of URL Filtering because you must
decrypt traffic to reveal the exact URL so the firewall can take the appropriate action. At
the least, decrypt high- and medium-risk traffic.
STEP 1 |Target traffic to decrypt based on URL categories because URL categories enable you to
easily identify risky traffic.
Decrypt the riskiest URL categories first and decrypt more traffic as you gain experience.
STEP 2 |In Security policy rules that control outbound internet traffic:
•Attach URL Filtering profiles to simplify Security policy. Configure a best practices URL
Filtering profile that blocks all categories of malicious websites (for both Site Access and
User Credential Submission) and alerts on all other categories, and attach it to all rules that
allow web access.
•Control traffic that you can’t decrypt for legal, compliance, business, privacy, regulatory,
or other reasons with URL categories. For example, create a Security policy rule, with the
appropriate users and applications, that specifies the appropriate categories as match
criteria and don’t decrypt traffic that matches the rule.
•Configure custom URL categories so that you can create exceptions to URL Filtering based
Security policy rules. Add the custom URL category to a URL Filtering profile and attach it
to the appropriate Security policy rule or use custom categories as match criteria in Security
policy. Exceptions enable you to block access to URL categories for most users but allow
them for specific users such as PEN testers and infosec, block an entire category such as
social networking but allow access to LinkedIn, or control what to decrypt. For example:
•Combine a URL category with a risk-based category as match criteria to block or allow a
URL category’s traffic based on risk. For example, to block access to risky finance sites,
create a Security policy rule that specifies both the financial-services URL category and
the high-risk category as match criteria and set the rule Action to Deny. Place this rule
above rules that allow access to the financial-services URL category so that the firewall
blocks high-risk sites before allowing access to the medium- and low-risk sites.
•If firewall resource availability prevents you from decrypting all the traffic that you can
decrypt legally and for business purposes, use custom URL categories to create Security
policy rules with matching low-risk traffic for which there is little value in decryption. For
example, to bypass decryption for low-risk streaming services, create a Security policy
rule that specifies both the streaming-media URL category and the low-risk category
as match criteria and set the rule Action to Allow. If the traffic uses TLSv1.2 or earlier,
create a No Decryption policy and profile for the traffic to block bad sessions. If the
traffic uses TLSv1.3 or later, don’t create a No Decryption policy and profile for the
traffic.
•Set the source zone in the Security policy rule to a protected internal network (trust zone).
Do not specify an external zone or any zone as the source because you apply URL Filtering
only to outbound traffic. (Applying URL Filtering to inbound traffic can even lead to DoS
attacks.)
## Security Policy Best Practices21
## ©
## 2026 Palo Alto Networks, Inc.

## Security Policy Best Practices
STEP 3 |To transition URL Filtering profiles safely to best practice settings and create best practices
URL Filtering profiles:
1.Clone the default URL Filtering profile (named default) and edit it.
2.Rename the profile appropriately (e.g., Best Practices URL Filtering Profile).
3.Set all actions for URL categories to alert for both Site Access and User Credential
Submission. (The default allow action does not generate logs.) You must manually set URL
categories to alert to generate logs and gain visibility into the traffic.
When a new category is added to URL Filtering, by default, the category is set to
allow Site Access and User Credential Submission. Manually set new categories to
alert on Site Access and User Credential Submission to get their URL Filtering logs.
Also update custom URL categories accordingly.
4.Set all actions for malicious URL categories to block both Site Access and User Credential
Submission. Make appropriate exceptions for PEN testing, threat research, and infosec as
needed:
•command-and-control—URLs and domains that malware or compromised systems use to
communicate with an attacker’s remote server.
•grayware—These sites don’t meet the definition of a virus or pose a direct security
threat, but they influence users to grant remote access or perform other unauthorized
actions. Grayware sites include scams, illegal activities, criminal activities, adware, and
other unwanted and unsolicited applications, including “typosquatting” domains.
•malware—Sites known to host malware or used for command-and-control activities.
•phishing—Sites known to host credential and personal information phishing pages,
including technical support scams and scareware.
•ransomware—Sites that are known to distribute ransomware.
•scanning-activity—Probing for existing vulnerabilities or conducting targeted attacks.
5.Some URL categories have the strong potential to be malicious but are not definitely
malicious. Set all actions for these URL categories to block both Site Access and User
## Security Policy Best Practices22
## ©
## 2026 Palo Alto Networks, Inc.

## Security Policy Best Practices
Credential Submission. Make appropriate exceptions for PEN testing, threat research, and
infosec as needed:
•dynamic-dns—Systems with dynamically assigned IP addresses that are often used to
deliver malware payloads or command-and-control malware.
•hacking—Sites relating to illegal or questionable access to or use of equipment and
software. Includes sites that facilitate the bypass of licensing and digital rights systems.
Make exceptions to this category for the appropriate PEN testing and threat
research users.
•insufficient-content—Websites and services that present test pages, no content,
provide API access not intended for end-user display, or require authentication without
displaying any other content.
•newly-registered-domains—Domains that domain generation algorithms often generate
or bad actors generate for malicious activity.
•not-resolved—If the PAN-DB cloud is unreachable and the URL is not in the firewall’s
URL Filtering cache, the firewall cannot the resolve and identify the URL category.
For highest security, enable Hold client request for category lookup to give the
firewall more time to resolve the URL category. This extends the time the firewall
has to query the category type from the cloud and results in better security but
might increase latency.
•parked—Domains that will often be used for credential phishing or personal information
theft.
•proxy-avoidance-and-anonymizers—URLs and services often used to bypass content
filtering products.
•unknown—Sites not yet identified by Palo Alto Networks (PAN-DB).
PAN-DB real-time updates learn unknown sites after the first attempt to access
an unknown site, so the firewall identifies unknown URLs quickly and then
handles them based on the actual URL category of the site.
If availability is critical to your business and you must allow traffic from
unknown sites, apply the strictest Security profiles to the traffic and investigate
all alerts for the traffic.
6.Set the action for Site Access and User Credential Submission to block the following URL
categories based on legal or business requirements and potential liability risk. If you don’t
block these sites, alert on and apply strict Security profiles to the traffic.
•abused-drugs—Sites that promote illegal and legal drug abuse.
•adult—All sites that contain adult content of any kind, including games and comics as well
as sexually explicit material, media, art, forums, and services.
•copyright-infringement—Domains with illegal content that poses a liability risk.
•extremism—Websites promoting terrorism, racism, child exploitation, etc.
•gambling—Lottery and gambling sites.
## Security Policy Best Practices23
## ©
## 2026 Palo Alto Networks, Inc.

## Security Policy Best Practices
•peer-to-peer—Peer-to-peer sharing of torrents, download programs, media files, or other
software applications. (Does not include shareware or freeware sites.)
•questionable—Sites that promote tasteless humor, offensive content targeting specific
demographics.
•weapons—Sale, review, descriptions of, or instructions regarding weapons and their use.
Also consider how you want to handle the cryptocurrency and alcohol-and-tobacco URL
categories. Either alert on them and apply strict Security profiles to the traffic or block
them, depending on your business needs.
7.Block User Credential Submission for the high-risk category. (Do not block Site Access for
the high-risk category.)
8.For the URL Filtering Settings in the URL Filtering profile:
•Disable Log Container Page Only, which is enabled by default. If you only log container
pages, you lose visibility into functional applications such as posting, uploading,
downloading, etc. Disable Log Container Page Only to see the complete log so that you
see the real functional application.
•If your environment is a school that takes federal funding, enable Safe Search
Enforcement (legal requirement).
9.Enable User Credential Detection (requires configuring and enabling User-ID).
STEP 4 |Apply URL Filtering to Security policy rules with DNS Sinkhole configured in the Anti-
Spyware Security profile (requires an Advanced Threat Protection or active legacy Threat
Protection subscription and a DNS Security subscription to use cloud-based DNS security) to
see which machines are infected and where they were trying to connect for DNS.
Policy Actions and Other Settings
Security policy actions specify whether to allow or block traffic, and how to block traffic you don’t
allow it. Quality of Service (QoS) controls bandwidth, if needed, to ensure that the traffic a rule
allows receives the appropriate bandwidth.
STEP 1 |Define an action for each Security policy rule.
•Allow only sanctioned and tolerated traffic. The more traffic you allow that doesn’t pertain
to your business, the greater the risk. The firewall blocks traffic that you don’t explicitly
allow in a Security policy rule.
•The more your Security policy rules follow the principle of least privilege access, the fewer
block rules you need. How to block traffic depends on how you want to respond to the
application that you’re blocking.
•Use Deny, which uses the application’s default action, unless you want the firewall to
respond to the application in a specific way by resetting the client, server, or both, or by
silently dropping the traffic.
•Use Drop when you want to deny service silently, without sending a reset response.
When you block clearly malicious traffic, such as when you block based on the
## Security Policy Best Practices24
## ©
## 2026 Palo Alto Networks, Inc.

## Security Policy Best Practices
predefined Palo Alto Networks EDLs, the Drop action prevents the malicious end of the
communication from knowing why it was blocked.
•If you have a use case for resetting only the client or only the server, ensure that you
understand the client-server directionality (which end of the communication initiates the
connection), which is based on the rule’s source and destination settings.
STEP 2 |If necessary, apply QoS to control bandwidth for certain applications.
QoS is optional. Understand the applications you want to prioritize for bandwidth and the
applications whose bandwidth you want to limit if you apply QoS to policy. For example,
during popular events such as the World Cup that use particular streaming applications, you
can allow employees to view the event using those applications and limit their bandwidth
to ensure that appropriate bandwidth is available for business activities. Another example is
when updates are released for popular applications, mass downloading can impact bandwidth
availability. To prevent that, apply QoS to limit the bandwidth available for that application’s
download traffic.
Logging and Log Forwarding
Logging and storing logs are critical for investigating incidents. Communicate with your:
•Security Operations Center (SOC) to ensure that you capture the right information to
investigate events if necessary.
•Audit compliance team to ensure that you capture the right information for audits and
compliance.
•Legal team to ensure that you don’t store cleartext or other data that violates local regulations,
compliance, business requirements, privacy, etc.
STEP 1 |Consider the log storage capacity you need now and in the future and size your log storage
capacity accordingly.
•Plan storage capacity so that you can retain logs long enough to investigate threats. The
length of time depends on your investigation procedures.
•Ensure that your SOC can ingest logs from wherever you store them. Strata Logging
Service centralizes log storage and analysis and provides a solution that scales with your log
volume.
•Don’t duplicate the same logs for storage in multiple places. Use either Strata Logging
Service or a separate storage space such as Log Collectors. When moving logs from one
storage space to another, don’t use duplication. Instead, prepare for and execute a hard
cutover instead.
If you enable duplicate log forwarding on firewalls or Panorama, System and
Configuration logs are not sent to Strata Logging Service so the Strata Logging
Service logs will be incomplete. For this reason, do not enable duplicate log
forwarding for log backup.
If you must split log storage, do it by separating log forwarding in a consistent
manner. For example, send all Prisma Access logs to Strata Logging Service and
send all firewall logs to Log Collectors.
## Security Policy Best Practices25
## ©
## 2026 Palo Alto Networks, Inc.

## Security Policy Best Practices
STEP 2 |Think about what you want to log, how you want to log it, and what you don’t want to log or
can’t log for compliance or storage space reasons.
For most applications, log all the information you can to help with Security Operating Center
(SOC) investigations. However, there are some applications and circumstances for which you
can’t take comprehensive logs:
•Assess whether the rule needs logging based on compliance, business requirements, audit
requirements such as ISO, privacy considerations (e.g., PII, GDPR), and SOC requirements.
Be careful about logging SSNs, credentials, PII, etc., in cleartext if applications don’t encrypt
that information.
•Basic services such as DNS, NTP, syslog, etc., create thousands of small sessions that result
in many unnecessary logs, which impacts log storage and makes investigating incidents
more difficult. For these services, configure only Threat log forwarding unless you have the
storage capacity to take other logs.
STEP 3 |In Security policy rules, log traffic at the end of the session instead of at the start to avoid
logging transient applications.
Log At Session Start also consumes more resources than logging only at the session end. In
most cases, you only Log At Session End. Enable both Log At Session Start and Log At Session
End only for troubleshooting why an application doesn't match a Security policy rule, to see
active long-lived tunnel sessions such as GRE tunnels (you can't see these sessions in the ACC
unless you log at the start of the session), and to gain visibility into Operational Technology/
Industrial Control Systems (OT/ICS) sessions, which are also long-lived sessions.
Policy Optimizer and the Cloud App-ID Engine (ACE) do not count rules that Log at
Session Start in their statistics.
STEP 4 |Log traffic that matches the intrazone-default rule, which allows all traffic within a zone by
default, and the interzone-deny rule, which blocks all traffic between zones that Security
policy rule doesn’t explicitly allow by default.
STEP 5 |Configure Log Forwarding profiles and assign them to Security policy rules to send logs to
the appropriate storage, such as Strata Logging Service or Log Collectors, and to alert the
appropriate administrators about events, especially critical, high, and medium threat events.
Strata Cloud Manager Managed Prisma Access forwards all logs to Strata Logging
## Service.
•Ensure that every Security policy rule has a Log Forwarding profile attached.
Create a basic default Log Forwarding profile for all new Security policy rules and name it
default and make sure it logs threats. Naming the profile default makes the firewall
apply it to all new Security policy rules automatically, so it ensures that all new rules have
Log Forwarding profiles.
It’s easier to replace or modify the profile for the few rules that require different logging
treatment, such as logs for traffic related to compliance, personal information, local
## Security Policy Best Practices26
## ©
## 2026 Palo Alto Networks, Inc.

## Security Policy Best Practices
regulations, business requirements, etc., or logs for common services such as DNS or NTP,
than it is to attach a Log Forwarding profile to every new rule individually.
For Security policy rules that govern IoT Security, use the IoT Security Default
Profile - EAL Enabled predefined Log Forwarding profile, which provides IoT
Security with all the log types it requires, including enhanced application logs.
•Use Log Forwarding for Security Services in Policy Optimizer to identify Security policy
rules that don’t have a Log Forwarding profile attached (select None in the filter). Add an
appropriate Log Forwarding profile to each rule that has none.
STEP 6 |For investigation purposes, ensure that you know the true source and destination of traffic,
not just the IP address of a proxy device such as a load balancer, NAT device, or malicious
DNS server that’s between the true source and the firewall. If there is a proxy device
between the firewall and the true source, depending on your network architecture and the
application:
•Place firewalls in front of load balancers to see the real source IP address.
•Take a pre-NAT Packet Capture by configuring a receive stage in the packet capture
settings.
•Apply a URL Filtering profile that enables logging the X-Forwarded-For (XFF) field field to
the Security policy rule (URL Filtering Settings tab in Objects > Profiles > URL Filtering).
The XFF field shows the original source IP address. The XFF log is in the URL Filtering Log.
## Security Profiles
Security profiles scan allowed traffic for threats such as viruses, malware, spyware, malicious file
types, and other known and unknown threats, and prevent those threats. Attach Security profiles
to Security policy rules that allow traffic to apply threat prevention to traffic that matches the
rule.
Use Day 1 Configurations for templates that provide use-case agnostic best practices Security
profiles to allowed traffic right way. Day 1 Configurations are available on the Customer Support
Portal (Tools > Run Day 1 Configuration) and require support login. From there, transition to best
practices threat blocking as described here.
To identify and prevent threats, the firewall must have visibility into application
traffic. Decrypt as much traffic as local regulations, business considerations, privacy
considerations, and technical ability allow. For SSL Forward Proxy (outbound) decryption,
implement User-ID and URL Filtering first so you can target decryption effectively. If
you don’t decrypt traffic, the firewall can’t analyze encrypted headers and payload
information.
Follow Threats Content Update best practices to ensure that your Security profile
signatures are up to date.
Get the Advanced Threat Prevention cloud service subscription to prevent threats including
unknown command-and-control and zero-day vulnerability threats in real time. Advanced Threat
Prevention is available for PAN-OS and for Prisma Access 3.2 Innovation and later Innovation
deployments. If you run an earlier version of Prisma Access, use the regular Threat Prevention
subscription.
## Security Policy Best Practices27
## ©
## 2026 Palo Alto Networks, Inc.

## Security Policy Best Practices
Air-gapped environments cannot use Advanced Threat Prevention because it’s a cloud
service and requires a cloud connection.
The best practice Security profile recommendations for Strata Cloud Manager
Managed Prisma Access differ slightly from the recommendations for PAN-OS and
Panorama Managed Prisma Access. In addition, in Strata Cloud Manager Managed Prisma
Access, you cannot apply individual Security profiles to Security policy rules, you can only
apply Profile Groups. Profile Groups include the Security profiles that you include in the
group.
Best practices advice focuses on what to do to be most secure, and that’s the ultimate goal for
your Security profiles. However, to ensure the availability of business-critical applications, start by
blocking known malicious traffic and alerting on most other traffic. Follow best practice Security
profile transition advice to move safely from alerting to best practice Security profiles that block
traffic and exercise caution when moving from alert to blocking to avoid impacting business-
critical applications.
The time to transition a Security profile setting from alert to block is when you’re
confident that the profile is appropriately tuned, you’ve made any necessary exceptions,
and you won’t inadvertently trigger a signature that blocks a business-critical application.
This streamlined section shows you the best practice settings. Create Best Practice Security
Profiles provides more in-depth information about the reasons for the settings.
•Antivirus profile (includes WildFire signature and inline machine learning actions)
•Anti-Spyware profile (includes DNS Policies/sinkholing and inline cloud analysis)
To provide comprehensive coverage, get an Advanced URL Filtering subscription and
a DNS Security subscription to gain visibility into and protect against malicious URLs,
domains, and abuses of the DNS protocol.
•Vulnerability Protection profile (includes inline cloud analysis)
•File Blocking profile
•WildFire Analysis profile
## Security Policy Best Practices28
## ©
## 2026 Palo Alto Networks, Inc.

## Security Policy Best Practices
STEP 1 |Clone the predefined default Antivirus profile, rename it, and edit it as you transition the
Antivirus profile safely to best practices settings.
To transition the Antivirus profile safely to a best practices profile:
1.False positives are rare. Deploy the best practices Antivirus profile for applications that
aren’t critical to your business right away.
2.For business-critical applications, start by alerting to ensure that you don’t affect the
availability of critical applications. Transition to blocking when you feel comfortable that the
Antivirus profile doesn’t block these applications.
3.If you have an existing deployment or are migrating and you have an existing block in place,
replicate it because you already understand the traffic and why you’re blocking it.
4.If you treat internal applications differently than external applications, you might need
an Antivirus profile for internet-facing traffic and a different Antivirus profile for internal
traffic.
Monitor the Threat logs to see whether any business-critical applications cause alerts or
blocks. Monitor the WildFire Submissions logs if you have an Advanced WildFire or legacy
WildFire subscription and use the WildFire action settings.
A best practices Antivirus profile blocks known malware, viruses, and ransomware bots:
•Enable real-time signature lookup globally on the device and in the Antivirus profile to hold
files until the firewall receives the latest real-time antivirus signature from the cloud:
Enable globally—Device > Setup > Content-ID > Content-ID Settings > Realtime
Signature Lookup, enable Hold for WildFire Real Time Signature Look Up, and set
## Security Policy Best Practices29
## ©
## 2026 Palo Alto Networks, Inc.

## Security Policy Best Practices
the Action On Real Time Signature Timeout to Reset Both. You must enable real-time
signature lookup globally to enable in Antivirus profiles.
Enable in Antivirus profile—Objects > Security Profiles > Antivirus and enable Hold for
WildFire Real Time Signature Look Up.
Holding files to ensure that WildFire gets the latest antivirus signatures protects you from
zero-day malware and outdated antivirus signatures that you might be exposed to if you
forward files without holding them for the latest signatures.
•Set the actions to take when the firewall detects viruses in certain protocols. The safest
action is to reset both the client and the server to ensure that the session is terminated:
Change the Signature Action to reset-both for the smtp, pop3, and imap protocols,
whose default action is to alert. Leave the Signature Action for the other protocols on
reset-both.
Change the WildFire Signature Action to reset-both for the smtp, pop3, and imap
protocols, whose default action is to alert. Leave the WildFire Signature Action for the
other protocols on reset-both.
Change the WildFire Inline ML Action to reset-both for the smtp, pop3, and imap
protocols, whose default action is to alert. Leave the WildFire Inline ML Action for the
other protocols on reset-both.
Attach a best practices profile to all allow rules.
A WildFire subscription is required to configure WildFire Signature Action and WildFire
Inline ML Action.
In Strata Cloud Manager Managed Prisma Access, Antivirus and WildFire come
together in one profile instead of having separate profiles.
STEP 2 |Clone the predefined default Anti-Spyware profile, rename it, and edit it as you transition the
Anti-Spyware profile safely to best practice settings. In addition to Anti-Spyware signature
policies, the profile also controls DNS sinkhole policies.
To transition the Anti-Spyware profile safely to a best practices profile, in Signature Policies:
1.False positives are relatively rare. For applications that aren’t critical to your business, block
critical and high severity signatures from the start.
2.Medium severity signatures might generate false positives, so they require initial
monitoring. Alert on medium severity signatures for internal traffic and block medium
severity signatures for external-facing traffic. Monitor the Threat logs ( Monitor > Logs >
Threat) to see if you can block applications for which you receive alerts or if you need to
allow them.
3.For business-critical applications, set the Action to alert to ensure application availability.
However, if you already protect applications with an Anti-Spyware profile that blocks
critical, high, and/or medium signatures, and you’re confident the profile meets your
business and security needs, use a similar profile to block spyware and protect those
applications.
4.Enable single packet capture for all severity signatures during the transition so you can
investigate events in greater detail if necessary if you have the resources. As you move
to best practice profiles, if low and informational events create too much packet capture
## Security Policy Best Practices30
## ©
## 2026 Palo Alto Networks, Inc.

## Security Policy Best Practices
activity (too large a volume of traffic) and the information isn’t particularly useful, transition
to disabling packet capture on those severities.
Packet captures consume management plane resources. Check system resources
(for example, Dashboard > System Resources) to understand usage before and
after you implement packet capture to ensure that your system has sufficient
resources to take all the packet captures.
5.Create exceptions as needed to remediate any confirmed false positives before you
implement full best-practice Anti-Spyware profiles.
If you treat internal applications differently than external applications, you might need
an Anti-Spyware profile for internet-facing traffic and a different Anti-Spyware profile
for internal traffic.
Transition the profile’s DNS Policies to best practices as soon as you are comfortable that you
understand the traffic you’re blocking:
•Set the Policy Action for DNS signatures to sinkhole to identify potentially compromised
hosts that attempt to access suspicious domains by tracking the hosts and preventing them
from accessing those domains. Set Packet Capture to extended-capture.
On PAN-OS systems, set the DNS Sinkhole address as the FQDN, for example,
sinkhole.paloaltonetworks.com, so that if the IP address changes, the setting is still
valid. For Prisma Access, use the sinkhole IP address.
•Sinkhole all of the DNS Security domain types and set Packet Capture to extended-capture
for Command and Control Domains and single-packet for all other domain types except
Parked Domains (PAN-OS 10.0 and later).
•Block all DNS record types, which are used by encrypted DNS queries, to prevent clients
from encrypting the client hello during the DNS resolution process.
Set the profile’s Inline Cloud Analysis (requires Advanced Threat Prevention subscription and
PAN-OS 10.2 and later) to Enable cloud inline analysis on all outbound traffic. Set the Action
to reset-both for all models.
In the transition Anti-Spyware profile, if you have existing antispyware controls that
block traffic and meet your business needs, implement those controls immediately
because you already understand the traffic and why you’re blocking it.
A best practices Anti-Spyware profile profile detects command-and-control (C2) traffic,
prevents compromised systems from establishing an outbound connection, and enables
DNS sinkholing to identify infected hosts. Use GlobalProtect to automatically quarantine a
## Security Policy Best Practices31
## ©
## 2026 Palo Alto Networks, Inc.

## Security Policy Best Practices
compromised device in PAN-OS and with Panorama Managed Prisma Access, and you can also
quarantine compromised devices in Strata Cloud Manager Managed Prisma Access.
## For Signature Policies:
1.Set the Action for critical, high, and medium severities to reset-both and set packet-capture
to single-packet.
2.Set the Action for low and informational severities to default and disable packet-capture.
For DNS Policies, use the same settings recommended for the transition period. Set the Policy
Action to sinkhole for all signature sources, set Packet Capture to extended-capture for Palo
Alto Networks Content and Command and Control Domains, and set Packet Capture to
single-packet for all other DNS Security domains except Parked Domains.
The best practice settings for Inline Cloud Analysis are the same as the transition settings.
Enable the feature on all outbound traffic and set the action to reset-both.
Use the DNS Security service to protect you from advanced DNS-based threats (requires
DNS Security license and Advanced Threat Prevention or active legacy Threat Prevention
subscription).
Attach a best practices profile to all allow rules.
STEP 3 |Clone the predefined strict Vulnerability Protection profile, rename it, and edit it as you
transition the Vulnerability Protection profile safely to best practices settings.
Vulnerability Protection profiles defend against buffer overflows, illegal code execution,
and other attempts to exploit client-side and server-side vulnerabilities. To transition the
Vulnerability Protection profile safely to a best practices profile:
1.False positives rates are low. Set rules for applications that aren’t critical to your business to
block (reset-both) right away.
2.For business-critical applications, start by alerting to ensure that you don’t affect the
availability of critical applications. Transition to blocking when you feel comfortable that the
Vulnerability Protection profile doesn’t block these applications.
3.If you have an existing deployment or are migrating and you have an existing block in place,
replicate it because you already understand the traffic and why you’re blocking it.
4.Set signatures in the brute-force category for critical, high, and medium severities to alert
and fine-tune them until you can comfortably transition to blocking. Set Packet Capture to
extended-capture.
5.Set signatures for critical and high severity rules to reset-both and set Packet Capture to
single-packet.
6.Set signatures for medium severity rules to alert and set Packet Capture to extended-
capture.
7.Set signatures for low and informational severity rules to default and set Packet Capture to
single-packet.
8.For Inline Cloud Analysis, use the same criteria for alerting versus blocking business
applications that you use for the initial Vulnerability Protection rules. If you have existing
## Security Policy Best Practices32
## ©
## 2026 Palo Alto Networks, Inc.

## Security Policy Best Practices
controls, replicate them to block traffic. For new controls, alert for at least a week before
transitioning to blocking. Move to blocking as soon as you can.
Packet captures consume management plane resources. Check system resources (for
example, Dashboard > System Resources) to understand usage before and after you
implement packet capture to ensure that your system has sufficient resources.
Monitor the Threat logs to see whether any business-critical applications cause alerts or
blocks. Monitor the WildFire Submissions logs if you have a WildFire subscription and use the
WildFire actions.
The best practices Vulnerability Protection profile controls how to handle client-side and
server-side vulnerabilities for critical, high, medium, low, and informational event severities. In
the profile, configure six rules:
1.Create the same three rules that prevent brute force attacks in the transition profile and set
the Action to reset-both and Packet Capture to single-packet.
2.Combine simple-client-critical, simple-client-high, simple-client-medium, simple-server-
critical, simple-server-high, and simple-server-low severities in one rule. Set the Action to
reset-both and set Packet Capture to single-packet.
For profiles that control internal (east-west) traffic, blocking medium severity
events might impact business applications. If blocking impacts business
applications, create a separate rule in the profile for medium severity events with
the Action set to alert. Apply this profile only to internal traffic.
3.For simple-client-low and simple-server-low severities, set the Action to default and set
Packet Capture to single-packet.
4.For simple-client-informational and simple-server-informational severities, set the Action to
default and disable packet capture. (Informational activity might generate a relatively high
volume of packet capture traffic that isn’t particularly useful compared to potential threat
packet captures.)
5.Set the Inline Cloud Analysis actions to reset-both.
To control Vulnerability Protection profiles more granularly and fine-tune Vulnerability
Protection for a particular use case, create separate rules in the profile for each severity for
both client-side and server-side detection. When the action and packet capture settings are
the same, it makes sense to combine them in one rule to simplify configuration.
Attach a best practices profile to all allow rules.
## Security Policy Best Practices33
## ©
## 2026 Palo Alto Networks, Inc.

## Security Policy Best Practices
STEP 4 |Transition your File Blocking profiles from alerting to blocking all potentially malicious file
types.
Strata Cloud Manager Managed Prisma Access does not support File Blocking profiles
for Security policy rules.
File Blocking profiles block potentially malicious file types used in cyberattacks. To transition
File Blocking profiles safely to best practice settings to a best practices profile:
•For business-critical applications, alert for all file types and move to a best practices File
Blocking profile as soon as possible. If you already have blocking controls in place, replicate
them and continue to block traffic that you already know you want to block.
•For applications that are not business-critical, start the transition to a best practice File
Blocking profile:
•Inbound and outbound traffic—Block 7z, bat, chm, class, cpl, dll, dlp, hta, jar, ocx, pif, scr,
torrent, vbe, and wsf files. Alert on all other files.
•Internal traffic—Block 7z, bat, chm, class, cpl, dlp, hta, jar, ocx, pif, scr, torrent, vbe, and
wsf files (this is the same as the inbound/outbound profile except it alerts on .dll files
instead of blocking them). Alert on all other files.
•Block any of the following file types that you can for users who don’t need them for
business purposes: cab, exe, flash, msi, Multi-Level-Encoding, PE, rar, tar, encrypted-rar,
and encrypted-zip.
If necessary, create exceptions for IT groups and others who need legitimate business
access to any of these file types. If you already block any other file types, continue to
block them.
Transition to a best practices File Blocking profile as quickly as you are comfortable
with doing so.
The predefined strict file blocking profile blocks file types that are typically used in cyber
attacks and that have no real use cases for upload and download. However, a few protocols
used for malicious purposes might also be required for activities such as Windows updates.
The strict file blocking profile blocks .exe., .dll, .pe, and .cab files. To make exceptions to allow
protocols for a specific activity such as Windows updates:
1.Create a specific Security policy rule that allows only the users who need access for
business purposes and the business applications that use the protocols you want to block
for other traffic.
2.Attach a File Blocking profile that allows the required protocols to the rule.
3.Place the rule above a Security policy rule with a File Blocking profile that blocks the
protocols for all other traffic.
This method allows you to use potentially malicious file types in a safe way that enables
business applications while blocking malicious traffic. Fine-tune the profiles and rulebase to
allow any required exceptions.
Attach a best practices profile to all allow rules.
## Security Policy Best Practices34
## ©
## 2026 Palo Alto Networks, Inc.

## Security Policy Best Practices
STEP 5 |Attach the default WildFire Analysis profile to all allow rules to detect and prevent zero-day
malware.
To get real-time updates and other advanced features, get an Advanced WildFire subscription
(PAN-OS 10.0 or later) or a WildFire subscription.
Deploy the default WildFire profile, which is the best practice profile. WildFire doesn’t impact
network traffic, so there is no transition period required. (However, the best practices WildFire
Action settings in the Antivirus profile impact traffic that generates signatures that result in a
reset or drop action or in a hold for looking up the latest antivirus signature.) Attach a WildFire
Analysis profile to all allow rules to send all files to WildFire for analysis.
In Strata Cloud Manager Managed Prisma Access, WildFire and Antivirus come
together in one profile, which you add to a Prisma Access profile group.
STEP 6 |Security profile groups consist of individual Security profiles combined in a named group,
which enables you to apply Security profiles more easily and consistently to Security policy
rules.
Create Security profile groups for different conditions, based on the logic of your rulebase:
•Each profile group should have a distinct purpose, such as creating profile groups specific
to the flow of traffic. For example, a profile group for inbound traffic doesn’t need a URL
Filtering profile, but a profile group for outbound traffic does.
Profile groups that are specific to the flow of traffic make it easier to make exceptions if
you want to treat internally-facing and externally-facing traffic differently. For example, you
might want to block something for internal traffic that you use and allow for external traffic.
In that case, you would use different profiles for internal and external traffic. Whether you
need separate profiles depends on how you want to treat the traffic.
•To make transitioning profiles from alert to block easier, create profile groups for initial
alerting and profile groups for best practice blocking. This makes it easy to alert on threats
in all allow rules. As you become comfortable enough to move from alert to block, profile
groups make it easy to make the change because you only have to swap out one object
instead of each individual profile.
•Consider creating a default profile group by naming the group default. For example,
create a group with profiles that alert but don’t block most traffic, based on best practice
Security profile transition advice. The firewall automatically applies the default profile group
to all new Security policy rules that allow traffic. (The firewall does not apply the default
profile to existing rules.) This ensures that all new allow rules have some level of threat
prevention. Edit or replace the default profile as needed.
## Security Policy Rulebase Best Practices
The Security policy rulebase is an ordered list of your Security policy rules. The order of the rules
determines how the firewall handles traffic.
Firewalls compare traffic to Security policy rules, starting with the first rule at the top of the
Security policy rulebase. When traffic matches a rule’s criteria, the firewall executes the rule’s
action on the traffic and doesn't compare the traffic to any other rules. If no rule matches the
traffic, the firewall drops the traffic (implicit deny). The way you order the rules in the rulebase
## Security Policy Best Practices35
## ©
## 2026 Palo Alto Networks, Inc.

## Security Policy Best Practices
is critical because the firewall takes action on the traffic on the first rule match and then stops
comparing the traffic to the rulebase.
If you migrated Security policy from another vendor’s firewall, the previous firewall might
have evaluated traffic against its rulebase differently. For example, the order of the rules
might not have made a difference on your old firewall but they are crucial on Palo Alto
Networks firewalls.
Understanding how you want to handle different types of traffic and how Security policy rules
work help you evaluate how to order rules in the rulebase. Design and optimize your Security
policy rulebase in a logical manner, as described in this section. For existing rulebases, if the
rulebase isn’t optimized as much as it could be, plan and test changes in accordance with the
advice in this section. If you plan to roll out the changes in phases, make the changes at the
appropriate time or times.
This section covers:
•Ordering Security policy rules in the rulebase
•Avoiding rulebase bloat
•Positioning to make exceptions to a rule
•Preventing and remediating rule shadowing
•Using device group hierarchies on Panorama to simplify the rulebase
STEP 1 |Order Security policy rules logically in the rulebase.
Because the firewall executes a policy rule’s action on traffic when that traffic matches the
rule’s criteria, the order of the rules is critical and determines which rule traffic matches, and
therefore, which action the firewall takes on the traffic and how the firewall inspects the
traffic:
1.Place rules that block malicious traffic at the top of the rulebase to prevent accidentally
allowing bad traffic later in the rulebase. If you have an active Advanced Threat Prevention
or active legacy Threat Prevention license, create block rules based on the predefined
external dynamic lists (EDLs) and test them to ensure that they don’t block traffic that you
want to allow. On Panorama, place these rules in the pre-rules so they execute before any
firewall-specific rules.
2.Allow basic infrastructure applications and common services such as DNS and NTP near the
top of the rulebase to prevent accidentally blocking them. These rules usually allow traffic
from any source zone to any destination zone and apply to everything and everyone.
On Panorama, place these rules in the pre-rules so they execute before any locally defined
rules on the firewall.
3.The logic for all other rules is to place the most specific rules near the top of the rulebase
and the most general rules closer to the bottom of the rulebase. If you place general rules
before specific rules in the rulebase, traffic that you intend to match the specific rule might
match the general rule instead, which might apply a different action and different inspection
## Security Policy Best Practices36
## ©
## 2026 Palo Alto Networks, Inc.

## Security Policy Best Practices
to the traffic than you want. This is called shadowing—another rule “shadows” the rule that
you intend the traffic to match.
4.If you have not yet converted or cannot convert all of your port- and service-based Security
policy rules to App-ID-based rules, place App-ID-based rules ahead of port- and service-
based rules.
STEP 2 |Keep the rulebase as small as you can for easier management and to avoid rulebase bloat.
1.If five of the following six objects are the same in multiple rules, combine those rules into
one rule:
•Source zone
•Destination zone
•Source IP address
•Destination IP address
•Service port
•Application
For example, if three rules specify different applications but have the same source and
destination zone, source and destination IP addresses, and service port, then you can
combine the rules into one rule that specifies the applications from each of the original
rules.
2.Use group objects to simplify policy creation and reduce rulebase size.
Use application groups and address groups to help consolidate rules that apply to all of the
group members.
If you use both individual objects and group objects in policy, be aware that
an object’s membership in a group might cause rule shadowing if the object is
specified individually in a rule and also specified in a rule as part of an object group.
In this case, the firewall might not take the intended action because the traffic
might match the wrong rule first. If possible, combine the rules, unless your change
control process requires a specific policy to track access. If you want to treat an
object differently than other objects in a group, remove the object from the group.
3.Disable or remove rules from the Security policy rulebase when you no longer need them.
Security policy rules might become unneeded when an organization changes applications
or infrastructure, or when you no longer need temporary testing rules. If you don't disable
or delete those rules, they might cause unexpected actions on traffic. It’s safest to disable a
rule first so that you can enable it again if disabling it causes issues. When you disable rules,
apply a tag with the date you disabled the rules. Periodically use Policy Optimizer’s Rule
Usage feature to check how long each rule has been unused. After a period of time where
you’re confident that you really don't need the rule, delete it.
Be aware of rules with applications that you use only for periodic events such as
quarterly meetings or annual conferences. It might be appropriate to configure a
Schedule that enables the rule only during the event time period.
4.Use Policy Optimizer to optimize the rulebase. Policy Optimizer finds unused rules, rules
with unused applications, rules that haven’t been used over time, and rules that don’t
## Security Policy Best Practices37
## ©
## 2026 Palo Alto Networks, Inc.

## Security Policy Best Practices
have Log Forwarding profiles, as well as enabling you to manage new SaaS applications in
Security policy if you have a SaaS Security subscription.
5.On Panorama, use common global device groups that apply to multiple VSYSs and firewalls
across the organization for common, global Security policy rules such as rules that control
common basic services and any other services or applications that you want to apply to
broad groups of devices. Create the device group hierarchy so that you don’t have to
repeat rules across groups—use the hierarchy to write a rule one time and apply it to all
appropriate firewall groups.
6.Review the Security policy rulebase periodically as part of regularly scheduled maintenance.
STEP 3 |To make an exception to a rule, place the more specific rule in front of the more general rule.
For example, you want to block your employees from going to malicious websites, so you
create a general Security policy rule that blocks access to all malicious websites for all
employees. However, your InfoSec team and PEN testers need access for testing purposes.
In this case, you create a rule that allows access to the required malicious websites for only
those users (decrypting the traffic, applying the strictest Threat profiles to the rule, and
specifying only the applications used for testing) and place that rule above the general rule in
the rulebase.
When the InfoSec and pen testers try to access the malicious sites for testing, they are
allowed, but no other users match the rule’s criteria, so the general rule blocks them. If you
place the InfoSec and pen test team access rule after the general block rule, the general rule
shadows the specific rule, and the InfoSec/pen tester traffic would match the general rule and
be blocked.
STEP 4 |Prevent general rules from shadowing more specific rules.
Shadowing is when you place a broad rule that includes the same match criteria as a more
specific rule higher in the rulebase than the specific rule, so traffic intended to match the
specific rule instead matches the general rule first and is never compared to the specific rule.
The result is that the firewall executes the action and inspection configured in the general rule
## Security Policy Best Practices38
## ©
## 2026 Palo Alto Networks, Inc.

## Security Policy Best Practices
when the intention is to execute the action and inspection in the specific rule. The general rule
shadows the specific rule.
A shadow rule might shadow more than one other rule in the rulebase.
A partial shadowing conflict may occur when you specify a bi-directional NAT rule
where the source or destination IP address (original or translated) overlaps with the
source or destination IP address (original or translated) of another NAT rule (either
shadowing or shadowed).
The easiest way to prevent shadowing is to construct the rulebase correctly from the start.
However, existing rulebases and migrated rulebases might have shadow rules. To prevent and
fix shadowing:
1.Understand the action that you want to take on the traffic and how you want to inspect it.
If the action and inspection in the specific rule are how you want to handle the traffic, move
the specific rule above the general rule in the rulebase. If the action and inspection in the
general rule are how you want to handle the traffic, then you don’t need the specific rule.
2.Place more specific Security policy rules above general rules in the rulebase. If you place the
general rule first, it shadows the specific rule, for example:
1.Create a general rule that blocks all access to Facebook.
2.Create a specific rule that allows marketing and PR groups to access Facebook, but place
the rule below the general Facebook rule in the rulebase.
3.The general rule blocks all Facebook access regardless of user group, so traffic never
matches the specific rule that allows access to the specific groups that you want to
allow.
The fix is to move the specific rule above the general rule in the rulebase.
3.Review and resolve shadowed rules to make sure the firewall executes the action you want
and inspects traffic in the manner you want.
When you write a new Security policy rule:
1.Select a commit option and then perform a Commit on the firewall or a Validate Commit
on Panorama to check for configuration issues. Do not commit the configuration.
Resolve issues that the validation check discovers before proceeding.
- Commit or Commit and Push the configuration.
3.When the commit finishes, select Tasks from the bottom-right ribbon to open the Task
## Manager.
4.In the Type column, click Commit All to bring up Job Status. (Commit and Push doesn't
provide shadowing information.)
5.Click the Status column message to open the Last Push State Details and select the Rule
Shadow tab. If there is no Rule Shadow tab, then the firewall has no shadowed rules.
6.The left side of Last Push State Details shows the rules that shadow other rules. The
name of each shadow rule is a link to the rule. For each shadow rule, click the number in
## Security Policy Best Practices39
## ©
## 2026 Palo Alto Networks, Inc.

## Security Policy Best Practices
the Count column to display the rules it shadows. The shadowed rule names are listed,
but they are not links to the shadowed rules.
7.The list of shadow rules is not persistent across commit operations, so it is crucial for you
to capture the list of shadowed rules for each shadow rule. For example, pull the status
via an API using a script, copy and paste the list into a text editor, take a screen capture,
take a photograph, or write down the names of the shadowing rules and the shadowed
rules.
The PAN-OS configuration Commit operation validates for shadow rules. If
rule shadowing is detected, it generates a warning message that identifies the
affected rules. If you perform another commit operation before you capture the
shadow list, the shadow information is lost. Be sure to capture this information
immediately.
8.Find each shadowing and shadowed rule in the Security policy rulebase and capture each
rule’s configuration.
9.Compare each shadow rule with the rules that it shadows side by side and understand
the purpose of each rule. This enables you to evaluate related rules together and
understand how you want to handle the applications the rules control.
10.When you understand how you want to handle the applications in a shadow rule and
its shadowed rules, combine rules to simplify the rulebase, disable or remove duplicate
rules, and move specific rules above general rules to resolve the shadowing.
11.Iterate to fix any remaining shadowing.
12.Repeat the process for each shadow rule.
On nonproduction test systems, you might want to keep shadowing and shadowed
rules for testing new policy rules and other testing purposes.
STEP 5 |On Panorama, position Security policy rules appropriately within device group hierarchies.
Position rules so that you don’t have to repeat the same rule unnecessarily in multiple device
groups. Rules that are common to multiple device groups belong above those groups in the
hierarchy so one rule applies to all of the groups.
•Construct the hierarchy in a thoughtful manner that only gives access to firewall groups
that you intend to have access. Think about the access that each firewall needs when you
construct device groups and think about the access each device group needs when you
create the device group hierarchy. The key to construction is commonality—which firewalls
need similar access, which groups of firewalls need similar access, and how to construct
a hierarchy that enables groups higher in the hierarchy to contain rules that apply to the
levels below them and eliminate the need to duplicate rules.
•Place rules that apply to all firewalls in the highest group in the hierarchy to avoid rule
duplication.
•Place rules that apply to sets of firewall groups high enough in the hierarchy so that you
don’t have to duplicate rules.
The Panorama Administrator’s Guide provides in-depth information about device groups,
including an example illustration of a device group hierarchy .
## Security Policy Best Practices40
## ©
## 2026 Palo Alto Networks, Inc.

## Security Policy Best Practices
## Policy Optimizer Best Practices
Policy Optimizer helps you convert port-based Security Policy rules to application-based rules and
transition to least privilege access policy rules:
•Discover and convert port-based rules (application is any instead of a specific application) to
application-based rules that follow the principle of least privilege access (Policies > Security >
## Policy Optimizer > Rules Without App Controls).
•Discover and remove unused applications from over-provisioned rules (Policies > Security >
## Policy Optimizer > Unused Apps).
•Discover and eliminate rules that you don’t use and understand policy rule usage (Policies >
## Security > Policy Optimizer > Rule Usage).
•Discover new applications that match application filters and application groups used in Security
policy rules. Evaluate new applications and whether you want to allow or block them (Policies
## > Security > Policy Optimizer > New App Viewer).
If you have a SaaS Security Inline subscription and use the App-ID Cloud Engine
(ACE), use Policy Optimizer to integrate ACE App-IDs into your Security policy
rulebase.
•Discover Security policy rules that don’t have a Log Forwarding profile attached and add Log
Forwarding profiles to those rules (Policies > Security > Policy Optimizer > Log Forwarding for
## Security Services).
Policy Optimizer is available in PAN-OS 9.0 and later for Panorama and PAN-OS firewalls
(firewalls can be on PAN-OS 8.1 if Panorama runs PAN-OS 9.0 or later). Policy Optimizer
is available for Strata Cloud Manager Managed Prisma Access and Panorama Managed
Prisma Access in PAN-OS 10.2.4 or later with Cloud Service Plugin 5.0 or later.
Strata Logging Service compatibility requires Panorama running PAN-OS 10.0.3 or later
with Cloud Services plugin 2.0 Innovation or later.
Policy Optimizer best practices covers:
•How to Use Policy Optimizer—Major use cases, how to add applications to Security policy
rules, sorting and filtering rules, and using application filters and application groups.
•Policy Optimizer Rulebase Workflows—How to plan a transition to application-based rules,
convert port-based rules to application-based rules, eliminate unused rules, and remove
unused applications to tighten the rulebase.
Decrypt all the traffic that local regulations, compliance, business requirements, and
privacy considerations allow as soon as you can to provide more accurate application
information and gain visibility into applications you control with Policy Optimizer. Without
decryption, the firewall can often identify parent applications but usually can’t identify
functional applications. For example, the firewall sees “facebook”, but not facebook-
post, facebook-download, facebook-file-sharing, etc. You must decrypt traffic to gain
visibility into and control of functional applications. For SSL Forward Proxy (outbound)
decryption, implement User-ID and URL Filtering first so you can target decryption
effectively.
## Security Policy Best Practices41
## ©
## 2026 Palo Alto Networks, Inc.

## Security Policy Best Practices
How to Use Policy Optimizer
This section describes the major Policy Optimizer use cases and how to use the tool. Policy
Optimizer Rulebase Workflows describes workflows.
Policy Optimizer use cases include:
•Migration from port-based application-based rules—View layer 7 applications that match each
port-based rule, select the applications you want to allow, and convert each rule to one or
more application-based rules.
•New deployments—Discover applications on your network and transition to application-based
policy over time.
•Mature deployments—Examine your rulebase, convert broad rules based on application filters
to tight rules based on application groups that allow only the applications you sanction, and
eliminate unused rules and applications.
•DevOps—Understand new or modified applications in your test environment. Work out how
to handle them in Security policy rules before making changes in your production environment.
Test the new and modified rules before you apply them in a production environment.
STEP 1 |Work with the appropriate people to understand the sanctioned applications you want to
allow on your network for business purposes and the tolerated applications you want to
allow for employees.
Be aware of which applications are business-critical. Be aware of which applications are
only used periodically for quarterly, annual, or other events, and evaluate relevant rules long
enough to see the activity of these applications. Knowing the business logic for allowing
applications helps you understand how to construct Security policy. To better understand
applications, look up content-delivered App-IDs in applipedia or in Objects > Applications on
the firewall or Panorama.
STEP 2 |Learn how to sort, filter, and examine Policy Optimizer information and statistics using
different metrics for different purposes.
Policy Optimizer statistics aren’t reported in real time. It takes about an hour or more,
depending on application traffic volume and rulebase size, to update the application list. After
you add an application to a rule, wait at least an hour before checking Traffic logs for the
application’s information. If you don’t see the information, wait a while and check again.
Policy Optimizer ignores traffic from rules that only Log at Session Start to avoid
counting transient applications. (For rules that also Log at Session End, Policy
Optimizer picks up the rules’ statistics.)
STEP 3 |Understand how to use application filters and application groups in Security policy.
Use application filters in Security policy rules to discover applications on your network. Then
convert those rules from application filters to application groups so you can specify the exact
applications to allow.
•Use application groups as much as possible to simplify and tighten Security policy rules and
reduce the size of the rulebase.
Application groups are user-defined sets of specific applications that you want to control in
one rule with similar security treatment. Add applications to rules using application groups
## Security Policy Best Practices42
## ©
## 2026 Palo Alto Networks, Inc.

## Security Policy Best Practices
(the linked topic focuses on ACE applications but applies to all applications) to control
multiple applications with one rule instead of creating a separate rule for each application.
Reuse application groups in different rules to give different users, sources, and destinations
different access to applications. Reusing groups automates adding applications to multiple
rules (when you make any change to an application group, the change is reflected in every
rule that includes the application group).
•Use application filters to:
•Discover applications on your network.
•Future-proof rules by handling new applications automatically when they match a
filter. This is useful both in the application discovery phase in migrations and new
deployments, and in mature environments.
For example, create an allow rule with an application filter based on the Palo Alto
Networks tag. This ensures that you allow all current Palo Alto Networks applications
and all future Palo Alto Networks applications.
Another example is creating a rule that filters for new content-delivered App-IDs to
safely handle them until you can examine them more closely.
•In mature rulebases, add applications to rules using application filters to block
undesirable types of applications. Use application groups to purposefully allow traffic
(the linked topic focuses on ACE applications but applies to all applications).
Application filters are dynamic sets of applications. Applications match application filters
based on attributes that you define, such as category, subcategory, risk, tags (pre-defined
tags or custom tags), and characteristics. The firewall automatically adds new applications
to a filter when they match the filter criteria. Security policy rules with an application filter
automatically control new applications that match the filter.
Application filters are looser controls than application groups. You control exactly which
applications are in an application group. The attributes you define control the applications
in an application filter, which can lead to allowing more applications than you need to allow.
That’s why filters are best for discovering traffic and for blocking application subcategories
of traffic. Reuse application filters in different rules to give different users, sources, and
destinations different access to applications.
Use application groups and application filters as much as you can instead of adding individual
applications to rules. Beginning with PAN-OS 10.1, you can add applications to application
groups and filters directly from Policy Optimizer, which is a best practice because it gives you
visibility into all of the applications that a rule sees.
Prior to PAN-OS 10.1, add applications to groups and filters using Objects > Application
Groups and Objects > Application Filters.
STEP 4 |Decide which applications to add to a rule based on the purpose of the rule. The rule’s
purpose helps determine who needs access to the applications and how (source, destination,
inspection, logging) to grant access.
## Security Policy Best Practices43
## ©
## 2026 Palo Alto Networks, Inc.

## Security Policy Best Practices
STEP 5 |Reuse application filter and application group objects in policy to give different user groups
different levels of access to those applications and/or treat different source and destination
combinations differently.
User-ID is integral to creating best practices Security policy based on the principle of least
privilege access. Without User-ID, you can’t specify who can use applications.
Reusing application group and application filter objects reduces rulebase bloat by simplifying
the rulebase.
## Policy Optimizer Rulebase Workflows
This section describes transitioning from port-based rules to application-based rules and
workflows for the Policy Optimizer tool. How to Use Policy Optimizer describes major use cases
and how to use the tool.
The end goal is to lock down the rules so that they allow only sanctioned applications and
applications that you tolerate for employee use. In conjunction with that, lock down the users
who have legitimate business reasons to access different applications. Use Traffic logs and the
ACC to help you narrow the scope of rules to specific users to avoid over-provisioning user
access. Work with application owners and other groups to understand who has business reasons
for accessing applications.
STEP 1 |Plan a phased transition from port-based to application-based rules and understand key
transition concepts and methods.
Migrations and new deployments planning and methodology:
•For migrations from port-based to application-based rules, start with your port-based
Security policy rulebase. For new deployments and migrations, create rules based on
application filters to gain visibility into different types of applications and add a catch-
all rule at the bottom of the rulebase so you don’t accidentally block mission-critical
applications. Apply best practices Threat Prevention profiles (both directions) and URL
Filtering profiles (outbound traffic) to these rules. As applications match the catch-all rules,
follow the advice in Step 2 to prioritize which rules to start converting and refining first, and
how long to observe rules with different types of applications before transitioning them to
application-based rules.
Policy Optimizer shows you the specific layer 7 applications (App-IDs) that match
each port-based rule.
•Run best practice assessment reports directly in AIOps to set a baseline so that you
understand your current best practices state. Run periodic reports to measure progress.
Progress means fewer port-based rules, fewer unused rules, and fewer rules with unused
applications over time.
Existing deployments planning and methodology:
•If the deployment consists of port-based rules or mostly of port-based rules, follow the
previous advice for migrating to application-based policy.
•If the deployment consists of mostly application-based rules, place a catch-all rule at the
bottom of the Security policy rulebase to discover and gain visibility into applications that
## Security Policy Best Practices44
## ©
## 2026 Palo Alto Networks, Inc.

## Security Policy Best Practices
don’t match other rules, with strict Security profiles to stop malicious traffic. Follow the
prioritzation advice in Step 2 to tighten the rules.
After you move applications from port-based rules to application-based rules, select the port-
based rules in Policy Optimizer and Reset Rule Hit Counter. This resets the Days with no new
apps counter so you can see when more new applications match the original port-based rules
and evaluate whether you want to allow or block them.
After you refine a rule, wait until Days with no new apps reaches at least seven days before
you revisit the rule to continue refining it. When the catch-all rules and port-based rules no
longer see applications that you want to allow, disable or delete them. Be aware of applications
your enterprise uses only for periodic events before you disable or delete a rule.
STEP 2 |Prioritize and convert port-based Security policy rules (rules with the application set to any)
to layer 7 application-based rules.
Prioritize which rules to convert from port-based rules to application-based rules at what
phase of the transition. These techniques are valid for migrations and new deployments, and
for existing application-based deployments where you need to tighten your rulebase:
1.In new and existing deployments, block known-malicious and risky traffic immediately.
2.Implement catch-all rules based on application filters.
3.Convert simple rules with well-known-applications after one week. For example, rules
that control port 21 (FTP), port 53 (DNS), port 22 (SSH) are good candidates for quick
conversion. The fewer and more well-known the applications in a port-based rule, the more
confident you can be in converting it to an application-based rule.
4.After 30 days, convert the most stable rules. Rules that see no new applications over a 30-
day period and that control relatively few applications are good candidates.
5.After at least 30 days, begin to convert internet access rules (ssl, web-browsing) and rules
that see the most traffic.
6.After a time period appropriate for the applications seen on the rule, convert rules with few
## Apps Seen.
7.As you convert rules, review each rule when Days with no new Apps reaches at least
seven days (longer for complex rules or rules with many applications) and handle and new
applications as needed.
Cloning rules is the safest way to transition from port-based rules to application-based rules.
Cloning preserves the original port-based rule and places the cloned rule directly above the
original rule. This enables you to carve out specific, application-based rules from the original
rule without risking application availability, as shown in this cloning use case example for
migrating your web browsing and ssl traffic to application-based rules. Applications that don’t
match cloned rules continue to match the original port-based rule. When the original rule stops
seeing applications that you want on your network for an appropriate period of time, you can
safely disable or delete the original rule.
Use application groups and application filters appropriately as you convert rules.
For migration scenarios, follow Best Practices for Migrating to Application-Based
## Policy.
## Security Policy Best Practices45
## ©
## 2026 Palo Alto Networks, Inc.

## Security Policy Best Practices
STEP 3 |As you examine rules, use application filters to block application types that you know you
don’t want on your network. Block traffic based on subcategories, tags, and characteristics.
Use application filters to make exceptions to block rules. Don’t use risk as blocking filter
criteria, use risk to determine how to inspect, log, and control the traffic appropriately.
In addition to the recommended block rules to stop known-malicious traffic, review your rules
regularly and block other traffic that you know you don’t want:
1.Identify application types that you don’t want on your network and create application filters
that match them. Create block rules based on those application filters and place them in
front of any catch-all rules (or clone the rule from an existing rule and place the cloned rule
directly above the original rule in the rulebase).
2.Determine if there are specific applications within the blocked application types that you
want to allow on your network. Clone the block rule, change the Action to Allow, and
remove all applications except the applications you want to allow. Place the allow rule
directly above the block rule to create exceptions to the block rule.
3.Monitor the block rule to see if you want to allow any other blocked applications. If you
created an allow rule for exceptions, add applications you want to allow to that rule.
Otherwise, create a new allow rule for the applications and place it directly above the block
rule in the rulebase.
For example, file sharing applications can be particularly risky. Decrypt the traffic, and in
the Security policy rule, allow only the specific file sharing applications you use for business
purposes for only the necessary users and inspect and log the traffic. In the next rule in the
rulebase, use an application filter based on the file-sharing subcategory to block all file sharing
applications that you don’t explicitly, purposefully allow.
STEP 4 |Remove unused applications from over-provisioned rules.
Understand an application’s purpose before you remove it from a rule.
•Compare Apps Used to Apps Allowed. If the rule allows more applications than the rule
uses, examine the unused applications and determine whether you can remove them.
•Be aware of applications used only for quarterly, yearly, or other periodic events. Make
sure you capture a long enough history of the rule to see those applications. Also take into
account applications that are active in your test environment and that have been added to
your production environment in anticipation of sanctioning the application.
STEP 5 |Remove unused rules from the Security policy rulebase.
Unused rules clutter and complicate the rulebase. Rule Usage shows you information about
unused rules over different time periods. Evaluate the applications in the rules to see if you
## Security Policy Best Practices46
## ©
## 2026 Palo Alto Networks, Inc.

## Security Policy Best Practices
need them even though they haven’t been used. Before you remove unused rules, take into
account:
•Block rules with no hits—Don’t disable or delete these rules. For example, a block rule
using a threat EDL receives no hits. That’s good, but you want to continue to block in case
malicious traffic tries to access your network.
•Temporary rules—For example, rules for contractors or auditors. Instead of deleting those
rules, if there’s a regular access time, configure a schedule to control when the rule is in
effect. If access is intermittent, disable the rules and enable them when needed.
•Disabled policy rules—Apply a tag with the date the rules were disabled. If the rules aren’t
used within a particular time period, for example, more than one year, the rule is a candidate
for deletion. Add a Description to indicate why the rule is disabled and why or when it may
need to be enabled, for example, for auditor or contractor access.
•Periodically-used applications—Some applications are only used for quarterly, yearly, or
other periodic events. Capture a long enough history of rules that control these types of
applications to be sure the applications are no longer in use.
STEP 6 |Ensure that each rule has an appropriate Log Forwarding profile attached.
Identify rules without Log Forwarding profiles and add profiles to them (Policies > Security >
Policy Optimizer > Log Forwarding for Security Services).
STEP 7 |Convert broad rules based on application filters into narrow rules based on application
groups.
Use Rule Usage statistics to understand how rules are used and use Policy Optimizer to add
applications to application groups (PAN-OS 10.1 and later; for PAN-OS 10.0 and earlier, add
applications to application groups in Objects > Application Groups) and create tighter rules.
The end goal is to allow only the applications you sanction instead of allowing a broader range
of applications that match an application filter. Use application filters to discover applications
on your network and block broad subcategories of applications, and use application groups to
specify the exact applications you want to allow. To convert application filter based rules into
application group based rules using Policy Optimizer:
•Examine the applications that match rules based on application filters and decide which
applications you want to allow.
•For each rule based on an application filter, select the applications to allow and add the
applications to an application group in a cloned or existing rule.
•After you move applications from rules based on application filters to rules based on
application groups, select those rules in Policy Optimizer and Reset Rule Hit Counter. This
resets the Days with no new apps counter so you can see when new applications match
those application filter based rules.
•Monitor rules based on application filters until the Days with no new apps counter reaches
a threshold that indicates a rule is no longer seeing new applications. The threshold
depends on your environment and the types of applications the application filter matches.
Take into account applications used only at certain periods, such as quarterly or annual
events, and leave the filter in place long enough to see those applications so you can
add them to the appropriate application groups. If the application filter rule matches no
## Security Policy Best Practices47
## ©
## 2026 Palo Alto Networks, Inc.

## Security Policy Best Practices
applications that you want on your network, disable or delete the rule, depending on your
enterprise’s policy.
STEP 8 |Review and update Security policy rules as new applications enter your environment.
Review new App-IDs regularly in New App Viewer. Add applications to existing and new
application groups or to add applications directly to existing Security policy rules. Continue to
convert application filters to application groups.
App-ID Cloud Engine Best Practices
The App-ID Cloud Engine (ACE) identifies thousands of SaaS applications that the firewall
previously identified as ssl or web browsing traffic, not as specific applications. ACE gives these
SaaS applications specific App-IDs so you can gain visibility into them, control over them, and use
them explicitly in Security policy.
ACE requires PAN-OS 10.1 or later and a SaaS Security Inline subscription. ACE is
available in Prisma Access Cloud Services 3.0 Innovation for Panorama Managed Prisma
Access and is also available in the SaaS Security Cheat Sheet for Strata Cloud Manager
## Managed Prisma Access.
ACE App-IDs are supported only in Security policy. You cannot use ACE App-IDs in any
other type of policy rule.
The firewall downloads the entire catalog of ACE App-IDs but only downloads ACE App-
ID signatures for applications seen in the environment.
ACE controls SaaS applications in outbound flows and acts like a cloud access security broker
(CASB). In new deployments, ACE identifies the SaaS applications on your network to simplify
moving to layer 7 application-based policy.
In existing deployments, ACE provides tools to safely understand and manage the potentially
many SaaS applications that were previously identified as ssl or web browsing traffic and control
them explicitly in Security policy.
Decrypt all the traffic that local regulations, compliance, business requirements, and
privacy considerations allow as soon as you can to provide more accurate application
information and gain visibility into ACE applications. Without decryption, the firewall
can often identify parent applications but usually can’t identify functional applications.
For example, the firewall sees “facebook”, but not facebook-post, facebook-download,
facebook-file-sharing, etc. You must decrypt traffic to gain visibility into and control of
functional applications. For SSL Forward Proxy (outbound) decryption, implement User-
ID and URL Filtering first so you can target decryption effectively.
## Security Policy Best Practices48
## ©
## 2026 Palo Alto Networks, Inc.

## Security Policy Best Practices
STEP 1 |Understand how ACE App-IDs work on the firewall before you enable ACE.
Read ACE processing and policy usage to learn how the firewall handles ACE App-IDs,
including:
•How and when the firewall downloads ACE App-IDs.
•The differences between ACE App-IDs and content-delivered App-IDs.
•How the firewall resolves conflicts between ACE App-IDs, content-delivered App-IDs,
and custom App-IDs, including container applications (e.g., facebook) and their functional
applications (e.g., facebook-post, facebook-download, etc.).
•HA behavior.
•Panorama behavior when committing or pushing.
ACE identifies specific SaaS applications that the firewall previously identified as ssl or web
browsing traffic. When you enable ACE:
•If you have a Security policy rule that allows ssl and web browsing traffic, downloaded ACE
App-IDs match that rule unless they match an application filter used in a rule. ACE App-
IDs match an application filter based on the filter’s criteria, including tags, just like content-
delivered App-IDs. If an ACE App-ID matches an application filter in a rule, the application
is added implicitly to the rule. That rule controls the ACE application instead of the ssl/
web browsing rule, including the rule’s action (allow or deny), the users who can access the
application, the sources and destinations, and how the application is inspected and logged.
•Until you add an ACE App-ID explicitly to a rule or an ACE App-ID matches an application
filter that implicitly adds it to a rule, an ACE application continues to match the ssl/web
browsing allow rule, the same as before enabling ACE.
•If you have no rule that allows ssl and web browsing traffic, follow the advice in Step 3 to
discover and control ACE App-IDs.
When you use an ACE App-ID explicitly in policy, the firewall treats the application the same
way it treats content-delivered applications.
STEP 2 |Review your Security policy rulebase to find rules that use application filters before you
enable ACE.
Application filters allow applications based on matching filter criteria, including tags, so they
automatically add applications to rules and you have to examine those rules to see which
specific applications each filter allows and who has access to those applications. When an ACE
App-ID matches an application filter in a rule, that rule may not allow the same users as the ssl
and web browsing rule. Users who had access to the application in the ssl and web browsing
## Security Policy Best Practices49
## ©
## 2026 Palo Alto Networks, Inc.

## Security Policy Best Practices
rule may lose access to the application because it no longer matches that rule and those users
aren’t specified in the explicit rule.
It’s critical to understand who needs to use which applications for business purposes,
especially in environments with many rules, applications, and user groups. For
example, if you use the Web Apps tag in an application group in a rule, the tag
implicitly adds matching ACE applications to the rule. Those ACE applications don’t
match the ssl and web browsing rule and only the users specified in the Web Apps rule
can access them.
If no rules have application filters, there is no risk that ACE applications will automatically
match existing rules after you enable ACE because you haven’t added any ACE applications
explicitly to rules yet.
If you use application filters in Security policy rules, when you enable ACE:
•For deny rules, ACE applications that match the rule are blocked, which is exactly what you
intend to do with applications that match the deny rule. The rule is more effective because
you now block unsanctioned SaaS applications that the firewall couldn’t identify without
## ACE.
•For allow rules, closely monitor the applications the rule allows. Implicitly adding
applications with a filter is based on criteria, not on an administrator purposefully adding
specific applications. The most impacted rules are rules with filters based on broad tags
such as Web App, which applies to the majority of both ACE and content-delivered App-
IDs.
In existing deployments, keep in mind that if you have a rule that allows ssl and
web browsing traffic, then you were allowing all of the applications that ACE now
identifies. Use application filters to block the types of traffic you know you don’t
want and continue to allow the rest of the applications while you evaluate what
you want to sanction and what you want to block.
Step 3, step 4, and step 5 show you how to use application filters to add ACE App-IDs to rules
safely.
STEP 3 |Explicitly allow ACE applications using application filters so you can evaluate the applications
in a controlled manner.
Creating application filters to allow application types that you want on your network is
easier than periodically reviewing all the new ACE applications to determine which specific
applications to allow. Application filters enable you to examine the same types of applications
side-by-side and determine which ones you want to allow for business purposes.
1.Create an application filter based on the App-ID Cloud Engine tag, which matches all ACE
App-IDs (applications that were identified as ssl or web browsing before ACE). Attach the
filter to a Security policy rule with the appropriate Security profiles and logging, and place
the rule at the bottom of the Security policy rulebase. This ensures that the rule matches
and allows all new and existing ACE App-IDs unless they are specified in an earlier rule. It
also ensures that the firewall block rules take effect before the firewall compares traffic to
the ACE allow rule.
2.As you become more familiar with ACE applications, create more specific application filter
rules based on subcategories, tags, risk, and characteristics to match smaller groups of
## Security Policy Best Practices50
## ©
## 2026 Palo Alto Networks, Inc.

## Security Policy Best Practices
applications. Place these allow rules directly above the general ACE allow rule based on the
App-ID Cloud Engine tag. Narrowing down the applications that match a filter enables you
to examine the more similar applications side-by-side and determine which ones you want
to allow for business purposes.
3.Review the New App Viewer in Policy Optimizer frequently to see which downloaded ACE
App-IDs match Security policy rules and to gain greater visibility into those applications.
Evaluate the applications and determine whether to allow or block them.
Do not add users to rules that have application filters to broaden them because that
allows more access than necessary to applications. Over-provisioning user access
increases risk and goes against Zero Trust Network Access principles. Allow only users
who need access for business purposes.
STEP 4 |Use application filters to block application types that you don’t want on your network based
on subcategories, tags, and characteristics. Don’t use risk as blocking filter criteria (risk is an
assessment of relative risk within a category or subcategory, not necessarily of malicious
usage). Use risk to determine how to inspect, log, and control the traffic appropriately.
Blocking based on application filters is easier than periodically reviewing all the new ACE
applications to determine what you do and don’t want on your network. Using application
filters means the firewall immediately blocks new applications that you know you don’t want.
1.Determine ACE application types that you don’t want on your network. Create block rules
based on those application types and place them above the catch-all rules.
2.Determine if there are specific applications within those types that you want to allow on
your network. If you want to allow some of the applications:
1.Clone the block rule.
2.Change the Action to Allow.
3.Remove all applications from the rule except the applications you want to allow.
4.Specify the users who need access to the allowed applications, add the appropriate
Security profiles, and configure logging.
5.Place the new allow rule directly above the block rule to create exceptions to the block
rule.
3.Monitor the block rule to see if there are any other specific applications that you want to
allow and either add them to an existing allow rule or create a new allow rule to make those
exceptions.
For example, file sharing applications can be particularly risky. Allow only file sharing
applications you use for business purposes, only for the necessary users, and inspect and
log the traffic. In the next rule in the Security policy rulebase, use an application filter
based on the file-sharing subcategory to block all file sharing applications that you don’t
explicitly, purposefully allow. Monitor the block rule to ensure that it doesn’t block file sharing
applications you want to allow.
## Security Policy Best Practices51
## ©
## 2026 Palo Alto Networks, Inc.

## Security Policy Best Practices
STEP 5 |Convert broad rules based on application filters into narrow rules based on application
groups.
Rule Usage statistics show how rules are used in your environment. Use Policy Optimizer
to add applications to application groups (PAN-OS 10.1 and later) or add applications to
application groups manually to create tighter rules.
The end goal is to allow only the applications you sanction instead of allowing a broader range
of applications that match an application filter. Use application filters to discover applications
on your network and use application groups to specify the exact applications you want to
allow. To use Policy Optimizer to convert application filter based rules into application group
based rules:
•Examine the applications that match rules based on application filters and decide which
applications you want to allow.
•For each rule based on an application filter, select the applications to allow and add the
applications to an application group in a cloned or existing rule.
•After you move applications to rules based on application groups, select the original
application filter based rules in Policy Optimizer and Reset Rule Hit Counter. This resets
the Days with no new apps counter so you can see when new applications match the
application filter based rules.
•Monitor rules based on application filters to see when the Days with no new apps counter
reaches a threshold that indicates that a rule is no longer seeing new applications. The
threshold depends on your environment and the types of applications the application filter
matches. Take into account applications used only at certain periods, such as quarterly or
annual events, and leave the filter in place long enough to see those applications. If the
application filter rule matches no applications that you want on your network, disable or
delete the rule, depending on your enterprise’s policy.
Keep the rule based on the App-ID Cloud Engine tag at the bottom of the rulebase
as a catch-all rule to allow new ACE applications. After you move from application
filter based rules to application group based rules, all new ACE App-IDs match the
catch-all rule. Periodically examine the rule to determine which applications to add to
existing rules and application groups, which applications require new rules, and which
applications you want to block.
STEP 6 |Check the New App Viewer frequently to gain visibility into and explicit control of new ACE
App-IDs that were previously identified as ssl or web browsing applications. Use the new
ACE App-IDs explicitly in policy instead of as ssl or web browsing applications.
Review new ACE App-IDs that the firewall downloads regularly in Policy Optimizer’s New App
Viewer. Use Policy Optimizer to add applications to existing and new application groups or to
add applications directly to existing Security policy rules. Continue to use Policy Optimizer to
convert application filters to application groups.
## Policy Recommendation Best Practices
SaaS Policy Recommendation and IoT Policy Recommendation enable SaaS Security and IoT
Security administrators to create Security policy recommendations and submit them to:
•PAN-OS firewalls and Panorama (SaaS and IoT Policy Recommendation).
## Security Policy Best Practices52
## ©
## 2026 Palo Alto Networks, Inc.

## Security Policy Best Practices
•Panorama Managed Prisma Access (SaaS and IoT Policy Recommendation).
•Strata Cloud Manager Managed Prisma Access (SaaS Policy Recommendation only).
Cloud-based services such as IoT and SaaS policy recommendation cannot be used in air-
gapped environments because they require a cloud connection.
In air-gapped environments, for IoT Security, consider using Panorama as the
management engine for interacting with the cloud service and receiving policy
recommendations. Then push the recommendations to the managed firewalls that don't
have cloud connectivity. This solution only applies to policy recommendations themselves.
Functions such as device-to-IP mapping still requires cloud connectivity for managed
devices.
SaaS Policy Recommendation controls unsanctioned SaaS applications in PAN-OS and Prisma
Access. IoT Policy Recommendation controls unmanaged network devices in PAN-OS and
Panorama Managed Prisma Access. Their workflows have many similarities.
## Requirements:
•SaaS Policy Recommendation:
•SaaS Security Inline license
The SaaS Security Inline license includes the App-ID Cloud Engine (ACE), which provides
thousands of SaaS App-IDs for policy recommendations. SaaS Policy Recommendation
requires ACE deployment.
•PAN-OS 10.1 or later for PAN-OS and Panorama Managed Prisma Access.
•Enterprise Data Loss Prevention (DLP) to implement best practices data loss prevention and
gain visibility into data.
•Set up Azure AD for User-ID to specify users in policy rule recommendations (you can't
create user-based policy rules without User-ID).
•IoT Policy Recommendation:
•IoT Security license.
•IoT Security prerequisites.
•Ensure the proper support for PAN-OS and/or support on Panorama Managed Prisma
## Access.
•Enable Device-ID in each zone in which you want to control IoT devices. (Device-ID is to
IoT Security what User-ID is to SaaS Security—Device-ID is the "who" of IoT Security.)
Panorama can push SaaS and IoT policy recommendations only to firewalls that have the
appropriate licenses, so they must be installed on firewalls that use IoT and SaaS policy
recommendations. If the managed devices don't have the appropriate licenses, the push
fails.
In addition to licenses, to function properly and in a best practices manner, both IoT and SaaS
policy recommendation require:
•A valid device certificate on each appliance that uses SaaS or IoT policy recommendation.
•A connection to Strata Logging Service for visibility into the traffic.
## Security Policy Best Practices53
## ©
## 2026 Palo Alto Networks, Inc.

## Security Policy Best Practices
•Log Forwarding to Strata Logging Service configured in each Security policy rule
recommendation. For SaaS Security, forward Traffic logs, URL Filtering logs, and Threat logs at
a minimum.
SaaS Policy Recommendation helps you control unsanctioned applications.
To secure sanctioned SaaS applications, use SaaS Security API. SaaS Security API
provides security for supported commonly sanctioned SaaS applications and enables
you to manage policy for those SaaS applications.
•Policy Recommendation Concepts—Crucial ideas to understand before you recommend
policies.
•Policy Recommendation Workflow—SaaS and IoT workflows and workflow best practices.
## Policy Recommendation Concepts
SaaS and IoT policy recommendation have many similarities in their workflows and goals. The
workflows and thought process for policy recommendation in PAN-OS and Prisma Access also
have many similarities. Review Security Policy Rule Best Practices to better understand best
practices for the components of rules.
Strata Cloud Manager Managed Prisma Access does not support IoT Policy
## Recommendation.
SaaS Security and IoT Security administrators submit policy recommendations to PAN-OS and
Prisma Access. PAN-OS administrators import SaaS policy recommendations and IoT policy
recommendations into PAN-OS and Panorama Managed Prisma Access. Strata Cloud Manager
Managed Prisma Access administrators import SaaS policy recommendations in the cloud
platform. Different administrators often must cooperate to recommend and implement policy
rules, so good communication between administrators is critical.
General best practices for IoT Policy Recommendation include:
•Know whether discovered devices belong on your network.
•Ensure that the discovered applications you see for devices are appropriate for those devices.
•Understand the detected device vulnerabilities.
•Allow enough time for IoT Security to collect enough data about devices to identify them with
high confidence.
General best practices for SaaS Policy Recommendation include:
•Know the applications and application types that should and should not be on your network.
Create a formal list of sanctioned, tolerated, and unsanctioned applications and application
types, and tag applications appropriately as you gain visibility into them. View usage data
for unsanctioned applications and use filters to see who uses applications and how they are
used. Use the Visibility tools to view discovered applications and then tag the discovered
applications.
•Understand the data you want to look for in files so you can create appropriate DLP profiles
for policy rule recommendations.
•Most SaaS policy rule recommendations are for blocking traffic. Applying the principle of least
privilege access to SaaS applications is more complex than applying it only to content-delivered
## Security Policy Best Practices54
## ©
## 2026 Palo Alto Networks, Inc.

## Security Policy Best Practices
applications because there are tens of thousands of SaaS applications to control. If SaaS policy
recommendations are too strict, they may impact business applications. Be sure that you
understand applications and application types that you intend to block before you block them.
Use filters to focus on high-risk categories such as file transfer and CMS applications and to
check which applications have the highest usage. Focus on those categories and subcategories
first.
•Use as many context-based components as possible to create least privilege access policy
recommendations. Implement User-ID using the Cloud Identity Engine (CIE) (requires Azure
AD) to make necessary access exceptions to users and groups. Use Enterprise DLP to prevent
loss of sensitive data.
•For Strata Cloud Manager Managed Prisma Access, if your organization's administrative
policy permits it, add the SaaS Security app to the cloud management console. Use the cloud
management console to manage SaaS policy recommendations (and SaaS Security and other
cloud apps) instead of using standalone apps to gain the following benefits:
•Manage all cloud security elements from a single interface instead of from different app
interfaces.
•One administrator can perform all of SaaS policy recommendation actions, including adding
the rule to thePrisma Access rulebase. If you manage with the standalone app, then you
can create the policy recommendation but you have to switch to another app or handoff to
another administrator to add the rule to Prisma Access.
To use SaaS Security and Enterprise DLP in the cloud management console, you must
enable Web Security in the console. (This is a free feature, not a subscription.)
You can create SaaS policy recommendations using predefined policy recommendations and by
creating user-created policy recommendations.
## Policy Recommendation Workflow
This workflow is valid for IoT Security and for both the SaaS Security app (PAN-OS, Panorama
Managed Prisma Access) and the cloud management console (Strata Cloud Manager Managed
Prisma Access). Each step indicates which administrators are involved. It's helpful for each
administrator to understand the responsibilities of other administrators who are involved in policy
recommendations.
STEP 1 |(All Administrators) Create open lines of communication between administrators who
administer different parts of policy recommendation.
Policy recommendation often requires different administrators to work together to
recommend, import, and integrate new SaaS Security and IoT Security policy rules into the
PAN-OS or Prisma Access rulebase. Devise a process that ensures good communication
when an IoT Security or SaaS Security administrator hands off a policy recommendation to a
Panorama, firewall, or Prisma Access administrator. The handoff occurs after an IoT Security or
SaaS Security administrator creates a new rule, modifies an existing rule, or deletes a rule and
enables (submits in SaaS Security) or activates (IoT Security) the rule.
The administration workflow is:
- SaaS Security Administrators create new rule recommendations, add applications, users/
user groups, and DLP profiles, and set the action. They review rule recommendations
and then submit them to PAN-OS, Panorama Managed Prisma Access, or Strata Cloud
## Security Policy Best Practices55
## ©
## 2026 Palo Alto Networks, Inc.

## Security Policy Best Practices
Manager Managed Prisma Access. Review the guidelines for SaaS Security administrator
collaboration and authoring.
IoT Security Administrators evaluate automatically generated rule recommendations,
modify them as needed, create policy sets (groups of rule recommendations based on traffic
from IoT devices in the same device profile), and submit them to PAN-OS and Panorama
## Managed Prisma Access.
- PAN-OS and Prisma Access Administrators import SaaS and IoT policy recommendations.
They evaluate rule recommendations, import them, and add Security profile groups and
other objects to the rules. They also order the rules in the Security policy rulebase. When
Panorama pushes policy recommendations to firewalls and Prisma Access, the firewall and
Prisma Access administrators import the recommended rules.
Administrators must communicate to add the appropriate objects to the recommended
rules and understand the purpose of those rules.
For Strata Cloud Manager Managed Prisma Access, the same administrator may
handle both SaaS policy recommendations and Prisma Access duties, especially if
the administrator manages both apps on the cloud management console.
- SaaS and IoT Security Administrators update or delete a rule recommendation and then
submit the change to PAN-OS or Prisma Access.
PAN-OS and Prisma Access Administrators see the rule update or deletion and either
import the updated rule or delete the rule from PAN-OS or Prisma Access.
Communication among administrators is crucial so that all parties understand the purpose of
recommended rules, the purpose of rule updates, and why a rule is deleted. Communication
among administrators helps ensure that SaaS and IoT policy recommendations don't sit in
PAN-OS or Prisma Access waiting for an administrator to notice their presence and import
them into the rulebase.
STEP 2 |(SaaS Security and IoT Security Administrator) SaaS Security administrators need to assess the
risks of unsanctioned SaaS applications and IoT Security administrators need to understand
device profiles, which describe types of unmanaged devices on the network and their
behavior.
IoT Security automatically learns about unmanaged devices on the network and creates a
device profile for each set of similar devices. The profile describes the devices' characteristics.
Be familiar with SaaS applications and IoT devices on your network:
•SaaS—Wait for at least seven business days of data before you analyze an application for
policy recommendation. Gather enough data to understand the application and its business
usage.
IoT—Monitor the list of device profiles to see which ones are eligible for policy
recommendation. You can create a policy recommendation when the confidence rating for
a device profile reaches 90%, which indicates high confidence about device behavior. Some
## Security Policy Best Practices56
## ©
## 2026 Palo Alto Networks, Inc.

## Security Policy Best Practices
devices produce less traffic and can take time to achieve a high confidence rating. Allow
time for IoT Security to collect sufficient data to achieve a 90% confidence rating.
•SaaS—Understand how and why users use specific SaaS applications and if there are
business reasons to allow those applications.
IoT—Understand whether the discovered devices belong on your network. If your business
is banking, then seeing a medical device on your network may indicate an issue.
•SaaS—Assess the Security and Privacy, Identity Access Management, and Compliance
attributes of SaaS applications based on risk tolerance.
IoT—In medical environments, assess the compliance risk of medical IoT devices.
•SaaS—Tag sanctioned, tolerated, and unsanctioned applications to categorize them.
STEP 3 |(SaaS Security Administrator) Configure predefined SaaS policy recommendations. (IoT
Security administrators skip to Step 5.)
Predefined SaaS policy rule recommendations block application access, personal account
access, and content sharing and access, and enforce read-only access for appropriate users.
Adding applications to predefined recommendations is an easy way to start locking down SaaS
applications.
To use SaaS Security and Enterprise DLP in the cloud management console, you must
enable Web Security in the console. (This is a free feature.)
In the cloud management console, the same administrator may be able to create SaaS
policy recommendations and import them into Prisma Access.
1.Select a predefined rule. (Discovered Apps > Policy Recommendations in the cloud
management console or Visibility > Security Rules in the SaaS Security console.)
2.Select and add applications to the rule. If the rule doesn't apply to all users, add users and
user groups. Be sure that you understand applications and application types that you intend
to block before you block them, and understand who needs to use certain applications for
business purposes.
Focus on risky application types first, such as file sharing, content management, and
collaboration and productivity applications. Reduce uploads to file sharing sites so that
only users who need to upload for business purposes have access to only the file sharing
applications used for business purposes.
3.If you have an Enterprise DLP license (best practice), add a DLP profile to inspect traffic for
sensitive information and protect against unauthorized access, including predefined profiles
for supported DLP applications.
4.Verify that the rule does what you want it to do in the way you want to do it.
- Save the default rule.
- Enable the rule to submit it to PAN-OS or Prisma Access. You must enable rules for PAN-
OS or Prisma Access administrators to import them.
Communicate about enabled rule(s) with the administrator who is responsible for checking,
evaluating, and importing SaaS policy recommendations.
## Security Policy Best Practices57
## ©
## 2026 Palo Alto Networks, Inc.

## Security Policy Best Practices
STEP 4 |(SaaS Security Administrator) Configure user-defined SaaS policy recommendations. (IoT
Security administrators skip to Step 5.)
Use the filters in the Discovered Applications view to find applications and their usage metrics
and to help you understand whether to block or allow an application. Focus on the riskiest
application categories, such as file transfer, content management, and collaboration and
## Security Policy Best Practices58
## ©
## 2026 Palo Alto Networks, Inc.

## Security Policy Best Practices
productivity applications. High Risk applications that also have high Usage tend to have the
highest risk potential. Select applications to see who uses the application and how they use it.
When you configure policy recommendations and submit them, PAN-OS and Prisma
Access create any attached HIP profiles, tags, and application groups automatically.
If you have an Enterprise DLP license on the target firewalls, the DLP profile is also
created (otherwise, the submission fails). The submission fails if the SaaS Security
administrator adds any other types of profiles to a rule recommendation and those
profiles do not already exist on the firewall. If the attached profile objects exist on the
firewall, the submission succeeds. (The PAN-OS or Prisma Access administrator can
add profiles to imported rule recommendations. In Strata Cloud Manager Managed
Prisma Access, you can only add profile groups, not individual profiles.)
The appropriate licenses for profiles need to be on all firewalls that import SaaS policy
recommendations.
User groups from CIE are consistent across your organization. If you don't use CIE or if
you can't sync from CIE, Users & Groups configuration is not available in SaaS Security
and you can't base SaaS policy recommendations on users. The best practice is to
use CIE and create application policy based on who needs to access applications for
business purposes.
To enforce SaaS Security and Enterprise DLP, you must enable Web Security in the
cloud management console. (This is a free feature.)
In the cloud management console, the same administrator may be able to create SaaS
policy recommendations and import them into Prisma Access.
To configure best practices SaaS policy recommendations:
1.Create new SaaS Security policy recommendations:
•SaaS Security console: Visibility > Security Rules > Create New Rule
•Cloud management console: Discovered Apps > Policy Recommendations > Add Policy
2.Follow best practices for specifying the rule Name and Description.
3.Add applications to the rule.
Use the category, risk, and capabilities filters to find SaaS applications. Add applications to
the rule directly from the filter results. Focus on the riskiest, highest usage applications first.
4.Select the User Activity to detect. All the applications selected for the rule must support
the selected user activities. If an application doesn't support an activity, the interface
returns an error.
5.Configure the rest of the rule's parameters:
•Users & Groups—You must use and sync from CIE to specify users and groups in SaaS
policy recommendation.
•Device Posture—Specify which types of devices can access the rule's applications. When
a rule is imported in PAN-OS or Prisma Access, the device posture automatically creates
a Host Information Profile (HIP) object for mobile devices.
•Data Profile—You must have an Enterprise DLP license in SaaS Security and on targeted
firewalls to use this feature. With an Enterprise DLP subscription, you can create rules
## Security Policy Best Practices59
## ©
## 2026 Palo Alto Networks, Inc.

## Security Policy Best Practices
for a specific DLP profile and block applications only if they contain data that matches
the profile.
•Response—Allow or Block the traffic that matches the rule. Most recommendations are
block rules to prevent over-provisioning access.
6.Verify that the rule does what you want it to do in the way you want to do it.
- Save the rule.
- Enable the rule to submit it to PAN-OS or Prisma Access. You must enable rules for PAN-
OS or Prisma Access administrators to import them.
Communicate about enabled rule(s) with the PAN-OS or Prisma Access administrator who is
responsible for checking, evaluating, and importing SaaS policy recommendations.
Create SaaS policy rule recommendations provides more details about the
workflow.
STEP 5 |(IoT Security Administrator) Configure IoT policy recommendations (PAN-OS and Panorama
Managed Prisma Access only) in the IoT Security app.
IoT Security automatically generates IoT policy recommendations based on the behavior of
devices that belong to a device profile when IoT Security reaches a confidence score (the
level of confidence IoT Security has in its identification of a device) of 90% or higher for the
profile. The confidence score rises over time as IoT Security gathers more information about
## Security Policy Best Practices60
## ©
## 2026 Palo Alto Networks, Inc.

## Security Policy Best Practices
the devices. You can edit automatically generated rules before you submit them to Panorama,
firewalls, or Prisma Access.
IoT Security doesn't provide policy recommendations for IT devices such as PCs, smart
phones, or tablets, but IoT Security does identify those devices.
Use the automatic policy recommendations to create policy rule sets based on the behavior
of IoT devices in the same device profile across multiple IoT Security tenants. A policy rule set
includes the policy rule recommendations you select to control the devices in a device profile.
1.Create new IoT Security policy recommendations in either of two ways:
•Navigate to the Profiles page, hover the cursor over a profile name, and click Create
Policy Set in the pop-up.
•Profiles > <profile-name> > Behaviors, select Outbound Behaviors, select Create Policy,
and then click Next.
- Select Policies shows the automatically generated policy recommendations for the selected
device profile, including the applications the devices use.
1.Make sure the applications you see in the list are appropriate for the devices. For
example, you shouldn't see the iTunes application when you're looking at printers or
cameras. If you see unexpected applications in the list, the device may be compromised.
Know your devices and device profiles so that you can craft appropriate
recommendations to govern them.
2.Check Alerts Raised. Investigate applications with a high number of alerts before you
add them to the policy set, especially if the alerts are high or critical severity.
3.Select the policies you want to apply to the devices. These policies are included in the
policy set for the device profile.
If you don't see an application that you want to include in the policy set, Add Rule to
manually select an application and a destination type and Create the rule.
4.By default, the rule applies to all (Any) destinations detected in traffic for the device
profile. If you want to restrict the destinations for an application, click Destination > Any,
## Security Policy Best Practices61
## ©
## 2026 Palo Alto Networks, Inc.

## Security Policy Best Practices
toggle Allow any destination off, and uncheck destinations you don't want to allow in
the list.
5.When you are satisfied the policy set contains the rules you want, select Next.
3.In Firewall Configuration > Policy configurations, modify automatically generated
recommendations as needed. Policy configurations shows the selected applications.
•Follow best practices for specifying the policy set Name and Description. Be sure the
name identifies what the rule does and the description indicates the rule's purpose.
•Leave Services as application-default to prevent applications from using non-standard
ports, which is an indication of evasive, potentially malicious behavior.
•Add Security profiles and Security profile groups, log forwarding profiles, and other
objects in Panorama or on firewalls, not in the IoT Security app.
4.Review the policy set. When you're sure it's configured as you want it, Create the policy set,
which also saves it.
- Activate Policy Set to make the policy rule recommendation available for import on
Panorama and individual firewalls.
Communicate about enabled rule(s) with the PAN-OS or Prisma Access administrator who is
responsible for checking, evaluating, and importing IoT policy recommendations.
Create an IoT Policy Set provides more details about the workflow.
STEP 6 |(Panorama and firewall Administrators) (Strata Cloud Manager Managed Prisma Access
administrator for SaaS Security only) Evaluate, import, and if necessary, modify policy rule
recommendations.
Because the cloud management console enables management of all cloud apps in one
place, the Strata Cloud Manager Managed Prisma Access administrator might be the
same administrator who created the SaaS Security policy recommendations.
Before you import rules:
•Create Security profile groups on Panorama, firewalls, and/or the cloud management
console that are ready for you to apply to imported SaaS Security and IoT Security policy
recommendations. At the least, create profile groups that alert on most traffic and block
known malicious traffic to maintain availability As you understand policy recommendations
## Security Policy Best Practices62
## ©
## 2026 Palo Alto Networks, Inc.

## Security Policy Best Practices
better over time, follow Security profile best practices to make the profile groups as strict as
possible without endangering the ability to access critical business applications and devices.
For SaaS profile groups, know the types of applications and understand who users the
applications to determine which profiles to use and how strict they should be at the start.
For IoT profile groups, know your devices and device profiles so that you can craft
appropriate Security profile groups to govern them. Understand what the application in the
rule means so you can apply the appropriate Security profiles to the group.
When you create Security profile groups, consult with the IoT Security and/or SaaS Security
administrator to ensure that the Security profile groups make sense for IoT and SaaS policy
recommendations.
•In IoT Security deployments, enable Device-ID in each zone in which you want to
control IoT devices. Device-ID is to IoT devices what User-ID is to users and App-ID is to
applications—a unique identifier. In zones without Device-ID enabled, you can't enforce
Security policy on IoT devices.
•SaaS policy recommendation requires the App-ID Cloud Engine (ACE), which identifies tens
of thousands of SaaS applications so you can create Security policy to control them. ACE
requires Log Forwarding to Strata Logging Service. Follow Log Forwarding best practices
when you create the Strata Logging Service profile.
If you use ACE App-IDs in any Security policy rule, even if the rule applies only to
one user or user group, the firewall enforces the ACE App-ID for all users. (Once
you use the ACE App-ID in policy, the firewall enforces the App-ID the same way it
enforces content-provided App-IDs.)
To import SaaS and IoT policy recommendations:
1.Periodically check for imported rules. Refresh the IoT or SaaS policy recommendation page
to ensure that you see the latest policy recommendations:
•Panorama: Panorama > Policy Recommendation > SaaS or Panorama > Policy
Recommendation > IoT.
•Firewalls: Device > Policy Recommendation > SaaS or Device > Policy Recommendation
> IoT.
•Strata Cloud Manager Managed Prisma Access (SaaS Policy Recommendation only):
Select Policy Recommendation > Manage > Web Security > Web Access Policy, and
then select the Policy Recommendations tab to see New SaaS Rule Recommendations.
2.Select and evaluate new rules. Ensure all of the objects, addresses, etc., in the imported rule
make sense. If you're not sure about something in the recommendation, talk with the IoT
## Security Policy Best Practices63
## ©
## 2026 Palo Alto Networks, Inc.

## Security Policy Best Practices
Security or SaaS Security administrator to ensure that you understand the purpose of the
rule and its components.
For SaaS policy rule recommendations, ensure that user access to the applications isn't too
broad.
3.The rule import process enables you to modify the rule as well as position it in the Security
policy rulebase. Select a rule or rules to import, then:
•Panorama and PAN-OS firewalls: Import Policy Rule.
You can import up to ten IoT policy rules at a time.
•Strata Cloud Manager Managed Prisma Access (SaaS Policy Recommendation only):
## Actions > Import.
Do not finish the rule import until you complete the following steps to add Security
and Log Forwarding profiles, assess the rule, and select its order it in the Security
policy rulebase.
When you import a rule, PAN-OS and Prisma Access automatically create some of the rule's
objects in the policy rule:
•Importing IoT policy recommendations automatically creates the Device object, including
device-to-IP mappings, based on the IoT device profile.
After Panorama imports the Device object and pushes it to managed firewalls,
the firewalls pull down the device-to-IP mapping directly from the cloud.
Panorama is not involved in refreshing the device-to-IP mapping.
•Importing SaaS policy recommendations automatically creates any required HIP profiles,
tags, and application groups. For Enterprise DLP profiles, the target devices must have an
Enterprise DLP license. Any other profiles can only be imported if they already exist on
the target device.
4.Add a Security profile group to each rule.
Using profile groups instead of individual profiles is faster, easier, and prevents accidentally
omitting a profile from a rule. It also enables you to start with a profile group that mostly
## Security Policy Best Practices64
## ©
## 2026 Palo Alto Networks, Inc.

## Security Policy Best Practices
alerts and easily replace it with a stricter profile group as you gain experience with SaaS
applications and IoT devices.
Applying profiles to SaaS application and IoT device rules differs:
•SaaS Security policy rule recommendations:
•PAN-OS and Panorama Managed Prisma Access— Apply Advanced Threat Prevention
and Advanced URL Filtering best practices profiles to SaaS application traffic.
•Strata Cloud Manager Managed Prisma Access—You can apply Security profile groups
to policy recommendations, but not individual Security profiles. Add Security profiles
to a profile group and apply the group to a rule.
The best practice Security profile recommendations for Strata Cloud
Manager Managed Prisma Access differ slightly from the recommendations
for PAN-OS and Panorama Managed Prisma Access.
•IoT Security policy rule recommendations—To prevent malicious behavior, make sure
Security profiles are appropriate for the device. Work with the IoT Security administrator
to understand the behavior and alerts for different devices shown in the device profiles.
Apply profiles to IoT policy recommendations based on behavior and alerts. Look for
common weaknesses in IoT devices, such as weak manufacturer credentials, connections
to risky URLs, out of date antivirus, allowing access to rogue devices, insecure protocols,
## Security Policy Best Practices65
## ©
## 2026 Palo Alto Networks, Inc.

## Security Policy Best Practices
and EOL operating systems, as well as devices that are unpatched or that can't be
patched.
•Apply Vulnerability Protection profiles and Anti-Spyware profiles (to prevent
command-and-control malware) to all devices.
•If a device has outbound traffic to the internet, especially to unknown destinations,
apply Advanced URL Filtering and Advanced Threat Prevention. If the device can send
files, add Advanced WildFire and File Blocking profiles.
•If the device has server ports and accepts incoming connections, apply DoS
Protection in addition to File Blocking, Advanced WildFire, and Advanced Threat
Prevention profiles.
5.Add a Log Forwarding profile to each rule.
•For IoT policy recommendations, add the IoT Security Default Profile - EAL Enabled
predefined Log Forwarding profile, which provides all the log types IoT Security requires,
including enhanced application logs.
•SaaS policy recommendation requires ACE to identify SaaS applications. ACE requires
Log Forwarding to Strata Logging Service, so Security policy rules based on SaaS
applications also require Log Forwarding to Strata Logging Service.
After you import rules, you can apply Log Forwarding profiles to multiple rules
at one time using Log Forwarding for Security Services in Policy Optimizer to
identify Security policy rules that don’t have a Log Forwarding profile attached
(select None in the filter).
6.In Panorama and in Strata Cloud Manager Managed Prisma Access, select whether the rule
is a pre-rule or a post-rule. (Does not apply to standalone firewalls.)
The precedence order for evaluating rules is pre-rules, then deployment-specific rules, then
post-rules. Strata Cloud Manager Managed Prisma Access pre- and post-rules reside in the
shared configuration folder. Panorama pre-rules and post-rules reside in Policies > Security.
In Panorama, you can specify device groups for the rule.
7.Select the rule that you want the imported rule to go after in the Security policy rulebase.
Follow rulebase best practices.
Do not choose No Rule Selection, which places the rule at the top of the Security
policy rulebase. The top of the rulebase is often the wrong place for a new rule.
For example, a new allow rule won't be subject to critical rules that block known
malicious traffic. A new block rule may block access for legitimate users if it isn't
placed after an allow rule for the application's legitimate users. Order each rule
appropriately in the rulebase.
8.Check the rule and if you're satisfied with it, import it.
•Strata Cloud Manager Managed Prisma Access—Import.
•Panorama and standalone firewalls—OK.
After importing rules, Panorama administrators must push the rules to managed firewalls
and firewall administrators must import them before they become active on the firewall.
## Security Policy Best Practices66
## ©
## 2026 Palo Alto Networks, Inc.

## Security Policy Best Practices
Refresh Device > Policy Recommendation > IoT or Device > Policy Recommendation >
SaaS to see the newest recommendations.
Firewall administrators may need to modify rules after importing them. Firewall
administrators should check with Panorama, SaaS Security, or IoT Security administrators
if they're not sure about the purpose of the rule.
Check the Security policy rulebase to ensure that the rule is in the proper order.
9.(IoT Security only) After importing the rule, view the Device Object to check the attribute
filters for the device.
Use IoT device attributes in Security policy to better identify devices. Importing an IoT
policy rule automatically imports the attributes associated with the device and creates its
Device-ID. Device-ID is to IoT devices what User-ID is to people. Although there are six
device attributes, firewalls often receive only one attribute from a device. If the Device
Object (Objects > Devices) specifies attributes that the device doesn't send to the firewall,
then the traffic doesn't match the device and the rule doesn't control the device, so only
specify attributes that devices send to the firewall.
Click the Device-ID in the rule to pop up its associated Device Object.
Run the CLI command show iot ip-device-mapping-mp all or show iot
ip-device-mapping-mp ip <IP-address> to validate that the firewall receives
the attributes imported with the rule. If the firewall doesn't receive an attribute that's
configured in the Device Object, remove the attribute from the device object.
For detailed configuration procedures, refer to the appropriate Administrator's Guide:
•IoT Security:
•Import procedure
•Import a Policy Set into Panorama
•Configure Device-ID
•SaaS Security:
•PAN-OS and Panorama Managed Prisma Access—Import SaaS Policy Recommendations
(For standalone firewalls; on Panorama, you also specify whether the imported rule is a
pre- or post-rule and push the rule to firewalls after importing it in Panorama.)
•Strata Cloud Manager Managed Prisma Access—View SaaS policy recommendations,
Import new SaaS policy recommendations.
STEP 7 |(All Administrators) Update and delete policy recommendations as needed to keep the
Security policy rulebase up to date.
Importing policy recommendations is an ongoing process. Administrators recommend new
rules, modify rules, and delete old rules. The IoT device population grows and device postures
change over time. The number of SaaS applications increases and the applications your
enterprise tags as sanctioned, tolerated, and unsanctioned change over time. Create checklists
## Security Policy Best Practices67
## ©
## 2026 Palo Alto Networks, Inc.

## Security Policy Best Practices
of daily, weekly, and monthly items to monitor and maintain visibility into IoT devices and SaaS
applications.
Procedures to import updated policy recommendations:
•IoT Security: Modify and update IoT policy rule recommendations includes both the IoT
Security and PAN-OS steps.
•SaaS Security:
•SaaS Security Inline—Modify Active SaaS Policy Rule Recommendations shows how to
modify an existing rule in SaaS Security.
•Strata Cloud Manager Managed Prisma Access—Update Imported SaaS Policy Rule
Recommendations on Strata Cloud Manager Managed Prisma Access.
If the same administrator is both the SaaS policy recommendation and Prisma
Access administrator, you can enable automatic updates to automatically apply rule
recommendation changes.
•Panorama Managed Prisma Access and PAN-OS—Import Updated SaaS Policy
Recommendation shows how to check for and import updated SaaS Security policy
recommendations.
Procedures to remove deleted policy recommendations:
•IoT: Delete and remove policy rule recommendations includes both the IoT Security and
PAN-OS steps.
•SaaS Security:
•SaaS Security Inline—Delete SaaS Policy Rule Recommendations shows how to delete an
existing rule in SaaS Security.
•Strata Cloud Manager Managed Prisma Access—Remove Deleted SaaS Policy Rule
Recommendations on Strata Cloud Manager Managed Prisma Access.
•Panorama Managed Prisma Access and PAN-OS—Remove Deleted SaaS Policy
## Recommendation.
## Security Policy Best Practices68
## ©
## 2026 Palo Alto Networks, Inc.

## Security Policy Best Practices
## Maintain Security Policy Best Practices
After you plan and deploy Security policy best practices, maintain your best practice deployment
as your network and its applications, users, devices, and infrastructure change.
STEP 1 |Keep all security subscriptions current to avoid gaps in coverage.
STEP 2 |Keep up with Applications and Threats content updates and follow best practices for
Applications and Threats content updates.
STEP 3 |Review Release notes for the latest features, changes to default behavior, issues, etc.
STEP 4 |Create daily, weekly, monthly (and any other period you need) maintenance checklists.
Security policy deployment maintenance is a recursive task because new applications, users,
and IoT devices are continuously added to and deleted from your environment as things
change over time. For example, checklists can include:
•Evaluating Applications and Threats content updates.
•Using Policy Optimizer for managing applications.
•Reviewing IoT and SaaS policy recommendations and updates. The posture of IoT devices
may change over time and SaaS applications used may change over time or need to be
treated differently and require updating. Keep sanctioned/tolerated/unsanctioned tags for
applications updated.
•Setting times to run Security posture analysis tools.
•Reviewing behavior changes and issues documented in the release notes.
•Reviewing Security policy rules to see if you can tighten them or if they are no longer
needed.
STEP 5 |Maintain App-ID in Security policy:
•Review new and modified content-delivered App-IDs and adjust rules as necessary.
•As you add new applications to your network, include them in specific, granular policy rules.
Use tags and application filters to automate adding sanctioned applications, including new
App-ID Cloud Engine applications, to rules.
•When your company stops using an application, remove it from allow rules to prevent
unauthorized use.
•Regularly review the applications your Security policy rules allow.
STEP 6 |Maintain User-ID in Security policy:
•As you add new users to your network, add them to the appropriate user groups to control
their access and include them in policy, or add them directly to rules if they belong to no
group.
•As users leave the company or as their contracts end, remove them from user groups to
prevent access. Remove individuals from rules if they weren't added as part of a group.
•Continue to follow best practices for user group mapping and best practices for dynamic
user groups (DUGs) as you add and remove users from groups and policy rules.
## Security Policy Best Practices69
## ©
## 2026 Palo Alto Networks, Inc.

## Security Policy Best Practices
STEP 7 |Maintain and update Security profiles and profile groups as your network and goals evolve.
When you add new allow rules, ensure that they have the appropriate Security profiles
attached.
STEP 8 |Update Log Forwarding as needed as for new rules and applications:
•Apply an appropriate Log Forwarding profile to every new Security policy rule or use a
default Log Forwarding profile to automatically apply a Log Forwarding profile to new rules.
If you use a default profile, check the rule to ensure that the default profile is appropriate
and if not, replace it with an appropriate profile.
•Periodically review what you’re logging and what you’re not logging and how you’re logging
it. Ensure that you’re logging the traffic you want to log and logging all the information you
want to log for Security Operating Center (SOC) operations.
•Update log forwarding profiles as administrators join and leave the company.
•As new applications come into your network, update Log Forwarding to accommodate
them.
STEP 9 |Use security posture analysis tools to check your best practices deployment:
•In PAN-OS and Prisma Access, use Strata Cloud Manager to check Security policy as you
create it.
•Use the Strata Cloud Manager Zero Trust Posture Center to continuously monitor and
measure progress toward a best practices deployment.
•Run the Security Lifecyle review (SLR) quarterly to get a better view into your network.
STEP 10 |Use firewall tools to check activity and adjust Security policy as needed.
•Use log information in PAN-OS (also applies to Panorama Managed Prisma Access) and
Strata Cloud Manager Managed Prisma Access to investigate and monitor traffic.
•Use the Application Command Center to see graphical summaries of applications, users,
threats, URLs, and content that traverses your network.
•Use App Scope reports to help understand changes in application usage and user activity,
bandwidth usage, and network threats.
•Create Custom reports to view the exact data you want to investigate.
STEP 11 |Check Policy Optimizer regularly to examine the rulebase and find and fix unused rules, over-
provisioned rules, and rules with unused applications. Add checking Policy Optimizer to your
regularly scheduled maintenance.
## Security Policy Best Practices70
## ©
## 2026 Palo Alto Networks, Inc.

## Security Policy Best Practices
STEP 12 |Use SecOps tools and services to monitor your entire security posture proactively, help
prevent threats, and investigate issues:
•Cortex XSIAM combines SOC analytics for proactive monitoring with SIEM capabilities.
•Cortex XSOAR provides comprehensive security orchestration, automation, and
response,including response playbooks, for comprehensive threat intelligence management
and real-time collaboration.
•Cortex XDR provides an extended detection and response platform that monitors and
manages cloud, network, and endpoint events and data.
•SOC Services such as SecOps Prevention Posture Assessment, optimization, and learning
workshops.
STEP 13 |The following resources provide more information about Palo Alto Networks platforms,
features, and support:
•The Security Best Practices Documentation Portal contains standalone books such as
IoT Security Best Practices, Administrative Access Best Practices, and Decryption Best
Practices, and links to best practices topics in various administrator's guides.
•Administrator's Guides:
•PAN-OS Administrator's Guide
•Prisma Access Administrator's Guide (Panorama Managed Prisma Access and Strata
## Cloud Manager Managed Prisma Access)
•SaaS Security Administrator’s Guide
•IoT Security Administrator's Guide
•Documentation Portals:
•Cloud Delivered Security Services (CDSS) documentation portal
•Cloud Identity Engine (CIE) documentation portal
•GlobalProtect documentation portal
•Palo Alto Networks Customer Support Portal
•Monitor Your IoT Security Deployment Using Best Practices
•IoT Security Solution Structure (summary of how the IoT Security solution works)
•SaaS Security on Prisma Access (Panorama Managed Prisma Access and Strata Cloud
## Manager Managed Prisma Access)
•Troubleshoot issues on SaaS Security Inline
## Security Policy Best Practices71
## ©
## 2026 Palo Alto Networks, Inc.

## Security Policy Best Practices
## Security Policy Best Practices72
## ©
## 2026 Palo Alto Networks, Inc.