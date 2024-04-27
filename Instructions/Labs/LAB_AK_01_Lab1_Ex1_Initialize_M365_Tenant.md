## WWL Tenants - Terms of Use

If you are being provided with a tenant as a part of an instructor-led training delivery, please note that the tenant is made available for the purpose of supporting the hands-on labs in the instructor-led training. 

Tenants should not be shared or used for purposes outside of hands-on labs. The tenant used in this course is a trial tenant and cannot be used or accessed after the class is over and are not eligible for extension. 

Tenants must not be converted to a paid subscription. Tenants obtained as a part of this course remain the property of Microsoft Corporation and we reserve the right to obtain access and repossess at any time. 

# Learning Path 1 - Lab 1 - Exercise 1 - Initialize your Microsoft 365 Tenant 

Adatum Corporation is a subsidiary of Contoso Electronics. Adatum runs its legacy applications (such as Microsoft Exchange Server 2019) in an on-premises deployment. However, it recently subscribed to Microsoft 365, thereby creating a hybrid deployment in which it must synchronize its on-premises and cloud deployments. 

As Adatum's Microsoft 365 administrator, you have been tasked with deploying Microsoft 365 in Adatum’s hybrid deployment using a virtualized lab environment. In this exercise, you will set up Adatum's Microsoft 365 trial tenant, and your instructor will guide you on how to obtain your Microsoft 365 credentials in your lab-hosted environment. You will use these credentials throughout the remaining labs in this course. 

In your lab environment, your lab hosting provider has already obtained a Microsoft 365 trial tenant for you. Your lab provider has also created two admin accounts that you will use in your VM lab environment: 

- A local administrator account for Adatum's on-premises environment (Adatum\Administrator).
- A default tenant admin account in Microsoft 365 (the display name for this user account is MOD Administrator). 

You will log into the Client 1 PC (LON-CL1) using the local Adatum\Administrator account. When you access Microsoft 365 for the first time, you will initially log in using the Microsoft 365 tenant admin account (MOD Administrator). You will then update Adatum's Microsoft 365 organizational profile, and you'll prepare your tenant for Microsoft Azure Active Directory and for later labs using Information Rights Management, audit alerts, Microsoft Graph PowerShell, and sensitivity labels.

**Important:** Microsoft Security has recently employed a new security hack in the trial tenants that are used in its training courses. This feature requires that all trial tenants used by Microsoft World-Wide Learning employ Multifactor Authentication (MFA) each time a user signs into Microsoft 365. Microsoft World-Wide Learning can NOT turn off this security requirement in its training labs. In addition, we can't use Conditional Access to turn MFA on or off for selected groups of users. MFA will be turned on for everyone and can never be turned off. Any time you sign in to Microsoft 365 in this trial tenant as one of the fictitious users, you must sign in with the user's account and password AND with a second form of authentication (you will use phone verification for the labs in this course).


### Task 1 - Obtain Your Microsoft 365 Credentials

Once you launch the lab, you'll be able to access the free Microsoft 365 trial tenant provided by your lab hosting provider in the Microsoft Virtual Lab environment. Within this tenant, your lab hosting provider has created a Microsoft 365 user account for a default tenant administrator named MOD Administrator. Your lab hosting provider has assigned this user account a unique username and password, and the account has been assigned the Microsoft 365 Global administrator role. You must retrieve this username and password so that you can sign into Microsoft 365 within the Microsoft Virtual Lab environment. You will also be assigned a tenant name and tenant prefix. You will also use this information in various tasks throughout the labs for this course.

Because this course can be offered by learning partners using any one of several authorized lab hosting providers, the actual steps involved to retrieve the UPN name and tenant ID associated with your tenant may vary by lab hosting provider. Therefore, your instructor will provide you with the necessary instructions on how to retrieve this information for your course. <br/>

You should write down the following information (provided by your instructor) for later use:

- **Tenant prefix.** This tenant prefix is for the Microsoft 365 user accounts that you will use to sign into Microsoft 365 throughout the labs in this course. The domain for each Microsoft 365 user account is in the format of {user alias}@xxxxxZZZZZZ.onmicrosoft.com, where xxxxxZZZZZZ is the tenant prefix. It consists of two parts - your lab hoster's prefix (xxxxx; some hosters use a generic prefix such as M365x, while others use their company initials or some other designation) and the tenant ID (ZZZZZZ; usually a 6 digit number). Record this xxxxxZZZZZZ tenant prefix value for later use. When any of the lab steps direct you to sign into Microsoft 365 as one of the user accounts (such as the MOD Administrator), you must enter the xxxxxZZZZZZ value that you obtained here as the tenant prefix portion of your .onmicrosoft.com domain.

- **Tenant password.** This is the password provided by your lab hosting provider for the tenant admin account. **Note:** You will use this password not only for the tenant admin account, but for each of the predefined user accounts that are used throughout the labs.

- **Custom Domain name.** Your lab hosting provider has created a custom domain name for Adatum. You will use this domain when adding a custom domain into Microsoft 365 in a later lab exercise. The domain name is in the format **xxxUPNxxx.xxxCustomDomainxxx.xxx.** You must replace **xxxUPNxxx** with the UPN number provided by your lab hosting provider, and you must replace **xxxCustomDomainxxx.xxx** with the lab hosting provider's domain name. For example, let's assume your lab hosting provider is Fabrikam Inc. If the UPN number it assigns to your tenant is AMPVU3a and its custom domain name is fabrikam.us, then the domain name for your new custom domain would be AMPVU3a.fabrikam.us. Your instructor will provide you with your lab hosting provider's UPN number and custom domain name.  


### Task 2- Set up Adatum's Organization Profile

Throughout the labs in this course, you will role-play by taking on the persona of Holly Dickson, Adatum’s Microsoft 365 Administrator. In your role as Holly, you have been tasked with setting up the company’s profile for its Microsoft 365 trial tenant. In this task, you will configure the required options for Adatum’s tenant. Since Holly has yet to create a personal Microsoft 365 user account for herself (you will do this in the next lab exercise), Holly will initially sign into Microsoft 365 using the default Microsoft 365 tenant admin account and password that was created by your lab hosting provider. This account is the MOD Administrator account, whose alias is "admin". The username for this account is admin@xxxxxZZZZZZ.onmicrosoft.com (where xxxxxZZZZZZ is the tenant prefix assigned by your lab hosting provider); the display name for this account will be MOD Administrator.

1. When you open your lab hosting provider's Virtual Machine environment, you need to begin with the Client 1 VM (LON-CL1). If your VM environment opens with one of the other machines (such as LON-DC1), then switch to **LON-CL1** now.

2. Log into **LON-CL1** as the local **Administrator** account that was created by your lab hosting provider with the password **Pa55w.rd**. 

3. On the taskbar at the bottom of your screen, select the **Microsoft Edge** icon. If necessary, maximize your browser window when it opens.

4. In your Edge browser, go to the **Microsoft 365 Home** page by entering the following URL in the address bar: **https://portal.office.com** 

5. In the **Sign in** dialog box, enter the **Administrative Username** provided by your lab hosting provider (this is the MOD Administrator account) for your Microsoft 365 trial tenant. The username should be in the form of **admin@xxxxxZZZZZZ.onmicrosoft.com**, where xxxxxZZZZZZ is the tenant prefix assigned by your lab hosting provider. Select **Next**. <br/>

	**Note:** Your lab hosting provider may provide the ability to select a **Type text** (or equivalent) button next to resource data such as usernames, passwords, PowerShell commands, and other data that must be entered throughout the course of these labs. Other lab hosting providers may provide an alternative method, such as the ability to copy and paste in this information. Take advantage of this functionality to save yourself from having to manually enter this information. 

6. In the **Enter password** dialog box, enter the unique **Administrative Password** provided by your lab hosting provider and then select **Sign in**.

7. As previously noted, Microsoft Security has recently employed a new security hack in the trial tenants that are used in its training courses. This feature requires that all trial tenants used by Microsoft World-Wide Learning employ Multifactor Authentication (MFA) each time a user signs into Microsoft 365. Microsoft World-Wide Learning can NOT turn off this security requirement in its training labs. <br/>

	Because MFA is required for all user sign-ins using this trial tenant, a **More information required** window appears. Select **Next**.

8. On the **Microsoft Authenticator** page that appears, you can download this mobile app or use a different method for MFA verification. For the purposes of this lab, we recommend you use your mobile phone so that you do not have to take time installing the Microsoft Authenticator app that you may not use again after this training class. Select the **I want to set up a different method** option at the bottom of the page (**Important:** Do NOT confuse this link with the **I want to use a different authenticator app** that appears above it). 

9. On the **Choose a different method** dialog box that appears, select the drop-down arrow in the **Which method would you like to use?** field, select **Phone**, and then select **Confirm**. 

10. In the **Phone** window that appears, under **What phone number would you like to use?** field, select your country or region, and then in the field next to it, enter your phone number (in the format **nnn-nnn-nnnn**). Verify the **Receive a code** option is selected and then select **Next**.

11. Retrieve the verification code from the text message that Microsoft Security sent to your phone.

12. In the **Phone** window, enter the 6-digit verification code in the code field and then select **Next**. When the **Phone** window displays a message indicating your phone was registered successfully, select **Next**.

13. On the **Success!** page, select **Done**.

14. If a **Stay signed in?** dialog box appears, select the **Don’t show this again** check box and then select **Yes.** 

15. If a **Welcome to Microsoft 365** dialog box appears in the middle of the screen, there's no option to close it. Instead, to the right of the window, select the forward arrow icon (**>**) two times and then select the check mark icon to advance through the slides in this messaging window. 

16. If a **Find more apps** dialog box or a **Create with Microsoft 365** dialog box appears, select the **X** in the upper right-hand corner of the boxes to close them. 

17. The **Welcome to Microsoft 365** page appears in your Edge browser in the **Home | Microsoft 365** tab. This is the MOD Administrator's Microsoft 365 home page. <br/>

	Notice that either an icon or a circle with "MA" (the initials for MOD Administrator) appears in the top-right corner of the screen. Some trial tenants show an icon; others show the "MA" initials in a circle; it all depends on whether your lab hosting provider added an icon to the MOD Administrator's account. The icon or initials represents the **MOD Administrator** account, which is the tenant administrator account created by your lab hosting provider that you just signed in as. If any of the existing Microsoft 365 user accounts that were created by your lab hosting provider have a picture associated with their account, the user's picture is displayed rather than the user's initials when you sign into Microsoft 365 as that user. However, when a user such as the MOD Administrator has no picture assigned to it, either the user's initials are displayed in place of the picture, or an icon is displayed if one was assigned to the account by your lab hosting provider. <br/>

	On the **Welcome to Microsoft 365** page, in the list of application icons that appear in the left-hand pane, select **Admin**; this opens the **Microsoft 365 admin center** in a new browser tab. 

18. In the **Microsoft 365 admin center**, select **Show all** in the left-hand navigation pane and then select **Settings**. In the **Settings** group, select **Org settings**. 

19. On the **Org settings** page, the **Services** tab is displayed by default. Select the **Organization profile** tab.

20. In the **Organization profile** tab, select **Organization information** from the list of profile data.

21. In the **Organization information** pane that appears, enter the following information: <br/>

    - Name: **Adatum Corporation** (Note: Adatum Corporation is a subsidiary of Contoso Inc. The Microsoft trial tenant that your lab hosting provider obtained for this lab may have been originally assigned to Contoso. If **Contoso** (or any other value) appears as the organization name, then change it to **Adatum Corporation**.)

    - Street Address: **555 Main Street**

    - City: **Redmond**

    - State or province: **Washington**

    - ZIP or postal code: **98052**

    - Phone: do not change

    - Technical contact: do not change

    - Preferred language: **English**

22. Select **Save**.

23. At the top of the **Organization information** pane, note the message indicating the changes have been saved. Select the **X** in the upper right-hand corner to close the pane.

24. Back on the **Organization profile** tab, in the list of organization profile data, select **Release preferences**.  <br/>

    **Note:** One of the benefits of Microsoft 365 is its ability to have the latest features and updates automatically applied to your environment. This process can reduce maintenance costs and overhead for an organization and allow early-adopter users to test new features. By setting up your **Release preferences**, you can control how and when your Microsoft 365 tenant receives these updates. <br/>

25. In the **Release preferences** pane that appears, the **Targeted release for select users** option enables you to create a control group of users who will preview updates so that you can prepare the updates for your entire organization. The **Targeted release for everyone** option is more commonly used in development environments, where you can get updates early for your entire organization. In non-development environments, such as Adatum, targeted release to a select group of users is a more typical preference as it enables an organization to control when it wants to make updates available to everyone once they've been reviewed by the control group. <br/>

	Select the **Targeted release for select users** option and then select **Save**.

26. In the **Release preferences** pane, below the list of release options, select the **Select users** option.

27. In the **Choose users for targeted release** pane that appears, select inside the **Who should receive targeted releases?** field. This displays the list of active users (these are the Microsoft 365 user accounts created for your trial tenant by your lab hosting provider). In this list, select each of the following users. <br/>

    **Note:** You must select each user, one at a time. After selecting a user, you must select inside the **Who should receive targeted releases?** field again to re-display the list so that you can select the next user. 

	- **Alex Wilber**
	- **Joni Sherman**
	- **Lynne Robbins**
	- **MOD Administrator** <br/>

    **Note:** Alex, Joni, and Lynne are part of Holly's Microsoft 365 pilot team. Their accounts will be used throughout the labs for this course.
    
28. Select **Save**.

29. At the top of the **Release preferences** pane, note the message indicating the 4 users were added to the targeted release. Select the **X** in the upper right-hand corner to close the pane. 

30. Remain logged into **LON-CL1** with Microsoft Edge open to the **Microsoft 365 admin center** for the next task.

### Task 3- Create a custom theme for Adatum's pilot project team

In the prior task, you learned that when someone is signed into Microsoft 365, the system will either display their photograph (if one is supplied), or their initials if no photograph is provided. Holly Dickson, Adatum's Microsoft 365 Administrator, is not satisfied with just seeing a picture or initials of the signed-in user. She wants to create a custom theme for the members of her pilot project team so that it also displays the signed-in user's name. At the end of the pilot project, if the pilot project team members prefer this design, she will configure this same option in the default theme so that it applies to all users. 

Custom themes must be associated with one or more Microsoft 365 groups. Therefore, to implement this change, Holly must first create a Microsoft 365 group for the members of the pilot project team. She can then create a custom theme associated with this group that enables the setting to display the signed-in user's name. In this task, you will create a Microsoft 365 group for the members of Adatum's Microsoft 365 pilot project team. You will then create a custom theme that displays the signed-in user's name, and you will assign the pilot project team to this theme. You will also review other options that can be configured with custom themes, and you can make any color changes that you wish.

**Note:** At the end of this task, you will attempt to save the custom theme that you created. There is a known platform issue in the Microsoft 365 admin center where sometimes it saves the custom theme just fine, and other times it returns a message that says "Sorry, we couldn't save your theme. Please try again later." If you receive this message, there's nothing you can do but move on. This won't affect any future labs, other than it won't display the user's name next to their user icon or initials on the heading line. You are still asked to do this task to gain the experience of creating a theme such as this, even though it may not get saved.

1. You should still be logged into LON-CL1 as the local **adatum\administrator** account, and in your Edge browser, you should still be logged into Microsoft 365 as the **MOD Administrator**. 

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

	**Note:** As previously mentioned at the start of this task, there's a known platform issue in the Microsoft 365 admin center where sometimes it saves a new custom theme, and other times it returns a message that says "Sorry, we couldn't save your theme. Please try again later." If you receive this message, it won't affect any future labs, other than it won't display the user's name next to their user icon or initials on the heading line. We still asked you to do this task even though you may receive this message in order to gain the experience of creating a theme such as this, even though it may not get saved. So if you get this error, skip the next step, which tests the custom theme. If your theme doesn't get saved, you won't be able to test it. However, you can still perform the remaining steps following the next step in order to learn about the Default theme. Whether or not your custom theme was saved, close the **M365 pilot project theme** pane.

23. If your theme did not get saved, then skip to the next step. However, if your theme was saved, then select the **Refresh** icon at the top of the screen, to the left of the address bar. Once the screen refreshes, note how the **MOD Administrator** name appears to the left of either the circle with the MA initials or the icon selected for this account by your lab-hosting provider. When members of the Microsoft 365 pilot project team sign in to Microsoft 365, this custom theme will display their username in the same location. If your lab-hosting provider assigned either an icon or the user's picture to the user's account profile, then their name will appear to the left of that. If neither an icon or picture was assigned to the user's account, then the system displays their user name to the left of their initials, which appear in a circle. 

24. In the list of organization profile data, select **Custom themes**.

25. In the **Customize Microsoft 365 for your organization** pane that appears, notice how it displays the **Default theme** and the **M365 pilot project theme** (if the theme was saved in the previous step). Select the **Default theme**. 

26. On the **Default theme** pane, notice how the **Show the user's display name** option is not selected for the default theme. If Holly later decides to make the **Show the user's display name** option a permanent feature, she will select this option in the **Default theme** pane so that it applies to all Adatum users, and she will delete the **M365 Pilot project theme**. <br/>

	Close the **Default theme** pane.

27. Remain logged into **LON-CL1** with Microsoft Edge open to the **Microsoft 365 admin center** for the next task.


### ‎Task 4 - Enable Information Rights Management for SharePoint Online 

In this task, you will turn on Information Rights Management (IRM) for SharePoint Online. 

**Important:** While you will validate IRM for Exchange and SharePoint in Lab 7, you must enable IRM for SharePoint Online now because it can take up to 60 minutes or more for IRM to show up in SharePoint Online. By the time you get to the validation exercise in Lab 7, IRM should have finished its internal configuration and you won’t have to wait for it to be present in SharePoint Online. Keep this time issue in mind if you plan to enable IRM in your real-world deployment.

1. You should still be logged into LON-CL1 as the local **adatum\administrator** account, and in your Edge browser, you should still be logged into Microsoft 365 as the **MOD Administrator**. 

2. In the **Microsoft 365 admin center**, under the **Admin centers** group, select **SharePoint**. This will open the **SharePoint admin center** in a new tab.

3. In the **Welcome to your new home page** window that appears, select **Take the tour**.

4. In the **SharePoint admin center**, select **Settings** in the navigation pane. 

5. At the bottom of the **Settings** page is a sentence that says **Can’t find the setting you’re looking for? Go to the classic settings page.** In this sentence, select the hyperlinked text that says: **classic settings page**.

6. On the classic **Settings** page, scroll down to the **Information Rights Management (IRM)** section. In the options to the right of this section, select the **Use the IRM service specified in your configuration** option, and then select the **Refresh IRM Settings** button.

7. The system should return you back to the top of the **Settings** page. Scroll to the bottom of the page and select the **OK** button. 

8. Once the changes have been saved, you will again be returned to the top of the **Settings** page. In your browser, close the current tab that you're on (the **https://xxxxxZZZZZZ-admin.sharepoint.com** tab). This will return you to the **Settings** page in the **SharePoint admin center**.

9. Close this **SharePoint admin center** tab in your Edge browser. Leave the other tabs open in your browser for the next task.


### Task 5 – Install Microsoft Graph PowerShell 

Microsoft Graph PowerShell is required to perform several configuration tasks when installing Microsoft 365. Because future lab exercises will perform several of these tasks using Windows PowerShell, you should begin by installing the Microsoft Graph PowerShell module. This module allows you to perform many of the Microsoft 365 user and organization administration tasks through PowerShell. It’s great for bulk tasks such as password resets, password policies, license management and reporting, and so on.  

1. On LON-CL1, you should still be logged in as the local **adatum\administrator** account. To install Microsoft Graph PowerShell, you must open an elevated instance of **Windows PowerShell**. Type **power** in the Search box that appears in the bottom left corner of the taskbar. In the list of search results, right-click on **Windows PowerShell** (do not select Windows PowerShell ISE) and select **Run as administrator** in the drop-down menu that appears. 

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

		Set-ExecutionPolicy unrestricted

	‎If you are prompted to verify that you want to change the execution policy, enter **A** to select **[A] Yes to All.** 

7. Leave your PowerShell window open as you will use it in the next task.

### Task 6 – Turn on Audit Logging to enable Alert Policies

In Lab 6, you will create Alert Policies using the Microsoft Defender portal. However, before you can implement alerts, an administrator must first turn on Audit Logging for the organization. Since it can take an hour or so for audit logging to become fully enabled once you turn it on, you will turn it on in this lab so that it's fully enabled by the time you get to Lab 6.

1. You should still be logged into LON-CL1 as the local **adatum\administrator** account, and you should still have Windows PowerShell open from the prior task. If you closed PowerShell at the end of the prior task, then open it again using the **Run as administrator** option. 

2. In your PowerShell window, run the following command to install the Exchange Online Management module, which contains the cmdlet to turn on audit logging:

		Install-Module ExchangeOnlineManagement

3. You will be prompted to confirm whether you want to install the module from an untrusted repository (PSGallery). Enter **A** to select **[A] Yes to All** and then press Enter.

4. A command prompt will appear once the Exchange Online Management module has been installed. Run the following command to connect to the module:

		Connect-ExchangeOnline

5. A **Sign in** window will appear requesting your credentials. Enter the MOD Administrator account provided by your lab hosting provider (**admin@xxxxxZZZZZZ.onmicrosoft.com**; where xxxxxZZZZZZ is the tenant prefix provided by your lab hosting provider) and then select **Next**. On the **Enter password** window, enter the **Administrative Password** provided by your lab hosting provider and then select **Sign in**.

6. Because MFA is required for all user sign-ins using this trial tenant, and since the MOD Administrator is already signed in to this Microsoft 365 tenant on LON-CL1, a **Verify your identity** window appears. Select the **Text +X XXX-XXX-XXnn** field (where **nn** are the final two digits of your phone number). This is the same phone number that you used to previously sign-in as the MOD Administrator on LON-CL1. Microsoft will send a verification code to your phone.

7. Retrieve the verification code from the text message that is sent to your phone.

8. In the **Enter code** window, enter the 6-digit verification code in the code field and then select **Verify**.
   
9. In the **Protect your account** window that appears, select **Skip for now (3 times left)**.

10. At the command prompt, run the following command to turn on audit logging:

		Set-AdminAuditLogConfig -UnifiedAuditLogIngestionEnabled $true

    **Note:** A warning message will be displayed indicating the admin audit log configuration change that you requested could take up to 60 minutes to take effect throughout the system. This is why you're enabling this feature now rather than waiting for the Alert Policy labs later in this course. 

11. At the command prompt, run the following command to confirm that audit logging is enabled:

		AdminAuditLogConfig 

12. In the list of properties that's displayed, verify the **UnifiedAuditLogIngestionEnabled** property is set to  **True**.

13. Do **NOT** close your PowerShell window. Leave the Windows PowerShell window open but minimize it for now. Remain logged into LON-CL1 and keep your Edge browser open.


### Task 7 - Run a PowerShell script to create and publish a sensitivity label

In this task, you will run a lab setup script that creates a sensitivity label and sensitivity label policy for future use in this lab series. Running this script is necessary to support the lab that you will perform on the last day of class to create a sensitivity label and label policy. The sensitivity label lab basically consists of two parts: 1) Creating a label and publishing a label policy, and 2) Testing the published label policy. The problem with the sensitivity label lab is that once you publish a label policy, it takes 24 hours for the published label policy to propagate through Microsoft 365. As such, you won't be able to test the label and policy that you create and publish on the last day of class. 

To address this timing issue, you will run a PowerShell script in this task that creates a sensitivity label and publishes it to a label policy. By the time you get to the last day of class, this label policy will have propagated through the system, and you'll be able to test it. 

**Note:** In the sensitivity label lab that you perform on the last day of class, you will create another label and label policy - just ones with different names. Their settings will be exactly the same as the ones created by this script. The sensitivity label lab will give you the experience of creating a label and publishing a label policy using the Microsoft 365 UI. However, when you perform the tasks to test the sensitivity label and label policy, you won't test the ones that you created and published in the UI, since they won't be available for testing until the next day. Instead, you will test the label and label policy that were created and published using the script that you run in this task. 

1. On **LON-CL1**, select the **File Explorer** icon from the Windows taskbar. Maximize the File Explorer window.

2. In **File Explorer**, under **This PC**, expand **Local Disk (C:)** and then navigate to the following folder location: **C:\Users\Administrator.ADATUM\Documents\Lab Setup**.

3. In the **Lab Setup** subfolder, you should find a file named **LabSetup.bat**. <br/>

    Right-click on the **LabSetup.bat** file and then select **Run as administrator**. Doing so will start the lab setup process.

    **Note:** If a **Windows protected your PC** pop-up warning is displayed, select **More info** and then select **Run anyway** at the bottom of the pop-up to continue. A **Lab setup** window will appear on the screen.

4. It may take up to 1 minute before a **Pick an account** window appears (if the **Lab setup** window appears on top of the **Pick and account** window, then select inside the **Pick an account** to access it). Select the administrator account provided by your lab hosting provider (**admin@xxxxxZZZZZZ.onmicrosoft.com**; where xxxxxZZZZZZ is the tenant prefix provided by your lab hosting provider). On the **Enter password** window, enter the **Administrative Password** provided by your lab hosting provider and then select **Sign in**.

5. Because MFA is required for all user sign-ins using this trial tenant, and since the MOD Administrator is already signed in to this Microsoft 365 tenant on LON-CL1, a **Verify your identity** window appears. Select the **Text +X XXX-XXX-XXnn** field (where **nn** are the final two digits of your phone number). This is the same phone number that you used to previously sign-in as the MOD Administrator on LON-CL1. Microsoft will send a verification code to your phone.

6. Retrieve the verification code from the text message that is sent to your phone.

7. In the **Enter code** window, enter the 6-digit verification code in the code field and then select **Verify**.
   
8. A **Pick an account** window will appear. On this window, select **MOD Administrator** from the list of available accounts. If prompted, enter the **Administrative Password** provided by your lab hosting provider and then select **Sign in**.

    **Important:** The **Lab Setup** process has a time-out of 5 minutes. If you fail to type in your credentials within this 5 minute time frame, a pop-up message displaying **Lab Setup Failed. EXITING...** will appear. Select **Ok**, close the Microsoft Sign-on window, and repeat steps 3-8.

9. Once the lab setup process has completed, a pop-up message displaying **Lab Setup Completed. EXITING...** will appear. Select **Ok** and proceed.

    **Note:** It may take up to 5 minutes for the lab setup process to complete.

Congratulations! You have completed all the steps to initialize your lab tenant. You are now ready to perform the remaining lab exercises.

# Proceed to Lab 1 - Exercise 2 
