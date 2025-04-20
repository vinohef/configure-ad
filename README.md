<p align="center">
<img src="https://i.imgur.com/pU5A58S.png" alt="Microsoft Active Directory Logo"/>
</p>

<h1>On-premises Active Directory Deployed in the Cloud (Azure)</h1>
This tutorial outlines the implementation of on-premises Active Directory within Azure Virtual Machines.<br />


<h2>Video Demonstration</h2>

- ### [YouTube: How to Deploy on-premises Active Directory within Azure Compute](https://www.youtube.com)

<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Active Directory Domain Services

<h2>Operating Systems Used </h2>

- Windows Server 2022
- Windows 10 (21H2)

<h2>Deployment and Configuration Steps</h2>

- Step 0: Setup Domain controller and Client-1
- Step 1: Install Active directory on DC
- Step 2: Create a Domain Admin user within the domain
- Step 3: Join Client-1 to the domain
- Step 4: Setup Remote desktop for non-admin users on Client-1

<h2>Deployment and Configuration Steps</h2>
Step 0: Setup Domain controller and client
Create a resource group
<p>
<img src="https://i.imgur.com/ssQA9XK.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Doesn't matter what you name it. I'm naming this one Active-Directory for the sake of the project.
</p>
<br />
Create a Virtual Network
<p>
<img src="https://i.imgur.com/uJayJdD.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
</p>
<br />
Create a Virtual Machine (You may want to name it dc-1). Make sure when choosing the image you choose "Windows server 2022"
<p>
<img src="https://i.imgur.com/XEEV5Lp.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
You may want to name it dc-1. Make sure when choosing the image you choose "Windows server 2022"
</p>
<br />

Once the VM is done being made (you'll get a notification when its done), set the domain controller to have a static IP address.

<p>
<img src="https://i.imgur.com/eVzgBSG.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
</p>
<br />

<p>
<img src="https://i.imgur.com/bI5fdVV.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
</p>
<br />



<p>
<img src="https://i.imgur.com/Yk3pPJ0.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>

</p>
<br />



<p>
<img src="https://i.imgur.com/Pbos67O.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
We do this because our DC is going to act as a DNS. Note the private IP address because we'll need this in a sec.
</p>
<br />

Once the VM is finished log into it and disable windows firewall.

<p>
<img src="https://i.imgur.com/slDrTuS.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
</p>
<br />



<p>
<img src="https://i.imgur.com/lyGLfSj.png" height="45%" width="45%" alt="Disk Sanitization Steps"/>
</p>
<p>
</p>
<br />



<p>
<img src="https://i.imgur.com/EEE8ACo.png" height="45%" width="45%" alt="Disk Sanitization Steps"/>
</p>
<p>
</p>
<br />



<p>
<img src="https://i.imgur.com/0NvtaDl.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
</p>
<br />



<p>
<img src="https://i.imgur.com/ZkWnn6E.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
</p>
<br />

Setup Client-1

<p>
<img src="https://i.imgur.com/XEEV5Lp.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Use a windows 10 image and make sure its in the same region as DC.
</p>
<br />



After Client-1 is setup change its dns settings to DC-1 private ip address.

<p>
<img src="https://i.imgur.com/inM7Mmy.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
</p>
<br />



<p>
<img src="https://i.imgur.com/jVqUSq9.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
</p>
<br />



<p>
<img src="https://i.imgur.com/lvkpcpK.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
</p>
<br />



<p>
<img src="https://i.imgur.com/jVqUSq9.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
</p>
<br />



<p>
<img src="" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
</p>
<br />



<p>
<img src="https://i.imgur.com/PR6XPfC.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
</p>
<br />



<p>
<img src="https://i.imgur.com/uMMRAMo.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Make sure you click save.
</p>
<br />

<p>
Open powershell as an admin and type "ipconfig /all"
</p>

<p>
<img src="https://i.imgur.com/3SJtooq.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
It should list the private IP of DC-1 for a DNS server.
<p>
</p>
<br />

Try to ping DC-1 private ip from client-1

<p>
<img src="https://i.imgur.com/bKijfLo.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
If the pings are successful then step 0 is finished.
</p>
<br />
<h2></h2>
Step 1: Installing Active Directory on DC
Inside Server Manager
<p>
<img src="https://i.imgur.com/4EGF7b3.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
</p>
<br />



<p>
<img src="https://i.imgur.com/LsEdtrN.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Select "Next" at the bottom until you get to the "Sever Roles" page
</p>
<br />


Click install
<p>
<img src="https://i.imgur.com/54J5DCt.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>

</p>
<br />



<p>
<img src="https://i.imgur.com/k7uYmy9.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>

</p>
<br />

Now we promote to DC and setup a new forest. We'll use "mydomain.com" in this example

Inside server manager
<p>
<img src="https://i.imgur.com/zCeI0ao.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
</p>
<br />




<p>
<img src="https://i.imgur.com/ARap9UH.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
</p>
<br />




<p>
<img src="https://i.imgur.com/sPQ3HNm.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
</p>
<br />




<p>
<img src="https://i.imgur.com/p48SO4n.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
</p>
<br />




<p>
<img src="https://i.imgur.com/sbb81dh.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Wont really be using this but make note of this anyway.
</p>
<br />




<p>
<img src="https://i.imgur.com/n908eax.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Uncheck "Create DNS delegation", hit next.
</p>
<br />




<p>
<img src="https://i.imgur.com/frdHdvp.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
After you finish installing everything your VM will restart. When you log back in you'll now have to log in as domain\username (ex: mydomain.com\labuser) because this VM is a DC now. 
</p>
<br />

<p>
Once you've logged back into your DC you're done with step 1.
</p>
<h2></h2>
Step 2: Create a Domain Admin user within the domain

Inside your DC

<p>
<img src="https://i.imgur.com/f8HZSbr.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
</p>
<br />




<p>
<img src="https://i.imgur.com/D6jhoCv.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
</p>
<br />




<p>
<img src="https://i.imgur.com/qrvZAUk.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Right click
</p>
<br />




<p>
<img src="https://i.imgur.com/lJO8Kka.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
</p>
<br />


We're creating 2 of these

<p>
<img src="https://i.imgur.com/Xu5fqxX.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
</p>
<br />



<p>
<img src="https://i.imgur.com/gpIkZz0.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
This is where we'll put our admin user
</p>
<br />




<p>
<img src="https://i.imgur.com/fwdPr7g.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
</p>
<br />




<p>
<img src="https://i.imgur.com/oNUXsXQ.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
This info doesnt really matter just make sure you remember the credentials
</p>
<br />




<p>
<img src="https://i.imgur.com/VaQX6tO.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
</p>
<br />




<p>
<img src="https://i.imgur.com/fzTCUyI.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>

</p>
<br />



<p>
<img src="https://i.imgur.com/xjCLi4L.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>

</p>
<br />



<p>
<img src="https://i.imgur.com/WQkFDUl.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>

</p>
<br />



<p>
<img src="https://i.imgur.com/IIIak3g.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>

</p>
<br />



<p>
<img src="https://i.imgur.com/A9n6IfM.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
After this Step 2 is done!
</p>
<br />
<h2></h2>

Step 3: Joining client-1 to the domian
Inside client-1 VM

<p>
<img src="https://i.imgur.com/slDrTuS.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>

</p>
<br />



<p>
<img src="https://i.imgur.com/knIhdz7.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>

</p>
<br />



<p>
<img src="https://i.imgur.com/uB89oVN.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>

</p>
<br />



<p>
<img src="https://i.imgur.com/PHOM2PW.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>

</p>
<br />



<p>
<img src="https://i.imgur.com/U85dBl7.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Enter the password for the admin account 
</p>
<br />



<p>
<img src="https://i.imgur.com/OyTf3IN.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>

</p>
<br />



<p>
<img src="https://i.imgur.com/RHGHxoZ.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Drag client 1 into the "_clients" OU, step 3 is done.
</p>
<br />

<h2></h2>

Step 4: Setup Remote desktop for non-admin users on Client-1

using client VM as the admin account made earlier 
<p>
<img src="https://i.imgur.com/slDrTuS.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>

</p>
<br />



<p>
<img src="https://i.imgur.com/knIhdz7.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>

</p>
<br />



<p>
<img src="https://i.imgur.com/fk1cKvb.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>

</p>
<br />



<p>
<img src="https://i.imgur.com/F5TjbiP.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>

</p>
<br />



<p>
<img src="https://i.imgur.com/yiTFChq.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>

</p>
<br />



<p>
<img src="https://i.imgur.com/Lqj7hgw.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>

</p>
<br />



<p>
<img src="https://i.imgur.com/dzgQCBU.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Step 4 is complete
</p>
<br />

<h2></h2>
Step 5: create a bunch of users using powershell
<p>
<img src="" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>

</p>
<br />



<p>
<img src="" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>

</p>
<br />



<p>
<img src="" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>

</p>
<br />



<p>
<img src="" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>

</p>
<br />



<p>
<img src="" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>

</p>
<br />



<p>
<img src="" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>

</p>
<br />



<p>
<img src="" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>

</p>
<br />



<p>
<img src="" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>

</p>
<br />




