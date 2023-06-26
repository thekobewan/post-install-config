<p align="center">
<img src="https://i.imgur.com/Clzj7Xs.png" alt="osTicket logo"/>
</p>

<h1>osTicket - Post-Install Configuration</h1>
This tutorial outlines the post-install configuration of the open-source help desk ticketing system osTicket.<br />


<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Internet Information Services (IIS)

<h2>Operating Systems Used </h2>

- Windows 10</b> (21H2)

<h2>Post-Install Configuration Objectives</h2>

1. Configure Roles
2. Configure Departments
3. Configure Teams
4. Allow Anyone to Create Tickets
5. Configure Agents (employees)
6. Configure Users (customers)
7. Configure SLA
8. Configure Help Topics

<h2>Prerequisites</h2>

In the previous project, we installed osTicket and the prerequisites required for it to run properly. In order to complete this project, osTicket must already be installed. Review the other tutorial [here](https://github.com/thekobewan/osticket-prereqs) before attempting this one.

<h2>Configuration Steps</h2>

<h3>Access osTicket</h3>

1. Navigate to Microsoft Azure portal > select ‘Virtual Machines’ > select ‘VM-osTicket > copy the Public IP address (Example: 20.14.93.5)
2. Open Microsoft Remote Connection (for Windows) or launch Microsoft Remote Desktop app (for MacOS) > paste Public IP address > log in with the username/password created in step 1 of the previous [lab](https://github.com/thekobewan/osticket-prereqs)
3. Navigate to the URL for admin login:  http://localhost/osTicket/scp/login.php
4. Login with the admin username & password created in step 3 of the previous lab. (Example: darin_admin)

<br>

<img src="https://i.imgur.com/e6mEVrm.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<img src="https://i.imgur.com/yD891Ta.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>


<br>

<h3>Admin vs Agent Portal</h3>

<p>Within osTicket, there is both an Admin Portal and an Agent Portal. We're going to be working with both portals.</p>

<p>The Admin Portal is designed for administrators to manage the osTicket ticketing system. It provides access to various administrative functions such as configuring support queues, managing staff members and permissions, and customizing system settings to efficiently handle and resolve customer support tickets.</p>

<p>The Agent Portal within osTicket is a web-based interface designed for support agents or staff members. It allows agents to access and manage support tickets assigned to them, communicate with customers, update ticket statuses, and collaborate with other agents to provide timely and effective customer support within the osTicket ticketing system.</p>

<br>

<h3>1: Configure Roles</h3>

<strong>What are roles in osTicket?</strong>

<p>According to osTicket:</p>
  <p>"Roles are the permissions granted to Agents per Department that they have access to. Each Role has a set of permissions that can be checked/unchecked for agents given that Role in association with a Department they have access to. An unlimited number of roles can be created and assigned to Agents with access to various departments." -osTicket</p>
  
  osTicket documentation on Roles: https://docs.osticket.com/en/latest/Admin/Agents/Roles.html
  
  <p>We’re going to create a role called ‘Supreme Admin' and anyone with this title of Supreme Admin has access to do literally anything.</p>
  
  1. Navigate to 'Admin Panel' within osTicket > Select 'Agents' > Select 'Roles' > Select 'Add a New Role'
  2. Give the name: 'Supreme Admin' > Navigate to ‘Permissions’ tab
  3. For the fun of it, we’re going to allow them to do everything: Check all the boxes [X] under the ‘Tickets’, ‘Tabs’, and ‘Knowledge Base’ > select 'Add Role'

<br>

<img src="https://i.imgur.com/lPmZ75w.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<img src="https://i.imgur.com/Rf686pZ.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<img src="https://i.imgur.com/LLYZLar.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>

<br>

<h3>2: Configure Departments</h3>

<Strong>What are Departments in osTicket?</strong>

<p>In osTicket, departments are organizational units or groups that are created to manage and categorize support tickets based on different criteria. They represent different areas or teams within an organization that handle specific types of inquiries or provide support for distinct products or services. Tickets can be assigned to specific departments, allowing for efficient routing and distribution of tickets to the appropriate teams or individuals for effective resolution.</p>

osTicket documentation on Departments: https://docs.osticket.com/en/latest/Admin/Agents/Departments.html

1. Navigate to Admin Panel > Select 'Agents' > Select 'Departments' > Select 'Add a New Department'
2. Give the name: 'System Administrators' 
3. There’s many settings inside of here, including SLA. We haven’t configured SLA yet so we’ll leave these default settings. At the bottom of the screen, select 'Create Dept'

<br>

<img src="https://i.imgur.com/EW5SMbk.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<img src="https://i.imgur.com/GzJhqAk.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>

<br>

<h3>3: Configure Teams</h3>

<Strong>What are Teams in osTicket?</strong>

<p>According to osTicket, "Teams allow you to pull Agents from different Departments and organize them to handle a specific issue or user via a Help Topic or Ticket Filter." Essentially, if you have many Departments and you want to pool the best technicians from each Department to solve a particular issue, you can do so by creating a Team within osTicket.</p>

osTicket documentation on Teams: https://docs.osticket.com/en/latest/Admin/Agents/Teams.html

1. Navigate to 'Admin Panel' > Select 'Agents' > Select 'Teams' > Select 'Add a New Team'
2. We’re going to create a Level I Support and a Level II Support. Since Level I was automatically generated, we’re going to create 'Level II Support'. We can add ourselves as part of the team for fun. 

<br>

<img src="https://i.imgur.com/sctylJ1.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<img src="https://i.imgur.com/efO4gEq.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>

<br>

<h3>4: Allow Anyone to Create Tickets</h3>

<p>We're going to alter the settings so that anyone can create a ticket, even anonymously. No one requires special authentication or permissions to create a ticket.</p>

1. Navigate to 'Admin Panel' > select 'Settings' > select 'User'
2. Make the sure the following is unchecked: [ ] “Require registration and login to create tickets”

<br>

<img src="https://i.imgur.com/Lp80F0t.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>


<br>

<h3>Item 5: Configure Agents (employees)</h3>

<strong>What are Agents in osTicket?</strong>

<p>According to osTicket, "Agents are given access to the help desk with the intent to respond and resolve the tickets." Agents are essentially the front-line employees/workers that solve technical issues and answer tickets.</p>

osTicket documentation on Agents: https://docs.osticket.com/en/latest/Admin/Agents/Agents.html

1. Navigate to 'Admin Panel' > select 'Agents' > select 'Add a New Agent'
2. For example purposes:

- Name: Jane Doe
- Email: janedoe@osticket.com
- username: jane.doe

3. Password setting: 

- select 'Set Password' > Uncheck [ ] ‘Send the agent a password reset email’
- set password: 'Password1' > Uncheck [ ]  ‘Require password change at next login’ > select ‘Set’

4. Navigate to 'Access' tab > Department: 'System Administrators' & Role: 'Supreme Admin' 
5. Navigate to 'Teams' tab > Select 'Level II Support' for Assigned Teams > select 'Create' 

<br>

<img src="https://i.imgur.com/2PQZOQ8.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<img src="https://i.imgur.com/Zna1nLT.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<img src="https://i.imgur.com/UBg9gIg.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>

<br>

5. Navigate to 'Admin Panel' > select 'Agents' > select 'Add a New Agent'
6. For example purposes:

- Name: John Doe
- Email: johndoe@osticket.com
- username: john.doe


7. Password setting:

- select 'Set Password' > Uncheck [ ] ‘Send the agent a password reset email’
- set password: 'Password1' > Uncheck [ ] ‘Require password change at next login’ > select ‘Set’

<p>**Side note: It is good practice to require users to change their password upon each login. However, for this exercise, we won't require this.</p>
<br>
  
8. Navigate to other tabs > 'Access' > Department: 'Support' & Role: 'View Only' & Extended Access: 'Support' > select 'Create'

<br>

<img src="https://i.imgur.com/OYXVn5r.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<img src="https://i.imgur.com/kswpMp3.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>

<br>

<h3>6: Configure Users (customers)</h3>

<Strong>What are Users?</strong>

<p>According to osTicket, "Users are the ticket owners of the tickets in the help desk. When a ticket is created in the help desk, the user is associated with their email address in the User Directory of the help desk." Users are the people who are experienching technical difficulties and require assistance from agents.</p>

osTicket documentation on Users: https://docs.osticket.com/en/latest/Agent/Users/User%20Directory.html

1. Navigate to 'Agent Portal'
2. Select 'Users' > Select 'Add a New User'
3. For example purposes:

- Email: karen@osticket.com
- Name: Karen Karen

<br>

<img src="https://i.imgur.com/p8mvMma.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<img src="https://i.imgur.com/LWFOYTp.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>

<br>

4. Navigate back to 'Users' > Select 'Add a New User'
5. For example purposes:

- Email: ken@osticket.com
- Name: Ken Ken

<br>

<img src="https://i.imgur.com/CUEDxBt.png.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<img src="https://i.imgur.com/FKGap9O.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>

<br>

<h3>7: Configure SLA</h3>

<Strong>What are SLAs?</strong>

<p>SLA stands for Service Level Agreement. They are meant to outline the agreed-upon levels of service that an IT department or service provider commits to deliver to its customers or end-users. These agreements typically cover areas such as response times, uptime, availability, resolution times, and other performance metrics, ensuring that IT services align with business needs and expectations. SLAs in IT help establish accountability, define service quality standards, and provide a basis for measuring and improving IT service delivery.</p>

<p>According to osTicket, "SLA Plans or Service Level Agreements, are unlimited in osTicket. The purpose of the SLA Plan is to provide a length of time in which the help desk Administrator expects tickets to be closed."</p>
  
  osTicket documentation on SLAs: https://docs.osticket.com/en/latest/Admin/Manage/SLA%20Plans.html
  
  1. Navigate to 'Admin Panel' > select 'Manage' > select 'SLA' > select 'Add a New SLA Plan'

<br>

<img src="https://i.imgur.com/F6yVy0o.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>

<br>

  2. Name: 'SEV-A'

<p>In this example, SEV-A is meant to symbolize a top-priority SLA ticket that has significant business impact if not resolved. An example of a SEV-A ticket would be the entire western region's mobile banking going down or a malware attack leaking user and company private information.</p>

- Schedule: '24/7'

<p>This means that this ticket should be solved as soon as possible within the time scope set in the next section. This means that if a ticket comes in even on the weekend, it must be resolved within the time frame created below.</p>

- Grace period: '1 hour'

<p>1 hour to solve a ticket is highly unreasonable. However, in this example, it's meant to depict how soon the ticket should be resolved or the time span granted to resolve the ticket. Since SEV-A is the most crucial type of ticket, it should be solved as soon as possible. Thus, for example, if a SEV-A ticket came in Saturday morning 8am, it should be resolved by Saturday morning 9am.</p>

- select 'Add Plan'

<br>

<img src="https://i.imgur.com/7SSCJNv.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>

<br>

3. Select 'Add new SLA Plan' 
4. Name: 'SEV-B'

- Grace period: '4 hours'
- Schedule: '24/7'

<p>SEV-B is similar to SEV-A. It has medium to high priority. In this example, due to the 24/7 setting, if a ticket came in even on the weekend such as Saturday afternoon 12pm, it should be resolved by Saturday afternoon 4pm.</p>

- select 'Add Plan'

<br>

<img src="https://i.imgur.com/0Cto6Ym.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>

<br>

5. Select 'Add new SLA Plan'
6. Name: 'SEV-C'

- Grace period: '8 hours'
- Schedule: '8 hours, Monday-Friday (normal business days)'
  
<p>This is an example of a ticket that is less urgent. If a ticket came in on the weekend, it wouldn't have to be resolved until the following business day. If a ticket came in Monday afternoon at 4pm, and the office closes at 5pm, then there'd be 7 hours remaining the following business day to resolve the ticket. If the office opens at 8am,you would have until Tuesday 3pm to resolve the ticket. </p>

<br>

<img src="https://i.imgur.com/XcO754R.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<img src="https://i.imgur.com/sTm4Hbc.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>


<br>

<h3>8: Configure Help Topics</h3>

<strong>What are Help Topics?</Strong>

<p>Help Topics are essentially common issues that may arise. Help Topics are created to help end-users/customers communicate the technical difficulties they're facing.</p>

<p>According to osTicket, "Help Topics will help streamline your end-user’s help desk experience to ensure proper assignment and prompt response to the ticket...Help Topics will determine what Department the ticket is routed to which will determine which Agents have access to the ticket. The Help Topic also can determine other configurations of the ticket, such as the ticket’s SLA (or Service Level Agreement) and priority of a ticket, i.e. Emergency to Low."</p>
  
  osTicket documentation on Help Topics: https://docs.osticket.com/en/latest/Admin/Manage/Help%20Topic.html
  
  <p>Karen and Ken, the users we just created, can choose what they need help with when filling out tickets on their end.</p>
  
  1. Navigate to 'Admin Panel' > select 'Manage' > select 'Help Topics' > select 'Add a New Help Topic'
  2. We will create the following Help Topics, leave all default settings:

- Business Critical Outage
- Personal Computer Issues
- Equipment Request
- Password Reset

<br>

<img src="https://i.imgur.com/Sr84UFm.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<img src="https://i.imgur.com/BXMEpky.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<img src="https://i.imgur.com/rhPpXkw.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<img src="https://i.imgur.com/WGl6wH0.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>

<br>

<p>Side note: It's possible to do email configuration inside of osTicket so that users can send an email and/or fill out a form. Doing so will automatically generate a ticket for Agents to access/answer. However, that won't be covered in this project.</p>

<p>Now that we have installed osTicket and configured each aspect of it, it's time to create tickets and examine the entire ticket lifecycle. You can find that tutorial here: (https://github.com/thekobewan/ticket-lifecycle/tree/main)
</p>
