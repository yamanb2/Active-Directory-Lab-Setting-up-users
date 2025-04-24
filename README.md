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
<br/>
<br/>
Now we can set up group policy management. Head into tools on server manager and click on group policy management. Click on the domain controller name, highlioght default domain policy, right click and hit edit. 
<img src="https://i.imgur.com/VIoy16I.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br/>
<br/>
Now click on policies, windows settings, and security settings. Here we can change a wide range of policies relating to the domain. 
<img src="https://i.imgur.com/6Nanwtr.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br/>
<br/>
Go to account policies and we can change account lockout threshold. 
<img src="https://i.imgur.com/4AKpLpS.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br/>
<br/>

<img src="https://i.imgur.com/u62R9ZQ.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br/>
<br/>
I changed mine to 5 invalid attempts and locking the computer for 30 minutes if the condition is true. 
<img src="https://i.imgur.com/X8R9qNX.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br/>
<br/>
Back in users and computers, I want to begin setting up the OUs and the new user. 
Right click testserver, go to new, and create a new OU called HR and another for IT. 
<br/>
<img src="https://i.imgur.com/ysXwPTa.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br/>
<br/>
Now create a new user, I named it charles and set a password. 
<img src="https://i.imgur.com/5ZbTOnC.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br/>
<br/>
Now I move the users into their correct OU, based on their role.
<img src="https://i.imgur.com/HhWVkEk.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br/>
<br/>

<img src="https://i.imgur.com/Prfedoh.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br/>
<br/>
Setting up a new virtual machine for the user I created, I add them to the domain using the same steps as the other user.
<img src="https://i.imgur.com/ulLShXG.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br/>
<br/>
After restarting I hit other user and login using the username and password I created for the new user. 
<img src="https://i.imgur.com/EylG7pZ.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>

<br/>
<br/>
Now we can go into File and storage services and add two new shares personal and HR
<img src="https://i.imgur.com/vZt2DRQ.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br/>
<br/>
Then go back to users and computers and create two new groups inside the users folder named HR and Personal
<img src="https://i.imgur.com/egqFdpx.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br/>
<br/>
Then change the permissions of the folders to allow the group to have read/write access to the folders
<img src="https://i.imgur.com/CkKDNU4.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br/>
<br/>
Add the user to the security groups
<img src="https://i.imgur.com/0yXHSTh.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br/>
<br/>
Now we can map the drive to charles personal computer
<img src="https://i.imgur.com/Ap6p5ZI.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br/>
<br/>
Go back to users and computers and in charles properties, connect it to the personal folder
<img src="https://i.imgur.com/QJeXihe.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br/>
<br/>
Here we can see both the personal and HR folder show up on charles computer.
<img src="https://i.imgur.com/dPn5lTY.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br/>
<br/>
</p>
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
