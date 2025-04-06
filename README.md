<h1>Active Directory Lab: Setting up users</h1>



<h2>Description</h2>
Project consists of adding features to the active directory domain. Creating profiles for differents users, helpdesk, HR, etc.. Ensuring that all the permissions are correct and follow the rules of least privelege.
<br />




<h2>Environments Used </h2>

- <b>Windows Server 2022</b> 
- <b>Windows 10 Pro</b>
- <b>Pfsense 2.7.2</b>

<h2>Chapter 1: Creating a helpdesk user</h2>

<p align="center">
Head into the server manager, in there go to roles and features. From there move onto server roles and add active directory domain services and go ahead and install it. Then click on the flag icon in server manager and promote the server to domain controller. 
  I named  mine testserver.com<br/>
<img src="https://i.imgur.com/v58VxAw.png" height="80%" width="80%" alt="First step"/>
<br />

<br />
From there head into users and computers. Click on the users folder and highlight the administrator. Make a copy of the administrator user and name the copy helpdesk  <br/>
<img src="https://i.imgur.com/jLC3xB3.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Hit next and set a password for the helpdesk user.
<img src="https://i.imgur.com/5yQDge2.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Now on the Windows 10 desktop that was created. Head into network and internet settings. Click on change adapter settings, hit properties. From there you want to double click on Ipv4 and go down to DNS settings.
You will want to input the ip address for the domain controller     <br/>
<img src="https://i.imgur.com/9xKwzEb.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Then head into system properties, advanced system settings, and head to the computer name section. In there click to join computer to domain. My domain is called testserver, so I input that. For username and password, use the server administrator password.  <br/>
<img src="https://i.imgur.com/jvKZuGo.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Here you can see both virtual computer instances getting a DHCP address from PFsense
<img src="https://i.imgur.com/JxdgTpp.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
After joining the domain, use the helpdesk username and password created earlier. From there head into Settings, system, and add optional features. From there add the RSAT features pertaining to a helpdesk user, giving access to the various tools needed by the user.    <br/>
<img src="https://i.imgur.com/W2xWDdd.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>

<!--
 ```diff
- text in red
+ text in green
! text in orange
# text in gray
@@ text in purple (and bold)@@
```
--!>
