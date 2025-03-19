<h1>Overview: Lab 7 RSOP, Group Policy, Disable Task Manager, Change Password and Logoff Option</h1>

This section of my home lab documentation focuses on configuring **Group Policy**, using **RSOP (Resultant Set of Policy)** to view policy results, disable **Task Manager** access as well as access to  **Logoff** and **Change Password** in a Windows environment when using Ctrl+Alt+Del keyboard shortcut. The project demonstrates how to enforce specific policies across computers and users in a domain, monitor the effective policies using RSOP reports. 

<h2>Objectives</h2>

1. **RSOP (Resultant Set of Policy):** Use RSOP to generate reports on the policies applied to computers and users.
2. **Group Policy Configuration:** Create and configure Group Policies to affect specific settings across domain-joined computers, for restrict Task Manager access.
5. **Policy Troubleshooting:** Troubleshoot and resolve policy application issues using RSOP and Group Policy tools like Group Policy Results Wizard.


<h2>Documentation</h2>

First, we will start with creating a new GPO(Group Policy Object) and call it "TaskManager".

To do this, open **Server Manager** on your Windows Server 2022. Then, select **Tools** and click on **Group Policy Management**. In the Group Policy Management console, select **Group Policy Objects** under the **junicetechie.com** domain. From here, we can configure the Group Policy to disable Task Manager and other features.



1. <p align="center">
   <img src="https://github.com/Eunice-Kamore/Group-Policy-Objects-Configuration-RSOP./blob/main/Images/1.png?raw=true" height="80%" width="80%" alt="Disk Sanitization Steps 1"/>
   <br />
   <br />
</p>

Next, right-click on Group Policy Objects and select New. Name the new policy "Task Manager". After creating it, select the Task Manager policy under Group Policy Objects. Then, go to the Delegations tab and select Add. Add Bob to grant him the necessary permissions for this policy.

2. <p align="center">
   <img src="https://github.com/Eunice-Kamore/Group-Policy-Objects-Configuration-RSOP./blob/main/Images/2.png?raw=true" height="80%" width="80%" alt="Disk Sanitization Steps 2"/>
   <br />
   <br />
</p>


3. <p align="center">
   <img src="https://github.com/Eunice-Kamore/Group-Policy-Objects-Configuration-RSOP./blob/main/Images/3.png?raw=true" height="80%" width="80%" alt="Disk Sanitization Steps 3"/>
   <br />
   <br />

Bob has been added.

4. <p align="center">
   <img src="https://github.com/Eunice-Kamore/Group-Policy-Objects-Configuration-RSOP./blob/main/Images/4.png?raw=true" height="80%" width="80%" alt="Disk Sanitization Steps 4"/>
   <br />
   <br />
</p>

Right-click on Task Manager, select Edit. 

5. <p align="center">
   <img src="https://github.com/Eunice-Kamore/Group-Policy-Objects-Configuration-RSOP./blob/main/Images/5.png?raw=true" height="80%" width="80%" alt="Disk Sanitization Steps 4"/>
   <br />
   <br />
</p>


Then go to User Configuration → Administrative Templates → System. Next, select Ctrl+Alt+Del Options.

6. <p align="center">
   <img src="https://github.com/Eunice-Kamore/Group-Policy-Objects-Configuration-RSOP./blob/main/Images/6.png?raw=true" height="80%" width="80%" alt="Disk Sanitization Steps 4"/>
   <br />
   <br />
</p>

Here we will enable “Remove Change Password” , “Remove Task Manager” and "Remove Logoff". Click on "Edit Policy" for each, one by one.

7. <p align="center">
   <img src="https://github.com/Eunice-Kamore/Group-Policy-Objects-Configuration-RSOP./blob/main/Images/19.png?raw=true" height="80%" width="80%" alt="Disk Sanitization Steps 5"/>
   <br />
   <br />
   </p>

The three options shows "Enabled".

8. <p align="center">
   <img src="https://github.com/Eunice-Kamore/Group-Policy-Objects-Configuration-RSOP./blob/main/Images/20.png?raw=true" height="80%" width="80%" alt="Disk Sanitization Steps 5"/>
   <br />
   <br />
   </p>

Then back on the Group Policy Management, drag the “Task Manager” and move it to “Sales”. Select “Yes”. The right-click on it and select "Enforced"


9. <p align="center">
   <img src="https://github.com/Eunice-Kamore/Group-Policy-Objects-Configuration-RSOP./blob/main/Images/9.png?raw=true" height="80%" width="80%" alt="Disk Sanitization Steps 6"/>
   <br />
   <br />
   </p>

Now, on Bob's account on Desktop1, open CMD and type the command gpupdate /force. This will immediately refresh the Group Policy settings for both the computer and user accounts.


10.<p align="center"> 
   <img src="https://github.com/Eunice-Kamore/Group-Policy-Objects-Configuration-RSOP./blob/main/Images/11.png?raw=true" height="80%" width="80%" alt="Disk Sanitization Steps 8"/>
   <br />
   <br />
   </p>


After updating the Group Policy on Bob's computer, right-click on the Start Button at the Taskbar, and you'll see the Task Manager but when you click on it it does not open and returns an error indicating that access has been successfully disabled.



11.<p align="center">
   <img src="https://github.com/Eunice-Kamore/Group-Policy-Objects-Configuration-RSOP./blob/main/Images/13.png?raw=true" height="80%" width="80%" alt="Disk Sanitization Steps 9"/>
   <br />
   <br />
   </p>



If we press Ctrl+Alt+Del on the virtual machine through keyboard inputs at the top menu, we will see that the Change Password and LogOff option has been removed, reflecting the changes made through Group Policy as compared to before the policies were applied.

12. <p align="center">
    <img src="https://github.com/Eunice-Kamore/Group-Policy-Objects-Configuration-RSOP./blob/main/Images/10.png?raw=true" height="80%" width="80%" alt="Disk Sanitization Steps 10"/>
    <br />
    <br />
</p>


13. <p align="center">
    <img src="https://github.com/Eunice-Kamore/Group-Policy-Objects-Configuration-RSOP./blob/main/Images/21.png?raw=true" height="80%" width="80%" alt="Disk Sanitization Steps 10"/>
    <br />
    <br />
</p>

To check which group policies have been applied to Bob's computer, open the command line and type gpresult /r. This will display the results of the Group Policy settings for both the computer and user accounts.


14. <p align="center">
    <img src="https://github.com/Eunice-Kamore/Group-Policy-Objects-Configuration-RSOP./blob/main/Images/17.png?raw=true" height="80%" width="80%" alt="Disk Sanitization Steps 11"/>
    <br />
    <br />
</p>


To generate a Group Policy report, go to Group Policy Management, right-click on Group Policy Results, and select Group Policy Results Wizard.... This will guide you through the process of generating a detailed report on the applied Group Policy settings for a user or computer.

15. <p align="center">
    <img src="https://github.com/Eunice-Kamore/Group-Policy-Objects-Configuration-RSOP./blob/main/Images/14.png?raw=true" height="80%" width="80%" alt="Disk Sanitization Steps 14"/>
    <br />
    <br />
</p>

Click Next, then select Another Computer and click Browse. Type in Desktop1 and select check names, once the name comes up, then click "OK" and "Next".


16. <p align="center">
    <img src="https://github.com/Eunice-Kamore/Group-Policy-Objects-Configuration-RSOP./blob/main/Images/15.png?raw=true" height="80%" width="80%" alt="Disk Sanitization Steps 15"/>
    <br />
    <br />
    </p>

Then on next page select junicetechie.com/b.smith, click Next, and then click Finish. This will generate a report for user Bob's Group Policy settings.

17. <p align="center">
    <img src="https://github.com/Eunice-Kamore/Group-Policy-Objects-Configuration-RSOP./blob/main/Images/18.png?raw=true" height="80%" width="80%" alt="Disk Sanitization Steps 16"/>
    <br />
    <br />
</p>

Once the result is generated, click "Finish" to view the report. 
On the report if you select the Details tab at the top of the report, it will display all of the policies that have been applied to Bob's account, giving you a detailed view of all the Group Policy settings for Bob. And you can see the TaskManager GPO that we configured appears here.

18. <p align="center">
    <img src="https://github.com/Eunice-Kamore/Group-Policy-Objects-Configuration-RSOP./blob/main/Images/16.png?raw=true" height="80%" width="80%" alt="Disk Sanitization Steps 17"/>
    <br />
    <br />
</p>


Congratulations! We have successfully explored Group Policy settings, disabled logoff functionality, removed the ability to change passwords, restricted access to Task Manager and leveraged RSOP to view GPO reports.

 👉 [Next Lab 8 : Windows 10 Remote Access using RDP, SSH and VNC tools]







