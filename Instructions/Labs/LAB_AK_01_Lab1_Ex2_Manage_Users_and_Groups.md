# Learning Path 1 - Lab 1 - Exercise 2 - Manage Users and Groups 

In the following lab exercise, you will continue in your role as Holly Dickson, Adatum's new Microsoft 365 Administrator. In this exercise, you will perform several user and group management functions within Microsoft 365. You will begin by creating a Microsoft 365 user account for Holly, who will be assigned the Microsoft 365 Global Administrator role. You will create several Microsoft 365 groups and assign existing Microsoft 365 users as members of those groups. You will then delete one of the groups and then use Windows PowerShell to recover the deleted group.

**Note:** The VM environment provided by your lab hosting provider comes with over 20 existing Microsoft 365 user accounts, as well as a large number of existing on-premises user accounts. Several of the existing Microsoft 365 user accounts will be used throughout the labs in this course. Even though the MOD Administrator account has been created by your lab hosting provider, you will still create Holly Dickson's user account, since having more than one user who's assigned the Microsoft 365 Global Administrator role is a best practice. It will also provide you with the experience of creating a Microsoft 365 user account in case you're not familiar with the process.


### Task 1 - Create a User Account for Adatum's Microsoft 365 Administrator

Holly Dickson is Adatum’s new Microsoft 365 Administrator. Since a Microsoft 365 user account has not been set up for her, she initially signed into Microsoft 365 as the MOD Administrator account (the default Global administrator) in the previous lab. In this task, you will continue to be logged in as the MOD Administrator, during which you will create a Microsoft 365 user account for Holly. You will also assign the Microsoft 365 Global Administrator role to Holly's account. This role will provide Holly with the permissions needed to perform all administrative functions within Microsoft 365. Following this task, you will log in using Holly's new account and you will perform all remaining labs using Holly's persona. 

**License Note:** Before creating Holly's account, you will first verify the number of available licenses. In doing so, you will note that while your lab tenant provides 20 Microsoft 365 E5 licenses and 20 Enterprise Mobility + Security E5 licenses, all those licenses have already been assigned to the existing user accounts created by your lab hosting provider. As such, you must first unassign one of each license from an existing user so that you can assign them to Holly.

**Important:** As a best practice in your real-world deployment, you should always write down the credentials of the first Global administrator account (in this lab, it's the MOD Administrator account, whose username is admin@xxxxxZZZZZZ.onmicrosoft.com, where xxxxxZZZZZZ is the tenant prefix assigned by your lab hosting provider). You should store away this account information for security reasons. **This account should be a NON-personalized identity** that owns the highest privileges possible in a tenant. It should **not** be MFA activated because it is not personalized. Because the username and password for this first Global admin account are typically shared among several users, this account is a perfect target for attacks; therefore, it's always recommended that organizations create personalized service admin accounts (for example, an Exchange admin, SharePoint admin, and so on) and keep as few personal Global admins as possible. For those personal Global admins that you do create in your real-world deployment, they should each be mapped to a single user (such as Holly Dickson), and they should each have Azure Active Directory Multi-Factor Authentication (MFA) enforced. 

That being said, you will not turn on MFA for Holly's account because time is limited in this training course, and we don't want to take up lab time by forcing you to log in using a second authentication method every time Holly logs in.

1. On the LON-CL1 VM, the **Microsoft 365 admin center** should still be open in your Microsoft Edge browser from the prior lab exercise. You should be signed into Microsoft 365 as the **MOD Administrator**. 

2. Since you are adding a new user, you should begin by checking license availability before adding the user account. In the **Microsoft 365 admin center** navigation pane, select **Billing** and then select **Licenses**. 

3. On the **Licenses** page, the **Subscriptions** tab is displayed by default. In the list of subscriptions, note the **Enterprise Mobility + Security E5** and **Microsoft 365 E5** subscriptions don't have any available licenses. Your lab tenant provides 20 licenses for each subscription, but all 40 licenses have been assigned. Since you must assign Holly both an **Enterprise Mobility + Security E5** license and a **Microsoft 365 E5** license, you must first unassign the licenses from an existing user account to make them available for Holly. 

4. In the **Microsoft 365 admin center** navigation pane, select **Users** and then select **Active users**. In the **Active users** list, you will see the list of existing user accounts that were created by your lab hosting provider. Since Christie Cline will be moving to a new role in the company and will no longer be part of the Microsoft 365 pilot project, you will unassign the **Enterprise Mobility + Security E5** and **Microsoft 365 E5** licenses from her account so that you can reassign them to Holly Dickson's new account.

5. On the **Active users** page, in the list of users, select **Christie Cline** (select Christie's name and not the check box next to her name).

6. In the **Christie Cline** pane that appears, the **Account** tab is displayed by default. Select the **Licenses and apps** tab. Under **Licenses (2)**, select the check boxes next to **Enterprise Mobility + Security E5** and **Microsoft 365 E5** to clear them, and then select **Save Changes**. Once the changes are saved, close the **Christie Cline** pane. 

7. You're now ready to create a user account for Holly Dickson, who is Adatum's new Microsoft 365 Administrator. In doing so, you will assign Holly the Microsoft 365 Global Administrator role, which gives Holly global access to most management features and data across Microsoft online services. You will also assign Holly the two licenses that you just unassigned from Christie Cline. <br/>

	In the **Active Users** window, select the **Add a user** option that appears on the menu bar above the list of active users. This starts the **Add a user** wizard.

8. In the **Set up the basics** page of the **Add a user** wizard, enter the following information:

	- First name: **Holly**

	- Last name: **Dickson** 

	- Display name: When you tab into this field, **Holly Dickson** will appear.

	- Username: **Holly** <br/>
	
		‎**IMPORTANT:** To the right of the **Username** field is the domain field. It will be prefilled with the **xxxxxZZZZZZ.onmicrosoft.com** cloud domain (where xxxxxZZZZZZ is the tenant prefix provided by your lab hosting provider).<br/>
	
		After configuring this field, Holly’s username should appear as:<br/>

		**Holly@xxxxxZZZZZZ.onmicrosoft.com**  
	
	- Clear (uncheck) the **Automatically create a password** check box, which will display a new field for entering an administrator defined password.

	- In the new **Password** field that appears, enter the same **Microsoft 365 Tenant Password** provided by your lab hosting provider for the tenant admin account (i.e. the MOD Administrator account)

	- Clear (uncheck) the **Require this user to change their password when they first sign in** check box 

9. Select **Next**. If a **Save password** dialog box appears towards the top of the screen, select **Never**.

10. In the **Assign product licenses** page, enter the following information: <br/>

	- Select location: **United States**

	- Licenses: Under the **Assign user a product license** option, select the **Enterprise Mobility + Security E5** and **Microsoft 365 E5** check boxes

11. Select **Next**.

12. In the **Optional settings** page, select the drop-down arrow to the right of **Roles**. 

13. In the **Roles** section, select the **Admin center access** option. By selecting this option, the most commonly used Microsoft 365 administrator roles are enabled below it.  <br/>

	**Note:** All the admin roles will be displayed if you select **Show all by category**, which appears after the last common role. For Holly, you don't need to view all the admin roles by category, since Holly will be assigned the Global Administrator role that appears in the list of commonly used roles.

14. Select the **Global Administrator** check box. <br/>

	**Note:** A warning message will be displayed indicating that Adatum already has 7 Global admins. In a normal environment, this would be excessive and not recommended. For the purposes of this lab, the lab hosting provider assigned the Global admin role to the MOD Administrator and six other user accounts, which is not something you would normally see in a real-world deployment. However, for the purpose of this lab in your fictitious Adatum lab environment, ignore this message. **That being said, the best practice guideline that you should follow is to have from two to four Global Administrators your real-world Microsoft 365 deployments.** 

15. Select **Next**.

16. On the **Review and finish** window, review your selections. If anything must be changed, select the appropriate **Edit** link and make the necessary changes. Otherwise, if everything is correct, select **Finish adding**. 

17. On the **Holly Dickson added to active users** page, under the **User details** section, select the **Show** option to verify Holly's password is the same **Microsoft 365 Tenant Password** provided by your lab hosting provider for the tenant admin account (i.e. the MOD Administrator account).  <br/>

	**Note:** If you accidentally entered a different password, then once you return to the **Active Users** page, you will need to select the **Reset a password** icon (the key icon that appears when you hover over Holly's account) to change her password to the correct value.

18. Select **Close.**

19. If a window appears asking whether you want to respond to a survey on your experience, select **Cancel**.

20. Remain logged into the Client 1 VM (LON-CL1) with the Microsoft 365 admin center open in your browser for the next task.

### Task 2 – Set up Microsoft 365 User Accounts

After completing the previous task, you should still be signed into the **Microsoft 365 admin center** as the **MOD Administrator** account. In this task, you will begin implementing Adatum’s Microsoft 365 pilot project as Holly Dickson, Adatum’s new Microsoft 365 Administrator. Therefore, you will begin this task by logging out of Microsoft 365 as the MOD Administrator and you will log back in as Holly. 

In the prior task, you noticed that your Microsoft 365 trial tenant came equipped with a list of active users. As Holly Dickson, Adatum's Microsoft 365 Administrator, you have selected the following members of the Microsoft 365 pilot project team to assist with the initial phase of the deployment: Alex Wilber, Joni Sherman, Lynne Robbins, and Patti Fernandez. 

Each user is a key member of your pilot project team. While their user accounts are already present in Microsoft 365, you need to configure their passwords so they can more easily sign into Microsoft 365 when needed in the upcoming lab exercises. You will assign the same **Microsoft 365 Tenant Password** provided by your lab hosting provider for the tenant admin account (i.e. the MOD Administrator account) as their user password, just as you did when you created Holly's account. You also need to add a Microsoft 365 group that will be used in a later lab exercise. 

**Note:** Using the same password for multiple users should obviously never be done in the real-world. However, we're doing it here in your training environment to simply make things easier for students as they progress through the labs.

1. On the LON-CL1 VM, the **Microsoft 365 admin center** should still be open in your Microsoft Edge browser from the prior task. You should be signed into Microsoft 365 as the **MOD Administrator**. <br/>

	On the **Microsoft 365 admin center** tab, in the upper-right corner of the screen, note that it displays the MOD Administrator's name and initials. The name is displayed because of the custom theme that you created in the prior lab exercise that was associated with a group of Microsoft 365 pilot project users that included the MOD Administrator. Keep this in mind once you log back in as Holly Dickson. <br/>

	Select the user icon for the **MOD Administrator** (the **MA** circle) in the upper right corner of your browser. In the **MOD Administrator** window that appears, select **Sign out.** <br/>
	
	**Important:** When signing out of one user account and signing in as another, you should close all your browser tabs except for the **Sign out** tab. This is a best practice that helps to avoid any confusion by closing the windows associated with the prior user. Once you're signed out of the MOD Administrator account, take a moment and close all other browser tabs except for the **Sign out** tab. 
	
2. In your Microsoft Edge browser, in the **Sign out** tab, enter the following URL in the address bar to sign back into Microsoft 365: **https://portal.office.com**. 

3. In the **Pick an account** window, only the MOD Administrator's tenant admin account (the admin@xxxxxZZZZZZ.onmicrosoft.com account) that you just signed out from appears. Select **Use another account**. 

4. In the **Sign in** window, enter **Holly@xxxxxZZZZZZ.onmicrosoft.com** (where xxxxxZZZZZZ is the tenant prefix provided by your lab hosting provider). Select **Next**.

5. In the **Enter password** window, enter the same **Microsoft 365 Tenant Password** provided by your lab hosting provider for the tenant admin account (i.e. the MOD Administrator account) and then select **Sign in**.

6. If a **Welcome to Microsoft 365** dialog box appears in the middle of the screen, there's no option to close it. Instead, to the right of the window, select the forward arrow icon (**>**) two times and then select the check mark icon to advance through the slides in this messaging window. 

7. If a **Find more apps** window appears, select the **X** in the upper right-hand corner of the window to close it. 

8. The **Welcome to Microsoft 365** page appears in your Edge browser in the **Home | Microsoft 365** tab. This is Holly's Microsoft 365 home page. Note that Holly's initials appear in the upper-right corner of the screen; however, Holly's name is not displayed. This is because Holly's account did not exist at the time you added the Microsoft 365 pilot project users to the group that was associated with the custom theme in the prior lab exercise. Since Holly wants to see her name at the top of each Microsoft 365 window when she's logged into the system, she first wants to add her account to the group of Microsoft 365 pilot project users. <br>

	In the column of application icons that appears on the far left-side of the screen, select **Admin**. This opens the **Microsoft 365 admin center** in a new browser tab. 

9. In the **Microsoft 365 admin center**, select **Teams & groups** in the navigation pane, and then under it, select **Active teams & groups**. 

10. In the **Active teams and groups** page, there's a tab for viewing each of the group types. The **Microsoft 365** tab is displayed by default; this tab displays the existing Microsoft 365 groups. In the list of Microsoft 365 groups, select **M365 pilot project**.

11. In the **M365 pilot project** pane that appears, the **General** tab is displayed by default. Select the **Membership** tab.

12. In the **Membership** tab, the **Owners** sub-tab is displayed by default in the navigation pane. Select the **Members** sub-tab that appears below it.

13. In the **Members** sub-tab, select **+Add members**.

14. In the **Add team members to M365 pilot project** pane that appears, select inside the **Search by name or email address** field. In the list of users that appears, scroll down and select **Holly Dickson**. Select the **Add (1)** button, and then close the **Add team members to M365 pilot project** pane.

15. Select the **Refresh** icon that appears at the top of the screen, to the left of the address bar. Note how Holly Dickson's name appears next to her initials in the upper-right corner of the screen (Note: you may have to refresh twice to see Holly's name).

16. In the **Microsoft 365 admin center**, in the left-hand navigation pane, select **Users**, and then under it, select **Active users**.

17. In the **Active Users** window, when you hover your mouse over a user's **Display name**, a **key icon** appears to the right of the user's name. By selecting the key icon, you can reset a user's password. You must reset the passwords for Alex Wilber, Joni Sherman, Lynne Robbins, and Patti Fernandez to the same **Microsoft 365 Tenant Password** provided by your lab hosting provider for the tenant admin account (i.e. the MOD Administrator account).<br/>

    Hover your mouse over **Alex Wilber** and select the key icon that appears.

18. In the **Reset password** pane for Alex, clear (uncheck) the **Automatically create password** check box. 

19. In the **Password** field that appears, enter the same **Microsoft 365 Tenant Password** provided by your lab hosting provider for the tenant admin account (i.e. the MOD Administrator account). Select the eye (**Show Password**) icon at the end of the **Password** field to display the value that you entered. Verify that you correctly entered the tenant password.

20. Clear (uncheck) the **Require this user to change their password when they first sign in** check box.

21. Select **Reset Password**. If a **Save password** dialog box appears at the top of the screen, select **Never**. Then select **Close** on the **Password has been reset** pane.

22. Repeat steps 17-21 for **Joni Sherman**, **Lynne Robbins**, and **Patti Fernandez**. For these three accounts, reset each of their passwords to the same **Microsoft 365 Tenant Password** provided by your lab hosting provider for the tenant admin account (i.e. the MOD Administrator account). In step 19, don't forget to show the password you entered to verify it's the correct value.

23. Remain logged into LON-CL1 with the **Microsoft 365 admin center** open in your browser for the next task.


### Task 3 – Set up Microsoft 365 Groups 

In this task, you will create three new groups that will be used in later labs. You will then manage the groups by assigning users to them. Two groups will be Microsoft 365 groups; the third will be a Security group. Creating the two types of groups will enable you to see some of the differences between the group types. After creating the groups, you will then delete one of them. This will set up the next task, which examines how to recover a deleted group using Windows PowerShell.

1. On LON-CL1, in your Edge browser, you should still be logged into Microsoft 365 as **Holly Dickson**. 

2. In the **Microsoft 365 admin center**, select **Teams & groups** in the navigation pane, and then under it, select **Active teams & groups**. 

3. In the **Active teams and groups** page, there's a tab for viewing each of the group types. The **Microsoft 365** tab is displayed by default; this tab displays the existing Microsoft 365 groups.  <br/>

    Select the **Add a group** option that appears on the menu bar above the list of groups. This initiates the **Add a group** wizard. 

4. In the **Add a group** wizard, on the **Choose a group type** page, the **Microsoft 365 (recommended)** option should be selected by default. If it isn't, then select this option now. Select **Next**. 

5. In the **Set up the basics** page, enter **Inside Sales** in the **Name** field, and then enter **Collaboration group for the Inside Sales team** in the **Description** field (Note: even if you don't enter a description, you must still select into this field to enable the **Next** button). Select **Next**.

6. You will now assign Allan Deyoung and Patti Fernandez as owners of the Inside Sales group. In the **Assign owners** window, select **+Assign owners**.
	
7. In the **Assign owners** pane that appears, select the check boxes next to **Allan Deyoung** and **Patti Fernandez**, and then select the **Add (2)** button at the bottom of the pane.

8. On the **Assign owners** page, Allan and Patti should appear as owners of the group. Select **Next**.

9. You will now assign Diego Siciliani and Lynne Robbins as members of the Inside Sales group. In the **Add members** page, select **+Add members**.

10. In the **Add members** pane that appears, select the check boxes next to **Diego Siciliani** and **Lynne Robbins**, and then select the **Add (2)** button at the bottom of the pane.

11. On the **Add members** page, Diego and Lynne should appear as members of the group. Select **Next**.

12. In the **Edit settings** page, enter the following information: <br/>

	- Enter **insidesales** in the **Group email address** field.
	- In the **Privacy** field, **Public** should be selected by default. Do not change this value.
	- Under the **Add Microsoft Teams to your group** section, verify the **Create a team for this group** check box is selected (select it if it's blank), and then select **Next**.

13. In the **Review and finish adding group** page, review the content that you entered. If anything needs to be fixed, select **Edit** under the specific area that needs adjustment, make any necessary corrections, and then select **Next** to continue back to this page. Once everything is correct, select **Create group**.

14. It may take a minute or so for the **Inside Sales group created** window to appear. Note the comment at the top of the page that it may take 5 minutes for the new group to appear in the list of Active groups. </br>

	Select **Close**. This returns you to the **Active teams and groups** page, which should display the **Microsoft 365** group tab. Since the Inside Sales group was a Microsoft 365 group, it should eventually display on this tab.

15. Repeat steps 3-14 to add a new group with the following information: <br/>

	- Group type: **Microsoft 365 (recommended)**

	- Name: **Accounting**

	- Description: **Complete list of all Accounting staff**<br/>

	- Owner: **Joni Sherman**

	- Members: You will not add members at this time.  **Note:** You can add members to a group at the time you create the group (as you did with the Inside Sales group), as well as after you create a group. For the purpose of this Accounting group, you will add members after you've created the group. This way you can see the two methods of adding group members. So for now, select **Next** to skip through this step and not add members at this time. <br/>

	- Group email address: **accounting**

	- Privacy: **Public**

16. After creating the Accounting group, you will be returned to the **Active teams and groups** window. It may take a few minutes for the Accounting group to appear, so you may need to select the **Refresh** option on the menu bar once or twice. Note that there are four tabs on this page, one for each group type (Microsoft 365, Distribution list, Mail-enabled security, and Security). The **Microsoft 365** tab is displayed by default, which is the group type assigned to the Accounting group. So the Accounting group should be displayed in this tab.

17. Once the **Accounting** group appears under the **Microsoft 365** tab, select the **Accounting** name. You will now add members to this group.

18. In the **Accounting** pane that appears, the **General** tab is displayed by default. Select the **Membership** tab.

19. In the **Membership** tab, four sub-tabs (Owners, Members, Site visitors, and About membership and permissions) are displayed in the left-hand column. The **Owners** sub-tab is displayed by default. In the **Owners** sub-tab, Joni Sherman should appear as the only group owner. 

20. Select the **Members** sub-tab. In the **Members** sub-tab, select the **Add members** button. 

21. In the **Add team members to Accounting** pane, select in the **Search by name or email address** field. This displays the list of active users. <br/>

	In the list of users, select **Alex Wilber**. Note that you have to select back into the field to display the list of users. Select **Joni Sherman**, select back in the field, and then select **Lynne Robbins**. Once all three users are selected, select the **Add (3)** button at the bottom of the pane.

22. Once the three new members have been added to the group, select the **X** in the upper right-hand corner of the **Accounting** pane to close it. 

23. After adding members to the Accounting group, you will be returned to the **Active teams and groups** window. Select the **Security** tab to display the list of Security groups. Repeat steps 3-14 to add a new group with the following information: <br/>

	- Group type: **Security**

	- Name: **IT Admins**

	- Description: **IT administrative personnel**<br/>

	**Note:** There is no owner, email address, or privacy setting for Security groups. Members must be added to a Security group after creating the group, which you will do in the next few steps. On the **Edit settings** page, you're NOT going to assign Azure AD roles to the group, so simply select **Next**.

24. After you finish adding the group, the **Active teams and groups** page should be displayed. Check whether the **IT Admins** group appears under the **Security** tab.   <br/>

	**Tip:** If the group does not immediately appear in the list of Security groups, wait a minute or so and then select the **Refresh** option on the menu bar (to the right of **Add a group**). You may need to wait an additional minute or two for the group to appear. <br/>

	**Note:** As you can see from the tabs on this page, there are two additional group types besides the Microsoft 365 and Security groups. These two group types are **Mail-enabled Security** groups and **Distribution** groups. Neither of these group types were used in this lab because it can take up to an hour for these two types of groups to appear in the Groups list; whereas Microsoft 365 groups and Security groups usually take just a minute to two to appear. 

25. You’re now ready to add members to the **IT Admins** security group. In the **Security** tab, select the **IT Admins** group (select the name and not the check box that appears to the left of the name). 

26. In the **IT Admins** pane that appears, the **General** tab is displayed by default. Select the **Members** tab.

27. The **Members** tab displays sections for the Owners and the Members. Under the **Members** section, you can see that there are no members. Under this section, select **View all and manage members** to add members to the group. 

28. In the **Members** pane that appears, select **+Add members**. This displays the list of active Microsoft 365 users.

29. In the list of users, select the check boxes for **Isaiah Langer**, **Megan Bowen**, and **Nestor Wilke**, and then at the bottom of the pane select the **Add (3)** button. 

30. In the **Members** pane, verify the three users that you selected appear. Select the **X** in the upper right-hand corner to close the **Members** pane. 

31. You now want to test the effect of deleting a group. In the list of **Active teams and groups**, select the **Microsoft 365** tab. In the list of Microsoft 365 groups, locate the **Inside Sales** group and then select the vertical ellipsis icon (**More actions**) that appears to the right of the **Inside Sales** group. In the drop-down menu that appears, select **Delete team**. 

32. In the **Delete Inside Sales?** pane that appears, select the **Delete team** button.

33. Once the group is deleted, select the **Close** button. 

34. This will return you to the list of **Active teams and groups**. The **Inside Sales** group should no longer appear under the **Microsoft 365** tab. If the Inside Sales group still displays, wait a couple of minutes and then select the **Refresh** option on the menu bar. The updated **Active teams and groups** list should no longer include the Inside Sales group.

35. To verify whether deleting this group affected any of its owners or members, select **Active Users** in the navigation pane. 

36. In the **Active users** list verify that the Inside Sales group's two owners (**Allan Deyoung** and **Patti Fernandez**) and the two members (**Diego Siciliani** and **Lynne Robbins**) still appear in the list of users. This verifies that deleting a group does not delete the user accounts that were owners or members of the group.

37. Remain logged into LON-CL1 with the **Microsoft 365 admin center** open in your browser for the next task.


### Task 4 – Recover Groups using PowerShell 

In this task, you will recover the Inside Sales group, which was a Microsoft 365 group. You can recover a deleted group for all group types except for security groups, which are deleted permanently. In this task, you will use Windows PowerShell to recover the Inside Sales group that you previously deleted. To use Windows PowerShell to perform this task, you will use Microsoft Graph PowerShell, which you should have installed in the first lab in this course.

**IMPORTANT - Microsoft Graph PowerShell work around:** In a normal situation, you would use the Restore-MgDirectoryDeletedItem cmdlet to restore a recently deleted application, group, servicePrincipal, administrative unit, or user object from the deleted items "container" (deleted items will remain available to restore for up to 30 days; after 30 days, the items are permanently deleted). This Microsoft Graph PowerShell cmdlet requires that you provide the object ID of the item being restored. While you would normally use the Get-MgDirectoryDeletedItem cmdlet to display the list of deleted objects (along with their object IDs), this cmdlet is currently not returning any data. As a workaround, this task will invoke a direct REST API call by using the Invoke-MgGraphRequest cmdlet.

**NOTE - Microsoft Graph PowerShell:** If you'll recall, in the first lab exercise for this course, you installed Microsoft Graph PowerShell. However, you did not import any of its 30+ sub-modules. You were told at the time that only 3 modules will be used in the labs for this training course, so you would install each sub-module individually as they were needed. For this lab exercise, you will import the **Microsoft.Graph.Identity.DirectoryManagement** sub-module and the **Microsoft.Graph.Groups** sub-module. You will then connect to these sub-modules with the appropriate Read/Write permissions that are needed to view and recover a deleted group. 

1. On LON-CL1, if Windows PowerShell is still open from the previous lab exercise, select the **Windows PowerShell** icon on the taskbar; otherwise, you must open an elevated instance of Windows PowerShell just as you did before. Maximize your PowerShell window.

2. In the prior lab exercise, you installed Microsoft Graph PowerShell. You must now import both the **Microsoft.Graph.Groups** sub-module (which contains the cmdlets to view and maintain Microsoft groups) and the **Microsoft.Graph.Identity.DirectoryManagement** sub-module (which contains the cmdlets necessary to recover the deleted group). To do so, type the following commands and then press Enter:  <br/>

		Import-Module Microsoft.Graph.Groups

		Import-Module Microsoft.Graph.Identity.DirectoryManagement

3. At the command prompt, you must now connect to Microsoft Graph and perform a request for permission to use the cmdlets that were just imported. Microsoft Graph PowerShell permissions are NOT pre-authorized. As such, you must perform a one-time, per-module request for permissions depending on your needs. <br/>

	- The 'Group.ReadWrite.All' scope is required to display the current list of active groups and restore the deleted group. <br/>
	- The 'Directory.ReadWrite.All' scope provides permission to read and write data in Adatum's directory, such as users and groups, and restore the deleted group. <br/>

	Type the following command and then press Enter: <br/>
		
		Connect-MgGraph -Scopes 'Group.ReadWrite.All', 'Directory.ReadWrite.All'

4. A **Sign in** window will appear requesting your credentials. Sign in using Holly's Microsoft 365 account of **Holly@xxxxxZZZZZZ.onmicrosoft.com** (where xxxxxZZZZZZ is the tenant prefix provided by your lab hosting provider). For the password, sign-in with the same **Microsoft 365 Tenant Password** provided by your lab hosting provider for the tenant admin account (i.e. the MOD Administrator account).  

5. On the **Permissions requested** dialog box that appears, select the **Consent on behalf of your organization** check box and then select **Accept**.

6. You will now use Microsoft Graph PowerShell to display the list of active groups. The Inside Sales group should not appear in this list. Type the following command and press Enter (Note: it may take a minute or so for the list of groups to appear):

		Get-MgGroup

7. As the note at the start of this task indicated, at this point you would normally run the **Get-MgDirectoryDeletedItem** cmdlet to display the list of deleted objects, which would include the object ID of the **Inside Sales** group that you deleted in the prior task. However, given the current issues with this cmdlet, you should instead run the following series of commands to retrieve this object ID. Type in each command and press Enter:  <br/>  
	
		$url = "https://graph.microsoft.com/v1.0/directory/deleteditems/microsoft.graph.group"

		Invoke-MgGraphRequest -Method GET -Uri $url -ContentType "application/json" -outVariable deletedGroups

		$DeletedGroup = $deletedGroups.value | where displayName -eq 'Inside Sales'

	**Note:** After running these commands, the attributes of the deleted Inside Sales group will be stored in the $DeletedGroup variable.

8. Now that you have captured the attributes of the Inside Sales group, you can run the **Restore-MgDirectoryDeletedItem** cmdlet to restore the group. When doing so, you must declare the group's object ID as the parameter next to "-DirectoryObjectId". While you would normally copy and paste in the object ID (for example: -DirectoryObjectId 'e76bbcdb-24c5-41a6-805d-b352976fd2a8'), the current issue with the **Get-MgDirectoryDeletedItem** cmdlet doesn't allow us to identify the actual Id value. As such, you had to run the prior commands to capture the group's attributes in the $DeletedGroup variable. You will now run the **Restore-MgDirectoryDeletedItem** cmdlet, where you will direct it to use the **id** field from among the attributes stored in the $DeletedGroup variable. Type in the following command and press Enter:  <br/>

		Restore-MgDirectoryDeletedItem -DirectoryObjectId $DeletedGroup.id

9. You should now verify the **Inside Sales** group has been recovered. While you can obviously do this in the **Microsoft 365 admin center**, since this task is working with PowerShell, let's verify the recovery using Microsoft Graph PowerShell. To do so, type the following command to get a list of the active groups, which should now include the Inside Sales Group:  <br/>

		Get-MgGroup

10. Leave your Windows PowerShell window open for the next exercise; simply minimize the PowerShell window for now.

11. You now want to verify that the recovery process correctly updated the group's membership. In your Edge browser, in the **Microsoft 365 admin center**, navigate to the **Active teams & groups** windows, select the **Microsoft 365** tab if necessary, and then in the list of Microsoft 365 groups, select the **Inside Sales** group (select the name and not the check box). <br/>

	**Note:** If the Inside Sales group does not appear, wait a minute or two and then select **Refresh** on the menu bar above the list of groups.

12. In the **Inside Sales** pane that appears, select the **Membership** tab. In the **Membership** tab, three sub-tabs (Owners, Members, and About membership and permissions) are displayed in the left-hand column. The **Owners** sub-tab is displayed by default. **Allan Deyoung** and **Patti Fernandez** should appear as owners of the group.

13. Select the **Members** sub-tab. **Diego Siciliani** and **Lynne Robbins** should appear as members of the group. You have just verified that the deleted group is now fully restored.

14. Close the **Inside Sales** window.

15. Remain logged into LON-CL1 and leave your browser tabs open so that they’re ready for the next task. 


# Proceed to Lab 1 - Exercise 3

