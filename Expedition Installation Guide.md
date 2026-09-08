

## Expedition Installation Guide
## Contact Information
## Corporate Headquarters:
## Palo Alto Networks
## 3000 Tannery Way
Santa Clara, CA 95054
## Palo Alto Networks, Inc.
www.paloaltonetworks.com
© 2021 Palo Alto Networks, Inc. Palo Alto Networks is a registered trademark of Palo Alto Networks. A list of our trademarks can be
found at  https://www.paloaltonetworks.com/company/trademarks.html. All other marks mentioned herein may be trademarks of their
respective companies.
## Revision Date: Sep 12, 2022

About the Documentation
## ●
For the most recent version of this guide, visit the Expedition Live Community
Documentation portal :
https://live.paloaltonetworks.com/t5/Expedition-Migration-Tool/ct-p/migration_tool
## ●
Have feedback or questions for us? Leave a comment on any page in the portal, or write to
us atfwmigrate@paloaltonetworks.com
## Copyright
## Palo Alto Networks, Inc.
www.paloaltonetworks.com
© 2021-2021 Palo Alto Networks, Inc. Palo Alto Networks is a registered trademark of Palo Alto Networks. A list of our
trademarks can be found at www.paloaltonetworks.com/company/ trademarks.html. All other marks mentioned herein
may be trademarks of their respective companies.
## Last Revised
## Sep 12, 2022
## Expedition Installation Guide© 2022 Palo Alto Networks, Inc.
## 2

Table of Contents
## Resources Needed4
## Installation Steps5
Install Ubuntu Server 20.04.* LTS (64-bits AMD)5
## Install Expedition Application13
Login to Expedition GUI16
Transfering between Expeditions (Optional)18
## FAQ26
© 2021 Palo Alto Networks, Inc.Expedition Installation Guide
## 3

## Resources Needed
The following resources are needed to install Expedition into your environment.
❏Ubuntu 20.04.* LTSServer (64-bits AMD)
*Please do not download Ubuntu 22.x , it is not supported at this point, expedition installation
script won’t execute at all.
The Ubuntu server image can be downloaded from thelink below:
https://ubuntu.com/download/server
The Ubuntu server will need to be provisioned by the end-user. Options include
downloading and installing Ubuntu 20.04.* LTS ISO onto a customer-managed server or to
provision an Ubuntu 20.04.* LTS virtual server available from Google Cloud, AWS or Azure.
❏Expedition installer File
## The Installer File
expedition1_Installer_latest.tgz
can be downloaded from below link:
https://conversionupdates.paloaltonetworks.com/expedition1_Installer_latest.tgz
## System Requirements
The recommended system requirements for the Expedition server are listed in the
following table.
Primary usageRecommended Compute Resources
## Migration
4 CPU/Cores
## 8 GB RAM
40 GB storage
1 nic with 100Mbps/1Gbps
Machine Learning (5 or fewer
firewalls)
8 CPU/Cores
## 16 GB RAM
1 x 6GB (OS related data)
1 x 150 GB SSD (Project Settings and connection.parquet files)
1 x 4 TB (Traffic and other log files)
1 nic with 100Mbps/1Gbps
Machine Learning (6 or more
firewalls)
8 CPU/Cores
## 32 GB RAM
1 x 6GB (OS related data)
1 x 150 GB SSD (Project Settings and connection.parquet files)
1 x 4 TB (Traffic and other log files)
1 nic with 100Mbps/1Gbps
## Expedition Installation Guide© 2022 Palo Alto Networks, Inc.
## 4

## Installation Steps
1)Install Ubuntu Server 20.04.* LTS (64-bits AMD)
## 1)
Download the Ubuntu iso file:
a)Visithttps://ubuntu.com/download/server, select“Option2: Manual Server
## Installation
Select“Alternative Downloads”
© 2021 Palo Alto Networks, Inc.Expedition Installation Guide
## 5

Click on“Ubuntu Server 20.04.* LTS”to download theimage. Make sure that the
downloaded image is the server amd64 iso.
b)Launch VMware Fusion and click“+”, select“new”
## Expedition Installation Guide© 2022 Palo Alto Networks, Inc.
## 6

c)Drag the downloadedubuntu-20.04.*-live-server-amd64.isofile to the installation
area to start installation
d)Choose theubuntu-20.04.*-live server-amd64.isoimage, and click“Continue”
© 2021 Palo Alto Networks, Inc.Expedition Installation Guide
## 7

e)Create an“expedition”account to install the Ubuntu VM , using the default password
“paloalto”. Click“Continue”.Note:You can change the login credential after you
completely finishedStep 2 Install Expedition
f)Review the setting , and click on“Finish”.It willauto start ubuntu vm installations.
## Expedition Installation Guide© 2022 Palo Alto Networks, Inc.
## 8

g)When the VM is auto-started , go to the menu bar and select“Virtual Machine”->
“Shutdown”to temporarily shutdown the VM.
Click“Settings”to display setting options ofthe VM:
Click“Processors & Memory”to increase the CPUand Memory resources , and change the
Settings to meet therecommended system requirementsper your primary use case.
© 2021 Palo Alto Networks, Inc.Expedition Installation Guide
## 9

Click“Show All”on the top of the menu bar to take you back to the all settings page.
Click“Hard Disk(SCSI)“to increase the hard drivespace to meet therecommended
system requirementsper your primary use case.
Once you finish changing all the settings , highlight the Ubuntu VM and right click to
select“Start Up”,  the Ubuntu VM installation willcontinue.
h)Select“English”as default language , click“Done”to continue.
i)By default , the Ubuntu server will auto acquire an IP address from the DHCP pool.
click“Done”to continue.  You could also assigna static IP if it’s prefered in your
environment.
## Expedition Installation Guide© 2022 Palo Alto Networks, Inc.
## 10

j)Continue to click“Done”to go through the default settings.  When it reaches the
“Profile Setup”screen, create an account“expedition”and default password
“paloalto”for login to the system. Click“Done”.
Note:You can change the login credential after youcompletely finishedStep 2 Install
## Expedition
k)Select toInstall OpenSSH server. click“Done”. Installationrequires connections to
the Internet , Installation will take less than5minutes.
© 2021 Palo Alto Networks, Inc.Expedition Installation Guide
## 11

l)Once Installation is completed, the“ Install Complete!”will be shownon the top ,
select“Reboot Now”to reboot the server.
## Expedition Installation Guide© 2022 Palo Alto Networks, Inc.
## 12

2)Install Expedition Application
1)Download the installer file:
There are two ways to download the installer, you can select one of the method
below:
1)Download the installer on the ubuntu VM by issue below command:
## $cd /tmp
$sudo wget
https://conversionupdates.paloaltonetworks.com/expedition1_Installer_latest.tgz
2)Download from any machine and move the installer to expedition VM:
a)Click on the URL
https://conversionupdates.paloaltonetworks.com/expedition1_Inst
aller_latest.tgzto download the latest version
b)From your local drive scp the installer file to the Ubuntu VM,
replace IP inredto your expedition IP
$scp expedition1_Installer_latest.tgz  expedition@192.168.55.147:/tmp
2)SSH to the Ubuntu VM using account“expedition”withthe default password
## “paloalto”
3)Unpack the installer file on UbuntuVM:
a)$cd /tmp
b)$tar -zxvf expedition1_Installer_latest.tgz
This will result in two new files. One is the installer, the second is another tgz file that
has some initial databases.
expedition@ubuntu : ~/tmp $ ls -al
## 4)
Make the initSetup.sh executable
a)$chmod 755 initSetup_*.sh
## 5)
Execute the installer script
© 2021 Palo Alto Networks, Inc.Expedition Installation Guide
## 13

a)Verify that you are able to reach the following external repositories:
i)
https://conversionupdates.paloaltonetworks.com
ii)
https://www.rabbitmq.com/
iii)
http(s)://ppa.launchpad.net
iv)
http://us.archive.ubuntu.com
v)
http(s)://launchpad.net
vi)
https://files.pythonhosted.org
b)If you are in doubt, we recommend disabling the Global Protect app temporarily
before you run the script
The Ubuntu server should have internet access as the installer script will perform an update of the
Expedition software by connecting to the Palo Alto Networks update servers for Expedition and
additional Ubuntu dependencies, such as MariaDB, Apache Web Server, RabbitMQ, JVM 1.8, etc.
c)$sudo ./initSetup*.sh
The script will start running, it requires the user account“expedition”to exist before
running the script.  If you did not create an “expedition” account in the previous step, it will
prompt you that the account is needed and stop the script.
## Expedition Installation Guide© 2022 Palo Alto Networks, Inc.
## 14

The installation will take approximately20 mins.You can ignore below cosmetic error
messages during the installation:
© 2021 Palo Alto Networks, Inc.Expedition Installation Guide
## 15

Once the script is completed , you will see the message below as the last message ,
you can then proceed to the next step to reboot the VM.
6)Reboot the Ubuntu VM
$sudo reboot
3)Login to Expedition GUI
a)The first time you login to the Expedition via google chrome, you will receive the
“Your connection is not private” warning message, enter“thisisunsafe”on the
screen to bypass the warning.  It is recommended to re-install the self-signed
certificate by following instructions listed on live community :
https://live.paloaltonetworks.com/t5/expedition-articles/access-expedition-gui-using-
google-chrome/ta-p/318360
b)Login with default credentials ,username=”admin”,password=”paloalto”
## Expedition Installation Guide© 2022 Palo Alto Networks, Inc.
## 16

c)If you see a failed check”Verify the Provided MLIP is UP”on the dashboard:
The solution is to verify Expedition ML Address is set correctly, by type“127.0.0.1”in
the“Settings”->“M.Learning” -> “Expedition ML Address”field, and click“Save”,
this step will reset the database and auto set the IP back to match your expedition IP.
© 2021 Palo Alto Networks, Inc.Expedition Installation Guide
## 17

d)Navigate back to the Dashboard, all internal checks listed on the right side should
show“green”checkmarks , meaning nothing needs tobe remediated. If there are
still checks that failed with the“red”mark, pleaseremediate them.
Transfering between Expeditions (Optional)
If transferring user accounts, devices, database,projects, or Firewall traffic logs from the old
Expedition server is required, Expedition v1.1.109 and above include a transfer assistant utility called
“migrate.php”in/var/www/html/OS/startup/migrate
## Expedition Installation Guide© 2022 Palo Alto Networks, Inc.
## 18

Using the above diagram as an example, we will transfer data from Expedition A- 10.0.0.39
on Ubuntu 16.04.* to Expedition B- 10.0.0.29 on Ubuntu 20.04.* . First step is to make sure
you can reach Expedition B from Expedition A. Here are the instructions on how to use the
migrate.php.
## 1)
Destination Expedition Server SSH Settings
(Belowinstructions can be found in the
migrate.php tool selection2. Enter Destination SSHSettings)
Three steps to set up Destination Expedition SSH Settings:
a)Create a private-public SSH key on Expedition A
Login to Expediation A 10.0.0.39 as'root'user,execute the following
command with default options(leave passphrase empty):
## #ssh-keygen -o
This will generate a pair of public-private keys for SSH communications.
Show the content of your public key using the command and copy the content :
## #cat ~/.ssh/id_rsa.pub
b)
Add Expedition A as a trusted ssh client in Expedition B
Login to  your destination Expedition B asroot, editthe authorized keys list
with the command:
© 2021 Palo Alto Networks, Inc.Expedition Installation Guide
## 19

# nano ~/.ssh/authorized_keys
Paste the content from Expedition A public key (previous step),Ctrl+Oto save the file
andCtrl +Xto exit out of Nano.
Make sure your trusted public key is added in one single line. Some editors may
introduce EoL characters that would alter the valid public key.
c)Test the connection from Expedition A to Expedition B
Test if your public-private keys are correctly set to SSH between the machines.
From Expedition A 10.0.0.39 trying to ssh to Expedition B 10.0.0.29 as root:
# ssh root@10.0.0.29
This will establish an SSH authenticated connectionWITHOUTyour root
password.
## Expedition Installation Guide© 2022 Palo Alto Networks, Inc.
## 20

2)Destination Expedition Server DB Settings
a)Allow remote MySQL connection on Expedition B
On the destination Expedition B(10.0.0.29), enter mysql using the default
credentials (root:paloalto). In case you define a different user and password, modify the SQL
statements to make them match.
## #mysql -uroot-ppaloaltomysql
Execute the following  three SQL statements (Replace the IP address10.0.0.39to the
IP of your Source Expedition)
GRANT ALL PRIVILEGES ON *.* TO 'root'@'10.0.0.39'IDENTIFIED BY 'paloalto' WITH GRANT
## OPTION;
## FLUSH PRIVILEGES;
exit;
© 2021 Palo Alto Networks, Inc.Expedition Installation Guide
## 21

b)Allow temporary remote MySQL connection on Expedition B
Open firewall-cmd to allow remote MySQL connections on Expedition B
firewall-cmd --add-port=3306/tcp
3)Run the Transfer Assistant Tool on Expedition A
Access  the Transfer Assistant tool on the  source Expedition server where you want
to transfer data from.  In the example here , the source Expedition A is 10.0.0.39, so we
will login to 10.0.0.39to access the tool.
a)
$cd /var/www/html/OS/startup/migrate
$php migrate.php
The tool main page will be displayed:
## 4)
Select Option1. Enter Destination Settings -> 1.Enter Destination IP
Enter the destination expedition server IP address you want to transfer the data to. In
the example here , we are trying to transfer data from a Expedition A (10.0.0.39) to the
Expedition B (10.0.0.29)  , so the destination Expedition IP is10.0.0.29
## Expedition Installation Guide© 2022 Palo Alto Networks, Inc.
## 22

## 5)
Select Option3. Enter Destination DB Settings
You will see the Instructions containing Step 1 and 2 that should already be
completed on Expedition B in theStep 2)DestinationExpedition Server DB
Settings, we will continue Step 3 to fill out thedatabase credentials and port info as
shown below. The tool already contains default values for these settings.
Enter the DB user for remote connection:
root
Enter the DB password:
paloalto
Enter the DB port:
## 3306
© 2021 Palo Alto Networks, Inc.Expedition Installation Guide
## 23

## 6)
Select Option4 Doneto go back to the main menu.
## 7)
SelectOption2 See Destination Settingsto reviewthe Destination Expedition
Server settings.  Verify the IP address is set as the IP of the destination Expedition B ,
ssh and database account are correctly configured. If you are transferring the traffic
log , please make sure the connections.paraquet path is set correctly. If they are not
correct, you can go back to the main menu and select option1 “Enter Destination
Settings”, there you can select options to changethe settings accordingly.
8)After you have verified the destination settings are correct, you can select option3
Migrate Users, Devices and Projects, it will  starttransferring the data from
Expedition A to Expedition B
## Expedition Installation Guide© 2022 Palo Alto Networks, Inc.
## 24

Once the transfer is completed, You can login to the Expedition B via GUI to check if user
account, projects have been transferred.
9)If transfering the traffic logs is required ,  selectOption 4 and 5to continue the
migration process, otherwise, selectOption 7to exitout of the tool.
10)Access Expedition B GUI , select“SETTINGS”->“CUSTOMPARAMS”, verify the user
and environment parameters in your destination Expedition B matches the setting
in Expedition A.
© 2021 Palo Alto Networks, Inc.Expedition Installation Guide
## 25

## FAQ
Can I upgrade my existing Expedition from Ubuntu 16.04?* to 20.04.* and run the new
installation script?
No, Installation of  a fresh Ubuntu 20.04.* server is required; there is no direct upgrade from
the expedition server running on Ubuntu 16.04 or older versions. In Expedition v1.1.109 and above,
the Transfer Assistant Tool is to help you migrate the data  from your old expedition server to the
new one.
Can I change the password for expedition or root account after installation ?
When running the Expedition Installation , an account name “expedition” with default
password is required and  the script will auto change the root password.  You can change the
password after a successful installation.
How can I provide feedback?
Please leave a comment in live community :
https://live.paloaltonetworks.com/t5/expedition/ct-p/migration_tool
or email us @fwmigrate@paloaltonetworks.com
## Expedition Installation Guide© 2022 Palo Alto Networks, Inc.
## 26