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
  
  - Log in to DC-1 using your domain admin credentials (mydomain.com\jane_admin).
  - Log in to Client-1 as a regular user (mydomain<someuser>).
  - On the C:\ drive of DC-1, create four folders: "read-access," "write-access," "no-access," and "accounting."
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

  - Share the folders with the following permissions for the "Domain Users" group:
  - "read-access" folder: "Domain Users" group with "Read" permission.
  - "write-access" folder: "Domain Users" group with "Read/Write" permissions.
  - "no-access" folder: "Domain Admins" group with "Read/Write" permissions.
</p>
<br />

<p>
<img src="https://i.imgur.com/bX90P1m.png" height="40%" width="40%" alt="Disk Sanitization Steps"/> <img src="https://i.imgur.com/iwuwew4.png" height="40%" width="40%" alt="Disk Sanitization Steps"/> <img src="https://i.imgur.com/JQwMtbT.png" height="40%" width="40%" alt="Disk Sanitization Steps"/>
</p>
<p>

  - On Client-1, use the Run command (Start > Run > \\dc-1) to navigate to the shared folder. 
  - Attempt to access the created folders.
</p>
<br />

<p>
<img src="https://i.imgur.com/fhJmxD9.png" height="40%" width="40%" alt="Disk Sanitization Steps"/> <img src="https://i.imgur.com/ksilc2f.png" height="40%" width="40%" alt="Disk Sanitization Steps"/> <img src="https://i.imgur.com/yNJKQZc.png" height="40%" width="40%" alt="Disk Sanitization Steps"/>
</p>
<p>

  - Return to DC-1, access Active Directory, and establish a security group named "Accounting."
  - On the “accounting” folder you created earlier, set the following permissions:
  - Folder: “accounting”, Group: “accounting”, Permissions: “Read/Write”
</p>
<br />

<p>
<img src="https://i.imgur.com/6d4JdSs.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
  
  - On Client-1, attempt to access the "accountants" folder. This access attempt should fail.
</p>
<br />

<p>
<img src="https://i.imgur.com/GPWzCr1.png" height="50%" width="50%" alt="Disk Sanitization Steps"/> <img src="https://i.imgur.com/KMgIjSg.png" height="50%" width="50%" alt="Disk Sanitization Steps"/>
</p>
<p>

  - Log back into Client-1 using the specified user account and attempt to access the "accounting" share at \DC-1.

</p>
<br />
