## WWL Tenants - Terms of Use

If you are being provided with a tenant as a part of an instructor-led training delivery, please note that the tenant is made available for the purpose of supporting the hands-on labs in the instructor-led training. 

Tenants should not be shared or used for purposes outside of hands-on labs. The tenant used in this course is a trial tenant and cannot be used or accessed after the class is over and are not eligible for extension. 

Tenants must not be converted to a paid subscription. Tenants obtained as a part of this course remain the property of Microsoft Corporation and we reserve the right to obtain access and repossess at any time. 

# Learning Path 1 - Lab 1 - Exercise 1 - Initialize your Microsoft 365 Tenant 

Adatum Corporation is a subsidiary of Contoso Electronics. Adatum runs its legacy applications (such as Microsoft Exchange Server 2019) in an on-premises deployment. However, it recently subscribed to Microsoft 365, thereby creating a hybrid deployment in which it must synchronize its on-premises and cloud deployments. 

As Adatum's Microsoft 365 administrator, you have been tasked with deploying Microsoft 365 in Adatum’s hybrid deployment using a virtualized lab environment. In this exercise, you will set up Adatum's Microsoft 365 trial tenant, and your instructor will guide you on how to obtain your Microsoft 365 credentials in your lab-hosted environment. You will use these credentials throughout the remaining labs in this course. 

In your lab environment, your lab hosting provider has already obtained a Microsoft 365 trial tenant for you. Your lab provider has also created two admin accounts that you will use in your VM lab environment: 

- An AD DS administrator account for Adatum's on-premises environment (Adatum\Administrator).
- A default tenant admin account in Microsoft 365 (the display name for this user account is MOD Administrator). 

You will log into the Client 1 PC (LON-CL1) using the Adatum\Administrator account. When you access Microsoft 365 for the first time, you will initially log in using the Microsoft 365 tenant admin account (MOD Administrator). You will then update Adatum's Microsoft 365 organizational profile, and you'll prepare your tenant for Microsoft Entra ID, and for later labs using Information Rights Management, audit alerts, and Microsoft Graph PowerShell.


### Task 1- Set up Adatum's Organization Profile

Throughout the labs in this course, you will role-play by taking on the persona of Holly Dickson, Adatum’s Microsoft 365 Administrator. In your role as Holly, you have been tasked with setting up the company’s profile for its Microsoft 365 trial tenant. In this task, you will configure the required options for Adatum’s tenant. Since Holly has yet to create a personal Microsoft 365 user account for herself (you will do this in the next lab exercise), Holly will initially sign into Microsoft 365 using the default Microsoft 365 tenant admin account and password that was created by your lab hosting provider. This account is the MOD Administrator account, whose alias is "admin". The username for this account is admin@xxxxxZZZZZZ.onmicrosoft.com (where xxxxxZZZZZZ is the tenant prefix assigned by your lab hosting provider); the display name for this account will be MOD Administrator.

1. Your lab-hosting provider will be providing two passwords that are used with the fictitious user accounts in your Microsoft 365 trial tenant. The MOD Administrator account, which is the default tenant administrator, has been assigned the **Administrative Password**. All other users - even those assigned an admin role - have been assigned the **User Password**. <br>

	For security purposes, Microsoft has configured your trial tenant so that all predefined users must change their password at their next sign-in. <br>
 
 	**Important:** Some lab hosting providers may provide the following new password fields that will be used to store the new passwords that you will assign to users the first time they sign in: <br>

	- **New Administrative Password** - This is the new password that you will assign to the MOD administrator and Holly Dickson
 	- **New User Password** - This is the new password that you will assign to all other users.

 	If these two new password fields appear in your VM, then enter a new password for each. These new password values will be stored in the VM and displayed in the lab instructions. <br>
 
	Other lab hosting providers may not provide these new password fields. For those environments, you must manually write down the new password that you plan to assign to users who sign in. <br>

	When designing your new passwords, keep in mind Microsoft's password guidelines: <br>

	- Minimum length of 8 character, with at least:
	   - 1 uppercase character
	   - 1 lowercase character
	   - 1 special character
	The passwords will not be validated against Microsoft's requirements until you change the old password at the user's next sign-in.

3. When you open your lab hosting provider's Virtual Machine environment, you need to begin with the Client 1 VM (LON-CL1). If your VM environment opens with one of the other machines (such as LON-DC1), then switch to **LON-CL1** now.

4. Log into **LON-CL1** as the **Administrator** account that was created by your lab hosting provider with the password **Pa55w.rd**. 

5. On the taskbar at the bottom of your screen, select the **Microsoft Edge** icon. If necessary, maximize your browser window when it opens.

6. In your Edge browser, go to the **Microsoft 365 Home** page by entering the following URL in the address bar: **https://portal.office.com** 

7. In the **Sign in** dialog box, enter the **Administrative Username** provided by your lab hosting provider (this is the MOD Administrator account) for your Microsoft 365 trial tenant. The username should be in the form of **admin@xxxxxZZZZZZ.onmicrosoft.com**, where xxxxxZZZZZZ is the tenant prefix assigned by your lab hosting provider. Select **Next**. <br/>

	**Note:** In the lab instructions that appear in your VM lab environment, your lab hosting provider may provide the ability to select a **Type text** (or equivalent) button next to resource data such as usernames, passwords, PowerShell commands, and other data that must be entered throughout the course of these labs. Other lab hosting providers may provide an alternative method, such as the ability to copy and paste in this information. Take advantage of this functionality to save yourself from having to manually enter this information. 

8. In the **Enter password** dialog box, enter the predefined **Administrative Password** provided by your lab hosting provider and then select **Sign in**. 

9. Your lab hosting provider may or may not have configured the MOD Admin account to require a new password at sign-in. If they did, then an **Update your password** dialog box will appear. If this occurs, enter the **Administrative Password** provided by your lab hosting provider in the **Current password** field, and then enter the New Administrative Password in the **New password** and **Confirm password** fields.

10. If a **Stay signed in?** dialog box appears, select the **Don’t show this again** check box and then select **Yes.** 

11. If a **Welcome to Microsoft 365** dialog box appears in the middle of the screen, there's no option to close it. Instead, to the right of the window, select the forward arrow icon (**>**) two times and then select the check mark icon to advance through the slides in this messaging window. 

12. If a **Find more apps** dialog box or a **Create with Microsoft 365** dialog box appears, select the **X** in the top corner of the boxes to close them. Similarly, if a Sign in to Microsoft Edge dialog box appears, select the **No thanks** button.

13. The **Welcome to Microsoft 365** page appears in your Edge browser in the **Home | Microsoft 365** tab. This is the MOD Administrator's Microsoft 365 home page. <br/>

	Notice that either an icon or a circle with "MA" (the initials for MOD Administrator) appears in the top-right corner of the screen. Some trial tenants show an icon; others show the "MA" initials in a circle; it all depends on whether your lab hosting provider added an icon to the MOD Administrator's account. The icon or initials represents the **MOD Administrator** account, which is the tenant administrator account created by your lab hosting provider that you just signed in as. If any of the existing Microsoft 365 user accounts that were created by your lab hosting provider have a picture associated with their account, the user's picture is displayed rather than the user's initials when you sign into Microsoft 365 as that user. However, when a user such as the MOD Administrator has no picture assigned to it, either the user's initials are displayed in place of the picture, or an icon is displayed if one was assigned to the account by your lab hosting provider. <br/>

	On the **Welcome to Microsoft 365** page, in the list of application icons that appear in the navigation pane, select **Admin**; this opens the **Microsoft 365 admin center** in a new browser tab. 

14. In the **Microsoft 365 admin center**, select **Show all** in the navigation pane and then select **Settings**. In the **Settings** group, select **Org settings**. 

15. On the **Org settings** page, the **Services** tab is displayed by default. Select the **Organization profile** tab.

16. In the **Organization profile** tab, select **Organization information** from the list of profile data.

17. In the **Organization information** pane that appears, enter the following information: <br/>

    - Name: **Adatum Corporation** (Note: Adatum Corporation is a subsidiary of Contoso Inc. The Microsoft trial tenant that your lab hosting provider obtained for this lab may have been originally assigned to Contoso. If **Contoso** (or any other value) appears as the organization name, then change it to **Adatum Corporation**.)

    - Street Address: **555 Main Street**

    - City: **Redmond**

    - State or province: **Washington**

    - ZIP or postal code: **98052**

    - Phone: do not change

    - Technical contact: do not change

    - Preferred language: **English**

18. Select **Save**.

	**Note:** When you attempt to save your org profile changes, you may receive an error statement that says: "Object reference not set to an instance of an object." This error appears intermittently for no known reason. We are troubleshooting it to try and resolve the issue. In the meantime, if you receive this message, simply continue on with the lab. Not being able to save the org profile changes that you made will not affect any future lab steps.

19. At the top of the **Organization information** pane, note the message indicating the changes have been saved. Select the **X** in the top corner of the pane to close it.

20. Back on the **Organization profile** tab, in the list of organization profile data, select **Release preferences**.  <br/>

    **Note:** One of the benefits of Microsoft 365 is its ability to have the latest features and updates automatically applied to your environment. This process can reduce maintenance costs and overhead for an organization and allow early-adopter users to test new features. By setting up your **Release preferences**, you can control how and when your Microsoft 365 tenant receives these updates. <br/>

21. In the **Release preferences** pane that appears, the **Targeted release for select users** option enables you to create a control group of users who will preview updates so that you can prepare the updates for your entire organization. The **Targeted release for everyone** option is more commonly used in development environments, where you can get updates early for your entire organization. In non-development environments, such as Adatum, targeted release to a select group of users is a more typical preference as it enables an organization to control when it wants to make updates available to everyone once they've been reviewed by the control group. <br/>

	Select the **Targeted release for select users** option and then select **Save**.

22. In the **Release preferences** pane, below the list of release options, select the **Select users** option.

23. In the **Choose users for targeted release** pane that appears, select inside the **Who should receive targeted releases?** field. This displays the list of active users (these are the Microsoft 365 user accounts created for your trial tenant by your lab hosting provider). In this list, select each of the following users. <br/>

    **Note:** You must select each user, one at a time. After selecting a user, you must select inside the **Who should receive targeted releases?** field again to re-display the list so that you can select the next user. 

	- **Alex Wilber**
	- **Joni Sherman**
	- **Lynne Robbins**
	- **MOD Administrator** <br/>

    **Note:** Alex, Joni, and Lynne are part of Holly's Microsoft 365 pilot team. Their accounts will be used throughout the labs for this course.
    
24. Select **Save**.

25. At the top of the **Release preferences** pane, note the message indicating the 4 users were added to the targeted release. Select the **X** in the upper right-hand corner to close the pane. 

26. Remain logged into **LON-CL1** with Microsoft Edge open to the **Microsoft 365 admin center** for the next task.

### Task 2- Create a custom theme for Adatum's pilot project team

In the prior task, you learned that when someone is signed into Microsoft 365, the system will either display their photograph (if one is supplied), or their initials if no photograph is provided. Holly Dickson, Adatum's Microsoft 365 Administrator, is not satisfied with just seeing a picture or initials of the signed-in user. She wants to create a custom theme for the members of her pilot project team so that it also displays the signed-in user's name. At the end of the pilot project, if the pilot project team members prefer this design, she will configure this same option in the default theme so that it applies to all users. 

Custom themes must be associated with one or more Microsoft 365 groups. Therefore, to implement this change, Holly must first create a Microsoft 365 group for the members of the pilot project team. She can then create a custom theme associated with this group that enables the setting to display the signed-in user's name. In this task, you will create a Microsoft 365 group for the members of Adatum's Microsoft 365 pilot project team. You will then create a custom theme that displays the signed-in user's name, and you will assign the pilot project team to this theme. You will also review other options that can be configured with custom themes, and you can make any color changes that you wish.

**Important:** At the end of this task, you will attempt to save the custom theme that you created. There is a known platform issue in the Microsoft 365 admin center where sometimes it saves the custom theme just fine, and other times it returns a message that says "Sorry, we couldn't save your theme. Please try again later." If you receive this message, there's nothing you can do but move on. Trying to save the theme at a later time usually returns the same error. This issue won't affect any future labs, other than it won't display the user's name next to their user icon or initials on the heading line. Despite this known issue, we still want you to perform this task to gain experience in creating a theme, even though it may not get saved in your trial tenant.

1. You should still be logged into LON-CL1 as the **adatum\administrator** account, and in your Edge browser, you should still be logged into Microsoft 365 as the **MOD Administrator**. 

2. In the **Microsoft 365 admin center**, select **Teams & groups** in the navigation pane, and then under it, select **Active teams & groups**. 

3. In the **Active teams and groups** page, there's a tab for viewing each of the group types. The **Teams & Microsoft 365 groups** tab is displayed by default. This tab displays the existing Microsoft 365 groups.  <br/>

    Select the **+Add a Microsoft 365 group** option that appears on the menu bar above the list of Teams and Microsoft 365 groups. This initiates the **Add a Microsoft 365 group** wizard. 

4. In the **Add a Microsoft 365 group** wizard, on the **Set up the basics** page, enter **M365 pilot project** in the **Name** field, and then enter **Members of the Microsoft 365 pilot project team** in the **Description** field (Note: even if you don't enter a description, you must still select into this field to enable the **Next** button). Select **Next**.

5. You will now assign the MOD Administrator as owner of the **M365 pilot project** group. In the **Assign owners** window, select **+Assign owners**.
	
6. In the **Assign owners** pane that appears, select the check box next to **MOD Administrator**, and then select the **Add (1)** button at the bottom of the pane.

7. On the **Assign owners** page, MOD Administrator should appear as owner of the group. Select **Next**.

8. You will now assign members to the M365 pilot project group. In the **Add members** page, select **+Add members**.

9. In the **Add members** pane that appears, select the check boxes next to the following users (in alphabetical order): **Alex Wilber**, **Allan Deyoung**, **Diego Siciliani**, **Isaiah Langer**, **Joni Sherman**, **Lynne Robbins**, **Megan Bowen**, **MOD Administrator**, **Nestor Wilke**, and **Patti Fernandez**. Then select the **Add (10)** button at the bottom of the pane.

10. On the **Add members** page, verify these 10 users are listed as members of the group. If you missed a user, select **+Add members** and then add any of the 10 users that you missed. When all 10 users appear on this page, select **Next**.

11. In the **Edit settings** page, enter the following information: <br/>

	- Enter **m365pilotproject** in the **Group email address** field.
	- In the **Privacy** field, select **Private**.
	- Under the **Add Microsoft Teams to your group** section, verify the **Create a team for this group** check box is selected (select it if it's blank), and then select **Next**.

12. In the **Review and finish adding group** page, review the content that you entered. If anything needs to be fixed, select **Edit** under the specific area that needs adjustment, make any necessary corrections, and then select **Next** to continue back to this page. Once everything is correct, select **Create group**.

13. Once the **M365 pilot project group created** window appears, note the comment at the top of the page that it may take 5 minutes for the new group to appear in the list of Active groups.  </br>

	Select **Close**. This returns you to the **Active teams and groups** page, which should display the **Teams & Microsoft 365 groups** tab. Since the M365 pilot project group was a Microsoft 365 group, it should eventually display on this tab. If necessary, select the **Refresh** option on the menu bar until you see the M365 pilot project group in the list of Teams and Microsoft 365 groups.

14. In the **Microsoft 365 admin center**, select **Settings** in the navigation pane and then select **Org settings**. 

15. On the **Org settings** page, the **Services** tab is displayed by default. Select the **Organization profile** tab.

16. The **Organization profile** tab displays the list of organization profile data. In the list of data, select **Custom themes**.

17. In the **Customize Microsoft 365 for your organization** pane that appears, you can customize the default theme that users see when signed into Microsoft 365, and you can add additional custom themes. You want to create a new custom theme that applies only to the members of the **M365 pilot project** group that you previously created, so select the **+Add theme** option.

18. In the **New group theme** pane that appears, the **General** tab is displayed by default. Enter **M365 pilot project theme** in the **Name** field.

19. Select inside the **Groups** field. In the list of groups that appears, select **M365 pilot project** if it appears in the list of groups. <br/>

	**Note:** If **M365 pilot project** doesn't appear in the list of groups, then enter **M365** in the **Groups** field. A search results box should appear that displays the **M365 pilot project** group. Select **M365 pilot project**. 

20. Select the **Show the user's display name** check box. This is the setting that Holly wants to customize for the M365 pilot project team members. This option displays the signed-in user's name next to their initials in each window heading.
 
21. Select the **Logos** tab and take some time to review its options. Do the same for the **Colors** tab. Note the various theme and branding options that are available for you to update. <br/>

	For the purpose of this lab, you can change any of the options or leave the default values as is. For example, in your real-world environment, you can add the logo of your company and set the background image as the default for all your users. For this lab, feel free to change the colors for your navigation pane, text color, icon color, and accent color. <br/>

	**Go ahead and explore the different options for this theme that will be used by the Microsoft 365 pilot project team members. Make any changes that you wish.** <br/>

	**Tip:** Some color patterns aesthetically distract users. If you do change any of the colors, it's recommended that you avoid using high contrasting colors together, such as neon colors and high-resolution colors like bright pink and white.

22. Select **Save**. 

	**Note:** As previously mentioned at the start of this task, there's a known platform issue in the Microsoft 365 admin center where sometimes it saves a new custom theme, and other times it returns a message that says "Sorry, we couldn't save your theme. Please try again later." If you receive this message, it won't affect any future labs. Since your custom theme didn't get save, the system simply won't display the user's name next to their user icon or initials on the heading line (plus any color changes you may have made won't appear). We still asked you to do this task even though you may receive this message in order to gain the experience of creating a theme such as this. So if you get this error, skip the next step, which tests the custom theme. However, you can still perform the remaining steps following the next step in order to learn about the Default theme. Whether or not your custom theme was saved, close the **M365 pilot project theme** pane.

23. If your custom theme did not get saved, then skip to the next step. However, if your custom theme was saved, then select the **Refresh** icon at the top of the screen, next to the address bar. Once the screen refreshes, note how the **MOD Administrator** name appears next to either the circle with the MA initials or the icon selected for this account by your lab-hosting provider. When members of the Microsoft 365 pilot project team sign in to Microsoft 365, this custom theme will display their username, just as the MOD Administrator name appears here. 

24. In the list of organization profile data, select **Custom themes**.

25. In the **Customize Microsoft 365 for your organization** pane that appears, notice how it displays the **Default theme** and the **M365 pilot project theme** (if the theme was saved in the previous step). Select the **Default theme**. 

26. On the **Default theme** pane, notice how the **Show the user's display name** option is not selected for the default theme. If Holly later decides to make the **Show the user's display name** option a permanent feature, she will select this option in the **Default theme** pane so that it applies to all Adatum users, and she will delete the **M365 Pilot project theme**. <br/>

	**Note:** If you received the "Sorry, we couldn't save your theme. Please try again later." error message when you previously tried to save your custom theme, then select this **Show the user's display name** option on the Default theme, and then select **Save**. We want you to see what happens when this option is selected, even if you couldn't save your custom theme. If you set this option on the Default theme, then select the **Refresh** icon at the top of the screen, to the left of the address bar. Once the screen refreshes, note how the **MOD Administrator** name appears to the left of either the circle with the MA initials or the icon selected for this account by your lab-hosting provider.
 
27. Close the **Default theme** pane.

28. Remain logged into **LON-CL1** with Microsoft Edge open to the **Microsoft 365 admin center** for the next task.


### ‎Task 3 - Enable Information Rights Management for SharePoint Online 

In this task, you will turn on Information Rights Management (IRM) for SharePoint Online. 

**Important:** While you will validate IRM for Exchange and SharePoint in Lab 7, you must enable IRM for SharePoint Online now because it can take up to 60 minutes or more for IRM to show up in SharePoint Online. By the time you get to the validation exercise in Lab 7, IRM should have finished its internal configuration and you won’t have to wait for it to be present in SharePoint Online. Keep this time issue in mind if you plan to enable IRM in your real-world deployment.

1. You should still be logged into LON-CL1 as the **adatum\administrator** account, and in your Edge browser, you should still be logged into Microsoft 365 as the **MOD Administrator**. 

2. In the **Microsoft 365 admin center**, under the **Admin centers** group, select **SharePoint**. This will open the **SharePoint admin center** in a new tab.

3. In the **Welcome to your new home page** window that appears, select **Take the tour**.

4. In the **SharePoint admin center**, select **Settings** in the navigation pane. 

5. At the bottom of the **Settings** page is a sentence that says **Can’t find the setting you’re looking for? Go to the classic settings page.** In this sentence, select the hyperlinked text that says: **classic settings page**.

6. On the classic **Settings** page, scroll down to the **Information Rights Management (IRM)** section. In the options to the right of this section, select the **Use the IRM service specified in your configuration** option, and then select the **Refresh IRM Settings** button.

7. The system should return you back to the top of the **Settings** page. Scroll to the bottom of the page and select the **OK** button. 

8. Once the changes have been saved, you will again be returned to the top of the **Settings** page. In your browser, close the current tab that you're on (the **https://xxxxxZZZZZZ-admin.sharepoint.com** tab). This will return you to the **Settings** page in the **SharePoint admin center**.

9. Close this **SharePoint admin center** tab in your Edge browser. Leave the other tabs open in your browser for the next task.


### Task 4 – Install Microsoft Graph PowerShell 

Microsoft Graph PowerShell is required to perform several configuration tasks when installing Microsoft 365. Because future lab exercises will perform several of these tasks using Windows PowerShell, you should begin by installing the Microsoft Graph PowerShell module. This module allows you to perform many of the Microsoft 365 user and organization administration tasks through PowerShell. It’s great for bulk tasks such as password resets, password policies, license management and reporting, and so on.  

1. On LON-CL1, you should still be logged in as the **adatum\administrator** account. To install Microsoft Graph PowerShell, you must open an elevated instance of **Windows PowerShell**. Right-click the **Windows (Start)** icon in the lower left corner of the taskbar, and then select **Windows PowerShell (Admin)**.

2. Maximize your PowerShell window. In **Windows PowerShell**, type the following command at the command prompt to install the Microsoft Graph PowerShell module from the PowerShell Gallery and then press Enter: <br/>

		Install-Module Microsoft.Graph -Scope CurrentUser

3. You will be prompted to confirm whether you want to install the module from an untrusted repository (PSGallery). Enter **A** to select **[A] Yes to All** and then press Enter.  <br/>

    **Note:** Your response will initiate the installation of all the Microsoft Graph sub-modules. Once all the installation messages for each sub-module have finished displaying, it will still take approximately 5 to 10 additional minutes to complete the Microsoft Graph PowerShell installation. During this time, the cursor will continue to blink below the untrusted repository message. <br/>

	**This may be a good time to take a short break.**

4. A command prompt will appear once Microsoft Graph PowerShell has been installed. You will now display the list of sub-modules that were installed. To do so, run the following command:

		Get-InstalledModule Microsoft.Graph.* | select *name*

5. Verify the list of installed sub-modules includes the following three sub-modules that will be used in later lab exercises: 

	- Microsoft.Graph.Groups
	- Microsoft.Graph.Identity.DirectoryManagement
 	- Microsoft.Graph.Users
  	
    If all three sub-modules appear in the list of installed sub-modules, then proceed to the next step. However, if any of these three sub-modules do not appear in the list, then run the following PowerShell command to manually install the missing sub-module:

		Install-Module -Name <module name> -Scope CurrentUser

    For example, if the Microsoft.Graph.Identity.DirectoryManagement module did not install, then you would run the following command:

		Install-Module -Name Microsoft.Graph.Identity.DirectoryManagement

6. PowerShell's execution policy settings dictate what PowerShell scripts can be run on a Windows system. Setting this policy to **Unrestricted** enables Holly to load all configuration files and run all scripts. At the command prompt, type the following command, and then press Enter:   <br/>

		Set-ExecutionPolicy RemoteSigned

	‎If you are prompted to verify that you want to change the execution policy, enter **A** to select **[A] Yes to All.** 

7. Leave your PowerShell window open as you will use it in the next task.

### Task 5 – Turn on Audit Logging to enable Alert Policies

In Lab 6, you will create Alert Policies using the Microsoft Defender portal. However, before you can implement alerts, an administrator must first turn on Audit Logging for the organization. Since it can take an hour or so for audit logging to become fully enabled once you turn it on, you will turn it on in this lab so that it's fully enabled by the time you get to Lab 6.

1. You should still be logged into LON-CL1 as the **adatum\administrator** account, and you should still have Windows PowerShell open from the prior task. If you closed PowerShell at the end of the prior task, then open it again using the **Run as administrator** option. 

2. In your PowerShell window, run the following command to install the Exchange Online Management module, which contains the cmdlet to turn on audit logging:

		Install-Module ExchangeOnlineManagement

3. You will be prompted to confirm whether you want to install the module from an untrusted repository (PSGallery). Enter **A** to select **[A] Yes to All** and then press Enter.

4. A command prompt will appear once the Exchange Online Management module has been installed. Run the following command to connect to the module:

		Connect-ExchangeOnline

5. A **Sign in** window will appear requesting your credentials. Enter the MOD Administrator account provided by your lab hosting provider (**admin@xxxxxZZZZZZ.onmicrosoft.com**; where xxxxxZZZZZZ is the tenant prefix provided by your lab hosting provider) and then select **Next**. On the **Enter password** window, enter the **Administrative Password** provided by your lab hosting provider and then select **Sign in**. If required, complete the MFA sign-in process. 

6. At the command prompt, run the following command to turn on audit logging:

		Set-AdminAuditLogConfig -UnifiedAuditLogIngestionEnabled $true

    **Note:** A warning message will be displayed indicating the admin audit log configuration change that you requested could take up to 60 minutes to take effect throughout the system. This is why you're enabling this feature now rather than waiting for the Alert Policy labs later in this course. 

7. At the command prompt, run the following command to confirm that audit logging is enabled:

		AdminAuditLogConfig 

8. In the list of properties that's displayed, verify the **UnifiedAuditLogIngestionEnabled** property is set to  **True**.

9. Do **NOT** close your PowerShell window. Leave the Windows PowerShell window open but minimize it for now. Remain logged into LON-CL1 and keep your Edge browser open.


Congratulations! You have completed all the steps to initialize your lab tenant. You are now ready to perform the remaining lab exercises.

# Proceed to Lab 1 - Exercise 2 
