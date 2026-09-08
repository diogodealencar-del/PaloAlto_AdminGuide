

How to Setup Palo Alto Networks Radius Authentication to a
## Windows 2012 R2 Domain Server

This guide will demonstrate how to get Radius authentication working between a Palo Alto Networks
device and a Windows 2012 R2 Domain Server.  Although this is not a recommendation on how to setup
a Windows 2012 R2 server in a production environment, the settings referred to in this document are
simply the settings used in the CSL lab environment to demonstrate using Radius to provide
administrator access using the Palo Alto Networks platform in conjunction with a Windows 2012 R2
server.
- Log in to the Palo Alto Networks device and setup radius server profile


- Setup Radius authentication profile


How to Setup Palo Alto Networks Radius Authentication to a
## Windows 2012 R2 Domain Server



- Add radius authentication profile to device management





How to Setup Palo Alto Networks Radius Authentication to a
## Windows 2012 R2 Domain Server

- Create an admin user


- Open the Group Policy Management control on the domain controller (ClientA in this lab). Set
the Default Domain Policy on the 2012 domain to store passwords using reversible encryption
(Required for CHAP authentication).  This policy should only be applied to the admin accounts to
be used for logging into the PANW devices.  This incurs a security risk and should not be applied
to all user accounts.  The Default Domain Policy is only referenced in this lab for ease of
configuration.

- Commit the changes to the running config.














How to Setup Palo Alto Networks Radius Authentication to a
## Windows 2012 R2 Domain Server



- Open Active Directory Users and Computers and create a security group for the NGFW admins


- Create admin user account.  Ensure the name matches the administrator account that was
created on the Palo Alto Networks device.







How to Setup Palo Alto Networks Radius Authentication to a
## Windows 2012 R2 Domain Server



- Add the user account to the security group that was created in the previous step.


- Open Server Manager on the Windows 2012 domain server.
- Click Manage>Add Roles and Features.
- Click Next and choose Role-based or feature-based installation.
- Select the server to install the service on (This is usually selected by default)
- Click Next and select Network Policy and Access Services.
- Click Next and Click Install and wait for the installation to complete.
- Open the Network Policy Server console.














How to Setup Palo Alto Networks Radius Authentication to a
## Windows 2012 R2 Domain Server



- Right-click on NPS and register the server in Active Directory.


- Expand Radius Clients and Servers > Radius Clients, right and choose New.









How to Setup Palo Alto Networks Radius Authentication to a
## Windows 2012 R2 Domain Server


- Enter the name of the Palo Alto Networks device that will authenticate using radius as well as
the IP address of the management interface (or whatever interface you’ve chosen for Radius in
the service route configuration on the device) and include the Shared Secret you used when
setting up the Radius Server profile.  Click OK.















How to Setup Palo Alto Networks Radius Authentication to a
## Windows 2012 R2 Domain Server


- In the NPS console, expand Policies>Network Policies, right click and select New.


- Give the policy a name and click Next.





How to Setup Palo Alto Networks Radius Authentication to a
## Windows 2012 R2 Domain Server


- Click the Add button, choose User Groups and click the second add button.





















How to Setup Palo Alto Networks Radius Authentication to a
## Windows 2012 R2 Domain Server


- Click the Add Groups button.


- Enter the name of the security group that you created in Active Directory earlier and click OK.


How to Setup Palo Alto Networks Radius Authentication to a
## Windows 2012 R2 Domain Server


- Clock OK again until you get back to the Specify Conditions page.


- Click Next, Choose Access Granted and click Next again.

How to Setup Palo Alto Networks Radius Authentication to a
## Windows 2012 R2 Domain Server


- Uncheck MSCHAP-V2 and MS-CHAP, and select only CHAP.


- Leave the Configure Restraints page at its defaults and click Next.

How to Setup Palo Alto Networks Radius Authentication to a
## Windows 2012 R2 Domain Server




- Leave the Configure Settings page at its defaults and click Next.


- Verify your settings on the Completing New Network Policy page and click Finish.

How to Setup Palo Alto Networks Radius Authentication to a
## Windows 2012 R2 Domain Server




- Move the new Network Policy to the top of the list.



How to Setup Palo Alto Networks Radius Authentication to a
## Windows 2012 R2 Domain Server













- Open the new Policy and check the box for Ignore user account dial-in properties. Click Ok.

How to Setup Palo Alto Networks Radius Authentication to a
## Windows 2012 R2 Domain Server



- Right Click on Connection Request Policies and select New.

- Give the policy a name and click Next.

How to Setup Palo Alto Networks Radius Authentication to a
## Windows 2012 R2 Domain Server
























- On the Specify Conditions page, select the condition(s) you want the client to meet in order to
authenticate.  In this example I selected 24 hours a day.

How to Setup Palo Alto Networks Radius Authentication to a
## Windows 2012 R2 Domain Server





How to Setup Palo Alto Networks Radius Authentication to a
## Windows 2012 R2 Domain Server



- Click Next and leave the Specify Connection Request Forwarding page at its defaults.

- Leave the Specify Authentication Methods page at its defaults and click Next.

How to Setup Palo Alto Networks Radius Authentication to a
## Windows 2012 R2 Domain Server



- Leave the Configure Settings page at its defaults and click Next.



- Verify your settings on the following page and click Finish.

How to Setup Palo Alto Networks Radius Authentication to a
## Windows 2012 R2 Domain Server



- Right-click NPS (Local) and choose Stop NPS Service.



- Wait a few seconds and right-click NPS-Local and choose Start NPS Service.

How to Setup Palo Alto Networks Radius Authentication to a
## Windows 2012 R2 Domain Server

- Log in to the Palo Alto Networks device using the new admin account.



