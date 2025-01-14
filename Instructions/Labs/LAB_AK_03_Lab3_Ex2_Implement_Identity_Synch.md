# Learning Path 3 - Lab 3 - Exercise 2 - Implement Identity Synchronization 

In this exercise, you will use Microsoft Entra Connect Sync to enable synchronization between Adatum’s on-premises Active Directory and Microsoft Entra ID. Microsoft Entra Connect Sync will then continue to synchronize any delta changes every 30 minutes. You will then make some user and group updates and then manually force an immediate synchronization rather than waiting for Microsoft Entra Connect Sync to automatically synchronize the updates. You will then verify whether the updates were synchronized.  

‎**IMPORTANT:** When you start this exercise, you should perform the first four tasks without any delay between them so that Microsoft Entra Connect Sync does not automatically synchronize the changes that you make to the identity objects.

### Task 1: Install Microsoft Entra Connect Sync and initiate synchronization

In this task, you will run the Microsoft Entra Connect Sync setup wizard to enable synchronization between Adatum’s on-premises Active Directory and Microsoft Entra ID. Once the configuration is complete, the synchronization process will automatically start. 

**IMPORTANT:** Azure Active Directory (Azure AD) has recently been rebranded to Microsoft Entra ID. As such, all Azure AD product features are in the process of being rebranded to Microsoft Entra. Since this rebranding effort is still on-going, some Azure AD features have not yet been rebranded to Microsoft Entra. For example, the original name of Microsoft Entra Connect Sync is Azure AD Connect. While the Microsoft Entra portal refers to this sync tool as Microsoft Entra Connect Sync, the installation wizard for this tool has not yet been rebranded. As of this writing, the wizard still refers to Azure AD Connect. Keep this in mind if you see Azure AD still referenced on Microsoft 365 pages, product names, or in this case, the Azure AD Connect installation wizard. Eventually, all Azure AD branding will be changed to Microsoft Entra. Microsoft World Wide Learning will strive to keep these lab instructions updated as the Microsoft 365 Engineering team continues its rebranding efforts.

1. You should still be logged into **LON-DC1** as **adatum\administrator** from the prior task. 

2. After finishing the earlier lab exercise in which you added Adatum's custom domain, you should still be logged into Microsoft 365 in your Edge browser as Holly Dickson.  

3. In your **Edge** browser, select the **Microsoft 365 admin center** tab, select **Users** in the navigation pane, and then select **Active Users**. <br/>

4. In the **Active users** window, select the **ellipsis** icon that appears at the end of the menu bar, and then in the drop-down menu that appears, select **Directory synchronization**. This initiates the **Add or sync users to Microsoft Entra ID** wizard. It may take a minute or so for the wizard to start.

5. In the **Add or sync users to Microsoft Entra ID** wizard, on the **About user synchronization** page, read through the content. In the **User status** section, note the number of existing Adatum cloud users and hybrid users. Select **Next**.

6. On the **Select a migration option** page, read the explanation of each option so that you understand the migration options that are available. Select the **Continuous sync** option and then select **Next**.

7. On the **Prepare by running IdFix** page, since you already ran IdFix in the prior lab exercise, there's no need to download and run it again. Select **Next**.

8. On the **Review synchronization tools** page, Holly's not sure which synchronization tool to select based on Adatum's synchronization requirements - **Microsoft Entra Connect Sync** or **Microsoft Entra Cloud Sync**. Holly has identified the following requirements that she thinks may impact this decision:

	- Holly wants Adatum's users to be able to access both on-premises and cloud applications using the same passwords. That way, each user doesn't have to remember multiple passwords.
	- Because Adatum plans to keep its on-premises Exchange environment, it must implement an Exchange hybrid deployment.
 	- Adatum has on-premises devices that need to be able to join Microsoft Entra ID as hybrid Microsoft Entra ID joined devices. As such, these devices require periodic network connectivity to Adatum's on-premises domain controllers. Without this connection, these devices become unusable. 

	On the **Review synchronization tools** page, Holly discovers that it provides a **Help me decide** feature that recommends which synchronization tool to use based on your synchronization requirements. Holly decides to use this feature, so select **Help me decide**.   

9. By selecting the **Help me decide** option, the wizard displays a list of predefined requirements that can impact which synchronization tool an organization should use. In the list of requirements that appears, select the following three Adatum requirements to see which sync tool the system recommends (Note how the recommendation either remains the same or changes after selecting each additional requirement): <br/>

	- Select **I require the ability for users to access both on-premises and cloud-based applications using the same passwords (Password hash sync and Password writeback).**  <br/>

		**Note:** After selecting this check box, note the recommendation that appears at the bottom of the page. For this one requirement, the system recommends using **Microsoft Entra Cloud Sync**. <br/>
	
	- Select **I have Exchange on-premises objects that I need to sync to the cloud (Exchange hybrid).**  <br/>

		**Note:** After selecting this second check box, the recommendation is still **Microsoft Entra Cloud Sync** based on these first two requirements. 

	- Select **I have devices on-premises that I need to access Microsoft Entra ID Hybrid Join.**  <br/>

		**Note:** After selecting this third check box, the recommendation changes to **Microsoft Entra Connect Sync**. 
	
 	**Note:** If you're wondering why the wizard changed its recommendation to Microsoft Entra Connect Sync based on this final requirement, it's because of the following reasons:

	- First off, understand that this final requirement means that Adatum has desktops, laptops, or servers located in its on-premises Active Directory environment that must be able to join Microsoft Entra ID (formerly Azure AD) as hybrid Microsoft Entra ID joined devices. Microsoft Entra ID Hybrid Join allows these on-premises devices to register their identity with Microsoft Entra ID. This enables them to access cloud-based services protected by  Microsoft Entra ID, such as Microsoft 365. 
	- So how does this affect which synchronization tool to use? Well, keep in mind that Microsoft Entra Connect Sync uses an on-premises sync agent while Microsoft Entra Cloud Sync is a pure cloud-based service. With Microsoft Entra Connect Sync, the sync agent is installed on-premises, and therefore can directly access Adatum's on-premises AD environment. This allows it to sync Adatum's device identities to the cloud without dependency on Microsoft Entra ID Hybrid Join. However, Microsoft Entra Cloud Sync has no on-premises component. It relies on the devices self-registering their identity to Microsoft Entra ID through Microsoft Entra ID Hybrid Join. Therefore, any issues with hybrid join or network connectivity breaks the Microsoft Entra Cloud Sync process. As a result, Microsoft Entra Connect Sync is the preferred synchronization option for this requirement.

10. Select **Next**. The wizard will deploy the recommended solution, **Microsoft Entra Connect Sync**. 

11. On the **Sync your users** page, select the **Download Microsoft Entra Connect Sync** box. This opens a new tab in your browser and takes you to the Microsoft Download Center, where the system should automatically initiate the download of the Microsoft Entra Connect Sync installation program. 

	If the download worked, then in the **Microsoft Download Center**, a message indicating **Thank you for downloading Microsoft Entra Connect** should appear. However, some tenants may experience an issue where this download request doesn't work, in which case the **Microsoft Download Center** window appears displaying the following error message: **"Were sorry, this download is no longer available.** This error has been reported to Microsoft Support and we're waiting on a fix. In the mean time, if you receive this error, then perform the following steps to manually download the Microsoft Entra Connect Sync installation program:

	- Enter the following URL in the address bar: **https://www.microsoft.com/en-ie/download/details.aspx?id=47594**
	- This URL takes you to the Microsoft Download Center page for Microsoft Entra Connect. On the **Microsoft Entra Connect** page, select the **Download** button. 

13. If a **Downloads** window appears at the top of the screen, select the **Open file** link that appears below the **AzureADConnect.msi** file once it's finished downloading. <br/>

	However, if a **Downloads** window doesn't appear at the top of the screen, select the ellipsis icon (three dots) that appears to the right of the **Profile 1** icon (the image of a person inside a circle). In the drop-down menu that appears, select **Downloads**. If a **Downloads** window appears at the top of the screen and it includes the **AzureADConnect.msi** file, then select the **Open file** link that appears below it. However, if **AzureADConnect.msi**  does not appear in the **Downloads** window, then on the **Microsoft Download Center** page, select the **click here to download manually** hyperlink and then repeat this step to open the **AzureADConnect.msi** file.

14. Opening the **AzureADConnect.msi** file starts the **Microsoft Entra Connect Sync** installation wizard. The first page of the wizard may appear and then suddenly disappear, or it may not appear at all. If either situation occurs, then select the wizard icon on the taskbar to display the setup wizard's UI. 

15. On the **Welcome to Microsoft Entra Connect Sync** window in the setup wizard, select the **I agree to the license terms and privacy notice** check box and then select **Continue**.

16. On the **Express Settings** page, read the instruction regarding a single Windows Server Active Directory forest and then select **Use express settings**.

17. On the **Connect to Azure AD** window, enter **Holly@xxxxxZZZZZZ.onmicrosoft.com** (where xxxxxZZZZZZ is the tenant prefix provided by your lab hosting provider) in the **USERNAME** field. <br/>

	In the **PASSWORD** field, enter the New Administrative Password that you assigned to Holly's account, and then select **Next**.  <br/>

	**Note:** If the **Next** button is not enabled, then tab off the **PASSWORD** field to enable it. 

18. On the **Connect to AD DS** page, enter **Adatum\Administrator** in the **USERNAME** field, enter **Pa55w.rd** in the **PASSWORD** field, and then select **Next**  (if the **Next** button is not enabled, then tab off the PASSWORD field to enable it). 

19. In the **Microsoft Entra sign-in configuration** window, select the **Continue without matching all UPN suffixes to verified domains** check box at the bottom of the page and then select **Next**.

20. On the **Ready to configure** screen, select the check box for **Start the synchronization process when configuration completes** if it’s not already selected, and then select **Install**.   <br/>

	**IMPORTANT:** While Holly eventually plans install an Exchange hybrid deployment, she will not do so now. For the purpose of this lab, do **NOT** select the **Exchange hybrid deployment** option. 

21. Wait for the configuration to complete (which may take several minutes). On the **Configuration complete** page, select **Exit**. 

22. Select the **Windows (Start)** icon in the lower left corner of the taskbar. In the **Start** menu that appears, select the icon to display all apps. Select **Azure AD Connect** to expand the group, and then select **Synchronization Service** to start this desktop application. <br/>

	**Note:** If you selected **Azure AD Connect** in the **Start** menu and it expanded and you were able to select **Synchronization Service**, then proceed to the next step (step 22). However, if **Azure AD Connect** did not expand when you selected it in the **Start** menu, then you will need to close all applications and then restart LON-DC1. <br/>

	**Important:** The remaining instructions in this step are what you should do if you needed to restart LON-DC1. <br/>

	If you had to restart LON-DC1, then after it restarts, follow the instructions from your lab hosting provider to select **Ctrl+Alt+Delete**. This will display the log on screen for LON-DC1. <br/>

	Log in as **Adatum\Administrator** with a password of **Pa55w.rd**. <br/>

	Minimize **Server Manager** after it opens, and then open the **Edge** browser and navigate to **htps://portal.office.com**. <br/>

	Log in as **Holly@xxxxxZZZZZZ.onmicrosoft.com**.  In the **Password** field, enter the **Administrative Password** provided by your lab hosting provider. If required, complete the MFA sign-in process. <br/>

	On the **Microsoft Office Home** page, select **Admin** to open the **Microsoft 365 admin center**. <br/>

	Then select the **Windows (Start)** icon in the lower left corner of the taskbar. In the **Start** menu that appears, select **Azure AD Connect** to expand the group (this time it should expand), and then select **Synchronization Service**.  

23. Maximize the **Synchronization Service Manager on LON-DC1** window. The **Operations** tab at the top of the screen is displayed by default so that you can monitor the synchronization process, which automatically started when you selected this program. 

24. Wait for the **Export** profile to complete for **xxxxxZZZZZZ.onmicrosoft.com - AAD**. When it finishes, its **Status** should be **completed-export-errors**. Once it's complete and you see this status, select this row.  

25. In the bottom portion of the screen, a detail pane appears showing the detailed information for this selected operation. 

	- In the **Export Statistics** pane on the left, note the number of on-premises users that were added to Azure Active Directory and the number that were updated. 
	- In the **Export Errors** pane on the right, note the errors that appear. If you recall back in the prior lab exercise when you ran the IdFix tool, there were two users with validation errors that you purposely did not fix (**Ngoc Bich Tran** and **An Dung Dao**). 

		Select the first link (CN={xxxxxx...) under the **Export Errors** column that applies to the first **DataValidationFailed** error. This will display the first of these two users that were not synchronized by the Azure AD Connect tool. Review the error to see why this account is broken. **Tip:** In the **Connector Space Object Properties** window, select the **Export Error** tab. In the **Error Information** section, select the **Detail** button. Review the detailed error information, and then select **Close**. Select **Close** again. <br/>

		Select the second Data Validation error link and verify this error is for the second user that you purposely did not fix. Follow the same steps as before to review the error for this user.   <br/>

	‎**IMPORTANT:** Because a synchronization had not been performed prior to this, the initial synchronization was a **Full Synchronization** (see the **Profile Name** column in the top pane). Because the synchronization process will continue to run automatically every 30 minutes, any subsequent synchronizations will display **Delta Synchronization** as its **Profile Name**. If you leave the **Synchronization Service Manager** window open, after 30 minutes you will see that it attempts to synchronize the two users who were not synchronized during the initial synchronization. These will display as a **Delta Synchronization** rather than a **Full Synchronization**.

26. Now that you have seen Azure AD Connect complete a Full Synchronization, in the next task you will make some updates and manually force an immediate synchronization rather than waiting for it to synchronize updates every 30 minutes. Close the **Synchronization Service Manager on LON-DC1** window. 

27. In your browser, close all tabs except for the **Home | Microsoft 365** tab and the **Active users - Microsoft 365 admin center** tab. 

28. Leave LON-DC1 open as it will be used in the next exercise.


### Task 2 - Create Group Accounts to Test Synchronization  

To test the manual, forced synchronization process, you will also set up several group scenarios to verify whether the forced synchronization function is working in Azure AD Connect. You will create a new security group, and you will update the group members in an existing, built-in security group, all within Adatum’s on-premises environment. 

Each group will be assigned several members. After the forced synchronization, you will validate that you can see each security group in Microsoft 365 and that its members were synced up from the on-premises group to the cloud group. You will also validate the built-in security group was not created in Microsoft 365, even though you added members to it in Adatum's on-premises environment. 

**Important:** Built-in groups are predefined, on-premises security groups that are located under the **Builtin** container in **Active Directory Users and Computers**. They are created automatically when you create an Active Directory domain. You can use these groups to control access to shared resources and delegate specific domain-wide administrative roles. **However, they are NOT synchronized to Microsoft 365, even after adding members to them.** You will validate this functionality in this task.

1. You should still be logged into **LON-DC1** as the **Administrator** from the prior task. 

2. If **Server Manager** is closed, then re-open it now; otherwise, select the **Server Manager** icon on the taskbar. 

3. In **Server Manager**, select **Tools** at the top right side of the screen, and then in the drop-down menu select **Active Directory Users and Computers.**

4. You will begin by adding members to one of the built-in, on-premises security groups. Maximize the **Active Directory Users and Computers** window. In the console tree in the side pane, under **Adatum.com**, select the **Builtin** folder. This will display all the built-in security group folders that were automatically created at the time the **Adatum.com** domain was created.

5. In the detail pane on the right, double-click the **Print Operators** security group.

6. In the **Print Operators Properties** window, select the **Members** tab and then select the **Add** button.

7. In the **Select Users, Contacts, Computers, Service Accounts, or Groups** window, in the **Enter the object names to select** field, type the following names (type all three at once with a semi-colon separating them):  

	- **Ashlee Pickett** 

	- **Juanita Cook** 

	- **Morgan Brooks**  

8. Select **Check Names**. Once they are all validated, select **OK** to return to the **Print Operators Properties** window.

9. In the **Print Operators Properties** window, select **OK** to return to the **Active Directory Users and Computers** window.

10. You will now create a new security group. In the console tree under **Adatum.com**, right-click on the **Research** folder, select **New,** and then select **Group**.  

11. In the **New Object - Group** window, enter the following information:

	- Group name: **Manufacturing**

	- Group scope: **Universal**

	- Group type: **Security**

12. Select **OK**.

13. In the console tree under **Adatum.com**, select the **Research** folder, and then in the detail pane on the right, double-click on the **Manufacturing** security group.  

14. In the **Manufacturing Properties** window, enter **manufacturing@adatum.com** in the **E-mail** field. <br/>

	**Note:** There are two types of security groups in Microsoft 365: a security group and a mail-enabled security group. By entering a value in the **E-mail** field for this on-premises security group, the synchronization process will create a mail-enabled security group in Microsoft 365.   

15. Select the **Members** tab, and then repeat steps 6-9 to add the following members to this group:  

	- **Bernardo Rutter**

	- **Charlie Miller**

	- **Dawn Williamson**  

16. Leave the **Active Directory Users and Computers** window open for the next task.

 
### Task 3 - Change Group Membership to Test Synchronization  

This task sets up another scenario for testing whether the sync process is working in Azure AD Connect (Microsoft Entra Connect Sync). In this task you will change the members of a group to see if they are reflected in the cloud once the group is synced. 

1. This task continues from where the previous task left off in LON-DC1. In the **Active Directory Users and Computers** window, in the console tree under **Adatum.com**, the **Research** organizational unit is still selected. <br/>

	In the detail pane on the right, double-click the **Research** security group.

2. In the **Research Properties** window, select the **Members** tab to view the members of this group.  

3. You want to remove the following users from the group:

	- **Cai Chu**  

	- **Shannon Booth**  

	- **Tia Zecirevic**  
	
	**Tip:** While you can remove each user individually, the quickest way is to remove all three at one time. Select the first user, then hold the **Ctrl** key down while scrolling down and selecting the other two. With all three users selected, select the **Remove** button and then select **Yes** to confirm the removal. Verify the three users have been removed, and then select **OK.**

4. Close the **Active Directory Users and Computers** window.
  
5. Leave LON-DC1 open as you will continue using it in the next task. <br/>

	‎**Important:** You should perform the next task immediately after completing this one so that Azure AD Connect (Microsoft Entra Connect Sync) doesn’t automatically synchronize the changes that you just made to the identity objects in the previous tasks.


### Task 4 - Force a manual synchronization   

In this task, you will force a sync between Adatum’s on-premises Active Directory and Microsoft Entra ID (formerly Azure AD) instead of waiting 30 minutes for Azure AD Connect (Microsoft Entra Connect Sync) to synchronize the identity objects. You must use PowerShell to perform a forced synchronization.

**IMPORTANT - PowerShell notice:** The prior lab exercise provided a disclaimer indicating why the tasks in that exercise used the MSOnline module rather than Microsoft Graph PowerShell. While Microsoft is in the process of replacing the two older PowerShell modules, MSOnline and Azure Active Directory (Azure AD) PowerShell, with Microsoft Graph PowerShell, there is some functionality in the older modules that has not yet been incorporated into Microsoft Graph PowerShell. The commands in the prior exercise and the command used in this task fall into that category. The prior exercise connected to the MSOnline module, which is also used in this task per the Start-ADSyncSyncCycle command. 

1. On LON-DC1, if the **Windows PowerShell** application is still open from the prior exercise, then **you MUST close it now**.  <br/>

	‎**WARNING:** The reason for this step is that if Windows PowerShell was opened BEFORE the Microsoft Azure AD Connect setup, the cmdlet **Start-ADSyncSyncCycle** that is used in step 3 will not be available and you will receive an error indicating that the cmdlet is not recognized when you attempt to run it. Therefore, it’s recommended that at this step, you close Windows PowerShell if it’s open.  

2. At this point, Windows PowerShell should NOT be open. You now want to reopen it. To open it, select the **magnifying glass (Search)** icon in the taskbar, type **power** in the Search box, and then in the menu, right-click on **Windows PowerShell** (not Windows PowerShell ISE) and select **Run as administrator**. Maximize the Windows PowerShell window once it opens.

3. In **Windows PowerShell**, run the following command to manually run a sync cycle between Adatum’s on-premises AD and Azure AD. The **Delta** switch is used here so that only the updates are synchronized.   <br/>

		Start-ADSyncSyncCycle -PolicyType Delta
	
	‎**Note:** If for any reason the Domain Controller VM was restarted after the original full synchronization run, the Microsoft Azure AD Sync service may not have restarted. If this occurred, you’ll receive an error when you try to perform the forced sync above. If this occurs, you’ll need to start the Microsoft Azure AD Sync service first and then perform the forced synchronization.

	**Note:** If the Start-ADSyncSyncCycle command is not found, the domain controller will need to be restarted for the PowerShell module to complete its installation.
	
4. Once the synchronization process has successfully completed, minimize your PowerShell window (do not close it) and proceed to the next task. You will use PowerShell in the next task to validate some of the results of the directory synchronization.

5. Remain in LON-DC1 and proceed to the next task.
  

### Task 5 - Validate the Results of Directory Synchronization   

In this task, you will validate whether the changes you made earlier were synchronized from Adatum’s on-premises Active Directory to Microsoft Entra ID (Azure AD). You will validate the changes using the Microsoft 365 admin center, and then you’ll perform the same validations using Windows PowerShell. This gives you experience in validating synchronization using both the Microsoft 365 admin center GUI and PowerShell.

**IMPORTANT - PowerShell notice:** This task employs basic PowerShell queries for Groups and Users, which are supported in Microsoft Graph PowerShell. Since Microsoft Graph PowerShell is replacing the two older PowerShell modules, MSOnline and Azure Active Directory (Azure AD) PowerShell, you will use Microsoft Graph PowerShell in this task.

1. You should still be logged into LON-DC1 as **adatum\administrator** with a password of **Pa55w.rd.**

2. Now let’s examine the synchronization results for the groups that you updated in the previous tasks. In your **Edge** browser, if tabs are still open for the **Home | Microsoft 365** page and the **Active users - Microsoft 365 admin center**, then proceed to the next step. <br/>

	Otherwise, enter **https://portal.office.com/** in the address bar to open the **Microsoft 365 Home** page, and then log in as **holly@xxxxxZZZZZZ.onmicrosoft.com** (where xxxxxZZZZZZ is the tenant prefix provided by your lab hosting provider). In the **Password** field, enter the New Administrative Password that you assigned to her account, and then on the **Microsoft 365 Home** page, navigate to the **Microsoft 365 admin center**. 

3. In the **Microsoft 365 admin center**, select **Teams & groups** in the navigation pane, and then select **Active teams & groups**. 

4. In the **Active teams and groups** window, the **Teams & Microsoft 365 groups** tab is displayed by default. Select the **Security groups** tab. Verify the **Print Operators** group does NOT appear in the list of security groups. As mentioned previously, built-in security groups such as the **Print Operators** group are not synced from the on-premises AD to Azure AD, even when you add members to the group as you did in the earlier task.

5. In the **Security groups** tab, verify the **Manufacturing** group appears. This group should have an email address displayed, which indicates that it's a mail-enabled security group rather than a standard security group. If you'll recall, you added an email address (**manufacturing@adatum.com**) to the **Manufacturing** group when you created it in a previous task.  <br/>

	**Note:** You may need to wait up to 10 minutes or so before the **Manufacturing** group appears. Continue to refresh the list until you see the group, which validates that the synchronization process synchronized this on-premises group to Microsoft 365.  

6. For the **Manufacturing** group, check the value displayed in the **Email** column. Verify the group email address was changed during directory synchronization from **manufacturing@adatum.com** to **manufacturing@xxxxxZZZZZZ.onmicrosoft.com**, which is the group's mailbox in Exchange Online. <br/>

	Hover your mouse over the icon in the **Sync status** column and verify that it indicates **Synced from on-premises**. 

7. To the right of the **Manufacturing** group is a vertical ellipsis icon (three periods vertically aligned). Hold your mouse over this icon. Note the message that appears which indicates you can only manage this group in your on-premises environment. 

8. Now let’s examine this group using Windows PowerShell. If **Windows PowerShell** is already open on the taskbar, then select the PowerShell icon and proceed to the next step; otherwise, type **PowerShell** in the **Search** field on the taskbar and then right-click on the **Windows PowerShell** application and select **Run as administrator**. Maximize your PowerShell window.

9. You should begin by installing Microsoft Graph PowerShell. Earlier in this training, you installed Microsoft Graph PowerShell on LON-CL1. At that time, you installed all 30+ sub-modules by running the following command: Install-Module Microsoft.Graph (where Graph is the parent module that contains the 30+ sub-modules). While you could install all 30+ sub-modules on LON-DC1, you're only going to use the Groups and Users sub-modules in this task, which is the last task in this training that uses PowerShell on LON-DC1. Therefore, to reduce installation time, you'll run the following two commands that will install just those two sub-modules and none of the other 30+ sub-modules. This also provides you with experience in installing specific sub-modules rather than the entire complement of Graph sub-modules.   <br/>

	a. Type the following command and press Enter (If you receive a message asking whether you want to install this module from an untrusted repository, enter **A** for **Yes to All**; do the same for the next command as well):  <br/>

		Install-Module Microsoft.Graph.Groups -Scope CurrentUser

	b. At the command prompt, type the following command and press Enter: <br/>

		Install-Module Microsoft.Graph.Users -Scope CurrentUser

10. Now that you have installed the Groups and Users sub-modules, you must import each of them in order to import their respective cmdlets into your PowerShell session. To do so, you must run the following two commands: <br/>

	a. Type the following command and press Enter:  <br/>

		Import-Module Microsoft.Graph.Groups

	a. Then type the following command and press Enter:  <br/>

		Import-Module Microsoft.Graph.Users

11. At the command prompt, you must now connect to Microsoft Graph and perform a request for permission to use the Groups and Users cmdlets that were just imported. To complete this task, you only need 'Read only' permissions for these two sub-modules. Type the following command and then press Enter: <br/>
		
		Connect-MgGraph -Scopes 'Group.Read.All', 'User.Read.All'

12. In the **Pick an account** window that appears, select **Holly Dickson's** account. In the **Enter password** window, enter the New Administrative Password that you assigned to her account and then select **Sign in**. 

13. If a **Permissions requested** dialog box appears, select the **Consent on behalf of your organization** check box and then select **Accept**.

14. You will now use PowerShell to display the list of groups in Microsoft 365. This list should include the groups that you manually created in Microsoft 365, as well as the groups that were created in the on-premises Active Directory that were just synchronized with Microsoft 365. Type the following command and then press Enter:

		Get-MgGroup | Format-List Id, DisplayName, Description, GroupTypes

15. You now want to display the members of the **Research** group. In the list of groups, highlight the object ID for the **Research** group and then press **Ctrl+C** to copy the ID to the clipboard. Then type the following command, paste in the Research group's object ID (**Ctrl+V**) in the appropriate spot, and then press Enter:  <br/>

		Get-MgGroupMember -GroupId 'paste in the group's object ID here'

16. In the list of group members that were displayed in the prior step, note how the results simply show the object ID of each member. Without displaying the user names, this command doesn't help you verify whether the group members were synchronized. To work around this issue, you're going to repeat the prior command, but this time you'll add an additional component that retrieves the User record for each member of the group and displays the User's attributes, which includes the user name. <br/>

	At the command prompt hit the UP arrow on your keyboard. This will automatically type the prior command that was run (which includes the Research group's object ID, so you don't have to re-paste it). Then following the object ID, type the remaining portion of the command (starting with **-All**) and press Enter:

		Get-MgGroupMember -GroupId 'the object ID of the Research group' -All | ForEach {Get-MgUser -UserId $_.Id}

17. In the list of members of the Research group, verify the following users are **NOT** included. Remember, in the prior task you removed these three users from the Research group in the on-premises Active Directory, prior to synchronizing the group to Microsoft 365:  

	- Cai Chu 

	- Shannon Booth  

	- Tai Zecirevic  

18. In the prior task, you added the **Manufacturing** group in the on-premises Active Directory, and you assigned three users to the group. You now want to verify the members of the **Manufacturing** group were synchronized when the group was added in Microsoft 365 during the synchronization process, <br/>

	To do so, you must first scroll back up to the list of groups, highlight the object ID for the **Manufacturing** group and then press **Ctrl+C** to copy the ID to the clipboard. <br/>

	Then hit the UP arrow on your keyboard to automatically type the prior command, which contains the object ID of the Research group that you pasted in during the prior step:  <br/>

		Get-MgGroupMember -GroupId 'the object ID of the Research group' -All | ForEach {Get-MgUser -UserId $_.Id}    <br/>

	**Important:** You must then replace the object ID of the Research group with the object ID of the Manufacturing group before running this command. To do so, use the left arrow on your keyboard to move your cursor to the start of the object ID, then highlight the object ID of the Research group and hit **Ctrl+V**. This will replace the ID of the Research group by pasting in the object ID of the **Manufacturing** group. Then press Enter to run the command. Doing so will display the members of the **Manufacturing** group. <br/>

	In the **Manufacturing** group, you earlier added the following members to the group in the on-premises Active Directory. You should now see each of these group members in this Microsoft 365 group following synchronization:  

	- Bernardo Rutter

	- Charlie Miller

	- Dawn Williamson

19. You have now validated that your test groups and user accounts were synchronized properly. Once you have completed the validation steps, close your PowerShell window. 
 
# End of Lab 3
 
