<p align="center">
<img src="https://i.imgur.com/pvZvAyx.png"/>
</p>

<h1>Network File Shares and Permissions</h1>
This tutorial outlines the Network File Shares and Permissions within Windows 10 Virtual Machine in Microsoft Azure.<br />


<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop

<h2>Operating Systems Used </h2>

- Windows 10</b> (21H2)

<h2>Why use Network File Shares and Permissions?</h2>

  - Network file shares and permissions help people on a network work together on files in an organized and secure way. They make sure everyone has the right access, keep data safe, and are flexible enough to grow with the organization's needs.

<h2>Installation Steps</h2>

<p>
<img src="https://i.imgur.com/81IQE3d.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
  
  - Connect/log into DC-1 as your domain admin account (mydomain.com\jane_admin)
  - Connect/log into Client-1 as a normal user (mydomain\<someuser>)
  - On DC-1, on the C:\ drive, create 4 folders: “read-access”, “write-access”, “no-access”, “accounting”
</p>
<br />

<p>
<img src="https://i.imgur.com/skWdEWE.png" height="60%" width="60%" alt="Disk Sanitization Steps"/> <img src="https://i.imgur.com/9ObcAmm.png" height="30%" width="30%" alt="Disk Sanitization Steps"/>
</p>
<p>
</p>
<br />

<p>
<img src="https://i.imgur.com/UiQEDCQ.png" height="30%" width="30%" alt="Disk Sanitization Steps"/> <img src="https://i.imgur.com/KANt1k6.png" height="30%" width="30%" alt="Disk Sanitization Steps"/> <img src="https://i.imgur.com/0IssZv2.png" height="30%" width="30%" alt="Disk Sanitization Steps"/>
</p>
<p>

  - Set the following permissions (share the folder) for the “Domain Users” group:
  - Folder: “read-access”, Group: “Domain Users”, Permission: “Read”
  - Folder: “write-access”,  Group: “Domain Users”, Permissions: “Read/Write”
  - Folder: “no-access”, Group: “Domain Admins”, “Permissions: “Read/Write”
</p>
<br />

<p>
<img src="https://i.imgur.com/bX90P1m.png" height="40%" width="40%" alt="Disk Sanitization Steps"/> <img src="https://i.imgur.com/iwuwew4.png" height="40%" width="40%" alt="Disk Sanitization Steps"/> <img src="https://i.imgur.com/JQwMtbT.png" height="40%" width="40%" alt="Disk Sanitization Steps"/>
</p>
<p>

  - On Client-1, navigate to the shared folder (start, run, \\dc-1)
  - Try to access the folders you just created.
</p>
<br />

<p>
<img src="https://i.imgur.com/fhJmxD9.png" height="40%" width="40%" alt="Disk Sanitization Steps"/> <img src="https://i.imgur.com/ksilc2f.png" height="40%" width="40%" alt="Disk Sanitization Steps"/> <img src="https://i.imgur.com/yNJKQZc.png" height="40%" width="40%" alt="Disk Sanitization Steps"/>
</p>
<p>

  - Go back to DC-1, in Active Directory, create a security group called “ACCOUNTANTS”
  - On the “accounting” folder you created earlier, set the following permissions:
  - Folder: “accounting”, Group: “ACCOUNTANTS”, Permissions: “Read/Write”
</p>
<br />

<p>
<img src="https://i.imgur.com/6d4JdSs.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
  
  - On Client-1, as  <someuser>, try to access the accountants folder. It should fail.
</p>
<br />

<p>
<img src="https://i.imgur.com/GPWzCr1.png" height="50%" width="50%" alt="Disk Sanitization Steps"/> <img src="https://i.imgur.com/KMgIjSg.png" height="50%" width="50%" alt="Disk Sanitization Steps"/>
</p>
<p>

  - On DC-1, make <someuser> a member of the “ACCOUNTANTS”  Security Group
  - Sign back into Client-1 as <someuser> and try to access the “accounting” share in \\DC-1\
</p>
<br />
