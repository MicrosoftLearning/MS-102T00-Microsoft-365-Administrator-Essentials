---
lab:
  title: Learning Path 3 - Lab 3 - Exercise 1 - Prepare for Identity Synchronization
  description: In this exercise, you will prepare for identity synchronization by configuring the UPN suffix for Adatum's on-premises domain, identifying and fixing directory errors using Active Directory tools, and preparing the on-premises environment for Microsoft Entra Connect Sync.
  duration: 15 minutes
  level: 300
  islab: true
  primarytopics:
    - Microsoft 365
    - Microsoft Entra ID
---

# Learning Path 3 - Lab 3 - Exercise 1 - Prepare for Identity Synchronization  

As in the previous lab exercises, you will take on the role of Holly Dickson, Adatum Corporation’s new Microsoft 365 Administrator. Adatum has recently subscribed to Microsoft 365, and you have been tasked with deploying the application in Adatum’s virtualized lab environment. In this lab, you will perform the tasks necessary to manage your Microsoft 365 identity environment using both the Microsoft 365 admin center and Windows PowerShell. 

During this exercise you will set up and manage Microsoft Entra Connect. You will create on-premises users and validate the sync process so that their identity is moved to the cloud. Some of the user and group maintenance steps may feel familiar from previous exercises; however, in this case they are needed to validate the synchronization process.

### Task 1: Configure your UPN suffix

In Active Directory, the default User Principal Name (UPN) suffix (i.e. the tenant prefix) is the DNS name of the domain where the user account was created. The Microsoft Entra Connect wizard uses the userPrincipalName attribute, or it lets you specify the on-premises attribute (in a custom installation) to be used as the user principal name in Microsoft Entra ID. This is the value that is used for signing into Microsoft Entra ID. 

If you recall, your VM environment was created by your lab hosting provider with an on-premises domain titled **adatum.com**. This domain included several on-premises user accounts, such as Holly Dickson, Laura Atkins, and so on. Then in an earlier lab in this course, you created a custom, accepted domain for Adatum titled **xxxUPNxxx.xxxCustomDomainxxx.xxx** (where xxxUPNxxx was the unique UPN name assigned to your tenant, and xxxCustomDomainxxx.xxx was the name assigned to the domain by your lab hosting provider).

In this task, you will use PowerShell to change the user principal name of the domain for the entire Adatum Corporation by replacing the originally established **adatum.com** domain with the custom **xxxUPNxxx.xxxCustomDomainxxx.xxx** domain. In doing so, you will update the UPN suffix for the primary domain and the UPN on every on-premises user account in AD DS with **@xxxUPNxxx.xxxCustomDomainxxx.xxx**. 

A company may change its domain name for a variety of reasons. For example, a company may purchase a new domain name, or a company may change its name and it wants its domain name to reflect the new company name, or a company may be sold and it wants its domain name to reflect the new parent company’s name. Regardless of the underlying reason, the goal of changing a domain name is typically to change the domain name on each user’s email address. 

For this lab, Adatum has purchased the new xxxUPNxxx.xxxCustomDomainxxx.xxx domain (provided by your lab hosting provider); therefore, it wants to change the domain name of all its users’ email addresses from @adatum.com to @xxxUPNxxx.xxxCustomDomainxxx.xxx.

1. Switch to **LON-DC1**, which is Adatum's domain controller, where you should still be logged in as **ADATUM\Administrator** and password **Pa55w.rd**. 

2. If **Windows PowerShell** is still open, then select the **PowerShell** icon on your taskbar; otherwise, you must open **Windows PowerShell** by selecting the magnifying glass (**Search**) icon on the taskbar, typing **power** in the Search box that appears,  right-clicking on **Windows PowerShell** (do not select Windows PowerShell ISE), and selecting **Run as administrator** in the drop-down menu. When Windows PowerShell opens, maximize the window.

3. Using **Windows PowerShell**, you must replace the on-premises **adatum.com** domain with the **xxxUPNxxx.xxxCustomDomainxxx.xxx** domain (where you will replace xxxUPNxxx with the unique UPN name assigned to your tenant, and you will replace xxxCustomDomainxxx.xxx with your lab hosting provider's custom domain). In doing so, you will update the UPN suffix for the primary domain and the UPN on every user in AD DS with **@xxxUPNxxx.xxxCustomDomainxxx.xxx**.

	>In the following PowerShell command, the **Set-ADForest** cmdlet modifies the properties of an Active Directory forest, and the **-identity** parameter specifies the Active Directory forest to modify. To perform this task, run the following command to set the **UPNSuffixes** property for the **adatum.com** forest (remember to change xxxUPNxxx to your unique UPN name and xxxCustomDomainxxx.xxx to your lab hosting provider's custom domain name):

	```powershell
	Set-ADForest -identity adatum.com -UPNSuffixes @{replace="xxxUPNxxx.xxxCustomDomainxxx.xxx"}
	```

4. You must then run the following command that changes all existing adatum.com accounts to the new UPN @xxxUPNxxx.xxxCustomDomainxxx.xxx domain (remember to change xxxUPNxxx to your unique UPN name and xxxCustomDomainxxx.xxx to your lab hosting provider's custom domain name):

	```powershell
	Get-ADUser -Filter * | ForEach-Object { Set-ADUser $_  -UserPrincipalName ($_.SamAccountName + "@xxxUPNxxx.xxxCustomDomainxxx.xxx" )}
	```

5. You will continue using PowerShell on LON-DC1 in the next task.


### Task 2: Prepare problem user accounts   

Integrating your on-premises Active Directory with Microsoft Entra ID makes your users more productive by providing a common identity for accessing both cloud and on-premises resources. However, errors can occur when identity data is synchronized from Windows Server Active Directory (AD DS) to Microsoft Entra ID. 

For example, two or more objects may have the same value for the **ProxyAddresses** attribute or the **UserPrincipalName** attribute in on-premises Active Directory. There are a multitude of different conditions that may result in synchronization errors. Organizations can discover and correct these errors using Active Directory tools such as Windows PowerShell and Active Directory Users and Computers. (Microsoft's IdFix tool was previously used for this discovery and remediation, but it's being retired.) 

In this task, you will run a script that breaks an on-premises user account. As part of your Adatum pilot project, you are purposely breaking an identity object so that you can identify and fix the broken account in the next task. 

1. On your Domain Controller VM (LON-DC1), in the Windows PowerShell window, run the following command to change the root source to **C:\labfiles** so that you can access any files from that location: <br/>

	```cmd
	CD C:\labfiles\
	```

3. Enter the following command that runs a PowerShell script that creates a problem user account. This script, which is stored in the C:\labfiles folder, will purposely create an issue with the userPrincipalName for Klemen Sic's on-premises user account; this will enable you to troubleshoot this account in the next task.  <br/>

	```powershell
	.\CreateProblemUsers.ps1
	```

	
	>**Important:** Wait until the script has finished before proceeding to the next task. This Windows PowerShell script will make the following change in AD DS to a single account, which you'll troubleshoot in the next task:

	- **Klemen Sic**. Update the userPrincipalName for Klemen to include an extra "@" character. 

4. Minimize your Windows PowerShell window.


### Task 3: Identify and fix directory errors 

In this task you will find and fix the userPrincipalName error that you purposely introduced for Klemen Sic in the previous task, before you synchronize identity data from your on-premises environment to Microsoft Entra ID.

>**Note:** Earlier versions of this lab used the **IdFix** directory synchronization error remediation tool for this task. IdFix is being retired, so this task uses **Active Directory** directly instead - Windows PowerShell to find the error, and either Windows PowerShell or **Active Directory Users and Computers** to fix it. This reflects how you would remediate directory objects in a current environment.

1. You should still be logged into **LON-DC1** as the **Administrator** from the prior task. 

2. If **Windows PowerShell** is not already open, select the **PowerShell** icon on the taskbar (or open **Windows PowerShell** as an administrator). Maximize the window.

3. The script you ran in the previous task broke Klemen Sic's userPrincipalName by adding an extra **@** character, producing a value that contains **@@**. Run the following command to find any user whose userPrincipalName contains a double **@**: <br/>

	```powershell
	Get-ADUser -Filter * -Properties UserPrincipalName | Where-Object { $_.UserPrincipalName -like "*@@*" } | Format-Table Name, SamAccountName, UserPrincipalName
	```

	The results should list a single user - **Klemen Sic** - and display his malformed userPrincipalName, which contains **@@**.

You can fix Klemen's userPrincipalName using either **Windows PowerShell** (Option A) or **Active Directory Users and Computers** (Option B). Complete only one of the two options.

**Option A - Fix the error using Windows PowerShell**

4. Run the following command to rebuild Klemen's userPrincipalName from his SamAccountName and the correct UPN suffix, which removes the extra **@** character (replace **xxxUPNxxx.xxxCustomDomainxxx.xxx** with the custom domain you configured in Task 1): <br/>

	```powershell
	Get-ADUser -Filter * -Properties UserPrincipalName | Where-Object { $_.UserPrincipalName -like "*@@*" } | ForEach-Object { Set-ADUser $_ -UserPrincipalName ($_.SamAccountName + "@xxxUPNxxx.xxxCustomDomainxxx.xxx") }
	```

5. Run the command from step 3 again. This time no users should be returned, which confirms that Klemen's userPrincipalName error is fixed. Skip Option B (step 6) and continue to step 7.

**Option B - Fix the error using Active Directory Users and Computers**

6. If you'd rather use the graphical tools, fix the error as follows (skip this step if you already completed Option A): <br/>

	a. Open **Server Manager**, select **Tools**, and then select **Active Directory Users and Computers**. <br/>

	b. Select the **View** menu and verify that **Advanced Features** is enabled (select it if it isn't). This makes the **Attribute Editor** tab available on user accounts. <br/>

	c. Right-click **adatum.com** and select **Find**. In the **Name** field, type **Klemen**, select **Find Now**, and then double-click **Klemen Sic** in the search results. <br/>

	d. In the **Klemen Sic Properties** window, select the **Attribute Editor** tab. Locate the **userPrincipalName** attribute and confirm that its value contains **@@**. <br/>

	e. Select **userPrincipalName**, select **Edit**, remove the extra **@** so that the value contains only a single **@** separating the logon name from the domain suffix, and then select **OK**. <br/>

	f. Select **OK** to close the **Klemen Sic Properties** window, and then close **Active Directory Users and Computers**.

7. Two other users - **An Dung Dao** and **Ngoc Bich Tran** - have directory errors that were already present in the environment. **Leave these errors in place.** In the next exercise, you'll see how the Microsoft Entra Connect Sync process reports these unresolved errors when it attempts to synchronize these accounts to the cloud. 

8. Leave your PowerShell window (and any open tools) available. You'll continue on LON-DC1 in the next exercise.

# Proceed to Lab 3 - Exercise 2
 
