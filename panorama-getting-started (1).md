# Panorama Getting Started
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
© 2025-2026 Palo Alto Networks, Inc. Palo Alto Networks is a registered trademark of Palo
Alto Networks. A list of our trademarks can be found at www.paloaltonetworks.com/company/
trademarks.html. All other marks mentioned herein may be trademarks of their respective companies.
Last Revised
January 21, 2026
Panorama Getting Started 2 ©2026 Palo Alto Networks, Inc.
Table of Contents
Panorama Overview.......................................................................................... 5
About Panorama.......................................................................................................................... 6
Panorama Models........................................................................................................................ 8
Centrally Manage Firewall Configuration and Updates with Panorama...................... 11
Switch Context Between Panorama and Firewall Views..................................... 11
Total Configuration Size for Panorama.................................................................... 12
Templates and Template Stacks................................................................................ 16
Device Groups................................................................................................................ 17
Centralized Logging and Reporting using Panorama........................................................ 23
Managed Collectors and Collector Groups............................................................. 23
Local and Distributed Log Collection........................................................................24
Caveats for a Collector Group with Multiple Log Collectors.............................. 25
Log Forwarding Options.............................................................................................. 28
Centralized Reporting................................................................................................... 29
Data Redistribution Using Panorama................................................................................... 31
Role-Based Access Control.....................................................................................................32
Administrative Roles..................................................................................................... 32
Authentication Profiles and Sequences....................................................................34
Access Domains............................................................................................................. 35
Administrative Authentication....................................................................................36
Panorama Commit, Validation, and Preview Operations.................................................38
Plan Your Panorama Deployment............................................................... 41
Determine Panorama Log Storage Requirements............................................................. 43
Deploy Panorama...................................................................................................................... 45
Cheat Sheet: Manage Prisma Access by Using Panorama.............................................. 46
Set Up Panorama............................................................................................. 49
Manage Large-Scale Firewall Deployments with Panorama...........................................50
Determine the Optimal Large-Scale Firewall Deployment Solution..................50
Increased Device Management Capacity for M-Series and Panorama Virtual
Appliance..........................................................................................................................51
Set Up the Panorama Virtual Appliance..............................................................................54
Setup Prerequisites for the Panorama Virtual Appliance.....................................55
Install the Panorama Virtual Appliance.................................................................... 59
Perform Initial Configuration of the Panorama Virtual Appliance................... 123
Set Up The Panorama Virtual Appliance as a Log Collector............................. 127
Set Up the Panorama Virtual Appliance with Local Log Collector...................135
Set up a Panorama Virtual Appliance in Panorama Mode.................................140
Panorama Getting Started 3 ©2026 Palo Alto Networks, Inc.
Table of Contents
Set up a Panorama Virtual Appliance in Management Only Mode................. 141
Expand Log Storage Capacity on the Panorama Virtual Appliance................. 142
Increase CPUs and Memory on the Panorama Virtual Appliance....................171
Increase the System Disk on the Panorama Virtual Appliance.........................178
Complete the Panorama Virtual Appliance Setup............................................... 218
Convert Your Panorama Virtual Appliance........................................................... 219
Set Up the M-Series Appliance...........................................................................................231
M-Series Appliance Interfaces................................................................................. 231
Perform Initial Configuration of the M-Series Appliance.................................. 233
Perform Initial Configuration of an Air Gapped M-Series Appliance.............. 239
M-Series Setup Overview......................................................................................... 243
Set Up the M-Series Appliance as a Log Collector............................................. 246
Increase Storage on the M-Series Appliance....................................................... 257
Configure Panorama to Use Multiple Interfaces................................................. 264
Register Panorama and Install Licenses............................................................................ 273
Register Panorama...................................................................................................... 274
Activate a Panorama Support License................................................................... 275
Activate/Retrieve a Firewall Management License when the Panorama Virtual
Appliance is Internet-connected..............................................................................276
Activate/Retrieve a Firewall Management License when the Panorama Virtual
Appliance is not Internet-connected...................................................................... 277
Activate/Retrieve a Firewall Management License on the M-Series
Appliance....................................................................................................................... 280
Install the Panorama Device Certificate............................................................................283
Install the Device Certificate for a Dedicated Log Collector........................................286
Access and Navigate Panorama Management Interfaces............................................. 289
Log in to the Panorama Web Interface................................................................. 289
Navigate the Panorama Web Interface................................................................. 290
Log in to the Panorama CLI......................................................................................291
Panorama Getting Started 4 ©2026 Palo Alto Networks, Inc.
Panorama Overview
Where Can I Use This? What Do I Need?
```
• NGFW (Managed by Panorama) No prerequisites needed
```
The Panorama® management server provides centralized monitoring and administration for
multiple next-generation firewalls, WildFire® appliances, and appliance clusters. Managing a
distributed network of firewalls individually can be complex, time-consuming, and lacks a unified
view of network activity. Panorama solves these challenges by offering a single location to
oversee all applications, users, and content traversing your network, significantly increasing
operational efficiency and enabling you to enforce consistent application enablement policies.To
meet diverse network needs, it is available in multiple models, including the virtual appliance and
various M-Series hardware appliances. To simplify large-scale deployments, the server offers
powerful features for centralized configuration and deployment. You can use templates and
template stacks to configure common base network and device settings, while device groups
allow for the centralized administration of globally shared and local policy rules.Panorama
also streamlines routine maintenance by allowing you to centrally deploy licenses, PAN-OS®
software, and dynamic content updates across all managed devices from one location. To safely
```
delegate responsibilities, Role-Based Access Control (RBAC) enables distributed administration
```
by defining granular privileges to restrict or grant access to specific firewalls and configuration
areas.For comprehensive visibility, it aggregates logs from all managed firewalls, providing an
essential audit trail of network activity and configuration changes. Using integrated tools like
```
the Application Command Center (ACC), log viewers, and robust reporting capabilities, you can
```
centrally analyze traffic patterns, investigate security incidents, and identify potential threats
across the entire network. Additionally, the management server optimizes large networks
through data redistribution, which seamlessly shares essential User-ID™ data and authentication
timestamps with managed firewalls to ensure consistent policy enforcement and maximize device
capacity.
5
Panorama Overview
About Panorama
Where Can I Use This? What Do I Need?
```
• NGFW (Managed by Panorama) No prerequisites needed
```
Panorama enables you to effectively configure, manage, and monitor your Palo Alto Networks
firewalls with central oversight. The three main areas in which Panorama adds value are:
• Centralized configuration and deployment
To simplify central management and rapid deployment of the firewalls and WildFire appliances
on your network, use Panorama to pre-stage the firewalls and WildFire appliances for
deployment. You can then assemble the firewalls into groups, and create templates to apply a
base network and device configuration and use device groups to administer globally shared and
local policy rules. See Centrally Manage Firewall Configuration and Updates with Panorama.
• Aggregated logging with central oversight for analysis and reporting
Collect information on activity across all the managed firewalls on the network and centrally
analyze, investigate and report on the data. This comprehensive view of network traffic, user
activity, and the associated risks empowers you to respond to potential threats using the rich
set of policies to securely enable applications on your network. See Centralized Logging and
Reporting.
• Distributed administration
Enables you to delegate or restrict access to global and local firewall configurations and
policies. See Role-Based Access Control for delegating appropriate levels of access for
distributed administration.
Six Panorama Models are available: the Panorama virtual appliance, M-600 appliance, M-500
appliance, and M-200 appliance are supported in PAN-OS 10.0 and later releases. The M-300
appliance and M-700 appliance are supported in PAN-OS 10.2 and later releases.Panorama
```
Centralized Management illustrates how you can deploy Panorama in a high availability (HA)
```
configuration to manage firewalls.
Panorama Getting Started 6 ©2026 Palo Alto Networks, Inc.
Panorama Overview
Figure 1: Panorama Centralized Management
Panorama Getting Started 7 ©2026 Palo Alto Networks, Inc.
Panorama Overview
Panorama Models
Where Can I Use This? What Do I Need?
```
• NGFW (Managed by Panorama) No prerequisites needed
```
Panorama is available as one of the following virtual or physical appliances, each of which
supports licenses for managing up to 25, 100, or 1,000 firewalls. Additionally, M-600 and M-700
appliances support licenses for managing up to 5,000 firewalls and similarly resourced Panorama
virtual appliances support licenses for managing up to 2,500 firewalls:
• Panorama virtual appliance—This model provides simple installation and facilitates server
consolidation for sites that need a virtual management appliance. You can install Panorama on
```
Alibaba Cloud, Amazon Web Services (AWS), AWS GovCloud, Microsoft Azure, Google Cloud
```
```
Platform (GCP), KVM, Hyper-V, Oracle Cloud Infrastructure (OCI), a VMware ESXi server, or
```
on VMware vCloud Air. The virtual appliance can collect firewall logs locally at rates of up to
20,000 logs per second and can manage Dedicated Log Collectors for higher logging rates. The
virtual appliance can function as a dedicated management server, a Panorama management
server with local log collection capabilities, or as a Dedicated Log Collector. For the supported
interfaces, log storage capacity, and maximum log collection rates, see the Setup Prerequisites
for the Panorama Virtual Appliance. You can deploy the virtual appliance in the following
```
modes:
```
• Panorama mode
In this mode, the Panorama virtual appliance supports a local Log Collector with 1 to 12
```
virtual logging disks (see Deploy Panorama Virtual Appliances with Local Log Collectors).
```
Each logging disk has 2TB of storage capacity for a total maximum of 24TB on a single
```
virtual appliance and 48TB on a high availability (HA) pair. Only Panorama mode enables
```
you to add multiple virtual logging disks without losing logs on existing disks. Panorama
mode also provides the benefit of faster report generation. In Panorama mode, the virtual
appliance does not support NFS storage.
• Management Only mode
In this mode, the Panorama virtual appliance is a dedicated management appliance for your
managed devices and Dedicated Log Collectors. Additionally, an appropriately resourced
Panorama virtual appliance can manage up to 2,500 firewalls in this mode. The Panorama
virtual appliance has no log collection capabilities except for config and system logs and
requires a Dedicated Log Collector to these store logs. By default, the virtual appliance in
Management Only mode has only one disk partition for all data so all logs forwarded to a
Panorama virtual appliance in Management Only mode are dropped. Therefore, to store
the log data from your managed appliances, you must configure log forwarding in order to
store the log data from your managed devices. For more information, see Increased Device
Management Capacity Requirements.
• Log Collector mode
The Panorama virtual appliance functions as a Dedicated Log Collector. If multiple firewalls
forward large volumes of log data, a Panorama virtual appliance in Log Collector mode
provides increased scale and performance. In this mode, the appliance does not have a web
Panorama Getting Started 8 ©2026 Palo Alto Networks, Inc.
Panorama Overview
```
interface for administrative access; it has only a command line interface (CLI). However, you
```
can manage the appliance using the web interface of the Panorama management server. CLI
access to a Panorama virtual appliance in Log Collector mode is necessary only for initial
setup and debugging. For configuration details, see Deploy Panorama with Dedicated Log
Collectors.
• As of September 1, 2025, the legacy mode is no longer supported on Panorama. For
additional information, see the official end-of-life notice.
• M-Series appliance—The M-200, M-300, M-500, M-600, and M-700 appliances are dedicated
hardware appliances intended for large-scale deployments. In environments with high logging
```
rates (over 10,000 logs per second) and log retention requirements, these appliances enable
```
scaling of your log collection infrastructure. For the supported interfaces, log storage capacity,
and maximum log collection rates, see M-Series Appliance Interfaces. All M-Series models
share the following attributes:
• RAID drives to store firewall logs and RAID 1 mirroring to protect against disk failures
• SSD to store the logs that Panorama and Log Collectors generate
• MGT, Eth1, Eth2, and Eth3 interfaces that support 1Gbps throughput
• Redundant, hot-swappable power supplies
• front-to-back airflow
The M-500 and M-600 appliances have the following additional attributes, which make them
more suitable for data centers:
• Eth4 and Eth5 interfaces that support 10Gbps throughput
Additionally, the following attribute makes the M-600 and M-700 appliances more suitable for
large-scale firewall deployments:
• The M-600 and M-700 appliances in Management Only mode can manage up to 5,000
firewalls.
You can deploy the M-Series appliances in the following modes:
• Panorama mode
The appliance functions as a Panorama management server to manage firewalls and
Dedicated Log Collectors. The appliance also supports a local Log Collector to aggregate
firewall logs. Panorama mode is the default mode. For configuration details, see Deploy
Panorama M-Series Appliances with Local Log Collectors.
• Management Only mode
The Panorama appliance is a dedicated management appliance for your managed devices
and Dedicated Log Collectors. The Panorama appliance has no log collection capabilities
except for config and system logs and your deployment requires a Dedicated Log Collector
to store these logs. By default, the Panorama appliance in Management Only mode has
only one disk partition for all data so all logs forwarded to a Panorama virtual appliance in
Management Only mode are dropped. Therefore, to store the log data from your managed
Panorama Getting Started 9 ©2026 Palo Alto Networks, Inc.
Panorama Overview
appliances, you must configure log forwarding in order to store the log data from your
managed devices.
• Log Collector mode
The appliance functions as a Dedicated Log Collector. If multiple firewalls forward large
volumes of log data, an M-Series appliance in Log Collector mode provides increased
scale and performance. In this mode, the appliance does not have a web interface for
```
administrative access; it has only a command line interface (CLI). However, you can manage
```
the appliance using the web interface of the Panorama management server. CLI access to an
M-Series appliance in Log Collector mode is necessary only for initial setup and debugging.
For configuration details, see Deploy Panorama with Dedicated Log Collectors.
For more details and specifications for the M-Series appliances, see the M-Series Appliance
Hardware Reference Guides.
Panorama Getting Started 10 ©2026 Palo Alto Networks, Inc.
Panorama Overview
Centrally Manage Firewall Configuration and Updates
with Panorama
Where Can I Use This? What Do I Need?
```
• NGFW (Managed by Panorama) No prerequisites needed
```
Panorama™ uses device groups and templates to group firewalls into logical sets that require
similar configuration. You use device groups and templates to centrally manage all configuration
elements, policies, and objects on the managed firewalls. Panorama also enables you to centrally
```
manage licenses, software (PAN-OS® software, SSL-VPN client software, GlobalProtect™ agent/
```
```
app software), and content updates (Applications, Threats, WildFire®, and Antivirus). All device
```
group, template, and template stack configuration objects are required to have a unique name.
In the event an unforeseen restart of your managed firewall or Panorama occurs, all uncommitted
configuration changes in your device groups and templates are preserved locally until you
successfully commit the changes. A restart can be the restart of the firewall or Panorama or
of a PAN-OS management process related to configuration management. For firewalls or
```
Panorama in a high availability (HA) configuration, the uncommitted configuration changes do not
```
automatically sync across the HA peers in the event of an unforeseen restart.
Switch Context Between Panorama and Firewall Views
Where Can I Use This? What Do I Need?
```
• NGFW (Managed by Panorama) No prerequisites needed
```
The Panorama™ web interface enables you to toggle between a Panorama-centric view and a
firewall-centric view using the Context drop-down at the top-left of every tab. Set the Context
to Panorama to manage firewalls centrally or switch context to the web interface of a specific
firewall to configure it locally. The similarity of the Panorama and firewall web interfaces enables
you to seamlessly move between them to monitor and manage firewalls.
The Context drop-down lists only the firewalls that are connected to Panorama. For a Device
Group and Template administrator, the drop-down lists only the connected firewalls that are
within the Access Domains assigned to that administrator. To search a long list, use the Filters
within the drop-down.
```
For firewalls in a high availability (HA) configuration, the icons have colored backgrounds to
```
```
indicate the HA state (as follows). Knowing the HA state is useful when selecting a firewall
```
context. For example, you generally make firewall-specific configuration changes on an active
firewall.
• Green
Active
Panorama Getting Started 11 ©2026 Palo Alto Networks, Inc.
Panorama Overview
• Yellow
```
Passive or the firewall is initiating (the initiating state lasts for up to 60 seconds after boot up).
```
• Red
```
The firewall is non-functional (error state), suspended (an administrator disabled the firewall),
```
```
or tentative (for a link or path monitoring event in an active/active HA configuration).
```
When you configure an admin role profile for a Device Group and Template admin, you must
assign a Device Admin Role that is pushed to your managed firewalls to context switch between
the Panorama and firewall web interface.
During the context switch, Panorama validates if the admin has access to a specific vsys or for all
vsys. If the admin has access to all vsys, then Panorama uses the device admin role context switch.
If the admin has access to one or some of the vsys, then Panorama uses the vsys admin role to
context switch.
Total Configuration Size for Panorama
Where Can I Use This? What Do I Need?
```
• NGFW (Managed by Panorama) No prerequisites needed
```
The total configuration file size of Panorama™ M-Series and virtual appliances is an important
piece of the performance metric when determining which M-Series appliance or the minimum
amount of virtual resources you need to allocate on your Panorama virtual appliance to ensure
that you meet your Security requirements. Exceeding the supported total configuration file size of
the Panorama management server results in reduced performance when performing configuration
changes, commits, and pushes to managed firewalls.
Starting with PAN-OS 11.1, both Panorama and managed firewalls proactively monitor
configuration size and alerts administrators when it nears or exceeds the recommended threshold.
The lower-end platforms with smaller configuration limits, might hit the warning during the config
push from Panorama.
The Panorama management server in Panorama mode supports a total configuration file size
of 80MB for all template, device group, and Panorama-specific configurations. The maximum
configuration file size supported by Panorama in Management Only mode depends on the
Panorama model or resources you allocate to the Panorama virtual appliance. Refer to the table
below for the recommended maximum configuration file size based on the Panorama M-Series
appliance model or on the resources you allocate to the Panorama virtual appliance.
Panorama Model Virtual Resources
Required
Maximum Configuration
File Size in Management
Only Mode
Maximum Configuration
File Size in Panorama
Mode
M-200 120 MB
M-300
N/A
150 MB
80 MB
Panorama Getting Started 12 ©2026 Palo Alto Networks, Inc.
Panorama Overview
Panorama Model Virtual Resources
Required
Maximum Configuration
File Size in Management
Only Mode
Maximum Configuration
File Size in Panorama
Mode
M-500 120 MB
M-600 150 MB
M-700 180 MB
• 16 vCPU
• 128GB memory
120 MBPanorama Virtual
Appliance
Refer to the Setup
Prerequisites for
the Panorama
Virtual Appliance
for additional
setup information.
• 56 vCPU
• 256GB memory
150 MB
Monitor Configuration Size
Where Can I Use This? What Do I Need?
```
• NGFW (Managed by Panorama) No prerequisites needed
```
```
(PAN-OS 11.1 and later releases) You can track the total configuration size as part of your regular
```
system health checks.
STEP 1 | View Configuration Size on the Dashboard.
1. Log in to the Panorama web interface.
2. In the Dashboard, locate the System Resources section.
The percentage comparison of the current configuration size against the maximum
supported limit appears.
STEP 2 | Drill Down into Configuration Components.
1. Select Dashboard > System Resources, and click the Configuration Size link.
The Configuration Size Distribution window provides a detailed breakdown of your
configuration by listing all components and their respective sizes. This helps you
Panorama Getting Started 13 ©2026 Palo Alto Networks, Inc.
Panorama Overview
determine exactly which device groups or templates constitute the majority of the
configuration.
Panorama Getting Started 14 ©2026 Palo Alto Networks, Inc.
Panorama Overview
STEP 3 | Review post-commit impact.
1. Perform a configuration change and initiate a Commit.
2. Wait for the commit to complete successfully.
3. Review the latest push details.
You can view the impact of the specific change on the configuration size.
```
The following screenshot is specific to the Commit-All or Push operations;
```
ensure you select the correct scope before finalizing.
4.
Operational Commands
Use the following CLI commands to retrieve detailed size metrics:
• • show management-server candidate config-size: Displays the size of the
current candidate configuration.
• show management-server last-committed config-size: Displays the size of the
running configuration.
• show config size distribution: Provides a percentage and megabyte breakdown
of configuration nodes for remediation.
The low-end firewalls are equipped with configuration file size capacity of 25–30 MB.
The pre-defined configurations occupy approximately 75% of this available space. Upon
installing standard content updates, the device reaches near-maximum capacity.
Panorama Getting Started 15 ©2026 Palo Alto Networks, Inc.
Panorama Overview
Templates and Template Stacks
Where Can I Use This? What Do I Need?
```
• NGFW (Managed by Panorama) No prerequisites needed
```
You use templates and template stacks to configure the settings that enable firewalls to
operate on the network. Templates are the basic building blocks you use to configure the
Network and Device tabs on Panorama™. You can use templates to define interface and zone
configurations, to manage the server profiles for logging and syslog access, or to define VPN
configurations. Template stacks give you the ability to layer multiple templates and create a
combined configuration. Template stacks simplify management because they allow you to define
a common base configuration for all devices attached to the template stack and they give you the
ability to layer templates to create a combined configuration. This enables you to define templates
with location- or function-specific settings and then stack the templates in descending order of
priority so that firewalls inherit the settings based on the order of the templates in the stack.
Both templates and template stacks support variables. Variables allow you to create placeholder
objects with their value specified in the template or template stack based on your configuration
needs. Create a template or template stack variable to replace IP addresses, Group IDs, and
interfaces in your configurations. Template variables are inherited by the template stack and you
can override them to create a template stack variable. However, templates do not inherit variables
defined in the template stack. When a variable is defined in the template or template stack and
pushed to the firewall, the value defined for the variable is displayed on the firewall.
Use templates to accommodate firewalls that have unique settings. Alternatively, you can push
a broader, common base configuration and then override certain pushed settings with firewall-
specific values on individual firewalls. When you override a setting on the firewall, the firewall
saves that setting to its local configuration and Panorama no longer manages the setting. To
restore template values after you override them, use Panorama to force the template or template
stack configuration onto the firewall. For example, after you define a common NTP server in a
template and override the NTP server configuration on a firewall to accommodate a local time
zone, you can later revert to the NTP server defined in the template.
When defining a template stack, consider assigning firewalls that are the same hardware model
and require access to similar network resources, such as gateways and syslog servers. This
enables you to avoid the redundancy of adding every setting to every template stack. The
following figure illustrates an example configuration in which you assign data center firewalls in
```
the Asia-Pacific (APAC) region to a stack with global settings, one template with APAC-specific
```
settings, and one template with data center-specific settings. To manage firewalls in an APAC
branch office, you can then re-use the global and APAC-specific templates by adding them to
another stack that includes a template with branch-specific settings. Templates in a stack have a
configurable priority order that ensures Panorama pushes only one value for any duplicate setting.
Panorama evaluates the templates listed in a stack configuration from top to bottom with higher
templates having priority. The following figure illustrates a data center stack in which the data
center template has a higher priority than the global template: Panorama pushes the idle timeout
value from the data center template and ignores the value from the global template.
Panorama Getting Started 16 ©2026 Palo Alto Networks, Inc.
Panorama Overview
Figure 2: Template Stacks
```
You cannot use templates or template stacks to set firewall modes: virtual private network (VPN)
```
```
mode, multiple virtual systems (multi-vsys) mode, or operational modes (normal or FIPS-CC mode).
```
For details, see Template Capabilities and Exceptions. However, you can assign firewalls that
have non-matching modes to the same template or stack. In such cases, Panorama pushes mode-
specific settings only to firewalls that support those modes. As an exception, you can configure
Panorama to push the settings of the default vsys in a template to firewalls that don’t support
virtual systems or that don’t have any virtual systems configured.
For the relevant procedures, see Manage Templates and Template Stacks.
Device Groups
Where Can I Use This? What Do I Need?
```
• NGFW (Managed by Panorama) No prerequisites needed
```
To use Panorama effectively, you have to group the firewalls in your network into logical units
called device groups. A device group enables grouping based on network segmentation, geographic
location, organizational function, or any other common aspect of firewalls that require similar
policy configurations. Using device groups, you can configure policy rules and the objects they
reference. You can organize device group hierarchically, with shared rules and objects at the top,
and device group-specific rules and objects at subsequent levels. This enables you to create a
hierarchy of rules that enforce how firewalls handle traffic. For example, you can define a set of
shared rules as a corporate acceptable use policy. Then, to allow only regional offices to access
peer-to-peer traffic such as BitTorrent, you can define a device group rule that Panorama pushes
```
only to the regional offices (or define a shared security rule and target it to the regional offices).
```
Panorama Getting Started 17 ©2026 Palo Alto Networks, Inc.
Panorama Overview
For the relevant procedures, see Manage Device Groups. The following topics describe device
group concepts and components in more detail:
Device Group Hierarchy
You can create a device group hierarchy to nest device groups in a tree hierarchy of up to four
```
levels, with lower-level groups inheriting the settings (policy rules and objects) of higher-level
```
groups. At the bottom level, a device group can have parent, grandparent, and great-grandparent
```
device groups (ancestors). At the top level, a device group can have child, grandchild, and great-
```
```
grandchild device groups (descendants). All device groups inheriting settings from the Shared
```
location—a container at the top of the hierarchy for configurations that are common to all device
groups.
Creating a device group hierarchy enables you to organize firewalls based on common policy
requirements without redundant configuration. For example, you could configure shared settings
that are global to all firewalls, configure device groups with function-specific settings at the
first level, and configure device groups with location-specific settings at lower levels. Without
a hierarchy, you would have to configure both function- and location-specific settings for every
device group in a single level under Shared.
Figure 3: Device Group Hierarchy
For details on the order in which firewalls evaluate policy rules in a device group hierarchy, see
Device Group Policies. For details on overriding the values of objects that device groups inherit
from ancestor device groups, see Device Group Objects.
In a multiple Panorama plugin deployment to perform, a device group containing firewalls
deployed in a particular hypervisor cannot be the child or parent of a device group containing
firewalls deployed in a different hypervisor. For example, if Panorama receives IP address updates
from VMware NSX-V and AWS, you cannot create a device group of NSX-V VM-Series firewalls
that is a child of an AWS VM-Series firewall device group.
Panorama Getting Started 18 ©2026 Palo Alto Networks, Inc.
Panorama Overview
Device Group Policies
Device groups provide a way to implement a layered approach for managing policies across a
```
network of managed firewalls. A firewall evaluates policy rules by layer (shared, device group,
```
```
and local) and by type (pre-rules, post-rules, and default rules) in the following order from top to
```
bottom. When the firewall receives traffic, it performs the action defined in the first evaluated
rule that matches the traffic and disregards all subsequent rules. To change the evaluation order
```
for rules within a particular layer, type, and rulebase (for example, shared Security pre-rules), see
```
Manage the Rule Hierarchy.
Whether you view rules on a firewall or in Panorama, the web interface displays them in
evaluation order. All the shared, device group, and default rules that the firewall inherits from
Panorama are shaded orange. Local firewall rules display between the pre-rules and post-rules.
Panorama Getting Started 19 ©2026 Palo Alto Networks, Inc.
Panorama Overview
Evaluation Order Rule Scope and Description Administration Device
Shared pre-rules
Device group pre-
rules
Panorama pushes shared pre-rules
to all the firewalls in all device
groups. Panorama pushes device
group-specific pre-rules to all the
firewalls in a particular device group
and its descendant device groups.
If a firewall inherits rules from
device groups at multiple levels
in the device group hierarchy, it
evaluates pre-rules in the order of
highest to lowest level. This means
the firewall first evaluates shared
rules and last evaluates the rules of
device groups with no descendants.
You can use pre-rules to enforce
the acceptable use policy of an
organization. For example, a pre-
rule might block access to specific
URL categories or allow Domain
```
Name System (DNS) traffic for all
```
users.
These rules are visible on firewalls
but you can only manage them in
Panorama.
Local firewall
rules
Local rules are specific to a single
```
firewall or virtual system (vsys).
```
A local firewall administrator, or
a Panorama administrator who
switches to a local firewall context,
can edit local firewall rules.
Device group
post-rules
Shared post-rules
Panorama pushes shared post-
rules to all the firewalls in all device
groups. Panorama pushes device
group-specific post-rules to all the
firewalls in a particular device group
and its descendant device groups.
If a firewall inherits rules from
device groups at multiple levels
in the device group hierarchy, it
evaluates post-rules in the order
of lowest to highest level. This
means the firewall first evaluates
the rules of device groups with
no descendants and last evaluates
shared rules.
Post-rules typically include rules
to deny access to traffic based on
the App-ID™ signatures, User-ID™
These rules are visible on firewalls
but you can only manage them in
Panorama.
Panorama Getting Started 20 ©2026 Palo Alto Networks, Inc.
Panorama Overview
Evaluation Order Rule Scope and Description Administration Device
```
information (users or user groups),
```
or service.
intrazone-default
interzone-default
The default rules apply only to
the Security rulebase, and are
```
predefined on Panorama (at the
```
```
Shared level) and the firewall (in
```
```
each vsys). These rules specify how
```
PAN-OS handles traffic that doesn’t
match any other rule.
The intrazone-default rule allows all
traffic within a zone. The interzone-
default rule denies all traffic
between zones.
If you override default rules, their
order of precedence runs from
the lowest context to the highest:
overridden settings at the firewall
level take precedence over settings
at the device group level, which
take precedence over settings at
the Shared level.
Default rules are initially read-
only, either because they are part
of the predefined configuration
or because Panorama pushed
them to firewalls. However, you
can override the rule settings for
tags, action, logging, and security
profiles. The context determines
the level at which you can override
the rules:
• Panorama—At the Shared or
device group level, you can
override default rules that
are part of the predefined
configuration.
• Firewall—You can override
default rules that are part of
the predefined configuration
on the firewall or vsys, or that
Panorama pushed from the
Shared location or a device
group.
Device Group Objects
Objects are configuration elements that policy rules reference, for example: IP addresses, URL
```
categories, security profiles, users, services, and applications. Rules of any type (pre-rules, post-
```
```
rules, default rules, and rules locally defined on a firewall) and any rulebase (Security, NAT, QoS,
```
```
Policy Based Forwarding, Decryption, Application Override, Captive Portal, and DoS Protection)
```
can reference objects. You can reuse an object in any number of rules that have the same scope
as that object in the Device Group Hierarchy. For example, if you add an object to the Shared
location, all rules in the hierarchy can reference that shared object because all device groups
inherit objects from Shared. If you add an object to a particular device group, only the rules in that
device group and its descendant device groups can reference that device group object. If object
values in a device group must differ from those inherited from an ancestor device group, you can
```
Override inherited object values (see Step Override inherited object values). You can also Revert
```
to Inherited Object Values at any time. When you Create Objects for Use in Shared or Device
Group Policy once and use them many times, you reduce administrative overhead and ensure
consistency across firewall policies.
You can configure how Panorama handles objects system-wide:
Panorama Getting Started 21 ©2026 Palo Alto Networks, Inc.
Panorama Overview
• Pushing unused objects
By default, Panorama pushes all objects to firewalls regardless of whether any shared or device
group policy rules reference the objects. Optionally, you can configure Panorama to push only
referenced objects. For details, see Manage Unused Shared Objects.
• Precedence of ancestor and descendant objects
By default, when device groups at multiple levels in the hierarchy have an object with the same
```
name but different values (because of overrides, as an example), policy rules in a descendant
```
device group use the object values in that descendant instead of object values inherited from
ancestor device groups or Shared. Optionally, you can reverse this order of precedence to
push values from Shared or the highest ancestor containing the object to all descendant device
groups. For details, see Manage Precedence of Inherited Objects.
Panorama Getting Started 22 ©2026 Palo Alto Networks, Inc.
Panorama Overview
Centralized Logging and Reporting using Panorama
Where Can I Use This? What Do I Need?
```
• NGFW (Managed by Panorama) No prerequisites needed
```
Panorama aggregates logs from all managed firewalls and provides visibility across all the traffic
on the network. It also provides an audit trail for all policy modifications and configuration
changes made to the managed firewalls. In addition to aggregating logs, Panorama can forward
them as SNMP traps, email notifications, syslog messages, and HTTP payloads to an external
server.
For centralized logging and reporting, you also have the option to use the cloud-based Strata
Logging Service that is architected to work seamlessly with Panorama. The Strata Logging Service
allows your managed firewalls to forward logs to the Strata Logging Service infrastructure instead
of to Panorama or to the managed Log Collectors, so you can augment your existing distributed
log collection setup or to scale your current logging infrastructure without having to invest time
and effort yourself.
```
The Application Command Center (ACC) on Panorama provides a single pane for unified
```
reporting across all the firewalls. It enables you to centrally Monitor Network Activity, to analyze,
investigate, and report on traffic and security incidents. On Panorama, you can view logs and
generate reports from logs forwarded to the Strata Logging Service, Panorama or to the managed
Log Collectors, if configured, or you can query the managed firewalls directly. For example, you
can generate reports about traffic, threat, and/or user activity in the managed network based on
```
logs stored on Panorama (and the managed collectors) or by accessing the logs stored locally on
```
the managed firewalls, or in the Strata Logging Service.
If you don’t Configure Log Forwarding to Panorama or the Strata Logging Service, you can
schedule reports to run on each managed firewall and forward the results to Panorama for a
combined view of user activity and network traffic. Although reports don’t provide a granular drill-
down on specific information and activities, they still provide a unified monitoring approach.
Managed Collectors and Collector Groups
Where Can I Use This? What Do I Need?
```
• NGFW (Managed by Panorama) No prerequisites needed
```
Panorama uses Log Collectors to aggregate logs from managed firewalls. When generating
reports, Panorama queries the Log Collectors for log information, providing you visibility into all
the network activity that your firewalls monitor. Because you use Panorama to configure and
manage Log Collectors, they are also known as managed collectors. Panorama can manage two
types of Log Collectors:
Panorama Getting Started 23 ©2026 Palo Alto Networks, Inc.
Panorama Overview
• Local Log Collector
This type of Log Collector runs locally on the Panorama management server. Only an M-700,
M-600, M-500, M-300, or M-100 appliance, or Panorama virtual appliance in Panorama mode
supports a local Log Collector.
• Dedicated Log Collector
This is an M-700, M-600, M-500, M-300, M-200, or M-100 appliance or Panorama virtual
appliance in Log Collector mode. You can use an M-Series appliance in Panorama mode or
```
a Panorama virtual appliance in Panorama or Legacy (ESXi and vCloud Air) mode to manage
```
Dedicated Log Collectors. To use the Panorama web interface for managing Dedicated Log
Collectors, you must add them as managed collectors. Otherwise, administrative access to a
Dedicated Log Collector is only available through its CLI using the predefined administrative
```
user (admin) account. Dedicated Log Collectors don’t support additional administrative user
```
accounts.
You can use either or both types of Log Collectors to achieve the best logging solution for your
```
environment (see Local and Distributed Log Collection).
```
A Collector Group is 1 to 16 managed collectors that operate as a single logical log collection
unit. If the Collector Group contains Dedicated Log Collectors, Panorama uniformly distributes
the logs across all the disks in each Log Collector and across all Log Collectors in the group. This
distribution optimizes the available storage space. To enable a Log Collector to receive logs,
you must add it to a Collector Group. You can enable log redundancy by assigning multiple Log
```
Collectors to a Collector Group (see Caveats for a Collector Group with Multiple Log Collectors).
```
The Collector Group configuration specifies which managed firewalls can send logs to the Log
Collectors in the group.
To configure Log Collectors and Collector Groups, see Manage Log Collection.
Local and Distributed Log Collection
Before you Configure Log Forwarding to Panorama, you must decide whether to use local Log
Collectors, Dedicated Log Collectors, or both.
A local Log Collector is easy to deploy because it requires no additional hardware or virtual
```
machine instance. In a high availability (HA) configuration, you can send logs to the local Log
```
```
Collector on both Panorama peers; the passive Panorama doesn’t wait for failover to start
```
collecting logs.
Dedicated Log Collectors are M-700, M-600, M-300, M-200, or Panorama virtual appliance in Log
Collector mode. Because they perform only log collection, not firewall management, Dedicated
Log Collectors allow for a more robust environment than local Log Collectors. Dedicated Log
Collectors provide the following benefits:
• Enable the Panorama management server to use more resources for management functions
instead of logging.
• Provide high-volume log storage on a dedicated hardware appliance.
• Enable higher logging rates.
• Provide horizontal scalability and redundancy with RAID 1 storage.
• Optimize bandwidth resources in networks where more bandwidth is available for firewalls to
send logs to nearby Log Collectors than to a remote Panorama management server.
Panorama Getting Started 24 ©2026 Palo Alto Networks, Inc.
Panorama Overview
```
• Enable you to meet regional regulatory requirements (for example, regulations might not allow
```
```
logs to leave a particular region).
```
Distributed Log Collection illustrates a topology in which the Panorama peers in an HA
configuration manage the deployment and configuration of firewalls and Dedicated Log
Collectors.
You can deploy the Panorama management server in an HA configuration but not the
Dedicated Log Collectors.
Figure 4: Distributed Log Collection
Caveats for a Collector Group with Multiple Log Collectors
```
You can Configure a Collector Group with multiple Log Collectors (up to 16) to ensure log
```
redundancy, increase the log retention period, and accommodate logging rates that exceed
```
the capacity of a single Log Collector (see Panorama Models for capacity information). In
```
any single Collector Group, all the Log Collectors must run on the same Panorama model: all
M-700 appliances, all M-600 appliances, all M-500 appliances, all M-300 appliances, all M-200
appliances, or all Panorama virtual appliances. For example, if a single managed firewall generates
48 TB of logs, the Collector Group that receives those logs will require at least three Log
Collectors that are M-300 appliances or one Log Collector that is an M-700 appliance or similarly
resourced Panorama virtual appliance.
A Collector Group with multiple Log Collectors uses the available storage space as one logical
unit and uniformly distributes the logs across all its Log Collectors. The log distribution is based
```
on the disk capacity of the Log Collectors (see Panorama Models) and a hash algorithm that
```
dynamically decides which Log Collector owns the logs and writes to disk. Although Panorama
uses a preference list to prioritize the list of Log Collectors to which a managed firewall can
forward logs, Panorama does not necessarily write the logs to the first Log Collector specified in
the preference list. For example, consider the following preference list:
Panorama Getting Started 25 ©2026 Palo Alto Networks, Inc.
Panorama Overview
Managed Firewall Log Forwarding Preference List Defined in a Collector Group
FW1 L1,L2,L3
FW2 L4,L5,L6
Using this list, FW1 will forward logs to L1 so long as that primary Log Collector is available.
However, based on the hash algorithm, Panorama might choose L2 as the owner who writes the
logs to its disks. If L2 becomes inaccessible or has a chassis failure, FW1 won’t know because it
can still connect to L1.
Figure 5: Example - Typical Log Collector Group Setup
In the case where a Collector Group has only one Log Collector and the Log Collector fails, the
```
firewall stores the logs to its HDD/SSD (the available storage space varies by firewall model). As
```
soon as connectivity is restored to the Log Collector, the firewall resumes forwarding logs where
it left off before the failure occurred.
In the case of a Collector Group with multiple Log Collectors, the firewall does not buffer logs to
its local storage if only one Log Collector is down. In the example scenario where L2 is down, FW1
continues sending logs to L1, and L1 stores the log data that would be sent to L2. Once L2 is back
up, L1 no longer stores log data intended for L2 and distribution resumes as expected. If one of
the Log Collectors in a Collector Group goes down, the logs that would be written to the down
Log Collector are redistributed to the next Log Collector in the preference list.
Palo Alto Networks recommends adding at least three Log Collectors to a Collector Group
to avoid split brain and log ingestion issues should one Log Collector go down. See the
changes to default Collector Group behavior for more information.
Two Log Collectors in a Collector Group are supported, but the Collector Group becomes
non-operational if one Log Collector goes down.
Panorama Getting Started 26 ©2026 Palo Alto Networks, Inc.
Panorama Overview
Figure 6: Example - When a Log Collector Fails
Palo Alto Networks recommends the following mitigations if using multiple Log Collectors in a
Collector Group:
• Enable log redundancy when you Configure a Collector Group. This ensures that no logs are
lost if any one Log Collector in the Collector Group becomes unavailable. Each log will have
two copies and each copy will reside on a different Log Collector. Log redundancy is available
only if each Log Collector has the same number of logging disks.
Because enabling redundancy creates more logs, this configuration requires more
storage capacity. When a Collector Group runs out of space, it deletes older logs.
Enabling redundancy doubles the log processing traffic in a Collector Group, which
reduces its maximum logging rate by half, as each Log Collector must distribute a copy
of each log it receives.
```
• Obtain an On-Site-Spare (OSS) to enable prompt replacement if a Log Collector failure occurs.
```
• In addition to forwarding logs to Panorama, configure forwarding to an external service as
standby storage. The external service can be a syslog server, email server, SNMP trap server, or
HTTP server.
If you enable log redundancy in a Collector Group and also configure syslog forwarding to an
external service, be aware that syslog forwarding sends both copies of each redundant log.
This results in duplicate logs being forwarded to your syslog server. Each log will be sent twice
—once from each Log Collector that stores a copy—effectively doubling the volume of logs
forwarded via syslog.
To avoid receiving duplicate logs on your syslog server, consider one of the following
```
approaches:
```
• Disable log redundancy if your primary goal is syslog forwarding and you can accept the
risk of potential log loss during Log Collector failures.
• Configure your syslog server to deduplicate incoming logs based on log attributes such as
serial number, session ID, and timestamp.
• Configure syslog forwarding on only one Log Collector in the Collector Group, though this
does not provide redundancy for syslog forwarding itself.
Panorama Getting Started 27 ©2026 Palo Alto Networks, Inc.
Panorama Overview
Log Forwarding Options
Where Can I Use This? What Do I Need?
```
• NGFW (Managed by Panorama) No prerequisites needed
```
By default, each firewall stores its log files locally. To use Panorama for centralized log monitoring
and report generation, you must Configure Log Forwarding to Panorama. Logs are forwarded
over the management interface by default unless you configure a dedicated service route to
forward logs. Panorama supports forwarding logs to either a Log Collector, the Strata Logging
Service, or both in parallel. You can also use external services for archiving, notification, or
analysis by forwarding logs to the services directly from the firewalls or from Panorama. External
services include the syslog servers, email servers, SNMP trap servers, or HTTP-based services.
In addition to forwarding firewall logs, you can forward the logs that the Panorama management
server and Log Collectors generate. The Panorama management server, Log Collector, or firewall
```
that forwards the logs converts them to a format that is appropriate for the destination (syslog
```
```
message, email notification, SNMP trap, or HTTP payload).
```
Palo Alto Networks firewalls and Panorama support the following log forwarding options. Before
choosing an option, consider the logging capacities of your Panorama Models and Determine
Panorama Log Storage Requirements.
• Forward logs from firewalls to Panorama and from Panorama to external services—This
configuration is best for deployments in which the connections between firewalls and external
services have insufficient bandwidth to sustain the logging rate, which is often the case when
the connections are remote. This configuration improves firewall performance by offloading
some processing to Panorama.
You can configure each Collector Group to forward logs to different destinations.
Figure 7: Log Forwarding to Panorama and then to External Services
• Forward logs from firewalls to Panorama and to external services in parallel—In this
configuration, both Panorama and the external services are endpoints of separate log
```
forwarding flows; the firewalls don’t rely on Panorama to forward logs to external services.
```
This configuration is best for deployments in which the connections between firewalls and
external services have sufficient bandwidth to sustain the logging rate, which is often the case
when the connections are local.
Panorama Getting Started 28 ©2026 Palo Alto Networks, Inc.
Panorama Overview
Figure 8: Log Forwarding to External Services and Panorama in Parallel
Centralized Reporting
Where Can I Use This? What Do I Need?
```
• NGFW (Managed by Panorama) No prerequisites needed
```
Panorama aggregates logs from all managed firewalls and enables reporting on the aggregated
data for a global view of application use, user activity, and traffic patterns across the entire
network. As soon as the firewalls are added to Panorama, the ACC can display all traffic traversing
your network. With logging enabled, clicking into a log entry in the ACC provides direct access to
granular details about the application.
For generating reports, Panorama uses two sources: the local Panorama database and the remote
firewalls that it manages. The Panorama database refers to the local storage on Panorama that is
allocated for storing both summarized logs and some detailed logs. If you have a distributed Log
Collection deployment, the Panorama database includes the local storage on Panorama and all
the managed Log Collectors. Panorama summarizes the information—traffic, application, threat
— collected from all managed firewalls at 15-minute intervals. Using the local Panorama database
allows for faster response times, however, if you prefer to not forward logs to Panorama,
Panorama can directly access the remote firewall and run reports on data that is stored locally on
the managed firewalls.
Panorama offers more than 40 predefined reports that can be used as is, or they can be
customized by combining elements of other reports to generate custom reports and report groups
that can be saved. Reports can be generated on demand, on a recurring schedule, and can be
scheduled for email delivery. These reports provide information on the user and the context so
that you correlate events and identify patterns, trends, and potential areas of interest. With the
Panorama Getting Started 29 ©2026 Palo Alto Networks, Inc.
Panorama Overview
integrated approach to logging and reporting, the ACC enables correlation of entries from multiple
logs relating to the same event.
For more information, see Monitor Network Activity.
Panorama Getting Started 30 ©2026 Palo Alto Networks, Inc.
Panorama Overview
Data Redistribution Using Panorama
Where Can I Use This? What Do I Need?
```
• NGFW (Managed by Panorama) No prerequisites needed
```
With data redistribution, you only have to configure each source once, then you can redistribute
multiple data types to as many clients as needed. This helps you to scale your network so that you
can easily add or remove source and clients as your network needs change.
Data redistribution also provides granularity by redistributing only the types of information to
only the firewalls or Panorama management systems that you specify. You can use subnets,
ranges, and regions to further reduce network traffic and maximize device capacity.
One of the key benefits of the Palo Alto Networks firewall is that it can enforce policies and
generate reports based on usernames and tags instead of IP addresses. The challenge for large-
scale networks is ensuring every firewall that enforces policies and generates reports has the
mappings and tags that apply for all of your policy rules. Additionally, every firewall that enforces
Authentication Policy requires a complete, identical set of authentication timestamps for your
user base. Whenever users authenticate to access services and applications, individual firewalls
record the associated timestamps but don’t automatically share them with other firewalls to
ensure consistency. Data redistribution solves these challenges for large-scale networks by
enabling you to redistribute the necessary data. However, instead of setting up extra connections
to redistribute the data between firewalls, you can leverage your Panorama infrastructure to
Redistribute Data to Managed Firewalls.
The infrastructure has existing connections that enable you to redistribute data in layers, from
firewalls to Panorama. Panorama can then redistribute the information to the firewalls that
enforce policies and generate reports.
Each firewall or Panorama management server can receive data from up to 100 redistribution
points. The redistribution points can be other firewalls or Panorama management servers.
However, you can also use Windows-based User-ID agents to perform the mapping and
redistribute the information to firewalls. Only the firewalls record authentication timestamps
when user traffic matches Authentication policy rules.
Panorama Getting Started 31 ©2026 Palo Alto Networks, Inc.
Panorama Overview
Role-Based Access Control
Where Can I Use This? What Do I Need?
```
• NGFW (Managed by Panorama) No prerequisites needed
```
```
Role-based access control (RBAC) enables you to define the privileges and responsibilities of
```
```
administrative users (administrators). Every administrator must have a user account that specifies
```
a role and authentication method. Administrative Roles define access to specific configuration
settings, logs, and reports within Panorama and firewall contexts. For Device Group and Template
administrators, you can map roles to Access Domains, which define access to specific device
```
groups, templates, and firewalls (through context switching). By combining each access domain
```
with a role, you can enforce the separation of information among the functional or regional areas
of your organization. For example, you can limit an administrator to monitoring activities for data
center firewalls but allow that administrator to set policies for test lab firewalls. By default, every
```
Panorama appliance (virtual appliance or M-Series appliance) has a predefined administrative
```
```
account (admin) that provides full read-write access (superuser access) to all functional areas
```
and to all device groups, templates, and firewalls. For each administrator, you can define an
authentication profile that determines how Panorama verifies user access credentials.
Instead of using the default account for all administrators, it is a best practice to create a
separate administrative account for each person who needs access to the administrative
or reporting functions on Panorama. This provides better protection against unauthorized
configuration changes and enables Panorama to log and identify the actions of each
administrator.
• Administrative Roles
• Authentication Profiles and Sequences
• Access Domains
• Administrative Authentication
Administrative Roles
Where Can I Use This? What Do I Need?
```
• NGFW (Managed by Panorama) No prerequisites needed
```
You configure administrator accounts based on the security requirements of your organization,
any existing authentication services that your network uses, and the required administrative roles.
A role defines the type of system access that is available to an administrator. You can define and
restrict access as broadly or granularly as required, depending on the security requirements of
your organization. For example, you might decide that a data center administrator can have access
to all device and networking configurations, but a security administrator can control only security
policy definitions, while other key individuals can have limited CLI or XML API access. The role
types are:
Panorama Getting Started 32 ©2026 Palo Alto Networks, Inc.
Panorama Overview
• Dynamic Roles
These are built-in roles that provide access to Panorama and managed firewalls. When new
```
features are added, Panorama automatically updates the definitions of dynamic roles; you
```
never need to manually update them. The following table lists the access privileges associated
with dynamic roles.
Dynamic Role Privileges
Superuser Full read-write access to Panorama
```
Superuser (read-
```
```
only)
```
Read-only access to Panorama
Panorama
administrator
Full access to Panorama except for the following actions:
• Create, modify, or delete Panorama or firewall administrators and
roles.
• Export, validate, revert, save, load, or import a configuration in the
Device > Setup > Operations page.
• Configure Scheduled Config Export functionality in the Panorama
tab.
• Generate Tech Support File, Generate Stats Dump File, and
```
Download Core Files (Panorama > Support)
```
• Admin Role Profiles
To provide more granular access control over the functional areas of the web interface, CLI,
and XML API, you can create custom roles. When new features are added to the product, you
must update the roles with corresponding access privileges: Panorama does not automatically
add new features to custom role definitions. You select one of the following profile types when
you configure an admin role profile.
Admin Role Profile Description
Panorama For these roles, you can assign read-write access, read-only access,
or no access to all the Panorama features that are available to
the superuser dynamic role except the management of Panorama
administrators and Panorama roles. For the latter two features, you can
assign read-only access or no access, but you cannot assign read-write
access.
An example use of a Panorama role would be for security
administrators who require access to security policy definitions, logs,
and reports on Panorama.
Custom Panorama admin roles have the following limitations:
```
• No access to Reboot Panorama (Panorama > Setup > Operations)
```
Panorama Getting Started 33 ©2026 Palo Alto Networks, Inc.
Panorama Overview
Admin Role Profile Description
• No access to Generate Tech Support File, Generate Stats Dump File,
```
and Download Core Files (Panorama > Support)
```
Device Group and
Template
For these roles, you can assign read-write access, read-only access, or
no access to specific functional areas within device groups, templates,
and firewall contexts. By combining these roles with Access Domains,
you can enforce the separation of information among the functional or
regional areas of your organization. Device Group and Template roles
have the following limitations:
• No access to the CLI or XML API
• No access to configuration or system logs
• No access to VM information sources
```
• No access to Reboot Panorama (Panorama > Setup > Operations)
```
• No access to Generate Tech Support File, Generate Stats Dump File,
```
and Download Core Files (Panorama > Support)
```
• In the Panorama tab, access is limited to:
```
• Device deployment features (read-write, read-only, or no access)
```
```
• The device groups specified in the administrator account (read-
```
```
write, read-only, or no access)
```
• The templates and managed firewalls specified in the
```
administrator account (read-only or no access)
```
An example use of this role would be for administrators in your
operations staff who require access to the device and network
configuration areas of the web interface for specific device groups and/
or templates.
Authentication Profiles and Sequences
Where Can I Use This? What Do I Need?
```
• NGFW (Managed by Panorama) No prerequisites needed
```
An authentication profile defines the authentication service that validates the login credentials
of administrators when they access Panorama. The service can be local authentication or an
```
external authentication service. Some services (SAML, TACACS+, and RADIUS) provide the option
```
to manage both authentication and authorization for administrative accounts on the external
server instead of on Panorama. In addition to the authentication service, the authentication profile
```
defines options such as Kerberos single sign-on (SSO) and SAML single logout (SSO).
```
```
Some networks have multiple databases (such as TACACS+ and LDAP) for different users and
```
user groups. To authenticate administrators in such cases, configure an authentication sequence—
a ranked order of authentication profiles that Panorama matches an administrator against during
Panorama Getting Started 34 ©2026 Palo Alto Networks, Inc.
Panorama Overview
login. Panorama checks against each profile in sequence until one successfully authenticates the
administrator. An administrator is denied access only if authentication fails for all the profiles in
the sequence.
Access Domains
Where Can I Use This? What Do I Need?
```
• NGFW (Managed by Panorama) No prerequisites needed
```
Access domains control administrative access to specific Device Groups and templates, and also
control the ability to sswitch context to the web interface of managed firewalls. Access domains
apply only to administrators with Device Group and Template roles. Mapping Administrative
Roles to access domains enables very granular control over the information that administrators
access on Panorama. For example, consider a scenario where you configure an access domain
that includes all the device groups for firewalls in your data centers and you assign that access
domain to an administrator who is allowed to monitor data center traffic but who is not allowed
to configure the firewalls. In this case, you would map the access domain to a role that enables
all monitoring privileges but disables access to device group settings. Additionally, Device Group
and Template admins can perform administrative tasks for managed firewalls in their access
domain such as viewing the configuration and system logs, perform configuration audits, review
pending tasks, and directly access firewall operations such as reboot, generating a tech support
file, executing a stats dump, and exporting a core file.
You configure access domains in the local Panorama configuration and then assign them to
administrative accounts and roles. You can perform the assignment locally or use an external
SAML, TACACS+, or RADIUS server. Using an external server enables you to quickly reassign
access domains through your directory service instead of reconfiguring settings on Panorama.
To use an external server, you must define a server profile that enables Panorama to access the
```
server. You must also define Vendor-Specific Attributes (VSAs) on the RADIUS or TACACS+
```
server, or SAML attributes on the SAML IdP server.
For example, if you use a RADIUS server, you would define a VSA number and value for each
administrator. The value defined has to match the access domain configured on Panorama.
When an administrator tries to log in to Panorama, Panorama queries the RADIUS server for the
administrator access domain and attribute number. Based on the response from the RADIUS
server, the administrator is authorized for access and is restricted to the firewalls, virtual systems,
device groups, and templates that are assigned to the access domain.
For the relevant procedures, see:
• Configure an Access Domain
• Configure RADIUS Authentication for Panorama Administrators
• Configure TACACS+ Authentication for Panorama Administrators
• Configure SAML Authentication for Panorama Administrator
Panorama Getting Started 35 ©2026 Palo Alto Networks, Inc.
Panorama Overview
Administrative Authentication
Where Can I Use This? What Do I Need?
```
• NGFW (Managed by Panorama) No prerequisites needed
```
```
You can configure the following types of authentication and authorization (Administrative Roles
```
```
and Access Domains) for Panorama administrators:
```
Authentication
Method
Authorization
Method
Description
Local Local The administrative account credentials and authentication
mechanisms are local to Panorama. You use Panorama to assign
administrative roles and access domains to the accounts. To
further secure the accounts, you can create a password profile
that defines a validity period for passwords and set Panorama-
wide password complexity settings. For details, see Configure
Local or External Authentication for Panorama Administrators.
SSH Keys Local The administrative accounts are local to Panorama, but
authentication to the CLI is based on SSH keys. You use
Panorama to assign administrative roles and access domains to
the accounts. For details, see Configure an Administrator with
SSH Key-Based Authentication for the CLI.
Certificates Local The administrative accounts are local to Panorama, but
authentication to the web interface is based on client certificates.
You use Panorama to assign administrative roles and access
domains to the accounts. For details, see Configure a Panorama
Administrator with Certificate-Based Authentication for the Web
Interface.
External
service
Local The administrative accounts you define locally on Panorama
serve as references to the accounts defined on an external Multi-
Factor Authentication, SAML, Kerberos, TACACS+, RADIUS, or
LDAP server. The external server performs authentication. You
use Panorama to assign administrative roles and access domains
to the accounts. For details, see Configure Local or External
Authentication for Panorama Administrators.
External External
service
The administrative accounts are defined only on an external
SAML, TACACS+, or RADIUS server. The server performs both
authentication and authorization. For authorization, you define
```
Vendor-Specific Attributes (VSAs) on the TACACS+ or RADIUS
```
server, or SAML attributes on the SAML server. Panorama maps
the attributes to administrator roles and access domains that you
define on Panorama. For details, see:
Panorama Getting Started 36 ©2026 Palo Alto Networks, Inc.
Panorama Overview
Authentication
Method
Authorization
Method
Description
• Configure SAML Authentication for Panorama Administrators
• Configure TACACS+ Authentication for Panorama
Administrators
• Configure RADIUS Authentication for Panorama
Administrators
Panorama Getting Started 37 ©2026 Palo Alto Networks, Inc.
Panorama Overview
Panorama Commit, Validation, and Preview Operations
Where Can I Use This? What Do I Need?
```
• NGFW (Managed by Panorama) No prerequisites needed
```
When you are ready to activate changes that you made to the candidate configuration on
```
Panorama or to push changes to the devices that Panorama manages (firewalls, Log Collectors,
```
```
and WildFire appliances and appliance clusters), you can Preview, Validate, or Commit
```
Configuration Changes. For example, if you add a Log Collector to the Panorama configuration,
firewalls cannot send logs to that Log Collector until you commit the change to Panorama and
then push the change to the Collector Group that contains the Log Collector.
You can filter changes by administrator or location and then commit, push, validate, or preview
only those changes. The location can be specific device groups, templates, Collector Groups, Log
Collectors, shared settings, or the Panorama management server.
When you commit changes, they become part of the running configuration. Changes that you
haven’t committed are part of the candidate configuration. Panorama queues commit requests
so that you can initiate a new commit while a previous commit is in progress. Panorama performs
the commits in the order they are initiated but prioritizes auto-commits that are initiated by
```
Panorama (such as FQDN refreshes). However, if the queue already has the maximum number of
```
```
administrator-initiated commits (10), you must wait for Panorama to finish processing a pending
```
```
commit before initiating a new one. You can Use the Panorama Task Manager ( ) to cancel
```
pending commits or to see details about commits that are pending, in progress, completed, or
failed. To check which changes a commit will activate, you can run a commit preview.
When you initiate a commit, Panorama checks the validity of the changes before activating them.
```
The validation output displays conditions that block the commit (errors) or that are important to
```
```
know (warnings). For example, validation could indicate an invalid route destination that you need
```
to fix for the commit to succeed. The validation process enables you to find and fix errors before
```
you commit (it makes no changes to the running configuration). This is useful if you have a fixed
```
commit window and want to be sure the commit will succeed without errors.
When you preview your configuration commit, any configuration object added between existing
any other existing object is displayed as a modified configuration object rather than an added
configuration object. For example, Address1 and Address2 are existing Address objects. A
Panorama admin later creates Address3 and adds the Address object between Address1 and
Address2. When the Panorama admin goes to preview the configuration changes, Address3 is
displayed as a modified configuration object.
Automated commit recovery is enabled by default, allowing the managed firewalls to locally
test the configuration pushed from Panorama to verify that the new changes do not break the
connection between Panorama and the managed firewall. If the committed configuration breaks
the connection between Panorama and a managed firewall then the firewall automatically fails
the commit and the configuration is reverted to the previous running configuration and the
```
Shared Policy or Template Status (Panorama > Managed Devices > Summary) gets out of sync
```
depending on which configuration objects were pushed. Additionally, the managed firewalls test
their connection to Panorama every 60 minutes and if a managed firewall detects that it can no
Panorama Getting Started 38 ©2026 Palo Alto Networks, Inc.
Panorama Overview
longer successfully connect to Panorama then it reverts its configuration to the previous running
configuration.
For details on candidate and running configurations, see Manage Panorama and Firewall
Configuration Backups.
To prevent multiple administrators from making configuration changes during concurrent
sessions, see Manage Locks for Restricting Configuration Changes.
When pushing configurations to managed firewalls, Panorama pushes the running
configuration. Because of this, Panorama does not let you push changes to managed
firewalls until you first commit the changes to Panorama.
Panorama Getting Started 39 ©2026 Palo Alto Networks, Inc.
Panorama Overview
Panorama Getting Started 40 ©2026 Palo Alto Networks, Inc.
Plan Your Panorama Deployment
Where Can I Use This? What Do I Need?
```
• NGFW (Managed by Panorama) No prerequisites needed
```
Determine the management approach. Do you plan to use Panorama to centrally configure
and manage the policies, to centrally administer software, content and license updates, and/or
centralize logging and reporting across the managed firewalls in the network?
If you already deployed and configured Palo Alto Networks firewalls on your network,
determine whether to transition the firewalls to centralized management. This process requires
a migration of all configuration and policies from your firewalls to Panorama. For details, see
Transition a Firewall to Panorama Management.
Verify the Panorama and firewall software versions. Panorama can manage firewalls running
PAN-OS versions that match the Panorama version or are earlier than the Panorama version.
See Panorama Management Compatibility for more information.
```
(Multi-vsys firewalls) If you already deployed and configured multi-vsys Palo Alto Networks
```
firewalls on your network, Palo Alto Networks recommends you transition and manage all
vsys configurations of the multi-vsys firewall from Panorama. This is required to avoid commit
issues on the multi-vsys firewall and allows you to take advantage of the optimized shared
object pushes from Panorama.
```
(Multi-vsys firewalls) Delete or rename any locally configured firewall Shared object that has
```
an identical name to an object in the Panorama Shared configuration. Otherwise, configuration
pushes from Panorama fail after the upgrade and display the error <object-name> is
already in use.
Determine your authentication method between Panorama and its managed devices and
high availability peer. By default, Panorama uses predefined certificates to authenticate
the SSL connections used for management and inter-device communication. However, you
can configure custom certificate-based authentication to enhance the security of the SSL
connections between Panorama, firewalls, and log collectors. By using custom certificates,
you can establish a unique chain of trust to ensure mutual authentication between Panorama
and the devices it manages. You can import the certificates from your enterprise public key
```
infrastructure (PKI) or generate it on Panorama.
```
```
Plan to use Panorama in a high availability configuration; set it up as an active/passive high
```
availability pair. See Panorama High Availability.
Plan how to accommodate network segmentation and security requirements in a large-scale
deployment. By default, Panorama running on an M-Series appliance uses the management
```
(MGT) interface for administrative access to Panorama and for managing devices (firewalls,
```
```
Log Collectors, and WildFire appliances and appliance clusters), collecting logs, communicating
```
with Collector Groups, and deploying software and content updates to devices. However, to
improve security and enable network segmentation, you can reserve the MGT interface for
```
administrative access and use dedicated M-Series Appliance Interfaces (Eth1, Eth2, Eth3, Eth4,
```
```
and Eth5) for the other services.
```
41
Plan Your Panorama Deployment
For meaningful reports on network activity, plan a logging solution:
• Verify the resource allocation for your Panorama virtual appliance deployed in Log Collector
mode on AWS or Azure. The Panorama virtual appliance does not retain Log Collector mode
if resized. This results in log data loss.
• Estimate the log storage capacity your network needs to meet security and compliance
requirements. Consider such factors as the logging capacities of your Panorama Models,
```
network topology, number of firewalls sending logs, type of log traffic (for example, URL
```
```
Filtering and Threat logs versus Traffic logs), the rate at which firewalls generate logs,
```
and the number of days for which you want to store logs on Panorama. For details, see
Determine Panorama Log Storage Requirements.
```
• Do you need to forward logs to external services (such as a syslog server) in addition to
```
Panorama? See Log Forwarding Options.
• Do you want to own or manage your own log storage on premises, or do you want to
leverage the Strata Logging Service provided by Palo Alto Networks?
• If you need a long-term storage solution, do you have a Security Information and Event
```
Management (SIEM) solution, such as Splunk or ArcSight, to which you can forward logs?
```
• Do you need redundancy in logging?
If you configure a Collector Group with multiple Log Collectors, you can enable redundancy
```
to ensure that no logs are lost if any one Log Collector becomes unavailable (see Caveats for
```
```
a Collector Group with Multiple Log Collectors).
```
Determine which role-based access privileges administrators require to access managed
firewalls and Panorama. See Configure Administrative Access to Panorama.
Plan the required Device Groups. Consider whether to group firewalls based on function,
security policy, geographic location, or network segmentation. An example of a function-based
device group is one that contains all the firewalls that a Research and Development team uses.
Consider whether to create smaller device groups based on commonality, larger device groups
to scale more easily, or a Device Group Hierarchy to simplify complex layers of administration.
Plan a layering strategy for administering policies. Consider how firewalls inherit and evaluate
policy rules within the Device Group Hierarchy, and how to best implement shared rules,
device-group rules, and firewall-specific rules to meet your network needs. For visibility and
centralized policy management, consider using Panorama for administering rules even if you
need firewall-specific exceptions for shared or device group rules. If necessary, you can Push a
Policy Rule to a Subset of Firewalls within a device group.
Plan the organization of your firewalls based on how they inherit network configuration
settings from Templates and Template Stacks. For example, consider assigning firewalls to
templates based on hardware models, geographic proximity, and similar network needs for
time zones, a DNS server, and interface settings.
Panorama Getting Started 42 ©2026 Palo Alto Networks, Inc.
Plan Your Panorama Deployment
Determine Panorama Log Storage Requirements
Where Can I Use This? What Do I Need?
```
• NGFW (Managed by Panorama) No prerequisites needed
```
When you Plan Your Panorama Deployment, estimate how much log storage capacity Panorama
requires to determine which Panorama Models to deploy, whether to expand the storage on
those appliances beyond their default capacities, whether to deploy Dedicated Log Collectors, and
whether to Configure Log Forwarding from Panorama to External Destinations. When log storage
reaches the maximum capacity, Panorama automatically deletes older logs to create space for new
ones.
Perform the following steps to determine the approximate log storage that Panorama requires.
For details and use cases, refer to Panorama Sizing and Design Guide.
STEP 1 | Determine the log retention requirements of your organization.
Factors that affect log retention requirements include:
• IT policy of your organization
• Log redundancy—If you enable log redundancy when you Configure a Collector Group, each
log will have two copies, which doubles your required log storage capacity.
• Regulatory requirements, such as those specified by the Payment Card Industry Data
```
Security Standard (PCI DSS), Sarbanes-Oxley Act, and Health Insurance Portability and
```
```
Accountability Act (HIPAA).
```
If your organization requires the removal of logs after a certain period, you can set the
expiration period for each log type. You can also set a storage quota for each log type
as a percentage of the total space if you need to prioritize log retention by type. For
details, see Manage Storage Quotas and Expiration Periods for Logs and Reports.
STEP 2 | Determine the average daily logging rates.
Do this multiple times each day at peak and non-peak times to estimate the average. The more
often you sample the rates, the more accurate your estimate.
1. Display the current log generation rate in logs per second:
• If Panorama is not yet collecting logs, access the CLI of each firewall, run the
following command, and calculate the total rates for all the firewalls. This command
displays the number of logs received in the last second.
> debug log-receiver statistics
• If Panorama is already collecting logs, run the following command at the CLI of
```
each appliance that receives logs (Panorama management server or Dedicated Log
```
Panorama Getting Started 43 ©2026 Palo Alto Networks, Inc.
Plan Your Panorama Deployment
```
Collector) and calculate the total rates. This command gives the average logging rate
```
for the last five minutes.
> debug log-collector log-collection-stats show incoming-logs
You can also use an SNMP manager to determine the logging rates of Log
```
Collectors (see the panLogCollector MIB, OID 1.3.6.1.4.1.25461.1.1.6) and
```
```
firewalls (see the panDeviceLogging, OID 1.3.6.1.4.1.25461.2.1.2.7).
```
2. Calculate the average of the sampled rates.
3. Calculate the daily logging rate by multiplying the average logs-per-second by 86,400.
STEP 3 | Estimate the required storage capacity.
```
This formula provides only an estimate; the exact amount of required storage will differ
```
from the formula result.
Use the formula:
```
[(<logs_per_second> x 86400) x <days_of retention>] x <average_log_size> ÷ (1024 x 1024 x
```
```
1024)
```
The average log size varies considerably by log type. However, you can use 489 bytes as an
approximate average log size.
For example, if Panorama must store logs for 30 days with a log rate of 1,500 LPS, then
```
the required log storage capacity is: [(1500 x 86400) x 30] x 489 ÷ (1024 x 1024 x 1024) =
```
1770GB.
The results above are calculations for the detailed logs only with the default quota settings
reserve 60% of the available storage for detail logs. This means that the calculated number
represents 60% of the storage used by the Log Collector. To calculate the total storage
required, divide this number by .60: 1770 ÷ .6 = 2951GB.
One third, roughly 33%, of the avilable disk space is allocated to logd formatted logs to support
upgrades, downgrades, and to support fixing database corruption. To calculate the total
storage, divide the storage required by .66: 2951 ÷ .66 = 4471 total storage.
STEP 4 | Next steps...
If you determine that Panorama requires more log storage capacity:
• Expand Log Storage Capacity on the Panorama Virtual Appliance.
• Increase Storage on the M-Series Appliance.
Panorama Getting Started 44 ©2026 Palo Alto Networks, Inc.
Plan Your Panorama Deployment
Deploy Panorama
Where Can I Use This? What Do I Need?
```
• NGFW (Managed by Panorama) No prerequisites needed
```
The following task list summarizes the steps to get started with Panorama. For an example of how
to use Panorama for central management, see Use Case: Configure Firewalls Using Panorama.
```
STEP 1 | (M-Series appliance only) Rack mount the appliance.
```
STEP 2 | Perform initial configuration to enable network access to Panorama. See Set Up the
Panorama Virtual Appliance or Set Up the M-Series Appliance.
STEP 3 | Register Panorama and Install Licenses.
STEP 4 | Install Content and Software Updates for Panorama.
```
STEP 5 | (Recommended) Set up Panorama in a high availability configuration. See Panorama High
```
Availability.
STEP 6 | Add a Firewall as a Managed Device.
```
STEP 7 | Add a Device Group or Create a Device Group Hierarchy, Add a Template, and (if applicable)
```
Configure a Template Stack.
```
STEP 8 | (Optional) Configure log forwarding to Panorama and/or to external services. See Manage
```
Log Collection.
STEP 9 | Monitor Network Activity using the visibility and reporting tools on Panorama.
Panorama Getting Started 45 ©2026 Palo Alto Networks, Inc.
Plan Your Panorama Deployment
Cheat Sheet: Manage Prisma Access by Using Panorama
Where Can I Use This? What Do I Need?
• Panorama Prisma Access License
You can manage your Prisma Access deployment using either Panorama or Strata Cloud Manager.
The set of supported features is not identical across Prisma Access managed by Panorama and
Prisma Access managed by Strata Cloud Manager. Refer to thecompatibility metrics to determine
which features are supported with each option. This helps you decide on the management
interface.
```
Important: You cannot switch management interfaces after you activate your Prisma Access
```
license. Therefore, determine your interface choice before you start.
For a comprehensive overview of Prisma Access features and management options, refer to
Prisma Access Overview.
Here's what you need to know to use Panorama to manage Prisma Access. The following tables
summarize the topics and steps.
Activation & Initial Onboarding
Deploy and activate the service.
Reference Topic Description
Activate Your Prisma Access License Complete the initial steps required to deploy
and activate the Prisma Access service.
Set Up Prisma Access Configure the foundational settings required
for Prisma Access deployment.
Activation and Onboarding
Reference Topic Description
Activate Your Prisma Access License Complete the initial steps required to deploy
and activate the Prisma Access service.
Set Up Prisma Access Configure the foundational settings required
for Prisma Access deployment.
How to Manage Prisma Access Understand the high-level steps for Prisma
Access management
Core Configuration and Security
Panorama Getting Started 46 ©2026 Palo Alto Networks, Inc.
Plan Your Panorama Deployment
Reference Topic Description
Configure a Service Connection in Prisma
```
Access (Panorama)
```
Configure a connection between Prisma
Access and your data center/headquarters.
```
Enable Private App Security (Panorama) Enable security for privately hosted
```
applications.
Configure App Acceleration in Prisma Access
```
(Panorama)
```
Configure settings to enhance application
performance.
Remote Networks—High Performance Configurations for high-performance remote
network connectivity.
```
Operations and Maintenance (Panorama Focused)
```
Reference Topic Description
Prisma Access Visibility and Monitoring Monitor the status, health, and traffic flowing
through Prisma Access.
Prisma Access and Associated Services
Processing Locations
Access information regarding the geographic
locations where Prisma Access and associated
services are processed.
Prisma Access Infrastructure Management Manage the underlying Prisma Access
infrastructure.
Prisma Access APIs Accessing and utilizing the management API.
Migrate Prisma Access from Panorama to
Strata Cloud Manager
Moving the management plane from
Panorama to Strata Cloud Manager.
Prisma Access Releases and Upgrades The process for managing and applying Prisma
Access software updates.
Panorama Getting Started 47 ©2026 Palo Alto Networks, Inc.
Plan Your Panorama Deployment
Panorama Getting Started 48 ©2026 Palo Alto Networks, Inc.
Set Up Panorama
Where Can I Use This? What Do I Need?
```
• NGFW (Managed by Panorama) No prerequisites needed
```
For centralized reporting and cohesive policy management across all the firewalls on your
network, you can deploy the Panorama™ management server as a virtual appliance or as a
dedicated M-Series hardware appliance. These appliances can operate in distinct modes like
Panorama mode or Management Only mode.
To begin, you must evaluate essential planning phases, determine log storage requirements based
on daily logging rates, and optimally structure large-scale firewall deployments by configuring an
```
active and passive High Availability (HA) pair for fault tolerance.
```
Next, you can follow comprehensive instructions to install and initially configure Panorama across
various cloud and hypervisor environments, including AWS, Azure, and ESXi, or as dedicated
hardware.
After the core system is initialized with a management IP address, you must register the
deployment and install the necessary management and support licenses. These licenses enable
you to oversee managed firewalls and retrieve PAN-OS software and dynamic content updates.
Finally, to ensure security and communication integrity, you can install device certificates on both
the Panorama server and any dedicated log collectors.
You can also deploy custom certificates to establish mutual authentication between HA peers and
```
configure Role-Based Access Control (RBAC) to securely govern administrative access to the web
```
interface, CLI, and XML API.
49
Set Up Panorama
Manage Large-Scale Firewall Deployments with
Panorama
Where Can I Use This? What Do I Need?
```
• NGFW (Managed by Panorama) No prerequisites needed
```
Panorama™ provides multiple options to manage a large-scale firewall deployment. For
consolidation of all management functions, Panorama supports management of up to 5,000
firewalls using an M-600, M-700 appliance, or Panorama virtual appliance on ESXi in Management
Only mode or up to 2,500 firewalls with a Panorama virtual appliance in Management Only mode.
To simplify the deployment and operational management of a large-scale firewall deployment
greater than 5,000 firewalls, the Panorama Interconnect plugin allows you to manage multiple
Panorama management server Nodes from a single Panorama Controller.
Determine the Optimal Large-Scale Firewall Deployment Solution
To ease the operational burden of managing the configuration of your large-scale firewall
deployment, Palo Alto Networks provides different firewall management options to best suit your
deployment scenario.
If your large-scale firewall deployment is composed of one or very few Panorama management
servers, you can deploy an M-600, M-700 appliance, or Panorama virtual appliance on ESXi to
manage up to 5,000 firewalls, or Panorama virtual appliance to manage up to 2,500 firewalls, to
leverage all Panorama capabilities from a single Panorama management server. The Increased
Device Management Capacity for M-Series and Panorama Virtual Appliance is ideal for vertically
scaled deployments where you manage a large number of firewalls from a single Panorama
management server rather than deploying multiple Panorama management servers to manage
fewer firewalls.
As of September 1, 2025 the Panorama Interconnect Plugin is no longer supported. For
additional information regarding this change and alternatives, see the official end-of-life
notice.
If your large-scale firewall deployment is composed of multiple Panorama management servers
with similar configurations, the Panorama Interconnect plugin allows you to manage multiple
Panorama Nodes from a single Panorama Controller. This plugin simplifies the deployment and
operational management of large scale firewall deployments because you can centrally manage
policy and configuration from a Panorama Controller. From the Panorama Controller, the device
group and template stack configuration is synchronized to the Panorama Nodes and pushed
to managed devices. The Panorama Interconnect plugin is ideal for horizontally-scaled firewall
deployments with multiple distributed Panorama management servers.
Panorama Getting Started 50 ©2026 Palo Alto Networks, Inc.
Set Up Panorama
Increased Device Management Capacity for M-Series and
Panorama Virtual Appliance
Where Can I Use This? What Do I Need?
```
• NGFW (Managed by Panorama) • Device management licence (per-device)
```
• Support license
• Outbound Internet Access
```
• Customer Support Portal (CSP) Account
```
• Panorama Superuser Role
You can manage up to 5,000 firewalls using a single M-600, M-700 appliance, or Panorama™
virtual appliance installed on VMware ESXi, or up to 2,5000 firewalls with all other supported
Panorama virtual appliances in order to reduce the management footprint of your large-scale
firewall deployment.
Increased Device Management Capacity Requirements
You can manage up to 5,000 firewalls using a single M-600, M-700 appliance, or Panorama™
virtual appliance installed on VMware ESXi, or up to 2,500 firewalls with all other supported
Panorama virtual appliances. For managing such large deployments from a single Panorama
management server alleviates the operational complexity of configuration management and
reduces the security and compliance risk of managing multiple Panorama management servers.
For details about the maximum number of template stacks that Panorama supports, see Template
Stacks.
For log collection, a single Panorama management server is ideal because it provides a centralized
location to view and analyze log data from managed devices rather than requiring you to access
each individual Panorama management server. To provide redundancy in the event of system or
network failure, Palo Alto Networks recommends deploying two Panorama management servers
```
in a high availability (HA) configuration. For Panorama system and config logs, an additional disk
```
with a minimum 92GB capacity is required. This additional disk is automatically detected by the
Panorama virtual appliance when Panorama is rebooted and mounted as a partition for system
and config log storage.
For generating pre-defined reports, you must enable Panorama to use Panorama data for pre-
defined reports. This generates pre-defined reports using log data already collected by Panorama
or the Dedicated Log Collector, which reduces the resource utilization when generating reports.
Enabling this setting is required, otherwise Panorama performance may be impacted, and
Panorama may become unresponsive.
To manage up to 5,000 firewalls, the Panorama management server must meet the following
minimum requirements:
Requirement 5,000 Firewalls 2,500 Firewalls
Model M-600 All supported Panorama
hypervisors. For more
Panorama Getting Started 51 ©2026 Palo Alto Networks, Inc.
Set Up Panorama
Requirement 5,000 Firewalls 2,500 Firewalls
M-700
VMware ESXi
information, see Panorama
Models.
Panorama Mode Management Only Management Only
System Disk Used to store the operating
system files, system logs,
software updates, and content
updates.
• M-Series Appliances—240GB
SSD
• ESXi—224GB
You must manually increase
the system disk to 224GB.
• 81GB—Used to store the
operating system files and
system logs.
• Additional disk with a
minimum 92GB capacity used
for storing Panorama system
and config logs.
CPUs 56 32
Memory 256GB 256GB
Log Collection Local log collection is not supported.
See Deploy Panorama with Dedicated Log Collectors to set up log
collection.
Logging and Reporting Enable the Use Panorama Data for Pre-Defined Reports setting
```
(Panorama > Setup > Management > Logging and Reporting Settings
```
```
> Log Export and Reporting)
```
Install Panorama for Increased Device Management Capacity
Activate the device management license to manage more than 1,000 firewalls from a single
M-600 Panorama™ management server or a single Panorama virtual appliance.
STEP 1 | Contact your Palo Alto Networks sales representative to obtain the Panorama device
management license that enables you to manage up to 5,000 firewalls.
• If you are deploying an M-600 appliance, obtain the PAN-M-600-P-1K device
management license.
• If you are deploying an M-700 appliance, obtain the PAN-M-700-P-1K device
management license.
• If you are deploying a Panorama virtual appliance, obtain the PAN-PRA-1000 device
management license.
Panorama Getting Started 52 ©2026 Palo Alto Networks, Inc.
Set Up Panorama
STEP 2 | Set up the Panorama management server.
```
• (M-600 and M-700 appliances only) Set Up the M-Series Appliance.
```
or
• Set Up the Panorama Virtual Appliance.
STEP 3 | Increase the System Disk for Panorama on an ESXi Server to 224GB.
A 224GB system disk is required for a Panorama virtual appliance installed on VMware
ESXi to manage up to 5,000 firewalls. Review the Increased Device Management Capacity
Requirements for more information.
STEP 4 | Change the Panorama management server to Management Only mode if Panorama is not
already in this mode.
• Begin at Step 5 to Set Up an M-Series Appliance in Management Only Mode.
• Set up a Panorama Virtual Appliance in Management Only Mode.
STEP 5 | Register your Panorama management server and install licenses.
1. Register Panorama.
2. Activate a Panorama Support License.
3. Activate the device management license on the Panorama management server.
• Activate/Retrieve a Firewall Management License on the M-Series Appliance.
• Activate/Retrieve a Firewall Management License when the Panorama Virtual
Appliance is not Internet-connected.
• Activate/Retrieve a Firewall Management License when the Panorama Virtual
Appliance is Internet-connected.
STEP 6 | Select Panorama > Licenses and verify that the device management license is successfully
activated.
If you are activating a new device management license on a Panorama, you can
manage up to 5,000 firewalls with an M-600, M-700 appliance, or Panorama virtual
appliance on ESXi, or up to 2,500 firewalls with a Panorama virtual appliance, but the
Description still displays Device management license to manage up to
1000 devices or more.
Panorama Getting Started 53 ©2026 Palo Alto Networks, Inc.
Set Up Panorama
Set Up the Panorama Virtual Appliance
Where Can I Use This? What Do I Need?
```
• NGFW (Managed by Panorama) • Device management licence
```
• Support license
• Outbound Internet Access
```
• Customer Support Portal (CSP) Account
```
You can set up the Panorama virtual appliance across a variety of platforms. Before beginning,
review the necessary setup prerequisites to ensure your infrastructure is ready. Next, install
the virtual appliance on a wide range of supported hypervisors and public cloud environments,
```
including VMware (ESXi and vCloud Air), Alibaba Cloud, AWS, Azure, Google Cloud Platform
```
```
(GCP), KVM, Hyper-V, and Oracle Cloud Infrastructure (OCI).
```
After the installation is complete, you can perform the initial configuration and select the specific
operating mode that fits your network deployment. You can set up the virtual appliance in
standard Panorama mode, Management Only mode, or as a dedicated Log Collector. For more
details about the Panorama virtual appliance and its modes, see Panorama Models.
You also have the flexibility to configure the appliance with a local log collector, if needed. As
your network management and logging demands grow, you can scale the resources of your virtual
appliance.
You can complete the virtual appliance setup and follow instructions to convert your appliance's
licensing or deployment type if your requirements change. This includes transitioning an
evaluation Panorama to a production deployment, converting to VM-Flex licensing, or moving a
```
production Panorama to an Enterprise License Agreement (ELA).
```
These topics assume you are familiar with the public and private hypervisor products
required to create the virtual appliance, and don’t cover any related concepts or
terminology.
• Setup Prerequisites for the Panorama Virtual Appliance
• Install the Panorama Virtual Appliance
• Perform Initial Configuration of the Panorama Virtual Appliance
• Set Up The Panorama Virtual Appliance as a Log Collector
• Set Up the Panorama Virtual Appliance with Local Log Collector
• Set up a Panorama Virtual Appliance in Panorama Mode
• Set up a Panorama Virtual Appliance in Management Only Mode
• Expand Log Storage Capacity on the Panorama Virtual Appliance
• Increase CPUs and Memory on the Panorama Virtual Appliance
• Increase the System Disk on the Panorama Virtual Appliance
• Complete the Panorama Virtual Appliance Setup
Panorama Getting Started 54 ©2026 Palo Alto Networks, Inc.
Set Up Panorama
• Convert Your Panorama Virtual Appliance
Setup Prerequisites for the Panorama Virtual Appliance
Where Can I Use This? What Do I Need?
```
• NGFW (Managed by Panorama) • Device management licence
```
• Support license
• Outbound Internet Access
```
• Customer Support Portal (CSP) Account
```
Complete the following tasks before you Install the Panorama Virtual Appliance:
Use a dedicated hypervisor host for Panorama and do not share resources with other virtual
machines.
Do not take or use snapshots of the virtual machine.
Use your browser to access the Palo Alto Networks Customer Support web site and Register
Panorama You will need the Panorama serial number that you received in the order fulfillment
email. After registering Panorama, you can access the Panorama software downloads page.
PAN-OS 12.1.2 and later releases require a minimum system disk size of 224 GB. Ensure you
upgrade the system disk before installation. For more information, see Increase the System
Disk on the Panorama Virtual Appliance.
Review the supported Panorama hypervisors to verify the hypervisor meets the minimum
version requirements to deploy Panorama.
If you will install Panorama on a VMware ESXi server, verify that the server meets the
minimum requirements as listed in the System Requirements for the Panorama Virtual
Appliance. These requirements apply to Panorama 5.1 and later releases. The requirements
vary based on whether you will run the virtual appliance in Panorama mode or Management
Only mode. For details on the modes, see Panorama Models.
If you install Panorama on VMware vCloud Air, you set the system settings during
installation.
Review the minimum resource requirements for deploying the Panorama virtual appliance on
```
Alibaba Cloud, Amazon Web Services (AWS), AWS GovCloud, Microsoft Azure, Google Cloud
```
```
Platform (GCP), Hyper-V, KVM, Oracle Cloud Infrastructure (OCI), and VMware ESXi to ensure
```
```
that the virtual machine meets the minimum required resources for the desired mode (Panorama,
```
```
Management Only, or Log Collector). The minimum resource requirements for the Panorama
```
```
virtual appliance are designed to help you achieve the maximum number of logs per second (LPS)
```
for log collection in Panorama and Log Collector mode. If you add or remove virtual logging disks
that results in a configuration that does not meet or exceed the number of virtual logging disks
```
recommended (below), your LPS will be reduced.
```
If the minimum resource requirements are not met for Panorama mode when you Install the
Panorama Virtual Appliance, Panorama defaults to Management Only mode for all supported
```
public (Alibaba Cloud, AWS, AWS GovCloud, Azure, GCP, and OCI) and private (Hyper-V,
```
Panorama Getting Started 55 ©2026 Palo Alto Networks, Inc.
Set Up Panorama
```
KVM, and VMware ESXi) hypervisors. If the minimum resource requirements are not met for
```
Management Only mode, Panorama defaults to Maintenance mode for all supported public
hypervisors, Hyper-V, and KVM.
Table 1: System Requirements for the Panorama Virtual Appliance
RequirementsPanorama Virtual
Appliance in
Management Only Mode
Panorama Virtual
Appliance in Panorama
Mode
Panorama Virtual
Appliance in Log
Collector Mode
Virtual
hardware
version
• VMware ESXi and vCloud Air—64-bit kernel-based VMware ESXi 6.0, 6.5, 6.7,
7.0, or 8.0.
```
The supported version of the virtual hardware family type (also known as the
```
```
VMware virtual hardware version) on the ESXi server is vmx-10.
```
The Panorama virtual appliance for ESXi does not support the
```
following:
```
• Creation of quiesced snapshots.
Disable Quiesce guest file system in the vSphere client or set the
quiesce flag to 0 or false in the vSphere CLI before creating a
snapshot of your virtual Panorama appliance.
• VMware vMotion to migrate a Panorama virtual appliance from
one ESXi server to another.
• Hyper-V—Windows Server 2016 with Hyper-V role or Hyper-V 2016,
Windows Server 2019 with Hyper-V role or Hyper-V 2019, and Windows
Server 2022 with Hyper-V role or Hyper-V 2022.
• KVM—Ubuntu version 16.04 or CentOS7
In Panorama mode, the virtual appliance running on any ESXi version supports
up to 12 virtual logging disks with 2TB of log storage each, for a total maximum
capacity of 24TB.
```
(ESXi and
```
vCloud Air
```
only)
```
Client
computer
To install the Panorama virtual appliance and manage its resources, you must
install a VMware vSphere Client or VMware Infrastructure Client that is
compatible with your ESXi server.
System
disk
```
• (PAN-12.1.2 and later releases) — The Panorama virtual appliance requires a
```
minimum system disk size of 224 GB to upgrade to or run the 12.1.2 and later
versions.
• Default—81GB
Panorama Getting Started 56 ©2026 Palo Alto Networks, Inc.
Set Up Panorama
RequirementsPanorama Virtual
Appliance in
Management Only Mode
Panorama Virtual
Appliance in Panorama
Mode
Panorama Virtual
Appliance in Log
Collector Mode
• Upgraded—224GB
An upgraded system disk is required for SD-WAN.
```
(Panorama and Log Collector mode) An upgraded system disk is required if you
```
added more than 8 logging disks.
For log storage, Panorama uses virtual logging disks instead of the system disk or
an NFS datastore.
Panorama must be initially installed with the Default system disk size, with the
option to increase the system disk size after initial installation.
The minimum resources
below are required to
achieve the specified
logging rate.
• Up to 10,000 logs/sec
```
(LPS):
```
• 16 CPUs
• 64GB memory
• 4x2TB logging disks
• Manage up to 500
managed devices
• Up to 20,000 log/sec
```
(LPS)
```
• 32 CPUs
• 128GB memory
• 8x2TB logging disks
• Manage up to 1,000
managed devices
The minimum resources
below are required to
achieve the specified
logging rate.
• Up to 15,000 log/sec
```
(LPS)
```
• 16 CPUs
• 64GB memory
• 4x2TB logging
disks
• Up to 25,000 logs/
```
sec (LPS)
```
• 32 CPUs
• 128GB memory
• 8x2TB logging
disks
CPUs,
memory,
and
logging
disks
• Manage up to 500
managed devices
• 16 CPUs
• 64GB memory
• Local log storage
not supported
• Manage up to 1,000
managed devices
• 32 CPUs
• 128GB memory
• Local log storage
not supported
• To manage more
than 1,000 firewalls,
see Increased
Device Management
Capacity
Requirements.
The first logging disk on the Panorama virtual
appliance must be 2TB in order to add additional
logging disks. If the first logging disk is smaller than
2TB, you are unable to add additional logging disks.
Minimum
CPUs and
memory
• 16 CPUs
• 64GB memory
The minimum resources below do not take LPS into
consideration and are only required for the Panorama
virtual appliance to function based on the number of
logging disks added. Palo Alto Networks recommends
you refer to the recommended resources above.
Panorama Getting Started 57 ©2026 Palo Alto Networks, Inc.
Set Up Panorama
RequirementsPanorama Virtual
Appliance in
Management Only Mode
Panorama Virtual
Appliance in Panorama
Mode
Panorama Virtual
Appliance in Log
Collector Mode
For larger Panorama deployments, be aware that
you may be under-provisioning your Panorama. This
may lead to impacted performance and may cause
Panorama to become unresponsive depending on the
number of firewalls managed, the configuration size,
the number of administrators logged in to Panorama,
and the volume of logs ingested.
• 2TB to 8TB—16 CPUs, 64GB memory
• 10TB to 24TB— 16 CPUs, 128GB memory
Log
storage
capacity
Panorama in
Management Only mode
requires log forwarding
to a Dedicated Log
Collector.
2TB to 24TB 2TB to 24TB
Supported Interfaces
Interfaces can be used for device management, log collection, Collector Group communication,
licensing and software updates. The Panorama virtual appliance supports up to six interfaces
```
(MGT and Eth1 - Eth5).
```
Table 2: Supported interfaces for public hypervisors
Function Alibaba
Cloud
Amazon Web Services
```
(AWS) and AWS
```
GovCloud
Microsoft
Azure
Google
Cloud
Platform
```
(GCP)
```
OCI
Device
Management
Any
interface
supported
Any
interface
supported
Any
interface
supported
Any
interface
supported
Any
interface
supported
Any
interface
supported
Device Log
Collection
Any
interface
supported
Any
interface
supported
Any
interface
supported
Any
interface
supported
Any
interface
supported
Any
interface
supported
Collector
Group
Communication
Any
interface
supported
Any
interface
supported
Any
interface
supported
Any
interface
supported
Any
interface
supported
Any
interface
supported
Panorama Getting Started 58 ©2026 Palo Alto Networks, Inc.
Set Up Panorama
Function Alibaba
Cloud
Amazon Web Services
```
(AWS) and AWS
```
GovCloud
Microsoft
Azure
Google
Cloud
Platform
```
(GCP)
```
OCI
Licensing
and
Software
Updates
MGT
interface
only
MGT
interface
only
MGT
interface
only
MGT
interface
only
MGT
interface
only
MGT
interface
only
Table 3: Supported Interfaces for Private Hypervisors
```
Function KVM Hyper-V VMware (ESXi,
```
```
vCloud Air)
```
Device Management Any interface
supported
Any interface
supported
Any interface
supported
Device Log Collection Any interface
supported
Any interface
supported
Any interface
supported
Collector Group
Communication
Any interface
supported
Any interface
supported
Any interface
supported
Licensing and Software
Updates
Any interface
supported
Any interface
supported
Any interface
supported
Install the Panorama Virtual Appliance
Where Can I Use This? What Do I Need?
```
• NGFW (Managed by Panorama) • Device management licence
```
• Support license
```
• Panorama Virtual Appliance license (serial
```
```
number)
```
```
• Customer Support Portal (CSP) Account
```
You can deploy the Panorama virtual appliance across a range of on-premises hypervisors and
public cloud environments.
Before installation, decide whether to run the virtual appliance in Panorama mode, Management
Only mode or Log Collector mode. Each mode has different resource requirements, as described
in Setup Prerequisites for the Panorama Virtual Appliance. You must complete the prerequisites
before starting the installation.
Panorama Getting Started 59 ©2026 Palo Alto Networks, Inc.
Set Up Panorama
As of September 1, 2025, the legacy mode is no longer supported on Panorama. For
additional information, see the official end-of-life notice.
Installation procedures vary by platform, but the underlying requirements and configuration goals
remain consistent across environments. Each platform-specific topic in this section provides the
steps needed to deploy the virtual appliance image, configure initial networking, and prepare
the instance for use. Follow the topic that corresponds to your target environment and refer
to the prerequisite guidance if you are unsure which mode or resource profile applies to your
deployment.
As new hypervisor and cloud platforms are validated and supported, additional installation topics
will be added to this section.
Install Panorama on VMware
Where Can I Use This? What Do I Need?
```
• NGFW (Managed by Panorama) • Device management licence
```
• Support license
• Outbound Internet Access
```
• Customer Support Portal (CSP) Account
```
You can install the Panorama virtual appliance on the ESXi and vCloud Air VMware platforms.
• Install Panorama on an ESXi Server
• Install Panorama on vCloud Air
Support for VMware Tools on the Panorama Virtual Appliance
```
VMware Tools is bundled with the software image (ovf) for the Panorama virtual appliance. The
```
support for VMware Tools allows you to use the vSphere environment—vCloud Director and
vCenter server—for the following:
• View the IP address assigned to the Panorama management interface.
• View resource utilization metrics on hard disk, memory, and CPU. You can use these metrics to
enable alarms or actions on the vCenter server or vCloud Director.
• Graceful shutdown and restart of Panorama using the power off function on the vCenter
server or vCloud Director.
• Enables a heartbeat mechanism between the vCenter server and Panorama for verifying that
Panorama is functioning, or if the firewall/Panorama is rebooting. If the firewall goes into
maintenance mode, heartbeats are disabled so that the vCenter server does not shut down the
firewall. Disabling heartbeats allows the firewall to stay operational in maintenance mode when
it cannot not send heartbeats to the vCenter server.
Install Panorama on an ESXi Server
Where Can I Use This? What Do I Need?
```
• NGFW (Managed by Panorama) • Device management licence
```
Panorama Getting Started 60 ©2026 Palo Alto Networks, Inc.
Set Up Panorama
Where Can I Use This? What Do I Need?
• Support license
```
• Panorama Virtual Appliance license (serial
```
```
number)
```
```
• Customer Support Portal (CSP) Account
```
Use these instructions to install a new Panorama virtual appliance on a VMware ESXi server. For
upgrades to an existing Panorama virtual appliance, skip to Install Content and Software Updates
for Panorama.
```
STEP 1 | Download the Panorama 11.1 base image Open Virtual Appliance (OVA) file.
```
1. Log in to the Palo Alto Networks Support Portal.
2. Select Updates > Software Updates and filter by Panorama Base Images to download
```
the OVA file (Panorama-ESX-11.1.0.ova).
```
STEP 2 | Install Panorama.
1. Launch the VMware vSphere Client and connect to the VMware server.
2. Select File > Deploy OVF Template.
3. Browse to select the Panorama OVA file and click Next.
4. Confirm that the product name and description match the downloaded version, and click
Next.
5. Enter a descriptive name for the Panorama virtual appliance, and click Next.
6. Select a datastore location (system disk) on which to install the Panorama image. See
the Setup Prerequisites for the Panorama Virtual Appliance for the supported Default
system disk sizes. After selecting the datastore, click Next.
The Panorama virtual appliance must be initially installed with the Default
system disk size. Installing the Panorama virtual appliance with a system disk
larger than the Default system disk size is not supported and may result in
limited utilization. You have the option to increase the system disk size after
initial installation
7. Select Thick Provision Lazy Zeroed as the disk format, and click Next.
8. Specify which networks in the inventory to use for the Panorama virtual appliance, and
click Next.
9. Confirm the selected options, click Finish to start the installation process, and click Close
when it finishes. Do not power on the Panorama virtual appliance yet.
Panorama Getting Started 61 ©2026 Palo Alto Networks, Inc.
Set Up Panorama
STEP 3 | Configure resources on the Panorama virtual appliance.
1. Right-click the Panorama virtual appliance and Edit Settings.
2. In the Hardware settings, allocate the CPUs and memory as necessary.
The virtual appliance boots up in Panorama mode if you allocate sufficient CPUs
```
and Memory and add a virtual logging disk (later in this procedure). Otherwise,
```
the appliance boots up in Management Only mode. For details on the modes,
see Panorama Models.
3. Set the SCSI Controller to LSI Logic Parallel.
4. (Optional) Add a virtual logging disk.
This step is required in the following scenarios:
• In Panorama mode to store logs on a dedicated logging disk.
• Manage your SD-WAN deployment in Management Only mode.
1. Add a disk, select Hard Disk as the hardware type, and click Next.
2. Create a new virtual disk and click Next.
3. Set the Disk Size to exactly 2TB.
```
In Panorama mode, you can later add additional logging disks (for a total
```
```
of 12) with 2TB of storage each. Expanding the size of a logging disk that is
```
already added to Panorama is not supported.
4. Select your preferred Disk Provisioning disk format.
Consider your business needs when selecting the disk provisioning format. For more
information regarding the disk provisioning performance considerations, refer to the
VMware Thick vs Thin Disks and All Flash Arrays document, or additional VMware
documentation.
When adding multiple logging disks, it is a best practice to select the same
Disk Provisioning format for all disks to avoid any unexpected performance
issues that may arise.
5. Select Specify a datastore or datastore structure as the location, Browse to a
datastore that has sufficient storage, click OK, and click Next.
6. Select a SCSI Virtual Device Node (you can use the default selection) and click Next.
Panorama will fail to boot if you select a format other than SCSI.
7. Verify that the settings are correct and click Finish.
5. Click OK to save your changes.
Panorama Getting Started 62 ©2026 Palo Alto Networks, Inc.
Set Up Panorama
STEP 4 | Power on the Panorama virtual appliance.
1. In the vSphere Client, right-click the Panorama virtual appliance and select Power >
Power On. Wait for Panorama to boot up before continuing.
2. Log in to the Panorama virtual appliance CLI from the ESXi console:
1. Right-click the Panorama virtual appliance and select Open Console.
2. Enter your username and password to log in (default is admin for both).
STEP 5 | Configure a new administrative password for the Panorama virtual appliance.
You must configure a unique administrative password before you can access the web interface
or CLI of the Panorama virtual appliance. The new password must be a minimum of eight
characters and include a minimum of one lowercase character, one uppercase character, and
one number or special character.
When you first log in to the Panorama CLI, you are prompted to enter the Old Password and
the New Password for the admin user before you can continue.
STEP 6 | Verify the Panorama is running the correct system mode.
admin> show system info
In the output, the system-mode indicates either panorama or management-only mode.
STEP 7 | Register the Panorama virtual appliance and activate the device management license and
support licenses.
1. (VM Flex Licensing Only) Provisioning the Panorama Virtual Appliance Serial Number.
When leveraging VM Flex licensing, this step is required to generate the Panorama
virtual appliance serial number needed to register the Panorama virtual appliance with
```
the Palo Alto Networks Customer Support Portal (CSP).
```
2. Register Panorama.
You must register the Panorama virtual appliance using the serial number provided by
Palo Alto Networks in the order fulfillment email.
This step is not required when leveraging VM Flex licensing as the serial number is
automatically registered with the CSP when generated.
3. Activate the firewall management license.
• Activate/Retrieve a Firewall Management License when the Panorama Virtual
Appliance is Internet-connected.
• Activate/Retrieve a Firewall Management License when the Panorama Virtual
Appliance is not Internet-connected.
4. Activate a Panorama Support License.
Panorama Getting Started 63 ©2026 Palo Alto Networks, Inc.
Set Up Panorama
STEP 8 | Increase the System Disk for Panorama on an ESXi Server if you intend to use the Panorama
virtual appliance for the following:
• Manage your SD-WAN deployment in Panorama mode.
• Requires additional storage space for dynamic updates when managing large-scale firewall
deployments.
STEP 9 | Complete configuring the Panorama virtual appliance for your deployment needs.
• For Panorama in Log Collector Mode.
1. Add a Virtual Disk to Panorama on an ESXi Server as needed.
Adding at least one virtual logging disk is required before you can change the Panorama
virtual appliance to Log Collector mode.
2. Begin at Step 6 to switch to Log Collector mode.
Enter the Public IP address of the Dedicated Log Collector when you add the
Log Collector as a managed collector to the Panorama management server. You
cannot specify the IP Address, Netmask, or Gateway.
• For Panorama in Panorama mode.
1. Add a Virtual Disk to Panorama on an ESXi Server.
Adding at least one virtual logging disk is required before you can change the Panorama
virtual appliance to Panorama mode.
2. Set up a Panorama Virtual Appliance in Panorama Mode.
3. Configure a Managed Collector.
• For Panorama in Management Only mode.
1. Set up a Panorama Virtual Appliance in Management Only Mode.
2. Configure a Managed Collector. to add a Dedicated Log Collector to the Panorama
virtual appliance.
Management Only mode does not support local log collection, and requires a Dedicated
Log Collector to store managed device logs.
• For SD-WAN deployments.
1. Increase the System Disk for Panorama on an ESXi Server
To leverage SD-WAN on Panorama deployed on ESXi, you must increase the system disk
to 224GB.
You cannot migrate back to a 81GB system disk after successfully increasing the
system disk to 224GB.
2. Set up a Panorama Virtual Appliance in Management Only Mode.
3. Add a Virtual Disk to Panorama on an ESXi Server.
To leverage SD-WAN, you must add a single 2TB logging disk to Panorama in
Management Only mode.
Panorama Getting Started 64 ©2026 Palo Alto Networks, Inc.
Set Up Panorama
Install Panorama on vCloud Air
Where Can I Use This? What Do I Need?
```
• NGFW (Managed by Panorama) • Device management licence
```
• Support license
```
• Panorama Virtual Appliance license (serial
```
```
number)
```
```
• Customer Support Portal (CSP) Account
```
Use these instructions to install a new Panorama virtual appliance in VMware vCloud Air. If you
are upgrading a Panorama virtual appliance deployed in vCloud Air, skip to Install Content and
Software Updates for Panorama.
```
STEP 1 | Download the Panorama 11.1 base image Open Virtual Appliance (OVA) file.
```
1. Go to the Palo Alto Networks software downloads site. (If you can’t log in, go to the Palo
```
Alto Networks Customer Support web site for assistance.)
```
2. In the Download column in the Panorama Base Images section, download the Panorama
```
11.1 release OVA file (Panorama-ESX-10.0.0.ova).
```
STEP 2 | Import the Panorama image to the vCloud Air catalog.
For details on these steps, refer to the OVF Tool User’s Guide.
1. Install the OVF Tool on your client system.
2. Access the client system CLI.
3. Navigate to the OVF Tool directory (for example, C:\Program Files\VMware\VMware
```
OVF Tool).
```
4. Convert the OVA file to an OVF package:
ovftool.exe <OVA‑file‑pathname> <OVF‑file‑pathname>
5. Use a browser to access the vCloud Air web console, select your Virtual
Private Cloud OnDemand location, and record the browser URL. You will
use the URL information to complete the next step. The URL format is:
```
https://<virtual‑cloud‑location>.vchs.vmware.com/compute/
```
cloud/org/<vCloud‑account‑number>/#/catalogVAppTemplateList?
```
catalog=<catalog‑ID>.
```
6. Import the OVF package, using the information from the vCloud Air URL to complete the
<virtual‑cloud‑location>, <vCloud‑account‑number>, and <catalog‑ID> variables. The
other variables are your vCloud Air username and domain <user>@<domain>, a virtual
data center <datacenter>, and a vCloud Air template <template>.
ovftool.exe -st="OVF" "<OVF‑file‑pathname>"
"vcloud://<user>@<domain>:password@<virtual-cloud-
location>.vchs.vmware.com?vdc=<datacenter>&org=<vCloud-
Panorama Getting Started 65 ©2026 Palo Alto Networks, Inc.
Set Up Panorama
account-number>&vappTemplate=<template>.ovf&catalog=default-
catalog"
STEP 3 | Install Panorama.
1. Access the vCloud Air web console and select your Virtual Private Cloud OnDemand
region.
2. Create a Panorama virtual machine. For the steps, refer to Add a Virtual Machine from
a Template in the vCloud Air Documentation Center. Configure the CPU, Memory and
Storage as follows:
• Set the CPU and Memory based on whether the virtual appliance mode: see Setup
Prerequisites for the Panorama Virtual Appliance.
• Set the Storage to configure the Panorama virtual appliance system disk. See Setup
Prerequisites for the Panorama Virtual Appliance for the supported disk sizes
based on the Panorama virtual appliance mode. For better logging and reporting
performance, select the SSD-Accelerated option.
To increase the log storage capacity, you must Add a Virtual Disk to Panorama on
vCloud Air. In Panorama mode, the virtual appliance does not use the system disk for
```
log storage; you must add a virtual logging disk.
```
STEP 4 | Create vCloud Air NAT rules on the gateway to allow inbound and outbound traffic for the
Panorama virtual appliance.
Refer to Add a NAT Rule in the vCloud Air Documentation Center for the detailed instructions:
1. Add a NAT rule that allows Panorama to receive traffic from the firewalls and allows
administrators to access Panorama.
2. Add a NAT rule that allows Panorama to retrieve updates from the Palo Alto Networks
update server and to access the firewalls.
STEP 5 | Create a vCloud Air firewall rule to allow inbound traffic on the Panorama virtual appliance.
Outbound traffic is allowed by default.
Refer to Add a Firewall Rule in the vCloud Air Documentation Center for the detailed
instructions.
STEP 6 | Power on the Panorama virtual appliance if it isn’t already on.
In the vCloud Air web console, select the Virtual Machines tab, select the Panorama virtual
machine, and click Power On.
You are now ready to Perform Initial Configuration of the Panorama Virtual Appliance.
Set Up Panorama on Alibaba Cloud
Where Can I Use This? What Do I Need?
```
• NGFW (Managed by Panorama) • Device management licence
```
• Support license
Panorama Getting Started 66 ©2026 Palo Alto Networks, Inc.
Set Up Panorama
Where Can I Use This? What Do I Need?
```
• Panorama Virtual Appliance license (serial
```
```
number)
```
```
• Customer Support Portal (CSP) Account
```
Set up a Panorama™ virtual appliance on Alibaba Cloud to centrally managed the configuration of
physical and VM-Series firewalls.
Upload the Panorama Virtual Appliance Image to Alibaba Cloud
Complete the following procedure to upload a Panorama™ management server qcow2 file
for KVM and create a custom image that you need to launch the Panorama virtual appliance.
Uploading and creating the image is required only once. You can use the same image for all
subsequent deployments of the Panorama virtual appliance.
STEP 1 | Download the Panorama qcow2 file for KVM from the Palo Alto Networks Customer
```
Support Portal (CSP).
```
1. Log in to the Palo Alto Networks CSP.
2. Select Updates > Software Updates and select Panorama Base Images from the
software updates filter drop-down.
3. Download the latest version of the Panorama-KVM qcow2 file.
STEP 2 | Log in to the Alibaba Cloud Console.
```
STEP 3 | Create an Object Storage Service (OSS) bucket for the Panorama virtual appliance image.
```
1. From the Alibaba Cloud menu, select Object Storage Service > Buckets and Create
Bucket.
2. Enter a descriptive Bucket Name.
3. Select the bucket Region.
This region must be in the same region you plan on deploying your Panorama virtual
appliance and in the same region as the firewalls you plan to manage with Panorama.
4. Configure the remaining OSS bucket settings as needed.
5. Click OK.
You are automatically taken to the OSS bucket Overview page after successful creation.
Panorama Getting Started 67 ©2026 Palo Alto Networks, Inc.
Set Up Panorama
STEP 4 | Upload the qcow2 file to the OSS bucket.
1. In the OSS bucket Overview, select Files and Upload the qcow2 file you downloaded in
the previous step.
2. For Upload To target, select Current.
3. For the File ACL, select Inherited from Bucket.
4. Click Select Files and select the qcow2 file.
Alternatively, you can drag and drop the qcow2 file into the Files to Upload section.
5. Upload the qcow2 file.
A Task List window appears displaying the upload Status. Continue to the next step after
the qcow2 file upload Status displays Uploaded.
Panorama Getting Started 68 ©2026 Palo Alto Networks, Inc.
Set Up Panorama
STEP 5 | Make the qcow2 file a bootable image.
1. In the OSS bucket Overview, select Files and click the qcow2 file you uploaded to view
the file Details.
2. Click Copy File URL and exit the file Details.
3. From the Alibaba Cloud menu, select Elastic Compute Service > Instances & Images >
Images and Import Image.
4. Paste the OSS Object Address for the qcow2 file.
This the file URL you copied in the previous step.
5. Enter an Image Name.
6. For the Operating System/Platform, select Linux CentOS.
7. For the System Disk (GiB), enter 81.
8. For the System Architecture, select x86_64.
9. For the Image Format, select QCOW2.
10. Click OK.
Panorama Getting Started 69 ©2026 Palo Alto Networks, Inc.
Set Up Panorama
Install Panorama on Alibaba Cloud
```
Use the Elastic Compute Service (ECS) to create a Panorama™ virtual appliance instance on
```
Alibaba Cloud. An ECS instance supports a single NIC by default and automatically attached an
```
Elastic Network Interface (ENI) to it. You must manually upload a Panorama virtual appliance
```
```
qcow2 image downloaded from the Palo Alto Networks Customer Supported Portal (CSP) to
```
Alibaba Cloud to successfully install the Panorama virtual appliance on Alibaba Cloud.
```
A Panorama virtual appliance deployed on Alibaba Cloud is Bring Your Own License (BYOL),
```
```
supports all deployment modes (Panorama, Log Collector, and Management Only), and shares the
```
same processes and functionality as the M-Series hardware appliances. For more information on
Panorama modes, see Panorama Models.
Review the Setup Prerequisites for the Panorama Virtual Appliance to determine the correct
```
Elastic Computer Service (ECS) instance type for your needs. The virtual resources requirement
```
for the Panorama virtual appliance is based on the total number of firewalls managed by the
```
Panorama virtual appliance and the required Logs Per Second (LPS) for forwarding logs from your
```
managed firewalls to your Log Collector.
Palo Alto Networks supports the following instance types.
• ecs.g5.xlarge, ecs.g5.2xlarge, ecs.g5.4xlarge
• ecs.sn2ne.xlarge, ecs.sn2ne.2xlarge, ecs.sn2ne.4xlarge
Under-provisioning the Panorama virtual appliance will impact management performance.
This includes the Panorama virtual appliance becoming slow or unresponsive depending
on how under-provisioning the Panorama virtual appliance is.
STEP 1 | Log in to the Alibaba Cloud Console.
Panorama Getting Started 70 ©2026 Palo Alto Networks, Inc.
Set Up Panorama
STEP 2 | Upload the Panorama Virtual Appliance Image to Alibaba Cloud.
```
STEP 3 | Set up the virtual private cloud (VPC) for your network needs.
```
Whether you launch the Panorama virtual appliance in an existing VPC or you create a new
VPC, the Panorama virtual appliance must be able to receive traffic from other instances in the
VPC and perform inbound and outbound communication between the VPC and the internet as
needed.
Refer to the Alibaba Cloud VPC documentation for more information.
1. Create a VPC and Configure Networks or use an existing VPC.
2. Verify that the network and security components are appropriately defined.
• Create an internet gateway to enable internet access to the subnet of your Panorama
virtual appliance. Internet access is required to install software and content updates,
activate licenses, and leverage Palo Alto Networks cloud services. Otherwise, you
must manually install updates and activate licenses.
• Create subnets. Subnets are segments of the IP address range assigned to the VPC in
which you can launch Alibaba Cloud instances. It is recommended that the Panorama
virtual appliance belong to the management subnet so that you can configure it to
access the internet if needed.
• Add routes to the route table for a private subnet to ensure traffic can be routed
across subnets in the VPC and from the internet if applicable.
Ensure you create routes between subnets to allow communication between:
• Panorama, managed firewalls, and Log Collectors.
```
• (Optional) Panorama and the internet.
```
• Ensure that the following ingress security rules are allowed for the VPC to manage
VPC traffic. The ingress traffic source for each rule is unique to your deployment
topology.
See Ports Used for Panorama for more information.
```
• Allow SSH (port 22) traffic to enable access to the Panorama CLI.
```
```
• Allow HTTPS (port 443 and 27280) traffic to enable access to the Panorama web
```
interface.
• Allow traffic on port 3978 to enable communication between Panorama, manage
firewalls, and managed Log Collectors. This port is also used by Log Collectors to
forward logs to Panorama.
• Allow traffic on port 28443 to enable managed firewalls to get software and
content updates from Panorama.
STEP 4 | Select Elastic Compute Service > Instances & Images > Instances and click Create Instance
in the upper right corner.
Panorama Getting Started 71 ©2026 Palo Alto Networks, Inc.
Set Up Panorama
STEP 5 | Create the Panorama virtual appliance instance.
1. Select Custom Launch.
2. Configure the Panorama virtual appliance instance.
• Billing Method—Select the desired subscription method for the instance.
• Region—Select a region of your choice. The region you select must provide on of the
supported instance types.
• Instance Type—Select one of the supported instance types. You can select Type-
based Selection to search for the instance type.
• Image— Select Custom Image and select the Panorama virtual appliance image you
uploaded.
• Storage—Choose a disk type and enter 81GiB as the system disk capacity.
```
• (Optional) Add Disk—Add additional logging disks.
```
If you intend to use the Panorama virtual appliance in Panorama mode or as a
Dedicated Log Collector, add the virtual logging disks during the initial deployment.
By default, the Panorama virtual appliance is in Panorama mode for the initial
deployment when you meet the Panorama mode resource requirements and have
added at least one virtual logging disk. Otherwise, the Panorama virtual appliance
defaults to Management Only mode. Change the Panorama virtual appliance to
Management Only mode if you just want to manage devices and Dedicated Log
Collectors, and to not collect logs locally.
The Panorama virtual appliance on Alibaba Cloud only supports 2TB logging disks,
and in total supports up to 24TB of log storage. You are unable to add a logging disk
smaller than 2TB, or a logging disk with a size not divisible by the 2TB logging disk
requirement. The Panorama virtual appliance partitions logging disks larger than 2TB
into 2TB partitions.
```
• (Optional) Snapshot—Specify how often a snapshot is automatically taken of the
```
Panorama virtual appliance instance to prevent risks and accidental data deletion.
• Duration—Specify the duration for the Panorama virtual appliance instance.
STEP 6 | Configure the Panorama virtual appliance network settings.
1. Select Next: Networking.
2. Configure the network settings for the Panorama virtual appliance instance.
• Network Type—Select the VPC and management VSwitch you created.
```
• Public IP Address—If you do not have a public IP address, enable (check) Assign
```
Public IPv4 Address and a public IPv4 address is automatically assigned to the
Panorama virtual appliance instance.
If you must use a specific IP address, or an address in a specific range, you can
request a custom IP address. Refer to the Elastic IP Address User Guide.
• Security Group—Select the management security group you created and enable Port
```
443 (HTTPS), Port 22, and Port 3389.
```
• Elastic Network Interface—No configuration needed. The Management interface is
already attached to eth0.
Panorama Getting Started 72 ©2026 Palo Alto Networks, Inc.
Set Up Panorama
STEP 7 | Configure the Panorama virtual appliance instance system settings.
1. Select Next: System Configurations.
2. Configure system settings for the Panorama virtual appliance instance.
• Logon Credentials—Select Key Pair and select the key pair. If a key pair has not
already been created, select Create Key Pair to create an new key pair on Alibaba
Cloud or import an existing key pair.
Password authentication is not supported.
• Instance Name—Enter a descriptive name for the Panorama virtual appliance. This the
name displayed for the instance throughout the Alibaba Cloud Console.
• Host—Enter a hostname for the Panorama virtual appliance instance.
```
STEP 8 | (Optional) Select Next: Grouping to configuring grouping for all Alibaba Cloud resources
```
associated with the Panorama virtual appliance instance.
STEP 9 | Select Preview to view the configuration before ordering.
STEP 10 | View and check the ECS Terms of Service and Product Terms of Service.
STEP 11 | Create Instance to create the Panorama virtual appliance instance.
When prompted, click Console to view the instance creation status.
```
STEP 12 | Allocate Elastic IP (EIP) addresses.
```
The EIP is a public IP address used to connect to the Panorama virtual appliance.
This step is required only if you want to enable internet access for the Panorama virtual
appliance.
1. Select Elastic Compute Service > Network & Security > VPC > Elastic IP Addresses >
Elastic IP Addresses.
Select Create EIP if you do not have any existing EIPs.
2. In the Actions column, select Bind Resource to bind an EIP to any interface exposed to
the Internet.
Panorama Getting Started 73 ©2026 Palo Alto Networks, Inc.
Set Up Panorama
STEP 13 | Log in to the Panorama CLI using the SSH to configure the Panorama virtual appliance
network settings.
You must configure the admin password, system IP address , netmask, and default gateway.
Additionally, you must add the Alibaba Cloud DNS servers to successfully connect to the Palo
Alto Networks update server.
You can also access the Panorama CLI from the Alibaba console. To access the
Panorama CLI from the Alibaba console, select Elastic Compute Service > Instances
& Images > Instances and select the Panorama virtual appliance instance. In the
Instance Details, select Connect.
You are prompted to create a VCN password for the Panorama virtual appliance
instance on first connection from the Alibaba VCN. Be sure to save this password as it
cannot be recovered and is required to connect using the VCN or update the password
in the future.
STEP 14 | Configure a new administrative password for the Panorama virtual appliance.
You must configure a unique administrative password before you can access the web interface
or CLI of the Panorama virtual appliance. To access the CLI, the private key used to launch the
Panorama virtual appliance is required.
The new password must be a minimum of eight characters and include a minimum of one
lowercase character, one uppercase character, and one number or special character.
Configure a new password using the following commands and follow the on screen prompts:
admin> configure
admin# set mgt-config users admin password
Panorama Getting Started 74 ©2026 Palo Alto Networks, Inc.
Set Up Panorama
STEP 15 | Configure the initial network settings for the Panorama virtual appliance.
admin> configure
admin# set deviceconfig system type static
admin# set deviceconfig system ip-address <instance-private-IP
address> netmask <netmask> default-gateway <default-gateway-IP>
The default gateway on Alibaba Cloud ends in .253. For example, if the private IP
address for your Panorama virtual appliance instance is 192.168.100.20, the default
gateway is 192.168.100.253.
admin# set deviceconfig system dns-setting servers primary
100.100.2.136
admin# set deviceconfig system dns-setting servers secondary
100.100.2.138
admin# commit
STEP 16 | Register the Panorama virtual appliance and activate the device management license and
support licenses.
1. (VM Flex Licensing Only) Provisioning the Panorama Virtual Appliance Serial Number.
When leveraging VM Flex licensing, this step is required to generate the Panorama
virtual appliance serial number needed to register the Panorama virtual appliance with
```
the Palo Alto Networks Customer Support Portal (CSP).
```
2. Register Panorama.
You must register the Panorama virtual appliance using the serial number provided by
Palo Alto Networks in the order fulfillment email.
This step is not required when leveraging VM Flex licensing as the serial number is
automatically registered with the CSP when generated.
3. Activate the firewall management license.
• Activate/Retrieve a Firewall Management License when the Panorama Virtual
Appliance is Internet-connected.
• Activate/Retrieve a Firewall Management License when the Panorama Virtual
Appliance is not Internet-connected.
4. Activate a Panorama Support License.
Panorama Getting Started 75 ©2026 Palo Alto Networks, Inc.
Set Up Panorama
STEP 17 | Complete configuring the Panorama virtual appliance for your deployment needs.
```
• (Management Only mode) Set up a Panorama Virtual Appliance in Management Only Mode.
```
```
• (Log Collector mode) Begin at Step 6 to Switch from Panorama mode to Log Collector
```
mode.
Enter the Public IP address of the Dedicated Log Collector when you Add the Log
Collector as a managed collector to the Panorama management server. You cannot
specify the IP Address, Netmask, or Gateway.
```
• (Panorama and Management Only mode) Configure a Managed Collector to add a
```
Dedicated Log Collector to the Panorama virtual appliance. Management Only mode does
not support local log collection, and requires a Dedicated Log Collector to store managed
device logs.
STEP 18 | Complete configuring the Panorama virtual appliance for your deployment needs.
• For Panorama in Log Collector Mode.
1. Add a Virtual Disk to Panorama on Alibaba Cloud as needed.
Adding at least one virtual logging disk is required before you can change the Panorama
virtual appliance to Log Collector mode.
2. Begin at Step 6 to switch to Log Collector mode.
Enter the Public IP address of the Dedicated Log Collector when you add the
Log Collector as a managed collector to the Panorama management server. You
cannot specify the IP Address, Netmask, or Gateway.
• For Panorama in Panorama mode.
1. Add a Virtual Disk to Panorama on Alibaba Cloud as needed.
Adding at least one virtual logging disk is required before you can change the Panorama
virtual appliance to Panorama mode.
2. Set up a Panorama Virtual Appliance in Panorama Mode.
3. Configure a Managed Collector.
• For Panorama in Management Only mode.
1. Set up a Panorama Virtual Appliance in Management Only Mode.
2. Configure a Managed Collector to add a Dedicated Log Collector to the Panorama virtual
appliance.
Management Only mode does not support local log collection, and requires a Dedicated
Log Collector to store managed device logs.
Install Panorama on AWS
Where Can I Use This? What Do I Need?
```
• NGFW (Managed by Panorama) • Device management licence
```
• Support license
Panorama Getting Started 76 ©2026 Palo Alto Networks, Inc.
Set Up Panorama
Where Can I Use This? What Do I Need?
```
• Panorama Virtual Appliance license (serial
```
```
number)
```
```
• Customer Support Portal (CSP) Account
```
You can now deploy Panorama™ and a Dedicated Log Collector on Amazon Web Services
```
(AWS). Panorama deployed on AWS is Bring Your Own License (BYOL), supports all deployment
```
```
modes (Panorama, Log Collector, and Management Only), and shares the same processes and
```
functionality as the M-Series hardware appliances. For more information on Panorama modes, see
Panorama Models.
STEP 1 | Log in to AWS Web Service console and select the EC2 Dashboard.
• Amazon Web Service Console
• AWS GovCloud Web Service Console
```
STEP 2 | Set up the virtual private cloud (VPC) for your network needs.
```
Whether you launch the Panorama virtual appliance in an existing VPC or you create a new
VPC, the Panorama virtual appliance must be able to receive traffic from other instances in the
VPC and perform inbound and outbound communication between the VPC and the internet as
needed.
Refer to the AWS VPC documentation for instructions on creating a VPC and setting it up for
access.
1. Create a new VPC or use an existing VPC. Refer to the AWS Getting Started
documentation
2. Verify that the network and security components are appropriately defined.
• Create an internet gateway to enable internet access to the subnet of your Panorama
virtual appliance. Internet access is required to install software and content updates,
activate licenses, and leverage Palo Alto Networks cloud services. Otherwise, you
must manually install updates and activate licenses.
• Create subnets. Subnets are segments of the IP address range assigned to the VPC in
which you can launch AWS instances. It is recommended that the Panorama virtual
Panorama Getting Started 77 ©2026 Palo Alto Networks, Inc.
Set Up Panorama
appliance belong to the management subnet so that you can configure it to access the
internet if needed.
• Add routes to the route table for a private subnet to ensure traffic can be routed
across subnets in the VPC and from the internet if applicable.
Ensure you create routes between subnets to allow communication between:
• Panorama, managed firewalls, and Log Collectors.
```
• (Optional) Panorama and the internet.
```
• Ensure that the following inbound security rules are allowed for the VPC to manage
VPC traffic. The ingress traffic source for each rule is unique to your deployment
topology.
See Ports Used for Panorama for more information.
```
• Allow SSH (port 22) traffic to enable access to the Panorama CLI.
```
```
• Allow HTTPS (port 443) traffic to enable access to the Panorama web interface.
```
• Allow traffic on port 3978 to enable communication between Panorama, manage
firewalls, and managed Log Collectors. This port is also used by Log Collectors to
forward logs to Panorama.
• Allow traffic on port 28443 to enable managed firewalls to get software and
content updates from Panorama.
STEP 3 | Deploy Panorama on Amazon Web Services.
1. Select Services > EC2 > Instances and Launch Instance.
2. Select AWS Marketplace, search for Palo Alto Networks Panorama, and Select
the Panorama AMI and Continue.
3. Choose the EC2 instance type for allocating the resources required for the Panorama
virtual appliance, and click Next: Configure Instance Details. Review the Setup
Prerequisites for the Panorama Virtual Appliance for resource requirements.
If you plan to use the Panorama virtual appliance as a Dedicated Log Collector,
ensure that you configure the appliance with the required resources during
initial deployment. The Panorama virtual appliance does not remain in Log
Collector mode if you resize the virtual machine after you deploy it, and this
results in a loss of log data.
4. Configure the instance details.
1. Select Next: Configure Instance Details.
2. For the Network, select the VPC.
3. Select the Subnet.
4. To Auto-assign Public IP select Enable.
This IP must be accessible by the firewalls you plan to manage using Panorama. This
allows you to obtain a publicly accessible IP address for the management interface
of the Panorama virtual appliance. You can later attach an Elastic IP address to the
management interface. Unlike the public IP address that is disassociated from the
virtual appliance when the instance is terminated, the Elastic IP address provides
Panorama Getting Started 78 ©2026 Palo Alto Networks, Inc.
Set Up Panorama
```
persistence and you can the IP address to a new (or replacement) instance of the
```
Panorama virtual appliance without the need to reconfigure the IP address whenever
the Panorama virtual appliance instance is powered off.
5. Configure any additional instance details as needed.
5. (Optional) Configure the Panorama virtual appliance storage.
1. Select Next: Add Storage.
2. Add New Volume to add additional log storage.
```
(SD-WAN only) If you plan on managing your SD-WAN deployment in Management
```
Only mode, you must add a 2TB logging disk.
If you intend to use the Panorama virtual appliance in Panorama mode or as a
Dedicated Log Collector, add the virtual logging disks during the initial deployment.
By default, the Panorama virtual appliance is in Panorama mode for the initial
deployment when you meet the Panorama mode resource requirements and have
added at least one virtual logging disk. Otherwise, the Panorama virtual appliance
defaults to Management Only mode. Change the Panorama virtual appliance to
Management Only mode if you just want to manage devices and Dedicated Log
Collectors, and to not collect logs locally.
The Panorama virtual appliance on AWS only supports 2TB logging disks, and in total
supports up to 24TB of log storage. You are unable to add a logging disk smaller than
2TB, or a logging disk with a size not divisible by the 2TB logging disk requirement.
The Panorama virtual appliance partitions logging disks larger than 2TB into 2TB
partitions.
6. (Optional) Select Next: Add Tags and add one or more tags as metadata to help you
identify and group the Panorama virtual appliance. For example, add a Name tag with a
Value that helps you identify which firewalls the Panorama virtual appliance manages.
7. Configure the instance security group.
1. Select Next: Configure Security Group.
2. Select an existing security group to assign a security group for the Panorama virtual
appliance instance.
3. Select the security group you previously created.
You can select the default security group to allow all inbound and outbound traffic
types.
8. Review and Launch the Panorama virtual appliance instance to verify that your
selections are accurate before you Launch.
9. Select an existing key pair or create a new one and acknowledge the disclaimer.
If you created a new key from AWS, download and save the key to a safe
location. The file extension is .pem. You must load the public key into
PuTTYgen and save it in .ppk format. You cannot regenerate this key if lost.
It takes about 30 minutes to finish deploying the Panorama virtual appliance after you
launch it on AWS. Deploying the Panorama virtual appliance may take longer depending
Panorama Getting Started 79 ©2026 Palo Alto Networks, Inc.
Set Up Panorama
on the number and size of the disks attached to the instance. View the Launch Time by
```
selecting the Panorama virtual appliance instance (Instances).
```
If you plan to use the Panorama virtual appliance as a Dedicated Log Collector,
ensure that you provision the appliance with the required resources. The
Panorama virtual appliance does not remain in Log Collector mode if you resize
the virtual machine after you deploy it and this results in a loss of log data.
STEP 4 | Shut down the Panorama virtual appliance.
1. On the EC2 Dashboard, select Instances.
2. Select the Panorama virtual appliance and click Instance State > Stop Instance.
```
STEP 5 | Create or assign an Elastic IP (EIP) address to the management interface.
```
1. Select Services > EC2 > Elastic IPs and Allocate Elastic IP address.
2. Select a Network Border Group to specify the logical group of zones from where the
public IP4v address is advertised.
3. For the Public IPv4 address pool, select Amazon’s pool of IPv4 addresses.
4. Allocate the EIP.
5. Click the IPv4 address in the Allocated IPv4 address column and Associate Elastic IP
address.
6. Select the Panorama virtual appliance Instance.
7. Select the Panorama virtual appliance Private IP address to with which to associate the
EIP.
Panorama Getting Started 80 ©2026 Palo Alto Networks, Inc.
Set Up Panorama
STEP 6 | Power on the Panorama virtual appliance.
1. On the EC2 Dashboard, select Instance.
2. From the list, select the Panorama virtual appliance and click Actions > Instance State >
Start.
STEP 7 | Configure a new administrative password for the Panorama virtual appliance.
You must configure a unique administrative password before you can access the web interface
of the Panorama virtual appliance. To access the CLI, the private key used to launch the
Panorama virtual appliance is required.
The new password must be a minimum of eight characters and include a minimum of one
lowercase character, one uppercase character, and one number or special character.
• If you have an SSH service installed on your computer:
1. Enter the following command to log into the Panorama virtual appliance:
ssh -i <private_key.ppk> admin@<public-ip_address>
2. Configure a new password using the following commands and follow the on screen
```
prompts:
```
admin> configure
Panorama Getting Started 81 ©2026 Palo Alto Networks, Inc.
Set Up Panorama
admin# set mgt-config users admin password
3. If you need to activate a BYOL, set the DNS server IP address so that the Panorama
virtual appliance can access the Palo Alto Networks licensing server. Enter the following
command to set the DNS server IP address:
admin# set deviceconfig system dns-setting servers
primary <ip_address>
4. Commit your changes with the command:
admin# commit
5. Terminate the SSH session.
• If you are using PuTTY to SSH into the Panorama virtual appliance:
1. If you are using an existing key pair and have the .ppk file available, continue to the
Step 7.3. If you created a new key pair or have only the .pem file of the existing key pair,
open PuTTYgen and Load the .pem file.
2. Save the private key to a local accessible destination.
3. Open PuTTY and select SSH > Auth and then Browse to the .ppk file you saved in the
previous step.
4. Select Sessions and enter the public IP address of the Panorama virtual appliance. Click
Open and click Yes when the security prompt appears.
5. Log in as admin when prompted.
6. Configure a new password using the following commands and follow the onscreen
```
prompts:
```
admin> configure
Panorama Getting Started 82 ©2026 Palo Alto Networks, Inc.
Set Up Panorama
admin# set mgt-config users admin password
7. Set the DNS server IP address so that the Panorama virtual appliance can access the
Palo Alto Networks licensing server. Enter the following command to set the DNS server
IP address:
admin# set deviceconfig system dns-setting servers
primary <ip_address>
8. Commit your changes with the command:
admin# commit
9. Terminate the SSH session.
STEP 8 | Register the Panorama virtual appliance and activate the device management license and
support licenses.
1. (VM Flex Licensing Only) Provisioning the Panorama Virtual Appliance Serial Number.
When leveraging VM Flex licensing, this step is required to generate the Panorama
virtual appliance serial number needed to register the Panorama virtual appliance with
```
the Palo Alto Networks Customer Support Portal (CSP).
```
2. Register Panorama.
You must register the Panorama virtual appliance using the serial number provided by
Palo Alto Networks in the order fulfillment email.
This step is not required when leveraging VM Flex licensing as the serial number is
automatically registered with the CSP when generated.
3. Activate the firewall management license.
• Activate/Retrieve a Firewall Management License when the Panorama Virtual
Appliance is Internet-connected.
• Activate/Retrieve a Firewall Management License when the Panorama Virtual
Appliance is not Internet-connected.
4. Activate a Panorama Support License.
Panorama Getting Started 83 ©2026 Palo Alto Networks, Inc.
Set Up Panorama
STEP 9 | Complete configuring the Panorama virtual appliance for your deployment needs.
• For Panorama in Log Collector Mode.
1. Add a Virtual Disk to Panorama on AWS as needed.
Adding at least one virtual logging disk is required before you can change the Panorama
virtual appliance to Log Collector mode.
2. Begin at Step 6 to switch to Log Collector mode.
Enter the Public IP address of the Dedicated Log Collector when you add the
Log Collector as a managed collector to the Panorama management server. You
cannot specify the IP Address, Netmask, or Gateway.
• For Panorama in Panorama mode.
1. Add a Virtual Disk to Panorama on AWS.
Adding at least one virtual logging disk is required before you can change the Panorama
virtual appliance to Panorama mode.
2. Set up a Panorama Virtual Appliance in Panorama Mode.
3. Configure a Managed Collector.
• For Panorama in Management Only mode.
1. Set up a Panorama Virtual Appliance in Management Only Mode.
2. Configure a Managed Collector to add a Dedicated Log Collector to the Panorama virtual
appliance.
Management Only mode does not support local log collection, and requires a Dedicated
Log Collector to store managed device logs.
Install Panorama on AWS GovCloud
Where Can I Use This? What Do I Need?
```
• NGFW (Managed by Panorama) • Device management licence
```
• Support license
```
• Panorama Virtual Appliance license (serial
```
```
number)
```
```
• Customer Support Portal (CSP) Account
```
```
You can now deploy Panorama™ and a Dedicated Log Collector on Amazon Web Services (AWS)
```
GovCloud. AWS GovCloud is an isolated AWS region that meets the regulatory and compliance
requirements of the US government agencies and customers. Panorama deployed on AWS
```
GovCloud is Bring Your Own License (BYOL), supports all deployment modes (Panorama, Log
```
```
Collector, and Management Only). For more information on Panorama modes, see Panorama
```
Models.
```
To secure your workloads that contain all categories of Controlled Unclassified Information (CUI)
```
```
data and government-oriented, publicly available data in the AWS GovCloud (US) region, the
```
Panorama virtual appliance provides the same security features offered in the standard AWS
Panorama Getting Started 84 ©2026 Palo Alto Networks, Inc.
Set Up Panorama
public cloud on AWS GovCloud. The Panorama virtual appliance on AWS GovCloud and the
standard AWS public cloud support the same features and capabilities.
Review the Setup Prerequisites for the Panorama Virtual Appliance to review the supported EC2
instance types. Once you are ready, refer to Install Panorama on AWS to install the Panorama
virtual appliance on AWS GovCloud.
See the following procedures to add additional logging storage to your Panorama virtual
appliance, or to increase the allocated CPU cores and memory:
• Add a Virtual Disk to Panorama on AWS
• Increase CPUs and Memory for Panorama on AWS
Install Panorama on Azure
Where Can I Use This? What Do I Need?
```
• NGFW (Managed by Panorama) • Device management licence
```
• Support license
```
• Panorama Virtual Appliance license (serial
```
```
number)
```
```
• Customer Support Portal (CSP) Account
```
You can now deploy Panorama™ and a Dedicated Log Collector on Microsoft Azure. Panorama
```
deployed on Azure is Bring Your Own License (BYOL), supports all deployment modes (Panorama,
```
```
Log Collector, and Management Only), and shares the same processes and functionality as the M-
```
Series hardware appliances. For more information on Panorama modes, see Panorama Models.
STEP 1 | Log into to the Microsoft Azure portal.
STEP 2 | Set up the virtual network for your network needs.
Whether you launch the Panorama virtual appliance in an existing virtual network or you
create a new virtual network, the Panorama virtual appliance must be able to receive
traffic from other instances in the virtual network and perform inbound and outbound
communication between the virtual network and the internet as needed.
Refer to the Microsoft Azure Virtual Network documentation for more information.
1. Create a Virtual Network or use an existing virtual network.
2. Verify that the network and security components are appropriately defined.
• Create a NAT gateway if you want to enable only outbound internet access for the
subnet to which the Panorama virtual appliance belongs.
• Create subnets. Subnets are segments of the IP address range assigned to the
VNet in which you can launch Microsoft Azure instances. It is recommended that
Panorama Getting Started 85 ©2026 Palo Alto Networks, Inc.
Set Up Panorama
the Panorama virtual appliance belong to the management subnet so that you can
configure it to access the internet if needed.
• Add routes to the route table for a private subnet to ensure traffic can be routed
across subnets in the VNet and from the internet if applicable.
Ensure you create routes between subnets to allow communication between:
• Panorama, managed firewalls, and Log Collectors.
```
• (Optional) Panorama and the internet.
```
• Ensure that the following ingress security rules are allowed for the VNet to manage
VNet traffic. The ingress traffic source for each rule is unique to your deployment
topology.
See Ports Used for Panorama for more information.
```
• Allow SSH (port 22) traffic to enable access to the Panorama CLI.
```
```
• Allow HTTPS (port 443) traffic to enable access to the Panorama web interface.
```
• Allow traffic on port 3978 to enable communication between Panorama, manage
firewalls, and managed Log Collectors. This port is also used by Log Collectors to
forward logs to Panorama.
• Allow traffic on port 28443 to enable managed firewalls to get software and
content updates from Panorama.
STEP 3 | Deploy the Panorama virtual appliance.
1. In the Azure Dashboard, select Virtual machines and Add a new virtual machine.
2. Search for Palo Alto Networks and select the latest Panorama virtual appliance image.
3. Create the Panorama virtual appliance.
Panorama Getting Started 86 ©2026 Palo Alto Networks, Inc.
Set Up Panorama
STEP 4 | Configure the Panorama virtual appliance.
1. Select your Azure Subscription.
2. Select the Azure Resource Group to contain all your Azure instance resources.
3. Enter a Virtual machine name for the Panorama virtual appliance.
4. Select the Region for the Panorama virtual appliance to be deployed in.
5. (Optional) Select the Availability options. See How to use availability sets for more
information.
6. Select the Image used to deploy the Panorama management server. Browse all public
and private images to deploy the Panorama management server from the Panorama
image on the Azure marketplace.
7. Configure the Panorama virtual appliance size. Review the Setup Prerequisites for the
Panorama Virtual Appliance for sizing requirements.
If you plan to use the Panorama virtual appliance as a Dedicated Log Collector,
ensure that you configure the appliance with the required resources during
initial deployment. The Panorama virtual appliance does not remain in Log
Collector mode if you resize the virtual machine after you deploy it, and this
results in a loss of log data.
8. Configure the unique Panorama virtual appliance administrator credentials.
You must configure a unique administrative password before you can access the web
interface and CLI of the Panorama virtual appliance.
1. Enter a Username for the Panorama virtual appliance administrator. To ensure that
your username is secure, admin is not a valid entry.
2. Enter a Password or copy and paste an SSH public key for securing administrative
access to the Panorama virtual appliance.
You must enable SSH key authentication if you plan to use this instance of the
Panorama virtual appliance in FIPS-CC operational mode. Although you can
deploy the Panorama virtual appliance using a username and password, you will
be unable to authenticate using the username and password after changing the
operational mode to FIPS-CC. After resetting to FIPS-CC mode, you must use
the SSH key to log in and can then configure a username and password that you
can use for subsequently logging in to the Panorama web interface. For details
on creating the SSH key, refer to the Azure documentation.
9. Configure the Panorama virtual appliance instance Networking
1. Select an existing Virtual network or create a new virtual network.
2. Configure the Subnet. The subnet is dependent on the virtual network you selected
or created in the previous step. If you selected an existing virtual network, you can
choose one of the subnets for the selected virtual network.
3. Select an existing Public IP address or create a new one. This creates the
management interface used to access your Panorama virtual appliance.
4. Select an existing NIC network security group or create a new security group.
Network security groups control traffic to the virtual machine. Make sure that HTTPS
and SSH are allowed for the Inbound rules.
Panorama Getting Started 87 ©2026 Palo Alto Networks, Inc.
Set Up Panorama
10. Configure the instance Management settings.
1. Select whether to enable Auto-shutdown. Auto-shutdown allows you to configure
a daily time to automatically shut down the virtual machine that you disable auto-
shutdown to avoid the possibility that a new public IP address gets assigned to the
virtual machine, that logs are dropped, that logs are not or that you are unable to
manage your firewalls while the Panorama virtual appliance is shut down.
2. Select whether to enable boot Monitoring. Select the Diagnostic storage account if
enabled. Monitoring automatically sends boot-up diagnostic logs to your Diagnostics
storage account. For more information, see Overview of Monitoring in Microsoft
Azure.
3. Configure any other settings as needed.
11. Review the summary, accept the terms of use and privacy policy, and Create the
Panorama virtual appliance.
STEP 5 | Verify that you the Panorama virtual appliance has been successfully deployed.
1. Select Dashboard > Resource Groups and select the resource group containing the
Panorama virtual appliance.
2. Under Settings, select Deployments for the virtual machine deployment status.
It takes about 30 minutes to deploy the Panorama virtual appliance. Launching
the Panorama virtual appliance may take longer depending on the resources
configured for the virtual machine. Microsoft Azure does not permit the ICMP
protocol to test whether it deployed successfully.
If you plan to use the Panorama virtual appliance as a Dedicated Log Collector,
ensure that you correctly configured the appliance the required resources. The
Panorama virtual appliance does not remain in Log Collector mode if you resize
the virtual machine after you deploy it and this results in a loss of log data.
STEP 6 | Configure a static Public IP address.
1. On the Azure portal, select Virtual machines and select the Panorama virtual machine.
2. Select Overview and click the Public IP address.
3. Under Assignment, select Static and Save the new IP address configuration.
STEP 7 | Log in to the web interface of the Panorama virtual appliance.
1. On the Azure portal, in All Resources, select the Panorama virtual appliance and view
the public IP address located in the Overview section.
2. Use a secure (https) connection from your web browser to log in to the Panorama virtual
appliance using the public IP address.
3. Enter the username and password of the Panorama virtual appliance. You are prompted
with a certificate warning. Accept the certificate warning and continue to the web page.
Panorama Getting Started 88 ©2026 Palo Alto Networks, Inc.
Set Up Panorama
STEP 8 | Register the Panorama virtual appliance and activate the device management license and
support licenses.
1. (VM Flex Licensing Only) Provisioning the Panorama Virtual Appliance Serial Number.
When leveraging VM Flex licensing, this step is required to generate the Panorama
virtual appliance serial number needed to register the Panorama virtual appliance with
```
the Palo Alto Networks Customer Support Portal (CSP).
```
2. Register Panorama.
You must register the Panorama virtual appliance using the serial number provided by
Palo Alto Networks in the order fulfillment email.
This step is not required when leveraging VM Flex licensing as the serial number is
automatically registered with the CSP when generated.
3. Activate the firewall management license.
• Activate/Retrieve a Firewall Management License when the Panorama Virtual
Appliance is Internet-connected.
• Activate/Retrieve a Firewall Management License when the Panorama Virtual
Appliance is not Internet-connected.
4. Activate a Panorama Support License.
STEP 9 | Complete configuring the Panorama virtual appliance for your deployment needs.
• For Panorama in Log Collector Mode.
1. Add a Virtual Disk to Panorama on Azure as needed.
Adding at least one virtual logging disk is required before you can change the Panorama
virtual appliance to Log Collector mode.
2. Begin at Step 6 to switch to Log Collector mode.
Enter the Public IP address of the Dedicated Log Collector when you add the
Log Collector as a managed collector to the Panorama management server. You
cannot specify the IP Address, Netmask, or Gateway.
• For Panorama in Panorama mode.
1. Add a Virtual Disk to Panorama on Azure.
Adding at least one virtual logging disk is required before you can change the Panorama
virtual appliance to Panorama mode.
2. Set up a Panorama Virtual Appliance in Panorama Mode.
3. Configure a Managed Collector.
• For Panorama in Management Only mode.
1. Set up a Panorama Virtual Appliance in Management Only Mode.
2. Configure a Managed Collector to add a Dedicated Log Collector to the Panorama virtual
appliance.
Management Only mode does not support local log collection, and requires a Dedicated
Log Collector to store managed device logs.
Panorama Getting Started 89 ©2026 Palo Alto Networks, Inc.
Set Up Panorama
Install Panorama on Google Cloud Platform
Where Can I Use This? What Do I Need?
```
• NGFW (Managed by Panorama) • Device management licence
```
• Support license
```
• Panorama Virtual Appliance license (serial
```
```
number)
```
```
• Customer Support Portal (CSP) Account
```
You can now deploy Panorama™ and a Dedicated Log Collector on Google Cloud Platform
```
(GCP). Panorama deployed on GCP is Bring Your Own License (BYOL), supports all deployment
```
```
modes (Panorama, Log Collector, and Management Only), and shares the same processes and
```
functionality as the M-Series hardware appliances. For more information on Panorama modes, see
Panorama Models.
To deploy the Panorama virtual appliance on GCP, you need to build a custom image. To begin
this process, you must download the Panorama tar.gz from the Palo Alto Networks Customer
Support portal and upload it to a GCP storage bucket. You can then create the custom image and
use the image to deploy the Panorama virtual appliance on GCP.
STEP 1 | Download the Panorama virtual appliance image.
1. Log in to the Palo Alto Networks Support Portal.
2. Select Updates > Software Updates and filter by Panorama Base Images.
3. Download the latest version of the Panorama on GCP tar.gz image.
Panorama Getting Started 90 ©2026 Palo Alto Networks, Inc.
Set Up Panorama
STEP 2 | Upload the Panorama virtual appliance image to the Google Cloud Platform.
1. Log in to the Google Cloud Console.
2. From the Products and Services menu, select Storage.
3. Click Create Bucket, configure the new storage bucket and click Create.
4. Select the storage bucket you created in the previous step, click Upload files, and select
the Panorama virtual appliance image you downloaded.
5. From the Products and Services menu, select Compute Engine > Images.
6. Click Create Image and create the Panorama virtual appliance image:
1. Name the Panorama virtual appliance image.
2. In the Source field, select Cloud Storage file from the drop-down menu.
3. Click Browse and navigate to the storage bucket where you uploaded the Panorama
virtual appliance image, and Select the uploaded image.
4. Create the Panorama virtual appliance image.
Panorama Getting Started 91 ©2026 Palo Alto Networks, Inc.
Set Up Panorama
Panorama Getting Started 92 ©2026 Palo Alto Networks, Inc.
Set Up Panorama
STEP 3 | Configure the Panorama virtual appliance.
1. From the Products and Services menu and select the Compute Engine.
2. Click Create Instance to begin deploying the Panorama virtual appliance.
3. Add a descriptive Name to easily identify the Panorama virtual appliance.
4. Select the Region and Zone where you want to deploy the Panorama virtual appliance.
5. Allocate the Machine Type and Customize the CPU cores, memory and CPU platform.
Review the Setup Prerequisites for the Panorama Virtual Appliance for minimum
resource requirements.
If you plan to use the Panorama virtual appliance as a Dedicated Log Collector,
ensure that you configure the appliance with the required resources during
initial deployment. The Panorama virtual appliance does not remain in Log
Collector mode if you resize the virtual machine after you deploy it, and this
results in a loss of log data.
The GCP zone selection determines the CPU platforms available to you. For
more information, refer to Regions and Zones for details.
6. Configure the Panorama boot disk.
1. For the Boot Disk, click Change > Custom image and select the Panorama image file
you uploaded in Step 2
2. Review the boot disk Size and verify the system disk is 81GB.
The Panorama virtual appliance must be initially installed with the Default
system disk size. Installing the Panorama virtual appliance with a system disk
larger than the Default system disk size is not supported and may result in
limited utilization. You have the option to increase the system disk size after
initial installation
3. Click Select to save your configuration.
7. Under Identity and API access, select Allow full access to all Cloud APIs.
Panorama Getting Started 93 ©2026 Palo Alto Networks, Inc.
Set Up Panorama
8. Under Firewall, select Allow HTTPS traffic.
STEP 4 | Expand Management, security, disks, networking, sole tenancy .
STEP 5 | Enable access to the serial port so you can manage the Panorama virtual appliance.
1. Select Management.
2. Enter the following name-value pair as Metadata:
serial-port-enable true
Panorama Getting Started 94 ©2026 Palo Alto Networks, Inc.
Set Up Panorama
STEP 6 | Reserve a static IP address for the management interface.
Reserve static internal and external IP addresses for the management interface in the
event that if the Panorama virtual appliance is rebooted, your managed devices do not lose
connection to the Panorama virtual appliance when the IP addresses are reassigned.
For more information on how to reserve IP addresses, refer to Reserving a Static Internal IP
Address and Reserving a Static External IP Address.
1. Select Networking.
2. Edit the network interface.
3. Select the Panorama virtual appliance Network.
4. Select the Panorama virtual appliance Subnetwork. Instances in the same subnetwork
will communicate with each other using their internal IP addresses.
5. Set the Primary internal IP address.
```
• Ephemeral (Automatic)— Automatically assign a primary internal IP address.
```
```
• Ephemeral (Custom)—Configure a custom IP range that GCP uses to assign a primary
```
internal IP address.
• Reserve a static internal IP address—Manually configure a static primary internal IP
address.
6. Set the External IP address.
• Ephemeral—Automatically assign an external IP address from a shared IP pool.
• Select an existing reserved external IP address.
• Create IP address—Reserve an external IP address.
7. Set IP forwarding to On to allow the Panorama virtual appliance to receive packets from
non-matching destinations or source IP addresses.
Panorama Getting Started 95 ©2026 Palo Alto Networks, Inc.
Set Up Panorama
STEP 7 | Configure the SSH key. You need an SSH key to access the Panorama virtual appliance CLI
to configure the administrative user password after the initial deployment.
• PuTTY Users
1. Select Security.
2. Select the Block project-wide SSH keys box. Only instance keys are currently supported
for logging in to the Panorama virtual appliance after initial deployment.
3. Paste the SSH key in the comment box. For information on the correct SSH key format
and how to generate SSH keys for GCP, refer to Managing SSH keys in Metadata.
When generating the SSH key, save the private key in .ppk format. The private
key is required to log in to the Panorama virtual appliance after the initial
deployment before you can configure the administrative password.
• Linux and macOS Users
1. Generate the SSH key from the CLI of your Linux device.
ssh-keygen -C admin@panorama -f <panorama_key_name>
Where admin@panorama is a comment GCP requires and <panorama_key_name> is
the name of the key file being generated.
2. Create an output file for the SSH key.
cat <panorama_key_name>.pub
After the output file for the SSH key is created, manually copy the SSH key contents.
3. Paste the public key into the SSH Keys section of the GCP instance creation.
```
STEP 8 | (Optional) Add additional storage for log collection. Repeat this step as needed to add
```
additional virtual logging disks.
If you intend to use the Panorama virtual appliance in Panorama mode or as a Dedicated Log
Collector, add the virtual logging disks during initial deployment. By default, the Panorama
virtual appliance is in Panorama mode for the initial deployment when you meet the Panorama
mode resource requirements and have added at least one virtual logging disk. Otherwise, the
Panorama Getting Started 96 ©2026 Palo Alto Networks, Inc.
Set Up Panorama
Panorama virtual appliance defaults to Management Only mode in which you can manage
devices and Dedicated Log Collectors, and cannot collect logs locally.
The Panorama virtual appliance on GCP only supports 2TB logging disks, and in total supports
up to 24TB of log storage. You are unable to add a logging disk smaller than 2TB, or a logging
Panorama Getting Started 97 ©2026 Palo Alto Networks, Inc.
Set Up Panorama
disk with a size not divisible by the 2TB logging disk requirement. The Panorama virtual
appliance partitions logging disks larger than 2TB into 2TB partitions.
1. Select Disks > Add new disk.
2. Enter the Name.
3. Expand the Type drop-down menu and select the desired type.
4. For the Source type, select Blank disk.
5. For the Mode, select Read/write.
6. Select the Deletion rule to configure whether to delete the virtual logging disk if the
Panorama virtual appliance instance is deleted. To
7. Set the Size (GB) of the virtual logging disk.
8. Set your preferred Encryption solution for the data on the virtual logging disk.
9. Click Done.
Panorama Getting Started 98 ©2026 Palo Alto Networks, Inc.
Set Up Panorama
STEP 9 | Create the Panorama virtual appliance. The Panorama virtual appliances takes roughly 10
minutes to boot up after initial deployment.
STEP 10 | Configure a new administrative password for the Panorama virtual appliance.
You must configure a unique administrative password before you can access the web interface
of the Panorama virtual appliance. To access the CLI, use the private key to launch the
Panorama virtual appliance.
The new password must be a minimum of eight characters and include a minimum of one
lowercase character, one uppercase character, and one number or special character.
• If you have an SSH service installed on your computer:
1. Enter the following command to log into the Panorama virtual appliance:
• Windows Devices
ssh -i <private_key.ppk> <username>@<public-ip_address>
• Linux Devices
ssh -i <prive_key.ppk> -oHostKeyAlgorithms=+ssh-rsa
<username>@<public-ip_address>
Including -oHostKeyAlgorithms=+ssh-rsa is required to specify the host key type. An
error is displayed if this is not included in the SSH login command.
2. Configure a new password using the following commands and follow the onscreen
```
prompts:
```
admin> configure
Panorama Getting Started 99 ©2026 Palo Alto Networks, Inc.
Set Up Panorama
admin# set mgt-config users admin password
3. If you have a BYOL that you need to, set the DNS server IP address so that the
Panorama virtual appliance can access the Palo Alto Networks licensing server. Enter the
following command to set the DNS server IP address:
admin# set deviceconfig system dns-setting servers
primary <ip_address>
4. Commit your changes:
admin# commit
5. Terminate the SSH session.
• If you are using PuTTY to SSH into the Panorama virtual appliance:
1. If you are using an existing key pair and have the .ppk file available, continue to Step
11.3. If you created a new key pair or only have the .pem file of the existing key pair,
open PuTTYgen and Load the .pem file.
2. Save the private key to a local accessible destination.
3. Open PuTTY and select SSH > Auth and Browse for the .ppk file saved in the previous
step.
4. Select Sessions and enter the public IP address of the Panorama virtual appliance. Then
Open and click Yes when the security prompt appears.
5. Login as admin when prompted.
6. Configure a new password using the following commands and follow the on screen
```
prompts:
```
admin> configure
Panorama Getting Started 100 ©2026 Palo Alto Networks, Inc.
Set Up Panorama
admin# set mgt-config users admin password
7. Set the DNS server IP address so that the Panorama virtual appliance can access the
Palo Alto Networks licensing server. Enter the following command to set the DNS server
IP address:
admin# set deviceconfig system dns-setting servers
primary <ip_address>
8. Commit your changes with the command:
admin# commit
9. Terminate the SSH session.
STEP 11 | Register the Panorama virtual appliance and activate the device management license and
support licenses.
1. (VM Flex Licensing Only) Provisioning the Panorama Virtual Appliance Serial Number.
When leveraging VM Flex licensing, this step is required to generate the Panorama
virtual appliance serial number needed to register the Panorama virtual appliance with
```
the Palo Alto Networks Customer Support Portal (CSP).
```
2. Register Panorama.
You must register the Panorama virtual appliance using the serial number provided by
Palo Alto Networks in the order fulfillment email.
This step is not required when leveraging VM Flex licensing as the serial number is
automatically registered with the CSP when generated.
3. Activate the firewall management license.
• Activate/Retrieve a Firewall Management License when the Panorama Virtual
Appliance is Internet-connected.
• Activate/Retrieve a Firewall Management License when the Panorama Virtual
Appliance is not Internet-connected.
4. Activate a Panorama Support License.
Panorama Getting Started 101 ©2026 Palo Alto Networks, Inc.
Set Up Panorama
STEP 12 | Complete configuring the Panorama virtual appliance for your deployment needs.
• For Panorama in Log Collector Mode.
1. Add a Virtual Disk to Panorama on Google Cloud Platform as needed.
Adding at least one virtual logging disk is required before you can change the Panorama
virtual appliance to Log Collector mode.
2. Begin at Step 6 to switch to Log Collector mode.
Enter the Public IP address of the Dedicated Log Collector when you add the
Log Collector as a managed collector to the Panorama management server. You
cannot specify the IP Address, Netmask, or Gateway.
• For Panorama in Panorama mode.
1. Add a Virtual Disk to Panorama on Google Cloud Platform.
Adding at least one virtual logging disk is required before you can change the Panorama
virtual appliance to Panorama mode.
2. Set up a Panorama Virtual Appliance in Panorama Mode.
3. Configure a Managed Collector.
• For Panorama in Management Only mode.
1. Set up a Panorama Virtual Appliance in Management Only Mode.
2. Configure a Managed Collector to add a Dedicated Log Collector to the Panorama virtual
appliance.
Management Only mode does not support local log collection, and requires a Dedicated
Log Collector to store managed device logs.
• For SD-WAN deployments.
1. Increase the System Disk for Panorama on Google Cloud Platform
To leverage SD-WAN on Panorama deployed on GCP, you must increase the the system
disk to 224GB.
You cannot migrate back to a 81GB system disk after successfully increasing the
system disk to 224GB.
2. Set up a Panorama Virtual Appliance in Management Only Mode.
3. Add a Virtual Disk to Panorama on Google Cloud Platform.
To leverage SD-WAN, you must add a single 2TB logging disk to Panorama in
Management Only mode.
Install Panorama on KVM
Where Can I Use This? What Do I Need?
```
• NGFW (Managed by Panorama) • Device management licence
```
• Support license
Panorama Getting Started 102 ©2026 Palo Alto Networks, Inc.
Set Up Panorama
Where Can I Use This? What Do I Need?
```
• Panorama Virtual Appliance license (serial
```
```
number)
```
```
• Customer Support Portal (CSP) Account
```
You can now deploy Panorama™ and a Dedicated Log Collector on KVM. Panorama deployed
```
on KVM is Bring Your Own License (BYOL), supports all deployment modes (Panorama, Log
```
```
Collector, and Management Only), and shares the same processes and functionality as the M-
```
Series hardware appliances. For more information on Panorama modes, see Panorama Models.
STEP 1 | Download the Panorama 11.1 base image QCOW2 file.
1. Log in to the Palo Alto Networks Support Portal.
2. Select Updates > Software Updates and filter by Panorama Base Images to download
```
the QCOW2 file (Panorama-KVM-11.1.0.qcow2).
```
STEP 2 | Create a new virtual machine image and add the Panorama virtual appliance image for KVM
to the Virtual Machine Manager.
1. On the Virtual Machine Manager, select Create a new virtual machine.
2. Select Import Existing disk image and click Forward.
3. Browse and select the Panorama virtual appliance image volume and Choose volume.
4. Click Forward.
Panorama Getting Started 103 ©2026 Palo Alto Networks, Inc.
Set Up Panorama
STEP 3 | Configure the memory and CPU settings.
Review the Setup Prerequisites for the Panorama Virtual Appliance for minimum resource
requirements.
If you plan to use the Panorama virtual appliance as a Dedicated Log Collector, ensure
that you configure the appliance with the required resources during initial deployment.
The Panorama virtual appliance does not remain in Log Collector mode if you resize
the virtual machine after you deploy it, and this results in a loss of log data.
1. Configure the Memory based on the requirements for the desired operational mode.
```
The Virtual Machine Manager may use MiB (mebibyte) to allocate memory
```
depending on the version you are running. If MiB is used, be sure to correctly
convert your required memory allocation to avoid under provisioning the
Panorama virtual appliance.
2. Configure the CPU based on the requirements for the desired operational mode.
3. Click Forward.
Panorama Getting Started 104 ©2026 Palo Alto Networks, Inc.
Set Up Panorama
STEP 4 | Name the Panorama virtual appliance, enable configuration customization, and select the
management interface bridge.
1. Enter a descriptive Name for the Panorama virtual appliance.
2. Customize configuration before install.
3. Make a Network selection—select the bridge for the management interface and accept
the default settings.
4. Click Finish.
STEP 5 | Configure the virtual system disk settings.
1. Select IDE Disk 1, go to Advanced options, and select the following:
• Disk Bus—VirtIO or IDE, depending on your configuration.
• Storage format—qcow2
2. Go to Performance options and set Cache mode to writethrough. This setting improves
installation time and execution speed on the Panorama virtual appliance.
3. Click Apply.
Panorama Getting Started 105 ©2026 Palo Alto Networks, Inc.
Set Up Panorama
STEP 6 | Configure the virtual machine console display to use the VNC server to interact with the
virtual machine.
1. Select Display Spice.
Continue to the next step if Display VNC is listed in the Hardware list because
the virtual machine is already configured to use the VNC server for the display.
2. In the Type drop-down, select VNC server.
3. Click Apply.
```
STEP 7 | (Optional) Add additional storage for log collection. Repeat this step as needed to add
```
additional virtual logging disks.
If you intend to use the Panorama virtual appliance in Panorama mode or as a Dedicated Log
Collector, add the virtual logging disks during the initial deployment. By default, the Panorama
virtual appliance is in Panorama mode for the initial deployment when you meet the Panorama
mode resource requirements and have added at least one virtual logging disk. Otherwise, the
Panorama virtual appliance defaults to Management Only mode. Change the Panorama virtual
appliance to Management Only mode if you just want to manage devices and Dedicated Log
Collectors, and to not collect logs locally.
The Panorama virtual appliance on KVM only supports 2TB logging disks, and in total supports
up to 24TB of log storage. You are unable to add a logging disk smaller than 2TB, or a logging
Panorama Getting Started 106 ©2026 Palo Alto Networks, Inc.
Set Up Panorama
disk with a size not divisible by the 2TB logging disk requirement. The Panorama virtual
appliance partitions logging disks larger than 2TB into 2TB partitions.
1. Add Hardware.
2. Configure the new Storage disk:
1. Create a disk image for a virtual machine and configure the virtual disk storage
```
capacity to 14901.2 GiB (this is equivalent to 2TB).
```
```
The Virtual Machine Manager may use GiB (gibibyte) to allocate memory
```
depending on the version you are running. If GiB is used, be sure to correctly
convert the required storage capacity to avoid under provisioning the virtual
logging disk and sending the Panorama virtual appliance into maintenance
mode.
2. Set the Device type to Disk device.
3. Set the Bus type to VirtIO or IDE, depending on your configuration.
4. Go to Advanced options and set Cache mode to writethrough.
3. Click Finish.
```
STEP 8 | Begin Installation ( ). The Panorama virtual appliances takes approximately 10
```
minutes to boot.
STEP 9 | Open a connection to the console of the Panorama virtual appliance.
You are prompted to log in to the firewall using the default username and password:
admin/admin.
STEP 10 | Configure a new administrative password for the Panorama virtual appliance.
You must configure a unique administrative password before you can access the web interface
or CLI of the Panorama virtual appliance. The new password must be a minimum of eight
characters and include a minimum of one lowercase character, one uppercase character, and
one number or special character.
When you first log in to the Panorama CLI, you are prompted to enter the Old Password and
the New Password for the admin user before you can continue.
Panorama Getting Started 107 ©2026 Palo Alto Networks, Inc.
Set Up Panorama
STEP 11 | Configure the network access settings for the management interface.
1. Enter configuration mode using the following command:
admin> configure
2. Use the following commands to configure and enable access to the management
```
interface:
```
admin# set deviceconfig system type static
admin# set deviceconfig system ip-address <Panorama-IP>
netmask <netmask> default-gateway <gateway-IP> dns-setting
servers primary <DNS-IP>
where <Panorama-IP> is the IP address you want to assign to the management interface,
<netmask> is the subnet mask, <gateway-IP> is the IP address of the network gateway,
and <DNS-IP> is the IP address of the DNS server.
admin# commit
STEP 12 | Register the Panorama virtual appliance and activate the device management license and
support licenses.
1. (VM Flex Licensing Only) Provisioning the Panorama Virtual Appliance Serial Number.
When leveraging VM Flex licensing, this step is required to generate the Panorama
virtual appliance serial number needed to register the Panorama virtual appliance with
```
the Palo Alto Networks Customer Support Portal (CSP).
```
2. Register Panorama.
You must register the Panorama virtual appliance using the serial number provided by
Palo Alto Networks in the order fulfillment email.
This step is not required when leveraging VM Flex licensing as the serial number is
automatically registered with the CSP when generated.
3. Activate the firewall management license.
• Activate/Retrieve a Firewall Management License when the Panorama Virtual
Appliance is Internet-connected.
• Activate/Retrieve a Firewall Management License when the Panorama Virtual
Appliance is not Internet-connected.
4. Activate a Panorama Support License.
Panorama Getting Started 108 ©2026 Palo Alto Networks, Inc.
Set Up Panorama
STEP 13 | Complete configuring the Panorama virtual appliance for your deployment needs.
• For Panorama in Log Collector Mode.
1. Add a Virtual Disk to Panorama on KVM as needed.
Adding at least one virtual logging disk is required before you can change the Panorama
virtual appliance to Log Collector mode.
2. Begin at Step 6 to switch to Log Collector mode.
Enter the Public IP address of the Dedicated Log Collector when you add the
Log Collector as a managed collector to the Panorama management server. You
cannot specify the IP Address, Netmask, or Gateway.
• For Panorama in Panorama mode.
1. Add a Virtual Disk to Panorama on KVM.
Adding at least one virtual logging disk is required before you can change the Panorama
virtual appliance to Panorama mode.
2. Set up a Panorama Virtual Appliance in Panorama Mode.
3. Configure a Managed Collector.
• For Panorama in Management Only mode.
1. Set up a Panorama Virtual Appliance in Management Only Mode.
2. Configure a Managed Collector to add a Dedicated Log Collector to the Panorama virtual
appliance.
Management Only mode does not support local log collection, and requires a Dedicated
Log Collector to store managed device logs.
Install Panorama on Hyper-V
Where Can I Use This? What Do I Need?
```
• NGFW (Managed by Panorama) • Device management licence
```
• Support license
```
• Panorama Virtual Appliance license (serial
```
```
number)
```
```
• Customer Support Portal (CSP) Account
```
You can now deploy Panorama™ and a Dedicated Log Collector on Hyper-V. Panorama deployed
```
on Hyper-V is Bring Your Own License (BYOL), supports all deployment modes (Panorama, Log
```
```
Collector, and Management Only), and shares the same processes and functionality as the M-
```
Series hardware appliances. For more information on Panorama modes, see Panorama Models.
Panorama virtual appliance and virtual Dedicated Log Collector on Hyper-V is available only on
PAN-OS 8.1.3 and later releases.
Panorama Getting Started 109 ©2026 Palo Alto Networks, Inc.
Set Up Panorama
STEP 1 | Download the Panorama 11.1 base image VHDX file.
1. Log in to the Palo Alto Networks Support Portal.
2. Select Updates > Software Updates and filter by Panorama Base Images to download
```
the VHDX file (Panorama-HPV-11.1.0.vhdx).
```
```
STEP 2 | Set up any vSwitch(es) that you will need. For more information, review the Virtual Switch
```
Types for more information.
1. From Hyper-V Manager, select the host and select Action > Virtual Switch Manager to
open the Virtual Switch Manager window.
2. Under Create virtual switch, select the type of vSwitch to create and click Create Virtual
Switch.
Panorama Getting Started 110 ©2026 Palo Alto Networks, Inc.
Set Up Panorama
STEP 3 | Install the Panorama virtual appliance.
1. On the Hyper-V Manager, select the host and select Action > New > Virtual Machine.
Configure the following settings in the New Virtual Machine Wizard:
1. Choose a Name and Location for the Panorama virtual appliance. The Panorama
virtual appliance stores the VHDX file at the specified location.
2. Choose Generation 1. This is the default option and the only version supported.
3. For Startup Memory, assign the memory based on the intended system mode.
See the Setup Prerequisites for the Panorama Virtual Appliance for the memory
requirements for each mode.
```
Do not enable dynamic memory; the Panorama virtual appliance requires
```
static memory allocation.
4. Configure Networking. Select an external vSwitch to connect the management
interface on the firewall.
5. To connect the Virtual Hard Disk, select Use an existing virtual hard disk and browse
to the VHDX file you downloaded earlier.
6. Review the summary and click Finish.
Panorama Getting Started 111 ©2026 Palo Alto Networks, Inc.
Set Up Panorama
STEP 4 | Allocate the Panorama virtual appliance CPU cores.
Review the Setup Prerequisites for the Panorama Virtual Appliance for minimum resource
requirements.
If you plan to use the Panorama virtual appliance as a Dedicated Log Collector, ensure
that you configure the appliance with the required resources during initial deployment.
The Panorama virtual appliance does not remain in Log Collector mode if you resize
the virtual machine after you deploy it, and this results in a loss of log data.
1. In the Hardware list, select Processor.
2. Edit the currently allocated Number of virtual processors.
STEP 5 | Connect at least one network adapter for the dataplane interface on the firewall. Repeat this
to create additional network interfaces on the Panorama virtual appliance.
1. Select Settings > Hardware > Add Hardware and select the Hardware type for your
network adapter.
Legacy Network Adapter and SR-IOV are not supported. If selected, the VM-
Series firewall will boot into maintenance mode.
2. Click OK.
```
STEP 6 | (Optional) Add additional storage for log collection. Repeat this step as needed to add
```
additional virtual logging disks. If you want to deploy the Panorama virtual appliance in
Management Only mode, continue to Step 6.
If you intend to use the Panorama virtual appliance in Panorama mode or as a Dedicated Log
Collector, add the virtual logging disks during the initial deployment. By default, the Panorama
virtual appliance is in Panorama mode for the initial deployment when you meet the Panorama
mode resource requirements and have added at least one virtual logging disk. Otherwise, the
Panorama virtual appliance defaults to Management Only mode. Change the Panorama virtual
Panorama Getting Started 112 ©2026 Palo Alto Networks, Inc.
Set Up Panorama
appliance to Management Only mode if you just want to manage devices and Dedicated Log
Collectors, and to not collect logs locally.
The Panorama virtual appliance on Hyper-V only supports 2TB logging disks, and in total
supports up to 24TB of log storage. You are unable to add a logging disk smaller than 2TB, or a
logging disk with a size not divisible by the 2TB logging disk requirement. The Panorama virtual
appliance partitions logging disks larger than 2TB into 2TB partitions.
1. On the Hyper-V Manager, select the host and select Action > New > Hard Disk.
2. If you see the Before You Begin prompt, click Next to begin adding the virtual logging
disk.
3. For the Disk Format, select VHDX. Click Next. to continue
4. For the Disk Type, select Fixed Size or Dynamically Expanding based on your needs.
Click Next to continue.
5. Specify the Name and Location for the virtual logging disk file. Click Next to continue.
6. To configure the disk, select Create a new virtual hard disk and enter the disk size. Click
Next to continue.
7. Review the Summary and Finish adding the virtual hard logging disk.
STEP 7 | Power on the Panorama virtual appliance.
1. Select the Panorama virtual appliance instance from the list of Virtual Machines.
2. Select Action > Start to power on the Panorama virtual appliance.
STEP 8 | Connect to the Panorama virtual appliance console from the Hyper-V Manager.
1. In the Virtual Machines list, select the Panorama virtual appliance.
2. Select Actions > Connect and enter the username and password to log in (default is
```
admin for both).
```
STEP 9 | Configure a new administrative password for the Panorama virtual appliance.
You must configure a unique administrative password before you can access the web interface
or CLI of the Panorama virtual appliance. The new password must be a minimum of eight
characters and include a minimum of one lowercase character, one uppercase character, and
one number or special character.
When you first log in to the Panorama CLI, you are prompted to enter the Old Password and
the New Password for the admin user before you can continue.
Panorama Getting Started 113 ©2026 Palo Alto Networks, Inc.
Set Up Panorama
STEP 10 | Configure the IP address of the management interface.
1. Enter the following commands, where <Panorama-IP> is the IP address you want to
assign to the Panorama management interface, <netmask> is the subnet mask, <gateway-
IP> is the IP address of the network gateway, and <DNS-IP> is the IP address of the DNS
```
server:
```
admin> configure
admin# set deviceconfig system ip-address <Panorama-IP>
netmask <netmask> default-gateway <gateway-IP> dns-setting
servers primary <DNS-IP>
admin# commit
admin# exit
2. Troubleshoot Connectivity to Network Resources to verify network access to external
services required for firewall management, such as the default gateway, DNS server, and
the Palo Alto Networks Update Server, as shown in the following example:
Panorama Getting Started 114 ©2026 Palo Alto Networks, Inc.
Set Up Panorama
STEP 11 | Register the Panorama virtual appliance and activate the device management license and
support licenses.
1. (VM Flex Licensing Only) Provisioning the Panorama Virtual Appliance Serial Number.
When leveraging VM Flex licensing, this step is required to generate the Panorama
virtual appliance serial number needed to register the Panorama virtual appliance with
```
the Palo Alto Networks Customer Support Portal (CSP).
```
2. Register Panorama.
You must register the Panorama virtual appliance using the serial number provided by
Palo Alto Networks in the order fulfillment email.
This step is not required when leveraging VM Flex licensing as the serial number is
automatically registered with the CSP when generated.
3. Activate the firewall management license.
• Activate/Retrieve a Firewall Management License when the Panorama Virtual
Appliance is Internet-connected.
• Activate/Retrieve a Firewall Management License when the Panorama Virtual
Appliance is not Internet-connected.
4. Activate a Panorama Support License.
STEP 12 | Complete configuring the Panorama virtual appliance for your deployment needs.
• For Panorama in Log Collector Mode.
1. Add a Virtual Disk to Panorama on Hyper-V as needed.
Adding at least one virtual logging disk is required before you can change the Panorama
virtual appliance to Log Collector mode.
2. Begin at Step 6 to switch to Log Collector mode.
Enter the Public IP address of the Dedicated Log Collector when you add the
Log Collector as a managed collector to the Panorama management server. You
cannot specify the IP Address, Netmask, or Gateway.
• For Panorama in Panorama mode.
1. Add a Virtual Disk to Panorama on Hyper-V.
Adding at least one virtual logging disk is required before you can change the Panorama
virtual appliance to Panorama mode.
2. Set up a Panorama Virtual Appliance in Panorama Mode.
3. Configure a Managed Collector.
• For Panorama in Management Only mode.
1. Set up a Panorama Virtual Appliance in Management Only Mode.
2. Configure a Managed Collector to add a Dedicated Log Collector to the Panorama virtual
appliance.
Management Only mode does not support local log collection, and requires a Dedicated
Log Collector to store managed device logs.
Panorama Getting Started 115 ©2026 Palo Alto Networks, Inc.
Set Up Panorama
```
Set Up Panorama on Oracle Cloud Infrastructure (OCI)
```
Where Can I Use This? What Do I Need?
```
• NGFW (Managed by Panorama) • Device management licence
```
• Support license
```
• Panorama Virtual Appliance license (serial
```
```
number)
```
```
• Customer Support Portal (CSP) Account
```
```
Set up a Panorama™ virtual appliance on Oracle Cloud Infrastructure (OCI) to centrally managed
```
the configuration of physical and VM-Series firewalls.
Upload the Panorama Virtual Appliance Image to OCI
Complete the following procedure to upload a Panorama qcow2 file for KVM and create a custom
image that you need to launch the Panorama virtual appliance. Uploading and creating the
image is required only once. You can use the same image for all subsequent deployments of the
Panorama virtual appliance.
STEP 1 | Download the Panorama qcow2 file for KVM from the Palo Alto Networks Customer
```
Support Portal (CSP).
```
1. Log in to the Palo Alto Networks CSP.
2. Select Updates > Software Updates and select Panorama Base Images from the
software updates filter drop-down.
3. Download the latest version of the Panorama-KVM qcow2 image.
STEP 2 | Log in to the Oracle Cloud Infrastructure console.
STEP 3 | Create a storage bucket for the qcow2 file.
1. Select Object Storage > Object Storage and Create Bucket.
2. Enter a descriptive Bucket Name.
3. For the Storage Tier, select Standard.
4. Create Bucket.
STEP 4 | Upload the qcow2 image to the OCI storage bucket.
1. Click the storage bucket you created in the previous step to view the bucket details.
2. Click Upload and select the qcow2 image you downloaded from the Palo Alto Networks
CSP.
3. Upload the image.
Panorama Getting Started 116 ©2026 Palo Alto Networks, Inc.
Set Up Panorama
STEP 5 | Create a pre-authenticated request for the qcow2 file.
This is required to create the object URL used in the creation of the custom image for the
Panorama virtual appliance.
1. Select Object Storage > Object Storage and click the storage bucket you created in the
previous step.
2. Select Pre-Authenticated Requests > Create Pre-Authenticated Request.
3. Enter a descriptive Name for your Pre-Authenticated Request.
4. Select Object and enter the qcow2 image name for the Object Name.
5. Create Pre-Authenticated Request.
6. For the Access Type, select Permit object reads and writes.
7. Enter an Expiration date and time.
8. Create Pre-Authenticated Request.
9. In the Pre-Authenticated Request Details, copy the Pre-Authenticated Request URL.
The Pre-Authenticated Request URL is required to create the custom image and
must be copied when displayed to you.
The Pre-Authenticated Request URL is only displayed after the request is
created and is not shown again.
10. Close the Pre-Authenticated Request Details after you copy the URL.
STEP 6 | Import the qcow2 file and create a custom Panorama virtual appliance image.
1. Select Compute > Custom Images and Import Image.
2. Enter a descriptive Name for your image.
3. Select Import from an Object Storage URL and paste the object storage URL.
4. For the Image type, select QCOW2.
5. For the Launch Mode, select Paravirtualized Mode.
6. Import Image.
```
Install Panorama on Oracle Cloud Infrastructure (OCI)
```
```
Create a Panorama™ virtual appliance instance on Oracle Cloud Infrastructure (OCI). An OCI
```
instance supports a single NIC by default. You must manually upload a Panorama virtual appliance
```
qcow2 image downloaded from the Palo Alto Networks Customer Supported Portal (CSP) to OCI
```
to successfully install the Panorama virtual appliance on OCI.
```
A Panorama virtual appliance deployed on OCI is Bring Your Own License (BYOL), supports
```
```
all deployment modes (Panorama, Log Collector, and Management Only), and shares the same
```
processes and functionality as the M-Series hardware appliances. For more information on
Panorama modes, see Panorama Models.
A machine running a Linux operating system is required successfully install the Panorama on
OCI. To successfully install Panorama on OCI, you must generate a .pub key using OpenSSH.
Additionally, you can only use a Linux machine to log into the Panorama CLI for the initial network
configuration.
Panorama Getting Started 117 ©2026 Palo Alto Networks, Inc.
Set Up Panorama
Review the Setup Prerequisites for the Panorama Virtual Appliance to determine the virtual
resources required for your needs. The virtual resources requirement for the Panorama virtual
appliance is based on the total number of firewalls managed by the Panorama virtual appliance
```
and the required Logs Per Second (LPS) for forwarding logs from your managed firewalls to your
```
Log Collector.
Under-provisioning the Panorama virtual appliance will impact management performance.
This includes the Panorama virtual appliance becoming slow or unresponsive depending
on how under-provisioning the Panorama virtual appliance is.
STEP 1 | Log in to the Oracle Cloud Infrastructure console.
```
STEP 2 | Set up the Virtual Cloud Network (VCN) for your network needs.
```
Whether you launch the Panorama virtual appliance in an existing VCN or you create a new
VCN, the Panorama virtual appliance must be able to receive traffic from other instances in the
VCN and perform inbound and outbound communication between the VCN and the internet
as needed.
Refer to the OCI VCN documentation for more information.
1. Configure a VCN or use an existing VCN.
2. Verify that the network and security components are appropriately defined.
• Create an internet gateway to enable internet access to the subnet of your Panorama
virtual appliance. Internet access is required to install software and content updates,
activate licenses, and leverage Palo Alto Networks cloud services. Otherwise, you
must manually install updates and activate licenses.
If the Panorama virtual appliance instance is part of a private subnet, you can
configure a NAT gateway to enable only outbound internet access for the subnet.
• Create subnets. Subnets are segments of the IP address range assigned to the VCN
in which you can launch OCI instances. It is recommended that the Panorama virtual
Panorama Getting Started 118 ©2026 Palo Alto Networks, Inc.
Set Up Panorama
appliance belong to the management subnet so that you can configure it to access the
internet if needed.
• Add routes to the route table for a private subnet to ensure traffic can be routed
across subnets in the VCN and from the internet if applicable.
Ensure you create routes between subnets to allow communication between:
• Panorama, managed firewalls, and Log Collectors.
```
• (Optional) Panorama and the internet.
```
• Ensure that the following ingress security rules are allowed for the VCN to manage
VCN traffic. The ingress traffic source for each rule is unique to your deployment
topology.
See Ports Used for Panorama for more information.
```
• Allow SSH (port 22) traffic to enable access to the Panorama CLI.
```
```
• Allow HTTPS (port 443 and 28270) traffic to enable access to the Panorama web
```
interface.
• Allow traffic on port 3978 to enable communication between Panorama, manage
firewalls, and managed Log Collectors. This port is also used by Log Collectors to
forward logs to Panorama.
• Allow traffic on port 28443 to enable managed firewalls to get software and
content updates from Panorama.
STEP 3 | Select Compute > Instances and Create Instance.
STEP 4 | Enter a descriptive Name for the Panorama virtual appliance image.
STEP 5 | Select the Availability domain.
STEP 6 | Select the Palo Alto Networks Panorama image.
See Upload the Panorama Virtual Appliance Image to OCI to upload and maintain
your own Panorama virtual appliance Custom Image on OCI.
1. Under Image and shape, select Change Image.
2. For the Image Source, select Partner Image.
If you maintain your own Panorama virtual appliance image, select Custom Image
instead and select the Panorama virtual appliance image you uploaded to OCI.
3. Search for Palo Alto Networks Panorama and select (check) the image.
Skip this step if you selected Custom Image in the previous step.
PAN-OS 10.2.0 is the default PAN-OS version.
4. Select Image.
Panorama Getting Started 119 ©2026 Palo Alto Networks, Inc.
Set Up Panorama
STEP 7 | Configure the instance resources.
Refer to the Setup Prerequisites for the Panorama Virtual Appliance for more information for
the minimum resources required based on your Panorama usage needs.
1. Under Image and shape, select Change Shape.
2. Select the shape with number of CPUs, amount of RAM, and number of interfaces you
require.
3. Select Shape.
STEP 8 | Configure the instance Networking settings.
1. For the Network, Select existing virtual cloud network and select the VCN.
2. For the Subnet, Select existing subnet and select the subnet.
It is recommended to deploy the Panorama virtual appliance instance in a management
subnet to safely allow internet access if needed.
3. (Optional) For the Public IP Address, select Assign a public IPv4 address if you want to
make the Panorama virtual appliance accessible from outside the VCN.
STEP 9 | Configure the Panorama virtual appliance instance boot volume.
1. For the Boot volume, specify a custom boot volume size.
2. For the Boot volume size, enter 81.
STEP 10 | Create the Panorama virtual appliance image.
STEP 11 | Log in to the Panorama virtual appliance CLI from the OCI console.
1. Generate a SSH Key for Panorama on OCI.
2. In the OCI console, select Instances and select the Panorama virtual appliance instance.
3. Select Console Connection and Create Console Connection.
4. Select Upload public key files (.pub) and upload the public SSH key you generated to
Create Console Connection.
5. In the Instance Details screen, expand the Console Connection options and Copy Serial
Connection for Linux/Mac.
6. On your Linux machine, open a terminal and paste the serial connection.
STEP 12 | Configure a new administrative password for the Panorama virtual appliance.
You must configure a unique administrative password before you can access the web interface
or CLI of the Panorama virtual appliance. The new password must be a minimum of eight
characters and include a minimum of one lowercase character, one uppercase character, and
one number or special character.
When you first log in to the Panorama CLI, you are prompted to enter the Old Password and
the New Password for the admin user before you can continue.
Panorama Getting Started 120 ©2026 Palo Alto Networks, Inc.
Set Up Panorama
STEP 13 | Configure the system IP address settings for the Panorama virtual appliance.
1. Configure the initial network settings for the Panorama virtual appliance.
admin> configure
admin# set deviceconfig system type static
admin# set deviceconfig system ip-address <instance-private-
IP address> netmask <netmask> default-gateway <default-
gateway-IP>
admin# set deviceconfig system dns-setting servers primary
<primary-dns-IP>
admin# set deviceconfig system dns-setting servers secondary
<secondary-dns-IP>
admin# commit
2. Verify you can log in to the Panorama web interface.
If you cannot log in to the Panorama web interface, review your route table and VCN
security rules to ensure the correct routes and security rules are created.
STEP 14 | Register the Panorama virtual appliance and activate the device management license and
support licenses.
1. (VM Flex Licensing Only) Provisioning the Panorama Virtual Appliance Serial Number.
When leveraging VM Flex licensing, this step is required to generate the Panorama
virtual appliance serial number needed to register the Panorama virtual appliance with
```
the Palo Alto Networks Customer Support Portal (CSP).
```
2. Register Panorama.
You must register the Panorama virtual appliance using the serial number provided by
Palo Alto Networks in the order fulfillment email.
This step is not required when leveraging VM Flex licensing as the serial number is
automatically registered with the CSP when generated.
3. Activate the firewall management license.
• Activate/Retrieve a Firewall Management License when the Panorama Virtual
Appliance is Internet-connected.
• Activate/Retrieve a Firewall Management License when the Panorama Virtual
Appliance is not Internet-connected.
4. Activate a Panorama Support License.
Panorama Getting Started 121 ©2026 Palo Alto Networks, Inc.
Set Up Panorama
STEP 15 | Complete configuring the Panorama virtual appliance for your deployment needs.
• For Panorama in Log Collector Mode.
1. Add a Virtual Disk to Panorama on Oracle Cloud Infrastructure (OCI) as needed.
Adding at least one virtual logging disk is required before you can change the Panorama
virtual appliance to Log Collector mode.
2. Begin at Step 6 to switch to Log Collector mode.
Enter the Public IP address of the Dedicated Log Collector when you add the
Log Collector as a managed collector to the Panorama management server. You
cannot specify the IP Address, Netmask, or Gateway.
• For Panorama in Panorama mode.
1. Add a Virtual Disk to Panorama on Oracle Cloud Infrastructure (OCI).
Adding at least one virtual logging disk is required before you can change the Panorama
virtual appliance to Panorama mode.
2. Set up a Panorama Virtual Appliance in Panorama Mode.
3. Configure a Managed Collector.
• For Panorama in Management Only mode.
1. Set up a Panorama Virtual Appliance in Management Only Mode.
2. Configure a Managed Collector to add a Dedicated Log Collector to the Panorama virtual
appliance.
Management Only mode does not support local log collection, and requires a Dedicated
Log Collector to store managed device logs.
Generate a SSH Key for Panorama on OCI
```
To connect to the Panorama™ virtual appliance installed on Oracle Cloud Infrastructure (OCI),
```
you must generate a public and private SSH key on a Linux machine. You use the generated SSH
key to log in to the Panorama CLI to set up a new administrative password and configure the
Panorama network settings.
A Linux machine is required to generate the SSH key and access the Panorama CLI for
the initial configuration. Generating a SSH from OCI or third-party applications such as
PuTTygen is not supported.
STEP 1 | Open the terminal on your Linux machine.
STEP 2 | Navigate to the hidden .ssh directory.
```
admin:~$ cd ~/.ssh
```
Panorama Getting Started 122 ©2026 Palo Alto Networks, Inc.
Set Up Panorama
STEP 3 | Generate an SSH key in the .ssh directory.
```
admin:~/.ssh$ ssh-keygen
```
When prompted, save the key in the default .ssh directory. A password for the key is
optional.
The default name for the private key is id_rsa and the default name for the public key is
id_rsa.pub.
STEP 4 | Copy the public key from the .ssh directory to your home directory.
This step is required to upload the public key to OCI.
```
admin: ~/.ssh$ cp id_rsa.pub ~
```
Perform Initial Configuration of the Panorama Virtual Appliance
Where Can I Use This? What Do I Need?
```
• NGFW (Managed by Panorama) • Device management licence
```
• Support license
• Outbound Internet Access
```
• Customer Support Portal (CSP) Account
```
Based on your Panorama model, use the Alibaba Cloud Console, AWS, Azure, GCP, or OCI web
interface, KVM Virtual Machine Manager, Hyper-V Manager, VMware vSphere Client, or vCloud
Air web console to set up network access to the Panorama virtual appliance. By default, the
Panorama virtual appliance is deployed in Panorama mode. For unified reporting, consider using
```
Greenwich Mean Time (GMT) or Coordinated Universal Time (UTC) as the uniform time zone
```
across Panorama and all the managed firewalls and Log Collectors.
Panorama Getting Started 123 ©2026 Palo Alto Networks, Inc.
Set Up Panorama
STEP 1 | Gather the required information from your network administrator.
```
Collect the following information for the management (MGT) interface:
```
```
IP address for the management (MGT) interface
```
The default management interface IP address is 192.168.1.1. if you do not
configure the management interface as described when you install the Panorama
virtual appliance.
Netmask
Default gateway
DNS server IP address
To complete the configuration of the MGT interface, you must specify the IP
```
address, netmask (for IPv4) or prefix length (for IPv6), and default gateway. If
```
```
you omit settings (such as the default gateway), you can access Panorama only
```
through the console port for future configuration changes. As a best practice,
always commit a complete MGT interface configuration.
STEP 2 | Access the console of the Panorama virtual appliance.
Panorama uses the MGT interface for management traffic, high availability synchronization, log
collection, and communication within Collector Groups.
Starting with PAN-OS 9.0.4, the default admin credentials are no longer supported.
When you first install the Panorama virtual appliance, you are required to log in to
the Panorama CLI to configure a unique admin password.
If this is the first time you are logging in to the Panorama CLI, you are prompted to
enter the Old Password and the New Password for the admin user before you can
continue with the initial configuration of the Panorama virtual appliance.
1. Access the console.
On an ESXi server:
1. Launch the VMware vSphere Client.
2. Select the Console tab for the Panorama virtual appliance and press enter to access
the login screen.
On vCloud Air:
1. Access the vCloud Air web console and select your Virtual Private Cloud OnDemand
region.
2. Select the Virtual Machines tab, right-click the Panorama virtual machine, and select
Open In Console.
2. Enter your username and password to log in (default is admin for both).
On Alibaba Cloud, AWS, Azure, GCP, KVM, Hyper-V, and OCI:
• Log in to the Panorama CLI.
Panorama Getting Started 124 ©2026 Palo Alto Networks, Inc.
Set Up Panorama
STEP 3 | Configure the network access settings for the MGT interface.
Panorama uses the MGT interface for management traffic, high availability synchronization, log
collection, and communication within Collector Groups.
1. Enter the following commands, where <Panorama-IP> is the IP address you want to
assign to the Panorama management interface, <netmask> is the subnet mask, <gateway-
IP> is the IP address of the network gateway, and <DNS-IP> is the IP address of the DNS
```
server:
```
> configure
# set deviceconfig system ip-address <Panorama-IP>
netmask <netmask> default-gateway <gateway-IP> dns-setting
servers primary <DNS-IP>
# commit
# exit
2. Troubleshoot Connectivity to Network Resources to verify network access to external
services required for firewall management, such as the default gateway, DNS server, and
the Palo Alto Networks Update Server, as shown in the following example:
Panorama Getting Started 125 ©2026 Palo Alto Networks, Inc.
Set Up Panorama
STEP 4 | Configure the general settings.
1. Using a secure connection (HTTPS) from a web browser, log in to the Panorama web
interface using the IP address and password you assigned to the management interface
```
(https://<IP address>).
```
2. Select Panorama > Setup > Management and edit the General Settings.
3. Enter a Hostname for the server and enter the network Domain name. The domain
```
name is just a label; Panorama doesn’t use it to join the domain.
```
4. Align the clock on Panorama and the managed firewalls to use the same Time Zone, for
example GMT or UTC. If you plan to use the Strata Logging Service, you must configure
NTP so that Panorama can stay in sync with the Strata Logging Service.
Timestamps are recorded when Panorama receives the logs and the managed firewalls
generate the logs. Aligning the time zones on Panorama and the firewalls ensures that
the timestamps are synchronized and the process of querying logs and generating
reports on Panorama is harmonious.
5. Enter the Latitude and Longitude to enable accurate placement of the Panorama
management server on the world map.
6. Enter the Serial Number you received in the order fulfillment email.
7. Click OK to save your changes.
```
STEP 5 | (Optional) Modify the management interface settings.
```
To configure connectivity to Panorama using an IPv6 IP address, you must configure
both an IPv4 and IPv6 to successfully configure Panorama using an IPv6 IP address.
Panorama does not support configuring the management interface with only an IPv6
IP address.
1. Select Panorama > Setup > Interfaces and click Management.
2. If your firewalls connect to the Panorama management server using a public IP address
```
that is translated to a private IP address (NAT), enter the public IP in the Public IP
```
Address field, and the private IP in the IP Address field to push both addresses to your
firewalls.
3. Select which Network Connectivity Services to allow on the interface (such as SSH
```
access).
```
Don’t select Telnet or HTTP. These services use plaintext and are less secure
than the other services.
4. Click OK to save your changes to the interface.
STEP 6 | Commit your configuration changes.
Select Commit > Commit to Panorama and Commit your changes.
Panorama Getting Started 126 ©2026 Palo Alto Networks, Inc.
Set Up Panorama
STEP 7 | Next steps...
1. If necessary, Expand Log Storage Capacity on the Panorama Virtual Appliance.
2. (Best Practice) Replace the default certificate that Panorama uses to secure HTTPS
```
traffic over the management (MGT) interface.
```
3. Activate a Panorama Support License.
4. Activate/Retrieve a Firewall Management License when the Panorama Virtual Appliance
is Internet-connected.
5. Install Content and Software Updates for Panorama.
6. Configure Administrative Access to Panorama
Set Up The Panorama Virtual Appliance as a Log Collector
Where Can I Use This? What Do I Need?
```
• NGFW (Managed by Panorama) • Device management licence
```
• Support license
• Outbound Internet Access
```
• Customer Support Portal (CSP) Account
```
If you want a dedicated virtual appliance for log collection, configure a Panorama virtual appliance
on ESXi, Alibaba Cloud, AWS, AWS GovCloud, Azure, Google Cloud Platform, KVM, Hyper-
```
V, or Oracle Cloud Infrastructure (OCI) in Log Collector mode. To do this, you first perform
```
the initial configuration of the virtual appliance in Panorama mode, which includes licensing,
```
installing software and content updates, and configuring the management (MGT) interface.
```
You then switch the Panorama virtual appliance to Log Collector mode and complete the
Log Collector configuration. Additionally, if you want to use dedicated M-Series Appliance
```
Interfaces (recommended) instead of the MGT interface for log collection and Collector Group
```
communication, you must first configure the interfaces for the Panorama management server,
then configure them for the Log Collector, and then perform a Panorama commit followed by a
Collector Group commit.
Perform the following steps to set up a new virtual appliance as a Log Collector or to convert an
existing virtual appliance that was previously deployed as a Panorama management server.
Switching the virtual appliance from Panorama mode to Log Collector mode reboots the
appliance, deletes the local Log Collector, deletes any existing log data, and deletes all
configurations except the management access settings. Switching the mode does not
delete licenses, software updates, or content updates.
STEP 1 | Set up the Panorama virtual appliance management server that will manage the Log Collector
if you have not already done so.
Perform one of the following tasks:
• Set Up the Panorama Virtual Appliance
• Set Up the M-Series Appliance
Panorama Getting Started 127 ©2026 Palo Alto Networks, Inc.
Set Up Panorama
STEP 2 | On the Panorama management server, create a device registration authentication key to
securely add the Dedicated Log Collector to Panorama management.
1. Log in to the Panorama Web Interface.
2. Select Panorama > Device Registration Auth Key and Add a new authentication key.
3. Configure the authentication key.
• Name—Add a descriptive name for the authentication key.
• Lifetime—Specify the key lifetime for how long you can use the authentication key to
onboard new Log Collectors.
• Count—Specify how many times you can use the authentication key to onboard new
Log Collectors.
• Device Type—Specify that this authentication key is used to authenticate only a Log
Collector.
You can select Any to use the device registration authentication key to
onboard firewalls, Log Collectors, and WildFire appliances.
```
• (Optional) Devices—Enter one or more device serial numbers to specify for which Log
```
Collectors the authentication key is valid.
4. Click OK.
5. Copy Auth Key and Close.
Panorama Getting Started 128 ©2026 Palo Alto Networks, Inc.
Set Up Panorama
STEP 3 | Record the management IP addresses of the Panorama management server.
```
If you deployed Panorama in a high availability (HA) configuration, you need the IP address of
```
each HA peer.
1. Log in to the web interface of the Panorama management server.
2. Record the IP Address of the solitary (non-HA) or active (HA) Panorama by selecting
Panorama > Setup > Management and checking the Management Interface Settings.
3. For an HA deployment, record the Peer HA IP Address of the passive Panorama by
selecting Panorama > High Availability and checking the Setup section.
STEP 4 | Set up the Panorama virtual appliance that will serve as a Dedicated Log Collector.
If you previously deployed this appliance as a Panorama management server, you can skip this
step because the MGT interface is already configured and the licenses and updates are already
installed.
The Panorama virtual appliance in Log Collector mode does not have a web interface for
configuration tasks, only a CLI. Therefore, before changing the mode on the Panorama virtual
appliance, use the web interface in Panorama mode to:
1. Set up the Panorama virtual appliance in one of the following supported hypervisors:
• Install Panorama on an ESXi Server
• Install Panorama on Alibaba Cloud
• Install Panorama on AWS
• Install Panorama on AWS GovCloud
• Install Panorama on Azure
• Install Panorama on Google Cloud Platform
• Install Panorama on Hyper-V
```
• Set Up Panorama on Oracle Cloud Infrastructure (OCI)
```
2. Perform Initial Configuration of the Panorama Virtual Appliance.
3. Register Panorama and Install Licenses.
4. Install Content and Software Updates for Panorama.
```
STEP 5 | (Panorama on Azure only) Modify the admin password.
```
The Dedicated Log Collector supports only the admin Administrator user in order to change
in to Log Collector mode. Modify the admin password to allow you to log in using the admin
Administrator user.
1. Log in to the Panorama Web Interface.
2. Select Panorama > Administrators and select admin.
3. Enter the Password, Confirm Password and click OK.
4. Select Commit > Commit to Panorama and Commit your changes.
Panorama Getting Started 129 ©2026 Palo Alto Networks, Inc.
Set Up Panorama
```
STEP 6 | (Panorama on AWS and Azure only) Delete all users, except for the admin user.
```
1. Log in to the Panorama Web Interface as admin.
2. Select Panorama > Administrators.
3. Select the existing Administrators, except admin, and Delete.
4. Select Commit > Commit to Panorama and Commit your changes.
STEP 7 | Log in to the Panorama CLI.
STEP 8 | Switch from Panorama mode to Log Collector mode.
1. Switch to Log Collector mode by entering the following command:
> request system system-mode logger
2. Enter Y to confirm the mode change. The virtual appliance reboots. If the reboot process
terminates your terminal emulation software session, reconnect to the virtual appliance
to see the Panorama login prompt.
If you see a CMS Login prompt, this means the Log Collector has not finished
rebooting. Press Enter at the prompt without typing a username or password.
3. Log back in to the CLI.
4. Verify that the switch to Log Collector mode succeeded:
> show system info | match system-mode
If the mode change succeeded, the output displays:
system-mode: logger
STEP 9 | Enable connectivity between the Log Collector and Panorama management server.
Enter the following commands at the Log Collector CLI, where <IPaddress1> is for the MGT
```
interface of the solitary (non-HA) or active (HA) Panorama and <IPaddress2> is for the MGT
```
```
interface of the passive (HA) Panorama, if applicable.
```
> configure
# set deviceconfig system panorama-server <IPaddress1> panorama-
server-2 <IPaddress2>
# commit
# exit
STEP 10 | Add the device registration authentication key to the Dedicated Log Collector.
admin> request authkey set <auth-key>
Panorama Getting Started 130 ©2026 Palo Alto Networks, Inc.
Set Up Panorama
STEP 11 | Record the serial number of the Log Collector.
You need the serial number to add the Log Collector as a managed collector on the Panorama
management server.
1. At the Log Collector CLI, enter the following command to display its serial number.
> show system info | match serial
2. Record the serial number.
STEP 12 | Add the Log Collector as a managed collector to the Panorama management server.
1. Select Panorama > Managed Collectors and Add a managed collector.
2. In the General settings, enter the serial number (Collector S/N) you recorded for the Log
Collector.
3. In the Panorama Server IP field, enter the IP address or FQDN of the solitary (non-HA)
```
or active (HA) Panorama. For HA deployments, enter the IP address or FQDN of the
```
passive Panorama peer in the Panorama Server IP 2 field.
These IP addresses must specify a Panorama interface that has Device Management and
Device Log Collection services enabled. By default, these services are enabled only on
the MGT interface. However, you might have enabled the services on other interfaces
when you Set Up the M-Series Appliance that is a Panorama management server.
4. Select Interfaces, click Management, and enter the Public IP Addressof the Dedicated
Log Collector.
5. Click OK twice to save your changes to the Log Collector.
6. Select Commit > Commit to Panorama and Commit your changes to the Panorama
configuration.
7. Verify that Panorama > Managed Collectors lists the Log Collector you added. The
Connected column displays a check mark to indicate that the Log Collector is connected
to Panorama. You might have to wait a few minutes before the page displays the
updated connection status.
At this point, the Configuration Status column displays Out of Sync and the Run
Time Status column displays disconnected. The status will change to In Sync and
connected after you configure a Collector Group.
STEP 13 | Enable the logging disks.
1. Select Panorama > Managed Collectors and edit the Log Collector.
2. Select Disks and Add each disk.
3. Click OK to save your changes.
4. Select Commit > Commit to Panorama and Commit your changes to the Panorama
configuration.
Panorama Getting Started 131 ©2026 Palo Alto Networks, Inc.
Set Up Panorama
```
STEP 14 | (Recommended) Configure the Ethernet1, Ethernet2, Ethernet3, Ethernet4, and Ethernet5
```
interfaces if the Panorama management server and Log Collector will use them for Device
```
Log Collection (receiving logs from firewalls) and Collector Group Communication.
```
If you previously deployed the Log Collector as a Panorama management server and
configured these interfaces, you must reconfigure them because switching to Log Collector
mode would have deleted all configurations except the management access settings.
1. Configure each interface on the Panorama management server (other than the MGT
```
interface) if you haven’t already:
```
1. Select Panorama > Setup > Interfaces and click the Interface Name.
2. Select <interface-name> to enable the interface.
3. Complete one or both of the following field sets based on the IP protocols of your
```
network:
```
• For ESXi
• IPv4—Public IP Address, IP Address, Netmask, and Default Gateway
IPv6—IPv6 Address/Prefix Length and Default IPv6 Gateway
• For Alibaba Cloud, AWS, Azure, GCP, and OCI
• Public IP address
4. Select the Device Management Services that the interface supports:
Device Management and Device Log Collection—You can assign one or more
interfaces.
Collector Group Communication—You can assign only one interface.
```
Device Deployment (software and content updates)—You can assign only one
```
interface.
5. Click OK to save your changes.
2. Configure each interface on the Log Collector (other than the MGT interface):
1. Select Panorama > Managed Collectors and edit the Log Collector.
2. Select Interfaces and click the name of the interface.
3. Select <interface-name> to enable the interface.
4. Complete one or both of the following field sets based on the IP protocols of your
```
network:
```
• For ESXi
• IPv4—Public IP Address, IP Address, Netmask, and Default Gateway
IPv6—IPv6 Address/Prefix Length and Default IPv6 Gateway
• For Alibaba Cloud, AWS, Azure, GCP, and OCI
• Public IP address
5. Select the Device Management Services that the interface supports:
Device Log Collection—You can assign one or more interfaces.
Collector Group Communication—You can assign only one interface.
Panorama Getting Started 132 ©2026 Palo Alto Networks, Inc.
Set Up Panorama
6. Click OK to save your changes to the interface.
3. Click OK to save your changes to the Log Collector.
4. Select Commit > Commit to Panorama and Commit your changes to the Panorama
configuration.
```
STEP 15 | (Optional) If your deployment is using custom certificates for authentication between
```
Panorama and managed devices, deploy the custom client device certificate. For more
information, see Configure Authentication Using Custom Certificates.
1. Select Panorama > Certificate Management > Certificate Profile and choose the
certificate profile from the drop-down or click New Certificate Profile to create one.
2. Select Panorama > Managed Collectors > Add > Communication for a Log Collector.
3. Select the Secure Client Communication check box.
4. Select the type of device certificate the Type drop-down.
• If you are using a local device certificate, select the Certificate and Certificate Profile
from the respective drop-downs.
• If you are using SCEP as the device certificate, select the SCEP Profile and Certificate
Profile from the respective drop-downs.
5. Click OK.
Panorama Getting Started 133 ©2026 Palo Alto Networks, Inc.
Set Up Panorama
```
STEP 16 | (Optional) Configure Secure Server Communication Sn a Log Collector. For more
```
information, see Configure Authentication Using Custom Certificates.
1. Select Panorama > Managed Collectors > Add > Communication.
2. Verify that the Custom Certificate Only check box is not selected. This allows you to
continue managing all devices while migrating to custom certificates.
When the Custom Certificate Only check box is selected, the Log Collector
does not authenticate and cannot receive logs from devices using predefined
certificates.
3. Select the SSL/TLS service profile from the SSL/TLS Service Profile drop-down. This
SSL/TLS service profile applies to all SSL connections between the Log Collector and
devices sending it logs.
4. Select the certificate profile from the Certificate Profile drop-down.
5. Select Authorize Client Based on Serial Number to have the server check clients against
the serial numbers of managed devices. The client certificate must have the special
keyword $UDID set as the CN to authorize based on serial numbers.
6. In Disconnect Wait Time (min), enter the number of minutes Panorama should wait
before breaking and reestablishing the connection with its managed devices. This field is
blank by default and the range is 0 to 44,640 minutes.
The disconnect wait time does not begin counting down until you commit the
new configuration.
7. (Optional) Configure an authorization list.
1. Click Add under Authorization List.
2. Select the Subject or Subject Alt Name as the Identifier type.
3. Enter an identifier of the selected type.
4. Click OK.
5. Select Check Authorization List to enforce the authorization list.
8. Click OK.
9. Select Commit > Commit to Panorama.
STEP 17 | Assign the Log Collector to a Collector Group.
1. Configure a Collector Group. You must perform a Panorama commit and then a Collector
Group commit to synchronize the Log Collector configuration with Panorama and to put
Panorama Getting Started 134 ©2026 Palo Alto Networks, Inc.
Set Up Panorama
```
the Eth1, Eth2, Eth3, Eth4, and Eth5 interfaces (if you configured them) in an operational
```
state on the Log Collector.
In any single Collector Group, all the Log Collectors must run on the same
Panorama model: all M-700 appliances, all M-600 appliances, all M-500
appliances, all M-300 appliances, all M-200 appliances, or all Panorama virtual
appliances.
As a best practice, Enable log redundancy across collectors if you add multiple
Log Collectors to a single Collector group. This option requires each Log
Collector to have the same number of logging disks.
2. Select Panorama > Managed Collectors to verify that the Log Collector configuration is
synchronized with Panorama.
The Configuration Status column should display In Sync and the Run Time Status column
should display connected.
3. Access the Log Collector CLI and enter the following command to verify that its
interfaces are operational:
> show interface all
The output displays the state as up for each interface that is operational.
4. If the Collector Group has multiple Log Collectors, troubleshoot connectivity to network
resources to verify they can communicate with each other by performing a Ping
connectivity test for each interface that the Log Collectors use. For the source IP
address, specify the interface of one of the Log Collectors. For the host IP address,
specify the matching interface of another Log Collector in the same Collector Group.
STEP 18 | Next steps...
To enable the Log Collector to receive firewall logs:
1. Configure Log Forwarding to Panorama.
2. Verify Log Forwarding to Panorama.
Set Up the Panorama Virtual Appliance with Local Log Collector
Where Can I Use This? What Do I Need?
```
• NGFW (Managed by Panorama) • Device management licence
```
• Support license
• Outbound Internet Access
```
• Customer Support Portal (CSP) Account
```
If the Panorama virtual appliance is in Legacy mode after you upgrade from a Panorama 8.0 or
```
earlier release to a Panorama 8.1 (or later) release, switch to Panorama mode in order to create a
```
Panorama Getting Started 135 ©2026 Palo Alto Networks, Inc.
Set Up Panorama
local Log Collector, add multiple logging disks without losing existing logs. increase log storage up
to 24TB, and enable faster report generation.
Once you change from Legacy mode to Panorama mode, Legacy mode will no longer be
available.
After upgrading to Panorama 8.1, the first step is to increase the system resources on the virtual
appliance to the minimum required for Panorama mode. Panorama reboots when you increase
resources, so perform this procedure during a maintenance window. You must install a larger
```
system disk (81GB), increase CPUs and memory based on the log storage capacity, and add a
```
virtual logging disk. The new logging disk must have at least as much capacity as the appliance
currently uses in Legacy mode and cannot be less than 2TB. Adding a virtual disk enables you to
migrate existing logs to the Log Collector and enables the Log Collector to store new logs.
If Panorama is deployed in an HA configuration, perform the following steps on the secondary
peer first and then on the primary peer.
STEP 1 | Determine which system resources you need to increase before the virtual appliance can
operate in Panorama mode.
You must run the command specified in this step even if you have determined that
Panorama already has adequate resources.
1. Access the Panorama CLI:
1. Use terminal emulation software such as PuTTY to open an SSH session to the IP
address that you specified for the Panorama MGT interface.
2. Log in to the CLI when prompted.
2. Check the resources you must increase by running the following command:
> request system system-mode panorama
Enter y when prompted to continue. The output specifies the resources you must
increase. For example:
Panorama mode not supported on current system disk of size
52.0 GB.
Please attach a disk of size 81.0 GB, then use 'request system
clone-system-disk' to migrate the current system disk
Please add a new virtual logging disk with more than 50.00 GB
of storage capacity.
Not enough CPU cores: Found 4 cores, need 8 cores
Panorama Getting Started 136 ©2026 Palo Alto Networks, Inc.
Set Up Panorama
STEP 2 | Increase the CPUs and memory, and replace the system disk with a larger disk.
1. Access the VMware ESXi vSphere Client, select Virtual Machines, right-click the
Panorama virtual appliance, and select Power > Power Off.
2. Right-click the Panorama virtual appliance and Edit Settings.
3. Select Memory and enter the new Memory Size.
4. Select CPUs and specify the number of CPUs (the Number of virtual sockets multiplied
```
by the Number of cores per socket).
```
5. Add a virtual disk.
You will use this disk to replace the existing system disk.
1. In the Hardware settings, Add a disk, select Hard Disk as the hardware type, and click
Next.
2. Create a new virtual disk and click Next.
3. Set the Disk Size to exactly 81GB and select the Thick Provision Lazy Zeroed disk
format.
4. Select Specify a datastore or datastore structure as the location, Browse to a
datastore of at least 81GB, click OK, and click Next.
5. Select a SCSI Virtual Device Node (you can use the default selection) and click Next.
Panorama will fail to boot if you select a format other than SCSI.
6. Verify that the settings are correct and then click Finish and OK.
6. Right-click the Panorama virtual appliance and select Power > Power On. Wait for
Panorama to reboot before continuing.
7. Return to the Panorama CLI and copy the data from the original system disk to the new
system disk:
> request system clone-system-disk target sdb
Enter y when prompted to continue.
The copying process takes around 20 to 25 minutes, during which Panorama reboots.
When the process finishes, the output tells you to shut down Panorama.
8. Return to the vSphere Client console, right-click the Panorama virtual appliance, and
select Power > Power Off.
9. Right-click the Panorama virtual appliance and Edit Settings.
10. Select the original system disk, click Remove, select Remove from virtual machine, and
click OK.
11. Right-click the Panorama virtual appliance and Edit Settings.
12. Select the new system disk, set the Virtual Device Node to SCSI (0:0), and click OK.
13. Right-click the Panorama virtual appliance and select Power > Power On. Before
```
proceeding, wait for Panorama to reboot on the new system disk (around 15 minutes).
```
Panorama Getting Started 137 ©2026 Palo Alto Networks, Inc.
Set Up Panorama
STEP 3 | Add a virtual logging disk.
This is the disk to which you will migrate existing logs.
1. In the VMware ESXi vSphere Client, right-click the Panorama virtual appliance and select
Power > Power Off.
2. Right-click the Panorama virtual appliance and Edit Settings.
3. Repeat the steps to Add a virtual disk. Set the Disk Size to a multiple of 2TB based on
the amount of log storage you need. The capacity must be at least as large as the existing
virtual disk or NFS storage that Panorama currently uses for logs. The disk capacity must
be a multiple of 2TB and can be up to 24TB. For example, if the existing disk has 5TB of
log storage, you must add a new disk of at least 6TB.
After you switch to Panorama mode, Panorama will automatically divide the new disk
into 2TB partitions, each of which will function as a separate virtual disk.
4. Right-click the Panorama virtual appliance and select Power > Power On. Wait for
Panorama to reboot before continuing.
STEP 4 | Switch from Legacy mode to Panorama mode.
After switching the mode, the appliance reboots again and then automatically creates a
local Log Collector and Collector Group. The existing logs won’t be available for querying or
reporting until you migrate them later in this procedure.
1. Return to the Panorama CLI and run the following command.
> request system system-mode panorama
Enter y when prompted to continue. After rebooting, Panorama automatically creates a
```
local Log Collector (named Panorama) and creates a Collector Group (named default) to
```
contain it. Panorama also configures the virtual logging disk you added and divides it into
```
separate 2TB disks. Wait for the process to finish and for Panorama to reboot (around
```
```
five minutes) before continuing.
```
2. Log in to the Panorama web interface.
3. In the Dashboard, General Information settings, verify that the Mode is now panorama.
In an HA deployment, the secondary peer is in a suspended state at this point because
```
its mode (Panorama) does not match the mode on the primary peer (Legacy). You will un-
```
Panorama Getting Started 138 ©2026 Palo Alto Networks, Inc.
Set Up Panorama
suspend the secondary peer after switching the primary peer to Panorama mode later in
this procedure.
4. Select Panorama > Collector Groupsto verify that the default collector group has been
created, and that the local Log Collector is part of the default collector group.
5. Push the configuration to the managed devices.
• If there are no pending changes:
1. Select Commit > Push to Devices and Edit Selections.
2. Select Collector Group and make sure the default collector group is selected.
3. Click OK and Push.
• If you have pending changes:
1. Select Commit > Commit and Push and Edit Selections.
2. Verify that your Device Group devices and Templates are included.
3. Select Collector Group and make sure the default collector group is selected.
4. Click OK and Commit and Push.
6. Select Panorama > Managed Collectors and verify that the columns display the following
information for the local Log Collector:
• Collector Name—This defaults to the Panorama hostname. It should be listed under
the default Collector Group.
• Connected—Check mark
• Configuration Status—In sync
• Run Time Status—connected
```
STEP 5 | (HA only) Switch the primary Panorama from Legacy mode to Panorama mode.
```
This step triggers failover.
1. Repeat Step 1 through Step 4 on the primary Panorama.
Wait for the primary Panorama to reboot and return to an active HA state. If preemption
is not enabled, you must manually fail back: select Panorama > High Availability and, in
the Operational Commands section, Make local Panorama functional.
2. On the primary Panorama, select Dashboard and, in the High Availability section, Sync to
peer, click Yes, and wait for the Running Config to display Synchronized status.
3. On the secondary Panorama, select Panorama > High Availability and, in the Operational
Commands section, Make local Panorama functional.
This step is necessary to bring the secondary Panorama out of its suspended HA state.
Panorama Getting Started 139 ©2026 Palo Alto Networks, Inc.
Set Up Panorama
STEP 6 | Migrate existing logs to the new virtual logging disks.
If you deployed Panorama in an HA configuration, perform this only on the primary peer.
Palo Alto Networks recommends migrating existing logs to the new virtual logging
disks during your maintenance window. The log migration requires a large number
of the Panorama virtual appliance CPU cores to execute and impacts Panorama
operational performance.
1. Return to the Panorama CLI.
2. Start the log migration:
> request logdb migrate vm start
The process duration varies by the volume of log data you are migrating. To check the
status of the migration, run the following command:
> request logdb migrate vm status
When the migration finishes, the output displays: migrationhas been done.
3. Verify that the existing logs are available.
1. Log in to the Panorama web interface.
2. Select Panorama > Monitor, select a log type that you know matches some existing
```
logs (for example, Panorama > Monitor > System), and verify that the logs display.
```
STEP 7 | Next steps...
Configure log forwarding to Panorama so that the Log Collector receives new logs from
firewalls.
Set up a Panorama Virtual Appliance in Panorama Mode
Where Can I Use This? What Do I Need?
```
• NGFW (Managed by Panorama) • Device management licence
```
• Support license
• Outbound Internet Access
```
• Customer Support Portal (CSP) Account
```
Panorama mode allows the Panorama™ virtual appliance to operate as a Panorama management
server with local log collection capabilities. By default, the Panorama virtual appliance is deployed
in Panorama mode when at least one virtual logging disk is attached to a Panorama virtual
appliance.
STEP 1 | Log in to the Panorama CLI.
Panorama Getting Started 140 ©2026 Palo Alto Networks, Inc.
Set Up Panorama
STEP 2 | Switch to Panorama mode.
1. Change to Panorama mode:
> request system system-mode panorama
2. Enter Y to confirm the mode change. The Panorama virtual appliance reboots. If the
reboot process terminates your terminal emulation software session, reconnect to the
Panorama virtual appliance to see the Panorama login prompt.
If you see a CMS Login prompt, this means the Panorama virtual appliance has not
finished rebooting. Press Enter at the prompt without typing a username or password.
STEP 3 | Verify that the switch to Panorama mode succeeded.
1. Log back in to the CLI.
2. Verify that the switch to Panorama mode succeeded:
> show system info | match system-mode
If the mode change succeeded, the output displays:
> system mode:panorama
Set up a Panorama Virtual Appliance in Management Only Mode
Where Can I Use This? What Do I Need?
```
• NGFW (Managed by Panorama) • Device management licence
```
• Support license
• Outbound Internet Access
```
• Customer Support Portal (CSP) Account
```
Management Only mode allows the Panorama virtual appliance to operate strictly as a Panorama
management server without local log collection capabilities. By default, the Panorama virtual
appliance is in Panorama mode for the initial deployment. It is recommended to change the
Panorama virtual appliance to Management Only immediately after the initial deployment
because changing to Management Only mode requires that there are no logs being forwarded
to the Panorama management server because the Panorama virtual appliance in Management
Only mode does not support log collection. After you change to Management Only mode, any
existing log data stored on the Panorama virtual appliance becomes inaccessible, and the ACC and
reporting features cannot query the logs stored on the Panorama virtual appliance.
If you configured a local Log Collector, the local Log Collector still exists on Panorama
when you change to Management Only mode despite having no log collection capabilities.
```
Deleting the local Log Collector (Panorama > Managed Collectors) deletes the Eth1/1
```
interface configuration the local Log Collector uses by default. If you decide to delete the
local Log Collector, you must reconfigure the Eth1/1 interface.
Panorama Getting Started 141 ©2026 Palo Alto Networks, Inc.
Set Up Panorama
STEP 1 | Log in to the Panorama CLI.
STEP 2 | Switch to Management Only mode.
1. Change to Management Only mode:
> request system system-mode management-only
2. Enter Y to confirm the mode change. The Panorama virtual appliance reboots. If the
reboot process terminates your terminal emulation software session, reconnect to the
Panorama virtual appliance to see the Panorama login prompt.
If you see a CMS Login prompt, this means the Panorama virtual appliance has not
finished rebooting. Press Enter at the prompt without typing a username or password.
STEP 3 | Verify that the switch to Management Only mode succeeded.
1. Log back in to the CLI.
2. Verify that the switch to Management Only mode succeeded:
> show system info | match system-mode
If the mode change succeeded, the output displays:
> system mode:management-only
Expand Log Storage Capacity on the Panorama Virtual Appliance
Where Can I Use This? What Do I Need?
```
• NGFW (Managed by Panorama) • Device management licence
```
• Support license
```
• Customer Support Portal (CSP) Account
```
As of September 1, 2025, the legacy mode is no longer supported on Panorama. For
additional information, see the official end-of-life notice.
After you Perform Initial Configuration of the Panorama Virtual Appliance, the available log
```
storage capacity and the options for expanding it depend on the virtual platform (VMware ESXi,
```
vCloud Air, Alibaba Cloud, AWS, AWS GovCloud, Azure, Google Cloud Platform, KVM, Hyper-V,
```
or OCI) and mode ( Panorama or Log Collector mode): see Panorama Models for details.
```
To expand the log storage capacity on the Panorama virtual appliance, you must add additional
logging disks. Expanding the log storage capacity of an existing logging disk is not supported,
```
and Panorama does not recognize the additional storage capacity. For example; if you added a
```
2TB logging disk, and then expanded that existing logging disk to 4TB, Panorama continues to
recognize the logging disk as having 2TB of storage capacity and ignores the additional 2TB of
storage capacity.
Panorama Getting Started 142 ©2026 Palo Alto Networks, Inc.
Set Up Panorama
For additional log storage, you can also forward firewall logs to Dedicated Log Collectors
```
(see Configure a Managed Collector) or Configure Log Forwarding from Panorama to
```
External Destinations.
Before expanding log storage capacity on Panorama, Determine Panorama Log Storage
Requirements.
• Add a Virtual Disk to Panorama on an ESXi Server
• Add a Virtual Disk to Panorama on vCloud Air
• Add a Virtual Disk to Panorama on Alibaba Cloud
• Add a Virtual Disk to Panorama on AWS
• Add a Virtual Disk to Panorama on Azure
• Add a Virtual Disk to Panorama on Google Cloud Platform
• Add a Virtual Disk to Panorama on KVM
• Add a Virtual Disk to Panorama on Hyper-V
```
• Add a Virtual Disk to Panorama on Oracle Cloud Infrastructure (OCI)
```
Add a Virtual Disk to Panorama on an ESXi Server
Where Can I Use This? What Do I Need?
```
• NGFW (Managed by Panorama) • Panorama virtual appliance operating in
```
Panorama mode or Log Collector mode on
VMware ESXi
• Initial logging disk of exactly 2TB
To expand log storage capacity on the Panorama virtual appliance, you can add virtual logging
disks. If the appliance is in Panorama mode, you can add 1 to 12 virtual logging disks of 2TB each
or 1 24TB logging disk, for a maximum total of 24TB. Additionally, it is recommended to add
logging disks with the same disk provisioning format to avoid any unexpected performance that
may arise from having multiple disk with different provisioning formats.
If Panorama loses connectivity to the new virtual disk, Panorama might lose logs during
the failure interval.
To allow for redundancy, use the virtual disk in a RAID configuration. RAID10 provides the
best write performance for applications with high logging characteristics.
If necessary, you can Replace the Virtual Disk on an ESXi Server.
Panorama Getting Started 143 ©2026 Palo Alto Networks, Inc.
Set Up Panorama
STEP 1 | Add additional disks to Panorama
In all modes, the first logging disk on the Panorama VM must be at least 2TB in order
to add additional disks. If the first logging disk is smaller than 2TB, you will be unable
to add additional disk space.
1. Access the VMware vSphere Client and select Virtual Machines.
2. Right-click the Panorama virtual appliance and select Power > Power off.
3. Right-click the Panorama virtual appliance and select Edit Settings.
4. Click Add in the Hardware tab to launch the Add Hardware wizard.
5. Select Hard Disk as the hardware type and click Next.
6. Create a new virtual disk and click Next.
7. Set the Disk Size. If the Panorama virtual appliance is in Panorama mode, set the size to
at least 2TB.
In Panorama mode, you can add disk sizes larger than 2TB and Panorama will
automatically create as many 2TB partitions as possible. For example, if disk sdc
was 24TB, it will create 12 2TB partitions. These disks will be named sdc1-12.
8. Select the Disk Provisioning format and click Next.
9. Specify a datastore or datastore structure, Browse to a datastore with enough space for
the specified Disk Size, click OK, and click Next.
10. Select a SCSI Virtual Device Node (you can use the default selection) and click Next.
```
The selected node must be in SCSI format; Panorama will fail to boot if you
```
select another format.
11. Verify that the settings are correct and then click Finish and OK.
The new disk appears in the list of devices for the virtual appliance.
12. Repeat Step 4 through Step 11 to add additional disks to the Panorama virtual appliance
if necessary.
13. Right click the Panorama virtual appliance and select Power > Power On. The virtual disk
initializes for first-time use. The size of the new disk determines how long initialization
takes.
STEP 2 | Configure each disk.
The following example uses the sdc virtual disk.
1. Log in to the Panorama CLI.
2. Enter the following command to view the disks on the Panorama virtual appliance:
show system disk details
The user will see the following response:
Name
: sdb
```
State : Present
```
```
Size : 2048000 MB
```
Panorama Getting Started 144 ©2026 Palo Alto Networks, Inc.
Set Up Panorama
```
Status : Available
```
```
Reason : Admin enabled
```
```
Name : sdc
```
```
State : Present
```
```
Size : 2048000 MB
```
```
Status : Available
```
```
Reason : Admin disabled
```
3. Enter the following command and confirm the request when prompted for all disks with
the Reason : Admin disabled response:
request system disk add sdc
The request system disk add command is not available on a Panorama
management server in Management Only mode because logging is not
supported in this mode. If you do not see the command, Set up a Panorama
Virtual Appliance in Panorama Mode to enable the logging disks. Once in
Panorama mode, Log in to the Panorama CLI and continue to Step 4 to verify
the disk addition.
4. Enter the show system disk details command to verify the status of the disk
addition. Continue to Step 3 when all newly added disk responses display Reason :
Admin enabled.
STEP 3 | Make disks available for logging.
1. Log in to the Panorama web interface.
2. Select Panorama > Managed Collectors and edit the Log Collector.
3. Select Disks and Add each newly added disk.
4. Click OK.
5. Select Commit > Commit to Panorama.
```
For Panorama in an Active/Passive high availability (HA) configuration, wait for
```
HA sync to complete before continuing.
6. Select Commit > Push to Devices and push the changes to the Collector Group the Log
Collector belongs to.
STEP 4 | Configure Panorama to receive logs.
This step is intended for new Panorama deployments in Panorama mode. If you are adding
logging disks to an existing Panorama virtual appliance, continue to Step 5.
1. Configure a Managed Collector.
2. Configure a Collector Group.
3. Configure Log Forwarding to Panorama.
STEP 5 | Verify that the Panorama Log Storage capacity has been increased.
1. Log in to the Panorama web interface.
2. Select Panorama > Collector Groups and select the Collector Group that the Panorama
virtual appliance belongs to.
3. Verify that the Log Storage capacity accurately displays the disk capacity.
Panorama Getting Started 145 ©2026 Palo Alto Networks, Inc.
Set Up Panorama
Add a Virtual Disk to Panorama on vCloud Air
Where Can I Use This? What Do I Need?
```
• NGFW (Managed by Panorama) • Panorama virtual appliance operating in
```
Panorama mode or Log Collector mode on
vCloud Air
• Initial logging disk of exactly 2TB
You can add virtual logging disks to expand log storage capacity on the Panorama™ virtual
appliance. If the appliance is in Panorama mode, you can add 1 to 12 virtual logging disks of 2TB
each or 1 24TB logging disk, for a maximum total of 24TB.
If Panorama loses connectivity to the new virtual disk, Panorama might lose logs for the
duration of the failure.
If necessary, you can Replace the Virtual Disk on an ESXi Server.
STEP 1 | Add additional disks to Panorama.
In all modes, the first logging disk on the Panorama VM must be at least 2TB to add
additional disks. If the first logging disk is less than 2TB, you will be unable to add
additional disk space.
1. Access the vCloud Air web console and select your Virtual Private Cloud On Demand
region.
2. Select the Panorama virtual appliance in the Virtual Machines tab.
3. Add another disk (Actions > Edit Resources).
4. Set the Storage size. If the Panorama virtual appliance is in Panorama mode, set the size
to at least 2TB.
In Panorama mode, you can add disk sizes larger than 2TB and Panorama will
automatically create as many 2TB partitions as possible. For example, if disk sdc
was 24TB, Panorama will create 12 2TB partitions. These disks will be named
sdc1 through sdc12.
5. Set the storage tier to Standard or SSD-Accelerated.
6. Repeat the previous steps to add additional disks to the Panorama virtual appliance as
needed.
7. Save your changes.
Panorama Getting Started 146 ©2026 Palo Alto Networks, Inc.
Set Up Panorama
STEP 2 | Configure each disk.
The following example uses the sdc virtual disk.
1. Log in to the Panorama CLI.
2. Enter the following command to view the disks on the Panorama virtual appliance:
show system disk details
The user will see the following response:
Name
: sdb
```
State : Present
```
```
Size : 2048000 MB
```
```
Status : Available
```
```
Reason : Admin enabled
```
```
Name : sdc
```
```
State : Present
```
```
Size : 2048000 MB
```
```
Status : Available
```
```
Reason : Admin disabled
```
3. Enter the following command and confirm the request when prompted for all disks with
the Reason : Admin disabled response:
request system disk add sdc
The request system disk add command is not available on a Panorama
management server in Management Only mode because logging is not
supported in this mode. If you do not see the command, Set up a Panorama
Virtual Appliance in Panorama Mode to enable the logging disks. Once in
Panorama mode, Log in to the Panorama CLI and continue to Step 4 to verify
the disk addition.
4. Enter the show system disk details command to verify the status of the disk
addition. Continue to the next step when all newly added disk responses display
```
Reason : Admin enabled.
```
STEP 3 | Make disks available for logging.
1. Log in to the Panorama web interface.
2. Select Panorama > Managed Collectors and edit the Log Collector.
3. Select Disks and Add each new disk.
4. Click OK.
5. Select Commit > Commit to Panorama.
```
For Panorama in an Active/Passive high availability (HA) configuration, wait for
```
HA sync to complete before continuing.
6. Select Commit > Push to Devices and push the changes to the Collector Group the Log
Collector belongs to.
Panorama Getting Started 147 ©2026 Palo Alto Networks, Inc.
Set Up Panorama
STEP 4 | Configure Panorama to receive logs.
This step is intended for new Panorama deployments in Panorama mode. If you are adding
logging disks to an existing virtual Panorama appliance, continue to the next step.
1. Configure a Managed Collector.
2. Configure a Collector Group.
3. Configure Log Forwarding to Panorama.
STEP 5 | Verify that the Panorama Log Storage capacity has been increased.
1. Log in to the Panorama web interface.
2. Select Panorama > Collector Groups and select the Collector Group to which the virtual
Panorama appliance belongs.
3. Verify that the Log Storage capacity accurately displays your new disk capacity.
Add a Virtual Disk to Panorama on Alibaba Cloud
Where Can I Use This? What Do I Need?
```
• NGFW (Managed by Panorama) • Panorama virtual appliance operating in
```
Panorama mode or Log Collector mode on
Alibaba
• Initial logging disk of exactly 2TB
After you Install Panorama on Alibaba Cloud, add additional virtual logging disks to expand log
storage capacity on the Panorama™ virtual appliance for logs generated by managed firewalls.
You can add virtual disks to a local Log Collector for a Panorama virtual appliance in Panorama
mode or for a Dedicated Log Collector. To add virtual disks, you must have access to the Alibaba
```
Cloud Console, the Panorama command-line interface (CLI), and the Panorama web interface.
```
The Panorama virtual appliance on Alibaba Cloud supports only 2TB logging disks and, in total,
supports up to 24TB of log storage. You cannot add a logging disk smaller than 2TB or a logging
disk of a size that is not evenly divisible by 2TB because the Panorama virtual appliance partitions
logging disks in to 2TB partitions. For example, if you attach a 4TB logging disk, Panorama will
create two 2TB partitions. However, you cannot add a 5TB logging disk because the leftover 1TB
is not supported as a partition.
STEP 1 | Log in to the Alibaba Cloud Console.
STEP 2 | Select Elastic Compute Service > Instances & Images > Instances and navigate to the
Panorama virtual appliance instance.
Panorama Getting Started 148 ©2026 Palo Alto Networks, Inc.
Set Up Panorama
STEP 3 | Add a virtual logging disk to Panorama.
In all modes, the first logging disk on the Panorama VM must be at least 2TB in order
to add additional disks. If the first logging disk is smaller than 2TB, you will be unable
to add additional disk space.
1. In the Actions column, select Manage.
2. Select Cloud Disk and Create Disk.
3. Configure the virtual logging disk.
• Attach—Select Attach to ECS Instance.
• ECS Instance—Select the region and the Panorama virtual appliance instance.
• Storage—Select type of virtual disk and enter the disk capacity.
```
• (Optional) Quantity—Specify how many virtual disks to create. By default, 1 virtual
```
disk is created. When creating multiple logging disks, be sure that the sum of all
virtual disks does not exceed 24TB.
• Terms of Service—Review the Alibaba Cloud Terms of Service and check after you
have reviewed.
4. Preview the virtual disk creation.
5. Create the new virtual disk.
A status window displays after you create the new virtual disk. After the virtual disk is
successfully created, Go to the Disk List to confirm the disk is successfully created.
STEP 4 | Configure each disk.
The following example uses the sdc virtual disk.
1. Log in to the Panorama CLI.
2. Enter the following command to view the disks on the Panorama virtual appliance:
show system disk details
The user will see the following response:
```
Name : sdb
```
```
State : Present
```
```
Size : 2048000 MB
```
```
Status : Available
```
Panorama Getting Started 149 ©2026 Palo Alto Networks, Inc.
Set Up Panorama
```
Reason : Admin disabled
```
3. Enter the following command and confirm the request when prompted for all disks with
the Reason : Admin disabled response:
request system disk add sdc
The request system disk add command is not available on a Panorama
management server in Management Only mode because logging is not
supported in this mode. If you do not see the command, Set up a Panorama
Virtual Appliance in Panorama Mode to enable the logging disks. Once in
Panorama mode, log in to the Panorama CLI and continue to the next step to
verify the disk addition.
4. Enter the show system disk details command to verify the status of the disk
addition. Continue to the next step when all newly added disk responses display
```
Reason : Admin enabled.
```
STEP 5 | Make disks available for logging.
1. Log in to the Panorama web interface.
2. Edit a Log Collector (Panorama > Managed Collectors).
3. Select Disks and Add each newly added disk.
4. Click OK.
5. Select Commit > Commit to Panorama.
```
For Panorama in an Active/Passive high availability (HA) configuration, wait for
```
HA sync to complete before continuing.
6. Select Commit > Push to Devices and push the changes to the Collector Group the Log
Collector belongs to.
```
STEP 6 | (New Panorama deployments in Panorama mode only) Configure Panorama to receive logs.
```
If you are adding logging disks to an existing Panorama virtual appliance, skip to step 6.
1. Configure a Collector Group.
2. Configure Log Forwarding to Panorama
STEP 7 | Verify that the Panorama Log Storage capacity is increased.
1. Log in to the Panorama web interface.
2. Select the Collector Group to which the Panorama virtual appliance belongs (Panorama
```
> Collector Groups).
```
3. Verify that the Log Storage capacity accurately displays the disk capacity.
Add a Virtual Disk to Panorama on AWS
Where Can I Use This? What Do I Need?
```
• NGFW (Managed by Panorama) • Panorama virtual appliance operating in
```
Panorama mode or Log Collector mode on
AWS
Panorama Getting Started 150 ©2026 Palo Alto Networks, Inc.
Set Up Panorama
Where Can I Use This? What Do I Need?
• Initial logging disk of exactly 2TB
After you Install Panorama on AWS or Install Panorama on AWS GovCloud, add virtual logging
disks to the Panorama™ virtual appliance instance to provide storage for logs generated by
managed firewalls. You can add virtual disks to a local log Collector for a Panorama virtual
appliance in Panorama mode or for a Dedicated Log Collector. To add virtual disks, you must have
```
access to the Amazon Web Service Console, the Panorama command-line interface (CLI), and the
```
Panorama web interface.
The Panorama virtual appliance on AWS supports only 2TB logging disks and, in total, supports up
to 24TB of log storage. You cannot add a logging disk smaller than 2TB or a logging disk of a size
that is not evenly divisible by 2TB because the Panorama virtual appliance partitions logging disks
in to 2TB partitions. For example, if you attach a 4TB logging disk, Panorama will create two 2TB
partitions. However, you cannot add a 5TB logging disk because the leftover 1TB is not supported
as a partition.
STEP 1 | Log in to AWS Web Service console and select the EC2 Dashboard.
• Amazon Web Service Console
• AWS GovCloud Web Service Console
Panorama Getting Started 151 ©2026 Palo Alto Networks, Inc.
Set Up Panorama
STEP 2 | Add a virtual logging disk to Panorama.
In all modes, the first logging disk on the Panorama VM must be at least 2TB in order
to add additional disks. If the first logging disk is smaller than 2TB, you will be unable
to add additional disk space.
1. On the EC2 Dashboard, select Volumes and Create Volume:
• Select your preferred Volume Type. For general purpose use, select General Purpose
```
SSD (GP2).
```
• Configure the Size of the volume as 2048 GiB.
• Select the same Availability Zone that your Panorama virtual appliance instance is
located in.
```
• (Optional) Encrypt the volume.
```
```
• (Optional) Add tags to your volume.
```
2. Click Create Volume.
3. In the Volumes page, select the volume you, and select Actions > Attach Volume.
4. Attach the Panorama virtual appliance Instance.
1. Select your Panorama Instance.
2. Specify the Device name for the logging disk volume you created.
Panorama Getting Started 152 ©2026 Palo Alto Networks, Inc.
Set Up Panorama
STEP 3 | Configure each disk.
The following example uses the sdc virtual disk.
1. Log in to the Panorama CLI.
2. Enter the following command to view the disks on the Panorama virtual appliance:
show system disk details
The user will see the following response:
```
Name : nvme1n1
```
```
State : Present
```
```
Size : 2048000 MB
```
```
Status : Available
```
```
Reason : Admin enabled
```
```
Name : nvme2n1
```
```
State : Present
```
```
Size : 2048000 MB
```
```
Status : Available
```
```
Reason : Admin disabled
```
3. Enter the following command and confirm the request when prompted for all disks with
the Reason : Admin disabled response:
request system disk add nvme2n1
The request system disk add command is not available on a Panorama
management server in Management Only mode because logging is not
supported in this mode. If you do not see the command, Set up a Panorama
Virtual Appliance in Panorama Mode to enable the logging disks. Once in
Panorama mode, Log in to the Panorama CLI and continue to Step 4 to verify
the disk addition.
4. Enter the show system disk details command to verify the status of the disk
addition. Continue to the next step when all newly added disk responses display
```
Reason : Admin enabled.
```
STEP 4 | Make disks available for logging.
1. Log in to the Panorama web interface.
2. Add the Log Collector to Panorama (Panorama > Managed Collectors).
3. Select Commit > Commit to Panorama.
4. Edit the Log Collector (Panorama > Managed Collectors) and select Disks. Select the
disks that do not match the local disk names.
5. Add each newly added disk and click OK.
6. Select Commit > Commit to Panorama.
```
For Panorama in an Active/Passive high availability (HA) configuration, wait for
```
HA sync to complete before continuing.
7. Select Commit > Push to Devices and push the changes to the Collector Group the Log
Collector belongs to.
Panorama Getting Started 153 ©2026 Palo Alto Networks, Inc.
Set Up Panorama
```
STEP 5 | (New Panorama deployments in Panorama mode only) Configure Panorama to receive logs.
```
If you are adding logging disks to an existing Panorama virtual appliance, skip to step 6.
1. Configure a Collector Group.
2. Configure Log Forwarding to Panorama.
STEP 6 | Verify that the Panorama Log Storage capacity is increased.
1. Log in to the Panorama web interface.
2. Select the Collector Group to which the Panorama virtual appliance belongs (Panorama
```
> Collector Groups).
```
3. Verify that the Log Storage capacity accurately displays the disk capacity.
Add a Virtual Disk to Panorama on Azure
Where Can I Use This? What Do I Need?
```
• NGFW (Managed by Panorama) • Panorama virtual appliance operating in
```
Panorama mode or Log Collector mode on
Azure
• Initial logging disk of exactly 2TB
After you Install Panorama on Azure, add virtual logging disks to the Panorama™ virtual appliance
instance to provide storage for logs generated by managed firewalls. You can add virtual disks to
a local log Collector for a Panorama virtual appliance in Panorama mode or for a Dedicated Log
Collector. To add virtual disks, you must have access to the Microsoft Azure portal, the Panorama
```
command-line interface (CLI), and the Panorama web interface.
```
The Panorama virtual appliance on Azure supports only 2TB logging disks and, in total, supports
up to 24TB of log storage. You cannot add a logging disk smaller than 2TB or a logging disk of a
size that is not evenly divisible by 2TB because the Panorama virtual appliance partition logging
disks in to 2TB partitions. For example, if you attach a 4TB logging disk, Panorama will create
two 2TB partitions. However, you cannot add a 5TB logging disk because the leftover 1TB is not
supported as a partition.
STEP 1 | Log in to the Microsoft Azure portal.
Panorama Getting Started 154 ©2026 Palo Alto Networks, Inc.
Set Up Panorama
STEP 2 | Add a virtual logging disk to Panorama.
In all modes, the first logging disk on the Panorama VM must be at least 2TB in order
to add additional disks. If the first logging disk is smaller than 2TB, you will be unable
to add additional disk space.
1. In the Azure Dashboard, select the Panorama Virtual Machines to which you want to
add a logging disk.
2. Select Disks.
3. +Add data disk.
4. In the drop-down for the new disk, Create disk.
5. Configure the logging disk.
1. Enter the disk Name.
2. Select the Resource group. If you Create new resource groups, enter the group name.
3. Verify the Account type (this field is automatically populated).
4. In the Source type drop-down, select None.
5. Select Change Size and select a 2048 GiB logging disk.
6. Create the new logging disk.
Panorama Getting Started 155 ©2026 Palo Alto Networks, Inc.
Set Up Panorama
7. For the Host caching, select Read/write.
STEP 3 | Enable each disk.
The following example uses the sdc virtual disk.
1. Log in to the Panorama CLI.
2. Enter the following command to view the disks on the Panorama virtual appliance:
show system disk details
The user will see the following response:
Name
: sdb
```
State : Present
```
```
Size : 2048000 MB
```
```
Status : Available
```
```
Reason : Admin enabled
```
```
Name : sdc
```
```
State : Present
```
```
Size : 2048000 MB
```
```
Status : Available
```
Panorama Getting Started 156 ©2026 Palo Alto Networks, Inc.
Set Up Panorama
```
Reason : Admin disabled
```
3. Enter the following command and confirm the request when prompted for all disks with
the Reason : Admin disabled response:
request system disk add sdc
The request system disk add command is not available on a Panorama
management server in Management Only mode because logging is not
supported in this mode. If you do not see the command, Set up a Panorama
Virtual Appliance in Panorama Mode to enable the logging disks. Once in
Panorama mode, Log in to the Panorama CLI and continue to Step 4 to verify
the disk addition.
4. Enter the show system disk details command to verify the status of the disk
addition. Continue to the next step when all newly added disk responses display
```
Reason : Admin enabled.
```
STEP 4 | Make disks available for logging.
1. Log in to the Panorama web interface.
2. Edit a Log Collector (Panorama > Managed Collectors)
3. Select Disks and Add each newly added disk.
4. Click OK.
5. Select Commit > Commit to Panorama.
```
For Panorama in an Active/Passive high availability (HA) configuration, wait for
```
HA sync to complete before continuing.
6. Select Commit > Push to Devices and push the changes to the Collector Group the Log
Collector belongs to.
```
STEP 5 | (New Panorama deployments in Panorama mode only) Configure Panorama to receive logs.
```
If you are adding logging disks to an existing Panorama virtual appliance, skip to step 6.
1. Configure a Collector Group.
2. Configure Log Forwarding to Panorama.
STEP 6 | Verify that the Panorama Log Storage capacity is increased.
1. Log in to the Panorama web interface.
2. Select the Collector Group to which the Panorama virtual appliance belongs (Panorama
```
> Collector Groups).
```
3. Verify that the Log Storage capacity accurately displays the disk capacity.
Add a Virtual Disk to Panorama on Google Cloud Platform
Where Can I Use This? What Do I Need?
```
• NGFW (Managed by Panorama) • Panorama virtual appliance operating in
```
Panorama mode or Log Collector mode on
Google Cloud Platform
Panorama Getting Started 157 ©2026 Palo Alto Networks, Inc.
Set Up Panorama
Where Can I Use This? What Do I Need?
• Initial logging disk of exactly 2TB
After you Install Panorama on Google Cloud Platform, add virtual logging disks to the Panorama™
virtual appliance instance to provide storage for logs generated by managed firewalls. You can
add virtual disks to a local log Collector for a Panorama virtual appliance in Panorama mode or for
a Dedicated Log Collector. The Panorama virtual appliance on Google Cloud Platform supports
only 2TB logging disks and, in total, supports up to 24TB of log storage. You cannot add a logging
disk smaller than 2TB or a logging disk of a size that is not evenly divisible by 2TB because the
Panorama virtual appliance partitions logging disks in to 2TB partitions. For example, if you attach
a 4TB logging disk, Panorama will create two 2TB partitions. However, you cannot add a 5TB
logging disk because the leftover 1TB is not supported as a partition.
STEP 1 | Log in to the Google Cloud Console.
STEP 2 | Add the virtual logging disk.
In all modes, the first logging disk on the Panorama VM must be at least 2TB in order
to add additional disks. If the first logging disk is smaller than 2TB, you will be unable
to add additional disk space.
1. In the Products & Services menu, select and then Edit the Panorama virtual appliance
```
instance (Compute Engine > VM Instances).
```
2. In the Additional Disks section, Add Item.
3. Create disk (Name drop-down).
Panorama Getting Started 158 ©2026 Palo Alto Networks, Inc.
Set Up Panorama
STEP 3 | Configure the virtual logging disks.
1. Enter the Name.
2. Expand the Disk Type drop-down menu and select the desired type.
3. For the Source type, select None (blank disk).
4. Set the Size (GB) of the virtual logging disk.
5. Click Create.
6. Save the changes to update the Panorama virtual appliance instance.
STEP 4 | Configure each disk.
The following example uses the sdc virtual disk.
1. Log in to the Panorama CLI.
2. Enter the following command to view the disks on the Panorama virtual appliance:
show system disk details
The user will see the following response:
Name
: sdb
```
State : Present
```
```
Size : 2048000 MB
```
Panorama Getting Started 159 ©2026 Palo Alto Networks, Inc.
Set Up Panorama
```
Status : Available
```
```
Reason : Admin enabled
```
```
Name : sdc
```
```
State : Present
```
```
Size : 2048000 MB
```
```
Status : Available
```
```
Reason : Admin disabled
```
3. Enter the following command and confirm the request when prompted for all disks with
the Reason : Admin disabled response:
request system disk add sdc
The request system disk add command is not available on a Panorama
management server in Management Only mode because logging is not
supported in this mode. If you do not see the command, Set up a Panorama
Virtual Appliance in Panorama Mode to enable the logging disks. Once in
Panorama mode, Log in to the Panorama CLI and continue to Step 4 to verify
the disk addition.
4. Enter the show system disk details command to verify the status of the disk
addition. Continue to the next step when all newly added disk responses display
```
Reason : Admin enabled.
```
STEP 5 | Make disks available for logging.
1. Log in to the Panorama web interface.
2. Edit a Log Collector (Panorama > Managed Collectors).
3. Select Disks and Add each newly added disk.
4. Click OK.
5. Select Commit > Commit to Panorama.
```
For Panorama in an Active/Passive high availability (HA) configuration, wait for
```
HA sync to complete before continuing.
6. Select Commit > Push to Devices and push the changes to the Collector Group the Log
Collector belongs to.
```
STEP 6 | (New Panorama deployments in Panorama mode only) Configure Panorama to receive logs.
```
If you are adding logging disks to an existing Panorama virtual appliance, skip to step 7.
1. Configure a Collector Group.
2. Configure Log Forwarding to Panorama.
STEP 7 | Verify that the Panorama Log Storage capacity is increased.
1. Log in to the Panorama web interface.
2. Select the Collector Group to which the Panorama virtual appliance belongs (Panorama
```
> Collector Groups).
```
3. Verify that the Log Storage capacity accurately displays the disk capacity.
Panorama Getting Started 160 ©2026 Palo Alto Networks, Inc.
Set Up Panorama
Add a Virtual Disk to Panorama on KVM
Where Can I Use This? What Do I Need?
```
• NGFW (Managed by Panorama) • Panorama virtual appliance operating in
```
Panorama mode or Log Collector mode on
KVM
• Initial logging disk of exactly 2TB
After you Install Panorama on KVM, add virtual logging disks to the Panorama™ virtual appliance
instance to provide storage for logs generated by managed firewalls. You can add virtual disks to
a local log Collector for a Panorama virtual appliance in Panorama mode or for a Dedicated Log
Collector. The Panorama virtual appliance on KVM supports only 2TB logging disks and, in total,
supports up to 24TB of log storage. You cannot add a logging disk smaller than 2TB or a logging
disk of a size that is not evenly divisible by 2TB because the Panorama virtual appliance partitions
logging disks in to 2TB partitions. For example, if you attach a 4TB logging disk, Panorama will
create two 2TB partitions. However, you cannot add a 5TB logging disk because the leftover 1TB
is not supported as a partition.
STEP 1 | Shutdown the Panorama virtual appliance instance on the Virtual Machine Manager.
STEP 2 | Double-click the Panorama virtual appliance instance in the Virtual Machine Manager and
Show virtual hardware details .
Panorama Getting Started 161 ©2026 Palo Alto Networks, Inc.
Set Up Panorama
STEP 3 | Add the virtual logging disk. Repeat this step as many times as needed.
In all modes, the first logging disk on the Panorama VM must be at least 2TB in order
to add additional disks. If the first logging disk is smaller than 2TB, you will be unable
to add additional disk space.
1. Create a disk image for a virtual image (Add Hardware > Storage) and configure the
virtual disk storage capacity to the appropriate 2TB value:2000GB or 14901.2GiB
depending on your Virtual Machine Manager.
```
Depending on the version, some Virtual Machine Managers use GiB (gibibyte)
```
to allocate memory. Be sure you correctly convert the required storage capacity
to avoid under provisioning the virtual logging disk and sending the Panorama
virtual appliance into maintenance mode.
2. In the Device type drop-down, select Disk device.
3. In the Bus type drop-down, select VirtIO or IDE based on your configuration.
4. Expand Advanced options and, in the Cache mode drop-down, select writethrough.
5. Click Finish.
STEP 4 | Power on the Panorama virtual appliance instance.
STEP 5 | Configure each disk.
The following example uses the sdc virtual disk.
1. Log in to the Panorama CLI.
2. Enter the following command to view the disks on the Panorama virtual appliance:
show system disk details
The user will see the following response:
Name
: sdb
```
State : Present
```
```
Size : 2048000 MB
```
```
Status : Available
```
```
Reason : Admin enabled
```
Panorama Getting Started 162 ©2026 Palo Alto Networks, Inc.
Set Up Panorama
```
Name : sdc
```
```
State : Present
```
```
Size : 2048 MB
```
```
Status : Available
```
```
Reason : Admin disabled
```
3. Enter the following command and confirm the request when prompted for all disks with
the Reason : Admin disabled response:
request system disk add sdc
The request system disk add command is not available on a Panorama
management server in Management Only mode because logging is not
supported in this mode. If you do not see the command, Set up a Panorama
Virtual Appliance in Panorama Mode to enable the logging disks. Once in
Panorama mode, Log in to the Panorama CLI and continue to Step 4 to verify
the disk addition.
4. Enter the show system disk details command to verify the status of the disk
addition. Continue to the next step when all newly added disk responses display
```
Reason : Admin enabled.
```
STEP 6 | Make disks available for logging.
1. Log in to the Panorama web interface.
2. Edit a Log Collector (Panorama > Managed Collectors).
3. Select Disks and Add each newly added disk.
4. Click OK.
5. Select Commit > Commit to Panorama.
```
For Panorama in an Active/Passive high availability (HA) configuration, wait for
```
HA sync to complete before continuing.
6. Select Commit > Push to Devices and push the changes to the Collector Group the Log
Collector belongs to.
```
STEP 7 | (New Panorama deployments in Panorama mode only) Configure Panorama to receive logs.
```
If you are adding logging disks to an existing Panorama virtual appliance, skip to step 8.
1. Configure a Collector Group.
2. Configure Log Forwarding to Panorama.
STEP 8 | Verify that the Panorama Log Storage capacity is increased.
1. Log in to the Panorama web interface.
2. Select the Collector Group to which the Panorama virtual appliance belongs (Panorama
```
> Collector Groups).
```
3. Verify that the Log Storage capacity accurately displays the disk capacity.
Panorama Getting Started 163 ©2026 Palo Alto Networks, Inc.
Set Up Panorama
Add a Virtual Disk to Panorama on Hyper-V
Where Can I Use This? What Do I Need?
```
• NGFW (Managed by Panorama) • Panorama virtual appliance operating in
```
Panorama mode or Log Collector mode on
Hyper-V
• Initial logging disk of exactly 2TB
After you Install Panorama on Hyper-V, add virtual logging disks to the Panorama™ virtual
appliance instance to provide storage for logs generated by managed firewalls. You can add
virtual disks to a local log Collector for a Panorama virtual appliance in Panorama mode or for a
Dedicated Log Collector. The Panorama virtual appliance on Hyper-V supports only 2TB logging
disks and, in total, supports up to 24TB of log storage. You cannot add a logging disk smaller
than 2TB or a logging disk of a size that is not evenly divisible by 2TB because the Panorama
virtual appliance partitions logging disks in to 2TB partitions. For example, if you attach a 4TB
logging disk, Panorama will create two 2TB partitions. However, you cannot add a 5TB logging
disk because the leftover 1TB is not supported as a partition.
STEP 1 | Power off the Panorama virtual appliance.
1. On the Hyper-V Manager, select the Panorama virtual appliance instance from the list of
Virtual Machines.
2. Select Action > Turn Off to power off the Panorama virtual appliance.
Panorama Getting Started 164 ©2026 Palo Alto Networks, Inc.
Set Up Panorama
STEP 2 | Add the virtual logging disk. Repeat this step as many times as needed.
In all modes, the first logging disk on the Panorama VM must be 2TB to add additional
disks. If the first logging disk is smaller than 2TB, you will be unable to add additional
disk space.
The IDE Controller supports only one additional disk besides the system disk. To add
more disks, choose a SCSI Controller.
For information on adding a disk larger than 2TB to Panorama on Hyper-V, see this
document.
1. Select the Panorama virtual appliance from the list of Virtual Machines, and select
Action > Settings.
2. In the Hardware list, select IDE Controller 0 or SCSI Controller.
3. From the IDE Controller or SCSI Controller drives list, select Hard Drive and Add the
new virtual logging disk.
4. Select the new Hard Drive created under IDE Controller 0 or SCSI Controller.
5. Under Media, add a New hard disk.
Panorama Getting Started 165 ©2026 Palo Alto Networks, Inc.
Set Up Panorama
Panorama Getting Started 166 ©2026 Palo Alto Networks, Inc.
Set Up Panorama
STEP 3 | Configure the new virtual logging disk.
1. If you see the Before You Begin prompt, click Next to begin adding the virtual logging
disk
2. For the Disk Format, select VHDX. Click Next to continue
3. For the Disk Type, select Dynamically Expanding based on your needs. Click Next to
continue.
4. Specify the Name and Location for the virtual logging disk file. Click Next to continue.
5. To configure the disk, select Create a new virtual hard disk and enter the disk size. Click
Next to continue.
6. Review the Summary and Finish adding the virtual hard logging disk.
7. Apply the new hard disk addition.
STEP 4 | Power on the Panorama virtual appliance.
1. Select the Panorama virtual appliance instance from the list of Virtual Machines.
2. Select Action > Start to power on the Panorama virtual appliance.
STEP 5 | Configure each disk.
The following example uses the sdc virtual disk.
1. Log in to the Panorama CLI.
2. Enter the following command to view the disks on the Panorama virtual appliance:
show system disk details
The user will see the following response:
Name
: sdb
```
State : Present
```
Panorama Getting Started 167 ©2026 Palo Alto Networks, Inc.
Set Up Panorama
```
Size : 2048000 MB
```
```
Status : Available
```
```
Reason : Admin enabled
```
```
Name : sdc
```
```
State : Present
```
```
Size : 2048 MB
```
```
Status : Available
```
```
Reason : Admin disabled
```
3. Enter the following command and confirm the request when prompted for all disks with
the Reason : Admindisabled response:
request system disk add sdc
The request system disk add command is not available on a Panorama
management server in Management Only mode because logging is not
supported in this mode. If you do not see the command, Set up a Panorama
Virtual Appliance in Panorama Mode to enable the logging disks. Once in
Panorama mode, Log in to the Panorama CLI and continue to Step 4 to verify
the disk addition.
4. Enter the show system disk details command to verify the status of the disk
addition. Continue to the next step when all newly added disk responses display
```
Reason : Admin enabled.
```
STEP 6 | Make disks available for logging.
1. Log in to the Panorama web interface.
2. Edit a Log Collector (Panorama > Managed Collectors).
3. Select Disks and Add each newly added disk.
4. Click OK.
5. Select Commit > Commit to Panorama.
```
For Panorama in an Active/Passive high availability (HA) configuration, wait for
```
HA sync to complete before continuing.
6. Select Commit > Push to Devices and push the changes to the Collector Group the Log
Collector belongs to.
```
STEP 7 | (New Panorama deployments in Panorama mode only) Configure Panorama to receive logs.
```
If you are adding logging disks to an existing Panorama virtual appliance, skip to Step 8.
1. Configure a Collector Group.
2. Configure Log Forwarding to Panorama.
STEP 8 | Verify that the Panorama Log Storage capacity is increased.
1. Log in to the Panorama web interface.
2. Select the Collector Group to which the Panorama virtual appliance belongs (Panorama
```
> Collector Groups).
```
3. Verify that the Log Storage capacity accurately displays the disk capacity.
Panorama Getting Started 168 ©2026 Palo Alto Networks, Inc.
Set Up Panorama
```
Add a Virtual Disk to Panorama on Oracle Cloud Infrastructure (OCI)
```
Where Can I Use This? What Do I Need?
```
• NGFW (Managed by Panorama) • Panorama virtual appliance operating in
```
Panorama mode or Log Collector mode on
OCI
• Initial logging disk of exactly 2TB
```
After you Install Panorama on Oracle Cloud Infrastructure (OCI), add additional virtual logging
```
disks to expand log storage capacity on the Panorama™ virtual appliance for logs generated
by managed firewalls. You can add virtual disks to a local Log Collector for a Panorama virtual
appliance in Panorama mode or for a Dedicated Log Collector. To add virtual disks, you must have
```
access to the OCI console, the Panorama command-line interface (CLI), and the Panorama web
```
interface.
The Panorama virtual appliance on OCI supports only 2TB logging disks and, in total, supports up
to 24TB of log storage. You cannot add a logging disk smaller than 2TB or a logging disk of a size
that is not evenly divisible by 2TB because the Panorama virtual appliance partitions logging disks
in to 2TB partitions. For example, if you attach a 4TB logging disk, Panorama will create two 2TB
partitions. However, you cannot add a 5TB logging disk because the leftover 1TB is not supported
as a partition.
STEP 1 | Log in to the Oracle Cloud Infrastructure console.
STEP 2 | Create a 2TB block volume.
1. Select Block Storage > Block Volumes and Create Block Volume.
2. Enter a descriptive Name for the volume.
3. Select the same Availability Domain as the Panorama virtual appliance instance.
4. Select the Custom volume size.
5. For the Volume Size, enter 2000.
6. Create Block Volume.
Panorama Getting Started 169 ©2026 Palo Alto Networks, Inc.
Set Up Panorama
STEP 3 | Attach a virtual logging disk to the Panorama virtual appliance instance.
In all modes, the first logging disk on the Panorama VM must be at least 2TB in order
to add additional disks. If the first logging disk is smaller than 2TB, you will be unable
to add additional disk space.
1. Select Compute > Instances and click the name of the Panorama virtual appliance
instance.
2. Under resources, select Attached Block Volumes and Attach Block Volume.
3. For the Volume, Select volume and select the virtual logging disk.
4. For the Attachment type, select Paravirtualized.
This is required for the Panorama virtual appliance to recognize the virtual logging disk.
5. For the Access, select Read/Write.
6. Attach the virtual logging disk.
STEP 4 | Configure each disk.
The following example uses the sdc virtual disk.
1. Log in to the Panorama CLI.
2. Enter the following command to view the disks on the Panorama virtual appliance:
show system disk details
The user will see the following response:
```
Name : sdb
```
```
State : Present
```
```
Size : 2048000 MB
```
```
Status : Unavailable
```
```
Reason : Admin disabled
```
3. Enter the following command and confirm the request when prompted for all disks with
the Reason : Admin disabled response:
request system disk add sdc
The request system disk add command is not available on a Panorama
management server in Management Only mode because logging is not
supported in this mode. If you do not see the command, Set up a Panorama
Virtual Appliance in Panorama Mode to enable the logging disks. Once in
Panorama mode, Log in to the Panorama CLI and continue to the next step to
verify the disk addition.
4. Enter the show system disk details command to verify the status of the disk
addition. Continue to the next step when all newly added disk responses display
```
Reason : Admin enabled.
```
Panorama Getting Started 170 ©2026 Palo Alto Networks, Inc.
Set Up Panorama
STEP 5 | Make disks available for logging.
1. Log in to the Panorama web interface.
2. Edit a Log Collector (Panorama > Managed Collectors).
3. Select Disks and Add each newly added disk.
4. Click OK.
5. Select Commit > Commit to Panorama.
```
For Panorama in an Active/Passive high availability (HA) configuration, wait for
```
HA sync to complete before continuing.
6. Select Commit > Push to Devices and push the changes to the Collector Group the Log
Collector belongs to.
```
STEP 6 | (New Panorama deployments in Panorama mode only) Configure Panorama to receive logs.
```
If you are adding logging disks to an existing Panorama virtual appliance, skip to step 6.
1. Configure a Collector Group.
2. Configure Log Forwarding to Panorama.
STEP 7 | Verify that the Panorama Log Storage capacity is increased.
1. Log in to the Panorama web interface.
2. Select the Collector Group to which the Panorama virtual appliance belongs (Panorama
```
> Collector Groups).
```
3. Verify that the Log Storage capacity accurately displays the disk capacity.
Increase CPUs and Memory on the Panorama Virtual Appliance
When you Perform Initial Configuration of the Panorama Virtual Appliance, you specify
the memory and number of CPUs based on whether the appliance is in Panorama mode or
Management Only mode and based on the log storage capacity or number of managed firewalls.
If you later add storage capacity or managed firewalls, you must also increase the memory and
CPUs. A Panorama virtual appliance in Log Collector mode must meet the system requirements,
and does not need to have the CPU and memory increased beyond the minimum requirement.
Review the Setup Prerequisites for the Panorama Virtual Appliance for the CPU and memory
requirements for each Panorama mode.
• Increase CPUs and Memory for Panorama on an ESXi Server
• Increase CPUs and Memory for Panorama on vCloud Air
• Increase CPUs and Memory for Panorama on Alibaba Cloud
• Increase CPUs and Memory for Panorama on AWS
• Increase CPUs and Memory for Panorama on Azure
• Increase CPUs and Memory for Panorama on Google Cloud Platform
• Increase CPUs and Memory for Panorama on KVM
• Increase CPUs and Memory for Panorama on Hyper-V
```
• Increase the CPUs and Memory for Panorama on Oracle Cloud Infrastructure (OCI)
```
Panorama Getting Started 171 ©2026 Palo Alto Networks, Inc.
Set Up Panorama
Increase CPUs and Memory for Panorama on an ESXi Server
For the minimum CPUs and memory that Panorama requires, see Increase CPUs and Memory on
the Panorama Virtual Appliance.
STEP 1 | Access the VMware vSphere Client and select Virtual Machines.
STEP 2 | Right-click the Panorama virtual appliance and select Power > Power Off.
STEP 3 | Right-click the Panorama virtual appliance and select Edit Settings.
STEP 4 | Select Memory and enter the new Memory Size.
```
STEP 5 | Select CPUs and specify the number of CPUs (the Number of virtual sockets multiplied by
```
```
the Number of cores per socket).
```
STEP 6 | Click OK to save your changes.
STEP 7 | Right-click the Panorama virtual appliance and select Power > Power On.
Increase CPUs and Memory for Panorama on vCloud Air
For the minimum CPUs and memory that Panorama requires, see Increase CPUs and Memory on
the Panorama Virtual Appliance.
STEP 1 | Access the vCloud Air web console and select your Virtual Private Cloud OnDemand region.
STEP 2 | In the Virtual Machines tab, select the Panorama virtual machine and Power Off.
STEP 3 | Select Actions > Edit Resources.
STEP 4 | Set the CPU and Memory.
STEP 5 | Save your changes.
STEP 6 | Select the Panorama virtual machine and Power On.
Increase CPUs and Memory for Panorama on Alibaba Cloud
You can change the instance type of the Panorama™ virtual appliance to increase the CPUs and
memory allocated to the Panorama virtual appliance instance. Be sure to review the supported
Alibaba Cloud instance types and the Setup Prerequisites for the Panorama Virtual Appliance
before changing the instance type.
STEP 1 | Log in to the Alibaba Cloud Console.
STEP 2 | Select Elastic Compute Service > Instances & Images > Instances and navigate to the
Panorama virtual appliance instance.
STEP 3 | In the Actions column, select More > Instance Status > Stop.
Panorama Getting Started 172 ©2026 Palo Alto Networks, Inc.
Set Up Panorama
STEP 4 | Change the Panorama virtual appliance instance type.
1. Select the Panorama virtual appliance if not already selected.
2. In the Actions column, select Change Instance Type.
3. Select the desired instance type and Change the instance type.
4. When prompted, select Console to view your Panorama virtual appliance instance.
STEP 5 | In the Actions column for the Panorama virtual appliance instance, select More > Instance
Status > Start.
STEP 6 | Verify the increased CPU and memory.
1. Log in to the Panorama CLI.
2. View the Panorma virtual appliance system information.
admin> show system info
3. Verify that the num-cpus and ram-in-gb display the correct number of CPUs and
amount of memory as per the instance type you selected.
Increase CPUs and Memory for Panorama on AWS
For the minimum CPUs and memory that Panorama™ requires, see Increase CPUs and Memory
on the Panorama Virtual Appliance.
STEP 1 | Log in to AWS Web Service console and select the EC2 Dashboard.
• Amazon Web Service Console
• AWS GovCloud Web Service Console
STEP 2 | On the EC2 Dashboard, select Instances and select the Panorama virtual appliance instance.
STEP 3 | Select Actions > Instance State > Stop to power off the Panorama virtual appliance instance.
STEP 4 | Select Actions > Instance Settings > Change Instance Type to change the Panorama virtual
appliance instance type.
STEP 5 | Select the Instance Type to which you want to upgrade and Apply it.
STEP 6 | Select Actions > Instance State > Start to power on the Panorama virtual appliance instance.
Increase CPUs and Memory for Panorama on Azure
For the minimum CPUs and memory that Panorama™ requires, see Increase CPUs and Memory
on the Panorama Virtual Appliance.
Panorama Getting Started 173 ©2026 Palo Alto Networks, Inc.
Set Up Panorama
STEP 1 | Log in to the Microsoft Azure portal.
STEP 2 | On the Azure Dashboard, under Virtual machines, select the Panorama virtual appliance.
STEP 3 | Select Overview and Stop the Panorama virtual appliance.
STEP 4 | Choose the new virtual machine Size and then Select it.
STEP 5 | Select Overview and Start the Panorama virtual appliance.
Increase CPUs and Memory for Panorama on Google Cloud Platform
For the minimum CPUs and memory that Panorama™ requires, see Increase CPUs and Memory
on the Panorama Virtual Appliance.
STEP 1 | Log in to the Google Cloud Console.
STEP 2 | Stop the Panorama virtual appliance instance.
1. Select the Panorama virtual appliance instance in the Products & Services menu
```
(Compute Engine > VM Instances).
```
2. Stop the Panorama virtual appliance instance. It can take 2 to 3 minutes for the
Panorama virtual appliance to completely shut down.
Panorama Getting Started 174 ©2026 Palo Alto Networks, Inc.
Set Up Panorama
STEP 3 | Reconfigure the Panorama virtual appliance resources.
1. Edit the Panorama virtual appliance instance details.
2. Under Machine Type, Customize the Panorama virtual appliance CPU cores and
memory.
STEP 4 | Save the changes to update the Panorama virtual appliance instance.
STEP 5 | Start the Panorama virtual appliance.
Increase CPUs and Memory for Panorama on KVM
For the minimum CPUs and memory that Panorama™ requires, see Increase CPUs and Memory
on the Panorama Virtual Appliance.
STEP 1 | Shutdown the Panorama virtual appliance instance on the Virtual Machine Manager.
STEP 2 | Double-click the Panorama virtual appliance instance in the Virtual Machine Manager and
Show virtual hardware details .
STEP 3 | Edit the allocated Panorama virtual appliance CPU cores.
1. Edit the currently allocated CPUs.
2. Apply the reconfigured CPU core allocation.
STEP 4 | Edit the allocated Panorama virtual appliance memory.
1. Edit the currently allocated Memory.
2. Apply the reconfigured memory allocation.
STEP 5 | Power on the Panorama virtual appliance instance.
Increase CPUs and Memory for Panorama on Hyper-V
For the minimum CPUs and memory that Panorama™ requires, see Increase CPUs and Memory
on the Panorama Virtual Appliance.
Panorama Getting Started 175 ©2026 Palo Alto Networks, Inc.
Set Up Panorama
STEP 1 | Power off the Panorama virtual appliance.
1. On the Hyper-V Manager, select the Panorama virtual appliance instance from the list of
Virtual Machines.
2. Select Action > Turn Off to power off the Panorama virtual appliance.
STEP 2 | On the Hyper-V Manager, select the Panorama virtual appliance instance form the list
of Virtual Machines, and select Action > Settings to edit the Panorama virtual appliance
resources.
STEP 3 | Edit the allocated Panorama virtual appliance memory.
1. In the Hardware list, select Memory.
2. Edit the currently allocated Startup RAM.
Panorama Getting Started 176 ©2026 Palo Alto Networks, Inc.
Set Up Panorama
STEP 4 | Edit the allocated Panorama virtual appliance CPU cores.
1. In the Hardware list, select Processor.
2. Edit the currently allocated Number of virtual processors.
STEP 5 | Apply the reallocated memory and CPU cores.
STEP 6 | Power on the Panorama virtual appliance.
1. Select the Panorama virtual appliance instance from the list of Virtual Machines.
2. Select Action > Start to power on the Panorama virtual appliance.
```
Increase the CPUs and Memory for Panorama on Oracle Cloud Infrastructure (OCI)
```
You can change the instance type of the Panorama™ virtual appliance to increase the CPUs
and memory allocated to the Panorama virtual appliance instance. Be sure to review the Setup
Prerequisites for the Panorama Virtual Appliance before modifying the Panorama virtual appliance
instance CPUs and memory.
STEP 1 | Log in to the Oracle Cloud Infrastructure console.
Panorama Getting Started 177 ©2026 Palo Alto Networks, Inc.
Set Up Panorama
STEP 2 | Power off the Panorama virtual appliance instance.
1. Select Compute > Instances and click the name of the Panorama virtual appliance
instance.
2. Stop the Panorama virtual appliance instance.
STEP 3 | Increase the CPUs and memory.
1. In the instance details, select Edit > Edit Shape.
2. Increase the number of CPUs and memory allocated to the instance.
3. Save Changes.
STEP 4 | In instance details, Start the Panorama virtual appliance.
STEP 5 | Verify the increased CPU and memory.
1. Log in to the Panorama CLI.
2. View the Panorma virtual appliance system information.
admin> show system info
3. Verify that the num-cpus and ram-in-gb display the correct number of CPUs and
amount of memory as per the instance type you selected.
Increase the System Disk on the Panorama Virtual Appliance
Expand the system disk capacity to 224GB for the Panorama virtual appliance to support large
datasets to allow for sufficient disk space for things such as dynamic updates when you Manage
Large-Scale Firewall Deployments with Panorama. Additionally, a 224GB system disk expands
storage for monitoring and reporting data for managed firewall health if you intended to use the
Panorama virtual appliance in Panorama mode to manage your SD-WAN deployment
• Increase the System Disk for Panorama on an ESXi Server
• Increase the System Disk for Panorama on a KVM Server
• Increase the System Disk for Panorama on Google Cloud Platform
• Increase the System Disk for Panorama on AWS
• Increase the System Disk for Panorama on Azure
•
Increase the System Disk for Panorama on an ESXi Server
Add a 224GB system disk to replace the default 81GB system disk. For the minimum resource
requirements for the Panorama virtual appliance, see Setup Prerequisites for the Panorama Virtual
Appliance.
Decreasing the Panorama virtual appliance system disk back to 81GB is not supported.
Panorama Getting Started 178 ©2026 Palo Alto Networks, Inc.
Set Up Panorama
```
STEP 1 | (Best Practice) Save and Export Panorama and Firewall Configurations. Save and Export
```
Panorama and Firewall Configurations
Save and export your Panorama and firewall configuration to ensure you can recover
Panorama if you encounter any issues.
STEP 2 | Access the VMware vSphere Client and navigate to your Panorama virtual appliance.
STEP 3 | Right-click the Panorama virtual appliance and select Power > Power Off.
STEP 4 | Add the new 224GB system disk.
1. Right-click the Panorama virtual appliance and Edit Settings.
2. Select New Hard Disk as the New Device and Add the new device.
3. Configure the new hard disk with 224GB and click OK.
STEP 5 | Right-click the Panorama virtual appliance and select Power > Power On.
Panorama may take up to 30 minutes to initialize the new system disk. During this
time the Panorama web interface and CLI are unavailable.
Panorama Getting Started 179 ©2026 Palo Alto Networks, Inc.
Set Up Panorama
STEP 6 | Migrate disk data from the old system disk to the new system disk.
In this example, we are migrating to the newly added system disk labeled sdb.
1. Log in to the Panorama CLI.
2. Enter the following command to view the available system disks for migration:
admin> request system clone-system-disk target ?
3. Migrate the disk data to the new system disk using the following command:
admin> request system clone-system-disk target sdb
Enter Y when prompted to begin the disk migration.
To begin the migration, Panorama reboots and takes at least 20 minutes to
complete the disk migration. During this time the Panorama web interface and
CLI are unavailable.
4. Monitor the disk migration from the web Console. Continue to the next step only after
Panorama displays the following message to indicate the disk migration is complete.
STEP 7 | Delete the old system disk.
1. Access the VMware vSphere Client and navigate to your Panorama virtual appliance.
2. Right-click the Panorama virtual appliance and select Power > Power Off.
3. Right-click the Panorama virtual appliance and Edit Settings.
4. Delete the old 81GB system disk and click OK.
Panorama Getting Started 180 ©2026 Palo Alto Networks, Inc.
Set Up Panorama
STEP 8 | Modify the Virtual Device Node for the new system disk.
1. Expand the settings options for the new system disk.
2. Select SCSI(0:0) as the Virtual Device Node.
3. Click OK to save your configuration changes.
STEP 9 | Right-click the Panorama virtual appliance and select Power > Power On.
STEP 10 | Verify that you successfully migrated to the new system disk.
1. Log in to the Panorama CLI.
2. Enter the following command to view the system disk partitions.
You must examine the /dev/root, /dev/sda5, /dev/sda6, and /dev/sda8
partitions to confirm the disk size is increased.
admin> show system disk-space
Panorama Getting Started 181 ©2026 Palo Alto Networks, Inc.
Set Up Panorama
Increase the System Disk for Panorama on a KVM Server
Add a 224GB system disk to replace the default 81GB system disk. For the minimum resource
requirements for the Panorama virtual appliance, see Setup Prerequisites for the Panorama Virtual
Appliance.
Decreasing the Panorama virtual appliance system disk back to 81GB is not supported.
```
STEP 1 | (Best Practice) Save and Export Panorama and Firewall Configurations.
```
Save and export your Panorama and firewall configuration to ensure you can recover
Panorama if you encounter any issues.
STEP 2 | Access the KVM Client and navigate to your Panorama virtual appliance.
STEP 3 | Right-click the Panorama virtual appliance and select Power > Power Off.
Panorama Getting Started 182 ©2026 Palo Alto Networks, Inc.
Set Up Panorama
STEP 4 | Add the new 224GB system disk.
1. Open Virt-manager and click Storage.
2. Select Create a disk image for the virtual machine and configure the new hard disk with
224GB.
3. Configure the new hard disk with 224GB and click OK.
STEP 5 | Power On the Panorama.
Panorama may take up to 30 minutes to initialize the new system disk. During this
time the Panorama web interface and CLI are unavailable.
STEP 6 | Execute the command show system disk details to verify that the new disk is added.
Panorama Getting Started 183 ©2026 Palo Alto Networks, Inc.
Set Up Panorama
STEP 7 | Log in to the Panorama CLI and migrate disk data from the existing system disk to the
new system disk by executing the command request system clone-system-disk
target.
In the example below, we are cloning the existing disk to the newly added system disk labeled
sdb.
Enter
Y
when prompted to begin the disk migration.
• To begin the migration, Panorama reboots and takes at least 20 minutes to
complete the disk migration. During this time the Panorama web interface and CLI
are unavailable.
• Monitor the disk migration from the web Console. Continue to the next step only
after Panorama displays a message to indicate the disk migration is complete.
Panorama Getting Started 184 ©2026 Palo Alto Networks, Inc.
Set Up Panorama
STEP 8 | Delete the old system disk.
1. Access the KVM Client and navigate to your Panorama virtual appliance.
2. Right-click the Panorama virtual appliance and select Power > Power Off.
3. Right-click the Panorama virtual appliance and Edit Settings.
4. Delete the old 81GB system disk and click OK.
STEP 9 | Shutdown the KVM instance.
STEP 10 | Power On the Panorama and verify that you successfully migrated to the new system disk.
1. Log in to the Panorama CLI.
2. Enter the following command to view the system disk partitions:
show system disk-partition
3. Verify the new disk is of 224 GB disk and displays a root volume of 16GB instead of
8GB.
Increase the System Disk on a KVM Server in Panorama-mode
To increase the system disk on a KVM Server in Panorama-mode:
Panorama Getting Started 185 ©2026 Palo Alto Networks, Inc.
Set Up Panorama
STEP 1 | Log in to the Panorama CLI.
STEP 2 | Execute the command show system info | match system-mode and verify the
system-mode of the Panorama is listed as panorama.
STEP 3 | Execute the command show system disk details and verify the following:
1. Status: Available
2. Reason: Admin enabled
STEP 4 | Shutdown the Panorama.
STEP 5 | Add a 224 GB disk using the virt-manager.
STEP 6 | Power ON the Panorama VM.
STEP 7 | Execute the command show system disk details and verify the new disk added is of
224 GB.
Panorama Getting Started 186 ©2026 Palo Alto Networks, Inc.
Set Up Panorama
STEP 8 | Execute the command request system clone-system-disk target and select the
required disk. This initiates a reboot on the Panorama following the disk cloning.
Panorama Getting Started 187 ©2026 Palo Alto Networks, Inc.
Set Up Panorama
STEP 9 | Verify the completion of disk cloning through virt-manager.
Panorama Getting Started 188 ©2026 Palo Alto Networks, Inc.
Set Up Panorama
Panorama Getting Started 189 ©2026 Palo Alto Networks, Inc.
Set Up Panorama
STEP 10 | Initiate a shutdown on the VM and delete the 81GB disk.
STEP 11 | Power on the Panorama VM.
Increase the System Disk for Panorama on Google Cloud Platform
Add a 224GB system disk to replace the default 81GB system disk. For the minimum resource
requirements for the Panorama virtual appliance, see Setup Prerequisites for the Panorama Virtual
Appliance.
```
STEP 1 | (Best Practice) Save and Export Panorama and Firewall Configurations.
```
Save and export your Panorama and firewall configuration to ensure you can recover
Panorama if you encounter any issues.
STEP 2 | Log in to the Google Cloud Console.
STEP 3 | In VM Instances, Stop the Panorama VM instance.
STEP 4 | Add the new 224GB system disk.
1. Select the Panorama VM instance and select Edit.
2. In the Additional disks section Add new disk.
3. Configure the new disk with 224GB and click OK.
STEP 5 | In VM Instances, Start the Panorama VM instance.
Panorama Getting Started 190 ©2026 Palo Alto Networks, Inc.
Set Up Panorama
STEP 6 | Migrate disk data from the old system disk to the new system disk.
In this example, we are migrating to the newly added system disk labeled sdb.
1. Log in to the Panorama CLI.
2. Enter the following command to view the available system disks for migration:
admin> request system clone-system-disk target ?
3. Migrate the disk data to the new system disk using the following command:
admin> request system clone-system-disk target sdb
Enter Y when prompted to begin the disk migration.
To begin the migration, Panorama reboots and takes at least 20 minutes to
complete the disk migration. During this time the Panorama web interface and
CLI are unavailable.
4. Monitor the disk migration by attempting to log in to the Panorama CLI. The Panorama
management server is in maintenance mode after the system disk migration is completed
and will allow you to log in to the Panorama CLI while in maintenance mode.
STEP 7 | Attach the new 224GB system disk.
1. In VM Instances, Stop the Panorama VM instance.
2. Select the Panorama VM instance and select Edit.
3. In the Additional disks section, detach the new 224GB system disk.
4. In the Boot Disk section, detach the old 81GB system disk.
5. In the Boot Disk section, Add item and select the new 224GB system disk.
6. Save your configuration changes.
STEP 8 | In VM Instances, Start the Panorama VM instance.
Panorama Getting Started 191 ©2026 Palo Alto Networks, Inc.
Set Up Panorama
STEP 9 | Verify that you successfully migrated to the new system disk.
1. Log in to the Panorama CLI.
2. Enter the following command to view the system disk partitions.
You must examine the /dev/root, /dev/sda5, /dev/sda6, and /dev/sda8
partitions to confirm the disk size is increased.
admin> show system disk-space
Increase the System Disk for Panorama on AWS
To increase the system disk on AWS, add a 224GB system disk to replace the default 81GB
system disk. For the minimum resource requirements for the Panorama virtual appliance, see
Setup Prerequisites for the Panorama Virtual Appliance.
Panorama Getting Started 192 ©2026 Palo Alto Networks, Inc.
Set Up Panorama
1. Save and Export Panorama and Firewall Configurations.
Save and export your Panorama and firewall configuration to ensure you can recover
Panorama if you encounter any issues.
2. Before you start with the migration, ensure that the serial console is enabled for the
instance type you are using.
Panorama Getting Started 193 ©2026 Palo Alto Networks, Inc.
Set Up Panorama
STEP 1 | Log in to the AWS Console.
STEP 2 | From EC2 > Instances, select the Panorama VM, click Instance state and stop the instance.
Panorama Getting Started 194 ©2026 Palo Alto Networks, Inc.
Set Up Panorama
STEP 3 | Create a new volume with type = <based on current panorama volume type> and Size =
224GB in the Panorama’s Availability Zone.
Ensure the new volume's type matches your existing EC2 instance. For example, a gp2
EC2 instance requires a gp2 volume type.
Panorama Getting Started 195 ©2026 Palo Alto Networks, Inc.
Set Up Panorama
Panorama Getting Started 196 ©2026 Palo Alto Networks, Inc.
Set Up Panorama
STEP 4 | Attach the created volume to the Panorama instance.
Panorama Getting Started 197 ©2026 Palo Alto Networks, Inc.
Set Up Panorama
Panorama Getting Started 198 ©2026 Palo Alto Networks, Inc.
Set Up Panorama
STEP 5 | Confirm the instance has the new 224GiB volume attached.
1. From your EC2 instance, select Instance and then the Panorama instance that has the
increased disk size.
2. Select the Storage tab and confirm that the disk with increased size is added.
STEP 6 | Start the Panorama Instance.
Panorama Getting Started 199 ©2026 Palo Alto Networks, Inc.
Set Up Panorama
STEP 7 | After the Panorama VM is up and running, confirm the disk is identified as a data disk using
the command:
show system disk details
Panorama Getting Started 200 ©2026 Palo Alto Networks, Inc.
Set Up Panorama
Panorama Getting Started 201 ©2026 Palo Alto Networks, Inc.
Set Up Panorama
Shows new 224 GB disk as below
```
Name : nvme1n1
```
```
State : Present
```
```
Size : 229376 MB
```
```
Status : Unavailable
```
```
Reason : Admin disabled
```
STEP 8 | Execute the command request system clone-system-disk target <new-disk>
admin@Panorama> request system clone-system-disk target
nvme1n1 Legacy logging disk
<value> Select target disk
admin@Panorama> request system clone-system-disk target nvme1n1
Executing this command will copy data from the system disk and
delete all data on the target disk. The system will reboot and
start the disk cloning procedure. The command will take at least
20 minutes to complete. Progress information will be available
```
only via the Console. Do you wish to continue? (y or n)
```
```
Broadcast message from root (Fri Sep 6 16:38:47 2024):
```
The system is going down for reboot NOW!
Panorama Getting Started 202 ©2026 Palo Alto Networks, Inc.
Set Up Panorama
STEP 9 | Select Instance state > Monitor and troubleshoot > EC2 serial console and Connect to
monitor the EC2 serial console and check the status of disk migration. Disk migration may
take approximately 30 minutes. Confirm successful completion of the process.
The following image shows an example of successful completion of the disk migration.
Panorama Getting Started 203 ©2026 Palo Alto Networks, Inc.
Set Up Panorama
Panorama Getting Started 204 ©2026 Palo Alto Networks, Inc.
Set Up Panorama
STEP 10 | Stop the Panorama instance after the disk migration is complete.
```
STEP 11 | Detach both disks (81GB and 224GB) individually. To detach the disks, select the Volume ID
```
of the disk you need to detach, then Actions > Detach volume.
Panorama Getting Started 205 ©2026 Palo Alto Networks, Inc.
Set Up Panorama
```
STEP 12 | Attach the new 224GB disk as the root volume (/dev/xvdp) to the Panorama instance. To
```
attach the disk, select the Volume ID of the disk you need to attach, then Actions > Attach
volume.
Panorama Getting Started 206 ©2026 Palo Alto Networks, Inc.
Set Up Panorama
STEP 13 | Start the instance.
STEP 14 | After the Panorama VM is running, execute the command show system disk-
partition to confirm it displays root volumes of 224GB.
panadmin@Panorama> show system disk-partition
Disk /dev/nvme0n1: 224 GiB, 240518168576 bytes, 469762048 sectors
```
Units: sectors of 1 * 512 = 512 bytes
```
```
Sector size (logical/physical): 512 bytes / 512 bytes
```
```
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
```
Disklabel type: dos
Disk identifier: 0x05ef63be
Device Boot Start End Sectors Size Id Type
/dev/nvme0n1p1 63 4016249 4016187 1.9G 83 Linux
/dev/nvme0n1p2 4016250 36033794 32017545 15.3G 83 Linux
/dev/nvme0n1p3 36033795 68051339 32017545 15.3G 83 Linux
/dev/nvme0n1p4 68051340 468857024 400805685 191.1G f W95
```
Ext'd (LBA)
```
/dev/nvme0n1p5 68051403 228074804 160023402 76.3G 83 Linux
/dev/nvme0n1p6 228074868 276093089 48018222 22.9G 83 Linux
/dev/nvme0n1p7 276093153 276109154 16002 7.8M 83 Linux
/dev/nvme0n1p8 276109218 468857024 192747807 91.9G 83 Linux
Disk /dev/loop0: 36.3 GiB, 38948306944 bytes, 76070912 sectors
```
Units: sectors of 1 * 512 = 512 bytes
```
```
Sector size (logical/physical): 512 bytes / 512 bytes
```
```
I/O size (minimum/optimal): 512 bytes / 512 bytes
```
Increase the System Disk for Panorama on Azure
For the minimum resource requirements for the Panorama virtual appliance, see Setup
Prerequisites for the Panorama Virtual Appliance.
1. Save and Export Panorama and Firewall Configurations.
Save and export your Panorama and firewall configuration to ensure you can recover
Panorama if you encounter any issues.
2. Power off the Panorama virtual appliance.
Panorama Getting Started 207 ©2026 Palo Alto Networks, Inc.
Set Up Panorama
STEP 1 | Add a 224GB system disk to replace the default 81GB system disk.
1. Log in to the Azure Console.
2. Expand Settings and click Disks > Create and attach a new disk.
3. Enter a Disk name to the new disk you are creating.
4. Select the Storage type and Encryption similar to the ones you had selected for the 81
GB disk.
5. Enter 224 as the Size (GB).
6. Select Read/write option for Host caching.
7. Click Apply.
STEP 2 | Check the disk size in the Panorama.
Panorama Getting Started 208 ©2026 Palo Alto Networks, Inc.
Set Up Panorama
STEP 3 | Initiate disk cloning.
1. Initiate disk cloning by executing the following command:
request system clone-system-disk target <disk name>
2. Verify the ongoing cloning status from the console.
3. Shutdown the Panorama VM from the Azure console.
STEP 4 | Detach the data disk from the Panorama VM to which it was added initially, and convert the
data disk to OS disk using powershell commands.
$managedDisk = Get-AzDisk -DiskName pnrma_new_data_disk -
ResourceGroupName arus-cpt-pnrma-rg
# Create disk configuration for the copy
$diskConfig = New-AzDiskConfig -SourceResourceId $managedDisk.Id -
Location $managedDisk.Location -CreateOption Copy -OsType Linux
New-AzDisk -Disk $diskConfig -DiskName pnrma_new_data_os_disk -
ResourceGroupName arus-cpt-pnrma-rg
pnrma_new_data_disk - name of the Data Disk that was initially
created in the previous step
arus-cpt-pnrma-rg - name of the resource group where
disk is present
Panorama Getting Started 209 ©2026 Palo Alto Networks, Inc.
Set Up Panorama
pnrma_new_data_os_disk - name of the new os disk that will be
created
$managedDisk = Get-AzDisk -DiskName pnrma_new_data_disk -
ResourceGroupName arus-cpt-pnrma-rg
$diskConfig = New-AzDiskConfig -SourceResourceId $managedDisk.Id -
Location $managedDisk.Location -CreateOption
New-AzDisk -Disk $diskConfig -DiskName pnrma_new_data_os_disk -
ResourceGroupName arus-cpt-pnrma-rg
Panorama Getting Started 210 ©2026 Palo Alto Networks, Inc.
Set Up Panorama
STEP 5 | Verify the OS disk you created.
STEP 6 | Create an Azure compute gallery.
1. From the Azure Console home page, click Azure compute galleries.
2. In the Azure compute gallery page, Click Create.
3. Select a Resource group.
4. You may retain the default settings for Sharing and Tags tabs.
5. Click Review+create.
Panorama Getting Started 211 ©2026 Palo Alto Networks, Inc.
Set Up Panorama
STEP 7 | Add a VM image definition from the Azure compute gallery.
1. Add the following details:
• Subscription
• Resource Group
• Region
• Target Azure Compute Gallery
• VM image definition name
• OS type
• Security type
• VM generation
• Higher storage performance with NVMe
• Accelerated networking
• VM architecture
• Hibernation supported
• OS state
• Publisher - Enter publisher as paloaltonetworks
• Offer - Enter offer as panorama
• SKU - Enter SKU as byol
• Ensure that the region, publisher, SKU, offer, and VM-Deployment sections
are similar to that of the existing Panorama. You can view this information
in the Source image details section of the VM Overview page in Azure Portal
page.
• The OS disk must be the one you created in step 5. Ensure that you select
this OS disk under the version tab while creating a VM definition.
• The CPU and memory values must be the same as that of the Panorama.
Panorama Getting Started 212 ©2026 Palo Alto Networks, Inc.
Set Up Panorama
Panorama Getting Started 213 ©2026 Palo Alto Networks, Inc.
Set Up Panorama
2. Click Review+Create to create the Azure compute gallery.
Panorama Getting Started 214 ©2026 Palo Alto Networks, Inc.
Set Up Panorama
STEP 8 | Create a VM from the Azure compute gallery.
1. Click the VM definition and click Create VM to create a VM from the Azure compute
gallery. This will create a new Panorama instance which will boot from the VM definition.
1. Configure the Basics settings.
1. When choosing the image, select the relevant Gallery Image definition that
was created in previous steps.
2. Ensure that the Azure infrastructure-related options align with the existing
Panorama configuration.
2. Add the Disks settings and ensure that the OS Disk selected is 224GB or more.
3. Add the Networking settings similar to that of the existing Panorama. This will bring up a
new panorama with the resized OS disk details.
Panorama Getting Started 215 ©2026 Palo Alto Networks, Inc.
Set Up Panorama
STEP 9 | Execute the following command to verify if the panrepo folder size has increased:
Show system disk space
STEP 10 | The new Panorama will have a different private IP address. You need to configure it with
the same IP address as the existing Panorama. To make the existing Panorama's IP address
available, assign a temporary, unused IP address to the existing Panorama. The existing
Panorama's IP address can only be changed when the VM is shut down. From the Azure
portal, assign the existing Panorama's IP address to the new Panorama's interface. Once
Panorama Getting Started 216 ©2026 Palo Alto Networks, Inc.
Set Up Panorama
```
the IP addresses are swapped, the Network Interface Card (NIC) will reset, and the new
```
Panorama will then have the IP address of the existing Panorama.
To change private/public IP of the Panorama, click PanoramaVM > Network Settings > IP
configurations. Select the network for which you need to change the IP address and click Edit.
Panorama Getting Started 217 ©2026 Palo Alto Networks, Inc.
Set Up Panorama
STEP 11 | If your existing Panorama had any data disks, detach them and then reattach them to the
new Panorama. Finally, boot the Panorama. The new Panorama should now have all devices
connected and function identically to the existing Panorama.
For an Active-Passive Panorama setup, apply these steps first to the Passive
Panorama, then repeat them for the Active Panorama.
In case of a Cloud NGFW set-up, the newly deployed Panorama instance will be
assigned a different Private IP address. It is necessary to configure this new instance to
use the same IP address as the existing Panorama.
To make the existing Panorama IP available to the new Panorama instance, you must
first assign a temporary, unused IP address to the current Panorama. The existing
Panorama IP address can only be changed while the VM is shut down.
Assign the existing Panorama IP to the new Panorama interface from the Azure
portal. Interchanging the IP addresses will cause the NIC to reset, resulting in the new
Panorama instance adopting the IP address of the existing Panorama instance. After
replacing the existing Panorama, complete the following steps:
1. If the original Panorama had any data disks, detach them and reattach them to the
new Panorama instance.
2. Start the new Panorama instance. The new Panorama should now be fully
functional, with all devices connected, and operating the same way as the original
Panorama.
3. After the Panorama is back online, you must re-fetch the device certificate and
licenses.
Complete the Panorama Virtual Appliance Setup
After you Perform Initial Configuration of the Panorama Virtual Appliance, continue with the
following tasks for additional configuration:
• Activate a Panorama Support License
• Activate/Retrieve a Firewall Management License when the Panorama Virtual Appliance is
Internet-connected
• Install Content and Software Updates for Panorama
• Access and Navigate Panorama Management Interfaces
• Configure Administrative Access to Panorama
• Manage Firewalls
Panorama Getting Started 218 ©2026 Palo Alto Networks, Inc.
Set Up Panorama
Convert Your Panorama Virtual Appliance
You can convert your evaluation Panorama™ virtual appliance to a production Panorama virtual
appliance to preserve its existing configuration and begin leveraging the management platform.
```
If you are utilizing Enterprise License Agreement (ELA) licensing, you can convert an existing
```
production Panorama virtual appliance to leverage the benefits of ELA licensing.
• Convert Your Evaluation Panorama to a Production Panorama with Local Log Collector
• Convert Your Evaluation Panorama to a Production Panorama without Local Log Collector
• Convert Your Evaluation Panorama to VM-Flex Licensing with Local Log Collector
• Convert Your Evaluation Panorama to VM-Flex Licensing without Local Log Collector
• Convert Your Production Panorama to an ELA Panorama
Convert Your Evaluation Panorama to a Production Panorama with Local Log
Collector
If you have an evaluation Panorama™ virtual appliance in Panorama mode configured with a local
Log Collector, you can convert it to a production Panorama by migrating the configuration from
the evaluation Panorama to the production Panorama and modifying as needed.
Logs ingested by the Log Collector on a Panorama virtual appliance cannot be migrated.
If you need to maintain access to the logs stored on your evaluation Panorama virtual
appliance, after you migrate the evaluation Panorama configuration to the production
Panorama, keep your evaluation Panorama powered on to access the logs locally for
the remainder of the evaluation license lifetime. Adding the evaluation Panorama to the
production Panorama as a managed collector is not supported.
STEP 1 | Plan the migration.
Upgrade the software on the Panorama virtual appliance before you convert your
evaluation Panorama virtual appliance to a production Panorama virtual appliance. Review
the Compatibility Matrix for the minimum PAN-OS version required for your hypervisor.
For important details about software versions, see Panorama, Log Collector, Firewall, and
WildFire Version Compatibility.
Schedule a maintenance window for the migration.
STEP 2 | Set up your production Panorama virtual appliance.
1. Set Up the Panorama Virtual Appliance.
2. Register the Panorama virtual appliance with the Palo Alto Networks Customer Support
```
Portal (CSP).
```
The Panorama serial number and authorization code are found in the Order Summary
email from Palo Alto Networks.
3. Install Content and Software Updates for Panorama.
Panorama Getting Started 219 ©2026 Palo Alto Networks, Inc.
Set Up Panorama
STEP 3 | Activate the device management license on the Palo Alto Networks Custer Support Portal
```
(CSP) for the production Panorama virtual appliance.
```
1. Log in to the Palo Alto Networks CSP.
2. Select Assets > Devices and locate your Panorama virtual appliance.
3. In the Action column, click the pencil icon to edit the device licenses.
4. Select Activate Auth-Code and enter the Authorization Code.
5. Select Agree and Submit to activate the device management license.
STEP 4 | Export the Panorama configuration from the evaluation Panorama virtual appliance.
1. Log in to the Panorama Web Interface.
2. Select Panorama > Setup > Operations.
3. Click Export named Panorama configuration snapshot, select running-config.xml
and click OK. Panorama exports the configuration to your client system as an XML file.
4. Locate the running-config.xml file you exported and rename the XML file. This is
required to import the configuration as Panorama does not support importing an XML
file with the name running-config.xml.
STEP 5 | Load the Panorama configuration snapshot that you exported from the evaluation Panorama
virtual appliance into the production Panorama virtual appliance.
1. Log in to the Panorama Web Interface of the production Panorama virtual appliance.
2. Select Panorama > Setup > Operations.
3. Click Import named Panorama configuration snapshot, Browse to the Panorama
configuration file you exported from the Panorama virtual appliance, and click OK.
4. Click Load named Panorama configuration snapshot, select the Name of the
```
configuration you just imported, leave the Decryption Key blank (empty), and click OK.
```
Panorama overwrites its current candidate configuration with the loaded configuration.
Panorama displays any errors that occur when loading the configuration file.
5. If errors occurred, save them to a local file. Resolve each error to ensure the migrated
configuration is valid.
Panorama Getting Started 220 ©2026 Palo Alto Networks, Inc.
Set Up Panorama
STEP 6 | Modify the configuration on the production Panorama virtual appliance.
1. Select Panorama > Setup > Management.
2. Edit the General Settings, modify the Hostname, and click OK.
3. Edit the Management Interface Settings to configure the management IP address and
click OK.
The most efficient approach is to assign a new IP address to the evaluation
Panorama virtual appliance and reuse its old IP address for the production
Panorama virtual appliance. This ensures that the evaluation Panorama virtual
appliance remains accessible and that firewalls can point to the production
Panorama virtual appliance without you reconfiguring the Panorama IP address
on each firewall.
4. Remove the Log Collector configuration imported from the evaluation Panorama.
1. Select Panorama > Collector Group and Delete all configured collector groups.
2. Select Panorama > Managed Collectors and Delete all configured Log Collectors.
5. Select Commit > Commit to Panorama and Commit your changes to the Panorama
configuration.
STEP 7 | Configure your Log Collectors and collector groups.
You must add the managed collectors, collector group configuration, and log forwarding
configurations you deleted in the previous step, as well as add the local Log Collector.
1. Configure a Managed Collector.
2. Configure a Collector Group.
3. Configure Log Forwarding to Panorama.
STEP 8 | Verify that the support and device management licenses are successfully activated.
1. Select Panorama > Licenses and Retrieve license keys from license server.
2. Verify the Device Management License displays the correct number of devices.
3. Select Panorama > Support and verify that the correct support Level and Expiry Date
are displayed.
Panorama Getting Started 221 ©2026 Palo Alto Networks, Inc.
Set Up Panorama
STEP 9 | Synchronize the production Panorama virtual appliance with the firewalls to resume firewall
management.
Complete this step during a maintenance window to minimize network disruption.
1. On the production Panorama virtual appliance, select Panorama > Managed Devices and
verify that the Device State column displays Connected for the firewalls.
```
At this point, the Shared Policy (device groups) and Template columns display Out of
```
sync for the firewalls.
2. Push your changes to device groups and templates:
1. Select Commit > Push to Devices and Edit Selections.
2. Select Device Groups, select every device group, Include Device and Network
Templates, and click OK.
3. Push your changes.
3. In the Panorama > Managed Devices page, verify that the Shared Policy and Template
columns display In sync for the firewalls.
Convert Your Evaluation Panorama to a Production Panorama without Local Log
Collector
Change the serial number of your evaluation Panorama virtual appliance in Management Only
mode or in Panorama mode with no local Log Collector configured to convert it to a production
Panorama virtual appliance.
If a local Log Collector is configured, see Convert Your Evaluation Panorama to a Production
Panorama with Local Log Collector.
STEP 1 | Log in to the Panorama web interface.
STEP 2 | Select Panorama > Setup > Management and edit the General Settings.
STEP 3 | Enter the Serial Number provided by Palo Alto Networks.
The Panorama serial number and authorization code are obtained from the deployment profile
you created in the previous step.
STEP 4 | Click OK.
STEP 5 | Select Commit and Commit to Panorama.
STEP 6 | Restart management server on the Panorama virtual appliance.
1. Log in to the Panorama CLI.
2. Restart the management server.
admin> debug software restart process management-server
All administrators are logged out of the Panorama web interface and CLI when
you restart the management server.
Panorama Getting Started 222 ©2026 Palo Alto Networks, Inc.
Set Up Panorama
STEP 7 | Verify that the support and device management licenses are successfully activated.
1. Log in to the Panorama web interface.
2. Select Panorama > Licenses and Retrieve license keys from license server.
3. Verify the Device Management License displays the correct number of devices.
4. Select Panorama > Support and verify that the correct support Level and Expiry Date
are displayed.
STEP 8 | Synchronize the production Panorama virtual appliance with the firewalls to resume firewall
management.
Complete this step during a maintenance window to minimize network disruption.
1. On the production Panorama virtual appliance, select Panorama > Managed Devices and
verify that the Device State column displays Connected for the firewalls.
```
At this point, the Shared Policy (device groups) and Template columns display Out of
```
sync for the firewalls.
2. Push your changes to device groups and templates:
1. Select Commit > Push to Devices and Edit Selections.
2. Select Device Groups, select every device group, Include Device and Network
Templates, and click OK.
3. Push your changes.
3. In the Panorama > Managed Devices page, verify that the Shared Policy and Template
columns display In sync for the firewalls.
Convert Your Evaluation Panorama to VM-Flex Licensing with Local Log Collector
If you have an evaluation Panorama™ virtual appliance in Panorama mode configured with a local
Log Collector, you can convert it to a production Panorama with VM Flex licensing by migrating
the configuration from the evaluation Panorama to the production Panorama and modifying as
needed.
If a local Log Collector is not configured, see Convert Your Evaluation Panorama to VM-Flex
Licensing without Local Log Collector.
Logs ingested by the Log Collector on a Panorama virtual appliance cannot be migrated.
If you need to maintain access to the logs stored on your evaluation Panorama virtual
appliance, after you migrate the evaluation Panorama configuration to the production
Panorama, keep your evaluation Panorama powered on to access the logs locally for
the remainder of the evaluation license lifetime. Adding the evaluation Panorama to the
production Panorama as a managed collector is not supported.
STEP 1 | Plan the migration.
Upgrade the software on the Panorama virtual appliance before you convert your
evaluation Panorama virtual appliance to a production Panorama virtual appliance. Review
the Compatibility Matrix for the minimum PAN-OS version required for your hypervisor.
Panorama Getting Started 223 ©2026 Palo Alto Networks, Inc.
Set Up Panorama
For important details about software versions, see Panorama, Log Collector, Firewall, and
WildFire Version Compatibility.
Schedule a maintenance window for the migration.
STEP 2 | Obtain the Panorama serial number and auth code from your flexible VM-Series licensing
deployment profile.
1. Log in to the Palo Alto Networks Customer Support Portal (CSP).
2. Create a deployment profile that enables a Panorama virtual appliance.
3. Provision Panorama to generate the a serial number for Panorama.
4. Copy the Serial Number and Auth Code.
STEP 3 | Set up your production Panorama virtual appliance.
1. Log in to the Palo Alto Networks CSP.
2. Set Up the Panorama Virtual Appliance.
3. Register the Panorama virtual appliance with the Palo Alto Networks Customer Support
```
Portal (CSP).
```
The Panorama serial number and authorization code you generated in the previous step.
4. Install Content and Software Updates for Panorama.
STEP 4 | Activate the device management license on the Palo Alto Networks CSP for the production
Panorama virtual appliance.
1. Select Assets > Devices and locate your Panorama virtual appliance.
2. In the Action column, click the pencil icon to edit the device licenses.
3. Select Activate Auth-Code and enter the Authorization Code.
4. Select Agree and Submit to activate the device management license.
STEP 5 | Export the Panorama configuration from the evaluation Panorama virtual appliance.
1. Log in to the Panorama Web Interface.
2. Select Panorama > Setup > Operations.
3. Click Export named Panorama configuration snapshot, select running-config.xml
and click OK. Panorama exports the configuration to your client system as an XML file.
4. Locate the running-config.xml file you exported and rename the XML file. This is
required to import the configuration as Panorama does not support importing an XML
file with the name running-config.xml.
STEP 6 | Load the Panorama configuration snapshot that you exported from the evaluation Panorama
virtual appliance into the production Panorama virtual appliance.
1. Log in to the Panorama Web Interface of the production Panorama virtual appliance.
2. Select Panorama > Setup > Operations.
3. Click Import named Panorama configuration snapshot, Browse to the Panorama
configuration file you exported from the Panorama virtual appliance, and click OK.
4. Click Load named Panorama configuration snapshot, select the Name of the
```
configuration you just imported, leave the Decryption Key blank (empty), and click OK.
```
Panorama Getting Started 224 ©2026 Palo Alto Networks, Inc.
Set Up Panorama
Panorama overwrites its current candidate configuration with the loaded configuration.
Panorama displays any errors that occur when loading the configuration file.
5. If errors occurred, save them to a local file. Resolve each error to ensure the migrated
configuration is valid.
STEP 7 | Modify the configuration on the production Panorama virtual appliance.
1. Select Panorama > Setup > Management.
2. Edit the General Settings, modify the Hostname, and click OK.
3. Edit the Management Interface Settings to configure the management IP address and
click OK.
The most efficient approach is to assign a new IP address to the evaluation
Panorama virtual appliance and reuse its old IP address for the production
Panorama virtual appliance. This ensures that the evaluation Panorama virtual
appliance remains accessible and that firewalls can point to the production
Panorama virtual appliance without you reconfiguring the Panorama IP address
on each firewall.
4. Remove the Log Collector configuration imported from the evaluation Panorama.
1. Select Panorama > Collector Group and Delete all configured collector groups.
2. Select Panorama > Managed Collectors and Delete all configured Log Collectors.
5. Select Commit > Commit to Panorama and Commit your changes to the Panorama
configuration.
STEP 8 | Reconfigure your Log Collectors and collector groups.
You must add the managed collectors, collector group configuration, and log forwarding
configurations you deleted in the previous step, as well as add the local Log Collector.
1. Configure a Managed Collector.
2. Configure a Collector Group.
3. Configure Log Forwarding to Panorama.
STEP 9 | Verify that the support and device management licenses are successfully activated.
1. Select Panorama > Licenses and Retrieve license keys from license server.
2. Verify the Device Management License displays the correct number of devices.
3. Select Panorama > Support and verify that the correct support Level and Expiry Date
are displayed.
Panorama Getting Started 225 ©2026 Palo Alto Networks, Inc.
Set Up Panorama
STEP 10 | Synchronize the production Panorama virtual appliance with the firewalls to resume firewall
management.
Complete this step during a maintenance window to minimize network disruption.
1. On the production Panorama virtual appliance, select Panorama > Managed Devices and
verify that the Device State column displays Connected for the firewalls.
```
At this point, the Shared Policy (device groups) and Template columns display Out of
```
sync for the firewalls.
2. Push your changes to device groups and templates:
1. Select Commit > Push to Devices and Edit Selections.
2. Select Device Groups, select every device group, Include Device and Network
Templates, and click OK.
3. Push your changes.
3. In the Panorama > Managed Devices page, verify that the Shared Policy and Template
columns display In sync for the firewalls.
Convert Your Evaluation Panorama to VM-Flex Licensing without Local Log Collector
Change the serial number of your evaluation Panorama virtual appliance in Management Only
mode or in Panorama mode with no local Log Collector configured to convert it to a production
Panorama virtual appliance.
If a local Log Collector is configured, see Convert Your Evaluation Panorama to VM-Flex Licensing
with Local Log Collector.
STEP 1 | Obtain the Panorama serial number and auth code from your flexible VM-Series licensing
deployment profile.
1. Log in to the Palo Alto Networks Customer Support Portal (CSP).
2. Create a deployment profile that enables a Panorama virtual appliance.
3. Provision Panorama to generate the a serial number for Panorama.
4. Copy the Serial Number and Auth Code.
STEP 2 | Log in to the Panorama web interface.
STEP 3 | Select Panorama > Setup > Management and edit the General Settings.
STEP 4 | Enter the Serial Number provided by Palo Alto Networks.
The Panorama serial number and authorization code you generated in the previous step.
STEP 5 | Click OK.
STEP 6 | Select Commit and Commit to Panorama.
Panorama Getting Started 226 ©2026 Palo Alto Networks, Inc.
Set Up Panorama
STEP 7 | Restart management server on the Panorama virtual appliance.
1. Log in to the Panorama CLI.
2. Restart the management server.
admin> debug software restart process management-server
All administrators are logged out of the Panorama web interface and CLI when
you restart the management server.
STEP 8 | Verify that the support and device management licenses are successfully activated.
1. Log in to the Panorama web interface.
2. Select Panorama > Licenses and Retrieve license keys from license server.
3. Verify the Device Management License displays the correct number of devices.
4. Select Panorama > Support and verify that the correct support Level and Expiry Date
are displayed.
STEP 9 | Synchronize the production Panorama virtual appliance with the firewalls to resume firewall
management.
Complete this step during a maintenance window to minimize network disruption.
1. On the production Panorama virtual appliance, select Panorama > Managed Devices and
verify that the Device State column displays Connected for the firewalls.
```
At this point, the Shared Policy (device groups) and Template columns display Out of
```
sync for the firewalls.
2. Push your changes to device groups and templates:
1. Select Commit > Push to Devices and Edit Selections.
2. Select Device Groups, select every device group, Include Device and Network
Templates, and click OK.
3. Push your changes.
3. In the Panorama > Managed Devices page, verify that the Shared Policy and Template
columns display In sync for the firewalls.
Convert Your Production Panorama to an ELA Panorama
You can convert your production Panorama™ virtual appliance to continue leveraging your
Panorama with the benefits of ELA licensing. To convert your production deployment, Panorama
must have out-bound Internet access.
Converting your production Panorama to ELA licensing is supported in Management Only and
Panorama mode with or without a local Log Collector configured. If your Panorama has a local Log
Collector configured, you must submit a support ticket with Palo Alto Networks to convert your
Panorama to ELA licensing.
Panorama Getting Started 227 ©2026 Palo Alto Networks, Inc.
Set Up Panorama
During conversion from a production Panorama to ELA licensing, do not change the
Panorama serial number if a local Log Collector is configured.
The log on the local Log collector become inaccessible and other Log Collectors in the
Collector Group may become inaccessible and no longer ingest logs if the serial number of
a Log Collector is changed.
STEP 1 | Covert your Panorama to ELA licensing.
• Panorama virtual appliance in Panorama mode with a local Log Collector.
Submit support ticket with Palo Alto Networks to convert your Panorama to ELA licensing.
This is required in order to preserve all existing logs on the local Log Collector when
converting a Panorama with a local Log Collector to ELA licensing. An example is provided
Panorama Getting Started 228 ©2026 Palo Alto Networks, Inc.
Set Up Panorama
below to assist in filing the support ticket. Create the ticket exactly as displayed below, and
select the OS Release your Panorama is running.
Continue to the next step only after Palo Alto Networks support successfully resolves your
support ticket.
• Panorama virtual appliance in Management Only mode or Panorama mode with no local
Log Collector.
1. Generate a serial number from your ELA licensing pool.
1. Log in to the Palo Alto Networks CSP.
2. Select Assets > VM-Series Auth-Codes and locate your ELA licensing pool.
3. In the Actions column, select Panorama and Provision a new serial number.
Confirm the new serial number provision when prompted.
4. Copy the newly provisioned serial number.
2. Log in to the Panorama web interface.
3. Select Panorama > Setup > Management and edit the General Settings.
4. Enter the Serial Number you provisioned.
5. Click OK.
6. Select Commit and Commit to Panorama.
STEP 2 | Log in to the Panorama web interface if not already logged in.
STEP 3 | Select Panorama > Licenses and Retrieve new licenses from the license server.
STEP 4 | Verify that Panorama retrieved the new licenses as per your ELA agreement.
Panorama Getting Started 229 ©2026 Palo Alto Networks, Inc.
Set Up Panorama
STEP 5 | Verify that the support and device management licenses are successfully activated.
1. Select Panorama > Licenses and verify that the correct licenses are activated.
2. Select Panorama > Support and verify that the correct support Level and Expiry Date
are displayed.
Panorama Getting Started 230 ©2026 Palo Alto Networks, Inc.
Set Up Panorama
Set Up the M-Series Appliance
Where Can I Use This? What Do I Need?
```
• NGFW (Managed by Panorama) • M-series hardware appliance
```
The M-700, M-600, M-300, and M-200 appliances are high performance hardware appliances
```
that you can deploy in Management Only mode (as Panorama management servers with no local
```
```
log collection), Panorama mode (as Panorama management servers with local log collection) or
```
```
in Log Collector mode (as Dedicated Log Collectors). The appliances provide multiple interfaces
```
that you can assign to various Panorama services such as firewall management and log collection.
Before setting up the appliance, consider how you can configure the interfaces to optimize
```
security, enable network segmentation (in large-scale deployments), and load balance the traffic
```
for Panorama services.
• M-Series Appliance Interfaces
• Perform Initial Configuration of the M-Series Appliance
• Perform Initial Configuration of an Air Gapped M-Series Appliance
• M-Series Setup Overview
• Set Up the M-Series Appliance as a Log Collector
• Increase Storage on the M-Series Appliance
• Configure Panorama to Use Multiple Interfaces
M-Series Appliance Interfaces
Where Can I Use This? What Do I Need?
```
• NGFW (Managed by Panorama) • M-series hardware appliance
```
The Panorama M-700, M-600, M-300, and M-200 appliances have several interfaces for
communicating with other systems such as managed firewalls and the client systems of Panorama
administrators. Panorama communicates with these systems to perform various services, including
```
managing devices (firewalls, Log Collectors, and WildFire appliances and appliance clusters),
```
collecting logs, communicating with Collector Groups, deploying software and content updates
to devices, and providing administrative access to Panorama. By default, Panorama uses its
```
management (MGT) interface for all these services. However, you can improve security by
```
reserving the MGT interface for administrative access and dedicating separate interfaces for the
other services. In a large-scale network with multiple subnetworks and heavy log traffic, using
multiple interfaces for device management and log collection also enables network segmentation
```
and load balancing (see Configure Panorama to Use Multiple Interfaces).
```
When assigning Panorama services to various interfaces, keep in mind that only the MGT
interface allows administrative access to Panorama for configuration and monitoring tasks. You
can assign any interface to the other services when you Perform Initial Configuration of the M-
Panorama Getting Started 231 ©2026 Palo Alto Networks, Inc.
Set Up Panorama
Series Appliance. The M-Series Appliance Hardware Reference Guides explain where to attach
cables for the interfaces.
The M-Series appliances, with the exception of the M-700, do not support Link
```
Aggregation Control Protocol (LACP) for aggregating interfaces. The M-700 supports
```
LACP for aggregate interface bond1.
Supported Interfaces
Interfaces can be used for device management, log collection, Collector Group communication,
licensing and software updates. See Configure Panorama to Use Multiple Interfaces for more
information on network segmentation.
Interface Maximum
Speed
M-700
Appliance
M-600
Appliance
M-300
Appliance
M-200
Appliance
1Gbps — —Management
```
(MGT)
```
10Gbps — —
1Gbps — —Ethernet 1
```
(Eth1)
```
10Gbps — —
Ethernet 2
```
(Eth2)
```
1Gbps — —
Ethernet 3
```
(Eth3)
```
1Gbps — —
Ethernet 4
```
(Eth4)
```
10Gbps — — —
Ethernet 5
```
(Eth5)
```
10Gbps — — —
The M-700 Appliance has two ports on its back panel labeled Ethernet 1/2 and Ethernet
```
1/3; however, the appliance uses a 20Gb aggregate software interface called bond1
```
instead of separate Eth2 and Eth3 subinterfaces.
Logging Rates
Review the logging rates for the all M-Series appliance models. To achieve the logging rates listed
below, the M-Series appliance must be a single log collector in a collector group and you must
install all the logging disks for your M-Series model.
Panorama Getting Started 232 ©2026 Palo Alto Networks, Inc.
Set Up Panorama
Model Capacities and
Features
M-700
Appliance
M-600
Appliance
M-300
Appliance
M-200
Appliance
Maximum Logging
Rate for Panorama
in Management
Only mode
Local log storage is not supported
Maximum Logging
Rate for Panorama
in Panorama Mode
36,500 logs/
second
25,000 logs/
second
16,500 logs/
second
10,000 logs/
second
Maximum Logging
Rate for Panorama
in Log Collector
Mode
73,000 logs/
second
50,000 logs/
second
33,000 logs/
second
28,000 logs/
second
Maximum Log
Storage on
Appliance
```
48TB (12x8TB
```
```
RAID disk)
```
```
48TB (12x8TB
```
```
RAID disk)
```
```
16TB (4x8TB
```
```
RAID disk)
```
```
16TB (4x8TB
```
```
RAID disk)
```
Default Log Storage
on Appliance
```
16TB (4x8TB
```
```
RAID disks)
```
```
16TB (4x8TB
```
```
RAID disks)
```
```
16TB (4x8TB
```
```
RAID disks)
```
```
16TB (4x8TB
```
```
RAID disks)
```
SSD Storage on
```
Appliance (for
```
logs that M-Series
```
appliances generate)
```
240GB 240GB 240GB 240GB
NFS Attached Log
Storage
Not available
Perform Initial Configuration of the M-Series Appliance
Where Can I Use This? What Do I Need?
```
• NGFW (Managed by Panorama) • M-series hardware appliance
```
• Super user role
By default, Panorama has an IP address of 192.168.1.1 and a username/password of admin/
admin. For security reasons, you must change these settings before continuing with other
configuration tasks. You must perform these initial configuration tasks either from the
```
Management (MGT) interface or using a direct serial port connection to the console port on the
```
M-700, M-600, M-500, M-300, or M-200 appliance.
Panorama Getting Started 233 ©2026 Palo Alto Networks, Inc.
Set Up Panorama
If you are configuring an M-Series appliance in Log Collector mode with 10GB interfaces,
you must complete this entire configuration procedure for the 10GB interfaces to display
as Up.
STEP 1 | Gather the required interface and server information from your network administrator.
```
• Gather the IP address, netmask (for IPv4) or prefix length (for IPv6), and default gateway
```
```
for each interface that you plan to configure (MGT, Eth1, Eth2, Eth3, Eth4, Eth5). Only the
```
MGT interface is mandatory.
Palo Alto Networks recommends that you specify all these settings for the MGT
```
interface. If you omit values for some of these settings (such as the default
```
```
gateway), you can access Panorama only through the console port for future
```
configuration changes. You cannot commit the configurations for other interfaces
unless you specify all these settings.
If you plan to use the appliance as a Panorama management server, Palo Alto Networks
recommends using the MGT interface only for managing Panorama and using other
interfaces for managing devices, collecting logs, communicating with Collector Groups, and
```
deploying updates to devices (see M-Series Appliance Interfaces).
```
• Gather the IP addresses of the DNS servers.
STEP 2 | Access the M-Series appliance from your computer.
1. Connect to the M-Series appliance in one of the following ways:
• Attach a serial cable from a computer to the Console port on the M-Series appliance
```
and connect using terminal emulation software (9600-8-N-1).
```
• Attach an RJ-45 Ethernet cable from a computer to the MGT port on the M-Series
appliance. From a browser, go to https://192.168.1.1. Enabling access to this
URL might require changing the IP address on the computer to an address in the
```
192.168.1.0 network (for example, 192.168.1.2).
```
2. When prompted, log in to the appliance using the default username and password
```
(admin/admin). The appliance starts initializing.
```
Panorama Getting Started 234 ©2026 Palo Alto Networks, Inc.
Set Up Panorama
STEP 3 | Change the default admin password.
```
Starting with PAN-OS 9.0.4, the predefined, default administrator password (admin/
```
```
admin) must be changed on the first login on a device. The new password must be
```
a minimum of eight characters and include a minimum of one lowercase and one
uppercase character, as well as one number or special character.
Be sure to use the best practices for password strength to ensure a strict password
and review the password complexity settings.
1. Click the admin link in the lower left of the web interface.
2. Enter the Old Password, New Password, and Confirm New Password, and then click
OK. Store the new password in a safe location.
To ensure that the MGT interface remains secure, configure Minimum Password
```
Complexity settings (select Panorama > Setup > Management) and specify the
```
interval at which administrators must change their passwords.
Panorama Getting Started 235 ©2026 Palo Alto Networks, Inc.
Set Up Panorama
STEP 4 | Configure the network access settings for each interface that you will use to manage
Panorama, manage devices, collect logs, communicate with Collector Groups, and deploy
updates to devices.
To configure connectivity to Panorama using an IPv6 IP address, you must configure
both an IPv4 and IPv6 to successfully configure Panorama using an IPv6 IP address.
Panorama does not support configuring the management interface with only an IPv6
IP address.
1. Select Panorama > Setup > Interfaces and click the Interface Name.
2. (Non-MGT interfaces only) Enable the interface.
3. Edit the network access settings of each interface that Panorama will use. Only the MGT
interface is required. The Eth1, Eth2, Eth3, Eth4, and Eth5 interfaces are optional and
apply only if you plan to use the M-Series appliance as a Panorama management server.
1. Complete one or both of the following field sets based on the IP protocols of your
```
network:
```
IPv4—Public IP Address, IP Address, Netmask, and Default Gateway
If your firewalls connect to the Panorama management server using a public
```
IP address that is translated to a private IP address (NAT), enter the public
```
IP in the Public IP Address field, and the private IP in the IP Address field to
push both addresses to your firewalls.
IPv6—IPv6 Address/Prefix Length and Default IPv6 Gateway
2. Select the Device Management Services that the interface supports:
Device Management and Device Log Collection—You can assign one or more
interfaces.
Collector Group Communication—You can assign only one interface.
```
Device Deployment (software and content updates)—You can assign only one
```
interface.
3. (Optional) Select the Network Connectivity Services that the interface supports.
```
(MGT interface only) Disable Telnet and HTTP; these services use plaintext
```
and so are less secure than other services.
4. Click OK to save your changes.
STEP 5 | Configure the hostname, time zone, and general settings.
1. Select Panorama > Setup > Management and edit the General Settings.
2. Align the clock on Panorama and the managed firewalls to use the same Time Zone, for
example GMT or UTC. If you plan to use the Strata Logging Service, you must configure
NTP so that Panorama can stay in sync with the Strata Logging Service.
The firewall records timestamps when it generate logs and Panorama records
timestamps upon receiving the logs. Aligning the time zones ensures that the timestamps
Panorama Getting Started 236 ©2026 Palo Alto Networks, Inc.
Set Up Panorama
are synchronized and that the process of querying logs and generating reports on
Panorama is harmonious.
3. Enter a Hostname for the server. Panorama uses this as the display name/label for the
appliance. For example, this is the name that appears at the CLI prompt. It also appears
in the Collector Name field if you add the appliance as a managed collector on the
Panorama > Managed Collectors page.
4. (Optional) Enter the Latitude and Longitude to enable accurate placement of the M-
Series appliance on the world map. The App Scope > Traffic Maps and App Scope >
Threat Maps use these values.
5. Click OK to save your entries.
STEP 6 | Configure the DNS servers and Palo Alto Networks Update Server.
1. Select Panorama > Setup > Services and edit the settings.
2. Enter the IP address of the Primary DNS Server and (optionally) of the Secondary DNS
Server.
3. Enter the URL or static address of the Update Server (default
```
updates.paloaltonetworks.com).
```
Select Verify Update Server Identity if you want Panorama to verify that the
Update Server from which it downloads software or content packages has an
SSL certificate that a trusted authority signed. This option adds an additional
level of security for communication between the Panorama management server
and Update Server.
4. Click OK to save your entries.
STEP 7 | Commit your configuration changes.
Select Commit > Commit to Panorama and Commit your changes.
If you plan to use the M-Series appliance as a Panorama management server and you
configured interfaces other than MGT, you must assign those interfaces to the Device
Log Collection or Collector Group Communication functions when you Configure a
Managed Collector.. To make the interfaces operational, you must then Configure a
Collector Group for the managed collector and perform a Collector Group commit.
Panorama Getting Started 237 ©2026 Palo Alto Networks, Inc.
Set Up Panorama
STEP 8 | Verify network access to external services required for Panorama management, such as the
Palo Alto Networks Update Server.
1. Connect to the M-Series appliance in one of the following ways:
• Attach a serial cable from your computer to the Console port on the M-Series
```
appliance. Then use a terminal emulation software (9600-8-N-1) to connect.
```
• Use terminal emulation software such as PuTTY to open an SSH session to the IP
address that you specified for the MGT interface of the M-Series appliance during
initial configuration.
2. Log in to the CLI when prompted. Use the default admin account and the password that
you specified during initial configuration.
3. Use the Update Server Connectivity test to verify network connectivity to the Palo Alto
Networks Update Server as shown in the following example.
1. Select Panorama > Managed Devices > Troubleshooting, and select Updates Server
Connectivity from the Select Test drop-down.
2. Execute the update server connectivity test.
4. Use the following CLI command to retrieve information on the support entitlement for
Panorama from the Update Server:
admin> request support check
If you have connectivity, the Update Server responds with the support status for
Panorama. Because Panorama is not registered, the Update Server returns the following
```
message:
```
Contact Us
```
https://www.paloaltonetworks.com/company/contact-us.html
```
Support Home
Panorama Getting Started 238 ©2026 Palo Alto Networks, Inc.
Set Up Panorama
```
https://www.paloaltonetworks.com/support/tabs/overview.html
```
Device not found on this update server
STEP 9 | Next steps...
1. Register Panorama and Install Licenses.
2. Install Content and Software Updates for Panorama.
As a best practice, replace the default certificate that Panorama uses to secure
HTTPS traffic over the MGT interface.
Perform Initial Configuration of an Air Gapped M-Series Appliance
Where Can I Use This? What Do I Need?
```
• NGFW (Managed by Panorama) • M-series hardware appliance
```
• Super user role
Perform the initial configuration for an air gapped M-Series appliance. By default, Panorama has
an IP address of 192.168.1.1 and a username/password of admin/admin. For security reasons,
you must change these settings before continuing with other configuration tasks. You must
```
perform these initial configuration tasks either from the Management (MGT) interface or using a
```
direct serial port connection to the console port on the M-700, M-600, M-500, M-300, or M-200
appliance.
The air gapped Panorama cannot connect to the Palo Alto Networks update server because an
outbound internet connection is required. To activate licenses, upgrade the PAN-OS software
version, and install dynamic content updates you must upload the relevant files to the air gapped
firewalls manually.
If you are configuring an M-Series appliance in Log Collector mode with 10GB interfaces,
you must complete this entire configuration procedure for the 10GB interfaces to display
as Up.
STEP 1 | Gather the required information from your network administrator.
```
• Private IP address for the management (MGT) port
```
• Netmask
• Default gateway
• DNS server address
• NTP server address
STEP 2 | Install and power on M-Series appliance.
Review your M-Series appliance hardware reference guide for details and best practices.
Panorama Getting Started 239 ©2026 Palo Alto Networks, Inc.
Set Up Panorama
STEP 3 | Connect to the M-Series appliance.
You must log in using the default admin username. You are immediately prompted to change
the default admin password before you can continue. The new password must be a minimum
of eight characters and include a minimum of one lowercase and one uppercase character, as
well as one number or special character.
You can connect to the M-Series appliance in one of the following ways:
• Connect a serial cable from your computer to the Console port and connect to the M-Series
```
appliance using terminal emulation software (9600-8-N-1). Wait a few minutes for the
```
```
boot-up sequence to complete; when the M-Series appliance is ready, the prompt changes
```
to the name of the M-Series, for example M-500 login.
• Log in to the Panorama CLI by connecting an RJ-45 Ethernet cable from your
computer to the MGT interface on the M-Series appliance. From a browser, go to
```
https://192.168.1.1.
```
You may need to change the IP address on your computer to an address in the
192.168.1.0/24 network, such as 192.168.1.2, to access this URL.
STEP 4 | Configure the network settings for the air gapped M-Series appliance.
The following commands set the interface IP allocation to static, configures the IP address
```
for the MGT interface, the Domain Name Server (DNS), and Network Time Protocol (NTP)
```
server.
admin> configure
admin# set deviceconfig system type static
admin# set deviceconfig system ip-address <IP-Address> netmask
<Netmask-IP> default-gateway <Gateway-IP>
admin# set deviceconfig system dns-settings servers primary <IP-
Address> secondary <IP-Address>
admin# set deviceconfig system ntp-servers primary-ntp-server ntp-
server-address <IP-Address>
admin# set deviceconfig system ntp-servers secondary-ntp-server
ntp-server-address <IP-Address>
Panorama Getting Started 240 ©2026 Palo Alto Networks, Inc.
Set Up Panorama
```
STEP 5 | Register the M-Series appliance with the Palo Alto Networks Customer Support Portal (CSP).
```
1. Log in to the Palo Alto Networks CSP.
2. Click Register a Device.
3. Select Register device using Serial Number and click Next.
4. Enter the required Device Information.
• Enter the M-Series appliance Serial Number.
```
• Check (enable) Device will be used offline.
```
• Select the PAN-OS OS Release running on the M-Series appliance.
5. Enter the required Location Information.
• Enter the City the M-Series appliance is located in,
• Enter the Postal Code the M-Series appliance is located in,
• Enter the Country the M-Series appliance is located in.
6. Agree and Submit.
7. Skip this step when prompted to generate the optional Day 1 Configuration config
file.
STEP 6 | Download the Panorama license keys.
The license key files are required to activate your Panorama licenses when air gapped.
1. Log in to the Palo Alto Networks CSP.
2. Select Product > Devices and locate the M-Series appliance you added.
3. Download all license keys files from the download links available License column.
You must download a license key file for each license you want to active on Panorama.
STEP 7 | Active the Panorama licenses.
1. Log in to the Panorama web interface.
2. Select Panorama > Licenses and Manually upload license key.
Click Choose File to select the license key file you downloaded in the previous step and
click OK.
3. Repeat this step to uploaded and activate all licenses.
Panorama Getting Started 241 ©2026 Palo Alto Networks, Inc.
Set Up Panorama
```
STEP 8 | (Optional) Configure general Panorama settings as needed.
```
1. Select Panorama > Setup > Management and edit the General Settings.
2. Enter a Hostname for Panorama and enter your network Domain name. The domain
```
name is just a label; it will not be used to join the domain.
```
3. Enter Login Banner text that informs users who are about to log in that they require
authorization to access the Panorama management functions.
As a best practice, avoid using welcoming verbiage. Additionally, you should ask
your legal department to review the banner message to ensure it adequately
warns that unauthorized access is prohibited.
4. Enter the Latitude and Longitude to enable accurate placement of the M-Series on the
world map.
5. Click OK.
6. Commit and Commit to Panorama.
Panorama Getting Started 242 ©2026 Palo Alto Networks, Inc.
Set Up Panorama
STEP 9 | Upgrade the PAN-OS and dynamic content versions on Panorama.
Review the PAN-OS Upgrade Guide and PAN-OS Release Notes for detailed information
about your target PAN-OS upgrade version.
1. Log in to the Palo Alto Networks CSP.
2. Download dynamic content updates.
```
Alternatively, you can use a Secure Copy Protocol (SCP) server to automatically
```
download dynamic content updates for Panorama, managed firewalls, Log
Collectors, and WildFire appliances. An outbound internet connection is required
for the SCP server to download dynamic content updates from the Palo Alto
Networks Update Server.
1. Select Updates > Dynamic Updates.
2. Select the dynamic Content type you want to install.
3. Download the dynamic content update to your local device.
4. Repeat this step to download all required dynamic content updates.
3. Download a PAN-OS software update.
1. Select Updates > Software Updates.
2. For the Content type, select Panorama M Base. For the Release type, select
```
All(default) or Preferred.
```
3. In the Download column, click the PAN-OS version to download the software image
to your local device.
4. Log in to the Panorama web interface.
5. Select Panorama > Dynamic Updates and Upload the dynamic content updates you
downloaded.
Repeat this step to Browse and select all the dynamic content release versions.
6. Install the dynamic content updates.
7. Select Panorama > Software and Upload the PAN-OS software image you download.
8. Install the PAN-OS software version.
Panorama needs to restart to finish installing the PAN-OS software upgrade.
STEP 10 | Connect Panorama to your network.
1. Disconnect Panorama from your computer.
2. Connect the MGT port to a switch port on your management network using an RJ-45
Ethernet cable. Make sure that the switch port you cable on Panorama is configured for
autonegotiation.
M-Series Setup Overview
Where Can I Use This? What Do I Need?
```
• NGFW (Managed by Panorama) • M-series hardware appliance
```
Panorama Getting Started 243 ©2026 Palo Alto Networks, Inc.
Set Up Panorama
When setting up an M-Series appliance, you can deploy it using one of three operational modes:
• Management Only Mode: Dedicates the appliance entirely to managing firewalls and
Dedicated Log Collectors, providing no local log collection capabilities aside from basic system
and configuration logs.
• Panorama Mode: Deploys the appliance as a management server that also collects logs locally,
which requires you to configure RAID disk arrays to make them available for logging.
• Log Collector Mode: Sets up the appliance as a Dedicated Log Collector, which also requires
you to configure the RAID disk arrays for logging before finalizing the Log Collector setup,
• Set Up an M-Series Appliance in Management Only Mode
• Set Up an M-Series Appliance in Panorama Mode
• Set Up an M-Series Appliance in Log Collector Mode
Set Up an M-Series Appliance in Management Only Mode
Set up the Panorama management server in Management Only mode to dedicate Panorama to
managing firewalls and Dedicated Log Collectors. Panorama in Management Only mode have
no log collection capabilities, except for config and system logs, and requires a Dedicated Log
Collector to store logs.
If you configured a local Log Collector, the local Log Collector still exists on Panorama
when you change to Management Only mode despite having no log collection capabilities.
```
Deleting the local Log Collector (Panorama > Managed Collectors) deletes the Eth1/1
```
interface configuration the local Log Collector uses by default. If you decide to delete the
local Log Collector, you must reconfigure the Eth1/1 interface.
STEP 1 | Rack mount the M-Series appliance. Refer to the M-Series Appliance Hardware Reference
Guide for instructions.
STEP 2 | Perform Initial Configuration of the M-Series Appliance.
STEP 3 | Register Panorama and Install Licenses.
STEP 4 | Install content and software updates on Panorama.
Panorama Getting Started 244 ©2026 Palo Alto Networks, Inc.
Set Up Panorama
STEP 5 | Change to Management Only mode.
1. Log in to the Panorama CLI.
2. Switch from Panorama mode to Management Only mode:
request system system-mode management-only
3. Enter Y to confirm the mode change. The Panorama management server reboots. If the
reboot process terminates your terminal emulation software session, reconnect to the
Panorama management server to see the Panorama login prompt.
If you see a CMS Login prompt, this means the Panorama management server has not
finished rebooting. Press Enter at the prompt without typing a username or password.
4. Log back in to the CLI.
5. Verify that the switch to Management Only mode succeeded:
show system info | match system-mode
If the mode change succeeded, the output displays:
system mode:management-only
STEP 6 | Configure Administrative Access to Panorama
STEP 7 | Manage Firewalls
STEP 8 | Manage Log Collection
Set Up an M-Series Appliance in Panorama Mode
STEP 1 | Rack mount the M-Series appliance. Refer to the M-Series Appliance Hardware Reference
Guide for instructions.
STEP 2 | Perform Initial Configuration of the M-Series Appliance.
STEP 3 | Register Panorama and Install Licenses.
STEP 4 | Install Content and Software Updates for Panorama.
STEP 5 | Configure each array. This task is required to make the RAID disks available for logging.
Optionally, you can add disks to Increase Storage on the M-Series Appliance.
STEP 6 | Configure Administrative Access to Panorama.
STEP 7 | Manage Firewalls.
STEP 8 | Manage Log Collection.
Set Up an M-Series Appliance in Log Collector Mode
STEP 1 | Rack mount the M-Series appliance. Refer to the M-Series Appliance Hardware Reference
Guide for instructions.
STEP 2 | Perform Initial Configuration of the M-Series Appliance
Panorama Getting Started 245 ©2026 Palo Alto Networks, Inc.
Set Up Panorama
STEP 3 | Register Panorama and Install Licenses
STEP 4 | Install Content and Software Updates for Panorama
STEP 5 | Configure each array. This task is required to make the RAID disks available for logging.
Optionally, you can add disks to Increase Storage on the M-Series Appliance.
STEP 6 | Set Up the M-Series Appliance as a Log Collector
STEP 7 | Manage Log Collection
Set Up the M-Series Appliance as a Log Collector
Where Can I Use This? What Do I Need?
```
• NGFW (Managed by Panorama) • M-series hardware appliance
```
• Log Collector License
If you want a dedicated appliance for log collection, configure an M-200, M-300, M-600, or
M-700 appliance in Log Collector mode. To do this, you first perform the initial configuration
of the appliance in Panorama mode, which includes licensing, installing software and content
```
updates, and configuring the management (MGT) interface. You then switch the M-Series
```
appliance to Log Collector mode and complete the Log Collector configuration. Additionally, if
```
you want to use dedicated M-Series Appliance Interfaces (recommended) instead of the MGT
```
interface for log collection and Collector Group communication, you must first configure the
interfaces for the Panorama management server, then configure them for the Log Collector, and
then perform a Panorama commit followed by a Collector Group commit.
Perform the following steps to set up a new M-Series appliance as a Log Collector or to convert
an existing M-Series appliance that was previously deployed as a Panorama management server.
If you are configuring an M-Series appliance in Log Collector mode with 10GB interfaces,
you must complete this entire configuration procedure for the 10GB interfaces to display
as Up.
Switching the M-Series appliance from Panorama mode to Log Collector mode reboots
the appliance, deletes the local Log Collector, deletes any existing log data, and deletes
all configurations except the management access settings. Switching the mode does not
delete licenses, software updates, or content updates.
STEP 1 | Set up the Panorama management server that will manage the Log Collector if you have not
already done so.
Perform one of the following tasks:
• Set Up the Panorama Virtual Appliance
• Set Up the M-Series Appliance
Panorama Getting Started 246 ©2026 Palo Alto Networks, Inc.
Set Up Panorama
STEP 2 | Record the management IP addresses of the Panorama management server.
```
If you deployed Panorama in a high availability (HA) configuration, you need the IP address of
```
each HA peer.
1. Log in to the web interface of the Panorama management server.
2. Record the IP Address of the solitary (non-HA) or active (HA) Panorama by selecting
Panorama > Setup > Management and checking the Management Interface Settings.
3. For an HA deployment, record the Peer HA IP Address of the passive Panorama by
selecting Panorama > High Availability and checking the Setup section.
STEP 3 | Set up the M-Series appliance that will serve as a Dedicated Log Collector.
If you previously deployed this appliance as a Panorama management server, you can skip this
step because the MGT interface is already configured and the licenses and updates are already
installed.
The M-Series appliance in Log Collector mode does not have a web interface for configuration
tasks, only a CLI. Therefore, before changing the mode on the M-Series appliance, use the web
interface in Panorama mode to:
1. Perform Initial Configuration of the M-Series Appliance.
2. Register Panorama and Install Licenses.
3. Install Content and Software Updates for Panorama.
STEP 4 | Access the CLI of the M-Series appliance.
1. Connect to the M-Series appliance in one of the following ways:
• Attach a serial cable from your computer to the Console port on the M-Series
```
appliance. Then use terminal emulation software (9600-8-N-1) to connect.
```
• Use terminal emulation software such as PuTTY to open an SSH session to the IP
address that you specified for the MGT interface of the M-Series appliance during
initial configuration.
2. Log in to the CLI when prompted. Use the default admin account and the password that
you specified during initial configuration.
Panorama Getting Started 247 ©2026 Palo Alto Networks, Inc.
Set Up Panorama
STEP 5 | Switch from Panorama mode to Log Collector mode.
1. Switch to Log Collector mode by entering the following command:
> request system system-mode logger
2. Enter Y to confirm the mode change. The M-Series appliance reboots. If the reboot
process terminates your terminal emulation software session, reconnect to the M-Series
appliance to see the Panorama login prompt.
If you see a CMS Login prompt, this means the Log Collector has not finished
rebooting. Press Enter at the prompt without typing a username or password.
3. Log back in to the CLI.
4. Verify that the switch to Log Collector mode succeeded:
> show system info | match system-mode
If the mode change succeeded, the output displays:
system-mode: logger
Panorama Getting Started 248 ©2026 Palo Alto Networks, Inc.
Set Up Panorama
STEP 6 | Configure the logging disks as RAID1 pairs.
If you previously deployed the appliance as a Panorama management server, you can skip this
step because the disk pairs are already configured and available.
The time required to configure the drives varies from several minutes to a couple of
hours, based on the amount of data on the drives.
1. Determine which disk pairs are present for configuring as RAID pairs on the M-Series
```
appliance:
```
> show system raid detail
Perform the remaining steps to configure each disk pair that has present disks. This
example uses disk pair A1/A2.
2. To add the first disk in the pair, enter the following command and enter y when
prompted to confirm the request:
> request system raid add A1
Wait for the process to finish before adding the next disk in the pair. To monitor the
progress of the RAID configuration, re-enter:
> show system raid detail
After the process finishes for the first disk, the output displays the disk pair status as
Available but degraded.
3. Add the second disk in the pair:
> request system raid add A2
4. Verify that the disk setup is complete:
> show system raid detail
After the process finishes for the second disk, the output displays the disk pair status as
Available and clean:
Disk Pair A Available
Status clean
Panorama Getting Started 249 ©2026 Palo Alto Networks, Inc.
Set Up Panorama
STEP 7 | Enable connectivity between the Log Collector and Panorama management server.
Enter the following commands at the Log Collector CLI, where <IPaddress1> is for the MGT
```
interface of the solitary (non-HA) or active (HA) Panorama and <IPaddress2> is for the MGT
```
```
interface of the passive (HA) Panorama, if applicable.
```
> configure
# set deviceconfig system panorama-server <IPaddress1> panorama-
server-2 <IPaddress2>
# commit
# exit
STEP 8 | Record the serial number of the Log Collector.
You need the serial number to add the Log Collector as a managed collector on the Panorama
management server.
1. At the Log Collector CLI, enter the following command to display its serial number.
> show system info | match serial
2. Record the serial number.
Panorama Getting Started 250 ©2026 Palo Alto Networks, Inc.
Set Up Panorama
STEP 9 | Create a device registration authentication key.
1. Select Panorama > Device Registration Auth Key and Add a new authentication key.
2. Configure the authentication key.
• Name—Add a descriptive name for the authentication key.
• Lifetime—Specify the key lifetime for how long you can use the authentication key to
onboard new Log Collectors.
• Count—Specify how many times you can use the authentication key to onboard new
Log Collectors.
• Device Type—Specify that this authentication key is used to authenticate only a Log
Collector.
You can select Any to use the device registration authentication key to
onboard firewalls, Log Collectors, and WildFire appliances.
```
• (Optional) Devices—Enter one or more device serial numbers to specify for which Log
```
Collectors the authentication key is valid.
3. Click OK.
4. Copy Auth Key and Close.
Panorama Getting Started 251 ©2026 Palo Alto Networks, Inc.
Set Up Panorama
STEP 10 | Add the Log Collector as a managed collector to the Panorama management server.
1. Select Panorama > Managed Collectors and Add a managed collector.
2. In the General settings, enter the serial number (Collector S/N) you recorded for the Log
Collector.
3. In the Panorama Server IP field, enter the IP address or FQDN of the solitary (non-HA)
```
or active (HA) Panorama. For HA deployments, enter the IP address or FQDN of the
```
passive Panorama peer in the Panorama Server IP 2 field.
These IP addresses must specify a Panorama interface that has Device Management and
Device Log Collection services enabled. By default, these services are enabled only on
the MGT interface. However, you might have enabled the services on other interfaces
when you Set Up the M-Series Appliance that is a Panorama management server.
4. Select Interfaces, click Management, and configure one or both of the following field
sets for the MGT interface based on the IP protocols of your network.
• IPv4—IP Address, Netmask, and Default Gateway
• IPv6—IPv6 Address/Prefix Length and Default IPv6 Gateway
5. Click OK twice to save your changes to the Log Collector.
6. Select Commit > Commit to Panorama and Commit your changes to the Panorama
configuration.
This step is required before you can enable logging disks.
7. Verify that Panorama > Managed Collectors lists the Log Collector you added. The
Connected column displays a check mark to indicate that the Log Collector is connected
to Panorama. You might have to wait a few minutes before the page displays the
updated connection status.
At this point, the Configuration Status column displays Out of Sync and the Run
Time Status column displays disconnected. The status will change to In Sync and
```
connected after you configure a Collector Group (Step Assign the Log Collector
```
```
to a Collector Group.).
```
STEP 11 | Add the device registration authentication key to the Log Collector.
Add the device registration authentication key only to a Dedicated Log Collector. A Panorama
in Panorama mode does not need to authenticate its own local Log Collector.
1. Log in to the Log Collector CLI.
2. Add the device registration authentication key.
admin> request authkey set <auth-key>
Panorama Getting Started 252 ©2026 Palo Alto Networks, Inc.
Set Up Panorama
STEP 12 | Enable the logging disks.
1. Select Panorama > Managed Collectors and edit the Log Collector.
2. Select Disks and Add each RAID disk pair.
3. Click OK to save your changes.
4. Select Commit > Commit to Panorama and Commit your changes to the Panorama
configuration.
```
STEP 13 | (Recommended) Configure the Ethernet1, Ethernet2, Ethernet3, Ethernet4, and Ethernet5
```
interfaces if the Panorama management server and Log Collector will use them for Device
```
Log Collection (receiving logs from firewalls) and Collector Group Communication.
```
If you previously deployed the Log Collector as a Panorama management server and
configured these interfaces, you must reconfigure them because switching to Log Collector
Panorama Getting Started 253 ©2026 Palo Alto Networks, Inc.
Set Up Panorama
```
mode (Switch from Panorama mode to Log Collector mode.) would have deleted all
```
configurations except the management access settings.
1. Configure each interface on the Panorama management server (other than the MGT
```
interface) if you haven’t already:
```
1. Select Panorama > Setup > Interfaces and click the Interface Name.
2. Select <interface-name> to enable the interface.
3. Complete one or both of the following field sets based on the IP protocols of your
```
network:
```
IPv4—IP Address, Netmask, and Default Gateway
IPv6—IPv6 Address/Prefix Length and Default IPv6 Gateway
4. Select the Device Management Services that the interface supports:
Device Management and Device Log Collection—You can assign one or more
interfaces.
Collector Group Communication—You can assign only one interface.
```
Device Deployment (software and content updates)—You can assign only one
```
interface.
5. Click OK to save your changes.
2. Configure each interface on the Log Collector (other than the MGT interface):
1. Select Panorama > Managed Collectors and edit the Log Collector.
2. Select Interfaces and click the name of the interface.
3. Select <interface-name> to enable the interface.
4. Complete one or both of the following field sets based on the IP protocols of your
```
network:
```
IPv4—IP Address, Netmask, and Default Gateway
IPv6—IPv6 Address/Prefix Length and Default IPv6 Gateway
5. Select the Device Management Services that the interface supports:
Device Log Collection—You can assign one or more interfaces.
Collector Group Communication—You can assign only one interface.
6. Click OK to save your changes to the interface.
3. Click OK to save your changes to the Log Collector.
4. Select Commit > Commit to Panorama and Commit your changes to the Panorama
configuration.
Panorama Getting Started 254 ©2026 Palo Alto Networks, Inc.
Set Up Panorama
```
STEP 14 | (Optional) If your deployment is using custom certificates for authentication between
```
Panorama and managed devices, deploy the custom client device certificate. For more
information, see Configure Authentication Using Custom Certificates.
1. Select Panorama > Certificate Management > Certificate Profile and choose the
certificate profile from the drop-down or click New Certificate Profile to create one.
2. Select Panorama > Managed Collectors > Add > Communication for a Log Collector.
3. Select the Secure Client Communication check box.
4. Select the type of device certificate the Type drop-down.
• If you are using a local device certificate, select the Certificate and Certificate Profile
from the respective drop-downs.
• If you are using SCEP as the device certificate, select the SCEP Profile and Certificate
Profile from the respective drop-downs.
5. Click OK.
Panorama Getting Started 255 ©2026 Palo Alto Networks, Inc.
Set Up Panorama
```
STEP 15 | (Optional) Configure Secure Server Communication on a Log Collector. For more
```
information, see Configure Authentication Using Custom Certificates.
1. Select Panorama > Managed Collectors > Add > Communication.
2. Verify that the Custom Certificate Only check box is not selected. This allows you to
continue managing all devices while migrating to custom certificates.
When the Custom Certificate Only check box is selected, the Log Collector
does not authenticate and cannot receive logs from devices using predefined
certificates.
3. Select the SSL/TLS service profile from the SSL/TLS Service Profile drop-down. This
SSL/TLS service profile applies to all SSL connections between the Log Collector and
devices sending it logs.
4. Select the certificate profile from the Certificate Profile drop-down.
5. Select Authorize Client Based on Serial Number to have the server check clients against
the serial numbers of managed devices. The client certificate must have the special
keyword $UDID set as the CN to authorize based on serial numbers.
6. In Disconnect Wait Time (min), enter the number of minutes Panorama should wait
before breaking and reestablishing the connection with its managed devices. This field is
blank by default and the range is 0 to 44,640 minutes.
The disconnect wait time does not begin counting down until you commit the
new configuration.
7. (Optional) Configure an authorization list.
1. Click Add under Authorization List.
2. Select the Subject or Subject Alt Name as the Identifier type.
3. Enter an identifier of the selected type.
4. Click OK.
5. Select Check Authorization List to enforce the authorization list.
8. Click OK.
9. Select Commit > Commit to Panorama.
STEP 16 | Assign the Log Collector to a Collector Group.
1. Configure a Collector Group. You must perform a Panorama commit and then a Collector
Group commit to synchronize the Log Collector configuration with Panorama and to put
Panorama Getting Started 256 ©2026 Palo Alto Networks, Inc.
Set Up Panorama
```
the Eth1, Eth2, Eth3, Eth4, and Eth5 interfaces (if you configured them) in an operational
```
state on the Log Collector.
In any single Collector Group, all the Log Collectors must run on the same
Panorama model: all M-700 appliances, all M-600 appliances, all M-500
appliances, all M-300 appliances, all M-200 appliances, or all Panorama virtual
appliances.
As a best practice, Enable log redundancy across collectors if you add multiple
Log Collectors to a single Collector group. This option requires each Log
Collector to have the same number of logging disks.
2. Select Panorama > Managed Collectors to verify that the Log Collector configuration is
synchronized with Panorama.
The Configuration Status column should display In Sync and the Run Time Status column
should display connected.
3. Access the Log Collector CLI and enter the following command to verify that its
interfaces are operational:
> show interface all
The output displays the state as up for each interface that is operational.
4. If the Collector Group has multiple Log Collectors, troubleshoot connectivity to network
resources to verify they can communicate with each other by performing a Ping
connectivity test for each interface that the Log Collectors use. For the source IP
address, specify the interface of one of the Log Collectors. For the host IP address,
specify the matching interface of another Log Collector in the same Collector Group.
STEP 17 | Next steps...
To enable the Log Collector to receive firewall logs:
1. Configure Log Forwarding to Panorama.
2. Verify Log Forwarding to Panorama.
Increase Storage on the M-Series Appliance
Where Can I Use This? What Do I Need?
```
• NGFW (Managed by Panorama) • M-series hardware appliance
```
After you Perform Initial Configuration of the M-Series Appliance, you can increase log storage
capacity of the appliance by upgrading the existing drive pairs to larger capacity drives or by
installing additional drive pairs in empty drive bays. For example, you can choose to upgrade the
existing 1TB drives to 2TB on an M-500 appliance, or you can add 2TB drives to the empty drive
```
bays (B1 through D2).
```
Panorama Getting Started 257 ©2026 Palo Alto Networks, Inc.
Set Up Panorama
The M-Series appliances leverage RAID 1 for data redundancy in the event of disk failure.
Therefore, the pair of drives in a RAID 1 array need to be identical. However, you are free
to mix drive capacities across different RAID 1 arrays. For example, the drives in the A1/
A2 RAID 1 array can be 1TB drives, and the drives in the B1/B2 RAID 1 array can be 2TB
drives.
```
The following table lists the maximum number of drive bays (disks) and the available drive
```
capacities supported on M-Series appliances.
```
Because each drive pair (A1/A2 for example) is in a RAID 1 array, the total storage
```
capacity is half of the total drives installed. For example, if an M-500 appliance has 2TB
drives installed in drive bays A1/A2 and B1/B2, the A1/A2 array provides 2TB total
storage and the B1/B2 array provides another 2TB for a total of 4TB.
Appliance Number of Supported Drive
```
Bays (Disks)
```
Supported Drive Capacity
M-200
Appliance
4 8TB
M-300
Appliance
4 8TB
M-500
Appliance
24 1TB or 2TB
M-600
Appliance
12 8TB
M-700
Appliance
12 8TB
Before expanding log storage capacity, Determine Panorama Log Storage Requirements. If you
need more log storage than a single M-Series appliance supports, you can add Dedicated Log
```
Collectors (see Configure a Managed Collector) or you can Configure Log Forwarding from
```
Panorama to External Destinations.
You don’t need to take the M-Series appliance offline to expand the storage when adding
drives to an M-Series appliance that is already deployed. When the additional drives
are configurable and available, the M-Series appliance redistributes the logs among all
available drives. This log redistribution process happens in the background and does
not impact uptime or the availability of the M-Series appliance. However, the process
```
does diminish the maximum logging rate. The Redistribution State column (Panorama >
```
```
Collector Groups) indicates the completion status of the process as a percentage.
```
• Add Additional Drives to an M-Series Appliance
• Upgrade Drives on an M-Series Appliance
Panorama Getting Started 258 ©2026 Palo Alto Networks, Inc.
Set Up Panorama
Add Additional Drives to an M-Series Appliance
Where Can I Use This? What Do I Need?
```
• NGFW (Managed by Panorama) • M-series hardware appliance
```
STEP 1 | Install the new drives in the appropriate drive bays.
Make sure to add the drives sequentially in the next open drive bays. For example, add drives
to B1 and B2 before adding drives to C1 and C2.
```
STEP 2 | Access the command line interface (CLI) on the M-Series appliance.
```
Connect to the M-Series appliance in one of two ways:
• Connect a serial cable from your computer to the Console port and connect to the M-Series
```
appliance using terminal emulation software (9600-8-N-1).
```
```
• Use terminal emulation software (such as PuTTY) to open a Secure Shell (SSH) session to
```
the IP address of the M-Series appliance.
STEP 3 | When prompted, log in to the appliance.
Use the default administrator account and the assigned password.
STEP 4 | Configure each array.
The time required to mirror the data on the drive can take minutes, a few hours, or
more than a day depending on the amount of data on the drive.
The following example uses the drives in bays B1 and B2.
1. Enter the following commands and confirm the request when prompted. This command
deletes any existing data on the disks you are adding to the M-Series appliance.
> request system raid add B1
> request system raid add B2
```
(RMA only) If you want to try and preserve the data on the disks, try the
```
following commands instead:
> request system raid add B1 force no-format
> request system raid add B2 force no-format
2. To monitor the progress of the RAID configuration, enter the following command:
> show system raid detail
When the RAID set up is complete, the following response displays:
Disk Pair A Available
Panorama Getting Started 259 ©2026 Palo Alto Networks, Inc.
Set Up Panorama
Status clean
Disk id A1 Present
```
model : ST91000640NS
```
```
size : 953869 MB
```
```
status : active sync
```
Disk id A2 Present
```
model : ST91000640NS
```
```
size : 953869 MB
```
```
status : active sync
```
Disk Pair B Available
Status clean
Disk id B1 Present
```
model : ST91000640NS
```
```
size : 953869 MB
```
```
status : active sync
```
Disk id B2 Present
```
model : ST91000640NS
```
```
size : 953869 MB
```
```
status : active sync
```
STEP 5 | Make the array available for logging.
To enable the array for logging, you must first add the appliance as a managed collector on
Panorama. If not already added, see Configure a Managed Collector.
1. Log in to the web interface of the Panorama management server that manages this Log
Collector.
2. Select Panorama > Managed Collectors and edit the Log Collector.
3. Select Disks and Add each array.
4. Click OK to save your changes.
5. Select Commit > Commit to Panorama and Commit your changes.
6. Select Commit > Push to Devices, select the Collector Group, and Push your changes.
Upgrade Drives on an M-Series Appliance
Where Can I Use This? What Do I Need?
```
• NGFW (Managed by Panorama) • M-200, M-300, M-500, M-600, or M-700
```
hardware appliance
```
STEP 1 | Access the command line interface (CLI) on the M-Series appliance.
```
Connect to the M-Series appliance in one of two ways:
• Connect a serial cable from your computer to the Console port and connect to the M-Series
```
appliance using terminal emulation software (9600-8-N-1).
```
```
• Use terminal emulation software (such as PuTTY) to open a Secure Shell (SSH) session to
```
the IP address of the M-Series appliance.
STEP 2 | When prompted, log in to the appliance.
Use the default administrator account and the assigned password.
Panorama Getting Started 260 ©2026 Palo Alto Networks, Inc.
Set Up Panorama
STEP 3 | Verify that the RAID 1 status for the installed drives shows there are at least two functioning
RAID 1 arrays. During the upgrade, you will upgrade one RAID 1 array at a time and there
must be at least one other RAID 1 array that is available to the appliance. The appliance will
show an abort error if you try to remove the only functioning array from the configuration.
Enter the following command to view RAID status:
> show system raid detail
For example, the following shows an output from an M-500 appliance with two available
```
arrays (Disk Pair A and Disk Pair B). If there is only one available array, you must add a second
```
array as described in Add Additional Drives to an M-Series Appliance before you upgrade the
drives.
Disk Pair A Available
Status clean
Disk id A1 Present
```
model : ST91000640NS
```
```
size : 953869 MB
```
```
status : active sync
```
Disk id A2 Present
```
model : ST91000640NS
```
```
size : 953869 MB
```
```
status : active sync
```
Disk Pair B Available
Status clean
Disk id B1 Present
```
model : ST91000640NS
```
```
size : 953869 MB
```
```
status : active sync
```
Disk id B2 Present
```
model : ST91000640NS
```
```
size : 953869 MB
```
```
status : active sync
```
Panorama Getting Started 261 ©2026 Palo Alto Networks, Inc.
Set Up Panorama
STEP 4 | Remove the first 1TB drive and replace it with a 2TB drive.
1. To remove the first drive from the RAID 1 array configuration (A1 in this example), enter
the following command and enter y when prompted to confirm the request:
> request system raid remove A1
2. Physically remove the first drive from the drive bay. Press the ejector button on the
drive carrier in drive bay A1 to release the ejector handle. Then pull the handle toward
you and slide the drive out of the appliance.
3. Remove a 2TB drive from its packaging and place the drive on a table next to the drive
you just removed. Take note of how the drive is installed in the carrier because you will
install the 2TB drive in this same carrier.
4. Remove the four screws holding the 1TB drive in the carrier and remove the drive from
the carrier.
5. Attach the 2TB drive to the carrier using the same four screws you removed from the
1TB drive and then reinsert the carrier with the 2TB drive into drive bay A1.
6. Enter the following command to verify the 2TB drive is recognized:
show system raid detail
```
Verify that the A1 disk shows the correct model and size (about 2TB). If the model and
```
size are not correct, run the above command again until the correct model and size are
shown.
If the wrong model and size are consistently shown, enter the following command:
request system raid remove A1
Wait for 30 seconds once you run the above command, then remove the disk and
reinsert it and repeat the show system raid detail command to verify the size and
model.
Panorama Getting Started 262 ©2026 Palo Alto Networks, Inc.
Set Up Panorama
STEP 5 | Copy the data from the remaining installed 1TB drive in the RAID 1 array to the newly
installed 2TB drive in that array.
The time required to copy the data may vary from several minutes to a few hours,
depending on the amount of data on the drive.
1. To copy the data from the 1TB drive in drive bay A2 to the newly installed 2TB drive in
drive bay A1, enter the following command and enter y when prompted:
> request system raid copy from A2 to A1
2. To view the status of the copy process, run the following command:
> show system raid detail
Continue running this command to view the RAID detail output until you see that the
```
array (A1/A2 in this example) shows Available.
```
At this point, drive A2 will show not in use because there is a drive size
mismatch.
STEP 6 | Upgrade the second drive in the RAID 1 array to a 2TB drive.
1. Remove the second 1TB drive (from drive bay A2 in the current example) for the RAID 1
array configuration:
> request system raid remove A2
2. Insert the carrier with the newly installed 2TB drive into drive bay A2 and add it to the
RAID 1 array configuration:
> request system raid add A2
The system will copy the data from A2 to A1 to mirror the drives.
3. To view the status of the copy process, run the following command:
> show system raid detail
```
Continue to view the RAID detail output until you see that the array (A1/A2 in this
```
```
example) shows Available and both disks show active sync.
```
Disk Pair A Available
Status clean
Disk id A1 Present
```
model : ST2000NX0253
```
```
size : 1907138 MB
```
```
status : active sync
```
Disk id A2 Present
```
model : ST2000NX0253
```
Panorama Getting Started 263 ©2026 Palo Alto Networks, Inc.
Set Up Panorama
```
size : 1907138 MB
```
```
status : active sync
```
STEP 7 | Upgrade drives for additional RAID 1 arrays as needed.
To upgrade additional RAID 1 arrays to 2TB drives, repeat this procedure replacing the drive
designators as applicable. For example, replace A1 with B1 and A2 with B2 to upgrade the
drives in the B1/B2 RAID 1 array.
Configure Panorama to Use Multiple Interfaces
Where Can I Use This? What Do I Need?
```
• NGFW (Managed by Panorama) • M-series hardware appliance
```
In a large-scale network, you can improve security and reduce congestion by implementing
network segmentation, which involves segregating the subnetworks based on resource usage,
user roles, and security requirements. Panorama supports network segmentation by enabling you
```
to use multiple M-Series Appliance Interfaces for managing devices (firewalls, Log Collectors, and
```
```
WildFire appliances and appliance clusters) and collecting logs; you can assign separate interfaces
```
to the devices on separate subnetworks.
Using multiple interfaces to collect logs also provides the benefit of load balancing, which is
particularly useful in environments where the firewalls forward logs at high rates to the Log
Collectors. If you enable the forward to all Log Collectors setting in the Collector Group log
forwarding preference list, logs are sent on all configured interfaces configured. Otherwise, logs
are forwarded over a single interface, and if that interface goes down, log forwarding continues
over the next configured interface. For example, you configure Eth1/1, Eth1/2, and Eth1/3 for log
forwarding. In the event the Eth1/1 interface goes down, log forwarding continues over Eth1/2.
Because administrators access and manage Panorama over the MGT interface, securing that
interface is especially important. One method for improving the security of the MGT interface
is to offload Panorama services to other interfaces. In addition to device management and log
collection, you can also offload Collector Group communication and deployment of software and
content updates to firewalls, Log Collectors, and WildFire appliances and appliance clusters. By
offloading these services, you can reserve the MGT interface for administrative traffic and assign
it to a secure subnetwork that is segregated from the subnetworks where your firewalls, Log
Collectors, and WildFire appliances and appliance clusters reside.
• Multiple Interfaces for Network Segmentation Example
• Configure Panorama for Network Segmentation
Multiple Interfaces for Network Segmentation Example
Where Can I Use This? What Do I Need?
```
• NGFW (Managed by Panorama) • M-series hardware appliance
```
Panorama Getting Started 264 ©2026 Palo Alto Networks, Inc.
Set Up Panorama
Figure 1 illustrates a deployment that uses multiple interfaces on M-500 appliances in Panorama
mode and Log Collector mode. In this example, the interfaces support network segmentation as
```
follows:
```
• Panorama management network—To protect the Panorama web interface, CLI, and XML API
from unauthorized access, the MGT interface on Panorama connects to a subnetwork that only
administrators can access.
• Internet—Panorama uses the MGT interface to communicate with external services such as the
Palo Alto Networks Update Server.
• Perimeter Gateway and Data Center—Panorama uses a separate pair of interfaces to manage
the firewalls and Log Collectors in each of these subnetworks. Managing firewalls typically
generates less traffic than querying Log Collectors for report information. Therefore, Panorama
```
uses 1Gbps interfaces (Eth1 and Eth2) for managing the firewalls and uses 10Gbps interfaces
```
```
(Eth4 and Eth5) for querying and managing the Log Collectors. Each Log Collector uses its MGT
```
interface to respond to the queries but uses its Eth4 and Eth5 interfaces for the heavier traffic
associated with collecting logs from the firewalls.
• Software and content updates—The firewalls and Log Collectors in both subnetworks retrieve
software and content updates over the Eth3 interface on Panorama.
Panorama Getting Started 265 ©2026 Palo Alto Networks, Inc.
Set Up Panorama
Figure 9: Multiple Panorama Interfaces
Configure Panorama for Network Segmentation
Where Can I Use This? What Do I Need?
```
• NGFW (Managed by Panorama) • M-series hardware appliance
```
To offload Panorama services from the MGT interface to other interfaces, start by configuring
the interfaces on the Panorama management server. If your network has heavy log traffic,
remember that the Eth4 and Eth5 interfaces on the M-600, and M-700 appliances support higher
```
throughput (10Gbps) than the other interfaces (1Gbps). Then, configure the Log Collectors in each
```
subnetwork to connect with specific interfaces on Panorama. For each Log Collector, you also
select an interface for Collector Group communication and one or more interfaces for collecting
logs from firewalls. Finally, configure the firewalls in each subnetwork to connect with interfaces
on Panorama.
Panorama Getting Started 266 ©2026 Palo Alto Networks, Inc.
Set Up Panorama
If you are configuring an M-Series appliance in Log Collector mode with 10GB interfaces,
you must complete this entire configuration procedure for the 10GB interfaces to display
as Up.
```
Palo Alto Networks recommends that you specify the IP address, netmask (for IPv4) or
```
```
prefix length (for IPv6), and default gateway for the MGT interface. If you omit one of
```
```
these settings (such as the default gateway), you can access the M-Series appliance only
```
through the console port for future configuration changes.
Perform the following steps to configure Panorama and Dedicated Log Collectors to use multiple
```
interfaces:
```
STEP 1 | Verify that the Panorama appliances and firewalls support multiple interfaces, and have the
prerequisite software versions and configurations.
The M-Series appliances must run Panorama 8.0 or later to use a separate interface for
deploying updates and to use multiple interfaces for device management and log collection.
The M-200 and M-600 appliances must run Panorama 8.1 or later while the M-300 and
M-700 must run Panorama 11.1 or later. Panorama appliances deployed on ESXi, vCloud,
Air, Hyper-V and KVM must run Panorama 8.1 or later.
If you deployed a Panorama or Log Collector as a virtual appliance, verify the Supported
Interfaces for the Panorama Virtual Appliance.
The M-Series appliances must run Panorama 6.1 or later to use separate interfaces for log
collection or Collector Group communication.
The initial configuration of each Panorama management server is complete. This includes
configuration of the MGT interface.
To configure an IPv6 IP address for the Panorama MGT interface, you must
configure both an IPv4 and IPv6 to successfully configure Panorama using an IPv6
IP address. Panorama does not support configuring the MGT interface with only an
IPv6 IP address.
Log Collectors and Collector Groups are configured. This includes configuration of the MGT
interface on the Log Collectors.
To configure an IPv6 IP address for the MGT interface of a Log Collector, you must
configure both an IPv4 and IPv6 to successfully configure Panorama using an IPv6
IP address. Panorama does not support configuring the MGT interface with only an
IPv6 IP address.
The initial configuration of the firewalls is complete, you have added the firewalls to
Panorama as managed devices, and the firewalls in each subnetwork are assigned to a
separate template.
The initial configuration of WildFire appliances is complete and you have added WildFire
appliances to Panorama as managed devices.
Panorama Getting Started 267 ©2026 Palo Alto Networks, Inc.
Set Up Panorama
```
STEP 2 | Configure the interfaces on the solitary (non-HA) or active (HA) Panorama management
```
server.
Because the MGT interface was configured during initial Panorama configuration, you
don’t have to configure it again.
Perform these steps for each interface:
1. Log in to the Panorama Web Interface of the solitary (non-HA) or active (HA) Panorama
management server.
2. Select Panorama > Setup > Interfaces.
3. Click an Interface Name to edit the interface.
4. Select <interface-name> to enable the interface.
5. Configure one or both of these field sets based on the IP protocols of your network:
• IPv4—IP Address, Netmask, and Default Gateway
• IPv6—IPv6 Address/Prefix Length and Default IPv6 Gateway
6. Select the services that the interface supports:
• Device Management and Device Log Collection—Manage firewalls, Log Collectors,
and WildFire appliances and appliance clusters, collect logs that the Log Collectors
generate, and query the Log Collectors for report information. To support a
segmented network, you can enable these services on multiple interfaces.
• Collector Group Communication—Communicate with the Collector Groups that
Panorama manages across all subnetworks.
• Device Deployment—Deploy software and content updates to managed firewalls, Log
Collectors, and WildFire appliances and appliance clusters across all subnetworks.
7. Click OK to save your changes to the interface.
8. Click Commit > Commit to Panorama and Commit your changes.
9. Click Commit > Push to Devices and push the changes to the Collector Group that
contain the Log Collectors you modified.
```
STEP 3 | (HA only) Configure the interfaces on the passive Panorama management server.
```
1. Log in to the Panorama Web Interface of the active Panorama management server.
2. Select Panorama > Managed Collectors and select the passive HA peer.
3. Select Interfaces and click an interface to edit.
4. Check the Enable Interface box to enable the interface.
5. Configure one or both of these field sets based on the IP protocols of your network:
• IPv4—IP Address, Netmask, and Default Gateway
• IPv6—IPv6 Address/Prefix Length and Default IPv6 Gateway
6. Select the services that the interface supports:
• Device Management and Device Log Collection—Manage firewalls, Log Collectors,
and WildFire appliances and appliance clusters, collect logs that the Log Collectors
Panorama Getting Started 268 ©2026 Palo Alto Networks, Inc.
Set Up Panorama
generate, and query the Log Collectors for report information. To support a
segmented network, you can enable these services on multiple interfaces.
• Collector Group Communication—Communicate with the Collector Groups that
Panorama manages across all subnetworks.
• Device Deployment—Deploy software and content updates to managed firewalls, Log
Collectors, and WildFire appliances and appliance clusters across all subnetworks.
7. Click OK to save your changes to the interface.
8. Select Commit > Commit and Push to commit your changes to Panorama and to push
the changes to Collector Groups that contain the passive HA peer you modified.
STEP 4 | Configure each Log Collector to connect with a Panorama interface.
To support a segmented network, you can connect the Log Collectors in each subnetwork to
separate Panorama interfaces. The interfaces must have Device Management and Device Log
Collection enabled, as described in the previous step.
1. Log in to the Panorama Web Interface of the solitary (non-HA) or active (HA) Panorama
management server.
2. Select Panorama > Managed Collectors and edit the Log Collector.
3. In the Panorama Server IP field, enter the IP address of an interface on the solitary (non-
```
HA) or active (HA) Panorama.
```
4. (HA only) In the Panorama Server IP 2 field, enter the IP address of an interface on the
passive Panorama that will support Device Management and Device Log Collection if
failover occurs on the active Panorama.
5. Click OK to save your changes.
6. Select Commit > Commit and Push to commit your changes to Panorama and to push
the changes to Collector Groups that contain the Log Collector you modified.
7. Perform the following steps on each Dedicated Log Collector:
1. Access the Log Collector CLI by using emulation software such as PuTTY to open a
SSH session to the Log Collector using its MGT interface IP address. When prompted,
log in using Panorama administrator credentials.
2. Run the following commands, where <IPaddress1> is for the solitary (non-HA) or
```
active (HA) Panorama and <IPaddress2> is for the passive Panorama (if applicable).
```
> configure
# set deviceconfig system panorama-server <IPaddress1>
panorama-server-2 <IPaddress2>
# commit
Panorama Getting Started 269 ©2026 Palo Alto Networks, Inc.
Set Up Panorama
```
STEP 5 | (HA only) Configure an interface on the passive Panorama management server to deploy
```
updates in case the active Panorama fails over.
1. Log in to the Panorama Web Interface of the passive Panorama management server.
2. Select Panorama > Setup > Interfaces.
3. Click an Interface Name to edit the interface.
4. Select <interface-name> to enable the interface.
5. Configure one or both of these field sets based on the IP protocols of your network:
• IPv4—IP Address, Netmask, and Default Gateway
• IPv6—IPv6 Address/Prefix Length and Default IPv6 Gateway
6. Select Device Deployment.
7. Click OK to save your changes.
8. Click Commit > Commit to Panorama and Commit your changes.
Panorama Getting Started 270 ©2026 Palo Alto Networks, Inc.
Set Up Panorama
STEP 6 | Configure the interfaces that the Log Collectors will use to collect logs from firewalls and
communicate with other Log Collectors.
Because the MGT interface was configured during initial configuration of the Log
Collectors, you don’t have to configure it again.
1. Log in to the Panorama Web Interface of the solitary (non-HA) or active (HA) Panorama
management server.
2. Select Panorama > Managed Collectors and edit the Log Collector.
3. Select Interfaces and perform the following steps for each interface:
1. Click an interface name to edit that interface.
2. Select <interface-name> to enable the interface.
3. Configure one or both of the following field sets based on the IP protocols of your
network.
IPv4—IP Address, Netmask, and Default Gateway
IPv6—IPv6 Address/Prefix Length and Default IPv6 Gateway
4. Select the functions that the interface supports:
Device Log Collection—Collect logs from firewalls. You can load balance the logging
traffic by enabling multiple interfaces to perform this function.
Collector Group Communication—Communicate with other Log Collectors in the
Collector Group.
5. Click OK to save your changes to the interface.
4. Click OK to save your changes to the Log Collector.
5. Select Commit > Commit and Push to commit your changes to Panorama and to push
the changes to Collector Groups that contain the Log Collectors you modified.
6. Select Panorama > Managed Collectors to verify that the Log Collectors are
synchronized and connected with Panorama.
The Configuration Status column should display InSync and the Run Time Status
column should display connected.
STEP 7 | Configure the firewalls to connect with a Panorama interface.
To support a segmented network, you can connect the firewalls in each subnetwork to
separate Panorama interfaces. The interfaces must have Device Management and Device
Panorama Getting Started 271 ©2026 Palo Alto Networks, Inc.
Set Up Panorama
Log Collection enabled. This step assumes that you use separate templates to configure the
firewalls in separate subnetworks.
In this example deployment, Panorama uses these interfaces to manage the firewalls
but not to collect firewall logs. You specify which Dedicated Log Collectors will collect
firewall logs when you configure Collector Groups.
1. Log in to the Panorama Web Interface of the solitary (non-HA) or active (HA) Panorama
management server.
2. On Panorama, select Device > Setup > Management, select a Template and edit the
Panorama Settings.
3. In the first Panorama Servers field, enter the IP address of an interface on the solitary
```
(non-HA) or active (HA) Panorama.
```
4. (HA only) In the second Panorama Servers field, enter the IP address of an interface on
the passive Panorama that will support device management if failover occurs.
5. Click OK to save your changes.
6. Select Commit > Commit and Push to commit your changes to Panorama and push the
template changes to firewalls.
7. Select Panorama > Managed Devices to verify that the firewalls are synchronized and
connected with Panorama.
The Device State column should display Connected. The Shared Policy and Template
columns should display InSync.
Panorama Getting Started 272 ©2026 Palo Alto Networks, Inc.
Set Up Panorama
Register Panorama and Install Licenses
Where Can I Use This? What Do I Need?
```
• NGFW (Managed by Panorama) • Customer Support Portal
```
• Panorama serial number
Before you can begin using Panorama for centralized management, logging, and reporting, you
are required to register, activate, and retrieve the Panorama device management and support
licenses. Every instance of Panorama requires valid licenses that entitle you to manage firewalls
and obtain support. The firewall device management license enforces the maximum number
of firewalls that Panorama can manage. This license is based on firewall serial numbers, not on
the number of virtual systems on each firewall. The support license enables Panorama software
```
updates and dynamic content updates (for the latest Applications and Threats signatures, as an
```
```
example). Additionally, Panorama virtual appliances on AWS and Azure must be purchased from
```
Palo Alto Networks, and cannot be purchased on the AWS or Azure marketplaces.
After upgrading your Panorama virtual appliance to PAN-OS 8.1, you are prompted if a capacity
license has not been successfully installed or if the total number of firewalls being managed by
Panorama exceeds the device management license. You have 180 days from the date of upgrade
to install a valid device management license if no license has been installed. If the number of
managed firewalls exceeds the device management license, you have 180 days to delete firewalls
to meet the device management license requirements or upgrade your device management
license. All commits fail if a valid device management license is not installed, or the existing
device management license limit is not met, within 180 days of upgrade. To purchase a device
management license, contact your Palo Alto Networks sales representative or authorized reseller.
If you want to use the cloud-based Strata Logging Service, you require a Strata Logging Service
license, in addition to the firewall management license and premium support license. To purchase
licenses, contact your Palo Alto Networks Systems Engineer or reseller.
If you are running an evaluation license for firewall management on your Panorama virtual
appliance and want to apply a Panorama license that you purchased, perform the tasks
Register Panorama and Activate/Retrieve a Firewall Management License when the
Panorama Virtual Appliance is Internet-connected.
• Register Panorama
• Activate a Panorama Support License
• Activate/Retrieve a Firewall Management License when the Panorama Virtual Appliance is
Internet-connected
• Activate/Retrieve a Firewall Management License when the Panorama Virtual Appliance is not
Internet-connected
• Activate/Retrieve a Firewall Management License on the M-Series Appliance
Panorama Getting Started 273 ©2026 Palo Alto Networks, Inc.
Set Up Panorama
Register Panorama
Where Can I Use This? What Do I Need?
```
• NGFW (Managed by Panorama) • Customer Support Portal
```
• Panorama serial number
STEP 1 | Record the Panorama serial number or auth-code and record your Sales Order Number or
Customer ID.
For the auth-code, Sales Order Number, or Customer ID, see the order fulfillment email that
Palo Alto Networks Customer Service sent when you placed your order for Panorama.
For the serial number, the location depends on the model:
• M-Series appliance—Log in to the Panorama web interface and record the Serial # value in
the Dashboard tab, General Information section.
• Panorama virtual appliance—See the order fulfillment email or refer to the serial number
generated when provisioning Panorama using VM Flex licensing.
The Panorama virtual appliance is automatically registered when you allocate a
serial number using VM Flex licensing.
Panorama Getting Started 274 ©2026 Palo Alto Networks, Inc.
Set Up Panorama
```
STEP 2 | Register Panorama in the Palo Alto Networks Customer Support Portal (CSP).
```
The steps depend on whether you already have a login for the Palo Alto Networks CSP.
• If this is the first Palo Alto Networks appliance you are registering and you do not yet have
a CSP login:
1. Go to the Palo Alto Networks CSP.
2. Click Create my account.
3. Enter Your Email Address and respond to the reCAPTCHA prompt.
4. Click Submit after you successfully respond to the reCAPTCHA prompt.
5. Select Register device using Serial Number or Authorization Code and click Submit
6. Complete the fields in the Create Contact Details and Create UserID and Password
sections.
7. Enter the Panorama Device Serial Number or Auth Code.
8. Enter your Sales Order Number or Customer ID.
9. Respond to the reCAPTCHA prompt.
10.Click Submit after you successfully respond to the reCAPTCHA prompt.
• If you already have a CSP login:
1. Log in to the Palo Alto Networks CSP.
2. Click Products > Devices > Register New Device.
You can also Register a Device in the CSP Support Home.
3. Select Register device using Serial Number and click Next.
4. Enter the Panorama Serial Number.
5. Enter the Device Name to apply a name to search for and identify your Panorama.
6. (Optional) Select a Device Tag to group Panorama with any other devices for which you
have selected a device tag.
```
The device tag must first be created at the account level (Products > Devices > Device
```
```
Tag) before it can be selected when you register Panorama.
```
7. If the Panorama management server is not internet-connected, check Device will be
used offline and select the OS Release version.
8. Enter the required Location Information (as indicated by the asterisks) if you have
purchased the 4 hour RMA.
9. Agree and Submit the EULA.
After you see the registration complete message, close the Device Registration dialog.
Activate a Panorama Support License
Where Can I Use This? What Do I Need?
```
• NGFW (Managed by Panorama) • Customer Support Portal
```
Panorama Getting Started 275 ©2026 Palo Alto Networks, Inc.
Set Up Panorama
Where Can I Use This? What Do I Need?
• Registered Panorama management server
Before activating a Panorama support license on a Panorama M-Series appliance or Panorama
virtual appliance, you must Register Panorama.
If the support license expires, Panorama can still manage firewalls and collect logs, but
software and content updates will be unavailable. The software and content versions on
Panorama must be the same as or later than the versions on the managed firewalls, or
else errors will occur. For details, see Panorama, Log Collector, Firewall, and WildFire
Version Compatibility.
STEP 1 | Log in to the Palo Alto Networks customer support portal to activate the auth-code.
1. Select Products > Devices and enter your Panorama serial number to Filter by the Serial
Number.
2. Select the pencil icon in the Action column, select Activate Auth-Code and enter your
support license Authorization Code, and click Agree and Submit.
STEP 2 | Log in to the Panorama web interface, and select Panorama > Support > Activate feature
using authorization code.
STEP 3 | Enter the Authorization Code and click OK.
```
STEP 4 | Verify that the subscription is activated. Check the details (for example, the Expiry Date,
```
```
support Level, and Description) in the Support section of the page.
```
Activate/Retrieve a Firewall Management License when the
Panorama Virtual Appliance is Internet-connected
Where Can I Use This? What Do I Need?
```
• NGFW (Managed by Panorama) • Panorama virtual appliance
```
• Customer Support Portal
• Outbound internet access
• Registered Panorama management server
In order to manage devices on Panorama, you need to activate a firewall management license
generated by PAN-OS. The device management license you activate determines the number
of devices Panorama can manage. Log Collectors and WildFire appliances are not treated
Panorama Getting Started 276 ©2026 Palo Alto Networks, Inc.
Set Up Panorama
as managed devices and do not count toward the number of devices allotted by the device
management license.
Before activating and retrieving a firewall management license on the Panorama virtual appliance,
you must Register Panorama. If you are running an evaluation license and want to apply a
license that you purchased, you must still register and activate/retrieve the purchased license.
Additionally, you must then change the serial number of the Panorama from the evaluation serial
number to the production serial number.
STEP 1 | Log in to the Panorama Web Interface.
STEP 2 | Select Panorama > Setup > Management and edit the General Settings.
```
STEP 3 | Enter the Panorama Serial Number (included in the order fulfillment email) and click OK.
```
STEP 4 | Select Panorama > Licenses to activate or retrieve the firewall management license:
• Retrieve license keys from license server—Panorama automatically retrieves and activates
the firewall management license from the Panorama Update Server.
• Activate feature using authorization code—Enter the firewall management license
authorization code and click OK to activate the license. The authorization code can be
obtained from the order fulfillment email or by logging in to the Palo Alto Networks
Customer Support web site by finding the Panorama management server.
• Manually upload license key—Log in to the Palo Alto Networks Customer Support web site,
find your Panorama management server, and download the firewall management license
key to your local device. After you download the license key, click Choose File to select the
license key and click OK.
STEP 5 | Verify the firewall management license is activated.
The Device Management License section now appears displaying the date the license was
issued, when the license expires, and a description of the firewall management license.
Activate/Retrieve a Firewall Management License when the
Panorama Virtual Appliance is not Internet-connected
Where Can I Use This? What Do I Need?
```
• NGFW (Managed by Panorama) • Panorama virtual appliance
```
• Customer Support Portal
• Registered Panorama management server
Panorama Getting Started 277 ©2026 Palo Alto Networks, Inc.
Set Up Panorama
Before activating and retrieving a firewall management license on the Panorama virtual appliance,
you must Register Panorama. In order to manage devices on Panorama, you will need to activate
a device management license. The device management license you activate will determine the
number of devices Panorama can manage. Log Collectors and WildFire appliances are not treated
as managed devices and will not count toward the number of devices allotted by the device
management license. If you are running an evaluation license and want to apply a license that you
purchased, you must still register and activate/retrieve the purchased license.
After upgrading to PAN-OS 8.1, you will be prompted to retrieve a valid Panorama management
license when you first log in to the Panorama web interface when Panorama has finished
rebooting. To activate or retrieve the valid management license if the Panorama virtual appliance
is offline or unable to reach the Palo Alto Networks update server, you must get the relevant
appliance information for the Panorama virtual appliance and upload it to the Customer Support
web site.
STEP 1 | Log in to the Panorama Web Interface.
```
STEP 2 | (Initial Deployment only) Enter the Panorama Serial Number.
```
1. Select Panorama > Setup > Management and edit the General Settings.
2. Enter the Panorama Serial Number (included in the order fulfillment email) and click OK.
3. Select Commit > Commit to Panorama and Commit your changes.
STEP 3 | Upload the Panorama virtual appliance information to the Customer Support website.
1. On the Retrieve Management License dialogue, click the here link to gather the UUID,
CPUID, Panorama Version and Virtual Platform information. Click Download Link to
Panorama Getting Started 278 ©2026 Palo Alto Networks, Inc.
Set Up Panorama
download a XML file of the required Panorama information that can be uploaded to the
Customer Support Portal.
On initial deployment, may need to log out and back in to the web interface to see the
dialogue.
2. Log in to the Palo Alto Networks Customer Support web site.
3. Click Get Support in the upper right-hand corner.
4. Select Products > Devices, find your Panorama virtual appliance and in the Action
```
column, click the edit icon ( ).
```
5. Select Is the Panorama Offline? and enter the Panorama information gathered in Step 2,
or click Select files... to upload the downloaded XML file.
6. Agree and Submit the EULA.
Panorama Getting Started 279 ©2026 Palo Alto Networks, Inc.
Set Up Panorama
STEP 4 | Install the device management license.
1. In the Actions column, download the device management license.
2. In the Panorama web interface, click Panorama > Licenses and Manually upload license
key.
3. Click Choose file, locate the downloaded device management license key and click OK.
STEP 5 | Confirm that the device management license was successfully uploaded by verify that the
Device Management License displays with the license information.
Activate/Retrieve a Firewall Management License on the M-Series
Appliance
Where Can I Use This? What Do I Need?
```
• NGFW (Managed by Panorama) • M- series hardware appliance
```
• Customer Support Portal
• Registered Panorama management server
In order to manage devices on Panorama, you need to activate a Capacity License. The Capacity
License determines the number of devices Panorama can manage. Log Collectors and WildFire
appliances are not treated as managed devices and do not count toward the number of devices
allotted by the Capacity License.
Before activating and retrieving a Panorama firewall management license on the M-Series
```
appliance:
```
• Register Panorama.
Panorama Getting Started 280 ©2026 Palo Alto Networks, Inc.
Set Up Panorama
• Locate the auth-codes for the product/subscription you purchased. When you placed your
order, Palo Alto Networks Customer Service sent you an email that listed the auth-code
associated with the purchase. If you cannot locate this email, contact Palo Alto Networks
Customer Support to obtain your codes before proceeding.
After you activate and retrieve the license, the Panorama > Licenses page displays the associated
issuance date, expiration date, and the number of firewalls that the license enables Panorama to
manage.
To activate and retrieve the license, the options are:
Use the web interface to activate and retrieve the license.
Select this option if Panorama is ready to connect to the Palo Alto Networks update server
```
(you completed the task Perform Initial Configuration of the M-Series Appliance) but you have
```
not activated the license on the Palo Alto Networks Customer Support web site.
1. Select Panorama > Licenses and click Activate feature using authorization code.
2. Enter the Authorization Code and click OK. Panorama retrieves and activates the
license.
Retrieve the license key from the license server.
```
If Panorama is not ready to connect to the update server (for example, you have not
```
```
completed the initial M-Series appliance setup), you can activate the license on the Support
```
website so that, when Panorama is ready to connect, you can then use the web interface to
retrieve the activated license. The process of retrieving an activated license is faster than the
process of both retrieving and activating.
1. Activate the license on the Palo Alto Networks Customer Support web site.
1. On a host with internet access, use a web browser to access the Palo Alto Networks
Customer Support web site and log in.
2. Select Products > Devices, find your M-Series appliance and, in the Action column,
```
click the edit icon ( ).
```
3. Select Activate Auth-Code, enter the Authorization Code and click Agree and Submit
to activate the license.
2. Configure Panorama to connect to the update server: see Perform Initial Configuration
of the M-Series Appliance.
3. Select Panorama > Licenses and click Retrieve license keys from the license server.
Panorama retrieves the activated license.
Manually upload the license from a host to Panorama. Panorama must have access to that host.
```
If Panorama is set up (you completed the task Perform Initial Configuration of the M-Series
```
```
Appliance) but does not have a connection to the update server, activate the license on the
```
Panorama Getting Started 281 ©2026 Palo Alto Networks, Inc.
Set Up Panorama
Support website, download it to a host that has a connection to the update server, then upload
it to Panorama.
1. Activate and download the license from the Palo Alto Networks Customer Support web
site.
1. On a host with internet access, use a web browser to access the Palo Alto Networks
Customer Support web site and log in.
2. Select Products > Devices, find your M-Series appliance and, in the Action column,
```
click the edit icon ( ).
```
3. Select Activate Auth-Code, enter the Authorization Code and click Agree and Submit
to activate the license.
4. In the Action column, click the download icon and save the license key file to the host.
2. In the Panorama web interface, select Panorama > Licenses, click Manually upload
license key and click Browse.
3. Select the key file you downloaded to the host and click Open.
4. Click OK to upload the activated license key.
Panorama Getting Started 282 ©2026 Palo Alto Networks, Inc.
Set Up Panorama
Install the Panorama Device Certificate
Where Can I Use This? What Do I Need?
```
• NGFW (Managed by Panorama) Device management license
```
Support license
Outbound internet access
```
Customer Support Portal (CSP) account
```
with one of the following user roles:
Super User, Standard User, Limited User,
Threat Researcher, AutoFocus Trial
Role, Group Super User, Group Standard
User, Group Limited User, Group Threat
Researcher, Authorized Support Center
```
(ASC) User, and ASC Full Service User.
```
Panorama superuser role
You must install the device certificate on the Panorama™ management server to use one or more
cloud services. You only need to install a device certificate once. The device certificate has a 90-
day lifetime. The firewall reinstalls the device certificate 15 days before the certificate expires.
In the event Panorama is unable to reinstall the device certificate on its own, you may need to
manually restore an expired device certificate.
To successfully install the device certificate, Panorama must have an outbound internet
```
connection and the following Fully Qualified Domain Names (FQDN) and ports must be allowed
```
on your network.
FQDN Ports
• http://ocsp.paloaltonetworks.com
• http://crl.paloaltonetworks.com
• http://ocsp.godaddy.com
TCP 80
• https://api.paloaltonetworks.com
• http://apitrusted.paloaltonetworks.com
• https://
certificatetrusted.paloaltonetworks.com
• https://certificate.paloaltonetworks.com
TCP 443
• *.gpcloudservice.com TCP 444 and TCP 443
Panorama Getting Started 283 ©2026 Palo Alto Networks, Inc.
Set Up Panorama
M-300 and M-700 appliances automatically install the device certificate when they first
connect to the Palo Alto Networks CSP during the initial registration process. You do not
need to manually install the device certificate for these M-Series appliances.
```
STEP 1 | Generate the One Time Password (OTP).
```
An OTP lifetime is 60 minutes and expires if not used within the 60 minute lifetime.
Panorama may only attempt to retrieve the OTP from the CSP one time. If Panorama
fails for any reason to fetch the OTP, the OTP expires and you must generate a new
OTP.
1. Log in to the Customer Support Portal with a user role that has permission to generate
an OTP.
2. Select Products > Device Certificates and Generate OTP.
3. For the Device Type, select Generate OTP for Panorama and click Next.
4. Select the Panorama Device serial number and Generate OTP.
5. Generate OTP and copy the OTP.
STEP 2 | Log in to the Panorama Web Interface as a Superuser.
A Panorama admin with Superuser access privileges is required to required to apply the OTP
used to install the device certificate on Panorama.
```
STEP 3 | Configure the Network Time Protocol (NTP) server.
```
An NTP server is required to validate the device certification expiration date, ensure the device
certificate does not expire early or become invalid.
1. Select Panorama > Setup > Services.
2. Select NTP and enter the hostname or IP address of the Primary NTP Server.
3. (Optional) Enter a the hostname or IP address of the Secondary NTP Server.
4. (Optional) To authenticate time updates from the NTP server(s), for Authentication
Type, select one of the following for each server.
```
• None (default)—Disables NTP authentication.
```
```
• Symmetric Key—Firewall uses symmetric key exchange (shared secrets) to
```
authenticate time updates.
```
• Key ID—Enter the Key ID (1-65534)
```
```
• Algorithm—Select the algorithm to use in NTP authentication (MDS or SHA1)
```
5. Click OK to save your configuration changes.
6. Select Commit and Commit to Panorama.
STEP 4 | Select Panorama > Setup > Management > Device Certificate Settings and Get certificate.
Panorama Getting Started 284 ©2026 Palo Alto Networks, Inc.
Set Up Panorama
STEP 5 | Enter the One-time Password you generated and click OK.
STEP 6 | Panorama successfully retrieves and installs the certificate.
Panorama Getting Started 285 ©2026 Palo Alto Networks, Inc.
Set Up Panorama
Install the Device Certificate for a Dedicated Log
Collector
Where Can I Use This? What Do I Need?
```
• NGFW (Managed by Panorama) Device management license
```
Support license
Outbound internet access
```
Customer Support Portal (CSP) account
```
with one of the following user roles:
Super User, Standard User, Limited User,
Threat Researcher, AutoFocus Trial
Role, Group Super User, Group Standard
User, Group Limited User, Group Threat
Researcher, Authorized Support Center
```
(ASC) User, and ASC Full Service User.
```
Panorama superuser role
You must install the device certificate on the Dedicated Log Collector to use Device Telemetry.
You only need to install a device certificate once. The device certificate has a 90-day lifetime. The
Dedicated Log Collector reinstalls the device certificate 15 days before the certificate expires. In
the event the Dedicated Log Collector is unable to reinstall the device certificate on its own, you
may need to manually restore an expired device certificate.
To successfully install the device certificate, the Dedicated Log Collector must have an outbound
```
internet connection and the following Fully Qualified Domain Names (FQDN) and ports must be
```
allowed on your network.
You must manually install the device certificate on each Dedicated Log Collector individually.
Installing the device certificate from the Panorama™ management server is not supported.
FQDN Ports
• http://ocsp.paloaltonetworks.com
• http://crl.paloaltonetworks.com
• http://ocsp.godaddy.com
TCP 80
• https://api.paloaltonetworks.com
• http://apitrusted.paloaltonetworks.com
• https://
certificatetrusted.paloaltonetworks.com
• https://certificate.paloaltonetworks.com
TCP 443
Panorama Getting Started 286 ©2026 Palo Alto Networks, Inc.
Set Up Panorama
FQDN Ports
• *.gpcloudservice.com TCP 444 and TCP 443
M-300 and M-700 appliances automatically install the device certificate when they first
connect to the Palo Alto Networks CSP during the initial registration process. You do not
need to manually install the device certificate for these M-Series appliances.
STEP 1 | Log in to the Dedicated Log Collector CLI as a Superuser.
An admin with Superuser access privileges is required to required to apply the OTP used to
install the device certificate on Panorama.
STEP 2 | View the current device certificate status on the Dedicated Log Collector.
admin>show device-certificate status
The Dedicated Log Collector displays one of the following responses:
• Device certificate was never installed—No device certificate found
• Device certificate expired—Current device certificate status: Expired
The response also displays the lifetime of the previous device certificate and the date and
time the last device certificate fetch was attempted.
• Device certificate fetch failed—Response displays the last time the device certificate fetch
was attempted.
```
STEP 3 | Generate the One Time Password (OTP).
```
An OTP lifetime is 60 minutes and expires if not used within the 60 minute lifetime.
The Dedicated Log Collector may only attempt to retrieve the OTP from the CSP one
time. If the Dedicated Log Collector fails for any reason to fetch the OTP, the OTP
expires and you must generate a new OTP.
1. Log in to the Customer Support Portal with a user role that has permission to generate
an OTP.
2. Select Products > Device Certificates and Generate OTP.
3. For the Device Type, select Generate OTP for Panorama and click Next.
4. Select the Panorama Device serial number and Generate OTP.
5. Generate OTP and copy the OTP.
Panorama Getting Started 287 ©2026 Palo Alto Networks, Inc.
Set Up Panorama
```
STEP 4 | Configure the Network Time Protocol (NTP) server.
```
An NTP server is required to validate the device certification expiration date, ensure the device
certificate does not expire early or become invalid.
1. Log in to the Dedicated Log Collector CLI as a Superuser.
An admin with Superuser access privileges is required to required to apply the OTP used
to install the device certificate on Panorama.
2. configure the NTP server.
admin>configure
admin#set deviceconfig system ntp-servers primary-ntp-server
ntp-server-address <ip_address>
admin#set deviceconfig system ntp-servers secondary-ntp-server
ntp-server-address <ip_address>
admin>commit
admin>exit
STEP 5 | Install the device certificate.
admin>request certificate fetch otp <otp_value>
STEP 6 | Verify the device certificate successfully installed.
admin> show device-certificate status
A successful device certificate installation displays the following response:
Device Certificate information:
Current device certificate status: Valid
Not valid before: 2022/11/30 15:17:47 PST
Not valid after: 2023/02/28 15:17:47 PST
Last fetched timestamp: 2022/11/30 15:29:42 PST
Last fetched status: success
Last fetched info: Successfully fetched Device Certificate
Panorama Getting Started 288 ©2026 Palo Alto Networks, Inc.
Set Up Panorama
Access and Navigate Panorama Management Interfaces
Where Can I Use This? What Do I Need?
```
• NGFW (Managed by Panorama) This is a core network security feature and
```
does not have prerequisites
Panorama provides three management interfaces:
• Web interface—The Panorama web interface has a look and feel similar to the firewall web
interface. If you are familiar with the latter, you can easily navigate, complete administrative
tasks, and generate reports from the Panorama web interface. This graphical interface enables
you to access Panorama using HTTPS and it is the best way to perform administrative tasks.
See Log in to the Panorama Web Interface and Navigate the Panorama Web Interface. If you
need to enable HTTP access to Panorama, edit the Management Interface Settings on the
Panorama > Setup > Management tab.
```
• Command line interface (CLI)—The CLI is a no-frills interface that allows you to type
```
commands in rapid succession to complete a series of tasks. The CLI supports two command
modes—operational and configuration—and each has its own hierarchy of commands and
statements. When you become familiar with the nesting structure and the syntax for the
commands, the CLI enables quick response times and administrative efficiency. See Log in to
the Panorama CLI.
• XML API—The XML-based API is provided as a web service that is implemented using HTTP/
HTTPS requests and responses. It enables you to streamline your operations and integrate with
existing, internally developed applications and repositories. For details on using the Panorama
API, refer to the PAN-OS and Panorama XML API Usage Guide.
Log in to the Panorama Web Interface
Where Can I Use This? What Do I Need?
```
• NGFW (Managed by Panorama) This is a core network security feature and
```
does not have prerequisites
The Panorama web interface for the M-600 appliance in Panorama or Management
Only mode is inaccessible if you have 6 or more concurrent API calls. A 504 Gateway
Timeout error is displayed when you try to log in to the Panorama web interface of an
M-600 appliance with 6 or more concurrent API calls.
STEP 1 | Launch an internet browser and enter the Panorama IP address using a secure connection
```
(https://<IP address>).
```
Panorama Getting Started 289 ©2026 Palo Alto Networks, Inc.
Set Up Panorama
STEP 2 | Log in to Panorama according to the type of authentication used for your account. If logging
in to Panorama for the first time, use the default value admin for your username and
password.
```
• SAML—Click Use Single Sign-On (SSO). If Panorama performs authorization (role
```
```
assignment) for administrators, enter your Username and Continue. If the SAML identity
```
```
provider (IdP) performs authorization, Continue without entering a Username. In both
```
cases, Panorama redirects you to the IdP, which prompts you to enter a username and
password. After you authenticate to the IdP, the Panorama web interface displays.
• Any other type of authentication—Enter your user Name and Password. Read the login
banner and select I Accept and Acknowledge the Statement Below if the login page has the
banner and check box. Then click Login.
STEP 3 | Read and Close any messages of the day.
Navigate the Panorama Web Interface
Where Can I Use This? What Do I Need?
```
• NGFW (Managed by Panorama) This is a core network security feature and
```
does not have prerequisites
Use the Panorama web interface to configure Panorama, manage and monitor firewalls, Log
Collectors, and WildFire appliances and appliance clusters, and access the web interface of each
firewall through the Context drop-down. Refer to the Panorama online help for details on the
options and fields in each web interface tab. The following is an overview of the tabs:
Tab Description
Dashboard View general information about the Panorama model and network
access settings. This tab includes widgets that display information
about applications, logs, system resources, and system settings.
ACC View the overall risk and threat level on the network, based on
information that Panorama gathered from the managed firewalls.
Monitor View and manage logs and reports.
Device Groups > Policies Create centralized policy rules and apply them to multiple
firewalls/device groups.
You must add a device group for this tab to display.
Device Groups > Objects Define policy objects that policy rules can reference and that
managed firewalls/device groups can share.
You must add a device group for this tab to display.
Panorama Getting Started 290 ©2026 Palo Alto Networks, Inc.
Set Up Panorama
Tab Description
Templates > Network Configure network setting, such as network profiles, and apply
them to multiple firewalls.
You must add a template for this tab to display.
Templates > Device Configure device settings, such as server profiles and admin roles,
and apply them to multiple firewalls.
You must add a template for this tab to display.
Panorama Configure Panorama, manage licenses, set up high availability,
access software updates and security alerts, manage administrative
access, and manage the deployed firewalls, Log Collectors, and
WildFire appliances and appliance clusters.
Log in to the Panorama CLI
Where Can I Use This? What Do I Need?
```
• NGFW (Managed by Panorama) This is a core network security feature and
```
does not have prerequisites
You can log in to the Panorama CLI using a serial port connection or remotely using a Secure Shell
```
(SSH) client.
```
Use SSH to log in to the Panorama CLI.
The same instructions apply to an M-Series appliance in Log Collector mode.
Optionally, you can Configure an Administrator with SSH Key-Based
Authentication for the CLI.
1. Ensure the following prerequisites are met:
• You have a computer with network access to Panorama.
• You know the Panorama IP address.
• The Management interface supports SSH, which is the default setting. If an
administrator disabled SSH and you want to re-enable it: select Panorama > Setup
Panorama Getting Started 291 ©2026 Palo Alto Networks, Inc.
Set Up Panorama
> Interfaces, click Management, select SSH, click OK, select Commit > Commit to
Panorama, and Commit your changes to the Panorama configuration.
2. To access the CLI using SSH:
1. Enter the Panorama IP address in the SSH client and use port 22.
2. Enter your administrative access credentials when prompted. After you log in, the
message of the day displays, followed by the CLI prompt in Operational mode. For
```
example:
```
admin@ABC_Sydney>
Use a serial port connection to log in to the Panorama CLI.
1. Make sure that you have the following:
• A null-modem serial cable that connects Panorama to a computer with a DB-9 serial
port
• A terminal emulation program running on the computer
2. Use the following settings in the terminal emulation software to connect: 9600 baud; 8
```
data bits; 1 stop bit; No parity; No hardware flow control.
```
3. Enter your administrative access credentials when prompted. After you log in, the
message of the day displays, followed by the CLI prompt in Operational mode.
Change to Configuration mode.
To switch to Configuration mode, enter the following command at the prompt:
admin@ABC_Sydney> configure
The prompt changes to admin@ABC_Sydney#.
##### Panorama Getting Started 292 ©2026 Palo Alto Networks, Inc.