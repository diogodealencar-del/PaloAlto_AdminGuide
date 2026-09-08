

## HOW TO CONFIGURE GLOBALPROTECT VPN
## USING AN EXTERNAL ROOT CA

## SS L  VP N
## CERT I FI CAT E  M ANA GE M ENT
## GLO BA LPR OT ECT


## Symptom
This document describes the steps to configure GlobalProtect VPN using an External Root CA such as Windows Server 2012 w/
AD Certificate Services running on it.

If a third-party certificate authority is being used (such as GlobalSign, GoDaddy, DigiCert, Symantec, etc.), the same steps below
can be followed to deploy GlobalProtect, but instead of each Windows Server step below (such as in step 2 and step 4), use the
third-party certificate vendor for each of those steps instead.

## Environment

## • Panorama
## • 10.50.1.50
## • Firewall
- Management interface: 10.50.1.10
- Untrust interface: 42.11.45.1/24
- DMZ interface: 172.16.45.1/24
- Web Server (behind DMZ): 172.16.45.50
## • Windows Server 2012
## • 172.16.45.50
- Windows 7 PC
## • 192.168.45.10

- Verify the Windows Server 2012 has Active Directory installed and running with groups and users created on it.
- Configure/verify that DNS is fully working between the following IP Addresses and systems (forward and reverse) (i.e. make
sure nslookup works):
- Windows 7 PC
## • Windows Server 2012
- PAN Firewall
- (i.e. Windows 7 PC must be able to nslookup the Outside interface IP address of the PAN firewall and resolve to the FQDN
of the firewall in a browser)


## Resolution

- Install Certificate Services on Windows Server 2012 (i.e. make Windows Server 2012 the Root CA)
- Export the Root CA Certificate from the Windows Server 2012 Root CA
- Install the Root CA Certificate on employee Windows/Mac PCs
- Import Root CA Certificate into firewall, generate CSR on firewall, get CSR signed by Windows Server 2012 Root CA, and
then install that signed certificate on the firewall
- Configure GlobalProtect on the Firewall and configure Security Policy rule to allow VPN traffic from Outside to Inside/DMZ
- Download/Activate GlobalProtect client software images which the Firewall will serve to the employee Windows/Mac PCs
- Download, install, and connect to the firewall using GlobalProtect VPN client software on employee Windows/Mac PCs
- Troubleshooting/Verification/Debugs

Install Certificate Services on Windows Server 2012 (i.e. make Windows Server 2012 the Root CA)
- Open Server Manager > click Add roles and Features



- Click Role-based and click Next



- Select the Windows Server and click Next



- Select Active Directory Certificate Services and click Next



- Click Next twice



- Select Certification Authority Web Enrollment and click Next twice



## 7. Click Next



- Check the Restart the destination server automatically if required checkbox and click Install
Wait for the loading bar to finish - Windows Server 2012 will not reboot.
Warning: this will cause the Windows Server 2012 to reboot (not yet, but it could later in a next step in this document)



- Once the loading bar is done above, click Configure Active Directory Certificate Services on the destination server



## 10. Click Next



- Check Certification Authority and Certification Authority Web Enrollment and click Next twice



- Select Root CA and click Next



- Select Create a new private key and click Next



- Select SHA256 as the hash algorithm which this Windows Server 2012 Root CA will use to sign certificates (most modern
browsers will show warnings for anything below SHA256) - click Next



- Save this information to a notepad - click Next until the next step (Confirmation screen)



## 16. Click Configure



- Launch  a  web  browser  and  go  to http://172.16.45.50/certsrv - type in  the  Administrator credentials  for  Windows  Server
## 2012



- Now the Windows Server 2012 is a Root CA. Now, it can sign CSRs submitted to it - Windows Server 2012 will take the
CSR and give back a signed certificate in return (i.e. that certificate will be signed by Windows Server 2012 which is the
Root CA)




Export the Root CA Certificate from the Windows Server 2012 Root CA
In this section, we will use Microsoft Windows Server 2012 as our Root CA for certificates. The Client PC's will trust this Root CA to
connect securely to the firewall via the GlobalProtect VPN client software. This will make sure the end users can connect securely to
the firewall over the internet and access internal resources from home. Their client PC will trust the connection in their browser and
in the GlobalProtect VPN client software.

- Click Download a CA certificate, certificate chain, or CRL



- Click Download CA Certificate




- Rename it to RootCACert




Install the Root CA Certificate on employee Windows/Mac PCs
- Put the RootCACert file on the Windows 7 client PC and double-click to install the certificate:



Note: If deploying GlobalProtect VPN in a large enterprise or if deploying GlobalProtect to many employee PC's/users, the Root CA
certificate can be pushed to the employee PCs using Windows Server 2012 Group Policy via this method instead of installing it on
each PC individually like we do below:



## 2. Click Next



- Select Place   all   certificates   in   the   following   store - click Browse and   select   the Trusted   Root   Certification
Authorities folder - click Ok and Next and click Finish






Note: If an Intermediate CA Certificate is also used/needed, the same process above can be performed to import it to the PC, but
choose 'Intermediate Certification Authorities' folder instead


Import Root CA certificate on to firewall, generate CSR on firewall, get CSR signed by Windows Server Root CA, and then
install that signed certificate on the firewall
- Go to http://172.16.45.50/certsrv and click Download a CA Certificate, certificate chain, or CRL



- Select Base 64 > click Download CA Certificate



- Rename it to RootCACertFW

- Go to Panorama or the Firewall and go to Device > Certificate Management > Certificates > click Import
- Type a Certificate Name for the Root CA Certificate
- Select the RootCACertFW certificate we just downloaded
- Select the File Format as Base64 Encoded Certificate (PEM)
## 8. Click Ok





Note: If you have an Intermediate Root CA Certificate, import it here now under the Root CA Certificate
- Go to Panorama or the Firewall and go to Device > Certificate Management > Certificates and click Generate
- Type  the Certificate  Name for  the  certificate  as GPPortalGatewayCert (this  field  will  be  important  later - remember
the Certificate Name)
- Type the Common Name as the Outside IP Address of the firewall (or whatever DNS name that IP Address nslookup's to
if on internet)
- Select the Signed By option as 'External Authority (CSR)'
- Click Add to  add  a  SAN  field  (IP)  to  the  certificate - this IP/SAN  field  must  match  the  firewall's  FQDN and  must  be
resolvable by the employee PC's in order to connect to the firewall's portal and gateway via the GlobalProtect VPN client
## 14. Click Generate



Warning: Most modern browsers as well as the firewall itself require that the firewall's Global Protect Server certificate SAN field
must match the FQDN of the firewall in order to connect successfully via VPN and for end users to navigate to the GlobalProtect
Portal in their browser successfully. If the SAN field exists at all with at least one entry in the certificate/CSR, then the FQDN being
used  for  portal/gateway  for  this  firewall  should  always  be  present  in  that  SAN  list. The  FQDN  of  the  firewall  can  be  found  here:



FQDN: fw1.panlab.com



- Select the checkbox for the CSR and click Export Certificate - the certificate will download to the PC



It will be named cert_GPPortalGatewayCert.csr



- Launch a web browser and go to http://172.16.45.50/certsrv
- Click Request a Certificate



## 18. Click Advanced Certificate Request



- Open cert_GPPortalGatewayCert.csr using Notepad - copy and paste the contents into the field like below:
## 20. Select Certificate Template Web Server
## 21. Click Submit



- Select Base 64 encoded
## 23. Click Download Certificate



This will download the now-signed certificate in the browser - rename it to GPPortalGatewayCert



Note: When importing this signed cert, it must have the exact same name as the CSR (Certificate Name field) we generated in the
Firewall Web UI above i.e. it must be named GPPortalGatewayCert
- Open  Panorama  again  and  go  to Device > Certificate  Management > Certificates >  checkbox  the  existing  CSR  and
click Import
- Type the Certificate Name
- Click Browse and select GPPortalGatewayCert.cer
- Select the File Format as Base64 Encoded Certificate (PEM)
## 28. Click Ok



At    this    point,    the    firewall    has    a    Root    CA    Certificate RootCACertFW,    and    the    firewall    has    a    Firewall    Server
Certificate GPPortalGatewayCert which is signed by that Root CA Certificate.

This  Firewall  Server  Certificate  is  the  certificate  which  will  be  presented  to  the  Client  PCs  when  they  connect  to  the  firewall  via
GlobalProtect. The Client PCs will trust this certificate because the client PC also trusts this Root CA due to the step we did earlier
in this document where we installed the Root CA Certificate on the Windows 7 Client PC




Configure  GlobalProtect  on  the Firewall  and  configure  Security  Policy  rule  to  allow  the  VPN  traffic  from  Outside  to
Inside/DMZ
- Go to Device > Certificate Management > SSL/TLS Service Profile and create an SSL/TLS Service Profile referencing
the signed Firewall Server Certificate GPPortalGatewayCert, which we got signed and imported in the above step:



- Go to Device > Server Profiles > LDAP > click Add
- Type a Profile Name
- Under Server  List >  click Add and  type  the  IP  address  of  the  Windows  Active  Directory (LDAP  server)  and port  389 for
## LDAP
## 5. Click Ok



- Navigate to Device > Authentication Profile > click Add
- Type a Name
- Select Type LDAP
- Select Server Profile created above panlabDCldapserverprof
- Type Login Attribute as sAMAccountName



- Click Advanced tab > click Add and add 'all' or select certain groups if GlobalProtect VPN should restrict access to certain
AD/LDAP groups only



- Create a tunnel interface to use for GlobalProtect VPN and give it a tunnel number
- Select the Virtual Router
- Select a Security Zone - it is recommended to create a separate Security Zone for VPN traffic as it gives more flexibility in
creating Security Policy for the VPN traffic
## 15. Click Ok



(no IP address needed for this tunnel.2 interface)
- Go to Network > GlobalProtect > Portals > click Add > General tab
- Select which Interface and IP address which is to be the GlobalProtect Portal that the Client PC's will connect to



- From the Authentication tab
- Select the SSL/TLS Service Profile created above
- Click Add under Client Authentication
- Type a Name
- Select the Authentication Profile we made above
- Select Yes (User Credentials OR Client Certificate Required)
## 24. Click Ok






- From the Agent tab
- Click Add under Agent
- Under Authentication tab type a Name



- Under External Gateways tab click Add
- Type a Name
- Enter  the FQDN of  the  Firewall  which  was  put  in  the  certificate's SAN/Host  Name  field earlier  in  this  document
(in GPPortalGatewayCert)



- Under the App tab select Connect Method drop-down and select On-demand (Manual user initiated connection)



## 32. Click Ok
- Click Add to add RootCACertFW (imported into the Firewall earlier in this document) to the list of Trusted Root CAs for the
GlobalProtect Portal



Note: If you have an Intermediate CA Certificate, add it here below the Root CA Certificate
## 34. Click Ok
- From Configure GlobalProtect Gateway
- Type a Name



- Select an SSL/TLS Service Profile
- Under Client Authentication, click Add



- Type a Name
- Select the Authentication Profile created earlier in the step above
- Select Yes (User Credentials OR Client Certificate Required)



## 42. Click Ok
- Select the Tunnel Interface created for this GlobalProtect configuration earlier in this document
- Select the checkbox 'Enable IPSec' - if GlobalProtect fails to connect to the Firewall over IPSec, it will fall back to SSL



- Under Client Settings tab click Add



- Type a Name



- Type a pool of IP addresses which will be the IP addresses the GlobalProtect Client PC's will receive as an IP Address on
their GlobalProtect VPN adapter on their PC when they connect via the GlobalProtect VPN Agent



Note: Make sure this pool of IP addresses does not overlap/is not already in use anywhere in the organization/company's existing
network.
## 48. Click Ok

Download/Activate GlobalProtect client software images which the Firewall will serve to the employee Windows/Mac PCs
- Go to Panorama/Firewall Web UI and go to Panorama tab > Device Deployment > click GlobalProtect Client
- Click Download and click Activate on whichever version of GlobalProtect software the end users will use. This will also be
the version which the Firewall gives to the Client PC's if they go to the Portal page of the Firewall and download GlobalProtect
for use.





Example: When the end user clicks Download Windows 64 bit GlobalProtect agent, they will now be downloading the GlobalProtect
5.0.4 installer, which will install version 5.0.4 of GlobalProtect software on their Client PC:



Once Activate is clicked, the end user can then go https://fw1.panlab.com in their browser and download the version of
GlobalProtect which has been currently Activated, or if they already have GlobalProtect installed, and they try to connect via

GlobalProtect VPN, the GlobalProtect software on their PC will prompt them to upgrade their version to the one the firewall is
offering/has Activated.


Download, install, and connect to the firewall using GlobalProtect VPN client software on employee Windows/Mac PCs
- Have the end user go to https://fw1.panlab.com and login using their credentials
Note: Remember, the GlobalProtect software could be pushed out to each PC so that end users can skip this step and just open
GlobalProtect on their laptop and Connect



- The end user will see a screen like this where they can choose which GlobalProtect software they would like to download
and install:



## 3. Click Connect



- Have the end user type their credentials and click Sign In



- The Client PC is now successfully connected into the corporate network via GlobalProtect VPN:



- The Client PC is connected via GlobalProtect VPN to the firewall over the internet, and the Client PC can reach a web server
behind the DMZ interface/zone of the firewall successfully now that he is VPN'd:




Troubleshooting/Verification/Debugs
- From the Client PC
- From the GlobalProtect Agent
- From the Firewall

From the Client PC
- Make sure the end user's PC can reach the firewall's Outside interface by its FQDN - and that it resolves to the correct IP
address



- Open GlobalProtect on the client PC > click the top-right three-bars icon in GlobalProtect > click Settings








From the GlobalProtect Agent
- Go to Settings > Troubleshooting tab > Collect Logs > unzip them and open > PanGPA.log
- Logs of the new GlobalProtect 5.0.4 software downloading and installing:

(T1216) 09/16/19 13:26:17:197 Debug( 642): PanClient sent successful with 3088 bytes
(T3192) 09/16/19 13:26:20:519 Debug(  93): Received data from Pan Service
(T3192) 09/16/19 13:26:20:519 Debug( 332): ### Download parameters ###:
m_dwLatestDownlaod=1568658367, m_bDownloadStarted=0, bCheckTunnelOK=1, m_bOnDemandRead=0,
bUsingCachedPortal=0, lastfaileddownload=0, m_nUpgradeMethod=2
(T3192) 09/16/19 13:26:20:519 Debug( 430): CPanClient::startUpgradeProcess, the download package
is h
(T3192) 09/16/19 13:26:20:519 Debug(  25): create thread 0x1d0 with thread ID 2844

(T3192) 09/16/19 13:26:20:519 Info (1238): CSessionPage::URMMsiDownload - update dialog thread
started

(T2844) 09/16/19 13:28:30:639 Info (1137): CPanDownloadProgress::OnInitDialog - downloadproc
thread started
(T1480) 09/16/19 13:28:30:795 Info (1040): Download started.
(T1480) 09/16/19 13:28:30:826 Debug( 433): winhttp SetSecureProtocol, hSession=02f07aa0,
bAllProtocol=0, gbFips=0
(T1480) 09/16/19 13:28:30:826 Debug( 433): winhttp SetSecureProtocol, hSession=02f08360,
bAllProtocol=0, gbFips=0
(T1480) 09/16/19 13:28:39:484 Info ( 154): DownloadURLToFile: HTTP 200 OK
(T1480) 09/16/19 13:28:39:484 Debug( 369): Content-length: 32768000
(T3192) 09/16/19 13:28:40:311 Debug( 977): Receive inactive message.
(T3192) 09/16/19 13:28:42:433 Debug( 977): Receive inactive message.
(T1480) 09/16/19 13:28:42:464 Info (1087): Download completed. total time = 12 (sec).
(T1480) 09/16/19 13:28:42:464 Info (1089): Update started: from version 5.0.3-29 to version
## 5.0.4-16.
(T1216) 09/16/19 13:28:52:495 Debug( 563): Send command to Pan Service
(T1216) 09/16/19 13:28:52:495 Debug( 590): Command = <request><type>software-
upgrade</type><command-line>C:\Users\jsmith\AppData\Local\Temp\_temp3120.msi</command-
line></request>
(T1216) 09/16/19 13:28:52:495 Debug( 642): PanClient sent successful with 144 bytes


From the Firewall
- Go to Monitor > Logs > System Logs


admin@PA-VM2(active)> show global-protect-gateway gateway name panlab_Gateway
GlobalProtect Gateway: panlab_Gateway (1 users)
Tunnel Type          : remote user tunnel
Tunnel Name          : panlab_Gateway-N
VSYS                       : vsys1 (id 1)
Tunnel ID                  : 3
Tunnel Interface           : tunnel.2
Tunnel IPv6 Enabled        : no
Encap Interface            : ethernet1/4
vr-id                      : 0
## Inheritance From           :
Local Address (IPv4)       : 42.11.45.1
SSL Server Port            : 443
IPSec Encap                : yes
Tunnel Negotiation         : ssl
HTTP Redirect              : no
UDP Port                   : 4501
## Max Users                  : 0
Exclude Video Traffic      : no
Gateway-Level IP Pool Ranges:
Gateway-Level IP Pool index:     0
Gateway-Level IPv6 Pool Ranges:
Gateway-Level IPv6 Pool index:     0
config name                : panlab_GWClientSettings
User Groups                :     any;
OS                         :     any;
IP Pool Ranges             :     192.168.1.50 - 192.168.1.250(192.168.1.51);
IP Pool index              :     0
IPv6 Pool Ranges           :
IPv6 Pool index            :     0
No Direct Access To Local Network:     no
Retrieve Framed IP Address :     no

Auth Server IP Pool Ranges :
Auth Server IPv6 Pool Ranges:
## Access Routes              :     0.0.0.0/0
## Exclude Access Routes      :
DNS Servers                :
DNS Suffix                 :
DNS Servers                :
WINS Servers               :
SSL Server Cert            : GPPortalGatewayCert
Client Authentication      :    Auth Name                  : panlab_GwClientAuth
Auth OS                    : Any
Auth Profile               : panlabLDAP_authprof
Allow User Credentials OR Client Cert: yes
## Client Cert Profile        :
Lifetime                   : 2592000 seconds
Idle Timeout               : 10800 seconds
Disconnect On Idle         : 10800 seconds
Disallow Automatic Restoration: no
Source IP Check            : no
Encryption                 : aes-128-cbc
Authentication             : sha1

admin@PA-VM2(active)> show global-protect-gateway current-user gateway panlab_Gateway
admin@PA-VM2(active)> show global-protect-gateway current-user user jsmith
## 2019-09-15 11:15:49
GlobalProtect Gateway: panlab_Gateway (1 users)
Tunnel Name          : panlab_Gateway-N
Domain-User Name           : \jsmith
Computer                   : COMP-WIN7-2
Primary Username           : jsmith
Region for Config          : KR
Source Region              : KR
Client                     : Microsoft Windows 7 Enterprise Edition Service Pack 1, 64-
bit
VPN Type                   : Device Level VPN
Mobile ID                  :
Client OS                  : Windows
Private IP                 : 192.168.1.50
Private IPv6               : ::
Public IP (connected)      : 42.11.45.10
Public IPv6                : ::
Client IP                  : 42.11.45.10
ESP                        : exist
SSL                        : none
## Login Time                 : Sep.15 11:07:18
Logout/Expiration          : Oct.15 11:07:18
## TTL                        : 2591489
Inactivity TTL             : 10302
Request - Login            : 2019-09-15 11:07:18.254 (1568570838254), 42.11.45.10
Request - GetConfig        : 2019-09-15 11:07:18.396 (1568570838396), 42.11.45.10
Request - SSLVPNCONNECT    :  (0), ::

admin@PA-VM2(active)> less mp-log rasmgr.log
2019-09-15 11:07:18.208 -0700 req->portal address 0x7fffdc096250
2019-09-15 11:07:18.251 -0700 192.168.1.50 is framed ip? no
2019-09-15 11:07:18.251 -0700 retrieve-framed-ip-address(no);  is-preferred-ip-a-framed-ip(no);
retrieve-framed-ip-address-v6(no);  is-preferred-ip-a-framed-ipv6(no);
2019-09-15 11:07:18.252 -0700 req->portal address 0x7fffd8064ca0
2019-09-15 11:07:18.254 -0700 new cookie:  ******
2019-09-15 11:07:18.254 -0700 rasmgr_sslvpn_client_register space panlab_Gateway-N domain  user
jsmith computer COMP-WIN7-2 result 0
2019-09-15 11:07:18.396 -0700 client existing address 42.11.45.10/24; preferred ip 192.168.1.50;
address-v6 2002::/16,1234:1234:2d0a::1234:1234/128; preferred ipv6 None; client exclude video
support yes; gw license no
2019-09-15 11:07:18.397 -0700 Adding info in usr info to haremoteusr info for:jsmith
2019-09-15 11:07:18.397 -0700 Installing GW Tunnel, indicate to
keymgr...exclude_video_traffic_enable=0 [0 0]
2019-09-15 11:07:31.066 -0700 Adding info in usr info to haremoteusr info for:jsmith

admin@PA-VM2(active)> less appweb-log sslvpn-access.log
42.11.45.1 - - [Sun Sep 15 11:07:18 2019 PDT] "POST /ssl-vpn/prelogin.esp?kerberos-
support=yes&tmp=tmp&clientVer=4100&host-id=433474f9-7a92-4f6f-9990-
43731e8697fe&clientos=Windows&os-
version=Microsoft+Windows+7+Enterprise+Edition+Service+Pack+1%2c+64-bit&ipv6-support=yes
## HTTP/1.1" 200 968

42.11.45.1 - - [Sun Sep 15 11:07:18 2019 PDT] "POST /ssl-vpn/login.esp HTTP/1.1" 200 2840
42.11.45.1 - - [Sun Sep 15 11:07:18 2019 PDT] "POST /ssl-vpn/getconfig.esp HTTP/1.1" 200 1809
42.11.45.1 - - [Sun Sep 15 11:07:31 2019 PDT] "POST /ssl-vpn/hipreportcheck.esp HTTP/1.1" 200
## 561
127.0.0.1 - - [Sun Sep 15 11:08:06 2019 PDT] "GET /robots.txt HTTP/1.1" 200 250

admin@PA-VM2(active)> show global-protect-gateway flow
total GlobalProtect-Gateway tunnel shown:                     2
id    name                  local-i/f         local-ip                      tunnel-i/f
--    ----                  ---------         --------                      ----------
3     panlab_Gateway-N      ethernet1/4       42.11.45.1                    tunnel.2

admin@PA-VM2(active)> show global-protect-gateway flow name panlab_Gateway
## 2019-09-15 11:18:38
id:                3
type:              GlobalProtect-Gateway
local ip:          42.11.45.1
inner interface:   tunnel.2         outer interface:  ethernet1/4
ssl cert:          GPPortalGatewayCert
active users:      1
assigned-ip                              remote-
ip                                MTU   encapsulation
------------------------------------------------------------------------------------------------
## ----------------------
192.168.1.50                             42.11.45.10                              1420  IPSec
SPI 4311646B (context 619)

admin@PA-VM2(active)> show global-protect-gateway flow tunnel-id 3
tunnel  panlab_Gateway-N
id:                3
type:              GlobalProtect-Gateway
local ip:          42.11.45.1
inner interface:   tunnel.2         outer interface:  ethernet1/4
ssl cert:          GPPortalGatewayCert
active users:      1
assigned-ip                              remote-
ip                                MTU   encapsulation
------------------------------------------------------------------------------------------------
## ----------------------
192.168.1.50                             42.11.45.10                              1420  IPSec
SPI 4311646B (context 619)




## Additional Information
To configure GlobalProtect VPN just using self-signed certificates on the firewall (instead of having an internal/external root CA
issue the certificates), the document below can be followed: Basic GlobalProtect Configuration with User-logon
