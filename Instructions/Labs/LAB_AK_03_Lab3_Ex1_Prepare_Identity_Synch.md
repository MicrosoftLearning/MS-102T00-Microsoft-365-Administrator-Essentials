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

For example, two or more objects may have the same value for the **ProxyAddresses** attribute or the **UserPrincipalName** attribute in on-premises Active Directory. There are a multitude of different conditions that may result in synchronization errors. Organizations can correct these errors by running Microsoft's IdFix tool, which performs discovery and remediation of identity objects and their attributes in an on-premises Active Directory environment in preparation for migration to Microsoft Entra ID. 

In this task, you will run a script that breaks an on-premises user account. As part of your Adatum pilot project, you are purposely breaking an identity object so that you can run the IdFix tool in the next task to see how you can fix the broken account. 

1. On your Domain Controller VM (LON-DC1), in the Windows PowerShell window, run the following command to change the root source to **C:\labfiles** so that you can access any files from that location: <br/>

	```cmd
	CD C:\labfiles\
	```

3. Enter the following command that runs a PowerShell script that creates a problem user account. This script, which is stored in the C:\labfiles folder, will purposely create an issue with the userPrincipalName for Klemen Sic's on-premises user account; this will enable you to troubleshoot this account in the next task using the IdFix tool.  <br/>

	```powershell
	.\CreateProblemUsers.ps1
	```

	
	>**Important:** Wait until the script has finished before proceeding to the next task. This Windows PowerShell script will make the following change in AD DS:

	- **Klemen Sic**. Update the userPrincipalName for Klemen to include an extra "@" character. 

4. Minimize your Windows PowerShell window.


### Task 3: Run the IdFix tool and fix identified issues 

In this task you will download and use the IdFix Directory Synchronization Error Remediation Tool to fix Klemen Sic's on-premises user account that you purposely broke in the previous task. Running the IdFix tool will correct any user account errors prior to synchronizing identity data between your on-premises environment and Microsoft Entra ID.

1. You should still be logged into **LON-DC1** as the **Administrator** from the prior task. 

2. On **LON-DC1**, select the **Microsoft Edge** icon on the taskbar. In your **Microsoft Edge** browser, open a new tab and enter the following URL in the address bar to access the Microsoft -IdFix Overview page: <br/>

	**https://microsoft.github.io/idfix**
	
3. On the **Microsoft - IdFix** page, in the navigation pane on the side of the screen, select **Step 2: Install IdFix**. 

4. On the **Step 2: Install IdFix** page, the first line in the instruction says: **Select *setup.exe* to download and install the IDFix tool on your Windows machine.**  <br/>

	In this instruction, select **setup.exe** to download the IdFix application to your machine. 

5. Once the **setup.exe** file is downloaded, a **Downloads** window will appear at the top-right of the page. In this window, under **setup.exe**, select **Open file** to install the file on LON-DC1. This will initiate the **Application Install** wizard.

6. In the **Do you want to install this application?** page in the **Application Install** wizard, select **Install**.

7. In the **IdFix Privacy Statement** message box, select **OK**. Once the IDFix tool is installed, the **Application Install** wizard will close and the **IDFix** tool will automatically open. 

8. In the **IdFix** tool that appears, maximize the window. On the menu bar at the very top of the screen, select **Query** to query the directory. After a short wait, you should see several errors. <br/>

	**Note:** If a **Schema Warning** dialog box appears, select **Yes** to continue.

9. Select the **ERROR** column heading to sort the records in alphabetical error sequence. <br/>

	>**Note:** If any **topleveldomain** errors appear, then ignore them as they cannot be fixed by the IdFix tool.  

10. In the **Klemen Sic** row, note the text in the **VALUE** column. It currently includes two **@@** signs, which occurred when you ran the script in the prior task that purposely broke Klemen's UserPrincipalName. Now note the text in the **UPDATE** column, which is the value the IDFix tool will change the UPN name to, should you direct it to do so. <br/>

	You want the IDFix tool to fix Klemen's UPN value, so select the drop-down arrow in Klemen's **ACTION** field and select **EDIT**. <br/>

	>**Note:** Do NOT update either of the remaining two user accounts. Ignore those for now.

11. On the menu bar at the top of the window, select **Apply**. 

12. In the **Apply Pending** dialog box that appears, select **Yes**. <br/>

	>**Note:** Notice the value in the **Action** column changed from **EDIT** to **COMPLETE** for Klemen Sic. This indicates the IdFix tool corrected the error by updating Klemen Sic's user object. 

13. On the menu bar at the top of the page, select **Query**. If a **Schema Warning** dialog box appears, select **Yes** to continue. If a dialog box appears indicating an unhandled exception has occurred, select **Continue**.<br/>

	In the query results, note how the Klemen Sic row no longer appears in the results, since the IdFix tool just fixed this user record. <br/>	

	As you can see, there are still two users whose errors have not been fixed (**An Dung Dao** and **Ngoc Bich Tran**). We are purposely leaving these errors alone so that you can see what happens during the synchronization process using the Microsoft Entra Connect tool in the next exercise when it processes users with these conditions. <br/>

	>**Important:** When there are format and duplicate errors for distinguished names, the **UPDATE** column either contains the same string as the **VALUE** column, or the **UPDATE** column entry is blank. In either case, this means that IdFix cannot suggest a remediation for the error. You can either fix these errors outside IdFix, or manually remediate them within IdFix. You can also export the results and use Windows PowerShell to remediate many different errors. 

14. Close the IdFix window. 

15. Leave your Edge browser open. However, you can close the **Step 2: Install Id-Fix - Microsoft - IdFix** tab since you are done using IdFix.

# Proceed to Lab 3 - Exercise 2
 
