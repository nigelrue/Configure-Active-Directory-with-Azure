<p align="center">
<img src="https://i.imgur.com/pU5A58S.png" alt="Microsoft Active Directory Logo"/>
</p>

<h1>On-premises Active Directory Deployed in the Cloud (Azure)</h1>
This tutorial outlines the implementation of on-premises Active Directory within Azure Virtual Machines.<br />

<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Active Directory Domain Services
- PowerShell

<h2>Operating Systems Used </h2>

- Windows Server 2022
- Windows 10 (21H2)

<h2>High-Level Deployment and Configuration Steps</h2>

- Step 1
- Step 2
- Step 3
- Step 4

<h2>Deployment and Configuration Steps</h2>

<p>
<img src="https://i.postimg.cc/Fz1nk6GZ/temp-Image-ZJh7lu.avif" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Step 1. Create a new Resource Group. Name it "RG-AD" and select region. Click "Review+Create".
</p>
<br />

<p>
<img src="https://i.postimg.cc/NMytsCr3/temp-Image-Tt3z8-G.avif" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Step 2. Create a new virtual machine using the recently created Resource Group "RG-AD" and name it VM-DC1. Select the same region and select the image: Wnidows Server 2022.
</p>
<br />

<p>
<img src="https://i.postimg.cc/d3rKd76n/temp-Image-IMODk-H.avif" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Step 3. Select a username and password and click "Review+Create".
</p>
<br />

<p>
<img src="https://i.postimg.cc/wx058Wkq/temp-Image-PPcu-ND.avif" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<img src="https://i.postimg.cc/Dy0r2qCq/temp-Imagei-Cgpet.avif" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Step 4. Create a second virtual machine using the "RG-AD" resource group and name it "Client 1" and use the image: Windows 10 Pro, Version 21H2.
</p>
<br />

<p>
<img src="https://i.postimg.cc/BQzxtXyR/temp-Imagev-Lem-IJ.avif" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Step 5. Make sure that both virtual machines are using the same virtual networks (VNETs) by verifying in the virtual machine's networking tab. Both should be using the "VM-DC1-vnet" virtual network.
</p>
<br />

<p>
<img src="https://i.postimg.cc/3R9GhRmS/temp-Image7-Cg-Gr-Y.avif" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Step 6. Select the virtual machine directory, select the domain controller virtual machine, "network settings" tab and then the network interface.
</p>
<br />

<p>
<img src="https://i.postimg.cc/BvTDhN6G/temp-Image-U9-Vtg-U.avif" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Step 7. Select "ipconfig1" under the IP Configurations list. Under "Assignment", switch from "Dynamic" to "Static" and click "Save".
</p>
<br />

<p>
<img src="https://i.postimg.cc/FzRLH4x9/temp-Image-X1ua8-S.avif" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Step 8. Connect to the virtual machine, "VM-DC1", using its public IP address and username/password.
</p>
<br />

<p>
<img src="https://i.postimg.cc/XqzyZz29/temp-Imagek-EY7-Sj.avif" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Step 9. Search for Windows Defender Firewall with Advanced Security. Navigate to the Inbound Rules and search for both: Core Networking Diagnostics-ICMP Echo Request (ICMPv4-In)'s (the Private profile and Dynamic profile). Enable rules for both.
</p>
<br />

<p>
<img src="https://i.postimg.cc/sX3WbSQG/temp-Image-V6gp-Cn.avif" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<img src="https://i.postimg.cc/1zhwcbyH/temp-Imagepf-Go-Cm.avif" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Step 10. Open Server Manager. Select  "Add Roles and Features" and click "Next". Make sure Role-based/feature based installation is selected and click "Next" and "Next" once more. 
</p>
<br />

<p>
<img src="https://i.postimg.cc/G2brd9Xs/temp-Imagefn0-INs.avif" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<img src="https://i.postimg.cc/B6N36sz7/temp-Imagej-Lv7l7.avif" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<img src="https://i.postimg.cc/PJxjv9sX/temp-Imagej-JJkk7.avif" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Step 11. Select "Active Directory Domain Services" and click "Add features". Continue with the default installation settings until the confirmation page and click "Install".
</p>
<br />

<p>
<img src="https://i.postimg.cc/1XwpwmxP/temp-Imagea-XTQJl.avif" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Step 12. Click on the flag/yellow caution icon and click "Promote this server to a domain controller".
</p>
<br />

<p>
<img src="https://i.postimg.cc/Gh00Cqqs/temp-Image7-Cma0c.avif" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Step 13. Select "Add a new forest" and choose a root domain name, "mydomain.com", and click "Next".
</p>
<br />

<p>
<img src="https://i.postimg.cc/CxLcT8Tq/temp-Imagely-Zla-B.avif" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Step 14. Choose a password and click "Next" and continue with the default installation settinigs until the option to "Install" comes up.
</p>
<br />

<p>
<img src="https://i.postimg.cc/T1dDLrcj/temp-Image-X2-Df-Zk.avif" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Step 15. Once Active Directory Domain Services is finished installing, the remote desktop connection will automatically sign out.
</p>
<br />

<p>
<img src="https://i.postimg.cc/jdNDx3KV/temp-Imagehp-JOi-Q.avif" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Step 16. Log into the domain controller virtual machine using the domain name chosen in step 13, followed by a forward slash and the username selected for the domain controller virtual machine.
</p>
<br />

<p>
<img src="https://i.postimg.cc/TPSxWGqt/temp-Imagev-Nlm-Qf.avif" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Step 17. On the Server Manager dashboard, select the Tools tab on the top right and select "Active Directory Users and Computers".
</p>
<br />

<p>
<img src="https://i.postimg.cc/tC7zBjh3/temp-Image-Odis-G0.avif" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<img src="https://i.postimg.cc/mkpyTXG1/temp-Image-Lw-Bp-Ow.avif" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Step 18. Right-click oon the newly created domain, "mydomain.com" and create two new folders; "Employees" and "Admins", by selecting "New" and then "Organizational Unit" within the Server Manager. 
</p>
<br />

<p>
<img src="https://i.postimg.cc/3wW4T8x1/temp-Imaged-Nxr-QI.avif" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<img src="https://i.postimg.cc/m2XTGQ1x/temp-Image-ULKc-UV.avif" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<img src="https://i.postimg.cc/SKGZwGjC/temp-Image-VEN0-RA.avif" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Step 19. Right-click on the newly created folder, "Admins", select "New", then "User" annd create a new user. Choose a password and continue until the option to "Finish" appears.
</p>
<br />

<p>
<img src="https://i.postimg.cc/4ds33XJj/temp-Image-Wpmgfu.avif" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<img src="https://i.postimg.cc/G22ZKfzH/temp-Image-M8-G0cg.avif" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<img src="https://i.postimg.cc/htMn0VgZ/temp-Imagexa6-RTT.avif" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<img src="https://i.postimg.cc/Kz3yFVTC/temp-Imagel-KHqrl.avif" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Step 20. To make this new user an actual admin, right-click the name, select "Propereties", then the "Member-of" tab and select "Add". Type "Domain Admins", click "Ok" and click "Apply" and then "Ok" once more. 
</p>
<br />

<p>
<img src="https://i.postimg.cc/7YjC18HQ/temp-Image-Ti-P99-N.avif" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Step 21. Logout of account and log back into the domain controller using the domain controller name plus the newly created admin user credentials. 
</p>
<br />

<p>
<img src="https://i.postimg.cc/yN17cvZb/temp-Image-F2-XLvf.avif" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Step 22. Navigate back to the Azure portal and then to the domain controller virtual machine. 
</p>
<br />

<p>
<img src="https://i.postimg.cc/mDQxn9CH/temp-Imagea3-IOTb.avif" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<img src="https://i.postimg.cc/v8tFLWQR/temp-Imagez-Wjep-B.avif" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<img src="https://i.postimg.cc/d3BbsKWQ/temp-Image-Zh2-Jn-R.avif" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<img src="https://i.postimg.cc/x8nrVd3F/temp-Imagewl0-Zqo.avif" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Step 23. Navigate to the Client 1 virtual machine. Go to the networking section, click ono the network interface and then navigate to the "DNS Servers" section. Click on "Custom" and enter in the domain controller's private IP address from step 22. Click "Save". Restart Client 1 virtual machine from the portal. 
</p>
<br />

<p>
<img src="https://i.postimg.cc/RZHWgMXn/temp-Image-Wx8yqi.avif" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Step 24. Navigate back to Remote Desktop Connection and log back into the Client 1 virtual machine using the original username/password.
</p>
<br />

<p>
<img src="https://i.postimg.cc/dVr8LmMX/temp-Imager-Jhs-JM.avif" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<img src="https://i.postimg.cc/VNFnFfkW/temp-Image-Znsd-Bp.avif" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<img src="https://i.postimg.cc/VNFnFfkW/temp-Image-Znsd-Bp.avif" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<img src="https://i.postimg.cc/vBqnp091/temp-Imagex-Fr5-ZT.avif" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<img src="https://i.postimg.cc/br4tvdmp/temp-Image-ROa1d-F.avif" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<img src="https://i.postimg.cc/BZzDpw4k/temp-Image-L0-FAdi.avif" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Step 25. Right-click the start menu and select "System". Click "Rename this PC" and then click "Change". Select "Domain" and enter the name of the root domain name created in step 13. Enter the admin user credentials created in step 19, "mydomain.com\george_admin". If done correctly, a message welcoming you to the new domain will pop up. The virtual machine will prompt for an automatically restart.
</p>
<br />

<p>
<img src="https://i.postimg.cc/y84LQNsM/temp-Image-Evwwz-F.avif" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Step 26. Navigate to Remote Desktop Connection and log into the Client 1 virtual machine using the admin user credentials. 
</p>
<br />

<p>
<img src="https://i.postimg.cc/rpzgzRJt/temp-Image-BCj-ZZh.avif" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<img src="https://i.postimg.cc/Vv9W2qY2/temp-Imagen-Xd-Djd.avif" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<img src="https://i.postimg.cc/qR3LxfWJ/temp-Image2-AUzs-U.avif" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<img src="https://i.postimg.cc/PJnM63km/temp-Imageo6-A5-OA.avif" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Step 27. Right-click the start button, navigate to "System" and then to "Remote Desktop", click "Select users that can remotely access this PC". From here, click "Add" and type in "Domain Users" and click "Ok". This will allow all user accounts access to the domain controller.
</p>
<br />

<p>
<img src="https://i.postimg.cc/YCT8Gqyn/temp-Image-OYIf-Wi.avif" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Step 28. Log into the domain controller virtual machine using the admin credentials.
</p>
<br />

<p>
<img src="https://i.postimg.cc/W3w7HmpC/temp-Image-Nr-YWo4.avif" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Step 29. Search for "Windows PowerShell ISE", right-click the app and select "Run as administrator" to be able to create new user accounts.
</p>
<br />

<p>
<img src="https://i.postimg.cc/hj8f8p4z/temp-Images-DP2-Vk.avif" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<img src="https://i.postimg.cc/Jzy0Y14W/temp-Image-Dvde-Hi.avif" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Step 30. Within PowerShell ISE, click "New Script" and paste the script in <a href="https://github.com/nigelrue/Configure-Active-Directory-with-Azure/blob/main/PowerShell%20Script">THIS DOCUMENT</a> and click "Run Script". *(Make sure the organizational unit in script line #43 matches the same one created in step 18)*
</p>
<br />

<p>
<img src="https://i.postimg.cc/15bVQgdz/temp-Imageh8m2-M7.avif" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Step 31. If done correctly, you should see the new user accounts being generated within Windows PowerShell.
</p>
<br />

<p>
<img src="https://i.postimg.cc/FFB7ydNx/temp-Image2-Oi-Wv-S.avif" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Step 32. Within Server Manager, open "Active Directory Users and Computers".
</p>
<br />

<p>
<img src="https://i.postimg.cc/Fz71tmgc/temp-Imagez-Hv4um.avif" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Step 33. Navigate to the "Employees" folder within the domain and observe the newly created user accounts.
</p>
<br />

<p>
<img src="https://i.postimg.cc/J7v2BLY2/temp-Image-Gse-MDQ.avif" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<img src="https://i.postimg.cc/brWxWmby/temp-Image6-GCP4v.avif" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Step 34. Select a random user, "bob.gog" and attempt to log into the Client 1 virtual machine using the password assigned to all accounts in the PowerShell script, "Password1".
</p>
<br />

<p>
<img src="https://i.postimg.cc/W3t5hWGV/temp-Image7a-Gbf-E.avif" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Step 35. If the login is successful, then the creation of new users within Active Directory was succesful. 
</p>
<br />

<p>
<img src="https://i.postimg.cc/52MKnmV5/temp-Imagelwx-Vhr.avif" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Step 36. Within Active Directory, the admin will be able to perform actions such as disabling an account, resetting of passwords and more.
</p>
<br />

