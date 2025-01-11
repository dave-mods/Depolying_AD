# Depolying AD
![image](https://github.com/user-attachments/assets/0d4e78e2-5b21-4865-af72-07242082ffb4)

# <b>Description<b/>
For this portion of the Active Directory project we will install Active Directory on the domain controller, create a domain admin, and join the client VM to the domain.
# <b>Environments And Utilities Used<b/>
 - Microsoft Azure
 - Virtual Machines
 - Remote Desktop Connection
 - Active Directory
# <b>Operating Systems Used<b/>
 - Windows Server
 - Windows 10
# <b>Project Walk-through<b/>
In Order to deploy AD start in dc-1. If Server Manager Dashboard isnt up bring it up by searching Server Manager in the search bar at the bottom.
![image](https://github.com/user-attachments/assets/c466a233-b23d-4a7d-b1a9-bfdd935d3643)

Inside of Server Manager click Add roles and features, then click Next 2x till you see Select destination server. The only option should be dc-1. Then Next again.
![image](https://github.com/user-attachments/assets/e1c6c6f6-689e-48dc-8db3-ab758fd3ded6)

Next on the Server Roles tab we want to pick Active Directory Domain Services, and pick Add Features. Then Next 2x. At the confirmation check the Restart if required box and hit Yes, then Install. When Done click Close.
![image](https://github.com/user-attachments/assets/be0175dc-3955-46a7-9848-63f43e9c961e)
![image](https://github.com/user-attachments/assets/45d3672c-0803-427a-a45c-a9bb50b72c5b)

Our next step after we just installed AD is to promote dc-1 to be a actual Domain Controller. We are going to need to configure it in a new Forest using "mydomain.com". It can be named anything this is just easy to remember. To do this click the Flag in the top right with the yellow sign. Select Promote this server to a domain controller.
![image](https://github.com/user-attachments/assets/52589cae-95f4-428d-8bbd-4e3d87859939)

In this next window select Add a new forest, then enter mydomain.com then hit Next. In the next window make the password "Password1". Leave the DNS Options box UNCHECKED and Next till the end then Install. Your dc-1 VM will restart.
![image](https://github.com/user-attachments/assets/4c93a4d0-449e-4a39-9629-776f2da4dbe5)
![image](https://github.com/user-attachments/assets/bd61c30b-46ba-4994-a241-7856847edbc6)
![image](https://github.com/user-attachments/assets/b35d131b-e62a-4196-a5e4-f4ebc0605ce4)

When your dc-1 VM restarts remote back in but here is where our login changes because it is now setup as a Domian Controller. We now have to login as "mydomain.com\labuser". Our password stays the same. So now we are siging in as a user on the domain instead of a local user.
![image](https://github.com/user-attachments/assets/b525b281-3c8a-4f77-afd8-72fc1ca04888)

Now that we are signed back in to dc-1, go to the search bar in the bottom and type in "Active Directory Users and Computers". 
![image](https://github.com/user-attachments/assets/f3f508a2-de18-4142-a9c8-a3c9cf61bb67)

















