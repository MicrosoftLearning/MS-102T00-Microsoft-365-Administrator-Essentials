# Learning Path 1 - Lab 1 - Exercise 2 - Manage Users and Groups 

In the following lab exercise, you will continue in your role as Holly Dickson, Adatum Corporation’s Microsoft 365 Administrator. In this exercise, you will perform several user and group management functions within Microsoft 365. You will begin by creating a Microsoft 365 user account for Holly, who will be assigned the Microsoft 365 Global Administrator role. You will create several Microsoft 365 groups and assign existing Microsoft 365 users as members of those groups. You will then delete one of the groups and then use Windows PowerShell to recover the deleted group.

**Note:** The VM environment provided by your lab hosting provider comes with 11 existing Microsoft 365 user accounts, as well as a large number of existing on-premises user accounts. Several of the existing Microsoft 365 user accounts will be used throughout the labs in this course. Even though the MOD Administrator account has been created for you by your lab hosting provider, you will still create Holly Dickson's user account, since having more than one user who's assigned the Microsoft 365 Global Administrator role is a best practice. It will also provide you with the experience of creating a Microsoft 365 user account in case you're not familiar with the process.


### Task 1 - Create a User Account for Adatum's Microsoft 365 Administrator

Holly Dickson is Adatum’s Microsoft 365 Administrator. Since a Microsoft 365 user account has not been set up for her, she initially signed into Microsoft 365 as the MOD Administrator account (the default Global administrator) in the previous lab. In this task, you will continue to be logged in as the MOD Administrator, during which you will create a Microsoft 365 user account for Holly. You will also assign the Microsoft 365 Global Administrator role to Holly's account. This role will give Holly permissions to perform all administrative functions within Microsoft 365. Following this task, you will log in using Holly's new account and you will perform all remaining labs using Holly's persona. 

**Important:** As a best practice in your real-world deployment, you should always write down the credentials of the first Global administrator account (in this lab, it's the MOD Administrator account, whose username is admin@xxxxxZZZZZZ.onmicrosoft.com, where xxxxxZZZZZZ is the tenant prefix assigned by your lab hosting provider). You should store away this account information for security reasons. **This account should be a non-personalized identity** that owns the highest privileges possible in a tenant. It should **not** be MFA activated because it is not personalized. Because the username and password for this first Global admin account are typically shared among several users, this account is a perfect target for attacks; therefore, it's always recommended that organizations create personalized service admin accounts (for example, an Exchange admin, SharePoint admin, and so on) and keep as few personal Global admins as possible. For those personal Global admins that you do create in your real-world deployment, they should each be mapped to a single user (such as Holly Dickson), and they should each have Azure Active Directory Multi-Factor Authentication (MFA) enforced. 

That being said, you will not turn on MFA for Holly's account because time is limited in this training course, and we don't want to take up lab time by forcing you to log in using a second authentication method every time Holly logs in.

1. On the LON-CL1 VM, the **Microsoft 365 admin center** should still be open in Internet Explorer from the prior lab, and you should be signed into Microsoft 365 as the **MOD Administrator**. 

2. In the **Microsoft 365 admin center** navigation pane, select **Users** and then select **Active users**. 

3. In the **Active users** list, you will see the list of existing user accounts that were created for you by your lab hosting provider. In this task, you are still logged in as the MOD Administrator, and as such, you must create a user account for Holly Dickson, who is Adatum's new Microsoft 365 Administrator. In doing so, you will assign Holly the Microsoft 365 role of Global Administrator, which gives Holly global access to most management features and data across Microsoft online services. <br/>

	In the **Active Users** window, select the **Add a user** option that appears on the menu bar above the list of active users. 

4. In the **Set up the basics** window, enter the following information:

	- First name: **Holly**

	- Last name: **Dickson** 

	- Display name: When you tab into this field, **Holly Dickson** will appear.

	- Username: **Holly** <br/>
	
		‎**IMPORTANT:** To the right of the **Username** field is the domain field. It will be prefilled with the **xxxxxZZZZZZ.onmicrosoft.com** cloud domain (where xxxxxZZZZZZ is the tenant prefix provided by your lab hosting provider).<br/>
	
		After configuring this field, Holly’s username should appear as:<br/>

		**Holly@xxxxxZZZZZZ.onmicrosoft.com**  
	
	- Clear (uncheck) the **Automatically create a password** check box, which will display a new field for entering an administrator defined password.

	- In the new **Password** field that appears, enter: **User.pw1** (**Hint**: Select the eye icon at the right side of the field to verify the password that you entered)

	- Clear (uncheck) the **Require this user to change their password when they first sign in** check box 

5. Select **Next**. If a **Save password** dialog box appears, select **Never**.

6. In the **Assign product licenses** window, enter the following information: <br/>

	- Select location: **United States**

	- Licenses: Under **Assign user a product license**, select **Enterprise Mobility + Security E5** and **Office 365 E5** 

7. Select **Next.**

8. In the **Optional settings** window, select the drop-down arrow to the right of **Roles.** 

9. In the **Roles** section, select the **Admin center access** option. By selecting this option, the most commonly used Microsoft 365 administrator roles are enabled below it.  <br/>

	**Note:** All the admin roles will be displayed if you select **Show all by category**, which appears after the last common role. For Holly, you don't need to view all the admin roles by category, since Holly will be assigned the Global admin role that appears in the list of most commonly used roles.

10. Select the **Global Administrator** check box.

    **Note:** A warning message will be displayed indicating that you now have 5 global admins. In a normal environment, this would be excessive and not recommended. For the purposes of this lab, the lab hosting provider assigned the Global admin role to the MOD Administrator and three of the other user accounts. Therefore, four of the 11 user accounts in your tenant are global admins, which is not something you would see in a real-world deployment. However, for the purpose of this lab in your fictitious Adatum lab environment, ignore this message. That being said, keep this guideline in mind for your real-world Microsoft 365 deployments. The best practice guideline that you should follow is to have from two to four Global admins.

11. Select **Next**.

12. On the **Review and finish** window, review your selections. If anything must be changed, select the appropriate **Edit** link and make the necessary changes. Otherwise, if everything is correct, select **Finish adding**. 

13. On the **Holly Dickson added to active users** page, under the **User details** section, select the **Show** option to verify Holly's password is **User.pw1**.  <br/>

	**Note:** If you accidentally entered a different password, then once you return to the **Active Users** page, you will need to select the **Reset a password** icon (the key icon that appears when you hover over Holly's account) to change her password to the correct value.

14. Select **Close.**

15. If a window appears asking whether you want to respond to a survey on your experience, select **Cancel**.

16. Remain logged into the Client 1 VM (LON-CL1) with the Microsoft 365 admin center open in your browser for the next task.

### Task 2 – Set up Microsoft 365 User Accounts

After completing the previous task, you should still be signed into the **Microsoft 365 admin center** as the **MOD Administrator** account. In this task, you will begin implementing Adatum’s Microsoft 365 pilot project as Holly Dickson, Adatum’s new Microsoft 365 Administrator. Therefore, you will begin this task by logging out of Microsoft 365 as the MOD Administrator and you will log back in as Holly. When you log in as Holly for the first time, you will be required to change her password, since you configured this option in the earlier task when you created Holly's user account. 

In the prior task, you noticed that your Microsoft 365 trial tenant came equipped with a list of active users. As Holly Dickson, Adatum's Microsoft 365 Administrator, you have selected the following users to help with your pilot project: Alex Wilber, Joni Sherman, Lynne Robbins, and Patti Fernandez. 

Each user is a key member of your pilot project team. While their user accounts are already present in Microsoft 365, you need to configure their passwords so they can more easily sign into Microsoft 365 when needed in the upcoming lab exercises. You will assign **User.pw1** as their user password, just as you did when you created Holly's account. You also need to add a Microsoft 365 group that will be used in a later lab exercise. 

**Note:** Using the same password for multiple users should obviously never be done in the real-world. However, we're doing it here in our training environment to simply make things easier for students as they progress through the labs.

1. On the LON-CL1 VM, the **Microsoft 365 admin center** should still be open in your Microsoft Edge browser from the prior task, and you should be signed into Microsoft 365 as the **MOD Administrator**. <br/>

	On the **Microsoft 365 admin center** tab, select the user icon for the **MOD Administrator** (the **MA** circle) in the upper right corner of your browser. In the **MOD Administrator** window that appears, select **Sign out.** <br/>
	
	**Important:** When signing out of one user account and signing in as another, you should close all your browser tabs except for the **Sign out** tab. This is a best practice that helps to avoid any confusion by closing the windows associated with the prior user. Once you're signed out of the MOD Administrator account, take a moment and close all other browser tabs except for the **Sign out** tab. 
	
2. In your Microsoft Edge browser, in the **Sign out** tab, enter the following URL in the address bar to sign back into Microsoft 365: **https://portal.office.com**. 

3. In the **Pick an account** window, only the MOD Administrator's tenant admin account (the admin@xxxxxZZZZZZ.onmicrosoft.com account) that you just signed out from appears. Select **Use another account**. 

4. In the **Sign in** window, enter **Holly@xxxxxZZZZZZ.onmicrosoft.com** (where xxxxxZZZZZZ is the tenant prefix provided by your lab hosting provider). Select **Next**.

5. In the **Enter password** window, enter **User.pw1** and then select **Sign in**.

6. If a **Welcome to your new Office, Holly** window appears, there's no option to close it. Instead, to the right of the window, select the right arrow icon (**>**) two times to advance through the slides in this messaging window, and then select the check mark icon on the final slide. 

7. If a **Find more apps** window appears, select the **X** in the upper right-hand corner of the window to close it.

8. On the **Microsoft Office Home** page, in the column of application icons that appears on the far left-side of the screen, select **Admin**. This opens the Microsoft 365 admin center in a new browser tab. 

9. In the **Microsoft 365 admin center**, in the left-hand navigation pane, select **Users**, and then under it, select **Active users**.

10. In the **Active Users** window, when you hover your mouse over a user's **Display name**, a **key icon** appears to the right of the user's name. By selecting the key icon, you can reset a user's password. You need to reset Alex, Joni, Lynne, and Patti's passwords to **User.pw1**.<br/>

    Hover your mouse over **Alex Wilber** and select the key icon that appears.

11. In the **Reset password** pane for Alex, clear (uncheck) the **Automatically create password** check box, and then enter **User.pw1** in the **Password** field that appears. Select the eye (**Show Password**) icon at the end of the **Password** field to display the value you entered. Verify you correctly spelled the password (**User.pw1**). <br/>

	Then clear (unselect) the **Require this user to change their password when they first sign in** check box.

12. Select **Reset Password** and then select **Close** on the **Password has been reset** pane.

13. Repeat steps 10-12 for **Joni Sherman**, **Lynne Robbins**, and **Patti Fernandez**. For these three accounts, reset each of their passwords to **User.pw1**. In step 11, don't forget to show the value you entered to verify you spelled it correctly.

14. Remain logged into LON-DC1 with the **Microsoft 365 admin center** open in your browser for the next task.


### Task 3 – Set up Microsoft 365 Groups 

In this task, you will create three new groups that will be used in later labs. You will then manage the groups by assigning users to them. Two groups will be Microsoft 365 groups; the third will be a Security group. Creating the two types of groups will enable you to see some of the differences between the group types. After creating the groups, you will then delete one of them. This will set up the next task, which examines how to recover a deleted group using Windows PowerShell.

1. You should still be logged into LON-CL1 as the local **Admin** account, and in your Edge browser, you should still be logged into Microsoft 365 as **Holly Dickson**. 

2. In the **Microsoft 365 admin center**, select **Teams & groups** in the navigation pane, and then under it, select **Active teams & groups**. 

3. In the **Active teams and groups** page, there's a tab for viewing each of the group types. The **Microsoft 365** tab is displayed by default; this tab displays the existing Microsoft 365 groups.  <br/>

    Select the **Add a group** option that appears on the menu bar above the list of groups. This initiates the **Add a group** wizard. 

4. In the **Add a group** wizard, on the **Choose a group type** page, the **Microsoft 365 (recommended)** option should be selected by default. If it isn't, then select this option now. Select **Next**. 

5. In the **Set up the basics** page, enter **Inside Sales** in the **Name** field, and then enter **Collaboration group for the Inside Sales team** in the **Description** field (Note: even if you don't enter a description, you must still select into this field to enable the **Next** button). Select **Next**.

6. You will now assign Allan Deyoung and Patti Fernandez as owners of the Inside Sales group. In the **Assign owners** window, select **+Assign owners**.
	
7. In the **Assign owners** pane that appears, select **Allan Deyoung** and **Patti Fernandez** from the list of active users, and then select the **Add (2)** button at the bottom of the pane.

8. On the **Assign owners** page, Allan and Patti should appear as owners of the group. Select **Next**.

9. You will now assign Diego Siciliani and Lynne Robbins as members of the Inside Sales group. In the **Add members** page, select **+Add members**.

10. In the **Add members** pane that appears, select **Diego Siciliani** and **Lynne Robbins** from the list of active users, and then select the **Add (2)** button at the bottom of the pane.

11. On the **Add members** page, Diego and Lynne should appear as members of the group. Select **Next**.

12. In the **Edit settings** page, enter the following information: <br/>

	- Enter **insidesales** in the **Group email address** field.
	- Even though Public is displayed in the **Privacy** field, select the field to display the two options that are available. Select **Public**.
	- Under the **Add Microsoft Teams to your group** section, verify the **Create a team for this group** check box is selected (select it if it's blank), and then select **Next**.

13. In the **Review and finish adding group** page, review the content that you entered. If anything needs to be fixed, select **Edit** under the specific area that needs adjustment, make any necessary corrections, and then select **Next** to continue back to this page. Once everything is correct, select **Create group**.

14. It may take a minute or so for the **New group created** window to appear. Note the comment at the top of the page that it may take 5 minutes for the new group to appear in the list of Active groups. </br>

	Select **Close**. This returns you to the **Active teams and groups** page, which should display the **Microsoft 365** group tab. Since the Inside Sales group was a Microsoft 365 group, it should eventually display on this tab.

15. Repeat steps 3-14 to add a new group with the following information: <br/>

	- Group type: **Microsoft 365 (recommended)**

	- Name: **Sales Group**

	- Description: **Complete list of all sales personnel, both internal and remote**<br/>

	- Owner: **Joni Sherman**

	- Members: You will not add members at this time, so select **Next**. <br/>

	**Note:** You can add members to a group at the time you create the group (as you did with the Inside Sales group), as well as after you create a group. For the purpose of this Sales Group, you will add members after you've created the group. This way you can see the two methods of adding group members. So for now, select **Next** to skip through this step and not add members at this time.

16. After creating the Sales Group, you will be returned to the **Active teams & groups** window. It may take a few minutes for the Sales Group to appear, so you may need to select the **Refresh** option on the menu bar once or twice. Note that there are four tabs on this page, one for each group type (Microsoft 365, Distribution list, Mail-enabled security, and Security). The **Microsoft 365** tab is displayed by default, which is the group type assigned to the Sales Group. So the Sales Group should be displayed in this tab.

17. Once the **Sales Group** appears in the list of groups under the **Microsoft 365** tab, select the **Sales Group** name. You will now add members to this group.

18. In the **Sales Group** pane that appears, the **General** tab is displayed by default. Select the **Members** tab.

19. In the **Members** tab, three sub-tabs (Owners, Members, and Site visitors) are displayed in the left-hand column. The **Owners** sub-tab is displayed by default. In the **Owners** sub-tab, Joni Sherman should appear as the only group owner. Select the **Members** sub-tab.

20. In the **Members** sub-tab, select the **Add members** button. 

21. In the **Add members to Sales group** pane, select in the **Search by name or email address** field. This displays the list of active users. <br/>

	In the list of users, select **Alex Wilber**. Note that you have to select back into the field to display the list of users. Select **Joni Sherman**, select back in the field, and then select **Lynne Robbins**. Once all three users are selected, select the **ADD(3)** button at the bottom of the pane.

22. Once the three new members have been saved in the group, select the **X** in the upper right-hand corner of the **Sales group** pane to close it. 

23. Repeat steps 3-14 to add a new group with the following information: <br/>

	- Group type: **Security**

	- Name: **IT Admins**

	- Description: **IT administrative personnel**<br/>

	**Note:** There is no owner, email address, or privacy setting for Security groups. Members must be added to a Security group after creating the group, which you will do in the next few steps. 

24. This returns you to the **Active teams and groups** page, which should still be displaying the **Microsoft 365** group tab. Since the IT Admins group was a Security group, select the **Security** tab.  <br/>

	**Tip:** If any of the new groups do not appear in their respective tabs on the **Active teams and groups** page, wait a minute or so and then select the **Refresh** option on the menu bar (to the right of **Add a group**). You may need to wait an additional minute or two for each group to appear. <br/>

	**Note:** The IT admins group does not have a group email address because it's a Security group. Two additional group types are Mail-enabled Security groups and Distribution groups. Neither of these group types were used in this lab because it can take up to an hour for these two types of groups to appear in the Groups list; whereas Microsoft 365 groups and Security groups usually take just a matter of minutes to appear. 

25. You’re now ready to add members to the IT Admin security group. In the list of **Active teams and groups**, select the **Security** tab, and then select the **IT Admins** group (select the name and not the check box that appears to the left of the name). 

26. In the **IT Admins** pane that appears, the **General** tab is displayed by default. Select the **Members** tab.

27. The **Members** tab displays sections for the Owners and the Members. Under the **Members** section, you can see that there are zero (0) members. Under this section, select **View all and manage members** to add members to the group. 

28. In the **Members** pane that appears, select **+Add members**. This displays the list of active Microsoft 365 users.

29. In the list of users, select the check boxes for **Isaiah Langer**, **Megan Bowen**, and **Nestor Wilke**, and then at the bottom of the pane select the **Add (3)** button. 

30. In the **Members** pane, verify the three users that you selected appear. Select the **X** in the upper right-hand corner to close the **Members** pane. 

31. You now want to test the effect of deleting a group. In the list of **Active teams and groups,** select the **Microsoft 365** tab, then select the vertical ellipsis icon (**More actions**) that appears to the right of the **Inside Sales** group. In the drop-down menu that appears, select **Delete team**. 

32. In the **Delete Inside Sales?** pane that appears, select the **Delete team** button.

33. Once the group is deleted, select the **Close** button. 

34. This will return you to the list of **Active teams and groups**. The **Inside Sales** group should no longer appear under the **Microsoft 365** tab. If the Inside Sales group still displays, wait a couple of minutes and then select the **Refresh** option on the menu bar. The updated **Active teams and groups** list should no longer include the Inside Sales group.

356. To verify whether deleting this group affected any of its owners or members, select **Users** and then **Active Users** in the navigation pane. 

36. In the **Active users** list verify that the Inside Sales group's two owners (**Allan Deyoung** and **Patti Fernandez**) and the two members (**Diego Siciliani** and **Lynne Robbins**) still appear in the list of users. This verifies that deleting a group does not delete the user accounts that were owners or members of the group.

37. Remain logged into LON-CL1 with the **Microsoft 365 admin center** open in your browser for the next task.


### Task 4 – Recover Groups using PowerShell 

In this task, you will recover the Inside Sales group, which was a Microsoft 365 group. You can recover a deleted group for all group types except for security groups, which are deleted permanently. In this task, you will use Windows PowerShell to recover the Inside Sales group that you previously deleted. To use Windows PowerShell to perform this task, you will use Microsoft Graph PowerShell, which you should have installed in the first lab in this course.

Microsoft Graph PowerShell uses the Restore-MgDirectoryDeletedItem cmdlet to restore a recently deleted application, group, servicePrincipal, administrative unit, or user object from the deleted items "container". Deleted items will remain available to restore for up to 30 days. After 30 days, the items are permanently deleted. 

For the purpose of this lab exercise, you will begin by importing the Microsoft.Graph.Identity.DirectoryManagement sub-module, which contains the cmdlets needed to restore a deleted group. You will then connect to this sub-module with Directory Read/Write permission, which is needed to recover a deleted group. 

1. If you’re not logged into LON-DC1 as **ADATUM\Administrator** and password **Pa55w.rd**, then please do so now.

2. If Windows PowerShell is still open from the previous exercise, select the **Windows PowerShell** icon on the taskbar; otherwise, you must open an elevated instance of Windows PowerShell just as you did before. Maximize your PowerShell window.

3. In ther prior lab exercise, you installed Microsoft Graph PowerShell. You must now import the **Microsoft.Graph.Identity.DirectoryManagement** sub-module so that you can recover the deleted group. To do so, type the following command and then press Enter:  <br/>

		Import-Module Microsoft.Graph.Identity.DirectoryManagement

4. At the command prompt, you now must connect to Microsoft Graph and perform a request for permissions. Microsoft Graph PowerShell permissions are NOT pre-authorized. As such, you must perform a one-time, per-module request for permissions depending on your needs. The 'Directory.ReadWrite.All' scope allows Microsoft Graph to read and write data in Adatum's directory, such as users and groups. Type the following command and then press Enter: <br/>

		Connect-MgGraph -Scopes 'Directory.ReadWrite.All'

5. A **Sign in** window will appear requesting your credentials. Sign in using Holly's Microsoft 365 account of **Holly@xxxxxZZZZZZ.onmicrosoft.com** (where xxxxxZZZZZZ is the tenant prefix provided by your lab hosting provider) and **User.pw1** as the Password.  

6. On the **Permissions requested** dialog box that appears, select the **Consent on behalf of your organization** check box, and then select **Accept**.

7. At the command prompt, type the following command and then press Enter to display the repository of deleted groups (this should display the **Inside Sales** group that you earlier deleted):<br/>  
	
		Get-AzureADMSDeletedGroup   

8. At the command prompt, either type or copy and paste in the following command; however, do not press Enter yet as you must first replace {objectId} with the actual Object ID of the deleted Inside Sales group.  <br/>

		Restore-AzureADMSDeletedDirectoryObject -Id {objectId}

	After entering or copy and pasting in the command, you must replace {objectId} with the Object ID of the Inside Sales group that appears in the table of deleted groups that was displayed after you ran the command in the prior step. To do so, you must select the entire ID of the Inside Sales group and then copy it to the clipboard by pressing Ctrl-C. To paste in the object ID, place your cursor in the correct position in the command line where {objectId} should appear and then press Ctrl-V. <br/>
	
	After pasting in the Object ID, press Enter to run the command. This will retrieve and restore the deleted group whose Object ID matches the value you entered. <br/>

	**NOTE:** If nothing happens when you hit Enter, then extraneous hidden characters may have been pasted in following the object ID. If this occurs, retype the command and then after pasting in the object ID, hit the Delete key a couple of times to delete any extraneous characters that may have been pasted in following the object ID, and then press Enter again.  
		
9. Leave your Windows PowerShell window open for the next exercise; simply minimize the PowerShell window for now.

10. You should now verify the **Inside Sales** group has been recovered. To do this, go to the **Microsoft 365 Admin Center** in your Edge browser, and then under **Groups** in the navigation pane, select **Active teams & groups**. 

11. Verify the **Inside Sales** group has been restored and is present in the list of active groups. If the Inside Sales group does not appear, wait a minute or two and then select **Refresh** on the menu bar above the list of groups.

12. You now want to verify that the recovery process correctly updated the group's membership. From the **Active groups** windows, select the **Microsoft 365** tab if necessary, and then in the list of Microsoft 365 groups, select the **Inside Sales** group (select the name and not the check box).

13. In the **Inside Sales** pane that appears, select the **Members** tab. **Allan Deyoung** and **Patti Fernandez** should appear as owners of the group, and **Diego Siciliani** and **Lynne Robbins** should appear as members of the group. You have just verified that the deleted group is now fully restored.

14. Close the **Inside Sales** window.

15. Remain logged into LON-DC1 and leave your browser tabs open so that they’re ready for the next task. 


# Proceed to Lab 1 - Exercise 3

