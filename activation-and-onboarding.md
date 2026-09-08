

## Activation & Onboarding
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
2025-2026   Palo   Alto   Networks,   Inc.   Palo   Alto   Networks   is   a   registered   trademark   of   Palo
Alto  Networks.  A  list  of  our  trademarks  can  be  found  at  www.paloaltonetworks.com/company/
trademarks.html. All other marks mentioned herein may be trademarks of their respective companies.
## Last Revised
## January 10, 2026
## Activation & Onboarding2
## ©
## 2026 Palo Alto Networks, Inc.

Table of Contents
Advanced DNS Security License Options.................................................... 5
Advanced DNS Security Prerequisites..........................................................7
Activate Advanced DNS Security.................................................................. 9
Enable  DNS  Security....................................................................................... 11
Enable Advanced DNS Security................................................................... 27
Activate Advanced DNS Security Resolver...............................................41
Enable Advanced DNS Security Resolver..................................................53
## Activation & Onboarding3
## ©
## 2026 Palo Alto Networks, Inc.

Table of Contents
## Activation & Onboarding4
## ©
## 2026 Palo Alto Networks, Inc.

Advanced DNS Security License
## Options
Where Can I Use This?What Do I Need?
•Prisma Access
## •NGFW
•VM-Series
•CN-Series
A Palo Alto Networks DNS Security
subscription; this can include:
Advanced DNS Security Resolver
## License
Advanced DNS Security License (for
enhanced feature support)
DNS Security License
The Advanced DNS Security and DNS
Security licenses also require the
installation of:
•Advanced Threat Prevention License
•Threat Prevention License
Powered by Precision AI, Palo Alto Networks DNS Security subscriptions provide essential DNS
threat protection. These are available primarily in two tiers for DNS protection: the standard DNS
Security subscription and the more robust Advanced DNS Security subscription. Both are Cloud-
Delivered Security Services (CDSS) that integrate directly with your Next-Generation Firewalls
and Prisma Access.
As a new standalone offering, the Advanced DNS Security Resolver provides a newer, cloud-
delivered offering that shiftsAdvanced DNS Security from a firewall function to a service-based
architecture.
All Advanced DNS Security and DNS Security subscriptions (not including the Advanced
DNS Security Resolver) require the installation of a valid Advanced Threat Prevention
or Threat Prevention license, as it relies on the subsystems contained within those
subscriptions.
•DNS Security—The base subscription provides foundational protection by checking DNS
Requests and identifying malicious domains against a cloud-based database of known domains.
The DNS Security license is EOS (end-of-sale) and no longer available.
•Advanced DNS Security—Introduced to combat more sophisticated, evasive threats, this
tier includes everything in the standard subscription, but also uses Precision AI and machine
learning to inspect changes in DNS responses to detect for various types of DNS hijacking in
real-time.
## 5

Advanced DNS Security License Options
•Advanced DNS Security Resolver—The Advanced DNS Resolver service provides cloud-based
DNS resolution and inspection capabilities. This service allows you to forward your internet-
bound DNS requests to a secure resolver managed by Palo Alto Networks, offering both
domain-to-IP resolution and protection against DNS-based threats based on the Advanced
DNS Security cloud service.
The Advanced DNS Security Resolver licensing is based on a Per User Per Year (PUPY)
model.
•Daily Request Limit: Each user is allocated 5,000 DNS requests per day.
•Usage Alerts: To provide visibility into service usage, the following occur when
usage limits have been exceeded:
•Initial Warning: If daily usage exceeds your number of user licenses, a warning
notification is displayed.
•Action for Persistent Usage: If elevated usage continues, a banner indicating the
overage will be displayed, and account team will be notified.
## Activation & Onboarding6
## ©
## 2026 Palo Alto Networks, Inc.

Advanced DNS Security
## Prerequisites
Where Can I Use This?What Do I Need?
•Prisma Access
## •NGFW
•VM-Series
•CN-Series
A Palo Alto Networks DNS Security
subscription; this can include:
Advanced DNS Security Resolver
## License
Advanced DNS Security License (for
enhanced feature support)
DNS Security License
The Advanced DNS Security and DNS
Security licenses also require the
installation of:
•Advanced Threat Prevention License
•Threat Prevention License
Palo Alto Networks Advanced DNS Security subscriptions may have certain dependencies based
on which subscription you have purchased.
•DNS Security
•Minimum PAN-OS version: PAN-OS 9.0 and later.
•An active Advanced Threat Prevention or Threat Prevention License must be present on the
device where the DNS Security license is located.
•Advanced DNS Security
•Minimum PAN-OS version: PAN-OS 11.2 and later. Operating an earlier version will only
allow base DNS Security features to function.
•While all features of the base DNS Security features are included with the Advanced DNS
Security license, it is delivered through the base DNS Security license; as such, both licenses
appear in the PAN-OS license list. In the case of Prisma Access, it is generally included as
part of the Prisma Access bundle and shows as a single entry under Security Services: DNS
## Security.
The DNS Security license requirement for an active Advanced Threat Prevention
or Threat Prevention License is carried over to Advanced DNS Security due to the
presence of the base license.
•Advanced DNS Security Resolver—As the Advanced DNS Security Resolver service sends all
its logs to Palo Alto Networks cloud-based logging service, the tenant where you activate the
license must be configured to use Strata Logging Service (formerly Cortex Data Lake). As this is
## 7

Advanced DNS Security Prerequisites
a functional requirement, the Advanced DNS Security Resolver service includes SLS with 1 yr
log retention.
As a standalone service, the Advanced DNS Security Resolver does not require any other Palo
Alto Networks services (e.g. CDSS subscriptions, NGFW, SASE, etc) for operation. However,
it does provide integration with Prisma Access Agent, a next-generation endpoint client
that enables secure connectivity and consistent security policies for hybrid, remote, and on-
premises users.
## Activation & Onboarding8
## ©
## 2026 Palo Alto Networks, Inc.

Activate Advanced DNS Security
Where Can I Use This?What Do I Need?
•Prisma Access
## •NGFW
•VM-Series
•CN-Series
A Palo Alto Networks DNS Security
subscription; this can include:
Advanced DNS Security Resolver
## License
Advanced DNS Security License (for
enhanced feature support)
DNS Security License
The Advanced DNS Security and DNS
Security licenses also require the
installation of:
•Advanced Threat Prevention License
•Threat Prevention License
You must activate your DNS Security or Advanced DNS Security subscription to enable your
organization to identify and block sophisticated DNS-layer threats, such as DNS tunneling, DGA-
based malware, and malicious domains. Activation for these integrated subscriptions is performed
by applying the authorization codes to your NGFW. These procedures assume you already have
all the required license auth codes necessary for activation.
If your subscription was purchased as part of a Prisma Access bundle, the Advanced DNS Security
features are automatically included. In these cases, no separate activation action is required for
the Advanced DNS Security component after you activate the primary bundle license, as is typical
for Prisma Access
You must install the device certificate on your NGFW before you can activate your Advanced
DNS Security license. Palo Alto Networks uses the device certificate to authentication the NGFW
and Prisma Access to allow them to connect to the Advanced DNS Security cloud service. Palo
Alto Networks requires the device certificate to use any Palo Alto Networks cloud service.
Palo Alto Networks begins enforcement of device certificate authentication for Advanced
DNS Security on February 11, 2026.
If you have NGFW with an active Advanced DNS Security license, you must install the
device certificate on your NGFW by March 13 2026 (30 days).
After this date, your NGFW will no longer be able to connect to the Advanced DNS
Security cloud service.
•Standalone NGFW and NGFW (Managed by Strata Cloud Manager)—Install the device
certificate on every NGFW access the Advanced DNS Security service.
## 9

Activate Advanced DNS Security
•NGFW (Managed by Panorama)—Install the device certificate for multiple NGFW from your
## Panorama
## ®
management server.
•Prisma Access (Managed by Panorama or Strata Cloud Manager)—Device certificate installed
by default. No action required.
After you install the device certificate on your NGFW, you can continue to activate the Advanced
DNS Security license:
•NGFW— The base DNS Security and Advanced DNS Security subscriptions are activated
similarly on NGFW to other cloud service subscriptions. Refer to Activate Subscription
Licenses for more information.
•Prisma Access— Prisma Access typically includes cloud service subscription-based features as
part of a bundle solution. As a result, these subscriptions are automatically enabled when you
activate your Prisma Access license.
For more information on activating Prisma Access, refer to: Activate Your Prisma Access
## License.
## Activation & Onboarding10
## ©
## 2026 Palo Alto Networks, Inc.

Enable DNS Security
Where Can I Use This?What Do I Need?
•Prisma Access
## •NGFW
•VM-Series
•CN-Series
Advanced DNS Security License (for
enhanced feature support) or DNS
## Security License
Advanced Threat Prevention or Threat
## Prevention License
To enable DNS Security, you must create (or modify) an Anti-Spyware security profile to access
the DNS Security service, configure the log severity and policy settings for the DNS signature
category (or categories), and then attach the profile to a security policy rule.
•Strata Cloud Manager
•PAN-OS & Panorama
## 11

Enable DNS Security
Enable DNS Security (Strata Cloud Manager)
STEP 1 |Use the credentials associated with your Palo Alto Networks support account and log in to
the Strata Cloud Manager on the hub.
STEP 2 |Verify that a DNS Security and a Threat Prevention (or Advanced Threat Prevention) license
is active. Select Manage > Configuration > NGFW and Prisma Access > Overview and click
the license usage terms link in the License panel. You should see green check marks next to
the following security services: Antivirus, Anti-Spyware, Vulnerability Protection, and DNS
## Security.
STEP 3 |Verify that a DNS Security and a Threat Prevention (or Advanced Threat Prevention)
license is active. Select Configuration > NGFW and Prisma Access > Overview and click
the license usage terms link in the License panel. You should see green check marks next to
the following security services: Antivirus, Anti-Spyware, Vulnerability Protection, and DNS
## Security.
STEP 4 |Verify that the paloalto-dns-security App-ID in your security policy is configured to enable
traffic from the DNS security cloud security service.
If your firewall deployment routes your management traffic though an Internet-
facing perimeter firewall configured to enforce App-ID security policies, you must
allow the App-IDs on the perimeter firewall; failure to do so will prevent DNS security
connectivity.
## Activation & Onboarding12
## ©
## 2026 Palo Alto Networks, Inc.

Enable DNS Security
STEP 5 |Configure DNS Security signature policy settings to send malicious DNS queries to the
defined sinkhole.
If you use an external dynamic list as a domain allow list, it does not have precedence
over the DNS Security domain policy actions. As a result, when there is a domain
match to an entry in the EDL and a DNS Security domain category, the action
specified under DNS Security is still applied, even when the EDL is explicitly configured
with an action of Allow. If you want to add DNS domain exceptions, add them to the
DNS Domain/FQDN Allow List located in the DNS Exceptions tab.
## 1.
Select Manage > Configuration > NGFW and Prisma Access > Security Services > DNS
## Security.
## 2.
Select Configuration > NGFW and Prisma Access > Security Services > DNS Security.
## 3.
Create or modify an existing DNS Security profile.
## 4.
Name the profile and, optionally, provide a description.
## 5.
In the DNS Categories section, beneath the DNS Security heading, there are individually
configurable DNS signature sources, which allow you to define separate policy actions as
well as the packet capture setting.
Palo Alto Networks recommends using the default action setting for all signature
sources to ensure optimum coverage as well as to assist with incidence response
and remediation. For more information about the best practices for configuring
your DNS Security settings, refer to Best Practices for Securing Your Network
from Layer 4 and Layer 7 Evasions.
•Select an action to be taken when DNS lookups are made to known malware sites for
the DNS Security signature source. The options are alert, allow, block, or sinkhole.
Palo Alto Networks recommends setting the action to sinkhole.
•You can fully bypass DNS traffic inspection by configuring a policy action of Allow
with a corresponding log severity of None for each DNS signature source.
•In the Packet Capture drop-down, select single-packet to capture the first packet of
the session or extended-capture to set between 1-50 packets. You can then use the
packet captures for further analysis.
## 6.
In the DNS Sinkhole Settings section, verify that a valid Sinkhole address is present.
For your convenience, the default setting (pan-sinkhole-default-ip) is set to access a
## Activation & Onboarding13
## ©
## 2026 Palo Alto Networks, Inc.

Enable DNS Security
Palo Alto Networks sinkhole server. Palo Alto Networks can automatically refresh this
address through updates.
Sinkhole forges a response to a DNS query for domains that match the DNS
category configured for a sinkhole action to the specified sinkhole server, to
assist in identifying compromised hosts. When the default sinkhole FQDN is
used, the firewall sends the CNAME record as a response to the client, with
the expectation that an internal DNS server will resolve the CNAME record,
allowing malicious communications from the client to the configured sinkhole
server to be logged and readily identifiable. However, if clients are in networks
without an internal DNS server, or are using software or tools that cannot
be properly resolve a CNAME into an A record response, the DNS request is
dropped, resulting in incomplete traffic log details that are crucial for threat
analysis. In these instances, you should use the following sinkhole IP address:
## (198.135.184.22).
If you want to modify the Sinkhole IPv4 or Sinkhole IPv6 address to a local server on
your network or to a loopback address, see Configure the Sinkhole IP Address to a Local
Server on Your Network.
## 7.
(Optional) Block the specified DNS resource record types record types used to exchange
keying information during the encryption of the client hello in the subsequent TLS
## Activation & Onboarding14
## ©
## 2026 Palo Alto Networks, Inc.

Enable DNS Security
connection. The following DNS RR types are available: SVCB (64), HTTPS (65), and ANY
## (255).
•While it is not necessary to block ECH in order to enable DNS Security over
DoH, Palo Alto Networks currently recommends blocking all DNS record
types used by ECH for optimum security. To block all DNS record types, you
must select each of the Block DNS Record Types: SVCB, HTTPS, and ANY.
•Type 64 and type 65 resource record standards are still in flux (in a draft
state) and are subject to change. For more information on DNS SVCB and
HTTPS RRs, refer to: Service binding and parameter specification via the
DNS (DNS SVCB and HTTPS RRs) as defined by the IETF.
## 8.
Save the DNS Security profile.
STEP 6 |Attach the DNS Security profile to a Security policy rule.
STEP 7 |Test that the policy action is enforced.
## 1.
Access the DNS Security test domains to verify that the policy action for a given threat
type is being enforced.
## 2.
To monitor the activity:
1.View the activity logs and search for the URL Domain with a sinkholed action to view
the log entries for the test domain you accessed.
STEP 8 |Optional—Create a decryption policy rule to decrypt DNS-over-TLS / port 853 traffic. The
decrypted DNS payload can then be processed using the DNS Security profile configuration
containing your DNS policy settings. When DNS-over-TLS traffic is decrypted, the resulting
DNS requests in the threat logs will appears as a conventional dns-base application with a
source port of 853.
STEP 9 |For other monitoring options, see Monitor DNS Security Subscription Services
## Activation & Onboarding15
## ©
## 2026 Palo Alto Networks, Inc.

Enable DNS Security
Enable DNS Security (NGFW (Managed by PAN-OS or
## Panorama))
PAN-OS 10.0 and later supports individually configurable DNS signature sources, which enables
you to define separate policy actions as well as a log severity level for a given signature source.
This enables you to create discrete, precise security actions based on the threat posture of a
domain type according to your network security protocols. The DNS signature source definitions
are extensible through PAN-OS content releases so, when new DNS Security analyzers are
introduced, you are able to create specific policies based on the nature of the threat. Upon
upgrade to PAN-OS 10.0 and later, the DNS Security source gets redefined into new categories to
provide extended granular controls; as a result, the new categories will overwrite the previously
defined action and acquire default settings. Make sure to reapply any sinkhole, log severity, and
packet captures settings appropriate for the newly defined DNS Security Categories.
•PAN-OS 11.0 and later
•PAN-OS 10.x
## •PAN-OS 9.1
Enable DNS Security (PAN-OS 11.0 and Later)
STEP 1 |Log in to the NGFW.
STEP 2 |To take advantage of DNS Security, you must have an active DNS Security and Threat
Prevention (or Advanced Threat Prevention) subscription.
Verify that you have the necessary subscriptions. To verify which subscriptions that you
currently have licenses for, select Device > Licenses and verify that the appropriate licenses
display and have not expired.
STEP 3 |Verify that the paloalto-dns-security App-ID in your security policy is configured to enable
traffic from the DNS security cloud security service.
If your firewall deployment routes your management traffic though an Internet-
facing perimeter firewall configured to enforce App-ID security policies, you must
allow the App-IDs on the perimeter firewall; failure to do so will prevent DNS security
connectivity.
## Activation & Onboarding16
## ©
## 2026 Palo Alto Networks, Inc.

Enable DNS Security
STEP 4 |Configure DNS Security signature policy settings to send malicious DNS queries to the
defined sinkhole.
If you use an external dynamic list as a domain allow list, it does not have precedence
over the DNS Security domain policy actions. As a result, when there is a domain
match to an entry in the EDL and a DNS Security domain category, the action
specified under DNS Security is still applied, even when the EDL is explicitly configured
with an action of Allow. If you want to add DNS domain exceptions, add them to the
DNS Domain/FQDN Allow List located in the DNS Exceptions tab.
## 1.
Select Objects > Security Profiles > Anti-Spyware.
## 2.
Create or modify an existing profile, or select one of the existing default profiles and
clone it.
## 3.
Name the profile and, optionally, provide a description.
## 4.
Select the DNS Policies tab.
## 5.
In the Signature Source column, beneath the DNS Security heading, there are
individually configurable DNS signature sources, which allow you to define separate
policy actions as well as a log severity level.
Palo Alto Networks recommends changing your default DNS Policies settings for
signature sources to ensure optimum coverage as well as to assist with incidence
response and remediation. Follow the best practices for configuring your DNS
Security settings as outlined in the Best Practices for Securing Your Network
from Layer 4 and Layer 7 Evasions.
•Specify the log severity level that is recorded when the firewall detects a domain
matching a DNS signature. For more information about the various log severity levels,
refer to Threat Severity Levels.
•Select an action to be taken when DNS lookups are made to known malware sites for
the DNS Security signature source. The options are default, allow, block, or sinkhole.
Verify that the action is set to sinkhole.
•You can fully bypass DNS traffic inspection by configuring a policy action of Allow
with a corresponding log severity of None for each DNS signature source.
•In the Packet Capture drop-down, select single-packet to capture the first packet of
the session or extended-capture to set between 1-50 packets. You can then use the
packet captures for further analysis.
## 6.
In the DNS Sinkhole Settings section, verify that Sinkhole is enabled. For your
convenience, the default Sinkhole address (sinkhole.paloaltonetworks.com) is set to
## Activation & Onboarding17
## ©
## 2026 Palo Alto Networks, Inc.

Enable DNS Security
access a Palo Alto Networks server. Palo Alto Networks can automatically refresh this
address through content updates.
Sinkhole forges a response to a DNS query for domains that match the DNS
category configured for a sinkhole action to the specified sinkhole server, to
assist in identifying compromised hosts. When the default sinkhole FQDN
(sinkhole.paloaltonetworks.com) is used, the firewall sends the CNAME record
as a response to the client, with the expectation that an internal DNS server will
resolve the CNAME record, allowing malicious communications from the client
to the configured sinkhole server to be logged and readily identifiable. However,
if clients are in networks without an internal DNS server, or are using software
or tools that cannot be properly resolve a CNAME into an A record response, the
DNS request is dropped, resulting in incomplete traffic log details that are crucial
for threat analysis. In these instances, you should use the following sinkhole IP
address: (198.135.184.22).
If you want to modify the Sinkhole IPv4 or Sinkhole IPv6 address to a local server on
your network or to a loopback address, see Configure the Sinkhole IP Address to a Local
Server on Your Network.
## 7.
(Optional) Block the specified DNS resource record types record types used to exchange
keying information during the encryption of the client hello in the subsequent TLS
## Activation & Onboarding18
## ©
## 2026 Palo Alto Networks, Inc.

Enable DNS Security
connection. The following DNS RR types are available: SVCB (64), HTTPS (65), and ANY
## (255).
•While it is not necessary to block ECH in order to enable DNS Security over
DoH, Palo Alto Networks currently recommends blocking all DNS record
types used by ECH for optimum security. To block all DNS record types, you
must select each of the Block DNS Record Types: SVCB, HTTPS, and ANY.
•Type 64 and type 65 resource record standards are still in flux (in a draft
state) and are subject to change. For more information on DNS SVCB and
HTTPS RRs, refer to: Service binding and parameter specification via the
DNS (DNS SVCB and HTTPS RRs) as defined by the IETF.
## 8.
Click OK to save the Anti-Spyware profile.
STEP 5 |Attach the Anti-Spyware profile to a Security policy rule.
## 1.
## Select Policies > Security.
## 2.
Select or create a Security Policy Rule.
## 3.
On the Actions tab, select the Log at Session End check box to enable logging.
## 4.
In the Profile Setting section, click the Profile Type drop-down to view all Profiles. From
the Anti-Spyware drop-down and select the new or modified profile.
## 5.
Click OK to save the policy rule.
## Activation & Onboarding19
## ©
## 2026 Palo Alto Networks, Inc.

Enable DNS Security
STEP 6 |Test that the policy action is enforced.
## 1.
Access the DNS Security test domains to verify that the policy action for a given threat
type is being enforced.
## 2.
To monitor the activity on the firewall:
1.Select ACC and add a URL Domain as a global filter to view the Threat Activity and
Blocked Activity for the domain you accessed.
2.Select Monitor > Logs > Threat and filter by (action eq sinkhole) to view logs
on sinkholed domains.
3.For more monitoring options, see Monitor DNS Security Subscription Services
STEP 7 |Optional—Create a decryption policy rule to decrypt DNS-over-TLS / port 853 traffic. The
decrypted DNS payload can then be processed using the Anti-Spyware profile configuration
containing your DNS policy settings. When DNS-over-TLS traffic is decrypted, the resulting
DNS requests in the threat logs will appears as a conventional dns-base application with a
source port of 853.
STEP 8 |Optional—See Infected Hosts that Attempted to Connect to a Malicious Domain
Enable DNS Security (PAN-OS 10.x)
STEP 1 |Log in to the NGFW.
STEP 2 |To take advantage of DNS Security, you must have an active DNS Security and Threat
Prevention (or Advanced Threat Prevention) subscription.
Verify that you have the necessary subscriptions. To verify which subscriptions that you
currently have licenses for, select Device > Licenses and verify that the appropriate licenses
display and have not expired.
STEP 3 |Verify that the paloalto-dns-security App-ID in your security policy is configured to enable
traffic from the DNS security cloud security service.
If your firewall deployment routes your management traffic though an Internet-
facing perimeter firewall configured to enforce App-ID security policies, you must
allow the App-IDs on the perimeter firewall; failure to do so will prevent DNS security
connectivity.
## Activation & Onboarding20
## ©
## 2026 Palo Alto Networks, Inc.

Enable DNS Security
STEP 4 |Configure DNS Security signature policy settings to send malicious DNS queries to the
defined sinkhole.
If you use an external dynamic list as a domain allow list, it does not have precedence
over the DNS Security domain policy actions. As a result, when there is a domain
match to an entry in the EDL and a DNS Security domain category, the action
specified under DNS Security is still applied, even when the EDL is explicitly configured
with an action of Allow. If you want to add DNS domain exceptions, add them to the
DNS Domain/FQDN Allow List located in the DNS Exceptions tab.
## 1.
Select Objects > Security Profiles > Anti-Spyware.
## 2.
Create or modify an existing profile, or select one of the existing default profiles and
clone it.
## 3.
Name the profile and, optionally, provide a description.
## 4.
Select the DNS Policies tab.
## 5.
In the Signature Source column, beneath the DNS Security heading, there are
individually configurable DNS signature sources, which allow you to define separate
policy actions as well as a log severity level.
Palo Alto Networks recommends changing your default DNS Policies settings for
signature sources to ensure optimum coverage as well as to assist with incidence
response and remediation. Follow the best practices for configuring your DNS
Security settings as outlined in the Best Practices for Securing Your Network
from Layer 4 and Layer 7 Evasions.
•Specify the log severity level that is recorded when the firewall detects a domain
matching a DNS signature. For more information about the various log severity levels,
refer to Threat Severity Levels.
•Select an action to be taken when DNS lookups are made to known malware sites for
the DNS Security signature source. The options are default, allow, block, or sinkhole.
Verify that the action is set to sinkhole.
•You can fully bypass DNS traffic inspection by configuring a policy action of Allow
with a corresponding log severity of None for each DNS signature source.
•In the Packet Capture drop-down, select single-packet to capture the first packet of
the session or extended-capture to set between 1-50 packets. You can then use the
packet captures for further analysis.
## 6.
In the DNS Sinkhole Settings section, verify that Sinkhole is enabled. For your
convenience, the default Sinkhole address (sinkhole.paloaltonetworks.com) is set to
## Activation & Onboarding21
## ©
## 2026 Palo Alto Networks, Inc.

Enable DNS Security
access a Palo Alto Networks server. Palo Alto Networks can automatically refresh this
address through content updates.
Sinkhole forges a response to a DNS query for domains that match the DNS
category configured for a sinkhole action to the specified sinkhole server, to
assist in identifying compromised hosts. When the default sinkhole FQDN
(sinkhole.paloaltonetworks.com) is used, the firewall sends the CNAME record
as a response to the client, with the expectation that an internal DNS server will
resolve the CNAME record, allowing malicious communications from the client
to the configured sinkhole server to be logged and readily identifiable. However,
if clients are in networks without an internal DNS server, or are using software
or tools that cannot be properly resolve a CNAME into an A record response, the
DNS request is dropped, resulting in incomplete traffic log details that are crucial
for threat analysis. In these instances, you should use the following sinkhole IP
address: (198.135.184.22).
If you want to modify the Sinkhole IPv4 or Sinkhole IPv6 address to a local server on
your network or to a loopback address, see Configure the Sinkhole IP Address to a Local
Server on Your Network.
## 7.
Click OK to save the Anti-Spyware profile.
## Activation & Onboarding22
## ©
## 2026 Palo Alto Networks, Inc.

Enable DNS Security
STEP 5 |Attach the Anti-Spyware profile to a Security policy rule.
## 1.
## Select Policies > Security.
## 2.
Select or create a Security Policy Rule.
## 3.
On the Actions tab, select the Log at Session End check box to enable logging.
## 4.
In the Profile Setting section, click the Profile Type drop-down to view all Profiles. From
the Anti-Spyware drop-down and select the new or modified profile.
## 5.
Click OK to save the policy rule.
STEP 6 |Test that the policy action is enforced.
## 1.
Access the DNS Security test domains to verify that the policy action for a given threat
type is being enforced.
## 2.
To monitor the activity on the firewall:
1.Select ACC and add a URL Domain as a global filter to view the Threat Activity and
Blocked Activity for the domain you accessed.
2.Select Monitor > Logs > Threat and filter by (action eq sinkhole) to view logs
on sinkholed domains.
3.For more monitoring options, see Monitor DNS Security Subscription Services
STEP 7 |Optional—Create a decryption policy rule to decrypt DNS-over-TLS / port 853 traffic. The
decrypted DNS payload can then be processed using the Anti-Spyware profile configuration
containing your DNS policy settings. When DNS-over-TLS traffic is decrypted, the resulting
DNS requests in the threat logs will appears as a conventional dns-base application with a
source port of 853.
STEP 8 |Optional—See Infected Hosts that Attempted to Connect to a Malicious Domain
Enable DNS Security (PAN-OS 9.1)
STEP 1 |Log in to the NGFW.
STEP 2 |To take advantage of DNS Security, you must have an active DNS Security and Threat
Prevention subscription.
Verify that you have the necessary subscriptions. To verify which subscriptions that you
currently have licenses for, select Device > Licenses and verify that the appropriate licenses
display and have not expired.
STEP 3 |Verify that the paloalto-dns-security App-ID in your security policy is configured to enable
traffic from the DNS security cloud security service.
If your firewall deployment routes your management traffic though an Internet-
facing perimeter firewall configured to enforce App-ID security policies, you must
allow the App-IDs on the perimeter firewall; failure to do so will prevent DNS security
connectivity.
## Activation & Onboarding23
## ©
## 2026 Palo Alto Networks, Inc.

Enable DNS Security
STEP 4 |Configure DNS Security signature policy settings to send malware DNS queries to the
defined sinkhole.
If you use an external dynamic list as a domain allow list, it does not have precedence
over the DNS Security domain policy actions. As a result, when there is a domain
match to an entry in the EDL and a DNS Security domain category, the action
specified under DNS Security is still applied, even when the EDL is explicitly configured
with an action of Allow.
## 1.
Select Objects > Security Profiles > Anti-Spyware.
## 2.
Create or modify an existing profile, or select one of the existing default profiles and
clone it.
## 3.
Name the profile and, optionally, provide a description.
## 4.
Select the DNS Signatures > Policies & Settings tab.
## 5.
If the Palo Alto Networks DNS Security source is not present, click Add and select it
from the list.
## 6.
Select an action to be taken when DNS lookups are made to known malware sites for
the DNS Security signature source. The options are alert, allow, block, or sinkhole. Verify
that the action is set to sinkhole.
## 7.
(Optional) In the Packet Capture drop-down, select single-packet to capture the first
packet of the session or extended-capture to set between 1-50 packets. You can then
use the packet captures for further analysis.
## 8.
In the DNS Sinkhole Settings section, verify that Sinkhole is enabled. For your
convenience, the default Sinkhole address (sinkhole.paloaltonetworks.com) is set to
## Activation & Onboarding24
## ©
## 2026 Palo Alto Networks, Inc.

Enable DNS Security
access a Palo Alto Networks server. Palo Alto Networks can automatically refresh this
address through content updates.
Sinkhole forges a response to a DNS query for domains that match the DNS
category configured for a sinkhole action to the specified sinkhole server, to
assist in identifying compromised hosts. When the default sinkhole FQDN
(sinkhole.paloaltonetworks.com) is used, the firewall sends the CNAME record
as a response to the client, with the expectation that an internal DNS server will
resolve the CNAME record, allowing malicious communications from the client
to the configured sinkhole server to be logged and readily identifiable. However,
if clients are in networks without an internal DNS server, or are using software
or tools that cannot be properly resolve a CNAME into an A record response, the
DNS request is dropped, resulting in incomplete traffic log details that are crucial
for threat analysis. In these instances, you should use the following sinkhole IP
address: (198.135.184.22).
If you want to modify the Sinkhole IPv4 or Sinkhole IPv6 address to a local server on
your network or to a loopback address, see Configure the Sinkhole IP Address to a Local
Server on Your Network.
## 9.
Click OK to save the Anti-Spyware profile.
STEP 5 |Attach the Anti-Spyware profile to a Security policy rule.
## 1.
## Select Policies > Security.
## 2.
Select or create a Security Policy Rule.
## 3.
On the Actions tab, select the Log at Session End check box to enable logging.
## 4.
In the Profile Setting section, click the Profile Type drop-down to view all Profiles. From
the Anti-Spyware drop-down and select the new or modified profile.
## 5.
Click OK to save the policy rule.
## Activation & Onboarding25
## ©
## 2026 Palo Alto Networks, Inc.

Enable DNS Security
STEP 6 |Test that the policy action is enforced.
## 1.
Access the DNS Security test domains to verify that the policy action for a given threat
type is being enforced.
## 2.
To monitor the activity on the firewall:
1.View the threat Activity and search for the URL test domain tand Blocked Activity for
the domain you accessed.
2.Select Monitor > Logs > Threat and filter by (action eq sinkhole) to view logs
on sinkholed domains.
3.For more monitoring options, see Monitor DNS Security Subscription Services
STEP 7 |Optional—Create a decryption policy rule to decrypt DNS-over-TLS / port 853 traffic. The
decrypted DNS payload can then be processed using the Anti-Spyware profile configuration
containing your DNS policy settings. When DNS-over-TLS traffic is decrypted, the resulting
DNS requests in the threat logs will appears as a conventional dns-base application with a
source port of 853.
STEP 8 |Optional—See Infected Hosts that Attempted to Connect to a Malicious Domain
## Activation & Onboarding26
## ©
## 2026 Palo Alto Networks, Inc.

Enable Advanced DNS Security
Where Can I Use This?What Do I Need?
•Prisma Access
## •NGFW
•VM-Series
•CN-Series
Advanced DNS Security License (for
enhanced feature support) or DNS
## Security License
Advanced Threat Prevention or Threat
## Prevention License
Advanced DNS Security supplements your existing DNS Security configuration to provide
additional protection against DNS hijacking by inspecting changes to DNS responses. You should
have fully configured DNS Security settings before proceeding with this step.
To enable Advanced DNS Security, you must create (or modify) an Anti-Spyware security profile
to access the Advanced DNS Security service, configure the log severity and policy settings for
the DNS signature category (or categories), and then attach the profile to a security policy rule.
You can specify up to a maximum of 100 DNS Zone Misconfigurations entries.
•PAN-OS 11.2 and later
•Strata Cloud Manager
## 27

Enable Advanced DNS Security
Enable Advanced DNS Security (Strata Cloud Manager)
STEP 1 |Use the credentials associated with your Palo Alto Networks support account and log in to
the Strata Cloud Manager on the hub.
STEP 2 |Verify that a DNS Security and a Threat Prevention license is active. Select Configuration >
NGFW and Prisma Access > Overview and click the license usage terms link in the License
panel. You should see green check marks next to the following security services: Antivirus,
Anti-Spyware, Vulnerability Protection, and DNS Security.
STEP 3 |Verify that a DNS Security and a Threat Prevention license is active. Select Configuration >
NGFW and Prisma Access > Overview and click the license usage terms link in the License
panel. You should see green check marks next to the following security services: Antivirus,
Anti-Spyware, Vulnerability Protection, and DNS Security.
STEP 4 |Update or create a new DNS Security profile to enable real-time Advanced DNS Security
queries. Typically, this is your existing DNS Security profile used for the DNS Security
configuration.
1.Select an existing DNS Security profile or Add a new one (Configuration > NGFW and
Prisma Access > Security Services > DNS Security).
2.Select an existing DNS Security profile or Add a new one (Configuration > NGFW and
Prisma Access > Security Services > DNS Security).
3.Select your DNS Security profile and then go to DNS Categories.
4.For each Advanced DNS Security domain category, specify a policy Action to take when a
corresponding domain type is detected. There are currently two analysis engines available:
DNS Misconfiguration Domains and Hijacking Domains.
## Policy Action Options:
•allow—The DNS query is allowed.
You can configure Strata Cloud Manager to generate an alert when the
applicable domain type is detected by setting the action to allow and the log
severity to informational.
•block—The DNS query is blocked.
•sinkhole—Forges a DNS response for a DNS query targeting a detected malicious
domain. This directs the resolution of the malicious domain name to a specific IP
## Activation & Onboarding28
## ©
## 2026 Palo Alto Networks, Inc.

Enable Advanced DNS Security
address (referred to as the Sinkhole IP), which is embedded as the response. The default
Sinkhole IP address is set to access a Palo Alto Networks server. Palo Alto Networks can
automatically refresh this IP address through content updates.
STEP 5 |(Optional) Specify any public-facing parent domains within your organization that you want
Advanced DNS Security to analyze and monitor for the presence of misconfigured domains.
Misconfigured domains are inadvertently created by domain owners who point alias records
to third party domains using CNAME, MX, NS record types, using entries that are no longer
valid, allowing an attacker to take over the domain by registering the expired or unused
domains.
TLDs (top-level domains) and root level domains cannot be added to the DNS Zone
Misconfigurations list.
1.Select a DNS Security profile (Configuration > NGFW and Prisma Access > Security
Services > DNS Security) that contains an Advanced DNS Security configuration.
2.Select a DNS Security profile (Configuration > NGFW and Prisma Access > Security
Services > DNS Security) that contains an Advanced DNS Security configuration.
3.In the DNS Zone Misconfigurations section, add public-facing parent domains with an
optional description to assist you in identifying domain usage or ownership within your
organization.
Entries must have a "." contained in the domain using the following format (e.g.
paloaltonetworks.com), otherwise it gets parsed as a hostname, which is considered
a private domain.
4.Click OK to exit and save the DNS Security security profile.
STEP 6 |(Optional) Monitor activity on Strata Cloud Manager for DNS queries that have been
detected using Advanced DNS Security. DNS Security Categories analyzed using Advanced
DNS Security real-time analysis of the DNS response packet have the prefix ‘adns’ followed
by the category. For example, adns-dnsmisconfig, whereby ‘dnsmisconfig’ indicates the
supported DNS category type. If the DNS domain category was determined by analyzing the
DNS request packet, the specified category is displayed with the prefix ‘dns’ followed by the
category. For example, ‘dns-grayware.’
## 1.
Access the Advanced DNS Security test domains to verify that the policy action for a
given threat type is being enforced.
## 2.
Select Incidents & Alerts > Log Viewer. You can filter the threat logs based
on the specific type of Advanced DNS Security domain category, for example
threat_category.value = 'adns-hijacking', whereby the variable adns-
hijacking indicates DNS queries that have been categorized as a malicious DNS
## Activation & Onboarding29
## ©
## 2026 Palo Alto Networks, Inc.

Enable Advanced DNS Security
hijacking attempt by Advanced DNS Security. The following Advanced DNS Security
threat categories available in the logs:
Advanced DNS Security Categories
•DNS Hijacking—adns-hijacking
DNS Hijacking domains have a threat ID of (UTID: 109,004,100).
•DNS Misconfiguration—adns-dnsmisconfig
DNS Misconfiguration domains have three threats IDs, which correspond to
three variants of DNS misconfiguration domains types: dnsmisconfig_zone
(UTID: 109,004,200), dnsmisconfig_zone_dangling (UTID: 109,004,201), and
dnsmisconfig_claimable_nx (UTID: 109,004,202). You can constrain the search
by cross-referencing a Threat-ID value that corresponds to a specific DNS
misconfiguration domain type. For example, threat_category.value = 'adns-
dnsmisconfig' and Threat ID = 109004200, whereby 109004200 indicates
the Threat ID of a DNS misconfiguration domain that does not route traffic to an
active domain due to a DNS server configuration issue.
DNS Categories analyzed using Advanced DNS Security enhanced response analysis.
•DNS —adns-benign
•Malware Domains —adns-malware
•Command and Control Domains—adns-c2
•Phishing Domains—adns-phishing
•Dynamic DNS Hosted Domains—adns-ddns
•Newly Registered Domains—adns-new-domain
•Grayware Domains—adns-grayware
•Parked Domains—adns-parked
•Proxy Avoidance and Anonymizers—adns-proxy
•Ad Tracking Domains—adns-adtracking
If the DNS query does not complete within the specified timeout period for
Advanced DNS Security, the DNS Security categorization will be used, when
possible. In those instances, the legacy notation for the category is used, for
example, instead of adns-malware, it will be categorized as dns-malware,
indicating that the DNS Security categorization value was used.
## 3.
Select Log Viewer. You can filter the threat logs based on the specific type of Advanced
DNS Security domain category, for example threat_category.value = 'adns-
hijacking', whereby the variable adns-hijacking indicates DNS queries that have
## Activation & Onboarding30
## ©
## 2026 Palo Alto Networks, Inc.

Enable Advanced DNS Security
been categorized as a malicious DNS hijacking attempt by Advanced DNS Security. The
following Advanced DNS Security threat categories available in the logs:
Advanced DNS Security Categories
•DNS Hijacking—adns-hijacking
DNS Hijacking domains have a threat ID of (UTID: 109,004,100).
•DNS Misconfiguration—adns-dnsmisconfig
DNS Misconfiguration domains have three threats IDs, which correspond to
three variants of DNS misconfiguration domains types: dnsmisconfig_zone
(UTID: 109,004,200), dnsmisconfig_zone_dangling (UTID: 109,004,201), and
dnsmisconfig_claimable_nx (UTID: 109,004,202). You can constrain the search
by cross-referencing a Threat-ID value that corresponds to a specific DNS
misconfiguration domain type. For example, threat_category.value = 'adns-
dnsmisconfig' and Threat ID = 109004200, whereby 109004200 indicates
the Threat ID of a DNS misconfiguration domain that does not route traffic to an
active domain due to a DNS server configuration issue.
DNS Categories analyzed using Advanced DNS Security enhanced response analysis.
•DNS —adns-benign
•Malware Domains —adns-malware
•Command and Control Domains—adns-c2
•Phishing Domains—adns-phishing
•Dynamic DNS Hosted Domains—adns-ddns
•Newly Registered Domains—adns-new-domain
•Grayware Domains—adns-grayware
•Parked Domains—adns-parked
•Proxy Avoidance and Anonymizers—adns-proxy
•Ad Tracking Domains—adns-adtracking
If the DNS query does not complete within the specified timeout period for
Advanced DNS Security, the DNS Security categorization will be used, when
possible. In those instances, the legacy notation for the category is used, for
example, instead of adns-malware, it will be categorized as dns-malware,
indicating that the DNS Security categorization value was used.
## 4.
Select a log entry to view the details of the DNS query.
## 5.
The DNS Category is displayed under the General pane of the detailed log view. In
addition, you can see other aspects if the threat, including the origin URL, the specific
threat type, and associated characteristics.
STEP 7 |(Optional) Retrieve a list of misconfigured domains and hijacked domains detected by the
Advanced DNS Security service. The misconfigured domains are based on the public-facing
parent domain entries added to DNS Zone Misconfigurations. This is available as a request
through AI Canvas.
## Activation & Onboarding31
## ©
## 2026 Palo Alto Networks, Inc.

Enable Advanced DNS Security
Enable Advanced DNS Security (PAN-OS 11.2 and Later)
Palo Alto Networks recommends enabling your DNS Security functionality prior to setting up
Advanced DNS Security.
STEP 1 |Log in to the NGFW.
STEP 2 |Update the content release version to 8832 or later.
STEP 3 |To prevent access to known and unknown malicious domains using Advanced DNS Security,
you must have an active Advanced DNS Security license. This should only be installed after
upgrading to PAN-OS 11.2.
Advanced DNS Security supports a licensing model that subsumes DNS Security
functionality into the Advanced DNS Security license when installed on a previously
unlicensed firewall. If you upgrade from a firewall with an existing DNS Security
license, entries indicating the presence of separate DNS Security and Advanced
DNS Security licenses are displayed. In this instance, the DNS Security license is
a passive entry and all DNS Security and Advanced DNS Security functionality is
conferred through the Advanced DNS License, including the relevant expiration date.
Firewalls without a previously installed DNS Security license show an Advanced DNS
Security license, however, it provides both DNS Security and Advanced DNS Security
functionality.
Consequently, if you downgrade from a PAN-OS release operating an Advanced DNS
Security license to a release that does not support Advanced DNS Security, the firewall
continues to display and confer DNS Security functionality through the Advanced DNS
Security license, however, it is limited to base DNS Security features.
To verify subscriptions for which you have currently-active licenses, select Device > Licenses
and verify that the appropriate licenses are available and have not expired.
## Activation & Onboarding32
## ©
## 2026 Palo Alto Networks, Inc.

Enable Advanced DNS Security
STEP 4 |Update or create a new Anti-Spyware Security profile to enable real-time Advanced DNS
Security queries. Typically, this is your existing Anti-Spyware security profile used for the
DNS Security configuration.
1.Select an existing Anti-Spyware security profile or Add a new one (Objects > Security
Profiles > Anti-Spyware).
2.Select your Anti-Spyware security profile and then go to DNS Policies.
3.For each Advanced DNS Security domain category, specify a Log Severity and Policy Action
to take when a domain type is detected using a corresponding analysis engine. There are
currently two analysis engines available: DNS Misconfiguration Domains and Hijacking
## Domains.
## Policy Action Options:
•allow—The DNS query is allowed.
You can configure the firewall to generate an alert when the applicable
domain type is detected by setting the action to allow and the log severity to
informational.
•block—The DNS query is blocked.
•sinkhole—Forges a DNS response for a DNS query targeting a detected malicious
domain. This directs the resolution of the malicious domain name to a specific IP
address (referred to as the Sinkhole IP), which is embedded as the response. The default
## Activation & Onboarding33
## ©
## 2026 Palo Alto Networks, Inc.

Enable Advanced DNS Security
Sinkhole IP address is set to access a Palo Alto Networks server. Palo Alto Networks can
automatically refresh this IP address through content updates.
## Log Severity Options:
•none—The event does not have an associated log severity level.
•low—Warning-level threats that have very little impact on an organization's
infrastructure. They usually require local or physical system access and may often result
in victim privacy or DoS issues and information leakage.
•informational—Suspicious events that do not pose an immediate threat, but that are
reported to call attention to deeper problems that could possibly exist.
•medium—Minor threats in which impact is minimized, such as DoS attacks that do not
compromise the target or exploits that require an attacker to reside on the same LAN as
the victim, affect only non-standard configurations or obscure applications, or provide
very limited access.
•high—Threats that have the ability to become critical but have mitigating factors; for
example, they may be difficult to exploit, do not result in elevated privileges, or do not
have a large victim pool.
•critical—Serious threats, such as those that affect default installations of widely deployed
software, result in root compromise of servers, and the exploit code is widely available
to attackers. The attacker usually does not need any special authentication credentials or
knowledge about the individual victims and the target does not need to be manipulated
into performing any special functions.
4.Click OK to exit the Anti-Spyware Security Profile configuration dialog and Commit your
changes.
STEP 5 |(Optional) Specify any public-facing parent domains within your organization that you want
Advanced DNS Security to analyze and monitor for the presence of misconfigured domains.
Misconfigured domains are inadvertently created by domain owners who point alias records
to third party domains using CNAME, MX, NS record types, using entries that are no longer
## Activation & Onboarding34
## ©
## 2026 Palo Alto Networks, Inc.

Enable Advanced DNS Security
valid, allowing an attacker to take over the domain by registering the expired or unused
domains.
TLDs (top-level domains) and root level domains cannot be added to the DNS Zone
Misconfigurations list.
1.Select an Anti-Spyware security profile (Objects > Security Profiles > Anti-Spyware) and go
to DNS Policies.
2.In the DNS Zone Misconfigurations section, add public-facing parent domains with an
optional description to assist you in identifying domain usage or ownership within your
organization.
Entries must have a "." contained in the domain using the following format (e.g.
paloaltonetworks.com), otherwise it gets parsed as a hostname, which is considered
a private domain.
3.Click OK to exit the Anti-Spyware Security Profile configuration dialog and Commit your
changes.
STEP 6 |(Optional) Configure the maximum Advanced DNS signature lookup timeout setting. When
this value is exceeded, the DNS response passes through without performing analysis using
Advanced DNS Security.
STEP 7 |(Optional [If you do not have the latest device certificate]) Install an updated firewall device
certificate used to authenticate to the Advanced Threat Prevention inline cloud analysis
service. Repeat for all firewalls enabled for inline cloud analysis.
If you have already installed an updated firewall device certificate as part of your IoT Security,
Device Telemetry, Advanced Threat Prevention, or Advanced URL Filtering onboarding
process, this step is not necessary.
STEP 8 |(Required when the firewall is deployed with an explicit proxy server) Configure the proxy
server used to access the servers that facilitate requests generated by all configured inline
## Activation & Onboarding35
## ©
## 2026 Palo Alto Networks, Inc.

Enable Advanced DNS Security
cloud analysis features. A single proxy server can be specified and applies to all Palo Alto
Networks update services, including all configured inline cloud and logging services.
## 1.
(PAN-OS 11.2.3 and later) Configure the proxy server through PAN-OS.
1.Select Device >  Setup >  Services and edit the Services details.
2.Specify the Proxy Server settings and Enable proxy for Inline Cloud Services. You can
provide either an IP address or FQDN in the Server field.
The proxy server password must contain a minimum of six characters.
3.Click OK.
STEP 9 |(Optional) Verify the status of your firewall connectivity to the Advanced DNS Security cloud
service.
STEP 10 |(Optional) Monitor activity on the firewall for DNS queries that have been detected using
Advanced DNS Security. DNS Security Categories analyzed using Advanced DNS Security
real-time analysis of the DNS response packet have the prefix ‘adns’ followed by the
category. For example, adns-dnsmisconfig, whereby ‘dnsmisconfig’ indicates the supported
DNS category type. If the DNS domain category was determined by analyzing the DNS
request packet, the specified category is displayed with the prefix ‘dns’ followed by the
category. For example, ‘dns-grayware.’
## 1.
Access the Advanced DNS Security test domains to verify that the policy action for a
given threat type is being enforced.
## 2.
Select Monitor > Logs > Threat. You can filter the logs based on the specific type of
Advanced DNS Security domain category, for example ( category-of-threatid
eq adns-hijacking ), whereby the variable adns-hijacking indicates DNS
queries that have been categorized as a malicious DNS hijacking attempt by Advanced
DNS Security. The following Advanced DNS Security threat categories available in the
logs:
Advanced DNS Security Categories
•DNS Hijacking—adns-hijacking
DNS Hijacking domains have a threat ID of (UTID: 109,004,100).
•DNS Misconfiguration—adns-dnsmisconfig
DNS Misconfiguration domains have three threats IDs, which correspond to
three variants of DNS misconfiguration domains types: dnsmisconfig_zone
(UTID: 109,004,200), dnsmisconfig_zone_dangling (UTID: 109,004,201), and
dnsmisconfig_claimable_nx (UTID: 109,004,202). You can constrain the search
by cross-referencing a Threat-ID value that corresponds to a specific DNS
## Activation & Onboarding36
## ©
## 2026 Palo Alto Networks, Inc.

Enable Advanced DNS Security
misconfiguration domain type. For example, ( category-of-threatid eq adns-
dnsmisconfig ) and (threatid eq 109004200), whereby 109004200 indicates the
Threat ID of a DNS misconfiguration domain that does not route traffic to an active
domain due to a DNS server configuration issue.
DNS Categories analyzed using Advanced DNS Security enhanced response analysis.
You must operate a firewall running PAN-OS 11.2 and later to take advantage
of enhanced Advanced DNS Security real-time analysis.
•DNS —adns-benign
•Malware Domains —adns-malware
•Command and Control Domains—adns-c2
•Phishing Domains—adns-phishing
•Dynamic DNS Hosted Domains—adns-ddns
•Newly Registered Domains—adns-new-domain
•Grayware Domains—adns-grayware
•Parked Domains—adns-parked
•Proxy Avoidance and Anonymizers—adns-proxy
•Ad Tracking Domains—adns-adtracking
If the DNS query does not complete within the specified timeout period for
Advanced DNS Security, the DNS Security categorization will be used, when
possible. In those instances, the legacy notation for the category is used, for
example, instead of adns-malware, it will be categorized as dns-malware,
indicating that the DNS Security categorization value was used.
## 3.
Select a log entry to view the details of the DNS query.
## 4.
The DNS Category is displayed under the Details pane of the detailed log view. In
addition, you can see other aspects of the threat, including the Threat ID, which
includes the origin domain, the specific threat category, and other associated
characteristics, as well as the associated Q type, and R data using the following format:
## Activation & Onboarding37
## ©
## 2026 Palo Alto Networks, Inc.

Enable Advanced DNS Security
hijacking:<FQDN>:<QTYPE>:<RDATA>, whereby <QTYPE> represents the DNS
resource record type and <RDATA> represents the hijacked IP Address.
## Activation & Onboarding38
## ©
## 2026 Palo Alto Networks, Inc.

Enable Advanced DNS Security
STEP 11 |(Optional) Retrieve a list of misconfigured domains and hijacked domains detected by the
Advanced DNS Security service. The misconfigured domains are based on the public-facing
parent domain entries added to DNS Zone Misconfigurations.
Misconfigured domain entries that are removed from your network are not
immediately reflected in the Advanced DNS Security dashboard statistics.
## 1.
Use the credentials associated with your Palo Alto Networks support account and log in
to Strata Cloud Manager on the hub.
## 2.
Select Dashboards > More Dashboards > DNS Security to open the DNS Security
dashboard.
## 3.
From the DNS Security dashboard, refer to the following widgets:
•Misconfigured Domains—View a list of non-resolvable domains associated with
the user-specified public-facing parent domain(s). For each entry, there is a
misconfiguration reason and a traffic hit count based on the source IP.
•Hijacked Domains—View a list of hijacked domains as determined by Advanced DNS
Security. For each entry, there is a categorization reason and a traffic hit count based
on the source IP.
## Activation & Onboarding39
## ©
## 2026 Palo Alto Networks, Inc.

Enable Advanced DNS Security
## Activation & Onboarding40
## ©
## 2026 Palo Alto Networks, Inc.

Activate Advanced DNS Security
## Resolver
Where Can I Use This?What Do I Need?
•Strata Cloud ManagerAdvanced DNS Security Resolver
## License
Palo Alto Networks Advanced DNS Security Resolver provides two licensing options: a standalone
license or part of an ELA (Enterprise License Agreement). Depending on the Advanced DNS
Security Resolver license model you purchased, you must either proceed with the ELA Add-on
activation, or, if you have a standard standalone license, you should have received a welcome
email. Contained in this email is an Activate Subscription link that kicks off your activation
process.
For more information about license activation and management for Palo Alto Networks products,
refer to:
•Common Services: License Activation, Subscription, & Tenant Management
•First time activation - one CSP account
•First time activation - multiple CSP accounts
•Return visit activation
•ELA Add-on Activation
## 41

Activate Advanced DNS Security Resolver
First time Advanced DNS Security Resolver Activation -
## One Customer Support Portal Account
If you have only one Customer Support Portal account, follow these steps for first time Advanced
DNS Security Resolver activation.
STEP 1 |Because you have only one Customer Support Portal account associated with your
username, the Customer Support Account is pre-populated.
STEP 2 |Allocate the product to the Recipient of your choice.
## 1.
The name provided matches your Customer Support Portal account for convenience.
You can use the name provided or change it.
STEP 3 |Select a Region where you want to deploy your product.
STEP 4 |The web interface shows the available Advanced DNS Security Resolver licenses that can be
assigned to a specified tenant. Confirm the value and select Done.
## Activation & Onboarding42
## ©
## 2026 Palo Alto Networks, Inc.

Activate Advanced DNS Security Resolver
STEP 5 |Agree to the terms and conditions, and Activate.
A single default tenant is auto-created behind the scenes, and the product is activated in the
tenant.
This tenant, and any others created by this Customer Support Portal account, will have
the  Superuser role.
STEP 6 |Advanced DNS Security Resolver activation is now complete for Strata Cloud Manager.
STEP 7 |(Optional) Manage your product from Strata Cloud Manager.
STEP 8 |(Optional) Manage identity and access.
## Activation & Onboarding43
## ©
## 2026 Palo Alto Networks, Inc.

Activate Advanced DNS Security Resolver
First time Advanced DNS Security Resolver Activation -
## Multiple Customer Support Portal Account
If you have multiple Customer Support Portal accounts, follow these steps for first time Advanced
DNS Security Resolver activation.
STEP 1 |If you have multiple Customer Support Portal accounts, choose the Customer Support
Account number that you want to use.
## Activation & Onboarding44
## ©
## 2026 Palo Alto Networks, Inc.

Activate Advanced DNS Security Resolver
STEP 2 |Allocate the product to the Recipient of your choice.
You can allocate your entire license to one recipient or you can share it with multiple recipients
in a tenant hierarchy. What is a tenant?
## 1.
If you need just one tenant, use or rename the tenant provided. The name provided
matches your Customer Support Portal account for convenience.
## 2.
(Optional) This step applies if you are a managed security service provider (MSSP), a
distributed enterprise customer, or need multiple tenants. After you create the first
tenant, you can Allocate to subtenant and use or rename the tenant provided.
## Activation & Onboarding45
## ©
## 2026 Palo Alto Networks, Inc.

Activate Advanced DNS Security Resolver
A subscription gets allocated on a tenant or a sub-tenant. This step is for choosing
a tenant where you want to allocate a license, not for building a complete tenant
hierarchy. You can create only a tenant and subtenant here, and you can choose to
allocate a license to that subtenant.
After activation, you can build out your tenant hierarchy as needed through
tenant management. You can create your tenant hierarchy to reflect your existing
organizational structure. You can also consider identity and access inheritance when
creating the hierarchy, in addition to tenant hierarchy limits.
## 3.
## Select Done.
STEP 3 |Select a Region where you want to deploy your product.
STEP 4 |The web interface shows the available Advanced DNS Security Resolver licenses that can be
assigned to a specified tenant. Confirm the value and select Done.
STEP 5 |Agree to the terms and conditions, and Activate.
This tenant, and any others created by this Customer Support Portal account, will have
the  Superuser role.
## Activation & Onboarding46
## ©
## 2026 Palo Alto Networks, Inc.

Activate Advanced DNS Security Resolver
STEP 6 |Advanced DNS Security Resolver activation is now complete for Strata Cloud Manager.
STEP 7 |(Optional) Manage your product from Strata Cloud Manager.
STEP 8 |(Optional) Manage identity and access.
## Activation & Onboarding47
## ©
## 2026 Palo Alto Networks, Inc.

Activate Advanced DNS Security Resolver
Return Visit Advanced DNS Security Resolver Activation
Follow these steps if you have already completed first time activation, you have already created
your tenant hierarchy through Identity & Access > Tenants or tenant management, and you are
returning to activate another product in your existing hierarchy.
STEP 1 |Choose the Customer Support Account number that you want to use to activate.
STEP 2 |Allocate the subscription to the Recipient tenant of your choice.
STEP 3 |Select a Region where you want to deploy your product.
## Activation & Onboarding48
## ©
## 2026 Palo Alto Networks, Inc.

Activate Advanced DNS Security Resolver
STEP 4 |The web interface shows the available Advanced DNS Security Resolver licenses that can be
assigned to a specified tenant. Confirm the value and select Done.
STEP 5 |Agree to the terms and conditions, and Activate.
STEP 6 |Advanced DNS Security Resolver activation is now complete for Strata Cloud Manager.
STEP 7 |(Optional) Manage your product from Strata Cloud Manager.
STEP 8 |(Optional) Manage identity and access.
## Activation & Onboarding49
## ©
## 2026 Palo Alto Networks, Inc.

Activate Advanced DNS Security Resolver
ELA Add-on Activation
The add-on for ELA (Enterprise License Agreement) is a consumption model for large enterprises
to assign subscriptions in bulk to assets purchased from Palo Alto Networks. ELA based solutions
offer the flexibility to enable any of the following licenses that are supported for a tenant or TSG:
STEP 1 |Start the ELA activation process from either the hub or Customer Support Portal.
•Customer Support Portal: Log in to your Customer Support Portal account, select Products
> Enterprise Agreements > Licenses and then click ELA-ADNSR Activation.
•Hub: Log into the hub and, from the tenant view, select ELA Activation > ADNSR.
Completion of either activation process loads a magic link that opens the Advanced DNS
Security Resolver activation page on the hub.
STEP 2 |If you have multiple Customer Support Portal accounts, choose the Customer Support
Account number that you want to use.
## Activation & Onboarding50
## ©
## 2026 Palo Alto Networks, Inc.

Activate Advanced DNS Security Resolver
STEP 3 |Allocate the product to the Recipient of your choice.
The tenant where Advanced DNS Security Resolver is to be activated (the recipient)
must be configured to use Strata Logging Service.
You must migrate to the newer SLS service before the Advanced DNS Security
Resolver can be enabled for the specified tenant, if you are currently using any of the
following legacy products:
•Cortex Data Lake
•AIOps for NGFW
•AIOps for NGFW Free
Additionally if you have any unactivated magic links, pending inflight or expired
quotes, these can interfere with the activation process. You must resolve any such
outstanding examples by requesting their removal or completing the request. Failure to
do so will produce an error indicating service incompatibilities.
Please contact your Authorized Support Center or sales representative for more
information on migrating from CDL to SLS.
## 1.
The name provided matches your Customer Support Portal account for convenience.
You can use the name provided or change it.
STEP 4 |Select a Region where you want to deploy your product. Your Advanced DNS Security
Resolver data and incidents reside in geographic locations based on where the enforcement
point that forwarded the traffic to Advanced DNS Security Resolver is located.
## Activation & Onboarding51
## ©
## 2026 Palo Alto Networks, Inc.

Activate Advanced DNS Security Resolver
STEP 5 |The web interface shows the available Advanced DNS Security Resolver licenses that can be
assigned to a specified tenant. Leave the value at the default setting and select Done.
This item is not applicable for ELA accounts, however, you must select Done to
proceed to the next step.
STEP 6 |Agree to the terms and conditions, and Activate.
A single default tenant is auto-created behind the scenes, and the product is activated in the
tenant.
This tenant, and any others created by this Customer Support Portal account, will have
the  Superuser role.
STEP 7 |Advanced DNS Security Resolver activation is now complete for Strata Cloud Manager. After
you log in to Strata Cloud Manager, you can access all Advanced DNS Security Resolver
management operations from Manage > Configuration > ADNS Resolver.
STEP 8 |(Optional) Manage your product from Strata Cloud Manager.
STEP 9 |(Optional) Manage identity and access.
## Activation & Onboarding52
## ©
## 2026 Palo Alto Networks, Inc.

Enable Advanced DNS Security
## Resolver
Where Can I Use This?What Do I Need?
•Strata Cloud ManagerAdvanced DNS Security Resolver
## License
To enable the Advanced DNS Security Resolver, you must create (or modify) a DNS Security
profile and add/verify connection sources used by the Advanced DNS Security Resolver service.
There are optional tasks that provide extended functionality and additional security options.
Please review all of the steps below before committing to the deployment process.
STEP 1 |Verify that you have a license for the Advanced DNS Security Resolver.
STEP 2 |Log in to the Strata Cloud Manager on the hub.
## 53

Enable Advanced DNS Security Resolver
STEP 3 |Configure an Advanced DNS Security Resolver security profile. You can also use the default
best-practice security profile, however, you should still review the configuration to verify
that it is appropriate for your deployment.
Alternatively, you can create an Advanced DNS Security Resolver security profile from
the Create Connection Source menu (Configuration > ADNS Resolver. This allows you
to create a security profile and add connection sources as part of a single workflow.
## 1.
Select Configuration > ADNS Resolver and then go to the DNS Security Profiles tab.
## 2.
Select Create DNS Security Profile and in the General tab, provide a name and
description for the security profile.
## 3.
In the Categories tab, for each of the domain categories listed under the primary
groupings (Content, DNS Security, and Advanced DNS Security), specify a policy Action
to take when a corresponding domain type is detected.
## Policy Action Options:
•allow—The DNS query is allowed.
•alert—The DNS query generates an alert. DNS queries that generate an alert are
saved in the DNS Security log.
•block—The DNS query is blocked.
•sinkhole—Forges a DNS response for a DNS query targeting a detected malicious
domain. This directs the resolution of the malicious domain name to a specific IP
address (referred to as the Sinkhole IP), which is embedded as the response.
## Activation & Onboarding54
## ©
## 2026 Palo Alto Networks, Inc.

Enable Advanced DNS Security Resolver
## 4.
(Optional) Specify any public-facing parent domains within your organization that you
want Advanced DNS Security Resolver to analyze and monitor for the presence of
misconfigured domains.
## 5.
(Optional) Add domains that you want the ADNS Resolver to bypass. If your organization
uses third party threat feeds as part of a comprehensive threat intelligence solution,
you can also reference those in the form of external dynamic lists (EDLs) as part of your
overrides configuration.
STEP 4 |Review your Advanced DNS Security Resolver configuration settings and provide connection
sources.
STEP 5 |Select Configuration > ADNS Resolver and then go to the DNS Resolver Configurations tab.
From here, you can review your DNS resolver details:
•Connection Source Verification Status—Provides a breakdown of the verification status
of all the connection sources you have added to your Advanced DNS Security Resolver
configuration. You must validate the egress IP address of a connection source to enable
processing of DNS requests. If the IP is not validated, it is not considered to be part of the
network and requests to that IP are rejected.
•DNS Resolver Info—The Palo Alto Networks Advanced DNS Security Resolver server
details. The server that you connect to is dependent on your geolocation. TheAdvanced
DNS Security Resolver connects you to the service via an anycast IP to provide optimum
service reliability and performance. You can toggle between IPv4 and IPv6 variants of the
assigned IP address.
•DNS Sinkhole Settings—Indicates the currently selected DNS sinkhole server (the default is
the Palo Alto Networks hosted DNS sinkhole) and the configured block page contents.
•Connection Sources—Lists all of the connection sources added to your Advanced DNS
Security Resolver. Connection sources are egress IP addresses in your branch/campus/
## Activation & Onboarding55
## ©
## 2026 Palo Alto Networks, Inc.

Enable Advanced DNS Security Resolver
datacenter that will be subject to the security policies dictated by the Advanced DNS
Security Resolver policies.
STEP 6 |Add and configure connection sources to your Advanced DNS Security Resolver
configuration.
STEP 7 |(Internal DNS Server) Configure your internal DNS server to use the Advanced DNS Security
Resolver anycast IP addresses located under DNS Resolver Info.
STEP 8 |Configure your ADNS Resolver sinkhole settings and, optionally, configure a customized
block page.
STEP 9 |(Optional) Update your access control configuration to include Advanced DNS Security
Resolver functionality. The following default Enterprise Roles provide multiple read and write
permissions for the Advanced DNS Security Resolver (shown as Atmos Resolver):
STEP 10 |(Optional) Add internal domains to be excluded from getting processed by the Advanced
DNS Security Resolver.
STEP 11 |(Optional) Search for threat intelligence that Palo Alto Networks has collected for a domain
using Strata Cloud Manager IOC Search.
The IOC Search does not currently support visualization of local network activity seen
by the Advanced DNS Security Resolver.
STEP 12 |(Optional) Review logs generated by the Advanced DNS Security Resolver in Strata Cloud
## Manager.
STEP 13 |(Optional) View Activity Insights: Domains for a high level view of the trends and statistics of
your DNS Security usage.
## Activation & Onboarding56
## ©
## 2026 Palo Alto Networks, Inc.