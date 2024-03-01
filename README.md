# A-day-in-the-life-of-a-Windows-Sysadmin
<h3>Task 1: Create a GPO - Disable Local Link Multicast Name Resolution (LLMNR)</h3>  

Since this task deals with Active Directory Group Policy Objects, you'll work in your nested Windows Server machine.  

Create a Group Policy Object that prevents your domain-joined Windows machine from using LLMNR. To do so, complete the following steps:  

 &emsp;&emsp;1. On the top right of the Server Manager screen, open the Group Policy Management tool to create a new GPO.  
 
 &emsp;&emsp;2. Right-click Group Policy Objects and select New.  

 &emsp;&emsp;3. Name the Group Policy Object No LLMNR.  
 
 &emsp;&emsp;4. Right-click the new No LLMNR GPO listing and select Edit to open the Group Policy Management Editor and find policies.  
 
 &emsp;&emsp;5. In the Group Policy Management Editor, you want the policy at the following path: Computer Configuration\Policies\Administrative Templates\Network\DNS Client.  
 
 &emsp;&emsp;Find the policy called Turn Off Multicast Name Resolution.  
 
 &emsp;&emsp;Enable this policy.  
 
 Exit the Group Policy Management Editor and link the GPO to the GC Computers organizational unit that you previously created.  
 
![GPOs](https://github.com/tjbuckley94/A-day-in-the-life-of-a-Windows-Sysadmin/assets/124013280/1a516e95-9b27-4d6f-a57b-288fab8adada)
  
<h3>Task 2: Create a GPO - Account Lockout</h3>  
Work within your nested Windows Server machine again to create another Group Policy Object. Create what you believe to be a reasonable account lockout Group Policy for the Windows 10 machine.  

 &emsp;&emsp;Name the Group Policy Object Account Lockout.  

 &emsp;&emsp;You can use Microsoft's 10/15/15 recommendation if you'd like.  

 &emsp;&emsp;When editing policies for this new GPO, keep in mind that you want computer configuration policies to apply to your GC Computers OU. Also, these policies involve Windows security settings and accounts.  

 &emsp;&emsp;Don't forget to link the GPO to your GC Computers organizational unit.  

![Account Lockout Policies](https://github.com/tjbuckley94/A-day-in-the-life-of-a-Windows-Sysadmin/assets/124013280/5c07c024-1738-476e-8203-c0db5ffa539b)  

<h3>Task 3: Create a GPO - Enabling Verbose PowerShell Logging and Transcription</h3>  

For this task, work in your Windows Server machine. Create a Group Policy Object to enable PowerShell logging and transcription. This GPO will combine multiple policies into one, although they are all under the same policy collection.  

1. Name the Group Policy Object PowerShell Logging  
2. Enable Turn on Module Logging  
3. Enable the Turn on PowerShell Script Block Logging policy  
4. Enable the Turn on Script Execution policy
5. Enable the Turn on PowerShell Transcription policy
6. Leave the Set the default source path for Update-Help policy as Not configured
7. Link this new PowerShell Logging GPO to the GC Computers OU

![Windows PowerShell policies](https://github.com/tjbuckley94/A-day-in-the-life-of-a-Windows-Sysadmin/assets/124013280/b5dbd001-239c-496b-9ecf-a98ecf38d4e0)  

<h3>Task 4: Create a Script - Enumerate Access Control Lists</h3>
Create a PowerShell script that will enumerate the Access Control List of each file or subdirectory within the current working directory.  
 &emsp;&emsp;$directory = Get-ChildItem .\  
 
 &emsp;&emsp;foreach ($item in $directory) {    
 &emsp;&emsp;Get-Acl $item  
 &emsp;&emsp;}  

