VM-Series Public Cloud Deployments
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
© 2023-2025 Palo Alto Networks, Inc. Palo Alto Networks is a registered trademark of Palo
Alto Networks. A list of our trademarks can be found at www.paloaltonetworks.com/company/
trademarks.html. All other marks mentioned herein may be trademarks of their respective companies.
Last Revised
February 21, 2025
VM-Series Public Cloud Deployments 2 ©2026 Palo Alto Networks, Inc.
Table of Contents
VM-Series Firewall on AWS............................................................................9
AWS Terminology..................................................................................................................... 11
VM-Series Firewall on AWS Cloud Environments............................................................ 14
VM-Series Firewall on AWS GovCloud....................................................................14
VM-Series Firewall on AWS China........................................................................... 14
VM-Series Firewall on AWS Outposts..................................................................... 15
Management Interface Mapping for Use with Amazon ELB.......................................... 16
Performance Tuning for the VM-Series Firewall on AWS.............................................. 18
View the DPDK Configuration on Your Firewall................................................... 18
Enable DPDK Packed I/O............................................................................................18
Deploy the VM-Series Firewall on AWS.............................................................................20
```
Obtain the Amazon Machine Image (AMI).............................................................. 22
```
```
Get the VM-Series Firewall Amazon Machine Image (AMI) ID.......................... 25
```
Planning Worksheet for the VM-Series in the AWS VPC................................... 28
Launch the VM-Series Firewall on AWS................................................................. 30
Launch the VM-Series Firewall on AWS Outpost................................................. 39
```
Create a Custom Amazon Machine Image (AMI)...................................................48
```
Encrypt EBS Volume for the VM-Series Firewall on AWS.................................. 51
Use the VM-Series Firewall CLI to Swap the Management Interface...............52
Enable CloudWatch Monitoring on the VM-Series Firewall............................... 53
Publish ENA Network Performance Metrics to AWS CloudWatch...................59
VM-Series Firewall Startup and Health Logs on AWS......................................... 60
VM-Series Integration with AWS Warm Pool................................................................... 66
AWS Warm Pool Integration...................................................................................... 66
Dependencies and Interactions..................................................................................67
Configure AWS Warm Pools for VM-Series Auto Scaling Groups.................... 67
Simplified Onboarding of VM-Series Firewall on AWS................................................... 71
Panorama Orchestrated Deployments in AWS................................................................. 86
Prepare for an Orchestrated AWS Deployment.................................................... 88
Orchestrate a VM-Series Firewall Deployment in AWS...................................... 95
View the Deployment Status................................................................................... 103
Traffic Flow and Configurations..............................................................................105
VM-Series Integration with an AWS Gateway Load Balancer.....................................113
Enable VM-Series Integration with a Gateway Load Balancer.........................116
Manually Integrate the VM-Series with a Gateway Load Balancer.................117
VM-Series Integration with AWS Cloud WAN.................................................... 122
Associate a VPC Endpoint with a VM-Series Interface..................................... 140
Enable Overlay Routing for the VM-Series on AWS..........................................144
VM-Series Public Cloud Deployments 3 ©2026 Palo Alto Networks, Inc.
Table of Contents
VM-Series Auto Scaling Group with AWS Gateway Load Balancer................150
Enable Session Resiliency on VM-Series for AWS..............................................164
High Availability for VM-Series Firewall on AWS.......................................................... 168
Secondary IP Move.....................................................................................................168
Dataplane Interface Move........................................................................................ 169
HA Links........................................................................................................................ 169
Heartbeat Polling and Hello Messages.................................................................. 170
Device Priority and Preemption.............................................................................. 170
HA Timers..................................................................................................................... 170
IAM Roles for HA........................................................................................................171
Configure Active/Passive HA on AWS Using a Secondary IP.......................... 174
Configure Active/Passive HA on AWS Using Interface Move......................... 180
Migrate Active/Passive HA on AWS......................................................................184
AWS Shared VPC Monitoring............................................................................................. 190
Use AWS Secrets Manager to Store VM-Series Certificates....................................... 213
Use Case: Secure the EC2 Instances in the AWS Cloud...............................................216
Use Case: Use Dynamic Address Groups to Secure New EC2 Instances within the
VPC.............................................................................................................................................230
Use Case: VM-Series Firewalls as GlobalProtect Gateways on AWS........................ 235
Components of the GlobalProtect Infrastructure............................................... 236
Deploy GlobalProtect Gateways on AWS............................................................ 237
Resource Monitoring on AWS.............................................................................................239
List of Attributes Monitored on the AWS VPC.............................................................. 240
IAM Permissions Required for Monitoring the AWS VPC............................................243
Set Up the AWS Plugin for VM Monitoring on Panorama........................................... 244
Planning Checklist for VM Monitoring on AWS..................................................245
IAM Roles and Permissions for Panorama............................................................ 246
Install or Upgrade the AWS Plugin.........................................................................250
Configure the AWS Plugin for VM Monitoring................................................... 251
Performance Tuning for the VM-Series Firewall on AWS............................................262
View the DPDK Configuration on Your Firewall.................................................262
Enable DPDK Packed I/O......................................................................................... 262
VM-Series Firewall on Azure......................................................................265
Deployments Supported on Azure..................................................................................... 266
Azure Networking and VM-Series Firewall...................................................................... 267
Azure Security Center Integration......................................................................................268
VM-Series Firewall Templates on Azure...........................................................................271
Minimum System Requirements for the VM-Series on Azure.....................................273
VM-Series on Azure Service Principal Permissions........................................................ 274
Permissions................................................................................................................... 274
VM-Series Public Cloud Deployments 4 ©2026 Palo Alto Networks, Inc.
Table of Contents
```
Deploy the VM-Series Firewall from the Azure Marketplace (Solution
```
```
Template)...................................................................................................................................278
```
Simplified Onboarding of VM-Series Firewall on Azure................................................288
```
Deploy the VM-Series Firewall from the Azure China Marketplace (Solution
```
```
Template)...................................................................................................................................304
```
Panorama Orchestrated Deployments in Azure............................................................. 310
Prepare for an Orchestrated Deployment............................................................ 312
Orchestrate a VM-Series Firewall Deployment in Azure.................................. 316
Deploy the VM-Series with the Azure Gateway Load Balancer..................................327
Create a Custom VM-Series Image for Azure................................................................. 336
Use Azure Security Center Recommendations to Secure Your Workloads..............338
Deploy a VM-Series Firewall Based on an Azure Security Center
Recommendation.........................................................................................................338
Connect an Existing VM-Series Firewall From Azure Security Center........... 340
Use Panorama to Forward Logs to Azure Security Center............................... 341
Deploy the VM-Series Firewall on Azure Stack..............................................................345
Deploy the VM-Series Firewall on Azure Stack HCI......................................................350
Deploy VM-Series on Azure Stack Edge.......................................................................... 373
Security Challenges in 5G and Edge Deployments.............................................373
Benefits of VM-Series Integration with Azure Stack Edge............................... 373
Enable Azure Application Insights on the VM-Series Firewall.....................................379
Deploy Application Insights Using Workspace.................................................... 382
Migrate Application Insights Manually...................................................................385
Application Insights Deletion................................................................................... 390
Downgrade....................................................................................................................390
Monitoring on Azure..............................................................................................................391
Attributes Monitored Using the Panorama Plugin on Azure............................ 391
Set Up the Azure Plugin for Monitoring on Panorama...................................... 393
Azure Health Monitoring...................................................................................................... 404
Set up Active/Passive HA on Azure.................................................................................. 408
```
Set up Active/Passive HA on Azure (North-South & East-West Traffic)....... 410
```
```
Set up Active/Passive HA on Azure (East-West Traffic Only)......................... 427
```
Use the Azure Key Vault to Store VM-Series Certificates........................................... 443
Use the ARM Template to Deploy the VM-Series Firewall..........................................446
Deploy the VM-Series and Azure Application Gateway Template............................. 450
Start Using the VM-Series & Azure Application Gateway Template.............. 453
VM-Series and Azure Application Gateway Template Parameters................. 457
Secure Kubernetes Services on Azure.............................................................................. 461
How Does the Panorama Plugin for Azure Secure Kubernetes Services?..... 461
A Sample Hub-and-Spoke Topology to Secure AKS Clusters.......................... 462
User-Defined Routing................................................................................................ 463
VM-Series Public Cloud Deployments 5 ©2026 Palo Alto Networks, Inc.
Table of Contents
AKS Cluster Communication.................................................................................... 463
Dynamic Address Groups with Kubernetes Labels.............................................465
Secure an AKS Cluster...............................................................................................465
Use Case: Deploy the VM-Series Firewall in Different Availability Zones in
Azure.......................................................................................................................................... 478
Clean up Resources.................................................................................................... 481
VM-Series Firewall on Google Cloud Platform......................................483
Supported Deployments on Google Cloud Platform..................................................... 486
Internet Gateway.........................................................................................................486
Segmentation Gateway..............................................................................................487
Hybrid IPSec VPN....................................................................................................... 487
Minimum System Requirements for the VM-Series Firewall on GCP........................489
Create a Custom VM-Series Firewall Image for Google Cloud Platform...................492
System Disk Size Increase on Google Cloud Platform.................................................. 495
Prepare to Set Up VM-Series Firewalls on Google Public Cloud................................ 500
Prepare to Deploy from the GCP Marketplace................................................... 500
Interface Order............................................................................................................ 505
Management Interface...............................................................................................505
```
Dataplane Interfaces (Untrust, Trust).....................................................................505
```
Additional Dataplane Interfaces.............................................................................. 506
Deployment Models for VM-Series on GCP....................................................................507
Auto Scale Model........................................................................................................508
Active/Passive HA Model......................................................................................... 510
Deploy the VM-Series Firewall from Google Cloud Platform Marketplace.............. 513
Management Interface Swap for Google Cloud Platform Load Balancing.....517
Use the VM-Series Firewall CLI to Swap the Management Interface............ 519
Enable Google Stackdriver Monitoring on the VM Series Firewall................. 520
Enable VM Monitoring to Track VM Changes on Google Cloud Platform
```
(GCP)...............................................................................................................................522
```
Use Dynamic Address Groups to Secure Instances Within the VPC.............. 525
Use Custom Templates or the gcloud CLI to Deploy the VM-Series
Firewall........................................................................................................................... 527
Enable Session Resiliency on VM-Series for GCP...............................................528
Use VM-Series Firewall to Configure NPTv6 Policy for IPv6 Forwarding Rule on
```
Google Cloud Platform (GCP)..............................................................................................532
```
Deploy Resources in GCP Using Gcloud...............................................................533
Create VM-SeriesFirewall with Gcloud..................................................................536
Create External Load Balancer................................................................................ 537
Configure VM-Series.................................................................................................. 538
Configure Network Interfaces to Handle IPv4/IPv6 Traffic............................. 539
Configure NAT Policy for IPv4 Forwarding Rule.................................................541
VM-Series Public Cloud Deployments 6 ©2026 Palo Alto Networks, Inc.
Table of Contents
Configure NPTv6 Policy for IPv6 Forwarding Rule............................................ 543
Configure Health Checks.......................................................................................... 544
Create Test Workloads.............................................................................................. 546
Test Inbound Internet Traffic...................................................................................546
Destroy Deployment.................................................................................................. 548
VM Monitoring with the Panorama Plugin for GCP...................................................... 550
Configure GCP Assets for VM Monitoring........................................................... 550
Review and Create Tags............................................................................................552
Install the Panorama Plugin for GCP......................................................................553
Configure VM Monitoring with the Panorama Plugin for GCP........................555
Securing VPC Networks with VM-Series Firewall on GCP.......................................... 559
Multiple Network Interface Architecture..............................................................559
VPC Network Peering Model...................................................................................561
Network Connectivity Center.................................................................................. 561
```
Google Cloud Network Security Integration (NSI) with VM-Series Firewalls...........564
```
Configure GCP NSI Overlay Support.................................................................................569
Configure GCP NSI Overlay Support Using CLI.................................................. 570
Secure Boot Support for VM-Series on GCP.................................................................. 575
Configuring GCP Load Balancer..........................................................................................579
Onboarding External Load Balancer....................................................................... 579
Onboarding Global HTTPS Load Balancer............................................................ 583
```
Configuring Global HTTP(s) Load Balancer with XFF Header.......................... 586
```
Autoscaling the VM-Series Firewall on Google Cloud Platform..................................591
Auto Scaling Components for Google Cloud Platform.......................................591
Deploy GCP Autoscaling Templates.......................................................................603
Set up Active/Passive HA on Google Cloud Platform...................................................632
Deploy the GCP Active/Passive HA.......................................................................634
VM-Series Firewall on Oracle Cloud Infrastructure............................. 647
Deployments Supported on OCI........................................................................................ 649
Prepare to Set Up the VM-Series Firewall on OCI........................................................ 651
Deploy the VM-Series Firewall from the Oracle Cloud Marketplace.........................654
Configure Active/Passive HA on OCI............................................................................... 659
Forward Metrics to Oracle Cloud Infrastructure............................................................ 669
Oracle Cloud Infrastructure Logging..................................................................................674
Bootstrap the VM-Series Firewall on OCI.......................................................................678
VM-Series Firewall on IBM Cloud............................................................ 681
Licensing Information.............................................................................................................682
System Requirements for VM-Series Firewall on IBM Cloud...................................... 683
Prepare to Set Up VM-Series Firewalls on IBM Cloud..................................................684
VM-Series Public Cloud Deployments 7 ©2026 Palo Alto Networks, Inc.
Table of Contents
Prerequisites................................................................................................................. 684
Dependencies............................................................................................................... 684
General Requirements................................................................................................685
Deploy the VM-Series Firewall Using IBM Cloud Schematics.....................................687
High Resiliency for VM-Series Firewall on IBM Cloud..................................................693
Configure IBM VPC VM-Series for HA................................................................. 693
Deploy the VM-Series Firewall................................................................................693
Deploy the NLB........................................................................................................... 694
Configure Security Groups........................................................................................694
Configure Custom Routes.........................................................................................694
Considerations for NLB Failovers and Custom Routes......................................694
VM-Series Firewall on Alibaba Cloud...................................................... 695
Minimum System Requirements for the VM-Series Firewall on Alibaba Cloud....... 697
VM-Series Firewall Software Requirements.........................................................697
Alibaba Cloud Instance Type Recommendations for the VM-Series
Firewall........................................................................................................................... 697
Alibaba Cloud CLI........................................................................................................699
Deploy the VM-Series Firewall on Alibaba Cloud.......................................................... 701
Create a VPC and Configure Networks.................................................................701
Create and Configure the VM-Series Firewall..................................................... 704
Secure North-South Traffic on Alibaba Cloud..................................................... 708
Configure Load Balancing on Alibaba Cloud........................................................ 712
Set up Active/Passive HA on Alibaba Cloud................................................................... 715
Create HAVIP...............................................................................................................717
```
Bind an Elastic IP(EIP) Address................................................................................ 720
```
Bind an ECS Instance................................................................................................. 723
Configure Route Table...............................................................................................726
Configure the VM-Series Firewall...........................................................................727
Test the Traffic............................................................................................................ 729
Failover Testing............................................................................................................732
```
Virtual CPU (vCPU) Instance Types........................................................................733
```
VM-Series Integration with an Alibaba Gateway Load Balancer.................................735
Integrate VM-Series Firewall with Alibaba Gateway Load Balancer...............737
VM-Series Firewall on Tencent Cloud China......................................... 753
Minimum System Requirements for VM-Series on Tencent Cloud............................ 755
License the VM-Series Firewall on Tencent Cloud........................................................ 756
Deploying the VM-Series Firewall on Tencent Cloud................................................... 757
VM-Series Public Cloud Deployments 8 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on AWS
Where Can I Use This? What Do I Need?
• AWS AWS account
```
Amazon Machine Image (AMI) ID
```
```
VM-Series License (PAYG or BYOL)
```
VM-Series plugin
Panorama
Panorama plugin for AWS
```
The VM-Series firewall can be deployed in the public Amazon Web Services (AWS) cloud and
```
AWS GovCloud. It can then be configured to secure access to the applications that are deployed
```
on EC2 instances and placed into a Virtual Private Cloud (VPC) on AWS.
```
VM-Series firewall now supports subscription to Web Proxy in AWS environments.
```
The Amazon Web Service (AWS) is a public cloud service that enables you to run your
```
applications on a shared infrastructure managed by Amazon. These applications can be deployed
on scalable computing capacity or EC2 instances in different AWS regions and accessed by users
over the internet.
For networking consistency and ease of management of EC2 instances, Amazon offers the
```
Virtual Private Cloud (VPC). A VPC is apportioned from the AWS public cloud, and is assigned a
```
```
CIDR block from the private network space (RFC 1918). Within a VPC, you can carve out public
```
or private subnets for your needs and deploy the applications on EC2 instances within those
subnets. To then enable access to the applications within the VPC, you can deploy the VM-Series
firewall on an EC2 instance. The VM-Seriesfirewall can then be configured to secure traffic to and
from the EC2 instances within the VPC.
The VM-Series firewall is available in both the public AWS cloud and on AWS GovCloud. The VM-
```
Series firewall in public AWS and AWS GovCloud supports the bring your own license (BYOL)
```
```
model and the hourly Pay-As-You-Go (PAYG), the usage-based licensing model that you can avail
```
from the AWS Marketplace. For licensing details, see VM-Series License Types.
```
VM-Series firewall now supports ARM-based instances on AWS Graviton 2 (ARM
```
```
compute) instances for public clouds. All features that were available in x86 environments
```
are now extended to ARM-based instances including hypervisor support, DPDK that
```
provide better performance, while reducing the operational (OPEX) costs, power
```
consumption, and footprints. ARM architecture support is currently available on AWS
BYOL VM-Flex licensing models on the AWS R6g and AWS M6g instances for AWS
Graviton 2 instances and supports ENA drivers.
For supported instance types, see VM-Series Models on AWS EC2 Instances.
You can deploy the VM-Series firewall on an AWS instance size with more resources than the
minimum VM-Series System Requirements. If you choose a larger instance size for the VM-Series
9
VM-Series Firewall on AWS
firewall model, although the firewall only uses the max vCPU cores and memory shown in the
table, it does take advantage of the faster network performance that AWS provides. If you want
to change the instance type on your VM-Series firewall that is licensed with the BYOL option, you
must deactivate the VM before you switch the instance type to ensure that your license is valid.
See Upgrade the VM-Series firewall to know why.
For guidance with sizing the VM-Series firewall on AWS, refer to this article.
VM-Series Public Cloud Deployments 10 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on AWS
AWS Terminology
Where Can I Use This? What Do I Need?
• AWS AWS account
```
Amazon Machine Image (AMI) ID
```
```
VM-Series License (PAYG or BYOL)
```
VM-Series plugin
Panorama
Panorama plugin for AWS
This document assumes that you're familiar with the networking and configuration of the AWS
VPC. To provide context for the terms used in this section, here’s a brief refresher on the AWS
```
terms (some definitions are taken directly from the AWS glossary) that are referred to in this
```
```
document:
```
Term Description
EC2 Elastic Compute Cloud
A web service that enables you to launch and manage Linux/UNIX and
Windows server instances in Amazon's data centers.
AMI Amazon Machine Image
An AMI provides the information required to launch an instance, which
is a virtual server in the cloud.
The VM-Series AMI is an encrypted machine image that includes the
operating system required to instantiate the VM-Series firewall on an
EC2 instance.
ELB Elastic Load Balancing
ELB is an Amazon Web Service that helps you improve the availability
and scalability of your applications by routing traffic across multiple
```
Elastic Compute Cloud (EC2) instances. ELB detects unhealthy EC2
```
instances and reroutes traffic to healthy instances until the unhealthy
instances are restored. ELB can send traffic only to the primary
interface of the next hop load-balanced EC2 instance. So, to use ELB
with a VM-Series firewall on AWS, the firewall must be able to use the
primary interface for dataplane traffic.
ENI Elastic Network Interface
An additional network interface that can be attached to an EC2
instance. ENIs can include a primary private IP address, one or more
VM-Series Public Cloud Deployments 11 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on AWS
Term Description
secondary private IP addresses, a public IP address, an elastic IP
```
address (optional), a MAC address, membership in specified security
```
groups, a description, and a source/destination check flag.
IP address types for
EC2 instances
An EC2 instance can have different types of IP addresses.
• Public IP address: An IP address that can be routed across the
internet.
• Private IP address: An IP address in the private IP address range as
defined in the RFC 1918. You can choose to manually assign an IP
address or to auto assign an IP address within the range in the CIDR
block for the subnet in which you launch the EC2 instance.
If you're manually assigning an IP address, Amazon reserves the first
```
four (4) IP addresses and the last one (1) IP address in every subnet for
```
IP networking purposes.
```
• Elastic IP address (EIP): A static IP address that you have allocated
```
in Amazon EC2 or Amazon VPC and then attached to an instance.
Elastic IP addresses are associated with your account, not with a
specific instance. They are elastic because you can easily allocate,
attach, detach, and free them as your needs change.
An instance in a public subnet can have a Private IP address, a Public
```
IP address, and an Elastic IP address (EIP); an instance in a private
```
subnet will have a private IP address and optionally have an EIP.
Instance type Amazon-defined specifications that stipulate the memory, CPU,
storage capacity, and hourly cost for an instance. Some instance types
are designed for standard applications, whereas others are designed
for CPU-intensive, memory-intensive applications, and so on.
VPC Virtual Private Cloud
An elastic network populated by infrastructure, platform, and
application services that share common security and interconnection.
IGW Internet gateway provided by Amazon.
Connects a network to the internet. You can route traffic for IP
addresses outside your VPC to the internet gateway.
IAM Role Identity and Access Management
Required for enabling high availability for the VM-Series firewall
on AWS. The IAM role defines the API actions and resources the
application can use after assuming the role. On failover, the IAM Role
allows the VM-Series firewall to securely make API requests to switch
the dataplane interfaces from the active peer to the passive peer.
VM-Series Public Cloud Deployments 12 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on AWS
Term Description
An IAM role is also required for VM Monitoring. See List of Attributes
Monitored on the AWS VPC.
Subnets A segment of the IP address range of a VPC to which EC2 instances
can be attached. EC2 instances are grouped into subnets based on
your security and operational needs.
There are two types of subnets:
• Private subnet: The EC2 instances in this subnet cannot be reached
from the internet.
• Public subnet: The internet gateway is attached to the public
subnet, and the EC2 instances in this subnet can be reached from
the internet.
Security groups A security group is attached to an ENI and it specifies the list of
protocols, ports, and IP address ranges that are allowed to establish
inbound/outbound connections on the interface.
In the AWS VPC, security groups and network ACLs control
```
inbound and outbound traffic; security groups regulate
```
access to the EC2 instance, while network ACLs regulate
access to the subnet. Because you're deploying the VM-
Series firewall, set more permissive rules in your security
groups and network ACLs and allow the firewall to safely
enable applications in the VPC.
Route tables A set of routing rules that controls the traffic leaving any subnet that is
associated with the route table. A subnet can be associated with only
one route table.
Key pair A set of security credentials you use to prove your identity
electronically. The key pair consists of a private key and a public key.
At time of launching the VM-Series firewall, you must generate a
key pair or select an existing key pair for the VM-Series firewall. The
private key is required to access the firewall in maintenance mode.
CloudWatch Amazon CloudWatch is a monitoring service that allows you to collect
and track metrics for the VM-Series firewalls on AWS. When enabled,
the firewalls use AWS APIs to publish native PAN-OS metrics to
CloudWatch.
VM-Series Public Cloud Deployments 13 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on AWS
VM-Series Firewall on AWS Cloud Environments
Where Can I Use This? What Do I Need?
• AWS AWS account
```
Amazon Machine Image (AMI) ID
```
```
VM-Series License (PAYG or BYOL)
```
VM-Series plugin
Panorama
Panorama plugin for AWS
VM-Series Firewall on AWS GovCloud
AWS GovCloud is an isolated AWS region that meets the regulatory and compliance requirements
of the US government agencies and customers.
```
To secure your workloads that contain all categories of Controlled Unclassified Information (CUI)
```
```
data and government-oriented, publicly available data in the AWS GovCloud (US) Region, the
```
VM-Series firewall provides the same robust security features in the standard AWS public cloud
and on AWS GovCloud. The VM-Series firewall on AWS GovCloud and the standard AWS public
cloud support the same capabilities.
On AWS GovCloud, you can deploy VM-Series firewalls only in a horizontally scalable manner
The VM-Series firewall on AWS GovCloud must have AWS Plugin version 5.1.1 or later and PAN-
OS version 10.2.3 or later installed. Ensure that your Panorama version is same or higher than
your VM-Series PAN-OS version.
If the VM-Series firewall on AWS GovCloud is offline, you must use the CSP to input the CPU
ID, UUID, and the auth code to generate a license file that includes the serial number. You can
then install the license on the firewall. See Serial Number and CPU ID Format for the VM-Series
Firewall and VM-Series Firewall Licensing.
For more information, see AWS GovCloud AMI to Deploy the VM-Series Firewall on AWS.
VM-Series Firewall on AWS China
The VM-Series firewall is available with the BYOL option on the AWS China Marketplace, and is
```
available in the AWS China (Beijing) and the AWS China (Ningxia) regions. You must have an AWS
```
China account that’s separate from your global AWS account to access this image and use AWS
resources on AWS China.
Make sure to review the VM-Series System Requirements before Launch the VM-Series Firewall
on AWS.
VM-Series Public Cloud Deployments 14 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on AWS
VM-Series Firewall on AWS Outposts
To provide the same level of security to the workloads located on-premises as those workloads
located in the AWS cloud, you can install the VM-Series firewall on AWS on an AWS Outposts
rack at your on-premises location. Use the AWS Marketplace BYOL AMIs for your AWS region to
deploy the VM-Series firewall instances in your AWS Outposts subnets.
```
See Register the VM-Series Firewall (with auth code), to create a support account and register
```
the VM-Series firewall on the Palo Alto Networks Customer Support website for activating your
support entitlement with Palo Alto Networks.
VM-Series Public Cloud Deployments 15 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on AWS
Management Interface Mapping for Use with Amazon
ELB
Where Can I Use This? What Do I Need?
• AWS AWS account
```
Amazon Machine Image (AMI) ID
```
```
VM-Series License (PAYG or BYOL)
```
VM-Series plugin
Panorama
Panorama plugin for AWS
```
By default, the elastic network interface (ENI) eth0 maps to the MGT interface on the firewall
```
and ENI eth1 maps to ethernet 1/1 on the firewall. Because the ELB can send traffic only to the
primary interface of the next hop load-balanced EC2 instance, the VM-Series firewall must be able
to use the primary interface for dataplane traffic.
The firewall can receive dataplane traffic on the primary interface in the following scenarios
where the VM-Series firewall is behind the Amazon ELB Service:
• The VM-Series firewalls is securing traffic outbound directly to the internet without the need
for using a VPN link or a Direct Connect link back to the corporate network.
• The VM-Series firewall secures an internet-facing application when there is exactly one
backend server, such as a web server, for each firewall. The VM-Series firewalls and web
servers can scale linearly, in pairs, behind ELB.
At present, for use cases that require an ELB sandwich-type deployment to scale out
firewalls and application layer EC2 instances, swapping the management interface
will not allow you to seamlessly deploy the ELB solution. The ability to swap the
management interface only partially solves the integration with ELB.
To allow the firewall to send and receive dataplane traffic on eth0 instead of eth1, you must swap
the mapping of the ENIs within the firewall such that ENI eth0 maps to ethernet 1/1 and ENI eth1
maps to the MGT interface on the firewall as shown below.
VM-Series Public Cloud Deployments 16 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on AWS
If possible, swap the management interface before you configure the firewall or define
policy rules.
Swapping how the interfaces are mapped allows ELB to distribute and route traffic to healthy
instances of the VM-Series firewall located in the same or different Availability Zones on AWS for
increased capacity and fault tolerance.
The interface swap is only required when the VM-Series firewall is behind the Amazon ELB
Service. If your requirement is to deploy the VM-Series firewalls in a traditional high availability
setup, you don’t need to configure the interface swap that is described in this section. Continue to
High Availability for VM-Series Firewall on AWS.
To swap the interfaces, you have the following options:
• At launch—When you launch the firewall, you can either enter the mgmt-interface-
```
swap=enable command in the User data field on the AWS management console (see Launch
```
```
the VM-Series Firewall on AWS) or CLI or you can include the new mgmt-interface-swap
```
operational command in the bootstrap configuration.
• After launch—After you launch the firewall, Use the VM-Series Firewall CLI to Swap the
```
Management Interface (set system setting mgmt-interface-swap enable yes
```
```
operational command) on the firewall.
```
• To prevent unpredictable behavior on the firewall, pick one method to consistently
specify the interface swap setting—in the bootstrap configuration, from the CLI on
the firewall, or using the Amazon EC2 User data field on the AWS console.
```
• Ensure that you have access to the AWS console (management console or CLI) to
```
view the IP address of the eth1 interface. Also, verify that the AWS Security Group
```
rules allow connections (HTTPS and SSH) to the new management interface.
```
• If you configured the firewall or defined policy rules before interface swap, check
whether any IP address changes for eth0 or eth1 impact policy rules.
VM-Series Public Cloud Deployments 17 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on AWS
Performance Tuning for the VM-Series Firewall on AWS
Where Can I Use This? What Do I Need?
• AWS AWS account
```
Amazon Machine Image (AMI) ID
```
```
VM-Series License (PAYG or BYOL)
```
VM-Series plugin
Panorama
Panorama plugin for AWS
The following configurations affect performance:
PAN-OS versions 9.0.3 and earlier support AWS C5 and M5 instance types that have Elastic
Network Adapter support for SR-IOV mode by default. For more details, see Elastic Network
Adapter – High Performance Network Interface for Amazon EC2.
PAN-OS versions 9.0.4 and later provide DPDK support for C5 and M5 instance types by
default. When the firewall is in DPDK mode, it uses DPDK drivers. For a list of supported
drivers, see PacketMMAP and PDK Drivers on VM-Series Firewalls and the official DPDK
release notes.
```
To benefit from IETF RFC 8926 (Geneve) encapsulation and improved throughput, upgrade to
```
PAN-OS 10.0.2 or later and refer to VM-Series Integration with AWS Gateway Load Balancer.
Use the VM-Series CLI to view your DPDK settings or enable packed I/O.
View the DPDK Configuration on Your Firewall
STEP 1 | Log in to the VM-Series firewall CLI.
STEP 2 | View your DPDK configuration. If DPDK is enabled the output is as follows:
> show system setting dpdk-pkt-io on
Device current Packet IO mode: DPDK
Device DPDK Packet IO capable: yes
Device default Packet IO mode: DPDK
Enable DPDK Packed I/O
STEP 1 | Log in to the VM-Series firewall CLI
VM-Series Public Cloud Deployments 18 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on AWS
STEP 2 | Enable DPDK:
> set system setting dpdk-pkt-io on
STEP 3 | Reboot the device.
On the firewall, select Device > Setup > Operations and select Reboot Device.
VM-Series Public Cloud Deployments 19 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on AWS
Deploy the VM-Series Firewall on AWS
Where Can I Use This? What Do I Need?
• AWS AWS account
```
Amazon Machine Image (AMI) ID
```
```
VM-Series License (PAYG or BYOL)
```
VM-Series plugin
Panorama
Panorama plugin for AWS
The VM-Series firewall secures inbound and outbound traffic to and from EC2 instances within
```
the AWS virtual private cloud (VPC). Because the AWS VPC only supports an IP network (Layer 3
```
```
networking capabilities), the VM-Series firewall can only be deployed with Layer 3 interfaces.
```
• Deploy the VM-Series firewall to secure the EC2 instances hosted in the AWS virtual private
cloud.
If you host your applications in the AWS cloud, deploy the VM-Series firewall to protect
and safely enable applications for users who access these applications over the internet. For
example, the following diagram shows the VM-Series firewall deployed in the Edge subnet to
which the internet gateway is attached. The applications are deployed in the private subnet,
which does not have direct access to the internet.
When users need to access the applications in the private subnet, the firewall receives the
request and directs it to the appropriate application, after verifying the security policy and
performing Destination NAT. On the return path, the firewall receives the traffic, applies its
security policy and uses Source NAT to deliver the content to the user. See Use Case: Secure
the EC2 Instances in the AWS Cloud.
Figure 1: VM-Series for EC2 Instances
VM-Series Public Cloud Deployments 20 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on AWS
• Deploy the VM-Series firewall for VPN access between the corporate network and the EC2
instances within the AWS virtual private cloud.
To connect your corporate network with the applications deployed in the AWS Cloud, you can
configure the firewall as a termination point for an IPSec VPN tunnel. This VPN tunnel allows
users on your network to securely access the applications in the cloud.
For centralized management, consistent enforcement of policy across your entire network, and
for centralized logging and reporting, you can also deploy Panorama in your corporate network.
If you need to set up VPN access to multiple VPCs, using Panorama allows you to group the
firewalls by region and administer them with ease.
Figure 2: VM-Series for VPN Access
• Deploy the VM-Series firewall as a GlobalProtect gateway to secure access for remote users
using laptops. The GlobalProtect agent on the laptop connects to the gateway, and based on
the request, the gateway either sets up a VPN connection to the corporate network or routes
```
the request to the internet. To enforce security compliance for users on mobile devices (using
```
```
the GlobalProtect app ), the GlobalProtect gateway is used with the GlobalProtect Mobile
```
Security Manager. The GlobalProtect Mobile Security Manager ensures that mobile devices
are managed and configured with the device settings and account information for use with
corporate applications and networks.
In each of the use cases above, you can deploy the VM-Series firewall in an active/
```
passive high availability (HA) pair. For information on setting up the VM-Series firewall
```
in HA, see Use Case: Use Dynamic Address Groups to Secure New EC2 Instances
within the VPC.
```
• Deploy the VM-Series firewall with the Amazon Elastic Load Balancing (ELB) service, whereby
```
the firewall can receive dataplane traffic on the primary interface in the following scenarios
where the VM-Series firewall is behind the Amazon ELB:
• The VM-Series firewalls is securing traffic outbound directly to the internet without the
need for using a VPN link or a Direct Connect link back to the corporate network.
• The VM-Series firewall secures an internet-facing application when there is exactly one
backend server, such as a web server, for each firewall. The VM-Series firewalls and web
servers can scale linearly, in pairs, behind ELB.
VM-Series Public Cloud Deployments 21 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on AWS
Figure 3: VM-Series with ELB
You can't configure the firewall to send and receive dataplane traffic on eth0 when the
firewall is in front of ELB. The VM-Series firewall must be placed behind the Amazon ELB.
You can either Use the VM-Series Firewall CLI to Swap the Management Interface or
enable it on bootstrap.
In addition to the links above that are covered under the Palo Alto Networks official
support policy, Palo Alto Networks provides Community supported templates in the Palo
Alto Networks GitHub repository that allow you to explore the solutions available to
jumpstart your journey into cloud automation and scale on AWS. See AWS Transit VPC
for a hub and subscribing VPC deployment that enables you to secure traffic between
VPCs, between a VPC and an on-prem/hybrid cloud resource, and secure outbound traffic
to the internet.
```
Obtain the Amazon Machine Image (AMI)
```
Where Can I Use This? What Do I Need?
• AWS AWS account
```
Amazon Machine Image (AMI) ID
```
```
VM-Series License (PAYG or BYOL)
```
VM-Series plugin
Panorama
Panorama plugin for AWS
Get the Amazon Machine Image for the public AWS cloud and the AWS GovCloud from the
respective Marketplace.
AWS Public Cloud AMI
The AMI for the VM-Series firewall is available in the AWS Marketplace for both the Bring Your
```
Own License (BYOL) and the usage-based pricing options.
```
VM-Series Public Cloud Deployments 22 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on AWS
For purchasing licenses with the BYOL option, contact your Palo Alto Networks sales engineer or
reseller.
AWS GovCloud AMI
```
The Bring Your Own License (BYOL) model and the usage-based model of the VM-Series firewall
```
are available on the AWS GovCloud Marketplace. With a GovCloud account, you can search
for Palo Alto Networks and find the AMIs for the VM-Series firewall on the Marketplace. Make
sure to review the supported EC2 instance types before you launch the firewall. For details, see
Launch the VM-Series Firewall on AWS.
VM-Series Public Cloud Deployments 23 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on AWS
Review System Requirements and Limitations for VM-Series on AWS
Requirement Details
EC2 instance types The EC2 instance type you select must meet the VM-Series System
Requirements for the VM-Series firewall model. If you deploy the
VM-Series firewall on an EC2 instance type that does not meet these
requirements, the firewall will boot into maintenance mode
To support VM Monitoring and high availability on AWS,
the VM-Series firewall must be able to directly reach the
AWS API service endpoints without any proxy servers
between the firewall management interface and the AWS
```
API endpoints (such as ec2.us-west-2.amazonaws.com).
```
Amazon Elastic Block
```
Storage (EBS)
```
The VM-Series firewall must use the Amazon Elastic Block Storage
```
(EBS) volume for storage. EBS optimization provides an optimized
```
configuration stack and additional, dedicated capacity for Amazon EBS
I/O.
Networking Because the AWS only supports Layer 3 networking capabilities, the
VM-Series firewall can only be deployed with Layer 3 interfaces. Layer
2 interfaces, virtual wire, VLANs, and subinterfaces are not supported
on the VM-Series firewall deployed in the AWS VPC.
Interfaces Support for a total of eight interfaces is available—one management
interface and a maximum of seven Elastic Network Interfaces
```
(ENIs) for data traffic. The VM-Series firewall does not support hot
```
```
attachment of ENIs; to detect the addition or removal of an Elastic
```
Network Interface you must reboot the firewall.
Your EC2 instance type selection determines the total
number of ENIs you can enable. For example, the c3.8xlarge
```
supports eight (8) ENIs.
```
Support entitlement
and Licenses
For the Bring Your Own License model, a support account and a valid
VM-Series license are required to obtain the Amazon Machine Image
```
(AMI) file, which is required to install the VM-Series firewall in the
```
AWS VPC. The licenses required for the VM-Series firewall—capacity
license, support license, and subscriptions for Threat Prevention, URL
Filtering, WildFire, etc—must be purchased from Palo Alto Networks.
To purchase the licenses for your deployment, contact your sales
representative. See VM-Series Firewall Licenses for Public Clouds.
For the usage-based licensing model, hourly and annual pricing
bundles can be purchased and billed directly to AWS. You must
however, register your support entitlement with Palo Alto Networks.
VM-Series Public Cloud Deployments 24 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on AWS
Requirement Details
For details see, Register the Usage-Based Model of the VM-Series
```
Firewall for Public Clouds (no auth code).
```
```
Get the VM-Series Firewall Amazon Machine Image (AMI) ID
```
Where Can I Use This? What Do I Need?
• AWS AWS account
```
Amazon Machine Image (AMI) ID
```
```
VM-Series License (PAYG or BYOL)
```
VM-Series plugin
Panorama
Panorama plugin for AWS
Use the following instructions to find the AMI ID for the VM-Series firewall that matches the
PAN-OS version, license type, and AWS region in which you want to launch the VM-Series
firewall.
STEP 1 | Install AWS CLI on the client that you are using to retrieve the AMI ID, and login with your
AWS credentials.
Refer to the AWS documentation for instructions on installing the CLI.
STEP 2 | Find the AMI-ID with the following CLI command.
aws ec2 describe-images --filters "Name=product-
code,Values=<license-type-value>" Name=name,Values=PA-VM-AWS*<PAN-
OS-version>* --region <region> --output json
You need to replace the value in the angle brackets <> with the relevant information as shown
```
below:
```
• Use the VM-Series product code for each license type. The values are:
• Bundle 1—
e9yfvyj3uag5uo5j2hjikv74n
• Bundle 2—
hd44w1chf26uv4p52cdynb2o
VM-Series Public Cloud Deployments 25 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on AWS
• BYOL—
6njl1pau431dv1qxipg63mvah
• Use the PAN-OS version— 10.0. If there are multiple feature releases within a PAN-OS
version all the AMI-IDs are listed for you. For example, in 9.0.x, you will view a listing of the
AMI IDs for PAN-OS versions 9.0, 9.0.3.xfr, 9.0.5.xfr, and 9.0.6, and you can use the AMI-
ID for the PAN-OS version you need.
• Get the AWS region details from: https://docs.aws.amazon.com/general/latest/gr/
rande.html.
For example: To find the AMI-ID for the VM-Series Bundle 1 for PAN-OS 10.0.0 in US
California region, the CLI command is:
aws ec2 describe-images --filters "Name=product-
code,Values=e9yfvyj3uag5uo5j2hjikv74n" "Name=name,Values=PA-VM-
AWS*10.0*" --region us-west-1 --output json
The output is:
```
{
```
"ProductCodes": [
```
{
```
"ProductCodeId": "e9yfvyj3uag5uo5j2hjikv74n",
"ProductCodeType": "marketplace"
```
}
```
],
"VirtualizationType": "hvm",
"Hypervisor": "xen",
"ImageOwnerAlias": "aws-marketplace",
"EnaSupport": true,
"SriovNetSupport": "simple",
"ImageId": "ami-06f7a63d7481d0ded",
"State": "available",
VM-Series Public Cloud Deployments 26 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on AWS
"BlockDeviceMappings": [
```
{
```
"DeviceName": "/dev/xvda",
```
"Ebs": {
```
"SnapshotId": "snap-0009036179b39824b",
"DeleteOnTermination": false,
"VolumeType": "gp2",
"VolumeSize": 60,
"Encrypted": false
```
}
```
```
}
```
],
"Architecture": "x86_64",
"ImageLocation": "aws-marketplace/PA-VM-AWS-10.0.0-
f1260463-68e1-4bfb-bf2e-075c2664c1d7-ami-06f7a63d7481d0ded.1",
"RootDeviceType": "ebs",
"OwnerId": "679593333241",
"RootDeviceName": "/dev/xvda",
"CreationDate": "2020-07-20T12:45:22.000Z",
"Public": true,
"ImageType": "machine",
"Name": "PA-VM-AWS-10.0.0-f1260463-68e1-4bfb-
bf2e-075c2664c1d7-ami-06f7a63d7481d0ded.1"
```
}
```
You can also output to a table format. For example, to see AMI for BYOL image for PAN-OS
10.0.2:
aws ec2 describe-images --filters "Name=product-
code,Values=6njl1pau431dv1qxipg63mvah" "Name=name,Values=PA-VM-
VM-Series Public Cloud Deployments 27 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on AWS
AWS*10.0.2*" --region us-west-1 --output table --query "Images[*].
```
{Name:Name,AMI:ImageId,State:State}"
```
-----------------------------------------------------------------------------
DescribeImages
|+-----------------------
+----------------------------------------------------------------------------
+-------------+| AMI | Name
| State |+-----------------------
+----------------------------------------------------------------------------
+-------------+| ami-037b90bd9b630f594| PA-VM-
AWS-10.0.2-7064e142-2859-40a4-ab62-8b0996b842e9-
ami-07a0e94019f2a2001.4 | available |+-----------------------
+----------------------------------------------------------------------------
+-------------+
PanOS 11.1.2 and later versions support ARM CPUs in AWS. Use the following
command to find ARM AMIs:
aws ec2 describe-images --filters "Name=name,Values=PA-
VMARM-AWS*11.1.*" --region us-east-1 --output table --
```
query "Images[*].{Name:Name,AMI:ImageId,State:State}"
```
Planning Worksheet for the VM-Series in the AWS VPC
Where Can I Use This? What Do I Need?
• AWS AWS account
```
Amazon Machine Image (AMI) ID
```
```
VM-Series License (PAYG or BYOL)
```
VM-Series plugin
Panorama
Panorama plugin for AWS
For ease of deployment, plan the subnets within the VPC and the EC2 instances that you want
to deploy within each subnet. Before you begin, use the following table to collate the network
information required to deploy and insert the VM-Series firewall into the traffic flow in the VPC:
Configuration Item Value
VPC CIDR
Security Groups
```
Subnet (public) CIDR
```
VM-Series Public Cloud Deployments 28 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on AWS
Configuration Item Value
```
Subnet (private) CIDR
```
```
Subnet (public) Route Table
```
```
Subnet (private) Route Table
```
Security Groups
• Rules for Management Access
```
to the firewall (eth0/0)
```
• Rules for access to the
dataplane interfaces of the
firewall
• Rules for access to the
interfaces assigned to the
application servers.
VM-Series firewall behind ELB
```
EC2 Instance 1 (VM-Series firewall)
```
An EIP is only required
for the dataplane
interface that is
attached to the public
subnet.
```
Subnet:
```
Instance type:
Mgmt interface IP:
Mgmt interface EIP:
Dataplane interface eth1/1
• Private IP:
```
• EIP (if required):
```
• Security Group:
Dataplane interface eth1/2
• Private IP:
```
• EIP (if required):
```
• Security Group:
```
EC2 Instance 2 (Application to be
```
```
secured)
```
Repeat these set of values for
additional applications being
deployed.
```
Subnet:
```
Instance type:
Mgmt interface IP:
Default gateway:
Dataplane interface 1
• Private IP:
VM-Series Public Cloud Deployments 29 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on AWS
Configuration Item Value
Requirements for HA If you're deploying the VM-Series firewalls in a high
```
availability (active/passive) configuration, you must
```
ensure the following:
• Create an IAM role and assign the role to the VM-
Series firewall when you're deploying the instance.
See IAM Roles for HA.
• Deploy the HA peers in the same AWS availability
zone.
• The active firewall in the HA pair must have at a
minimum of three ENIs: two dataplane interfaces and
one management interface.
The passive firewall in the HA pair must have one ENI for
management, and one ENI that functions as a dataplane
```
interface; you will configure the dataplane interface as
```
an HA2 interface.
Don't attach additional dataplane interfaces
to the passive firewall in the HA pair. On
failover, the dataplane interfaces from
the previously active firewall are moved —
detached and then attached—to the now
```
active (previously passive) firewall.
```
Launch the VM-Series Firewall on AWS
Where Can I Use This? What Do I Need?
• AWS AWS account
```
Amazon Machine Image (AMI) ID
```
```
VM-Series License (PAYG or BYOL)
```
VM-Series plugin
Panorama
Panorama plugin for AWS
If you have not already registered the capacity auth code that you received with the order
fulfillment email with your support account, see Register the VM-Series Firewall. After registering,
deploy the VM-Series firewall using an AMI published in the Marketplace or Create a Custom
```
Amazon Machine Image (AMI) in the AWS VPC as follows:
```
STEP 1 | Access the AWS Console.
Log in to the AWS console and select the EC2 Dashboard.
VM-Series Public Cloud Deployments 30 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on AWS
STEP 2 | Set up the VPC for your network needs.
Whether you launch the VM-Series firewall in an existing VPC or you create a new VPC, the
VM-Series firewall must be able to receive traffic from the EC2 instances and perform inbound
and outbound communication between the VPC and the internet.
Refer to the AWS VPC documentation for instructions on creating a VPC and setting it up for
access.
For an example with a complete workflow, see Use Case: Secure the EC2 Instances in the
AWS Cloud.
1. Create a new VPC or use an existing VPC. Refer to the AWS Getting Started
documentation.
2. Verify that the network and security components are defined suitably.
• Enable communication to the internet. The default VPC includes an internet gateway,
and if you install the VM-Series firewall in the default subnet it has access to the
internet.
• Create subnets. Subnets are segments of the IP address range assigned to the VPC in
which you can launch the EC2 instances. The VM-Series firewall must belong to the
public subnet so that it can be configured to access the internet.
• Create security groups as needed to manage inbound and outbound traffic from the
EC2 instances/subnets.
• Add routes to the route table for a private subnet to ensure that traffic can be routed
across subnets and security groups in the VPC, as applicable.
3. If you want to deploy a pair of VM-Series firewalls in HA, you must define IAM Roles for
HA before you can Configure Active/Passive HA on AWS.
4. (Optional) If you're using bootstrapping to perform the configuration of your VM-Series
firewall, refer to Bootstrap the VM-Series Firewall on AWS. For more information about
bootstrapping, see Bootstrap the VM-Series Firewall.
STEP 3 | Launch the VM-Series firewall.
```
Although you can add additional network interfaces (ENIs) to the VM-Series
```
firewall when you launch, AWS releases the autoassigned Public IP address for the
management interface when you restart the firewall. Hence, to ensure connectivity to
the management interface you must assign an Elastic IP address for the management
interface, before attaching additional interfaces to the firewall.
If you want to conserve EIP addresses, you can assign one EIP address to the eth 1/1 interface
and use this interface for both management traffic and data traffic. To restrict services
VM-Series Public Cloud Deployments 31 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on AWS
permitted on the interface or limit IP addresses that can login the eth 1/1 interface, attach a
management profile to the interface.
1. On the EC2 Dashboard, click Launch Instance.
2. Select the VM-Series AMI. To get the AMI, see Obtain the AMI.
3. Launch the VM-Series firewall on an EC2 instance.
1. Choose the EC2 instance type for allocating the resources required for the firewall,
and click Next. See VM-Series System Requirements, for resource requirements.
2. Select the VPC.
3. Select the public subnet to which the VM-Series management interface will attach.
4. Select Automatically assign a public IP address. This allows you to obtain a publicly
accessible IP address for the management interface of the VM-Series firewall.
```
You can later attach an Elastic IP address to the management interface; unlike
```
the public IP address that is disassociated from the firewall when the instance is
terminated, the Elastic IP address provides persistence and can be reattached to
VM-Series Public Cloud Deployments 32 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on AWS
```
a new (or replacement) instance of the VM-Series firewall without the need to
```
reconfigure the IP address wherever you might have referenced it.
5. Select Launch as an EBS-optimized instance.
6. Add another network interface for deployments with ELB so that you can swap the
management and data interfaces on the firewall. Swapping interfaces requires a
```
minimum of two ENIs (eth0 and eth1).
```
• Expand the Network Interfaces section and click Add Device to add another
network interface.
Make sure that your VPC has more than one subnet so that you can add additional
ENIs at launch.
If you launch the firewall with only one ENI:
• The interface swap command will cause the firewall to boot into
maintenance mode.
• Reboot the firewall when you add the second ENI.
• Expand the Advanced Details section and in the User data field enter mgmt-
interface-swap=enable as text to perform the interface swap during launch.
Bootstrap Package—If you're bootstrapping the firewall with the
bootstrap package, you can also enter a semicolon separator after mgmt-
VM-Series Public Cloud Deployments 33 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on AWS
interface-swap=enable, then enter vmseries-bootstrap-aws-
```
s3bucket=<bucketname>.
```
User Data—If you're bootstrapping with user data, enter a semicolon separator
after mgmt-interface-swap=enable, and enter additional key-value pairs
according to Enter a Basic Configuration as User Data.
AWS Secret—If you're bootstrapping with an AWS secret, enter a semicolon
separator after mgmt-interface-swap=enable, and enter the secret name as a
key-value pair, as described in Bootstrap the VM-Series Firewall on AWS.
7. Accept the default Storage settings. The firewall uses a volume type SSD (gp2).
This key pair is required for first time access to the firewall. It's also required
to access the firewall in maintenance mode.
8. (Optional) Tagging. Add one or more tags to create your own metadata to identify
and group the VM-Series firewall. For example, add a Name tag with a Value that
helps you remember that the ENI interfaces have been swapped on this VM-Series
firewall.
9. Select an existing Security Group or create a new one. This security group is for
restricting access to the management interface of the firewall. At a minimum consider
enabling HTTPS and SSH access for the management interface.
10.If prompted, select an appropriate SSD option for your setup.
11.Select Review and Launch. Review that your selections are accurate and click Launch.
12.Select an existing key pair or create a new one, and acknowledge the key disclaimer.
```
13.Download and save the private key to a safe location; the file extension is .pem. You
```
cannot regenerate this key, if lost.
It takes 5-7 minutes to launch the VM-Series firewall. You can view the progress on
the EC2 Dashboard. When the process completes, the VM-Series firewall displays on
the Instances page of the EC2 Dashboard.
VM-Series Public Cloud Deployments 34 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on AWS
STEP 4 | Configure a new administrative password for the firewall.
On the VM-Series firewall CLI, you must configure a unique administrative password
before you can access the web interface of the firewall. To log in to the CLI, you require
the private key that you used to launch the firewall.
1. Use the public IP address to SSH into the Command Line Interface (CLI) of the VM-
Series firewall. You will need the private key that you used or created in 3 above to
access the CLI.
If you added an additional ENI to support deployments with ELB, you must first
create and assign an Elastic IP address to the ENI to access the CLI, see 6.
If you're using PuTTY for SSH access, you must convert the .pem format to a .ppk
format. See https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/putty.html
2. Enter the following command to log in to the firewall:
ssh-i <private_key.pem> admin@<public-ip_address>
3. Configure a new password, using the following command and follow the onscreen
```
prompts:
```
configure
set mgt-config users admin password
4. If you have a BYOL that needs to be activated, set the DNS server IP address so that
the firewall can access the Palo Alto Networks licensing server. Enter the following
command to set the DNS server IP address:
set deviceconfig system dns-setting servers primary <ip_address>
5. Commit your changes with the command:
commit
6. Terminate the SSH session.
STEP 5 | Shut down the VM-Series firewall.
1. On the EC2 Dashboard, select Instances.
2. From the list, select the VM-Series firewall and click Actions > Stop.
```
STEP 6 | Create and assign an Elastic IP address (EIP) to the ENI used for management access to the
```
firewall and reboot the VM-Series firewall.
1. Select Elastic IPs and click Allocate New Address.
2. Select EC2-VPC and click Yes, Allocate.
3. Select the newly allocated EIP and click Associate Address.
4. Select the Network Interface and the Private IP address associated with the
management interface and click Yes, Associate.
STEP 7 | Create a virtual network interface and attach the interface to the VM-Series firewall. The
```
virtual network interfaces are called Elastic Network Interfaces (ENIs) on AWS, and serve as
```
VM-Series Public Cloud Deployments 35 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on AWS
the dataplane network interfaces on the firewall. These interfaces are used for handling data
traffic to/from the firewall.
You will need at least two ENIs that allow inbound and outbound traffic to/from the firewall.
```
You can add up to seven ENIs to handle data traffic on the VM-Series firewall; check your EC2
```
instance type to verify the maximum number supported on it.
1. On the EC2 Dashboard, select Network Interfaces, and click Create Network Interface.
2. Enter a descriptive name for the interface.
3. Select the subnet. Use the subnet ID to make sure that you have selected the correct
subnet. You can only attach an ENI to an instance in the same subnet.
4. Enter the Private IP address to assign to the interface or select Auto-assign to
automatically assign an IP address within the available IP addresses in the selected
subnet.
5. Select the Security group to control access to the dataplane network interface.
6. Click Yes, Create.
7. To attach the ENI to the VM-Series firewall, select the interface you created, and click
Attach.
8. Select the Instance ID of the VM-Series firewall, and click Attach.
9. Repeat the steps above for creating and attaching at least one more ENI to the firewall.
```
STEP 8 | (Not required for the Usage-based licensing model) Activate the licenses on the VM-Series
```
firewall.
This task isn’t performed on the AWS management console. Access to the Palo Alto
Networks Customer Support Portal and the web interface of the VM-Series firewall is
required for license activation.
See Activate the License.
VM-Series Public Cloud Deployments 36 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on AWS
STEP 9 | Disable Source/Destination check on every firewall dataplane network interface. Disabling
this option allows the interface to handle network traffic that is not destined to the IP
address assigned to the network interface.
1. On the EC2 Dashboard, select the network interface, for example eth1/1, in the
Network Interfaces tab.
2. In the Action drop-down, select Change Source/Dest. Check.
3. Click Disabled and Save your changes.
4. Repeat Steps 1-3 for each firewall dataplane interface.
VM-Series Public Cloud Deployments 37 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on AWS
STEP 10 | Configure the dataplane network interfaces as Layer 3 interfaces on the firewall.
For an example configuration, see the steps 14 through 17 in Use Case: Secure the EC2
Instances in the AWS Cloud.
On the application servers within the VPC, define the dataplane network interface of
the firewall as the default gateway.
1. Using a secure connection (HTTPS) from your web browser, login using the EIP address
```
and password you assigned during initial configuration (https://<Elastic_IP address>).
```
```
You will see a certificate warning; that’s okay. Continue to the webpage.
```
2. Select Network > Interfaces > Ethernet.
3. Click the link for ethernet 1/1 and configure as follows:
• Interface Type: Layer3
• On the Config tab, assign the interface to the default router.
• On the Config tab, expand the Security Zone drop-down and select New Zone.
Define a new zone, for example VM_Series_untrust, and then click OK.
• On the IPv4 tab, select either Static or DHCP Client.
If using the Static option, click Add in the IP section, and enter the IP address and
network mask for the interface, for example 10.0.0.10/24.
Make sure that the IP address matches the ENI IP address that you assigned earlier.
```
If using DHCP, select DHCP Client; the private IP address that you assigned to the
```
ENI in the AWS management console will be automatically acquired.
4. Click the link for ethernet 1/2 and configure as follows:
• Interface Type: Layer3
• Security Zone: VM_Series_trust
• IP address: Select the Static or DHCP Client radio button.
For static, click Add in the IP section, and enter the IP address and network mask for
the interface. Make sure that the IP address matches the attached ENI IP address that
you assigned earlier.
5. Click Commit. Verify that the link state for the interfaces is up.
For DHCP, clear the Automatically create default route to default gateway
provided by server check box. For an interface that is attached to the private
subnet in the VPC, disabling this option ensures that traffic handled by this
interface does not flow directly to the internet gateway on the VPC.
VM-Series Public Cloud Deployments 38 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on AWS
STEP 11 | Create NAT rules to allow inbound and outbound traffic from the servers deployed within
the VPC.
1. Select Policies > NAT on the web interface of the firewall.
2. Create a NAT rule to allow traffic from the dataplane network interface on the firewall
to the web server interface in the VPC.
3. Create a NAT rule to allow outbound access for traffic from the web server to the
internet.
STEP 12 | Create security policies to allow or deny traffic to/from the servers deployed within the VPC.
1. Select Policies > Security on the web interface of the firewall.
2. Click Add, and specify the zones, applications, and logging options that you would like to
execute to restrict and audit traffic traversing through the network.
STEP 13 | Commit the changes on the firewall.
Click Commit.
STEP 14 | Verify that the VM-Series firewall is securing traffic and that the NAT rules are in effect.
1. Select Monitor > Logs > Traffic on the web interface of the firewall.
2. View the logs to make sure that the applications traversing the network match the
security policies you implemented.
Launch the VM-Series Firewall on AWS Outpost
Where Can I Use This? What Do I Need?
• AWS AWS account
```
Amazon Machine Image (AMI) ID
```
```
VM-Series License (PAYG or BYOL)
```
VM-Series Public Cloud Deployments 39 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on AWS
Where Can I Use This? What Do I Need?
VM-Series plugin
Panorama
Panorama plugin for AWS
Follow this procedure to deploy the VM-Series firewall on an AWS Outpost rack. If you have not
already registered the capacity auth code that you received with the order fulfillment email, with
your support account, see Register the VM-Series Firewall.
STEP 1 | Access the AWS Outposts Console.
STEP 2 | Extend your VPC to include your AWS Outpost rack.
The VM-Series firewall must be able to receive traffic from the EC2 instances and perform
inbound and outbound communication between the VPC and the internet.
Refer to the AWS Outpost documentation for instructions on connecting your Outpost to your
VPC.
1. Verify that the network and security components are defined suitably.
• Enable communication to the internet. The Outpost requires a local gateway to
connect to your local LAN and the internet.
• Create an Outpost subnet.
• Create security groups as needed to manage inbound and outbound traffic from the
EC2 instances/subnets.
• Add routes to the route table for a private subnet to ensure that traffic can be routed
across subnets and security groups in the VPC, as applicable.
2. If you want to deploy a pair of VM-Series firewalls in HA, you must define IAM Roles for
HA before you can configure High Availability for VM-Series Firewall on AWS.
3. (Optional) If you're using bootstrapping to perform the configuration of your VM-Series
firewall, refer to Bootstrap the VM-Series Firewall on AWS. For more information about
bootstrapping, see Bootstrap the VM-Series Firewall.
STEP 3 | Launch the VM-Series firewall.
```
Although you can add additional network interfaces (ENIs) to the VM-Series
```
firewall when you launch, AWS releases the autoassigned Public IP address for the
management interface when you restart the firewall. Hence, to ensure connectivity to
the management interface you must assign an Elastic IP address for the management
interface, before attaching additional interfaces to the firewall.
If you want to conserve EIP addresses, you can assign one EIP address to the eth 1/1 interface
and use this interface for both management traffic and data traffic. To restrict services
VM-Series Public Cloud Deployments 40 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on AWS
permitted on the interface or limit IP addresses that can login the eth 1/1 interface, attach a
management profile to the interface.
1. On the EC2 Dashboard, click Launch Instance.
2. Select the VM-Series AMI. To get the AMI, see Obtain the AMI.
3. Launch the VM-Series firewall on an EC2 instance.
1. Choose the EC2 instance type for allocating the resources required for the firewall,
and click Next. See VM-Series System Requirements, for resource requirements.
2. Select the VPC.
3. Select the public subnet on Outpost to which the VM-Series management interface
will attach.
4. Select Automatically assign a public IP address. This allows you to obtain a publicly
accessible IP address for the management interface of the VM-Series firewall.
```
You can later attach an Elastic IP address to the management interface; unlike
```
the public IP address that is disassociated from the firewall when the instance is
terminated, the Elastic IP address provides persistence and can be reattached to
VM-Series Public Cloud Deployments 41 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on AWS
```
a new (or replacement) instance of the VM-Series firewall without the need to
```
reconfigure the IP address wherever you might have referenced it.
5. Select Launch as an EBS-optimized instance.
6. Add another network interface for deployments with ELB so that you can swap the
management and data interfaces on the firewall. Swapping interfaces requires a
```
minimum of two ENIs (eth0 and eth1).
```
• Expand the Network Interfaces section and click Add Device to add another
network interface.
Make sure that your VPC has more than one subnet so that you can add additional
ENIs at launch.
If you launch the firewall with only one ENI:
• The interface swap command will cause the firewall to boot into
maintenance mode.
• Reboot the firewall when you add the second ENI.
• Expand the Advanced Details section and in the User data field enter mgmt-
interface-swap=enable as text to perform the interface swap during launch.
If you're bootstrapping the firewall, you can also enter vmseries-
bootstrap-aws-s3bucket=<bucketname> with a comma
separator after mgmt-interface-swap=enable.
7. Accept the default Storage settings. The firewall uses a volume type SSD (gp2)
This key pair is required for first-time access to the firewall. It's also required
to access the firewall in maintenance mode.
8. (Optional) Tagging. Add one or more tags to create your own metadata to identify
and group the VM-Series firewall. For example, add a Name tag with a Value that
VM-Series Public Cloud Deployments 42 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on AWS
helps you remember that the ENI interfaces have been swapped on this VM-Series
firewall.
9. Select an existing Security Group or create a new one. This security group is for
restricting access to the management interface of the firewall. At a minimum, consider
enabling HTTPS and SSH access for the management interface.
10.If prompted, select an appropriate SSD option for your setup.
11.Select Review and Launch. Review that your selections are accurate and click Launch.
12.Select an existing key pair or create a new one, and acknowledge the key disclaimer.
```
13.Download and save the private key to a safe location; the file extension is .pem. You
```
can't regenerate this key, if lost.
It takes 5-7 minutes to launch the VM-Series firewall. You can view the progress on
the EC2 Dashboard. When the process completes, the VM-Series firewall displays on
the Instances page of the EC2 Dashboard.
STEP 4 | Configure a new administrative password for the firewall.
On the VM-Series firewall CLI, you must configure a unique administrative password
before you can access the web interface of the firewall. To log in to the CLI, you require
the private key that you used to launch the firewall.
1. Use the public IP address to SSH into the Command Line Interface (CLI) of the VM-
Series firewall. You will need the private key that you used or created in the Step 3
above to access the CLI.
If you added an additional ENI to support deployments with ELB, you must first
create and assign an Elastic IP address to the ENI to access the CLI, see Step 6.
If you're using PuTTY for SSH access, you must convert the .pem format to a .ppk
format. See https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/putty.html
2. Enter the following command to log in to the firewall:
ssh-i <private_key.pem> admin@<public-ip_address>
3. Configure a new password, using the following command and follow the onscreen
```
prompts:
```
configure
set mgt-config users admin password
4. If you have a BYOL that needs to be activated, set the DNS server IP address so that
the firewall can access the Palo Alto Networks licensing server. Enter the following
command to set the DNS server IP address:
set deviceconfig system dns-setting servers primary <ip_address>
5. Commit your changes with the command:
commit
6. Terminate the SSH session.
VM-Series Public Cloud Deployments 43 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on AWS
STEP 5 | Shut down the VM-Series firewall.
1. On the EC2 Dashboard, select Instances.
2. From the list, select the VM-Series firewall and click Actions > Stop.
```
STEP 6 | Create and assign an Elastic IP address (EIP) to the ENI used for management access to the
```
firewall and reboot the VM-Series firewall.
1. Select Elastic IPs and click Allocate New Address.
2. Select EC2-VPC and click Yes, Allocate.
3. Select the newly allocated EIP and click Associate Address.
4. Select the Network Interface and the Private IP address associated with the
management interface and click Yes, Associate.
STEP 7 | Create a virtual network interface and attach the interface to the VM-Series firewall. The
```
virtual network interfaces are called Elastic Network Interfaces (ENIs) on AWS, and serve as
```
VM-Series Public Cloud Deployments 44 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on AWS
the dataplane network interfaces on the firewall. These interfaces are used for handling data
traffic to/from the firewall.
You will need at least two ENIs that allow inbound and outbound traffic to/from the firewall.
```
You can add up to seven ENIs to handle data traffic on the VM-Series firewall; check your EC2
```
instance type to verify the maximum number supported on it.
1. On the EC2 Dashboard, select Network Interfaces, and click Create Network Interface.
2. Enter a descriptive name for the interface.
3. Select the subnet. Use the subnet ID to make sure that you have selected the correct
subnet. You can only attach an ENI to an instance in the same subnet.
4. Enter the Private IP address to assign to the interface or select Autoassign to
automatically assign an IP address within the available IP addresses in the selected
subnet.
5. Select the Security group to control access to the dataplane network interface.
6. Click Yes, Create.
7. To attach the ENI to the VM-Series firewall, select the interface you created, and click
Attach.
8. Select the Instance ID of the VM-Series firewall, and click Attach.
9. Repeat the steps above for creating and attaching at least one more ENI to the firewall.
```
STEP 8 | (Not required for the Usage-based licensing model) Activate the licenses on the VM-Series
```
firewall.
This task isn’t performed on the AWS management console. Access to the Palo Alto
Networks Customer Support Portal and the web interface of the VM-Series firewall is
required for license activation.
See Activate the License.
VM-Series Public Cloud Deployments 45 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on AWS
STEP 9 | Disable Source/Destination check on every firewall dataplane network interface. Disabling
this option allows the interface to handle network traffic that is not destined to the IP
address assigned to the network interface.
1. On the EC2 Dashboard, select the network interface, for example eth1/1, in the
Network Interfaces tab.
2. In the Action drop-down, select Change Source/Dest. Check.
3. Click Disabled and Save your changes.
4. Repeat Steps 1-3 for each firewall dataplane interface.
VM-Series Public Cloud Deployments 46 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on AWS
STEP 10 | Configure the dataplane network interfaces as Layer 3 interfaces on the firewall.
For an example configuration, see the steps 14 through 17 in Use Case: Secure the EC2
Instances in the AWS Cloud.
On the application servers within the VPC, define the dataplane network interface of
the firewall as the default gateway.
1. Using a secure connection (HTTPS) from your web browser, login using the EIP address
```
and password you assigned during initial configuration (https://<Elastic_IP address>).
```
```
You will see a certificate warning; that’s okay. Continue to the webpage.
```
2. Select Network > Interfaces > Ethernet.
3. Click the link for ethernet 1/1 and configure as follows:
• Interface Type: Layer3
• On the Config tab, assign the interface to the default router.
• On the Config tab, expand the Security Zone drop-down and select New Zone.
Define a new zone, for example VM_Series_untrust, and then click OK.
• On the IPv4 tab, select either Static or DHCP Client.
If using the Static option, click Add in the IP section, and enter the IP address and
network mask for the interface, for example 10.0.0.10/24.
Make sure that the IP address matches the ENI IP address that you assigned earlier.
```
If using DHCP, select DHCP Client; the private IP address that you assigned to the
```
ENI in the AWS management console will be automatically acquired.
4. Click the link for ethernet 1/2 and configure as follows:
• Interface Type: Layer3
• Security Zone: VM_Series_trust
• IP address: Select the Static or DHCP Client radio button.
For static, click Add in the IP section, and enter the IP address and network mask for
the interface. Make sure that the IP address matches the attached ENI IP address that
you assigned earlier.
5. Click Commit. Verify that the link state for the interfaces is up.
For DHCP, clear the Automatically create default route to default gateway
provided by server check box. For an interface that is attached to the private
subnet in the VPC, disabling this option ensures that traffic handled by this
interface does not flow directly to the internet gateway on the VPC.
VM-Series Public Cloud Deployments 47 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on AWS
STEP 11 | Create NAT rules to allow inbound and outbound traffic from the servers deployed within
the VPC.
1. Select Policies > NAT on the web interface of the firewall.
2. Create a NAT rule to allow traffic from the dataplane network interface on the firewall
to the web server interface in the VPC.
3. Create a NAT rule to allow outbound access for traffic from the web server to the
internet.
STEP 12 | Create security policies to allow or deny traffic to/from the servers deployed within the VPC.
1. Select Policies > Security on the web interface of the firewall.
2. Click Add, and specify the zones, applications, and logging options that you would like to
execute to restrict and audit traffic traversing through the network.
STEP 13 | Commit the changes on the firewall.
Click Commit.
STEP 14 | Verify that the VM-Series firewall is securing traffic and that the NAT rules are in effect.
1. Select Monitor > Logs > Traffic on the web interface of the firewall.
2. View the logs to make sure that the applications traversing the network match the
security policies you implemented.
```
Create a Custom Amazon Machine Image (AMI)
```
Where Can I Use This? What Do I Need?
• AWS AWS account
```
Amazon Machine Image (AMI) ID
```
```
VM-Series License (PAYG or BYOL)
```
VM-Series Public Cloud Deployments 48 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on AWS
Where Can I Use This? What Do I Need?
VM-Series plugin
Panorama
Panorama plugin for AWS
A custom VM-Series AMI gives you the consistency and flexibility to deploy a VM-Series firewall
with the PAN-OS version you want to use on your network, instead of restricting to using only
an AMI that is published to the AWS public Marketplace or to the AWS GovCloud Marketplace.
Using a custom AMI speeds up the process of deploying a firewall with the PAN-OS version of
your choice because it reduces the time to provision the firewall with an AMI published on the
AWS public or AWS GovCloud marketplace, and then performing software upgrades to get to the
PAN-OS version you have qualified or want to use on your network.
You can create a custom AMI with the BYOL, Bundle 1, or Bundle 2 licenses. The process of
creating a custom AMI requires you to remove all configuration from the firewall and reset it
to factory defaults. In this workflow, you’ll launch a new instance of the firewall from the AWS
Marketplace instead of using an existing firewall that you have fully configured.
When creating a custom AMI with a BYOL version of the firewall, you must first activate
the license on the firewall. This allows you to access and download PAN-OS software
updates to upgrade your firewall. You then have to deactivate the license on the firewall
before you reset the firewall to factory defaults and create the custom AMI. If you don’t
deactivate the license, you lose the license that you applied on this firewall instance.
STEP 1 | Launch the VM-Series firewall from the Marketplace.
See 3
```
STEP 2 | (Only for BYOL) Activate the license.
```
STEP 3 | Install software updates and upgrade the firewall to the PAN-OS version you plan to use.
```
STEP 4 | (Only for BYOL) Deactivate the license.
```
STEP 5 | Perform a private data reset.
A private data reset removes all logs and restores the default configuration.
The system disks are not erased, so the content updates from step 4 are intact.
1. Access the firewall CLI.
2. Remove all logs and restore the default configuration.
request system private-data-reset shutdown
Enter y to confirm.
Wait for firewall to shutdown.
VM-Series Public Cloud Deployments 49 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on AWS
STEP 6 | Create the custom AMI while the system is shutdown.
1. Log in to the AWS Console and select the EC2 Dashboard.
2. Stop the VM-Series firewall.
3. Select the VM-Series firewall instance, and click Image > Create Image.
4. Enter a custom image name, and click Create Image.
The disk space of 60 GB is the minimum requirement.
5. Verify that the custom AMI is created and has the correct product code.
1. On the EC2 Dashboard, select AMI.
2. Select the AMI that you created. Depending on whether you selected an AMI
with the BYOL, Bundle 1, or Bundle 2 licensing options, you should see one of the
following Product Codes in the details:
• BYOL—6njl1pau431dv1qxipg63mvah
• Bundle 1—6kxdw3bbmdeda3o6i1ggqt4km
• Bundle 2—806j2of0qy5osgjjixq9gqc6g
VM-Series Public Cloud Deployments 50 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on AWS
STEP 7 | Encrypt EBS Volume for the VM-Series Firewall on AWS.
STEP 8 | Configure the administrative password on the firewall.
See 4
Encrypt EBS Volume for the VM-Series Firewall on AWS
Where Can I Use This? What Do I Need?
• AWS AWS account
```
Amazon Machine Image (AMI) ID
```
```
VM-Series License (PAYG or BYOL)
```
VM-Series plugin
Panorama
Panorama plugin for AWS
EBS encryption is available for all AWS EC2 instance types on which you can deploy the VM-
Series firewall. To securely store data on the VM-Series firewall on AWS, you must first create
an EBS-backed EC2 instance from a VM-Series image that is published on the AWS public or
GovCloud Marketplace, or from a custom AMI. During instance creation, select the option to
```
encrypt the EBS volume with an AWS KMS (Key Management Service) key. You may choose
```
to use the default master key for your AWS account or any KMS key that you have previously
created using the AWS Key Management Service.
STEP 1 | Create an encryption key on AWS or skip this step if you want to use the default master key
for your account.
You will use this key to encrypt the EBS volume on the firewall. Note that the key is region
specific.
VM-Series Public Cloud Deployments 51 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on AWS
STEP 2 | To encrypt an EBS volume:
1. Launch an Amazon EC2 instance.
2. Specify your EBS volumes- If you are using an unencrypted AMI, the encryption
properties will be listed as Not Encrypted.
3. Select an AWS KMS key for encrypting the volume. You may select the same KMS key
for each volume that you want to create, or you may use a different KMS key for each
volume.
4. Select Review and launch the instance. Your instance will launch with an encrypted
Amazon EBS volume that uses the KMS key you selected.
For information on encrypting existing EBS volumes, see Encrypting an existing EBS volume.
Use the VM-Series Firewall CLI to Swap the Management
Interface
Where Can I Use This? What Do I Need?
• AWS AWS account
```
Amazon Machine Image (AMI) ID
```
```
VM-Series License (PAYG or BYOL)
```
VM-Series plugin
Panorama
VM-Series Public Cloud Deployments 52 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on AWS
Where Can I Use This? What Do I Need?
Panorama plugin for AWS
```
If you did not swap the management interface (MGT) with the dataplane interface (ethernet 1/1)
```
when deploying the firewall, you can use the CLI to enable the firewall to receive dataplane traffic
on the primary interface after launching the firewall.
STEP 1 | Complete steps 1 through 7 in Launch the VM-Series Firewall on AWS.
```
Before you proceed, verify that the firewall has a minimum of two ENIs (eth0 and
```
```
eth1). If you launch the firewall with only one ENI, the interface swap command will
```
cause the firewall to boot into maintenance mode.
STEP 2 | On the EC2 Dashboard, view the IP address of the eth1 interface and verify that the AWS
```
Security Group rules allow connections (HTTPS and SSH) to the new management interface
```
```
(eth1).
```
STEP 3 | Log in to the VM-Series firewall CLI and enter the following command:
set system setting mgmt-interface-swap enable yes
STEP 4 | Confirm that you want to swap the interface and use the eth1 dataplane interface as the
management interface.
STEP 5 | Reboot the firewall for the swap to take effect. Use the following command:
request restart system
STEP 6 | Verify that the interfaces have been swapped. Use the following command:
debug show vm-series interfaces all
Phoenix_interface Base-OS_port Base-OS_MAC PCI-ID
Driver
```
mgt(interface-swap) eth0 0e:53:96:91:ef:29 0000:00:04.0
```
ixgbevf
Ethernet1/1 eth1 0e:4d:84:5f:7f:4d 0000:00:03.0
ixgbevf
Enable CloudWatch Monitoring on the VM-Series Firewall
Where Can I Use This? What Do I Need?
• AWS AWS account
```
Amazon Machine Image (AMI) ID
```
```
VM-Series License (PAYG or BYOL)
```
VM-Series plugin
Panorama
Panorama plugin for AWS
VM-Series Public Cloud Deployments 53 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on AWS
The VM-Series firewall on AWS can publish native PAN-OS metrics to AWS CloudWatch, which
you can use to monitor the firewalls. These metrics allow you to assess performance and usage
patterns that you can use to take action for launching or terminating instances of the VM-Series
firewalls.
The firewalls use AWS APIs to publish the metric to a namespace, which is the location on AWS
where the metrics are collected at a specified time interval. When you configure the firewalls to
publish metrics to AWS CloudWatch, there are two namespaces where you can view metrics—
the primary namespace collects and aggregates the selected metric for all instances configured to
use the namespace, and the secondary namespace that is automatically created with the suffix
_dimensions allows you to filter the metrics using the hostname and AWS instance ID metadata
```
(or dimensions) and get visibility into the usage and performance of individual VM-Series firewalls.
```
You can monitor the metric in CloudWatch or create auto scaling policies to trigger alarms and
take an action to manually deploy a new instance of the firewall when the monitored metric
```
reaches a threshold value. Refer to the AWS CloudWatch and Auto Scaling Groups (ASG)
```
documentation on best practices for setting the alarm conditions for a scale-out or scale in action.
For a description on the PAN-OS metrics that you can publish to CloudWatch, see Custom PAN-
OS Metrics Published for Monitoring.
VM-Series Public Cloud Deployments 54 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on AWS
```
STEP 1 | Assign the appropriate permissions for the AWS Identity and Access Management (IAM) user
```
role that you use to deploy the VM-Series firewall on AWS.
Whether you launch a new instance of the VM-Series firewall or upgrade an existing VM-
Series firewall on AWS, the IAM role associated with your instance, must have permissions to
publish metrics to CloudWatch.
1. On the AWS console, select IAM.
2. Edit the IAM role to grant the following permissions:
You can copy and the paste the permissions here:
```
{
```
"Version": "2012-10-17",
"Statement": [
```
{
```
"Effect": "Allow",
"Action": [
"cloudwatch:PutMetricData"
],
"Resource": [
"*"
]
```
}
```
]
```
}
```
VM-Series Public Cloud Deployments 55 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on AWS
STEP 2 | Enable CloudWatch on the VM-Series firewall on AWS.
1. Log in to the web interface on the VM-Series firewall
2. Select Device > VM-Series.
3. In AWS CloudWatch Setup, click Edit ( ) and select Enable CloudWatch Monitoring.
1. Enter the CloudWatch Namespace to which the firewall can publish metrics. The
namespace can't begin with AWS.
The aggregated metrics for all VM-Series firewall in an HA pair or auto scaling
deployment are published to the namespace you entered above. The namespace
with the _dimensions suffix that is automatically created enables you to filter and
view metrics for a specific VM-Series firewall using the hostname or AWS instance ID
metadata attached to the firewall.
2. Set the Update Interval to a value between 1-60 minutes. This is the frequency at
which the firewall publishes the metrics to CloudWatch. The default is 5 minutes.
4. Commit the changes.
Until the firewall starts to publish metrics to CloudWatch, you can't configure alarms for
PAN-OS metrics.
VM-Series Public Cloud Deployments 56 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on AWS
STEP 3 | Verify that you can see the metrics on CloudWatch.
1. On the AWS console, select CloudWatch > Metrics, to view CloudWatch metrics by
category.
2. From the Custom Metrics drop-down, select the namespace.
3. Verify that you can see PAN-OS metrics in the viewing list.
To filter by hostname or AWS Instance ID of a specific firewall, select _dimensions.
VM-Series Public Cloud Deployments 57 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on AWS
STEP 4 | Configure alarms and action for PAN-OS metrics on CloudWatch.
Refer to the AWS documentation: http://docs.aws.amazon.com/AmazonCloudWatch/latest/
monitoring/AlarmThatSendsEmail.html
A VM-Series firewall with bootstrap configuration will take about 7-9 minutes to be available
for service. So, here are some examples on how to set alarms that trigger auto scaling for the
VM-Series firewall:
• If you have deployed 2 instances of the VM-Series firewalls as Global Protect Gateways
that secure remote users, use the GlobalProtect Gateway Active Tunnels metric. You
can configure an alarm for when the number of active tunnels is greater than 300 for 15
minutes, you can deploy 2 new instances of the VM-Series firewall, which are bootstrapped
and configured to serve as Global Protect Gateways.
• If you are using the firewall to secure your workloads in AWS, use the Session Utilization
metric to scale in or scale out the firewall based on resource usage. You can configure an
alarm for when the session utilization metric is greater than 60% for 15 minutes, to deploy
one instance of the VM-Series instance firewall. And conversely, if Session Utilization is less
than 50% for 30 minutes, terminate an instance of the VM-Series firewall.
VM-Series Public Cloud Deployments 58 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on AWS
Publish ENA Network Performance Metrics to AWS CloudWatch
Where Can I Use This? What Do I Need?
• AWS AWS account
```
Amazon Machine Image (AMI) ID
```
```
VM-Series License (PAYG or BYOL)
```
VM-Series plugin
Panorama
Panorama plugin for AWS
The ENA network performance metrics on AWS provide enhanced visibility into the limitations
and performance of your network adapter within the AWS environment. By integrating with
```
AWS CloudWatch, you can monitor key metrics such as bandwidth and packets per second (PPS).
```
These metrics are published every five minutes from the configured VM-Series firewall to AWS
CloudWatch, enabling you to optimize VM instance sizing, plan scaling activities, and gain insights
into the network performance of your VM-Series instances. With real-time performance data, you
can streamline troubleshooting and improve operational monitoring.
Prerequisites
Following are the prerequisites to enable ENA performance metrics to AWS CloudWatch:
• PAN-OS version 11.2.5 or above
• VM-Series Plugin version 5.1.6 or above
• An IAM role to the AWS instance with read/write privileges to AWS CloudWatch Metrics and
for other CloudWatch configurations.
The ENA Network performance metrics publishing to AWS CloudWatch is disabled, by
default. Each metric costs $0.33 per month per interface. To avoid additional costs,
metrics are disabled by default and you must enable it explicitly.
Enable or Disable ENA metrics using CLI Commands:
Run the following commands to enable or disable ENA metrics using CLI commands:
To enable:
request plugins vm_series aws ena-performance-metric enable yes
To disable:
request plugin vm_series aws ena-performance-metrics enable no
Enable/Disable ENA metrics using Bootstrap Command:
For auto-scaling or initial configuration, include the following bootstrap command:
plugin-op-command = ena_perf_metrics:enable
VM-Series Public Cloud Deployments 59 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on AWS
Enable/Disable ENA metrics using VM-Series web interface:
You can enable or disable ENA metrics on VM-Series web interface. For more information, see
Enable CloudWatch Monitoring on the VM-Series Firewall.
Debugging and Verifying CloudWatch publication status
Check plugin_vm_series.log for CloudWatch publication status and confirm metric updates
every minute when enabled.
To verify, run the following command:
debug dataplane pow status | match "extended statistics\|_allowance"
VM-Series Firewall Startup and Health Logs on AWS
Where Can I Use This? What Do I Need?
• AWS AWS account
```
Amazon Machine Image (AMI) ID
```
```
VM-Series License (PAYG or BYOL)
```
VM-Series plugin
Panorama
Panorama plugin for AWS
To aid in debugging deployment issues, the VM-Series firewall provides system logs during the
system startup. After the system boots successfully, the firewall can generate status messages for
system events and can report changes in system resources as health status. Messages are logged
to the VM-Series firewall console at /dev/ttyS0 and /dev/tty0.
If you correctly configure your environment, you can also use the AWS CloudWatch service to
view logs for VM-Series firewalls deployed in AWS.
View VM-Series Firewall Logs in CloudWatch
To view VM-Series firewall logs in CloudWatch, the firewall must, at minimum, be running the
VM-Series plugin version that supports system messages, as noted in the Compatibility Matrix.
• Ensure your AWS environment is up to date, and that Boto3 is available.
VM-Series Public Cloud Deployments 60 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on AWS
• Create an IAM role and policy that permits VM-Series firewalls to create a log group and a log
stream in CloudWatch, and write log events to the log stream.
To ensure that CloudWatch can display VM-Series firewall logs, your IAM role must include a
policy that allows the following actions:
"logs:CreateLogGroup", "logs:CreateLogStream", "logs:PutLogEvents"
• Ensure the VM-Series plugin version supports firewall startup and health logs, as specified in
the Compatibility Matrix.
The VM-Series plugin includes a logging script that connects to the AWS CloudWatch service.
1. The script creates the log group PaloAltoNetworksFirewalls. All VM-Series firewall instances in
your deployment use this log group.
2. The script creates a log stream unique to your VM-Series firewall. Each of your firewalls
configure CloudWatch has its own log stream based on the firewall’s instance ID.
3. When an event is logged, the log message and timestamp are sent to the log group using the
firewall’s log stream.
VM-Series Firewall System Messages
To aid in debugging, the VM-Series firewall provides system messages during the system startup.
After the system starts, the firewall can generate status messages to report system health. Critical
health events or errors are always reported, and you can enable periodic health messages to log
the system status at an interval you choose.
Message Format
The log message format is as follows:
Log level : Resource : State : Details
• Log level
• CRITICAL
• ERROR
• INFO
Each CRITICAL or ERROR event has a unique MSGID in the logs. If you have enabled Periodic
Health Messages, the MSGID helps you distinguish new CRITICAL or ERROR messages from
unresolved issues you have seen before.
Log level : Resource : State : MSGID : Details
A health status ERROR will include an error code. For example:
```
ERROR : HA : DOWN : MSGID : HA status <>
```
VM-Series Public Cloud Deployments 61 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on AWS
• Resource
• BOOTSTRAP
• CONTENT
• HA
• INTERFACE
• LICENSE
• MGMTINTERFACE
• PANORAMA
• PANOS
• PERIODIC_STATUS
• SYSTEM
• State
• START/READY
• COMPLETE/FAIL
• UP/DOWN
• HEALTHY/UNHEALTHY
• Details—The details are typically passed on from the resource.
System Startup Messages
The following list is loosely ordered according to system startup events. However, the order can
change as events occur.
• Base OS start and network initialization
```
INFO : SYSTEM : START : Palo Alto Networks Firewall Initializing
```
• PAN-OS bootstrap
```
INFO : BOOTSTRAP : COMPLETE : Firewall Successfully Bootstrapped
```
or
```
ERROR : BOOTSTRAP : FAIL : MSGID : Firewall bootstrap failureError -
```
<>
```
• Management interface swap (if applicable)
```
```
INFO : MGMTINTERFACE : COMPLETE : Firewall Interface Swap Configured
```
or
```
ERROR : MGMTINTERFACE : MSGID : COMPLETE : Firewall Interface Swap
```
failed <>
VM-Series Public Cloud Deployments 62 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on AWS
• PAN-OS start
```
INFO : PANOS : START : Firewall version <x,yz> Starting
```
or
```
CRITICAL : PANOS : FAIL: MSGID : Firewall failed to start version
```
<x,yz>
```
INFO : SYSTEM : START : Palo Alto Networks Firewall Initializing
```
• Load license
```
INFO : LICENSE : COMPLETE : Firewall successfully licensed <model>
```
or
```
CRITICAL : LICENSE : FAIL : MSGID : Firewall failed to license
```
<reason>
• Load content
```
INFO : CONTENT : COMPLETE : Firewall content version <> loaded.
```
or
```
ERROR : CONTENT : FAIL : MSGID : Firewall content version <> failed
```
to load.
• Dataplane processes up, and auto commit
```
INFO : COMMIT : COMPLETE : Auto-commit job successful.Firewall
```
license - <model>
or
```
CRITICAL : COMMIT : FAIL: Auto-commit job failed <reason>.
```
```
• Panorama registration, Panorama connected (if applicable)
```
```
INFO : PANORAMA : COMPLETE: Connected to Panorama <IP>
```
or
```
ERROR : PANORAMA : FAIL : MSGID: Failed to connect to Panorama <IP>
```
• System ready and interfaces up
```
INFO : SYSTEM : READY : Firewall ready to process traffic.Firewall
```
license - <model>
Health Status Messages
Health messages report the status of a resource. After a successful system startup, all system
health events are set to Up, and subsequent state changes are reported. As mentioned in Message
Format, health status ERROR messages will contain a status code. In the sample messages below,
<> is a place holder for the status code.
If an administrator performs an intentional shutdown, the shutdown isn’t reported.
VM-Series Public Cloud Deployments 63 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on AWS
• CloudLoggingConnectionFailed
```
If there are no CloudWatch logs (due to connection failure), you can check the PAN-OS log
```
vm_cloud_logging.log.
• Data path interface failure
```
Message: ERROR : INTERFACE : DOWN : MSGID : Interface <> went down
```
```
• HA interface failure—This message applies to a single firewall; it does not imply anything
```
about the health of the HA pair. For example, the primary firewall state can be UP when the
secondary is down.
```
INFO : HA : UP : HA status <>
```
or
```
ERROR : HA : DOWN : MSGID : HA status <>
```
• Peer HA interface failure—This message is the status of the peer in the HA pair.
```
ERROR : PEER_HA : UP : Peer HA status <>
```
or
```
ERROR : PEER_HA : DOWN : MSGID : Peer HA status <>
```
• Panorama Connectivity
```
ERROR : PANORAMA : DOWN : MSGID : Lost Panorama <IP> connectivity
```
or
```
INFO : PANORAMA : UP : Panorama <IP> connected
```
Periodic Health Messages
When there are no health changes, you can choose to generate a periodic health status message.
```
By default, the cloud logging interval is 0 (no messages).
```
For example, if your status remains up, the message is:
```
INFO : PERIODIC_STATUS : HEALTHY : All resources healthy
```
If unresolved health failures exist, the periodic message reprints them. As mentioned in Message
Format, the MSGID helps you distinguish between errors when you're viewing periodic logs.
```
INFO : PERIODIC_STATUS : UNHEALTHY : Resources unhealthy
```
```
ERROR : INTERFACE : DOWN : MSGID : Interface ethernet1/2 down
```
• Set the periodic interval from 10 to 300 seconds
• CLI:
request plugins vm_series cloud-logging interval <seconds>
• XML API:
api/?type=op&cmd=<request>
<plugins>
<vm_series>
<cloud-logging>
VM-Series Public Cloud Deployments 64 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on AWS
<interval>seconds</interval>
</cloud-logging>
</vm_series>
</plugins>
</request>
• Display the cloud logging interval—Use the CLI to display the current interval in seconds.
show plugins vm_series cloud-logging interval
• Disable periodic logging—Use the CLI to turn off periodic logging.
request plugins vm_series cloud-logging interval 0
VM-Series Public Cloud Deployments 65 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on AWS
VM-Series Integration with AWS Warm Pool
Where Can I Use This? What Do I Need?
• VM-Series PAN-OS® 11.2.11 or later and 12.1.5 or
later
Network administrator or superuser access
The AWS Warm Pool feature integrates your Palo Alto Networks® VM-Series firewalls with AWS
ASG warm pool support. With this integration, you can choose to maintain a pool of pre-initialized
VM-Series instances, significantly reducing the time required for them to become operational
during scale-out events.
Traditional VM-Series scaling in AWS can take 15 to 20 minutes for a new instance to become
fully operational. This impacts application availability and security posture during traffic spikes.
AWS warm pools mitigate this by pre-initializing firewalls, allowing them to enter service in under
90 seconds. This improves the responsiveness of your security infrastructure.
When your ASG scales out, a pre-initialized VM-Series instance from the warm pool transitions
to the InService state. Credit consumption only happens in InService state transition and not for
warm instances.
AWS Warm Pool Integration
```
Palo Alto Networks VM-Series firewalls integrate with AWS Auto Scaling Group (ASG) warm
```
pools to enhance scaling capabilities. The following are the key components that orchestrate the
lifecycle of your firewall instances within AWS.
VM-Series Firewall Instances
These instances are the core security appliances providing network security services. Within the
warm pool context, these are the instances pre-initialized and managed, ready to scale out rapidly.
```
AWS Auto Scaling Group (ASG)
```
The ASG acts as the container and manager for your VM-Series instances. It dynamically adds or
removes instances from service based on demand and health. The Warm Pool is an integral part of
the ASG's scaling mechanism, providing a ready pool of instances.
IAM Role
```
You must attach an AWS Identity and Access Management (IAM) role with specific permissions
```
to your VM-Series instances. This role grants authority to the firewall to interact with AWS Auto
Scaling services, specifically to update the instance's health status within the ASG. The IAM policy
must include the following permissions:
• "autoscaling:DescribeAutoScalingInstances",
• "autoscaling:DescribeLifecycleHooks",
• "autoscaling:CompleteLifecycleAction",
VM-Series Public Cloud Deployments 66 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on AWS
• "autoscaling:DescribeLoadBalancerTargetGroups",
• "elasticloadbalancing:DescribeTargetHealth",
• "logs:CreateLogGroup", "logs:CreateLogStream",
• "logs:PutLogEvents"
Ensure that the firewall allows these permissions. Additionally, include logs:permissions are
needed for monitoring and debugging of Cloudwatch log.
Dependencies and Interactions
The AWS Warm Pool feature for VM-Series firewalls relies on seamless interaction with the
following AWS and Palo Alto Networks services:
• AWS Services - CloudWatch - Used for publishing logs related to warm pool operations. This
allows you to monitor provisioning status and debug issues.
• Lifecycle Hooks - Lifecycle hooks are customizable actions defined within the ASG that pause
instance transitions at specific points. This allows the firewall to perform provisioning tasks
before the instance proceeds. Two lifecycle hooks are mandatory for this feature:
• LaunchLifecycleHook - Used for transitions from Warmed:Pending:Wait to
```
Warmed:Pending:Proceed and from Pending to InService. Configure the heartbeat timeout
```
to accommodate the full configuration push and provisioning time for the firewall, typically
```
ranging from 5 to 20 minutes (for example, 600 seconds or more). The default result for this
```
hook must be CONTINUE.
• TerminateLifecycleHook - Used for instance termination, allowing for cleanup actions
such as delicensing and public IP release. A timeout of 300 seconds with a default result of
ABANDON is suggested for this hook.
Configure AWS Warm Pools for VM-Series Auto Scaling Groups
Leveraging AWS Warm Pools significantly reduces the time required for VM-Series firewalls to
scale out and become ready to inspect traffic, improving application availability and performance
during traffic surges.
```
STEP 1 | Deploy your AWS Auto Scaling Group (ASG) with Warm Pool configuration.
```
VM-Series Public Cloud Deployments 67 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on AWS
STEP 2 | Configure the warm pool settings within your ASG. The Warmed:Running state ensures the
firewall is fully booted and ready to receive configuration, which is essential for rapid scale-
out.
1. Navigate to EC2 > Auto Scaling groups and click the ASG on which you wish to configure
the warm pool.
2. Click Actions > Edit in the warm pool section.
3. Select Running in the warm pool instance state drop-down and click Save changes.
STEP 3 | Create the necessary IAM role and attach the required permissions to your VM-Series
instances.
1. Navigate to EC2 > Instances > click the required instance on which you wish to create the
IAM role.
2. Create an IAM role that you will attach to your VM-Series instances.
3. Attach a custom policy to this role with the Create the necessary IAM role.
STEP 4 | Configure two mandatory lifecycle hooks for your Auto Scaling Group.
1. Click Create Lifecycle Hook in the ASG page.
1. Set Lifecycle transition to Instance Launch.
2. Set Default result to CONTINUE.
3. Configure Heartbeat timeout to allow sufficient time for firewall configuration and
content push. This timeout should be equal to the time it takes for the configuration to
```
be pushed to the device and can range from 5 to 20 minutes (for example, 600-1200
```
VM-Series Public Cloud Deployments 68 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on AWS
```
seconds), depending on the size and complexity of your security policy. A heartbeat
```
```
timeout of at least 600 seconds (10 minutes) is recommended.
```
2. Create a Terminate Lifecycle Hook:
1. Set Lifecycle transition to Instance Terminate.
2. Set Default result to ABANDON.
3. Configure Heartbeat timeout (for example, 300 seconds) to allow for any necessary
cleanup tasks, such as releasing public IPs. A default of 30 seconds is generally sufficient
for termination as no delicensing is performed by the firewall.
STEP 5 | Monitor your VM-Series instance logs in AWS CloudWatch for provisioning and operational
status.
1. Navigate to CloudWatch > Logs > Log groups in the AWS console.
2. Search for the log group named PaloAltoNetworksFirewalls.
3. Within this log group, locate log streams. Click the required instance ID. All warm pool
specific logs are pushed to this designated CloudWatch log group, allowing you to easily
VM-Series Public Cloud Deployments 69 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on AWS
track the lifecycle and health of your VM-Series instances. Per instance ID, only one stream
is created, which contains all transition logs.
VM-Series Public Cloud Deployments 70 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on AWS
Simplified Onboarding of VM-Series Firewall on AWS
Where Can I Use This? What Do I Need?
• AWS AWS account
```
Amazon Machine Image (AMI) ID
```
```
VM-Series License (PAYG or BYOL)
```
VM-Series plugin
Panorama
Panorama plugin for AWS
The simplified onboarding flow streamlines the deployment and initial configuration of VM-Series
```
firewalls in AWS. It supports east-west deployment (with transit gateway), centralized egress, and
```
distributed inbound deployment of VM-Series firewall.
Prerequisites
For simplified onboarding of VM-Series firewall on AWS, ensure to use the following PAN-OS
versions and license types:
Supported PAN-OS Version
• PAN-OS version 10.2 or above
Supported License Types
```
• PAYG (Pay-as-you-go)
```
Simplified Onboarding of VM-Series in Security VPC using CFT
1. Login to your AWS CloudFormation console.
2. On the Stacks page, select Create stack.
VM-Series Public Cloud Deployments 71 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on AWS
3. Select choose an existing template option.
VM-Series Public Cloud Deployments 72 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on AWS
VM-Series Public Cloud Deployments 73 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on AWS
4. In the Specify template section, you can select Amazon S3 URL or Upload a template file as
your template source option.
If you select Amazon S3 URL, provide a URL to the template file in an S3 bucket.
If you select Upload a template file, upload a template file from your local directory.
5. Click Next.
6. In the Specify stack details page, enter the Stack Name.
VM-Series Public Cloud Deployments 74 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on AWS
7. In the Parameters section, enter values for the parameters that were defined in the template.
1. Enter your Security VPC CIDR.
2. Enter the number of Desired Firewalls.
3. Select the Firewall Instance Type and size for the autoscaled VM-Series firewall.
4. Enter your firewall AMI ID.
5. Enter your Amazon EC2 Key pair in the Key Name field.
VM-Series Public Cloud Deployments 75 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on AWS
VM-Series Public Cloud Deployments 76 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on AWS
8. Enter the number and list of Availability Zones.
VM-Series Public Cloud Deployments 77 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on AWS
9. In the Transit Gateways section, select True if you want CFT to create a new transit gateway.
VM-Series Public Cloud Deployments 78 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on AWS
VM-Series Public Cloud Deployments 79 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on AWS
Select False if you already have a transit gateway and enter the existing transit gateway ID.
VM-Series Public Cloud Deployments 80 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on AWS
VM-Series Public Cloud Deployments 81 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on AWS
If you select Yes for Panorama managed devices, then enter the following bootstrap parameter
```
values:
```
• Enter the Panorama IP address for firewalls to connect.
```
• Enter the secondary Panorama IP address (if HA enabled), for firewalls to connect.
```
• Enter the Panorama Device Group name.
• Enter the Template Stack name.
• Enter the Panorama Log Collector group name.
• Enter the VM Auth Key.
• Enter the Certificate PIN ID.
• Enter the Certificate PIN value for installing device certificates on VMs.
• Enter the Additional bootstrap parameters as key value pairs.
If you select No for Panorama Managed Devices, you can skip the above Bootstrap Info
section.
10.Click Next.
VM-Series Public Cloud Deployments 82 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on AWS
11.In the Configure Stack Options page, select your optional IAM role and stack failure options.
VM-Series Public Cloud Deployments 83 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on AWS
VM-Series Public Cloud Deployments 84 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on AWS
If your template contains IAM resources, for Capabilities, select I acknowledge that AWS
CloudFormation might create IAM resources with custom names.
12.Click Next.
13.Review the details of your stack and click Submit.
AWS CloudFormation will then create all the resources defined in your template.
You can view the Stack details on CloudFormation > Stacks page, and then understand the
events updated, parameters, and resources are being created, updated, or deleted.
Simplified Onboarding Bootstrap Parameters
Following are the bootstrap parameter for simplified onboarding on AWS:
plugin-op-commands=simplified-onboarding:enable,dep-
```
plan:combined,dep-arch:two-arm,aws-gwlb-inspect:enable,aws-gwlb-
```
overlay-routing:enable
op-command-modes=mgmt-interface-swap
For more information, see Bootstrap the VM-Series firewall on AWS.
Public IP Address Management
The IP addresses for MGMT and untrust interfaces are automatically allocated and assigned when
deployed using Simplified Onboarding.
VM-Series Public Cloud Deployments 85 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on AWS
Panorama Orchestrated Deployments in AWS
Where Can I Use This? What Do I Need?
• AWS AWS account
```
Amazon Machine Image (AMI) ID
```
```
VM-Series License (PAYG or BYOL)
```
VM-Series plugin
Panorama
Panorama plugin for AWS
The Panorama plugin for AWS 3.0.1 or later orchestrates VM-Series firewall deployments in AWS
and enables security policies for managed firewalls. AWS Orchestration is designed as a plug-
and-play model for setting up security deployments in AWS. It simplifies the deployment of the
```
existing Gateway Load Balancer (GWLB) solution by bringing all configuration into one screen
```
on Panorama. Panorama lets the plugin manage your deployment and configure resources. This
plugin also performs firewall management by generating the needed baseline configuration to get
traffic flowing for the deployment. When you configure the policies, the plugin services Inbound,
Outbound, and east-west flows for all traffic protocols. Use this plugin to configure, deploy, and
manage your security deployments.
The image below highlights the topology of the Security VPC deployment. Here, all security
resources are deployed into the plugin-managed Security VPC. The GWLB solution is leveraged to
redirect traffic from your applications to the firewall stack.
VM-Series Public Cloud Deployments 86 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on AWS
VM-Series Public Cloud Deployments 87 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on AWS
As part of the infrastructure setup on the AWS cloud, the plugin creates Security VPC with GWLB
endpoints, firewalls, and NAT Gateway subnets and route tables. The plugin does not create AWS
```
Transit Gateway (TGW).
```
VM-Series firewall can inspect traffic routed between the VPCs.
The Inbound traffic flow originating in the Application VPC flows in through IGW is redirected to
the GWLB endpoint based on edge route. The traffic enters through the GWLB endpoint to the
firewalls in the Security VPC for inspection. After the inspection, the traffic is sent back to the
GWLB endpoint and directed to the original application.
For Outbound and East-West traffic, this solution leverages TGW. When you create a TGW, the
plugin creates TGW attachments and route tables in the Security VPC. You have to attach your
Application VPC to the TGW used in the Security VPC configuration. Also direct the Outbound
and East-West traffic to the TGW by adding routes to the route tables associated with your
workload subnets. You have to modify the Application VPC attachment route table to direct the
East-West and Outbound traffic to the Security VPC attachment.
The plugin monitors TGW attachments to learn any newly added and deleted VPC attachments.
When the plugin detects an existing or new attachment, it makes necessary changes in the
Security VPC to ensure that the firewall inspects the traffic entering TGW before sending it back
to the TGW. These changes include adding routes to the NAT Gateway route table to direct
Outbound traffic back to the GWLB endpoint, and to the GWLB endpoint route table to return
traffic to the TGW after inspection. The plugin updates the TGW attachment route table to
ensure that the traffic coming back from the Security VPC to the TGW is sent to the correct
Application attachment. Traffic from the Application VPC is directed to TGW through routing.
When traffic hits the TGW attachment in Security VPC, the attachment route table sends the
traffic to the Security VPC. From there, it's directed to the existing GWLB endpoint, then to the
firewall for inspection. The Outbound traffic flows out to the original destination address through
NAT Gateway. The East-West traffic is sent back to the TGW where the route table directs the
traffic to the original destination address.
Prepare for an Orchestrated AWS Deployment
Where Can I Use This? What Do I Need?
• AWS AWS account
```
Amazon Machine Image (AMI) ID
```
```
VM-Series License (PAYG or BYOL)
```
VM-Series plugin
Panorama
Panorama plugin for AWS
Complete the following tasks on AWS and Panorama before you orchestrate a VM-Series firewall
on AWS.
VM-Series Public Cloud Deployments 88 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on AWS
• AWS
• Panorama-orchestrated deployments on AWS require two availability zones and supports
up to six availability zones.
• Create an AWS user or instance profile for a specific AWS account with programmatic
access and necessary permissions to allow the plugin to create resources on security VPC.
For Security Account—An AWS Account with a user or instance profile who has the
necessary permissions to launch AWS resources such as VPCs, VM instances, AWS load
balancer, NAT gateways, and endpoints. The plugin needs the existing user or instance
profile to have the following set of permissions to declare the IAM role valid. The CFT
hyperlink under Security Account creates a policy with the following permissions.
"Statement":[
```
{
```
"Effect": "Allow",
"Action": "ec2:*",
"Resource": "*"
```
},
```
```
{
```
"Effect": "Allow",
"Action": "elasticloadbalancing:*",
"Resource": "*"
```
},
```
```
{
```
"Effect": "Allow",
"Action": "cloudwatch:*",
"Resource": "*"
```
},
```
```
{
```
"Effect": "Allow",
"Action": "autoscaling:*",
"Resource": "*"
```
},
```
```
{
```
"Effect": "Allow",
"Action": "sts:assumerole",
"Resource": "*"
```
},
```
```
{
```
"Effect": "Allow",
"Action": "cloudformation:*",
"Resource": "*"
```
},
```
```
{
```
"Effect": "Allow",
"Action": [
"iam:Get*",
"iam:List*",
"iam:PassRole"
],
"Resource": "*"
```
},
```
```
{
```
"Effect": "Allow",
"Action": "ram:*",
VM-Series Public Cloud Deployments 89 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on AWS
"Resource": "*"
```
}
```
]
```
},
```
The following granulized permissions accommodate your requirements and security
permissions. These permissions provide a detailed explanation for the API calls made from
the plugin. The permissions are granulized to accommodate every action that will be called
from the CFT and plugin backend code for both Security VPC and cross-account Application
VPC.
The following permissions are not implemented in the AWS plugin for Panorama
version 3.0.1 because the detailed permissions list exceeds the AWS policy size
limitation. For inline policies, you can add as many policies as you want for a user,
role, or group, but the total aggregate policy size per entity can’t exceed these
limits—user policy size can’t exceed 2,048 characters , role policy size can’t exceed
10,240 characters, and groups policy size can’t exceed 5,120 characters. Due to
these limitations and backend validation time, you must use the above-mentioned
permissions.
```
{
```
"Version": "2012-10-17",
"Statement": [
```
{
```
"Sid": "VisualEditor0",
"Effect": "Allow",
"Action": [
"ec2:AuthorizeSecurityGroupIngress",
"cloudwatch:PutMetricData",
"ec2:Describe*",
"cloudwatch:DeleteAlarms",
"autoscaling:DescribePolicies",
"ec2:DeleteVpcEndpoints",
"ec2:AttachInternetGateway",
"ec2:AcceptTransitGatewayVpcAttachment",
"autoscaling:ExecutePolicy",
"ec2:DeleteRouteTable",
"sts:GetSessionToken",
"cloudformation:DescribeStackEvents",
"ec2:RevokeSecurityGroupEgress",
"ec2:CreateRoute",
"ec2:CreateInternetGateway",
"cloudformation:UpdateStack",
"ec2:DeleteInternetGateway",
"iam:ListRolePolicies",
"autoscaling:TerminateInstanceInAutoScalingGroup",
"iam:ListPolicies",
"ec2:DisassociateTransitGatewayRouteTable",
"iam:GetRole",
"iam:GetPolicy",
"ec2:CreateTags",
"elasticloadbalancing:CreateTargetGroup",
"ec2:RunInstances",
VM-Series Public Cloud Deployments 90 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on AWS
"ec2:DisassociateRouteTable",
"ec2:CreateVpcEndpointServiceConfiguration",
"ec2:CreateTransitGatewayRoute",
"ec2:CreateTransitGatewayVpcAttachment",
"elasticloadbalancing:DescribeAccountLimits",
"elasticloadbalancing:AddTags",
"cloudformation:DeleteStack",
"cloudwatch:DescribeAlarms",
"ec2:DeleteNatGateway",
"ram:AssociateResourceShare",
"autoscaling:DeleteAutoScalingGroup",
"ec2:CreateSubnet",
"elasticloadbalancing:ModifyLoadBalancerAttributes",
"iam:GetRolePolicy",
"ec2:ModifyVpcEndpoint",
"ec2:DisassociateAddress",
"autoscaling:DescribeAutoScalingInstances",
"ec2:ModifyVpcEndpointServicePermissions",
"ec2:CreateNatGateway",
"ec2:CreateVpc",
"ec2:ModifySubnetAttribute",
"iam:PassRole",
"autoscaling:DescribeScalingActivities",
"sts:DecodeAuthorizationMessage",
"autoscaling:DescribeLoadBalancerTargetGroups",
"iam:ListAttachedGroupPolicies",
"ec2:DeleteLaunchTemplateVersions",
"sts:GetServiceBearerToken",
"iam:ListAccessKeys",
"ram:DisassociateResourceShare",
"ec2:ReleaseAddress",
"ec2:DeleteLaunchTemplate",
"elasticloadbalancing:CreateLoadBalancer",
"ec2:AcceptVpcEndpointConnections",
"iam:ListGroupPolicies",
"iam:ListRoles",
"elasticloadbalancing:DeleteTargetGroup",
"ram:AssociateResourceSharePermission",
"ec2:CreateLaunchTemplate",
"elasticloadbalancing:DescribeTargetGroups",
"elasticloadbalancing:DeleteListener",
"ram:UpdateResourceShare",
"iam:GetPolicyVersion",
"ec2:DeleteSubnet",
"ec2:ModifyVpcEndpointServiceConfiguration",
"ec2:CreateTransitGatewayRouteTable",
"ec2:ModifyTransitGateway",
"cloudformation:DescribeStackResource",
"ec2:AssociateRouteTable",
"elasticloadbalancing:DeleteLoadBalancer",
"elasticloadbalancing:DescribeLoadBalancers",
"logs:CreateLogStream",
"ec2:GetLaunchTemplateData",
"ec2:DeleteTransitGatewayVpcAttachment",
"autoscaling:DescribeAutoScalingGroups",
VM-Series Public Cloud Deployments 91 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on AWS
"iam:ListAttachedRolePolicies",
"logs:GetLogEvents",
"autoscaling:UpdateAutoScalingGroup",
"ec2:AssociateTransitGatewayRouteTable",
"elasticloadbalancing:ModifyTargetGroupAttributes",
"autoscaling:SetDesiredCapacity",
"cloudformation:DescribeStackResources",
"ec2:CreateRouteTable",
"ec2:DetachInternetGateway",
"cloudformation:DescribeStacks",
"ec2:DeleteTransitGatewayRouteTable",
"sts:AssumeRole",
"ec2:DeleteTransitGatewayRoute",
"iam:GetUserPolicy",
"iam:ListGroupsForUser",
"ec2:DeleteVpc",
"iam:GetGroupPolicy",
"ec2:AssociateAddress",
"autoscaling:CreateAutoScalingGroup",
"ram:AcceptResourceShareInvitation",
"ec2:DeleteTags",
"logs:DescribeLogStreams",
"ec2:DeleteVpcEndpointServiceConfigurations",
"autoscaling:DeletePolicy",
"elasticloadbalancing:RemoveTags",
"elasticloadbalancing:CreateListener",
"elasticloadbalancing:DescribeListeners",
"autoscaling:PutScalingPolicy",
"ec2:CreateSecurityGroup",
"iam:ListAttachedUserPolicies",
"ec2:ModifyVpcAttribute",
"ec2:ModifyInstanceAttribute",
"ec2:GetTransitGatewayRouteTableAssociations",
"ram:DeleteResourceShare",
"ec2:AuthorizeSecurityGroupEgress",
"ec2:ModifyTransitGatewayVpcAttachment",
"iam:GetInstanceProfile",
"ram:DisassociateResourceSharePermission",
"elasticloadbalancing:DescribeTags",
"ec2:DeleteRoute",
"iam:ListUserPolicies",
"logs:PutLogEvents",
"ec2:AllocateAddress",
"ec2:CreateLaunchTemplateVersion",
"cloudwatch:PutMetricAlarm",
"cloudformation:CreateStack",
"ec2:CreateVpcEndpoint",
"ec2:DeleteSecurityGroup",
"ec2:StartVpcEndpointServicePrivateDnsVerification",
"ec2:ModifyLaunchTemplate",
"iam:ListUsers",
"ram:CreateResourceShare"
],
"Resource": "*"
VM-Series Public Cloud Deployments 92 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on AWS
```
}
```
]
```
}
```
For Application Account—An AWS account other than the Security account that hosts
either TGW or the applications that need to be protected. Within this account you must
create a RoleARN with the following permissions.
```
{
```
"Version": "2012-10-17",
"Statement": [
```
{
```
"Action": [
"ec2:Describe*",
"ec2:DisassociateTransitGatewayRouteTable",
"ec2:CreateTransitGatewayRoute",
"ec2:CreateTransitGatewayRouteTable",
"ec2:AssociateTransitGatewayRouteTable",
"ec2:DeleteTransitGatewayRouteTable",
"ec2:DeleteTransitGatewayRoute",
"ec2:GetTransitGatewayRouteTableAssociations"
],
"Resource": "*",
"Effect": "Allow"
```
},
```
```
{
```
"Action": [
"iam:Get*",
"iam:List*"
],
"Resource": "*",
"Effect": "Allow"
```
}
```
]
```
}
```
• Dedicated CIDR block—A CIDR block reserved for the Security VPC. The plugin manages
this CIDR block, using it to launch firewalls, load balancers, and other deployment resources
for the Security VPC.
• AWS transit gateway—Create a TGW and ensure that the selected AWS user has
permission to configure the TGW resources.
The AWS account must have the following two IAM roles:
• AWSServiceRoleForElasticLoadBalancing
• AWSServiceRoleForAutoScaling
VM-Series Public Cloud Deployments 93 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on AWS
• Panorama
• Panorama Plugin for AWS—Version 3.0.1 or later.
• VM-Series Plugin—Version 2.0.6 or later.
• PanOS—Version 10.0.5 or later.
• Create a valid license API key configured on Panorama for delicensing the firewalls.
• Create an IAM role on the plugin under Panorama > Plugins > AWS > Setup > IAM Roles.
This configuration needs the Access Key and Secret Key associated with the user you
created in your AWS account.
Configure IAM Roles for AWS Plugin in Panorama
With the AWS plugin 3.0.1 or later, you can use IAM roles to enable Panorama to authenticate
and retrieve metadata on the resources deployed within your AWS account. When your
Panorama is not deployed on AWS, you have two options. You can either provide the long-term
IAM credentials for the AWS accounts, or set up an Assume Role on AWS to allow access to the
defined AWS resources within the same AWS account or cross-accounts. An Assume Role is
recommended as the more secure option.
STEP 1 | To validate the AWS user credentials created for Security VPC, go to Panorama > Plugins >
AWS > Setup > IAM Roles.
STEP 2 | Click Add and enter the following details under Security Account Detail.
• Enter a name for the IAM role and an optional description.
• Enter the AWS access key and secret key to validate permissions. Reenter the secret key
to confirm the secret access key.
• Select an account type—Instance Profile or AWS Account Credentials. If your Panorama
is deployed on AWS, you can choose to either attach an instance profile with the correct
permissions to your Panorama or add the credentials associated with the IAM role on
Panorama. If your Panorama isn’t deployed on AWS, you must enter the credentials for
the IAM role locally on Panorama.
STEP 3 | Under Application Account Details, search and select the needed RoleARNs to provide valid
permissions to the Security account to access the resources in the Application VPC.
The status of validity of monitoring and deployment is color-coded for ease of identification.
```
• Valid (Green)—Indicates that the secret key and access key are valid. Also, all RoleARNs
```
entered for application account access have valid permissions to do necessary action.
```
• Partially valid (Orange)—Indicates that the secret key and access key are valid but one or
```
more RoleARNs entered for application account access don’t have valid permissions to do
VM-Series Public Cloud Deployments 94 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on AWS
the necessary action. Click the status hyperlink to open the IAM and see which specific
RoleARNs don’t comply.
```
• Invalid (Red)—Indicates that the secret key and access key entered are either invalid or don’t
```
have permissions to do the necessary action.
```
• Commit Required (Gray)—Indicates that a commit is required for the role.
```
```
• Validating (Gray)—Indicates that the plugin is trying to connect to AWS to check the
```
necessary requirements. If this status continues for more than a few seconds, verify if the
connection to AWS is established.
Only the IAM roles with green or orange status are allowed for further deployment
configuration.
Orchestrate a VM-Series Firewall Deployment in AWS
Where Can I Use This? What Do I Need?
• AWS AWS account
```
Amazon Machine Image (AMI) ID
```
```
VM-Series License (PAYG or BYOL)
```
VM-Series plugin
Panorama
Panorama plugin for AWS
Complete the following procedure to orchestrate a VM-Series firewall deployment in AWS.
Panorama deployments on AWS with an instance profile isn't supported when deployed
behind a proxy.
STEP 1 | Log on to the Panorama web interface.
STEP 2 | Install the Panorama plugin for AWS 3.0.1 or later.
To upgrade the Panorama plugin for AWS to version 3.0.1, you must first upgrade
the plugin to version 2.0.2. After you install the AWS plugin version 3.0.1 you can't
downgrade to version 2.0.x or below.
If you have a Panorama HA configuration, repeat the installation/upgrade process on
each Panorama peer.
```
If you currently have a Panorama plugin for any cloud platform installed, installing (or
```
```
uninstalling) an additional plugin requires a Panorama reboot so that you can commit
```
changes.
STEP 3 | Configure the IAM roles for orchestration.
STEP 4 | Select Panorama > Plugins > AWS > Deployments to Add a new deployment.
VM-Series Public Cloud Deployments 95 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on AWS
STEP 5 | Enter the generic details of the deployment in the General tab.
• Enter a Name and an optional Description to identify the deployment in Panorama and
AWS cloud.
• Select an IAM Role from the drop-down. The list displays IAM roles that has valid or
partially valid deployment permissions.
Once an IAM role has been created and added to you deployment, you can edit
```
information in the IAM (such as secret key and access key). However, you cannot
```
edit the name of the IAM role. To change the name, you must delete the IAM and
create another.
VM-Series Public Cloud Deployments 96 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on AWS
STEP 6 | Enter the Security VPC related information in the Security VPC tab.
• Select the AWS Region in which you intend to launch the deployment. The list displays
regions based on the selected IAM role.
• Enter a VPC CIDR value to create resources in the Security VPC. This CIDR will be
managed by the AWS plugin.
• Select two or more Availability Zones from the pre-populated list and follow the same
mapping in AWS. This list is populated based on the region you selected.
STEP 7 | Select Firewall > Image and enter the following details.
```
• License Type—The standard license types Bring Your Own License (BYOL), Pay As you
```
Go-Marketplace-Bundle1, and Pay As you Go-Marketplace-Bundle2 are provided as
VM-Series Public Cloud Deployments 97 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on AWS
```
options in the drop-down (based on the selected regions). If you select Bring Your Own
```
License, be prepared to enter a license authcode.
Pay as you go Bundle 1 and Bundle 2 can't be used with an AMI custom image.
```
• (Optional—Appears only if you choose Bring Your Own License license type) License
```
Authcode—Enter the authcode for your BYOL. This authcode determines which instance
types appear on the Instance Type drop-down.
• Instance Type—Choose supported instance types from the drop-down. This list is derived
from the license authcode.
• Image Type—Select Marketplace Image or Custom Image.
If you select Marketplace Image, select from the drop-down, PanOS Version 10.0.5 or
later supported in the regions you selected when you configured the Security VPC.
```
If you select Custom Image, enter the Amazon Machine Image (AMI) ID and select a
```
PanOS Version 10.0.5 or later.
• Device Certificate—The device certificate is generated on the Customer Support portal,
and enables you to retrieve your site license entitlements for AutoFocus or Cortex Data
Link. Select Disable if you are not using these licenses. To configure the device certificate
PIN, select Enable and enter the following information:
PIN ID—Enter the PIN ID.
Confirm PIN ID—Re-enter the PIN ID.
PIN Value—Enter the PIN.
Confirm VM PIN Value—Re-enter the PIN.
VM-Series Public Cloud Deployments 98 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on AWS
STEP 8 | Select Firewall > Basic and enter the following details.
• AWS Key Name—The name of an SSH key you will use to log into the firewalls after they
are deployed. This key is bootstrapped into the firewall and can be used for debugging
when the firewall is up and running.
• Existing Device Group—If you select No, the plugin creates format of the device group
name. If you select Yes, select an existing Device Group from the drop-down list.
• Primary Panorama IP—The IP address of the Panorama you're using. The drop-down
displays public and private IP addresses on the management interface. Select an IP
address from the drop-down.
If you deployed Panorama behind a proxy, you must manually enter the public IP
of the primary Panorama under Panorama > Setup > Interfaces.
If Panorama private IP is used, routes may need to be added to the AWS Route
Tables for plugin deployed firewall subnets and existing Panorama subnet,
in order to facilitate connectivity between the newly deployed firewalls and
Panorama.
• Secondary Panorama IP—If you have a Panorama HA, the drop-down displays the IP
addresses on the management interface of the secondary device. Select an IP address
from the drop-down.
If the secondary Panorama has a public IP address, it may not appear in the
drop-down. In this case, you must manually add the IP address of the secondary
Panorama.
```
• Min Firewalls—The minimum number of firewalls in an Auto Scaling Group (ASG). A value
```
between 1 and 25.
• Max Firewalls—The maximum number of firewalls in an ASG. A value between 2 and 25.
• FirewallInstanceARN—From the drop-down, choose the assume RoleARN created on
AWS cloud that is associated with the firewall instance to publish autoscaling metrics. The
drop-down displays only the RoleARNs you entered on the Setup > IAM Roles page.
VM-Series Public Cloud Deployments 99 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on AWS
```
STEP 9 | (Optional) Select Firewall > Advanced and enter the following details.
```
• Autoscaling Metric—Choose a metric from the drop-down: Data Plane CPU Util Percent
```
(default), Active Sessions, Data Plane Packet Buffer Util Percent, or Session Util Percent.
```
• Scale In Threshold—Choose a value for the scale in threshold. The value depends on your
chosen metric.
• Scale Out Threshold—Choose a value for the scale out threshold. The value depends on
your chosen metric.
• Scale Out Threshold—Choose a value for the scale out threshold. The value depends on
your chosen metric.
• Jumbo Frame—Disabled by default. You can only enable this option when preparing the
initial deployment. Select Enable to enable jumbo frame support on the firewall.
VM-Series Public Cloud Deployments 100 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on AWS
STEP 10 | Select whether to connect to a Transit Gateway to handle traffic routing across Security
VPC and Application VPC.
• Choose if you want to Connect to TGW. If you select Yes, be prepared to enter a TGW ID
to which you want to attach the Security VPC.
This configuration is required for Outbound or East-West traffic flows only.
```
• (Optional) Select a TGW ID to which you want to attach the Security VPC.
```
You have to share the TGW if you want to use them across accounts. You can
```
share it using Resource Access Manager (RAM) on AWS. Create RAM based on
```
the account where the TGW is located.
• Select Application Account Names. If the TGW and Security VPC are in the same
account, select the Application Account with which you want to share the TGW. The
plugin creates the RAM on the Security Account to share the TGW across the selected
VM-Series Public Cloud Deployments 101 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on AWS
Application accounts. You must accept the invitation for RAM on the account you select
here.
If the TGW and Security VPC are in the same account, select an Application
account with which you want to share the TGW. If the TGW is in an Application
account, make sure that the TGW is shared on RAM.
```
If the TGW is in an Application account (other than the Security account):
```
1. Make sure the TGW is shared with the Security account.
2. Use the CFT hyperlink under Setup > IAM Roles > Application Account Details. From
the CFT, you can create the RAM for the mentioned TGW.
3. On the Security account, make sure to go to RAM in the AWS console and accept the
request to share the TGW.
STEP 11 | Commit to add the deployment and push to firewalls.
VM-Series Public Cloud Deployments 102 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on AWS
View the Deployment Status
Where Can I Use This? What Do I Need?
• AWS AWS account
```
Amazon Machine Image (AMI) ID
```
```
VM-Series License (PAYG or BYOL)
```
VM-Series plugin
Panorama
Panorama plugin for AWS
If there is an entry in the Deployment Status column, click the hyperlink to view the deployment
details.
The possible status messages are:
• Commit changes—You have added a deployment for the first time but have not yet committed
the changes.
Every configuration change for the deployment must be committed so that the plugin
can pick up your changes.
• Deploying—The plugin is deploying or updating the deployment. For more information, click
the hyperlink to view the detailed status.
• Failure—Deployment has failed. Click the hyperlink and view the Detailed Status for the
Security stack.
• Not Deployed—The plugin is ready to deploy the configuration, but the deployment has not
begun.
• Success—The plugin has successfully deployed the Security stack and the firewalls have
connected to Panorama. The firewalls can pass traffic.
• Warning—Deployment has successfully finished but something external to the deployment has
failed. For example, you might see this message:
FWs have not connected after 20 minutes of the deployment completing.
Click the hyperlink and view the Security stack.
Once the deployment is deployed, the plugin allows you to modify a certain subset of parameters.
Once the changes have been made, you must do a commit before clicking the Redeploy button.
When an update happens, the plugin makes sure the Panorama config is created and accurate. It
```
redeploys the CFT to apply any changes, and attach or detach from the configured TGW (if this
```
```
configuration was modified).
```
• Deploy—After you commit your initial configuration, select Deploy to launch the deployment.
• Redeploy—Modify a deployment, commit your changes, and select Redeploy.
Commit changes to the deployment before you click Redeploy.
VM-Series Public Cloud Deployments 103 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on AWS
• Undeploy—Delete a deployment, but keep the configuration so it can be redeployed later.
To remove an existing deployment and its configuration, check a deployment and select
Delete at the bottom of the Deployments page.
Detailed Status
To access the Detailed Status, click the hyperlink in the Deployment Status column. From the
detailed status you can learn where to apply configuration, view the error message from a stack
failure, or view the deployment status when it's deploying.
• Name—The deployment name.
• Status—See above for a description of each status.
• Detail—Details on the deployment you selected in Deployment Status. For example, if the
deployment was successful, displays the date and time of the deployment, or if there was a
stack failure, displays an error message.
• Policy Device Group—The plugin can create a policy device group for your deployment
or you can choose an existing device group to act as the policy device group for a specific
deployment.
• Config Device Group—The plugin creates a configuration device group as a child of the policy
device group. The plugin puts configuration information for the deployment in the config
device group, ensuring that your policy device group remains untouched if you remove the
deployment.
Don’t put policy information in the config device group.
• Template Stack—Displays the template stack associated with the VM-Series firewall. Any
custom configuration is applied to this template stack.
• External IP—Displays the public IP addresses of the NAT Gateways in the Security VPC, one
for each availability zone. The outbound public IP addresses are used for all outbound traffic
from the deployment, and for outbound traffic from the VM-Series firewall management
interface.
To allow firewalls to connect to Panorama, the outbound public IP addresses must be
whitelisted in your Panorama security group.
• CloudFormation Link—This link opens the AWS console to display the current stack in the
CloudFormation services section. You can see where the stack is deployed and debug issues
with the deployment.
• CloudWatch Link—This link opens the AWS console to display PaloAltoNetworkFirewalls logs
and log groups related to the firewall.
• AutoScalingGroup Link—This link opens the AWS console to display the details of the ASG
associated with the deployment, and list of instances under the ASG. You can view logs
associated with these instances on CloudWatch Link.
• Endpoint Service Name—The GWLB endpoint name created as part of the deployment. For
example, com.amazonaws.vpce.us-east-1.vpce-svc-0d00ebcb0000dc000.
• Cloudformation Stack Name— For example mynw-aws2-virgexstdg0-c0b0f.
VM-Series Public Cloud Deployments 104 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on AWS
Traffic Flow and Configurations
Where Can I Use This? What Do I Need?
• AWS AWS account
```
Amazon Machine Image (AMI) ID
```
```
VM-Series License (PAYG or BYOL)
```
VM-Series plugin
Panorama
Panorama plugin for AWS
VM-Series
The plugin deploys and manages the Security VPC. The plugin updates the Security VPC route
tables based on the attachments discovered on the AWS Transit Gateway.
Inbound Traffic Flow
Table 1: Inbound traffic flow combinations
Application Traffic Type
1 In Security Account Inbound
2 In Application Account Cross-Outbound
Use Case: Inbound Traffic - Application is in the Security Account.
The plugin creates a VPC Service endpoint on the Security Account. The GWLB endpoints must
be associated with the VPC Endpoint Service.
VM-Series Public Cloud Deployments 105 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on AWS
Use Case: Inbound Traffic - Application is in other Application Account.
When the application is in a different account, on the AWS console in the navigation pane, choose
Endpoint Services and select your Endpoint Service. Select Actions > Add Principal to allow
principals. For example, arn:aws:iam::AccountNumber:root. The GWLB endpoints must be
associated with the VPC Endpoint Service.
VM-Series Public Cloud Deployments 106 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on AWS
Outbound and East-West Traffic Flow
Table 2: Outbound traffic flow combinations
Transit Gateway Application Traffic Type
1 In Security Account In Security Account Outbound
2 In Security Account In Application
Account
Outbound
VM-Series Public Cloud Deployments 107 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on AWS
Transit Gateway Application Traffic Type
3 In Application
Account
In Application
Account
Cross-Outbound
4 In Application
Account
In Security Account Cross-Outbound
Use Case: Outbound Traffic - Transit Gateway and Application is in the Security Account.
The plugin scan for the attachments on the configured TGW. When the plugin detects an
existing or new attachment, it makes necessary route table modifications on the Security VPC
components.
Use Case: Outbound Traffic - Transit Gateway is in Security Account and Application is in the
Application Account
When TGW is in the Security Account, to protect the applications that are not in the Security
```
Account, the TGW is shared across these applications using Resource Access Manager (RAM)
```
in the AWS console. You can choose the accounts with which you want to share the TGW from
the plugin user interface. Once the deployment is in Deploying state, monitor the RAM on the
Application Account for an invitation to share resources.
VM-Series Public Cloud Deployments 108 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on AWS
Use Case: Outbound Traffic - Transit Gateway and Application are in the Application Account
When TGW is the Application Account, it must be shared with the Security Account using the
RAM. To create a TGW attachment and route table, a RoleARN from this account must be added
to the IAM role used for the deployment. Use the CFT hyperlink under Setup > Application
Account to configure the Application Account prerequisites.
VM-Series Public Cloud Deployments 109 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on AWS
Table 3: East-West traffic flow combinations
Transit Gateway Application 1 Application 2 Traffic Type
1 In Security
Account
In Security
Account
In Security
Account
East-West
```
2 (multi account
```
```
application)
```
In Security
Account
In Security
Account
In Application
Account
East-West
3 In Application
Account
In Application
Account
In Application
Account
Cross East-West
```
4 (multi account
```
```
application)
```
In Application
Account
In Application
Account
In Security
Account
Cross East-West
Use Case: East-West Traffic - Transit Gateway and Application1 are in the Security Account and
Application2 is in the Security Account
VM-Series Public Cloud Deployments 110 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on AWS
When TGW is in the Security Account, to protect the applications that are not in the Security
```
Account, the TGW is shared across these applications using Resource Access Manager (RAM)
```
in the AWS console. You can choose the accounts with which you want to share the TGW from
the plugin user interface. Once the deployment is in Deploying state, monitor the RAM on the
Application Account for an invitation to share resources.
Use Case: East-West Traffic - Transit Gateway and Application1 are in the Application Account
and Application2 is in the Security Account
When TGW is the Application Account, it must be shared with the Security Account using the
RAM. To create a TGW attachment and route table, a RoleARN from this account must be added
to the IAM role used for the deployment. Use the CFT hyperlink under Setup > Application
Account to configure the Application Account prerequisites.
VM-Series Public Cloud Deployments 111 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on AWS
VM-Series Public Cloud Deployments 112 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on AWS
VM-Series Integration with an AWS Gateway Load
Balancer
Where Can I Use This? What Do I Need?
• AWS AWS account
```
Amazon Machine Image (AMI) ID
```
```
VM-Series License (PAYG or BYOL)
```
VM-Series plugin
Panorama
Panorama plugin for AWS
```
The AWS Gateway Load Balancer (GWLB) is an AWS-managed service that allows you to deploy
```
a stack of VM-Series firewalls and operate in a horizontally scalable and fault-tolerant manner.
You can then expose the AWS GWLB with the stack of firewalls as a VPC Endpoint Service for
```
traffic inspection and threat prevention. By creating Gateway Load Balancer endpoints (GWLBE)
```
for the VPC Endpoint Service, you can easily insert an auto scaling VM-Series firewall stack in the
outbound, east-west, and inbound traffic paths of your applications. VM-Series firewalls and the
GWLB use the GENEVE encapsulation to keep your traffic packet headers and payload intact,
providing complete visibility of the source’s identity to your applications.
The VM-Series firewall supports decryption when deployed behind a GWLB for forward
and inbound use cases, including TLS1.2 and TLS1.3 utilizing DHE/ECDHE ciphers.
The image below describes how the integration of GWLB with VM-Series simplifies your AWS
```
transit gateway(TGW) environments. You attach a centralized security VPC to your transit
```
gateway. The centralized security VPC includes a GWLB to scale and load-balance traffic across
the stack of VM-Series firewalls.
Deploying the VM-Series firewall behind a GWLB requires you to configure the AWS
transit gateway.
VM-Series Public Cloud Deployments 113 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on AWS
To ensure that the VM-Series firewall can inspect traffic that is routed between VPC attachments,
you must enable appliance mode on the transit gateway VPC attachment for the security VPC
containing the VM-Series firewall. You can enable appliance mode using the command:
modify-transit-gateway-vpc-attachment --transit-gateway-attachment-id
<value> --options ApplianceModeSupport=enable
For more instructions, see enabling appliance mode.
This ensures that bidirectional traffic is routed symmetrically—both request and response traffic
are directed to the same Gateway endpoint in the firewall VPC and the GWLB will maintain
persistence to the same VM-Series firewall for inspection before continuing to the correct
destination.
When deployed with a GWLB, you can use the VM-Series firewall to protect:
• Inbound traffic—traffic originating outside the VPC and destined to resources within your
application VPC, such as web servers. VM-Series firewalls prevent malware and vulnerabilities
from entering the network in traffic allowed by AWS security groups.
• Outbound traffic—traffic originating within the application VPCs and destined to external
resources on the internet. The VM-Series firewalls protect outbound traffic flows by ensuring
```
that workloads in application VPCs connect to permitted services (such as Windows Update)
```
and allowed URL categories and preventing data exfiltration of sensitive information.
Additionally, VM-Series security profiles prevent malware and vulnerabilities from entering the
network in the return traffic.
• East-West traffic—in a transit gateway environment, East-West traffic refers to Inter-
VPC traffic, such as the traffic between source and destination workloads in two different
application VPCs. The VM-Series firewalls protect east-west traffic flows against malware
propagation.
To protect the inbound traffic to your application VPCs:
1. Create GWLBE endpoints(GWLBE1 and GWLBE2 in the figure above) having separate subnets
associated in your spoke VPCs. Ensure that you have separate subnets for GWLB endpoints,
ALB, and Application and Transit Gateway attachment within the application VPC.
VM-Series Public Cloud Deployments 114 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on AWS
2. Add route tables in the application VPC (in addition to the VPC local route) as follows:
1. Route table with IGW edge association - Add route destined to ALB with target as GWLBE.
2. Route table with ALB subnet association - Add route destined to 0.0.0.0/0 with target as
GWLBE.
3. Route table with GWLBE subnet association - Add route destined to 0.0.0.0/0 with target
as IGW.
With these routes in place, the inbound traffic arriving at VPC IGW is routed toward GWLBE. The
GWLBE forwards the traffic to GWLB which in turn sends the traffic to the VM-Series firewall in
the Security VPC for inspection. The firewall sends the request traffic back to the application VPC
GWLBE, which then forwards the traffic to the application through ALB. Response traffic to this
request is sent by ALB toward the application GWLBE, which then sends the traffic to GWLB. The
GWLB in turn sends the traffic to the VM-Series firewall. After inspecting the response traffic, the
firewall sends the response traffic back to the application GWLBE, which in turn sends the traffic
to IGW.
To protect the outbound traffic of the application VPCs:
1. Create a GWLBE(GWLBE3 in the figure above) in the centralized firewall VPC. Ensure that you
have separate subnets for GWLB endpoint, Transit Gateway attachment, NAT Gateway within
the Security VPC.
2. Create a NAT Gateway in the Security VPC.
3. Add route tables as follows:
1. Route table with Application subnet association - Add route destined to 0.0.0.0/0 with
target as TGW. This is in addition to the VPC local route.
2. Route tables in Security VPC:
• Route table with TGW attachment subnet association - In addition to VPC local route,
add route destined to 0.0.0.0/0 with target as GWLBE3.
• Route table with GWLBE subnet association - In addition to VPC local route, add route
destined to 0.0.0.0/0 with target as NAT Gateway. Add route destined to Application
VPC CIDRs with target as TGW.
• Route table with NAT Gateway subnet association - In addition to VPC local route, add
route destined to 0.0.0.0/0 with target as IGW. Add route destined to Application VPC
CIDRs with target as GWLBE3.
3. Add Transit Gateway Route tables as follows:
• Route table with App1-1 VPC TGW-Attachment association - Add route destined to
0.0.0.0/0 with attachment ID as Security VPC TGW attachment.
• Route table with App2-2 VPC TGW-Attachment association - Add route destined to
0.0.0.0/0 with attachment ID as Security VPC TGW attachment.
```
• Route table with Security VPC TGW-Attachment association - (a) Add route destined
```
```
to App-1 VPC CIDR with attachment ID as Application-1 VPC TGW attachment. (b)
```
Add route destined to App-2 VPC CIDR with attachment ID as Application-2 VPC TGW
attachment.
```
With this configuration in place, outbound traffic initiated from Application(App1) is sent to
```
TGW and TGW forwards that to the Security VPC subnet. The traffic is then routed to Security
```
GWLBE(GWLBE3) which sends the traffic to VM-Series firewall for inspection through GWLB.
```
VM-Series Public Cloud Deployments 115 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on AWS
The VM-Series firewall sends the traffic back to GWLBE3 after inspection and GWLBE3
forwards the traffic to NAT Gateway, which sends the traffic through IGW. Similarly, the
response traffic passes through the NAT Gateway to GWLBE3, VM-Series firewall, and TGW
after which it's routed back to the application.
The East-West traffic is also managed with the routes and configuration described in the steps
above. When the traffic is sent from App1 to App2, the traffic passes through TGW, which
routes the traffic to GWLBE3. The GWLBE3 forwards the traffic to the VM-Series firewall
through GWLB. The VM-Series firewall sends the packet back to GWLBE3 after inspection.
GWLBE3 then forwards the packet to App2 through TGW. The response traffic from App-2 to
App-1 will take the reverse path.
It's recommended to have all subnets in the same AZ to avoid cross-zone traffic
charges.
Enable VM-Series Integration with a Gateway Load Balancer
Where Can I Use This? What Do I Need?
• AWS AWS account
```
Amazon Machine Image (AMI) ID
```
```
VM-Series License (PAYG or BYOL)
```
VM-Series plugin
Panorama
Panorama plugin for AWS
When integrating the VM-Series firewall with a GWLB, you must first enable the VM-Series
firewall to properly process traffic redirected to the firewall by the GWLB endpoints. You can
enable this functionality using the VM-Series firewall CLI, through the VM-Series bootstrapping
package, or the user-data field in the AWS console.
VM-Series firewall deployment with a GWLB requires:
• PAN-OS 10.0.2 or later
• VM-Series plugin 2.0.2 or later
• Panorama 10.0.2 or later if you are using Panorama to manage your firewalls
The table below lists the commands required to enable GWLB traffic inspection with a VPC
endpoint. Operation commands can be used in the bootstrapping init-cfg.txt file or in the user-
data field in the AWS console.
Bootstrap Parameter CLI Command Description
op-command-modes=mgmt-
interface-swap
op-command-modes=mgmt-
interface-swap
Swaps eth0 and eth1. GWLB
by default sends traffic
only to Eth0 of its target
instances. By swapping,
VM-Series Public Cloud Deployments 116 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on AWS
Bootstrap Parameter CLI Command Description
This command
requires the
firewall to
reboot before
taking effect.
Eth0 becomes the data
interface and eth1 becomes
the management interface.
plugin-op-commands=aws-
gwlb-inspect:enable
request plugins vm_series
aws gwlb inspect enable
<yes/no>
Enables the VM-Series
firewall to process traffic
passing through a GWLB.
Manually Integrate the VM-Series with a Gateway Load Balancer
Where Can I Use This? What Do I Need?
• AWS AWS account
```
Amazon Machine Image (AMI) ID
```
```
VM-Series License (PAYG or BYOL)
```
VM-Series plugin
Panorama
Panorama plugin for AWS
Complete the following procedure to manually integrate your VM-Series firewall on AWS with a
GWLB.
If you associate VPC endpoints to an interface or subinterfaces via user data while
bootstrapping and your bootstrap.xml file does not include the interface configuration,
you can configure the interfaces after the firewall boots up.
STEP 1 | Set up the security VPC. See the AWS documentation for more information about creating
your security VPC.
• Create two subnets—one for management and one for data.
• Create two security groups—one for firewall management and one for data.
• The management subnet security groups should allow HTTPS and SSH for management
access.
• Ensure that the security groups in your data VPC allows GENEVE-encapsulated packets
```
(UDP port 6081).
```
• If your deployment includes a transit gateway and traffic that will move between VPCs, you
must enable appliance mode on security VPC attachment.
The target group of the GWLB can’t use HTTP for health checks because the VM-
Series firewall does not allow access with an unsecured protocol. Instead, use another
protocol such as HTTPS or TCP.
VM-Series Public Cloud Deployments 117 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on AWS
STEP 2 | Launch the VM-Series firewall.
1. On the EC2 Dashboard, click Launch Instance.
2. Select the Palo Alto VM-Series AMI. To get the AMI, see Obtain the AMI.
3. Launch the VM-Series firewall on an EC2 instance.
1. Choose the EC2 instance type for allocating the resources required for the firewall,
and click Next. See VM-Series System Requirements, for resource requirements.
2. Select the security VPC.
3. Select the data subnet to attach to eth0.
4. Add another network interface for eth1 to act as the management interface after the
```
interface swap. Swapping interfaces requires a minimum of two ENIs (eth0 and eth1).
```
• Expand the Network Interfaces section and click Add Device to add another
network interface and configure Management subnet to this interface.
Make sure that your VPC has more than one subnet so that you can add additional
ENIs at launch.
If you launch the firewall with only one ENI:
• The interface swap command will cause the firewall to boot into
maintenance mode.
• Reboot the firewall when you add the second ENI.
• Expand the Advanced Details section and in the User data field enter as text to
perform the interface swap during launch.
mgmt-interface-swap=enable
plugin-op-commands=aws-gwlb-inspect:enable
If you set the target type to the IP address of a specific interface on the
VM-Series firewall, you don’t need to enable management interface swap.
5. Accept the default Storage settings. The firewall uses volume type SSD (gp2).
6. If prompted, select an appropriate SSD option for your setup.
7. (Optional) Tagging. Add one or more tags to create your own metadata to identify
and group the VM-Series firewall. For example, add a Name tag with a Value that
VM-Series Public Cloud Deployments 118 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on AWS
helps you remember that the ENI interfaces have been swapped on this VM-Series
firewall.
8. Select the data Security Group for eth0 (data interface). Enable traffic on UDP port
6081.
If you enable health checks to the firewall, you can’t use HTTP. Instead, use another
protocol such as HTTPS or TCP.
9. Select Review and Launch. Review that your selections are accurate and click Launch.
10.Select an existing key pair or create a new one, and acknowledge the key disclaimer.
This key pair is required for first time access to the firewall. It's also required
to access the firewall in maintenance mode.
```
11.Download and save the private key to a safe location; the file extension is .pem. You
```
can’t regenerate this key, if lost.
It takes 5-7 minutes to launch the VM-Series firewall. You can view the progress on
the EC2 Dashboard. When the process completes, the VM-Series firewall displays on
the Instances page of the EC2 Dashboard.
```
STEP 3 | Attach the management security group to eth1 (management interface). Allow SSH and
```
HTTPS. See the AWS Documentation for more information.
```
STEP 4 | Create and assign an Elastic IP address (EIP) to the ENI used for management access (eth1) to
```
the firewall.
1. Select Elastic IPs and click Allocate New Address.
2. Select EC2-VPC and click Yes, Allocate.
3. Select the newly allocated EIP and click Associate Address.
4. Select the Network Interface and the Private IP address associated with the
management interface and click Yes, Associate.
VM-Series Public Cloud Deployments 119 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on AWS
STEP 5 | Configure a new administrative password for the firewall.
On the VM-Series firewall CLI, you must configure a unique administrative password
before you can access the web interface of the firewall. To log in to the CLI, you require
the private key that you used to launch the firewall.
1. Use the EIP to SSH into the command-line interface(CLI) of the VM-Series firewall. You
will need the private key that you used or created above and using the username admin
to access the CLI.
If you're using PuTTY for SSH access, you must convert the .pem format to a .ppk
format. See https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/putty.html
2. Enter the following command to log in to the firewall:
ssh-i <private_key.pem> admin@<public-ip_address>
3. Configure a new password, using the following command and follow the onscreen
```
prompts:
```
configure
set mgt-config users admin password
4. If you have a BYOL that needs to be activated, set the DNS server IP address so that
the firewall can access the Palo Alto Networks licensing server. Enter the following
command to set the DNS server IP address:
set deviceconfig system dns-setting servers primary <ip_address>
5. Commit your changes with the command:
commit
6. Terminate the SSH session.
VM-Series Public Cloud Deployments 120 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on AWS
STEP 6 | Configure the dataplane network interface as a Layer 3 interface on the firewall.
On the application servers within the VPC, define the dataplane network interface of
the firewall as the default gateway.
1. Using a secure connection (HTTPS) from your web browser, login using the Elastic IP
```
Address and password you assigned during initial configuration (https://<Elastic_IP
```
```
address>). You will see a certificate warning; that’s okay. Continue to the webpage.
```
2. Select Network > Interfaces > Ethernet.
3. Click the link for ethernet 1/1 and configure as follows:
• Interface Type: Layer3
• On the Config tab, assign the interface to the default virtual router.
• On the Config tab, expand the Security Zone drop-down and select New Zone.
Define a new zone and leave the remaining fields with default values and then click
OK.
• On the IPv4 tab, select DHCP Client.
```
If using DHCP, select DHCP Client; the private IP address that you assigned to the
```
ENI in the AWS management console will be automatically acquired.
• On the Advanced tab, create a management profile to enable HTTP service as part of
management profile creation and allow Health check probes from GWLB.
```
• (optional) On the IPv6 tab, select Enable IPv6 on this Interfaceand select DHCPv6
```
Client.
The VM-Series for AWS behind a GWLB only supports IPv6 as part of AWS
Dualstack, meaning that clients communicate with load balancers using both
IPv4 and IPv6 addresses. IPv6 only is not supported on the AWS GWLB. See
AWS documentation for more information.
Additionally, you must create a security policy that allows IPv6 traffic.
4. Click Commit. Verify that the link state for the interface is up.
STEP 7 | Create security policies to allow/deny traffic.
Because the VM-Series treats traffic as intrazone when integrated with a GWLB, a
default intrazone rule allows all traffic. It is a best practice to override the default
intrazone rule with a deny action for traffic that does not match any of your other
security policy rules.
1. Select Policies > Security on the web interface of the firewall.
2. Click Add, and specify the security zones, applications and logging options that you
would like to execute to restrict and audit traffic traversing through the network.
STEP 8 | Commit the changes on the firewall.
VM-Series Public Cloud Deployments 121 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on AWS
VM-Series Integration with AWS Cloud WAN
Where Can I Use This? What Do I Need?
• AWS AWS account
```
Amazon Machine Image (AMI) ID
```
```
VM-Series License (PAYG or BYOL)
```
VM-Series plugin
Panorama
Panorama plugin for AWS
```
AWS Cloud WAN is a managed wide area networking (WAN) service that enables you to build a
```
unified network that interconnects cloud and on-premises environments. It provides a centralized
dashboard to connect on-premises, branch offices, data centers, and Amazon VPCs across the
AWS global network and even other cloud providers.
```
Deploying a cloud WAN lets you employ Next-Generation Firewalls (NGFW) and intrusion
```
```
prevention systems (IPS) to inspect network traffic as part of a defense-in-depth strategy. This
```
is done using a separate and centralized security VPC where security appliances are set up, and
traffic is routed in and out using cloud WAN. Having a separate security VPC provides a simplified
and centralized way to manage security inspection.
Cloud WAN helps with connectivity within AWS through AWS Network Manager, an interface,
which centrally manages your global network. A global network is a single private network that
acts as the root-level container for your network objects and can contain both transit gateways
and a core network. The core network consists of network policies, attachments such as VPCs,
and transit gateway route tables.
Cloud WAN allows mapping of VPCs to segments and the regional connection point for your
attachments as defined in the policy. Policies can be defined for traffic redirection between the
same or different segments to be inspected by a firewall.
You can use cloud WAN services to:
• Deploy a security VPC behind GWLB in a security segment and redirect traffic arriving from
cloud attachments to the VPC, before forwarding to the destination.
• Collect logs and manage activities such as auto scaling, TAG collection, and so on, in Panorama
managed firewalls.
• Filter and inspect traffic to/from the internet using north-south traffic.
• Inspect traffic for inter VPC communication
AWS Cloud WAN can be deployed using two methods:
• Federating Transit Gateways with Cloud WAN – In this method you replace statically created
transit gateway peering connections with Cloud WAN. While federating transit gateways
with Cloud WAN, you will need to register the transit gateways using the AWS Network
Manager and create peering between the transit gateways and create attachments to the
transit gateways, and then apply the Cloud WAN configuration.
VM-Series Public Cloud Deployments 122 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on AWS
• Cloud WAN only – In this method Cloud WAN is used for all connectivity and transit gateways
are removed.
Considerations before deploying the AWS Cloud WAN:
• Peering between transit gateways and cloud WAN is supported in the same region, and not
across regions.
• Cloud WAN does not support native integration with AWS Direct Connect.
• For use cases that require AWS site-to-site VPN connections over Direct Connect using
private IP addresses, ensure that you connect Cloud WAN with a transit gateway.
• While deploying Cloud WAN along with transit gateways, ensure that the transit gateway ASN
is different from the ASN used for Cloud WAN’s core network edges.
• While creating the core network, ensure that you add all the regions your VPCs are configured
to, in the Edge locations section under core network policy settings. You will also need to
```
create segments and add the type of segment (Dev, Prod, Management, or Security) that these
```
regions belong to, under the segment name.
Use Cases
You can use Cloud WAN to route traffic between:
```
• VPCs in the same segment and in the same region (isolated attachments).
```
• VPCs in different segments of the same region.
```
• VPCs in the same segment across different regions (isolated attachments).
```
• VPCs in different segments across different regions.
Deploy the AWS Cloud WAN
```
Let us consider a use case where VPCs are in the same segment and in the same region (isolated
```
```
attachments). To configure this setup, deploy the VM-Series firewall behind a GWLB similar to
```
VM-Series integration with an AWS Gateway Load Balancer. You can deploy the VM-Series
firewall behind the GWLB in a security VPC, which is directly connected to a Cloud WAN or
through a transit gateway with a Cloud WAN attachment.
To migrate completely off the transit gateway, you must connect your VPCs directly to the
Cloud WAN.
Egress traffic from the Production VPC is routed to the Cloud WAN, which is then routed to
the Security VPC for inspection and sent out through NAT gateway and internal gateway. In the
reverse direction, traffic from the Security VPC reaches the Security segment and then based on
the routing configuration, is sent to the VPC attachment.
VM-Series Public Cloud Deployments 123 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on AWS
To inspect traffic between VPCs in the same segment and the same region with AWS Cloud
```
WAN(only) deployment, execute the following tasks:
```
VM-Series Public Cloud Deployments 124 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on AWS
1. Log in to AWS Network Manager and Create global network.
VM-Series Public Cloud Deployments 125 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on AWS
VM-Series Public Cloud Deployments 126 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on AWS
VM-Series Public Cloud Deployments 127 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on AWS
2. Create a core network and core network policy.
Use the AWS Cloud WAN console to create a core network policy version following these
```
tasks:
```
• Configure the network settings.
VM-Series Public Cloud Deployments 128 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on AWS
VM-Series Public Cloud Deployments 129 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on AWS
• To edit a policy version, click Policy versions, select the required policy and click Edit.
Make necessary changes and click Create Policy.
• After the change set the state of the policy version changes to Ready to execute,
execute the policy by clicking View or apply change set . Alternatively, click Compare
policy version to view the JSON document.
• • Create network policy segments within your core network.
While configuring policy versions, ensure that you add the applications – APP VPC 1
```
(10.1.0.0/16) and APP VPC 2(10.2.0.0/16) in the Prod segment and the firewall, and
```
```
Security VPC (100.64.0.0/16) in the security segment.
```
VM-Series Public Cloud Deployments 130 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on AWS
• Create segment sharing and segment route actions.
• Create policy attachments.
```
You may choose to add tags such as Prod Segment (value) to the Segment (key).
```
These tags are reflected only after you add the segments in the Cloud WAN.
VM-Series Public Cloud Deployments 131 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on AWS
3. Create an attachment.
• Use a VPC or transit gateway route table as an attachment type while creating an
attachment.
• To ensure that the VM-Series firewall can inspect traffic that is routed between
VPC attachments, you must enable appliance mode on the VPC attachment for the
security VPC containing the VM-Series firewall.
VM-Series Public Cloud Deployments 132 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on AWS
VM-Series Public Cloud Deployments 133 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on AWS
4. Update VPC Route tables.
Now that the necessary Cloud WAN constructs are in place, the VPCs need to be adjusted to
facilitate packet forwarding toward the core network. The application and firewall instances or
the respective VPCs need to be tagged similar to that of the segment. Add specific tags to the
attachment to match the attachment created during Create policy attachments. of step 2.
To enable communication between attachment VPCs and the Core network, VPC route tables
need to be updated from the existing target transit gateway route to the corresponding Core
Network ARN as shown below.
VM-Series Public Cloud Deployments 134 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on AWS
VM-Series Public Cloud Deployments 135 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on AWS
VM-Series Public Cloud Deployments 136 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on AWS
Packet Walkthrough
The following steps describe a packet walkthrough when an EC2 instance in Application VPC 1
communicates with an EC2 instance in Application VPC 2:
```
• When a client in APP VPC 1(10.1.0.0/16) starts a connection to a server in APP VPC 2
```
```
(10.2.0.0/16), it does a VPC (App subnet) route table lookup. The packet matches the default
```
route entry with the Core Network ARN as the target and the packet gets routed to the Core
Network.
VM-Series Public Cloud Deployments 137 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on AWS
• When the packet arrives at the core network, it does a Prod Segment Route table lookup
because APP VPC 1 is associated with the Prod Segment. The packet matches the default
entry with Security attachment as the target and the packet gets routed to Security VPC.
VM-Series Public Cloud Deployments 138 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on AWS
```
• When the packet arrives at the Security VPC(100.64.0.0/16) attachment, it does a VPC
```
```
(CWAN subnet) route table lookup. The packet matches the default route with firewall
```
endpoint 1 as the target and the packet gets routed to a firewall, through the firewall’s
endpoint, for inspection.
• The firewall inspects the traffic, compares it to its security policy, and allows it through. The
```
firewall routes the packet back to the firewall’s endpoint, where it does a VPC (Firewall subnet)
```
route table lookup. The packet matches the default route entry with the Core Network ARN as
the target, and the packet gets routed to the Core Network.
• When the packet arrives at the core network, it does a Shared Security Route table lookup
because the Security VPC is associated with the Security Segment. The packet matches the
VM-Series Public Cloud Deployments 139 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on AWS
```
APP VPC 2 CIDR(10.2.0.0/16) entry with APP VPC 2 Attachment as the target and the packet
```
gets routed to APP VPC 2.
```
• When the packet arrives at APP VPC 2, it does a VPC (CWAN subnet) route table lookup. The
```
packet matches the VPC CIDR entry with local as the target and the packet gets routed to
Instance.
Return traffic traces the same path in the opposite direction.
Associate a VPC Endpoint with a VM-Series Interface
Where Can I Use This? What Do I Need?
• AWS AWS account
```
Amazon Machine Image (AMI) ID
```
```
VM-Series License (PAYG or BYOL)
```
VM-Series plugin
Panorama
Panorama plugin for AWS
You can associate one or more VPC endpoints with an interface or subinterface of the VM-
Series firewall. You can provide consistent policy enforcement by associating all the endpoints
in a single VPC to the same subinterface on the firewall. Or, if your deployment has VPCs with
overlapping IP address, you can associate endpoints in different VPCs with different subinterfaces
for differentiated policy enforcement.
Associating a VPC to an interface or subinterface is not mandatory to integrate the VM-
Series firewall with a GWLB.
VM-Series Public Cloud Deployments 140 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on AWS
You can configure interfaces and associate a VPC with firewall interfaces using the following
```
methods:
```
• Include the interface configuration in your bootstrap.xml file and the association
commands as part of the init-cfg.txt file or AWS user-data.
• After deploying the firewall, manually configure your interfaces and use the firewall CLI to
associate your VPCs with interfaces.
You can associate multiple VPC endpoints to a single interface on the VM-Series firewall.
However, you must associate each VPC endpoint individually. For example, to associate
VPC endpoint 1 and VPC endpoint 2 with subinterface ethernet1/1.2, you must execute the
association command separately for each VPC endpoint.
The table below describes the commands used to associate a VPC with an interface. You can
include the operation command in your init-cfg.txt file or in the AWS user-data.
Bootstrap Parameter CLI Command Description
plugin-op-commands=
aws-gwlb-associate-
```
vpce:<vpce-
```
id>@ethernet<subinterface>
request plugins vm_series
aws gwlb associate vpc-
endpoint <vpce-id> interface
<subinterface>
Associates a VPC endpoint
with an interface or
subinterface on the firewall.
The specified interface is
assigned to a security zone.
VM-Series Public Cloud Deployments 141 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on AWS
Bootstrap Parameter CLI Command Description
— request plugins vm_series
aws gwlb disassociate vpc-
endpoint <vpce-id> interface
<subinterface>
Disassociates a VPC
endpoint with an interface or
subinterface on the firewall.
The specified interface is
assigned to a security zone.
— show plugins vm_series aws
gwlb
Displays the operating state
of the firewall as it relates to
your GWLB deployment. It
does not display the firewall
configuration.
For example, if you configure
an association to an interface
that does not exist, that
association is configured but
not part of the operating
state. Therefore, it is not
displayed.
When associating a VPC endpoint using the bootstrapping init-cfg.txt file or AWS user-date, you
can list multiple interfaces or subinterfaces together. All the commands must be on a single line in
a comma-separated list with no spaces as shown in the following example.
plugin-op-commands=aws-gwlb-inspect:enable,aws-gwlb-associate-
```
vpce:vpce-0913731043b5c0ebc@ethernet1/1.1,aws-gwlb-associate-
```
```
vpce:vpce-08207ccb4cb23a1de@ethernet1/1.1,aws-gwlb-associate-
```
```
vpce:vpce-07b66cca88821d6e1@ethernet1/1.2,aws-gwlb-associate-
```
```
vpce:vpce-0a9a583fdb928492b@ethernet1/1.3
```
If you are using subinterfaces to separate traffic, create a subinterface for each VPC and associate
it to a VPC.
VM-Series Public Cloud Deployments 142 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on AWS
STEP 1 | Configure the subinterface.
1. Log in to the firewall web interface.
2. Select Network > Interface.
3. Highlight ethernet1/1 and click Add Subinterface.
4. Enter a numerical suffix (1-9,999) to identify the subinterface.
5. Enter a VLAN Tag (1 to 4,094) for the subinterface. This field is required but the VLAN is
not used.
6. Select Virtual Router as default.
7. Select a Security Zone.
8. On the IPv4 tab, set the Type to DHCP Client.
9. Click OK.
10. Repeat this command for each VPC endpoint.
STEP 2 | Associate the interface with a VPC endpoint.
1. Log in to the firewall CLI.
2. Execute the following command:
request plugins vm_series aws gwlb associate vpc-endpoint <vpce-
id> interface <subinterface>
For example:
request plugins vm_series aws gwlb associate vpc-endpoint
vpce-02c4e6g8ha97h7e39 interface ethernet1/1.4
You can locate the VPC endpoint ID in the AWS console.
3. Repeat this command for each interface and VPC endpoint association.
STEP 3 | Verify your interface to VPC endpoint associations.
show plugins vm_series aws gwlb
GWLB enabled: True
Overlay Routing: False
-------------------------------------------------------------
VPC endpoint Interface
VM-Series Public Cloud Deployments 143 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on AWS
--------------------------------------------------------------
vpce-0aeb1a919bd4ae609 ethernet1/1.1
vpce-0294375bfe413f04a ethernet1/1.2
STEP 4 | If necessary, you can use the following command to disassociate a VPC endpoint from an
interface.
request plugins vm_series aws gwlb disassociate vpc-endpoint <vpce-
id> interface <subinterface>
Enable Overlay Routing for the VM-Series on AWS
Where Can I Use This? What Do I Need?
• AWS AWS account
```
Amazon Machine Image (AMI) ID
```
```
VM-Series License (PAYG or BYOL)
```
VM-Series plugin
Panorama
Panorama plugin for AWS
Overly routing requires PAN-OS 10.0.5 or later.
Using overlay routing in your VM-Series firewall integration the AWS GWLB allows you to
```
use two-zone policy to inspect traffic leaving (egressing) your AWS environment. This allows
```
packets to leave the VM-Series firewall through a different interface than that which they entered
through.
When overlay routing is configured, the firewall is able to perform a Layer 3 route lookup a
packet’s inner header. If the destination is the same as the ingress interface, the packet will be
```
directed as normal. All future packets in the session are treated as vwire; as if overlay routing
```
was not enabled. If the packet is going to an outbound destination, the firewall decapsulates
the packet and forwards the packet to the IGW or NAT gateway. When the packet returns, the
firewall reapplies the encapsulation.
VM-Series Public Cloud Deployments 144 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on AWS
Use the following procedure to enable overlay routing.
STEP 1 | Before you begin, ensure that you create different subnets for the trust and untrust
interfaces.
STEP 2 | Manually Integrate the VM-Series with a Gateway Load Balancer.
```
STEP 3 | (Optional) Associate a VPC Endpoint with a VM-Series Interface.
```
STEP 4 | Use overlay routing CLI command. This CLI command is not required if you included the
overlay routing op-command in the AWS user-data or the init-cfg.txt bootstrap file.
1. Log in to the firewall command line interface.
2. Execute the following command.
request plugins vm_series aws gwlb overlay-routing enable yes
STEP 5 | Log in to the firewall web interface.
VM-Series Public Cloud Deployments 145 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on AWS
STEP 6 | Disable Automatically create default route pointing to default gateway provided by server
```
on the trust (ingress) interface.
```
1. Select Network > Interfaces > Ethernet.
2. Click on your trust interface and then the IPv4 tab.
3. Uncheck Automatically create default route pointing to default gateway provided by
server.
4. Click OK.
VM-Series Public Cloud Deployments 146 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on AWS
STEP 7 | Configure interface Ethernet 1/2.
1. Select Network > Interfaces > Ethernet.
2. Select the Interface Type—Layer 3.
3. On the Config tab, expand the Security Zone drop-down and select New Zone. This
zone will act as your untrust zone and directing outbound traffic out of your security
VPC. Define the new zone, such as VM-Series-untrust, and then click OK.
4. On the IPv4 tab, select DHCP Client.
5. Select Automatically create default route pointing to default gateway provided by
server.
6. Click OK.
VM-Series Public Cloud Deployments 147 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on AWS
STEP 8 | Configure a virtual router.
1. Select Network > Virtual Routers > Add.
2. Enter a descriptive Name for the virtual router.
3. Under Interfaces, Add Ethernet1/1, any subinterfaces under Ethernet1/1, and
Ethernet1/2.
4. Click Static Routes > Add.
1. Enter a descriptive name for the static route.
2. As the Destination, enter the private IP address of the application VPC subnet.
3. Select the trust (ingress) interface from the Interface drop-down.
4. For Next Hop, select IP Address and enter the IP address of the gateway of the trust
interface. You can find the gateway IP address on Network > Interfaces > Ethernet >
Dynamic-DHCP Client.
5. Click OK.
VM-Series Public Cloud Deployments 148 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on AWS
5. Ensure that the static routes can reach all application VPC in your deployment. You
```
can either make a few large aggregated routes (covering all RFC1918) or application
```
VPC specific routes. If you use subinterfaces, you do not need to route back to the sub-
interface. The egress check looks only for the matching interface instead of the matching
subinterface.
6. Click OK.
STEP 9 | Create a NAT policy for traffic egressing Ethernet1/2.
1. Select Policies > NAT > Add.
2. Enter a descriptive Name for the NAT policy rule.
3. Select ipv4 from the NAT Type drop-down.
4. On the Original Packet tab, set the Source Zone to any and the Destination Zone to
```
your untrust (egress) zone.
```
5. On the Translated Packet tab, set the following parameters.
• Translation Type: Dynamic IP and Port
• Address Type: Interface Address
```
• Interface: Select your untrust (egress) port from the drop-down.
```
• IP Address: None
6. Click OK.
VM-Series Public Cloud Deployments 149 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on AWS
STEP 10 | Commit your changes.
VM-Series Auto Scaling Group with AWS Gateway Load Balancer
Where Can I Use This? What Do I Need?
• AWS AWS account
```
Amazon Machine Image (AMI) ID
```
```
VM-Series License (PAYG or BYOL)
```
VM-Series plugin
Panorama
Panorama plugin for AWS
The Palo Alto Networks auto scaling template for AWS helps you integrate and configure the VM-
Series firewall with a GWLB to protect applications deployed in AWS. The template leverages
AWS scalability features to independently and automatically scale VM-Series firewalls deployed in
AWS to meet surges in application workload resource demand.
These templates are community supported.
This solution provides a security VPC template and an application template. The security VPC
template deploys the VM-Series firewall auto scaling group, a GWLB, a GWLBE, GWLBE subnet,
security attachment subnet, and a NAT gateway for each availability zone. Download the
CloudFormation templates from the Palo Alto Networks GitHub Repository.
The VM-Series auto scaling template for integration with an AWS GWLB includes the following
building blocks:
Building Block Description
PAN
Components
• Panorama running 10.0.2 or later
• PAN-OS 10.0.2 or later
• VM-Series plugin 2.0.2 or later installed on Panorama
Firewall
template
```
Based on the number of availability zones (AZs) you choose, the firewall-
```
new-vpc-v3.0.template deploys the following:
VM-Series Public Cloud Deployments 150 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on AWS
Building Block Description
```
(Community
```
supported
```
template)
```
The template supports a maximum of four AZs.
• Subnets for Lambda management, transit gateway attachments, GWLB
endpoints, and NAT gateways, as well as trust subnets.
• Routes tables for each subnet
• Transit gateway attachments and route tables
• NAT and internet gateways
• An auto scaling group with one VM-Series firewall per AZ.
• One GWLB and a GWLB endpoint in each AZ.
The VPC CIDR for the firewall template should be larger than /23.
Due to the many variations in a production environment that includes but
isn’t limited to specific number components, such as subnets, availability
zones, route tables, and security groups. Deploy the firewall-new-vpc-
v3.0.template in a new VPC.
The VM-Series auto scaling template for AWS does not deploy
a transit gateway or Panorama. Deploy a transit gateway and
Panorama before launching firewall-new-vpc-v3.0.template.
Application
template
```
(Community
```
supported
```
template)
```
```
Based on the number of availability zones (AZs) you choose, the panw-aws-
```
app-v3.0.template deploys the following:
The template supports a maximum of four AZs.
• Subnets for Lambda, transit gateway attachments, GWLB endpoints,
application load balancers.
• Routes tables for each subnet, as well as an inbound route table associated
with the internet gateway to direct inbound traffic to the GWLB endpoint.
• One application load balancer
• One internet gateway
• An auto scaling group with one Ubuntu instance per AZ.
The VPC CIDR for the application template should be larger than /23.
The application template is intended to be used as an example for
validating the security template.
Lambda
functions
AWS Lambda provides robust, event-driven automation without the need
for complex orchestration software. In addition to deploying the components
described in the rows above, the firewall-new-vpc-v3.0.template
performs the following functions:
VM-Series Public Cloud Deployments 151 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on AWS
Building Block Description
```
• Adds or removes an interface (ENI) when a firewall is launched or
```
terminated.
• Deletes all the associated resources when you delete a stack or terminate
an instance.
• Removes a firewall as a Panorama managed device when there is a scale-in
event.
• Deactivates the license when a scale-in event results in a firewall
termination.
• Monitors the transit gateway periodically for new attachments or
detachments, and updates the route tables accordingly in the security
VPC.
Bootstrap files
The
bootstrap.xml
file provided
in the GitHub
repository is
provided for
testing and
evaluation
only. For a
production
deployment,
you must
modify the
sample
credentials
in the
bootstrap.xml
prior to
launch.
This solution requires the init-cfg.txt file and the bootstrap.xml file so that the
VM-Series firewall has the basic configuration for handling traffic.
• The init-cfg.txt file includes the mgmt-interface-swap operational
command to enable the firewall to receive dataplane traffic on its primary
```
interface (eth0). This auto scaling solution requires the swapping of the
```
dataplane and management interfaces to enable the GWLB to forward
web traffic to the auto scaling tier of VM-Series firewalls.
• The bootstrap.xml file enables basic connectivity for the firewall
network interfaces and allows the firewall to connect to the AWS
CloudWatch namespace that matches the stack name you enter when you
launch the template.
If you need to delete these templates from AWS, always delete the application template
first. Attempting to delete the firewall template causes the deletion to fail.
Before Launching the Templates
Where Can I Use This? What Do I Need?
• AWS AWS account
```
Amazon Machine Image (AMI) ID
```
```
VM-Series License (PAYG or BYOL)
```
VM-Series plugin
VM-Series Public Cloud Deployments 152 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on AWS
Where Can I Use This? What Do I Need?
Panorama
Panorama plugin for AWS
Before you launch the templates to integrate a VM-Series firewall auto scaling group with an
AWS GWLB, you must complete the following procedure.
STEP 1 | Ensure that you have the following before you begin.
• Obtain the auth code for a bundle that supports the number of firewalls that might
be required for your deployment. You must save this auth code in a text file named
```
authcodes (no extensions), and put the authcodes file in the /license folder of the
```
bootstrap package.
• Download the files required to launch the VM-Series Gateway Load Balancer template from
the GitHub repository.
• Create a Transit Gateway. This transit gateway connects your security and application
VPCs.
```
• Take note of the transit gateway ID; you will need it later when deploying the template.
```
• You must add a 0.0.0.0/0 route to the application attachment route table pointing to the
security attachment to protect east-west and outbound traffic.
• Ensure that Default route table association and Default route table propagation are
disabled.
• The recommended VPC CIDR for the firewall and application templates should be larger
than /23.
The target group of the gateway GWLB cannot use HTTP for health checks because
the VM-Series firewall does not allow access with an unsecured protocol. Instead use
HTTPS or TCP.
STEP 2 | Deploy Panorama running 10.0.2 and configure the following.
Panorama must allow AWS public IP addresses. The VM-Series firewall accesses Panorama
using the external IP address of the NAT gateway created by the template.
STEP 3 | Download and install the VM-Series plugin on Panorama.
1. Select Panorama > Plugins and use Check Now to look for new plugin packages. The
VM-Series plugin name is vm_series.
2. Consult the plugin release notes to determine which version provides upgrades useful to
you.
3. Select a version of the plugin and select Download in the Action column.
4. Click Install in the Action column. Panorama alerts you when the installation is complete.
5. To view the plugin, select Device > VM-Series.
VM-Series Public Cloud Deployments 153 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on AWS
STEP 4 | Configure the template.
1. Log in to the Panorama web interface.
2. Select Panorama > Templates and click Add.
1. Enter a descriptive Name.
2. Click OK.
3. Configure the virtual router.
1. Select Network > Virtual Routers.
2. Ensure that you have selected the template you create above from the Template
drop-down.
3. Click Add.
4. Name the virtual router using the following format: VR-<tempstackname>.
5. Enable ECMP on the virtual router.
6. Click OK.
4. Configure the interface and create the zone.
1. Select Network > Interfaces and click Add Interface.
2. Select Slot 1 and then select the Interface name (for example, ethernet 1/1).
3. Set Interface Type to Layer 3.
4. On the Config tab, select New Zone from the Security Zone drop-down. In the Zone
dialog, define a Name for new zone, for example Internet, and then click OK.
5. In the Virtual Router drop-down, select virtual router your created above.
6. Select IPv4 and click DHCP Client.
7. Click OK.
5. Create a management profile that allows HTTPS on the interface created above to
support Health Checks.
1. Select Network > Network Profiles > Interface Mgmt and click Add.
2. Select the protocols that the interface permits for management traffic: Ping, Telnet,
SSH, HTTP, HTTP OCSP, HTTPS, or SNMP.
Don’t enable HTTP or Telnet because those protocols transmit in cleartext
and therefore aren’t secure.
6. Assign the Interface Management profile to an interface.
1. Select Network > Interfaces, select the type of interface (Ethernet, VLAN, Loopback,
```
or Tunnel), and select the interface.
```
2. Select Advanced > Other info and select the Interface Management Profile you just
added.
3. Click OK.
7. Configure the DNS server and FQDN refresh time.
1. Select Device > Setup > Services and click the Edit icon.
2. Set the Primary DNS Server to 169.254.169.253. This is the AWS DNS address.
3. Set the Minimum FQDN Refresh Time to 60 seconds.
VM-Series Public Cloud Deployments 154 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on AWS
4. Click OK.
8. Commit your changes. This is required before proceeding to the next step.
9. Create an administrator.
1. Select Device > Administrators.
2. Enter pandemo as the Name.
3. Set the Password to demopassword and Confirm.
4. Click OK.
10. Commit your changes.
STEP 5 | Configure a template stack and add the template to the template stack.
1. Select Panorama > Templates and Add Stack.
2. Enter a unique Name to identify the stack.
3. Click Add and select the template.
4. Click OK to save the template stack.
STEP 6 | Create the Device Group.
1. Select Panorama > Device Groups.
2. Click Add.
3. Enter a descriptive Name.
4. Click OK.
5. Add an allow all security pre-rule.
1. Ensure that you have selected the device group you create above from the Device
Group drop-down.
2. Select Policies > Security > Pre Rules and click Add.
3. Enter a descriptive Name.
4. Under Source, User, Destination, Application, and Service/URL Category, select any.
5. Under Actions, select Allow.
6. Click OK.
6. Commit your changes.
STEP 7 | Add the license deactivation API key for the firewall to Panorama.
1. Log in to the Customer Support Portal.
2. Select Products > Assets > API Key Management.
3. Copy the API key.
4. Use the CLI to install the API key copied in the previous step.
request license api-key set key <key>
VM-Series Public Cloud Deployments 155 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on AWS
STEP 8 | After deploying Panorama, you must open the following ports as described below on the
Panorama security group in AWS.
```
• Port 443 (HTTPS)—Upon initial deployment of the firewall template, leave HTTPS open so
```
Lambda can connect to Panorama.
When you secure port 443 you specify an IP address range from which you will allow
connections, as well as the EIPs assigned to the NAT gateways. The number of NAT
gateways in your deployment depends on the number of availability zones you configure.
To find NAT gateway EIPs in AWS, go to VPC > NAT Gateways. Note the EIP information
for the security group for HTTPS.
Additionally, to allow Panorama to release the firewall license after stack deletion, you must
allow traffic from the CIDR range of the region where you deployed the firewall template.
You can find the CIDR for your region at this link.
• Port 3978—Port 3978 must be able to receive traffic from any IP address.
Launch the Firewall Template
Where Can I Use This? What Do I Need?
• AWS AWS account
```
Amazon Machine Image (AMI) ID
```
```
VM-Series License (PAYG or BYOL)
```
VM-Series plugin
Panorama
Panorama plugin for AWS
This workflow describes how to deploy the firewall template.
STEP 1 | Modify the init-cfg.txt file and upload it to the /config folder.
Because you use Panorama to bootstrap the VM-Series firewalls, your init-cfg.txt file
should be modified as follows. No bootstrap.xml file is needed.
Ensure that you use the device group and template names you created above in the init-cfg.txt
file.
```
type=dhcp-client
```
ip-address=
default-gateway=
```
netmask=
```
ipv6-address=
ipv6-default-gateway=
```
hostname=
```
vm-auth-key=
panorama-server=
panorama-server-2=
```
tplname=
```
```
dgname=
```
dhcp-send-hostname=yes
VM-Series Public Cloud Deployments 156 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on AWS
dhcp-send-client-id=yes
dhcp-accept-server-hostname=yesdhcp-accept-server-domain=yes
plugin-op-commands=aws-gwlb-inspect:enable
Your init-cfg.txt file must include plugin-op-commands=aws-gwlb-inspect:enable.
This is required when integrating the VM-Series firewall with a GWLB.
Add the device certificate auto-registration PIN to the init-cfg.txt file to automatically install a
device certificate when your VM-Series firewall instance is deployed.
STEP 2 | Add the license auth code in the /license folder of the bootstrap package.
1. Use a text editor to create a new text file named authcodes (no extension).
2. Add the authcode for your BYOL licenses to this file, and save. The authcode must
represent a bundle, and it must support the number of firewalls that might be required
for your deployment. If you use individual authcodes instead of a bundle, the firewall
only retrieves the license key for the first authcode in the file.
```
STEP 3 | Upload Lambda code for the firewall template (panw-aws.zip) and the Application
```
```
template (app.zip) to an S3 bucket. You can use the same S3 bucket that you use for
```
bootstrapping.
If the Application stack is managed by a different account than the firewall, use the Application
account to create another s3 bucket in the same AWS region as the firewall template and copy
app.zip to that s3 bucket.
STEP 4 | Select the firewall template.
1. In the AWS Management Console, select CloudFormation > Create Stack.
2. Select Upload the latest firewall template from the Git repository, to choose the firewall
template to deploy the resources that the template launches. Click Open and Next.
3. Specify the Stack name. The stack name allows you to uniquely identify all the resources
that are deployed using this template.
STEP 5 | Enter a descriptive Name for your stack. The name must be 28 characters or less.
STEP 6 | Configure the parameters for the VPC.
1. Enter the number of availability zones and select the region from the availability zone
drop-down.
2. Look up the AMI ID for the VM-Series firewall and enter it. Make sure that the AMI ID
matches the AWS region, PAN-OS version and the BYOL or PAYG licensing option you
VM-Series Public Cloud Deployments 157 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on AWS
```
opted to use. See Get the VM-Series Firewall Amazon Machine Image (AMI) ID for more
```
information.
3. Select the EC2 Key pair (from the drop-down) for launching the firewall. To log in to the
firewalls, you must provide the name of this key pair and the private key associated with
it.
4. Select Yes if you want to Enable Debug Log. Enabling the debug log generates more
verbose logs that help with troubleshooting issues with the deployment. These logs are
generated using the stack name and are saved in AWS CloudWatch.
By default, the template uses CPU utilization as the scaling parameter for the VM-Series
firewalls. Custom PAN-OS metrics are automatically published to the CloudWatch namespace
that matches the stack name you specified earlier.
STEP 7 | Specify the name of the Amazon S3 bucket.
1. Enter the name of the S3 bucket that contains the bootstrap package.
If the bootstrap bucket isn’t set up properly or if you enter the bucket name incorrectly,
the bootstrap process fails, and you cannot log in to the firewall. Health checks for the
load balancers also fail.
2. Enter the name of the S3 bucket that contains the panw-aws.zip file. As mentioned
earlier you can use one S3 bucket for the Bootstrap and Lambda code.
STEP 8 | Specify the keys for enabling API access to the firewall and Panorama.
1. Enter the key that the firewall must use to authenticate API calls. The default key is
based on the sample file and you should only use it for testing and evaluation. For a
production deployment, you must create a separate PAN-OS login just for the API call
and generate an associated key.
2. Enter the API Key to allow AWS Lambda to make API calls to Panorama. For a
production deployment, you should create a separate login just for the API call and
generate an associated key.
STEP 9 | Add your AWS account numbers. You must provide the account number used to deploy any
VPC that is connected to your GWLB. Add these values as a comma-separated list. You can
add additional account numbers after deploying the template.
To locate your account number, click your AWS username in the top right of the AWS console
and select My Security Credentials.
STEP 10 | Enter the transit gateway ID. The transit gateway ID is required to secure east-west and
outbound traffic. If you do not enter a transit gateway ID, the template assumes that only
inbound traffic should be inspected by firewalls integrated with the GWLB.
STEP 11 | Enter the CIDR for the security VPC.
STEP 12 | Review the template settings and launch the template.
1. Select I acknowledge that this template might cause AWS CloudFormation to create
IAM resources.
2. Click Create to launch the template. The CREATE_IN_PROGRESS event displays.
3. On successful deployment the status updates to CREATE_COMPLETE.
VM-Series Public Cloud Deployments 158 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on AWS
STEP 13 | Verify that the template has launched all required resources.
```
STEP 14 | Create rules allowing the NAT gateway IP address(es) on the security group where your
```
Panorama appliance is deployed. This is required to allow your firewalls to connect to
VM-Series Public Cloud Deployments 159 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on AWS
Panorama. You can find the list of NAT gateway IP addresses in the CFT security stack
output.
VM-Series Public Cloud Deployments 160 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on AWS
1. Access the AWS VPC console.
2. Select Security Groups on the navigation pane.
3. Select the security where Panorama is deployed.
4. Select Actions > Edit Inbound Rules > Add rule.
5. Add rules allowing the NAT gateway IP addresses for Custom TCP Rule for port range
3978.
6. Click Save rules.
Launch the Application Template
Where Can I Use This? What Do I Need?
• AWS AWS account
```
Amazon Machine Image (AMI) ID
```
```
VM-Series License (PAYG or BYOL)
```
VM-Series plugin
Panorama
Panorama plugin for AWS
Complete the following procedure to launch the application template.
STEP 1 | Create an S3 bucket from which you will launch the application template.
• If this is a cross-account deployment, create a new bucket.
• If there is one account you can create a new bucket or use the S3 bucket you created
```
earlier (you can use one bucket for everything).
```
STEP 2 | Upload the app.zip file into the S3 bucket.
VM-Series Public Cloud Deployments 161 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on AWS
STEP 3 | Select the application launch template you want you launch.
1. In the AWS Management Console, select CloudFormation > CreateStack
2. Select Upload a template to Amazon S3, to choose the application template to deploy
the resources that the template launches within the same VPC as the firewalls, or to a
different VPC. Click Open and Next.
3. Specify the Stack name. The stack name allows you to uniquely identify all the resources
that are deployed using this template.
```
STEP 4 | Select the Availability Zones (AZ) that your setup will span in Select list of AZ.
```
STEP 5 | Enter a descriptive VPC Name.
STEP 6 | Configure the parameters for Lambda.
1. Enter the S3 bucket name where app.zip is stored.
2. Enter the name of the zip file name.
STEP 7 | Select the EC2 instance type for the Ubuntu web server launched by this template.
STEP 8 | Enter your Amazon EC2 key pair.
VM-Series Public Cloud Deployments 162 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on AWS
```
STEP 9 | Enter the name of the service configuration (Service Name) for the GWLB endpoint in the
```
security VPC.
1. Select DynamoDB from the Services drop-down in the AWS console.
2. Select Tables and locate your security VPC table. The table name will be <stack name>-
gwlb-<region>. For example—cft-deployment-gwlb-us-east-1.
3. Click the Items tab and copy the Service Name.
4. Paste the Service Name into the application template configuration parameters.
VM-Series Public Cloud Deployments 163 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on AWS
STEP 10 | Enter the transit gateway ID. This is the same transit gateway you created before deploying
the firewall template.
STEP 11 | Review the template settings and launch the template.
STEP 12 | After the application has been deployed, you must add a route to the transit gateway route
table to enable east-west and outbound traffic inspection.
1. Log in to the AWS VPC console.
2. Select Transit Gateway Route Tables and choose your transit gateway route table.
This route table is created by the template and is called <app-stack-name>-<region>-
PANWAppAttRt.
3. Select Routes and click Create static route.
4. Enter 0.0.0.0/0 in the CIDR field.
5. From the Choose attachment drop-down, select the VM-Series firewall VPC attachment.
6. Click Create static route.
```
STEP 13 | (Optional) Create a bastion host (also called a jump box) to access the web server created by
```
the application template.
1. Create a public-facing subnet in your application VPC.
2. Add a route to this subnet from your IP address to the internet gateway.
3. Create a new EC2 instance in the public subnet with a public IP address.
4. Create a security group for this EC2 instance that allows SSH from your IP address.
Enable Session Resiliency on VM-Series for AWS
Where Can I Use This? What Do I Need?
• AWS AWS account
```
Amazon Machine Image (AMI) ID
```
```
VM-Series License (PAYG or BYOL)
```
VM-Series plugin
Panorama
Panorama plugin for AWS
Session resiliency allows the VM-Series firewall to maintain session continuity during a failure
```
event. The AWS Gateway Load Balancer (GWLB) a can detect and deregister unhealthy VM-
```
Series firewalls deployed in a horizontally scalable cluster behind the GWLB. With session
resiliency enabled, the GWLB can rehash existing traffic sessions flowing toward an unhealthy
VM-Series and redirect the traffic to a healthy VM-Series firewall.
To maintain sessions failing over to healthy VM-Series firewalls, you must deploy a Redis cache
accessible to your VM-Series firewalls— ElastiCache for Redis for AWS. The Redis cache maintains
session information. When your load balancer detects an unhealthy VM-Series firewall, the
load balancer rebalances traffic to a healthy VM-Series firewall. The healthy VM-Series firewall
VM-Series Public Cloud Deployments 164 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on AWS
accesses the Redis cache for session information and continues to inspect and forward the
existing traffic.
Your load balancer must meet the following requirements to support session resiliency.
• Your load balancer must be a Gateway Load Balancer.
• Set Rebalance Existing Flow to On to allow the GWLB to rehash existing flows. See the AWS
documentation for more information.
• Enable In-Transit Encryption to encrypt connections to the Redis cache using TLS.
```
• According to AWS Gateway Load Balancer (GWLB) specifications, typical failover
```
events take 30 to 120 seconds to complete. To ensure that connections persist despite
these delays, both the client and server nodes need to be configured with a TCP
```
Retransmission Timeout (RTO) policy capable of accommodating this latency.
```
• We recommend consulting your OS vendor’s documentation for specific tuning
parameters. The following example demonstrates how to adjust these settings on a
Windows-based environment.
Health Check Configuration
Cross-zone load balancing Enabled
Target Group
Deregistration delay 60 seconds
Healthy/Unhealthy threshold 2
Health check timeout 2 seconds
Health check interval 5 seconds
Your ElastiCache for Redis instance must meet the following requirements to support session
resiliency on the VM-Series firewall.
• Standard tier
• Deploy the Redis cache in the same region and zone as your VM-Series firewall instances.
• Ensure that your firewall management interface will be able to access your ElastiCache
instance. For example, have both devices in the same VPC.
When sizing your memory store for Redis, use the following guidelines.
• Base the size of Redis cache on the maximum number of sessions supported by your VM-
Series firewall instance. See Maximum Limits Based on Tier and Memory to the maximum
sessions for your firewall.
• Each redis entry per session uses approximately 128 bytes. Therefore, one VM-Series firewall
that supports 10,000,000 sessions requires approximately 1.3 GB of storage. And a cluster of
10 VM-Series firewalls requires at least 13 GB.
VM-Series Public Cloud Deployments 165 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on AWS
• Use the following formula to calculate the redis requirements.
```
(128 x <number of sessions>) x 10-9 = require redis cache size per firewall
```
Before enabling session resiliency, review the AWS blog about Target Failover for
Existing Traffic Flows.
```
Session resiliency can't be enabled on existing VM-Series firewall instances; only on newly
```
deployed instances.
Enable session resiliency on the VM-Series firewall by passing the configuration as part of a
bootstrapping init-cfg.txt file or in the user data field. Before you begin, make sure you have the
following information.
Field Description
op-command-modes=mgmt-interface-
swap
Allows you to swap the management interface
```
(MGT) with the dataplane interface (ethernet
```
```
1/1) when deploying the firewall. For details,
```
see Management Interface Mapping for Use
with Amazon ELB.
plugin-op-commands= 1. Enables session resiliency.
VM-Series Public Cloud Deployments 166 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on AWS
Field Description
1. set-sess-ress:True
2. aws-gwlb-inspect:enable
2. Enables the VM-Series firewall to process
traffic passing through a GWLB.
redis-endpoint= Provide the IP address or FQDN and port of
your ElastiCache Redis endpoint.
```
redis-auth= (optional) The auth code your VM-Series
```
firewall uses to connect with the Redis
endpoint.
STEP 1 | Deploy your ElastiCache for Redis instance.
STEP 2 | Prepare your bootstrap files.
op-command-modes=mgmt-interface-swap
plugin-op-commands=set-sess-ress:True, aws-gwlb-inspect:enable
redis-endpoint=<redis-IP-address:port>
redis-auth=<redis-auth-code>
STEP 3 | Bootstrap your firewalls.
VM-Series Public Cloud Deployments 167 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on AWS
High Availability for VM-Series Firewall on AWS
Where Can I Use This? What Do I Need?
• AWS AWS account
```
Amazon Machine Image (AMI) ID
```
```
VM-Series License (PAYG or BYOL)
```
VM-Series plugin
Panorama
Panorama plugin for AWS
```
The VM-Series firewall on AWS supports active/passive HA only; if it is deployed with Amazon
```
```
Elastic Load Balancing (ELB), it does not support HA (in this case ELB provides the failover
```
```
capabilities).
```
To ensure redundancy, you can deploy the VM-Series firewalls on AWS in an active/passive
```
high availability (HA) configuration. The active peer continuously synchronizes its configuration
```
and session information with the identically configured passive peer. A heartbeat connection
between the two devices ensures failover if the active device goes down. There are two options
for deploying the VM-Series firewall on AWS in HA—Secondary IP move and Dataplane Interface
```
(ENI) move.
```
To ensure that all traffic to your internet-facing applications passes through the firewall, you
have two options. You can either configure the application’s public IP address on the Untrust
```
interface (E1/2 in the illustration above) of the VM-Series firewall, or you can configure AWS
```
ingress routing. The AWS ingress routing capability allows you to associate route tables with the
AWS internet gateway and add route rules to redirect the application traffic through the VM-
Series firewall. This redirection ensures that all internet traffic passes through the firewall without
having to reconfigure the application endpoints.
Secondary IP Move
When the active peer goes down, the passive peer detects this failure and becomes active.
Additionally, it triggers API calls to the AWS infrastructure to move the configured secondary IP
addresses from the dataplane interfaces of the failed peer to itself. Additionally, AWS updates the
route tables to ensure that traffic is directed to the active firewall instance. These two operations
VM-Series Public Cloud Deployments 168 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on AWS
ensure that inbound and outbound traffic sessions are restored after failover. This option allows
you to take advantage of DPDK to improve the performance of your VM-Series firewall instances
and provides better failover time than interface-move HA, while supporting all the features
provided by interface-move.
Secondary IP Move HA requires VM-Series plugin 2.0.1 or later.
You can now configure up to four IP addresses per SD-WAN interface, to achieve HA
failover in active/passive configurations of your AWS public cloud environment. You
can achieve this by configuring a second floating IP address on the SD-WAN interfaces.
The floating IP on the SD-WAN interface of the external zone must match with that of
the internal zone. This feature is supported on PAN-OS 11.1.0 and above and on IPv4
addresses only.
Dataplane Interface Move
When the active peer goes down, the passive peer detects the failure and becomes active.
Additionally, it triggers API calls to the AWS infrastructure to move all the dataplane interfaces
```
(ENIs) from the failed peer to itself.
```
HA Links
The devices in an HA pair use HA links to synchronize data and maintain state information. On
AWS, the VM-Series firewall uses the following ports:
VM-Series Public Cloud Deployments 169 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on AWS
• Control Link—The HA1 link is used to exchange hellos, heartbeats, and HA state information,
and management plane sync for routing and User-ID information. This link is also used to
synchronize configuration changes on either the active or passive device with its peer.
The management port is used for HA1. TCP port 28769 and 28260 for cleartext
```
communication; port 28 for encrypted communication (SSH over TCP).
```
• Data Link—The HA2 link is used to synchronize sessions, forwarding tables, IPSec security
associations and ARP tables between devices in an HA pair. Data flow on the HA2 link is
```
always unidirectional (except for the HA2 keep-alive); it flows from the active device to the
```
passive device.
```
Ethernet1/1 must be assigned as the HA2 link; this is required to deploy the VM-Series firewall
```
```
on AWS in HA. The HA data link can be configured to use either IP (protocol number 99) or
```
```
UDP (port 29281) as the transport.
```
The VM-Series firewall on AWS does not support backup links for HA1 or HA2.
Heartbeat Polling and Hello Messages
The firewalls use hello message and heartbeats to verify that the peer device is responsive and
operational. Hello messages are sent from one peer to the other at the configured Hello Interval to
verify the state of the device. The heartbeat is an ICMP ping to the HA peer over the control link,
and the peer responds to the ping to establish that the devices are connected and responsive. For
```
details on the HA timers that trigger a failover, see HA Timers. (The HA timers for the VM-Series
```
```
firewall are the same as that of the PA-5200 Series firewalls).
```
Device Priority and Preemption
The devices in an HA pair can be assigned a device priority value to indicate a preference for
which device should assume the active role and manage traffic upon failover. If you need to use
a specific device in the HA pair for actively securing traffic, you must enable the preemptive
behavior on both the firewalls and assign a device priority value for each device. The device with
the lower numerical value, and therefore higher priority, is designated as active and manages all
traffic on the network. The other device is in a passive state, and synchronizes configuration and
state information with the active device so that it is ready to transition to an active state should a
failure occur.
By default, preemption is disabled on the firewalls and must be enabled on both devices. When
```
enabled, the preemptive behavior allows the firewall with the higher priority (lower numerical
```
```
value) to resume as active after it recovers from a failure. When preemption occurs, the event is
```
logged in the system logs.
Preemption is not recommended for HA in the VM-Series firewall on AWS.
HA Timers
```
High availability (HA) timers are used to detect a firewall failure and trigger a failover. To reduce
```
the complexity in configuring HA timers, you can select from three profiles: Recommended,
Aggressive, and Advanced. These profiles auto-populate the optimum HA timer values for the
specific firewall platform to enable a speedier HA deployment.
VM-Series Public Cloud Deployments 170 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on AWS
Use the Recommended profile for typical failover timer settings and the Aggressive profile for
faster failover timer settings. The Advanced profile allows you to customize the timer values to
suit your network requirements.
HA Timer on the VM-Series
on AWS
Default values for Recommended/Aggressive profiles
Promotion hold time 2000/500 ms
Hello interval 8000/8000 ms
Heartbeat interval 2000/1000 ms
Max number of flaps 3/3
Preemption hold time 1/1 min
Monitor fail hold up time 0/0 ms
Additional master hold up
time
500/500 ms
IAM Roles for HA
Where Can I Use This? What Do I Need?
• AWS AWS account
```
Amazon Machine Image (AMI) ID
```
```
VM-Series License (PAYG or BYOL)
```
VM-Series plugin
Panorama
Panorama plugin for AWS
AWS requires that all API requests must be cryptographically signed using credentials issued
by them. To enable API permissions for the VM-Series firewalls that will be deployed as an HA
pair, you must create a policy and attach that policy to a role in the AWS Identity and Access
```
Management (IAM) service. The role must be attached to the VM-Series firewalls at launch. The
```
policy gives the IAM role permissions for initiating API actions required to move interfaces or
secondary IP addresses from the active peer to the passive peer when failover is triggered.
For detailed instructions on creating policy, refer to the AWS documentation on Creating
Customer Managed Polices. For detailed instructions on creating an IAM role, defining which
accounts or AWS services can assume the role, defining which API actions and resources the
application can use upon assuming the role, refer to the AWS documentation on IAM Roles for
Amazon EC2.
VM-Series Public Cloud Deployments 171 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on AWS
The IAM policy, which is configured in the AWS console, must have permissions for the following
```
actions and resources (at a minimum):
```
The following IAM actions, permissions, and resources are required to enable HA. To
enable AWS Cloudwatch monitoring, see Enable CloudWatch Monitoring on the VM-
Series Firewall for the required IAM action.
IAM Action,
Permission, or
Resource
Description Interface Move Secondary IP
Move
AttachNetworkInterfaceFor permission to attach an ENI to
an instance.
DescribeNetworkInterfacesFor fetching the ENI parameters
to attach an interface to the
instance.
DetachNetworkInterfaceFor permission to detach the ENI
from the EC2 instance.
DescribeInstances For permission to obtain
information on the EC2 instances
in the VPC.
AssociateAddress For permissions to move public
IP addresses associated with the
primary IP addresses from the
passive to active interfaces.
AssignPrivateIpAddressesFor permissions to assign
secondary IP addresses and
associated public IP addresses to
interfaces on the passive peer.
DescribeRouteTables For permission to retrieve all route
tables associated to the VM-Series
firewall instances.
ReplaceRoute For permissions to update the
AWS route table entries.
GetPolicyVersion For permission to retrieve AWS
policy version information.
GetPolicy For permission to retrieve AWS
policy information.
VM-Series Public Cloud Deployments 172 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on AWS
IAM Action,
Permission, or
Resource
Description Interface Move Secondary IP
Move
ListAttachedRolePoliciesFor permission to retrieve the list
of all managed policies attached to
a specified IAM role.
ListRolePolicies For permission to retrieve a list
of the names of inline policies
embedded in a specified IAM role.
GetRolePolicy For permission to retrieve a
specified inline policy embedded
in a specified IAM role.
policy For permission to access the IAM
policy Amazon Resource Name
```
(ARN).
```
role For permission to access the IAM
roles ARN.
route-table For permission to access the route
table Amazon Resource Name
```
(ARN) to update it upon failover.
```
```
Wild card (*) In the ARN field, use the * as a
```
wild card.
The following screenshot shows the access management settings for the IAM role described
above for secondary-IP HA:
VM-Series Public Cloud Deployments 173 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on AWS
The minimum permissions you need for interface move HA are:
```
{ "Version":"2012-10-17", "Statement":[ { "Sid":"VisualEditor0", "Effect":"Allow", "Action":
```
[ "ec2:AttachNetworkInterface", "ec2:DetachNetworkInterface", "ec2:DescribeInstances",
```
"ec2:DescribeNetworkInterfaces" ], "Resource":"*" } ]}
```
The minimum permissions you need for secondary IP move HA are:
```
{ "Statement": [ { "Action": [ "ec2:AttachNetworkInterface", "ec2:DetachNetworkInterface",
```
"ec2:DescribeInstances", "ec2:DescribeNetworkInterfaces", "ec2:AssignPrivateIpAddresses",
"ec2:AssociateAddress", "ec2:DescribeRouteTables" ], "Effect": "Allow", "Resource": [ "*" ],
```
"Sid": "VisualEditor0" }, { "Action": "ec2:ReplaceRoute", "Effect": "Allow", "Resource":
```
```
"arn:aws:ec2:*:*:route-table/*", "Sid": "VisualEditor1" } ], "Version": "2012-10-17"}
```
Configure Active/Passive HA on AWS Using a Secondary IP
Where Can I Use This? What Do I Need?
• AWS AWS account
```
Amazon Machine Image (AMI) ID
```
```
VM-Series License (PAYG or BYOL)
```
VM-Series plugin
Panorama
Panorama plugin for AWS
Complete the following procedure to deploy new VM-Series firewalls as an HA pair with
secondary IPv4 addresses.
VM-Series Public Cloud Deployments 174 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on AWS
STEP 1 | Before you deploy the VM-Series firewalls for your HA pair, ensure the following:
• Use the VPC Planning Worksheet to verify that your VPC is prepared for the VM-Series
firewall.
• Secondary IP Move HA requires VM-Series plugin 2.0.1 or later.
• Deploy both HA peers in the same AWS availability zone.
Starting with VM-Series plugin 2.0.3, you can deploy the HA peers in different availability
zones. Although this type of deployment is not recommended, it is supported.
• Create an IAM role and assign the role to the VM-Series firewalls when you deploy the
instances.
• The active and passive firewalls must have at least four interfaces each—a management
interface, an HA2 interface, an untrust interface, and a trust interface. Additionally, the trust
and untrust interfaces on the active firewall must be assigned a secondary IPv4 address.
The management interface must be used as the HA1 interface.
• Verify that the network and security components are defined suitably.
```
• Enable communication to the internet from the management interface (at least udp/53
```
```
and tcp/443). The default VPC includes an internet gateway, and if you install the VM-
```
Series firewall in the default subnet it has access to the internet.
• Create subnets. Subnets are segments of the IP address range assigned to the VPC in
which you can launch the EC2 instances. The VM-Series firewall must belong to the
public subnet so that it can be configured to access the internet.
• Create a data security group that includes the firewall data interfaces. Additionally,
```
configure the security to allow all traffic (0.0.0.0/0), so security is enforced by the
```
firewalls. This is required to maintain existing sessions during failover.
• Add routes to the route table for a private subnet to ensure that traffic can be routed
across subnets and security groups in the VPC, as applicable.
• If you are bootstrapping the firewall, create the necessary S3 bucket containing the
required bootstrap files.
VM-Series Public Cloud Deployments 175 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on AWS
STEP 2 | Deploy the VM-Series Firewall on AWS.
1. If your VM-Series firewalls do not have the VM-Series plugin 2.0.1 or later installed,
upgrade the plugin before continuing.
2. Configure ethernet 1/1 as the HA2 interface on each HA peer.
1. Open the Amazon EC2 console.
2. Select Network Interface and then select your network interface.
3. Select Actions > Manage IP Addresses.
4. Leave the field blank to allow AWS to assign an IP address dynamically or enter an IP
address within the subnet range for the VM-Series firewall.
5. Click Yes and Update.
6. Select Actions > Change Source/Dest. Check and select Disable.
7. Repeat this process on the second (to be passive) HA peer.
3. Add a secondary IPv4 address to your dataplane interfaces on the first (to be active) HA
peer.
1. Select Network Interface and then select your network interface.
2. Select Actions > Manage IP Addresses > IPv4 Addresses > Assign new IP.
3. Leave the field blank to allow AWS to assign an IP address dynamically or enter an IP
address within the subnet range for the VM-Series firewall.
4. Click Yes and Update.
4. Associate an Elastic (public) IP address on the primary instance with the untrust interface
of the active peer.
1. Select Elastic IPs and then choose the Elastic IP address to associate.
2. Select Actions > Associate Elastic IP.
3. Under Resource Type, select Network Interface.
4. Choose the network interface with which to associate the Elastic IP address.
5. Click Associate.
5. For outbound traffic inspection, add an entry to the subnet route table that sets the next
hop as the firewall trust interface.
1. Select VPC > Route Tables.
2. Choose your subnet route table.
3. Select Actions > Edit routes > Add route.
4. Enter the Destination CIDR Block or IP address.
5. For Target, enter the network interface of the firewall trust interface.
6. Click Save routes.
6. To use AWS Ingress Routing, create a route table and associate the internet gateway to
it. Then add an entry with the next hop set as the active firewall untrust interface.
1. Select Route Tables > Create route table.
2. (Optional) Enter a descriptive Name tag for your route table.
3. Click Create.
VM-Series Public Cloud Deployments 176 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on AWS
4. Click your route table and select Actions > Edit edge associations.
5. Select Internet gateways and choose your VPC internet gateway.
6. Click Save.
7. Click your route table and select Actions > Edit routes.
8. For the Target, select Network Interface and choose the untrust interface of the
active firewall.
9. Click Save routes.
STEP 3 | Configure the interfaces on the firewall. You must configure the HA2 data link and at least
two Layer 3 interfaces for your untrust and trust interfaces. Complete this workflow on the
first HA peer and then repeat the steps on the second HA peer.
1. Log in to the firewall web interface.
2. Select Network > Interfaces > Ethernet and click on your untrust interface.
In this example, the HA2 interface is ethernet 1/1, the trust interface is ethernet 1/2,
and the untrust interface is ethernet 1/3.
3. Click the link for ethernet 1/1 and configure as follows:
• Interface Type: HA
4. Click the link for ethernet 1/2 and configure as follows:
• Interface Type: Layer3
• On the Config tab, assign the interface to the default router.
• On the Config tab, expand the Security Zone drop-down and select New Zone.
Define a new zone, for example trust-zone, and then click OK.
• On the IPv4 tab, select DHCP Client.
• Check Enable.
• On the untrust interface, check Automatically create default route pointing to
default gateway provided by server. This option tells the firewall to create a static
route to a default gateway.
• Repeat these steps for ethernet 1/3.
5. Repeat the above steps on the passive peer.
VM-Series Public Cloud Deployments 177 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on AWS
STEP 4 | Enable HA.
1. Select Device > High Availability > General.
2. Edit the Setup settings.
3. Enter the private IP address of the passive peer in the Peer HA1 IP address field.
4. Click OK.
5. Edit the Election Settings to specify a particular firewall to be the active peer. Enter a
lower numerical Device Priority value on the active firewall.
If both firewalls have the same Device Priority value, the firewall with the lowest MAC
value on the HA1 control becomes the active firewall.
Enabling preemption is not recommended.
6. Click OK.
7. Commit your changes.
8. Repeat the above steps on the passive peer.
```
STEP 5 | Set up the Control Link (HA1) to use the management port.
```
1. Select Device > High Availability > General, and edit the Control Link (HA1) section.
2. (Optional) Select Encryption Enabled, for secure HA communication between the peers.
To enable encryption, you must export the HA key from a firewall and import it into the
peer firewall.
1. Select Device > Certificate Management > Certificates.
2. Select Export HA key. Save the HA key to a network location that the peer firewall
can access.
3. On the peer firewall, navigate to Device > Certificate Management > Certificates,
and select Import HA key to browse to the location that you saved the key and
import it into the peer firewall.
VM-Series Public Cloud Deployments 178 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on AWS
```
STEP 6 | Set up the Data Link (HA2) to use ethernet1/1.
```
1. Select Device > High Availability > General, edit the Data Link (HA2) section.
2. Select Port ethernet1/1.
3. Enter the IP address for ethernet1/1.
This IP address must match the address assigned to the ENI on the EC2 Dashboard.
4. Enter the Netmask.
5. Enter a Gateway IP address if the HA1 interfaces are on separate subnets.
6. Select IP or UDP for Transport. Use IP if you need Layer 3 transport (IP protocol number
```
99). Use UDP if you want the firewall to calculate the checksum on the entire packet
```
```
rather than just the header, as in the IP option (UDP port 29281).
```
7. (Optional) Modify the Threshold for HA2 Keep-alive packets. By default, HA2 Keep-
alive is enabled for monitoring the HA2 data link between the peers. If a failure occurs
```
and this threshold (default is 10000 ms) is exceeded, the defined action will occur. A
```
critical system log message is generated when an HA2 keep-alive failure occurs.
You can configure the HA2 keep-alive option on both firewalls, or just one
firewall in the HA pair. If you enable this option on one firewall, only that firewall
will send the keep-alive messages.
VM-Series Public Cloud Deployments 179 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on AWS
STEP 7 | After you finish configuring HA on both firewalls, verify that the firewalls are paired in
active/passive HA.
1. Access the Dashboard on both firewalls and view the High Availability widget.
2. On the active HA peer, click Sync to peer.
3. Confirm that the firewalls are paired and synced.
• On the passive firewall: the state of the local firewall should display Passive and the
Running Config should show as Synchronized.
• On the active firewall: the state of the local firewall should display Active and the
Running Config should show as Synchronized.
4. From the firewall command line interface, execute the following commands:
• To verify failover readiness:
show plugins vm_series aws ha state
• To show secondary IP mapping:
show plugins vm_series aws ha ips
Configure Active/Passive HA on AWS Using Interface Move
Where Can I Use This? What Do I Need?
• AWS AWS account
```
Amazon Machine Image (AMI) ID
```
```
VM-Series License (PAYG or BYOL)
```
VM-Series plugin
Panorama
Panorama plugin for AWS
Complete the following procedure to configure active-passive HA using interface move mode.
STEP 1 | Make sure that you have followed the prerequisites.
For deploying a pair of VM-Series firewalls in HA in the AWS cloud, you must ensure the
```
following:
```
```
• Select the IAM role you created when launching the VM-Series firewall on an EC2 instance;
```
you cannot assign the role to an instance that is already running. See IAM Roles for HA.
For detailed instructions on creating an IAM role, defining which accounts or AWS services
can assume the role, and defining which API actions and resources the application can use
upon assuming the role, refer to the AWS documentation.
• DPDK is not supported on the VM-Series firewall on AWS in an interface-move HA
deployment. If your have VM-Series plugin 2.0.1 or later on your firewalls, you must disable
DPDK.
Disabling DPDK requires the firewall to reboot. If you are using bootstrapping to deploy
the VM-Series firewall, you can avoid rebooting the firewall by disabling DPDK in the initi-
VM-Series Public Cloud Deployments 180 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on AWS
cfg.txt file by using op-cmd-dpdk-pkt-io=off. See Bootstrap the VM-Series Firewall on
AWS for more information.
• The active firewall in the HA pair must have at a minimum three ENIs: two dataplane
interfaces and one management interface.
The passive firewall in the HA pair, must have one ENI for management, and one ENI that
```
functions as dataplane interface; you will configure the dataplane interface as an HA2
```
interface.
Do not attach additional dataplane interfaces to the passive firewall in the HA pair.
On failover, the dataplane interfaces from the previously active firewall are moved
```
—detached and then attached—to the now active (previously passive) firewall.
```
• The HA peers must be deployed in the same AWS availability zone. While VM-Series HA
Across AWS Availability Zones is not a recommended solution, it is supported.
STEP 2 | Launch the VM-Series Firewall on AWS.
STEP 3 | Once the firewall is up and running, ensure that the failover mode suits your requirement
and change if required.
On firewall with VM-Series plugin 2.0.1 or later, the secondary IP mode is enabled by
default.
```
STEP 4 | (VM-Series plugin 2.0.1 or later) Disable DPDK on the active and passive firewalls. DPDK
```
is enabled by default and interface-move HA mode does not support DPDK, so you must
```
disable it; enabling Packet MMAP.
```
1. Log in to the passive firewall CLI.
2. Disable DPDK using the following command. Executing this command restarts the
firewall.
admin@PA-VM> set system setting dpdk-pkt-io off
STEP 5 | Enable HA.
1. Select Device > High Availability > General, and edit the Setup section.
2. Select Enable HA.
STEP 6 | Configure ethernet 1/1 as an HA interface. This interface must be used for HA2
communication.
1. Select Network > Interfaces.
2. Confirm that the link state is up on ethernet1/1.
3. Click the link for ethernet1/1 and set the Interface Type to HA.
VM-Series Public Cloud Deployments 181 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on AWS
```
STEP 7 | Set up the Control Link (HA1) to use the management port.
```
1. Select Device > High Availability > General, and edit the Control Link (HA1) section.
2. (Optional) Select Encryption Enabled, for secure HA communication between the peers.
To enable encryption, you must export the HA key from a device and import it into the
peer device.
1. Select Device > Certificate Management > Certificates.
2. Select Export HA key. Save the HA key to a network location that the peer device can
access.
3. On the peer device, navigate to Device > Certificate Management > Certificates, and
select Import HA key to browse to the location that you saved the key and import it
in to the peer device.
```
STEP 8 | Set up the Data Link (HA2) to use ethernet1/1.
```
1. Select Device > High Availability > General, edit the Data Link (HA2) section.
2. Select Port ethernet1/1.
3. Enter the IP address for ethernet1/1. This IP address must be the same that assigned to
the ENI on the EC2 Dashboard.
4. Enter the Netmask.
5. Enter a Gateway IP address if the HA1 interfaces are on separate subnets.
6. Select IP or UDP for Transport. Use IP if you need Layer 3 transport (IP protocol number
```
99). Use UDP if you want the firewall to calculate the checksum on the entire packet
```
```
rather than just the header, as in the IP option (UDP port 29281).
```
7. (Optional) Modify the Threshold for HA2 Keep-alive packets. By default, HA2 Keep-
alive is enabled for monitoring the HA2 data link between the peers. If a failure occurs
```
and this threshold (default is 10000 ms) is exceeded, the defined action will occur. A
```
critical system log message is generated when an HA2 keep-alive failure occurs.
You can configure the HA2 keep-alive option on both devices, or just one device
in the HA pair. If you enable this option on one device, only that device will send
the keep-alive messages.
VM-Series Public Cloud Deployments 182 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on AWS
STEP 9 | Set the device priority and enable preemption.
Use this setting if you want to make sure that a specific device is the preferred active device.
For information, see Device Priority and Preemption.
1. Select Device > High Availability > General and edit the Election Settings section.
2. Set the numerical value in Device Priority. Make sure to set a lower numerical value on
the device that you want to assign a higher priority to.
If both firewalls have the same device priority value, the firewall with the lowest
MAC address on the HA1 control link will become the active device.
3. Select Preemptive.
You must enable preemptive on both the active and the passive device.
4. Modify the failover timers. By default, the HA timer profile is set to the Recommended
profile and is suited for most HA deployments.
```
STEP 10 | (Optional) Modify the wait time before a failover is triggered.
```
1. Select Device > High Availability > General and edit the Active/Passive Settings.
2. Modify the Monitor fail hold up time to a value between 1-60 minutes; default is 1
minute. This is the time interval during which the firewall will remain active following a
link failure. Use this setting to avoid an HA failover triggered by the occasional flapping
of neighboring devices.
STEP 11 | Configure the IP address of the HA peer.
1. Select Device > High Availability > General, and edit the Setup section.
2. Enter the IP address of the HA1 port on the peer. This is the IP address assigned to the
```
management interface (ethernet 0/0), which is also the HA1 link on the other firewall.
```
3. Set the Group ID number between 1 and 63. Although this value is not used on the VM-
Series firewall on AWS, but cannot leave the field blank.
STEP 12 | Configure the other peer.
Repeat steps 3 to 9 on the HA peer.
STEP 13 | After you finish configuring both devices, verify that the devices are paired in active/passive
HA.
1. Access the Dashboard on both devices, and view the High Availability widget.
2. On the active device, click the Sync to peer link.
3. Confirm that the devices are paired and synced, as shown below:
• On the passive device: The state of the local device should display passive and the
configuration is synchronized.
• On the active device: The state of the local device should display active and the
configuration is synchronized.
VM-Series Public Cloud Deployments 183 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on AWS
STEP 14 | Verify that failover occurs properly.
1. Verify the HA mode.
show plugins vm_series aws ha failover-mode
2. Verify that the packet IO mode is set to packet MMAP.
show system setting dpdk-pkt-io
3. Shut down the active HA peer.
1. On the EC2 Dashboard, select Instances.
2. From the list, select the VM-Series firewall and click Actions > Stop.
4. Check that the passive peer assumes the role of the active peer and that the dataplane
interfaces have moved over to the now active HA peer.
Migrate Active/Passive HA on AWS
Where Can I Use This? What Do I Need?
• AWS AWS account
```
Amazon Machine Image (AMI) ID
```
```
VM-Series License (PAYG or BYOL)
```
VM-Series plugin
Panorama
Panorama plugin for AWS
Both high availability modes are supported, allowing you to migrate between each mode if your
deployment requires it. Because interface-move mode does not support DPDK, you must disable
it on the VM-Series firewall before completing the migration. Disabling DPDK requires you to
reboot the VM-Series firewall, which will impact any traffic sessions on the active firewall.
Migrate Active/Passive HA on AWS to Secondary IP Mode
Complete the following procedure to migrate your existing VM-Series firewall HA pair from
interface-move HA to secondary-IP HA.
Secondary IP Move HA requires VM-Series plugin 2.0.1 or later.
STEP 1 | Upgrade the VM-Series Plugin on the passive HA peer and then the active peer.
VM-Series Public Cloud Deployments 184 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on AWS
STEP 2 | Create a secondary IP address for all data interfaces on the active peer.
1. Log in to the AWS EC2 console.
2. Select Network Interface and then choose then select your network interface.
3. Select Actions > Manage IP Addresses > IPv4 Addresses > Assign new IP.
4. Leave the field blank to allow AWS to assign an IP address dynamically or enter an IP
address within the subnet range for the VM-Series firewall.
5. Click Yes and Update.
```
STEP 3 | Associate a secondary Elastic (public) IP address with the untrust interface of the active peer.
```
1. Log in to the AWS EC2 console.
2. Select Elastic IPs and then choose then select the Elastic IP address to associate.
3. Select Actions > Associate Elastic IP.
4. Under Resource Type, select Network Interface.
5. Choose the network interface with which to associate the Elastic IP address.
6. Click Associate.
STEP 4 | Create a route table pointing to the subnet containing the trust interface.
1. Select Route Tables > Create route table.
2. (Optional) Enter a descriptive Name tag for your route table.
3. Select your VPC.
4. Click Create.
5. Select Subnet Associations > Edit subnet associations.
6. Select the Associate checkbox for the subnet containing the trust interface.
7. Click Save.
STEP 5 | Update the IAM roles with additional actions and permissions required to migrate to
secondary IP move HA.
IAM Action, Permission, or Resource Description
AssociateAddress For permissions to move public IP addresses
associated with the primary IP addresses from the
passive to active interfaces.
AssignPrivateIpAddresses For permissions to move secondary IP addresses and
associated public IP addresses from the passive to
active interfaces.
UnassignPrivateIpAddress For permissions to unassign secondary IP addresses
and associated public IP addresses from interfaces
on the active peer.
DescribeRouteTables For permission to retrieve all route tables associated
to the VM-Series firewall instances.
VM-Series Public Cloud Deployments 185 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on AWS
IAM Action, Permission, or Resource Description
ReplaceRoute For permission to update the AWS route table
entries.
GetPolicyVersion For permission to retrieve AWS policy version
information.
GetPolicy For permission to retrieve AWS policy information.
ListAttachedRolePolicies For permission to retrieve the list of all managed
policies attached to a specified IAM role.
ListRolePolicies For permission to retrieve a list of the names of
inline policies embedded in a specified IAM role.
GetRolePolicy For permission to retrieve a specified inline policy
embedded in a specified IAM role.
policy For permission to access the IAM policy Amazon
```
Resource Name (ARN).
```
role For permission to access the IAM roles ARN.
route-table For permission to access the route table ARN.
```
Wild card (*) In the ARN field, use the * as a wild card.
```
```
STEP 6 | Create new interfaces (ENIs) on the passive firewall in the same subnet as the active firewall
```
data interfaces.
Do not assign secondary IP addresses to these new interfaces.
1. Open the Amazon EC2 console.
2. Select Network Interfaces > Create Network Interfaces.
3. Enter a descriptive Name for your new interface.
4. Under Subnet, select the subnet of the untrust interface of the active firewall.
5. Under Private IP, leave the field blank to allow AWS to assign an IP address dynamically
or enter an IP address within the subnet range for the untrust interface of the active
firewall.
6. Under Security groups, select one or more security groups.
7. Select Yes and Create.
8. Select Actions > Change Source/Dest. Check and select Disable.
9. Repeat these steps for the subnet of the trust interface of the active firewall.
VM-Series Public Cloud Deployments 186 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on AWS
STEP 7 | Attach the new ENIs to the passive firewall instance. Attach these ENIs to the passive
firewall in the correct order because the secondary IP HA method is based on the network
interface index assigned by AWS. For example, if eth1/2 on the active firewall is part of
subnet A and eth1/3 is part of subnet B, then you must attach the interface that is part of
subnet A and the interface that is part of subnet B. In this example, AWS has assigned an
index value of 2 to eth1/2 and a value of 3 to eth1/3. This indexing must be maintained for
the failover to occur successfully.
1. To attach the ENIs created above, select the untrust interface your created and click
Attach.
2. Select the Instance ID of the passive firewall and click Attach.
3. Repeat these steps for the trust interface.
STEP 8 | Log in to the passive and set the interfaces to get their IP addresses through DHCP.
1. Log in to the passive VM-Series firewall web interface.
2. Select Network > Interfaces.
3. Click on the first data interface.
4. Select IPv4.
5. Select DHCP Client.
6. On the untrust interface only, select Automatically create default route pointing to
default gateway provided by server.
7. Click OK.
8. Repeat this process for each data interface.
STEP 9 | If you have configured any NAT policies on the VM-Series firewall that reference the private
IP addresses of the data interfaces, those policies must be updated to reference the newly
assigned secondary IP addresses instead.
1. Access the web interface of the active VM-Series firewall.
2. Select Policies > NAT.
3. Click on the NAT policy rule to be modified and then Translated Packet.
4. Under Translated Address, click Add and enter the secondary IP address created in
AWS.
5. Delete the primary IP address.
6. Click OK.
7. Repeat these steps as necessary.
8. Commit your changes.
VM-Series Public Cloud Deployments 187 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on AWS
STEP 10 | Enable secondary IP HA failover mode.
1. Access the VM-Series firewall CLI on the active peer.
2. Execute the following command.
request plugins vm_series aws ha failover-mode secondary-ip
3. Commit your changes.
4. Confirm your HA mode by executing the following command.
show plugins vm_series aws ha failover-mode
5. Repeat this command on the passive peer.
STEP 11 | After your finish configuring HA on both firewalls, verify that the firewalls are paired in
active/passive HA.
1. Access the Dashboard on both firewalls and view the high availability widget.
2. On the active HA peer, click Sync to peer.
3. Confirm that the firewalls are paired and synced.
• On the passive firewall: the state of the local firewall should display Passive and the
Running Config should show as Synchronized.
• On the active firewall: the state of the local firewall should display Active and the
Running Config should show as Synchronized.
4. From the firewall command-line interface, execute the following commands:
• To verify failover readiness:
show plugins vm_series aws ha state
• To show secondary IP mapping:
show plugins vm_series aws ha ips
Migrate Active/Passive HA on AWS to Interface Move Mode
Complete the following procedure to migrate your existing VM-Series firewall HA pair from
secondary-IP HA to interface-move HA.
STEP 1 | Disable DPDK support on the passive HA peer. Interface-move HA mode does not support
```
DPDK, so you must disable it; enabling Packet MMAP.
```
1. Log in to the passive firewall CLI.
2. Disable DPDK using the following command. Executing this command restarts the
firewall.
admin@PA-VM> set system setting dpdk-pkt-io off
VM-Series Public Cloud Deployments 188 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on AWS
STEP 2 | Disable DPDK support on the active HA peer.
1. Log in to the active firewall CLI.
2. Disable DPDK using the following command. Executing this command restarts the
firewall.
admin@PA-VM> set system setting dpdk-pkt-io off
Restarting the firewall will impact traffic.
STEP 3 | Change the HA mode on the active peer from secondary-IP mode to interface-move mode.
1. Access the VM-Series firewall CLI on the active peer.
2. Execute the following command.
request plugins vm_series aws ha failover-mode interface-move
3. Commit your changes.
4. Confirm your HA mode by executing the following command.
show plugins vm_series aws ha failover-mode
5. Repeat this command on the passive peer.
STEP 4 | Delete the data interfaces from the passive firewall instance.
1. Log in to the AWS EC2 console.
2. Select Network Interfaces.
3. Select a data interface on the passive firewall instance and click Delete.
4. In the Delete Network Interface window, click Yes, Delete.
5. Repeat this process for each data interface on the passive firewall instance.
VM-Series Public Cloud Deployments 189 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on AWS
AWS Shared VPC Monitoring
Where Can I Use This? What Do I Need?
• AWS AWS account
```
Amazon Machine Image (AMI) ID
```
```
VM-Series License (PAYG or BYOL)
```
VM-Series plugin
Panorama
Panorama plugin for AWS
AWS Shared VPC set up enables you to share and manage VPC subnets with multiple AWS
accounts and deploy resources in a shared and centrally managed network. Configure multiple
monitoring definitions with the same VPC-ID and with different AWS credentials. This enables
you to track IPs from multiple accounts within the shared VPC enhancing the security and
network management.
If you try setting up a monitoring definition using the same VPC-ID with the same
credentials, the configuration window in Panorama throws an error message on a
duplicate entry.
```
Prerequisites:
```
• PAN-OS version 10.2.4 or above
• AWS Plugin version 5.4.0
Setting Up Monitoring Definitions in AWS Shared VPC
To set up and enable monitoring of VM instances across multiple AWS accounts in a shared VPC,
perform the following steps:
VM-Series Public Cloud Deployments 190 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on AWS
1. Set up a shared VPC.
1. Create a Shared VPC in your AWS Account.
VM-Series Public Cloud Deployments 191 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on AWS
VM-Series Public Cloud Deployments 192 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on AWS
2. Create a Subnet within this shared VPC.
3. Using the AWS Resource Access Manager (RAM) share the subnet with AWS Account.
VM-Series Public Cloud Deployments 193 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on AWS
VM-Series Public Cloud Deployments 194 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on AWS
2. Create virtual machines in the shared subnets in Account A and Account B. For example, create
VM1 in Account A and VM2 in Account B within the shared subnet.
VM-Series Public Cloud Deployments 195 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on AWS
3. Configure the IAM roles for cross-account access.
1. In Account B, go to IAM > Roles > Create Role.
2. Select AWS Account as the trusted entity type.
3. Select Another AWS Account and enter Account A’s Account ID.
4. Assign the AmazonEC2ReadOnlyAccess policy to the role.
VM-Series Public Cloud Deployments 196 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on AWS
VM-Series Public Cloud Deployments 197 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on AWS
5. Note the Role ARN after creation.
VM-Series Public Cloud Deployments 198 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on AWS
4. In Panorama, configure the AWS plugin for monitoring.
1. In panorama, go to AWS > NGFW > Set Up > IAM Roles.
2. Select Account A’s IAM credentials for onboarding.
VM-Series Public Cloud Deployments 199 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on AWS
VM-Series Public Cloud Deployments 200 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on AWS
3. Create first Monitoring Definition for Account A IAM role, select the VPC-ID of the shared
VPC.
VM-Series Public Cloud Deployments 201 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on AWS
VM-Series Public Cloud Deployments 202 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on AWS
VM-Series Public Cloud Deployments 203 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on AWS
If you try setting up a monitoring definition using the same VPC-ID with the same
credentials, the configuration window on Panorama throws an error message on a
duplicate entry.
4. Verify that the AWS portal dashboard displays VM1’s IP address.
VM-Series Public Cloud Deployments 204 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on AWS
VM-Series Public Cloud Deployments 205 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on AWS
5. Create Second Monitoring Definition for Account B.
1. Create a new Monitoring Definition.
2. Using Account A’s IAM Role, create a new monitoring definition.
3. Enter the Role ARN from Account B’s IAM role.
VM-Series Public Cloud Deployments 206 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on AWS
VM-Series Public Cloud Deployments 207 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on AWS
4. Select the same Shared VPC ID.
VM-Series Public Cloud Deployments 208 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on AWS
VM-Series Public Cloud Deployments 209 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on AWS
5. After the monitoring retrieval process, verify that the AWS dashboard now displays VM2’s
IP address.
VM-Series Public Cloud Deployments 210 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on AWS
VM-Series Public Cloud Deployments 211 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on AWS
You can also check the VM2’s IP on the Panorama Monitoring Definition Detailed status
window.
If VPC is shared to the third account, you can repeat the step of creating and getting the
role ARN from the third account. Create a third monitoring definition to harvest IP-tags
from the third account. This provides you the flexibility for device group configurations.
For the three monitoring definitions that are monitoring the shared VPC in different accounts:
• If firewalls are separate per account: Assign different plugin notify groups for each
monitoring definition.
• If firewalls are shared across accounts: Use the same plugin notify group for all monitoring
definitions.
VM-Series Public Cloud Deployments 212 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on AWS
Use AWS Secrets Manager to Store VM-Series
Certificates
Where Can I Use This? What Do I Need?
• AWS AWS account
```
Amazon Machine Image (AMI) ID
```
```
VM-Series License (PAYG or BYOL)
```
VM-Series plugin
Panorama
Panorama plugin for AWS
You can integrate cloud-native key managers to store certificates. Private keys used for
certificates are not stored on a firewall’s hard drive, thereby eliminating security problems.
Administrators retain certificates and private keys in cloud storage. The firewall uses AWS Secrets
Manager to retrieve the certificates and private keys from cloud storage, and uses them for
features like decryption and IPSec.
Only VM-Series firewalls are supported to enable certificate retrieval via AWS Secrets
Manager. If you're using AWS Secrets Manager certificates, you can’t downgrade to an
earlier version of PAN-OS.
For outbound and inbound decryption, upload the certificates to the native key manager and
provide the required access permissions to the NGFW.
An NGFW on a public cloud can use AWS Secrets Manager for storing certificates. With such
cases, the required access management policies are configured, using PAN-OS or the CLI, for the
same instances.
For environments using autoscaling, an instance boots up in a state with the necessary
certificates retrieved and ready to decrypt traffic without additional manual configuration.
When a certificate is updated in the cloud, it must be reimported as a new certificate onto the
firewall. Assign IAM roles to an instance to enable the instance to retrieve certificates from the
AWS Secrets Manager store. The IAM role must have Get permission for Secrets from AWS
Secrets Manager.
All certificates are deleted when a master key changes and then refetched upon commit.
When the configuration is synchronized to the passive firewall under HA, the certificate
is automatically downloaded by the management daemon on the passive firewall. As a
result, the certificate itself isn’t synchronized.
STEP 1 | In the AWS Management Console, create an IAM role or select a role that was previously
created. The IAM role you use must have read and write privileges.
VM-Series Public Cloud Deployments 213 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on AWS
STEP 2 | Select the IAM Role policy in the Instances section of the AWS Console to view the Secrets
Manager.
STEP 3 | In the Permissions tab, select the Secrets Manager. You’ll use this screen to view public and
private keys.
STEP 4 | In the Secrets screen, select the name of the secrets file associated with the IAM role.
STEP 5 | In the Secret field, select Key/value to display the private and public key. Both keys should
be the same. Additionally, private or public keys must match the format AWS expects in
Secrets Manager. If the format does not match, key retrieval fails.
The Rotation configuration option must be Disabled. This feature isn’t supported.
STEP 6 | Return to your resource group and select the VM-Series firewall. Click Identity > User
Assigned and add the Managed Identity.
STEP 7 | Return to Secrets Manager and select Certificates. Import your certificate.
STEP 8 | Log in to the VM-Series firewall.
STEP 9 | Select Device > Certificate Management > Certificates > Import.
STEP 10 | Under Cloud, enter the certificate name and set the file format.
STEP 11 | Select Cloud, choose AWS from the Cloud Platform drop-down:
1. Enter the Certificate Name; copy this from the Certificate Name field in AWS Secrets
Manager > Secrets.
2. Select AWS for the Cloud Platform.
3. Enter the Cloud Secret Name; copy this from Secret name field in AWS Secrets
Manager > Secrets.
4. You can specify the Algorithm in the Certificate Information screen. Choose the
algorithm for your configuration, either RSA or Elliptical Curve DSA. By default, the
algorithm is set to use RSA. Configure the certificate to use either Forward Trust
Certificate, Forward Untrust Certificate, or Trusted Root CA. You can alternately select
all algorithms for the certificate.
5. Click OK.
6. Commit your changes.
VM-Series Public Cloud Deployments 214 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on AWS
STEP 12 | Verify that the certificate was added successfully:
1. Select Device > Certificate Management > Certificates.
2. Your new certificate should be listed.
Certificate details are not displayed in the Certificates
screen. To view this information in the CLI, use the command:
show shared certificate <cert-name>
Certificate details are not displayed in the Certificates
screen. To view this information in the CLI, use the command:
show shared certificate <cert-name>
You can confirm the configuration of certificate integration in Panorama. Use the Device
Certificate window to determine if the certificate is used. Keep in mind that because data isn’t
```
stored in the running configuration (the hard drive), all fields in the Device Certificates table
```
```
are empty, except for the Usage field (if configured) and the Cloud Secret Name.
```
VM-Series Public Cloud Deployments 215 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on AWS
Use Case: Secure the EC2 Instances in the AWS Cloud
Where Can I Use This? What Do I Need?
• AWS AWS account
```
Amazon Machine Image (AMI) ID
```
```
VM-Series License (PAYG or BYOL)
```
VM-Series plugin
Panorama
Panorama plugin for AWS
In this example, the VPC is deployed in the 10.0.0.0/16 network with two /24 subnets:
10.0.0.0/24 and 10.0.1.0/24. The VM-Series firewall will be launched in the 10.0.0.0/24 subnet
to which the internet gateway is attached. The 10.0.1.0/24 subnet is a private subnet that will
```
host the EC2 instances that need to be secured by the VM-Series firewall; any server on this
```
```
private subnet uses NAT for a routable IP address (which is an Elastic IP address) to access
```
the internet. Use the Planning Worksheet for the VM-Series in the AWS VPC to plan the
```
design within your VPC; recording the subnet ranges, network interfaces, and the associated IP
```
addresses for the EC2 instances, and security groups, will make the setup process easier and more
efficient.
VM-Series Public Cloud Deployments 216 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on AWS
The following image depicts the logical flow of traffic to/from the web server to the internet.
Traffic to/from the web server is sent to the data interface of the VM-Series firewall that is
attached to the private subnet. The firewall applies policy and processes incoming/outgoing traffic
from/to the internet gateway of the VPC. The image also shows the security groups to which the
data interfaces are attached.
VM-Series Public Cloud Deployments 217 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on AWS
```
STEP 1 | Create a new VPC with a public subnet (or select an existing VPC).
```
1. Log in to the AWS console and select the VPC Dashboard.
2. Verify that you’ve selected the correct geographic area (AWS region). The VPC will be
deployed in the currently selected region.
3. Select Start VPC Wizard, and select VPC with a Single Public Subnet.
In this example, the IP CIDR block for the VPC is 10.0.0.0/16, the VPC name is Cloud
DC, the public subnet is 10.0.0.0/24, and the subnet name is Cloud DC Public subnet.
You will create a private subnet after creating the VPC.
4. Click Create VPC.
STEP 2 | Create a private subnet.
Select Subnets, and click Create a Subnet. Fill in the information.
In this example, the Name tag for the subnet is Web/DB Server subnet, it is created in the
Cloud data center VPC and is assigned a CIDR block of 10.0.1.0/24.
VM-Series Public Cloud Deployments 218 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on AWS
STEP 3 | Create a new route table for each subnet.
Although a main route table is automatically created on the VPC, we recommend
creating new route tables instead of modifying the default route table.
To direct outbound traffic from each subnet, you will add routes to the route table associated
with each subnet, later in this workflow.
1. Select Route Tables > Create Route Table.
2. Add a Name, for example CloudDC-public-subnet-RT, select the VPC you created in
Step 1, and click Yes, Create.
3. Select the route table, click Subnet Associations and select the public subnet.
4. Select Create Route Table.
5. Add a Name, for example CloudDC-private-subnet-RT, select the VPC you created in
Step 1, and click Yes, Create.
6. Select the route table, click Subnet Associations and select the private subnet.
STEP 4 | Create Security Groups to restrict inbound/outbound internet access to the EC2 instances in
the VPC.
By default, AWS disallows communication between interfaces that do not belong to the same
security group.
Select Security Groups and click the Create Security Group button. In this example, we create
three security groups with the following rules for inbound access:
• CloudDC-Management that specifies the protocols and source IP addresses that can
connect to the management interface of the VM-Series firewall. At a minimum you need
VM-Series Public Cloud Deployments 219 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on AWS
SSH, and HTTPS. In this example, we enable SSH, ICMP, HTTP, and HTTPS on the network
interfaces that are attached to this security group.
```
The management interface (eth 0/0) of the VM-Series firewall will be assigned to CloudDC-
```
management-sg.
• Public-Server-CloudDC that specifies the source IP addresses that can connect over
HTTP, FTP, SSH within the VPC. This group allows traffic from the external network to the
firewall.
The dataplane interface eth1/1 of the VM-Series firewall will be assigned to Public-Server-
CloudDC.
• Private-Server-CloudDC that has very limited access. It only allows other EC2 instances on
the same subnet to communicate with each other, and with the VM-Series firewall.
The dataplane interface eth1/2 of the VM-Series firewall and the application in the private
subnet will be attached to this security group.
The following screenshot shows the security groups for this use case.
STEP 5 | Deploy the VM-Series firewall.
Only the primary network interface that will serve as the management interface will
be attached and configured for the firewall during the initial launch. The network
interfaces required for handling data traffic will be added in Step 6.
See Step 3 in Launch the VM-Series Firewall on AWS.
VM-Series Public Cloud Deployments 220 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on AWS
```
STEP 6 | Create and attach virtual network interfaces, referred to as Elastic Network Interfaces (ENIs),
```
to the VM-Series firewall. These ENIs are used for handling data traffic to/from the firewall.
1. On the EC2 Dashboard, select Network Interfaces, and click Create Network Interface.
2. Enter a descriptive name for the interface.
3. Select the subnet. Use the subnet ID to make sure that you have selected the correct
subnet. You can only attach an ENI to an instance in the same subnet.
4. Enter the Private IP address that you want to assign to the interface or select
Autoassign to automatically assign an IP address within the available IP addresses in the
selected subnet.
5. Select the Security group to control access to the network interface.
6. Click Yes, Create.
In this example, we create two interfaces with the following configuration:
```
• For Eth1/1 (VM-Series-Untrust)
```
• Subnet: 10.0.0.0/24
• Private IP:10.0.0.10
• Security group: Public-Server-CloudDC
```
• For Eth1/2 (VM-Series-Trust)
```
• Subnet: 10.0.1.0/24
• Private IP: 10.0.1.10
• Security group: Private-Server-CloudDC
7. To attach the ENI to the VM-Series firewall, select the interface you just created, and
click Attach.
8. Select the Instance ID of the VM-Series firewall, and click Attach.
9. Repeat steps 7 and 8 to attach the other network interface.
VM-Series Public Cloud Deployments 221 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on AWS
STEP 7 | Create an Elastic IP address and attach it to the firewall dataplane network interface that
requires direct internet access.
In this example, VM-Series_Untrust is assigned an EIP. The EIP associated with the interface is
the publicly accessible IP address for the web server in the private subnet.
1. Select Elastic IPs and click Allocate New Address.
2. Select EC2-VPC and click Yes, Allocate.
3. Select the newly allocated EIP and click Associate Address.
4. Select the Network Interface and the Private IP address associated with the interface
and click Yes, Associate.
In this example, the configuration is:
STEP 8 | Disable Source or Destination check on each network interface attached to the VM-Series
firewall. Disabling this attribute allows the interface to handle network traffic that is not
destined to its IP address.
1. Select the network interface in the Network Interfaces tab.
2. In the Action drop-down, select Change Source/Dest. Check.
3. Click Disabled and Save your changes.
4. Repeat steps 1-3 for additional network interfaces, firewall-1/2 in this example.
VM-Series Public Cloud Deployments 222 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on AWS
```
STEP 9 | In the route table associated with the public subnet (from step 3), add a default route to the
```
internet gateway for the VPC.
1. From the VPC Dashboard, select Route Tables and find the route table associated with
the public subnet.
2. Select the route table, select Routes and click Edit.
3. Add a route to forward packets from this subnet to the internet gateway. In this
example, 0.0.0.0.0 indicates that all traffic from/to this subnet will use the internet
gateway attached to the VPC.
STEP 10 | In the route table associated with the private subnet, add a default route to send traffic to
the VM-Series firewall.
Adding this route enables the forwarding of traffic from the EC2 instances in this private
subnet to the VM-Series firewall.
1. From the VPC Dashboard, select Route Tables and find the route table associated with
the private subnet.
2. Select the route table, select Routes and click Edit.
3. Add a route to forward packets from this subnet to the VM-Series firewall network
interface that resides on the same subnet. In this example, 0.0.0.0/0 indicates that all
```
traffic from/to this subnet will use eni-abf355f2 (ethernet 1/2, which is CloudDC-VM-
```
```
Series-Trust) on the VM-Series firewall.
```
For each web or database server deployed on an EC2 instance in the private
subnet, you must define a default route to the IP address of the VM-Series
firewall so that the firewall is the default gateway for the server.
Perform steps 11 through 16 on the VM-Series firewall.
VM-Series Public Cloud Deployments 223 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on AWS
STEP 11 | Configure a new administrative password for the firewall.
An SSH tool such as PuTTY is required to access the CLI on the firewall and change the
default administrative password. You cannot access the web interface until you SSH
and change the default password.
1. Use the public IP address you configured on the firewall, to SSH into the Command Line
```
Interface (CLI) of the VM-Series firewall.
```
You will need the private key that you used or created in Launch the VM-Series Firewall
on AWS, steps 3-12 to access the CLI.
2. Enter the following command to log in to the firewall:
ssh-i <private_key_name> admin@<public-ip_address>
3. Configure a new password, using the following command and follow the onscreen
```
prompts:
```
configure
set mgt-config users admin password
commit
4. Terminate the SSH session.
STEP 12 | Access the web interface of the VM-Series firewall.
Open a web browser and enter the EIP of the management interface. For example:
```
https://54.183.85.163
```
STEP 13 | Activate the licenses on the VM-Series firewall. This step is only required for the BYOL
```
license; the usage-based licenses are automatically activated.
```
See Activate the license.
VM-Series Public Cloud Deployments 224 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on AWS
STEP 14 | On the VM-Series firewall, configure the dataplane network interfaces on the firewall as
Layer 3 interfaces.
1. Select Network > Interfaces > Ethernet.
2. Click the link for ethernet 1/1 and configure as follows:
• Interface Type: Layer3
• Select the Config tab, assign the interface to the default router.
• On the Config tab, expand the Security Zone drop-down and select New Zone.
Define a new zone, for example untrust, and then click OK.
```
• Select IPv4, select DHCP Client; the private IP address that you assigned to the
```
network interface in the AWS management console will be acquired automatically.
• On the Advanced > Other Info tab, expand the Management Profile drop-down, and
select New Management Profile.
• Enter a Name for the profile, such as allow_ping, and select Ping from the Permitted
Services list, then click OK.
• To save the interface configuration, click OK.
3. Click the link for ethernet 1/2 and configure as follows:
• Interface Type: Layer3
• Select the Config tab, assign the interface to the default router.
• On the Config tab, expand the Security Zone drop-down and select New Zone.
Define a new zone, for example trust, and then click OK.
• Select IPv4, select DHCP Client.
• On the IPv4 tab, clear the Automatically create default route to default gateway
provided by server check box. For an interface that is attached to the private subnet
in the VPC, disabling this option ensures that traffic handled by this interface does not
flow directly to the IGW on the VPC.
• On the Advanced > Other Info, expand the Management Profile drop-down, and
select the allow_ping profile you created earlier.
• Click OK to save the interface configuration.
4. Click Commit to save the changes. Verify that the Link state for the interface is up . If
the link state is not up, reboot the firewall.
VM-Series Public Cloud Deployments 225 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on AWS
STEP 15 | On the VM-Series firewall, create Destination NAT and Source NAT rules to allow inbound/
outbound traffic to/from the applications deployed within the VPC.
1. Select Policies > NAT.
2. Create a Destination NAT rule that steers traffic from the firewall to the web server.
1. Click Add, and enter a name for the rule. For example, NAT2WebServer.
2. In the Original Packet tab, make the following selections:
```
• Source Zone: untrust (where the traffic originates)
```
```
• Destination Zone: untrust (the zone for the firewall dataplane interface with which
```
```
the EIP for the web server is associated.)
```
• Source Address: Any
• Destination Address: 10.0.0.10
• In the Translated Packet tab, select the Destination Address Translation check box
and set the Translated Address: to 10.0.1.62, which is the private IP address of the
web server.
3. Click OK.
3. Create a Source NAT rule to allow outbound traffic from the web server to the internet.
1. Click Add, and enter a name for the rule. For example, NAT2External.
2. In the Original Packet tab, make the following selections:
```
• Source Zone: trust (where the traffic originates)
```
```
• Destination Zone: untrust (the zone for the firewall dataplane interface with which
```
```
the EIP for the web server is associated.)
```
• Source Address: Any
• Destination Address: Any
3. In the Translated Packet tab, make the following selections in the Source Address
Translation section:
• Translation Type: Dynamic IP and Port
• Address Type: Translated Address
```
• Translated Address: 10.0.0.10 (the firewall dataplane interface in the untrust
```
```
zone.)
```
4. Click OK.
4. Click Commit to save the NAT policies.
VM-Series Public Cloud Deployments 226 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on AWS
STEP 16 | On the VM-Series firewall, create security policies to manage traffic.
Instead of entering a static IP address for the web server, use a dynamic address
group. Dynamic address groups allow you to create policy that automatically adapts
to changes so that you do not need to update the policy when you launch additional
web servers in the subnet. For details, see Use Case: Use Dynamic Address Groups
to Secure New EC2 Instances within the VPC.
1. Select Policies > Security.
In this example, we have four rules. A rule that allows management access to the firewall
traffic, a rule to allow inbound traffic to the web server, a third rule to allow internet
VM-Series Public Cloud Deployments 227 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on AWS
access to the web server, and in the last rule we modify a predefined intrazone-default
rule to log all traffic that is denied.
2. Create a rule to allow management access to the firewall.
1. Click Add and enter a Name for the rule. Verify that the Rule Type is universal.
2. In the Source tab, add untrust as the Source Zone.
3. In the Destination tab, add trust as the Destination Zone.
4. In the Applications tab, Add ping and ssh.
5. In the Actions tab, set the Action to Allow.
6. Click OK.
3. Create a rule to allow inbound traffic to the web server.
1. Click Add and enter a Name for the rule and verify that the Rule Type is universal.
2. In the Source tab, add untrust as the Source Zone.
3. In the Destination tab, add trust as the Destination Zone.
4. In the Applications tab, Add web-browsing.
5. In the Service/URL Category tab, verify that the service is set to application-default.
6. In the Actions tab, set the Action to Allow.
7. In the Profile Settings section of the Actions tab, select Profiles and then attach the
default profiles for antivirus, anti-spyware, and vulnerability protection.
8. Click OK.
4. Create a rule to allow internet access to the web server.
1. Click Add and enter a Name for the rule and verify that the Rule Type is universal.
2. In the Source tab, add trust as the Source Zone.
3. In the Source Address section of the Source tab, add 10.0.1.62, the IP address of the
web server.
4. In the Destination tab, add untrust as the Destination Zone.
5. In the Service/URL Category tab, verify that the service is set to application-default.
6. In the Actions tab, set the Action to Allow.
7. In the Profile Settings section of the Actions tab, select Profiles and then attach the
default profiles for antivirus, anti-spyware, and vulnerability protection.
8. Click OK.
5. Edit the interzone-default rule to log all traffic that is denied. This predefined interzone
rule is evaluated when no other rule is explicitly defined to match traffic across different
zones.
1. Select the interzone-default rule and click Override.
VM-Series Public Cloud Deployments 228 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on AWS
2. In the Actions tab, select Log at session end.
3. Click OK.
6. Review the complete set of security rules defined on the firewall.
7. Click Commit to save the policies.
STEP 17 | Verify that the VM-Series firewall is securing traffic.
1. Launch a web browser and enter the IP address for the web server.
2. Log in to the web interface of the VM-Series firewall and verify that you can see the
traffic logs for the sessions at Monitor > Logs > Traffic.
```
• Traffic inbound to the web server (arrives at EC2 instance in the AWS VPC):
```
```
• Traffic outbound from the web server (EC2 instance in the AWS VPC):
```
You have successfully deployed the VM-Series firewall as a cloud gateway!
VM-Series Public Cloud Deployments 229 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on AWS
Use Case: Use Dynamic Address Groups to Secure New
EC2 Instances within the VPC
Where Can I Use This? What Do I Need?
• AWS AWS account
```
Amazon Machine Image (AMI) ID
```
```
VM-Series License (PAYG or BYOL)
```
VM-Series plugin
Panorama
Panorama plugin for AWS
In a dynamic environment such as the AWS-VPC where you launch new EC2 instances on-
demand, the administrative overhead in managing security policy can be cumbersome. Using
Dynamic Address Groups in security policy allows for agility and prevents disruption in services or
gaps in protection.
In this example, you can use the VM Information Source on the firewall to monitor a VPC and use
Dynamic Address Groups in security policy to discover and secure EC2 instances. As you spin up
EC2 instances, the Dynamic Address Group collates the IP addresses of all instances that match
the criteria defined for group membership, and then security policy is applied for the group. The
security policy in this example allows internet access to all members of the group.
Instead of using VM Information Source on the firewall, you can opt to use Panorama as
the central point for communicating with your VPCs. Using the AWS plugin on Panorama,
you can retrieve the IP address-to-tag mapping and register the information on the
managed firewalls for which you configure notification. For more details on this option,
see Resource Monitoring on AWS.
This workflow in the following section assumes that you have created the AWS VPC and
deployed the VM-Series firewall and some applications on EC2 instances. For instructions on
setting up the VPC for the VM-Series, see Use Case: Secure the EC2 Instances in the AWS Cloud.
VM-Series Public Cloud Deployments 230 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on AWS
STEP 1 | Configure the firewall to monitor the VPC.
1. Select Device > VM Information Sources.
2. Click Add and enter the following information:
1. A Name to identify the VPC that you want to monitor. For example, VPC-CloudDC.
2. Set the Type to AWS VPC.
3. In Source, enter the URI for the VPC. The syntax is
ec2.<your_region>.amazonaws.com.
4. Add the credentials required for the firewall to digitally sign API calls made to the
AWS services. You need the following:
• Access Key ID: Enter the alphanumeric text string that uniquely identifies the user
who owns or is authorized to access the AWS account.
• Secret Access Key: Enter the password and confirm your entry.
5. (Optional) Modify the Update interval to a value between 5-600 seconds. By default,
the firewall polls every 5 seconds. The API calls are queued and retrieved within
every 60 seconds, so updates may take up to 60 seconds plus the configured polling
interval.
6. Enter the VPC ID that is displayed on the VPC Dashboard in the AWS management
console.
7. Click OK, and Commit the changes.
8. Verify that the connection Status displays as connected.
VM-Series Public Cloud Deployments 231 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on AWS
STEP 2 | Tag the EC2 instances in the VPC.
For a list of tags that the VM-Series firewall can monitor, see List of Attributes Monitored on
the AWS VPC.
A tag is a name-value pair. You can tag the EC2 instances either on the EC2 Dashboard on the
AWS management console or using the AWS API or AWS CLI.
In this example, we use the EC2 Dashboard to add the tag:
VM-Series Public Cloud Deployments 232 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on AWS
STEP 3 | Create a Dynamic Address Group on the firewall.
View the tutorial to see a large picture view of the feature.
1. Select Object > Address Groups.
2. Click Add and enter a Name and a Description for the address group.
3. Select Type as Dynamic.
4. Define the match criteria.
1. Click Add Match Criteria, and select the And operator.
2. Select the attributes to filter for or match against. In this example, we select the
ExternalAccessAllowed tag that you just created and the subnet ID for the private
subnet of the VPC.
5. Click OK.
6. Click Commit.
VM-Series Public Cloud Deployments 233 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on AWS
STEP 4 | Use the Dynamic Address Group in a security policy.
To create a rule to allow internet access to any web server that belongs to the Dynamic
Address Group called ExternalServerAccess.
1. Select Policies > Security.
2. Click Add and enter a Name for the rule and verify that the Rule Type is universal.
3. In the Source tab, add trust as the Source Zone.
4. In the Source Address section of the Source tab, Add the ExternalServerAccess group
you created.
5. In the Destination tab, add untrust as the Destination Zone.
6. In the Service/URL Category tab, verify that the service is set to application-default.
7. In the Actions tab, set the Action to Allow.
8. In the Profile Settings section of the Actions tab, select Profiles and then attach the
default profiles for antivirus, antispyware, and vulnerability protection.
9. Click OK.
10. Click Commit.
STEP 5 | Verify that members of the Dynamic Address Group are populated on the firewall.
Policy will be enforced for all IP addresses that belong to this address group, and are displayed
here.
1. Select Policies > Security, and select the rule.
2. Select the drop-down arrow next to the address group link, and select Inspect. You can
also verify that the match criteria are accurate.
3. Click the more link and verify that the list of registered IP addresses is displayed.
VM-Series Public Cloud Deployments 234 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on AWS
Use Case: VM-Series Firewalls as GlobalProtect
Gateways on AWS
Where Can I Use This? What Do I Need?
• AWS AWS account
```
Amazon Machine Image (AMI) ID
```
```
VM-Series License (PAYG or BYOL)
```
VM-Series plugin
Panorama
Panorama plugin for AWS
Securing mobile users from threats and risky applications is often a complex mix of procuring
and setting up the security and IT infrastructure, ensuring bandwidth and uptime requirements in
multiple locations around the globe while staying within your budget.
The VM-Series firewall on AWS melds the security and IT logistics required to consistently
and reliably protect devices used by mobile users in regions where you don’t have a presence.
By deploying the VM-Series firewall in the AWS cloud, you can quickly and easily deploy
GlobalProtect™ gateways in any region without the expense or IT logistics that are typically
required to set up this infrastructure using your own resources.
To minimize latency, select AWS regions that are closest to your users, deploy the VM-Series
firewalls on EC2 instances, and configure the firewalls as GlobalProtect gateways. With this
solution, the GlobalProtect gateways in the AWS cloud enforce security policy for internet traffic
so there is no need to backhaul that traffic to the corporate network. Additionally, for access
to resources on the corporate network, the VM-Series firewalls on AWS leverage the LSVPN
functionality to establish IPSec tunnels back to the firewall on the corporate network.
For ease of deployment and centralized management of this distributed infrastructure, use
Panorama to configure the GlobalProtect components used in this solution. Optionally, to ensure
that mobile devices, such as smartphones and tablets, are safe for use on your network, use a
Mobile Device Manager to configure and manage mobile devices.
VM-Series Public Cloud Deployments 235 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on AWS
Components of the GlobalProtect Infrastructure
Where Can I Use This? What Do I Need?
• AWS AWS account
```
Amazon Machine Image (AMI) ID
```
```
VM-Series License (PAYG or BYOL)
```
VM-Series plugin
Panorama
Panorama plugin for AWS
To block risky applications and protect mobile users from malware, you must set up the
GlobalProtect infrastructure, which includes the GlobalProtect portal, the GlobalProtect gateway,
and the GlobalProtect app. Additionally, for access to corporate resources, you must set up an
IPSec VPN connection between the VM-Series firewalls on AWS and the firewall in the corporate
```
headquarters using LSVPN (a hub and spoke VPN deployment).
```
• The GlobalProtect agent/app is installed on each end-user system that is allowed to access
corporate applications and resources. The agent first connects to the portal to obtain
information on the gateways and then establishes a secure VPN connection to the closest
GlobalProtect gateway. The VPN connection between the end-user system and the gateway
ensures data privacy.
• The GlobalProtect portal provides the management functions for the GlobalProtect
infrastructure. Every end-user system receives configuration information from the portal,
including information about available gateways as well as any client certificates that may be
```
required to connect to the GlobalProtect gateway(s). In this use case, the GlobalProtect portal
```
is a hardware-based firewall that is deployed in the corporate headquarters.
• The GlobalProtect gateway delivers mobile threat prevention and policy enforcement based on
applications, users, content, device, and device state. In this use case, the VM-Series firewalls
VM-Series Public Cloud Deployments 236 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on AWS
on AWS function as the GlobalProtect gateways. The GlobalProtect gateway scans each user
request for malware and other threats, and, if policy allows, sends the request to the internet
```
or to the corporate network over the IPSec tunnel (to the LSVPN gateway).
```
• For LSVPN, you must configure the GlobalProtect portal, GlobalProtect gateway for LSVPN
```
(hub), and the GlobalProtect Satellites (spokes).
```
In this use case, the hardware-based firewall in the corporate office is deployed as the
GlobalProtect portal and the LSVPN gateway. The VM-Series firewalls on AWS are configured
to function as GlobalProtect satellites. The GlobalProtect satellites and gateway are configured
to establish an IPSec tunnel that terminates on the gateway. When a mobile user requests an
application or resource that resides on the corporate network, the VM-Series firewall routes
the request over the IPSec tunnel.
Deploy GlobalProtect Gateways on AWS
Where Can I Use This? What Do I Need?
• AWS AWS account
```
Amazon Machine Image (AMI) ID
```
```
VM-Series License (PAYG or BYOL)
```
VM-Series plugin
Panorama
Panorama plugin for AWS
To secure mobile users, in addition to deploying and configuring the GlobalProtect gateways
on AWS, you need to set up the other components required for this integrated solution. The
following table includes the recommended workflow:
Deploy the VM-Series firewall on AWS.
See Deploy the VM-Series Firewall on AWS.
Configure the firewall at the corporate headquarters.
In this use case, the firewall is configured as the GlobalProtect portal and the LSVPN gateway.
• Configure the GlobalProtectportal.
• Configure the GlobalProtectportal for LSVPN.
• Configure the portal to authenticateLSVPN satellites.
VM-Series Public Cloud Deployments 237 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on AWS
Set up a template on Panorama for configuring the VM-Series firewalls on AWS as
GlobalProtect gateways and LSVPN satellites.
To easily manage this distributed deployment, use Panorama to configure the firewalls on
AWS.
```
• Create template(s) on Panorama.
```
Then use the following links to define the configuration in the templates.
• Configure the firewall as a GlobalProtect gateway.
• Prepare the satellite to join the LSVPN.
Create device groups on Panorama to define the network access policies and internet access
rules and apply them to the firewalls on AWS.
See Create device groups.
Apply the templates and the device groups to the VM-Series firewalls on AWS, and verify that
you have configured the firewalls properly.
Deploy the GlobalProtect client software.
Every end-user system requires the GlobalProtect agent or app to connect to the
GlobalProtect gateway.
See Deploy the GlobalProtectclient software.
VM-Series Public Cloud Deployments 238 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on AWS
Resource Monitoring on AWS
Where Can I Use This? What Do I Need?
• AWS AWS account
```
Amazon Machine Image (AMI) ID
```
```
VM-Series License (PAYG or BYOL)
```
VM-Series plugin
Panorama
Panorama plugin for AWS
As you deploy or terminate resources in the AWS public cloud, you can either use the Panorama
plugin for AWS or use the AWS resource information sources on the firewall to consistently
enforce security policy rules on these workloads. See the Compatibility Matrix for Panorama
plugin version information.
The Panorama plugin for AWS is built for scale and allows you to monitor up to 1000 AWS
VPCs on the AWS public cloud. With this plugin, you use Panorama as an anchor to poll your
```
AWS accounts for tags, and then distribute the metadata (IP address-to-tag mapping) to many
```
firewalls in a device group. Because Panorama communicates with your AWS accounts to retrieve
AWS resource information, you’re able to streamline the number of API calls made to the cloud
environment. When using Panorama and the AWS plugin, you can centralize the retrieval of
tags and Security policy management to ensure consistent policies for hybrid and cloud-native
architectures.
If you do not have Panorama or you have a simpler deployment and need to monitor 10 VPCs or
```
fewer, you can use the VM Information Source on the firewall (hardware or VM-Series firewall) to
```
monitor your AWS workloads. You can use the metadata, which the firewall retrieves, in Dynamic
Address Groups and reference them in Security policies to secure your VM workloads as they spin
up or down and IP addresses change frequently. See Use Case: Use Dynamic Address Groups to
Secure New EC2 Instances within the VPC.
As you deploy or terminate resources in the AWS public cloud, you need a way to synchronously
```
update Security policy on your Palo Alto Networks® firewall(s) so that you can secure these EC2
```
instances. To enable this capability from Panorama, you must install the AWS plugin on Panorama
and enable API communication between Panorama and your AWS VPCs. Panorama can then
```
collect a predefined set of attributes (or metadata elements) as tags for your AWS resources and
```
```
register the information to your Palo Alto Networks® firewall(s). When you reference these tags
```
in Dynamic Address Groups and match against them in Security policy rules, you can consistently
enforce policy across all assets deployed within your AWS accounts.
VM-Series Public Cloud Deployments 239 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on AWS
List of Attributes Monitored on the AWS VPC
Where Can I Use This? What Do I Need?
• AWS AWS account
```
Amazon Machine Image (AMI) ID
```
```
VM-Series License (PAYG or BYOL)
```
VM-Series plugin
Panorama
Panorama plugin for AWS
As you provision or modify virtual machines in your AWS VPCs, you have two ways of monitoring
these instances and retrieving the tags for use as match criteria in Dynamic Address Groups.
• VM Information Source—On a Palo Alto Networks Next-Generation Firewall, you can monitor
```
up to a total of 32 tags—14 predefined and 18 user-defined key-value pairs (tags).
```
• AWS plugin on Panorama—The Panorama plugin for AWS allows you to connect Panorama to
your AWS VPC on the public cloud and retrieve the IP address-to-tag mapping for your virtual
machines. Panorama then registers the VM information to the managed Palo Alto Networks®
```
firewall(s) that you have configured for notification. With the plugin, Panorama can retrieve a
```
total of 32 tags for each virtual machine, 11 predefined tags and up to 21 user-defined tags.
```
The maximum length of the tag-value (name and value included) must be 116
```
characters or less. If a tag is longer than 116 characters, Panorama does not retrieve
the tag and register it on the firewalls.
Attributes
Monitored on
the AWS-VPC
VM
Information
Source on the
Firewall
AWS Plugin on
Panorama
AMI ID ImageId.<ImageId string> Yes Yes
Architecture Architecture.<Architecture string> Yes No
Availability
Zone
AvailabilityZone.<string> Yes Yes
Guest OS GuestOS.<guest OS name> Yes No
IAM Instance
Profile
Iam-instance-
profile.<instanceProfileArn>
No Yes
Instance ID InstanceId.<InstanceId string> Yes No
VM-Series Public Cloud Deployments 240 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on AWS
Attributes
Monitored on
the AWS-VPC
VM
Information
Source on the
Firewall
AWS Plugin on
Panorama
Instance State InstanceState.<instance state> Yes No
Instance Type InstanceType.<instance type> Yes No
Key Name KeyName.<KeyName string> Yes Yes
Owner ID
The value for
this attribute is
fetched from
the ENI.
Account-number.<OwnerId> No Yes
Placement
Tenancy, Group
Name
Placement.Tenancy.<string>
Placement.GroupName.<string>
Yes Yes
Private DNS
Name
PrivateDnsName.<Private DNS Name> Yes No
Public DNS
Name
PublicDnsName.<Public DNS Name> Yes Yes
Subnet ID SubnetID.<subnetID string> Yes Yes
Security Group
ID
Sg-id.<sg-xxxx> No Yes
Security Group
Name
Sg-name.<SecurityGroupName> No Yes
VPC ID VpcId.<VpcId string> Yes Yes
```
Tag (key, value) aws-tag.<key>.<value> Yes;
```
Up to a
maximum
of 18 user-
defined
tags are
supported.
The user-
defined tags
are sorted
alphabetically,
```
Yes;
```
Up to a
maximum
of 21 user-
defined tags are
supported. The
user-defined
tags are sorted
alphabetically,
and the first
21 tags are
VM-Series Public Cloud Deployments 241 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on AWS
Attributes
Monitored on
the AWS-VPC
VM
Information
Source on the
Firewall
AWS Plugin on
Panorama
and the first
18 tags are
available for
use on the
firewalls.
available
for use on
Panorama and
the firewalls.
VM-Series Public Cloud Deployments 242 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on AWS
IAM Permissions Required for Monitoring the AWS VPC
Where Can I Use This? What Do I Need?
• AWS AWS account
```
Amazon Machine Image (AMI) ID
```
```
VM-Series License (PAYG or BYOL)
```
VM-Series plugin
Panorama
Panorama plugin for AWS
To enable VM Monitoring, the user’s AWS login credentials tied to the AWS Access Key and
Secret Access Key must have permissions for the attributes listed above. These privileges allow
the firewall to initiate API calls for monitoring the virtual machines in the AWS VPC.
The IAM policy associated with the user must either have global read-only access such as
AmazonEC2ReadOnlyAccess, or must include individual permissions for all monitored attributes.
The following IAM policy example lists the permissions for initiating the API actions for
monitoring the resources in the AWS VPC:
```
{ “Version”: “2012-10-17",
```
“Statement”: [
```
{
```
“Sid”: “VisualEditor0”,
“Effect”: “Allow”,
“Action”: [
“elasticloadbalancing:DescribeLoadBalancerAttributes”,
“elasticloadbalancing:DescribeLoadBalancers”,
“elasticloadbalancing:DescribeTags”,
“ec2:DescribeInstances”,
“ec2:DescribeNetworkInterfaces”,
“ec2:DescribeVpcs”,
“ec2:DescribeVpcEndpoints”,
“ec2:DescribeSubnets”
],
“Resource”: “*”
```
}
```
]
```
}
```
VM-Series Public Cloud Deployments 243 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on AWS
Set Up the AWS Plugin for VM Monitoring on Panorama
Where Can I Use This? What Do I Need?
• AWS AWS account
```
Amazon Machine Image (AMI) ID
```
```
VM-Series License (PAYG or BYOL)
```
VM-Series plugin
Panorama
Panorama plugin for AWS
To find all the virtual machine workloads that your organization has deployed in the AWS public
cloud, you need to install the AWS plugin on Panorama and configure Monitoring Definitions
that enable Panorama to authenticate to your AWS VPCs and retrieve VM information on the
workloads. Panorama retrieves the IP address of the VMs that are running—public IP address, and
primary and secondary private IP addresses—and the associated tags. For a list of the metadata
elements that Panorama supports, see List of Attributes Monitored on the AWS VPC.
After Panorama fetches the attributes, to push the virtual machine information from Panorama
```
to the firewalls, you must add the firewalls (hardware or VM-Series) as managed devices on
```
Panorama, and group the firewalls into one or more Device Groups. You can then specify which
device groups are part of the Notify Group, which is a configuration element in a Monitoring
Definition, that Panorama uses to register the IP address-to-tag mapping it retrieves from AWS.
Finally, to consistently enforce Security policies across the EC2 instances, you must set up
Dynamic Address Groups and reference them in policy rules that allow or deny traffic to the IP
addresses of the VMs. For streamlining your configuration and managing policies and objects
centrally from Panorama, you can define the Dynamic Address Groups and Security policy rules
on Panorama and push them to the firewalls instead of managing the Dynamic Address Groups
and Security policy rules locally on each firewall.
The AWS plugin version 3.0.1 or later is for monitoring EC2 instances for up to 1000
VPCs on the AWS public cloud, AWS GovCloud, and AWS China. However, because
Panorama can’t be deployed on AWS China, the IAM role does not support instance
```
profiles on AWS China; you must provide the AWS credentials.
```
While configuring the monitoring definition, ensure that you attach the parent device
group to the plugin notify-group and that all children DGs are unattached from the notify
group.
To ensure that the DAU propagates all IP tags from parent device group to children DGs
that are connected to the firewall, run the command debug dau settings device group
recursive yes on Panorama CLI.
VM-Series Public Cloud Deployments 244 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on AWS
Planning Checklist for VM Monitoring on AWS
For Panorama to interact with the AWS APIs and collect information on your EC2 instances,
you need to create an IAM role and assign the policies that grant the permissions required to
authenticate to AWS and access the EC2 instances within your VPC. You can add 100 IAM roles
to manage up to 1000 VPCs on Panorama.
Gather the VPC ID.
```
Tag your EC2 instances on AWS. You can tag (define a name-value pair) the EC2 instances
```
either on the EC2 Dashboard on the AWS management console or using the AWS API or AWS
CLI. See List of Attributes Monitored on the AWS VPC for the list of supported attributes.
Check for duplicate IP addresses across the VPCs for which you will enable monitoring. If you
have duplicate IP addresses across AWS VPCs, the metadata will be appended together or
swapped and this may cause unexpected results in policy enforcement.
Duplicate IP addresses are written to the plugin_aws_ret.log file that you can access
from the CLI on Panorama.
Review the requirements for Panorama and the managed firewalls:
• Minimum system requirements—Panorama virtual appliance or hardware-based Panorama
appliance.
Panorama Minimum Requirements
Memory CPUs Number of
Monitored VPCs
Number of Tags Registered
16GB 4 1-100
32 GB 8 100-500
System
Resources
64 GB 16 500-1000
Panorama 9.1 or later with AWS
```
plugin v 2.0 (or later) is tested
```
to retrieve 10,000 IP addresses
with 13 tags for each, or 5000 IP
addresses with 25 tags for each, and
successfully register them to the
firewalls included within a device
group. The tag length—includes name
and value—for each EC2 instance
is assumed to be 64 bytes per tag.
For example, the EC2 instance name
tag is aws.ec2.tag.Name.prod-web-
app-4523-lvss6j.
Panorama OS
version
10.0.5 or later
AWS plugin
version
3.0.1 or later
Licenses Active support license and a device management license on Panorama for
managing the firewalls.
VM-Series Public Cloud Deployments 245 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on AWS
Panorama Minimum Requirements
Palo Alto Networks Next-Generation Firewalls must also have a valid
support license.
Roles and
Permissions
to retrieve
metadata on the
EC2 instances
See IAM Roles and Permissions for Panorama
• You must add the firewalls as managed devices on Panorama and create Device Groups
so that you can configure Panorama to notify these groups with the VM information it
retrieves. Device groups can include VM-Series firewalls or virtual systems on the hardware
firewalls.
• If your Panorama appliances are in a high availability configuration, you must manually
install the same version of the AWS plugin on both Panorama peers. Additionally, if you're
using instance profiles, you must attach the same instance profile to both Panorama peers.
You configure the AWS plugin on the active Panorama peer only. On commit, the
configuration is synced to the passive Panorama peer. Only the active Panorama
peer polls the AWS accounts you have configured for VM Monitoring.
• Set up the credentials/permissions that Panorama requires to digitally sign API calls to the
AWS services.
You can choose whether you want to provide the long-term credentials—Access Key ID
and Secret Access Key—that enable access to the resources within each AWS account, or
set up an Assume Role on AWS to allow access to defined AWS resources within the same
AWS account or cross-accounts. With an Assume Role, you must set up a trust relationship
and define the permissions while creating the role itself. This is useful in a cross-account
deployment where the querying account does not have permissions to see or handle data
from the queried account. For the Panorama plugin to successfully authenticate to the VPC
and retrieve the tags, you must configure the Assume Role to use the AWS Security Token
```
Service (STS) API to any AWS service. And a user from the querying account must have
```
STS permissions to query the Assume Role and obtain the temporary security credentials
to access resources. If your Panorama is deployed on AWS, you can opt to use an instance
profile instead of providing the AWS credentials for the IAM role. The instance profile
includes the role information and associated credentials that Panorama needs to digitally
sign API calls to the AWS services. See IAM Roles and Permissions for Panorama for more
details.
IAM Roles and Permissions for Panorama
With the AWS plugin, you can use IAM roles or instance profiles to enable Panorama to
authenticate and retrieve metadata on the resources deployed within your AWS accounts.
• When your Panorama is not deployed on AWS, you have two options. You can either provide
the long-term IAM credentials for the AWS accounts you want to monitor, or set up an
Assume Role on AWS to allow access to defined AWS resources within the same AWS account
or cross-accounts. An Assume Role is recommended as the more secure option.
VM-Series Public Cloud Deployments 246 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on AWS
• When your Panorama is deployed on AWS, in addition to the two options listed above, you can
also add an instance profile that allows the IAM role to be passed to the EC2 instance. You can
use an instance profile where all your monitored resources and Panorama are hosted within
the same account, or an instance profile with Assume Role for cross account access where your
Panorama and monitored resources are deployed across different AWS accounts. If you use
the instance profile, you don’t enter your AWS credentials on Panorama.
Option 1: IAM role with long term credentials
Roles and
Permissions
Required
The AWS credentials associated with the AWS account that has the VPC/EC2
instances you want to monitor.
The JSON format for the minimum permissions associated with the IAM role
with long-term credentials is as follows:
```
{ “Version”: “2012-10-17",
```
“Statement”: [
```
{
```
“Sid”: “VisualEditor0”,
“Effect”: “Allow”,
“Action”: [
“elasticloadbalancing:DescribeLoadBalancerAttributes”,
“elasticloadbalancing:DescribeLoadBalancers”,
“elasticloadbalancing:DescribeTags”,
“ec2:DescribeInstances”,
“ec2:DescribeNetworkInterfaces”,
“ec2:DescribeVpcs”,
“ec2:DescribeVpcEndpoints”,
“ec2:DescribeSubnets”
],
“Resource”: “*”
```
}
```
]
```
}
```
Inputs on
Panorama
Enter the Access Key ID and Secret Access Key for the user in Panorama >
Plugins > AWS > Setup > IAM Role.
Option 2: IAM role with Assume Role
Roles and
Permissions
Required
While you can use this option to monitor VPCs within the same or cross account,
this option is recommended to enable cross account access by assuming a role
that allows you to access resources to which you may normally have access.
To assume a role from a different account, your AWS account must be trusted
by that role and defined as a trusted entity in its trust policy. In addition, a user
who wants to access a role in a different account must have a policy with secure
```
token service (STS) access that specifies the role ARN.
```
On Account 1 that you want to monitor:
VM-Series Public Cloud Deployments 247 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on AWS
• Create an IAM role with required permissions. For VM Monitoring you need
the following permissions.
```
{ “Version”: “2012-10-17",
```
“Statement”: [
```
{
```
“Sid”: “VisualEditor0”,
“Effect”: “Allow”,
“Action”: [
“elasticloadbalancing:DescribeLoadBalancerAttributes”,
“elasticloadbalancing:DescribeLoadBalancers”,
“elasticloadbalancing:DescribeTags”,
“ec2:DescribeInstances”,
“ec2:DescribeNetworkInterfaces”,
“ec2:DescribeVpcs”,
“ec2:DescribeVpcEndpoints”,
“ec2:DescribeSubnets”
],
“Resource”: “*”
```
}
```
]
```
}
```
• Copy the Role ARN.
• Create a user and add the Account ID for Account 2 as a trusted entity. This
allows Account 2 the permissions to use this role to access the resources
within your Account 1.
On Account 2 that requires access to account 1
• Attach the following policy with STS permissions and modify the Role ARN to
match what you created on Account 1.
```
{ "Version": "2012-10-17",
```
"Statement":
```
{
```
"Effect": “Allow",
"Action": "sts:AssumeRole",
"Resource":"arn:aws:iam::012347211234:role/
PAN-OS-assume-role"
```
}
```
```
}
```
Inputs on
Panorama
• Enter the Access Key ID and Secret Access Key for the user on Account 2 on
Panorama > Plugins > AWS > Setup > IAM Role.
• Enter the Role ARN for the AWS Account 1, which you want to monitor in
the Panorama > Plugins > AWS > Monitoring Definitions.
Option 3: Instance profile
VM-Series Public Cloud Deployments 248 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on AWS
Roles and
Permissions
Required
Only when Panorama is deployed as an EC2 instance on AWS
When you use the AWS Management console to create an IAM role,
the console automatically creates an instance profile with the same
name as the role. Because the role and the instance profile have the
```
same name, when you launch tour Panorama (EC2 instance) with an
```
IAM role, the instance profile of the same name is associated with it.
When Panorama and the resources you want to monitor are all in a single AWS
account.
Create an IAM role with AmazonEC2ReadOnlyAccess.
Inputs on
Panorama
Select Instance Profile as the option in Panorama > Plugins > AWS > Setup >
IAM Role.
Option 4: Instance profile with Assume Role
Roles and
Permissions
Required
Use instance profile with Assume role when Panorama and the resources you
want to monitor are deployed across AWS accounts.
For Panorama HA, make sure to attach the same instance profile to both
Panorama peers.
On Account 1, where your EC2 instances are deployed:
• Create an IAM role.
```
• To this role, add the AWS Account ID (Account 2) where your Panorama is
```
deployed as a trusted entity.
• Attach the JSON policies as detailed above for VM Monitoring.
• Copy the Role ARN. This role is required for Panorama to retrieve metadata
on your EC2 instances or EKS clusters.
On Account 2, where your Panorama is deployed:
```
• Create an IAM role and attach the JSON policy (with the STS policy and
```
```
resource ARN you got from Account 1).
```
• For each additional AWS account you want to monitor, copy the same STS
policy and modify the Role ARN.
Inputs on
Panorama
• Select Instance Profile as the option in Panorama > Plugins > AWS > Setup >
IAM Role
• Enter the Role ARN for the AWS account, which you want to monitor in the
Panorama > Plugins > AWS > Monitoring Definitions.
For example Account 1 in this example.
VM-Series Public Cloud Deployments 249 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on AWS
Install or Upgrade the AWS Plugin
To get started with monitoring your EC2 instances on AWS, refer to the Compatibility Matrix for
the Panorama Plugin for AWS and VM-Series plugin versions required to support VM monitoring.
```
To upgrade an earlier Panorama plugin for AWS version to a later version (for example, going
```
```
from version 1.0 to version 4.0), you must first upgrade to the Panorama and VM-Series plugin
```
```
versions required for the latest version (currently, 4.0), then install as directed below to perform
```
an upgrade.
```
After you install the latest AWS plugin (for example, v4.0) you can’t downgrade to an
```
```
earlier version (for example, v2.0).
```
If you have a Panorama HA configuration, repeat the installation or upgrade process on each
Panorama peer.
Install or uninstall plugins during a planned maintenance window.
```
If you currently have a Panorama plugin for any cloud platform installed, installing (or uninstalling)
```
an additional plugin requires a Panorama reboot so commit changes.
If you have a standalone Panorama or two Panorama appliances installed in an HA pair with
multiple plugins installed, plugins might not receive updated IP-tag information if one or more of
the plugins is not configured. This occurs because Panorama won’t forward IP-tag information to
unconfigured plugins. Additionally, this issue can occur if one or more of the Panorama plugins
```
isn’t in the Registered or Success state (positive state differs on each plugin). Ensure that your
```
plugins are in the positive state before continuing or executing the commands described below.
If you encounter this issue, there are two workarounds:
• Uninstall the unconfigured plugin or plugins. It's recommended that you do not install a plugin
that you do not plan to configure right away
• You can use the following commands to work around this issue. Execute the following
command for each unconfigured plugin on each Panorama instance to prevent Panorama from
waiting to send updates. If you do not, your firewalls may lose some IP-tag information.
request plugins dau plugin-name <plugin-name> unblock-device-push yes
You can cancel this command by executing:
request plugins dau plugin-name <plugin-name> unblock-device-push no
The commands described are not persistent across reboots and must be used again for any
subsequent reboots. For Panorama in HA pair, the commands must be executed on each
Panorama.
VM-Series Public Cloud Deployments 250 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on AWS
STEP 1 | Log in to the Panorama web interface, select Panorama > Plugins and click Check Now to
get the AWS plugin version that supports VM monitoring.
STEP 2 | Download and Install the plugin.
After you successfully install, Panorama refreshes and the AWS plugin displays on the
Panorama > Plugins tab.
On the Panorama Dashboard General Information widget you can verify the
Panorama plugin for AWS version that is installed.
```
STEP 3 | (Panorama in HA) Commit > Commit to Panorama.
```
If your Panorama is in HA, commit the changes to the Panorama configuration to ensure that
tags are registered to the Panorama peer on failover.
Configure the AWS Plugin for VM Monitoring
To begin monitoring the virtual machines in your AWS public cloud deployment, after you Install
the AWS Plugin you must create a Monitoring Definition. This definition specifies the IAM Role
that is authorized to access the EC2 instances within the AWS VPC you want to monitor and the
Notify Group that includes the firewalls to which Panorama should push all the IP-address-to-
tag mappings it retrieves. To enforce this policy, you must then create Dynamic Address Groups
and reference them in Security policy. The Dynamic Address Groups enable you to filter the tags
you want to match on, so that the firewall can get the public and private IP addresses registered
against each tag, and then allow or deny access to traffic to and from the workloads based on the
policy rules you define.
STEP 1 | Log in to the Panorama web interface.
VM-Series Public Cloud Deployments 251 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on AWS
STEP 2 | Set up the following objects for enabling VM Monitoring on AWS.
Verify that monitoring is enabled on the plugin. This setting must be enabled for Panorama
to communicate with the AWS public cloud for VM Monitoring.
The check box for Enable Monitoring is on Panorama > Plugins > AWS > Setup > General.
Add a notify group.
1. Select Panorama > Plugins > AWS > Setup > Notify Groups > Add.
2. Enter a Name to identify the group of firewalls to which Panorama pushes the VM
information it retrieves.
3. Select the Device Groups, which are a group of firewalls or virtual systems, to which
```
Panorama will push the VM information (IP address-to-tag mapping) it retrieves from
```
your AWS VPCs. The firewalls use the update to determine the most current list of
members that constitute Dynamic Address Groups referenced in policy. If you're using
VM-Series Public Cloud Deployments 252 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on AWS
the Panorama plugin for Azure and AWS, you can target the same firewall or virtual
system with tags from both environments.
Think through your Device Groups carefully.
• Because a Monitoring Definition can include only one notify group, make sure
to select all the relevant Device Groups within your notify group. If you want
to unregister the tags that Panorama has pushed to a firewall included in a
notify group, you must delete the Monitoring Definition.
• To register tags to all virtual systems on a firewall enabled for multiple virtual
systems, you must add each virtual system to a separate device group on
Panorama and assign the device groups to the notify group. If you assign all
the virtual systems to one device group, Panorama will register tags to only
one virtual system on the firewall.
4. Select the tags that you want to retrieve from the AWS VPCs.
```
You can Select All 32 Tags (the default) or pick the Custom Tags you want to retrieve for
```
your instances. With the Custom Tags option, you can Add the predefined tags and the
user-defined tags that you want to use as match criteria in the Security policy. If you are
monitoring a large number of EC2 instances, reducing the number of tags you retrieve
VM-Series Public Cloud Deployments 253 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on AWS
ensures more efficient use of the CPU and memory capacity on your Panorama. Refer to
Planning Checklist for VM Monitoring on AWS for some guidelines.
Add an IAM Role.
An IAM role is an entity that allows you to delegate access so that Panorama can make
```
service requests on your behalf to the AWS resources (virtual machines that are deployed
```
```
as EC2 instances).
```
1. Select Panorama > Plugins > AWS > Setup > IAM Role > Add.
VM-Series Public Cloud Deployments 254 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on AWS
2. Enter a Name and optionally a Description to identify the IAM role.
3. Select Account Type—Instance Profile or AWS Account Credentials. If your Panorama is
deployed on AWS, you can choose to either attach an instance profile with the correct
permissions to your Panorama or add the credentials associated with the IAM role on
VM-Series Public Cloud Deployments 255 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on AWS
Panorama. If your Panorama is not deployed on AWS, you must enter the credentials for
the IAM role locally on Panorama.
4. (For AWS Account Credentials only) Enter the Secret Access Key and re-enter it to
confirm, and click OK.
```
(For AWS GovCloud only), you must set the AWS region running the op-command. The
```
following is an example to set the AWS region using the op-command:
request plugins aws set-aws-region region <aws-govcloud-region>
STEP 3 | Create a Monitoring Definition for each VPC you want to monitor.
When you add a new Monitoring definition, it's enabled by default.
• Select Panorama > Plugins > AWS > Monitoring Definition > General, to Add a new
definition.
• Enter a Name and optionally a Description to identify the AWS VPC for which you use this
definition.
• Select the IAM Role, Add the VPC ID from the VPC Dashboard on the AWS management
console, and Notify Group.
• Select AWS Regions:
• All—Select all AWS regions.
• Select—Select specific AWS regions. Search AWS regions from the Member search bar
or Add new regions.
```
• (Optional) Enter the Role ARN, if you have set up role chaining and IAM roles with
```
temporary credentials that have permissions to use the AWS STS API to access AWS
VM-Series Public Cloud Deployments 256 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on AWS
resources with the same account or cross-account. The Role ARN must belong to the VPC
you want to monitor.
• Select a Notify Group, and Enable monitoring.
```
(For AWS GovCloud only), configure the AWS region under monitoring definition using the
```
CLI and commit the changes. Run the following command on CLI:
set plugins aws monitoring-definition <vm-mon-name> aws-regions
<aws-govcloud-region>
VM-Series Public Cloud Deployments 257 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on AWS
• On the VPC IDs tab, add the VPC IDs from the VPC dashboard on the AWS Management
Console.
VM-Series Public Cloud Deployments 258 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on AWS
STEP 4 | Commit the changes on Panorama.
Verify that the status for the Monitoring Definition displays as Success. If it fails, verify that
you entered the AWS VPC ID accurately and provided the correct keys and IDs for authorizing
access.
Click Validate to verify that Panorama can authenticate using the IAM role and keys
and to communicate with the AWS VPCs you’ve entered above.
VM-Series Public Cloud Deployments 259 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on AWS
STEP 5 | Verify that you can view the VM information on Panorama, and define the match criteria for
Dynamic Address Groups.
On HA failover, the newly active Panorama attempts to reconnect to the AWS cloud
and retrieve tags for all monitoring definitions. If Panorama is unable to reconnect
with even one of the monitoring definitions that you have configured and enabled,
Panorama generates a system log message
```
Unable to process accounts after HA switch-over; user-
```
intervention required.
If this happens, you must log into Panorama and verify the monitoring definitions to
fix invalid credentials or remove invalid accounts. Although Panorama is disconnected
from the AWS cloud, all tags that were retrieved for the monitoring definitions before
the failover are retained and the firewalls can continue to enforce policy on that list
of IP addresses. Panorama removes all tags associated with the accounts only when
you delete a monitoring definition. As a best practice, to monitor this issue, you can
configure action-oriented log forwarding to an HTTPS destination from Panorama so
that you can take action immediately.
VM-Series Public Cloud Deployments 260 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on AWS
STEP 6 | Know where to find the logs related to the AWS plugin on Panorama for troubleshooting.
• Use the CLI command less plugins-log to view a list of all available logs
less plugins-log plugin_aws_ret.log displays logs related to IP address and tag
retrieval.
less plugins-log plugin_aws_proc.log displays logs related to processing of the
registered IP address and tags.
less plugins-log plugin_aws.log displays logs related to the AWS plugin
configuration and daemons.
Use show plugins aws vm-mon-status for the status of the Monitoring Definitions.
admin@Panorama> show plugins aws vm-mon-status
Mon-Def Name VPC Status Last Updated Time
Error Msg
-----------------------------------------------------------------------------
MD-Ins-Prof-ARN vpc-07986b091 Success 2019-12-02T10:24:56.007000
MD-gov vpc-7ea1cf1a Success 2019-12-02T10:24:56.008000
MD-IAM-ARN vpc-025a83c123 Success 2019-12-02T10:24:56.012000
VM-Series Public Cloud Deployments 261 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on AWS
Performance Tuning for the VM-Series Firewall on AWS
Where Can I Use This? What Do I Need?
• AWS AWS account
```
Amazon Machine Image (AMI) ID
```
```
VM-Series License (PAYG or BYOL)
```
VM-Series plugin
Panorama
Panorama plugin for AWS
The following configurations affect performance:
PAN-OS versions 9.0.3 and earlier support AWS C5 and M5 instance types that have Elastic
Network Adapter support for SR-IOV mode by default. For more details, see Elastic Network
Adapter – High Performance Network Interface for Amazon EC2.
PAN-OS versions 9.0.4 and later provide DPDK support for C5 and M5 instance types by
default. When the firewall is in DPDK mode, it uses DPDK drivers. For a list of supported
drivers, see PacketMMAP and PDK Drivers on VM-Series Firewalls and the official DPDK
release notes.
```
To benefit from IETF RFC 8926 (Geneve) encapsulation and improved throughput, upgrade to
```
PAN-OS 10.0.2 or later and refer to VM-Series Integration with AWS Gateway Load Balancer.
Use the VM-Series CLI to view your DPDK settings or enable packed I/O.
View the DPDK Configuration on Your Firewall
STEP 1 | Log in to the VM-Series firewall CLI.
STEP 2 | View your DPDK configuration. If DPDK is enabled the output is as follows:
> show system setting dpdk-pkt-io on
Device current Packet IO mode: DPDK
Device DPDK Packet IO capable: yes
Device default Packet IO mode: DPDK
Enable DPDK Packed I/O
STEP 1 | Log in to the VM-Series firewall CLI
VM-Series Public Cloud Deployments 262 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on AWS
STEP 2 | Enable DPDK:
> set system setting dpdk-pkt-io on
STEP 3 | Reboot the device.
On the firewall, select Device > Setup > Operations and select Reboot Device.
VM-Series Public Cloud Deployments 263 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on AWS
VM-Series Public Cloud Deployments 264 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on Azure
Where Can I Use This? What Do I Need?
• Microsoft Azure
• Microsoft Azure Stack
• Azure® Marketplace
• Azure China Marketplace
• Azure Government Marketplace
```
VM-Series License (PAYG or BYOL)
```
VM-Series plugin
Panorama
Panorama plugin for Azure
The VM-Series firewall provides a complete set of security functionality to protect your virtual
machine workloads and data. The capabilities that the firewall enables are different from native
security features such as Security Groups, web application firewalls and native, port-based
firewall.
```
On Azure, the VM-Series is available in the bring your own license (BYOL) model or in the pay-
```
```
as-you-go (PAYG) hourly model. Microsoft Azure allows you to deploy the firewall to secure your
```
workloads within the virtual network in the cloud, so that you can deploy a public cloud solution
or you can extend the on-premises IT infrastructure to create a hybrid solution.
```
Deploy the VM-Series firewall on Azure in a virtual network (VNet) using the Resource Manager
```
deployment mode. You can deploy the VM-Series firewall on the standard Azure public cloud,
Azure China, and Azure Government—including DoD on Azure Government, which meets the
security requirements for DoD Impact Level 5 data and FedRAMP High standards.
The VM-Series firewall on the marketplace for the Azure public cloud, Azure Government, and
```
Azure DoD regions, supports both the Bring Your Own License (BYOL) model and the hourly Pay-
```
```
As-You-Go (PAYG) option (usage-based licensing). For licensing details, see VM-Series Firewall
```
License Types, and refer to the list of supported Azure regions in which you can deploy the VM-
Series firewall.
For Azure China, the VM-Series firewall is available in the BYOL option only. See Deploy the VM-
```
Series Firewall from the Azure China Marketplace (Solution Template) for the workflow.
```
Deploying the VM-Series firewall on Azure Stack, Microsoft's private cloud solution allows you to
use Azure services within your organization's data center. With Azure Stack, build a hybrid cloud
solution that unifies your public Azure deployment with your on-premises Azure Stack set up. To
download the VM-Series firewall BYOL offer from the Azure Marketplace and make it available to
your tenants on the Azure Stack, see Deploy the VM-Series Firewall on Azure Stack.
265
VM-Series Firewall on Azure
Deployments Supported on Azure
Use the VM-Series firewall on Azure to secure your network users in the following scenarios:
• Hybrid and VNet to VNet—The VM-Series firewall on Azure allows you to securely extend
your physical data center/private cloud into Azure using IPSec and ExpressRoute. To improve
your data center security, if you have segmented your network and deployed your workloads
in separate VNets, you can secure traffic flowing between VNets with an IPSec tunnel and
policies that allow application traffic.
• Inter-Subnet —The VM-Series firewall can front your servers in a VNet and protects against
lateral threats for inter-subnet traffic between applications in a multi-tier architecture.
• Gateway—The VM-Series firewall serves as the VNet gateway to protect Internet-facing
```
deployments in the Azure Virtual Network (VNet). The VM-Series firewall secures traffic
```
destined to the servers in the VNet and it also protects against lateral threats for inter-subnet
traffic between applications in a multi-tier architecture.
• GlobalProtect—Use the Azure infrastructure to quickly and easily deploy the VM-Series
firewall as GlobalProtect™ and extend your gateway security policy to remote users and
devices, regardless of location.
```
You can continue with Deploy the VM-Series Firewall from the Azure Marketplace (Solution
```
```
Template), Deploy the VM-Series Firewall on Azure Stack, Deploy the VM-Series Firewall on
```
Azure Stack HCI, or Orchestrate a VM-Series Firewall Deployment in Azure.
You can also learn about the VM-Series Firewall Templates on Azure that you can use to deploy
the firewall.
For information on bootstrapping, see Bootstrap the VM-Series Firewall on Azure and Bootstrap
the VM-Series Firewall on Azure Stack.
VM-Series Public Cloud Deployments 266 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on Azure
Azure Networking and VM-Series Firewall
Where Can I Use This? What Do I Need?
• Microsoft Azure
• Microsoft Azure Stack
• Azure® Marketplace
• Azure China Marketplace
• Azure Government Marketplace
```
VM-Series License (PAYG or BYOL)
```
VM-Series plugin
Panorama
Panorama plugin for Azure
The Azure VNet infrastructure does not require virtual machines to have a network interface in
```
each subnet. The architecture includes an internal route table (called system routes) that directly
```
connects all virtual machines within a VNet such that traffic is automatically forwarded to a virtual
machine in any subnet. For a destination IP address that isn't within the VNet, the traffic is sent
to the default internet gateway or to a VPN gateway, if configured. To route traffic through the
```
VM-Series firewall, you must create user-defined routes (UDRs) that specify the next hop for
```
traffic leaving a subnet. This route forces traffic destined to another subnet to go to the VM-
Series firewall instead of using the system routes to directly access the virtual machine in the
other subnet. For example, in a two-tiered application with a web tier and a database tier, you can
set up UDRs for directing traffic from the web subnet to the DB subnet through the VM-Series
firewall.
On Azure, UDRs are for traffic leaving a subnet only. You can't create user-defined routes
to specify how traffic comes into a subnet from the internet or to route traffic to virtual
machines within a subnet. UDRs allow you to direct outbound traffic to an interface on
the VM-Series firewall so that you can always ensure that the firewall secures traffic to
the internet also.
For documentation on Microsoft Azure, refer to https://azure.microsoft.com/en-us/
documentation/.
The solution templates for deploying the VM-Series firewall that’s available in the Azure
Marketplace, have three network interfaces. To Set up Active/Passive HA on Azure, you will need
to add an additional interface for the HA2 link. If you want to customize the template, use the
ARM templates that are available in the GitHub repository.
VM-Series Public Cloud Deployments 267 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on Azure
Azure Security Center Integration
Where Can I Use This? What Do I Need?
• Microsoft Azure
• Microsoft Azure Stack
• Azure® Marketplace
• Azure China Marketplace
• Azure Government Marketplace
```
VM-Series License (PAYG or BYOL)
```
VM-Series plugin
Panorama
Panorama plugin for Azure
Azure Sentinel
Microsoft has deprecated Azure Security Center support for partner security solutions and
replaced it with Azure Sentinel.
The VM-Series firewall is integrated with the Azure Security Center to provide a unified view for
monitoring and alerting on the security posture of your Azure workloads. On the Azure Security
Center, the VM-Series firewall is available as a partner security solution that protects your Azure
workloads from threats and mitigates any gaps in securing your business and intellectual property
in the public cloud. To enable this integration and display logs as security alerts directly on the
Azure Security Center dashboard, the VM-Series firewall on Azure includes a Log Forwarding
profile.
To get started, you need to enable the Azure Security Center on your Azure subscription. You
then have two ways in which you can enable this integration:
• Deploy the VM-Series firewall based on a recommendation on the Azure Security Center
dashboard.
The Azure Security Center dashboard recommends that you deploy a VM-Series firewall to
secure a workload that is exposed to the internet. You can only deploy the firewall in a new
resource group or an existing resource group that’s empty. This is because Azure currently
restricts you from deploying a multi-NIC appliance in an existing resource group. Therefore,
VM-Series Public Cloud Deployments 268 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on Azure
after you deploy the VVM-Series firewall you must manually configure it to be in the path of
traffic of the workload that you need to secure.
When you deploy the firewall from the Azure Security Center, the firewall is launched with
```
three network interfaces—management, external facing (untrust) and internal facing (trust)—
```
```
and a user-defined route (UDR) that sends all outbound traffic from the trust subnet to the
```
trust interface on the firewall so that internet-bound traffic is always inspected by the firewall.
The default configuration includes two example Security policy rules:
• outbound-default rule allows all traffic from the trust zone to the untrust zone on the
application default port.
• inbound-default rule allows all web-browsing traffic from the untrust zone to the trust zone,
after inspecting traffic with the default antivirus, antispyware, and Vulnerability Protection
Security Profiles.
The firewall also forwards all files that are intercepted with the inbound or outbound rule to
the WildFire public cloud for analysis. Both rules include a URL Filtering profile that blocks
all traffic to the URL categories copyright-infringement, dynamic DNS, extremism, malware,
phishing, and unknown. In addition to these Security Profiles, both Security policy rules are
enabled to log at session end and to forward threat and WildFire Submissions logs as security
alerts to the Azure Security Center dashboard.
To make practical use of this integration and Deploy a VM-Series Firewall Based on an Azure
Security Center Recommendation within the same resource group as the workloads you want
to secure, you can stage a workload with a public IP address that is exposed to the internet.
When the Azure Security Center detects the security risk, it triggers a recommendation
to deploy a next-generation firewall, and you can then deploy the VM-Series firewall in a
new resource group into which you can add your workloads later. You must then delete the
workload that you staged to trigger the recommendation.
• Select a VM-Series firewall that you have already deployed for securing your workloads.
If you have a Standard tier of Azure Security Center subscription, Azure Security Center
discovers and displays all existing VM-Series firewalls that you have deployed either from the
Azure Marketplace or using a customized deployment with the Azure CLI, PowerShell, or ARM
VM-Series Public Cloud Deployments 269 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on Azure
template. The firewalls within your Azure subscription are grouped under Security Solutions on
the Azure Security Center dashboard.
Microsoft Azure does not support the discovery of existing firewalls with the Free tier
subscription.
To Connect an Existing VM-Series Firewall From Azure Security Center, you must set up a
Linux virtual machine and configure syslog forwarding to forward firewall logs in the Common
Event Format as alerts to the Azure Security Center. The additional configuration enables a
single pane of glass view for monitoring all your Azure assets.
Forwarding a large volume of logs to the Azure Security Center, may result in an additional
subscription cost to you.
VM-Series Public Cloud Deployments 270 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on Azure
VM-Series Firewall Templates on Azure
Where Can I Use This? What Do I Need?
• Microsoft Azure
• Microsoft Azure Stack
• Azure® Marketplace
• Azure China Marketplace
• Azure Government Marketplace
```
VM-Series License (PAYG or BYOL)
```
VM-Series plugin
Panorama
Panorama plugin for Azure
You can deploy the VM-Series firewall on Azure using templates. Palo Alto Networks provides
two kinds of templates—Solution templates and ARM templates.
• Solution Templates in the Azure Marketplace—The solution templates that are available in the
Azure Marketplace allow you to deploy the VM-Series firewall using the Azure portal. You can
```
use an existing resource group and storage account (or create them new) to deploy the VM-
```
Series firewall with the following default settings for all regions except Azure China:
```
• VNet CIDR 10.8.0.0/16; you can customize the CIDR to a different private IP address range.
```
```
• Three subnets— 10.8.0.0/24 (management), 10.8.1.0/24 (untrust), 10.8.2.0/24 (trust)
```
• Three network interfaces, one in each subnet. If you customize the VNet CIDR, the subnet
ranges map to your changes.
To use the solution template, see Deploy the VM-Series Firewall from the Azure Marketplace
```
(Solution Template) for Azure China, see Deploy the VM-Series Firewall from the Azure China
```
```
Marketplace (Solution Template).
```
• ARM Templates in the GitHub Repository—In addition to Marketplace based deployments,
Palo Alto Networks provides Azure Resource Manager templates in the GitHub Repository to
simplify the process of deploying the VM-Series firewall on Azure.
• Use the ARM Template to Deploy the VM-Series Firewall—The basic ARM template
```
includes two JSON files (a template file and a Parameters File) to help you deploy and
```
provision all the resources within the VNet in a single, coordinated operation. These
templates are provided under an as-is, best effort, support policy.
If you want to use the Azure CLI to locate all the images available from Palo Alto
```
Networks, you need the following details to complete the command (show vm-
```
```
image list):
```
• Publisher: paloaltonetworks
• Offer: vmseries-flex
• SKU: byol, bundle1, bundle 2
• Version: 10.0.0, or latest
• Deploy the VM-Series and Azure Application Gateway Template to support a scale-out
security architecture that protects your internet-facing web applications using two VM-
VM-Series Public Cloud Deployments 271 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on Azure
```
Series firewalls between a pair of (external and internal) Azure load balancers VM-Series and
```
the Azure Application Gateway. This template is currently not available for Azure China.
• Use the ARM template to deploy the VM-Series firewall in to an existing Resource Group,
for example when you want to Set up Active/Passive HA on Azure.
In addition to the ARM templates covered under the Palo Alto Networks official support policy,
Palo Alto Networks provides Community supported templates in the Palo Alto Networks GitHub
repository, that allows you to explore the solutions available to jumpstart your journey in to cloud
automation and scale on Azure.
VM-Series Public Cloud Deployments 272 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on Azure
Minimum System Requirements for the VM-Series on
Azure
Where Can I Use This? What Do I Need?
• Microsoft Azure
• Microsoft Azure Stack
• Azure® Marketplace
• Azure China Marketplace
• Azure Government Marketplace
```
VM-Series License (PAYG or BYOL)
```
VM-Series plugin
Panorama
Panorama plugin for Azure
Azure Sentinel
ARM template
```
You must deploy the VM-Series firewall in the Azure Resource Manager (ARM) mode only; the
```
```
classic mode (Service Management based deployments) isn't supported. The VM-Series firewall on
```
Azure must meet the following requirements:
• Azure Linux VMs of the following types—supported instance types.
```
These types include support for Accelerated Networking (SR-IOV).
```
• For memory, disk and CPU cores required to deploy the VM-Series firewall, see VM-Series
System Requirements.
You can add additional disk space of 40GB to 8TB for logging purposes. The VM-Series firewall
```
uses Azure managed disks where available; it does not utilize the temporary disk that Azure
```
provides with some instance types.
```
• Up to eight network interfaces (NICs). A primary interface is required for management access
```
and up to seven interfaces for data traffic.
On Azure, because a virtual machine does not require a network interface in each subnet, you
```
can set up the VM-Series firewall with three network interfaces (one for management traffic
```
```
and two for dataplane traffic). To create zone-based policy rules on the firewall, in addition to
```
the management interface, you need at least two dataplane interfaces so that you can assign
one dataplane interface to the trust zone, and the other dataplane interface to the untrust
zone. For an HA deployment, you will need another interface for the HA2 link between the HA
peers.
Because the Azure VNet is a Layer 3 network, the VM-Series firewall on Azure supports Layer
3 interfaces only.
To ensure high availability, you can Set up Active/Passive HA on Azure in a traditional
configuration with session synchronization, or use a scale-out architecture using cloud-native
load balancers such as the Azure Application Gateway or Azure Load Balancer to distribute traffic
across a set of healthy instances of the firewall. For details, see Deploy the VM-Series and Azure
Application Gateway Template.
VM-Series Public Cloud Deployments 273 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on Azure
VM-Series on Azure Service Principal Permissions
Where Can I Use This? What Do I Need?
• Microsoft Azure
• Microsoft Azure Stack
• Azure® Marketplace
• Azure China Marketplace
• Azure Government Marketplace
```
VM-Series License (PAYG or BYOL)
```
VM-Series plugin
Panorama
Panorama plugin for Azure
For Panorama to interact with the Azure APIs and collect information on your workloads,
you need to create an Azure Active Directory application and a Service Principal that has the
permissions required to authenticate with Azure AD and access the resources within your
subscription.
To create the Active Directory application and Service Principal, follow the instructions in How to:
Use the portal to create an Azure AD application and service principal that can access resources.
During the application generation process, there is a step to "Assign application to role" and assign
an IAM role of "reader" to the application.
If you don't have the necessary permissions to create and register the AD application, ask your
Azure AD or subscription administrator to create a Service Principal.
After the application has been registered, record these values so you can enter them in the
Panorama plugin for Azure at a later time:
• Application ID
```
• Secret Key (record it when you make the secret key; the secret key isn't visible once you
```
```
navigate away from the page).
```
• Tenant ID
Permissions
The following table lists the minimum built-in roles required and the granular permissions if you
would like to customize the role.
To support Permissions
Azure High Availability See Set up Active/Passive HA on Azure.
Azure Application
Insights
Enable Azure Application
Insights on the VM-
Series Firewall
“Microsoft.Authorization/*/read”,
“Microsoft.Network/networkInterfaces/*”,
“Microsoft.Network/networkSecurityGroups/*”,
“Microsoft.Network/virtualNetworks/*”,
VM-Series Public Cloud Deployments 274 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on Azure
To support Permissions
“Microsoft.Compute/virtualMachines/read”
Azure Monitoring
Set Up the Azure Plugin
for Monitoring on
Panorama
Requires a minimum Role of Reader for Service Principal.
Alternatively, you can add the following custom permissions:
“Microsoft.Compute/virtualMachines/read”,
“Microsoft.Network/networkInterfaces/read”,
“Microsoft.Network/virtualNetworks/read”,
“Microsoft.Network/virtualNetworks/subnets/
read”,
“Microsoft.Network/applicationGateways/read”,
“Microsoft.Network/locations/serviceTags/read”,
"Microsoft.Network/loadBalancers/read",
"Microsoft.Network/publicIPAddresses/read",
"Microsoft.Resources/subscriptions/
resourcegroups/read"
“Microsoft.Resources/subscriptions/
resourcegroups/*”,
“Microsoft.Resources/deployments/write”,
“Microsoft.Resources/deployments/
operationStatuses/read”,
“Microsoft.Resources/deployments/read”,
“Microsoft.Resources/deployments/delete”
"Microsoft.Network/publicIPPrefixes/write",
"Microsoft.Network/publicIPPrefixes/read",
"Microsoft.Network/publicIPPrefixes/delete",
"Microsoft.Network/publicIPAddresses/write",
"Microsoft.Network/publicIPAddresses/read",
"Microsoft.Network/publicIPAddresses/delete",
"Microsoft.Network/publicIPAddresses/join/
action",
Panorama Orchestrated
Deployments
Create a Custom Role
and Associate It with an
Active Directory
"Microsoft.Network/natGateways/write",
"Microsoft.Network/natGateways/read",
"Microsoft.Network/natGateways/delete",
VM-Series Public Cloud Deployments 275 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on Azure
To support Permissions
"Microsoft.Network/natGateways/join/action",
"Microsoft.Network/virtualNetworks/read",
"Microsoft.Network/virtualNetworks/write",
"Microsoft.Network/virtualNetworks/delete",
"Microsoft.Network/virtualNetworks/subnets/
write",
"Microsoft.Network/virtualNetworks/subnets/
read",
"Microsoft.Network/virtualNetworks/subnets/
delete",
"Microsoft.Network/virtualNetworks/subnets/join/
action",
"Microsoft.Network/virtualNetworks/
virtualNetworkPeerings/read",
"Microsoft.Network/networkSecurityGroups/write",
"Microsoft.Network/networkSecurityGroups/read",
"Microsoft.Network/networkSecurityGroups/
delete",
"Microsoft.Network/networkSecurityGroups/join/
action",
"Microsoft.Network/loadBalancers/write",
"Microsoft.Network/loadBalancers/read",
"Microsoft.Network/loadBalancers/delete",
"Microsoft.Network/loadBalancers/probes/join/
action",
"Microsoft.Network/loadBalancers/
backendAddressPools/join/action",
"Microsoft.Network/loadBalancers/
frontendIPConfigurations/read",
"Microsoft.Network/locations/serviceTags/read",
"Microsoft.Network/applicationGateways/read",
"Microsoft.Network/networkInterfaces/read",
VM-Series Public Cloud Deployments 276 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on Azure
To support Permissions
"Microsoft.Compute/virtualMachineScaleSets/
write",
"Microsoft.Compute/virtualMachineScaleSets/
read",
"Microsoft.Compute/virtualMachineScaleSets/
delete",
"Microsoft.Compute/virtualMachineScaleSets/
virtualMachines/read",
"Microsoft.Compute/virtualMachines/read",
"Microsoft.Compute/images/read",
"Microsoft.insights/components/write",
"Microsoft.insights/components/read",
"Microsoft.insights/components/delete",
"Microsoft.insights/autoscalesettings/write"
VM-Series Public Cloud Deployments 277 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on Azure
Deploy the VM-Series Firewall from the Azure
```
Marketplace (Solution Template)
```
Where Can I Use This? What Do I Need?
• Microsoft Azure
• Microsoft Azure Stack
• Azure® Marketplace
• Azure Government Marketplace
```
VM-Series License (PAYG or BYOL)
```
VM-Series plugin
Panorama
Panorama plugin for Azure
ARM template
The following instructions describe how to deploy the solution template for the VM-Series
firewall that’s available in the Azure® Marketplace and the Azure Government Marketplace.
```
To use the customizable Azure Resource Manager (ARM) templates available in the GitHub
```
repository, see Use the ARM Template to Deploy the VM-Series Firewall.
STEP 1 | Set up an Azure account.
1. If you don't have one already, create a Microsoft® account.
2. Log in to the Azure portal (https://portal.azure.com or https://
```
portal.azure.us) using your Microsoft account credentials.
```
If you are using a trial subscription, you may need to open a support request
```
(Help + Support > New Support Request) to increase the quota of allocated VM
```
cores.
VM-Series Public Cloud Deployments 278 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on Azure
STEP 2 | Find the VM-Series solution template in the Azure Marketplace.
1. Select Marketplace > Virtual Machines.
2. Search for Palo Alto Networks® and a list of offerings for the VM-Series firewall will
```
display. For the differences in the BYOL (bring your own license) and PAYG (pay as you
```
```
go) models, see VM-Series Firewall Licenses for Public Clouds.
```
3. Select an offering to Create a new VM-Series firewall.
VM-Series Public Cloud Deployments 279 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on Azure
STEP 3 | Deploy the firewall.
1. Configure basic settings for the firewall.
1. Select your Azure Subscription.
2. Create a new resource group or select an existing resource group that’s empty. The
resource group will hold all the resources associated with the VM-Series firewall for
this deployment.
Azure has removed the option to select an existing resource group for
Marketplace solutions that enable multiple network interface controllers
```
(NICs). To deploy the firewall into an existing resource group, use the ARM
```
template in the GitHub Repository or use your own custom ARM template.
3. Select the Azure Region in which you are deploying the firewall.
4. Enter a Username for the firewall administrator.
5. Select the Authentication type—Password or SSH Public Key.
Enable SSH key authentication if you plan to use the firewall in FIPS-CC
operational mode. Although you can deploy the VM-Series firewall using
a username and password, you will be unable to authenticate using the
username and password after changing the operational mode to FIPS-CC.
After resetting to FIPS-CC mode, you must use the SSH key tologinn and can
then configure a username and password that you can use for subsequently
logging in to the firewall web interface. For details on creating the SSH key,
refer to the Azure documentation.
6. Enter a Password (up to 31 characters) or copy and paste an SSH public key for
securing administrative access to the firewall.
2. Configure networking.
```
A new Azure Virtual Network (VNet) is automatically preconfigured.
```
1. Configure the subnets for the network interfaces.
If you use the default subnets, you must review the configuration. If you use an
existing VNet, you must have set up three subnets: one each for the management,
trust, and untrust interfaces. If you create a new VNet, verify or change the prefixes
VM-Series Public Cloud Deployments 280 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on Azure
for each subnet. The default subnets are 10.8.0.0/24 for the management subnet,
10.8.1.0/24 for the untrust subnet, and 10.8.2.0/24 for the trust subnet.
2. Enter the source IP address or IP range (include the CIDR block) that can access the
VNet. Network Security Group: inbound source IP allows you to restrict inbound
access to the Azure VNet.
Restrict access to the firewall. Make sure to supply a CIDR block that
corresponds to your dedicated management IP addresses or network. Don't
make the allowed source network range larger than necessary and never
configure the allowed source as 0.0.0.0/0. Verify your IP address before you
configure it on the template to make sure that you don't lock yourself out.
3. Define management access to the firewall.
1. Use the default variable ((new) fwMgmtPublicIP)) to assign a Public IP address to the
```
management interface (eth0) of the firewall.
```
Accelerated Networking is supported on management interface on Azure
VMs in PAN-OS 10.2.8, 10.2.10, 10.2.11, 11.1, 11.2 and 12.1.
2. Enter a prefix to access the firewall using a DNS name. Combine the prefix you enter
with the suffix displayed on screen to access the web interface of the firewall. For
```
example: <yourname><your-region>.cloudapp.azure.com
```
3. Select the latest VM-Series Version.
4. Enter a display name to identify the VM-Series firewall within the resource group.
VM-Series Public Cloud Deployments 281 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on Azure
4. Add the information to configure the firewall at launch. See Bootstrap the VM-Series
Firewall on Azure.
1. Select yes to Enable Bootstrap.
2. Enter the Storage Account Name that holds the bootstrap package.
3. Enter the Storage Account Access Key. This firewall needs this access key to
authenticate to the storage account and access the files stored within.
4. Add the File share name to which you have uploaded the files required for
bootstrapping the firewall. The storage account must be in the same region in
VM-Series Public Cloud Deployments 282 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on Azure
whichyou'ree deploying the firewall and it must have the correct folder structure for
bootstrapping.
5. Select the Azure virtual machine tier and size to meet your needs. Use the Change
size link to view supported instance types, and to review the Minimum System
Requirements for the VM-Series on Azure.
5. Review the summary, and OK. Then accept the terms of use and privacy policy, and
Create to launch the firewall.
6. Verify that you have successfully deployed the VM-Series firewall.
1. Select Dashboard > Resource Groups and select the resource group.
2. Select your resource group and see the Overview for detailed status on which
resources are deployed successfully.
STEP 4 | Attach a public IP address for the untrust interface of the VM-Series firewall. When you
create a new public IP address, you get one from the block of IP addresses that Microsoft
VM-Series Public Cloud Deployments 283 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on Azure
owns, so you can’t choose a specific one. The maximum number of public IP addresses you
can assign to an interface is based on your Azure subscription.
1. On the Azure portal, select the network interface for which you want to add a public IP
```
address (such as the eth1 interface).
```
2. Select IP Configurations > Add and, for Public IP address, select Enabled. Create a new
public IP address or select one that you have available.
3. Verify that you can view the secondary IP address associated with the interface.
When you attach a secondary IP address to a network interface, the VM-Series firewall
does not automatically acquire the private IP address assigned to the interface. You
will need to manually configure the private IP address using the VM-Series firewall web
interface. See Configure the dataplane network interfaces as Layer 3 interfaces on
the firewall.
STEP 5 | Log in to the web interface of the firewall.
1. On the Azure portal, in All Resources, select the VM-Series firewall and view the full
DNS name for the firewall.
1. Using a secure (HTTPS) connection from your web browser, log in to the DNS name for
the firewall.
2. Enter the username and password that you defined in the parameters file. You will see a
certificate warning but that is OK—continue to the webpage.
VM-Series Public Cloud Deployments 284 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on Azure
STEP 6 | Activate the license on the VM-Series firewall.
For the BYOL version
1. Create a Support Account.
2. Register the VM-Series Firewall (with auth code).
3. On the firewall web interface, select Device > Licenses and select Activate feature using
authentication code.
4. Enter the capacity authentication code (auth-code) that you registered on
the Customer Support Portal. The firewall will connect to the update server
```
(updates.paloaltonetworks.com), and download the license and reboot
```
automatically.
5. Log back in to the web interface and confirm the following on the Dashboard:
• A valid serial number displays in Serial#.
If the term Unknown displays, it means the firewall isn't licensed. To view traffic logs
on the firewall, you must install a valid capacity license.
• The VM Mode displays as Microsoft Azure.
For the PAYG version
1. Create a Support Account.
2. Register the Usage-Based Model of the VM-Series Firewall for Public Clouds (no auth
```
code).
```
STEP 7 | Configure the dataplane network interfaces as Layer 3 interfaces on the firewall.
If you are hosting multiple websites or services with different IP addresses and SSL certificates
on a single server, you might need to configure more than one IP address on the VM-Series
firewall interfaces.
1. Select Network > Interfaces > Ethernet.
2. Click ethernet 1/1 and configure as follows:
```
• Set Interface Type to Layer3 (default).
```
• On the Config tab, assign the interface to the default router.
• Also on the Config tab, expand the Security Zone drop-down and select New Zone.
Define a new zone called UnTrust, and then click OK.
• On the IPv4 tab, select DHCP Client if you plan to assign only one IP address on the
interface—the firewall will automatically acquire the private IP address assigned in
the ARM template. If you plan to assign more than one IP address, select Static and
VM-Series Public Cloud Deployments 285 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on Azure
manually enter the primary and secondary IP addresses assigned to the interface on
the Azure portal.
```
• Disable (clear) the Automatically create default route to default gateway provided
```
by server to ensure that traffic handled by this interface does not flow directly to the
default gateway in the VNet.
3. Click ethernet 1/2 and configure as follows:
```
• Set Interface Type to Layer3 (default).
```
• Set Security Zone to Trust.
• Set IP address DHCP Client or Static.
```
• Disable (clear) the Automatically create default route to default gateway provided
```
by serverto ensure that traffic handled by this interface does not flow directly to the
default gateway in the VNet.
4. Commit your changes and verify that the link state for the interfaces is up.
5. Add a static route on the virtual router of the VM-Series firewall for any networks that
the firewall needs to route.
For example, to add a default route to the destination subnets for the servers that the
firewall secures:
• Select Network > Virtual Router > default >
• Select Static Routes > IPv4, and add the next hop IP address for the destination
```
servers. You can set x.x.x.1 as the next hop IP address for all traffic (destined to
```
```
0.0.0.0/0 from interface ethernet1/1).
```
STEP 8 | Configure the firewall for your specific deployment.
• Gateway—Deploy a third-party load balancer in front of the UnTrust zone.
• Hybrid and Inter-VNet—Deploy an Azure VPN Gateway or a NAT virtual machine in front
the UnTrust zone.
• Inter-Subnet—On the VM-Series firewall, add an intrazone Security policy rule to allow
traffic based on the subnets attached to the Trust interface.
• GlobalProtect™—Deploy a NAT virtual machine in front of the UnTrust zone.
STEP 9 | Direct traffic to the VM-Series firewall.
1. To ensure that the VM-Series firewall secures all traffic within the Azure resource group,
configure static routes on the firewall.
2. Configure user-defined routes to direct all traffic through the interfaces on the VM-
Series firewall. Refer to the Azure documentation on UDRs for details.
The user-defined routes on the internal subnets must send all traffic through the Trust
interface. The user-defined routes on the UnTrust side direct all traffic from the internet
through the UnTrust interface on the VM-Series firewall. The traffic from the internet
may be coming from an Azure Application Gateway or Azure Load Balancer, or through
the Azure VPN Gateway in the case of a hybrid deployment that connects your on-
premise network with the Azure cloud.
VM-Series Public Cloud Deployments 286 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on Azure
STEP 10 | To publish PAN-OS® metrics to Azure Application Insights, see Enable Azure Application
Insights on the VM-Series Firewall.
VM-Series Public Cloud Deployments 287 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on Azure
Simplified Onboarding of VM-Series Firewall on Azure
The simplified onboarding flow streamlines the deployment and initial configuration of VM-Series
firewalls in Azure. This flow deploys production-ready out-of-the-box architecture and firewall
configuration for users who may be new to VM-Series on Azure.
```
The firewall configuration includes essentials like interfaces (ethernet1/1 and ethernet1/2), zones
```
```
(untrust and trust), virtual Routers (untrust-vr and trust-vr), static routes, outbound NAT policies,
```
```
and security policies (defaults to allow health probe traffic).
```
Prerequisites
For simplified onboarding of VM-Series firewall on Azure, ensure to use the following PAN-OS
versions and license types:
Supported PAN-OS Version
• PAN-OS version 10.2.14 or above
PAN-OS version 11.1.8 or above
• PAN-OS version 11.2.5 or above
Supported License Types
```
• BYOL (Bring your own license)
```
```
• PAYG (Pay-as-you-go)
```
Simplified Onboarding for VM Series Solution templates on Azure Marketplace
Azure Marketplace Solution Templates support both Single Firewall and load balancer based
reference architectures.
The following are the steps for a simplified onboarding of multiple VM-Series firewalls with load
balancers.
VM-Series Public Cloud Deployments 288 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on Azure
1. Navigate to Azure Marketplace.
1. Log in to the Azure portal.
2. In the Azure portal dashboard, click the search bar at the top.
3. Search for VM-Series Next-Generation Firewall and select the listing titled VM-Series
Next-Generation Firewall by Palo Alto Networks.
VM-Series Public Cloud Deployments 289 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on Azure
VM-Series Public Cloud Deployments 290 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on Azure
4. In the Plan drop down menu, select High Resiliency with Load Balancers.
5. Click Create on the marketplace overview page.
2. Basic configuration.
Configure basic settings for the firewall.
1. Select your Azure Subscription.
2. Create a new resource group or select an existing resource group that is empty. The
resource group will hold all the resources associated with the VM-Series firewall for this
deployment.
3. Azure has removed the option to select an existing resource group for Marketplace
```
solutions that enable multiple network interface controllers (NICs). To deploy the firewall
```
into an existing resource group, use the ARM template in the GitHub Repository or use your
own custom ARM template.
4. Select the Azure Region in which you are deploying the firewall.
5. Enter a Username for the firewall administrator.
6. Select the Authentication type—Password or SSH Public Key.
7. Enter a Password (up to 31 characters) or copy and paste an SSH public key for securing
administrative access to the firewall.
8. Confirm the password.
9. Select the License Type.
10.Enter the Deployment Tag that you specified while creating the resource group.
11.Click Next.
VM-Series Public Cloud Deployments 291 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on Azure
3. Configure networking.
You can see that the Virtual Network, management subnet, public subnet, private
subnet, and Network Security group IP addresses are already populated.
1. Select the Deployment architecture.
VM-Series Public Cloud Deployments 292 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on Azure
VM-Series Public Cloud Deployments 293 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on Azure
VM-Series with high resiliency load balancers support four different deployment
```
architectures: Common firewall set with LB, Dedicated inbound firewall set with Public
```
LB, Dedicated outbound and east-west firewall set with ILB, and Dedicated inbound and
outbound firewalls sets with public LB and ILB. Select one of these for your deployment
architecture. For more information, see Deploy the VM-Series Firewall from the Azure
```
Marketplace (Solution Template).
```
2. Click Next.
VM-Series Public Cloud Deployments 294 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on Azure
4. VM-Series Configuration.
1. Select the VM-Series Version.
2. Select the Default configuration - outbound and E/W bootstrap option to boot the firewalls
with default pre-configurations needed for outbound traffic inspection.
VM-Series Public Cloud Deployments 295 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on Azure
VM-Series Public Cloud Deployments 296 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on Azure
3. Select the Availability Option
4. Click Next.
5. Review the summary, and OK. Then accept the terms of use and privacy policy, and click
Create to launch the firewall.
5. Optional
Validate Firewall Configuration
1. Log in to the VM-Series firewall web interface. For more information, see Launch the
firewall web interface.
2. Go to the Network tab.
3. Click interfaces and verify if the interfaces are correctly assigned:
• Ethernet1/1 should be in the Untrust zone.
• Ethernet1/2 should be in the Trust zone.
4. Verify Routing. In the Virtual Router section, ensure static routes for outbound and east-
west traffic are present.
5. Verify Security Policies.
Navigate to the Policies tab and confirm default rules are present:
• Intra-zone traffic is allowed.
• Inter-zone traffic is denied.
Verify the presence of a NAT policy for outbound internet traffic.
VM-Series Public Cloud Deployments 297 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on Azure
6. Peer Application VNet with the trust Vnet
1. Navigate to the Azure portal and open the FirewallVNet resource.
2. Go to the Peerings section.
VM-Series Public Cloud Deployments 298 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on Azure
VM-Series Public Cloud Deployments 299 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on Azure
3. Click Add.
4. Enter a name.
5. Select the application VNet whose traffic you wish to inspect
6. Click Add to create the peering.
You can repeat the above process to peer the FirewallVNet with AppVNet2.
VM-Series Public Cloud Deployments 300 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on Azure
7. Configure Route Tables for each application subnet.
VM-Series Public Cloud Deployments 301 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on Azure
VM-Series Public Cloud Deployments 302 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on Azure
1. Create Route tables for each application subnet:
• Go to Route Tables in the Azure portal and click Create.
```
• Enter the Region and Name the table (e.g., AppVM1RouteTable) and associate it with the
```
subnet of AppVNet1.
• Repeat the process for AppVNet2.
2. Add Routes:
You must add two routes to each table:
Route 1- Outbound Traffic:
• Enter the Destination IP address.
• Enter the Next Hop type.
• Enter the Next Hop IP Address. This should be the frontend IP of the firewall’s load
balancer.
• Click Add.
Route 2 - East-West Traffic:
• Enter the Destination IP address. This is the subnet of the other application VNet.
• Enter the Next Hop type.
• Enter the Next Hop IP Address. This should be the frontend IP of the firewall’s load
balancer.
Click Add.
You must add two routes to each table:
Route 1- Outbound Traffic:
• Enter the Destination IP address.
• Enter the Next Hop type.
• Enter the Next Hop IP Address. This should be the frontend IP of the firewall’s load
balancer.
• Click Add.
Route 2 - East-West Traffic:
• Enter the Destination IP address. This is the subnet of the other application VNet.
• Enter the Next Hop type.
• Enter the Next Hop IP Address. This should be the frontend IP of the firewall’s load
balancer.
• Click Add.
VM-Series Public Cloud Deployments 303 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on Azure
Deploy the VM-Series Firewall from the Azure China
```
Marketplace (Solution Template)
```
Where Can I Use This? What Do I Need?
• Microsoft Azure
• Microsoft Azure Stack
• Azure China Marketplace
```
VM-Series License (PAYG or BYOL)
```
VM-Series plugin
Panorama
Panorama plugin for Azure
ARM template
The following instructions show you how to deploy the solution template for the VM-Series
firewall that’s available in the Azure China Marketplace. The Azure China Marketplace supports
only the BYOL model of the VM-Series firewall. You can deploy the firewall in an existing
resource group that’s empty or into a new resource group. The default VNet in the template
is 10.0.0.0/16, and it deploys a VM-Series firewall that has three network interfaces, one
management, and two dataplane interfaces as shown below. To use the customizable ARM
templates available in the GitHub repository, see Use the ARM Template to Deploy the VM-Series
Firewall.
STEP 1 | Set up an Azure account.
1. Create a Microsoft account.
2. Log in to the Azure portal (https://portal.azure.com) using your Microsoft
account credentials.
```
If you're using a trial subscription, you may need to open a support request (Help
```
- Support > New Support Request) to increase the quota of allocated VM cores.
VM-Series Public Cloud Deployments 304 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on Azure
STEP 2 | Find the VM-Series solution template in the Azure Marketplace.
1. Search for Palo Alto Networks on the Azure China marketplace (https://
```
market.azure.cn). The offering for the different PAN-OS versions of the VM-Series
```
firewalls displays.
2. Select an offering and click Immediate deployment of.
STEP 3 | Deploy the firewall.
1. Select your Azure Subscription.
2. Select a resource group for holding all the resources associated with the VM-Series
firewall in this deployment.
You can deploy the VM-Series firewall into a new resource group, or an
existing Resource Group that’s empty. To deploy the firewall into an existing
resource group that has other resources, use the ARM template in the GitHub
Repository or your own custom ARM template. Ensure that the existing
resources match the parameter values you provide in the ARM template.
1. If you create a new resource group, enter a name for the resource group and select
the Azure China region where you want to deploy the firewall.
2. If you select an existing resource group, select the Azure China region for this
resource group, and select complete deployment.
3. Configure basic settings for the firewall.
1. Enter the storage account name for an existing account or create a new one.
2. Enter the name for the blob storage container to which the firewall vhd mage will be
copied and saved.
3. Enter a DNS name for accessing the Public IP address on the management
```
interface (eth0) of the firewall. To access the web interface of the firewall,
```
you must combine the prefix you enter with the suffix, for example
<yourDNSname><china_region>.cloudapp.azure.com.
4. Enter a Username for the firewall administrator.
5. Enter a Password for securing administrative access to the firewall.
6. Select the Azure virtual machine tier and size to meet your needs. See Minimum
System Requirements for the VM-Series on Azure.
7. Enter a VmName, which is a display name to identify the VM-Series firewall within
the resource group.
8. Use a PublicIPAddressName to label the firewall management interface within the
resource group. Microsoft Azure binds the DNS name that you defined with this
VM-Series Public Cloud Deployments 305 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on Azure
name so that you can access the management interface on the firewall from the
public internet.
9. Enter a VirtualNetworkName to identify your VNet. The default IP Address Prefix for
the VNet is 10.0.0.0/16. You can change this to meet your IP addressing needs.
10.Configure the subnets for the network interfaces. If you use an existing VNet, you
must have defined three subnets, one each for the management, trust, and untrust
interfaces. If you create a new VNet, verify or change the prefixes for each subnet.
The default subnets are 10.0.1.0/24, 10.0.2.0/24, and 10.0.3.0/24. You can allocate
these subnets to the management, trust, and untrust interfaces as you would like.
4. Review the summary, accept the terms of use and privacy policy, and click Immediate
deployment to deploy the firewall. The deployment may take 20 minutes and you can
use the link on the page to verify progress.
5. Verify that you have successfully deployed the VM-Series firewall.
1. Log in to the Azure China portal (https://portal.azure.cn) using your Microsoft
account credentials.
2. Select Dashboard > Resource Groups, select the resource group.
3. Select All Settings > Deployments > Deployment History for detailed status.
VM-Series Public Cloud Deployments 306 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on Azure
STEP 4 | Attach a public IP address for the untrust interface of the VM-Series firewall. This allows
you to access the interface from the public internet and is useful for any internet-facing
application or service.
1. On the Azure portal, select the network interface for which you want to add a public IP
address. For example the eth1 interface.
2. Select IP Configurations > Add and for Public IP address, select Enabled. Create a new
public IP address or select one that you have available.
3. Verify that you can view the secondary IP address associated with the interface.
When you attach a secondary IP address to a network interface, the VM-Series firewall
does not automatically acquire the private IP address assigned to the interface. You
will need to manually configure the private IP address using the VM-Series firewall web
interface. See Configure the dataplane network interfaces as Layer 3 interfaces on
the firewall.
```
Each interface on the VM-Series firewall on Azure can have one dynamic (default) or static
```
```
private IP address, and multiple public IP addresses (static or dynamic) associated with it.
```
The maximum number of public IP addresses you can assign to an interface is based on your
Azure subscription. When you create a new public IP address you get one from the block of IP
addresses Microsoft owns, so you can’t choose a specific one.
STEP 5 | Log in to the web interface of the firewall.
1. On the Azure portal, in All Resources, select the VM-Series firewall and view the full
DNS name for the firewall.
2. Using a secure connection (https) from your web browser, log in to the DNS name for
the firewall.
3. Enter the username/password you defined earlier. You will see a certificate warning;
that’s okay. Continue to the web page.
VM-Series Public Cloud Deployments 307 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on Azure
STEP 6 | Activate the license on the VM-Series firewall.
1. Create a Support Account.
2. Register the VM-Series Firewall (with auth code).
3. On the firewall web interface, select Device > Licenses and select Activate feature using
authentication code.
4. Enter the capacity auth-code that you registered on the support portal. The firewall will
```
connect to the update server (updates.paloaltonetworks.com), and download the license
```
and reboot automatically.
5. Log back in to the web interface and confirm the following on the Dashboard:
• A valid serial number displays in Serial#.
If the term Unknown displays, it means the device isn't licensed. To view traffic logs
on the firewall, you must install a valid capacity license.
• The VM Mode displays as Microsoft Azure.
STEP 7 | Configure the dataplane network interfaces as Layer 3 interfaces on the firewall.
If you're hosting multiple websites or services with different IP addresses and SSL certificates
on a single server, you might need to configure more than one IP address on the VM-Series
firewall interfaces.
1. Select Network > Interfaces > Ethernet.
2. Click the link for ethernet 1/1 and configure as follows:
```
• Interface Type: Layer3 (default).
```
• On the Config tab, assign the interface to the default router.
• On the Config tab, expand the Security Zone drop-down and select New Zone.
Define a new zone called UnTrust, and then click OK.
• On the IPv4 tab, select DHCP Client if you plan to assign only one IP address on the
interface. The private IP address assigned in the ARM template will be automatically
acquired. If you plan to assign more than one IP address select Static and manually
enter the primary and secondary IP addresses assigned to the interface on the Azure
portal.
• Clear the Automatically create default route to default gateway provided by server
check box. Disabling this option ensures that traffic handled by this interface does not
flow directly to the default gateway in the VNet.
3. Click the link for ethernet 1/2 and configure as follows:
```
• Set Interface Type to Layer3 (default).
```
• Security Zone: Trust
• IP address: Select DHCP Client or Static.
• Clear the Automatically create default route to default gateway provided by server
check box. Disabling this option ensures that traffic handled by this interface does not
flow directly to the default gateway in the VNet.
4. Click Commit. Verify that the link state for the interfaces is up.
VM-Series Public Cloud Deployments 308 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on Azure
STEP 8 | Configure the firewall for your specific deployment.
• Gateway—Deploy a 3rd party load balancer in front of the UnTrust zone.
• Hybrid and Inter-VNet—Deploy an Azure VPN Gateway or a NAT virtual machine in front
the UnTrust zone.
• Inter-Subnet—On the VM-Series firewall, add an intra-zone security policy rule to allow
traffic based on the subnets attached to the Trust interface.
• GlobalProtect—Deploy a NAT virtual machine in front of the UnTrust zone.
STEP 9 | Direct traffic to the VM-Series firewall.
1. To ensure that the VM-Series firewall secures all traffic within the Azure resource group,
configure static routes on the firewall.
2. Configure UDRs to direct all traffic through the interfaces on the VM-Series firewall.
Refer to the Azure documentation on UDRs for details.
The UDRs on the internal subnets must send all traffic through the Trust interface.
The UDRs on the UnTrust side direct all traffic from the internet through the UnTrust
interface on the VM-Series firewall. The traffic from the internet may be coming from an
Azure Application Gateway or Azure Load Balancer, or through the Azure VPN Gateway
in case of a hybrid deployment that connects your on-premises network with the Azure
cloud.
VM-Series Public Cloud Deployments 309 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on Azure
Panorama Orchestrated Deployments in Azure
Where Can I Use This? What Do I Need?
• Microsoft Azure
• Microsoft Azure Stack
• Azure® Marketplace
• Azure China Marketplace
• Azure Government Marketplace
```
VM-Series License (PAYG or BYOL)
```
VM-Series plugin
Panorama
Panorama plugin for Azure
The Panorama plugin for Azure centrally deploys, configures, and monitors your security posture
in Azure cloud. It orchestrates VM-Series deployments in your Azure network so that you can
enable security policies for managed firewalls. The plugin links to your Azure ARM deployment
and Azure Monitor pages, providing visibility into the deployment status, usage, and performance
of your VM-Series firewalls.
In Azure, the plugin orchestrates the deployment of Azure resources such as load balancers,
subnets, and NAT gateways as well as VM-Series firewall autoscaling sets. In Panorama the plugin
automatically configures Panorama device groups, template stacks, and NAT policies. It reads the
tags from your Azure resources, then centrally enables tag-based policies on a group of firewalls.
The Panorama plugin can orchestrate deployments in one or more regions in your Azure
environment. A deployment can consist of a hub stack or an inbound stack or both, depending on
the traffic that needs to be secured for your deployment:
• A hub firewall stack protects outbound traffic and east-west traffic between your application
workloads.
• An Inbound firewall stack secures traffic to and from your public facing applications.
You can configure the number of firewalls in each stack. You have the option to configure a static
amount of firewalls in your deployment or a range for the VMSS to use for scaling. Both stacks in
the deployment create a VMSS of VM-Series firewalls and they can each scale up to as many as
25 firewalls.
Hub Stack
```
A deployment uses a hub stack and leverages the Azure Internal Standard Load Balancer (with
```
```
HA ports) to scale and load balance across a set of firewalls. You can then use the Standard Load
```
```
balancer’s private IP address (2, “Hub/Egress Private IP” in the following figure) to route traffic
```
to the firewalls for inspection and threat prevention. The hub stack secures your applications’
outbound and east-west traffic.
VM-Series Public Cloud Deployments 310 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on Azure
To protect your outbound traffic and east-west traffic, add route rules in your application VNETs
to redirect traffic to the hub stack for inspection.
Inbound Stack
An Inbound firewall stack scales independently and adds visibility and security to your
applications’ Inbound traffic.
Each inbound stack can secure up to 10 applications.
To protect your inbound HTTP traffic, add UDRs in the Application Gateway’s subnet route tables
```
to route all traffic to the Inbound stack (3, Ingress Private IP in the following figure). To protect
```
the non-HTTP inbound traffic, use the Panorama plugin to create frontend entries for your
```
application endpoints (4, Ingress Public IP frontends in the following figure). To enable inspection,
```
the Panorama plugin automatically creates load balancer rules on the Azure Public Standard Load
Balancer and NAT rules on the firewalls.
If you only have HTTP/HTTPS inbound traffic you can leave out the Inbound stack and protect
that traffic with just the hub stack.
VM-Series Public Cloud Deployments 311 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on Azure
See Prepare for an Orchestrated Deployment and Orchestrate a VM-Series Firewall Deployment
in Azure.
Prepare for an Orchestrated Deployment
Where Can I Use This? What Do I Need?
• Microsoft Azure
• Microsoft Azure Stack
• Azure® Marketplace
• Azure China Marketplace
• Azure Government Marketplace
```
VM-Series License (PAYG or BYOL)
```
VM-Series plugin
Panorama
Panorama plugin for Azure
Complete the following tasks before you orchestrate a VM-Series firewall on Azure.
Configuration Prerequisites
Complete the following basic tasks on Panorama and Azure.
VM-Series Public Cloud Deployments 312 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on Azure
• Azure
• Create a service principal to enable the plugin to make API calls.
• Plan a CIDR block dedicated to VM-Series firewall Transit VNet. The plugin manages this
CIDR block and uses it to deploy the initial firewall VNet and perform as future upgrades to
new template stacks.
The minimum CIDR range is /22.
• Panorama
• Ensure that you have a valid license API key configured on Panorama. This allows the plugin
to manage to delicense on scale-in auto scaling events. See Install a License Deactivation
API Key.
• Install the latest version of the VM-Series plugin on Panorama to allow Application Insight
configuration to be added to the template stack.
• Qualified Azure Regions
Panorama orchestrated deployments are supported in all regions that support the VM-Series
```
firewall. The following regions have been qualified; if you deploy in an unlisted region and you
```
encounter an issue, contact support.
• West US
• West US 2
• North Central US
• East US
• East US 2
• West Europe
• Germany West Central
• UAE North
• West India
• Australia Southeast
While planning your deployment, please note that if you're currently running a Panorama plugin
for Azure version 2.x, upgrading to the current version isn't allowed. Along with this, once the
current version is installed, downgrading to a version 2.x plugin isn't allowed. See the Panorama
plugin for Azure in the Compatibility Matrix.
Orchestration Permissions
There is a sample JSON file with permissions for the template Deployer role. In the
AssignableScopes section, include all relevant subscriptions that must be queried, including
the subscription into which the deployment is deployed and EVERY subscription containing an
application VNET that is peered to the VM-Series firewall VNet where protected resources exist.
```
{
```
"Name": "Template Deployment",
"IsCustom": true,
"Description": "Manage template deployments.",
"Actions": [
VM-Series Public Cloud Deployments 313 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on Azure
"Microsoft.Resources/subscriptions/resourcegroups/*",
"Microsoft.Resources/deployments/write",
"Microsoft.Resources/deployments/operationStatuses/read",
"Microsoft.Resources/deployments/read",
"Microsoft.Resources/deployments/delete",
"Microsoft.Network/publicIPPrefixes/write",
"Microsoft.Network/publicIPPrefixes/read",
"Microsoft.Network/publicIPPrefixes/delete",
"Microsoft.Network/publicIPAddresses/write",
"Microsoft.Network/publicIPAddresses/read",
"Microsoft.Network/publicIPAddresses/delete",
"Microsoft.Network/publicIPAddresses/join/action",
"Microsoft.Network/natGateways/write",
"Microsoft.Network/natGateways/read",
"Microsoft.Network/natGateways/delete",
"Microsoft.Network/natGateways/join/action",
"Microsoft.Network/virtualNetworks/read",
"Microsoft.Network/virtualNetworks/write",
"Microsoft.Network/virtualNetworks/delete",
"Microsoft.Network/virtualNetworks/subnets/write",
"Microsoft.Network/virtualNetworks/subnets/read",
"Microsoft.Network/virtualNetworks/subnets/delete",
"Microsoft.Network/virtualNetworks/subnets/join/action",
"Microsoft.Network/virtualNetworks/virtualNetworkPeerings/
read",
"Microsoft.Network/networkSecurityGroups/write",
"Microsoft.Network/networkSecurityGroups/read",
"Microsoft.Network/networkSecurityGroups/delete",
"Microsoft.Network/networkSecurityGroups/join/action",
"Microsoft.Network/loadBalancers/write",
"Microsoft.Network/loadBalancers/read",
"Microsoft.Network/loadBalancers/delete",
"Microsoft.Network/loadBalancers/probes/join/action",
"Microsoft.Network/loadBalancers/backendAddressPools/join/
action",
"Microsoft.Network/loadBalancers/frontendIPConfigurations/
read",
"Microsoft.Network/locations/serviceTags/read",
"Microsoft.Network/applicationGateways/read",
"Microsoft.Network/networkInterfaces/read",
"Microsoft.Compute/virtualMachineScaleSets/write",
"Microsoft.Compute/virtualMachineScaleSets/read",
"Microsoft.Compute/virtualMachineScaleSets/delete",
"Microsoft.Compute/virtualMachineScaleSets/virtualMachines/
read",
"Microsoft.Compute/virtualMachines/read",
"Microsoft.Compute/images/read",
"Microsoft.insights/components/write",
"Microsoft.insights/components/read",
"Microsoft.insights/components/delete",
"Microsoft.insights/autoscalesettings/write"
]
"NotActions": [
],
"AssignableScopes": [
```
"/subscriptions/{deployment-subscription}",
```
VM-Series Public Cloud Deployments 314 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on Azure
```
"/subscriptions/{app1-subscription}",
```
```
"/subscriptions/{app2-subscription}",
```
.
.
.
]
```
}
```
Create a Custom Role and Associate It with an Active Directory
STEP 1 | To create an Active Directory in Azure, Navigate to Azure Active Directory and click on App
Registrations on the left. Create a custom role using the permissions the plugin requires.
An example JSON is included below.
1. Click add and provide a name. Select the role created from the above JSON file, leave
"Assign access to" as Active Directory user, and then select the Active Directory created
in the first step and click Save.
2. Select the type.
Don't modify anything under Redirect URI.
STEP 2 | Create a custom role with the permissions the plugin requires.
See Orchestration Permissions.
1. Log in to the Azure CLI.
az login
2. Create a custom role from the file in Orchestration Permissions.
az role definition create --role-definition <role-json-file>
VM-Series Public Cloud Deployments 315 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on Azure
STEP 3 | Associate the role with Active Directory you created in Step 1. You can use the console or
the CLI.
Repeat this step in every subscription defined in the assignableScope section of
the custom role in Orchestration Permissions.
Console
1. On the Azure portal, navigate to Subscriptions and select your subscription.
2. On the left select Access Control (IAM) and then Role Assignments on the top bar.
3. Select Add and chose add role assignment.
• Select the role created you created in Step 3 and leave "Assign access to" as Active
Directory user.
• Select the Active Directory created in Step 1 and click Save.
```
CLI:
```
In the following command, <role-name> refers to the name in the sample JSON file, in the
earlier example, Template Deployment.
az ad sp create-for-rbac --name <name-of-service-principal>
--role <role-name>
--output json
Find Your Azure Directory Domain Name
For the plugin to provide links to your Azure deployment and Application Insights instance in
Azure Portal, you must identify the directory domain for your subscription, as shown below:
Orchestrate a VM-Series Firewall Deployment in Azure
Where Can I Use This? What Do I Need?
• Microsoft Azure
• Microsoft Azure Stack
• Azure® Marketplace
• Azure China Marketplace
```
VM-Series License (PAYG or BYOL)
```
VM-Series plugin
Panorama
Panorama plugin for Azure
VM-Series Public Cloud Deployments 316 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on Azure
Where Can I Use This? What Do I Need?
• Azure Government Marketplace
You can create a maximum of ten orchestrated deployments. Additionally, each orchestrated
deployment supports up to 100 frontend applications.
Azure China and Azure Government are not supported.
VM-Series Public Cloud Deployments 317 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on Azure
STEP 1 | Create a service principal.
Onboard your created service principal credentials to give the Panorama plugin permissions to
make necessary API calls to orchestrate your deployment.
1. Select Setup > Service Principal > Add.
2. Enter a Name and an optional Description to identify the service account.
3. Enter the Subscription ID for the Azure subscription you want to monitor.
You must log in to your Azure portal to get this subscription ID.
4. Enter the Client ID. The client ID is the Application ID associated with your Azure Active
Directory application.
5. Enter the Client Secret and reenter it to confirm.
6. Enter the Tenant ID.
The tenant ID is the Directory ID you saved when you set up the Active Directory
application.
7. Click Validate to verify that the keys and IDs you entered are valid, and Panorama can
communicate with the Azure subscription using the API.
It can take up to a minute to validate. You can update the page to check your progress.
8. When the service principal is valid, commit your changes.
The commit ensures the service principal is available when you configure the deployment.
VM-Series Public Cloud Deployments 318 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on Azure
VM-Series Public Cloud Deployments 319 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on Azure
STEP 2 | Configure your Azure deployment.
1. Select Deployments and Add a configuration.
2. Select Build > General.
• Supply a Name and an optional Description.
• Choose a service principal from the drop list.
You must select a valid service principal to enable the Azure tab.
If you don't see your service principal, return to Step 1 and ensure the service
principal is valid and committed.
3. On the Build > Azure tab, select a region.
The drop list is dynamic—it lists all regions that have a Palo Alto Networks VM-Series
Next Generation Firewall image.
• Existing VNET.
• Select No to create a new VNET.
The plugin uses the VNET CIDR and Directory Domain to create a VNET for you.
• Select Yes to indicate an existing VNET.
• VNET CIDR—Enter your CIDR range. The prefix must be smaller than or equal to /22.
For example, 192.168.0.0/22.
• Directory Domain—See Find Your Azure Directory Domain Name. This string is part
of the URL for all resources in the subscription, and it helps the plugin link to your
deployments.
VM-Series Public Cloud Deployments 320 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on Azure
If you selectYes the plugin asks for the VNET Resource Group, the VNET Name, the
Security CIDR, and the Directory Domain.
• VNET Resource Group—Choose from a list of all resource groups in your selected
region.
• VNET Name—Choose from a list of VNETS in your chosen resource group.
• Security CIDR—Enter your CIDR range. The prefix must be smaller than or equal
to /22. For example, 192.168.0.0/22.
• Directory Domain—See Find Your Azure Directory Domain Name. This string is part
of the URL for all resources in the subscription, and it helps the plugin link to your
deployments.
The VNET Resource Group and VNET name help the plugin locate your existing VNET.
Anything the plugin deploys goes into a resource group that the plugin manages.
VM-Series Public Cloud Deployments 321 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on Azure
STEP 3 | Configure the VM-Series firewall stacks for your deployment.
You can deploy the hub stack to protect Outbound/East-West traffic. You can deploy the
Inbound stack to protect inbound traffic. You can also deploy both stacks if all traffic flows
need to be protected.
The configuration parameters are the same for both stacks.
• License Type—Select BYOL, Bundle 1, or Bundle 2.
```
• License Authcode—(BYOL only). Enter the authcode sent in your Welcome letter.
```
• VM Size
• The drop list displays the VM sizes that correlate with the authcode you entered.
• Bundle1 or Bundle2—Choose any VM size.
Existing Device Group—The device group must be unique across both stacks and deployments.
That is, you need a separate dedicated device group for each stack in each deployment.
If you select No the plugin creates a device group.
If you select Yes, select an existing device group from the drop-down.
• Min Firewalls— A value between 1 and 25 for a VMSS.
• Max Firewall— A value between 1 and 25 for a VMSS.
VM-Series Public Cloud Deployments 322 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on Azure
STEP 4 | Select Build > Firewall > Basic to configure information common to both Stacks.
For Image Type, select Marketplace Image or Custom Image.
```
• Image Resource Group—(custom image only) Choose the resource group containing your
```
custom image. For a custom image, the list displays all resource groups that contain an
image from the region you selected in Step 2.b.
```
• Image—(custom image only) The drop-down displays all images in your chosen resource
```
group.
```
• Software Version—(Marketplace Image) Only valid software versions are displayed. Consult
```
the Compatibility Matrix for the minimum PAN-OS version.
• Username—The administrator username for the firewall you create. The name must be legal
for both VM-Series firewall and Azure. Refer to What are the user name requirments when
creating a VM?
• Password—The administrator password for the firewall you create. The password must
```
meet the character and length requirements (31 characters) for both VM-Series firewall and
```
Azure. Refer to What are the password requirements when creating a VM?.
• Confirm Password—Reenter your password.
• Primary Panorama IP—Specify the Panorama IP address the firewall can use to connect to
the Panorama when it boots up. Choose between the public or private IP address displayed
in the drop-down, or type in the Panorama IP address.
```
• Secondary Panorama IP—(Only if Panorama is in HA setup.) Specify the secondary
```
Panorama IP the firewall can use to connect to the Panorama when it boots up. Choose
from drop-down or type in the correct IP.
• Configure Device Certificate PIN. Because these values are encrypted, you must enter and
confirm each value.
• Device Certificate PIN ID—The device certificate ID.
• Confirm Device Certificate PIN ID
• Device Certificate PIN Value—The certificate PIN value.
• Confirm Device Certificate PIN Value
VM-Series Public Cloud Deployments 323 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on Azure
STEP 5 | Select Build > Firewall > Advanced optional default values.
Check Advanced to edit the default values.
• Autoscaling Metric—Default is dataplane CPU Util Percent.
• Scale In Threshold—Accept the default or define a scale in thresholdt.
• Scale Out Threshold—Accept the default or define a scale in threshold.
• Jumbo Frame—Disabled by default.
Click OK and commit your changes. Refresh the page until you can see the Deploy button, and
click Deploy to launch the deployment. Once the deployment starts, information is written to
the Deployments page.
Deployment takes 15-20 minutes to complete.
If there is an entry in the Deployment Status column, click the hyperlink to view the
deployment details.
The possible status messages are:
• Commit changes—You have added a deployment for the first time but have not yet
committed the changes.
Every configuration change for the deployment must be committed so that the
plugin can pick up your changes.
• Deploying—The plugin is deploying or updating the deployment. For more information, click
the hyperlink to view the detailed status.
• Failure—Deployment has failed. Click the hyperlink and view the Detailed Status for the
Security stack.
• Not Deployed—The plugin is ready to deploy the configuration, but the deployment has not
begun.
• Success—The plugin has successfully deployed the Security stack and the firewalls have
connected to Panorama. The firewalls can pass traffic.
• Warning—Deployment has successfully finished but something external to the deployment
has failed. For example, you might see this message:
FWs have not connected after 20 minutes of the deployment
completing.
Click the hyperlink and view the Security stack.
Once the deployment is deployed, the plugin allows you to modify a certain subset of
parameters. Once the changes have been made, you must do a commit before clicking the
VM-Series Public Cloud Deployments 324 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on Azure
Redeploy button. When an update happens, the plugin makes sure the Panorama config is
created and accurate.
• Deploy—After you commit your initial configuration, select Deploy to launch the
deployment.
• Redeploy—Modify a deployment, commit your changes, and select Redeploy.
Commit changes to the deployment before you click Redeploy.
• Undeploy—Delete a deployment, but keep the configuration so it can be redeployed later.
To remove an existing deployment and its configuration, check a deployment and
select Delete at the bottom of the Deployments page.
STEP 6 | Select Azure > Deployments to view deployment status.
• The Resource Group column displays resource groups the plugin has created.
• The firewall’s management interface uses the firewall Access IP to connect to Panorama.
You must whitelist this address to ensure that Panorama can connect with Panorama to get
the needed configuration.
If Panorama is deployed in a public cloud, make sure to add the firewall Access IP to
the Panorama security group.
See Ports Used for Panorama to determine which ports you need to open to allow traffic.
• Open the link in the Deployment Status column for additional details for each stack.
• Hub-Stack—The hub stack Public IP matches the firewall Access IP in the deployment
summary because the NAT gateway is the same for egress traffic from the deployment
and the management traffic from the firewalls.
All outbound and east-west traffic should be routed to the Egress Private IP for
inspection. You can direct traffic to this address if you configured UDRs.
• Inbound-Stack—The Private IP is the address on the Azure internal load balancer that
fronts the firewalls. You can direct traffic to this address if you're configuring UDRs.
• Follow the links to view deployment information and Application Insights on Azure.
• The Deployment details can show Success, Warning, and Failure messages
STEP 7 | Configure inbound protection for backend TCP/UDP applications.
The public load balancer that fronts the inbound firewall stack is the entry point for any
backend UDP or TCP applications. Add the following configuration to allow the plugin to
VM-Series Public Cloud Deployments 325 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on Azure
manage the necessary load balancer and firewall configuration to route to your backend
application.
1. Select Azure > Deployments and select your deployment.
2. Select the Protect tab and click Add.
3. Supply the application Name and choose a Protocol.
Enter the protection details:
• Frontend IP Type—Select one of new Public IP, existing frontend, and existing Public
IP.
If you select existing frontend, the Frontend Name lists all known frontends on the
load balancer.
```
• Resource Group—(Existing Public IP only) From the drop-down, select the resource
```
group where your desired frontend IP address exists.
```
• IP Name—(Existing Public IP only) Use to map IP to a frontend on the load balancer,
```
configure the load balancer, and create a NAT rule.
• Frontend Port—Add the frontend port that should be configured to receive traffic on
the public load balancer.
• Backend IP—Add the IP address of your backend application.
• Backend Port—Add the port your backend application is expecting to receive traffic
on.
Click OK.
4. Commit to add the configuration on the load balancer and push to the firewalls.
VM-Series Public Cloud Deployments 326 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on Azure
Deploy the VM-Series with the Azure Gateway Load
Balancer
Where Can I Use This? What Do I Need?
• Microsoft Azure
• Microsoft Azure Stack
• Azure® Marketplace
• Azure China Marketplace
• Azure Government Marketplace
```
VM-Series License (PAYG or BYOL)
```
VM-Series plugin
Panorama
Panorama plugin for Azure
You can now deploy the VM-Series firewall for Azure in integration with the Azure gateway
```
load balancer (GWLB). Securing inbound traffic requires complete visibility of the traffic source’s
```
identity as it travels to its destination in the cloud. When you deploy the VM-Series firewalls
behind a public standard load balancer, the source IP addresses of inbound traffic are replaced
with the IP address of the load balancer. As a result, application source identity is obfuscated. By
deploying the VM-Series firewalls behind the Azure GWLB, traffic packet headers and payload
are kept intact, which provides complete visibility of the source’s identity as it travels to its
destination. When Azure GWLB integration is enabled, the VM-Series uses VXLAN packets to
inspect the inner packet of traffic and apply policy to that packet.
When deployed behind the Azure GWLB, VM-Series firewalls can enforce a zone-based security
policy. You can segment VNet-bound and internet-bound traffic by assigning a trust zone to the
VNet-bound traffic and untrust-zone for the internet-bound traffic.
With this integration, you can deploy the VM-Series firewall as a backend to the Azure GWLB in
all supported regions.
VM-Series Public Cloud Deployments 327 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on Azure
• VM-Series firewall integration with the Azure GWLB requires PAN-OS 10.1.4 or later
and VM-Series plugin 2.1.4 or later.
• VM-Series firewall integration with the Azure GWLB is supports IPv4 only. IPv6 only is
not supported on the Azure GWLB.
Follow best practices to not overlap the CIDRs used by different VNets.
VM-Series Public Cloud Deployments 328 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on Azure
STEP 1 | Deploy the VM-Series firewall behind Azure GWLB using the ARM template.
```
STEP 2 | (Optional) Add additional VM-Series firewall instances behind GWLB deployed in Step 1.
```
1. Create a VM using the Microsoft Azure CLI.
Provide the input parameters in the sample command below.
az vm create \
--resource-group <myResourceGroup> \
--name <myPA-VM> \
--vnet-name secVnet \
--subnet Subnet-mgmt \
--public-ip-sku Standard \
--size Standard_DS3_V2 \
--nsg networkSecurityGroup1 \
--admin-username <username> \
--admin-password <password> \
--image paloaltonetworks:vmseries-flex:bundle1:10.1.4 \
--plan-name bundle1 \
--plan-product vmseries-flex \
--plan-publisher paloaltonetworks \
VM-Series Public Cloud Deployments 329 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on Azure
--custom-data "storage-account=<myStorageAccountName>,access-
```
key=<myAccessKey>,file-share=<FileName>,share-
```
```
directory=<SharedDirectoryName>"
```
The init-cfg.txt file is required to bootstrap the VM-Series firewall. It
provides the basic information the firewall needs to connect to your network.
The init-cfg.txt file in the bootstrap folder includes the following
information.
• To deploy the solution with default ports:
plugin-op-commands=azure-gwlb-inspect:enable
• To deploy the solution with custom ports, use the sample command in the
init-cfg.txt file if custom data field is used to define the VNI IDs and
port information. Define the internal and external VNI identifiers in the range
of 800 to 1000.
plugin-op-commands=azure-gwlb-inspect:enable
+internal-port-<internalport>+external-port-
<externalport>+internal-vni-<internalvni>+external-
vni-<internalvni>
If you choose to use custom ports, use these sample commands to configure
the GWLB.
az network lb address-pool tunnel-interface
add --resource-group <myResourceGroup> --lb-
name <myGatewayLoadBalancer> --address-pool
<myBackendPool> --type external --protocol vxlan
--identifier <VNI> --port <port>
az network lb address-pool tunnel-interface
add --resource-group <myResourceGroup> --lb-
name <myGatewayLoadBalancer> --address-pool
<myBackendPool> --type internal --protocol vxlan
--identifier <VNI> --port <port>
For more information, see Custom data and Cloud-init on Azure Virtual
Machines.
2. Create a NIC in the data subnet.
az network nic create -g <myResourceGroup> --vnet-name secVnet
--subnet Subnet-data -n <myDataNIC> --accelerated-networking
true --ip-forwarding true
3. Stop the VM created in Step 1.
az vm deallocate -n <myPA-VM> -g <myResourceGroup>
VM-Series Public Cloud Deployments 330 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on Azure
4. Add the NIC created in Step 2 to the VM.
az vm nic add -g <myResourceGroup> --vm-name <myPA-VM> --nics
<myDataNIC>
5. Add the VM to the backend address pool of the GWLB.
az network nic ip-config address-pool add --address-pool
BackendPool1 --ip-config-name ipconfig1 --nic-name
<myDataNIC> --resource-group <myResourceGroup> --lb-name
securityLB
6. Start the VM.
az vm start -n <myPA-VM> -g <myResourceGroup>
7. Connect to the firewall using SSH. Enter the following in the firewall CLI to verify if the
GWLB is enabled.
show plugins vm_series azure gwlb
```
(Optional) If you don't bootstrap the firewall, the user data is used to configure the ports and
```
VNI IDs. Use the following sample commands on the firewall CLI to enable or disable GWLB,
configure custom ports and VNI IDs, and view GWLB status and port/VNI ID mapping.
The port numbers and VNI IDs must match with the ones in the GWLB backend
address pool.
request plugins vm_series azure gwlb inspect enable yes
request plugins vm_series azure gwlb parameters internal-port 2000
external-port 2001 internal-vni 800 external-vni 801
show plugins vm_series azure gwlb
Sample output:
GWLB enabled : True
Internal Tunnel Port: 2000
Internal Tunnel VNI: 800
External Tunnel Port: 2001
VM-Series Public Cloud Deployments 331 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on Azure
External Tunnel VNI: 801
```
(Manual bootstrap configuration) If you did not bootstrap the VM-Series firewall with GWLB in
```
Step1 or Steps 2.1 to 2.7, perform the following manual processes.
1. Manually configure the dataplane network interfaces as Layer 3 interfaces on the firewall.
1. On the VM-Series firewall web interface, select Network > Interfaces > Ethernet.
2. Click ethernet 1/1 and configure as follows:
```
• Set Interface Type to Layer3 (default).
```
• On the Config tab, assign the interface to a virtual router.
• Also on the Config tab, expand the Security Zone drop-down and select New Zone.
Define an internal and external zone, then click OK.
• On the IPv4 tab, select DHCP Client.
• Disable the Automatically create default route to default gateway provided by server
to ensure that traffic handled by this interface does not flow directly to the default
gateway in the VNet.
VM-Series Public Cloud Deployments 332 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on Azure
3. On the Advanced tab, create a Management Profile to allow health checks to be
received by the firewall.
4. Commit your changes and verify that the link state for the interfaces is up.
2. Create a static route on the VM-Series firewall.
1. On the VM-Series firewall web interface, select Network > Virtual Routers and select
the virtual router associated with the data interface.
2. Select Static Routes and click Add.
3. Configure the static route.
VM-Series Public Cloud Deployments 333 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on Azure
VM-Series Public Cloud Deployments 334 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on Azure
4. Click OK.
5. Commit your changes.
3. Create two subinterfaces under eth1/1 to enforce zone-based security policies.
1. On the VM-Series firewall web interface, select Network > Interface.
2. Highlight ethernet1/1 and click Add Subinterface.
3. Enter a numerical suffix (1 to 9,999) to identify the subinterface.
4. Enter a VLAN Tag for the subinterface. This field is required but the VLAN isn't used.
VNI ID/Port for the internal tunnel is mapped to the VLAN 1 tag and the
external tunnel is mapped to the VLAN 2 tag. The VLAN 1 tag and VLAN 2 tag
```
must always be mapped to the internal (trust) zone and external (untrust) zone
```
respectively.
5. Select the Virtual Router associated with the data interface.
6. Select a Security Zone.
7. On the IPv4 tab, set the Type to DHCP Client.
8. Click OK.
9. Repeat this command for the second subinterface.
10.Commit your changes.
VM-Series Public Cloud Deployments 335 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on Azure
Create a Custom VM-Series Image for Azure
Where Can I Use This? What Do I Need?
• Microsoft Azure
• Microsoft Azure Stack
• Azure® Marketplace
• Azure China Marketplace
• Azure Government Marketplace
```
VM-Series License (PAYG or BYOL)
```
VM-Series plugin
Panorama
Panorama plugin for Azure
You can create a custom VM-Series firewall image for later use in your Azure deployment. A
custom image gives you flexibility and consistency to deploy the VM-Series firewall with the
PAN-OS version you want to use instead of being restricted to using only an image available
through the Azure marketplace. Additionally, your custom image can include the latest content
and antivirus updates.
Creating a custom image requires that you remove all private data—user configuration, users,
plugin configuration, etc—before creating the VHD. Additionally, Complete the following
procedure to prepare and create a custom image.
If the VM-Series firewall used to create your custom image was deployed using a premium
disk type, any VM-Series firewall deployed using the custom image must be deployed
using the same premium disk type. However, if you create an image using firewall
deployed with a standard disk type, you can deploy the firewall using a standard or
premium disk type.
STEP 1 | Log in to Azure.
STEP 2 | Deploy the VM-Series firewall from the Azure Marketplace.
```
STEP 3 | (BYOL license only) Activate your license.
```
STEP 4 | Upgrade the VM-Series Firewall to PAN-OS 10.0.3. Upgrading to PAN-OS 10.0.3 also
upgrades the VM-Series plugin to 2.0.3.
STEP 5 | Access the VM-Series firewall command-line interface via SSH using the username and
password provided in the Azure Marketplace template.
STEP 6 | Verify that your VM-Series firewall has the correct PAN-OS, VM-Series plugin, content, and
antivirus versions.
show system info
If you're using PAN-OS 10.1, ensure that you upgrade the VM-Series plugin to version
2.1.7 or higher and if you're using PAN-OS 10.2.0, ensure you're using VM-Series
plugin to 3.0.3 or higher.
```
STEP 7 | (BYOL license only) Deactivate your license.
```
VM-Series Public Cloud Deployments 336 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on Azure
STEP 8 | Perform a private data reset on the VM-Series firewall. This command requires the firewall
```
to reboot. Wait for the VM-Series firewall to reboot complete before continuing; the reboot
```
can take five to seven minutes.
request system private-data-reset shutdown
Wait for firewall to shutdown.
STEP 9 | Create a new VHD image from the VM-Series instance.
1. Log in to the Azure CLI.
2. Verify that you're using the correct subscription.
az account set --subscription <subscription-id>
3. Execute the following commands to generalize the VM, allowing it to be imaged for
multiple deployments, and create the new VHD.
az vm deallocate --resource-group <myResourceGroup> --name
<myVM>
az vm generalize --resource-group <myResourceGroup> --name
<myVM>
az image create --resource-group <myResourceGroup> --name
<myImage> --source <resource-id-of-VM>
STEP 10 | Create a new VM-Series firewall from your custom image.
az vm create --resource-group <myResourceGroup> --name <myNewVM>
--image <myImage> --admin-username <newUser> --admin-password
<newPassword> --plan-name byol --plan-product vmseries-flex --plan-
publisher paloaltonetworks --size Standard_DS2_v2
STEP 11 | After deploying a VM-Series firewall with your custom image, verify your deployment.
1. Log in to the firewall using the credentials provided while bringing up the VM from the
custom image.
2. After logging in successfully, verify that your firewall is running the correct PAN-OS
version and has the correct content and antivirus versions.
show system info
```
STEP 12 | (Optional) Copy the custom image to another region.
```
az image copy –source-resource-group <source-rg> –source-object-name
<pa-vm-image-name> –target-location <target-region> –target-resource-
group <destination-rg>
VM-Series Public Cloud Deployments 337 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on Azure
Use Azure Security Center Recommendations to Secure
Your Workloads
Where Can I Use This? What Do I Need?
• Microsoft Azure
• Microsoft Azure Stack
• Azure® Marketplace
• Azure China Marketplace
• Azure Government Marketplace
```
VM-Series License (PAYG or BYOL)
```
VM-Series plugin
Panorama
Panorama plugin for Azure
Azure Sentinel
Microsoft has deprecated Azure Security Center support for partner security solutions
and replaced it with Azure Sentinel.
When you deploy new workloads within your Azure subscription that is enabled for Azure
Security Center, Azure Security Center enables you to secure these workloads in two ways. In
one workflow, Azure Security Center recommends you to deploy a new instance of the VM-Series
firewall to secure an internet-facing application workload. In the other workflow, Azure Security
```
Center discovers VM-Series firewalls (partner security solutions) that you have deployed within
```
the Azure subscription and you have to then perform additional configuration to connect the VM-
Series firewall to Azure Security Center so that you can view alerts on the dashboard. See Azure
Security Center Integration for details on the integration and the pros and cons of each workflow.
Deploy a VM-Series Firewall Based on an Azure Security Center
Recommendation
Azure Security Center scans your Azure resources and provides recommendations to secure
workloads that need a next-generation firewall. The recommendation displays on the dashboard
and you can then either deploy a new instance of the VM-Series firewall from the Azure
marketplace or you can use the Azure CLI, PowerShell, or an ARM template. The advantage of
using a customized deployment using Azure CLI, PowerShell, or ARM template is that you can
deploy the VM-Series firewall within the same resource group as the workload that you need to
secure. When you deploy the VM-Series firewall using the Azure marketplace, Azure requires that
you deploy the firewall into a new resource group or an empty resource group only. Therefore,
the marketplace deployment requires you to then ensure that the traffic from the workload you
want to secure is steered to the firewall that is in a different resource group.
STEP 1 | Log in to your Azure portal and access the Security Center dashboard.
VM-Series Public Cloud Deployments 338 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on Azure
STEP 2 | Select Recommendations.
STEP 3 | Select Add a Next Generation Firewall, and select the workload you want to secure.
STEP 4 | Choose whether you want to deploy a new instance of the VM-Series firewall or use an
existing instance of the VM-Series firewall.
To use this workflow, stage a workload with a public IP address that is exposed to the internet
and deploy an instance of the VM-Series firewall in a new resource group. Then, delete the
VM-Series Public Cloud Deployments 339 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on Azure
workload you staged, and deploy your production workloads within the resource group in
which you deployed the VM-Series firewall.
```
• To Create New, see Deploy the VM-Series Firewall from the Azure Marketplace (Solution
```
```
Template).
```
• To Use existing solution, select the VM-Series firewall that you have previously deployed.
Connect an Existing VM-Series Firewall From Azure Security
Center
When an Azure Security Center detects that you have deployed the VM-Series firewall within the
Azure subscription, it displays the firewall as a security solution. You can then connect the VM-
```
Series firewall to Security Center using the Common Event Format (CEF) over syslog, and view
```
firewall logs as alerts on the Security Center dashboard.
STEP 1 | Log in to your Azure portal and access the Security Center dashboard.
STEP 2 | Select Security Solutions to view all available VM-Series firewalls within this Azure
subscription.
VM-Series Public Cloud Deployments 340 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on Azure
STEP 3 | Expand Discovered solutions, and select the VM-Series firewall instance that is in the same
resource group as the workload you want to secure and click Connect.
To view firewall logs as alerts on the Security Center dashboard, you need to follow the four-
step process that displays on the screen.
STEP 4 | On successfully connecting the VM-Series firewall to Security Center, the VM-Series firewall
displays in the Connected solutions list.
Click View to verify that the firewall is protecting the workload that you need to secure.
Use Panorama to Forward Logs to Azure Security Center
Where Can I Use This? What Do I Need?
• Microsoft Azure
• Microsoft Azure Stack
• Azure® Marketplace
```
VM-Series License (PAYG or BYOL)
```
VM-Series plugin
Panorama
VM-Series Public Cloud Deployments 341 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on Azure
Where Can I Use This? What Do I Need?
• Azure China Marketplace
• Azure Government Marketplace
Panorama plugin for Azure
If you're using Panorama to manage your firewalls, you can use templates and device groups
to forward firewall logs to the Azure Security Center. With the default Azure Security Center
Log Forwarding profile, Threat, and WildFire Submissions log of low, medium, high, or critical
severity generated on the firewall is displayed as security alerts on the Azure Security Center
dashboard. So that you can focus and triage alerts more efficiently, you can set up granular log
filters to only forward logs of interest to you, or forward high and critical severity logs only. You
can also selectively attach the Log Forwarding profile to a few Security policy rules based on your
applications and security needs.
To enable the Azure Security Center integration from Panorama, use the following workflow.
STEP 1 | Add the firewall as a managed device on Panorama.
STEP 2 | From Panorama, create a template and a device group to push log forwarding settings to the
firewalls that will be forwarding logs to the Azure Security Center.
VM-Series Public Cloud Deployments 342 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on Azure
STEP 3 | Specify the log types to forward to the Logging Service.
The way you enable forwarding depends on the log type. For logs that are generated based on
a policy match, you use a Log Forwarding profile within a device group, and for other log types
you use the Log Settings configuration within a template.
1. Configure forwarding of system, configuration, User-ID, and HIP Match logs.
1. Select Device > Log Settings.
2. Select the Template that contains the firewalls you want to forward logs to the
Logging Service.
3. For each log type that you to forward to the Logging Service, Add a match list filter.
Give it a Name, optionally define a Filter.
4. Add Built-in Actions and enter a Name. The Azure-Security-Center-Integration action
will be autoselected. Click OK.
5. Click OK.
2. Configure forwarding of all other log types that are generated when a policy match
occurs such as Traffic, Threat, WildFire Submission, URL Filtering, Data Filtering, and
VM-Series Public Cloud Deployments 343 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on Azure
Authentication logs. To forward these logs, you must create and attach a Log Forwarding
profile to each policy rule for which you want to forward logs.
1. Select the Device Group, and then select Objects > Log Forwarding to Add a profile.
In the Log Forwarding profile match list, add each log type that you want to forward.
2. Select Add in Built-in Actions to enable the firewalls in the device group to forward
the logs to the Azure Security Center.
3. Create basic security policy rules in the device group and select Actions to attach the
Log Forwarding profile you created for forwarding logs to the Azure Security Center.
Until the firewall has interfaces and zones and a basic Security policy, it won't let any
```
traffic through, and only traffic that matches a Security policy rule will be logged (by
```
```
default).
```
4. For each rule you create, select Actions and select the Log Forwarding profile that
allows the firewall to forward logs to the Azure Security Center.
STEP 4 | Commit your changes to Panorama and, push them to the template and device group you
created.
STEP 5 | Verify that the firewall logs are being forwarded to the Azure Security Center.
1. Log in to the Azure portal, select the Azure Security Center.
2. Verify that you can see firewall logs as Security alerts on the Azure Security Center
dashboard.
VM-Series Public Cloud Deployments 344 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on Azure
Deploy the VM-Series Firewall on Azure Stack
Where Can I Use This? What Do I Need?
• Microsoft Azure
• Microsoft Azure Stack
• Azure® Marketplace
• Azure China Marketplace
• Azure Government Marketplace
```
VM-Series License (PAYG or BYOL)
```
VM-Series plugin
Panorama
Panorama plugin for Azure
You can deploy the VM-Series firewall on Azure Stack to secure inter-subnet traffic between
applications in a multi-tier architecture and outbound traffic from servers within your Azure Stack
deployment. If you want to use the VM-Series firewall as a gateway that secures inbound traffic
destined to the servers within your Azure Stack deployment, you must deploy a NAT appliance
in front of the firewall that receives inbound traffic and forwards it to the firewall. The NAT
appliance is required because on Azure Stack you can't assign a public IP address to a non-primary
interface of a virtual machine, such as the VM-Series firewall.
The VM-Series firewall on Azure stack does not have support for bootstrapping, Azure
Application Insights, or the Azure Security Center integration.
Unlike on public Azure, you don't have a solution template to deploy the VM-Series firewall on
Azure Stack. Therefore, you must use an ARM template to deploy the VM-Series firewall. To
get started, you can use the community supported sample ARM template on GitHub, and then
develop your own ARM template for production deployments.
STEP 1 | Download marketplace items from Azure to AzureStack.
To deploy the VM-Series firewall on Azure Stack, you need access to the BYOL offer of the
```
VM-Series firewall PAN-OS image (8.1 or later). You can download the image directly from the
```
Azure Marketplace to Azure Stack in a connected deployment.
STEP 2 | Access the Azure Stack portal.
```
Your Azure Stack operator (either a service provider or an administrator in your organization),
```
should provide the correct URL to access the portal.
STEP 3 | Deploy the VM-Series firewall.
A solution template for the VM-Series firewall isn't available on Azure Stack. Therefore, you
must reference the image that you downloaded in the previous step, in an ARM template to
VM-Series Public Cloud Deployments 345 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on Azure
deploy the VM-Series firewall. To get started, you can deploy the sample ARM template that’s
available on GitHub under the community-supported policy:
1. Get the sample Azure Stack GitHub template.
• Select azurestackdeploy.json to view the contents.
• Click Raw and copy the contents of the JSON file.
2. Deploy the sample GitHub template.
You can deploy the firewall in an existing resource group that’s empty or into a
new resource group. The default VNet in the template is 192.168.0.0/16, and it
deploys a VM-Series firewall has three network interfaces, one management interface
VM-Series Public Cloud Deployments 346 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on Azure
on 192.168.0.0/24 subnet and two dataplane interfaces on 192.168.1.0/24 and
192.168.2.0/24 subnets. You can customize these subnets to match your needs.
• Log in to the Azure Stack portal.
• Select New > Custom > Template deployment.
• Edit template, delete all existing content in the template, and paste the JSON
template contents you copied earlier andSave.
• Edit parameters, enter the values for the required parameters and modify the defaults
if you need to, then click OK.
VM-Series Public Cloud Deployments 347 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on Azure
• Choose the Subscription you want to use, and then click OK.
• Choose an existing Resource Group that’s empty or create a new one, and click OK.
• Click Create. A new tile on the dashboard displays the progress of the template
deployment.
VM-Series Public Cloud Deployments 348 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on Azure
STEP 4 | Next Steps:
1. Log in to the web interface of the firewall.
```
Using a secure connection (HTTPS) from your web browser, log in to the DNS name for
```
the firewall. Enter the username/password you defined earlier. You will see a certificate
```
warning; that’s okay. Continue to the webpage.
```
2. Activate the license on the VM-Series firewall.
1. Create a Support Account and Register the VM-Series Firewall (with Auth Code).
2. On the firewall web interface, select Device > Licenses and select Activate feature
using authentication code.
3. Enter the capacity auth code that you registered on the support portal. The firewall
```
will connect to the update server (updates.paloaltonetworks.com), and download the
```
license and reboot automatically.
4. Log back in to the web interface on the Dashboard, confirm that a valid Serial#
displays.
The VM Mode displays as Microsoft Azure.
If the term Unknown displays, it means the device isn't licensed. To view traffic logs
on the firewall, you must install a valid capacity license.
STEP 5 | Deploy the VM-Series firewall using an Azure Solution Template.
VM-Series Public Cloud Deployments 349 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on Azure
Deploy the VM-Series Firewall on Azure Stack HCI
Where Can I Use This? What Do I Need?
• Microsoft Azure
• Microsoft Azure Stack
• Azure® Marketplace
• Azure China Marketplace
• Azure Government Marketplace
```
VM-Series License (PAYG or BYOL)
```
VM-Series plugin
Panorama
Panorama plugin for Azure
You can deploy the VM-Series firewall on Azure Stack HCI within Software Defined Networking
```
(SDN) architecture. Azure Stack HCI is a hyperconverged infrastructure (HCI) cluster solution that
```
hosts virtualized Windows and Linux workloads and their storage in a hybrid environment that
combines on-premises infrastructure with Azure cloud services. For more information, see Azure
Stack HCI solution overview.
You can deploy the VM-Series firewall on Azure Stack HCI and protect the inbound traffic,
outbound traffic, and east-west traffic between various vNETs. The VM-Series firewall traffic
is pinned to an active interface with an out-of-band management interface, where the internal
applications and inbound traffic are routed through route tables to force traffic through the
firewall load balancer for east-west and north-south traffic to provide internal microsegmentation
and a security perimeter. The SDN Gateway then allows traffic to pass in and out of the internal
SDN via the hub vNet.
Perform the following steps to deploy the VM-Series firewall on Azure Stack HCI SDN:
1. To get started, you will need the following:
• One or more servers from the Azure Stack HCI Catalog and Azure subscription.
• Operating system licenses for your workload VMs – for example, Windows Server. See
Activate Windows Server VMs.
• An internet connection for each server in the cluster that can connect via HTTPS outbound
traffic to well-known Azure endpoints at least every 30 days. See Azure connectivity
requirements for more information.
• For clusters stretched across sites:
```
• At least one 1 GB connection between sites (a 25 GB RDMA connection is preferred).
```
```
• At least four severs (two in each site).
```
• An average latency of 5 ms round trip between sites if you want to do synchronous
replication where writes occur simultaneously in both sites.
```
• To use SDN infrastructure, you need a virtual hard disk (VHD) for the Azure Stack HCI
```
operating system to create Network Controller, Multiplexer, and Gateway VMs on
```
Management Network (see Plan to deploy Network Controller, Deploy SDN Software Load
```
```
Balancer, and Deploy SDN Gateway).
```
For more information, see What you need for Azure Stack HCI.
VM-Series Public Cloud Deployments 350 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on Azure
2. Create an Azure Stack HCI cluster using any one of the below given methods:
• Using Windows Admin Center. For more information, see Create an Azure Stack HCI cluster
using Windows Admin Center.
• Using Windows PowerShell. For more information, see Create an Azure Stack HCI cluster
using Windows PowerShell.
3. Register Azure Stack HCI cluster with Azure for monitoring, support, billing, and hybrid
services.
VM-Series Public Cloud Deployments 351 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on Azure
4. Deploy the SDN infrastructure using any one of the following methods:
• Deploy using Windows Admin Center
• Deploy using SDN Express
• Deploy at cluster creation
This document considers the Windows Admin Center option for deploying the VM-
Series firewall.
After successfully deploying the SDN infrastructure, go to the SDN Infrastructure dashboard
on your Windows Admin Center and ensure that all server nodes are healthy.
VM-Series Public Cloud Deployments 352 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on Azure
VM-Series Public Cloud Deployments 353 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on Azure
5. After deploying the SDN infrastructure, create a Hyper-V Network Virtualization (HNV) virtual
network.
VM-Series Public Cloud Deployments 354 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on Azure
VM-Series Public Cloud Deployments 355 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on Azure
By modeling a VLAN-based network as an SDN logical network, you can apply network policies
to workloads that are attached to these networks. For more information, see Manage Tenant
Logical Network.
VM-Series Public Cloud Deployments 356 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on Azure
VM-Series Public Cloud Deployments 357 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on Azure
6. Deploy the VM-Series firewall.
Download the VHDX file. Register your VM-Series firewall and obtain the VHDX file.
• Go to https://www.paloaltonetworks.com/services/support.
• Filter by PAN-OS for VM-Series Base Images and download the VHDX file. For example,
PA-VM-HPV-7.1.0.vhdx.
VM-Series Public Cloud Deployments 358 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on Azure
7. Install the VM-Series firewall.
Perform the following steps to install the VM-Series firewall on Azure Stack HCI:
Add a virtual machine.
1. Go to Windows Admin Center > Cluster Manager and select the Cluster.
2. Go to Virtual Machines > Add> New.
VM-Series Public Cloud Deployments 359 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on Azure
VM-Series Public Cloud Deployments 360 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on Azure
Configure the following settings in the New Virtual Machine Wizard:
• Enter the Name for the VM-Series firewall.
• Select Generation 1. This is the default option and the only version supported.
VM-Series Public Cloud Deployments 361 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on Azure
VM-Series Public Cloud Deployments 362 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on Azure
• Select the Host and Path for the VM-Series firewall. Browse the VHD/VHDX FW image file.
```
Note: You must store the VHD/VHDX in location C:/ClusterStorage/Volumes.
```
• For Startup Memory, assign the memory based on the VM-Series System Requirements of
your VM-Series model.
• To configure networking, from the Virtual Network dropdown menu, select vNet.
```
A converged virtual switch (vSwitch) gets created while bringing up the Azure Stack
```
HCI cluster.
• Select Virtual Switch > Isolation Mode > Virtual Network > Virtual Subnet.
• Click Add IP Address and enter the IP address for the management interface.
```
• Select Network Security Group (optional).
```
• To connect the Virtual Hard Disk, select Use an existing virtual hard disk and browse to the
VHDX file you downloaded earlier in Step 6.
• Click Create.
VM-Series Public Cloud Deployments 363 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on Azure
8. After successfully installing the VM-Series firewall on the cluster, you can add more Network
Adapters for data traffic. Perform the following to add a Network Adapter:
• Select your VM, go to Settings > Network.
VM-Series Public Cloud Deployments 364 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on Azure
VM-Series Public Cloud Deployments 365 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on Azure
• Click Add Network Adapter.
VM-Series Public Cloud Deployments 366 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on Azure
VM-Series Public Cloud Deployments 367 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on Azure
• Select Virtual Switch > Isolation Mode > Virtual Network > Virtual Subnet.
• Click Add IP Address and enter the IP address for the data interface.
```
• Select Network Security Group (optional).
```
• Click Save Network Settings.
VM-Series Public Cloud Deployments 368 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on Azure
VM-Series Public Cloud Deployments 369 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on Azure
Connect at least one network adapter for the data interface on the firewall. You can create
and add more Network Adapters using the same steps above.
9. (Optional) Enable MAC address spoofing if you're not using Layer 3 with MAC address.
1. Double-click the dataplane virtual network adapter and click Advanced Settings.
2. Click the Enable MAC address spoofing check box and click Apply.
10.Bootstrap the VM-Series Firewall.
VM-Series Public Cloud Deployments 370 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on Azure
11.Power on the firewall.
VM-Series Public Cloud Deployments 371 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on Azure
VM-Series Public Cloud Deployments 372 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on Azure
Deploy VM-Series on Azure Stack Edge
Where Can I Use This? What Do I Need?
• Microsoft Azure
• Microsoft Azure Stack
• Azure® Marketplace
• Azure China Marketplace
• Azure Government Marketplace
```
VM-Series License (PAYG or BYOL)
```
VM-Series plugin
Panorama
Panorama plugin for Azure
VM-Series can now secure 5G traffic within Microsoft Azure Stack Edge. The Microsoft Azure
Stack Edge is a purpose-built hardware-as-a-service that allows you to run workloads while
gaining actionable insights at the edge of the network, where data originates. Azure Stack Edge
will host Azure 5G Core network functions that will help the enterprise edge applications connect
either to other break-out applications or to the internet. With Palo Alto Networks best in class 5G
Security, Azure customers can now protect their 5G connected enterprise applications using VM-
Series firewalls.
See Azure Stack Edge for more information on the Azure Stack Edge box. For the
VM-Series offer on Azure Stack Edge, see VM-Series Next-Gen Firewall Edge Azure
Application.
Security Challenges in 5G and Edge Deployments
5G and edge-deployed networks have transformed enterprises and industries. These deployments
use next generation mobile technology, which guarantees reliable networks, however they lack
security against a complex and evolving threat landscapes.
These security challenges include:
• Greater number of connected and BYOD devices increases attack vectors.
• Limited control and visibility into user traffic.
• Internet-based attacks, or from compromised management systems.
• Open source and exposed APIs.
• Resource theft.
• Network configuration attacks.
```
• DoS (Denial of Services) and spoofing attacks on 5G protocols.
```
• Limited visibility into subscribers and equipment.
• Untrusted applications and services.
Benefits of VM-Series Integration with Azure Stack Edge
5G-Native Security with VM-Series
VM-Series Public Cloud Deployments 373 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on Azure
VM-Series deployments with Azure Stack Edge provide enterprise grade security paradigms to 5G
deployments. These deployments use the following security features:
• Real-time correlation of threats to 5G end-user application traffic. Provides security controls
and enforcement to inspect tunneled end-user traffic to enterprise applications.
• Containerized 5G security. Provides for secure, highly distributed cloud-native 5G networks.
```
• 5G MEC security. Enables industry digitization with MEC (multi-access edge computing),
```
complementing 5G access networks.
The VM-Series deployment on Azure Stack Edge for enterprise 5G security protects edge
applications within the following areas:
• RAN security. SCTP stateful inspection to protect Azure 5GC from the RAN.
• GTP-U Security. Tunnel content inspection to protect the payload end-user, edge application
traffic within the GTP-U tunnel.
• Internet Perimeter. Secure Inbound Outbound traffic into the remote edge, break-out
application, and internet traffic at the perimeter.
The image below illustrates how VM-Series firewalls are used in Azure Stack Edge deployments:
Deploy the VM-Series Firewall on Azure Stack Edge
You can deploy the VM-Series firewall on Azure Stack Edge to secure inter-subnet traffic
between applications in a multitier architecture and outbound traffic from servers within your
Azure Stack Edge deployment.
The NAT appliance is required because in Azure Stack deployments you can't assign a
public IP address to a nonprimary interface or a virtual machine, such as the VM-Series
firewall. This NAT appliance receives inbound traffic and forwards it to the VM-Series
firewall.
To deploy the VM-Series firewall on Azure Stack Edge:
STEP 1 | Configure a virtual switch for the management port. If Azure Private 5G Core is being
coinstalled, the virtual switch for the management port will be configured as part of that
VM-Series Public Cloud Deployments 374 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on Azure
installation. If you're not installing Azure Private 5G Core, use the instructions provided
below.
1. Add a virtual switch for the management port, for example, port 2.. For more
information, see Configure virtual switches.
2. Configure the switch as a Compute virtual switch. You don't need to configure any
Kubernetes nodes or service IP addresses.
STEP 2 | Create and register an Azure Network Function Manager device resource. After performing
steps 1-2, three virtual switches are available: management, LAN, and WAN. On the Azure
Stack Edge GPU, LAN is port 5, and WAN is port 6. On Azure Stack Edge Pro 2, LAN is port
3 and WAN is port 4.
STEP 3 | Configure the required virtual networks on the LAN and WAN virtual switches. Add a virtual
network for the firewall’s untrust1 interface on the LAN virtual switch using a nonzero VLAN
ID.
STEP 4 | Add another virtual network for the firewall's untrust2 interface on the WAN virtual switch
using a nonzero VLAN ID.
STEP 5 | Create a User Assigned Managed Identity with permission for
Microsoft.HybridNetwork/devices/join/action on your Azure Stack Edge. The
Azure Portal user will need either Owner or User Access administrator permissions on the
ASE Resource Group to be able to create a user assigned managed identity.
STEP 6 | Navigate to the Azure Portal Marketplace and select the version for your VM-Series firewall.
STEP 7 | In the Azure Portal Marketplace, search for VM-Series Palo Alto.
STEP 8 | Select the VM-Series Palo Alto Networks NGFW Edge Azure Application option. Choose 8
CPU or the 16 CPU option from the Plan drop-down.
STEP 9 | Click Create. When you create the VM-Series firewall, the installation process guides you
through the steps to configure basic information, manage details, configure network settings
and the firewall. Once you complete these steps, review and create the firewall.
STEP 10 | Configure Basic information, including:
1. Subscription. Select the subscription used for the Azure Stack Edge when it was
deployed.
2. Resource Group. Select a resource group specific to this deployment. If one does not
exist, click Create new and use a name similar to ase-VM-Series-p5gc.
3. Region. Refer to the Microsoft Technical Team for the appropriate region.
4. Select the Azure Network Function Manager device on which the VNF will be deployed.
5. Application Name. Enter a name for the application.
6. Managed Resource Group. This resource group retains the resources required by the
managed app. Use the default value for this field.
STEP 11 | The Azure Portal user needs at least User Access administrator permission on the ASE
Resource Group to configure the role assignment.
VM-Series Public Cloud Deployments 375 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on Azure
STEP 12 | Create a custom role with permissions for Microsoft.HybridNetwork/devices/join/
action, unless one already exists. For more information, see Create or update Azure
custom roles using the Azure portal.. Use the information provided in step 1 for the
```
Microsoft.HybridNetwork/devices/join/action; the Clone a role method isn't appropriate in
```
this context.
STEP 13 | Configure Managed Identify details. Select a managed identity. If one does not exist, create
one using the portal. Ensure the managed identity uses the correct subscription and resource
group.
STEP 14 | Create a user-assigned managed identity, unless one already exists. For more information,
see Create a user-assigned managed identity.
STEP 15 | Assign the user-assigned managed identity the custom role from above at the scope of the
Azure Stack Edge, or the Resource Group or Subscription containing the Azure Stack Edge.
For more information, see User-assigned managed identity.
STEP 16 | Continue creating the VM-Series firewall using the wizard. Configure Network settings.
Configure the IP addresses of the management, LAN, and WAN interfaces, along with any
VLANs used in the deployment.
The table below shows the interfaces and how they map to the Azure Stack Edge device and
Azure Private 5G Core. Use this table to create reference designs for VM-Series deployments
on Azure Stack Edge and Azure Private 5G Core.
Interface
Short Name
```
(NFM)
```
Interface
Full Name
```
(VM-Series
```
```
managed app )
```
Interface
Name in
Panorama
Interface
Name mapped
with security
zone Name
Azure Stack
Edge Physical
port
Description
mgmt Management
interface
Management Management 1,2,3,4 This is the
firewall’s
management
Internet
Protocol,
from which it
communicates
with
Panorama in
the cloud.
mgmt-
inspect
Management
interface for
inspection
Ethernet 1/1 trust-access 1,2,3,4 This is the
IP address
for providing
firewall
functionality
to the OAM
network.
lan1 First LAN
Interface
Ethernet 1/2 trust-access 5 This is
used to
VM-Series Public Cloud Deployments 376 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on Azure
Interface
Short Name
```
(NFM)
```
Interface
Full Name
```
(VM-Series
```
```
managed app )
```
Interface
Name in
Panorama
Interface
Name mapped
with security
zone Name
Azure Stack
Edge Physical
port
Description
communicate
with the
RAN’s N2
interface or
N2 and N3
interface.
lan2 Second LAN
Interface
Ethernet 1/3 untrust-n2 5 This is
used to
communicate
with the
RAN’s N2
interface or
N2 and N3
interface.
lan3 Third LAN
Interface
Ethernet 1/4 untrust-n3 5 This can
be used to
communicate
with the
RAN’s N3
interface
independently.
wan1 First WAN
Interface
Ethernet 1/5 trust-core 6 This is
used to
communicate
with the
Azure Private
5G Core N6
interface.
wan2 Second WAN
Interface
Ethernet 1/6 untrust-
mgmt
6 This is
used to
communicate
with the
internet on
behalf of
the OAM
network.
wan3 3rd WAN
Interface
Ethernet 1/7 untrust-n6 6 This is
used to
communicate
with the
internet or
VM-Series Public Cloud Deployments 377 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on Azure
Interface
Short Name
```
(NFM)
```
Interface
Full Name
```
(VM-Series
```
```
managed app )
```
Interface
Name in
Panorama
Interface
Name mapped
with security
zone Name
Azure Stack
Edge Physical
port
Description
other data
networks on
behalf of the
UEs.
STEP 17 | Complete the VM-Series configuration:
1. Enter the VM name representing the VM-Series firewall. Use a meaningful description.
2. Enter Custom Data. This important information is used for cloud-init parameters. It
provides the VM-Series firewall with licensing information and the IP address of the
Panorama server used for communication.
```
Within the init-cfg.txt file, the Custom data format resembles the following (replace bold text
```
```
with appropriate values):
```
```
type=dhcp-client; hostname=panfw001; tplname=ngfw-stack;
```
```
dgname=ngfw-device; op-command-modes=jumbo-frame; tplname=ngfw-
```
```
stack; dgname=ngfw-device; op-command-modes=jumbo-frame;panorama-
```
```
server=1.2.3.4; vm-auth-key=123456789123456; authcodes=
```
```
panorama-server=1.2.3.4; vm-auth-key=123456789123456;
```
```
authcodes=D1234567; timezone=UTC+3
```
Use the vm-auth-key generated on Panorama using the command request bootstrap vm-
auth-key generate lifetime 24. Use a timezone with a UTC offset value that
reflects the location of the Azure Stack Edge box. You can also check the Azure Stack Edge
box local time and ensure the same is reflected in UTC offset format within the custom data.
STEP 18 | Review and create the VM-Series firewall. Verify that all the settings are correct, then deploy
the VM-Series firewall.
STEP 19 | After deploying the firewall on the Azure Stack Edge device verify its connection to
Panorama. Check the status using the CLI of the VM-Series NGFW:
admin@pa-azr-ase> show panorama-status
Panorama Server 1 : <panorama ip>
```
Connected : yes
```
VM-Series Public Cloud Deployments 378 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on Azure
Enable Azure Application Insights on the VM-Series
Firewall
Where Can I Use This? What Do I Need?
• Microsoft Azure
• Microsoft Azure Stack
• Azure® Marketplace
• Azure China Marketplace
• Azure Government Marketplace
```
VM-Series License (PAYG or BYOL)
```
VM-Series plugin
Panorama
Panorama plugin for Azure
The VM-Series firewall on Azure can publish custom PAN-OS metrics natively to Azure
Application Insights that you can use to monitor the firewalls directly from the Azure portal.
These metrics allow you to assess performance and usage patterns that you can use to set alarms
and take action to automate events such as launching or terminating instances of the VM-Series
firewalls. See Custom PAN-OS Metrics Published for Monitoring for a description on the metrics
that are available.
To configure application insights on Azure VM-Series firewalls, you must have internet
access and allow the following primary global ingestion endpoints.
• dc.services.visualstudio.com
• dc.applicationinsights.azure.com
• dc.applicationinsights.microsoft.com
VM-Series Public Cloud Deployments 379 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on Azure
STEP 1 | On the Azure portal, create your Application Insights instance to monitor the firewall and
copy the Instrumentation Key from Configure > Properties.
The firewall needs this key to authenticate to the Application Insights instance and publish
metrics to it. See VM-Series on Azure Service Principal Permissions for the permissions
required.
VM-Series Public Cloud Deployments 380 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on Azure
STEP 2 | Enable the firewall to publish metrics to your Application Insights instance.
1. Log in to the VM-Series firewall on Azure.
2. Select Device > VM-Series > Azure.
3. Edit Azure Application Insights and enter the Instrumentation Key you copied earlier.
The default interval for publishing metrics is 5 minutes. You can change this to vary from
1-60 minutes.
4. Commit your changes.
The firewall generates a system log to it record the success or failure to authenticate to
Azure Application Insights.
VM-Series Public Cloud Deployments 381 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on Azure
STEP 3 | Verify that you can view the metrics on the Azure Application Insights dashboard.
1. On the Azure portal, select the Application Insights instance, and select Monitoring >
Metrics to view the PAN-OS custom metrics.
2. Select the metrics that you want to monitor for trends and trigger alerts. Refer to the
Microsoft Azure documentation for details on exploring metrics on Application Insights.
Deploy Application Insights Using Workspace
Beginning with Azure plugin 4.2.0, Azure recommends deploying Application Insights using
Workspaces and plans to end support for Classic Application Insights from February 2024. It's not
mandatory to migrate Application Insights to workspace while upgrading to Azure plugin 4.2.0.
VM-Series Public Cloud Deployments 382 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on Azure
However, it's recommended, as you will have to migrate Application Insights before February
2024.
Considerations before upgrading to Azure plugin 4.2.0:
• It's recommended that you migrate Application Insights before upgrading to Azure plugin 4.2.0.
• If you don't wish to migrate now, but want to upgrade the Azure plugin, then:
• You may retain the existing deployment and create a new deployment to bring up
workspace Application Insights. You can also leverage the new deployment for auto-scaling
solutions.
• You may undeploy the existing deployment and deploy it again, which would then create
the workspace Application Insights.
• You may redeploy an existing deployment, which will bring up the workspace Application
Insights.
Deploying Application Insights using workspaces requires you to create a Resource group and
associate the workspace with it. It's advised to name your workspace as <resource_group_name>-
workspaces. If you deploy both hub and inbound stack, then you will need to create two
Application Insights, and both of them need to be associated with the same workspace.
VM-Series Public Cloud Deployments 383 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on Azure
VM-Series Public Cloud Deployments 384 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on Azure
Migrate Application Insights Manually
To manually migrate your existing Application Insights, you will need to check if your current
Application Insights are classic or workspace. To verify the deployment method of Application
```
Insights:
```
Navigate to Azure Portal → Resource Group → Application Insights → Properties. If the
Application Insight is classic, the workspace field value will appear empty, and the Migrate to
Workspace-based link will be available.
VM-Series Public Cloud Deployments 385 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on Azure
To migrate the Application Insights, search log analytics workspace on Azure Portal and click
Create to create a log analytics workspace.
VM-Series Public Cloud Deployments 386 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on Azure
Select the subscription and resource group associated with the current deployment. While naming
the workspace, use the convention 'resource_group_name-workspaces'. The workspace can be
associated with hub stack Application Insights and/or inbound stack Application Insights. Ensure
that the region is consistent with the deployment region and click Review + Create.
VM-Series Public Cloud Deployments 387 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on Azure
After the workspace is created successfully, it appears in the resource group.
Click Migrate to Workspace-based link in the Application Insights Property tab. The newly
created workspace appears.
Select the workspace and click Apply.
```
Note: Migration is irreversible and the resource can't be reverted to classic application insights
```
once migrated.
VM-Series Public Cloud Deployments 388 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on Azure
VM-Series Public Cloud Deployments 389 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on Azure
Application Insights Deletion
Delete the Application Insights instance first, and then delete the workspace along with other
resources in the resource group that the deployment is associated with.
Downgrade
Downgrade isn't allowed as you will need to deploy Application Insights using the classic method,
which isn't recommended.
VM-Series Public Cloud Deployments 390 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on Azure
Monitoring on Azure
Where Can I Use This? What Do I Need?
• Microsoft Azure
• Microsoft Azure Stack
• Azure® Marketplace
• Azure China Marketplace
• Azure Government Marketplace
```
VM-Series License (PAYG or BYOL)
```
VM-Series plugin
Panorama
Panorama plugin for Azure
Monitoring on Microsoft® Azure® enables you to dynamically update security policy rules to
consistently enforce Security policy across all assets deployed within your Azure subscription.
To enable this capability, you need to install the Panorama plugin for Azure and enable API
communication between Panorama and your Azure subscriptions. Panorama can then collect
the IP address-to-tag mapping for all your Azure assets and push or distribute Azure resources
information to your Palo Alto Networks firewalls.
As you deploy or terminate virtual machines in the Azure public cloud, you can use the Panorama
plugin for Azure to consistently enforce security policy rules on these workloads.
The Panorama plugin for Azure is built for scale and allows you to monitor up to 100 Azure
subscriptions on the Azure public cloud. With this plugin, you use Panorama as an anchor to poll
```
your subscriptions for tags, and then distribute the metadata (IP address-to-tag mapping) to many
```
firewalls in a device group. Because Panorama communicates with your Azure subscriptions to
retrieve Azure resource information, you’re able to streamline the number of API calls made to
the cloud environment. Although you can define Security policy locally on the firewall, using
Panorama and the plugin centralizes Security policy management, ensuring consistent policies for
hybrid and cloud-native architectures.
See the Panorama plugin version information in the Compatibility Matrix.
Attributes Monitored Using the Panorama Plugin on Azure
When using the Panorama plugin for Azure, Panorama gathers the following set of metadata
elements or attributes on the virtual machines in your Microsoft® Azure® deployment. Panorama
can retrieve a total of 32 tags for each VM, 11 predefined tags, and up to 21 user-defined tags.
The maximum length of a tag can be 127 characters. If a tag is longer than 127
characters, Panorama does not retrieve the tag and register it on the firewalls. Also the
```
tags should not include non-ASCII special characters such as { or ".
```
Up to a maximum of 21 user-defined tags are supported. The user-defined tags are sorted
alphabetically, and the first 21 tags are available for use on Panorama and the firewalls.
The Panorama plugin on Azure version 3.0 or later supports the following tags:
VM-Series Public Cloud Deployments 391 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on Azure
• Load Balancer
```
Load balancer tags for each application gateway and standard load balancer (both public and
```
```
private IP addresses). Each load balancer has predefined tags for resource group, load balancer
```
name and region, and supports up to 21 user-defined tags specific to load balancing.
• Subnet/VNET
Subnet/VNET tags for each subnet and VNET in your subscription. Each subnet and VNET
tag is associated with the full IP CIDR range so you can create policies based on a CIDR
range rather than individual IP addresses. The plugin queries every subnet and VNET in your
subscription and creates tags for them.
The following attributes are monitored in all Panorama plugin for Azure versions:
Attributes Monitored on the Azure
VPC
Example
VM Name azure.vm-name
OS Type azure.os-type
OS Publisher azure.os-publisher
OS Offer azure.os-offer
OS SKU azure.os-sku.
Azure Region azure.region
Resource Group Name azure.resource-group
Network Security Group Name azure.nsg-name
Subscription ID azure.sub-id
Load Balancer azure.slb
App Gateway azure.appgw
Virtual Network Name azure.vnet-name
Subnet Name azure.subnet-name
Service Tag azure.svg-tag
User Defined Tags azure.tag.key.value
Service Tag Monitoring
The Panorama plugin on Azure version 3.0 supports service tags. For example, azure.svg-tag.
VM-Series Public Cloud Deployments 392 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on Azure
Azure Service tags simplify security for Azure virtual machines and Azure virtual networks
because you can restrict network access to just the Azure services you want to use. A service tag
represents a group of IP address prefixes for a particular Azure service. For example, a tag can
represent all storage IP addresses.
```
The plugin makes a daily API call (at 5:00 am UTC) to retrieve all service tags from the Azure
```
Portal, parses the payload to form IP-Service Mappings, and stores the mappings in the plugin
database. The mappings are passed to configd, then on to Panorama. If the API call fails to
return service information, the plugin forms the IP-Service mappings from the contents of
service_tags_public.json. Plugin logs report the origin of the IP-Service mappings, the
daily retrieval, or the JSON file.
The plugin also updates service tags for a new installation of the plugin, commit events, and
monitoring definition addition or deletion.
A sample IP-Service mapping is shown below:
Service Name: AppServiceManagementazure.svc-tag.<service-name>
```
Example:
```
azure.svc-tag.AppServiceManagement.WestUS2
Public IP CIDRs:
13.166.40.0/26
54.179.89.0/18
Set Up the Azure Plugin for Monitoring on Panorama
Where Can I Use This? What Do I Need?
• Microsoft Azure
• Microsoft Azure Stack
• Azure® Marketplace
• Azure China Marketplace
• Azure Government Marketplace
```
VM-Series License (PAYG or BYOL)
```
VM-Series plugin
Panorama
Panorama plugin for Azure
To find all the workloads that your organization has deployed in the Azure cloud, you need to
install the Azure plugin on Panorama and configure Monitoring Definitions that enable Panorama
```
to authenticate to your Azure subscription(s) and retrieve information on the Azure workloads.
```
Panorama retrieves the primary private IP address of Azure resources and the associated tags.
For a list of the metadata elements that Panorama supports, see Attributes Monitored Using the
Panorama Plugin on Azure.
After Panorama fetches the attributes, to push the resource information from Panorama to the
```
firewalls, you must add the firewalls (hardware or VM-Series) as managed devices on Panorama,
```
and group the firewalls into one or more Device Groups. You can then specify which device
groups are part of the Notify Group, which is a configuration element in a Monitoring Definition,
that Panorama uses to register the IP address-to-tag mapping it retrieves from Azure.
Finally, to consistently enforce Security policies across your Azure workloads, you must set up
Dynamic Address Groups and reference them in policy rules that allow or deny traffic to the IP
VM-Series Public Cloud Deployments 393 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on Azure
addresses of the Azure resources. For streamlining your configuration and managing policies and
objects centrally from Panorama, you can define the Dynamic Address Groups and Security policy
rules on Panorama and push them to the firewalls instead of managing the Dynamic Address
Groups and Security policy rules locally on each firewall.
The Azure plugin is for monitoring Azure resources on the Azure public cloud. Azure
Government or Azure China are not supported.
Plan Checklist for Monitoring with the Azure Plugin
• Set up the Active Directory application and a Service Principal to enable API access—For
Panorama to interact with the Azure APIs and collect information on your workloads, you need
to create an Azure Active Directory Service Principal. This Service Principal has the permissions
required to authenticate to the Azure AD and access the resources within your subscription.
To complete this set up, you must have permissions to register an application with your Azure
AD tenant, and assign the application to a role in your subscription. If you don't have the
necessary permissions, ask your Azure AD or subscription administrator to create a Service
Principal with an IAM role of reader or the custom permissions specified in VM-Series on Azure
Service Principal Permissions.
• Make sure that the subscription ID is unique across Service Principals. Panorama allows you
to use only one service principal to monitor an Azure subscription. You can monitor up to
100 Azure subscriptions, with 100 Service principal resources. Starting with Panorama plugin
for Azure version 3.2.0, you can monitor up to 500 Azure subscriptions. Take note of the
processing times described in the table below.
Number of Subscriptions
100 200 300 400 500
System
Resources
Utilization
• CPU:
22%
• Memory:
0.025
MB
• CPU:
23.8%
• Memory:
0.025 MB
• CPU:
31.8%
• Memory:
0.025 MB
• CPU:
28.6%
• Memory:
0.025 MB
• CPU:
39.2%
• Memory:
0.025 MB
Average Time
to Process All
Monitoring
Definitions
1 Hour, 15
Minutes
2 Hours, 30
Minutes
3 Hours, 30
Minutes
4 Hours 5 Hours
Average
Tag Update
Processing
Time
5 minutes 10 minutes 15 minutes 20 minutes 25 minutes
The information in the table above was captured on an instance with 8 vCPUs and
32GB of memory.
VM-Series Public Cloud Deployments 394 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on Azure
• Panorama can push up to 8000 IP address-to tag mappings to the firewalls or virtual system
assigned to a device group. Review the requirements for Panorama and the managed firewalls:
```
• Minimum system requirements (see the Panorama Plugin information in the Compatibility
```
```
Matrix):
```
Panorama virtual appliance or hardware-based Panorama appliance running Panorama
8.1.3 or later, with an active support license and a device management license for managing
firewalls.
Licensed next-generation firewalls running PAN-OS 8.0 or 8.1.
• You must add the firewalls as managed devices on Panorama and create Device Groups so
that you can configure Panorama to notify these groups with the information it retrieves.
Device groups can include VM-Series firewalls or virtual systems on the hardware firewalls.
• The number of tags that the Panorama plugin can retrieve and register is as follows:
On Panorama running 8.1.3 or later managing firewalls running PAN-OS 8.1.3 or lower, the
firewalls or virtual systems included within a device group can have 7000 IP addresses with
10 tags each, or 6500 IP addresses with 15 tags each.
On Panorama 8.1.3 or later managing firewalls running PAN-OS 8.0.x, 2500 IP addresses
with 10 tags each.
• If your Panorama appliances are in a high availability configuration, you must manually
install the same version of the Azure plugin on both Panorama peers.
You configure the Azure plugin on the active Panorama peer only. On commit,
the configuration is synced to the passive Panorama peer. Only the active
Panorama peer polls the Azure subscriptions you have configured for Monitoring.
Install the Azure Plugin
To get started with Monitoring on Azure, you need to download and install the Azure plugin on
Panorama. If you have a Panorama HA configuration, repeat this installation process on each
Panorama peer.
```
If you currently have installed a Panorama plugin, the process of installing (or uninstalling)
```
another plugin requires a Panorama reboot to enable you to commit changes. So, install
additional plugins during a planned maintenance window to allow for a reboot.
If you have a standalone Panorama or two Panorama appliances installed in an HA pair with
multiple plugins installed, plugins might not receive updated IP-tag information if one or more of
the plugins isn't configured. This occurs because Panorama won't forward IP-tag information to
unconfigured plugins. Additionally, this issue can occur if one or more of the Panorama plugins
```
isn't in the Registered or Success state (positive state differs on each plugin). Ensure that your
```
plugins are in the positive state before continuing or executing the commands described below.
If you encounter this issue, there are two workarounds:
• Uninstall the unconfigured plugin or plugins. It's recommended that you do not install a plugin
that you don't plan to configure right away
VM-Series Public Cloud Deployments 395 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on Azure
• You can use the following commands to work around this issue. Execute the following
command for each unconfigured plugin on each Panorama instance to prevent Panorama from
waiting to send updates. If you don't, your firewalls may lose some IP-tag information.
request plugins dau plugin-name <plugin-name> unblock-device-push yes
You can cancel this command by executing:
request plugins dau plugin-name <plugin-name> unblock-device-push no
The commands described are not persistent across reboots and must be used again for any
subsequent reboots. For Panorama in HA pair, the commands must be executed on each
Panorama.
STEP 1 | Log in to the Panorama web interface, select Panorama > Plugins and click Check Now to
get the list of available plugins.
STEP 2 | Select Download and Install the plugin.
After you successfully install, Panorama refreshes and the Azure plugin displays on the
Panorama tab.
STEP 3 | Restart Panorama.
Select Panorama > Setup > Operations > Reboot Panorama
Configure the Azure Plugin for Monitoring
To begin monitoring the resources in your Azure public cloud deployment, after you Install
the Azure Plugin you must create a Monitoring Definition. This definition specifies the Service
Principal that is authorized to access the resources within the Azure subscription you want to
monitor and the Notify Group that includes the firewalls to which Panorama should push all
the IP address-to-tag mappings it retrieves. To enforce policy, you must then create Dynamic
Address Groups and reference them in Security policy. The Dynamic Address Groups enable you
to filter the tags you want to match on, so that the firewall can get the primary private IP address
registered for the tags, and then allow or deny access to traffic to and from the workloads based
on the policy rules you define.
STEP 1 | Log in to the Panorama web interface.
VM-Series Public Cloud Deployments 396 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on Azure
STEP 2 | Set up the following objects for enabling Monitoring on Azure.
Add a Service Principal.
The Service Principal is the service account that you created on the Azure portal. This
account is attached to the Azure AD and has limited permissions to access and monitor the
resources in your Azure subscription.
1. Select Panorama > Plugins > Azure > Setup > Service Principal > Add.
While configuring the monitoring definition, ensure that you attach the parent
DG to the plugin notify-group and that all children DGs are unattached from the
notify group.
To ensure that the DAU propagates all IP tags from parent DG to children DGs
that are connected to the firewall, run the command debug dau settings device-
group recursive yes on Panorama CLI
2. Enter a Name and optionally a Description to identify the service account.
3. Enter the Subscription ID for the Azure subscription you want to monitor. You must log
in to your Azure portal to get this subscription ID.
4. Enter the Client Secret and reenter it to confirm.
5. Enter the Tenant ID. The tenant ID is the Directory ID you saved when you set up the
Active Directory application.
6. Click Validate to verify that the keys and IDs you entered are valid , and Panorama can
communicate with the Azure subscription using the API.
Add a notify group.
1. Select Panorama > Plugins > Azure > Setup > Notify Groups > Add.
VM-Series Public Cloud Deployments 397 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on Azure
2. Enter a Name and optionally a Description to identify the group of firewalls to which
Panorama pushes the information it retrieves.
3. Select the Device Groups, which are a group of firewalls or virtual systems, to which
```
Panorama will push the information (IP address-to-tag mapping) it retrieves from your
```
Azure subscriptions. The firewalls use the update to determine the most current list of
members that constitute Dynamic Address Groups referenced in policy.
4. Select the option Select All Tags or Custom Tags.
This enables you to specify the labels that you prefer and generate required tags. You
must enter the key of the user tag to configure the user tags.
For example:
```
If your virtual machine (VM) on Azure cloud is tagged as UserID with a value
```
SampleValue, enter UserID under the user tags. You can then see that
azure.tag.UserID.SampleValue is populated as the user tag.
You must think through your Device Groups carefully because a Monitoring
Definition can include only one notify group, make sure to select all the relevant
Device Groups within your notify group. If you want to deregister the tags that
Panorama has pushed to a firewall included in a notify group, you must delete
the Monitoring Definition.
To register tags to all virtual systems on a firewall enabled for multiple virtual
systems, you must add each virtual system to a separate device group on
Panorama and assign the device groups to the notify group. Panorama will
register tags to only one virtual system, if you assign all the virtual systems to
one device group.
5. Click OK.
6. Verify that monitoring is enabled on the plugin. This setting must be enabled for
Panorama to communicate with the Azure public cloud for Monitoring.
The check box for Enable Monitoring is on Panorama > Plugins > Azure > Setup >
General.
VM-Series Public Cloud Deployments 398 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on Azure
STEP 3 | Create a Monitoring Definition.
When you add a new Monitoring definition, it is enabled by default.
• Select Panorama > Plugins > Azure > Monitoring Definition, to Add a new definition.
• Enter a Name and optionally a Description to identify the Azure subscription for which you
use this definition.
• Select the Service Principal and Notify Group.
Panorama requires the keys and IDs that you specify in the Service Principal configuration
to generate an Azure Bearer Token, which is used in the header of the API call to collect
information on your workloads.
• The Panorama plugin for Azure 5.1.0 supports one service principal for multiple
monitoring definitions.
• The Panorama plugin for Azure 5.0.0 or below version, does not support one
service principal for multiple monitoring definitions.
• Select the Azure Regions
VM-Series Public Cloud Deployments 399 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on Azure
.
No two monitoring definitions can have exactly the same Service Principal and
Region configured. The plugin will fail the commit operation for monitoring
definitions that have the same Service Principal and Region configured.
VM-Series Public Cloud Deployments 400 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on Azure
STEP 4 | Commit the changes on Panorama.
Verify that the status for the Monitoring Definition displays as Success. If it fails, verify that
you entered the Azure Subscription ID accurately and provided the correct keys and IDs for
the Service Principal.
You can select a monitoring definition and click Dashboard to view the tag details of a
monitoring definition.
The location filter on the Monitoring Definition Detailed Status dialogue box filters the
dashboard details by location.
Click more to view the IP address of the tag and then go to Associated tags to view all tags
associated with this IP address.
VM-Series Public Cloud Deployments 401 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on Azure
VM-Series Public Cloud Deployments 402 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on Azure
STEP 5 | Verify that you can view the information on Panorama, and define the match criteria for
Dynamic Address Groups.
Some browser extensions may block API calls between Panorama and Azure, which
prevents Panorama from receiving match criteria. If Panorama displays no match
criteria and you're using browser extensions, disable the extensions and Synchronize
Dynamic Objects to populate the tags available to Panorama.
On HA failover, the newly active Panorama attempts to reconnect to the Azure cloud
and retrieve tags for all monitoring definitions. If there is an error with reconnecting
even one monitoring definition, Panorama generates a system log message
```
Unable to process subscriptions after HA switch-over;
```
user-intervention required.
When you see this error, you must log in to Panorama and fix the issue, for example
remove an invalid subscription or provide valid credentials, and commit your changes
to enable Panorama to reconnect and retrieve the tags for all monitoring definitions.
Even when Panorama is disconnected from the Azure cloud, the firewalls have the
list of all tags that had been retrieved before failover, and can continue to enforce
policy on that list of IP addresses. Panorama removes all tags associated with the
subscription only when you delete a monitoring definition. As a best practice, to
monitor this issue, configure action-oriented log forwarding to an HTTPS destination
from Panorama so that you can take immediate action.
VM-Series Public Cloud Deployments 403 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on Azure
Azure Health Monitoring
PA-VMs on Azure are susceptible to unrecoverable outcomes due to backend maintenance
events outside of the firewalls' control. These silent maintenance events, such as hotplug
```
of network interfaces (“hotplug events”), live host migrations, and updates to NIC drivers,
```
hypervisors, or networking, can lead to unrecoverable firewall states. The Azure health monitoring
daemon focuses on performing checks, notifying customers about these occurrences, and offering
remediation through graceful failover.
Azure health monitoring daemon detects the following events and states and performs a default
remediation or logging action in accordance to your setting of the auto-remediation bootstrap
value.
Azure health monitoring daemon checks for the following:
• Events:
• Events of type Freeze on Azure scheduled event service.
• Hotplug events characterized by rapid de-association and re-association of the NIC on any of
the data plane interfaces on the Azure host.
• States:
• Any configured dataplane interfaces are down
• System runlevel running state is false
• Any dataplane interface did not receive DHCP served IP
• Management link is down
• License status is unlicensed
• Thermite certificate is absent
• No panorama connection or failed to register
• Accelerated networking is not enabled
How Does the Azure Health Monitoring Function?
The Azure health monitoring daemon periodically runs checkers to determine the status of the
```
VM-Series firewall and marks the health checker status (pass, fail, or unknown) in the log. Critical
```
failures generate syslog entries. In the event of an unhealthy instance, the Azure scheduled event
triggers any of the following remediation methods:
• Auto-remediate for all: Easier solution, results in a remediation action for only scheduled
events with event type freeze, detected at runtime.
• DIY using syslog: You can decide on remediation by using syslog events and adding your own
workflows to remediate the event.
VM-Series Public Cloud Deployments 404 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on Azure
Remediation
```
Prerequisite:
```
VM-Series Public Cloud Deployments 405 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on Azure
To enable auto-remediation, configure custom data at the time of deployment with the following
key-value pair:
health-auto-remedy=true
Actions summary for events and states for different auto-remediation settings:
```
Bootstrap value (custom data) Freeze event is detected
```
```
health-auto-remedy=true Active → Passive failover (how HA pairs)
```
Healthprobe failure for load balancer fronted
FWs
health-auto-remedy=false
Or bootstrap parameter is absent
FW logs an event in syslogs
Remediation is currently available on high availability and load balancer based Azure scheduled
```
events:
```
HA Pair Architectures:
If you have an active-passive system and if your active system detects a scheduled event is
posted, then the health monitor proactively fails over the active to the passive. A freeze event is
detected and a suspend followed by a functional command is triggered on the firewall where the
scheduled event is detected. This shifts the firewall from active to passive.
Palo Alto Network suggests that you have your HA pair set up across different availability
zones or regions to avoid the HA paired firewalls being impacted by the same event.
Load Balancer Based Architectures:
In case of a freeze event, the health probe is failed. The health check packets are based on a
fixed source IP which can be used to drop health check packets. The traffic managed by the load
balancer will be stopped and the load balancer will then have to re-balance the traffic. After the
event is cleared, the heath probe is re-enabled and the backend instance will show up as healthy
again.
VM-Series Public Cloud Deployments 406 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on Azure
Logging summary for events and states:
Hotplug events always result in an event in syslogs. Detection of any of the states listed above
will only result in an event firewall logs to vmhost_health.log. If accelerated networking is not
enabled, it will result in a syslog event.
VM-Series Public Cloud Deployments 407 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on Azure
Set up Active/Passive HA on Azure
Where Can I Use This? What Do I Need?
• Microsoft Azure
• Microsoft Azure Stack
• Azure® Marketplace
• Azure China Marketplace
• Azure Government Marketplace
```
VM-Series License (PAYG or BYOL)
```
VM-Series plugin
Panorama
Panorama plugin for Azure
```
You can configure a pair of VM-Series firewalls on Azure in an active/passive high availability (HA)
```
configuration. For HA on Azure, you must deploy both firewall HA peers within the same Azure
Resource Group and you must install the same version of the VM-Series Plugin on both HA peers.
```
• Set up Active/Passive HA on Azure (North-South & East-West Traffic)—If you have an
```
internet-facing application deployed on your Azure infrastructure, and you need to secure
north-south traffic, you require a floating IP address to secure traffic on failover. This floating
IP address, which enables external connectivity, is always attached to the active peer. On
failover, the process of detaching the IP address and reattaching it to the now active peer can
take a few minutes.
```
• Set up Active/Passive HA on Azure (East-West Traffic Only)—If your application access and
```
security requirements are contained within the Azure infrastructure and you need to secure
east-west traffic only, you don't need a floating IP address. Instead, the HA implementation
automatically reconfigures the UDRs in the Azure routing tables to provide a faster failover
time.
• You can deploy the VM-Series firewalls in Active/Passive HA mode across different
```
Availability Zones (AZs) on Azure. This deployment enhances availability and resilience
```
by placing the Active and Passive firewalls in separate AZs.
• All VM-Series firewall interfaces must be assigned an IPv4 address when deployed in a
public cloud environment. IPv6 addresses are not supported.
To enable HA on the VM-Series firewall on Azure, you must create an Azure Active Directory
application and Service Principal that includes the permissions listed in the table below.
Azure HA
Type
Permissions Role Scope
Secondary
IP Move
HA
"Microsoft.Authorization/
*/read""Microsoft.Compute/
virtualMachines/
read""Microsoft.Network/
networkInterfaces/
*""Microsoft.Network/
networkSecurityGroups/
• Virtual network in which
the VMs are deployed
• Two VM-Series firewalls
• NICs of both VM-Series
firewalls
• Network Security Group
VM-Series Public Cloud Deployments 408 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on Azure
Azure HA
Type
Permissions Role Scope
*""Microsoft.Network/
virtualNetworks/join/
action""Microsoft.Network/
virtualNetworks/subnets/join/action"
The following permissions are required only if
you have assigned a public IP address to any of
your data interfaces. Standard SKU interface is
recommended.
"Microsoft.Network/
publicIPAddresses/join/
action""Microsoft.Network/
publicIPAddresses/
read""Microsoft.Network/
publicIPAddresses/write"
• Public IP addresses of
the VM-Series firewalls
UDR HA "Microsoft.Authorization/
*/read""Microsoft.Compute/
virtualMachines/
read""Microsift.Network/routeTables/
*"
• Two VM-Series firewalls
• NICs of both VM-Series
firewalls
• Route tables associated
with UDR
Secondary
IP Move
and UDR
"Microsoft.Authorization/
*/read""Microsoft.Compute/
virtualMachines/
read""Microsoft.Network/
networkInterfaces/
*""Microsoft.Network/
networkSecurityGroups/
*""Microsoft.Network/
routeTables/*""Microsift.Network/
virtualNetworks/join/
action""Microsoft.Network/
virtualNetworks/subnets/join/action"
The following permissions are required only if
you have assigned a public IP address to any of
your data interfaces. Standard SKU interface is
recommended.
"Microsoft.Network/
publicIPAddresses/join/
action""Microsoft.Network/
publicIPAddresses/
read""Microsoft.Network/
publicIPAddresses/write"
• Virtual network in which
the VMs are deployed
• Two VM-Series firewalls
• NICs of both VM-Series
firewalls
• Network Security Group
• Public IP addresses of
the VM-Series firewalls
• Route tables associated
with UDR
VM-Series Public Cloud Deployments 409 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on Azure
```
Set up Active/Passive HA on Azure (North-South & East-West
```
```
Traffic)
```
If you want to secure north-south traffic to your applications in your Azure infrastructure, use this
workflow with floating IP addresses that can quickly move from one peer to the other. Because
you can't move the IP address associated with the primary interface of the firewall on Azure, you
need to assign a secondary IP address that can function as a floating IP address. When the active
firewall goes down, the floating IP address moves from the active to the passive firewall so that
the passive firewall can seamlessly secure traffic as soon as it becomes the active peer. In addition
```
to the floating IP address, the HA peers also need HA links—a control link (HA1) and a data link
```
```
(HA2)—to synchronize data and maintain state information.
```
For North-South deployments, failover reassigns the Floating or Secondary IP to the newly
active firewall. Azure platform constraints prevent preserving active sessions, requiring the
clients to re-establish connections.
Set up the Firewalls for Enabling HA
Gather the following details for configuring HA on the VM-Series firewalls on Azure.
Set up the Active Directory application and a Service Principal to enable programmatic API
access.
• For the firewall to interact with the Azure APIs, you need to create an Azure Active
Directory Service Principal. This Service Principle has the permissions required to
authenticate to the Azure AD and access the resources within your subscription. To
VM-Series Public Cloud Deployments 410 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on Azure
complete this set up, you must have permission to register an application with your Azure
AD tenant, and assign the application to a role in your subscription. If you don't have the
necessary permissions, ask your Azure AD or subscription administrator to create a Service
VM-Series Public Cloud Deployments 411 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on Azure
Principal. See the table above for the required permissions. Copy the following details for
use later in this workflow:
```
• Client ID—The Application ID associated with the Active Directory (On the Azure portal,
```
click Home > Azure Active Directory > App registrations, select your application and
```
copy the ID).
```
```
• Tenant ID—The Directory ID associated with the Active Directory (On the Azure portal,
```
click Home > Azure Active Directory > Properties > Directory ID, select the application
```
and copy the ID).
```
• Azure Subscription ID—The Azure subscription in which you have deployed the firewalls.
You must Connect Before Logon to your Azure portal to get this subscription ID.
• Resource Group Name— The resource group name in which you have deployed the
firewalls that you want to configure as HA peers. Both firewalls must be in the same
resource group.
VM-Series Public Cloud Deployments 412 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on Azure
```
• Secret Key—The authentication key associated with the Active Directory application (On
```
the Azure portal, click Home > Azure Active Directory > Certificates & secrets, copy the
Value under Client secrets. If you don't have a Secret Key, create one first, then copy
VM-Series Public Cloud Deployments 413 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on Azure
```
the value). To log in as the application, you must provide both the key value and the
```
Application ID.
VM-Series Public Cloud Deployments 414 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on Azure
VM-Series Public Cloud Deployments 415 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on Azure
Know where to get the templates you need to deploy the VM-Series firewalls within the same
Azure resource group.
For an HA configuration, both HA peers must belong to the same Azure Resource Group. If
you deploy the first instance of the firewall from the Azure Marketplace, and must use your
custom ARM template or the Palo Alto Networks sample GitHub template for deploying the
second instance of the firewall into the existing resource group. The reason you need a custom
template or the Palo Alto Networks sample template is because Azure does not support the
ability to deploy the firewall into a Resource Group that isn't empty.
Copy the deployment information for the first firewall instance. For example:
Match the VM Name of VM-Series firewall as shown in the screenshot above with
the Hostname on the firewall web interface. Add the same name on Device > Setup >
Management, because the hostname of the firewall is used to trigger failover.
VM-Series Public Cloud Deployments 416 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on Azure
Plan the network interface configuration on the VM-Series firewalls on Azure.
To set up HA, you must deploy both HA peers within the same Azure resource group and
both firewalls must have the same number of network interfaces. A minimum of four network
interfaces is required on each HA peer:
```
• Management interface (eth0)—Private and public IP address associated with the primary
```
interface. The public IP address enables access to the firewall web interface and SSH
access.
You can use the private IP interface on the management interface as the HA1 peer IP
address for the control link communication between the active/passive HA peers. If you
want a dedicated HA1 interface, you must attach an additional network interface on each
firewall, and this means that you need five interfaces on each firewall.
```
• Untrust interface (eth1/1)—Primary private IP address with /32 netmask, and secondary IP
```
```
configuration with both a private IP address (any netmask) and a public IP address.
```
On failover, when the passive peer transitions to the active state, the public IP address
associated with the secondary IP configuration is detached from the previously active peer
and attached to the now active HA peer.
```
• Trust interface (eth1/2)—Primary and secondary private IP addresses. On failover, when
```
the passive peer transitions to the active state, the secondary private IP address is detached
from the previously active peer and is attached to the now active HA peer.
```
• HA2 (eth 1/3)—Primary private IP address. The HA2 interface is the data link that the HA
```
peers use for synchronizing sessions, forwarding tables, IPSec security associations and ARP
tables.
Interface Active Firewall
Peer
Passive
Firewall Peer
Description
Trust Secondary IP
address
— The trust interface of the active peer requires
a secondary IP configuration that can float to
the other peer on failover. This secondary IP
configuration on the trust interface must be a
private IP address with the netmask of the servers
that it secures. On failover, the VM-Series plugin
calls the Azure API to detach this secondary
private IP address from the active peer and attach
it to the passive peer. Attaching this IP address to
the now active peer ensures that the firewall can
receive traffic on the floating IP on the untrust
interface and send it through to the floating IP on
the trust interface and on to the workloads.
Untrust Secondary IP
address
— The untrust interface of the firewall requires a
secondary IP configuration that includes a static
private IP address with a netmask for the untrust
subnet, and a public IP address for accessing the
backend servers or workloads over the internet.
On failover, the VM-Series plugin calls the Azure
API to detach the secondary IP configuration
VM-Series Public Cloud Deployments 417 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on Azure
Interface Active Firewall
Peer
Passive
Firewall Peer
Description
from the active peer and attach it to the passive
peer before it transitions to the active state. This
process of floating the secondary IP configuration,
enables the now active firewall to continue
processing inbound traffic that is destined to the
workloads.
HA2 Add a NIC
to the
firewall from
the Azure
management
console.
Add a NIC
to the
firewall from
the Azure
management
console.
On the active and passive peers, add a dedicated
HA2 link to enable session synchronization.
The default interface for HA1 is the management
interface, and you can opt to use the management
interface instead of adding an additional interface
to the firewall. For enabling data flow over the
HA2 link, you need to add an additional network
interface on the Azure portal and configure the
interface for HA2 on the firewall.
Configure Active/Passive HA on the VM-Series Firewall on Azure
In this workflow, you deploy the first instance of the VM-Series firewall using the VM-Series
firewall solution template in the Azure marketplace, and the second instance of the firewall using
the sample GitHub template.
```
The authentication key (client secret) associated with the Active Directory application
```
required for setting up the VM-Series firewall in an HA configuration, is encrypted with
VM-Series plugin version 1.0.4 on the firewall and on Panorama. Because the key is
encrypted in VM-Series plugin version 1.0.4, you must install the same version of the
plugin on Panorama and the managed VM-Series firewalls to centrally manage the
firewalls from Panorama.
You can now configure up to four IP addresses per SD-WAN interface, to achieve HA
failover in active/passive configurations of your Azure public cloud environment. You
can achieve this by configuring a second floating IP address on the SD-WAN interface.
The floating IP on the SD-WAN interface of the external zone must match with that of
the internal zone. This feature is supported on PAN-OS 11.1.0 and above and on IPv4
addresses only.
VM-Series Public Cloud Deployments 418 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on Azure
STEP 1 | Deploy the VM-Series firewall using a solution template and set up the network interfaces
for HA.
1. Add a secondary IP configuration to the untrust interface of the firewall.
```
You must attach the secondary IP configuration—with a private IP address (any netmask)
```
and a public IP address—to the firewall that will be designated as the active peer. The
secondary IP configuration always stays with the active HA peer, and moves from one peer
to the other when a failover occurs.
In this workflow, this firewall will be designated as the active peer. The active HA peer
has a lower numerical value for device priority that you configure as a part of the HA
VM-Series Public Cloud Deployments 419 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on Azure
configuration on the firewall, and this value indicates a preference for which firewall
assumes the role of the active peer.
2. Add a secondary IP configuration to the trust interface of the firewall.
The secondary IP configuration for the trust interface requires a static private IP address
only. This IP address moves from the active firewall to the passive firewall on failover so
VM-Series Public Cloud Deployments 420 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on Azure
that traffic flows through from the untrust to the trust interface and to the destination
subnets that the firewall secures.
3. Attach a network interface for the HA2 communication between the firewall HA peers.
1. Add a subnet within the virtual network.
2. Create and attach a network interface to the firewall.
4. Set up your route table on Azure.
Your next hop should point to the floating IP address as shown here:
VM-Series Public Cloud Deployments 421 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on Azure
VM-Series Public Cloud Deployments 422 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on Azure
STEP 2 | Configure the interfaces on the firewall.
Complete these steps on the active HA peer, before you deploy and set up the passive HA
peer.
1. Log in to the firewall web interface.
2. Configure ethernet 1/1 as the untrust interface and ethernet 1/2 as the trust interface.
Select Network > Interfaces and configure as follows:
VM-Series Public Cloud Deployments 423 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on Azure
3. Configure ethernet 1/3 as the HA interface.
To set up the HA2 link, select the interface and set Interface Type to HA. Set link speed
and duplex to auto.
VM-Series Public Cloud Deployments 424 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on Azure
STEP 3 | Configure the VM-Series plugin to authenticate to the Azure resource group in which you
have deployed the firewall.
Set up the Azure HA configuration on the VM-Series plugin.
To encrypt the client secret, use the VM-Series plugin version 1.0.4 or later. If using Panorama
to manage your firewalls, you must install the VM-Series plugin version 1.0.4 or later.
1. Select Device > VM-Series to enable programmatic access between the firewall plugin and
the Azure resources.
2. Enter the Client ID. The client ID is the Application ID associated with your Azure Active
Directory application.
3. Enter the Client Secret and reenter it to confirm.
4. Enter the Tenant ID. The tenant ID is the Directory ID you saved when you set up the
Active Directory application.
5. Enter the Subscription ID for the Azure subscription you want to monitor.
6. Enter the Resource Group name.
7. (For Azure Stack deployments only) Enter the Resource Mgr Endpoint URL. This field is
mandatory ONLY for Azure Stack deployments. Don't enter a value for this field if you're
```
using a regular Azure Cloud deployment; HA failover won't succeed if you specify the
```
Resource Mgr Endpoint URL for a regular Azure Cloud deployment.
This field is available in VM-Series plugin 2.1.2 and later.
8. Click Validate to verify that the keys and IDs you entered are valid, and that VM-Series
plugin can successfully communicate with the Azure resources using the API.
VM-Series Public Cloud Deployments 425 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on Azure
STEP 4 | Enable HA.
1. Select Device > Setup > HA.
2. Enter Peer HA1 IP address as the private IP address of the passive peer.
3. (Optional) Edit the Control Link (HA1). If you don't plan to use the management interface
```
for the control link and have added an additional interface (for example ethernet 1/4), edit
```
this section to select the interface to use for HA1 communication.
4. Edit the Data Link (HA2) to use Port ethernet 1/3 and add the IP address of this peer
and the Gateway IP address for the subnet. In the transport mode, the UPD is the only
supported transport mode in Azure environments.
STEP 5 | Commit the changes.
STEP 6 | Set up the passive HA peer within the same Azure resource group.
1. Deploy the second instance of the firewall.
• Download the custom template and parameters file from GitHub.
• Log in to the Azure Portal.
• Search for custom template and select Deploy from a custom template.
• Select Build your own template in the editor > Load file.
• Select the azuredeploy.json that you downloaded earlier, and Save.
• Complete the inputs, agree to the terms and Purchase.
Make sure to match the following inputs to that of the firewall instance you have
already deployed— Azure subscription, name of the resource group, location of
the resource group, name of the existing VNet into which you want to deploy the
VM-Series Public Cloud Deployments 426 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on Azure
firewall, VNet CIDR, subnet names, subnet CIDRs, and start the IP address for the
management, trust, and untrust subnets.
2. Repeat Step 1and Step 2 to set up the interfaces and configure the firewall as the
passive HA peer.
3. Skip Step 3 and complete Enable HA (Step 5). In Step 4 modify the IP addresses as
appropriate for this passive HA peer.
STEP 7 | After you finish configuring both firewalls, verify that the firewalls are paired in active/
passive HA.
1. Access the Dashboard on both firewalls, and view the high availability widget.
2. On the active firewall, click the Sync to peer link.
3. Confirm that the firewalls are paired and synced, as shown as follows:
• On the passive firewall: the state of the local firewall should display passive and the
Running Config should show as synchronized.
• On the active firewall: The state of the local firewall should display active and the
Running Config should show as synchronized.
4. On the passive peer, verify that the VM-Series plugin configuration is now synced.
Select Device > VM-Series and validate that you can view the Azure HA configuration that
you had omitted configuring on the passive peer.
```
Set up Active/Passive HA on Azure (East-West Traffic Only)
```
If your resources are all deployed within the Azure infrastructure and you don't need to enforce
security for north-south traffic to the Azure VNet, you can deploy a pair of VM-Series firewalls
```
in an active/passive high availability (HA) configuration without floating IP addresses. The HA
```
```
peers will still need HA links—a control link (HA1) and a data link (HA2)—to synchronize data and
```
maintain state information.
You must have the VM-Series plugin version 1.0.9 or later, and you must deploy both firewall HA
peers within the same Azure resource group.
VM-Series Public Cloud Deployments 427 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on Azure
Set up the Firewalls for Enabling HA
Gather the following details for configuring HA on the VM-Series firewalls on Azure.
Set up the Active Directory application and a Service Principal to enable programmatic API
access.
• For the firewall to interact with the Azure APIs, you need to create an Azure Active
Directory Service Principal. This Service Principle has the permissions required to
authenticate to the Azure AD and access the resources within your subscription. To
complete this set up, you must have permissions to register an application with your Azure
AD tenant, and assign the application to a role in your subscription. If you don't have the
necessary permissions, ask your Azure AD or subscription administrator to create a Service
VM-Series Public Cloud Deployments 428 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on Azure
Principal. See the table above for the required permissions. Copy the following details for
use later in this workflow:
```
• Client ID—The Application ID associated with the Active Directory (On the Azure portal,
```
click Home > Azure Active Directory > App registrations, select your application and
```
copy the ID).
```
```
• Tenant ID—The Directory ID associated with the Active Directory (On the Azure portal,
```
click Home > Azure Active Directory > Properties > Directory ID, select the application
```
and copy the ID).
```
• Azure Subscription ID—The Azure subscription in which you have deployed the firewalls.
You must log in to your Azure portal to get this subscription ID.
• Resource Group Name— The resource group name in which you have deployed the
firewalls that you want to configure as HA peers. Both firewalls must be in the same
resource group.
VM-Series Public Cloud Deployments 429 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on Azure
```
• Secret Key—The authentication key associated with the Active Directory application (On
```
the Azure portal, click Home > Azure Active Directory > Certificates & secrets, copy the
Value under Client secrets. If you don't have a Secret Key, create one first, then copy
VM-Series Public Cloud Deployments 430 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on Azure
```
the value). To log in as the application, you must provide both the key value and the
```
Application ID.
VM-Series Public Cloud Deployments 431 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on Azure
VM-Series Public Cloud Deployments 432 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on Azure
Know where to get the templates you need to deploy the VM-Series firewalls within the same
Azure resource group.
For an HA configuration, both HA peers must belong to the same Azure resource group. If
you deploy the first instance of the firewall from the Azure Marketplace, and must use your
custom ARM template or the Palo Alto Networks sample GitHub template for deploying the
second instance of the firewall into the existing resource group. The reason you need a custom
template or the Palo Alto Networks sample template is because Azure does not support the
ability to deploy the firewall into an resource group that isn't empty.
Copy the deployment information for the first firewall instance. For example:
Match the VM Name of VM-Series firewall as shown in the screenshot above with
the Hostname on the firewall web interface. Add the same name on Device > Setup >
Management, because the hostname of the firewall is used to trigger failover.
VM-Series Public Cloud Deployments 433 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on Azure
Plan the network interface configuration on the VM-Series firewalls on Azure.
To set up HA, you must deploy both HA peers within the same Azure resource group and
both firewalls must have the same number of network interfaces. A minimum of four network
interfaces is required on each HA peer:
```
• Management interface (eth0)—Private and public IP address associated with the primary
```
interface. The public IP address enables access to the firewall web interface and SSH
access.
You can use the private IP interface on the management interface as the HA1 peer IP
address for the control link communication between the active/passive HA peers. If you
want a dedicated HA1 interface, you must attach an additional network interface on each
firewall, and this means that you need five interfaces on each firewall.
```
• Untrust interface (eth1/1)—Primary private IP address with /32 netmask.
```
On failover, when the passive peer transitions to the active state, the VM-Series plugin
automatically sends traffic to the primary private IP address of the passive peer. The Azure
UDRs enable the traffic flow.
```
• Trust interface (eth1/2)—Primary private IP address. On failover, when the passive peer
```
transitions to the active state, the VM-Series plugin automatically sends traffic to the
primary private IP address of the passive peer.
```
• HA2 (eth 1/3)—Primary private IP address. The HA2 interface is the data link that the HA
```
peers use for synchronizing sessions, forwarding tables, IPSec security associations and ARP
tables.
Interface Active Firewall Peer Passive Firewall Peer Description
HA2 Add a NIC to the
firewall from the
Azure management
console.
Add a NIC to the
firewall from the
Azure management
console.
On the active and
passive peers, add a
dedicated HA2 link
to enable session
synchronization.
The default interface
for HA1 is the
management interface,
and you can opt to
use the management
interface instead of
adding an additional
interface to the
firewall. For enabling
data flow over the
HA2 link, you need
to add an additional
network interface
on the Azure portal
and configure the
interface for HA2 on
the firewall.
VM-Series Public Cloud Deployments 434 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on Azure
Configure Active/Passive HA on the VM-Series Firewall on Azure
In this workflow, you deploy the first instance of the VM-Series firewall using the VM-Series
firewall solution template in the Azure marketplace, and the second instance of the firewall using
the sample GitHub template.
```
The authentication key (client secret) associated with the Active Directory application
```
required for setting up the VM-Series firewall in an HA configuration, is encrypted with
VM-Series plugin version 1.0.9 on the firewall and on Panorama. Because the key is
encrypted in VM-Series plugin version 1.0.9, you must install the same version of the
plugin on Panorama and the managed VM-Series firewalls to centrally manage the
firewalls from Panorama.
STEP 1 | Deploy the VM-Series firewall using a solution template and set up the network interfaces
for HA.
For securing east-west traffic within an Azure VNet, you only need a primary IP address for
the trust and untrust firewall interfaces. When a failover occurs, the UDR changes and the
route points to the primary IP address of the peer that transitions to the active state.
1. Add a Primary IP configuration to the trust interface of the active firewall peer.
In this workflow, this firewall will be designated as the active peer. The active HA peer
has a lower numerical value for device priority that you configure as a part of the HA
VM-Series Public Cloud Deployments 435 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on Azure
configuration on the firewall, and this value indicates a preference for which firewall
assumes the role of the active peer.
2. Add a primary IP configuration to the untrust interface of the active firewall peer.
3. Attach a network interface for the HA2 communication between the firewall HA peers.
VM-Series Public Cloud Deployments 436 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on Azure
1. Add a subnet within the virtual network.
2. Create and attach a network interface to the firewall.
4. Set up your route table on Azure.
Create a route to the Next hop of primary IP address of the trust and untrust interfaces of
the active firewall peer.
After failover, the next hop for the database server to frontend server route will change
from 10.9.2.5 to 10.9.2.4. Similarly, the next hop of frontend server to database server
route will change from 10.9.1.5 to 10.9.1.4.
VM-Series Public Cloud Deployments 437 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on Azure
STEP 2 | Configure the interfaces on the firewall.
Complete these steps on the active HA peer, before you deploy and set up the passive HA
peer.
1. Log in to the firewall web interface.
2. Configure ethernet 1/1 as the untrust interface and ethernet 1/2 as the untrust
interface.
Select Network > Interfaces and configure as follows:
VM-Series Public Cloud Deployments 438 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on Azure
3. Configure ethernet 1/3 as the HA interface.
To set up the HA2 link, select the interface and set Interface Type to HA. Set link speed
and duplex to auto.
VM-Series Public Cloud Deployments 439 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on Azure
STEP 3 | Configure the VM-Series plugin to authenticate to the Azure resource group in which you
have deployed the firewall.
Set up the Azure HA configuration on the VM-Series plugin.
To encrypt the client secret, use the VM-Series plugin version 1.0.4 or later. If using Panorama
to manage your firewalls, you must install the VM-Series plugin version 1.0.4 or later.
1. Select Device > VM-Series to enable programmatic access between the firewall plugin and
the Azure resources.
2. Enter the Client ID. The client ID is the Application ID associated with your Azure Active
Directory application.
3. Enter the Client Secret and reenter it to confirm.
4. Enter the Tenant ID. The tenant ID is the Directory ID you saved when you set up the
Active Directory application.
5. Enter the Subscription ID for the Azure subscription you want to monitor.
6. Enter the Resource Group name.
7. (For Azure Stack deployments only) Enter the Resource Mgr Endpoint URL.
This field is available in VM-Series plugin 2.1.2 and later.
8. Click Validate to verify that the keys and IDs you entered are valid, and that VM-Series
plugin can successfully communicate with the Azure resources using the API.
VM-Series Public Cloud Deployments 440 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on Azure
STEP 4 | Enable HA.
1. Select Device > Setup > HA.
2. Enter Peer HA1 IP address as the private IP address of the passive peer.
3. (Optional) Edit the Control Link (HA1). If you don't plan to use the management interface
```
for the control link and have added an additional interface (for example ethernet 1/4), edit
```
this section to select the interface to use for HA1 communication.
4. Edit the Data Link (HA2) to use Port ethernet 1/3 and add the IP address of this peer and
the Gateway IP address for the subnet.
STEP 5 | Commit the changes.
STEP 6 | Set up the passive HA peer within the same Azure resource group.
1. Deploy the second instance of the firewall.
• Download the custom template and parameters file from GitHub.
• Log in to the Azure Portal.
• Search for custom template and select Deploy from a custom template.
• Select Build your own template in the editor > Load file.
• Select the azuredeploy.json that you downloaded earlier, and Save.
• Complete the inputs, agree to the terms and Purchase.
Make sure to match the following inputs to that of the firewall instance you have
already deployed— Azure subscription, name of the resource group, location of
the resource group, name of the existing VNet into which you want to deploy the
VM-Series Public Cloud Deployments 441 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on Azure
firewall, VNet CIDR, subnet names, subnet CIDRs, and start the IP address for the
management, trust and untrust subnets.
2. Repeat Step 1and Step 2 to set up the interfaces and configure the firewall as the
passive HA peer.
3. Skip Step 3 and complete Enable HA (Step 5). In Step 4 modify the IP addresses as
appropriate for this passive HA peer.
STEP 7 | After you finish configuring both firewalls, verify that the firewalls are paired in active/
passive HA.
1. Access the Dashboard on both firewalls, and view the high availability widget.
2. On the active firewall, click the Sync to peer link.
3. Confirm that the firewalls are paired and synced, as shown as follows:
• On the passive firewall: the state of the local firewall should display passive and the
Running Config should show as synchronized.
• On the active firewall: The state of the local firewall should display active and the
Running Config should show as synchronized.
4. On the passive peer, verify that the VM-Series plugin configuration is now synced.
Select Device > VM-Series and validate that you can view the Azure HA configuration that
you had omitted configuring on the passive peer.
VM-Series Public Cloud Deployments 442 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on Azure
Use the Azure Key Vault to Store VM-Series Certificates
Where Can I Use This? What Do I Need?
• Microsoft Azure
• Microsoft Azure Stack
• Azure® Marketplace
• Azure China Marketplace
• Azure Government Marketplace
```
VM-Series License (PAYG or BYOL)
```
VM-Series plugin
Panorama
Panorama plugin for Azure
You can integrate cloud-native key managers to store certificates. Private keys used for
certificates are not stored on a firewall’s hard drive, thereby eliminating security problems.
Administrators retain certificates and private keys in cloud storage. The firewall uses the Azure
Key Vault to retrieve the certificates and private keys from cloud storage, and uses them for
features like decryption and IPSec.
Only VM-Series firewalls are supported to enable certificate retrieval via the Azure Key
Vault. If you're using Key Vault certificates, you can't downgrade to an earlier version of
PAN-OS.
For outbound and inbound decryption, upload the certificates to the native key manager and
provide the required access permissions to the NGFW. An NGFW on a public cloud can use
Key Vault for storing certificates. With such cases, the required access management policies are
configured, using PAN-OS or the CLI, for the same instances.
For environments using autoscaling, an instance boots up in a state with the necessary
certificates retrieved and ready to decrypt traffic without additional manual configuration.
When a certificate is updated in the cloud, it must be reimported as a new certificate onto the
firewall. Assign IAM roles to an instance to enable the instance to retrieve certificates from the
Azure Key Vault store. The IAM role must have Get permission for Secrets on the Azure Key
Vault.
You can retrieve certificates from the Key Vault’s Certificate Store, not its Secrets section. PEM is
the only supported format. PKCS12 or chained certificate isn't supported.
All certificates are deleted when a master key changes, and then refetched upon commit.
When the configuration is synchronized to the passive firewall under HA, the certificate
is automatically downloaded by the management daemon on the passive firewall. As a
result, the certificate itself isn't synchronized.
STEP 1 | Download a certificate.
VM-Series Public Cloud Deployments 443 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on Azure
STEP 2 | Create a Key Vault on Azure in the same resource group where your VM-Series firewall is
```
deployed. Use the Key Vault where you stored the certificate (public and private key) in PEM
```
format.
Upload the certificate and private key together in .pem format.
STEP 3 | After you create the Key Vault, under Access Policies, click Create and add the Managed
Identity.
STEP 4 | Return to your resource group and select the VM-Series firewall. Click Identity > User
Assigned and add the Managed Identity.
Permissions in the Managed Identify must also be provided to Key Vault.
STEP 5 | Return to your Key Vault and select Certificates. Import your certificate PEM file.
Certificates must be kept in PEM format in Key Vault > Certificates.
STEP 6 | Log in to the VM-Series firewall.
STEP 7 | Select Device > Certificate Management > Certificates > Import.
If you want to import an ECDSA certificate, modify the private key:
----Begin EC PRIVATE KEY----
&
----END EC PRIVATE KEY----
To
----BEGIN PRIVATE KEY----
&
----END PRIVATE KEY----
If you want to import a PEM certificate, modify the private key:
----BEGIN PRIVATE KEY----
&
----END PRIVATE KEY----
STEP 8 | Under Cloud, enter the certificate name and set the file format to PEM.
STEP 9 | Select Cloud as the Certificate Type, then configure the following fields:
1. Enter the Certificate Name; copy this from the Key Vault in the Azure Portal.
2. Choose Azure from the Cloud Platform drop-down.
3. Enter the Azure Key Vault URI to specify the location of the Key Vault; copy this from
the Key Vault in the Azure Portal.
4. Enter the Cloud Secret Name. This is used to store the certificate in the Azure Key Vault.
5. You can specify the Algorithm in the Certificate Information screen. Choose the
algorithm for your configuration, either RSA or Elliptical Curve DSA. By default, the
algorithm is set to use RSA. Configure the certificate to use either Forward Trust
VM-Series Public Cloud Deployments 444 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on Azure
Certificate, Forward Untrust Certificate, or Trusted Root CA. You can alternately select
all algorithms for the certificate.
6. Click OK.
7. Commit your changes.
STEP 10 | Verify that the certificate was added successfully:
1. Select Device > Certificate Management > Certificates.
2. Your new certificate should be listed.
Certificate details are not displayed in the Certificates
screen. To view this information in the CLI, use the command:
show shared certificate <cert-name>
You can confirm the configuration of certificate integration in Panorama. Use the Device
Certificate window to determine if the certificate is used. Keep in mind that because data isn't
```
stored in the running configuration (the hard drive), all fields in the Device Certificates table
```
```
are empty, except for the Usage field (if configured) and the Cloud Secret Name.
```
VM-Series Public Cloud Deployments 445 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on Azure
Use the ARM Template to Deploy the VM-Series
Firewall
Where Can I Use This? What Do I Need?
• Microsoft Azure
• Microsoft Azure Stack
• Azure® Marketplace
• Azure China Marketplace
• Azure Government Marketplace
```
VM-Series License (PAYG or BYOL)
```
VM-Series plugin
Panorama
Panorama plugin for Azure
In addition to Marketplace based deployments, Palo Alto Networks provides a GitHub repository,
which hosts sample ARM templates that you can download and customize for your needs. ARM
templates are JSON files that describe the resources required for individual resources such as
network interfaces, a complete virtual machine or even an entire application stack with multiple
virtual machines.
ARM templates are for advanced users, and Palo Alto Networks provides the ARM template
under the community-supported policy. To learn about ARM templates, refer to the Microsoft
documentation on ARM Templates.
```
To simplify the deployment of all the required resources, the two-tier sample template (https://
```
```
github.com/PaloAltoNetworks/azure/tree/master/two-tier-sample) includes two JSON files:
```
• Template File—The azureDeploy.json is the main resources file that deploys all the
components within the resource group.
• Parameters File—The azureDeploy.parameters.json is the file that includes the parameters
required to successfully deploy the VM-Series firewall in the VNet. It includes details such as
the virtual machine tier and size, username, and password for the firewall, the name of the
storage container for the firewall. You can customize this file for your Azure VNet deployment.
To help you deploy the firewall as a gateway for Internet-facing applications, the template
provisions the VM-Series firewall, a database server, and a web server. The VNet uses the
private nonroutable IP address space 192.168.0.0/16. You can modify the template to use
172.16.0.0/12, or 10.0.0.0/8.
The ARM template also provides the necessary user-defined rules and IP forwarding flags to
enable the VM-Series firewall to secure the Azure resource group. For the five subnets—Trust,
Untrust, Web, DB, and NAT—included in the template, you have five route tables, one for each
subnet with user-defined rules for routing traffic to the VM-Series firewall and the NAT virtual
machine.
For the four subnets—Trust, Untrust, Web, and DB—included in the template, you have four route
tables, one for each subnet with user-defined rules for routing traffic to the VM-Series firewall.
VM-Series Public Cloud Deployments 446 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on Azure
Figure 4: Deploy VM-Series Firewall Using the ARM Template
STEP 1 | Download the two-tier sample ARM template from the GitHub repository.
Download and save the files to a local client: https://github.com/PaloAltoNetworks/azure/
tree/master/two-tier-sample
STEP 2 | Create a Resource Group on Azure.
1. Log in to the Azure CLI using the command: az login
If you need help, refer to the Azure documentation on installing the CLI, or for details on
how to access the CLI on Azure Government or Azure China.
2. Create a resource group.
STEP 3 | Deploy the ARM template.
1. Open the Parameters File with a text editor and modify the values for your deployment:
In Azure China, you must edit the path for the storage account that hosts the
VHD image required to deploy the VM-Series firewall. In the variables section of
the template file, find the parameter called userImageNameURI and replace the
value with the location where you saved the VHD image.
2. Deploy the template in the resource group you created.
az deployment group create --name <YourResourceGroupName>
--resource-group <YourResourceGroupName>
--parameters ’@<path-to-template-parameter-azureDeploy.json>’
3. Check the progress and status of the deployment from the Azure CLI:
azure deployment group show <YourResourceGroupName>
VM-Series Public Cloud Deployments 447 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on Azure
When the template is deployed the ProvisioningStateis Running.
If the ProvisioningStateis Failed, you must check for errors on the
Azure portal at Resource Group > Events. Filter for only events in the last one
hour, select the most recent events, and drill down to find the errors.
4. Verify that you have successfully deployed the VM-Series firewall.
1. Select Dashboard > Resource Groups, and select the resource group.
2. Select All Settings > Deployments > Deployment History for detailed status.
The address space within the VNet uses the prefix 192.168, which is defined
in the ARM template.
5. Attach a public IP address to the untrust interface on the firewall.
VM-Series Public Cloud Deployments 448 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on Azure
STEP 4 | Configure the firewall as a VNet gateway to protect your Internet-facing deployment.
1. Log in to the management interface IP address on the firewall.
2. Configure the dataplane network interfaces as Layer 3 interfaces on the firewall
```
(Network > Interfaces > Ethernet).
```
3. Add static rules to the virtual router on the firewall. To route traffic through the firewall
```
in this example, you need three static routes on the firewall (Network > Virtual Routers,
```
```
select the router and click Static Routes):
```
1. Route all outbound traffic through the UnTrust zone, ethernet1/1 to the Azure router
at 192.168.1.1.
2. Route all inbound traffic destined to the web server subnet through the Trust zone,
ethernet1/2 to the Azure router at 192.168.2.1.
3. Route all inbound traffic destined to the database server subnet through the Trust
zone, ethernet1/2 to the Azure router at 192.168.2.1.
4. Create security policy rules (Policies > Security) to allow inbound and outbound traffic
on the firewall. You also need security policy rules to allow appropriate traffic from the
web server subnet to the database server subnet and vice versa.
5. Commit the changes on the firewall.
6. Verify that the VM-Series firewall is securing traffic (Monitor > Logs > Traffic).
VM-Series Public Cloud Deployments 449 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on Azure
Deploy the VM-Series and Azure Application Gateway
Template
Where Can I Use This? What Do I Need?
• Microsoft Azure
• Microsoft Azure Stack
• Azure® Marketplace
• Azure Government Marketplace
```
VM-Series License (PAYG or BYOL)
```
VM-Series plugin
Panorama
Panorama plugin for Azure
The VM-Series and Azure Application Gateway template is a starter kit that you can use to deploy
VM-Series firewalls to secure web workloads for internet-facing deployments on Microsoft Azure
```
(currently not available for Azure China).
```
```
This template deploys two VM-Series firewalls between a pair of (external and internal) Azure
```
load balancers. The external load balancer is an Azure Application Gateway, which is an HTTP
```
(Layer 7) load balancer that also serves as the internet-facing gateway, which receives traffic
```
and distributes it through the VM-Series firewall on to the internal load balancer. The internal
```
load balancer is an Azure Load Balancer (Layer 4) that fronts a pair of web servers. The template
```
supports the BYOL and the Azure Marketplace versions of the VM-Series firewall.
As demand on your web workloads increases and you increase capacity for the web server tier
you can manually deploy additional VM-Series firewalls to secure your web server tier.
VM-Series Public Cloud Deployments 450 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on Azure
The VM-Series and Azure Application Gateway template launches an Azure Application Gateway
```
(Layer 7 load balancer) and an Azure (Layer 4) load balancer. Nested between the Application
```
gateway and the load balancer are a pair of VM-Series firewalls in an Availability Set, and a pair of
sample web servers running Apache 2 on Ubuntu in another Availability Set. The Availability Sets
provide protection from planned and unplanned outages. The following topology diagram shows
the resources that the template deploys:
VM-Series Public Cloud Deployments 451 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on Azure
You can use a new or an existing storage account and resource group in which to deploy all the
resources for this solution within an Azure location. It does not provide default values for the
resource group name and storage account name, you must enter a name for them. While you can
create a new or use an existing VNet, the template creates a default VNet named vnet-FW with
```
the CIDR block 192.168.0.0/16, and allocates five subnets (192.168.1.0/24 - 192.168.5.0/24) for
```
deploying the Azure Application Gateway, the VM-Series firewalls, the Azure load balancer and
the web servers. Each VM-Series firewall is deployed with three network interfaces—ethernet0/1
```
in the Mgmt subnet (192.168.0.0/24), ethernet1/1 in Untrust subnet (192.168.1.0/24), and
```
```
ethernet1/2 in the Trust subnet (192.168.2.0/24).
```
```
The template creates a Network Security Group (NSG) that allows inbound traffic from any source
```
IP address on ports 80,443, and 22. It also deploys the pair of VM-Series firewalls and the web
server pair in their respective Availability Sets to ensure that at least one instance of each is
available during a planned or unplanned maintenance window. Each Availability Set is configured
to use three fault domains and five update domains.
The Azure Application Gateway acts as a reverse-proxy service, which terminates a client
connection and forwards the requests to backend web servers. The Azure Application Gateway is
set up with an HTTP listener and uses a default health probe to test that the VM-Series firewall IP
```
address (for ethernet1/1) is healthy and can receive traffic.
```
```
The template does not provide an auto-scaling solution; you must plan your capacity
```
needs and then deploy additional resources to Adapt the Template for your deployment.
The VM-Series firewalls are not configured to receive and secure web traffic destined to the
web servers. Therefore, at a minimum, you must configure the firewall with a static route to send
traffic from the VM-Series firewalls to the default router, configure the destination NAT policy
to send traffic back to the IP address of the load balancer, and configure Security policy rules.
The NAT policy rule is also required for the firewall to send responses back to the health probes
from the HTTP listener on the Azure Application Gateway. To assist you with a basic firewall
configuration, the GitHub repository includes a sample configuration file called appgw-sample.xml
that you can use to get started.
VM-Series Public Cloud Deployments 452 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on Azure
Start Using the VM-Series & Azure Application Gateway Template
Where Can I Use This? What Do I Need?
• Microsoft Azure
• Microsoft Azure Stack
• Azure® Marketplace
• Azure Government Marketplace
```
VM-Series License (PAYG or BYOL)
```
VM-Series plugin
Panorama
Panorama plugin for Azure
The VM-Series & Azure Application Gateway template launches all the resources you need to
deploy and secure your web workloads for internet facing deployments on Microsoft Azure,
excluding Azure China. This section provides details on how to deploy the template, configure the
firewalls to route and secure traffic destined to the web servers, and extend the capabilities and
resources that this template provides to accommodate your deployment needs.
Deploy the Template to Azure
Use the following instructions to deploy the template to Azure.
VM-Series Public Cloud Deployments 453 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on Azure
STEP 1 | Deploy the template.
Currently not available for deploying in Azure China.
1. Access the template from https://github.com/PaloAltoNetworks/azure-
applicationgateway
2. Click Deploy to Azure.
3. Fill in the details for deploying the template. See VM-Series and Azure Application
Gateway Template Parameters for a description and the default values, if any, for each
parameter.
At a minimum, you have to pick the Azure Subscription, Resource Group, Location,
Storage Account Name, and a Username/password or SSH Key for the administrative
account on the VM-Series firewalls.
4. Click Purchase to accept the terms and conditions and deploy the resources.
If you have validation errors, click to view the details and fix your errors.
5. On the Azure portal, verify that you have successfully deployed the template resources,
including the VM-Series firewalls.
1. Select Dashboard > Resource Groups, select the resource group.
2. Select Overview to review all the resources that have been deployed. The
deployment status should display Succeeded.
VM-Series Public Cloud Deployments 454 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on Azure
3. Note the Public IP address or the DNS name assigned to eth0-VM-Series0 and eth0-
VM-Series1 to access the management interface of the VM-Series firewalls.
STEP 2 | Log in to the firewalls.
1. Using a secure connection (HTTPS) from your web browser, log in to the IP address for
eth0-VM-Series0 or the DNS name for the firewall.
2. Enter the username/password you defined in the parameters file. You will see a
```
certificate warning; that’s okay. Continue to the webpage.
```
VM-Series Public Cloud Deployments 455 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on Azure
STEP 3 | Configure the VM-Series firewall.
You can either configure the firewall manually or import the Sample Configuration File
provided in the GitHub repository and customize it for your security needs.
• Configure the firewall manually—You must do the following at a minimum:
1. Configure the dataplane network interfaces as Layer 3 interfaces on the firewall
```
(Network > Interfaces > Ethernet).
```
2. Add a static rule to the virtual router on the firewall. This static rule specifies the
firewall’s untrust interface IP address as the next hop address for any traffic destined for
```
ethernet1/1. (Network > Virtual Routers, select the router and click Static Routes).
```
3. Create security policy rules (Policies > Security) to allow inbound and outbound traffic
on the firewall.
4. Add NAT policies (Policies > NAT). Create destination NAT and source NAT rules on the
firewall to send traffic to the web servers and back out to the client who initiated the
request.
The destination NAT rule is for all traffic that arrives on the firewall’s untrust interface.
This rule is required to translate the destination IP address on the packet to that of the
internal load balancer so that all traffic is directed to the internal load balancer and on to
the backend web servers.
The source NAT rule is for all traffic from the backend web server and destined to the
untrust interface on the firewall. This rule translates the source address to the IP address
of the trust interface on the firewall.
5. Commit your changes.
• Import the sample configuration file:
6. Download and save the Sample Configuration File to your local client.
7. Select Device > Setup > Operations, click Import named configuration snapshot,
Browse to the sample configuration file that you have saved locally, and click OK.
8. Click Load named configuration snapshot, select the Name of the sample configuration
file you imported, and click OK.
9. Change the IP address of the address objects and the static route to match the IP
address from the CIDR block you used. Update address objects to use the private IP
addresses for eth1-VM-Series0 and eth1-VM-Series1.
10. Important! Create a new admin user account. Select Device > Administrators and Add a
new account.
11. Modify the Hostname in the General Settings widget in Device > Setup > Management.
12. Commit your changes, and log out. The commit overwrites the running configuration
with the sample configuration file and updates you just made. On commit, the hostname
and the administrator user account that you specified when deploying the template
are overwritten. You will now need to login using the new admin user account and
password.
• Log in to the firewall—Use the credentials you created and delete the pan demo
administrative account imported as part of the sample configuration file.
VM-Series Public Cloud Deployments 456 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on Azure
STEP 4 | Log in and configure the other instance of the VM-Series firewall.
See step Configure the VM-Series firewall.
STEP 5 | Verify that you have configured the firewalls properly.
From your web browser, use HTTP to access the IP address or DNS name for the app gateway.
Be able to view the default Apache 2 Ubuntu webpage.
If you have used the sample configuration firewall, log in to the firewall and view the Traffic
logs generated on session start in Monitor > Logs > Traffic.
VM-Series and Azure Application Gateway Template Parameters
Where Can I Use This? What Do I Need?
• Microsoft Azure
• Microsoft Azure Stack
• Azure® Marketplace
• Azure Government Marketplace
```
VM-Series License (PAYG or BYOL)
```
VM-Series plugin
Panorama
Panorama plugin for Azure
The following table lists the required and optional parameters and the default values:
Parameter Description
```
Resource group Create new or use existing (no default).
```
Subscription The type of Azure subscription you will use to cover the cost of
the resources deployed with the template.
VM-Series Public Cloud Deployments 457 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on Azure
Parameter Description
Location Select the Azure location to which you want to deploy the
```
template (no default).
```
Network Security Group
Network Security Group
Name
The network security group limits the source IP addresses from
which the VM-Series firewalls and web servers can be accessed.
```
Default: nsg-mgmt
```
Network Security Group
Inbound Src IP
The source IP addresses that can log in to the management port of
the VMs deployed by the template.
The default value 0.0.0.0/0 means you can log into the firewall
management port from any IP address.
Storage Account
```
Storage Account Name Create new or enter the name of an existing Storage Account (no
```
```
default). The name must be globally unique.
```
Storage Account Type Choose between standard and premium storage and your data
replication needs for local redundancy, geo-redundancy, and read-
access geo-redundancy.
```
The default option is Locally Redundant Storage (LRS). The other
```
options are Standard GRS, Premium LRS, and Standard RAGRS.
VNet
Virtual Network Create a new or enter the name of an existing VNet.
The default name for the VNet is vnet-FW
Virtual Network Address
Prefix
192.168.0.0/16
Azure Application Gateway
App Gateway Name myAppGw
App Gateway DNS
Name
Enter a globally unique DNS name for the Azure Application
Gateway.
App Gateway Subnet
Name and Prefix
Default name is AppGWSubnet and the subnet prefix is
192.168.3.0/24.
Azure Load Balancer and Web Servers
VM-Series Public Cloud Deployments 458 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on Azure
Parameter Description
Internal Load Balancer
Name
myPrivateLB
Internal Load Balancer
Subnet Name and Prefix
The default name is backendSubnet and the subnet prefix is
192.168.4.0/24.
Backend VM Size The default size is Standard tier D1 Azure VM. Use the drop-down
in the template to view the other Azure VM options available for
the backend web servers.
Firewalls
```
Firewall Model Choose from BYOL or PAYG (bundle 1 or bundle 2, each bundle
```
```
includes the VM-300 and a set of subscriptions).
```
Firewall VM Name and
Size
The default name for the firewall is VM-Series, and the default size
is Standard tier D3 Azure VM.
Use the drop-down in the template to view the other Azure VM
options available for the VM-Series firewalls
Mgmt Subnet Name and
Prefix
The management subnet for the VM-Series firewalls and the web
servers deployed in this solution.
Default name is Mgmt and the subnet prefix is 192.168.0.0/24.
Mgmt Public IP address
Name
Enter a hostname to access the management interface on each
firewall. The names must be globally unique.
Trusted Subnet Name
and Prefix
The subnet to which eth1/1 on the VM-Series firewall is
```
connected; this subnet connects the VM-Series firewall to the
```
Azure Application gateway. The firewall receives web traffic
destined to the web servers on eth1/1.
Default name is Trust and the subnet prefix is 192.168.2.0/24.
Untrusted Subnet Name The subnet to which eth1/2 on the VM-Series firewall is
connected. The firewall receives return and outbound web traffic
on this interface.
Default name is Untrust and the subnet prefix is 192.168.1.0/24.
The name must be globally unique.
Username Enter the username for the administrative account on the VM-
Series firewalls and the web servers.
Authentication Type Either enter a password for authentication or use an SSH public
```
key (no default).
```
VM-Series Public Cloud Deployments 459 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on Azure
Adapt the Template
As your needs evolve, you can scope your capacity needs and extend the template for your
deployment scenario. Here are some ways you can build on the starter template to meet your
planned capacity needs:
• Deploy additional VM-Series firewalls behind the Azure Application Gateway. You can
manually install more VM-Series firewalls into the same Availability Set or launch a new
Availability Set and manually deploy additional VM-Series firewalls.
• Configure the VM-Series firewalls beyond the basic configuration provided in the sample
configuration file in the GitHub repository.
```
• Enable HTTPS load balancing (SSL offload) on the Azure Application Gateway. Refer to the
```
Azure documentation for details.
• Add or replace the sample web servers included with the template.
Sample Configuration File
To help you get started, the GitHub repository contains a sample configuration file named appgw-
sample.xml that includes the following rules/objects:
• Address objects—Two address objects, firewall-untrust-IP and internal-load-balancer-
IP, which you will need to modify to match the IP addresses in your setup. You need to modify
these address objects to use the private IP addresses assigned to eth1-VM-Series0 and eth1-
VM-Series1 on the Azure portal.
• Static route—The default virtual router on the firewall has a static route to 192.168.1.1, and
this IP address is accurate if you use the default template values. If you have changed the
Untrust subnet CIDR, you’ll need to update the IP address to match your setup. All traffic
coming from the backend web servers, destined for the application gateway, uses this IP
address as the next hop for delivering packets to the untrust interface on the firewall.
• NAT policy Rule—The NAT policy rule enables destination NAT and source NAT.
• The destination NAT rule is for all traffic that arrives on the firewall’s untrust interface
```
(ethernet1/2), which is the firewall-untrust-IP address object. This rule translates the
```
destination IP address on the packet to that of the internal load balancer so that all traffic is
directed to the internal load balancer and thus to the backend web servers.
• The source NAT rule is for all traffic from the backend web server and destined to the
untrust network interface on the firewall. This rule translates the source address to the IP
```
address of the trust interface on the firewall (ethernet1/2).
```
• Security Policy Rule—Two Security policy rules are defined in the sample configuration file.
The first rule allows all inbound web-browsing traffic and generates a log at the start of a
session on the firewall. The second rule blocks all other traffic and generates a log at the start
and end of a session on the firewall. You can use these logs to monitor all traffic to the web
servers in this deployment.
• Administrative User Credentials— The sample configuration file includes a username and
password for logging in to the firewall, which is set to pandemo/demopassword. After you
import the sample configuration, you must either change the password and set it to a strong,
custom password or create a new administrator account and delete the pan demo account.
VM-Series Public Cloud Deployments 460 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on Azure
Secure Kubernetes Services on Azure
Where Can I Use This? What Do I Need?
• Microsoft Azure
• Microsoft Azure Stack
• Azure® Marketplace
• Azure Government Marketplace
```
VM-Series License (PAYG or BYOL)
```
VM-Series plugin
Panorama
Panorama plugin for Azure
To secure Azure Kubernetes services, you must first install the Azure plugin on Panorama and
configure an Azure Secure Kubernetes Services on Azure deployment. The Azure plugin for
Panorama supports tag-based VM monitoring and Secure Kubernetes Services on Azure, secures
```
inbound traffic for Azure Kubernetes Services (AKS) clusters, and monitors outbound traffic from
```
AKS clusters. The Panorama orchestrated deployment allows you to use the Azure auto scale
metrics and the scale-in and scale-out thresholds to manage surges in demand for application
workload resources by independently scaling the VM-Series firewalls.
To secure inbound traffic for your AKS cluster, you must first Secure Kubernetes Services on
Azure. The Panorama orchestrated deployment works with Secure Kubernetes Services on Azure
to gather information about your network and resources, then create an auto-scaling tier of VM-
Series firewalls for either Secure Kubernetes Services on Azure deployments. See the Palo Alto
Networks Compatibility Matrix, to verify the minimum OS, plugin, and template versions required
to secure AKS clusters.
```
Palo Alto Networks provides a AKS template that deploys an Azure Kubernetes Service (AKS)
```
cluster in a new Azure VNet. The Azure plugin on Panorama helps you set up a connection,
which can monitor Azure Kubernetes cluster workloads, harvesting services you have annotated
as “internal load balancer” and creating tags you can use in dynamic address groups. Use the
Panorama Dynamic Address Groups to apply a security policy on inbound traffic routed to
services running on your AKS cluster.
How Does the Panorama Plugin for Azure Secure Kubernetes
Services?
```
Use VM-Series firewalls to secure inbound traffic for Azure Kubernetes Service (AKS) clusters.
```
```
The VM-Series firewall can only secure services exposed by a load balancer (such as an Azure load
```
```
balancer). You can monitor only outbound traffic using this service.
```
This chapter reviews the different components that enable the Azure plugin for Panorama to
connect to an AKS cluster.
Requirements
This solution requires the following components. See the Panorama plugin information in the
Compatibility Matrix for the minimum version requirements.
• VM-Series firewalls.
VM-Series Public Cloud Deployments 461 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on Azure
• Panorama—Your Panorama version must be the same or higher than your VM-Series PAN-OS
version.
• Panorama plugin for Azure.
• A Panorama orchestrated deployment.
• Azure AKS template version 1.0. This template creates an AKS cluster.
```
Enable AKS advanced networking (CNI) for the cluster.
```
An AKS deployment requires advanced networking to configure VNet Peering for the hub and
```
spoke VNets (see A Sample Hub-and-Spoke Topology to Secure AKS Clusters).
```
A Sample Hub-and-Spoke Topology to Secure AKS Clusters
The following diagram illustrates a sample auto scale deployment that secures inbound traffic for
Azure AKS clusters. Let’s review some of the components.
• Auto scaling Infrastructure—The Azure Auto Scaling templates create the messaging
infrastructure and the basic hub and spoke architecture.
• AKS Clusters—The Palo Alto Networks AKS template creates an AKS cluster in a new VNet.
Given the name of the Spoke resource group, the template tags the VNet and AKS cluster with
the Spoke resource group name, so that the resource group is discovered by the Azure auto
VM-Series Public Cloud Deployments 462 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on Azure
scaling plugin for Panorama. The Azure plugin for Panorama queries service IP addresses on
the Staging ILB to learn about AKS cluster services.
```
Only one Spoke firewall scale set is to be associated with an AKS cluster; if you expose
```
multiple services in a single AKS cluster, they must be protected by the same Spoke.
For each resource group, create a subnet-based address group. In the above diagram,
```
for example, create an address group for 10.240.0.0/24 (AKS Cluster 1).
```
• VNet Peering—You must manually configure VNET peering to communicate with other VNets
in the same region.
Cross-region peering isn't supported.
You can use other automation tools to deploy AKS clusters. If you deploy in an existing
```
VNet (the hub firewall VNet, for example) you must manually configure VNet peering
```
to the inbound and outbound hub and spoke resource groups, and manually tag the
VNet and AKS cluster with the resource group name.
• User-Defined Routes and Rules—You must manually configure user-defined routes and rules
```
(see User-Defined Routing). In the diagram above, incoming traffic can be redirected, according
```
to UDR rules, to the firewall ILB for inspection. Outbound traffic exiting an AKS Cluster is
```
redirected to the hub firewall ILB with Azure user-defined routing (UDR) rules. The solution
```
assumes Allow All as a default policy for Kubernetes orchestration to function as-is, but to
apply the policy you can use an allowlist or a denylist to allow or deny outbound traffic.
User-Defined Routing
Manually create user-defined routing and routing rules to govern inbound or outbound traffic.
Inbound
In the above diagram, inbound traffic from the Application gateway is driven to the backend pool,
and based on UDR rules, redirected to the firewall ILB. For example, create a UDR pointing to the
VNet subnet so that the traffic for Kubernetes services is pointed to the firewall ILB.
Outbound
On the hub firewall set, for each AKS cluster being protected. Create static routes for the cluster
subnet CIDR, with the next hop being the gateway address of the hub VNet trust subnet.
All outbound traffic for an AKS cluster is directed to the hub firewall set with a single UDR rule.
AKS Cluster Communication
The Panorama plugin for Azure can only communicate with the AKS controller node for a given
AKS cluster. For Outbound AKS traffic, the next hop is the hub firewall ILB. Because Outbound
traffic is monitored, you must Allow All traffic. The following topics emphasize common practices
that help you establish connectivity. Keep them in mind when you plan your networks and
subnets.
VM-Series Public Cloud Deployments 463 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on Azure
Create AKS Cluster Authentication
When you connect the AKS cluster in Azure plugin for Panorama you must enter a secret
authorization token. Use Kubernetes commands to perform the following steps.
1. Create a ClusterRole.
2. Create a ClusterRoleBinding.
1. Create a .yaml file for the ClusterRoleBinding. For example, create a text file named
crb.yaml.
```
apiVersion: rbac.authorization.k8s.io
```
```
kind: ClusterRoleBinding
```
```
metadata:
```
```
name: default-view
```
```
roleRef:
```
```
apiGroup: rbac.authorization.k8s.io
```
```
kind: ClusterRole
```
```
name: view
```
```
subjects:
```
- kind: ServiceAccount
```
name: default
```
```
namespace: default
```
2. Use Azure Cloud Shell to apply the crb.yaml role binding.
kubectl apply -f crb.yaml
3. View the service account you created.
kubectl get serviceaccounts
3. Save the service account credential to a .json file.
1. On your local machine, change to the directory in which you want to save the credential.
2. Use kubectl command to create the token.
```
MY_SA_TOKEN=‘kubectl get serviceaccounts default -o
```
```
jsonpath=’{.secrets[0].name}’‘
```
3. View the token name.
$ echo $MY_SA_TOKEN
4. Display the credential.
kubectl get secret $MY_SA_TOKEN -o json
You need the token when you connect the AKS cluster in Azure plugin for Panorama, in Step 3.d.
Use an Address Group to Identify Traffic
To create some granularity for monitored Outbound traffic, create an address group specifically
```
for the AKS cluster VNet subnet (for example, 10.240.0.97/32 in the above diagram). You can
```
then write rules that allow incoming or returning traffic rather than using Allow All.
If you create an address group, be careful to maintain the communication between the AKS
controller and any worker nodes. See Add the Subnet Address Group to the Top-Level Policy.
VM-Series Public Cloud Deployments 464 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on Azure
If communication is interrupted, application traffic can be lost or your application
deployment might have problems.
Add the Subnet Address Group to the Top-Level Policy
To maintain connectivity, the address group must be part of the top-level policy in Panorama. You
can configure the cluster address group, or bootstrap the cluster to configure the cluster address
group.
Add the address group to the top-level policy before you configure VNet peering or User-
Defined Routing.
Prevent Application Disruption When Workload and AKS Cluster VNets Are Peered
If an AKS cluster coexists with VM workloads that run in separate VNets, and the VNet is peered
```
with both the workload spoke (Inbound) and the hub (Outbound), you must create address groups
```
to differentiate the workloads and the AKS traffic, and add the address group to Top-Level Policy
as described above.
Dynamic Address Groups with Kubernetes Labels
When monitoring an AKS cluster resource, the Azure plugin automatically generates the following
IP tags for AKS services.
aks.<aks cluster name>.<aks service name>
Tags are not generated for nodes, pods, or other resources.
```
If the AKS service has any labels, the tag is as follows (one per label):
```
aks.<aks cluster name>.svc.<label>.<value>
If a labelSelector tag is defined for a cluster, the plugin generates the following IP tag:
aks_<labelSelector>.<aks cluster name>.<aks service name>
Secure an AKS Cluster
Where Can I Use This? What Do I Need?
• Microsoft Azure
• Microsoft Azure Stack
• Azure® Marketplace
• Azure Government Marketplace
```
VM-Series License (PAYG or BYOL)
```
VM-Series plugin
Panorama
Panorama plugin for Azure
VM-Series Public Cloud Deployments 465 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on Azure
```
To enable Panorama to connect to the load balancers in an Azure Kubernetes Services (AKS)
```
cluster, you must enable the Azure plugin on Panorama to establish a connection with your AKS
cluster. Then, you must configure the device groups and templates to which the firewalls belong
so that Panorama can push configuration objects and policy rules to your managed firewalls.
Before You Begin
To secure AKS, you must first deploy the Azure Auto Scaling solution available on GitHub.
To secure a web application running as a service within a Kubernetes cluster you must plan the
VNets, subnets, and UDRs. VM-Series firewalls and Panorama provide you with security and
visibility of your Kubernetes services.
Review “Secure Kubernetes Services on Azure”.
You must have AKS advanced networking to use the Palo Alto Networks AKS template.
Design your AKS subnets before you deploy AKS clusters. Review A Sample Hub-and-Spoke
Topology to Secure AKS Clusters, and AKS Cluster Communication.
```
The template creates a single AKS cluster (Service) as a sample. Specify CIDR ranges for the
```
VNet, VNet subnet, and the service. The CIDR ranges must not overlap
Size your subnets to your requirements. Avoid unnecessarily large ranges, as they can affect
performance.
See User-Defined Routing. Specify specific UDR routes rather than broad subnet-specific
routes.
Plan how you want to peer your VNets. If you're peering AKS clusters, be sure you have read
AKS Cluster Communication.
Think about the ways in which you want to identify traffic.
If you plan to use an address group on Outbound AKS traffic, see Add the Subnet Address
Group to the Top-Level Policy.
If you have service names or tags that are not unique across namespaces, use the label
selector to filter both a tag and a namespace so that you get a unique result.
Use the Template to Deploy an AKS Cluster
The Azure AKS template is a sample that provisions a cluster in a new VNet.
STEP 1 | On GitHub, go to PaloAltoNetworks/azure-aks and locate the build package in the
repository.
STEP 2 | Unzip the build package. Edit the files azuredeploy.json and parameters.json for
your own deployment, and save.
STEP 3 | Issue the following Azure CLI commands to deploy the template.
az group deployment validate --resource-group RG_NAME
--template-file azuredeploy.json
--parameters @parameters.json
az group deployment create --name DEPLOYMENT_NAME
VM-Series Public Cloud Deployments 466 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on Azure
--resource-group RG_NAME
--template-file azuredeploy.json
--parameters @parameters.json
STEP 4 | Deploy your applications or services on the AKS Cluster.
1. Annotate your service YAML file so that the type is load balancer, and annotate it as
service.beta.kubernetes.io/azure-load-balancer-internal: "true". For example:
```
apiVersion: v1
```
```
kind: Service
```
```
metadata:
```
```
name: azure-vote-front
```
```
labels:
```
```
service: "azure-vote-front"
```
```
tier: "stagingapp"
```
```
annotations:
```
service.beta.kubernetes.io/azure-load-balancer-internal:
"true"
```
spec:
```
```
type: LoadBalancer
```
```
ports:
```
- port: 80
```
selector:
```
```
app: azure-vote-front
```
2. If you have not done so, Create AKS Cluster Authentication before continuing.
3. Deploy your service on your AKS cluster.
For example, you can deploy your application through kubectl:
kubectl apply -f myapplication.yaml
For a sample, see: https://github.com/Azure-Samples/azure-voting-app-redis/blob/
master/azure-vote-all-in-one-redis.yaml
4. Use kubectl to get the service IP for the deployed service.
kubectl get services -o wide
In the EXTERNAL-IP column 10.240.0.97 is for the ILB, according to your annotation in
Step a. Use the service IP to create a user-defined route on Azure.
VM-Series Public Cloud Deployments 467 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on Azure
STEP 5 | Create a UDR rule to point your service to the firewall ILB behind the application gateway.
In Azure, go to your inbound spoke resource group, view the route table and add a new route
based on the destination service IP. In the following screen, the value in the tov1service
ADDRESS PREFIX column is the service IP.
Connect the AKS Cluster in Azure Plugin for Panorama
This task assumes you have deployed a Panorama orchestrated deployment, and that you have
created templates, template stacks and device groups.
See the Panorama online help for more on filling out each form.
VM-Series Public Cloud Deployments 468 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on Azure
STEP 1 | Select Panorama > Azure > Deployments to view the monitoring definition you created
when you configured the deployment. As shown below, if Auto Program Routes is enabled,
the firewall routes are programmed for you.
VM-Series Public Cloud Deployments 469 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on Azure
STEP 2 | In AKS, tag your Resource Groups. The tags are name/value pairs.
1. Select Home > Resource groups and choose a resource group.
2. Select Tags and define name and value pairs. As shown in the following figure, the tag
names must be inboundgrouprg and HubRG:
• inboundgrouprg—your spoke resource group name
• HubRG—your hub resource group name
The template takes the name of the Spoke resource group as a parameter, and tags the
VNet and AKS cluster with the Spoke resource group name so that it can be discovered
by the Panorama plugin for Azure.
The templates deploy resources in separate VNets. If you manually deploy the AKS
cluster and service in the same VNet as the Spoke firewall set, you must manually
create tags for the spoke resource group name.
VM-Series Public Cloud Deployments 470 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on Azure
STEP 3 | In Panorama, select Panorama > Azure > Setup.
1. On the General tab, enable monitoring.
2. On the Notify Groups tab, Add a notification group and select the device groups to be
notified.
3. On the Service Principal tab, Add and Validate a service principal.
Use the Service Principal you created for the orchestrated deployment.
4. On the AKS Cluster tab, Add an AKS cluster.
• Enter the exact name of the AKS cluster.
• Enter the API server address. To find the address in Azure, view your AKS service and
select Overview.
```
• Upload the AKS credential JSON file (see Create AKS Cluster Authentication).
```
5. Fill in the remaining fields and Add one or more tags.
If you have service names or tags that are not unique across namespaces, use
the label selector to filter both a tag and a namespace so that you get a unique
result.
VM-Series Public Cloud Deployments 471 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on Azure
STEP 4 | Select Panorama > Azure > Monitoring Definition
1. Add a Monitoring definition.
2. Enter a name and description, and select AKS Cluster Monitoring.
3. Select an AKS Cluster and a Notify Group, check Enable, and click OK.
Set Up VNet Peering
If you plan to use an address group to identify traffic, be sure to add the subnet address group to
your top-level Panorama policy before you configure peering.
After deploying an AKS cluster, set up VNet Peering from the Inbound VNet to your cluster, and
from your cluster to the firewall VNet.
Redirect Traffic to a Firewall ILB
```
Manually create user-defined routes (UDRs) and routing rules to redirect traffic to a particular
```
ILB. For an example, see how the diagram in “Secure Kubernetes Services on Azure” depicts an
inbound UDR.
STEP 1 | Create URL routing rules that redirect web traffic to the appropriate backend pool.
VM-Series Public Cloud Deployments 472 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on Azure
STEP 2 | Update the UDR rules for the application gateway subnet to add a route for the service
CIDR, with the next hop being the Inbound firewall Load Balancer from the Spoke firewall
resource group.
Apply Policy to Relevant AKS Service
STEP 1 | In Panorama, select Policies.
STEP 2 | In the Device Group list, choose the device group for your AKS service.
STEP 3 | Add a Security policy rule. Fill out the form, and on the Destination tab Add the destination
address or address group.
Deploy and Secure AKS Services
These steps outline how you can secure inbound and outbound traffic traversing to Kubernetes
services using VM-Series firewall and the Azure plugin for Panorama.
STEP 1 | In the application deployment environment, create a YAML file for the application or use a
file that already exists. The following is a sample application YAML file:
```
apiVersion: apps/v1
```
```
kind: Deployment
```
```
metadata:
```
```
name: azure-vote-back
```
```
spec:
```
```
replicas: 1
```
```
selector:
```
```
matchLabels:
```
```
app: azure-vote-back
```
```
template:
```
```
metadata:
```
```
labels:
```
VM-Series Public Cloud Deployments 473 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on Azure
```
app: azure-vote-back
```
```
spec:
```
```
containers:
```
- name: azure-vote-back
```
image: redis
```
```
resources:
```
```
requests:
```
```
cpu: 100m
```
```
memory: 128Mi
```
```
limits:
```
```
cpu: 250m
```
```
memory: 256Mi
```
```
ports:
```
- containerPort: 6379
```
name: redis
```
---
```
apiVersion: v1
```
```
kind: Service
```
```
metadata:
```
```
name: azure-vote-back
```
```
labels:
```
```
service: backend
```
```
spec:
```
```
ports:
```
- port: 6379
```
selector:
```
```
app: azure-vote-back
```
---
```
apiVersion: apps/v1
```
```
kind: Deployment
```
```
metadata:
```
```
name: azure-vote-front
```
```
spec:
```
```
replicas: 5
```
```
selector:
```
```
matchLabels:
```
```
app: azure-vote-front
```
```
template:
```
```
metadata:
```
```
labels:
```
```
app: azure-vote-front
```
```
spec:
```
```
containers:
```
- name: azure-vote-front
```
image: microsoft/azure-vote-front:v1
```
```
resources:
```
```
requests:
```
```
cpu: 100m
```
```
memory: 128Mi
```
```
limits:
```
```
cpu: 250m
```
```
memory: 256Mi
```
```
ports:
```
- containerPort: 80
```
env:
```
- name: REDIS
VM-Series Public Cloud Deployments 474 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on Azure
```
value: "azure-vote-back"
```
---
```
apiVersion: v1
```
```
kind: Service
```
```
metadata:
```
```
name: azure-vote-front
```
```
labels:
```
```
service: "azure-vote-front"
```
```
type: "production"
```
```
providesecurity: "yes"
```
```
a: "value"
```
```
b: "value"
```
```
c: "value"
```
```
tier: "stagingapp"
```
```
annotations:
```
service.beta.kubernetes.io/azure-load-balancer-internal: "true"
```
spec:
```
```
type: LoadBalancer
```
```
ports:
```
- port: 80
```
selector:
```
```
app: azure-vote-front
```
STEP 2 | Edit your YAML file to label Kubernetes services.
Labels enable the corresponding tag-to-IP mapping to be created when you use the Panorama
plugin for AKS to connect to the cluster. For example, in the above sample file look for the
application labels in the service metadata. They are: azure-vote-back and azure-vote-
front.
STEP 3 | In your AKS cluster, apply the YAML file.
VM-Series Public Cloud Deployments 475 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on Azure
STEP 4 | In Panorama, create an address group using a resource group tag.
1. On the Objects tab, select a device group from the Device Group list.
2. Select Address Groups and Add an address group.
1. Specify a name, and select the Dynamic type.
2. Add addresses. Adding spawns a window that lists detected addresses. Populating the
list can take several minutes.
3. You can choose one or more addresses for the Match Criteria. Select AND or OR for
the criteria relationship.
4. If you have many addresses, enter a string in the search box to filter the output, as
shown in the following figure.
5. In the address list, click the + to include the address in the address group match
criteria.
6. When the match criteria are complete, click OK.
STEP 5 | Show policy using the address group.
VM-Series Public Cloud Deployments 476 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on Azure
STEP 6 | View secured AKS services.
In Panorama > Azure > Deployments, view your monitoring definition, and in the Action
column select the Protected Applications and Services link.
The Protected? column summarizes the security status of your resource groups. It might take
several minutes for the window to populate. If you have many resource groups, enter a string
in the search box to filter the output.
```
This output is based on the Azure resource group configuration; it does not query the device
```
group or template stack membership.
VM-Series Public Cloud Deployments 477 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on Azure
Use Case: Deploy the VM-Series Firewall in Different
Availability Zones in Azure
Where Can I Use This? What Do I Need?
• Microsoft Azure
• Microsoft Azure Stack
• Azure® Marketplace
```
VM-Series License (PAYG or BYOL)
```
VM-Series plugin
Panorama
Panorama plugin for Azure
This page helps you to deploy the VM-Series firewall in different availability zones in Azure. This
VM-Series setup protects your virtual network from availability zone outages.
Deploy the VM-Series firewall in different availability zones using the azureDeploy.json ARM
template. You can edit this template as per your network architecture.
VM-Series Public Cloud Deployments 478 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on Azure
Figure 5: Deploy VM-Series in Different Availability Zones Architecture
This template deploys the following into a new or existing VNET with 4 subnets:
2 x VM-Series firewalls
• 3 x Interfaces
• management: <fw_name>-nic0
• dataplane1: <fw_name>-nic1
• dataplane2: <fw_name>-nic2
VM-Series Public Cloud Deployments 479 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on Azure
• Managed Disks
• BYOL/Bundle1/Bundle2 License
```
• (Optional) Accelerated Networking
```
```
• (Optional) Bootstrap Capable
```
```
• (Optional) Public IPs for interfaces:
```
• management: <fw_name>-nic0-pip
• dataplane1: <fw_name>-nic1-pip
2 x Networking Security Groups
• management: <nsg_name>-mgmt
• dataplane: <nsg_name>-data
1 x Standard SKU Public Load Balancer
• Backend Pool: <fw1_name>-nic1 & <fw2_name>-nic1
1 x Standard SKU Internal Load Balancer with HA ports
• Backend Pool: <fw1_name>-nic2 & <fw2_name>-nic2
By default, the template uses the deployment resource group as the location of the
VNET. If the VNET is in a different resource group, the resource group must be specified
at deployment time. When deploying a new VNET into a different resource group, the
resource group must exist before deployment.
STEP 1 | Clone the Palo Alto GitHub repo for Azure templates.
STEP 2 | Download and save the azureDeploy.json ARM template to a local client in Azure.
STEP 3 | Log in to Azure CLI:
az login
STEP 4 | Create a resource group in Azure to deploy the VM-Series firewall in a new resource group.
STEP 5 | Edit the azureDeploy.parameters.json template to modify the parameter values for your
deployment.
STEP 6 |You can deploy the template resources in the Azure cloud in either of the two ways:
1. Use the Deploy to Azure (Button) for a custom deployment template.
2. Deploy manually in the resource group that you created:
az deployment group create \
--name <DeploymentName> \
--resource-group <YourResourceGroupName> \
--parameters '@<path-to-template-parameter-azureDeploy.json>'
VM-Series Public Cloud Deployments 480 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on Azure
STEP 7 | Verify the VM-Series firewall deployment under Azure Resource groups, or using the Azure
```
CLI:
```
az deployment group show <YourResourceGroupName>
STEP 8 | Configure the firewall as a VNet gateway to protect your Internet-facing deployment.
1. Log in to the management interface IP address on the firewall.
2. Configure the dataplane network interfaces as Layer 3 interfaces on the firewall
```
(Network > Interfaces > Ethernet).
```
3. Add static rules to the virtual router on the firewall. To route traffic through the firewall
```
in this example, you need three static routes on the firewall (Network > Virtual Routers,
```
```
select the router and click Static Routes):
```
1. Route all outbound traffic through the UnTrust zone, ethernet1/1 to the Azure router
at 192.168.1.1.
2. Route all inbound traffic destined to the web server subnet through the Trust zone,
ethernet1/2 to the Azure router at 192.168.2.1.
3. Route all inbound traffic destined to the database server subnet through the Trust
zone, ethernet1/2 to the Azure router at 192.168.2.1.
4. Create security policy rules (Policies > Security) to allow inbound and outbound traffic
on the firewall. You also need security policy rules to allow appropriate traffic from the
web server subnet to the database server subnet and vice versa.
5. Commit the changes on the firewall.
6. Verify that the VM-Series firewall is securing traffic (Monitor > Logs > Traffic).
Clean up Resources
STEP 1 | Delete resource group:
az group delete --name <DeploymentName>
STEP 2 | Delete resource:
az resource delete \
--resource-group <DeploymentName>
VM-Series Public Cloud Deployments 481 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on Azure
VM-Series Public Cloud Deployments 482 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on Google
Cloud Platform
Where Can I Use This? What Do I Need?
```
• Google Cloud Platform (GCP) VM-Series License (PAYG or BYOL)
```
VM-Series plugin
Panorama
Panorama plugin for GCP
VM-Series firewalls bring next-generation firewall features to the Google® Cloud
```
Platform™(GCP). To maximize performance, VM-Series firewalls on GCP support the Data Plane
```
```
Development Kit (DPDK) libraries, which provide fast packet processing and improve network
```
performance based on specific combinations of VM-Series firewall licenses and Google Cloud
```
Platform virtual machine (VM) sizes.
```
The VM-Series firewall integration with GCP allows you to deploy the VM-Series firewall as a
```
virtual machine (VM) running on a Google Compute Engine instance. For a simplified process,
```
Deploy the VM-Series Firewall from Google Cloud Platform Marketplace. After you deploy the
VM-Series firewall, you can configure the following optional services:
• Enable Google Stackdriver Monitoring on the VM Series Firewall—From the firewall, push
PAN-OS metrics to the Google Stackdriver service.
• Enable VM Monitoring to Track VM Changes on Google Cloud Platform—Set up a VM
Information Source that monitors the specific GCP zone containing your instances. The
```
monitored VM metadata can include predefined GCP properties (such as the project ID) and
```
```
user-defined properties (such as labels and network tags).
```
You can deploy the VM-Series firewall on a Google® Compute Engine instance in a network in
```
your virtual private cloud (VPC). The deployment types are:
```
Internet Gateway
The VM-Series firewall secures north-south traffic to and from the internet to protect applications
from known and unknown threats. A Google project can have up to five VPC networks. For a
typical example of an internet gateway, refer to the Google configuration examples.
```
In public cloud environments, it's a common practice to use a scale-out architecture (see the figure
```
```
below) rather than larger, higher performing VMs. This architecture (sometimes called a sandwich
```
```
deployment) avoids a single point of failure and enables you to add or remove firewalls as needed.
```
483
VM-Series Firewall on Google Cloud Platform
Segmentation Gateway
```
A segmentation gateway secures east-west traffic between virtual private clouds (VPCs) to ensure
```
data protection compliance and application access. The following figure shows a firewall securing
both north-south and east-west traffic.
VM-Series Public Cloud Deployments 484 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on Google Cloud Platform
Hybrid IPSec VPN
The VM-Series firewall serves as an IPSec VPN termination point, which enables secure
```
communications to and from applications hosted on the Google Cloud Platform (GCP).
```
The deployment in the figure below shows a site-to-site VPN from an on-premises network to a
VM-Series firewall deployed on GCP and an IPSec connection from an on-premises network to a
Google Cloud VPN gateway.
Live migration for VM firewall is unsupported in GCP. Initiating live migration can severely
degrade firewall network I/O traffic, causing packet processing to stall or fail completely.
VM-Series Public Cloud Deployments 485 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on Google Cloud Platform
Supported Deployments on Google Cloud Platform
Where Can I Use This? What Do I Need?
```
• Google Cloud Platform (GCP) VM-Series License (PAYG or BYOL)
```
VM-Series plugin
Panorama
Panorama plugin for GCP
You can deploy the VM-Series firewall on a Google® Compute Engine instance in a network in
```
your virtual private cloud (VPC). The deployment types are:
```
Internet Gateway
The VM-Series firewall secures North/South traffic to and from the internet to protect
applications from known and unknown threats. A Google project can have up to five VPC
networks. For a typical example of an internet gateway, refer to the Google configuration
examples.
```
In public cloud environments, it is a common practice to use a scale-out architecture (see the
```
```
figure below) rather than larger, higher performing VMs. This architecture (sometimes called a
```
```
sandwich deployment) avoids a single point of failure and enables you to add or remove firewalls
```
as needed.
VM-Series Public Cloud Deployments 486 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on Google Cloud Platform
Segmentation Gateway
```
A segmentation gateway secures East/West traffic between virtual private clouds (VPCs) to
```
ensure data protection compliance and application access. The following figure shows a firewall
securing both North/South and East/West traffic.
Hybrid IPSec VPN
The VM-Series firewall serves as an IPSec VPN termination point, which enables secure
```
communications to and from applications hosted on Google Cloud Platform (GCP).
```
The deployment in the figure below shows a site-to-site VPN from an on-premises network to a
VM-Series firewall deployed on GCP and an IPSec connection from an on-premises network to a
Google Cloud VPN gateway.
VM-Series Public Cloud Deployments 487 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on Google Cloud Platform
VM-Series Public Cloud Deployments 488 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on Google Cloud Platform
Minimum System Requirements for the VM-Series
Firewall on GCP
Where Can I Use This? What Do I Need?
```
• Google Cloud Platform (GCP) VM-Series License (PAYG or BYOL)
```
VM-Series plugin
Panorama
Panorama plugin for GCP
Choose a VM-Series Firewall Licenses for Public Clouds and a license method: Bring your
```
own license (BYOL) or pay-as-you-go (PAYG). To deploy a VM-Series firewall on a Google
```
Compute Engine instance, you must choose a machine type that supports the VM-Series System
Requirements for your license.
A single Google Compute Engine instance supports up to eight network interfaces. If you want to
configure eight interfaces, choose n1-standard-8 or a larger machine type.
Bundles 1 and 2Capacity BYOL
PAYG Marketplace
VM-100 firewall
VM-200 firewall
VM-300 firewall
VM-1000-HV firewall
VM-500 firewall
VM-700 firewall
The VM-Series firewall supports the predefined standard machine types listed below. You can
choose a higher performing machine type or you can create your own custom machine type if the
resource requirements are compatible with your VM-Series firewall license.
• n1-standard-4
• n1-standard-8
• n1-standard-16
VM-Series Public Cloud Deployments 489 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on Google Cloud Platform
• n2-standard-4
• n2-standard-8
• n2-standard-16
• n2-standard-32
Custom Machine Types:
• e2-standard-4
• e2-standard-8
• e2-standard-16
• e2-standard-32
General Requirements
The components in this checklist are common to deploying a VM-Series firewall that you
manage directly or with Panorama. Additional requirements apply for the Panorama plugin for
services such as Stackdriver monitoring, VM monitoring, auto scaling, or securing Kubernetes
deployments.
Always consult the Compatibility Matrix for Panorama plugin information for public clouds. This
release requires the following software:
• GCP account—You must have a GCP user account with a linked email address and you must
know the username and password for that email address.
• Google Cloud SDK—If you have not done so, install Google Cloud SDK, which includes Google
Cloud APIs, gcloud and other command-line tools. You can use the command-line interface to
deploy the firewall template and other templates.
• PAN-OS on VM-Series firewalls on GCP—VM-Series firewalls running a PAN-OS version
available from the Google Marketplace.
• VM-Series firewalls—you can deploy the VM-Series firewalls that you want to manage from
Panorama, through the Google Cloud Platform using a Palo Alto Networks image from the
Google Marketplace.
• VM-Series Licenses—You must license a VM-Series firewall to obtain a serial number. You
will need a serial number to add a VM-Series firewall as a Panorama managed device. If
you're using the Panorama plugin for GCP to deploy VM-Series firewalls you must supply a
BYOL auth code. The Google Marketplace handles your service billing, but the firewalls you
deploy will directly interface with the Palo Alto Networks licensing server.
• VM-Series plugin on the firewall—VM-Series firewalls running PAN-OS 9.0 and later include
the VM-Series plugin, which manages integration with public and private clouds. As shown
in the Compatibility Matrix, the VM-Series plugin has a minimum version that corresponds
to each PAN-OS release.
The VM-Series plugin version is automatically upgraded following a major PAN-OS upgrade.
For minor releases it's up to you to determine whether a VM-Series plugin upgrade is
necessary, and if so, perform a manual upgrade. See Install the Panorama Plugin for GCP.
VM-Series Public Cloud Deployments 490 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on Google Cloud Platform
• Panorama running in Management mode—A Panorama physical or virtual appliance running
a PAN-OS version that is the same or later than the managed firewalls. Virtual instances don't
need to be deployed in GCP.
• You must have a licensed version of Panorama.
• Panorama must have network access to the VPCs in which the VMs you want to manage
are deployed.
• If you intend to manage VMs deployed in GCP, or configure features such as auto scaling,
your PAN-OS, and VM-Series plugin versions must meet the Public Cloud requirements to
support the Panorama plugin for GCP.
• VM-Series plugin on Panorama. See Install the Panorama Plugin for GCP
• Panorama plugin for GCP version 2.0.0—The GCP plugin manages the interactions required
to license, bootstrap, and configure firewalls deployed with the VM Monitoring or auto scaling
templates. The GCP plugin, in conjunction with the VM Monitoring or auto scaling templates,
uses Panorama templates stacks, and device groups to program NAT rules that direct traffic to
managed VM-Series firewalls.
See Install the Panorama Plugin for GCP.
VM-Series Public Cloud Deployments 491 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on Google Cloud Platform
Create a Custom VM-Series Firewall Image for Google
Cloud Platform
Where Can I Use This? What Do I Need?
```
• Google Cloud Platform (GCP) VM-Series License (PAYG or BYOL)
```
VM-Series plugin
Panorama
Panorama plugin for GCP
Palo Alto Networks posts VM-Series firewall base image versions or minor versions with critical
```
fixes (such as PAN-OS 11.0) on the Google Cloud Platform (GCP) Marketplace. These versions are
```
available when you deploy a VM-Series firewall from the GCP Marketplace. However, you might
need to deploy a PAN-OS version that is earlier or later than the Marketplace version.
To deploy a VM-Series firewall version that is not available on the Marketplace, you can create a
custom VM-Series firewall image with a BYOL license.
The basic steps to create a custom firewall from a firewall instance are as follows:
• Deploy a new firewall from the GCP Marketplace.
• Activate your firewall license, download your desired PAN-OS software version to your
firewall, use Dynamic Update to update your Applications and Threats content, and deactivate
the firewall license.
• Perform a private data reset from the GCP console.
• Create a custom image from the upgraded firewall.
STEP 1 | Before you create your custom image, review your accounts, plan and create the networks
for VM-Series firewall deployment, for the VM-Series firewall deployment, and plan your
network interfaces.
STEP 2 | Deploy the VM-Series Firewall from Google Cloud Platform Marketplace.
You cannot create an image from an existing firewall. Starting from the GCP Marketplace
ensures that your custom image can be licensed.
```
STEP 3 | (BYOL Only)Activate the license.
```
1. Select Device > Licenses and activate the license.
The firewall reboots when licensing is complete.
2. Log in to the firewall.
VM-Series Public Cloud Deployments 492 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on Google Cloud Platform
STEP 4 | Upgrade to your preferred PAN-OS version and install software updates.
1. Select Device > Software > Check Now and download your required PAN-OS version.
If you do not see the version you want, download it from the Palo Alto Networks
customer support website as follows.
1. Log in and select Updates > Software Updates.
From the Filter By list, choose PAN-OS for VM-Series.
2. Select a PAN-OS version and download it to your local machine.
3. On your VM-Series firewall, Select Device > Software and Upload your PAN-OS
version from your local machine to your device.
2. Install your chosen version.
3. Upgrade the PAN-OS software version.
4. Select Device > Dynamic Updates and upgrade your Applications and Threats and any
other content you want to include in your base image.
```
STEP 5 | (BYOL Only) Deactivate the VM from the firewall.
```
If you do not deactivate the license, you lose the license that you applied on your
firewall instance.
1. Select Device > Licenses and under License Management, select Deactivate VM.
2. Select Complete Manually, and Export the license token.
3. Return to the Palo Alto Networks customer support website, select Assets > VM-Series
```
Auth-Codes > Deactivate License(s) and upload the license token.
```
STEP 6 | Perform a private data reset.
A private data reset removes all logs and restores the default configuration.
The system disks are not erased, so the content updates from 4 are intact.
1. Access the firewall CLI and keep it active.
2. From the GCP console, delete SSH keys from your VM-Series firewall.
1. Select Compute Engine > VM Instances and select your instance name.
2. In the Details view, select EDIT.
3. Under SSH Keys, click the Show and edit link and click X to remove any SSH keys.
4. Save your changes.
3. (Optional) Export a copy of the configuration.
4. In the CLI, request a private data reset.
request system private-data-reset shutdown
Enter y to confirm.
Wait for firewall to shutdown.
5. From the GCP console, select Compute Engine > VM instances and STOP the firewall.
VM-Series Public Cloud Deployments 493 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on Google Cloud Platform
STEP 7 | Create a custom image in the GCP console.
These steps are based on Creating, deleting, and deprecating custom images.
1. Select Compute Engine > Images > Create Image.
2. Name your image and select the Google-managed key (see Google-managed encryption
```
keys).
```
3. Select Disk for the Source, and for the Source disk, select your stopped VM-Series
firewall VM and click Create.
4. (Optional) When the image is complete, click the Equivalent REST link, and from the
REST response, copy the selfLink. This is the URI link for any type of CI/CD pipeline that
you require.
For example: projects/my-vpc-vpcID/global/images/pa-vm-8-1-9
Using this link points directly to your image so you can use it in a template or a script.
For example:
```
sourceImage: https://www.googleapis.com/compute/v1/projects/
```
```
{{project}}/global/images/pa-vm-8-1-9}
```
VM-Series Public Cloud Deployments 494 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on Google Cloud Platform
System Disk Size Increase on Google Cloud Platform
Where Can I Use This? What Do I Need?
• VM-Series 10.2.17 PAN-OS 11.1 or later
```
60 GB or 80GB disk (If you use /opt/
```
panlogs for local logging, create an 80GB
disk so that the partition has enough
```
space.) Ensure the new disk includes the
```
identical guest-os-features as the primary
drive.
gcloud access in Cloud Shell, or on a
machine where gcloud is authenticated
Permission to stop VM instances and
attach and detach disks in Compute Engine
VM-Series software firewalls deployed from older base images such as 10.2.x keep the original,
smaller /dev/root partitions, even after you upgrade PAN-OS to 11.1.x or 11.2.x. Cloning the
system disk to a 60GB or 80GB disk increases the root partition across both sysroots from 6.9G
to 12G.
The firewall has to reboot twice during this procedure, so plan a maintenance window.
Your software version and configuration don't change.
STEP 1 | Check the current disk layout and software version.
admin> show system disk-space
admin> show system info | match sw
STEP 2 | Stop the firewall.
1. In the Google Cloud console, select Compute Engine > VM instances.
2. Select the firewall instance.
3. Click Stop.
STEP 3 | Create a new blank disk of the same type as the original disk.
gcloud compute disks create <new_disk_name> \
--size=60GB \
--zone=<zone> \
--type=pd-ssd \
--guest-os-features=GVNIC,MULTI_IP_SUBNET
• If you use /opt/panlogs for local logging, create an 80GB disk so that the
partition has enough space.
• Ensure the new disk includes the identical guest-os-features as the primary drive.
VM-Series Public Cloud Deployments 495 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on Google Cloud Platform
STEP 4 | Attach the new disk to the firewall.
1. Click Edit.
2. Under Additional disks, click Attach existing disk.
3. For Disk, choose the new disk.
4. Click Save.
STEP 5 | Click Start/Resume.
STEP 6 | Connect to the firewall through the serial console, or log in to the CLI using SSH.
STEP 7 | List the available target disks.
admin> request system clone-system-disk target ?
STEP 8 | Clone the system disk to the new disk and enter Y when prompted.
admin> request system clone-system-disk target sdb
VM-Series Public Cloud Deployments 496 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on Google Cloud Platform
STEP 9 | Monitor the console. The cloning procedure requires approximately 20 to 30 minutes. Verify
the drive transfer is fully finished prior to proceeding.
STEP 10 | Stop the firewall.
VM-Series Public Cloud Deployments 497 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on Google Cloud Platform
STEP 11 | Detach both disks.
1. Click Edit.
2. Under Additional disks, detach the new disk.
3. Under Boot disk, click Detach boot disk to detach the old disk.
4. Click Save.
VM-Series Public Cloud Deployments 498 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on Google Cloud Platform
STEP 12 | Set the new disk as the boot disk.
1. Click Edit.
2. Under Boot disk, click Configure boot disk.
3. On the Existing disks tab, choose the new disk.
4. Click Select, and then click Save.
STEP 13 | Click Start/Resume.
STEP 14 | Verify that the new partitions are in use and that the software version is unchanged.
admin> show system disk-space
admin> show system info | match sw
```
STEP 15 | (Optional) Delete the old boot disk to avoid storage charges.
```
VM-Series Public Cloud Deployments 499 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on Google Cloud Platform
Prepare to Set Up VM-Series Firewalls on Google Public
Cloud
Where Can I Use This? What Do I Need?
```
• Google Cloud Platform (GCP) VM-Series License (PAYG or BYOL)
```
VM-Series plugin
The process to Deploy the VM-Series Firewall from Google Cloud Platform Marketplace requires
preparation tasks.
If you're deploying using the Google Marketplace, you must create your project networks and
subnetworks, and plan networks and IP address assignments for the VM-Series firewall interfaces
in advance. During the deployment, you must choose from existing networks and subnetworks.
Refer to the following topics when planning your deployment:
Prepare to Deploy from the GCP Marketplace
Review these requirements to ensure that you have proper accounts and permissions before you
```
use the Google Marketplace to deploy the firewall on a Google Compute Engine (GCE) instance.
```
General Accounts and Permissions
You, and any users you allow, must have the following minimal roles or equivalent Identity and
```
Access Management (IAM) permissions to connect to the VM-Series firewall:
```
Compute Viewer—Compute Viewer enables you to get and list compute engine resources
without being able to read the data stored on those resources.
Storage Object Viewer—Enables you to bootstrap using a Google storage bucket in the
same project.
Users in your organization might have IAM permissions or predefined roles that
are more permissive than required. Ensure that you appropriately restrict VM-Series
firewall access.
You can also restrict access with service accounts, as described in Google Authentication
Methods.
Monitoring Metric Writer—Required for Stackdriver.
Available Google Resources
Your project must have sufficient resources to deploy the VM-Series firewall as a Google
Compute Engine instance. If you're deploying a GCP Marketplace solution, determine whether
the solution deploys other VMs in addition to the firewall. In the Google Cloud Console, select
IAM & admin > Quotas to review the resource quotas for your project and the networks and disk
space consumed. If you're running out of resources, you can ask Google to allocate more for your
organization.
VM-Series Public Cloud Deployments 500 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on Google Cloud Platform
Google Authentication Methods
GCP supports multiple ways to connect to an instance. You can authenticate with a service
account or an SSH key pair.
1. Service Accounts—Service Accounts apply to applications or VMs—not to end users. They are
commonly used to control access when you use programs or scripts, or when you access the
firewall from the gcloud command line. If you're using Google Service Accounts to authenticate
```
instances or applications, you must know the email address for the account(s). Refer to
```
Creating and Managing Service Account Keys.
Using a service account is necessary if you want to connect to the VM-Series firewall from
outside the project—either from a different project or from the command line. For example, if
you want to enable a physical next generation firewall to monitor your VM-Series firewall, you
must save the VM-Series firewall service account information to a JSON file. In the physical
firewall, you upload the file when you configure the connection.
1. Select IAM & Admin > Service accounts and choose +Create Service Account.
Enter the service account name and description, and click Create.
2. Select a role type from the drop menu, and on the right, select an appropriate access level.
For example, select Project > Editor. You can select multiple roles for a service account.
When you're finished, click Continue.
3. Grant specific users permission to access this service account. Select members from the
Permissions column on the right to give them permission to access the roles in the previous
step.
2. SSH Keys—If you deploy the VM-Series firewall from the Marketplace, you must supply one
Open SSH key in RSA format for the Google Compute Engine instance metadata.
The VM-Series firewall only accepts one key at deployment.
At deployment time, you paste the public key into the Marketplace deployment, as described in
SSH Key Pair. After deployment, you use the private key to SSH in to the firewall to configure
the administrator account. To add users, see Manage Firewall Administrators.
You can authenticate in several ways:
• Create service accounts for instances—You can create a service account for a specific instance
or instance group, and grant specific permissions, which in turn can be granted to users.
VM-Series Public Cloud Deployments 501 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on Google Cloud Platform
• Use the default service account for your project—If you're using the Google Cloud Platform
```
(GCP) Console, then you logged in with your email address and can access a GCE instance
```
based on whatever permissions or roles the project administrator assigned to your account.
Every Google Compute Engine instance created with the Google Cloud Console or the gcloud
command-line tool has a default service account with the name in email address format:
<project-number>-compute@developer.gserviceaccount.com
To see the service account name for the firewall instance, view the instance details and scroll
```
to the bottom (refer to the Compute Engine default service account).
```
The default service account can manage authentication to VMs in the same project as a VM-
Series firewall. Access scopes allow the firewall to initiate API calls to VMs in the Google Cloud
project.
• Use IAM permissions and the Google APIs—If you use the Google SDK APIs and gcloud, then
you must call the APIs to authenticate.
• You typically use the Google SDK when you want to manage the firewall from a command
line or you want to run a script to configure the firewall.
• You need to access the Google APIs if a virtual machine you connect to has a custom image
with applications that require Google APIs.
SSH Key Pair
When you deploy the VM-Series firewall from the Google Marketplace, you need an SSH key pair
to authenticate with the VM-Series firewall.
Create the key pair according to your key generator documentation. Don't edit the public
key file. Editing risks introducing illegal characters.
The VM-Series firewall manages authentication differently than GCE instances. After deployment,
you first login with the admin user. The VM-Series firewall default username is accepted only
once. After a successful login, you set an administrator username and password for the VM-Series
```
web interface (see Deploy the VM-Series Firewall from Google Cloud Platform Marketplace).
```
The Google Marketplace deployment interface SSH key field displays the following placeholder:
```
admin:ssh-rsa your-SSH-key
```
admin Is the VM-Series firewall administrator username required to login to the firewall for the
first time. You add the admin: prefix into the Marketplace field when you Deploy the VM-Series
Firewall from Google Cloud Platform Marketplace.
You can't login to the VM-Series firewall if you don't supply the entire public key, or your key has
illegal characters when you paste the key into the Marketplace SSH key field. When you SSH in to
the VM-Series firewall for the first time, the public key is transferred to the firewall.
If the public key is corrupted, you must delete the deployment and start over. Any networks and
subnetworks remain, but the firewall rules must be recreated.
VM-Series Public Cloud Deployments 502 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on Google Cloud Platform
STEP 1 | Create an SSH key pair and store the SSH Key pair in the default location for your operating
system mentioned in Locating an SSH key.
• Linux or macOS—Use ssh-keygen to create the key pair in your .ssh directory.
• Windows—Use PuTTYgen to create the key pair.
```
The content of the Key comment field does not matter to the VM-Series firewall; you can
```
```
accept the default (the key creation date) or enter a comment that helps you remember the
```
name of the key pair. Use the Save private key button to store the private key in your .ssh
directory.
STEP 2 | Select the full public key.
• Linux or macOS—Open your public key in a text editor and copy the public key.
• Windows—You must use the PuTTY Key Generator to view the public key. Launch
PuTTYgen, click Load, and browse to private key you saved in your .ssh directory.
In PuTTYgen, scroll down to ensure you select the entire key, right click, and choose Copy.
STEP 3 | Enter the public key in the SSH key field as detailed below.
1. In the Marketplace SSH key field, delete the placeholder text, and type:
```
admin:
```
Make sure there are no extra spaces following the colon.
2. Insert the cursor after admin: and choose Paste as plain text. The key must be on a
single line, as shown below:
3. Move the cursor to the end of the key, add a space, and type: admin
The final contents of the SSH key field must be:
```
admin:ssh-rsa [KEY] admin
```
VM-Series Public Cloud Deployments 503 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on Google Cloud Platform
STEP 4 | Check the key.
After the deployment, and before you attempt to login to the firewall, view the management
instance and check the key for linefeeds or extra spaces:
If the key is all on one line and the format is admin:ssh-rsa [KEY] admin, you're finished.
```
STEP 5 | (Optional) If something is wrong you must replace the key.
```
1. Click the X to delete the key, then click + Add item.
2. Enter the key as described in step 3. Now, the SSH key field must show:
```
admin:ssh-rsa [KEY] admin
```
3. Click Save to deploy the updated deployment.
4. Recheck the key.
```
Virtual Private Cloud (VPC) Network Planning
```
```
Before you deploy from the Google Market place, make a plan for VPC networks (referred to
```
```
as networks), subnetworks (also called subnets), and Google firewall rules. Create networks and
```
subnetworks before you start to Deploy the VM-Series Firewall from Google Cloud Platform
Marketplace.
The Marketplace deployment page displays only networks and subnetworks that exist
when you start the deployment. If a network is missing, you must exit the deployment,
create the network, and start over.
VPC networks—You must create a custom network specifically for each VM-Series firewall
network interface.
See VM-Series Firewall Licenses for Public Clouds to determine the number of network
interfaces needed based on your VM-Series firewall license. At a minimum, set up the three
VPC networks and subnets required to launch the VM-Series firewall.
```
A GCP project has a default network with preset configurations and firewall rules; you can
```
delete the default network, if unused.
By default, there are up to five networks in a project. Your GCP administrator can request
additional networks for your project.
To connect to the management interface, you must create a GCP firewall rule that allows
access. You can do this during the deployment if you choose Enable GCP Firewall rule
for connections to Management interface then supply a CIDR block for Source IP in GCP
Firewall rule for connections to Management Interface.
Be sure your networks include all instances you want to secure.
VM-Series Public Cloud Deployments 504 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on Google Cloud Platform
Subnetworks—A compute engine instance can support up to eight Layer 3 interfaces on a
single instance. The Management, Trust, and Untrust interfaces consume three interfaces and
you can create up to five additional dataplane interfaces. Typically the dataplane interfaces
represent application networks.
IP address—You supply IP address ranges when you create interface subnetworks, and you
have the option to enable an external address when you deploy a subnetwork.
• When you create a network subnet, you must specify an IP address range. This range is
used for your internal network, so it can't overlap with other subnets.
• During deployment, you can choose to enable an external IP address when you create a
network interface. By default, you're given an ephemeral IP address. You can't supply a
reserved static IP address during the deployment, but you can promote the ephemeral
```
address to a static IP address after you complete the deployment process (see Promoting an
```
```
ephemeral external IP address).
```
Network Interface Planning
When you deploy from Google Cloud Platform Marketplace, the default VM-Series firewall
deployment has three interfaces: the management plane interface and the Untrust and Trust
dataplane interfaces. You can define additional dataplane instances, depending on the available
```
compute resources on your VM; see VM-Series Firewall Licenses for Public Clouds.
```
All VM-Series firewall interfaces must be assigned an IPv4 address when deployed in a
public cloud environment. IPv6 addresses are not supported.
During the deployment you have the opportunity to name these interfaces.
Interface Order
When you deploy with Marketplace, the order of the network interfaces is predefined. The
management interface maps to eth0, Untrust to eth1, and Trust to eth2. Marketplace uses this
order because mapping the management interface to eth0 and the Untrusted interface to eth1 is
a requirement if you need to Swap the Management Interface for load balancing.
Management Interface
The first network interface you add is mapped to eth0 on the firewall and includes the option to
enable IP forwarding. You use this network interface to manage the VM-Series firewall. Typically,
this interface has an external IP address.
An external IP address is only required if a dataplane interface is attached to the public
subnet. At creation time, you can receive an ephemeral IP address and later promote it to
```
a static IP address after you complete the deployment (refer to Promoting an ephemeral
```
```
external IP address).
```
```
Dataplane Interfaces (Untrust, Trust)
```
When you deploy from Marketplace, the order in which you add interfaces is predetermined.
VM-Series Public Cloud Deployments 505 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on Google Cloud Platform
• You configure the Untrust interface after the management interface. This order means that
the untrusted interface is mapped to eth1. The Untrust interfaces are typically attached to the
public subnet, and have an external IP address.
An external IP address is only required if a dataplane interface is attached to the public
subnet. At creation time, you can receive an ephemeral IP address, then promote it to a
static IP address, as discussed in Promoting an ephemeral external IP address.
• The Trust interface follows the Untrust interface, and it's mapped to eth2. The Trust network
often does not have an external IP address. You can add any additional dataplane interfaces
after the Trust interface.
Additional Dataplane Interfaces
Plan interfaces for applications you must secure, such as web servers, databases, and other
applications in your network. You can create up to five additional dataplane interfaces in addition
to the three required to launch your firewall. Ensure that the applications you want to secure are
in networks that connect to the VM-Series firewall.
VM-Series Public Cloud Deployments 506 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on Google Cloud Platform
Deployment Models for VM-Series on GCP
```
Deploy your VM-Series firewall on Google Cloud platform (GCP) using any one of the following
```
deployment models:
• Autoscale Model
• Active/Passive Model
VPC Networks
At a minimum, the VM-Series requires 3 network interfaces with each belonging to separate VPC
```
networks: untrust (NIC0), management (NIC1), and trust (NIC2), with the ability to add up to 5
```
additional dataplane interfaces.
Google Cloud’s external load balancers can only distribute traffic to the primary interface
of a virtual machine. Therefore, when deploying the VM-Series, it is important to attach
the instance’s primary interface, NIC0, to the untrusted VPC, attach NIC1 to the
management VPC, and perform a management interface swap. This enables the untrust
dataplane interface to receive traffic from external load balancers.
Untrust VPC
```
The VM-Series untrust interface (NIC0) acts as the internet gateway for cloud resources within
```
the trust VPC, including as well as for cloud resources in networks connected to the trust VPC.
For outbound internet traffic, you can attach an External IP address to the untrust interface, or
deploy a Cloud NAT to an untrust VPC. For inbound internet traffic, you can use any of Google’s
external load balancers to distribute traffic to the VM-Series untrust interfaces for inspection.
```
Note: In the active/passive model, an external pass-through load balancer must be used for both
```
internet inbound and internet outbound traffic. This is because only the external pass-through
load balancer supports connection tracking.
Management VPC
```
The VM-Series management interface (NIC1), which is connected to the management VPC,
```
provides access to the VM-Series user interface and connects to Panorama or Strata Cloud
Manager for centralized management.
Trust VPC
```
The VM-Series trust interface (NIC2) is connected to a trust VPC network. It is recommended
```
to configure the trust interface as the backend service of an internal passthrough network load
balancer. Internal TCP/UDP Load Balancer. This setup facilitates traffic distribution for egress
traffic originating from the trust VPC or for workload VPCs linked to the trust VPC network.
It is common to use the trust VPC in the following ways:
• A shared VPC network that shares its subnets to various service projects within the Google
Cloud organization.
• A hub VPC network that provides transitive routing and inspection for multiple workload VPC
```
networks (spokes).
```
VM-Series Public Cloud Deployments 507 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on Google Cloud Platform
Workload VPCs
```
If you need to secure multiple VPC networks (workload VPCs), you can use either the VPC
```
peering architecture, the multiple network interface architecture, or a combination of both. In all
scenarios, routes in the workload VPCs must be configured to direct traffic to the internal load
balancer in the trust VPC.
```
To inspect inter-VPC traffic (i.e. VPC-to-VPC, VPC-to-on-premises, or VPC-to-internet traffic),
```
you can create custom static routes in the workload VPCs, using the internal load balancer in the
trust VPC as the next hop.
```
To inspect intra-VPC traffic (i.e. subnet-to-subnet within a VPC, or traffic within a subnet), you
```
can create policy based routes, using the internal load balancer in the trust VPC as the next hop.
Auto Scale Model
Where Can I Use This? What Do I Need?
```
• Google Cloud Platform (GCP) VM-Series License (PAYG or BYOL)
```
VM-Series plugin
Panorama
Panorama plugin for GCP
In the autoscale model, VM-Series are deployed to a zonal or regional managed instance group
```
(MIG). The MIG references an instance template which defines the VM-Series networking
```
configuration, bootstrap definitions, and the VM-Series image. Therefore, all of the firewalls
within the MIG are identical and are managed as a single entity using Panorama or Strata Cloud
Manager. Lastly, the MIG can be set as the backend service of Google Cloud’s Passthrough
```
Network Load Balancer (NLB), enabling traffic distribution among the VM-Series dataplane
```
interfaces.
VM-Series Public Cloud Deployments 508 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on Google Cloud Platform
The autoscale model provides is best for environments requiring the following:
• Ability to horizontally autoscale the VM-Series to meet the performance requirements of the
applications it is protecting.
• Cost optimization since all firewalls are actively securing traffic.
For more Information, see:
• Community Tutorial using Terraform
Session Resiliency with Autoscale Model
Session resiliency across the VM-Series MIG can be achieved by leveraging Memorystore
for Redis within GCP. Once configured, the Redis database synchronizes sessions across all
operational firewalls within the MIG. In the event of a firewall or zone failure, the passthrough
network load balancers transfer sessions from the failed firewall to any available firewalls within
the MIG, thus maintaining session continuity.
It is recommended to deploy VM-Series using the session resiliency brings you the following
```
benefits:
```
• Cost optimization, scalability, and simplified upgrading through a scale-out architecture.
VM-Series Public Cloud Deployments 509 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on Google Cloud Platform
• Session Continuity in case of an NGFW’s failure.
• The clustering in the cloud mode of VM-Series deployment is supported on PAN-OS
version 11.1 and above only.
• Network Load Balancer only syncs the sessions with the Redis database. The NGFW
NAT tables are not synced.
Active/Passive HA Model
Where Can I Use This? What Do I Need?
```
• Google Cloud Platform (GCP) VM-Series License (PAYG or BYOL)
```
VM-Series plugin
Panorama
Panorama plugin for GCP
In the active/passive HA model, each VM-Series firewall belongs to an unmanaged instance
```
group across separate zones within the same region. Only the primary (active) VM-Series firewall
```
receives network traffic from Google Cloud load balancers. The health check configured on the
load balancers determines the HA state of the primary VM-Series firewall. If the health check fails
on the primary VM-Series firewall, the load balancers use connection tracking to carry the active
sessions to the secondary VM-Series firewall. At that point, the secondary VM-Series firewall
becomes the primary firewall while maintaining session continuity.
This model is suited for environments with any or all of the following requirements:
• Maintaining session continuity through stateful failover between the VM-Series firewalls.
• Horizontal scaling of the VM-Series for performance is not required.
• Inability to centrally manage the firewalls using Panorama or Strata Cloud Manager.
• Establishing IPsec tunnels through the load balancers to the VM-Series firewall.
• Preserving the original client IP address for internet inbound traffic to internal applications
protected by the VM-Series firewalls.
VM-Series Public Cloud Deployments 510 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on Google Cloud Platform
For more Information, see:
• Community Tutorial using Terraform
• After deploying the VM-Series firewall, the load balancer's health checks will only pass on the
active VM-Series firewall. This is because the dataplane of the passive firewall is inactive and
VM-Series Public Cloud Deployments 511 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on Google Cloud Platform
is unable to pass the health checks. During a failure event, when the passive firewall becomes
active, along with its dataplane, the health checks will pass.
• Unlike the autoscale model which uses a Cloud NAT or public IP address, traffic outbound to
the internet from the trust VPC uses a forwarding rule on the external load balancer as the
translated address.
VM-Series Public Cloud Deployments 512 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on Google Cloud Platform
Deploy the VM-Series Firewall from Google Cloud
Platform Marketplace
Where Can I Use This? What Do I Need?
```
• Google Cloud Platform (GCP) VM-Series License (PAYG or BYOL)
```
VM-Series plugin
Panorama
Panorama plugin for GCP
To deploy the VM-Series firewall using the GCP market place template, you must first create a
VPC Network for each interface on the firewall. After you deploy the firewall from the Google
Marketplace, you can log in to the firewall to adjust the configuration to work within your GCP
VPC configuration. You can also enable monitoring so you can collect metrics that enable you to
improve resource management or create Security policy rules that automatically adapt to changes
in your application environment.
You can use Google® Cloud Platform Marketplace to deploy the VM-Series firewall on a fixed
```
vCPU capacity license (VM-Series Models). The licensed images available from public clouds are:
```
• VM-Series Next-Generation Firewall Bundle 1
• VM-Series Next-Generation Firewall Bundle 2
```
• VM-Series Next-Generation Firewall (BYOL)
```
The Marketplace deploys an instance of the VM-Series firewall with a minimum of one
```
management interface and two dataplane interfaces (Trust and Untrust). You can add additional
```
dataplane interfaces for up to five Google Compute Engine instances in your virtual private cloud
```
(VPC).
```
Before you deploy the VM-Series firewall, you must create or choose a project in your
organization and create any networks and subnets that will connect to the firewall, as described in
VPC Network Planning and Network Interface Planning.
You cannot attach multiple network interfaces to the same VPC network. Every interface you
create must have a dedicated network with at least one subnet. Ensure that your networks
include any additional dataplane instances you create.
All VM-Series firewall interfaces must be assigned an IPv4 address when deployed in a
public cloud environment. IPv6 addresses are not supported.
STEP 1 | Choose a Bootstrap Method.
VM-Series Public Cloud Deployments 513 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on Google Cloud Platform
STEP 2 | Locate the VM-Series firewall listing in the Marketplace.
1. Log in to the Google Cloud Console.
2. From the Products and Services menu, select Marketplace.
3. Search for VM-Series.
4. Select one of the VM-Series firewall licensing options.
STEP 3 | Click Launch on Compute Engine.
STEP 4 | Name the instance and choose resources.
1. Enter the Deployment Name (this name is displayed in the Deployment Manager). The
name must be unique and cannot conflict with any other deployment in the project.
2. Select a Zone. See Regions and Zones for a list of supported zones.
3. Select a Machine Type based on the VM-Series System Requirements for your license
and the Minimum System Requirements for the VM-Series Firewall on GCP.
STEP 5 | Specify instance metadata.
The options Bootstrap Bucket and Interface Swap affect the initial configuration the first time
the VM-Series firewall boots.
1. Bootstrap Bucket (Optional)—If you plan to use a bootstrap file, enter the name of
a storage bucket, or the path to a folder within the storage bucket, that contains the
bootstrap package. You need permission to access the storage bucket. For example:
vmseries-bootstrap-gce-storagebucket=<bucketname>
or
vmseries-bootstrap-gce-storagebucket=<bucketname/directoryname>
If you choose to bootstrap with custom metadata, continue to Step 6.
2. Interface Swap (Optional)—Swap the Management interface (eth0) and the first
```
dataplane interface (eth1) at deployment time. Interface swap is only necessary when
```
```
you deploy the VM-Series firewall behind Google Cloud Platform HTTP(S) Load
```
Balancing. For details, see Management Interface Swap for Google Cloud Platform Load
Balancing.
3. SSH key—Paste in the public key from an SSH key pair. Follow the instructions for your
OS in SSH Key Pair, to create, copy, and paste the key. Windows users must view the
key in PuTTY, copy from the user interface, and paste into Marketplace deployment.
If the key is not formatted properly, the VM-Series firewall does not allow you to
log in. You must delete the deployment and start over.
4. Click More to reveal additional metadata options. The options blockProjectKeys, and
```
enableSerialConsole are properties of the instance; you can change these metadata
```
values after a successful deployment.
```
• blockProjectKeys (Optional)—If you Block Project Keys, you can use only the public
```
SSH key you supply to access the instance.
```
• enableSerialConsole (Optional)—Interacting with the Serial Console enables you to
```
monitor instance creation and perform interactive debugging tasks.
VM-Series Public Cloud Deployments 514 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on Google Cloud Platform
STEP 6 | Specify custom metadata.
If you choose to bootstrap with custom metadata, add any key-value pairs that you did not add
in Step 5. See init-cfg.txt File Components for the list of key-value pairs. For example:
STEP 7 | Configure the boot disk.
1. Boot disk type—Select from SSD Persistent disk or Standard Persistent Disk. See Storage
Options.
2. Enter the Boot disk size—60GB is the minimum size. You can edit the disk size later but
you must stop the VM to do so.
STEP 8 | Configure the management interface.
1. Management VPC Network name—Choose an existing network
2. Management Subnet name—Choose an existing subnet.
3. Enable External IP for Management interface (Optional)—If you enable this option, you
can use the IP address assigned to the VM-Series firewall management interface to use
SSH to access the VM-Series firewall web interface.
4. Enable GCP Firewall rule for connections to Management interface (Optional)—This
option automatically creates a GCP firewall Allow rule for an external source IP address
that you supply.
5. Source IP in GCP Firewall rule for connections to Management Interface—If you Enable
GCP Firewall rule for connections to Management interface, enter a source IP address
or a CIDR block.
• Do not use 0.0.0.0/0. Supply an IP address or a CIDR block that corresponds to your
dedicated management IP addresses or network. Do not make the source network
range larger than necessary.
• Verify the address to ensure that you do not lock yourself out.
STEP 9 | Configure the Untrust dataplane interface.
1. Untrust VPC Network name—Choose an existing network.
2. Untrust Subnet name—Choose an existing subnet.
3. Enable External IP for Untrust—Enable GCP to provide an ephemeral IP address to act as
the external IP address.
VM-Series Public Cloud Deployments 515 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on Google Cloud Platform
STEP 10 | Configure the Trust dataplane interface.
1. Trust VPC Network name—Choose an existing network.
2. Trust Subnet name—Choose an existing network.
3. Enable External IP for Trust—Enable GCP to provide an ephemeral IP address to act as
the external IP address.
STEP 11 | Configure additional interfaces. You must enter the number of dataplane interfaces you want
```
to add; the default is 0 (none). The deployment page always displays fields for five additional
```
dataplanes numbered 4 through 8.
1. Additional Dataplane interfaces—Enter the number of additional dataplane instances.
```
If this number is 0 (default), dataplane numbers 4 through 8 are ignored even
```
if you fill out the interface fields. If, for example, you specify 2 and then fill out
information for three interfaces, only the first two are created.
2. Additional Dataplane # VPC name—Choose an existing network.
3. Dataplane # Subnet name—Choose a subnet that exists.
4. Enable External IP for dataplane # interface—Enable GCP to provide an ephemeral IP
address to act as the external IP address.
STEP 12 | Deploy the instance.
STEP 13 | Use Google Cloud Deployment Manager to view and manage your deployment.
STEP 14 | Use the CLI to change the administrator password on the firewall.
1. Log in to the VM-Series firewall from the command line. In your SSH tool, connect to the
External IP for the management interface, and specify the path to your private key.
Windows users: Use PuTTY to connect to the VM-Series firewall and issue command
line instructions. To specify the path to the private key, select Connection > SSH > Auth.
In Private key file for authentication: click Browse to select your private key.
2. Enter configuration mode:
VMfirewall> configure
3. Enter the following command:
VMfirewall# set mgt-config users admin password
4. Enter and confirm a new password for the administrator.
5. Commit your new password:
VMfirewall# commit
6. Return to command mode:
VMfirewall# exit
7. (Optional) If you used a bootstrap file for interface swap, use the following command to
view the interface mapping:
VMfirewall> debug show vm-series interfaces all
VM-Series Public Cloud Deployments 516 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on Google Cloud Platform
STEP 15 | Access the VM-Series firewall web interface.
1. In a browser, create a secure (https) connection to the IP address for the management
interface.
If you get a network error, check to see that you have a GCP firewall rule that allows the
connection.
2. When prompted, enter the username (admin) and the administrator password you
specified from the CLI.
3. (Optional) If you bootstrapped, then Verify Bootstrap Completion.
If you see problems, search the log information on the VM-Series firewall. Choose
Monitor > System and, in the manual search field, enter description contains
'bootstrap' and look for a message in the results that indicates that the bootstrap
was successful.
After you log in to the firewall, you can add administrators and create interfaces, zones, NAT
rules, and policy rules, just as you would on a physical firewall.
Management Interface Swap for Google Cloud Platform Load
Balancing
Where Can I Use This? What Do I Need?
```
• Google Cloud Platform (GCP) VM-Series License (PAYG or BYOL)
```
VM-Series plugin
Panorama
Panorama plugin for GCP
Because internal load balancing can send traffic only to the primary interface of the next hop
load-balanced Google Compute Engine instance, the VM-Series firewall must be able to use eth0
for dataplane traffic.
All VM-Series firewall interfaces must be assigned an IPv4 address when deployed in a
public cloud environment. IPv6 addresses are not supported.
The firewall can receive dataplane traffic on eth0 if the VM-Series firewall is behind the Google
Cloud Platform internal load balancing interface.
• The VM-Series firewalls secure traffic outbound directly to the internet without requiring a
VPN link or a Direct Connect link back to the corporate network.
• The VM-Series firewall secures an internet-facing application when there is exactly one back-
end server, such as a web server, for each firewall. The VM-Series firewalls and web servers
can scale linearly, in pairs, behind the Google internal load balancing address.
To allow the firewall to send and receive dataplane traffic on eth0 instead of eth1, you must swap
the mapping of the internal load balancing network interface within the firewall so that eth0 maps
to ethernet 1/1, and eth1 maps to the MGT interface on the firewall.
VM-Series Public Cloud Deployments 517 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on Google Cloud Platform
If possible, swap the management interface mapping before you configure the firewall and
define policy rules.
Swapping how the interfaces are mapped allows Google Cloud Platform to distribute and route
traffic to healthy instances of the VM-Series firewall located in the same or different zones.
Swap the Management Interface
You can swap the interfaces when you configure the firewall after it is created.
At creation— When you deploy the VM-Series firewall, you can enable interface swap in two
ways.
• Google Cloud Console — In the Create Instance form, enter a key-value pair in the Metadata
field, where mgmt-interface-swap is the key, and enable is the value.
• Bootstrap File — Create a bootstrap file the includes the mgmt-interface-swap operational
command in the bootstrap configuration, as described in Bootstrap the VM-Series Firewall on
Google Cloud Platform. In the Create Instance form, enter a key-value pair in the Metadata
field to enable the bootstrap option.
From the VM-Series firewall—Log in to the firewall, and Use the VM-Series Firewall CLI to Swap
the Management Interface. In operational mode, issue the following command:
set system setting mgmt-interface-swap enable yes
• Pick one method to specify the interface swap setting— the bootstrap configuration
```
file, the firewall CLI, or the Google Compute Engine instance Metadata field (accessed
```
```
from the Google Cloud Console). Using one method ensures predictable behavior on
```
the firewall.
From the Google Cloud Console you can't confirm whether you have swapped eth0
and eth1. After swapping, you must remember that load balancing is on eth0 and the
firewall management interface is eth1 so that you can properly configure Google Cloud
Platform load balancing, and create security policy rules to secure load balancing to
one or more VM-Series firewalls.
• If you configured the VM-Series firewall before swapping, check whether any IP
address changes for eth0 and eth1 impact policy rules.
VM-Series Public Cloud Deployments 518 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on Google Cloud Platform
Use the VM-Series Firewall CLI to Swap the Management
Interface
Where Can I Use This? What Do I Need?
```
• Google Cloud Platform (GCP) VM-Series License (PAYG or BYOL)
```
VM-Series plugin
Panorama
Panorama plugin for GCP
This task is only required if your architecture places the VM-Series firewall behind the
Google Cloud Platform internal load balancer.
```
If you did not specify metadata to swap the management interface (MGT) with the dataplane
```
interface when you deployed the firewall, you can use the CLI to enable the firewall to receive
dataplane traffic on the primary interface.
STEP 1 | Deploy the VM-Series Firewall from Google Cloud Platform Marketplace.
Before you proceed, verify that the firewall has a minimum of two network interfaces
```
(eth0 and eth1). If you launch the firewall with only one interface, the interface swap
```
command causes the firewall to boot into maintenance mode.
STEP 2 | On the Google Cloud Console, view the VM instance details to verify the network interface
IP addresses of the eth1 interface and verify that any security rules allow connections
```
(HTTPS and SSH) to the new management interface (eth1).
```
STEP 3 | Log in to the VM-Series firewall CLI and enter the following command:
set system setting mgmt-interface-swap enable yes
You can view the default mapping from the command line interface. The output is similar to
```
this:
```
> debug show vm-series interfaces all
Interface_name Base-OS_port
mgt eth0
Ethernet1/1 eth1
Ethernet1/2 eth2
```
STEP 4 | Confirm that you want to swap the interface (use the eth1 dataplane interface as the
```
```
management interface).
```
STEP 5 | Reboot the firewall for the swap to take effect:
request restart system
VM-Series Public Cloud Deployments 519 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on Google Cloud Platform
STEP 6 | Verify that the interfaces have been swapped:
debug show vm-series interfaces all
Enable Google Stackdriver Monitoring on the VM Series Firewall
Where Can I Use This? What Do I Need?
```
• Google Cloud Platform (GCP) VM-Series License (PAYG or BYOL)
```
VM-Series plugin
Panorama
Panorama plugin for GCP
A VM-Series firewall on a Google® Compute Engine instance can publish custom PAN-OS metrics
to Google Stackdriver. These metrics allow you to assess performance and usage patterns so that
you can manage your firewall resources accordingly.
Google Stackdriver Permissions
Authentication requirements vary based on whether you can use the default service account to
authenticate or need to use Google APIs to authenticate.
You can authenticate in two ways:
• Use the default service account for the VM-Series firewall instance—If you are using the
```
Google Cloud Platform (GCP™) Console, then you logged in with your email address and can
```
access the instance based on whatever permissions or roles the project administrator assigned
to your account.
• Use IAM permissions and the Google APIs—If you use the Google SDK APIs and gcloud, then
you must call the APIs to authenticate. You typically use the Google SDK when you want to
manage the firewall from a command line or you want to run a script to configure the firewall.
Every Google Compute Engine instance created with the Google Cloud Console or the gcloud
command line tool has a default service account with the name in email address format:
<project-number>-compute@developer.gserviceaccount.com
To see the service account name for the firewall instance, view the instance details and scroll to
```
the bottom (refer to the Compute Engine default service account).
```
The default service account can manage authentication for monitoring VMs in the same project as
a VM-Series firewall.
• Access scopes allow the firewall to initiate API calls to monitor VMs in a Google Cloud project.
• You don’t need to access the Google APIs unless one of the monitored virtual machines has a
custom image with applications that require Google APIs.
If you want to set up monitoring from a physical firewall or from a VM-Series firewall in a
different project, you must use the Google APIs to authenticate. There are two prerequisites:
• Google APIs must be installed.
VM-Series Public Cloud Deployments 520 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on Google Cloud Platform
• Your account must have the roles Monitoring Metric Writer and Stackdriver Account Viewer.
Enable Google Stackdriver
For a description of the PAN-OS metrics that you can publish to Google Stackdriver, see Custom
PAN-OS Metrics Published for Monitoring.
STEP 1 | Push PAN-OS metrics from a VM-Series firewall on a Google Compute Engine instance to
Stackdriver.
1. Log in to the web interface on the VM-Series firewall.
2. Select Device > VM-Series. Under Google Cloud Stackdriver Monitoring Setup, click
```
Edit ( ).
```
1. Check Publish PAN-OS metrics to Stackdriver.
2. Set the Update Interval (range is 1 - 60 minutes; default is 5). This is the frequency at
which the firewall publishes the metrics to Stackdriver.
3. Click OK.
3. Commit your changes.
Wait until the firewall starts to publish metrics to Stackdriver before you configure
alarms for PAN-OS metrics.
VM-Series Public Cloud Deployments 521 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on Google Cloud Platform
STEP 2 | Verify that you can see the metrics on Stackdriver.
1. In the Google Cloud Console, select Products and Services > Monitoring.
2. In Stackdriver, choose Resources > Metrics Explorer.
3. In the Find resource type and metric section, enter custom in the search field to filter
the PAN-OS metrics.
STEP 3 | Configure alerts and actions for PAN-OS metrics on Stackdriver. See Monitoring Quickstart
for Google Compute Engine and Stackdriver Introduction to Alerting.
Enable VM Monitoring to Track VM Changes on Google Cloud
```
Platform (GCP)
```
Where Can I Use This? What Do I Need?
```
• Google Cloud Platform (GCP) VM-Series License (PAYG or BYOL)
```
VM-Series plugin
Panorama
Panorama plugin for GCP
```
You can enable any firewall that runs PAN-OS 9.0 (virtual or physical) and above to monitor
```
application workloads deployed on Google Compute Engine instances. VM Monitoring enables
you to monitor a predefined set of metadata elements or attributes on the VM-Series firewall. In
the PAN-OS 9.1 Administrator’s Guide, see Attributes Monitored on Virtual Machines in Cloud
Platforms.
VM-Series Public Cloud Deployments 522 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on Google Cloud Platform
With an awareness of virtual machine adds, moves, and deletes within a Google VP. You can
create Security policy rules that automatically adapt to changes in your application environment.
```
As you deploy or move virtual machines, the firewall collects attributes (or metadata elements).
```
```
You can use this metadata for policy matching and to define Dynamic Address Groups (see Use
```
```
Dynamic Address Groups to Secure Instances Within the VPC).
```
You can configure up to 10 VM information sources on each firewall or on each virtual system
on a firewall capable of multiple virtual systems. Information sources can also be pushed using
Panorama templates.
To perform VM monitoring, you must have the IAM role Monitoring Metric Writer.
STEP 1 | Log in to your deployed firewall.
VM-Series Public Cloud Deployments 523 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on Google Cloud Platform
STEP 2 | Enable VM Monitoring.
1. Select Device > VM Information Sources.
2. Add a VM information source and enter the following information:
• Specify a Name to identify the instance that you want to monitor.
• Select the Google Compute Engine Type.
• Select Enabled.
• Choose the Service Authentication Type.
• If you choose VM-Series running in GCE, you're authenticating with the default
service account generated when an instance is created. This is part of the instance
metadata.
• If you want to monitor from a firewall outside the current project, choose Service
Account. Upload the service account credentials in JSON format. See Creating and
Managing Service Account Keys.
```
• (Optional) Modify the Update interval to a value between 5-600 seconds. By default
```
the firewall polls every 5 seconds. The API calls are queued and retrieved every 60
seconds, an update takes up to 60 seconds plus the configured polling interval.
```
• (Optional) To change the number of hours before timeout, check Enable timeout
```
```
when the source is disconnected and enter the timeout (hours) before the connection
```
```
to the monitored source is closed (range is 2 to 10; default is 2).
```
If the firewall can't access the host and the specified limit is reached, the firewall
closes the connection to the source.
• Click OK and Commit your changes.
VM-Series Public Cloud Deployments 524 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on Google Cloud Platform
STEP 3 | Verify the connection status.
If the connection status is pending or disconnected, verify that the source is operational and
that the firewall is able to access the source. If you use a port other than the management
```
(MGT) port for communicating with the monitored source, then you must change the service
```
```
route (select Device > Setup > Services, click Service Route Configuration, and modify the
```
```
Source Interface for the VM Monitor service).
```
Use Dynamic Address Groups to Secure Instances Within the VPC
Where Can I Use This? What Do I Need?
```
• Google Cloud Platform (GCP) VM-Series License (PAYG or BYOL)
```
VM-Series plugin
Panorama
Panorama plugin for GCP
```
In a dynamic environment such as the Google® Cloud Platform (GCP™), where you launch
```
new instances on-demand, the administrative overhead in managing Security policy can be
cumbersome. Using use dynamic address groups in policy enables agility and prevents disruption
in services or gaps in protection.
This workflow assumes that you have deployed the VM-Series firewall, configured some
applications on instances, and enabled Google Stackdriver monitoring. Follow the below steps to
configure the firewall to monitor the VPC.
VM-Series Public Cloud Deployments 525 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on Google Cloud Platform
STEP 1 | Label instances in the VPC.
A label is a name-value pair. You can label resources from the Google Cloud Console, from
```
Google API calls, or from the Google Cloud Shell. In this task, we are labeling instances;
```
however, labels can be applied to many resources, as described in Labeling Resources.
You can also add labels from the Instance browser.
The labels you create support your strategy for differentiating your resources in ways that are
useful to your Security policy.
STEP 2 | Create a Dynamic Address Group on the firewall.
1. Select Objects > Address Groups.
2. Add a Dynamic Address Group and specify a Name and a Description.
3. Set Type to Dynamic.
4. Define the match criteria.
1. Add Match Criteria and select the And operator.
2. Select the attributes to filter for or to match against.
5. Click OK.
6. Click Commit.
VM-Series Public Cloud Deployments 526 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on Google Cloud Platform
STEP 3 | Use the Dynamic Address Group in a Security policy rule.
Create a rule to allow internet access to any web server that belongs to the Dynamic Address
Group called my-data.
1. Select Policies > Security.
2. Add a rule and a Name for the rule and verify that the Rule Type is universal.
3. In the Source tab, add trust as the Source Zone.
4. In the Source Address section, Add your new my-data group.
5. In the Destination tab, add untrust as the Destination Zone.
6. In the Service/URL Category tab, verify that the service is set to application-default.
7. In the Actions tab, set the Action to Allow.
8. In the Profile Settings, set the Profile Type to Profiles and then attach the default
profiles for antivirus, antispyware, and vulnerability protection.
9. Click OK.
10. Click Commit.
STEP 4 | Verify that members of the Dynamic Address Group are populated on the firewall.
The policy will be enforced for all IP addresses that belong to this address group and that are
displayed here.
1. Select Policies > Security and select the rule.
2. Select Inspect from the drop-down. You can also verify that the match criteria are
accurate.
3. Click more to verify that the list of registered IP addresses is displayed.
Use Custom Templates or the gcloud CLI to Deploy the VM-Series
Firewall
Where Can I Use This? What Do I Need?
```
• Google Cloud Platform (GCP) VM-Series License (PAYG or BYOL)
```
VM-Series plugin
Panorama
Panorama plugin for GCP
The official VM-Series images published on Google Cloud Platform Marketplace are available
in the paloaltonetworksgcp-public project. You need to know the secure path to these
images if you want to call them from the gcloud command line, or refer to them in a template
you have written or adapted.
• BYOL: vmseries-byol-<version>
• PAYG Bundle 1: vmseries-bundle1-<version>
• PAYG Bundle 2: vmseries-bundle2-<version>
VM-Series Public Cloud Deployments 527 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on Google Cloud Platform
Use the gcloud CLI to find the current image names and project:
gcloud compute images list --project paloaltonetworksgcp-public
--no-standard-images
NAME PROJECT FAMILY DEPRECATED
STATUS
vmseries-bundle1-810 paloaltonetworksgcp-public
READY
vmseries-bundle2-810 paloaltonetworksgcp-public
READY
vmseries-byol-810 paloaltonetworksgcp-public
READY
Add the --uri flag to see the image paths:
gcloud compute images list --project paloaltonetworksgcp-public
--no-standard-images --uri
```
https://www.googleapis.com/compute/v1/projects/paloaltonetworksgcp-
```
public
/global/images/vmseries-bundle1-810
```
https://www.googleapis.com/compute/v1/projects/paloaltonetworksgcp-
```
public
/global/images/vmseries-bundle2-810
```
https://www.googleapis.com/compute/v1/projects/paloaltonetworksgcp-
```
public
/global/images/vmseries-byol-810
For an example, download the gcp-two-tier template from https://github.com/PaloAltoNetworks.
```
This template separates the image name (which includes the PAN-OS version) from the URL path.
```
```
In two-tier-template.py the image variable expects the image name; for example: vmseries-
```
byol-810. vm-series-template.py uses the values of COMPUTE_URL_BASE and sourceImage
to build the path.
Enable Session Resiliency on VM-Series for GCP
Where Can I Use This? What Do I Need?
```
• Google Cloud Platform (GCP) VM-Series License (PAYG or BYOL)
```
VM-Series plugin
Panorama
Panorama plugin for GCP
Session resiliency allows the VM-Series firewall to maintain session continuity during a failure
```
event. The GCP Network Load Balancer (NLB) can detect and deregister unhealthy VM-Series
```
firewalls deployed in a horizontally scalable cluster behind it. With session resiliency enabled,
the NLB rehashes existing traffic sessions flowing toward an unhealthy VM-Series and redirects
VM-Series Public Cloud Deployments 528 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on Google Cloud Platform
the traffic to a healthy VM-Series firewall. This allows a VM-Series firewall cluster to continue
inspecting long-lived application sessions, even in the case of VM-Series appliance failures.
Traffic inspection of the rehashed traffic flows is Layer 4 only. The VM-Series firewall
inspects traffic in new sessions up to Layer 7.
To maintain sessions failing over to healthy VM-Series firewalls, you must deploy a Standard-tier
Memorystore for Redis cache accessible to your VM-Series firewalls. The Redis cache maintains
session information. When your load balancer detects an unhealthy VM-Series firewall, the
load balancer rebalances traffic to a healthy VM-Series firewall. The healthy VM-Series firewall
accesses the Redis cache for session information and continues to inspect and forward the
existing traffic.
Your load balancer must meet the following requirements to support session resiliency.
• Your load balancer must be an Internal pass-through Network Load Balancer
• Set your load balancer connection persistence on unhealthy nodes to NEVER_PERSIST.
Your Memorystore for Redis instance must meet the following requirements to support session
resiliency on the VM-Series firewall.
• Standard tier
• Deploy the Redis cache in the same region and zone as your VM-Series firewall instances
• From the Network drop-down, select the VPC network associated with the VM-Series firewall
management interface
• Enable AUTH to limit access to only trusted users
• Enable In-Transit Encryption to encrypt connections to the Redis cache using TLS
When sizing your Memorystore for Redis, use the following guidelines.
• Base the size of the Redis cache on the maximum number of sessions supported by your VM-
Series firewall instance. See Maximum Limits Based on Tier and Memory to the maximum
sessions for your firewall.
• When session resiliency is enabled, the maximum number of sessions is capped at 70% of
the amount listed in the link above. For example, if your firewall supports up to 10,000,000
sessions, the maximum is 7,000,000 with session resiliency.
• Each redis entry per session uses approximately 128 bytes. Therefore, one VM-Series firewall
that supports 10,000,000 sessions requires approximately 1.3 GB of storage. And a cluster of
10 VM-Series firewalls requires at least 13 GB.
• Use the following formula to calculate the redis requirements.
```
(128 x <number of sessions>) x 10-9 = require redis cache size per firewall.
```
VM-Series Public Cloud Deployments 529 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on Google Cloud Platform
```
Session resiliency can't be enabled on existing VM-Series firewall instances; only on newly
```
deployed instances.
Enable session resiliency on the VM-Series firewall by passing the configuration as part of a
bootstrapping init-cfg.txt file or in the user data field.
Bootstrap Parameter Description
op-command-modes=mgmt-interface-
swap
Allows you to swap the management interface
```
(MGT) with the dataplane interface (ethernet
```
```
1/1) when deploying the firewall. For details,
```
see Management Interface Swap for Google
Cloud Platform Load Balancing.
plugin-op-commands=set-sess-
```
ress:True
```
Enables session resiliency.
redis-endpoint= Provide the IP address or FQDN and port of
your Redis endpoint.
redis-auth= Optional The auth code your VM-Series
firewall uses to connect with the Redis
endpoint.
redis-certificate= OptionalThe root CA certificate string used to
connect to the Redis endpoint. The certificate
must be a base64-encoded string using utf-8
encoding.
STEP 1 | Deploy your Redis cache.
VM-Series Public Cloud Deployments 530 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on Google Cloud Platform
STEP 2 | Prepare your boostrap file.
op-command-modes=mgmt-interface-swap
plugin-op-commands=set-sess-ress:True
redis-endpoint=<redis-IP-address:port>
redis-auth=<redis-auth-code>
redis-certificate=
STEP 3 | Bootstrap your VM-Series firewalls.
STEP 4 | Log in to the firewall.
STEP 5 | Create an address object for the load balancer frontend IP address.
1. Select Objects > Address and click Add.
2. Enter a descriptive Name.
3. Set the Type to IP Netmask and enter the load balancer frontend IP address.
4. Click OK.
STEP 6 | Create a loopback interface to send health check packets to the load balancer.
1. Select Networking > Interfaces > Loopback and click Add.
2. Enter a descriptive Name.
3. On the Config tab, set the Virtual Router to default and the Security Zone to your trust
zone.
4. On the IPv4 tab, add the address object you created previously.
5. Click OK.
STEP 7 | Create a Management Profile.
1. Select Network > Network Profiles > Interface Mgmt and click Add.
2. Enable Ping, SSH, HTTPS, and SNMP.
Don't enable HTTP or Telnet because those protocols transmit in cleartext and
therefore are not secure.
3. Click OK.
STEP 8 | Add your Management Profile to your loopback interface.
1. Select NetworkInterfaces, select your loopback interface.
2. Select Advanced > Other info and select the Interface Management Profile you just
added.
3. Click OK.
STEP 9 | Commit your changes.
VM-Series Public Cloud Deployments 531 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on Google Cloud Platform
Use VM-Series Firewall to Configure NPTv6 Policy for
```
IPv6 Forwarding Rule on Google Cloud Platform (GCP)
```
This section shows a use case to test the inbound internet traffic destined to IPv6 forwarding rule
```
to the web app on internal-vm in the trust VPC on the Google Cloud Platform (GCP).
```
Where Can I Use This? What Do I Need?
```
• Google Cloud Platform (GCP) VM-Series License (PAYG or BYOL)
```
VM-Series plugin
Panorama
Panorama plugin for GCP
For this workflow, deploy and configure the VM-Series firewall in GCP. Create an NPTv6 policy to
translate traffic destined to the IPv6 forwarding rule to the web app on internal-vm, and test the
inbound internet traffic through the VM-Series firewall.
VM-Series firewalls add security to the NPTv6 traffic on GCP.
Architecture
Figure 6: VM-Series firewall resource deployed in GCP
VM-Series Public Cloud Deployments 532 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on Google Cloud Platform
The architecture shows the VM-Series deployed with 3 network interfaces, each belonging to
a dual-stack subnet, and belongs to an unmanaged instance group that serves as the backend
service of an external pass-through load balancer.
The load balancer is configured with IPv4 and IPv6 frontend addresses to distribute internet
inbound traffic to the untrust interface. The test workloads are deployed to test north-south
traffic. The external-vpc contains an Ubuntu VM to test internet inbound traffic through the VM-
Series to the internal-vm in the trust network.
```
Prerequisites:
```
• Google Cloud project
• Access to Google Cloud Shell with permissions to deploy the resources in GCP
• If using BYOL, a VM-Series auth key to license the firewall
Deploy Resources in GCP Using Gcloud
Create the cloud resources needed to support the VM-Series IPv4/IPv6 topology. This includes,
VPC networks, firewall rules, instance groups, load balancers, and the VM-Series compute
instances.
Create VPC Networks
Create the VPC networks for the VM-Series network interfaces. The table below describes each
VPC network’s function as it relates to the VM-Series firewalls.
VPC NIC Description
UNTRUST NIC0 Serves as the internet gateway for cloud resources
deployed or connected to the trust-vpc.
MGMT NIC1 Serves as the VM-Series MGT and HA1 interface.
TRUST NIC2 Serves as the default gateway for cloud resources
deployed or connected to the trust-vpc.
STEP 1 | In GCP cloud shell, enable the required Google Cloud APIs: .
gcloud services enable compute.googleapis.com
STEP 2 | Set your deployment project, region, and zone:
gcloud config set project PROJECT_ID
gcloud config set compute/region REGION
gcloud config set compute/zone ZONE
VM-Series Public Cloud Deployments 533 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on Google Cloud Platform
STEP 3 | Set environment variables to specify the deployment project, region, zone, and naming
```
prefix:
```
export PREFIX=panw
export CIDR_MGMT=10.0.0.0/28
export CIDR_UNTRUST=10.0.1.0/28
export CIDR_UNTRUST_LB=10.0.1.16/28
export CIDR_TRUST=10.0.2.0/28
export MGMT_SOURCE_RANGES=0.0.0.0/0
Variable Definition
```
PREFIX A string appended to the start of a resource’s name (i.e. $PREFIX-vpc).
```
CIDR_<NAME> The prefixes for the subnets to be created in each VPC network.
MGMT_SOURCE_RANGES A list of IPv4/IPv6 addresses, which can access the VM-Series MGT interface.
STEP 4 | Create the mgmt-vpc, untrust-vpc, and trust-vpc networks with their subnets:
gcloud compute networks create $PREFIX-mgmt-vpc \
--subnet-mode=custom
gcloud compute networks create $PREFIX-untrust-vpc \
--subnet-mode=custom
gcloud compute networks create $PREFIX-trust-vpc \
--subnet-mode=custom \
--enable-ula-internal-ipv6
gcloud compute networks subnets create $PREFIX-mgmt-subnet \
--network=$PREFIX-mgmt-vpc \
--range=$CIDR_MGMT
gcloud compute networks subnets create $PREFIX-untrust-subnet \
--network=$PREFIX-untrust-vpc \
--range=$CIDR_UNTRUST \
--stack-type=IPV4_IPV6 \
--ipv6-access-type=EXTERNAL
gcloud compute networks subnets create $PREFIX-untrust-subnet-lb \
--network=$PREFIX-untrust-vpc \
--range=$CIDR_UNTRUST_LB \
--stack-type=IPV4_IPV6 \
--ipv6-access-type=EXTERNAL
gcloud compute networks subnets create $PREFIX-trust-subnet \
--network=$PREFIX-trust-vpc \
VM-Series Public Cloud Deployments 534 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on Google Cloud Platform
--range=$CIDR_TRUST \
--stack-type=IPV4_IPV6 \
--ipv6-access-type=INTERNAL
STEP 5 | Create firewall rules for each VPC network to allow traffic to the VM-Series network
```
interfaces:
```
VPC Rule Name Description
MGMT ingress-mgmt Allows TCP:443/22 to
the MGT interface from
MGMT_SOURCE_RANGES.
UNTRUST ingress-untrust Allows all ingress traffic to the VM-
Series untrust interface.
TRUST ingress-trust Allows all ingress traffic to the VM-
Series trust interface.
gcloud compute firewall-rules create $PREFIX-ingress-mgmt \
--network=$PREFIX-mgmt-vpc \
--direction=ingress \
--allow=tcp:443,tcp:22 \
--source-ranges=$MGMT_SOURCE_RANGES
gcloud compute firewall-rules create $PREFIX-ingress-untrust \
--network=$PREFIX-untrust-vpc \
--direction=ingress \
--allow=all \
--source-ranges=0.0.0.0/0
gcloud compute firewall-rules create $PREFIX-ingress-untrust-ipv6 \
--network=$PREFIX-untrust-vpc \
--direction=ingress \
--allow=all \
--source-ranges=::/0
gcloud compute firewall-rules create $PREFIX-ingress-trust \
--network=$PREFIX-trust-vpc \
--direction=ingress \
--allow=all \
--source-ranges=0.0.0.0/0
gcloud compute firewall-rules create $PREFIX-ingress-trust-ipv6 \
--network=$PREFIX-trust-vpc \
--direction=ingress \
--allow=all \
--source-ranges=::/0
Allowing all traffic to the untrust/trust networks enables the VM-Series rules to be
enforced on all traffic.
VM-Series Public Cloud Deployments 535 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on Google Cloud Platform
Create VM-SeriesFirewall with Gcloud
Create VM-Series managed instance group and instance template.
STEP 1 | Set environment variables to specify the deployment project, region, zone, and naming
prefix.
1. Variable Definition
NIC_<NAME> The configuration for each of the VM-Series network
interfaces. The 'no-address' argument skips adding a public
address to the interface.
VMSERIES_IMAGE The name of the VM-Series image from
paloaltonetworksgcp-public project.
To get a full list of publicly available VM-Series images run
the following command:
gcloud compute images list \
--project paloaltonetworksgcp-
public \
--filter='name ~ .*vmseries-flex.*'
VMSERIES_INSTANCE The instance shape for the VM-Series firewalls
VMSERIES_COUNT The number of VM-Series firewalls to deploy
export NIC_UNTRUST=network=$PREFIX-untrust-vpc,subnet=$PREFIX-
untrust-subnet
export NIC_MGMT=network=$PREFIX-mgmt-vpc,subnet=$PREFIX-mgmt-subnet
export NIC_TRUST=network=$PREFIX-trust-vpc,subnet=$PREFIX-trust-
subnet,no-address
export VMSERIES_IMAGE=vmseries-flex-bundle1-1112
export VMSERIES_INSTANCE=n2-standard-4
export VMSERIES_COUNT=1
STEP 2 | Create an SSH key and export the public key to the environment variable VMSERIES_KEY:
ssh-keygen -f ~/.ssh/vmseries -t rsa -C admin
```
export VMSERIES_KEY=$(cat ~/.ssh/vmseries.pub)
```
STEP 3 | Create the VM-Series instance template and instance group:
gcloud compute instance-templates create $PREFIX-vmseries-template
\
VM-Series Public Cloud Deployments 536 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on Google Cloud Platform
--image=$VMSERIES_IMAGE \
--image-project=paloaltonetworksgcp-public \
--machine-type=$VMSERIES_INSTANCE \
--network-interface=$NIC_UNTRUST,stack-type=IPV4_IPV6 \
--network-interface=$NIC_MGMT \
--network-interface=$NIC_TRUST,stack-type=IPV4_IPV6 \
--boot-disk-type=pd-ssd \
--boot-disk-device-name=persistent-disk-0 \
--boot-disk-auto-delete \
--can-ip-forward \
--scopes=default \
--metadata="dhcp-accept-server-hostname=yes,mgmt-interface-
```
swap=enable,\
```
ssh-keys=admin:$VMSERIES_KEY"
gcloud compute instance-groups managed create $PREFIX-vmseries-mig
\
--size=$VMSERIES_COUNT \
--template=$PREFIX-vmseries-template \
--update-policy-type=opportunistic \
--update-policy-minimal-action=replace \
--update-policy-replacement-method=substitute
Create External Load Balancer
Create an external TCP/UDP load balancer by defining a health check, backend service, and
forwarding rules for both IPv4 and IPv6 traffic.
STEP 1 | In the GCP cloud shell, create the health check, forwarding rule, and backend service:
gcloud compute health-checks create tcp $PREFIX-vmseries-hc \
```
--region=$(gcloud config get-value compute/region)
```
gcloud compute backend-services create $PREFIX-vmseries-extlb \
--health-checks=$PREFIX-vmseries-hc \
```
--health-checks-region=$(gcloud config get-value compute/region)
```
\
--load-balancing-scheme=EXTERNAL \
--protocol=UNSPECIFIED \
--tracking-mode=PER_SESSION \
--connection-persistence-on-unhealthy-backends=NEVER_PERSIST
gcloud compute forwarding-rules create $PREFIX-vmseries-extlb-ipv4
\
--backend-service=$PREFIX-vmseries-extlb \
--load-balancing-scheme=EXTERNAL \
--ip-protocol=L3_DEFAULT \
--ip-version=IPV4 \
--ports=ALL
gcloud compute forwarding-rules create $PREFIX-vmseries-extlb-ipv6
\
--backend-service=$PREFIX-vmseries-extlb \
--load-balancing-scheme=EXTERNAL \
--ip-protocol=L3_DEFAULT \
VM-Series Public Cloud Deployments 537 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on Google Cloud Platform
--ip-version=IPV6 \
--subnet=$PREFIX-untrust-subnet-lb \
--ports=ALL
STEP 2 | Add the VM-Series-managed instance group to the backend service of the load balancer:
gcloud compute backend-services add-backend $PREFIX-vmseries-extlb
\
--instance-group=$PREFIX-vmseries-mig
STEP 3 | Record the IP address assigned to the IPv4 and IPv6 forwarding rules:
```
gcloud compute forwarding-rules list --format="value(IPAddress)"
```
Sample output:
34.145.122.74
2600:1900:4040:2c06:8000:0:0:0/96
Configure VM-Series
Access the firewall’s console and set credentials for the admin user. Then, apply a baseline
configuration to enable the firewall to respond to health checks and also route VPC network
traffic.
Set Credentials
STEP 1 | Retrieve the MGMT addresses assigned to NIC1 on the vmseries-active firewall:
gcloud compute instances list \
--filter='name:vmseries' \
```
--format='get(networkInterfaces[1].networkIP,
```
```
networkInterfaces[1].accessConfigs[0].natIP)'
```
STEP 2 | Open an SSH session to vmseries-active using your private SSH key:
ssh admin@MGMT_IP -i ~/.ssh/vmseries
STEP 3 | On the VM-Series, enter configuration mode and set a password for the admin user:
configure
set mgt-config users admin password
STEP 4 | Commit the changes. Enter exit twice to terminate the session:
commit
```
STEP 5 | (Optional) If you set the VMSERIES_IMAGE to use a BYOL (i.e. vmseries-flex-byol-1100),
```
```
access the VM-Series user interface (https://MGMT_IP) and license the firewall.
```
VM-Series Public Cloud Deployments 538 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on Google Cloud Platform
Configure Network Interfaces to Handle IPv4/IPv6 Traffic
Enable DHCPv4 and DHCPv6 on the VM-Series network interfaces to handle IPv4/IPv6 traffic.
STEP 1 | On the VM-Series, go to Network > Zones and select Add.
STEP 2 | Create two zones: untrust and trust.
Figure 7:
STEP 3 | Go to Network > Interfaces > Ethernet.
VM-Series Public Cloud Deployments 539 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on Google Cloud Platform
```
STEP 4 | Configure ethernet1/1 (untrust) as follows: <image>
```
In the IPv4 tab, check Automatically create default route. In the IPv6 tab, check
Accept Router Advertised Route and uncheck Enable Prefix Delegation.
VM-Series Public Cloud Deployments 540 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on Google Cloud Platform
```
STEP 5 | Configure ethernet1/2 (trust) as follows:
```
In the IPv4 tab, uncheck Automatically create default route. In the IPv6 tab, uncheck
Accept Router Advertised Route and uncheck Enable Prefix Delegation.
STEP 6 | Commit the changes.
Configure NAT Policy for IPv4 Forwarding Rule
Create a NAT policy to translate traffic destined to the IPv4 forwarding rule to a web app on the
internal-vm in the trust VPC.
```
Prerequisites:
```
• In Google Cloud, record the IPv4 and IPv6 addresses of the internal-vm:
Figure 8: IPv4 and IPv6 addresses in GCP for internal-vm
VM-Series Public Cloud Deployments 541 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on Google Cloud Platform
STEP 1 | On the VM-Series, go to Policies > NAT and select Add.
STEP 2 | Configure the policy to translate the IPv4 forwarding rule to the internal-vm IPv4 address.
Original Packet Source Zone untrust
Destination Zone untrust
Destination Interface ethernet1/1
```
Destination Address 34.29.169.107 (IPv4
```
```
forwarding rule address)
```
Source Translation Translation Type Dynamic IP and Port
Address Type Interface Address
Interface ethernet1/2
DST Translation Translation Type Dynamic IP
VM-Series Public Cloud Deployments 542 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on Google Cloud Platform
```
Translated Address 10.0.3.10 (IPv4 of internal-
```
```
vm)
```
When load-balancing internet inbound traffic through multiple firewalls, source
translation is necessary to ensure a synchronous response from the backend
application.
Configure NPTv6 Policy for IPv6 Forwarding Rule
Create an NPTv6 policy to translate traffic destined to the IPv6 forwarding rule to the web app on
internal-vm.
NPTv6 performs stateless translation, moving traffic from one IPv6 prefix to another by
eliminating the IPv6 header checksum. Therefore, a checksum-neutral address must be
calculated and used as the original packet's destination in the NPTv6 policy.
STEP 1 | Generate a checksum neutral address on VM-Series:
1. In Cloud Shell, SSH to the VM-Series using its management IP:
ssh admin@1.1.1.1
2. Generate the checksum for traffic between the IPv6 address of the internal-vm and the
IPv6 forwarding rule address on the external load balancer:
test nptv6 cks-neutral source-ip fd20:eb0:af94:0:0:0:0:0 dest-
network
2600:1900:4000:5db5:8000:1:0:0/96
Replace fd20:eb0:af94:0:0:0:0:0 with the IPv6 address of your
internal-vm and replace 2600:1900:4000:5db5:8000:1:0:0/96 with
the IPv6 address assigned to your load balancer's forwarding rule.
3. Record the generated checksum neutral address:
The checksum neutral address of fd20:eb0:af94:: is
2600:1900:4000:5db5:8000:1:5eae:0 in
2600:1900:4000:5db5:8000:1:0:0/96
subnet
Use this checksum neutral public IPv6 address in your NPTv6 configuration as
the Destination Address in the NAT policy rule.
VM-Series Public Cloud Deployments 543 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on Google Cloud Platform
STEP 2 | Create NPTv6 policy:
1. On the VM-Series, go to Policies > NAT and select Add.
2. Set NAT Type to nptv6.
3. Configure the policy to translate the checksum IP to the internal-vm IPv6 address.
Figure 9: NPTv6 Policy
Original Packet Source Zone untrust
Destination Zone untrust
Destination Interface ethernet1/1
Destination Address 2600:1900:4000:5db5:8000:1:5eae:0
```
(checksum neutral address)
```
DST Translation Translation Type Dynamic IP
Translated Address fd20:eb0:af94:0:0:0:0:0/96
```
(IPv6 of internal-vm)
```
Configure Health Checks
Configure the VM-Series to receive and respond to the load balancer’s health checks.
VM-Series Public Cloud Deployments 544 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on Google Cloud Platform
STEP 1 | On the VM-Series CLI, enter configuration mode.
STEP 2 | Create a Management Profile to allow the load balancer health check ranges:
set network profiles interface-management-profile lb-checks http
yes
set network profiles interface-management-profile lb-checks
permitted-ip 35.191.0.0/16
set network profiles interface-management-profile lb-checks
permitted-ip 130.211.0.0/22
set network profiles interface-management-profile lb-checks
permitted-ip 209.85.152.0/22
set network profiles interface-management-profile lb-checks
permitted-ip 209.85.204.0/22
set network profiles interface-management-profile lb-checks
permitted-ip 2600:1901:8001::/48
STEP 3 | Create a loopback and assign the load balancer’s forwarding rules as the interface’s
addresses.
set network interface loopback units loopback.1 ip 34.145.122.74
set network interface loopback units loopback.1 ipv6 address
2600:1900:4040:2c06:8000:0:0:0
set network interface loopback units loopback.1 ipv6 enabled yes
set network interface loopback units loopback.1 interface-
management-profile lb-checks
set zone lb-checks network layer3 loopback.1
set network virtual-router lb-checks interface loopback.1
STEP 4 | Create a security policy to allow the health checks to communicate with the loopback
```
interface:
```
set rulebase security rules lb-checks from any to any
set rulebase security rules lb-checks source 35.191.0.0/16
set rulebase security rules lb-checks source 130.211.0.0/22
set rulebase security rules lb-checks source 209.85.152.0/22
set rulebase security rules lb-checks source 209.85.204.0/22
set rulebase security rules lb-checks source 2600:1901:8001::/48
set rulebase security rules lb-checks destination any
set rulebase security rules lb-checks application web-browsing
service application-default
set rulebase security rules lb-checks action allow
STEP 5 | Commit the changes.
commit
STEP 6 | In Google Cloud, go to Network Services → Load Balancing and verify the health checks for
both forwarding rules are listed as healthy.
VM-Series Public Cloud Deployments 545 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on Google Cloud Platform
Create Test Workloads
```
Deploy VMs to test north/south IPv4 and IPv6 traffic. First, create an Ubuntu VM (internal-vm)
```
```
within the trust VPC. Then, create an external network (external-vpc) containing a VM (external-
```
```
vm). The external-vm will be used to test inbound traffic to the internal-vm through the VM-
```
Series firewall.
STEP 1 | In the Cloud shell, create the internal-vm in the trust VPC and the external-vpc containing
the external-vm:
gcloud compute instances create $PREFIX-internal-vm \
--machine-type=f1-micro \
--image-family=ubuntu-2004-lts \
--image-project=ubuntu-os-cloud \
--network-interface subnet=$PREFIX-trust-subnet,stack-
```
type=IPV4_IPV6,no-address
```
gcloud compute networks create $PREFIX-external-vpc \
--subnet-mode=custom
gcloud compute networks subnets create $PREFIX-external-subnet \
--network=$PREFIX-external-vpc \
--range=10.111.10.0/28 \
--stack-type=IPV4_IPV6 \
--ipv6-access-type=EXTERNAL
gcloud compute firewall-rules create $PREFIX-ingress-external \
--network=$PREFIX-external-vpc \
--direction=ingress \
--allow=tcp:22 \
--source-ranges=0.0.0.0/0
gcloud compute instances create $PREFIX-external-vm \
--machine-type=f1-micro \
--image-family=ubuntu-2004-lts \
--image-project=ubuntu-os-cloud \
--network-interface subnet=$PREFIX-external-subnet,stack-
```
type=IPV4_IPV6
```
STEP 2 | Record the IPv4 and IPv6 addresses assigned to the internal-vm.
gcloud compute instances describe $PREFIX-internal-vm \
--
```
format='get(networkInterfaces[0].networkIP,networkInterfaces[0].ipv6Address)'
```
Sample output:
10.0.2.3 fd20:1fa:809f:2000:0:1:0:0
Test Inbound Internet Traffic
Access the external-vm to test internet inbound traffic through the IPv4/IPv6 external load
balancer to the web application on internal-vm.
VM-Series Public Cloud Deployments 546 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on Google Cloud Platform
```
Prerequisites:
```
• Go to Policies > Security and Add a security policy to allow web-browsing to the traffic flow.
• Commit the changes.
• In Cloud Shell, create default routes in the trust-vpc to steer IPv4/IPv6 traffic to the VM-Series
trust interface for inspection.
gcloud compute routes create ipv4-default \
--network=trust-vpc \
--destination-range=0.0.0.0/0 \
--next-hop-instance=vmseries \
--next-hop-instance-zone=us-central1-a
gcloud beta compute routes create ipv6-default \
--network=trust-vpc \
--destination-range=::0/0 \
--next-hop-instance=vmseries \
--next-hop-instance-zone=us-central1-a
STEP 1 | In the GCP cloud shell, SSH to the external VM.
gcloud compute ssh your-domain@external-vm --zone=us-central1-a
STEP 2 | Attempt to reach the web application using the load balancer's IPv4 address.
curl http://34.29.169.107:80/?[1-3]
STEP 3 | Attempt to reach the web application using the checksum neutral IPv6 address:
curl -6 'http://[2600:1900:4000:5db5:8000:1:5eae:0]:80/?[1-3]'
STEP 4 | On the VM-Series, go to Monitor > Logs > Traffic and enter the below filter query to search
for the inbound traffic:
```
( zone.src eq 'untrust' ) and ( zone.dst eq 'trust' ) and ( app eq
```
```
'web-browsing' )
```
Figure 10: VM-Series monitors and Translates the inbound traffic for IPv4 and IPv6
The traffic log monitor shows the VM-Series firewall correctly inspecting and
translating both the IPv4 and IPv6 traffic.
VM-Series Public Cloud Deployments 547 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on Google Cloud Platform
Destroy Deployment
Delete the created cloud resources in GCP:
gcloud config set project PROJECT_ID
gcloud config set compute/region REGION
gcloud config set compute/zone ZONE
export PREFIX=panw
gcloud compute instances delete $PREFIX-internal-vm --quiet
gcloud compute instances delete $PREFIX-external-vm --quiet
gcloud compute networks subnets delete $PREFIX-external-subnet --
quiet
gcloud compute firewall-rules delete $PREFIX-ingress-external --
quiet
gcloud compute networks delete $PREFIX-external-vpc --quiet
gcloud compute forwarding-rules delete $PREFIX-vmseries-extlb-ipv4
--quiet
gcloud compute forwarding-rules delete $PREFIX-vmseries-extlb-ipv6
--quiet
gcloud compute backend-services delete $PREFIX-vmseries-extlb --
quiet
gcloud compute health-checks delete $PREFIX-vmseries-hc --quiet \
```
--region=$(gcloud config get-value compute/region)
```
gcloud compute instance-groups managed delete $PREFIX-vmseries-mig
--quiet \
```
--region=$(gcloud config get-value compute/region)
```
gcloud compute instance-templates delete $PREFIX-vmseries-template
--quiet
gcloud compute firewall-rules delete $PREFIX-ingress-trust-ipv6 --
quiet
gcloud compute firewall-rules delete $PREFIX-ingress-trust --quiet
gcloud compute firewall-rules delete $PREFIX-ingress-untrust-ipv6
--quiet
gcloud compute firewall-rules delete $PREFIX-ingress-untrust --
quiet
gcloud compute firewall-rules delete $PREFIX-ingress-mgmt --quiet
gcloud compute networks subnets delete $PREFIX-trust-subnet --quiet
VM-Series Public Cloud Deployments 548 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on Google Cloud Platform
gcloud compute networks subnets delete $PREFIX-untrust-subnet-lb --
quiet
gcloud compute networks subnets delete $PREFIX-untrust-subnet --
quiet
gcloud compute networks subnets delete $PREFIX-mgmt-subnet --quiet
gcloud compute networks delete $PREFIX-trust-vpc --quiet
gcloud compute networks delete $PREFIX-untrust-vpc --quiet
gcloud compute networks delete $PREFIX-mgmt-vpc --quiet
VM-Series Public Cloud Deployments 549 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on Google Cloud Platform
VM Monitoring with the Panorama Plugin for GCP
Where Can I Use This? What Do I Need?
```
• Google Cloud Platform (GCP) VM-Series License (PAYG or BYOL)
```
VM-Series plugin
Panorama
Panorama plugin for GCP
The Panorama plugin for GCP retrieves the internal and external IP addresses from running VMs,
and periodically retrieves IP-to-tag mappings from VMs in connected GCP VPCs.You can use tags
to organize VMs into dynamic address groups, and then reference your tags in Security policy
rules that allow or deny traffic to specific VM IP addresses. To consistently enforce Security
policy, you can then push rules to your VM-Series firewalls.Workloads in the cloud are often
ephemeral. To write a granular security policy based on your requirement, you can use the
```
application’s tags in Panorama security policy using the dynamic address groups (DAGs) .
```
As a result, as workloads come up and down, the appropriate security policy will be applied.The
Panorama plugin for GCP version 3.0.0 and above supports shared VPC architectures. When you
```
use a Shared VPC, a single host project may define (and share) the VPCs for all service projects
```
underneath to deploy your resources. By onboarding the host project into the Panorama plugin
for GCP, you can automatically onboard your service projects as well.The Panorama plugin for
```
Google Cloud Platform (GCP) version 2.0.0 enables you to create a VM monitoring configuration
```
that authenticates with a GCP project and monitors VM-Series firewalls and other VMs deployed
within it. Once you establish a connection to your project, the plugin can retrieve IP-address-to-
tag communication between Panorama and GCP assets. Tags can be predefined attributes, user-
```
defined labels for VMs, and user-defined network tags (see Review and Create Tags ).
```
Configure GCP Assets for VM Monitoring
You can monitor VM-Series firewalls you deployed from the GCP marketplace, firewalls you
deployed with auto scaling firewall templates, GCE instances you created from to the GCP
console or the gcloud command line, or other virtual machines deployed in GCP. If you deploy
PAN-OS VMs from the Marketplace, follow the instructions in Set Up the VM-Series Firewall on
Google Cloud Platform.
Review IAM Roles
Ensure that you have the following minimum permissions for VM Monitoring tasks:
• In the GCP console, create service accounts for your project and grant the permission project
owner or editor.
Service account creation can't be automated. If you don't have permission to create a service
account you can ask an administrator to create it and assign an appropriate role to you.
• View your service accounts: read-only.
• View PAN-OS VMs deployed from the Google Marketplace: Compute viewer.
VM-Series Public Cloud Deployments 550 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on Google Cloud Platform
• Assign a user-defined tag to an instance: Project owner, editor or Instance Admin.
Create a Service Account
Before you use the GCP plugin on Panorama to configure VM Monitoring, you must use the
GCP console to create service accounts that grant permissions to access your GCP project, VM-
Series firewalls deployed within it, any other VMs that you want Panorama to manage, and related
networks and subnetworks. The GCP plugin for Panorama retrieves pre-defined attributes for
Google assets, user defined VM labels, and user-defined network tags.
From the Panorama plugin for GCP version 3.1.0 or later, in a shared VPC setup, you can create
service accounts for host projects, and grant permissions to the service projects. For more
information, see creating cross project service account in GCP. These service account credentials
must be used in Monitoring Definition to retrieve tags for multiple attached service projects.
Every project has a default service account that was automatically created when the project was
created. If you create a separate service account specifically for VM Monitoring, you have greater
control of users and their roles. You can configure up to 100 service accounts per project.
STEP 1 | In the Google Cloud Platform console, select the project you want to monitor.
STEP 2 | Select IAM & Admin > Service accounts and choose +Create Service Account.
Enter the service account name and description, and click Create.
STEP 3 | Select a role type from the drop menu, and on the right, select an appropriate access level.
For example, select Project > Editor. You can select multiple roles for a service account.
When you're finished, click Continue.
STEP 4 | Grant specific users permission to access this service account. Select members from the
Permissions column on the right to give them permission to access the roles in the previous
step.
```
STEP 5 | (Optional) Click +CREATE KEY to create a credential that allows you to authenticate with the
```
Google Cloud CLI to access VM-Series firewalls, networks, and other VMs associated with
this service account.
The key is downloaded automatically. Be sure to store it in a secure location. The JSON format
for the generated private key is as follows:
```
{
```
"type": "service_account",
"project_id": "gcp-xxx",
"private_key_id": "<private-key-id>",
"private_key": "-----BEGIN PRIVATE KEY-----<private-key-
value>-----END PRIVATE KEY-----\n",
"client_email": "<client-email>",
"client_id": "<client-id>",
"auth_uri": "<auth-uri>",
"token_uri": "<token-uri>",
"auth_provider_x509_cert_url": "<auth-provider-x509-cert-url>",
"client_x509_cert_url": "<client-x509-cert-url>"
```
}
```
VM-Series Public Cloud Deployments 551 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on Google Cloud Platform
Review and Create Tags
“Tag” is a general term for a predefined attributes, user-defined labels, and user-defined network
tags.
```
• Predefined tags (attributes) are automatically created for Google VMs. When you configure
```
VM Monitoring you can choose to monitor all eight of the predefined attributes, or you can
create a customized list of attributes to monitor.
• You can define your own tags for VM labels and network tags.
Tag VMs and networks so that you can identify and group them so that you can structure rules to
enforce Security policy. You can tag any VM deployed in your Google project—for example, a VM-
Series firewall, a web server, an application server, or a load balancer.
• Tags must be associated with a VM. This also applies to networks and subnetworks.
```
• If there are multiple IP addresses associated with an instance (for example if you tagged the
```
```
VM-Series firewall trust and untrust interfaces), Panorama generates multiple sets of tag
```
information.
The total number of tags that the Panorama plugin can retrieve and register depends on the PAN-
OS version Panorama is running and the version of the managed VM-Series firewalls.
Google zone, Google region, VPC name, and subnet name are used to tag network interfaces on
VMs with multiple interfaces. specific to network interface.
Predefined Attributes
The Google Cloud Platform plugin for Panorama retrieves the following predefined tags from any
managed VM:
• Project ID—For example: google.project-id.myProjectId.
To find your project information in the Google console, select your project, then select IAM &
Admin > Settings.
• Service account—Your service account in the form of an email address. For example:
google.svc-accnt.sa-name@project-id.iam.gserviceaccount.com.
To find your Service account, view the VM instance details.
• VPC name—The name of the VPC network for a managed VM. For example: google.vpc-
name.myvnet.
• Subnet name—The name of a subnet you created for a managed VM interface. For example,
for the VM-Series firewall untrust interface, the name of the subnet you created for the
untrust interface: google.subnet-name-untrust.web.
• OS SKU—The operating system you chose when you deployed the managed VM. For example:
google.os-sku.centos-7.
This attribute isn't supported if the VM uses a custom image.
• Google zone—The zone you selected when you deployed the VM. For example:
google.zone.us-east1-c.
VM-Series Public Cloud Deployments 552 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on Google Cloud Platform
• Google region—The region containing the zone you selected. For example: google.region.us-
east1.
• Instance group name—For example: google.instance-group.myInstanceGroup. To view or
create an instance group in the Google console, select Compute Engine > Instance Group.
User-defined Labels
Panorama uses up to 16 user-defined labels. If you have more than 16 labels, Panorama sorts your
user-defined labels alphabetically and uses the first 16 tags.
Review the Google requirements for label key-value pairs: Keys have a minimum length of one
character and a maximum length of 63 characters, and can't be empty. Values can be empty, and
have a maximum length of 63 characters.
To create or view labels in the GCP console, go to Compute Engine > VM Instances and select
Show Info Panel. Select one or more VMs and in the Info Panel, select Labels. Click +Add a label,
add a key and value, and click Save.
User-defined Network Tags
Panorama uses up to eight user-defined network tags. If you have more than eight tags, Panorama
sorts your user-defined labels alphabetically and uses the first 8 tags.
Google limits network tags as follows:
• Maximum 63 characters per tag.
```
• You can use lowercase letters, numbers, and dashes; a tag must start with a lowercase letter,
```
and end with a number or a lowercase letter.
To create or view network tags in the GCP console, go to Compute Engine > VM Instances and
```
select an instance. Edit the instance, and scroll down to Network Tags, enter tags (separated by
```
```
commas), and Save. See Configuring Network Tags.
```
Install the Panorama Plugin for GCP
Where Can I Use This? What Do I Need?
```
• Google Cloud Platform (GCP) VM-Series License (PAYG or BYOL)
```
VM-Series plugin
Panorama
Panorama plugin for GCP
The Panorama plugin for GCP is required if you want to use Panorama to manage VM Monitoring
or auto scaling deployments created with Palo Alto Networks templates. Install the plugin version
that supports the GCP features you want to configure, as detailed in the Compatibility Matrix
table for Public Clouds.
You can't upgrade the Panorama plugin for GCP from version 1.0.0 to version 2.0.x. If you
have installed version 1.0.0, remove it before installing 2.0.x.
VM-Series Public Cloud Deployments 553 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on Google Cloud Platform
If you have a standalone Panorama or two Panorama appliances installed in an HA pair with
multiple plugins installed, the plugins might not receive updated IP-tag information if one or more
of the plugins isn't configured. This occurs because Panorama won't forward IP-tag information
to unconfigured plugins. Additionally, this issue can occur if one or more of the Panorama plugins
```
isn't in the Registered or Success state (positive state differs on each plugin). Ensure that your
```
plugins are in the positive state before continuing or executing the commands described below.
If you encounter this issue, there are two workarounds:
• Uninstall the unconfigured plugin or plugins. It's recommended that you don't install a plugin
that you don't plan to configure right away
• You can use the following commands to work around this issue. Execute the following
command for each unconfigured plugin on each Panorama instance to prevent Panorama from
waiting to send updates. If you don't, your firewalls might lose some IP-tag information.
request plugins dau plugin-name <plugin-name> unblock-device-push yes
You can cancel this command by executing:
request plugins dau plugin-name <plugin-name> unblock-device-push no
The commands described are not persistent across reboots and must be used again for any
subsequent reboots. For Panorama in HA pair, the commands must be executed on each
Panorama.
STEP 1 | Verify your Panorama installation.
On Panorama, ensure that your PAN-OS version meets the requirements to support GCP auto
scaling.
STEP 2 | Remove the Panorama plugin for GCP v1.0.
If you have the Panorama plugin v1.0 installed, you must remove it.
STEP 3 | Install the Panorama plugin for GCP.
Select Panorama > Plugins, and type gcp in the search bar. Install the plugin version that
```
supports the features you want to configure (see the Compatibility Matrix table for Public
```
```
Clouds).
```
After the installation, you can see the plugin in the Panorama dashboard General Information
list. View Panorama > Google Cloud Platform and you see the Setup, Monitoring Definition,
and AutoScaling interfaces.
```
STEP 4 | (Optional) If your Panorama appliances are in a high availability configuration, you must
```
manually install the same version of the Google plugin on both Panorama peers.
Configure the Google plugin on the active Panorama peer only. On commit, the
configuration syncs to the passive Panorama peer. Only the active Panorama peer
polls Google VMs you have configured for VM Monitoring.
VM-Series Public Cloud Deployments 554 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on Google Cloud Platform
Configure VM Monitoring with the Panorama Plugin for GCP
Where Can I Use This? What Do I Need?
```
• Google Cloud Platform (GCP) VM-Series License (PAYG or BYOL)
```
VM-Series plugin
Panorama
Panorama plugin for GCP
This topic describes the steps to configure VM Monitoring in the Panorama plugin for Google
```
Cloud Platform (GCP).
```
After you tag your GCP assets and create service accounts, make your assets available to
Panorama so you can set up VM monitoring.
Prepare Panorama to Configure VM Monitoring
Follow these steps to enable Panorama to manage and monitor your GCP assets. Any VM
deployed in GCP can be a managed device in Panorama.
STEP 1 | In Panorama, add the VM-Series firewalls and other VMs associated with your GCP project
as managed devices.
STEP 2 | Add a Device Group and assign managed devices to it. A Device Group is a group of firewalls
or virtual systems that you want to manage as a group.
A VM can be a member of only one Device Group. Plan your Device Groups carefully.
STEP 3 | Add a template. Name the template and accept the default VPC.
STEP 4 | Add a template stack. Add the stack, Add the template you created, and select your devices.
STEP 5 | Commit the changes.
Set Up VM Monitoring
STEP 1 | If you have not done so, Install the Panorama Plugin for GCP.
STEP 2 | Log in to the Panorama web interface and select Panorama > #.
VM-Series Public Cloud Deployments 555 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on Google Cloud Platform
STEP 3 | Set up VM monitoring.
1. Configure general settings.
1. Select Panorama > Google Cloud Platform > Setup > General. To edit the settings,
click the gear.
• Check Enable Monitoring to permit VM monitoring on all projects for which you
configure a service account.
• Enter the Monitoring Interval in seconds. This is the length of time between tag
retrieval events.
2. Add a notify group. A notify group is a list of Device Groups to which Panorama pushes
IP address-to-tag mappings and updates.
A project can have only one notify group.
1. Select Panorama > Google Cloud Platform > Setup > Notify Groups and click Add.
2. Enter a Name to identify the group of firewalls to which Panorama pushes the VM
```
information (IP address-to-tag mappings) it retrieves.
```
3. Select the Device Groups to which Panorama will push the VM information (IP
```
address-to-tag mappings) retrieved from your project. The VM-Series firewalls
```
use the update to determine the current member list for Dynamic Address Groups
referenced in Security policy.
Plan your Device Groups carefully.
4. Select predefined or custom tags.
• Select All 8 Predefined Tags—Choose this option to select all predefined attributes
```
(tags).
```
• Custom Tags—Choose this option to create tag lists for predefined attributes, user-
defined labels, and user-defined network tags.
5. • Make sure to include all relevant Device Groups in a single notify group.
• If you want to deregister the tags that Panorama has pushed to a firewall included
in a notify group, you must delete the monitoring definition.
• To register tags to all virtual systems on a firewall enabled for multiple virtual
systems, you must add each virtual system to a separate Device Group on
Panorama and assign the Device Groups to the notify group. Panorama will
register tags to only one virtual system, if you assign all the virtual systems to one
Device Group.
3. Add GCP Service Account Credential.
• Name the service account credential.
```
• (Optional) Enter a description of the service account.
```
• Browse to upload the JSON file generated when you created service accounts.
In Shared VPC Setup, you have to create service accounts for host projects, and grant
permissions to the service projects. You can use these service accounts in the GCP
VM-Series Public Cloud Deployments 556 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on Google Cloud Platform
plugin. This will allow you to retrieve tags that are part of service projects attached to
the host project.
Use the Panorama web interface. You can't use the CLI to add a service account.
You can only use a service account for one credential. Don't create multiple
credentials from a single JSON file.
After you add the service account credential, you can validate the credential from your
Panorama command line:
request plugins gcp validate-service-account <svc-acct-credential-
name>
STEP 4 | Create a Monitoring Definition.
A monitoring definition consists of the service account credential for your project and a notify
group. All the networking assets in your project are monitored, and the tags retrieved are
pushed to the Device Groups you list in your monitoring definition. When you add a new
monitoring definition, it is enabled by default.
A project can have only one monitoring definition, and a monitoring definition can
include only one notify group.
1. Select Panorama > Google Cloud Platform > Monitoring Definition and click Add.
2. Name the monitoring definition.
3. Enter an optional Description for the project and assets you are monitoring.
4. Select the Service Account credential you created in the previous step.
5. Select a Notify Group.
6. Enable monitoring for the elements associated with this service account.
STEP 5 | Commit the changes on Panorama.
Verify that the status for the Monitoring Definition displays as Success. If it fails, verify that
you entered the project ID accurately and provided the correct keys and IDs for the service.
VM-Series Public Cloud Deployments 557 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on Google Cloud Platform
STEP 6 | Verify that you can view the VM information on Panorama, and define the match criteria for
Dynamic Address Groups.
On HA failover, the secondary Panorama attempts to reconnect to Google Cloud Platform
and retrieve tags for all monitoring definitions. If there is an error with reconnecting even one
monitoring definition, Panorama generates a system log message:
```
Unable to process subscriptions after HA switch-over; user-
```
intervention required.
If you see this error, fix the issue in Panorama. For example, remove an invalid subscription
or provide valid credentials, and commit your changes to enable Panorama to reconnect and
retrieve the tags for all monitoring definitions.
Even when Panorama is disconnected from Google Cloud Platform, the firewalls have
the list of all tags that had been retrieved before failover, and can continue to enforce
policy on that list of IP addresses. When you delete a monitoring definition, Panorama
removes all tags associated with registered VMs. As a best practice, configure action-
oriented log forwarding to an HTTPS destination from Panorama so that you can
take immediate action.
VM-Series Public Cloud Deployments 558 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on Google Cloud Platform
Securing VPC Networks with VM-Series Firewall on
GCP
Where Can I Use This? What Do I Need?
```
• Google Cloud Platform (GCP) VM-Series License (PAYG or BYOL)
```
VM-Series plugin
Panorama
Panorama plugin for GCP
There are several architectures the VM-Series supports to secure Google Cloud networks.
Both the autoscale and active/passive deploymentconfigure-vm-monitoringconfigure-vm-
monitoringonfigure-vm-monitoring models support the architectures described in this section.
Multiple VPC networks can be secured using the multiple network interface architecture, VPC
peering architecture, or a combination of both architectures.
The following are architectures for deploying VM-Series firewalls in your Google Cloud Platform:
Multiple Network Interface Architecture
In the multiple interface architecture, additional dataplane interfaces are attached to workload
VPC networks, with each interface set as a backend service of an internal pass-through load
balancer. In the autoscale model, these load balancers distribute traffic to the firewalls. In the
active/passive model, they manage stateful traffic failover between the firewall HA pair. Custom
or policy-based routes in each workload VPC direct traffic to the respective load balancer within
the same VPC.
• In Google Cloud, a maximum of 8 interfaces can be allocated on a per virtual machine
basis.
• In Google Cloud, you cannot attach or detach network interfaces after a virtual
machine is created. Therefore, it is important to plan your network interface allocation
prior to firewall deployment.
The following diagram is an example of the multiple interface architecture:
VM-Series Public Cloud Deployments 559 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on Google Cloud Platform
The following examples show the different traffic patterns that run through the VM-Series
firewalls in this configuration:
1. An inbound request is made to an application hosted in VPC C. The external load balancer
```
(External LB) distributes the request to the VM-Series untrust interfaces. The VM-Series
```
firewall inspects and forwards the request through the NIC4 in VPC C and to the destination
application.
2. The route table of VPC B routes traffic that is destined to the internet to the IP address of
```
Internal LB B (10.2.0.10). The load balancer distributes the traffic to NIC3 on the VM-Series
```
VM-Series Public Cloud Deployments 560 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on Google Cloud Platform
```
firewalls. The VM-Series inspects and forwards the traffic through its untrust interface (NIC0)
```
to the internet.
3. A resource in VPC A makes a request to a resource in VPC B. The route table of VPC A routes
the request to the Internal LB A . The load balancer distributes the request to NIC2 on the VM-
Series. The VM-Series inspects and forwards the request through NIC3 to the resource in VPC
B. VPC B routes its return traffic to Internal LB B using the route table of VPC B. .
4. A resource in VPC A makes a request within VPC A. A policy based route within VPC A steers
the intra-VPC traffic to the forwarding rule of Internal LB A. The VM-Series inspects and
forwards the traffic through NIC2 to the destination in VPC A. The return traffic uses the same
routing path as the request traffic.
VPC Network Peering Model
VPC Network Peering enables you to create a hub and spoke topology to secure many VPC
networks with VM-Series. Unlike the multiple interface architecture, VPC peering enables you to
connect and disconnect up to 25 workload VPCs as needed. In this architecture, the trust VPC
serves as a hub network for workload VPCs which are connected as spoke networks. Each spoke
VPC network has custom or policy-based routes to steer inter-VPC and intra-VPC traffic to the
internal load balancer in the hub network.
In the configuration displayed in the previous diagram, the VM-Series firewalls inspect the traffic
as follows:
1. Traffic from the internet to applications in the spoke networks is distributed by the external
```
passthrough load balancer to the VM-Series untrust interfaces (NIC0). The VM-Series firewall
```
```
inspects the traffic and forwards permissible traffic through its trust interface (NIC2) to the
```
application in the spoke network.
2. Traffic from the spoke networks destined to the internet are routed to the internal load
balancer in the hub VPC. The VM-Series firewall inspects the traffic and forwards permissible
```
traffic through its untrust interface (NIC0) to the internet.
```
3. Traffic between spoke networks or traffic within a spoke network (routed via policy-based
```
route) is routed to the internal load balancer in the hub VPC. The VM-Series firewall inspects
```
```
and forwards the traffic through the trust interface (NIC2) into the hub network which routes
```
permissible traffic to the destination spoke network.
Combining the Architectures
If you require transitive routing and security for more than 25 VPC networks, you can combine
the multiple network interface and VPC peering architectures together. In this architecture,
each additional dataplane interface serves as a hub network which can have up to 25 spoke VPC
networks. Full transitive routing across the spoke networks and hubs is supported.
Network Connectivity Center
```
Network Connectivity Center (NCC) utilizes a hub-and-spoke model for managing global
```
connectivity across diverse networks. By integrating VM-Series with NCC, a full mesh networking
model is created between VM-Series and connected spokes. VM-Series connects to the hub
as a router appliance, exchanging routes with Cloud Routers via BGP. This integration enables
VPC-to-VPC connectivity across projects and organizations, secure remote network connections
to Google Cloud, global WAN network creation, and cross-region failover. Two key topologies
VM-Series Public Cloud Deployments 561 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on Google Cloud Platform
include VPC-to-VPC, facilitating route exchange between separate VPCs, and Global VPC,
enabling regional failover and dynamic route propagation for continuous service across multiple
regions.
```
Network Connectivity Center (NCC) leverages a hub-and-spoke model to provide a place to
```
manage global connectivity across various networks. The hub is a global resource that connects
attached spokes with a simple and singular connectivity model. Integrating Google Cloud Network
Connectivity Center with VM-Series creates a full mesh networking model between the VM-
Series and all other connected spokes.
The VM-Series connects to the hub as a router appliance, enabling you to exchange routes with
Cloud Routers using BGPUsing the VM-Series firewall with NCC, enables you to achieve the
```
following:
```
• Connect multiple VPC networks to one another across projects and organizations within GCP.
See VPC-to-VPC topologies for more information.
• Connect remote networks to Google Cloud while providing full BGP route exchange. See site-
to-cloud connectivity for more information.
• Create a global WAN network secured with VM-Series deployed in Google Cloud. See site-to-
site connectivity for more information.
• Facilitate cross-region failover across regionally distributed firewalls.
Topology 1: VPC-to-VPC Topology
```
In this topology, two VM-Series firewalls are deployed, each with a network interface (NIC) in
```
```
separate VPC networks (VPC 1 and VPC 2). Each NIC is configured as a router appliance spoke
```
connected to an NCC hub and has established BGP peering with a cloud router in each VPC.
In this scenario, the VM-Series firewalls and the Cloud Routers facilitate a full route exchange
between VPC 1 and VPC 2. As a result, the workloads in VPC 1 have routes to reach the
workloads in VPC 2 through the propagated routes. In the event of a zone or firewall failure, BGP
route convergence propagates routes to the secondary VM-Series firewall, ensuring continuity.
Topology 2: Global VPC
Three VPCs have been created — mgmt, untrust, and vpc1 — with each containing subnets in the
regions us-east1 and us-west1. Additionally, one VM-Series firewall has been deployed in each
```
region (named us-east1-vmseries and us-west1-vmseries), with a network interface card (NIC) in
```
each VPC. Specifically, the firewall's NIC in vpc1 is configured as a router appliance connected
to an NCC hub. Within each region, the firewalls are configured as BGP neighbors with Cloud
Routers, facilitating end-to-end route propagation. Should there be a regional failure, egress traffic
from the affected region in vpc1 is automatically rerouted to the firewall in the remaining healthy
region through dynamic route propagation, ensuring continuity of service.For more information,
see Google Cloud NCC & VM-Series Tutorial.
VM-Series Public Cloud Deployments 562 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on Google Cloud Platform
VM-Series Public Cloud Deployments 563 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on Google Cloud Platform
```
Google Cloud Network Security Integration (NSI) with
```
VM-Series Firewalls
```
Google Cloud's Network Security Integration (NSI) with Palo Alto Networks® software firewalls,
```
```
including VM-Series Next-Generation Firewalls (NGFWs), addresses common cloud security
```
challenges. Traditional cloud security deployments often faced complexities such as intricate
routing, operational overhead, and VPC peering limitations. This integration simplifies deploying
advanced security services within Google Cloud, ensuring consistent security policies and faster
protection across cloud infrastructure without altering your application architecture or existing
networking. It provides granular East-West traffic inspection, crucial for preventing lateral threat
movement, and Layer 7 network runtime security through deep packet inspection, which controls
applications, users, and content to protect against sophisticated threats.
VM-Series Public Cloud Deployments 564 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on Google Cloud Platform
VM-Series Public Cloud Deployments 565 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on Google Cloud Platform
The NSI architecture operates on a producer-consumer model for scalable security. In this
```
model, security services (the producer) are deployed as a scalable backend behind a Google
```
```
Cloud internal load balancer, serving workloads (the consumer). Key components include Palo
```
Alto Networks® software firewalls with a load balancer for advanced threat prevention and
efficient traffic distribution, along with Intercept Deployments and Endpoint Groups for security
enforcement and policy management. Geneve encapsulation is used to tunnel traffic to the
firewall for inspection without requiring extensive network modifications. Within the Geneve
```
packets, both the Security Profile Group ID (SPG-ID) and VPC ID are passed, providing context for
```
traffic.
NSI offers two primary modes:
```
• Inline (Packet Intercept) — Provides inline inspection for real-time threat prevention and
```
blocking.
```
• Out-of-Band (Packet Mirroring) — Offers out-of-band monitoring for non-disruptive threat
```
intelligence, compliance, and auditing.
Prerequisites
Before configuring the VM-Series firewall, ensure the following prerequisites are met:
VM-Series Public Cloud Deployments 566 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on Google Cloud Platform
```
• Google Cloud Network Security Integration (NSI) Environment Setup:
```
• Fully provisioned and operational Google Cloud NSI environment.
• Producer and Consumer VPCs defined and interconnected.
• Intercept Deployments and Endpoint Groups configured and linked.
• Firewall rules in the Consumer VPC configured for Layer 7 redirection.
• Palo Alto Networks® VM-Series Firewall Deployment:
• A VM-Series firewall instance deployed within your Google Cloud Producer VPC.
```
Google Cloud Deployment (for VM-Series Firewall Configuration):
```
STEP 1 | Create a Security Profile Group.
• In GCP, go to Network Security Integration > Security Profile Groups.
• Click Create Security Profile Group.
```
• Define traffic inspection policies (For example: allow/block rules).
```
• Click Save.
This defines inspection criteria for intercepted traffic.
STEP 2 | Set Up Intercept Endpoint Group
• Go to Network Security Integration > Intercept Endpoint Groups.
• Click Create Intercept Endpoint Group.
```
• Select the consumer VPC(s) whose traffic should be intercepted.
```
• Associate the relevant Security Profile Group.
• Click Save.
This links consumer VPCs to the security inspection pipeline.
STEP 3 | Create Intercept Deployment Group
In the producer project:
• Go to Network Security Integration > Intercept Deployment Groups.
• Click Create Intercept Deployment Group.
• Associate the previously created Intercept Endpoint Group.
```
• Specify load balancing details if needed (to direct traffic to VM-Series firewall).
```
• Click Save.
VM-Series Public Cloud Deployments 567 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on Google Cloud Platform
STEP 4 | Deploy the Intercept Deployment
• Go to Intercept Deployments.
• Click Create Intercept Deployment.
• Link it to the Intercept Deployment Group.
• Configure backend service/load balancer pointing to VM-Series firewall NICs.
• Save.
This step deploys the inspection service tied to the endpoint and deployment groups.
STEP 5 | Configure Firewall Rules in Consumer VPCs.
• In each consumer VPC, configure firewall rules to permit traffic destined for the Intercept
Endpoint Group.
```
• (Optional), Set explicit routes if required by your architecture.
```
STEP 6 | Enable Geneve Encapsulation on the VM-Series Firewall.
You must configure the VM-Series firewall to handle Geneve-encapsulated packets.
Option A: Enable via CLI:
SSH into the VM-Series firewall and run the following command:
request plugins vm_series geneve-inspect enable yes|no
This command requires you to reboot the VM-Series firewall.
Commit
Option B: Enable via Bootstrap Configuration:
Add the following setting to the init-cfg.txt in your bootstrap package:
geneve-inspect=enable
Configure necessary firewall rules in GCP to permit traffic redirection. You must
ensure that routing rules allow return traffic post-inspection and validate endpoint
associations across VPCs.
You can validate the deployment initiating the test traffic between VMs in the
consumer VPC.
• On the VM-Series firewall, go to Monitor > Traffic Logs for intercepted traffic
entries.
• Confirm traffic is processed according to your policies.
VM-Series Public Cloud Deployments 568 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on Google Cloud Platform
Configure GCP NSI Overlay Support
Where Can I Use This? What Do I Need?
• VM-Series PAN-OS® 12.1.8 or later
GCP NSI Overlay Support extends your VM-Series firewall deployments within Google Cloud
```
Platform's Network Security Intercept (NSI) framework. This feature enables your VM-Series to
```
operate in a bump-in-the-wire mode, providing advanced network visibility and security without
requiring changes to your existing network routing policies.
It introduces overlay functionality, allowing inspected packets to egress directly from your
firewall rather than being hairpinned back to your consumer VPCs. This architecture operates
on a producer-consumer model where your VM-Series firewalls act as the producer of security
services, and your workloads are the consumers. This architecture helps you reduce overall
deployment costs by centralizing egress for all your consumer VPCs.
In your Google Cloud environment, GCP NSI transparently redirects traffic from your Workload
VPCs to your VM-Series firewalls. This redirection is initiated by VPC firewall policies applying to
```
a Security Profile Group (SPG) and Security Profile (SP) configured for Custom Intercept, directing
```
```
traffic to an Intercept Endpoint Group (EPG) and Deployment Group (DPG).
```
```
A forwarding rule then sends geneve-encapsulated traffic to an Internal Load Balancer (ILB),
```
distributing it to your cross-zone deployed VM-Series instances. Your VM-Series firewalls,
```
provisioned with management (nic0), trust (nic1), and untrust (nic2) network interfaces,
```
decapsulate these Geneve packets for deep inspection. With NSI overlay support, inner routing is
enabled, allowing your firewall to use its routing table to forward inspected traffic directly.
Autoscaling is currently not supported in GCP NSI Overlay.
VM-Series Public Cloud Deployments 569 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on Google Cloud Platform
Configure GCP NSI Overlay Support Using CLI
This procedure details how to enable and configure GCP NSI Overlay Support on your VM-
Series firewall. This feature allows your firewall to perform direct packet egress in a GCP NSI
environment.
This procedure assumes your VM-Series software firewall is already deployed within a
GCP NSI environment and is running PAN-OS 12.1.8 or later.
```
STEP 1 | Follow steps 1–5 to configure your Google Cloud Network Security Integration (NSI)
```
environment.
While configuring your GCP environment for NSI, ensure that you configure nic0 as
Management, nic1 as Trust, and nic2 as Untrust interfaces.
Keep regional restrictions in mind during deployment. Your security endpoint
placement rules and the target consumer workloads must reside in the same
geographic region.
STEP 2 | Implement PAN-OS device configuration.
Log in to your VM-Series firewall and configure the interfaces using the PAN-OS CLI.
1. Assign all application workload VPC traffic to enter dynamically through nic1
```
(ethernet1/1).
```
set network interface ethernet ethernet1/1 layer3 dhcp-
client enable yes set network virtual-router default interface
ethernet1/1 set zone Trust network layer3 ethernet1/1
2. Configure overlay egress out of nic2 (ethernet1/2).
set network interface ethernet ethernet1/2 layer3 dhcp-
client enable yes set network virtual-router default interface
ethernet1/2 set zone Untrust network layer3 ethernet1/2
3. Disable the default route for the data plane interface.
1. Enter set network interface ethernet1/1 layer3 config-type
static no-default-route yes
2. Replace ethernet1/1 with the actual interface connected to your Application VPCs.
4. Commit the configuration changes.
STEP 3 | Configure Egress NAT.
1. Configure the no-NAT rule for east-west Trust-to-Trust traffic.
set rulebase nat rules no-nat-east-west from Trust to Trust set
rulebase nat rules no-nat-east-west source any destination any
service any
2. Configure source NAT (SNAT) for north-south Trust-to-Untrust traffic.
set rulebase nat rules egress-nat from Trust to Untrust set
rulebase nat rules egress-nat source any destination any
VM-Series Public Cloud Deployments 570 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on Google Cloud Platform
service any set rulebase nat rules egress-nat source-translation
dynamic-ip-and-port interface-address interface ethernet1/2
3. Commit the changes.
Perform the GCP NSI Health Check
STEP 1 | If the producer project was configured with an internal load balancer and regional health
checks, run the infrastructure deployment command.
google_compute_region_health_check.main
STEP 2 | Ensuring your firewall instances can respond to Google Cloud probing requires the proper
configuration of network management profiles, allowed IP ranges, and security policy rules.
To enable HTTPS management capabilities on the firewall to allow GCP probing, execute the
```
command:
```
set network profiles interface-management profile gcp-lb-profile
https yes
STEP 3 | Group the health check source addresses to permit incoming probes through the rulebase.
set address gcp-lb-check-ip-1 ip-netmask 35.191.0.0/16 set address
gcp-lb-check-ip-2 ip-netmask 130.211.0.0/22 set address gcp-lb-check-
ip-3 ip-netmask 209.85.152.0/22 set address gcp-lb-check-ip-4 ip-
netmask 209.85.204.0/22 set address-group gcp-lb-check-ips static
[ gcp-lb-check-ip-1 gcp-lb-check-ip-2 gcp-lb-check-ip-3 gcp-lb-check-
ip-4 ]
```
STEP 4 | Allow the GCP load balancer and Managed Instance Group (MIG) probe IP blocks within the
```
management profile.
set network profiles interface-management-profile gcp-lb-profile
https yes set network profiles interface-management-profile gcp-lb-
profile permitted-ip 35.191.0.0/16 set network profiles interface-
management-profile gcp-lb-profile permitted-ip 130.211.0.0/22
set network profiles interface-management-profile gcp-lb-profile
permitted-ip 209.85.152.0/22 set network profiles interface-
management-profile gcp-lb-profile permitted-ip 209.85.204.0/22
STEP 5 | Retrieve the load balancer IP for your deployment and configure static routes so the firewall
```
returns health check responses via ethernet1/1 (nic1).
```
1. Run the following gcloud command to retrieve the forwarding rule IP:
gcloud compute forwarding-rules list
2. Use the returned IP address to configure the address object and loopback interface. For
example, if the IP is 10.120.1.2:
set address gcp-lb-fwd-rule-1 ip-netmask 10.120.1.2/32 set address-
group gcp-lb-fwd-rules static [ gcp-lb-fwd-rule-1 ] set network
interface loopback units loopback.1 ip gcp-lb-fwd-rule-1 set
network virtual-router default interface loopback.1 set zone
gcp-lb-check network layer3 loopback.1 set network interface
loopback units loopback.1 interface-management-profile gcp-lb-
VM-Series Public Cloud Deployments 571 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on Google Cloud Platform
profile set network virtual-router default routing-table ip static-
route gcp-healthcheck-1 destination 130.211.0.0/22 interface
ethernet1/1 nexthop ip-address 10.120.1.1 set network virtual-
router default routing-table ip static-route gcp-healthcheck-2
destination 35.191.0.0/16 interface ethernet1/1 nexthop ip-address
10.120.1.1
STEP 6 | Configure the security policy rule to allow health check traffic.
set rulebase security rules gcp-lb-check-allow from any to any set
rulebase security rules gcp-lb-check-allow source gcp-lb-check-
ips set rulebase security rules gcp-lb-check-allow destination
gcp-lb-fwd-rules set rulebase security rules gcp-lb-check-allow
application ssl set rulebase security rules gcp-lb-check-allow
service application-default set rulebase security rules gcp-lb-check-
allow action allow
STEP 7 | Once deployed, health check performance can be audited directly from the GCP
environment via the gcloud CLI toolset:
1. To verify the Internal Load Balancer backend health status:
gcloud compute backend-services get-health
backend-service-name --region=region --
```
format="table(status.healthStatus[0].instance,status.healthStatus[0].healthS
```
2. To verify the Managed Instance Group (MIG) detailed state:
gcloud compute instance-groups managed
list-instances mig-name --region=region --
```
format="table(name,instanceHealth[0].detailedHealthState,currentAction)"
```
Enable GCP NSI Overlay Support on the VM-Series Firewall
STEP 1 | Enable the GCP NSI inspection plugin.
request plugins vm_series gcp nsi inspect enable yes
This activates the core GCP NSI Overlay Support feature, allowing your firewall to process
Geneve-encapsulated traffic for inspection.
STEP 2 | Verify the GCP NSI inspection status.
show plugins vm_series gcp nsi status
STEP 3 | Verify Geneve encapsulation and decapsulation counters for traffic inspection.
show counter global filter delta yes | match geneve
Observe incrementing geneve_encap and geneve_decap counters to confirm your firewall
is processing NSI-related traffic.
VM-Series Public Cloud Deployments 572 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on Google Cloud Platform
STEP 4 | Configure pod traffic visibility for GKE workloads.
Complete the following to allow pod traffic to reach your firewalls in the producer project.
1. Enable intranode visibility for pod-to-pod traffic.
This may take some time to propagate if you enable it after the cluster is already
running.
2. Deploy the ip-masq-agent DaemonSet on all cluster nodes so the firewall can see
pod-to-pod traffic.
```
apiVersion: apps/v1
```
```
kind: DaemonSet
```
```
metadata:
```
```
name: ip-masq-agent
```
```
namespace: kube-system
```
```
labels:
```
k8s-app: ip-masq-agent
```
spec:
```
```
selector:
```
```
matchLabels:
```
k8s-app: ip-masq-agent
```
template:
```
```
metadata:
```
```
labels:
```
k8s-app: ip-masq-agent
```
spec:
```
```
hostNetwork: true
```
```
priorityClassName: system-node-critical
```
```
tolerations:
```
- operator: Exists
```
nodeSelector:
```
kubernetes.io/os: linux
```
containers:
```
- name: ip-masq-agent
```
image: registry.k8s.io/networking/ip-masq-
```
```
agent:v2.8.0
```
```
args:
```
- --masq-chain=IP-MASQ
- --nomasq-all-reserved-ranges=false
- --v=2
```
securityContext:
```
```
privileged: true
```
```
capabilities:
```
```
add: ["NET_ADMIN", "NET_RAW"]
```
```
volumeMounts:
```
- name: config
```
mountPath: /etc/config
```
```
volumes:
```
- name: config
```
configMap:
```
```
name: ip-masq-agent
```
```
optional: true
```
```
items:
```
- key: config
VM-Series Public Cloud Deployments 573 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on Google Cloud Platform
```
path: ip-masq-agent
```
3. Update the ip-masq-agent ConfigMap in kube-system to add the specific CIDRs to
the nonMasqueradeCIDRs section, ensuring pod traffic reaches the firewall via the NSI
fabric while maintaining original pod IPs.
```
apiVersion: v1
```
```
kind: ConfigMap
```
```
metadata:
```
```
name: ip-masq-agent
```
```
namespace: kube-system
```
```
data:
```
```
config: |
```
```
nonMasqueradeCIDRs:
```
- 0.0.0.0/0
- 10.40.0.0/16 # Replace with your GKE Management/
Control Plane subnet
```
resyncInterval: 60s
```
4. (Optional) To inspect inter-VPC traffic, configure Network Connectivity Center (NCC).
Disable GCP NSI Overlay Support
Use this procedure to deactivate GCP NSI Overlay Support on your VM-Series firewall.
STEP 1 | Disable GCP NSI inspection.
request plugins vm_series gcp nsi inspect enable no
STEP 2 | Commit the configuration changes.
VM-Series Public Cloud Deployments 574 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on Google Cloud Platform
Secure Boot Support for VM-Series on GCP
Secure Boot for VM-Series firewalls enhances your security posture by ensuring the integrity of
the boot process. Secure Boot verifies that only trusted software components are loaded during
startup, protecting against malicious code injection and unauthorized modifications to the boot
```
sequence. Secure Boot leverages the Unified Extensible Firmware Interface (UEFI) and a chain
```
of trust established through cryptographic signatures. It prevents rootkits, bootkits, low-level
attacks, ensures boot integrity, and provides confidence in the authenticity of your VM-Series
instances across your cloud environment.
Prerequisites
PAN-OS Version 12.1 or later
• Secure boot support is available only for fresh installations of VM-Series with PAN-OS
version 12.1 or later. Secure boot will not be enabled for upgraded VM-Series models.
• Make sure to enable UEFI boot mode when creating the GCP instance.
• Secure Boot is enabled by default on GCP when explicitly turned on during instance
creation.
• If you want to downgrade your VM-Series firewall, you must disable Secure Boot in the
GCP Console and then restart the VM-instance before you begin the downgrade.
Enable UEFI boot mode and Secure Boot Support for VM-Series on GCP
Perform the following steps to enable UEFI boot mode and secure boot support for VM-Series on
```
GCP:
```
1. From the GCP console, select Compute Engine > VM instances.
2. In the Boot Disk Settings section, select an VM-Series image that supports UEFI and Secure
Boot.
VM-Series Public Cloud Deployments 575 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on Google Cloud Platform
3. Go to the Security and Access section, enable the following options:
• Secure Boot
```
• vTPM (Virtual Trusted Platform Module)
```
• Integrity Monitoring
VM-Series Public Cloud Deployments 576 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on Google Cloud Platform
VM-Series Public Cloud Deployments 577 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on Google Cloud Platform
For more information on creating VM-Series instances on GCP, see Set Up the VM-Series Firewall
on Google Cloud Platform and Create a Custom VM-Series Firewall Image for Google Cloud
Platform.
To verify the secure boot support on your VM-Series instance on GCP, SSH into the Command
```
Line Interface (CLI) of the VMSeries firewall and run the following command:
```
show system secure-boot status
VM-Series Public Cloud Deployments 578 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on Google Cloud Platform
Configuring GCP Load Balancer
Where Can I Use This? What Do I Need?
```
• Google Cloud Platform (GCP) VM-Series License (PAYG or BYOL)
```
VM-Series plugin
Panorama
Panorama plugin for GCP
The following are ways to configure your GCP load balancer:
Onboarding External Load Balancer
The external TCP load balancer distributes TCP/UDP traffic from the internet to the VM-Series
firewall. Internal applications can be onboarded by creating a forwarding rule for each application.
Here, we will onboard two applications by allocating frontend IPs to an external TCP load
balancer.
Before you begin, you need the following:
```
• The IPs of the backend applications (i.e. app1: 10.1.0.10, app2: 10.2.0.10).
```
• If you do not have an environment, use this Terraform plan to build a test bed environment.
Following are the steps to onboard external TCP load balancer:
VM-Series Public Cloud Deployments 579 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on Google Cloud Platform
1. Login to your GCP console and create the External TCP/UDP Load Balancer.
2. Configure the backend service.
Here is an example:
gcloud compute health-checks create tcp vmseries-hc \
--request=/php/login.php \
--port=80 \
--region=us-central1
gcloud compute backend-services create vmseries-external-lb \
--load-balancing-scheme=EXTERNAL \
--protocol=TCP \
VM-Series Public Cloud Deployments 580 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on Google Cloud Platform
--health-checks=vmseries-hc \
--health-checks-region=us-central1 \
--region=us-central1
gcloud compute backend-services add-backend vmseries-external-lb \
--instance-group=vmseries-us-central1-a \
--instance-group-zone=us-central1-a \
--region=us-centrall
3. Create a forwarding rule for each application.
gcloud compute forwarding-rules create app1 \
--load-balancing-scheme=EXTERNAL \
--region=us-central1 \
--ports=ALL \
--backend-service=vmseries-external-lb
gcloud compute forwarding-rules create app2 \
--load-balancing-scheme=EXTERNAL \
--region=us-central1 \
--ports=ALL \
--backend-service=vmseries-external-lb
VM-Series Public Cloud Deployments 581 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on Google Cloud Platform
4. Click Create.
5. On your VM-Series firewall web interface, create two NAT policies to IP map the load balancer
forwarding rule address to the correct internal application.
You can see the following details in your traffic logs:
Automation Example:
Below is a Terraform code sample that automates the manual steps above.
A forwarding rule is created on an existing external TCP load balancer. The forwarding rule
address is used within the VM-Series NAT policy to map to a backend application.
# Create GCP LB forwarding rule
```
resource "google_compute_forwarding_rule" "default" {
```
VM-Series Public Cloud Deployments 582 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on Google Cloud Platform
```
name = "my-forwarding-rule"
```
```
target = var.target
```
```
region = "us-central1"
```
```
load_balancing_scheme = "EXTERNAL"
```
```
all_ports = true
```
```
}
```
# Create VM-Series NAT policy
```
resource "panos_nat_rule_group" "main" {
```
```
provider = panos
```
```
position_keyword = "bottom"
```
```
rule {
```
```
name = "my-nat-policy"
```
```
original_packet {
```
```
source_zones = ["untrust"]
```
```
destination_zone = "untrust"
```
```
destination_interface = "ethernet1/1"
```
```
service = "any"
```
```
source_addresses = ["any"]
```
```
destination_addresses =
```
```
["${google_compute_forwarding_rule.default.ip_address}"]
```
```
}
```
```
translated_packet {
```
```
source {
```
```
dynamic_ip_and_port {
```
```
interface_address {
```
```
interface = "ethernet1/2"
```
```
}
```
```
}
```
```
}
```
```
destination {
```
```
dynamic_translation {
```
```
address = "<ip-address>"
```
```
}
```
```
}
```
```
}
```
```
}
```
Onboarding Global HTTPS Load Balancer
```
The Global HTTP(s) Load Balancer distributes traffic from the internet to the VM-Series firewall.
```
Internal applications can be onboarded by creating port mappings between the backend service
and VM-Series NAT policies. Here, we will onboard two separate HTTP applications using port
mappings.
Before you begin, you need the following:
```
• The IPs of the backend applications (i.e. app1: 10.1.0.10, app2: 10.2.0.10).
```
```
• A unique port number to map each application (i.e. app1:TCP/1000, app2:TCP/2000).
```
• If you do not have an environment, use this Terraform plan to build a test bed environment.
VM-Series Public Cloud Deployments 583 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on Google Cloud Platform
Following are the steps to onboard the global HTTPS load balancer:
1. Log in to your GPS console and create a health check for app1 and app2.
2. Create a Global HTTPS Load Balancer.
3. Create 2 frontend addresses on port TCP/80. Each frontend will map to a backend application.
4. Create a backend service for each application. Select the corresponding names port and health
check for each application.
This is an example:
gcloud compute instance-groups set-named-ports vmseries \
--region=us-central1 \
--named-ports=app1:1000,app2:2000
gcloud compute backend-services create app1 \
--load-balancing-scheme=EXTERNAL_MANAGED \
--protocol=HTTP \
--port-name=app1 \
--health-checks=app1 \
--connection-draining-timeout=300 \
--global
gcloud compute backend-services add-backend app1 \
--instance-group=vmseries \
--instance-group-region=us-central1 \
--balancing-mode=RATE \
--max-rate-per-instance=10000 \
--global
gcloud compute backend-services create app2 \
--load-balancing-scheme=EXTERNAL_MANAGED \
--protocol=HTTP \
--port-name=app2 \
--health-checks=app2 \
--connection-draining-timeout=300 \
--global
gcloud compute backend-services add-backend app2 \
--instance-group=vmseries \
--instance-group-region=us-central1 \
--balancing-mode=RATE \
--max-rate-per-instance=10000 \
--global
gcloud compute url-maps create global-https-lb \
--default-service app1 \
--global
gcloud compute target-http-proxies create global-https-lb-target-
proxy \
--url-map=global-https-lb \
--global-url-map \
--global
gcloud compute forwarding-rules create app1 \
VM-Series Public Cloud Deployments 584 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on Google Cloud Platform
--load-balancing-scheme=EXTERNAL_MANAGED \
--network-tier=PREMIUM \
--target-http-proxy=global-https-lb-target-proxy \
--ports=80 \
--global
gcloud compute forwarding-rules create app2 \
--load-balancing-scheme=EXTERNAL_MANAGED \
--network-tier=PREMIUM \
--target-http-proxy=global-https-lb-target-proxy \
--ports=80 \
--global
5. Configure the routing rules. Set the frontend address as the host to direct traffic to each
backend.
6. On your VM-Series firewall web interface, create 2 NAT policies to map the named port to the
correct destination.
Automation Example:
```
Here is a Terraform example that onboards a new backend service to an existing HTTP(s) load
```
balancer. The PAN-OS Terraform provider creates a service object and NAT policy for the new
```
service:
```
# Assign named port to instance group
```
resource "google_compute_instance_group_named_port" "main" {
```
```
group = var.instance_group
```
```
zone = “us-central1-a”
```
```
name = "app2"
```
```
port = "2000"
```
```
}
```
# Create health check
```
resource "google_compute_health_check" "main" {
```
```
name = "app2"
```
```
tcp_health_check {
```
```
port = "2000"
```
```
}
```
```
}
```
# Create backend service
```
resource "google_compute_backend_service" "main" {
```
```
name = "app2"
```
```
port_name = "app2"
```
```
load_balancing_scheme = "EXTERNAL_MANAGED"
```
```
health_checks = [google_compute_health_check.main.self_link]
```
```
backend {
```
```
balancing_mode = "RATE"
```
```
capacity_scaler = 1
```
```
group = var.instance_group
```
```
max_rate_per_instance = "10000"
```
```
}
```
```
}
```
# Create forwarding rule
VM-Series Public Cloud Deployments 585 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on Google Cloud Platform
```
resource "google_compute_global_forwarding_rule" "main" {
```
```
name = "app2"
```
```
load_balancing_scheme = "EXTERNAL_MANAGED"
```
```
port_range = "80"
```
```
target = var.global_lb_self_link
```
```
}
```
# Create VM-Series service object
```
resource "panos_service_object" "main" {
```
```
name = "app2"
```
```
vsys = "vsys1"
```
```
protocol = "tcp"
```
```
destination_port = "2000"
```
```
}
```
# Create VM-Series NAT policy
```
resource "panos_nat_rule_group" "main" {
```
```
provider = panos
```
```
position_keyword = "bottom"
```
```
rule {
```
```
name = "app2"
```
```
original_packet {
```
```
source_zones = ["untrust"]
```
```
destination_zone = "untrust"
```
```
destination_interface = "ethernet1/1"
```
```
service = panos_service_object.main.name
```
```
source_addresses = ["any"]
```
```
destination_addresses = ["any"]
```
```
}
```
```
translated_packet {
```
```
source {
```
```
dynamic_ip_and_port {
```
```
interface_address {
```
```
interface = "ethernet1/2"
```
```
}
```
```
}
```
```
}
```
```
destination {
```
```
dynamic_translation {
```
```
address = "<ip-address>"
```
```
}
```
```
}
```
```
}
```
```
}
```
```
}
```
```
Configuring Global HTTP(s) Load Balancer with XFF Header
```
The Palo Alto Networks NGFW can read the XFF field and use the XFF IP address when enforcing
security policy. Additionally, you can configure various logs and reports to display the XFF IP
address along with the source IP address.
VM-Series Public Cloud Deployments 586 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on Google Cloud Platform
Following are the steps to add Client Source IP Header to HTTPS Load Balancer
1. Run the following gcloud command to add the client’s source IP address as a custom header.
Replace <backend-services> with your backend service that contains the VM-Series
instance group.
gcloud compute backend-services update <backend-service> \
--global \
```
--custom-request-header='X-Forwarded-For:{client_ip_address}'
```
VM-Series Public Cloud Deployments 587 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on Google Cloud Platform
2. Your HTTPS load balancer’s custom request headers should like the image below:
VM-Series Public Cloud Deployments 588 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on Google Cloud Platform
3. In your VM-Series web interface, go to Device > Setup > Content-ID >X-Forwarded-For
Headers.
4. Set Use X-Forwarded-For Header to Enabled for Security Policy.
5. Commit the changes.
The following are the steps to view the Custom Header in Traffic Logs:
1. Go to Monitor > Traffic.
VM-Series Public Cloud Deployments 589 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on Google Cloud Platform
2. Add the X-Forward-For IP log field to view the client IP address.
3. Curl your web server through the HTTPS load balancer.
4. The traffic logs should now contain your client source IP address under the X-Forwarded-For
IP column.
VM-Series Public Cloud Deployments 590 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on Google Cloud Platform
Autoscaling the VM-Series Firewall on Google Cloud
Platform
Where Can I Use This? What Do I Need?
```
• Google Cloud Platform (GCP) VM-Series License (PAYG or BYOL)
```
VM-Series plugin
Panorama
Panorama plugin for GCP
```
The Panorama plugin for Google Cloud Platform (GCP) version 2.0.0 assists you in deploying
```
the VM-Series firewall in GCP and enables Panorama to manage VM-Series firewalls securing
VM monitoring or auto scaling deployments in GCP. Using Panorama for centralized policy and
firewall management increases operational efficiency in managing and maintaining a distributed
network of firewalls.
With Panorama maintaining your GCP managed instance groups you can create application
enablement policies that protect and control the network.
The auto scaling deployment supports using a shared VPC network configuration or VPC network
peering to create a common VPC network in which a host project contains shared VPC networks
and the VM-Series firewalls, and a service project contains a vm-based or container-based
```
application deployment (a Kubernetes cluster). Palo Alto Networks supplies templates to help you
```
deploy the VM-Series firewalls in the host project and deploy an optional sample application in
the service project.
BYOL and PAYG licenses can be used for the VM-Series firewalls. During licensing, VM-Series
firewall instances talk directly to the Palo Alto Networks license server.
If you choose BYOL your deployment can deactivate license instances in response to a scale-
down event. If a VM-Series firewall’s deployment information is configured in the Panorama
plugin for GCP and the firewall is automatically removed, Panorama detects the firewall status and
automatically deregisters the firewall.
Auto Scaling Components for Google Cloud Platform
Typical GCP auto scaling deployments use a host project and a service project and form a
common VPC network between the two. The Panorama plugin for GCP can secure an auto
scaling deployment in a single project with host and service VPCs, or host and service projects
in a shared VPC or peered VPC network configuration, where the host project contains the VM-
Series firewalls and the shared VPC networks, and the service project contains your application
deployment. If your application is deployed in a Kubernetes cluster, a peered VPC is required.
Auto Scaling Requirements
General Requirements—Ensure your environment meets the basic requirements.
VM-Series Public Cloud Deployments 591 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on Google Cloud Platform
Panorama plugin for GCP—If you have not done so, Install the Panorama Plugin for GCP.
If you previously installed the Panorama plugin for GCP version 1.0.0, remove it before
you install 2.0.X. You cannot upgrade.
Palo Alto Networks Auto Scale templates version 1.0—Palo Alto Networks provides the
templates to deploy VM-Series firewall instances in the host project and configure and deploy
a sample application in a service project. See About the Auto Scaling Templates for more about
the templates.
Download the templates from GitHub. The zip file contains separate zip files for the firewall
and application templates.
Prepare to Deploy the Auto Scaling Templates
Complete the following tasks before you deploy the auto scaling templates.
Prepare a Host Project and Required Service Accounts
You need a host project and a service project to form the shared VPC topology that supports
the firewall and application templates. You can create a new host project or prepare an existing
project to act as your host.
To set up the Shared VPC an organization administrator must grant the host project administrator
the Shared VPC admin role. The Shared VPC admin can enable a project to act as a host, and
grant the Service Project admin role to the service project administrator. Review the GCP
documentation on Administrators and IAM roles.
STEP 1 | In the GCP console, create a GCP project to act as the host. If you want to use an existing
project, skip to the next step.
To create a new project, select your organization or No organization, click New Project and fill
in your project information. Note, this is your only chance to EDIT the project ID.
The Google Cloud SDK must be installed and configured so that you can authenticate
with your host project from the CLI. You will use the command-line interface to deploy
the firewall template and the application template, and to attach the service project to
the host project.
VM-Series Public Cloud Deployments 592 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on Google Cloud Platform
STEP 2 | Enable APIs and services required for auto scaling. The required APIs are:
Cloud Pub/Sub API
Cloud Deployment Manager API
Cloud Storage API
Compute Engine API
Google Compute Engine Instance Group Manager API
Google Compute Engine Instance Group Updater API
Google Compute Engine Instance Groups API
Kubernetes Engine API
Stackdriver API
Stackdriver Logging API
Stackdriver Monitoring API
You can enable APIs from the GCP console or the GCP CLI, as shown below.
Enable APIs from the GCP console.
1. Select the host project, and from the Navigation menu, select APIs & Services.
2. Search for and view each required API.
3. ENABLE any APIs that don't display the “API enabled” status.
Enable APIs from the CLI.
1. In the CLI, view your configuration to ensure that you are in the correct project.
gcloud config list
If not, set the project as follows:
gcloud config set project <project-name>
2. Issue the following commands to enable the required APIs.
gcloud services enable pubsub.googleapis.com
gcloud services enable deploymentmanager.googleapis.com
gcloud services enable storage-component.googleapis.com
gcloud services enable compute.googleapis.com
gcloud services enable replicapool.googleapis.com
gcloud services enable replicapoolupdater.googleapis.com
gcloud services enable resourceviews.googleapis.com
gcloud services enable container.googleapis.com
gcloud services enable stackdriver.googleapis.com
gcloud services enable logging.googleapis.com
VM-Series Public Cloud Deployments 593 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on Google Cloud Platform
gcloud services enable monitoring.googleapis.com
3. Confirm that the required APIs are enabled.
gcloud services list --enabled
STEP 3 | Create a service account for deploying the VM-Series firewall, and assign the IAM roles
required for auto scaling a service or a Kubernetes cluster.
When you configure the firewall templates, you add the email address for this service account
to the VM-Series firewall .yaml file. Within the host project, the template uses credentials
VM-Series Public Cloud Deployments 594 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on Google Cloud Platform
from this service account to create a host VPC with subnets, deploy VM-Series firewalls in the
VPC, configure Stackdriver custom metrics, create a Pub/Sub topic, and more.
1. In the GCP console, select IAM & Admin > Service accounts and select +CREATE SERVICE
ACCOUNT.
Fill in the service account details and click CREATE.
2. Give the service account permission to auto-scale resources in this project.
Select a role type from the drop menu, and on the right, select an appropriate access level.
For example, select Project > Editor. You can select multiple roles for a service account.
Compute Engine > Compute Admin
Compute Engine > Compute Network User
Pub/Sub > Admin
Monitoring > Monitoring Metric Writer
Stackdriver > Stackdriver Accounts Editor
Storage > Storage Admin
```
(GKE only) Kubernetes > Kubernetes Engine Cluster Admin
```
```
(GKE only) Kubernetes > Kubernetes Engine Viewer
```
Continue when you are finished adding roles.
3. Click +CREATE KEY to create a key for the host service account.
```
• (Optional) Add email addresses to grant other users or administrators access to this
```
service account.
• Click JSON to download the private key in JSON form.
• Store the key in a safe location. You will need this key when you Deploy GCP
Autoscaling Templates.
4. Click DONE.
VM-Series Public Cloud Deployments 595 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on Google Cloud Platform
STEP 4 | Create a service account that a Panorama administrator can use to interact with this host
project.
1. In the GCP console, select IAM & Admin > Service accounts and select +CREATE SERVICE
ACCOUNT.
2. Fill in the service account details and click CREATE.
3. Grant service account access.
Select a role type from the drop menu, and on the right, select an appropriate access level.
For example, select Project > Editor. You can select multiple roles for a service account.
Compute Engine > Compute Viewer
Deployment Manager > Viewer
Pub/Sub > Admin
Click CONTINUE.
4. Click +CREATE KEY to create a key for the host service account.
```
• (Optional) Add email addresses to grant other users or administrators access to this
```
service account.
• Select JSON to download the private key in JSON form.
• Store the key in a safe location. You will need this key when you Deploy GCP
Autoscaling Templates.
```
STEP 5 | (Optional) In the CLI, ensure you can communicate with your new host project.
```
1. Set your project to the host project you created.
gcloud set project <your-autoscale-host-project-name>
2. Create a configuration for auto scaling. Your new configuration is automatically activated
unless you disable activation.
gcloud config configurations create <CONFIGURATION_NAME> gcloud
config list
Obtain a Licensing API Key
You need a Licensing API key so Panorama can license and de-license managed assets in GCP.
STEP 1 | Log in to the Support portal and selectAssets > Licensing API and click Enable. The key is
displayed.
Only a Super User can view the Enable link to generate this key. See How to Enable,
Regenerate, Extend the Licensing API Key.
STEP 2 | Select the key and copy it.
VM-Series Public Cloud Deployments 596 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on Google Cloud Platform
STEP 3 | From the CLI, SSH in to Panorama and issue the following command, replacing <key> with
the API key you copied from the support portal:
request license api-key set key <key>
API Key is successfully set
Configure the Panorama Plugin for GCP to Secure an Auto Scaling Deployment
In Panorama, create assets to support the auto scaling firewall deployment.
STEP 1 | Create a template, and a template stack that includes the template, and Commit the changes.
STEP 2 | In the Network context, select either the template or the template stack. Select Virtual
Routers and Add a virtual router.
When the firewall template creates static routes, they are added to this virtual router.
Define only one router for the auto scale deployment.
VM-Series Public Cloud Deployments 597 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on Google Cloud Platform
STEP 3 | In the Network context, select the template you created, select Interfaces and Add
Interface.
• On the Config tab, select a slot, select the Interface name and select the Layer3 Interface
Type. From the Security Zone menu, select New Zone, name the zone Untrust and click
OK.
• On the IPv4 tab enable DHCP Client and Automatically create default route pointing to
```
default gateway provided by server (enabled by default) and click OK.
```
```
STEP 4 | Add the ethernet1/2 (Trust) Layer 3 interface.
```
• On the Config tab, choose the same slot as the previous step, select the Interface name
```
(ethernet1/2), and select the Layer3 Interface Type. From the Security Zone menu, select
```
New Zone name the zone Trust and click OK.
• On the IPv4 tab enable DHCP Client, disable Automatically create default route pointing to
default gateway provided by server and click OK.
VM-Series Public Cloud Deployments 598 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on Google Cloud Platform
STEP 5 | Return to your template stack and the virtual router you created earlier. Place the untrust
```
and trust interfaces (ethernet1/1 and ethernet1/2) in the virtual router, and click OK.
```
STEP 6 | Configure the Stackdriver for your auto scaling deployment.
You must have the VM-Series plugin on Panorama to configure Stackdriver.
1. In the Device context, select the template stack you created earlier from the template
drop menu.
2. Select Device > VM-Series > Google and click the Edit cog ( ). Enable Publish PAN-
OS metrics to Stackdriver.
3. Commit your changes.
VM-Series Public Cloud Deployments 599 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on Google Cloud Platform
STEP 7 | Create a Device Group that references the template or template stack you created in step 1.
This Device Group will contain the VM-Series firewalls you create with the firewall template.
1. Add a security policy that allows web-browsing traffic from Untrust to Trust.
In the Policies context, select the Device Group you created. Select Security > Pre Rules
and Add the following security policy.
STEP 8 | Set up the GCP service account for the host project.
1. In the Panorama context, expand Google Cloud Platform, select Setup, and click Add.
2. Supply a name and description for the host service account you created in Step 4.
3. Upload the JSON credentials file you created in Step 4.4.
After you add a service account credential, you can validate the credential from your
```
Panorama command line (you cannot validate from the web interface):
```
request plugins gcp validate-service-account
gcp_service_account <svc-acct-credential-name>
VM-Series Public Cloud Deployments 600 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on Google Cloud Platform
STEP 9 | Set up auto scaling on the Panorama plugin for GCP.
1. In the Panorama context, expand Google Cloud Platform, select AutoScaling, and click
Add.
2. Supply the firewall Deployment Name and an optional description for the deployment.
3. For the GCP Service Account Credential, supply the GCP service account name from
Step 8.
4. Choose the Device Group you created in Step 7, and the template stack you created in
Step 1.
5. Disable License Management Only to ensure traffic is secured.
STEP 10 | Commit your changes.
Prepare a VM-Series Firewall Bootstrap Package for Auto Scaling
During bootstrap, the initial request from the firewall provides the host IP address and serial
number, and the VM auth key so Panorama can validate the VM auth key and add the firewall
as a managed device. Panorama can then assign the firewall to the appropriate device group and
template so that you can centrally configure and administer the firewall using Panorama.
In this case, you must generate a VM auth key on Panorama and include the key in the init-cfg.txt
file that you use for bootstrapping. The VM auth key allows Panorama to authenticate the newly
bootstrapped VM-Series firewall. The bootstrap package must include.
• In the /config directory, an init-cfg.txt file that includes the Panorama IP address
• In the /license directory, the VM authentication key in a file named authcodes.
```
The lifetime of the key can vary between 1 hour and 8,760 hours (1 year). After the specified
```
time, the key expires and Panorama won't register VM-Series firewalls without a valid auth-key
in this connection request.
STEP 1 | Set up a Google storage bucket with the folders required to Bootstrap the VM-Series
Firewall on Google Cloud Platform. You can use an existing bootstrap package or create a
new bootstrap package for these folders.
STEP 2 | Edit the values in the sample init-cfg.txt file to customize the file for your environment.
The firewall templates include a sample init-cfg.txt file.
Parameter Value Comment
type dhcp-client
VM-Series Public Cloud Deployments 601 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on Google Cloud Platform
Parameter Value Comment
hostname <pa-vm> Optional name you assigned
when you prepared the host
project. Only required if a
specific host is necessary, and
dhcp-send-hostname is no.
vm-auth-key <vmauthkey> A key that Panorama must
validate before adding a
firewall as a managed device.
See Generate the VM Auth
Key on Panorama.
panorama-server <panorama-ip> The IP address of the
Panorama management
device you configured in
Configure the Panorama
Plugin for GCP to Secure an
Auto Scaling Deployment
tplname <template-stack-name> The template stack you
created in Configure the
Panorama Plugin for GCP
to Secure an Auto Scaling
Deployment.
dgname <dg-name> The name of the Device
Group you created in the
Panorama plugin for GCP.
dns-primary Your primary DNS server.
dns-secondary Your secondary DNS server.
dhcp-send-hostname yes Leave as is.
dhcp-send-client-id yes Leave as is.
dhcp-accept-server-
hostname
yes Leave as is.
dhcp-accept-server-domain yes Leave as is.
STEP 3 | Upload your edited init-cfg.txt file to the /config folder in your bootstrap package.
```
STEP 4 | If you are using BYOL, create a text file named authcodes (no extension), add your auth
```
code, and upload the file to the /license folder.
VM-Series Public Cloud Deployments 602 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on Google Cloud Platform
Deploy GCP Autoscaling Templates
Where Can I Use This? What Do I Need?
```
• Google Cloud Platform (GCP) VM-Series License (PAYG or BYOL)
```
VM-Series plugin
Panorama
Panorama plugin for GCP
About the Auto Scaling Templates
Download the Palo Alto Networks auto scaling templates from https://github.com/
PaloAltoNetworks/GCP-AutoScaling. The zip file contains separate zips for firewall and
application templates. Each zip is a template directory containing several files, but you only need
to edit the YAML files.
Firewall Templates
The firewall directory files create VM-Series firewalls and other deployment resources. They
create new networks and the familiar subnetworks for the VM-Series firewall: management,
untrust, and trust. They also deploy a Cloud Pub/Sub messaging service to relay information from
GCP to the Panorama plugin for GCP. With this infrastructure in place, the plugin can leverage
Dynamic Address Groups to apply security policy on inbound traffic routed to services running
on GCP, and use auto scale metrics to deploy VM-Series firewalls to meet increased demand for
application workload resources or to eliminate firewalls that are no longer needed.
To configure your load balancer, edit the .yaml file for an external application load balancer
```
(ALB) or network load balancer (NLB).
```
```
• ALB (HTTP External Load Balancer)
```
To customize an ALB, edit vm-series-fw-alb.yaml.
HTTP external load balancer is a proxy-based load balancer that performs SNAT and DNAT on
the inbound traffic from the internet. The HTTP load balancer is designed to support only the
80 and 8080 TCP ports.
To support multiple applications using HTTP load balancer in load balancer sandwich
architecture, we can use the GCP HTTP load balancer urlMap and namedPort to map different
URLs to different ports in the load balancer. In turn, the VM-Series firewall can translate the
ports to different applications, each represented by one internal load balancer per application.
```
• NLB (TCP Load Balancer)
```
To customize an NLB, edit vm-series-fw-nlb.yaml.
TCP load balancer is a nonproxy based load balancer, which means it does not perform NATing
on inbound traffic from the internet.
The TCP load balancer in GCP allows adding multiple frontend IP addresses with an arbitrary
port, making it possible to support multiple applications.
Another advantage of TCP load balancer is that the original client IP address is preserved,
which is desirable for some applications.
VM-Series Public Cloud Deployments 603 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on Google Cloud Platform
Application Template
The application directory provides a sample application. You configure and deploy an internal
```
load balancer (ILB) to enable your application servers to subscribe to the Pub/Sub service and
```
communicate with your VM-Series firewalls and the GCP plugin on Panorama.
To customize the application template, edit apps.yaml as described in Deploy the Firewall
Template and Application Template.
Deploy the Firewall Template
Edit the Firewall Templates from the host project.
All VM-Series firewall interfaces must be assigned an IPv4 address when deployed in a
public cloud environment. IPv6 addresses are not supported.
STEP 1 | Edit the vm-series-fw-nlb.yaml or vm-series-fw-alb.yaml environment variables
to reflect your cloud environment.
The sample in this workflow is for the NLB. See vm-series-fw-nlb.yaml and vm-series-fw-
alb.yaml for further explanation of the template parameters.
```
properties:
```
```
region: us-east1
```
```
zones:
```
-us-east1-b
# Do not modify the lb-type field.
lb-type: nlb
cloud-nat: yes
forwarding-rule-port: 80
# Only one app is allowed
urlPath-namedPort-maps:
- appName: app1
# ssh key PUBLIC:
VM-Series Public Cloud Deployments 604 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on Google Cloud Platform
- optional
The autoscaling firewall template requires you to enter the value in single quotes and prepend
the key with admin: followed by a space. This is the same convention used for the Google
Marketplace template, as detailed in SSH Key Pair. For example:
bootstrap-bucket: bootstrap-autoscale
```
image: vmseries-byol-814
```
machine-type: n1-standard-4
For the service-account, supply the email address for the host project service account you
created previously.
service-account: sa-pan@gcp-autoscale-
kk.iam.gserviceaccount.com
The fw-instance-tag value will be the managed instance group name in the deployment.
fw-instance-tag: vm-series-fw
Choose one metric for auto scaling. Possible values are: panSessionActive,
panSessionUtilization, DataPlaneCPUUtilizationPct, DataPlanePacketBufferUtilization, or
panSessionUtilization.
```
metric: custom.googleapis.com/VMSeries/panSessionActive
```
max-size: 2
min-size: 1
target-type: GAUGE
util-target: 100
# Greenfield deployment
mgmt-network-cidr: 172.22.2.0/24
untrust-network-cidr: 172.22.1.0/24
trust-network-cidr: 172.22.3.0/24
mgmt-network-access-source-range:
- 199.167.54.229/32
- 199.167.52.5/32
mgmt-network-access-ports:
VM-Series Public Cloud Deployments 605 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on Google Cloud Platform
- 22
- 443
STEP 2 | Deploy the firewall template.
gcloud deployment-manager deployments create <your-template>
--config apps.yaml
--automatic-rollback-on-error
Take note of the outputs the CLI prints after the deployment—the subnet names, the
deployment name, and the Panorama Pub/Sub topic name. You need these values to configure
the Shared VPC and for the application template deployment.
The firewall deployment name must be configured in the Panorama plugin for GCP auto scaling
definition.
Prepare a Service Project
Create a separate service project, or choose an existing project, for your application.
To learn more about host and service projects in a shared VPC, see the Shared VPC Overview,
and review the Administrators and IAM roles. A host project administrator must have the proper
role to set up the Shared VPC and make the application project a service project for the host
project. See the instructions in Provisioning Shared VPC.
STEP 1 | Enable the service project APIs from the GCP console or the CLI.
The required APIs are:
Cloud Deployment Manager API
Cloud Pub/Sub API
Compute Engine API
Enable APIs from the GCP console.
1. Select the service project, and from the Navigation menu, select APIs & Services.
2. Search for and view each required API.
3. ENABLE any APIs that don't display the “API enabled” status.
Enable APIs from the CLI.
1. In the CLI, view your configuration to ensure that you are in the correct project.
gcloud config list
If not, set the project as follows:
gcloud config set project <project-name>
2. Issue the following commands to enable the required APIs.
gcloud services enable deploymentmanager.googleapis.com
VM-Series Public Cloud Deployments 606 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on Google Cloud Platform
gcloud services enable pubsub.googleapis.com
gcloud services enable compute.googleapis.com
3. Confirm that the required APIs are enabled.
gcloud services list --enabled
STEP 2 | Make the application project a service project for the host project.
Add the service account from Service/application project administrator as a member in host
project with following roles:
• Compute Network User
• Pub/Sub Admin
STEP 3 | Choose a VPC configuration.
• If the Service project will share the networks in the host project, continue to Configure the
Shared VPC.
• If the Service project has its own VPC network for the application deployment, continue to
Configure a Peered VPC.
Configure the Shared VPC
After the firewall template is deployed in the host project, configure the service project that
supports your applications. An administrator with shared VPC credentials performs these tasks
from the host project. To understand more about the host project and service projects in the
context of shared VPC, see the Shared VPC Overview.
STEP 1 | Create a shared VPC using the Trust VPC created when you deployed the firewall template.
```
Set up a shared VPC for the host (firewall) project:
```
gcloud compute shared-vpc enable HOST_PROJECT_ID
STEP 2 | Attach the service/application project to the host project.
gcloud compute shared-vpc associated-projects add
[SERVICE_PROJECT_ID]--host-project [HOST_PROJECT_ID]
Additional options are available to share only specific subnets, rather than all subnets in the
host project.
STEP 3 | If you want to use the sample application template to deploy an application, continue to
Deploy the Application Template.
If you have already deployed an application and you want to secure it in your auto scaling
deployment, go to Manually Onboard an Application to an Existing Auto Scaling Deployment.
If you have deployed a service in a GKE cluster, continue to Onboard a GKE Cluster in a
Shared VPC.
VM-Series Public Cloud Deployments 607 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on Google Cloud Platform
Configure a Peered VPC
A VPC network peering connection must be made between two VPCs. If the VPCs are in two
different projects, a connection must be created in both projects.
STEP 1 | In the host project, peer the Trust VPC network of the firewall deployment with the
Application VPC.
gcloud beta compute networks peerings create [PEERING-NAME] \
--network=[MY-LOCAL-NETWORK] \
--peer-project [SERVICE-PROJECT-ID] \
--peer-network [PEER-NETWORK-NAME] \
[--import-custom-routes] \
[--export-custom-routes]
STEP 2 | In the service project, peer the Trust VPC network of the application deployment with the
Trust VPC network of the firewall deployment.
gcloud beta compute networks peerings create [PEERING-NAME] \
--network=[MY-LOCAL-NETWORK] \
--peer-project [HOST-PROJECT-ID] \
--peer-network [PEER-NETWORK-NAME] \
[--import-custom-routes] \
[--export-custom-routes]
STEP 3 | If you want to use the sample application template to deploy an application, continue to
Deploy the Application Template.
If you have already deployed an application and you want to secure it in your auto scaling
deployment, go to Manually Onboard an Application to an Existing Auto Scaling Deployment.
If you have deployed a service in a GKE cluster, continue to Onboard a GKE Cluster in a
Peered VPC.
Deploy the Application Template
The Service project administrator deploys the Application Template from the service project.
```
STEP 1 | Create a separate application project (service project) to deploy the application (see Prepare
```
```
a Service Project).
```
STEP 2 | Prepare the apps.yaml file as outlined in apps.yaml.
STEP 3 | Deploy a new application with the application template and define a label for the named
port.
gcloud deployment-manager deployments create <your-template>
--config apps.yaml
--automatic-rollback-on-error
Continue to View the Onboarded Application in the Panorama Plugin for GCP.
VM-Series Public Cloud Deployments 608 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on Google Cloud Platform
Onboard a New Application
When you use the Application Template to deploy an application, it takes care of the connection
to the host project. You can secure applications you did not deploy with the application template,
provided they are deployed in a service project with the capabilities described in Prepare a Service
Project.
Manually Onboard an Application to an Existing Auto Scaling Deployment
To secure an application you have deployed using an external load balancer and an autoscaled
VM-Series firewall deployment, follow these steps. For each application you onboard, you must
supply the application name, the named ports, and the path.
STEP 1 | Prepare to add a new named port and URL path to the HTTP external load balancer created
when you deployed the firewall template.
STEP 2 | Update all instance groups named-ports with an additional service name and port values. The
following sample onboards the applications app2 and app3.
gcloud compute instance-groups set-named-ports
fw-template2-fw-igm-us-east1-b
--zone us-east1-b
--named-ports=app1:80,app2:81,app3:82
gcloud compute instance-groups set-named-ports
fw-template2-fw-igm-us-east1-c
--zone us-east1-c
--named-ports=app1:80,app2:81,app3:82
STEP 3 | Create a new http-health-check.
gcloud compute backend-services create fw-template2-backend-app3
--protocol="HTTP"
--port-name=app3
--http-health-checks=fw-template2-healthcheck-app3
--load-balancing-scheme="EXTERNAL"
--global
STEP 4 | Create a new backend service with the port-name created earlier on the HTTP external load
balancer.
gcloud compute backend-services create fw-template2-backend-app3
--protocol="HTTP" --port-name=app3
--http-health-checks=fw-template2-healthcheck-app3 --load-
balancing-scheme="EXTERNAL"
--global
Check to see if the new backend service is visible.
gcloud compute backend-services list
VM-Series Public Cloud Deployments 609 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on Google Cloud Platform
STEP 5 | Edit url-maps and add a new path rule. For example:
- paths:
- /app3
- /app3/*service:
```
https://www.googleapis.com/compute/v1/projects/<project-name>/
```
global/backendServices/fw-template2-backend-app3
gcloud compute url-maps edit fw-template2-ext-loadbalancer
STEP 6 | To secure this application with the VM-Series firewall, manually trigger the pub/sub message
through the gcloud CLI. This sends a message to the topic created in the firewall template.
gcloud pubsub topics publish
projects/topics/hj-asg-891ca3-gcp-pavmqa-panorama-apps-
deployment
--attribute ilb-ip=172.22.9.34,
app-deployment-name=hj-asg-891ca3-app1,
ilb-port=80,
named-port=81,
network-cidr=172.22.9.0/24,
fw-deployment-name=hj-asg-891ca3,
host-project=gcp-pavmqa,
```
type=ADD-APP
```
--message "ADD-APP"
STEP 7 | View the Onboarded Application in the Panorama Plugin for GCP.
```
STEP 8 | (Optional) To update application attributes, such as ilb-ip, ilb-port, or named-port, issue the
```
pubsub command:
gcloud pubsub topics publish projects/gcp-pavmqa/topics/hj-
asg-891ca3-gcp-pavmqa-panorama-apps-deployment
--attribute ilb-ip=172.22.9.34,
app-deployment-name=hj-asg-891ca3-app1,
ilb-port=80,
named-port=81,
network-cidr=172.22.9.0/24,
fw-deployment-name=hj-asg-891ca3,
host-project=gcp-pavmqa,
```
type=UPDATE-APP
```
--message "UPDATE-APP"
```
STEP 9 | (Optional) To stop securing the application, issue the following command:
```
gcloud pubsub topics publish projects/gcp-pavmqa/topics/hj-
asg-891ca3-gcp-pavmqa-panorama-apps-deployment
--attribute ilb-ip=172.22.3.20,app-deployment-name=fw-templ-3-
app-1,
ilb-port=80,
VM-Series Public Cloud Deployments 610 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on Google Cloud Platform
named-port=80,
fw-deployment-name=hj-asg-891ca3,
```
type=DEL-APP
```
--message "DEL-APP"
Onboard a GKE Cluster
To onboard a private GKE cluster, the GCP plugin for Panorama requires the following
information.
• In GCP, expose the ELB frontend for the cluster to the GKE service so the VM-Series firewall
can get the named port information for the service.
• The cluster API server address.
• The service account credential for the service in which the cluster is deployed, in JSON format.
The GKE cluster name must not exceed 24 characters. This ensures that if you deploy
auto scaling in a peered VPC configuration the static route name does not exceed 31
characters.
Onboard a GKE Cluster in a Shared VPC
To onboard the GKE cluster, you must share the Host project Trust network VPC with the Service
project. See Configure the Shared VPC.
For security reasons, only private clusters should be used in an auto scaling deployment.
See Creating a private cluster.
STEP 1 | Set the Host project ID.
gcloud config set project [HOST_PROJECT_ID]
```
STEP 2 | (Optional) Set a compute zone or region for clusters.
```
If the cluster is zonal, enter the following:
gcloud config set compute/zone [COMPUTE_ZONE]
If the cluster is regional, enter the following:
gcloud config set compute/region [COMPUTE_REGION]
STEP 3 | In the Host project, update secondary ranges in the Trust VPC subnet.
gcloud compute networks subnets update [TRUST_SUBNETWORK_NAME]
--add-secondary-ranges
[PODS_IP_RANGE_NAME] = [POD_RANGE_CIDR],
VM-Series Public Cloud Deployments 611 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on Google Cloud Platform
[SERVICE_IP_RANGE_NAME]=[SERVICE_RANGE_CIDR]
Pods and service IP ranges must be within: 10.0.0.0/8, 172.16.0.0/12 or
192.168.0.0/16, and cannot collide with existing IP ranges in the subnetwork.
STEP 4 | In the Service project, create a private cluster in the shared VPC.
1. Set the Service project ID.
gcloud config set project [SERVicE_PROJECT_ID]
2. Create a private cluster in the shared VPC.
gcloud container clusters create [CLUSTER_NAME]
--project [SERVICE_PROJECT_ID]
--zone=[ZONE_NAME]
--enable-ip-alias
--enable-private-nodes
--network projects/[HOST_PROJECT_ID]/global/networks/
[NETWORK_NAME]
--subnetwork projects/[HOST_PROJECT_ID]/regions/
[REGION_NAME]
/subnetworks/[TRUST_SUBNETWORK_NAME]
--cluster-secondary-range-name=[PODS_IP_RANGE_NAME]
--services-secondary-range-name=[SERVICE_IP_RANGE_NAME]
--master-ipv4-cidr=[MASTER_IPV4_CIDR]
--enable-master-authorized-networks
--master-authorized-networks=[PANORAMA_MANAGEMENT_IP/32],
[MY_MANAGEMENT_IP/32]
STEP 5 | Check your current cluster context:
kubectl config current-context
STEP 6 | Check all cluster contexts.
kubectl config get-context
STEP 7 | Change to another cluster.
kubectl config use-context [CONTEXT_NAME]
If you created your cluster in the GCP console, generate a kubeconfig entry:
gcloud container clusters get-credentials [CLUSTER_NAME]
STEP 8 | Create a cluster role in a .yaml file—for example, gke_cluster_role.yaml.
```
apiVersion: rbac.authorization.k8s.io/v1beta1
```
VM-Series Public Cloud Deployments 612 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on Google Cloud Platform
```
kind: ClusterRole
```
```
metadata:
```
```
name: gke-plugin-role
```
```
rules:
```
- apiGroups:
- ""
```
resources:
```
- services
```
verbs:
```
- list
STEP 9 | Apply the cluster role.
kubectl apply -f gke_cluster_role.yaml
STEP 10 | Create a cluster role binding in a .yaml file—for example,
gke_cluster_role_binding.yaml.
```
kind: ClusterRoleBinding
```
```
apiVersion: rbac.authorization.k8s.io/v1beta1
```
```
metadata:
```
```
name: gke-plugin-role-binding
```
```
subjects:
```
- kind: ServiceAccount
```
name: [SERVICEACCOUNT_NAME]
```
```
namespace: default
```
```
roleRef:
```
```
kind: ClusterRole
```
```
name: gke-plugin-role
```
```
apiGroup: rbac.authorization.k8s.io
```
STEP 11 | Apply the cluster role binding.
kubectl apply -f gke_cluster_role_binding.yaml
STEP 12 | Create a service account.
kubectl create serviceaccount [SERVICEACCOUNT_NAME]
STEP 13 | Export the service account secret token in JSON format.
```
MY_TOKEN=`kubectl get serviceaccounts [SERVICEACCOUNT_NAME]
```
```
-o jsonpath='{.secrets[0].name}'`
```
kubectl get secret $MY_TOKEN -o json > [FILE_NAME].json
VM-Series Public Cloud Deployments 613 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on Google Cloud Platform
STEP 14 | Get the API server address.
kubectl config view --minify | grep server | cut -f 2- -d ":" | tr
-d " "
STEP 15 | In the Panorama plugin for GCP, add the service account information.
Select Panorama > Google Cloud Platform > Setup.
Name the credential, enter a description, and enter the API server address from step 14, and
for GKE Service Account Credential, upload the JSON file you exported in step 13.
After you add a service account credential, you can validate the credential from your
```
Panorama command line (you cannot validate from the web interface):
```
request plugins gcp validate-service-account gke_service_account
<svc-acct-credential-name>
STEP 16 | Set up auto scaling on the Panorama plugin for GCP.
1. In the Panorama context, expand Google Cloud Platform, select AutoScaling, and click
Add.
2. Supply the Firewall Deployment Name and an optional description for the deployment.
3. For the GCP Service Account Credential, supply the GCP service account name created
in Auto Scaling Components for Google Cloud Platform, step 4.
4. Choose the Device Group and the template stack you created in when you configured
the Panorama plugin for GCP.
5. Disable License Management Only to ensure traffic is secured.
6. Enter the exact GKE Cluster Name.
7. (Optional) Enter a Description of the GKE cluster.
8. Enter the Network CIDR for the GKE cluster.
9. Select the GKE Service Account corresponding to the GKE cluster.
STEP 17 | Commit your changes.
```
STEP 18 | (Optional) Create and deploy a service template according to Using the Sample GKE Service
```
Templates, or deploy a GKE service in the GCP console.
Onboard a GKE Cluster in a Peered VPC
To onboard the GKE cluster, you must create and peer the Service VPC with the firewall Trust
network in the Host project, as described in Configure a Peered VPC.
For security reasons, only private clusters should be used in an auto scaling deployment.
See Creating a private cluster.
STEP 1 | Set the project ID.
gcloud config set project [PROJECT_ID]
VM-Series Public Cloud Deployments 614 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on Google Cloud Platform
STEP 2 | Set a compute zone or region for clusters.
If the cluster is zonal, enter the following:
gcloud config set compute/zone [COMPUTE_ZONE]
If the cluster is regional, enter the following:
gcloud config set compute/region [COMPUTE_REGION]
STEP 3 | Update the service project VPC network with the secondary IP ranges for the pods and
services.
gcloud compute networks subnets update [GKE_PEERED_VPC_SUBNETWORK]
--region=[REGION]
--add-secondary-ranges PODS_IP_RANGE_NAME=[ip cidr],
```
SERVICE_IP_RANGE_NAME=[ip cidr]
```
STEP 4 | Enable cloud NAT.
Cloud NAT is required to deploy a private cluster.
gcloud compute routers create [ROUTER_NAME]
--network [NETWORK_NAME]
--region [REGION_NAME]
gcloud compute routers nats create [NAT_CONFIG_NAME]
--router-region [REGION_NAME]
--router [ROUTER_NAME]
--nat-all-subnet-ip-ranges
--auto-allocate-nat-external-ip
STEP 5 | Create a new private cluster in the Service VPC.
gcloud container clusters create [CLUSTER_NAME]
--project [SERVICE_PROJECT_ID]
--zone=[ZONE_NAME]
--enable-ip-alias
--network [NETWORK_NAME]
--subnetwork [SUBNETWORK_NAME]
--enable-private-nodes
--cluster-secondary-range-name=[PODS_IP_RANGE_NAME]
--services-secondary-range-name=[SERVICE_IP_RANGE_NAME]
--master-ipv4-cidr=[MASTER_IPV4_CIDR]
--enable-master-authorized-networks
--master-authorized-networks=[PANORAMA_MANAGEMENT_IP/32],
[MY_MANAGEMENT_IP/32]
VM-Series Public Cloud Deployments 615 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on Google Cloud Platform
STEP 6 | Check your current cluster context:
kubectl config current-context
STEP 7 | Check all cluster contexts.
kubectl config get-context
STEP 8 | Change to another cluster.
kubectl config use-context [CONTEXT_NAME]
If you created your cluster in the GCP console, generate a kubeconfig entry:
gcloud container clusters get-credentials [CLUSTER_NAME]
STEP 9 | Create a cluster role in a .yaml file—for example, gke_cluster_role.yaml.
```
apiVersion: rbac.authorization.k8s.io/v1beta1
```
```
kind: ClusterRole
```
```
metadata:
```
```
name: gke-plugin-role
```
```
rules:
```
- apiGroups:
- ""
```
resources:
```
- services
```
verbs:
```
- list
STEP 10 | Apply the cluster role.
kubectl apply -f gke_cluster_role.yaml
STEP 11 | Create a cluster role binding in a .yaml file—for example,
gke_cluster_role_binding.yaml.
```
kind: ClusterRoleBinding
```
```
apiVersion: rbac.authorization.k8s.io/v1beta1
```
```
metadata:
```
```
name: gke-plugin-role-binding
```
```
subjects:
```
- kind: ServiceAccount
```
name: [SERVICEACCOUNT_NAME]
```
```
namespace: default
```
```
roleRef:
```
```
kind: ClusterRole
```
```
name: gke-plugin-role
```
VM-Series Public Cloud Deployments 616 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on Google Cloud Platform
```
apiGroup: rbac.authorization.k8s.io
```
STEP 12 | Apply the cluster role binding.
kubectl apply -f gke_cluster_role_binding.yaml
STEP 13 | Create a service account.
kubectl create serviceaccount [SERVICEACCOUNT_NAME]
STEP 14 | Export the service account secret token in JSON format.
```
MY_TOKEN=`kubectl get serviceaccounts [SERVICEACCOUNT_NAME]
```
```
-o jsonpath='{.secrets[0].name}'`
```
kubectl get secret $MY_TOKEN -o json >[FILE_NAME].json
STEP 15 | Get the API server address.
kubectl config view --minify | grep server | cut -f 2- -d ":" | tr
-d " "
STEP 16 | In the Panorama plugin for GCP, add the service account information.
Select Panorama > Google Cloud Platform > Setup.
Name the credential and enter the API server address from step 15, and upload the JSON file
you exported in step 14.
After you add a service account credential, you can validate the credential from your
Panorama command line:
request plugins gcp validate-service-account <svc-acct-credential-
name>
VM-Series Public Cloud Deployments 617 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on Google Cloud Platform
STEP 17 | Set up auto scaling on the Panorama plugin for GCP.
1. In the Panorama context, expand Google Cloud Platform, select AutoScaling, and click
Add.
2. Supply the Firewall Deployment Name and an optional description for the deployment.
3. For the GCP Service Account Credential, supply the GCP service account name from
step 16.
4. Choose the Device Group and the Template Stack you created in when you configured
the Panorama plugin for GCP.
5. Disable License Management Only to ensure traffic is secured.
6. Enter the exact GKE Cluster Name.
7. (Optional) Enter a Description of the GKE cluster.
8. Enter the Network CIDR for the GKE cluster.
9. Select the GKE Service Account corresponding to the GKE cluster.
```
STEP 18 | (Optional) In your service project, create and deploy a GKE template according to Using the
```
Sample GKE Service Templates, or deploy a GKE service use the GCP console. Onboard a
GKE Cluster
View the Onboarded Application in the Panorama Plugin for GCP
Select Panorama > Google Cloud Platform > Autoscaling to view your onboarded application. The
Details column is only visible if you have an onboarded application.
Each link in the Details column triggers an action.
VM-Series Public Cloud Deployments 618 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on Google Cloud Platform
• Show Status— View the details for applications onboarded to a GCP VM-Series firewall
deployment.
The following fields display information obtained from the selected deployment. You specified
these values in the pub/sub message or through GKE cluster service polling.
• Application/GKE Service Name—An application deployment name, or the name of a GKE
service.
• Host Project—The name of the host project.
• Cluster/Namespace—A GKE cluster name followed by the namespace, for example,
mycluster/namespace9.
• Named Port—The port assigned to the named port for the service.
• ILB IP—The ILB IP address.
• ILB Port—The ILB port number.
For autoscaling an application, this property is ilb-port in apps.yaml.
For securing a GKE cluster, this value is the port number of the GKE cluster, as specified in
the .yaml file you used to deploy the service in your cluster.
• Configuration Programmed— True if a NAT rule exists, False if not.
• Protected— True when an application is onboarded successfully, or False if onboarding
failed. If False, see the Not Protected Reason column for an explanation.
• Not Protected Reason— If Protected is False, it displays the reason the application is not
protected. Some common reasons are:
• Configuration Programmed—True if a NAT rule exists, False if not.
• Protected—True when an application is onboarded successfully, or False if onboarding
failed. If False, see the Not Protected Reason column for an explanation.
• Not Protected Reason—If Protected is False, it displays the reason the application is not
protected. Some common reasons are:
• You deployed a UDP service in the GKE cluster.
• You specified a named port that is already in use. Only one application can listen on a
specific named port.
• You chose the License management only option, so we do not program the
configuration.
• No matching label found for GKE services.
• Delicense Inactive VMs—Answer Yes to trigger the delicensing function for inactive VMs.
VM-Series Public Cloud Deployments 619 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on Google Cloud Platform
• Trigger GKE services Sync—Answer Yes to poll the services running in the clusters, and
program the NAT, address, and service objects, and static routes if necessary. By default,
Panorama automatically polls 10 minutes after the completion of the previous poll.
View the Deployment Status from the CLI
You can use the Panorama CLI to manage deployed applications. The command-line actions
parallel those described in View the Onboarded Application in the Panorama Plugin for GCP. In
the following commands, the autoscaling_name is the firewall Deployment Name you entered
in the auto scaling configuration.
```
• List the onboarded (protected) applications.
```
show plugins gcp show-protected-apps autoscaling_name <fw-
deployment-name>
• Trigger the delicensing function for firewalls in the specified deployment.
request plugins gcp force-delicensing autoscaling_name <fw-
deployment-name>
• For a GKE deployment, force the plugin to read the pub-sub messages, and sync NAT rules
that are programmed based on the pub-sub messages.
request plugins gcp gke-service-discovery autoscaling_name <fw-
deployment-name>
Parameters in the Auto Scaling Templates for GCP
You can download the template .zip file from https://github.com/PaloAltoNetworks/GCP-
AutoScaling. The .zip file contains directories to support firewall templates for network load
balancer and application load balancer configurations, and the application template.
The template YAML files have the following general format:
#Copyright and license information
:
:
```
imports: <do not change>
```
:
:
```
resources:
```
-name: vm-series-fw <do not change>
-type:vm-series-fw.py <do not change
-properties:
:
:
```
outputs: <do not change>
```
:
:
In all .yaml files, you customize the resources properties for your deployment. Do not change
anything in the imports or outputs sections.
VM-Series Public Cloud Deployments 620 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on Google Cloud Platform
Firewall Templates
The following sections detail the parameters for the NLB and ALB .yaml files.
vm-series-fw-nlb.yaml
In the vm-series-fw-nlb.yaml template, edit the -properties.
Parameter Sample Value Comment
region us-central1 https://cloud.google.com/
compute/docs/regions-zones
zones
- <list of zones>
zones- us-central1-a If applicable, list multiple
zones as follows:
zones- us-central1-a- us-
central1-b- us-central1-c- us-
central1-f
lb-type nlb Do not change.
cloud-nat yes Do not change.
forwarding-rule-port 80 80 or 8080
urlPath-namedPort-maps-
appname urlPath-namedPort-m
aps
-MyApplication
Enter your application name.
sshkey 'admin:ssh-rsa <PASTE KEY>' Review SSH Key Pair. In
single quotes, type admin:
followed by a space, and
paste in your key. This is the
same convention used for the
Google Marketplace template.
bootstrap-bucket bootstrap-autoscale The name of the GCP bucket
that contains your bootstrap
file.
image vm-series-byol-814 The BYOL image currently
available from the Google
marketplace.
If you are using PAYG or
another license model, the
image might be different.
machine-type n1-standard-4 n1-standard-4 is default for
BYOL.
VM-Series Public Cloud Deployments 621 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on Google Cloud Platform
Parameter Sample Value Comment
If your license permits it,
you can use any machine
type in Minimum System
Requirements for the VM-
Series Firewall on GCP.
service-account The unique service account
name for the host project.
fw-instance-tag vm-series-fw The instance tag you provided
in GCP.
metric custom.googleapis.com/
VMSeries/panSessionActive
The custom API path for VM-
Series, and your chosen auto
scaling metric.
Supply only one of the
following metrics.
panSessionActive
panSessionUtilizatio
n
DataPlaneCPUUtilizat
ionPct
DataPlanePacketBuffe
rUtilization
panSessionUtilizatio
n
max-size 2
min-size 1
target-type GAUGE Currently GAUGE is the only
valid type.
util-target 100
To deploy the VM-Series firewall you need a dedicated network and subnetwork for the
firewall’s managment, untrust, and trust interfaces. Fill out the information for either a new
```
deployment (configure the template to create new networks) or existing deployment (use
```
```
existing networks). Be sure to remove or comment out the network deployment parameters
```
you are not using.
New Deployment: Enter values to create management, untrust, and trust networks and
subnetworks for the firewall.
mgmt-network-cidr 172.22.2.0/24
VM-Series Public Cloud Deployments 622 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on Google Cloud Platform
Parameter Sample Value Comment
untrust-network-cidr 172.22.1.0/24
trust-network-cidr 172.22.3.0/24
mgmt-network-access-
source-range- <permitted-ip-
range>
mgmt-network-access-source-range
- <permitted-ip-range-1>
- <permitted-ip-range-2>
mgmt-network-access-ports-
<port-number> mgmt-network-access
-ports
- 22
- 443
Existing Deployment: Enter the name of each existing network or subnetwork
mgmt-network my-mgmt-network
mgmt-subnet my-mgmt-subnet
trust-network my-trust-network
trust-subnet my-trust-subnet
untrust-network my-untrust-network
untrust-subnet my-untrust-subnet
vm-series-fw-alb.yaml
In the vm-series-fw-alb.yaml template, edit the -properties.
Parameter Sample Value Comment
region us-central1 https://cloud.google.com/
compute/docs/regions-zones
zones
- <list of zones>
zones- us-central1-a If applicable, list multiple zones
as follows:
zones- us-central1-a- us-
central1-b- us-central1-c- us-
central1-f
lb-type alb Do not change.
cloud-nat yes Do not change.
VM-Series Public Cloud Deployments 623 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on Google Cloud Platform
Parameter Sample Value Comment
forwarding-rule-port 80 80
connection-draining-timeout 300 The timeout value is in
seconds.
urlPath-namedPort-m
```
aps:
```
- appname:
```
namedPort:
```
```
urlMapPaths:
```
- '/app1'
- '/app1/*'
urlPath-namedPort-m
```
aps:
```
- appName: app1
```
namedPort: 80
```
```
urlMapPaths:
```
- '/app1'
- '/app1/*'
- appName: app2
```
namedPort: 81
```
```
urlMapPaths:
```
- '/app2'
- '/app2/*'
List your apps and the
corresponding named port
sshkey 'admin:ssh-rsa <PASTE KEY>' Review SSH Key Pair. In
single quotes, type admin:
followed by a space, and paste
in your key. This is the same
convention used for the Google
Marketplace template.
bootstrap-bucket bootstrap-bucket-name The name of the GCP bucket
that contains your bootstrap
file.
image vm-series-byol-814 The BYOL image is currently
available from the Google
marketplace.
If you are using PAYG or
another license model, the
image might be different
machine-type n1-standard-4 n1-standard-4 is default for
BYOL.
If your license permits it,
you can use any machine
type in Minimum System
Requirements for the VM-
Series Firewall on GCP.
service-account The unique service account name for the service project.
VM-Series Public Cloud Deployments 624 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on Google Cloud Platform
Parameter Sample Value Comment
fw-instance-tag vm-series-fw The instance tag you provided
in GCP.
metric custom.googleapis.com/
VMSeries/panSessionActive
The custom API path for VM-
Series, and your chosen auto
scaling metric.
Supply only one of the
following metrics.
panSessionActive
panSessionUtilization
DataPlaneCPUUtilizati
onPct
DataPlanePacketBuffer
Utilization
panSessionUtilization
max-size 2
min-size 1
target-type GAUGE Currently GAUGE is the only
valid type.
util-target 100 Enter the goal utilization target
value for the auto scaling.
New Deployment: Enter values to create management, untrust, and trust networks and
subnetworks for the firewall.
mgmt-network-cidr 192.168.12.0/24
untrust-network-cidr 192.168.11.0/24
trust-network-cidr 192.168.11.0/24
mgmt-network-access-
source-range- <permitted-
ip-range>
mgmt-network-access-source-range- <permitted-
ip-range-1>- <permitted-ip-range-2>
mgmt-network-access-
ports- <port-number>
mgmt-network-access-
ports- 22- 443
Existing Deployment: Enter the name of each existing network or subnetwork
mgmt-network existing-vpc-mgmt
VM-Series Public Cloud Deployments 625 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on Google Cloud Platform
Parameter Sample Value Comment
mgmt-subnet existing-subnet-mgmt
trust-network existing-vpc-trust
trust-subnet existing-subnet-trust
untrust-network existing-vpc-untrust
untrust-subnet existing-subnet-untrust
Application Template
apps.yaml
```
The application template creates the connection between the host project (which contains the
```
```
VM-Series firewalls) and the service project, which contains the application or services that the
```
firewall deployment secures.
Parameter Sample Value Comment
host-project your-host-project-name The name of the project
containing the VM-Series
firewall deployment.
fw-deployment-
name
my-vm-series-firewall-name
region us-central1 https://cloud.google.com/
compute/docs/regions-zones
zones
- <list of zones>
zones- us-central1-a If applicable, list multiple
zones as follows:
zones- us-central1-a
-
us-central1-b-
us-central1-c-
us-central1-f
app-machine-type n1-standard-2 The machine type for the VM
running your application or
service. If your license permits
it, you can use any machine
type in Minimum System
Requirements for the VM-
Series Firewall on GCP.
VM-Series Public Cloud Deployments 626 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on Google Cloud Platform
Parameter Sample Value Comment
```
app-instance-tag web-app-vm You applied this tag (label) in
```
GCP.
sshkey 'admin:ssh-rsa <PASTE KEY>' Review SSH Key Pair. In
single quotes, type admin:
followed by a space, and
paste in your key. This is the
same convention used for the
Google Marketplace template.
trust-network <project-name>/<vpc-network-
name>
For a shared VPC, the
<project-name> is the host
project name.
For peered VPCs the <project-
name> is the Service project
name.
trust-subnet <project-name>/<subnet-name> For a shared VPC, the
<project-name> is the host
project name.
For peered VPCs the <project-
name> is the Service project
name.
trust-subnet-cidr 10.2.0.0/24 For a greenfield deployment,
the Host project Trust subnet
```
CIDR (the trust-network-
```
cidr parameter in the firewall
```
template).
```
For a brownfield deployment,
the CIDR for the Trust
network.
vm-series-fw-
template-topic
<pubsub-topic> Enter the topic name created
by the firewall deployment.
The application template
posts a message to the topic
to program the firewall
configuration to forward
traffic.
ilb-port 80 Enter the port number for
your application’s internal-
load-balancer-port. output.
VM-Series Public Cloud Deployments 627 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on Google Cloud Platform
Parameter Sample Value Comment
urlPath-namedPort 83 Enter the port number for the
urlPath-namedPort output.
Sample GKE Service Templates
These sample templates demonstrate how to configure a GKE service so it is secured by the VM-
Series firewall. For the basics on creating your own cluster services, see Creating a private cluster.
Using the Sample GKE Service Templates
You can create a service template based on the sample content in the .yaml files that follow.
Typically you create a single .yaml file.
To be secured by the VM-Series firewall, services in the cluster must be labeled "panw-named-
```
port=<named_port>" as shown in web-service.yaml or web-service-v2.yaml.
```
1. Deploy a .yaml file as follows:
kubectl apply -f [FILE_NAME].yaml
2. Configure the VPC deployment.
• In a shared VPC deployment, launch the GKE cluster in the shared VPC as described in
Configure the Shared VPC.
• In a peered VPC deployment, peer the GKE cluster VPC to the host project Trust network.
See Configure a Peered VPC.
After a deployment, you can delete all services deployed in the service template .yaml
file as follows:
kubectl delete -f [FILE_NAME].yaml
gke_cluster_role.yaml
```
apiVersion: rbac.authorization.k8s.io/v1beta1
```
```
kind: ClusterRole
```
```
metadata:
```
```
name: gke-plugin-role
```
```
rules:
```
- apiGroups:
- ""
```
resources:
```
- services
```
verbs:
```
- list
gke_cluster_role_binding.yaml
```
kind: ClusterRoleBinding
```
VM-Series Public Cloud Deployments 628 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on Google Cloud Platform
```
apiVersion: rbac.authorization.k8s.io/v1beta1
```
```
metadata:
```
```
name: gke-plugin-role-binding
```
```
subjects:
```
- kind: ServiceAccount
```
name: hj-gke-891ca3-cluster1-sa
```
```
namespace: default
```
```
roleRef:
```
```
kind: ClusterRole
```
```
name: gke-plugin-role
```
```
apiGroup: rbac.authorization.k8s.io
```
web-deployment.yaml
```
apiVersion: extensions/v1beta1
```
```
kind: Deployment
```
```
metadata:
```
```
name: web
```
```
namespace: default
```
```
spec:
```
```
selector:
```
```
matchLabels:
```
```
run: web
```
```
template:
```
```
metadata:
```
```
labels:
```
```
run: web
```
```
spec:
```
```
containers:
```
- image: gcr.io/google-samples/hello-app:1.0
```
imagePullPolicy: IfNotPresent
```
```
name: web
```
```
ports:
```
- containerPort: 8080
```
protocol: TCP
```
web-service.yaml
```
apiVersion: v1
```
```
kind: Service
```
```
metadata:
```
```
name: web
```
```
namespace: default
```
```
annotations:
```
cloud.google.com/load-balancer-type: "Internal"
```
labels:
```
panw-named-port-port1: "80"
```
spec:
```
```
ports:
```
# the port that this service should serve on
- name: port1
```
port: 80
```
```
protocol: TCP
```
```
targetPort: 8080
```
VM-Series Public Cloud Deployments 629 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on Google Cloud Platform
```
selector:
```
```
run: web
```
```
type: LoadBalancer
```
web-deployment-v2.yaml
```
apiVersion: extensions/v1beta1
```
```
kind: Deployment
```
```
metadata:
```
```
name: web2
```
```
namespace: default
```
```
spec:
```
```
selector:
```
```
matchLabels:
```
```
run: web2
```
```
template:
```
```
metadata:
```
```
labels:
```
```
run: web2
```
```
spec:
```
```
containers:
```
- image: gcr.io/google-samples/hello-app:2.0
```
imagePullPolicy: IfNotPresent
```
```
name: web2
```
```
ports:
```
- containerPort: 8080
```
protocol: TCP
```
web-service-v2.yaml
```
apiVersion: v1
```
```
kind: Service
```
```
metadata:
```
```
name: web2
```
```
namespace: default
```
```
annotations:
```
cloud.google.com/load-balancer-type: "Internal"
```
labels:
```
panw-named-port-port2: "81"
```
spec:
```
```
ports:
```
# the port that this service should serve on
- name: port2
```
port: 81
```
```
protocol: TCP
```
```
targetPort: 8080
```
```
selector:
```
```
run: web2
```
```
type: LoadBalancer
```
Multiple Ports in a Service
For multiple ports in one service, edit labels and map the target port name and number in the
format panw-named-port-<service-spec-port-name>, as shown in the sample below.
VM-Series Public Cloud Deployments 630 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on Google Cloud Platform
```
apiVersion: v1
```
```
kind: Service
```
```
metadata:
```
```
name: carts
```
```
annotations:
```
cloud.google.com/load-balancer-type: "Internal"
```
labels:
```
panw-named-port-carts-http: "6082"
panw-named-port-carts-https: "6083"
```
namespace: default
```
```
spec:
```
```
type: LoadBalancer
```
```
ports:
```
# the port that this service should serve on
- name: carts-http
```
protocol: TCP
```
```
port: 80
```
```
targetPort: 80
```
- name: carts-https
```
protocol: TCP
```
```
port: 443
```
```
targetPort: 443
```
```
selector:
```
```
name: carts
```
VM-Series Public Cloud Deployments 631 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on Google Cloud Platform
Set up Active/Passive HA on Google Cloud Platform
Where Can I Use This? What Do I Need?
```
• Google Cloud Platform (GCP) VM-Series License (PAYG or BYOL)
```
VM-Series plugin
Panorama
Panorama plugin for GCP
```
You can configure a pair of VM-Series firewalls hosted in Google Cloud Platform (GCP) in an
```
```
active/passive high availability (HA) configuration. For HA on GCP, you must deploy both firewall
```
HA peers within the same Resource Group and you must install the same version of the VM-
Series Plugin on both HA peers.
Deploying an Active/Passive high availability pair of VM-Series firewalls hosted in GCP provides
benefits such as:
• Synchronization across all Palo Alto Networks configuration.
• Stateful synchronization between instances to maintain state on failover.
• Controlled HA failover in approximately 3 seconds.
```
The architecture is very similar to the traditional Load Balancer(LB) architecture recommended for
```
GCP in which the external LB points manages the untrust traffic and an internal LB manages the
trust/egress or east-west traffic.
VM-Series Public Cloud Deployments 632 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on Google Cloud Platform
VM-Series Public Cloud Deployments 633 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on Google Cloud Platform
The VM-Series firewalls are deployed as an active/passive pair and the HA2 interface is dedicated
to the HA2 interface of the VM-Series firewall on NIC 3.
The HA setup on GCP supports connection tracking, which tracks the connection between an
external client server through the external LB to the backend of the firewall. During a firewall
```
failover, the LBs carry over the connections to the secondary firewall (which now becomes active)
```
without any disruptions.
```
The internal LBs (backend pool) are set to active/active, but the standby firewall won't process
```
any traffic. The LBs perform a health-check and if they realize that the active firewall is down and
the standby firewall is now active, they run a health check on the new active firewall. The traffic is
now distributed over the firewall, which has now become active.
```
Note: GCP HA supports interface connection tracking. However, in situations beyond interfaces
```
```
(such as having rules in the Google infrastructure to stop health checks), LB health checks are not
```
tracked as a part of HA transition.
The following are the use cases for deploying HA in GCP:
• IPSec termination of site-to-site VPNs.
```
• Legacy applications that need visibility of the original source client IP (No SNAT solution) for
```
inbound traffic flows.
• Requirements for session failover on failure of the VM-Series firewall.
Deploy the GCP Active/Passive HA
Where Can I Use This? What Do I Need?
```
• Google Cloud Platform (GCP) VM-Series License (PAYG or BYOL)
```
VM-Series plugin
Panorama
Panorama plugin for GCP
Use the following procedures to manage your existing deployment profiles.
Prepare to set up an Active/Passive HA in GCP
STEP 1 | Enable the required APIs, generate an SSH key, and clone the GitHub repository using:
gcloud services enable compute.googleapis.com
ssh-keygen -f ~/.ssh/vmseries-tutorial -t rsa
git clone https://github.com/PaloAltoNetworks/google-cloud-
vmseries-ha-tutorial
cd google-cloud-vmseries-ha-tutorial
STEP 2 | Create a terraform.tfvars file.
cp terraform.tfvars.example terraform.tfvars
VM-Series Public Cloud Deployments 634 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on Google Cloud Platform
STEP 3 | Edit the new terraform.tfvars file and set variables for the following variables:
Variable Description
project_id Set to your Google Cloud deployment
project.
public_key_path Set to match the full path you created
previously.
mgmt_allow_ips Set to a list of IPv4 ranges that can access
the VM-Series management interface.
```
prefix (Optional) If set, this string will be
```
prepended to the created resources.
```
vmseries_image_name (Optional) Defines the VM-Series image to
```
deploy. A full list of images can be found
here.
```
STEP 4 | (Optional) If you are using BYOL image (i.e. vmseries-flex-byol-*), the license can be
```
applied during deployment by adding your VM-Series authcode to bootstrap_files/
authcodes
STEP 5 | Save your terraform.tfvars file.
Deploy the GCP Active/Passive HA
STEP 1 | Initialize and apply the Terraform plan.
terraform init
terraform apply
STEP 2 | Enter yes to start the deployment. After all the resources are created, the Terraform
displays the following message:
Apply complete!
```
Outputs:
```
```
EXTERNAL_LB_IP = "ssh
```
paloalto@1.1.1.1 -i ~/.ssh/vmseries-tutorial"
```
EXTERNAL_LB_URL = "https://1.1.1.1"
```
```
VMSERIES_ACTIVE = "https://2.2.2.2"
```
```
VMSERIES_PASSIVE = "https://3.3.3.3"
```
VM-Series Public Cloud Deployments 635 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on Google Cloud Platform
All the infrastructure should now be deployed and will boot up and configure by itself. Visit the
external_nat_ip by using http://x.x.x.x after a few minutes after the deployment to find the
default webpage from the workload-vm.
Test the GCP Active/Passive HA Deployment
You can now test the deployment by accessing the workload-vm that resides in the trust VPC
network. All the workload-vm traffic is routed directly through the VM-Series HA pair.
STEP 1 | Use the output EXTERNAL_LB_URL to access the web service on the workload-vm
through the VM-Series firewall.
gcloud compute ssh workload-vm
STEP 2 | Use the output EXTERNAL_LB_SSH to open an SSH session through the VM-Series to the
workload-vm.
ssh paloalto@1.1.1.1 -i ~/.ssh/vmseries-tutorial
STEP 3 | Run a preloaded script on the workload VM, to test the failover mechanism across the VM-
Series firewalls.
/network-check.sh
You will observe an output similar to the code block below, where x.x.x.x is the IP address
is EXTERNAL_LB_IP address.
Wed Mar 12 16:40:18 UTC 2023 -- Online -- Source IP = x.x.x.x
Wed Mar 12 16:40:19 UTC 2023 -- Online -- Source IP = x.x.x.x
Wed Mar 12 16:40:20 UTC 2023 -- Online -- Source IP = x.x.x.x
Wed Mar 12 16:40:21 UTC 2023 -- Online -- Source IP = x.x.x.x
Log in to the VM-Series firewalls using the VMSERIES_ACTIVE and VMSERIES_PASSIVE
output values. Notice the HA Status of the firewalls in the bottom-right hand corner of the
management window.
VM-Series Public Cloud Deployments 636 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on Google Cloud Platform
STEP 4 | Perform a user-initiated failover.
• On the Active firewall, click the Device > High Availabilty > Operational
Commands.
• Click Suspend local device for high availability.
• When prompted, click OK to initiate the failover.
VM-Series Public Cloud Deployments 637 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on Google Cloud Platform
• You might notice that the SSH session to the workload-vm is still active. This indicates the
session successfully failed over between the VM-Series firewalls. The script output should
also display the same source IP address.
Wed Mar 12 16:47:18 UTC 2023 -- Online -- Source IP = x.x.x.x
Wed Mar 12 16:47:19 UTC 2023 -- Online -- Source IP = x.x.x.x
Wed Mar 12 16:47:21 UTC 2023 -- Offline
Wed Mar 12 16:47:22 UTC 2023 -- Offline
Wed Mar 12 16:47:23 UTC 2023 -- Online -- Source IP = x.x.x.x
Wed Mar 12 16:47:24 UTC 2023 -- Online -- Source IP = x.x.x.x
Onboarding Internet Applications
You can onboard and secure multiple internet facing applications through the VM-Series firewall.
This is done by mapping forwarding rules on the external load balancer to NAT policies defined on
the VM-Series firewall.
STEP 1 | In Cloud Shell, deploy a virtual machine into a subnet within the trusted VPC network. The
virtual machine in this example runs a sample application for you.
gcloud compute instances create my-app2
\
--network-interface subnet="panw-us-
central1-trust",no-address \
--zone=us-central1-a \
--image-project=panw-gcp-team-testing \
--image=ubuntu-2004-lts-apache-ac \
--machine-type=f1-micro
STEP 2 | Record the INTERNAL_IP address of the new virtual machine.
```
name: my-app2
```
```
ZONE: us-central1-a
```
```
MACHINE_TYPE: f1-micro
```
```
PREEMPTIBLE:
```
```
INTERNAL_IP: 10.0.2.4
```
```
EXTERNAL_IP:
```
```
status: RUNNING
```
STEP 3 | Create a new forwarding rule on the external TCP load balancer.
gcloud compute forwarding-rules create
panw-vmseries-extlb-rule2 \
--load-balancing-scheme=EXTERNAL \
--region=us-central1 \
--ip-protocol=L3_DEFAULT \
--ports=ALL \
--backend-service=panw-vmseries-extlb
VM-Series Public Cloud Deployments 638 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on Google Cloud Platform
STEP 4 | Retrieve and record the address of the new forwarding rule.
gcloud compute forwarding-rules describe
panw-vmseries-extlb-rule2 \
--region=us-central1 \
```
--format='get(IPAddress)'
```
```
(Output)
```
34.172.143.223
STEP 5 | On the active VM-Series, click Policies > NAT > Add and enter a name for the rule.
VM-Series Public Cloud Deployments 639 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on Google Cloud Platform
STEP 6 | Configure the Original Packet as follows:
• Source Zone: untrust
• Destination Zone: untrust
• service: service-http
```
• Destination Address: Set to the forwarding rule's IP address (34.172.143.223).
```
VM-Series Public Cloud Deployments 640 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on Google Cloud Platform
VM-Series Public Cloud Deployments 641 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on Google Cloud Platform
STEP 7 | In the Translated Packet tab, configure the Destination Address Translation as follows:
• Translated Type: Static IP
```
• Translated Address: Set to the INTERNAL_IP of the sample application (10.0.2.4).
```
VM-Series Public Cloud Deployments 642 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on Google Cloud Platform
VM-Series Public Cloud Deployments 643 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on Google Cloud Platform
STEP 8 | Click OK and commit the changes.
STEP 9 | Access the sample application using the forwarding rule's address.
```
http://34.172.143.223/
```
Delete the Resources
You can delete all the resources when you no longer need them.
```
STEP 1 | (Optional) If you onboarded an additional application, delete the forwarding rule and sample
```
application machine.
gcloud compute forwarding-rules delete
panw-vmseries-extlb-rule2 \
--region=us-central1
gcloud compute instances delete my-app2
\
VM-Series Public Cloud Deployments 644 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on Google Cloud Platform
--zone=us-central1-a
STEP 2 | Delete the Terraform using the command:
terraform destroy
STEP 3 | At the prompt to perform the actions, enter yes. After all the resources are deleted,
Terraform displays the following message:
Destroy complete!
VM-Series Public Cloud Deployments 645 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on Google Cloud Platform
VM-Series Public Cloud Deployments 646 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on Oracle
Cloud Infrastructure
Where Can I Use This? What Do I Need?
```
• Oracle Cloud Infrastructure (OCI) instance VM-Series License (BYOL)
```
VM-Series plugin
Panorama
Panorama plugin for OCI
```
Deploy the VM-Series firewall on Oracle Cloud Infrastructure (OCI) cloud. With the VM-Series
```
on OCI, you can protect and segment your workloads, prevent advanced threats, and improve
visibility into your applications as you move to the cloud.
OCI is a public cloud computing service that enables you to run your applications in a highly
available, hosted environment offered by Oracle. You can deploy the VM-Series firewall to secure
your applications and services running in your OCI environment.
The VM-Series firewalls support the following OCI VM shapes. See the Oracle Cloud
Infrastructure documentation for more information about VM shapes.
VM-Series Model Minimum OCI Shape OCPUs Memory
• VM-100
• Software NFGW
Credit-based
VM-Series
VM.Standard2.4 4 60
• VM-300
• Software NFGW
Credit-based
VM-Series
VM.Standard2.4 4 60
• VM-500
• Software NFGW
Credit-based
VM-Series
VM.Standard2.8 8 120
• VM-700
• Software NFGW
Credit-based
VM-Series
VM.Standard2.16 16 240
647
VM-Series Firewall on Oracle Cloud Infrastructure
VM-Series Model Minimum OCI Shape OCPUs Memory
• VM-100,
VM-300,
VM-500, and
VM-700
• Software NFGW
Credit-based
VM-Series
VM.Optimized3.Flex
VM.Standard3.Flex
18 256
VM.Standard.E4.Flex
```
(AMD instance)
```
comes with default 1
CPU and maximum of
64 OCPUs
64 GB per OCPU, up
to 1024 GB total
VM.Standard.E5.Flex
```
(AMD instance)
```
comes with default 1
CPU and maximum of
94 OCPUs
64 GB per OCPU, up
to 1049 GB total
• VM-100,
VM-300,
VM-500, and
VM-700
• Software NFGW
Credit-based
VM-Series
VM.Standard.E6.Flex
```
(AMD instance)
```
comes with default 1
CPU and maximum of
126 OCPUs
64 GB per OCPU, up
to 1454 GB total
AMD VM.Standard.E4.Flex, VM.Standard.E5.Flex, and VM.Standard.E6.Flex instances
come with one default CPU and supports one vNIC. For multiple vNICs, configure OCPUs
in the required range.
You can deploy the VM-Series firewall on an OCI instance with more resources than the minimum
VM-Series System Requirements. If you choose a larger shape size for the VM-Series firewall
model. Although the firewall only uses the maximum vCPUs cores and memory listed on the
system requirements page, it does take advantage of the faster network performance that the
larger shape provides.
VM-Series Public Cloud Deployments 648 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on Oracle Cloud Infrastructure
Deployments Supported on OCI
Use the VM-Series firewall on OCI to secure your cloud environment in the following scenarios:
• North-South Traffic—You can use the VM-Series firewall to secure traffic entering your cloud
network from an untrusted source or exiting your cloud network to reach an untrusted source.
For either type of traffic, you must configure route table rules in your VCN and NAT policy
rules on the firewall.
In this example, outbound traffic is exiting the trust subnet in your VCN. You must configure a
source address translation policy onto a public IP address and a route table rule that redirects
that traffic to the firewall. The route rule points outgoing traffic to the firewall’s interface in the
trust subnet of the VCN. When the firewall receives this traffic, it performs the source address
translation on the traffic and applies any other security policy you have configured.
```
• Inter-VCN Traffic (East-West)—The VM-Series firewall allows you to secure traffic moving
```
```
within your cloud environment between Virtual Cloud Networks (VCN). Each subnet must
```
belong to a different VCN because, by default, no route rules are used to enable traffic within a
VCN. In this scenario, you configure an interface on the firewall connected to a subnet in each
VCN.
In the example below, a user in the Trust subnet wants to access data in the DB subnet.
Configure a route on OCI that reaches DB subnet CIDR next hop, which points to the interface
Trust subnet network on the VM-Series firewall.
OCI uses a series of route tables to send traffic out of your VCN and one route table is added to
each subnet. A subnet is a division of your VCN. If you don't specify a route table, the subnet uses
the VCN’s default route table.
VM-Series Public Cloud Deployments 649 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on Oracle Cloud Infrastructure
```
Each route table rule specifies a destination CIDR block and a next hop (target) for any traffic that
```
matches the CIDR. OCI only uses a subnet’s route table if the destination IP address is outside the
```
VCN’s specified CIDR block; route rules are not required to enable traffic within the VCN. And, if
```
traffic has overlapping rules, OCI use the most specific rule in the route table to route traffic.
If there is no route rule that matches the traffic that’s attempting to leave the VCN, the
traffic is dropped.
Each subnet requires a route table and once you have added a route table to a subnet, you can't
change it. However, you can add, remove, or edit rules in a route table after it has been created.
VM-Series Public Cloud Deployments 650 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on Oracle Cloud Infrastructure
Prepare to Set Up the VM-Series Firewall on OCI
Where Can I Use This? What Do I Need?
```
• Oracle Cloud Infrastructure (OCI) instance VM-Series License (BYOL)
```
VM-Series plugin
Panorama
Panorama plugin for OCI
The process to deploy the VM-Series firewall on Oracle Cloud Infrastructure requires the
completion of preparation tasks.
Virtual Cloud Networks
```
A virtual cloud network (VCN) is a virtual private network that you set up in your OCI
```
environment. To deploy the VM-Series firewall in OCI, your VCN must have at least three virtual
```
network interface cards (VNICs) for the management interface and two data interfaces.
```
OCI uses a series of route tables to send traffic out of your VCN and one route table is added
to each subnet. A subnet is a division of your VCN. If you don't specify a route table, the subnet
uses the VCN’s default route table.Each route table rule specifies a destination CIDR block and a
```
next hop (target) for any traffic that matches the CIDR. OCI only uses a subnet’s route table if the
```
```
destination IP address is outside the VCN’s specified CIDR block; route rules are not required to
```
enable traffic within the VCN. And, if traffic has overlapping rules, OCI use the most specific rule
in the route table to route traffic.
If there is no route rule that matches the traffic that’s attempting to leave the VCN, the
traffic is dropped.
Each subnet requires a route table and once you have added a route table to a subnet, you can't
change it. However, you can add, remove, or edit rules in a route table after it is created.
SSH Keys
You must create an SSH key pair to login to the firewall for the first time. You can't use the
default username and password to access the firewall for the first time. After the firewall boots
up for the first time, you must access the firewall through the CLI and create a new username and
password.
1. Create an SSH key pair and store the SSH Key pair in the default location for your operating
system.
• On Linux or macOS, use ssh-keygen to create the key pair in your .ssh directory.
• On Windows, use PuTTYgen to create the key pair.
```
The content of the Key comment field does not matter to the VM-Series firewall; you can
```
```
accept the default (the key creation date) or enter a comment that helps you remember the
```
name of the key pair. Use the Save private key button to store the private key in your .ssh
directory.
VM-Series Public Cloud Deployments 651 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on Oracle Cloud Infrastructure
2. Select the full public key.
• Linux or macOS:
Open your public key in a text editor and copy the public key.
• Windows: You must use the PuTTY Key Generator to view the public key. Launch
PuTTYgen, click Load, and browse to private key you saved in your .ssh directory.
In PuTTYgen, scroll down to ensure you select the entire key, right click, and choose Copy.
Initial Configuration User Data
Use the following bootstrapping parameters when setting up the VM-Series firewall instance.
OCI uses this information to perform the initial configuration of the firewall, which provides the
firewall with a hostname and license and connects the firewall to Panorama, if applicable.
The vm-auth-key parameter is only required if your VM-Series firewall can connect to
the Palo Alto Networks licensing servers.
The Panorama-related fields are required only if you have a Panorama appliance and want
to use Panorama to manage your VM-Series firewall.
Field Description
```
hostname= Host name for the firewall.
```
vm-auth-key= Virtual machine authentication key for registering
the firewall with Panorama.
panorama-server= IPv4 or IPv6 address of the primary Panorama
server. This field isn't required but recommended
for centrally managing your firewalls.
VM-Series Public Cloud Deployments 652 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on Oracle Cloud Infrastructure
Field Description
panorama-server-2= IPv4 or IPv6 address of the secondary Panorama
server. This field isn't required but recommended.
```
tplname= Panorama template stack name. If you add a
```
Panorama server IP address, as a best practice,
assign the firewall to a template stack on Panorama
and enter the template stack name in this field
so that you can centrally manage and push
configuration settings to the firewall.
```
dgname= Panorama device group name. If you add a
```
Panorama server IP address, as a best practice,
create a device group on Panorama and enter the
device group name in this field so that you can
group the firewalls logically and push policy rules
to the firewall.
```
authcodes= Used to license the VM-Series firewall with the
```
Palo Alto Networks licensing server.
op-command-modes=jumbo-frame Used to enable jumbo frame mode on the VM-
Series firewall. Because OCI deploys VM instances
in jumbo mode by default, it's recommended that
you launch the VM-Series firewall in jumbo mode
to achieve the best throughput.
Paste the bootstrapping parameters into the OCI console in the following format.
```
hostname=<fw-hostname>
```
vm-auth-key=<auth-key>
panorama-server=<panorama-ip>
panorama-server-2=<panorama2-ip>
```
tplname=<template-stack-name>
```
```
dgname=<device-group-name>
```
```
authcodes=<firewall-authcode>
```
op-command-modes=jumbo-frame
VM-Series Public Cloud Deployments 653 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on Oracle Cloud Infrastructure
Deploy the VM-Series Firewall from the Oracle Cloud
Marketplace
Where Can I Use This? What Do I Need?
```
• Oracle Cloud Infrastructure (OCI) instance VM-Series License (BYOL)
```
VM-Series plugin
Panorama
Panorama plugin for OCI
Complete the following procedure to deploy the VM-Series firewall in OCI from the Oracle Cloud
Marketplace.
All VM-Series firewall interfaces must be assigned an IPv4 address when deployed in a
public cloud environment. IPv6 addresses are not supported.
STEP 1 | Log in to the Oracle Cloud Marketplace.
STEP 2 | Find the VM-Series firewall application in the Oracle Cloud Marketplace.
1. Search for Palo Alto Networks and a list of offerings for the VM-Series firewall will
display.
2. Select an offering.
3. Click Get App.
4. Select your Region and click Sign In.
5. Select the Version and Compartment.
6. Accept the Oracle and Partner terms.
7. Click Launch Instance.
STEP 3 | Enter a descriptive Name for your VM-Series firewall instance.
STEP 4 | Select an Availability Domain.
VM-Series Public Cloud Deployments 654 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on Oracle Cloud Infrastructure
STEP 5 | Select Virtual Machine under Shape Type.
STEP 6 | Select the shape with the number of CPUs, amount of RAM, and number of interfaces
required for the VM-Series firewall model. See the Compute Shapes page for the amount of
resources provided by the different compute shapes. See VM-Series System Requirements
for more information about the resources required for each VM-Series firewall model.
STEP 7 | Under Networking, select your Virtual cloud network compartment, Virtual cloud network,
Subnet compartment, and Subnet for your management interface. You can only add one
interface when creating the VM-Series firewall instance. You will add additional interfaces
later.
```
STEP 8 | (Optional) Set the boot volume to a size larger than the default. By default, the boot volume
```
is set to 60GB. Complete this procedure if you require a larger boot volume to support
features such as attaching logs.
1. Select Custom boot volume size (in GB).
2. Enter 60 or greater. 60 GB is the minimum hard drive size required by the VM-Series
firewall.
VM-Series Public Cloud Deployments 655 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on Oracle Cloud Infrastructure
STEP 9 | Add your SSH key.
1. Under Add SSH Key, select Paste SSH Key.
2. Paste your SSH key into the field provided.
STEP 10 | Add the bootstrapping parameters.
1. Click Show Advanced Options.
2. Under User data, select Paste cloud-init script.
3. Paste the boostrap parameters into the field provided.
```
hostname=<fw-hostname>
```
vm-auth-key=<auth-key>
panorama-server=<panorama-ip>
panorama-server-2=<panorama2-ip>
```
tplname=<template-stack-name>
```
```
dgname=<device-group-name>
```
```
authcodes=<firewall-authcode>
```
op-command-modes=jumbo-frame
STEP 11 | Click Create.
When the VM-Series firewall is launched, OCI creates and attaches a primary VNIC to the
instance. This VNIC resides in the subnet you specified in the instance network setting and
connects to the VM-Series firewall’s management interface.
VM-Series Public Cloud Deployments 656 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on Oracle Cloud Infrastructure
STEP 12 | Configure a new administrative password for the firewall.
1. Use the management IP address to SSH into the command line interface (CLI) of the VM-
Series firewall.
2. Enter the following command to login to the firewall:
ssh-i <private_key.pem> admin@<public-ip_address>
3. Configure a new password, using the following command and follow the onscreen
```
prompts:
```
configure
set mgt-config users admin password
STEP 13 | Attach a vNIC to your VM-Series firewall instance for each data interface. You must attach
at least two data interfaces to your firewall instance—untrust and trust.
1. Select your newly launched VM-Series firewall instance and select Attached VNICs >
Create VNIC.
2. Enter a descriptive Name for your vNIC.
3. Select your VCN from the Virtual Cloud Network drop-down.
4. Select your subnet from the Subnet drop-down.
5. Specify a Private IP Address. This is only required if your want to choose a particular
IP for the vNIC. If you don't specify an IP, OCI will assign an IP address from the CIDR
block you assigned to the subnet.
6. Select Assign Public IP Address for public facing vNICs such as your untrust subnet.
7. Click Create VNIC.
8. Repeat this procedure for each vNIC your deployment requires.
VM-Series Public Cloud Deployments 657 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on Oracle Cloud Infrastructure
STEP 14 | Configure the dataplane network interfaces as Layer 3 interfaces on the firewall.
1. Log in to the firewall.
2. Select Network > Interfaces > Ethernet.
3. Click the link for ethernet 1/1 and configure as follows:
• Interface Type: Layer3
• On the Config tab, assign the interface to the default router.
• On the Config tab, expand the Security Zone drop-down and select New Zone.
Define a new zone, for example untrust-zone, and then click OK.
• On the IPv4 tab, select either Static.
• Click Add in the IP section and enter the IP address and network mask for the
interface. Make sure that the IP address matches the IP address that you assigned
to the corresponding subnet in VCN. For example, if you add this interface to your
untrust zone, make sure you assign the untrust vNIC IP address configured in your
VCN.
4. Repeat this procedure for each vNIC configured in your VCN except your management
vNIC.
Always only delete interfaces at the bottom of the interface list. Deleting firewall
interfaces in the wrong order results in an interface mismatch between the firewall
and OCI. For example, say you have five data interfaces, then delete interface two on
the firewall and add a new interface at the bottom. After rebooting the firewall, the
newly added interface will take the place of the deleted interface two instead of taking
a place at the bottom of the list.
VM-Series Public Cloud Deployments 658 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on Oracle Cloud Infrastructure
Configure Active/Passive HA on OCI
Where Can I Use This? What Do I Need?
```
• Oracle Cloud Infrastructure (OCI) instance VM-Series License (BYOL)
```
VM-Series plugin
Panorama
Panorama plugin for OCI
```
You can configure a pair of VM-Series firewalls on OCI in an active/passive high availability (HA)
```
configuration. To ensure uptime in an HA setup on OCI, you must create a secondary, floating
IP addresses that can quickly move from one peer to the other. When the active firewall goes
down, the floating IP address moves from the active to the passive firewall so that the passive
firewall can seamlessly secure traffic as soon as it becomes the active peer. In addition to the
```
floating IP address, the HA peers also need HA links—a control link (HA1) and a data link (HA2)—
```
to synchronize data and maintain state information.
The VM-Series firewall for OCI in FIPS mode on PAN-OS version 10.2 and above supports
high availability.
To allow the firewalls to move the floating IP address upon failover, you must place the firewall
instances in a dynamic group on OCI. Dynamic groups allow you to group the firewall instances
as principal actors and create policy to allow the instances in the dynamic group to make API calls
against OCI services. You will use matching rules to add the HA peer instances to the dynamic
group and then create the policy the floating IP from one VNIC to another.
VM-Series Public Cloud Deployments 659 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on Oracle Cloud Infrastructure
Both VM-Series firewalls in the HA pair must have the same number of network interfaces. Each
firewall requires a minimum of four interfaces—management, untrust, trust, and HA. You can
configure additional data interfaces as required by your deployment.
• Management interface—the private and public IP addresses associated with the primary
interface. You can use the private IP address on the management interface as the IP address
for the HA1 interface between the peers. If you want a dedicated HA interface, you must
attach an additional interface to each firewall, for a total of five interfaces each.
• Untrust and trust interfaces—each of these data interfaces on the active HA peer require a
primary and secondary IP address. Upon failover, when the passive HA peer transitions to the
active state, the secondary private IP address is detached from the previously active peer and
attached to the now active HA peer.
• HA2 interface—this interface has a single private IP address on each HA peer. The HA2
interface is the data link peers use to synchronize sessions, forwarding tables, IPsec security
associations, and ARP tables.
STEP 1 | Bootstrap the VM-Series Firewall on OCI and set up the network interfaces for HA.
1. (Optional) Configure a dedicated HA1 interface on each HA peer.
1. From the OCI Console, select Compute > Instances and click on the name of your
active peer instance.
2. Select Attached VNICs and click Create VNIC.
3. Enter a descriptive name for your HA1 interface.
4. Select the VCN and subnet.
5. Enter a private IP address.
6. Click Create VNIC.
7. Repeat this process on your passive peer instance.
2. Configure an HA2 interface on each HA peer.
1. From the OCI Console, select Compute > Instances and click on the name of your
active peer instance.
2. Select Attached VNICs and click Create VNIC.
3. Enter a descriptive name for your HA2 interface.
4. Select the VCN and subnet. The HA2 interface should be on a separate subnet from
your data interfaces.
5. Enter a private IP address.
6. Click Create VNIC.
7. Repeat this process on your passive peer instance.
3. Add a secondary IP address to your dataplane interfaces on the active peer.
1. From the OCI Console, select Compute > Instances and click on the name of your
active peer instance.
2. Select Attached VNICs and click on your untrust VNIC.
3. Select IP Addresses and click Assign Private IP Address.
4. Enter the IP address and click Assign.
5. Repeat this procedure for each dataplane interface on your active peer.
VM-Series Public Cloud Deployments 660 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on Oracle Cloud Infrastructure
STEP 2 | Create security rules to allow the HA peers to synchronize data and maintain state
information. By default, OCI allows ICMP traffic only. You must open the necessary HA
ports.
1. Open the ports for your HA1 interface.
1. From the OCI Console, select Networking > Virtual Cloud Networks and select your
VCN.
2. Select Subnets and select the subnet containing your HA1 interface.
3. Select Security Lists and click the default security list to edit it.
4. Click Add Ingress Rule.
5. Enter the Source CIDR that includes the HA peer HA1 port IP address.
6. Select TCP from the IP Protocol drop-down.
7. Click +Additional Ingress Rule.
VM-Series Public Cloud Deployments 661 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on Oracle Cloud Infrastructure
You need to create two additional rules for TCP ports 28260 and 28769 as the
Destination Port Range.
VM-Series Public Cloud Deployments 662 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on Oracle Cloud Infrastructure
8. If encryption is enabled on your VM-Series firewall for the HA1 link, create an
additional rules for ICMP and TCP port 28.
9. Click Add Ingress Rules.
VM-Series Public Cloud Deployments 663 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on Oracle Cloud Infrastructure
2. Open the ports for your HA2 interface.
1. From the OCI Console, select Networking > Virtual Cloud Networks and select your
VCN.
2. Select Subnets and select the subnet containing your HA2 interface.
3. Select Security Lists and click the default security list to edit it.
4. Click Add Ingress Rule.
5. Enter the Source CIDR that includes the HA peer HA2 port IP address.
6. Select UDP or IP from the IP Protocol drop-down.
7. If the transport mode is UDP, enter 29281 into Source Port Range. If the transport
mode is IP, enter 99 into Source Port Range.
8. Click Add Ingress Rules.
VM-Series Public Cloud Deployments 664 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on Oracle Cloud Infrastructure
STEP 3 | Add both HA peers to a dynamic group and create a policy that allows the HA peers to
move the floating IP address. You must have the OCID of each HA peer instance to build the
dynamic group matching rules.
1. Create the dynamic group.
1. From the OCI Console, select Identity > Dynamic Groups > Create Dynamic Group.
2. Enter a descriptive Name for your dynamic group.
3. Click Rule Builder.
4. Select Any of the following rules from the first drop-down.
5. Select Match instances with ID: from the Attributes drop-down and paste one of the
peer OCIDs into the Value field.
6. Click +Additional Line.
7. Select Match instances with ID: from the Attributes drop-down and paste the other
peer OCID into the Value field.
8. Click Add Rule.
9. Click Create Dynamic Group.
2. Create the policy rule.
1. From the OCI Console, select Identity > Policies > Create Policy.
2. Enter a descriptive Name for your policy.
3. Enter the first policy statement.
Allow dynamic-group <dynamic_group_name> to use virtual-
network-family in compartment <compartment_name>
4. Click +Another Statement.
5. Enter the second policy statement.
Allow dynamic-group <dynamic_group_name> to use instance-
family in compartment <compartment_name>
6. Click Create.
VM-Series Public Cloud Deployments 665 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on Oracle Cloud Infrastructure
STEP 4 | Configure the interfaces on the firewall. You must configure the HA2 data link and at least
two Layer 3 interfaces for your untrust and trust interfaces. Complete this workflow on the
first HA peer and then repeat the steps on the second HA peer.
1. Log in to the firewall web interface.
2. (Optional) If you're using the management interface as HA1, you must set the interface
IP Type to static and configure a DNS server.
1. Select Device > Setup > Interfaces > Management.
2. Set the IP Type to Static.
3. Enter the private IP address of the primary VNIC of your VM-Series firewall instance.
4. Click OK.
5. Select Device > Setup > Services.
6. Click Edit.
7. Enter the IP address of the Primary DNS Server.
8. Click OK.
9. Commit your changes.
3. Select Network > Interfaces > Ethernet and click on your untrust interface. In this
example, the HA2 interface is 1/1, the trust interface is ethernet 1/2, and the untrust
interface is ethernet 1/3.
4. Click the link for ethernet 1/1 and configure as follows:
• Interface Type: HA
5. Click the link for ethernet 1/2 and configure as follows:
• Interface Type: Layer3
• On the Config tab, assign the interface to the default router.
• On the Config tab, expand the Security Zone drop-down and select New Zone.
Define a new zone, for example trust-zone, and then click OK.
• On the IPv4 tab, select either Static.
• Click Add in the IP section and enter the primary IP address and network mask for the
interface. Make sure that the IP address matches the IP address that you assigned to
VM-Series Public Cloud Deployments 666 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on Oracle Cloud Infrastructure
the corresponding subnet in VCN. For example, if you add this interface to your trust
zone, make sure you assign the trust vNIC IP address configured in your VCN.
• Click Add in the IP section and enter the secondary, floating IP address and network
mask.
6. Click the link for ethernet 1/3 and configure as follows:
• Interface Type: Layer3
• On the Config tab, assign the interface to the default router.
• On the Config tab, expand the Security Zone drop-down and select New Zone.
Define a new zone, for example untrust-zone, and then click OK.
• On the IPv4 tab, select either Static.
• Click Add in the IP section and enter the primary IP address and network mask for
the interface. Make sure that the IP address matches the IP address that you assigned
to the corresponding subnet in VCN. For example, if you add this interface to your
untrust zone, make sure you assign the untrust vNIC IP address configured in your
VCN.
• Click Add in the IP section and enter the secondary, floating IP address and network
mask.
VM-Series Public Cloud Deployments 667 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on Oracle Cloud Infrastructure
STEP 5 | Enable HA.
1. Select Device > High Availability > General.
2. Edit the Setup settings.
3. Enter the private IP address of the passive peer in the Peer HA1 IP address field.
4. Click OK.
5. (Optional) Edit the Control Link (HA1). If you don't plan to use the management interface
```
for the control link and have added an additional interface (for example ethernet 1/4),
```
edit this section to select the interface to use for HA1 communication.
6. Edit the Data Link (HA2) to use Port ethernet 1/1 and add the IP address of active peer
and the Gateway IP address for the subnet.
7. Select IP or UDP from the Transport drop-down. Ethernet isn't supported.
8. Click OK.
STEP 6 | Commit your changes.
STEP 7 | Repeat step 4 and step 5 on the passive HA peer.
STEP 8 | After your finish configuring HA on both firewalls, verify that the firewalls are paired in
active/passive HA.
1. Access the Dashboard on both firewalls and view the high availability widget.
2. On the active HA peer, click Sync to peer.
3. Confirm that the firewalls are paired and synced.
• On the passive firewall: the state of the local firewall should display Passive and the
Running Config should show as Synchronized.
• On the active firewall: the state of the local firewall should display Active and the
Running Config should show as Synchronized.
VM-Series Public Cloud Deployments 668 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on Oracle Cloud Infrastructure
Forward Metrics to Oracle Cloud Infrastructure
Where Can I Use This? What Do I Need?
```
• VM-Series (Managed by PAN-OS®,
```
```
Panorama®, or Strata Cloud Manager)
```
```
• Prisma AIRS (Managed by PAN-OS®,
```
```
Panorama®, or Strata Cloud Manager)
```
OCI Cloud environment
Client certificates for mTLS
OCI Kafka Metric Forwarding enables your OCI Firewalls to directly push operational metrics to
OCI Kafka. This feature moves away from traditional polling mechanisms, improving scalability
and providing a unified data path for metrics. Your firewalls can actively transmit data directly
to OCI Kafka, eliminating intermediary VMs. OCI Kafka simplifies data ingestion architectures. It
offers enhanced scalability and high availability, handling increased metric volume and velocity
from more firewalls through its managed service design.
Your OCI Firewalls collect and push several types of operational data:
• Data flow metrics
• System metrics for firewall resource health
• Customer metrics for user and application activity
• App-ID™ metrics for application identification details
Each metric includes essential metadata such as timestamp, instance ID, compartment ID, and
PAN-OS version for analysis. This feature exports existing identified metrics more efficiently,
without introducing new categories.
The metric forwarding system consists of the following components:
```
• OCI Firewall (VM-Series): Acts as the primary source for operational metrics, collecting data
```
flow, system, customer, and App-ID metrics.
• OCI Kafka: A managed service within Oracle Cloud Infrastructure that serves as the
centralized, scalable, and highly available destination for forwarded metrics. This
implementation replaces existing OCI streaming pools.
The entire metric forwarding solution relies on the availability and configuration of an external
OCI Kafka managed service. This service handles the complexities of a Kafka cluster, including
high availability and scalability. Your OCI Firewall continuously collects a defined set of metrics. A
VM-Series plugin within your firewall establishes an internal connection with daemon to send this
data.
The firewall periodically collects and sends metrics to defined Kafka topics. The demon processes
the metrics received from your firewall and pushes them directly to your configured OCI Kafka
```
topic. This communication is secured using Mutual TLS (mTLS), requiring client certificates for
```
authentication and encryption.
VM-Series Public Cloud Deployments 669 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on Oracle Cloud Infrastructure
Configure OCI Forwarding Metrics
This section provides a step-by-step walkthrough for deploying and configuring the OCI Kafka
metric forwarding feature on your OCI Firewalls using CLI.
1. Configure Kafka metric forwarding parameters.
Use the request plugins vm_series kafka-metric-server command to define a
new Kafka metric server.
admin@PA-VM> request plugins vm_series kafka-metric-server client-
cert client2
kafka-broker bootstrap-clstr-a6tvlyfwpiixb84g.kafka.us-
phoenix-1.oci.oraclecloud.com:9093 kafka-topic metrics server-name
METRICS
Kafka metric server configured successfully
```
Name : METRICS
```
```
Broker : bootstrap-clstr-a6tvlyfwpiixb84g.kafka.us-
```
phoenix-1.oci.oraclecloud.com:9093
```
Topic : metrics
```
Client Certificate : configured
This command establishes a new Kafka metric server configuration on your firewall. It specifies
the client certificate for mTLS, the Kafka broker endpoint, the target topic for metrics, and a
unique name for this configuration.
2. Verify the configured Kafka metric servers.
Execute the show plugins vm_series kafka-metric-servers command to display
active configurations.
admin@PA-VM> show plugins vm_series kafka-metric-servers
Configured Kafka Metric Servers :
--------------------------------------------------
```
Name : METRICS
```
```
Broker : bootstrap-clstr-a6tvlyfwpiixb84g.kafka.us-
```
phoenix-1.oci.oraclecloud.com:9093
```
Topic : metrics
```
Client Certificate : configured
--------------------------------------------------
```
Total : 1 Kafka metric server(s) configured
```
3. (Optional) Debug and monitor Kafka metric forwarding.
1. Check the Kafka log level configuration using debug plugins vm_series kafka set-log-level
show.
admin@PA-VM> debug plugins vm_series kafka set-log-level show
Kafka Log Level Configuration
=======================================================
VM-Series Public Cloud Deployments 670 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on Oracle Cloud Infrastructure
```
Timestamp : 2026-04-06 12:09:29
```
Config File : /etc/fluent-bit/fluent-bit-kafka.conf
```
Input :
```
```
Log_Level : info
```
```
Output :
```
rdkafka.debug : broker,topic,security
```
Pipeline PID : 1137139 (running)
```
This command provides insight into the current logging configuration for the Kafka metric
forwarding process, indicating what level of detail is being captured.
2. View the pipeline statistics using debug plugins vm_series kafka statistics.
admin@PA-VM> debug plugins vm_series kafka statistics
```
Fluent Bit Pipeline Statistics (accumulated)
```
=================================================================
```
Process : Running (PID 1137139, uptime 3h 47m 29s)
```
```
Timestamp : 2026-04-06 15:50:48
```
```
Summary :
```
Total Input Records : 890
Total Input Bytes : 1.60 MB
Total Output Records : 890
Total Output Bytes : 1.60 MB
Total Dropped : 0
```
Pending (in-flight) : 0
```
Buffered Chunks : 0
Buffer Memory : 0 B
Input Plugins :
Name Records Bytes
----------------------------------------------------------
kafka_METRICS_in 890 1.60 MB
storage_backlog.1 0 0 B
```
Output Plugins (per topic) :
```
Name Queued Bytes Dropped Retried
Errors Status
---------------------------------------------------------------------------
kafka_METRICS_out 890 1.60 MB 0
0 0 OK
```
STATUS : All records queued to Kafka output plugin
```
```
NOTE : These are Fluent Bit pipeline counters. 'Delivered' means
```
VM-Series Public Cloud Deployments 671 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on Oracle Cloud Infrastructure
queued to the Kafka client library, not confirmed by
broker.
Run 'debug plugins vm_series kafka config-status' to verify
broker connectivity and mTLS handshake.
```
3. Verify broker connectivity and mTLS handshake status using debug plugins
vm_series kafka config-status.
admin@PA-VM> debug plugins vm_series kafka config-status
<response status="success">
<result>
Kafka Configuration Status
=================================================================
```
Timestamp : 2026-04-06 15:51:48
```
Fluent Bit :
```
Process : Running (PID 1137139)
```
```
Health API : N/A (process running)
```
Config File : present
Kafka Metrics Server SDB :
```
Status : configured
```
```
Name : METRICS
```
```
Broker : bootstrap-clstr-a6tvlyfwpiixb84g.kafka.us-
```
phoenix-1.oci.oraclecloud.com:9093
```
Topic : metrics
```
Client Certificate : configured
Kafka Output [kafka_METRICS_out] :
```
Brokers : bootstrap-clstr-a6tvlyfwpiixb84g.kafka.us-
```
phoenix-1.oci.oraclecloud.com:9093
```
Topics : metrics
```
```
Match : firewall_metrics
```
Security Protocol : SSL
```
Compression : snappy
```
SSL/mTLS : Configured
VM-Series Public Cloud Deployments 672 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on Oracle Cloud Infrastructure
Broker Connectivity :
bootstrap-clstr-a6tvlyfwpiixb84g.kafka.us-
```
phoenix-1.oci.oraclecloud.com:9093 TCP OK (6.4 ms)
```
```
mTLS OK (12.0 ms)
```
Certificate & Key Status :
```
Client Cert : Present (expires : Mar 18 22:07:05 2027 GMT)
```
Private Key : Present
```
STATUS : All checks passed — Kafka configuration is valid
```
</result>
</response>
```
VM-Series Public Cloud Deployments 673 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on Oracle Cloud Infrastructure
Oracle Cloud Infrastructure Logging
Where Can I Use This? What Do I Need?
• VM-Series
• Prisma AIRS
OCI Network Firewall running PAN-OS®
11.2.13, 12.1.8 and 12.2.2 onwards.
OCI Managed Kafka Cluster: Must be
active with an accessible bootstrap
endpoint operating on port 9093.
Kafka Topics: It is recommended that you
have the following three topics prior to
```
setup: fw-traffic, fw-threat, and fw-url.
```
mTLS Certificates: A client certificate and
private key bundle in PKCS12 format.
PA-VM Reachability & Certificate Import:
The PA-VM must be active, reachable, and
have the following certificates imported:
• Kafka-CA: The Kafka cluster CA
certificate imported in PEM format as a
standard certificate.
• Kafka-Client-Cert: The client certificate
- private key imported as a keypair.
```
Cloud-native enterprise environments deployed within Oracle Cloud Infrastructure (OCI) can now
```
use OCI Logging that enables the PA-VM firewalls to stream traffic, threat, URL logs, and so on,
directly into an OCI Managed Kafka cluster.
You can use OCI Logging to:
• Centralize firewall log analytics directly into a managed OCI Kafka event stream.
```
• Secure log transit using mutual TLS (mTLS) authentication.
```
```
• Ensure strict adherence to structured log formats ($type $time_generated <json>) required by
```
high-throughput SIEM and streaming parsers.
This integration relies on high-numbered, unprivileged syslog ports running locally on the PA-VM.
PAN-OS forwarders send logs to localhost, where an internal engine intercepts, parses, formats,
and safely pumps the data out to the designated Kafka topics.
The following are a few examples of the supported log types:
Log Type Syslog Port Kafka Topic Syslog Profile Server Name
traffic 5141 `fw-test` `syslog-kafka-
traffic`
`traffic`
VM-Series Public Cloud Deployments 674 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on Oracle Cloud Infrastructure
Log Type Syslog Port Kafka Topic Syslog Profile Server Name
threat 5142 `fw-threat` `syslog-kafka-
threat`
`threat`
url 5143 `fw-test2` `syslog-kafka-
url`
`url`
Configure OCI Logging
1. Configure Kafka logging servers.
Define a named Kafka server with its broker address, topic, partition key, and client certificate.
Run this command once per Kafka destination. If you run the command again with the
same server name, it updates the existing entry.
request plugins vm_series kafka-server server-name traffic kafka-
broker <bootstrap>:9093 kafka-topic fw-traffic kafka-part-key 0
client-cert Kafka-Client-Cert
request plugins vm_series kafka-server server-name threat kafka-
broker <bootstrap>:9093 kafka-topic fw-threat kafka-part-key 1
client-cert Kafka-Client-Cert
request plugins vm_series kafka-server server-name url kafka-broker
<bootstrap>:9093 kafka-topic fw-url kafka-part-key 2 client-cert
Kafka-Client-Cert
2. Associate log types to syslog ports.
Map each log type you want to forward to the Kafka server and assign a syslog port for that
log type. Run this command once per log type. You can reuse the same port across multiple log
types on the same server.
request plugins vm_series kafka-server-log-type server-name traffic
syslog-port 5141 type log-type traffic
request plugins vm_series kafka-server-log-type server-name threat
syslog-port 5142 type log-type threat
request plugins vm_series kafka-server-log-type server-name url
syslog-port 5143 type log-type url
3. Configure PAN-OS syslog server profiles.
```
Enter configuration mode (configure) and direct the syslog profiles to point to the local input
```
ports on 127.0.0.1 using standard BSD format over TCP.
set shared log-settings syslog syslog-kafka-traffic server syslog-
kafka-traffic server 127.0.0.1 transport TCP port 5141 format BSD
facility LOG_USER
set shared log-settings syslog syslog-kafka-threat server syslog-
kafka-threat server 127.0.0.1 transport TCP port 5142 format BSD
facility LOG_USER
set shared log-settings syslog syslog-kafka-url server syslog-
kafka-url server 127.0.0.1 transport TCP port 5143 format BSD
facility LOG_USER
VM-Series Public Cloud Deployments 675 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on Oracle Cloud Infrastructure
4. Crucial Apply Custom Log Format.
The syslog-pan parser expects a custom $type $time_generated <json> format. Standard
PAN-OS BSD syslog CSV output will fail parsing, drop all records and leave your Kafka topics
completely empty. Use the XML API to apply these specific XPaths and elements:
• Traffic Format
• XPath:
/config/shared/log-settings/syslog/entry[@name='syslog-kafka-
traffic']/format
• Element:
```
<traffic>\$type \$time_generated {"src_ip": "\$src", "sport":"\
```
$sport", "dst_ip": "\$dst", "dport":"\$dport", "proto": "\
$proto", "app": "\$app", "rule":"\$rule", "action": "\$action",
"bytes_recv":"\$bytes_received", "bytes_sent":"\$bytes_sent",
"pkts_received": "\$pkts_received", "pkts_sent":"\$pkts_sent",
"start_time": "\$start", "elapsed_time": "\$elapsed",
"repeat_count":"\$repeatcnt", "category":"\$category",
"src country":"\$srcloc", "dst country":"\$dstloc",
"session_end_reason": "\$session_end_reason", "xff_ip": "\
```
$xff_ip"}</traffic>
```
• Threat Format
• XPath:
/config/shared/log-settings/syslog/entry[@name='syslog-kafka-
threat']/format
• Element:
```
<threat>\$type \$time_generated {"src_ip": "\$src", "sport":"\
```
$sport", "dst":"\$dst", "dport":"\$dport", "proto": "\$proto",
"app":"\$app", "rule":"\$rule", "action": "\$action",
"threat_category": "\$thr_category", "sub_type": "\$subtype",
"threat_content_name":"\$threatid", "severity": "\$severity",
"direction": "\$direction", "repeatcnt":"\$repeatent",
"data_filter_reason": "\$reason", "filetype": "\$filetype",
```
"contentver": "\$contentver"}</threat>
```
• URL Format
• XPath:
/config/shared/log-settings/syslog/entry[@name='syslog-kafka-
url']/format
• Element:
```
<url>\$type \$time_generated {"src_ip":"\$src", "sport":"\
```
$sport", "dst":"\$dst", "dport":"\$dport", "proto": "\
$proto", "app":"\$app", "rule":"\$rule", "action": "\
$action", "url_idx":"\$url_idx", "url_category_list": "\
VM-Series Public Cloud Deployments 676 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on Oracle Cloud Infrastructure
$url_category_list", "severity": "\$severity", "direction":
"\$direction", "repeatent":"\$repeatent", "xff":"\$xff",
```
"url_filename":"\$misc"}</url>
```
5. Configure log forwarding profile.
Route each individual log type to its corresponding newly created syslog profile. Run the
following in configuration mode:
set shared log-settings profiles kafka-log-fwd match-list traffic-
fwd filter "All Logs" log-type traffic send-syslog syslog-kafka-
traffic
set shared log-settings profiles kafka-log-fwd match-list threat-
fwd filter "All Logs" log-type threat send-syslog syslog-kafka-
threat
set shared log-settings profiles kafka-log-fwd match-list url-fwd
filter "All Logs" log-type url send-syslog syslog-kafka-url
6. Attach log forwarding profile to security rules
Attach the forwarding profile to the specific security rules governing the traffic you intend to
stream. Make sure log-end yes is verified to cleanly capture session termination traffic logs.
set rulebase security rules allow-interzone log-setting kafka-log-
fwd
set rulebase security rules allow-interzone log-end yes
7. Commit the configuration.
Verification and Health Check
To check Kafka server statuses: Execute the command:
```
show plugins vm_series kafka-servers (verify traffic, threat, and url outputs show
```
```
correct brokers and cert profiles).
```
To check log port mapping: Execute the command:
```
show plugins vm_series kafka-server-log-type-mapping (verify traffic points to
```
```
5141, threat to 5142, and url to 5143).
```
Check Pipeline Health
Validate the running states of your connections and streaming statistics:
Connectivity/mTLS Health: Run
debug plugins vm_series kafka config-status and confirm that it outputs: STATUS:
All checks passed, mTLS OK, Private Key: Present on all 3 outputs.
Live Statistics: Run
debug plugins vm_series kafka statistics. Ensure traffic_logs_input > 0
after passing some ICMP traffic, Total Dropped: 0, and the output status reads OK for all
```
three log outputs (traffic_output, threat_output, url_output).
```
VM-Series Public Cloud Deployments 677 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on Oracle Cloud Infrastructure
Bootstrap the VM-Series Firewall on OCI
Where Can I Use This? What Do I Need?
```
• Oracle Cloud Infrastructure (OCI) instance VM-Series License (BYOL)
```
VM-Series plugin
Panorama
Panorama plugin for OCI
You can bootstrap new instances of the VM-Series firewall on OCI by creating the necessary files
and placing them in an OCI storage bucket. You must attach the necessary policies required to
access the storage bucket, instance-family, virtual-network-family to a dynamic-group on OCI.
This is required to make the API calls. Ensure that the VM-Series firewall instance being deployed
meets the match criteria of the dynamic group you will create.
STEP 1 | Choose a bootstrap method.
STEP 2 | Create bootstrap files as described in Prepare the Bootstrap Package.
STEP 3 | Log in to the OCI console.
STEP 4 | Create an object storage bucket.
The object storage bucket must be in the same region where you plan to deploy the VM-Series
firewall.
STEP 5 | Create a Dynamic Group to define the permissions needed to allow the VM-Series firewalls
to access the object storage bucket.
STEP 6 | Define the policy statements so your VM-Series firewall can access the bootstrap files.
Your policy must include the following statements.
Allow dynamic-group <dynamic_group_name> to use instance-family in
compartment <compartment_name>
Allow dynamic-group <dynamic_group_name> to use virtual-network-
family in compartment <compartment_name>
Allow dynamic-group <group name> to read buckets in compartment
<compartment_name>
Allow dynamic-group <group name> to read objects in compartment
<compartment_name>
STEP 7 | Create folders in your previously created object storage bucket. This folder structure must
match the structure of the bootstrap package. You can create the folder structure directly in
the storage bucket or, if you have multiple bootstrap packages, you can create a subfolder
for each one. Each subfolder must follow the structure of bootstrap package folders.
VM-Series Public Cloud Deployments 678 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on Oracle Cloud Infrastructure
STEP 8 | Launch the VM-Series firewall.
To deploy the VM-Series firewall using a bootstrap package, deploy the VM-Series firewall as
normal. However, instead of adding bootstrap parameters directly in the User Data field, you
will instead use the following commands to identify the location of the bootstrap package.If
your bootstrap package is at the top level of the storage bucket structure, use the following.
vmseries-bootstrap-oci-bucket=<bucket-name>
If your storage bucket has bootstrap packages in individual folders, use the following.
vmseries-bootstrap-oci-bucket=<bucket-name>/<folder-name>
VM-Series Public Cloud Deployments 679 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on Oracle Cloud Infrastructure
VM-Series Public Cloud Deployments 680 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on IBM Cloud
Where Can I Use This? What Do I Need?
```
• IBM Cloud VM-Series License (BYOL)
```
VM-Series plugin
Panorama
Panorama plugin for IBM Cloud
```
The VM-Series Next Generation Firewalls (NGFW) allow you to migrate your business-critical
```
applications to the cloud and protect the increased public cloud footprint from threats, data loss,
and business disruption by:
• Offering unmatched application visibility and precise control.
• Preventing threats from moving laterally between workloads and stopping data exfiltration.
• Eliminating security-induced application development bottlenecks with automation and
centralized management.
See the following topics for system requirements and licensing information:
681
VM-Series Firewall on IBM Cloud
Licensing Information
```
The VM-Series firewall supports the bring-your-own-license (BYOL) model on IBM Cloud. For
```
```
more information, see Bring Your Own License (BYOL).
```
VM-Series Public Cloud Deployments 682 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on IBM Cloud
System Requirements for VM-Series Firewall on IBM
Cloud
To deploy a VM-Series firewall on an IBM Cloud instance, you must choose a machine type that
supports the VM-Series System Requirements for your license.
Refer to the table below for the minimum recommended predefined standard machine types.
Capacity Minimum Recommended Predefined Machine Types
VM-100 Firewall bx2d-2x8
VM-200 Firewall bx2d-2x8
VM-300 Firewall bx2d-4x16
VM-500 Firewall bx2d-4x16
VM-700 Firewall bx2d-16x64
You can choose a higher performing machine type or create your own custom machine type, if the
resource requirements are compatible with your VM-Series firewall license. A single IBM Cloud
instance supports up to five network interfaces. For more information on machine types, see
Instance Profiles.
VM-Series Public Cloud Deployments 683 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on IBM Cloud
Prepare to Set Up VM-Series Firewalls on IBM Cloud
Where Can I Use This? What Do I Need?
```
• IBM Cloud VM-Series License (BYOL)
```
VM-Series plugin
Panorama
Panorama plugin for IBM Cloud
Deploying the VM-Series firewall from IBM Cloud Platform requires preparation tasks. If you're
deploying using the IBM Cloud catalog, you must create your project networks and subnetworks,
and plan IP address assignments for the VM-Series firewall interfaces in advance. During the
deployment, you must choose from existing networks and subnetworks.
Prerequisites
To set up the VM-Series firewall on IBM Cloud, you will need:
• Access to IBM Cloud Gen 2 VPC
• A VPC with at least two subnets and one IP address unassigned in each subnet. The IP
addresses to the VM-Series VSI will be assigned from the user-provided subnets. For more
information, see
• One of the following regions to install PAN-OS:
• us-east
• us-south
• ca-tor
• eu-gb
• eu-de
• eu-fr2
• au-syd
• jp-osa
• jp-tok
Dependencies
Before you can apply the template in IBM Cloud, complete the following steps:
• Ensure that you have the following permissions in IBM Cloud Identity and Access
```
Management:
```
• Manager service access role for IBM Cloud Schematics
• Operator platform role for VPC Infrastructure
VM-Series Public Cloud Deployments 684 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on IBM Cloud
• Ensure the following resources exist in your VPC Gen 2 environment:
• VPC
• SSH Key - Public SSH Key Doc
• VPC has two subnets - one for management, the other for dataplane traffic
```
• Floating IP (FIP) address to assign to the management interface of VM-Series instance post
```
deployment. FIP is used to access your VPC virtual server instance over the public internet.
For more information, see Creating a floating IP address.
General Requirements
The components in this checklist are common to deploying a VM-Series firewall that you manage
directly or with Panorama.
Refer to the Compatibility Matrix for Panorama plugin information for public clouds. This release
requires the following software:
• IBM Cloud account—You must have an IBM Cloud user account with a linked email address
and you must know the username and password for that email address.
IBM Cloud SDK—If you have not done so, install the IBM Cloud Software, which includes IBM
Cloud APIs and command-line tools. You can use the command-line interface to deploy the
firewall template and other templates.
• PAN-OS on VM-Series firewalls on IBM Cloud—VM-Series firewalls running a PAN-OS version
available from the IBM Cloud Catalog.
• VM-Series firewalls—VM-Series firewalls that you want to manage from Panorama must
be deployed in IBM Cloud Platform using a Palo Alto Networks image from the IBM Cloud
Catalog. Firewalls must meet the minimum system requirements.
• VM-Series Licenses—You must license a VM-Series firewall to obtain a serial number. A
serial number is required to add a VM-Series firewall as a Panorama managed device. If
you're using the Panorama plugin for IBM Cloud to deploy VM-Series firewalls, you must
supply a BYOL auth code. The IBM Cloud handles your service billing, but the firewalls you
deploy will directly interface with the Palo Alto Networks licensing server.
• VM-Series plugin on the firewall—VM-Series firewalls running PAN-OS 9.0 and later include
the VM-Series plugin, which manages integration with public and private clouds. As shown
VM-Series Public Cloud Deployments 685 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on IBM Cloud
in the Compatibility Matrix, the VM-Series plugin has a minimum version that corresponds
to each PAN-OS release.
When there is a major PAN-OS upgrade the VM-Series plugin version is automatically
upgraded. For minor releases it's up to you to determine whether a VM-Series plugin
upgrade is necessary, and if so, perform a manual upgrade.
• Panorama running in Management mode—A Panorama physical or virtual appliance running
a PAN-OS version that is the same or later than the managed firewalls. Virtual instances
don't need to be deployed in IBM Cloud.
You must have:
• A licensed version of Panorama.
• Panorama having network access to the VPCs in which the VMs you want to manage are
deployed.
• VM-Series plugin on Panorama. See Install the VM-Series Plugin on Panorama.
VM-Series Public Cloud Deployments 686 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on IBM Cloud
Deploy the VM-Series Firewall Using IBM Cloud
Schematics
Where Can I Use This? What Do I Need?
```
• IBM Cloud VM-Series License (BYOL)
```
VM-Series plugin
Panorama
Panorama plugin for IBM Cloud
To deploy the VM-Series firewall using the IBM catalog template, you must first create a VPC
network for each interface on the firewall. For instructions on creating a VPC network, see
Getting Started with VPC network.
```
You can deploy the VM-Series Next-Generation Firewall (BYOL) through IBM cloud Schematics.
```
The IBM cloud terraform template deploys an instance of the VM-Series firewall with a minimum
of one management interface and two dataplane interfaces. You can add additional dataplane
```
interfaces for up to five IBM cloud instances in your virtual private cloud (VPC).
```
Before you deploy the VM-Series firewall, you must create or choose a project in your
organization and create any networks and subnets that will connect to the firewall. You can't
attach multiple network interfaces to the same VPC network. Every interface you create must
have a dedicated network with at least one subnet. Ensure that your networks include any
additional dataplane instances you create.
All VM-Series firewall interfaces must be assigned an IPv4 address when deployed in a
public cloud environment. IPv6 addresses are not supported.
STEP 1 | Locate the VM-Series firewall listing in IBM Cloud Catalog.
1. Log in to IBM Cloud.
2. Click Catalog.
3. Search for Palo Alto Networks VM-Series Firewall - BYOL in the IBM Cloud catalog
search box.
4. Click the Palo Alto Networks VM-Series Firewall - BYOL tile.
STEP 2 | Configure your workspace.
1. Enter the Deployment Name (this name is displayed in the Deployment Manager). The
name must be unique and can't conflict with any other deployment in the project.
2. Select a Resource group. For instructions to create a resource group, see Creating a
Resource Group.
3. Enter the relevant Tags. Tags help you in identifying your deployment.
VM-Series Public Cloud Deployments 687 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on IBM Cloud
STEP 3 | Specify the values for the following parameters:
Parameter Description Sample Value
image_name VM-Series image to be installed. pa-vm-kvm-9-1-3-1
or pa-vm-kvm-10-0-6
region VPC region that you want your VPC virtual
servers to be provisioned.
us-east
ssh_key_name The name of your public SSH key to be used
for VSI. For information on creating an SSH
key, see Public SSH Key.
vm-series-ssh-key
```
subnet_id1 The ID of the subnet (management) which will
```
be associated with the first interface of the
VNF instance. Click the subnet details in the
VPC subnet Listing to determine this value.
0717-xxxxxx-xxxx-
xxxxx-8fae-xxxxx
```
subnet_id2 The ID of the subnet (dataplane) which will be
```
associated with the second interface of the
VNF instance. Click the subnet details in the
VPC subnet Listing to determine this value.
0717-xxxxxx-xxxx-
xxxxx-8fae-xxxxx
vnf_instance_name Name of the VNF instance to be provisioned
```
(lower-case).
```
vm-series-fw-vsi
vnf_profile The profile of compute CPU and memory
resources to be used when provisioning
the vnf instance. For more information, see
Instance Profiles.
bx2-8x32
vnf_security_group The name of the security group to which the
```
VNF Instance's first interface(management)
```
belongs to.
vm-series-mgmt-sg
STEP 4 | Installing the terraform template.
1. Click Install.
2. Navigate to IBM cloud > Schematics > Workspaces and choose your workspace to view
and edit details related to your workspace.
STEP 5 | Accessing the management interface of the VM-Series firewall.
1. Navigate to IBM cloud > VPC Infrastructure > Floating IPs and copy the Floating IP of
your VPC instance on which you have deployed the VM-Series firewall.
2. Open a browser and enter the IP address in the URL region of the browser prefixing it
```
with HTTPS(for example, https://161.xxx.173.xxx). The VM-Series firewall management
```
VM-Series Public Cloud Deployments 688 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on IBM Cloud
interface login screen appears. If you're using a VPN connection, you may have to
```
terminate the connection before connecting to the VM-Series console (URL).
```
3. Log in to the interface using the following credentials: Username: admin Password:
admin
You will be prompted to change your password on your first login. You will be
able to access the interface only after logging in with the changed password.
Use Case:
In this example, the client is in a different zone compared to the rest of the resources.
VM-Series Public Cloud Deployments 689 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on IBM Cloud
Step 1: The ingress routing table directs the traffic towards the LBs in the direction of client to
server. In this case, since the client is in a different zone, the traffic source for the routing table is
the VPC zone.
VM-Series Public Cloud Deployments 690 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on IBM Cloud
Step 2: The Load Balancer sends the packets to one of the firewalls. Since the FW DP subnets and
the server subnet are in the same VPC, they can reach each other through the default gateways.
You need not configure custom routing on the firewall if the DP interface is configured as DHCP.
If the static IP is configured on the DP interface, then the default route needs to be configured on
the FW.
Step 3: Attach the Interface Management profile that permits HTTP/HTTPS probes to the DP
interface.
Step 4: Configure the security policy to allow the ingress traffic.
VM-Series Public Cloud Deployments 691 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on IBM Cloud
Step 5: For the return traffic moving in the direction of server to client, there must be an egress
```
routing table attached to the subnet of the server, directing the traffic (destined to the client) to
```
the LB. The LB forwards the packet to the same FW as the traffic in the other direction. The FW
will forward the packet via its default gateway to the client.
VM-Series Public Cloud Deployments 692 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on IBM Cloud
High Resiliency for VM-Series Firewall on IBM Cloud
Where Can I Use This? What Do I Need?
```
• IBM Cloud VM-Series License (BYOL)
```
VM-Series plugin
Panorama
Panorama plugin for IBM Cloud
You can deploy the VM-Series firewalls on IBM Cloud to ensure redundancy in the network by
```
using the active/active high availability (HA) configuration. The Network Load Balancer (NLB)
```
Route Mode feature is used to support the VM-Series HA and is currently supported only with
private IP and TCP data traffic.
The ingress routing capability allows you to associate route tables with the IBM internet
gateway and add route rules to redirect the application traffic through the VM-Series firewall.
This redirection ensures that all internet traffic passes through the firewall without having to
reconfigure the application endpoints.
For more information on network load balancer for VPC Gen 2 Offering, see
• Load Balancer for VPC Gen 2 Catalog Tile
• About IBM Cloud Network Load Balancer for VPC
Configure IBM VPC VM-Series for HA
To configure the VPC resources for HA, you will need to:
• Create a VPC. For instructions on creating a VPC network, see Getting Started with VPC
network.
• Create one subnet for the VM-Series management traffic interface. This can be shared
between multiple VM-Series to support clustering.
• Create one subnet that will be shared between the VM-Series data traffic interface and the
```
Network Load Balancer (NLB).
```
• Create any additional subnets needed for the VSI workloads that will be routed through the
NLB or VNFs.
• Grant a service authorization for your IBM Cloud Account to allow the NLB to modify custom
routes if an NLB failover occurs.
Deploy the VM-Series Firewall
While deploying the VM-Series firewall in HA mode, you will need to ensure the following:
• The VM-Series data interface is on the same shared subnet as the NLB we will provision later.
```
• Allow IP Spoofing is enabled on the VM-Series data interface (shared subnet with NLB)
```
through the Network Interfaces page of the VPC VSI User Interface.
VM-Series Public Cloud Deployments 693 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on IBM Cloud
• Health checks for the VNF configuration is enabled from the NLB.
Deploy the NLB
You can deploy an NLB using the UI, CLI, or REST API. For instructions on deploying an NLB, see
Creating a route mode Network Load Balancer for VPC.
Configure Security Groups
The VM-Series data network interface is attached to a VPC Security Group. While configuring the
Security Groups, ensure that the Security Group has Inbound rules that allow traffic on the health
port setup between the NLB and the VM-Series. For example, if the health check is set up for
```
TCP on port 80 (HTTP), then create an inbound rule under the same Security Group. Additionally,
```
ensure that the rules are created to allow or restrict data traffic.
Configure Custom Routes
Custom routes are created to ensure that the ingress data traffic is routed through the NLB on its
way to the VM-Series and target destination. In some cases custom routes may also be needed
to ensure egress traffic is returned to the original client source. For more information, see About
routing tables and routes.
Considerations for NLB Failovers and Custom Routes
• Deploy the NLB as an active/passive cluster. Ensure that each node has a distinct IP and the
active IP is used in the custom routes that are created. You can use an nslookup on the NLB
hostname, to determine the primary IP for use in your route config.
• Configure the VM-Series to allow traffic from both the active and passive NLB nodes. This is
needed for the health check. The NLB IPs can be retrieved from the NLB UI > Overview >
Private IPs.
• The custom routes are automatically updated to hop to the new NLB IP, if the NLB fails over to
the other node.
VM-Series Public Cloud Deployments 694 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on Alibaba
Cloud
Where Can I Use This? What Do I Need?
• Alibaba Cloud International Regions
subscription
• Alibaba Cloud Mainland China subscription
```
VM-Series License (BYOL)
```
VM-Series plugin
Panorama
Deploying the VM-Series firewall on Alibaba Cloud protects networks you create within Alibaba
Cloud. You can deploy VM-Series firewalls to secure inbound and outbound north-south traffic in
internet facing applications and hybrid cloud deployments.
Securing east-west traffic within the same VPC is not supported because Alibaba Cloud
does not support subnet routing.
The VM-Seriesfirewall on Alibaba Cloud runs on the KVM hypervisor and supports up to 8
```
network interfaces when you select an Alibaba Cloud instance with sufficient resources (see
```
```
Minimum System Requirements for the VM-Series Firewall on Alibaba Cloud).
```
The VM-Series firewall on Alibaba Cloud supports BYOL licensing and the VM-Series ELA
on Alibaba Cloud International Regions and Mainland China. PAYG licensing is not currently
supported.
In Alibaba Cloud, your VPC logically isolates your virtual network. After creating a VPC, you can
create VSwitches to further segment your virtual private network, as shown in the following
diagram. To secure inbound traffic, both DNAT and SNAT must be configured on the firewall.
695
VM-Series Firewall on Alibaba Cloud
Inbound traffic originates from a client outside of your VPC going to the VM-Series firewall
untrust interface. The firewall inspects the traffic and sends it to an application through the trust
interface. Traffic returning from the application must travel through the VM-Series firewall trust
interface, which inspects the return traffic flow and sends it out through the untrust interface.
Outbound traffic typically originates from an external application. Typically you route the internet
```
facing traffic within a VPC to a NAT gateway (with EIP attached). To do this, add a default
```
gateway route in the VPC routing table, with the VM-Series firewall IP address of the application
subnet as the next hop. Configure SNAT using the untrust interface IP to ensure traffic originating
from the internet returns through the VM-Series firewall.
Refer to Secure North-South Traffic on Alibaba Cloud for a sample configuration.
VM-Series Public Cloud Deployments 696 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on Alibaba Cloud
Minimum System Requirements for the VM-Series
Firewall on Alibaba Cloud
Where Can I Use This? What Do I Need?
• Alibaba Cloud International Regions
subscription
• Alibaba Cloud Mainland China subscription
```
VM-Series License (BYOL)
```
VM-Series plugin
Panorama
VM-Series Firewall Software Requirements
Ensure that you have the software and licenses required to complete a VM-Series deployment on
Alibaba Cloud.
• To deploy the VM-Series firewall on Alibaba Cloud, you must use a VM-Series image you
obtain from the Alibaba Marketplace. The image incorporates PAN-0S version 10.0.3 and VM-
Series plugin version 2.0.3.
• Before you deploy, choose the VM-Series ELA or BYOL license, a capacity license, and a
subscription bundle. See VM-Series Model License Types.
• You must be able to SSH into the VM-Series firewall to complete the deployment. If your OS
does not support SSH, install third-party software, such as Putty.
Alibaba Cloud Instance Type Recommendations for the VM-Series
Firewall
```
Before creating the VM-Series firewall, you must choose an Elastic Compute Service (ECS)
```
instance type that supports the minimum system requirements for your VM-Series model. Review
the instance type documentation to ensure the ECS instance type has the resources to secure
your network configuration.
The VM-Series for AliCloud deployed on g6 and g7 instances support Packet MMAP only.
VM-Series Model Elastic Compute Service Instance Type
VM-100, Software NGFW Credits ecs.g5.xlarge
ecs.g6.xlarge
ecs.g7ne.xlarge
ecs.sn2ne.xlarge
ecs.g9i instance family
ecs.g8i instance family
VM-Series Public Cloud Deployments 697 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on Alibaba Cloud
VM-Series Model Elastic Compute Service Instance Type
VM-300, Software NGFW Credits ecs.g5.xlarge
ecs.g6.2xlarge
ecs.g7ne.2xlarge
ecs.sn2ne.xlarge
ecs.g9i instance family
ecs.g8i instance family
VM-500, Software NGFW Credits ecs.g5.2xlarge
ecs.g6.2xlarge
ecs.g7ne.2xlarge
ecs.sn2ne.2xlarge
ecs.g9i instance family
ecs.g8i instance family
VM-700, Software NGFW Credits ecs.g5.4xlarge
ecs.g6.4xlarge
ecs.g7ne.4xlarge
ecs.sn2ne.4xlarge
ecs.g9i instance family
ecs.g8i instance family
Software NGFW Credits g6 Instance Family
g7ne Instance Family
ecs.g9i instance family
ecs.g8i instance family
For ecs.g9i and ecs.g8i instances, ensure that the VM-Series image must have NVMe
driver supported.
The VM-Series for AliCloud deployed on g5, g6, and g7 instances support PacketMMAP
only.
If you want to specify PacketMMAP, run the following command to disable DPDK for VM-
Series on AliCloud:
op-cmd-dpdk-pkt-io=off
VM-Series Public Cloud Deployments 698 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on Alibaba Cloud
Alibaba Cloud CLI
You will need Aliyun version 3.0.4 or higher to create a VPC and Vswitches for the VM-Series
firewall. However, you should plan your network before you start, evaluate the applications you
want to protect, and determine where you will deploy the VM-Series firewall to inspect and
secure north-south traffic.
Choose Licenses and Plan Networks
Evaluate the applications you need to protect and create networks that permit the VM-Series
firewall to inspect your inbound and outbound application traffic.
STEP 1 | Plan and design your VPC.
1. Plan networks, including CIDR Blocks for your VPCs and Vswitches.
Refer to Create a VPC and Configure Networks for a sample procedure.
2. Plan your IP addresses. If you need specific addresses or address ranges, refer to the
Elastic IP Address User Guide.
3. Plan security groups.
STEP 2 | Evaluate your applications and network configurations and calculate the firewall capacity you
need to secure your applications and networks.
STEP 3 | Obtain VM-Series firewall licenses.
```
Although you do not need a license to install the VM-Series firewall (you can activate a license
```
```
after the installation), you must choose an appropriate VM-Series model and ECS instance type
```
before deploying the firewall.
1. Choose a VM-Series model.
The VM-Series firewall supports up to 8 interfaces, provided the VM-Series
model and Alibaba Cloud instance have sufficient resources.You can use the
model
Use the VM-Series model you have chosen to choose one of the Alibaba Cloud Instance
Type Recommendations for the VM-Series Firewall.
2. Choose a VM-Series capacity license that meets your needs.
3. Purchase a BYOL subscription bundle (if you do not already have one). You receive
an auth code for your VM-Series subscription, and you must supply it during the
deployment.
STEP 4 | Plan how to configure Alibaba accounts and permissions to access the VM-Series firewall.
For a start, see the Security FAQ, and learn about Instance RAM Roles.
Prepare to Use the Aliyun Command Line Interface
This chapter focuses on the ECS Console, however, everything you do in the ECS Console can
be done from the Aliyun command line interface. The CLI is required if you want to use the VM-
Series firewall to secure load balancing on Alibaba Cloud.
Install and configure a recent version of Aliyun, the Alibaba Cloud command line interface.
VM-Series Public Cloud Deployments 699 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on Alibaba Cloud
STEP 1 | Create an AccessKey and save the Access Key ID and Secret in a secure place.
STEP 2 | Download a supported version of Aliyun from https://github.com/aliyun/aliyun-cli.
STEP 3 | Install Aliyun.
STEP 4 | Configure Aliyun.
The configuration prompts you for your Access Key and other information.
If your deployment uses a storage bucket, the region must match the region for your bucket.
aliyun configure
Configuring profile '' in '' authenticate mode...
Access Key Id [*************8rq]: *************8rq
Access Key Secret [***************************tM2]:
***************************tM2
Default Region Id [us-west-1]: us-west-1
```
Default Output Format [json]: json (Only support json))
```
Default Language [zh|en] en: en
Saving profile[] ...Done.
available regions:
...
VM-Series Public Cloud Deployments 700 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on Alibaba Cloud
Deploy the VM-Series Firewall on Alibaba Cloud
Where Can I Use This? What Do I Need?
• Alibaba Cloud International Regions
subscription
• Alibaba Cloud Mainland China subscription
```
VM-Series License (BYOL)
```
VM-Series plugin
Panorama
The VM-Series firewall assumes a minimum of three interfaces: management, untrust, and trust.
When you create an Alibaba Cloud VPC, it's logically isolated. To segment your virtual private
network into subnets you create VS.witches, each having its own CIDR block. Because the VM-
Series firewall has multiple interfaces, it can inspect traffic on all subnets.
Typically external inbound traffic encounters the VM-Series firewall untrust interface. The firewall
inspects the inbound traffic and sends it to an application through the trust interface. Return
traffic from the application goes to the firewall’s trust interface, where the firewall inspects the
return traffic and sends it out through the untrust interface.
Use the following steps to deploy the Active/Passive HA on Alibaba Cloud:
Create a VPC and Configure Networks
Use the Alibaba Cloud console to create a VPC, VS.witches, security groups, and security group
rules.
All VM-Series firewall interfaces must be assigned an IPv4 address when deployed in a
public cloud environment. IPv6 addresses are not supported.
STEP 1 | Open the VPC console and select your region from the menu. Note, the region you select
must provide one of the instance types that Palo Alto Networks supports.
STEP 2 | From the Alibaba Cloud Console homepage, select Products and Services > Networking >
Virtual Private Cloud.
STEP 3 | Create a VPC.
In this step you create a VPC and Management, Untrust, and Trust VS.witches. The ECS
console creates a VPC and a switch using the same form.
1. Select Create VPC.
Specify the VPC name, an IPv4 CIDR Block, and a description. Refer to Create a VPC.
Property Value
Name Your choice
VM-Series Public Cloud Deployments 701 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on Alibaba Cloud
Property Value
IPv4 CIDR Bock Your choice. Refer to the CIDR block FAQ.
Resource Group Your Choice.
2. Select Create VSwitch.
• Name the vSwitch Management.
• Choose the Zone, specify an IPv4 CIDR Block that is a subset of the block you
specified for the VPC, and specify a Description.
```
• At the bottom, click Add to add another vSwitch (don't click OK until you have added
```
```
all VS.witches).
```
Refer to Create a VSwitch.
3. Add the Untrust vSwitch in the same manner.
4. Add the Trust vSwitch.
5. Click OK.
View the VPC details and make any changes before you click Complete.
STEP 4 | Create security groups and security group rules.
• From the Alibaba Cloud Console homepage, select Elastic Compute Service > Networking
& Security > Security Groups.
• On the upper right, click Create Security Group.
1. Create the management security group.
Refer to Create a security group to fill out the following fields.
Property Value
Template Customize
Security Group Name Management
Security Group Type Basic
Network Type VPC
VPC Select the VPC you created earlier.
VM-Series Public Cloud Deployments 702 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on Alibaba Cloud
Property Value
Resource Group Your choice
• Complete the form and click OK.
ECS console prompts you to create rules for this security group. This task describes
some basic security group rules that allow you to bring up the VM-Series firewall. You
can create more rules to enforce your network security requirements.
2. Select Create Rules Now and create rules for HTTPS and SSH.
Select the Inbound tab, and click Add Security Group Rule.
• Create an Inbound rule to allow HTTPS in this security group. For example:
Property Value
Rule Direction Inbound
Action Allow
```
Protocol Type HTTPS (443)
```
Priority 100
Authorization Type
Authorization Object
Refer to Add security group rules.
• Click Add Security Group Rule to create an inbound rule to allow SSH on the
management interface.
Property Value
Rule Direction Inbound
Action Allow
Protocol Type Customized TCP
Port Range 1/65535
Authorization Type Refer to Add security group rules.
VM-Series Public Cloud Deployments 703 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on Alibaba Cloud
Property Value
Authorization Object
Click OK and select Back to return to the Security Groups page.
3. Select Create Security Group and create the Untrust security group.
When prompted, create a rule for the Untrust security group.
Property Value
Rule Direction Inbound
Action Allow
Protocol Type Custom TCP
Port Range 1/65535
Priority 100
Authorization Type
Authorization Object
Refer to Add security group rules.
Click OK and select Back to return to the Security Groups page.
4. Create the Trust security group.
When prompted, click Add Security Group Rule and duplicate the Untrust rule.
Continue to Create and Configure the VM-Series Firewall.
Create and Configure the VM-Series Firewall
Where Can I Use This? What Do I Need?
• Alibaba Cloud International Regions
subscription
• Alibaba Cloud Mainland China subscription
```
VM-Series License (BYOL)
```
VM-Series plugin
Panorama
This task uses the ECS console to create a VM-Series firewall instance with a minimum of three
```
interfaces: management, untrust, and trust. An ECS instance supports a single NIC by default, and
```
```
automatically attaches an Elastic Network Interface (ENI) to it. To support the VM-Series firewall,
```
```
you must separately create the Untrust, and Trust Elastic Network Interfaces (ENIs) and attach
```
them to your instance.
STEP 1 | From the Alibaba Cloud console homepage, select Elastic Compute Service > Instances &
Images > Instances, and click Create Instance on the upper right.
VM-Series Public Cloud Deployments 704 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on Alibaba Cloud
STEP 2 | Select Custom Launch.
STEP 3 | Click Basic Configurations.
1. Fill in the following values. For example:
Property Value
Billing Method Subscription.
Region Your choice. You can also select a zone. The region you select
must provide one of the required instance types.
Instance Type One of the types in Alibaba Cloud Instance Type
Recommendations for the VM-Series Firewall. You can use Type-
based Selection to search for the instance type.
Image Select Marketplace Image and search for the Alibaba Marketplace
for VM-Series. The image combines the OS and the VM-Series
firewall.
Storage Choose a disk type and specify 60 GB.
Snapshot Your choice.
VM-Series Public Cloud Deployments 705 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on Alibaba Cloud
Property Value
Duration Your choice.
2. Select Next: Networking.
STEP 4 | On the Networking page, supply the following values.
1. Network (select VPC).
• Choose the VPC you created in Create a VPC and Configure Networks.
• Choose the Management vSwitch.
2. Public IP address.
If you don't have a public IP address, enable Assign Public IP address and the system will
allocate one. If you must use a specific IP address, or an address in a specific range, you
can request a custom IP address. Refer to the Elastic IP Address User Guide.
3. Security Group.
Select the Management security group.
4. Elastic Network Interface.
The management interface is already attached to eth0.
5. Select Next: System Configurations.
VM-Series Public Cloud Deployments 706 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on Alibaba Cloud
STEP 5 | On the System Configurations page, fill in the following values.
1. Logon Credentials: Select Key Pair.
Password authentication isn't supported.
2. Name the VM-Series firewall instance and supply a hostname.
Make any corrections.
Select Preview to view your settings thus far.
3. Following Advanced (based or instance RAM roles or cloud-init) click Show.
• The RAM role is optional.
• In the User Data field, enter basic bootstrap information as key-value pairs separated
by newlines. See Enter a Basic Configuration as User Data. For example, enter the
following in the User Data field.
```
type=dhcp-client
```
```
hostname=Ca-FW-DC1
```
vm-auth-key=7550362253****
panorama-server=10.*.*.20
panorama-server-2=10.*.*.21
```
tplname=FINANCE_TG4
```
```
dgname=finance_dg
```
op-cmd-dpdk-pkt-io=on
dhcp-send-hostname=yes
dhcp-send-client-id=yes
dhcp-accept-server-hostname=yes
dhcp-accept-server-domain=yes
```
authcodes=I7115398
```
vm-series-auto-registration-pin-id=abcdefgh1234****
vm-series-auto-registration-pin-value=zyxwvut-0987****
```
op-command-modes (mgmt-interface-swap and jumbo frame) are not
```
supported for Alibaba Cloud.
op-cmd-dpdk-pkt-io=on supports DPDK. If you want to specify
PacketMMAP, specify op-cmd-dpdk-pkt-io=off
Grouping is Optional. Select Preview to view the configuration before ordering.
STEP 6 | View the terms of service, and select Create Order to create the VM-Series firewall instance.
View the purchase order and select Subscribe.
STEP 7 | From the console homepage, choose > Elastic Compute Service > Networks and Security >
ENIs and select Create ENI in the top-right corner. Create Elastic Network Interfaces for the
Untrust and Trust interfaces.
1. Create the Untrust ENI.
In the Actions column, select Bind to Instance and select the instance you created.
2. Create the Trust ENI and bind it to the instance.
VM-Series Public Cloud Deployments 707 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on Alibaba Cloud
```
STEP 8 | Allocate Elastic IP (EIP) addresses.
```
Allocate EIP addresses for the VM-Series firewall management interface and the Untrust
network interface. In this example, the Trust interface isn't exposed to the internet, so you
don't need a third IP address.
If you already have two EIPs, go to the next step.
1. Associate an EIP with the VM-Series firewall management interface .
2. Associate an EIP with the VM-Series firewall Untrust network interface.
The second interface you attach is assigned to network interface 1 on the VM-Series
firewall.
STEP 9 | Restart your instance to attach the new network interfaces.
On the Instances list, select your instance, select Manage, and select Restart on the upper
right.
STEP 10 | SSH in to the VM-Series firewall with the security key and set the admin password:
developer1$ ssh -i dev1-vpc1.pem admin@18.***.145.153
Welcome admin.
admin> configure
Entering configuration mode
[edit]
admin# set mgt-config users admin password
Enter password:<password>
Confirm password:<password>
[edit]
admin# commit
STEP 11 | Access the VM-Series firewall web interface.
Open a web browser and enter the EIP for the management interface.
Secure North-South Traffic on Alibaba Cloud
Where Can I Use This? What Do I Need?
• Alibaba Cloud International Regions
subscription
• Alibaba Cloud Mainland China subscription
```
VM-Series License (BYOL)
```
VM-Series plugin
Panorama
After creating a VPC, you can create vSwitches to segment your virtual private network into
```
subnets. This sample features a VPC with CIDR 192.168.0.0/16; you can enter your own values.
```
Four vSwitches create four subnets.
VM-Series Public Cloud Deployments 708 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on Alibaba Cloud
vSwitch Name Interface Sample CIDR
mgmt eth0 192.168.0.0/24
untrust eth1 192.168.1.0/24
web eth2 192.168.2.0/24
db eth3 192.168.3.0/24
In the following diagram, the VM-Series firewall connects to two trusted subnets, web and db.
Inbound traffic is initiated when an external client accesses the VM-Series firewall’s Untrust
interface. The firewall inspects the traffic and sends it to an application. For example, the firewall
sends traffic to a Web server through the Trust interface. The traffic returning from the Web
server must hit the VM-Series firewall’s Trust interface. The firewall inspects the return traffic
flow, and sends it out through the Untrust interface.
To secure inbound traffic, both DNAT and SNAT must be configured on the firewall.
STEP 1 | Create NAT rules for inbound traffic.
Here’s a sample of the NAT rules for inbound traffic protection.
<nat>
<rules>
<entry name="inbound_web">
<source-translation>
<dynamic-ip-and-port>
<interface-address>
<interface>ethernet1/2</interface>
</interface-address>
</dynamic-ip-and-port>
</source-translation>
<destination-translation>
VM-Series Public Cloud Deployments 709 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on Alibaba Cloud
<translated-address>web_server</translated-
address>
</destination-translation>
<to>
<member>untrust</member>
</to>
<from>
<member>any</member>
</from>
<source>
<member>any</member>
</source>
<destination>
<member>fw_untrust</member>
</destination>
<service>any</service>
<to-interface>ethernet1/1</to-interface>
</entry>
</rules>
</nat>
<address>
<entry name="fw_untrust">
<ip-netmask>192.168.1.4</ip-netmask>
</entry>
<entry name="fw_trust">
<ip-netmask>192.168.2.201</ip-netmask>
</entry>
<entry name="web_server">
<ip-netmask>192.168.2.203</ip-netmask>
</entry>
</address>
STEP 2 | Secure outbound traffic.
As shown in the diagram above, an application initiates the outbound traffic. For example, a
web server must run yum install to update rpm packages. Typically the internet facing
VM-Series Public Cloud Deployments 710 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on Alibaba Cloud
```
traffic within a VPC is routed to a NAT gateway (with an EIP attached). To secure outbound
```
traffic, you must force outbound traffic to go through the VM-Series firewall.
1. Add a default gateway route in the VPC routing table with firewall IP in the subnet of the
web server as the next hop.
2. View your entry in the route table.
3. Configure SNAT rules using the Untrust interface IP to ensure traffic returning from the
internet goes through the VM-Series firewall.
VM-Series Public Cloud Deployments 711 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on Alibaba Cloud
Here's a sample SNAT configuration.
<nat>
<rules>
<entry name="outbound_web">
<source-translation>
<dynamic-ip-and-port>
<interface-address>
<interface>ethernet1/1</interface>
</interface-address>
</dynamic-ip-and-port>
</source-translation>
<to>
<member>untrust</member>
</to>
<from>
<member>trust</member>
</from>
<source>
<member>any</member>
</source>
<destination>
<member>any</member>
</destination>
<service>any</service>
<to-interface>any</to-interface>
</entry>
</rules>
</nat>
Configure Load Balancing on Alibaba Cloud
Where Can I Use This? What Do I Need?
• Alibaba Cloud International Regions
subscription
• Alibaba Cloud Mainland China subscription
```
VM-Series License (BYOL)
```
VM-Series plugin
Panorama
On Alibaba Cloud, you can deploy the VM-Series firewall in a load balancer sandwich
configuration where the firewall is deployed between a public network and a private network, as
shown below.
VM-Series Public Cloud Deployments 712 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on Alibaba Cloud
In Create a VPC and Configure Networks, you created Untrust and Trust ENIs and attached them
to the VM-Series firewall instance as secondary ENIs.
```
When you use the console to add multiple backend servers to Alibaba Server Load Balancer (SLB),
```
the SLB sends traffic to the primary ENI of the next-hop backend servers. Because the primary
```
ENI is the management interface, traffic must go to the Untrust interface (a secondary ENI) for
```
inspection.
To ensure that internet traffic goes to dataplane interfaces rather than the management interface,
use the Alibaba CLI to attach the VM-Series firewall untrust ENIs to your SLB instance.
You must install the Aliyun command line interface to use the following CLI commands.
STEP 1 | Create the public and private VPCs for a load balancer sandwich configuration, and deploy
the VM-Series firewalls.
The remaining steps are sample CLI commands you can adapt to your environment.
STEP 2 | Create the load balancer.
slb CreateLoadBalancer --RegionId us-west-1 --LoadBalancerName wli-
slb
--VpcId vpc-rj91ry36ghwgc8cf2fr7z --LoadBalancerSpec slb.s1.small
--AddressType internet --MasterZoneId us-west-1a
--SlaveZoneId us-west-1b
```
{
```
"NetworkType": "classic",
"LoadBalancerName": "**********",
"Address": "***********,
"ResourceGroupId": "rg-************ofi",
VM-Series Public Cloud Deployments 713 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on Alibaba Cloud
"RequestId": "0B8BA2AA-E837-****-****-B82A8A1D5FBB",
"AddressIPVersion": "ipv4",
"LoadBalancerId": "lb-******************mvz",
"VSwitchId": "",
"VpcId": "vpc-*****************r7z"
```
}
```
STEP 3 | Add backend servers.
Use the CLI to add interfaces one at a time. The order in which you add the interfaces
determines which NIC receives the interface.
aliyun slb AddBackendServers --LoadBalancerId lb-
******************mvz
--BackendServers
'[
```
{
```
"ServerId":"eni-******************bzw",
"Type":"eni","Weight":"100"
```
}
```
]'
STEP 4 | Create an HTTP Listener that performs a health check.
aliyun slb CreateLoadBalancerHTTPListener
--LoadBalancerId lb-******************mvz
--ListenerPort 80 --StickySession on
--HealthCheck on --HealthCheckURI '/'
VM-Series Public Cloud Deployments 714 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on Alibaba Cloud
Set up Active/Passive HA on Alibaba Cloud
Where Can I Use This? What Do I Need?
• Alibaba Cloud International Regions
subscription
• Alibaba Cloud Mainland China subscription
```
VM-Series License (BYOL)
```
VM-Series plugin
Panorama
The VM-Series firewall on Alibaba Cloud now supports active/passive HA deployments using a
new feature of Alibaba cloud called HAVIP.
The HAVIP listens to the ARP/GARP messages sent by the VM-Series firewalls to determine
which network interfaces belong to the active VM-Series firewall, and then forward traffic to
those interfaces.
The HAVIP deployment architecture consists of two HAVIP interfaces and two VM-Series
firewalls that are configured in active/standby HA mode.
```
One of the HAVIPs is configured with a public IP address (external HAVIP). The Untrust interface
```
```
of each VM-Series firewall is bound to this external HAVIP. The other HAVIP (internal HAVIP)
```
does not have an attached public IP address. The Trust interface of each VM-Series firewall is
bound to the internal HAVIP.
VM-Series Public Cloud Deployments 715 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on Alibaba Cloud
In this example, the External HAVIP is in the same subnet as the Untrust interfaces, while the
Internal HAVIP is in the same subnet as the Trust interfaces.
• The HAVIP address must be in the same subnet as the network interfaces that are
bound to it.
• Subnets in Alibaba Cloud can't span multiple zones, so this solution will only work if
both VM-Series firewalls are in the same availability zone.
VM-Series Public Cloud Deployments 716 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on Alibaba Cloud
Create HAVIP
STEP 1 | Click VPC > HAVIP > Create HAVIP on your Alibaba Cloud console.
STEP 2 | Choose the VPC and vSwitch.
VM-Series Public Cloud Deployments 717 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on Alibaba Cloud
STEP 3 | Provide a private IP address for the HAVIP and click OK.
VM-Series Public Cloud Deployments 718 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on Alibaba Cloud
VM-Series Public Cloud Deployments 719 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on Alibaba Cloud
```
Bind an Elastic IP(EIP) Address
```
STEP 1 | Click the HAVIP you created to enter its configuration.
VM-Series Public Cloud Deployments 720 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on Alibaba Cloud
```
STEP 2 | Create an Elastic IP Address (EIP) and click Bind, to bind the EIP to the HAVIP.
```
VM-Series Public Cloud Deployments 721 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on Alibaba Cloud
VM-Series Public Cloud Deployments 722 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on Alibaba Cloud
Bind an ECS Instance
To bind with an instance, use the primary network interface of the instance. For VM-Series
firewalls, the primary network interface is the management interface.
To bind the Untrust interfaces of the VM-Series firewalls to the HAVIP:
STEP 1 | Click the Bind button under ECS Instances.
STEP 2 | Choose ENI as the resource type, and then choose the Instance and ENI to bind to the
HAVIP.
VM-Series Public Cloud Deployments 723 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on Alibaba Cloud
STEP 3 | Repeat the same procedure for the other Untrust interface.
VM-Series Public Cloud Deployments 724 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on Alibaba Cloud
Once the EIP and both Untrust interfaces are bound to the HAVIP, you may find them in the
HAVIP configuration page.
VM-Series Public Cloud Deployments 725 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on Alibaba Cloud
STEP 4 | Repeat the same procedure to create the Internal HAVIP. For the Internal HAVIP, there is no
need to bind any EIP to it. The configuration for the Internal HAVIP should be similar to the
image below:
Configure Route Table
Traffic from the servers should be routed to the Internal HAVIP. To achieve this, a static route is
configured in the route table associated with the server subnet.
Click VPC > Route Tables.
After creating the route table, add a custom route entry to point the default route to the Internal
HAVIP, and associate this route table with the server vSwitch.
VM-Series Public Cloud Deployments 726 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on Alibaba Cloud
Configure the VM-Series Firewall
The VM-Series firewalls are configured in active/passive HA mode with configuration sync
enabled.
STEP 1 | Configure the Untrust and Trust interfaces with static IPs. The Untrust interface is
configured with the private IP address of the External HAVIP, while the Trust interface
is configured with the private IP address of the Internal HAVIP. As configuration sync is
VM-Series Public Cloud Deployments 727 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on Alibaba Cloud
enabled, when a failover occurs, the newly active VM-Series firewall will use the same set of
IP addresses for its Untrust and Trust interfaces.
STEP 2 | Ensure that the route table in the VM-Series firewall includes the default route via the
Untrust interface, and a route to the server subnet via the Trust interface.
VM-Series Public Cloud Deployments 728 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on Alibaba Cloud
STEP 3 | Configure the NAT rules for Inbound and Outbound traffic.
For Inbound traffic, the NAT rule must have a destination address match on the private
IP address of the External HAVIP. This destination address is translated to the web server
address by the NAT rule.
For Outbound traffic, the SNAT rule will match the source addresses of the servers. The
source address will then be SNAT to the private IP address of the External HAVIP. The
External HAVIP in turn SNATs the traffic to the public IP address of the External HAVIP.
Test the Traffic
Testing Inbound Traffic
The web server is accessed via the public IP address of the External HAVIP. In the following
diagrams, observe that the client can successfully access the web server, as well as the public IP
address of the client.
VM-Series Public Cloud Deployments 729 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on Alibaba Cloud
VM-Series Public Cloud Deployments 730 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on Alibaba Cloud
Testing Outbound Traffic
Accessing the internet from the server, the source IP address used is detected to be that of the
External HAVIP.
VM-Series Public Cloud Deployments 731 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on Alibaba Cloud
Failover Testing
Start a ping test on the server. The active VM-Series firewall gets suspended and the passive VM-
Series firewall will then become active. From the ping test, there could be around 11 ping drops
before the traffic resumes. So, the failover time is around 11 seconds.
VM-Series Public Cloud Deployments 732 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on Alibaba Cloud
Two VM-Series firewalls can be deployed on Alibaba Cloud in active/passive HA mode with
Alibaba Cloud HAVIP to provide high availability. This provides session and configuration sync
between the two VM-Series firewalls. However, this only works in a single availability zone.
If an increase in capacity is required, the VM-Series firewalls need to be scaled-up, for
example VM-300 → VM-500.
```
Virtual CPU (vCPU) Instance Types
```
The VM-Series firewalls used in the testing have four network interfaces: Management, Untrust,
Trust, and HA2. On most Alibaba Cloud instance types, the four vCPU instance types provide
VM-Series Public Cloud Deployments 733 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on Alibaba Cloud
three network interfaces. The eight vCPU instance types and above provide four or more network
interfaces.
If four vCPU instance types need to be used, the VM-Series firewalls need to be deployed in one-
arm mode as there can only be three network interfaces attached to each firewall. Inbound and
outbound traffic will traverse the same data interface.
VM-Series Public Cloud Deployments 734 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on Alibaba Cloud
VM-Series Integration with an Alibaba Gateway Load
Balancer
Where Can I Use This? What Do I Need?
• Alibaba Cloud International Regions
subscription
• Alibaba Cloud Mainland China subscription
```
VM-Series License (BYOL)
```
VM-Series plugin
Panorama
```
The Alibaba Gateway Load Balancer (GWLB) operates at Layer 3 (the network layer) of the OSI
```
model, acting as a transparent load balancer that distributes traffic to various backend servers.
It listens for traffic on all ports of a specified IP address, forwarding it to backend server groups
using the Geneve protocol.
Backend servers capable of supporting the Geneve protocol can be grouped logically. Each
server group contains one or more backend servers responsible for processing requests routed
```
by the GWLB. A GWLB Endpoint(GWLBe) serves as the consumer-side connection within a
```
```
Virtual Private Cloud (VPC), allowing VPC traffic to be seamlessly redirected to the GWLB and
```
subsequently to appliances like firewalls.
VM-Series integration with Alibaba GWLB only supports the IPv4 protocol version.
The image below describes the integration of Alibaba GWLB with VM-Series. You attach a
centralized security VPC to your transit gateway. The centralized security VPC includes a GWLB
to scale and load-balance traffic across the stack of VM-Series firewalls.
VM-Series Public Cloud Deployments 735 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on Alibaba Cloud
For outbound traffic, the application server subnet's route table directs traffic to the GWLB
endpoint. From there, the GWLB endpoint sends the traffic to the GWLB, which then forwards
it to the firewalls. The firewalls conduct a security inspection of the traffic and return it to
the GWLB. The GWLB then routes the traffic back to the GWLB endpoint via the connection
established through the private link service. Traffic is forwarded to the NAT gateway based on
the route table for the GWLB endpoint subnet. The gateway performs a Source Network Address
```
Translation (SNAT) and subsequently routes the traffic to the Internet client.
```
For inbound traffic, the NAT-IPv4 gateway first receives business traffic from the Internet
```
and performs a Destination Network Address Translation (DNAT). It then sends this traffic to
```
```
the Gateway Load Balancer (GWLB) endpoint, guided by its route table. The GWLB endpoint
```
```
subsequently forwards the traffic to the GWLB, which then directs it to the Firewalls (FWs).
```
The FWs conduct security checks on the traffic and return it to the GWLB. The GWLB, in
turn, forwards the traffic back to the GWLB endpoint via a connection established through the
PrivateLink service. Finally, the traffic is sent to the application server, based on the route table
configured for the GWLB endpoint subnet.
Flow of Traffic
• Business VPC to GWLBe: Traffic originating from an Business VPC, destined for external
networks or other internal segments requiring security inspection, is first routed to a Gateway
Load Balancer Endpoint.
• GWLBe to GWLB: The GWLBe transparently forwards these packets to the Gateway Load
Balancer.
• GWLB Encapsulation and Distribution: The GWLB encapsulates the traffic using the GENEVE
protocol, adding metadata, and then distributes it to the available firewalls in the security VPC.
VM-Series Public Cloud Deployments 736 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on Alibaba Cloud
• Security Inspection by Firewalls: The VM-Series firewalls perform comprehensive security
inspection, applying configured policies for threat detection, intrusion prevention, URL filtering,
and more.
• Return to GWLB: After inspection, the clean traffic is sent back to the GWLB.
• GWLB to GWLBe to Business VPC: The GWLB then directs the traffic back through the
GWLBe to the Business VPC, preserving the original IP and flow.
Integrate VM-Series Firewall with Alibaba Gateway Load Balancer
Where Can I Use This? What Do I Need?
• Alibaba Cloud International Regions
subscription
• Alibaba Cloud Mainland China subscription
```
VM-Series License (BYOL)
```
VM-Series plugin
Panorama
The following are the pre-requisites to integrate your VM-Series firewall with an Alibaba GWLB:
• Create two VPCs—one business VPC and one security VPC.
VM-Series Public Cloud Deployments 737 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on Alibaba Cloud
• Create two subnets for each firewall in the security VPC—one for management and one for
data.
VM-Series Public Cloud Deployments 738 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on Alibaba Cloud
• Create a GWLB subnet as a part of the security VPC.
VM-Series Public Cloud Deployments 739 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on Alibaba Cloud
• Create two security groups—one for firewall management and one for data. The management
subnet security groups must allow https and ssh for management access.
VM-Series Public Cloud Deployments 740 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on Alibaba Cloud
```
• Ensure that the security group(s) in your data VPC allows GENEVE-encapsulated packets (UDP
```
```
port 6081).
```
• Enable appliance mode on security VPC attachment, if your deployment includes a transit
gateway and traffic that will move between VPCs.
Complete the following procedure to manually integrate your VM-Series firewall with an Alibaba
GWLB.
VM-Series Public Cloud Deployments 741 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on Alibaba Cloud
STEP 1 | On the PA-VM, configure the following:
1. Configure ethernet1/1 for DHCP, enabling interface management to “allow all” and map
it to the untrust zone.
2. Configure a security policy to permit health checks, specifying source IP as GWLB
instance IP.
3. Configure the security policy to allow-all.
4. Set Firewall Interface MTU connected to GWLB to 1432. GENEVE adds 64-68 bytes
of overhead to the original packet. So, the effective MTU available to your firewall is:
```
[ 1500 (VPC MTU) - 64 (GENEVE overhead) = 1436 bytes ].
```
set network interface ethernet ethernet1/1 layer3 mtu 1432
5. Disable DPDK on the firewall.
set system setting dpdk-pkt-io off
6. Enable Geneve Inspection on the firewall.
request plugins vm_series geneve-inspect enable yes
7. Enable the user identification on the zone.
VM-Series Public Cloud Deployments 742 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on Alibaba Cloud
set network zone Trust user-identification enable yes
STEP 2 | To use the GWLB service, you must first create a GWLB instance. Create a GWLB instance
and attach two data vSwitches to it, ensuring each vSwitch is in a different zone.
1. Log on to theGWLB console and select the region where the GWLB instance is
deployed.
2. Click Create GWLB on the Instances page.
3. Configure the parameters on the Gateway Load Balancer - Alibaba Cloud International
Site. The following table describes only the key parameters. Use the default values for
other parameters. For more information about the parameters, seeCreate and manage a
GWLB instance.
Parameter Description
Instance Name Specify an instance name.
VPC Select the security VPC.
Region and Zone Select the region in which you want to create the
GWLB instance.
Zone Select one or more zones.
IP version Select IPv4 as the IP version.
Service-linked Role The first time you create a GWLB instance,
click Create Service-linked Role to create the
AliyunServiceRoleForGwlb service-linked role.
This parameter is displayed only the first
time you create a GWLB instance.
4. Click OK.
5. Return to the Instances page and select the region where the GWLB instance is
deployed to view the GWLB instance.
VM-Series Public Cloud Deployments 743 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on Alibaba Cloud
STEP 3 | Create a backend server group by adding the secondary data interfaces of both firewalls, in
advanced mode.
1. Click Create Server Group on the Server Groups page,
2. Configure the parameters in the Create Server Group dialog box, and click Create.
The following table describes only the key parameters. Use the default values for other
parameters. For more information about the parameters, see Create and manage a
server group.
Parameter Description
Server Group Type Select a server group type. For example, Server is
selected.
Server Group Name Specify a server group name.
VPC Select the security VPC in which the ECS instances are
deployed.
Select the VPC in which the GWLB
instance is deployed.
Scheduling Algorithm Select a scheduling algorithm. For example, 5-tuple
Hashing.
Health Check Method Select a health check method or disable health checks.
For example, HTTP.
Health Check Path will be /php/login.php
Health check status code will be http_2xx.
VM-Series Public Cloud Deployments 744 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on Alibaba Cloud
Parameter Description
Health Check Port Specify a health check port. For example, 80.
3. Click Add Backend Server, in the The server group is created message.
4. Click Add Backend Server, on the Backend Servers tab of the page that appears
subsequently.
5. Append and toggle Advanced Mode to see the secondary NICs of the firewall and set
the Server Type in the Add Backend Server panel. You may choose to set Server Type
to ECS/ENI.
6. Select FW1 and FW2 data interface and click Next.
VM-Series Public Cloud Deployments 745 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on Alibaba Cloud
STEP 4 | Configure a listener and add the server group you created in the previous step, as backend
server.
1. Click GWLB > Instances and click the instance ID.
2. Click the Listeners tab and click Create IP Listener.
3. Set Server Group Type in Select Server Group, and select the server group that is
created.
4. Click OK on the backend server list page.
STEP 5 | Configure an endpoint service
1. Log on to the VPC console.
2. Click Create Endpoint Service.
3. Configure the parameters on the Create Endpoint Service page and click OK. The
following table describes only the parameters that are relevant to this topic.
Parameter Description
```
Region Specify the region. For example, China (Ulanqab).
```
Service Resource Type Select the type of the service resource that you want
to add to the endpoint service. For example, GWLB.
Select Service Resource Select the zone where the service resource is available
and select the service resource. For example, select
Ulanqab Zone B and select the GWLB instance
created in Step 2.
VM-Series Public Cloud Deployments 746 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on Alibaba Cloud
Parameter Description
Network Type Select the network type. For example, IPv4.
Automatically Accept Endpoint
Connections
Specify whether the endpoint service automatically
accepts connection requests from endpoints.
If you select Yes, after an endpoint
is created, the endpoint service
automatically accepts connection requests
from the endpoint.
Service Payer Specify the service payer. For example, Service
Consumer.
Click OK.
4. Add the GWLB service resource for each zone by clicking "Add Service Resource." For
example, if a GWLB instance spans two zones, add it as a service resource for the first
zone, and then repeat the process for the second zone.
VM-Series Public Cloud Deployments 747 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on Alibaba Cloud
STEP 6 | Configure a GWLB endpoint.
1. Log on to the Endpoint console.
2. Click Create Endpoint on the Interface Endpoint tab of the Endpoints page.
3. Configure the parameters on the Create Endpoint page, and click OK. The following
table describes only the parameters that are relevant to this topic:
Parameter Description
```
Region Specify the region. For example, China (Ulanqab).
```
Endpoint Name Specify an endpoint name.
Endpoint Type Select an endpoint type. For example, Gateway
Endpoint.
Endpoint Service Select an endpoint service. For example, Select Service
as in Configure an endpoint service.
VPC Select the VPC in which the endpoint is deployed. For
example, you may choose to select the business VPCs.
Zone and vSwitch Select the zone where the service resource of the
endpoint service is deployed and select the vSwitch
in this zone. The system automatically creates an
```
endpoint elastic network interface (ENI) in the
```
vSwitch. For example, you may choose to select
Ulanqab Zone B and the vSwitch of the GWLB
endpoint subnet.
VM-Series Public Cloud Deployments 748 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on Alibaba Cloud
Parameter Description
Network Type Select the network type. For example, IPv4.
4. Click the System Route tab on the Route Entry List tab of the Route Table Details page,
and view the routes that are created by the system. Routes destined for the CIDR block
of a vSwitch of the VPC to which the route table belongs are automatically added by
VM-Series Public Cloud Deployments 749 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on Alibaba Cloud
the system to a custom route table. These routes are used for communication between
cloud resources within the vSwitch.
5. Modify system routes: Click Route Entry List > System Route, find the system route
that you want to modify and click Modify in the Actions column. In the Modify Route
VM-Series Public Cloud Deployments 750 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on Alibaba Cloud
Entry dialog box, configure the parameters and click OK. Then this route appears on the
Custom Route tab.
The parameters are described below:
Parameter Description
Destination CIDR Block Displays the destination CIDR block of traffic.
Destination CIDR Block cannot be modified.
Name Specify a new route name.
VM-Series Public Cloud Deployments 751 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on Alibaba Cloud
Parameter Description
Next Hop Select the type of the next hop. For example, GWLB
Endpoint.
GWLB Endpoint Select an endpoint service. For example, Select Service
as in Configure an endpoint service.
VPC Select the GWLB endpoint that you created in
Configure a GWLB endpoint.
For more information, see Alibaba Cloud documentation.
VM-Series Public Cloud Deployments 752 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on Tencent
Cloud China
Where Can I Use This? What Do I Need?
```
• Tencent Cloud China VM-Series License (BYOL)
```
VM-Series plugin
Panorama
Deploy the VM-Series firewall to secure your inbound and outbound north-south traffic in
Tencent cloud.
The VM-Series firewall on Tencent Cloud only supports inbound and outbound north-
south traffic protection, not east-west traffic.
The VM-Series firewall on Tencent Cloud supports BYOL and PAYG licensing.
753
VM-Series Firewall on Tencent Cloud China
VM-Series Public Cloud Deployments 754 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on Tencent Cloud China
Minimum System Requirements for VM-Series on
Tencent Cloud
On Tencent Cloud, you can deploy the VM-Series firewall using the PA-VM qcow2 images.
Ensure that your Panorama is of version 10.2.1 or above.
VM-Series Public Cloud Deployments 755 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on Tencent Cloud China
License the VM-Series Firewall on Tencent Cloud
The VM-Series firewall on Tencent cloud supports BYOL and PAYG licenses. For more
information on VM-Series firewall licensing and licensing types, see License Types.
Register the VM-Series firewall performing the steps described in Initiate VM-Series Firewall
Registration procedure.
After the firewall registration, log in to the firewall and select Device > Licenses.
License keys must be installed through the web interface. The firewall does not support
license key installation through SCP or FTP.
• Click Manually Upload License.
• Confirm that the Dashboard displays a valid serial number and that the PA-VM license displays
in the Device > Licenses tab.
VM-Series Public Cloud Deployments 756 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on Tencent Cloud China
Deploying the VM-Series Firewall on Tencent Cloud
Where Can I Use This? What Do I Need?
```
• Tencent Cloud China VM-Series License (BYOL)
```
VM-Series plugin
Panorama
Following are the steps to deploy the VM-Series firewall on the Tencent cloud:
VM-Series Public Cloud Deployments 757 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on Tencent Cloud China
STEP 1 | Begin with creating a VPC and Subnets on Tencent Cloud. Perform the following steps:
By default, the Tencent cloud webpage is in Chinese language. Translate the webpage
to English, and then proceed with the deployment procedure.
1. Go to the Tencent console and click Log In.
2. Click Sub-user.
VM-Series Public Cloud Deployments 758 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on Tencent Cloud China
VM-Series Public Cloud Deployments 759 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on Tencent Cloud China
3. Enter your Sub-User login credentials.
4. Click Login.
5. Click Console.
VM-Series Public Cloud Deployments 760 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on Tencent Cloud China
VM-Series Public Cloud Deployments 761 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on Tencent Cloud China
6. Go to Private Networks > New.
7. In the Private Network > Information section, enter the VPC name and CIDR details.
VM-Series Public Cloud Deployments 762 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on Tencent Cloud China
VM-Series Public Cloud Deployments 763 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on Tencent Cloud China
8. In the Initial Subnet Information section, enter the subnet name and IP address details.
9. Click Save.
To create Subnets, perform the following steps:
1. In the Private Network menu, click subnets.
2. Click New.
3. Select your VPC.
4. Enter the subnet Name and Availability zone.
5. Click Save.
You must create at least 3 subnets namely management, untrust, and trust subnets for
your VPC.
VM-Series Public Cloud Deployments 764 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on Tencent Cloud China
STEP 2 | Upload the PA-VM qcow2 image file on the Tencent Cloud.
You must have Panorama version 10.2.1 or above.
1. In your Tencent console, click Object Storage.
2. Go to Bucket List > Upload Files > Select Files.
3. Select the image file from your local machine, and then click Upload.
VM-Series Public Cloud Deployments 765 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on Tencent Cloud China
STEP 3 | Import the image file on the cloud server.
1. Go to the Cloud server > Mirror > Import an image.
VM-Series Public Cloud Deployments 766 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on Tencent Cloud China
VM-Series Public Cloud Deployments 767 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on Tencent Cloud China
2. Select the I have made the above preparations checkbox.
3. Click Next Step.
4. Enter the Region.
VM-Series Public Cloud Deployments 768 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on Tencent Cloud China
VM-Series Public Cloud Deployments 769 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on Tencent Cloud China
5. Enter the Name and Image file URL.
To copy the temporary link to the image file:
• Go to your image file, click Details.
• Copy the temporary link shown on the screen.
6. Select Other Linux as the Operating System option.
7. Select 64-bit for System Structure.
8. Select the Enable Forced Import checkbox.
9. Click Next Step.
10.Click Sure.
VM-Series Public Cloud Deployments 770 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on Tencent Cloud China
STEP 4 | Create a VM-Series firewall instance.
1. Go to your VM-Series image file and click Create Instance.
2. Click Sure.
3. In the Basic Configuration section, select your Billing Model and Region.
VM-Series Public Cloud Deployments 771 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on Tencent Cloud China
VM-Series Public Cloud Deployments 772 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on Tencent Cloud China
4. Select your instance, and click Next Step.
5. In the Network and Bandwidth section, select your VPC and subnet.
6. (Optional) Select the Manually assigning IP address checkbox to manually allocate the IP
address out of the subnet.
7. Select Assign the Independent IP checkbox to obtain a public interface for your firewall.
8. Select your Security Group.
9. Enter the Instance Name.
10.Click Associate the Key and select your key option.
You can either create a new key or import an existing public key.
11.Click Save.
12.Click Next.
13.Select the Terms and conditions checkbox.
14.Click Activate.
The VM-Series firewall now gets deployed. Go to Cloud Server > Examples to see the list of
VM-Series firewall instances deployed.
VM-Series Public Cloud Deployments 773 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on Tencent Cloud China
STEP 5 | Create Elastic Network Interfaces for your VM-Series Firewall.
1. In the Tencent console, go to Cloud Server > Examples.
2. Select your VM-Instance.
3. Click the Elastic Network Interface tab.
4. Click Bind an ENI.
```
Note: By default, a VM-Series instance deployed will have one management
```
interface.
5. Click Create a New Elastic Network Card.
VM-Series Public Cloud Deployments 774 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on Tencent Cloud China
6. Enter the name and subnet for your ENI.
7. Click Save.
VM-Series Public Cloud Deployments 775 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on Tencent Cloud China
• Ensure that you create an elastic card each for an untrust and trust interface.
• Ensure that you bind an EIP for your untrust interface. Go to your untrust interface,
go to IPV4 address management tab, click Bind an ENIP, and then Create a new
one.
• Ensure that you bind an EIP on your untrust interface.
• Go to your untrust interface, and then click IPV4 Address Management tab.
• Click Binding.
• Click Create a New one and then create a new EIP and bind it to the untrust
interface.
VM-Series Public Cloud Deployments 776 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on Tencent Cloud China
STEP 6 | Configure the VM-Series firewall.
1. Log in to your VM-Series firewall web interface.
2. License the VM-Series Firewall.
3. Go to Networks > Zones.
4. Click Add and create a trust zone.
Repeat the above step to create an untrust zone.
5. Go to Networks > Interfaces and configure the Layer 3 interfaces for ethernet 1/1 and
ethernet 1/2.
6. Commit your changes.
Verify that the firewall is passing traffic. Select Monitor > Session Browser and verify that
you are seeing new sessions.
VM-Series Public Cloud Deployments 777 ©2026 Palo Alto Networks, Inc.
VM-Series Firewall on Tencent Cloud China
VM-Series Public Cloud Deployments 778 ©2026 Palo Alto Networks, Inc.