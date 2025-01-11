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

We will Right click mydomain.com, go down to New, then click Organizational Unit. we will do this 2x. 1st we will name "_EMPLOYEES". 2nd will be "_ADMINS". Pay very close attetion these MUST be done right or this will not work.
![image](https://github.com/user-attachments/assets/56c27378-509c-4d08-a386-85ba90915a5e)
![image](https://github.com/user-attachments/assets/8d3185cc-41c7-4f71-bae4-72df10694ce5)

Now to make a admin we will go into the _ADMINS folder, right click, go down to NEW then User. We will name the admin "Jane Doe". User name will be "jane_admin". Then hit next and we keep the password Cyberlab123!. For the lab we will check the Password never expires box. You probaly wouldnt do this in real life this is just for the lab.
![image](https://github.com/user-attachments/assets/330b44b5-ce1d-4e79-b424-2621eb630469)
![image](https://github.com/user-attachments/assets/8a457e3e-bab5-4f7d-b692-3ffdebdd1c0e)

So now that Jane had been added to the _ADMINS folder we need to make her a actual admin now. Right click Jane Doe in the _ADMINS folder and go down to Properties. In the Properties box go to "Member of" tab, hit ADD..., type in "Domain Admins" check names and it will find it then hit OK. Then Apply and then OK. Now we should see Domain Admins added to the Members of list. Now we can log out of dc-1, close the connection and log back in with jane_admin.
![image](https://github.com/user-attachments/assets/d91baf0a-39ee-481e-9234-e3f7aa9d7522)
![image](https://github.com/user-attachments/assets/ba3ee3af-f22b-411e-b4f9-0ea949c0bb2d)
![image](https://github.com/user-attachments/assets/a439b239-1dbe-4648-ba91-bbb6daee134b)

Remote Desktop back in dc-1 as "mydomain.com\jane_admin". We will use this from now on to log into dc-1.
![image](https://github.com/user-attachments/assets/441540b6-4252-4458-bd86-caf6011c4752)

Now log into client-1 VM using Remote Desktop. User name here is "labuser" and our "Cyberlab123!" password. In client-1 go to the search bar at the bottom and search "About your PC".
![image](https://github.com/user-attachments/assets/7ba2206c-b2d2-46e7-bb89-fcaf4b5c051d)

Go to "Rename this PC (advanced) then down to "To rename this computer...." and hit "Change" then Domain, here we will enter "mydomain.com" and hit OK. Here we will use mydomain.com\jane_admin and the password as this account will give us the permission we need to be on that domian. We will have to restart the client-1 VM.
![image](https://github.com/user-attachments/assets/5080137f-dda0-43d1-9bd5-7378123a844e)
![image](https://github.com/user-attachments/assets/f58fdad4-1187-4819-b40e-e975c5446837)

Go back to the dc-1 VM we have open and we will verify that client-1 is now on the domain. To do this go back to the Active Directory Users and Computers. Expand mydomain.com, go to computers and we will see client-1.
![image](https://github.com/user-attachments/assets/634e6d3d-30c4-442e-a04a-5fc90f858137)

Now we will create a new OU called "_CLIENTS". Go back into the Computers file and drag client-1 from there to the new _CLIENTS folder
![image](https://github.com/user-attachments/assets/c638502b-5881-4b49-a3d4-997778aa0fd7)

# <b>We have fully built and deployed AD<b/>
We have successfully installed AD on the domain controller, created a domain admin, and joined the client VM to the domain. Next we will create users in Powershell by running a script and then manage the accounts and group policy.
