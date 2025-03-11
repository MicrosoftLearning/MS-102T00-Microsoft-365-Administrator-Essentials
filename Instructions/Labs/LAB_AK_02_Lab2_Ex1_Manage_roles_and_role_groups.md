# Learning Path 2 - Lab 2 - Exercise 1 - Manage roles and role groups

In this exercise, you will continue in your role as Holly Dickson, Adatum's new Microsoft 365 Administrator. As part of Adatum's Microsoft 365 pilot project, you will manage administration delegation by assigning Microsoft 365 administrator roles to several of the Microsoft 365 user accounts that were created by your lab hosting provider. This exercise will provide you with experience in using three different methods to assign these roles: 1) by assigning a role directly to a user account in the Microsoft 365 admin center, 2) by creating a role group, assigning roles to the role group, and then assigning the role group to a user in the Microsoft 365 admin center, and 3) by assigning a role to a user using Windows PowerShell. Once you have assigned Microsoft 365 admin roles to several of the existing user accounts, you will then test those assignments by verifying the users have the permissions to act in accordance with their roles.

### Task 1 - Assign an administrator role in the Microsoft 365 Admin Center

Holly Dickson has been assigned the Microsoft 365 Global Administrator role. As you continue in your role as Holly, you will use the Microsoft 365 admin center to assign administrator rights to one of the Adatum users. In this task, you will assign the Billing Administrator role to Diego Siciliani's user account.

1. In the prior lab exercise, you created a new domain for Adatum on LON-DC1. You should now switch back to **LON-CL1** to perform the Microsoft 365 administrative tasks in this lab exercise. As a best practice, typical Microsoft 365 administrative tasks should be performed on a client PC rather than the company's domain controller.  <br/>

	Switch to **LON-CL1**. 

2. On **LON-CL1**, in the **Microsoft 365 admin center** in your Edge browser, you should still be logged in as Holly Dickson from a prior lab exercise. In the navigation pane, select **Users** and then select **Active Users**. 

3. In the **Active users** list, select **Diego Siciliani**.  <br/>

	**Note:** Select Diego’s name; do not select the check box to the left of his name. The check box is typically used for selecting multiple users when you want to perform one of the user-related actions on the menu bar that appears above the list of users, such as **Manage product licenses** and **Manage roles**. Selecting a user’s name opens a property pane specifically for that user.

4. In the **Diego Siciliani** pane that appears, the **Account** tab is displayed by default. In this tab, scroll down to the **Roles** section and select **Manage roles**. 

5. In the **Manage admin roles** window, the **User (no admin center access)** option is currently selected by default. Now that you want to assign Diego an administrator role, select the **Admin center access** option. This enables a list of commonly used admin roles for selection. 

6. Diego has been promoted to Billing Administrator, but since this role does not appear in the list of commonly used roles, scroll down and select **Show all by category**. 

7. In the list of roles that are sorted by category, scroll down to the **Other** category, select the **Billing Administrator** check box, and then select **Save changes**. <br/>

	**Tip:** Note the message that appears at the top of the pane once the admin role change is saved. This message provides the following best practice that you should keep in mind as you maintain administrative roles in your real-world deployments: **Give users only the access they need by assigning the least-permissive role.**

8. On the **Manage admin roles** window, select the **X** in the upper-right corner of the screen to close it. This returns you to the **Active users** list. 

9. Remain logged into LON-CL1 and the Microsoft 365 admin center as Holly Dickson.


### ‎Task 2 - Assign an administrator role using a role group in the Microsoft 365 admin center

In the prior task, you assigned an administrator role directly to Diego Siciliani's user account in the Microsoft 365 admin center. In this task, you will assign roles using a role group instead. You will create a Security role group, assign user management roles to it, and then assign the role group to Lynne Robbin's user account in the Microsoft 365 admin center.

1. On LON-CL1, you should still be logged into the Microsoft 365 admin center as Holly Dickson. If not, then do so now.

2. In the **Microsoft 365 admin center**, select **Teams & groups** in the navigation pane, and then select **Active teams & groups**. 

3. On the **Active teams & groups** page, the **Teams & Microsoft 365 groups** tab is displayed by default. Select the **Security groups** tab.

4. On the **Security groups** tab, select **+Add a security group** on the menu bar. Doing so initiates the **Add a security group** wizard.

5. In the **Add a security group** wizard, on the **Set up the basics** page, enter **User management role group** in the **Name** field. Enter **This role group contains user management roles** in the **Description** field. Select **Next**.

6. On the **Edit settings** page, select the **Azure AD roles can be assigned to the group** check box, and then select **Next**.

7. On the **Review and finish adding group** page, review the settings. If any settings need to be changed, select the appropriate **Edit** option and make the change. When all the settings are correct, select **Create group**.

8. Once the **User management role group** is created, select **Close**.

9. Now that you created the role group, you must assign the corresponding roles to it. On the **Active teams and groups** page, the **Security groups** tab is displayed. Select the **User management role group** to open its details pane.

10. On the **User management role group** pane, the **General** tab is displayed by default. Under the **Roles** section, select **Manage roles**.

11. On the **Manage admin roles** pane that appears, select the **Admin center access** option. In the list of common administrator roles that appears directly below this option, select the **User Administrator** and **User Experience Success Manager** check boxes. Then select the **Show all by category** option. Scroll down to the **Identity** category. Note how the **User Administrator** role is already selected, since you selected this earlier in the list of commonly used roles. In this **Identity** category, select the **Helpdesk Administrator** role and then select **Save changes**. 

12. In the **Manage admin roles** pane, the three selected roles should appear under the **Admin center access** option. Select the **X** in the upper-right corner of the pane to close it.

13. Under the **Security groups** tab, select **User management role group**. In the **User management role group** pane that appears, verify the three roles appear in the **Roles** section. Close this pane.

14. Now that you've assigned the roles to the role group, you must assign the role group to Lynne Robbin's user account. In the **Microsoft 365 admin center**, select **Active users**.

15. On the **Active users** page, select **Lynne Robbins**. 

16. In the **Lynne Robbins** pane that appears, the **Account** tab is displayed by default. In the prior task, when you assigned the Billing Administrator role to Diego Siciliani's account, you selected the **Manage roles** option under the **Roles** section. However, since you will be assigning Lynne's roles through a role group, you must assign Lynne as a member of the Security role group that you just created. It's through the group assignment that Lynne will inherit the roles assigned to the role group. Therefore, under the **Groups** section, select **Manage groups**. 

17. On the **Manage groups** pane, select **+Assign memberships**.

18. On the **Assign memberships** pane, select the **User management role group** check box, and then select **Add(1)**.

19. Once a **Saved** notification appears at the top of the page, close this pane. 

20. To verify that Lynne inherited the roles that were assigned to the User management role group, select **Lynne Robbins** from the list of active users. 

21. In the **Lynne Robbins** pane that appears, in the **Account** tab that is displayed by default, you should see the three User management roles that were assigned to the Lynne. Under the **Roles** section**, select **Manage roles**.

22. In the **Manage admin roles** pane that appears, under the **Admin center access** option, note the three roles that are selected and the name of the group from which they were assigned to Lynne. Also note how the three roles are grayed out. This indicates that you can't unselect the roles from this window. Because the roles were assigned to Lynne from a role group that contained these roles, you can only unassign the roles by removing Lynne as a member of the role group. You have just verified that Lynne is assigned these roles. Close this **Manage admin roles** pane.

23. Remain logged into LON-CL1 and the Microsoft 365 admin center as Holly Dickson.

### Task 3 - Assign an administrator role using Windows PowerShell  

In this task, you will use Windows PowerShell to assign a role to a user account. Doing so will give you experience performing this management function in PowerShell, since some administrators prefer performing maintenance such as this using PowerShell.

In this task, Holly wants to assign Patti Fernandez to the Service Support Administrator role. To add a user to an admin role using the Microsoft Graph PowerShell module, you must first obtain the object ID of the user and the object ID of the role. In this task, you will use Microsoft Graph to obtain the respective IDs and then create the role assignment. 

PowerShell also enables you to display all the users assigned to a specific role, which can be very important when auditing your Microsoft 365 deployment. In this task, you will also learn how to use PowerShell to display all the users assigned to a specific role.

1. On LON-CL1, select the Windows PowerShell icon on the taskbar that you left open from a prior lab. If you closed the PowerShell window, then open an elevated instance of it using the same instruction as before. 

2. In the earlier lab exercise, you connected to Microsoft Graph and requested "Directory.ReadWrite.All" permissions to run the cmdlets that restored the deleted group. To update User and role objects in this task, Holly must now request Read/Write permissions for each object. To request these permissions, type the following command at the command prompt and then press Enter:  <br/>

		Connect-MgGraph -Scopes 'User.ReadWrite.All', 'RoleManagement.ReadWrite.Directory'

3. In the **Pick an account** window that appears, select Holly Dickson's account.

4. On the **Permissions requested** dialog box that appears, select the **Consent on behalf of your organization** check box, and then select **Accept**.

5. Holly wants to assign **Patti Fernandez** to the **Service Support Administrator** role. To assign this role using Microsoft Graph PowerShell, you must first obtain the object ID of the Service Support Administrator role so that you can assign it to Patti.

	**Important:** Before you perform this step, verify your PowerShell window is in full screen mode. The role name appears in the second column of the output. If you're not in full screen mode, you won't see the role name associated with each Object ID. 

6. To assign a role in Microsoft Graph PowerShell, you must first locate its object ID. There's two ways in which you can view the role templates - you can either display the entire list of role templates, or you can display the template for a specific role. As a learning experience, you will perform both methods so that you can see the difference. <br/>

	Let's start by displaying the complete list of role templates along with their object ID and display name. To do so, type in the following command and then press Enter: <br/>

		Get-MgDirectoryRoleTemplate | Sort DisplayName | Format-Table Id, DisplayName

	As you can see after having run this command, you must scroll through the list of role templates looking for the Service Support Administrator role. You can easily see how this can be tedious, even with the table sorted. As an alternative, run the following command to query for a specific role template - in this case, the "Service Support Administrator" role template: <br/>

 		Get-MgDirectoryRoleTemplate | ? DisplayName -eq "Service Support Administrator" | Format-Table Id, DisplayName

	After having run this command, you can see that it displays only the requested role template. Obviously, there may be times when displaying the entire list of role templates is necessary. But when you need to look up a single role template, running the second PowerShell command will be much more efficient than having to scroll through the entire list of templates.

7. To assign Patti Fernandez to the newly enabled Service Support Administrator role, you must first obtain the object ID for Patti's user account. To do so, type the following command and press Enter:

		Get-MgUser -Filter "DisplayName eq 'Patti Fernandez'" | Format-Table ID, DisplayName

8. Now that you know the object ID of the Service Support Administrator role and the object ID of Patti's user account, you can assign the role to Patti. Perform the following steps to complete this process, replacing the two IDs for the values displayed from the previous two steps.

		New-MgRoleManagementDirectoryRoleAssignment -RoleDefinitionId 'paste in the role ID here' -PrincipalId 'paste in Pattis ID here' -DirectoryScopeId '/'

	**Note:** The DirectoryScopeId parameter indicates the assignment is at the tenant / directory level.

9. You now want to verify that Patti has been assigned to the Service Support Administrator role. To do this, we will run two commands. The first obtains the assigned role and stores it in a variable, and the second displays IDs of the users assigned to the role.

		$assignedRole = Get-MgDirectoryRole -Filter "DisplayName eq 'Service Support Administrator'"
		Get-MgDirectoryRoleMember -DirectoryRoleId $assignedRole.Id

10. The prior command only displays the IDs of the users assigned to the selected role. However, you can match the ID that's displayed with Patti's ID to verify that her account has been assigned the **Service Support Administrator** role. As you can see, Patti is the only user assigned to the role. 

11. Let's now repeat this process to see all the users assigned to the Global Administrator role.

		$assignedRole = Get-MgDirectoryRole -Filter "DisplayName eq 'Global Administrator'"
		Get-MgDirectoryRoleMember -DirectoryRoleId $assignedRole.Id

12. Verify there are multiple Adatum users who've been assigned the Global Administrator role. In a real-world scenario, the Microsoft 365 Administrator would use this PowerShell command to monitor how many global admins exist in their Microsoft 365 deployment. They would then remove the Global Administrator role from any users who truly shouldn't have it (remember, the best practice guideline is to have between 2 to 4 global admins in a Microsoft 365 deployment, depending on the size of the organization).  <br/>

	In the case of this lab, while your lab hosting provider assigned the Global Administrator role to users other than the MOD Administrator (and you assigned it to Holly Dickson), you'll leave these users as is. In this fictitious Adatum deployment, there's no point in wasting your time removing this role from their accounts. Plus, some of the future lab tasks are based on these users being assigned the Global Administrator role. <br/>

	**IMPORTANT:** Just remember that in your real-world deployment, the Microsoft 365 Administrator should monitor the Global Administrator role on a periodic basis to keep the number of assigned users between 2 and 4.
	
13. Leave your Windows PowerShell session open for future lab exercises, but minimize it before going on to the next task.


### Task 4 - Validate role assignments 

In this task, you will begin by examining the administrative properties of two users, Joni Sherman and Lynne Robbins. You will then log into the Microsoft 365 home page on the Client 2 VM (LON-CL2) as each user to confirm several of the changes that you made when managing their administrative delegation in the prior tasks. Finally, as Lynne Robbins, you will perform two important user account maintenance tasks - resetting passwords and blocking user accounts.

1. On LON-CL1, you should still be logged into the Microsoft 365 admin center as Holly Dickson. If not, then do so now.

2. In the **Microsoft 365 admin center**, if you are not displaying the **Active Users**, then navigate to that page now.  

3. In the **Active users** list, select **Joni Sherman**. 

4. In the **Joni Sherman** properties window, the **Account** tab is displayed by default. Under the **Roles** section, it should indicate that Joni has **No administrator access**. Select the **X** in the upper right corner to close Joni's properties window.

5. In the **Active users** list, select **Lynne Robbins**. 

6. In **Lynne Robbins's** properties window, it should indicate that Lynne has been assigned the **User Administrator** role. Close Lynne's properties window.

7. Switch to the Client 2 VM (**LON-CL2**).

8. In **LON-CL2**, on the log-in screen, you will log in as the local **LON-CL2\Admin** account with a password of **Pa55w.rd**.

9. If a **Networks** window appears, select **Yes**.

10. On the taskbar, select the **Microsoft Edge** icon. Maximize your Edge browser window if necessary.

11. In your **Edge** browser navigate to **https://portal.office.com**. 

12. You will begin by signing into Microsoft 365 as **Joni Sherman**. In the **Sign-in** window, enter **JoniS@xxxxxZZZZZZ.onmicrosoft.com** (where xxxxxZZZZZZ is the tenant prefix provided by your lab hosting provider). Since you're signing in as Joni Sherman, enter this **User Password** provided by your lab hosting provider in the **Enter password** window. <br>

	In the **Update your password** dialog box that appears, enter the **User Password** provided by your lab hosting provider in the **Current password** field. Then enter the New User Password in the **New password** and **Confirm password** fields and select **Sign in**.

13. On the **Stay signed in?** window, select the **Don't show this again** check box and then select **Yes**. If a **Save password** window appears, select **Never**.

14. If a **Welcome to Microsoft 365** dialog box appears in the middle of the page, select the forward-arrow (>) twice and then the check mark to close it.

15. If a **Find more apps** window or a **Create with Microsoft 365** window or any other introductory-type window appears, select the **X** in the top corner of the window to close it.

16. On the **Welcome to Microsoft 365** window, which is Joni's Microsoft 365 home page, a navigation pane appears on the side of the screen that indicates the applications the user has permission to access. In this **Apps** pane, note how the **Admin** option is not displayed. This is because Joni was never assigned a Microsoft 365 administrator role. 

17. You will now sign out of Microsoft 365 as Joni. In **Microsoft Edge**, at the top right of the **Welcome to Microsoft 365** page, select the user icon for **Joni Sherman** (the circle in the top corner with Joni's picture in it), and in the **Joni Sherman** window that appears, select **Sign out.** 

18. You will now sign back into Microsoft 365 as **Lynne Robbins**. In your current **Edge** browser tab, it should display a message indicating **Joni, you're signed out now**. In this window, it gives you the option of signing back in as Joni, or signing in as a different user. <br/>

	Select **Switch to a different account**, and in the **Email address** field that appears, enter **LynneR@xxxxxZZZZZZ.onmicrosoft.com** (where xxxxxZZZZZZ is the tenant prefix provided by your lab hosting provider) and then select **Sign in**. In the **Enter password** window, enter the **User Password** provided by your lab hosting provider and select **Sign in**. <br>

	In the **Update your password** dialog box that appears, enter the **User Password** provided by your lab hosting provider in the **Current password** field. Then enter the New User Password in the **New password** and **Confirm password** fields and select **Sign in**. 

19. If a **Welcome to Microsoft 365** dialog box appears, select the forward arrow (>) two times and then select the check mark to close the window.

20. If a **Find more apps** window or a **Create with Microsoft 365** window or any other introductory-type window appears, select the **X** in the top corner of the window to close it.

21. On the **Welcome to Microsoft 365** window, which is Lynne's Microsoft 365 home page, note how the **Admin** icon is displayed in the navigation pane on the side of the screen. This icon appears because Lynne was assigned to a Microsoft 365 administrator role. Select the **Admin** icon to open the Microsoft 365 admin center.

22. In the **Microsoft 365 admin center**, select **Users** on the navigation pane and then select **Active users**. 

23. As the **User Administrator**, Lynne has permission to change user passwords. Lynne was recently contacted by **Diego Siciliani** and **Pradeep Gupta**, who each reported that their passwords may have been compromised. Per Adatum's company policy, Lynne must reset their passwords to a temporary value, and then force them to reset their password at their next login.   <br/>

	‎In the **Active users** list, as you move your mouse from one user account to another, notice the **key (Reset a password)** icon that appears to the right of each user's name. Select the key icon that appears to the right of **Diego Siciliani's** name.

24. In the **Reset password** window for Diego, if the **Automatically create a password** check box displays a check mark, then select this box to clear it. This will enable Lynne to manually assign Diego a temporary password.  

25. Enter **diego** in the **Password** field. Note to the right of the password, the system displays a message indicating this is a **Weak** password. Also note the message that appears below the field indicating the requirements for a strong password. Finally, note how the **Reset password** button at the bottom of the pane is not enabled. **This button will only be enabled once you enter a strong password**.  

26. Verify the **Require this user to change their password when they first sign in** checkbox is selected (if not, then select it now to show a checkmark). Enter **Pa55w.rd** in the **Password** field. Note that the **Password** field indicates this is a Strong password. <br/>

	However, now select the **Require this user to change their password when they first sign in** checkbox to clear it. Note the error message that appears indicating the password (Pa55w.rd) contains a word, phrase, or series of numbers that makes it easily guessable. In this case, you entered a variation of the word **password**, which will trigger this error. The system allows you to enter this password if you force the user to change it at their first sign-in. But if you don't force the user to enter a different password at their first sign-in, then this password isn't allowed.

27. After these two failed password attempts, Lynne has decided to let Microsoft 365 automatically generate a password. Select the **Automatically create a password** check box so that it displays a check mark. 
	
28. The password that's automatically generated will just be a temporary password because Lynne wants to force Diego to change it the next time he logs in. Therefore, verify the **Require this user to change their password when they first sign in** check box displays a check mark; if the box is clear, then select it so that it displays a check mark.

29. Select **Reset password**.

30. If prompted to save the password, select **never** to close the window.

31. You should receive an error message indicating that you cannot reset Diego’s password because he has been assigned an admin role. In Diego’s case, you assigned him the Billing Administrator role earlier in this lab exercise. Since only Global administrators can change another administrator's password, and because Lynne is not a Global administrator, she will have to ask Holly Dickson to make this change. Select **Close** in the **Reset password** pane. 

32. If a survey request window appears, select **Cancel**.

33. You now want to change Pradeep Gupta's password. In the **Active users** list, select the **key (Reset a password)** icon that appears to the right of **Pradeep Gupta**. 

34. In the **Reset password** window that appears for Pradeep, verify the **Automatically create a password** check box displays a check mark; if it doesn't, then select this box now so that the system automatically generates a password for Pradeep.  <br/>

	This is just a temporary password because Lynne wants to force Pradeep to change it the next time he logs in. Therefore, verify the **Require this user to change their password when they first sign in** check box displays a check mark; if the box is clear, then select it so that it displays a check mark.
	
35. Select the **Reset password** button.

36. On the **Password has been reset** window, you should receive a message indicating that you successfully reset the password for Pradeep. Select **Close**.

37. Management has recently discovered that Alex Wilber's username may have been compromised. As a result, Lynne has been asked to block Alex's account so that no one can sign in with his username until management is able to determine the extent of the issue. In the **Active users** list, select the check box to the left of **Alex Wilber's** name (do NOT select Alex’s name itself).  <br/>

	**Important:** Since you are going to run a global command rather than a command associated with Alex's account, you only want Alex's account selected in the list of active users. If any other user account is selected, you must unselect that user account before proceeding. Scroll through the list of active users and verify that no other user account is selected. If an account other than Alex is selected, select the account's check box to clear it. **Only Alex Wilber's account should be selected.**

38. In the menu bar at the top of the page, select the **ellipsis icon (...)** to display a drop-down menu of additional actions. In the menu that appears, select **Edit sign-in status**.

39. In the **Block sign-in** pane that appears, verify Alex's email address appears below the **Block sign-in** heading. Select the **Block this user from signing in** check box, and then select **Save changes.** 

40. The **Block sign-in** window should display a message indicating that Alex is now blocked from signing in (and no one can sign in with Alex's username in the event that his username was actually compromised). In addition, Alex will automatically be signed out of Microsoft services within 60 minutes. Select the **X** in the top corner of the pane to close it. 

41. Lynne has just been informed that **Nestor Wilke's** username has also been potentially compromised. Repeat steps 37 through 40 to block Nestor from signing in (and to block anyone else from using his username to sign in). <br/>

	When you tried to block Nestor's sign in, you should have received an error message indicating **Changes could not be saved**. The reason that you received this error is that Nestor is a Global Administrator, and Lynne is not. Only a Global Administrator can block another Global Admin from being able to sign in. Lynne will need to ask Holly Dickson to make this change. <br/>

	Close the **Block sign-in** pane.

42. You previously blocked Alex Wilber from being able to sign in. To verify whether he is blocked, you will attempt to sign in as Alex. Log out of Microsoft 365 by selecting the user icon for **Lynne Robbins** (the circle with Lynne's picture in the top corner), and in the **Lynne Robbins** window that appears, select **Sign out.** 

43. As a best practice, close all your browser tabs except for the **Sign out** tab once you have been signed out. On the **Sign out** tab, navigate to **https://portal.office.com**. 

44. In the **Pick an account** window, select **Use another account**. In the **Sign in** window, enter **AlexW@xxxxxZZZZZZ.onmicrosoft.com** (where xxxxxZZZZZZ is the tenant prefix provided by your lab hosting provider). In the **Enter password** window, enter the **User Password** provided by your lab hosting provider.  <br/>

	The **Pick an account** window should appear, and it should display an error message indicating **Your account has been locked. Contact your support person to unlock it, then try again.** You have just verified that Alex (or someone who has obtained Alex's username and password) cannot log in. <br/>

	**Note:** It can take a few minutes for the account block to fully implement. Until the block has been implemented in the system, Alex may still be able to log on, but none of the Microsoft 365 services will be available to him, and they will not appear in the Microsoft 365 portal. Once an account is unblocked, the services will become available again. <br/>

	If you can sign in as Alex, sign back out and wait a few minutes. This may be a good time to take a short break. Then attempt to sign back in as Alex. By this time, you should hopefully receive the error message that indicates Alex's account has been blocked from signing in. 
	
45. Switch back to **LON-CL1**. 

46. In **LON-CL1**, you should still be logged into **Microsoft 365** as Holly Dickson in your Edge browser. The **Active users** list should be displayed in the **Microsoft 365 admin center** from earlier in this task. 

47. Upon further investigation, Adatum's CTO has determined that Alex Wilber's account has, in fact, not been compromised; therefore, the CTO has asked Holly to remove the block on Alex's user account. Repeat steps 37 through 40 to unblock his account. Note how the **Block sign-in** window from step 39 now displays the **Unblock sign-in** window instead.  <br/>

	In the **Unblock sign-in** window, the **Block this user from signing in** check box is currently selected. Select this check box to clear it, and then select **Save changes**. <br/>
	
	**IMPORTANT:** A warning message is displayed indicating it can take up to 15 minutes before Alex can sign in again. Given the time constraints with the training, you will **NOT** try to verify whether Alex can log back in. If you want, you can try logging in as Alex at a later time if you're on a break or have spare time and you want to test this out. For now, remain on LON-CL1 and simply close the **Unblock sign-in** window.
	
48. On LON-CL1, leave your browser and all tabs open and proceed to the next exercise. 


# Proceed to Lab 2 - Exercise 2