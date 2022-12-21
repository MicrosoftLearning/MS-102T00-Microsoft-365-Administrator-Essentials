# Learning Path 3 - Lab 3 - Exercise 2 - Implement Identity Synchronization 

In this exercise, you will enable synchronization between Adatum’s on-premises Active Directory and Azure Active Directory. Azure AD Connect will then continue to synchronize any delta changes every 30 minutes. You will then make some user and group updates and then manually force an immediate synchronization rather than waiting for Azure AD Connect to automatically synchronize the updates. You will then verify whether the updates were synchronized.  

‎**IMPORTANT:** When you start this exercise, you should perform the first four tasks without any delay between them so that Azure AD Connect does not automatically synchronize the changes that you make to the identity objects.

### Task 1: Install Azure AD Connect and Initiate Synchronization

In this task, you will run the Azure AD Connect setup wizard to enable synchronization between Adatum’s on-premises Active Directory and Azure Active Directory. Once the configuration is complete, the synchronization process will automatically start. 

1. You should still be logged into **LON-DC1** as the local **adatum\administrator** from the prior task. 

2. After finishing the previous lab exercise, you should still be logged into Microsoft 365 in your Edge browser as Holly Dickson.  

3. In your **Edge** browser, select the **Microsoft 365 admin center** tab, and then in the navigation pane, select **Users**, and then select **Active Users**. <br/>

4. In the **Active users** window, select the **ellipsis** icon that appears at the end of the menu bar, and then in the drop-down menu, select **Directory synchronization**. This initiates the **Add or sync users to Microsoft 365** wizard.

5. In the **Add or sync users to Microsoft 365** wizard, on the **Select a migration option** page, select the **Continuous sync** option and then select **Next**.

6. On the **Prepare by running IdFix** page, select **Next**.

7. On the **Review synchronization tools** page, Holly had originally planned to select the **Azure AD Connect** option given Adatum's Exchange hybrid deployment. But just to verify that this is the correct solution, Holly has decided to use the system tool that recommends the synchronization tool to use based on your synchronization requirements. Holly will use this feature to verify whether Azure AD Connect is the correct choice for Adatum. <br/>

	Select **Help me decide**. This option enables you to select from amongst a variety of requirements that your organization may have.  

8. In the list of requirements that appears, select the following Adatum requirements to see which sync tool the system recommends: <br/>

	- **I have a single or multiple connected forests that I need to sync users and groups from.** <br/>

		**Note:** After selecting this check box, note the recommendation that appears at the bottom of the page. By just selecting this one requirement, the system recommends using **Azure AD cloud sync**. <br/>

	- **I require the ability for users to access both on-premises and cloud-based applications using the same passwords (Password hash sync and Password writeback).**  <br/>

		**Note:** After selecting this second requirement, the recommendation is still **Azure AD cloud sync**. <br/>
	
	- **I have Exchange on-premises objects that I need to sync to the cloud (Exchange hybrid).**  <br/>

		**Note:** After selecting this third check box, the recommendation has changed to **Azure AD Connect**. This confirms that Holly's initial thought of selecting Azure AD Connect was the same as what the system would have recommended given Adatum's synchronization requirements.

9. Select **Next**. The system will initiate synchronization using the recommended solution, **Azure AD Connect**. 

10. On the **Sync your users** page, select the **Download Azure AD Connect** box. This opens a new tab in your browser and takes you to the Microsoft Download Center.

11. In the **Microsoft Download Center**, a message indicating **Thank you for downloading Microsoft Azure Active Directory Connect** should appear. <br/>

	If a **Downloads** window appears at the top of the screen, select the **Open file** link that appears below the **AzureADConnect.msi** file once it's finished downloading. <br/>

	However, if a **Downloads** window doesn't appear at the top of the screen, select the ellipsis icon (three dots) that appears to the right of the **Profile 1** icon (the image of a person inside a circle). In the drop-down menu that appears, select **Downloads**. If a **Downloads** window appears at the top of the screen and it includes the **AzureADConnect.msi** file, then select the **Open file** link that appears below it. However, if **AzureADConnect.msi**  does not appear in the **Downloads** window, then on the **Microsoft Download Center** page, select the **click here to download manually** hyperlink and then repeat this step to open the **AzureADConnect.msi** file.

12. Opening the **AzureADConnect.msi** file initiates the installation of the Microsoft Azure Active Directory Connect Tool by starting the **Microsoft Azure Active Directory Connect** wizard. The first page of the wizard may appear and then suddenly disappear, or it may not appear at all. If either situation occurs, then select the wizard icon on the taskbar. 

13. On the **Welcome to Azure AD Connect** window in the setup wizard, select the **I agree to the license terms and privacy notice** check box and then select **Continue**.

14. On the **Express Settings** page, read the instruction regarding a single Windows Server AD forest and then select **Use express settings**.

15. On the **Connect to Azure AD** window, enter **Holly@xxxxxZZZZZZ.onmicrosoft.com** (where xxxxxZZZZZZ is the tenant prefix provided by your lab hosting provider) in the **USERNAME** field, enter **User.pw1** in the **PASSWORD** field, and then select **Next** (if the **Next** button is not enabled, then tab off the PASSWORD field to enable it). 

16. On the **Connect to AD DS** page, enter **adatum\Administrator** in the **USERNAME** field, enter **Pa55w.rd** in the **PASSWORD** field, and then select **Next**  (if the **Next** button is not enabled, then tab off the PASSWORD field to enable it). 

17. In the **Azure AD sign-in configuration** window, select the **Continue without matching all UPN suffixes to verified domains** check box at the bottom of the page and then select **Next**.

18. On the **Ready to configure** screen, select the check box for **Start the synchronization process when configuration completes** if it’s not already selected, and then select **Install**.   <br/>

	**Note:** While Holly eventually plans install an Exchange hybrid deployment, she will not do so now. For the purpose of this lab, do **NOT** select the **Exchange hybrid deployment** option. 

19. Wait for the configuration to complete (which may take several minutes). On the **Configuration complete** page, select **Exit**. 

20. Select the **Windows (Start)** icon in the lower left corner of the taskbar. In the **Start** menu that appears, select the icon to display all apps. Select **Azure AD Connect** to expand the group, and then select **Synchronization Service** to start this desktop application. <br/>

	**Note:** If you selected **Azure AD Connect** in the **Start** menu and it expanded and you were able to select **Synchronization Service**, then proceed to the next step. However, if **Azure AD Connect** did not expand when you selected it in the **Start** menu, then you will need to close all applications and then restart LON-DC1. The remaining instruction in this step is what to do if you needed to restart LON-DC1. <br>

	After LON-DC1 restarts, follow the instructions from your lab hosting provider to select **Ctrl+Alt+Delete**. This will display the log on screen for LON-DC1. <br/>
	Log in as **Adatum\Administrator** with a password of **Pa55w.rd**. Minimize **Server Manager** after it opens, and then open **Edge** and navigate to **htps://portal.office.com**. Log in as **Holly@xxxxxZZZZZZ.onmicrosoft.com** with a Password of **User.pw1**. On the **Microsoft Office Home** page, select **Admin** to open the **Microsoft 365 admin center**. <br/>

	Then select the **Windows (Start)** icon in the lower left corner of the taskbar. In the **Start** menu that appears, select **Azure AD Connect** to expand the group (this time it should expand), and then select **Synchronization Service**.  

21. Maximize the **Synchronization Service Manager on LON-DC1** window. The **Operations** tab at the top of the screen is displayed by default so that you can monitor the synchronization process, which automatically started when you selected this program. 

22. Wait for the **Export** profile to complete for **xxxxxZZZZZZ.onmicrosoft.com**. When it finishes, its **Status** should be **completed-export-errors**. Once it's complete and you see this status, select this row.  

23. In the bottom portion of the screen, a detail pane appears showing the detailed information for this operation. 

	- In the **Export Statistics** pane on the left, note the number of users that were added and the number that were updated. 
	- In the **Export Errors** pane on the right, note the errors that appear. If you recall back in the prior lab exercise when you ran the IdFix tool, there were two users with validation errors that you purposely did not fix (**Ngoc Bich Tran** and **An Dung Dao**). 

		Select the first link (CN={xxxxxx...) under the **Export Errors** column that applies to the first **Data Validation** error. This will display the first of these two users that were not synchronized by the Azure AD Connect tool. Review the error to see why this account is broke. <br/>

		Select the second Data Validation error link and verify this error is for the second user that you purposely did not fix. Review the error for this user.   <br/>

	‎**IMPORTANT:** Because a synchronization had not been performed prior to this, the initial synchronization was a **Full Synchronization** (see the **Profile Name** column in the top pane). Because the synchronization process will continue to run automatically every 30 minutes, any subsequent synchronizations will display **Delta Synchronization** as its **Profile Name**. If you leave the **Synchronization Service Manager** window open, after 30 minutes you will see that it attempts to synchronize the two users who were not synchronized during the initial synchronization. These will display as a **Delta Synchronization** rather than a **Full Synchronization**.

24. Now that you have seen Azure AD Connect complete a Full Synchronization, in the next task you will make some updates and manually force an immediate synchronization rather than waiting for it to synchronize updates every 30 minutes. Close the **Synchronization Service Manager on LON-DC1** window. 

25. In your browser, close all tabs except for the **Microsoft Office Home** tab and the **Microsoft 365 admin center** tab. 

26. Leave LON-DC1 open as it will be used in the next exercise.


### Task 2 - Create Group Accounts to Test Synchronization  

To test the manual, forced synchronization process, you will also set up several group scenarios to verify whether the forced synchronization function is working in Azure AD Connect. You will create a new security group, and you will update the group members in an existing, built-in security group, all within Adatum’s on-premises environment. 

Each group will be assigned several members. After the forced synchronization, you will validate that you can see the new security group in Microsoft 365 and that its members were synced up from the on-premises group to the cloud group. You will also validate that you can NOT see the built-in security group in Microsoft 365, even though you added members to it in Adatum's on-premises environment. Built-in groups are predefined security groups that are located under the **Builtin** container in **Active Directory Users and Computers**. They are created automatically when you create an Active Directory domain, and you can use these groups to control access to shared resources and delegate specific domain-wide administrative roles. **However, they are NOT synchronized to Microsoft 365, even after adding members to them within their on-premises AD group.** You will validate this functionality in this task.

1. You should still be logged into **LON-DC1** as the **Administrator** from the prior task. 

2. If **Server Manager** is closed, then re-open it now; otherwise, select the **Server Manager** icon on the taskbar. 

3. In **Server Manager**, select **Tools** at the top right side of the screen, and then in the drop-down menu select **Active Directory Users and Computers.**

4. You will begin by adding members to one of the built-in security groups. Maximize the **Active Directory Users and Computers** window. In the console tree in the left-hand pane, under **Adatum.com**, select the **Builtin** folder. This will display all the built-in security group folders that were automatically created at the time the **Adatum.com** domain was created.

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

14. In the **Manufacturing Properties** window, enter **Manufacturing@adatum.com** in the **E-mail** field.  

15. Select the **Members** tab, and then repeat steps 6-9 to add the following members to this group:  

	- **Bernardo Rutter**

	- **Charlie Miller**

	- **Dawn Williamson**  

16. Leave the **Active Directory Users and Computers** window open for the next task.

 
### Task 3 - Change Group Membership to Test Synchronization  

This task sets up another scenario for testing whether the sync process is working in Azure AD Connect. In this task you will change the members of a group to see if they are reflected in the cloud once the group is synced. 

1. This task continues from where the previous task left off in LON-DC1. In the **Active Directory Users and Computers** window, in the console tree under **Adatum.com**, the **Research** organizational unit is still selected. <br/>

	In the detail pane on the right, double-click the **Research** security group.

2. In the **Research Properties** window, select the **Members** tab to view the members of this group.  

3. You want to remove the following users from the group:

	- **Cai Chu**  

	- **Shannon Booth**  

	- **Tia Zecirevic**  
	
	While you can remove each user individually, the quickest way is to remove all three at one time. Select the first user, then hold the **Ctrl** key down while scrolling down and selecting the other two. With all three users selected, select the **Remove** button and then select **Yes** to confirm the removal. Verify the three users have been removed, and then select **OK.**

4. Close the **Active Directory Users and Computers** window.
  
5. Leave LON-DC1 open as you will continue using it in the next task. <br/>

	‎**Important:** You should perform the next task immediately after completing this one so that Azure AD Connect doesn’t automatically synchronize the changes that you just made to the identity objects in the previous tasks.


### Task 4 - Force a manual synchronization   

In this task, you will force a sync between Adatum’s on-premises AD and Azure AD instead of waiting 30 minutes for Azure AD Connect to synchronize the identity objects. You must use PowerShell to perform a forced synchronization.

**IMPORTANT - PowerShell notice:** The prior lab exercise provided a disclaimer indicating why the tasks in that exercise used the MSOnline module rather than Microsoft Graph PowerShell. While Microsoft is in the process of replacing the two older PowerShell modules, MSOnline and Azure Active Directory (Azure AD) PowerShell, with Microsoft Graph PowerShell, there is some functionality in the older modules that has not yet been incorporated into Microsoft Graph PowerShell. The commands in the prior exercise and the command used in this task fall into that category. The prior exercise connected to the MSOnline module, which is also used in this task per the Start-ADSyncSyncCycle command. 

1. On LON-DC1, if the **Windows PowerShell** application is still open from the prior exercise, then **you MUST close it now**.  <br/>

	‎**WARNING:** The reason for this step is that if Windows PowerShell was opened BEFORE the Azure AD Connect setup, the cmdlet **Start-ADSyncSyncCycle** that is used in step 3 will not be available and you will receive an error indicating that the cmdlet is not recognized when you attempt to run it. Therefore, it’s recommended that at this step, you close Windows PowerShell if it’s open and then restart it.  

2. At this point, Windows PowerShell should NOT be open. You now want to reopen it. To open it, select the **magnifying glass (Search)** icon in the taskbar, type **power** in the Search box, and then in the menu, right-click on **Windows PowerShell** (not Windows PowerShell ISE) and select **Run as administrator**.  

3. In **Windows PowerShell**, run the following command to manually run a sync cycle between Adatum’s on-premises AD and Azure AD. The **Delta** switch is used here so that only the updates are synchronized.   <br/>

		Start-ADSyncSyncCycle -PolicyType Delta
	
	‎**Note:** If for any reason the Domain Controller VM was restarted after the original full synchronization run, the Microsoft Azure AD Sync service may not have restarted. If this occurred, you’ll receive an error when you try to perform the forced sync above. If this occurs, you’ll need to start the Microsoft Azure AD Sync service first and then perform the forced synchronization.

	**Note:** If the Start-ADSyncSyncCycle command is not found, the domain controller will need to be restarted for the PowerShell module to complete its installation.
	
4. Once the synchronization process has successfully completed, minimize your PowerShell window (do not close it) and proceed to the next task. You will use PowerShell in the next task to validate some of the results of the directory synchronization.

5. Remain in LON-DC1 and proceed to the next task.
  

### Task 5 - Validate the Results of Directory Synchronization   

In this task, you will validate whether the changes you made earlier were synchronized from Adatum’s on-premises AD to Azure AD. You will validate the changes using the Microsoft 365 admin center, and then you’ll perform the same validations using Windows PowerShell. This gives you experience in validating synchronization using both the Microsoft 365 admin center GUI and PowerShell.

**IMPORTANT - PowerShell notice:** This task employs basic PowerShell queries for Groups and Users, which are supported in Microsoft Graph PowerShell. Since Microsoft Graph PowerShell is replacing the two older PowerShell modules, MSOnline and Azure Active Directory (Azure AD) PowerShell, you will use Microsoft Graph PowerShell in this task.

1. You should still be logged into LON-DC1 as the local **adatum\administrator** with a password of **Pa55w.rd.**

2. Now let’s examine the synchronization results for the groups that you updated in the previous tasks. In your **Edge** browser, if tabs are still open for the **Microsoft Office Home** page and the **Microsoft 365 admin center**, then proceed to the next step. <br/>

	Otherwise, enter **https://portal.office.com/** in the address bar to open the **Microsoft Office Home** page, log in as **holly@xxxxxZZZZZZ.onmicrosoft.com** (where xxxxxZZZZZZ is the tenant prefix provided by your lab hosting provider) with a password of **User.pw1**, and then on the **Microsoft Office Home** page, navigate to the **Microsoft 365 admin center**. 

3. In the **Microsoft 365 admin center**, select **Teams & groups** in the navigation pane, and then select **Active teams & groups**. 

4. In the **Active teams and groups** window, the **Microsoft 365** tab is displayed by default. Select the **Security** tab. Verify the **Print Operators** group does NOT appear in the list of security groups. As mentioned previously, built-in groups such as the **Print Operators** security group are not synced from the on-premises AD to Azure AD, even when you add members to the group as you did in the earlier task.

5. Select the **Mail-enabled security** tab. Verify the **Manufacturing** group appears. <br/>

	**Note:** You may need to wait up to 10 minutes before the **Manufacturing** group appears. Continue to refresh the list until you see the group.  

6. For the **Manufacturing** group, check the value displayed in the **Email** column. Verify the group email address was changed during directory synchronization from **manufacturing@adatum.com** to **manufacturing@xxxxxZZZZZZ.onmicrosoft.com**, which is the group's mailbox in Exchange Online. <br/>

	Hover your mouse over the icon in the **Sync status** column and verify that it indicates **Synced from on-premises**. 

7. Select the **Manufacturing** group to open the **Manufacturing** pane. 

8. In the **Manufacturing** pane, under the Manufacturing title at the top of the pane, note that it’s a mail-enabled security group that contains three members. Also note the message indicating that you can only manage this group in your on-premises environment using either Active Directory users and groups (i.e. Users and Computers) or the on-premises Exchange admin center. <br/>

	The window currently displays the **General** tab. Select the **Members** tab. Note that the group has no owner (the system did not automatically assign Holly Dickson as the group owner). Verify the three users that you added as members of the on-premises group (Bernardo, Dawn, and Charlie) have been synced up and are members of this cloud-based group as well. Close the **Manufacturing** pane.

9. Now let’s examine this group using Windows PowerShell. If **Windows PowerShell** is already open on the taskbar, then select the PowerShell icon and proceed to the next step; otherwise, type **PowerShell** in the **Search** field on the taskbar and then right-click on the **Windows PowerShell** application and select **Run as administrator**. Maximize your PowerShell window.

10. You should begin by installing Microsoft Graph PowerShell. Earlier in this training, you installed Microsoft Graph PowerShell on LON-CL1. At that time, you installed all 30+ sub-modules by running the following command: Install-Module Microsoft.Graph (where Graph is the parent module that contains the 30+ sub-modules). While you could install all 30+ sub-modules on LON-DC1, you're only going to use the Groups and Users sub-modules in this task, which is the last task in this training that uses PowerShell on LON-DC1. Therefore, to reduce installation time, you'll run the following two commands that will install just those two sub-modules and none of the other 30+ sub-modules. This also provides you with experience in installing specific sub-modules rather than the entire complement of Graph sub-modules.   <br/>

	a. Type the following command and press Enter:  <br/>

		Install-Module Microsoft.Graph.Groups -Scope CurrentUser  <br/>

	b. Then type the following command and press Enter:  <br/>

		Import-Module Microsoft.Graph.Users -Scope CurrentUser  <br/>

11. Now that you have installed the Groups and Users sub-modules, you must import each of them in order to import their respective cmdlets into your PowerShell session. To do so, you must run the following two commands: <br/>

	a. Type the following command and press Enter:  <br/>

		Import-Module Microsoft.Graph.Groups

	a. Then type the following command and press Enter:  <br/>

		Import-Module Microsoft.Graph.Users

12. At the command prompt, you must now connect to Microsoft Graph and perform a request for permission to use the Groups and Users cmdlets that were just imported. To complete this task, you only need 'Read only' permissions for these two sub-modules. Type the following command and then press Enter: <br/>
		
		Connect-MgGraph -Scopes 'Group.Read.All', 'User.Read.All'

13. In the **Pick an account** window that appears, select **Holly Dickson's** account. In the **Enter password** window, enter **User.pw1** and then select Sign in. 

14. If a **Permissions requested** dialog box appears, select the **Consent on behalf of your organization** check box and then select **Accept**.

15. You will now use PowerShell to display the list of groups. Type the following command and then press Enter:

		Get-MgGroup | Format-List Id, DisplayName, Description, GroupTypes

16. You now want to display the members of the **Research** group. In the list of groups, highlight the object ID for the **Research** group and then press **Ctrl+C** to copy the ID to the clipboard. Then type the following command, paste in the Research group's object ID (**Ctrl+V**) in the appropriate spot, and then press Enter:  <br/>

		Get-MgGroupMember -GroupId 'paste in the group's object ID here'

17. In the list of group members that were displayed in the prior step, note how the results simply show the object ID of each member. It does not display each user's name, which basically renders the results useless. <br/>

	To display each member's name, you're going to repeat the prior command, but this time you will add an additional component that retrieves the User record for each member of the group and displays the User's attributes. To do so, at the command prompt hit the UP arrow on your keyboard. This will automatically type the prior command. Then type the remaining portion of the command below and press Enter:

		Get-MgGroupMember -GroupId 'paste in the group's object ID here' -All | ForEach {Get-MgUser -UserId $_.Id}

18. In the list of members of the Research group, verify the membership does **NOT** contain the following users that you earlier removed from the group in AD DS:  

	- Cai Chu 

	- Shannon Booth  

	- Tai Zecirevic  

19. To verify the membership of the **Manufacturing** group, scroll back up to the list of groups, highlight the object ID for the **Manufacturing** group and then press **Ctrl+C** to copy the ID to the clipboard. <br/>

	Then hit the UP arrow on your keyboard to automatically type the prior command, which contains the object ID of the Research group that you pasted in during the prior step:  <br/>

		Get-MgGroupMember -GroupId 'the object ID of the Research group' -All | ForEach {Get-MgUser -UserId $_.Id}    <br/>

	You then need to replace the object ID of the Research group with the ID of the Manufacturing group. To do so, use the left arrow on your keyboard to move your cursor to the start of the object ID, then highlight the object ID of the Research group and hit **Ctrl+V**. This will replace the ID of the Research group by pasting in the object ID of the **Manufacturing** group. Then press Enter to run the command. Doing so will display the members of the **Manufacturing** group. <br/>

	In the **Manufacturing** group, you added the following members in AD DS, each of which you should see in the list of group members:  

	- Bernardo Rutter

	- Charlie Miller

	- Dawn Williamson

20. Once you have completed the validation steps, close your PowerShell window. 
 
# Proceed to Lab 3 - Exercise 3
 
