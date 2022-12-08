# Learning Path 1 - Lab 1 - Exercise 1 - Set up your Microsoft 365 Tenant

In the labs for this course, you are taking on the role of Holly Dickson, Adatum Corporation's Enterprise Administrator. Adatum Corporation is a subsidiary of Contoso Electronics. Adatum does NOT have legacy, on-premises servers; therefore, you will be implementing Microsoft 365 in a cloud-only deployment. You have deployed Microsoft 365 in a virtualized lab environment, and you have been tasked with completing a pilot project that tests the security, compliance, and device management features in Microsoft 365 as they relate to Adatum's business requirements.

You have just started the pilot project; therefore, in this first lab you will set up a personalized Microsoft 365 user account for Holly that will be used throughout all the labs in this course. This first exercise also requires that you perform several setup tasks that will initialize your trial tenant for the remaining labs in this course. You must configure your trial tenant, create a personalized Global Admin user account in Microsoft 365 for Holly, configure several test users and groups that will be used throughout the remaining labs, and turn on Information Rights Management (IRM) in SharePoint Online as well as audit logging.

### Task 1 - Obtain Your Office 365 Credentials

Once you launch the lab, a free trial tenant will be automatically created for you to access Microsoft 365 in the Microsoft Virtual Lab environment. Within this tenant, your lab hosting provider will create a Microsoft 365 user account for a default tenant administrator named MOD Administrator. Your lab hosting provider will assign this user account a unique username and password, and the account will be assigned the Microsoft 365 Global administrator role. You must retrieve this username and password so that you can sign into Microsoft 365 within the Microsoft Virtual Lab environment.

1. Because this course can be offered by learning partners using any one of several authorized lab hosting providers, the actual steps involved to retrieve the tenant prefix, tenant ID, and tenant password associated with your trial tenant may vary by lab hosting provider. Therefore, your instructor will provide you with the necessary instructions on how to retrieve this information for your course. The information that you should write down for later use includes:

	- **Tenant prefix.** This tenant prefix is for the Microsoft 365 user accounts that you will use to sign into Microsoft 365 throughout the labs in this course. The domain for each Microsoft 365 user account is in the format of {user alias}@xxxxxZZZZZZ.onmicrosoft.com, where xxxxxZZZZZZ is the tenant prefix. It consists of two parts - your lab hoster's prefix (xxxxx; some hosters use a generic prefix such as M365x, while others use their company initials or some other designation) and the tenant ID (ZZZZZZ; usually a 6 digit number). Record this xxxxxZZZZZZ tenant prefix value for later use. When any of the lab steps direct you to sign into Microsoft 365 as one of the user accounts (such as the MOD Administrator), you must enter the xxxxxZZZZZZ value that you obtained here as the tenant prefix portion of your .onmicrosoft.com domain.

	- **Tenant password.** This is the password provided by your lab hosting provider for the tenant admin account.


### Task 2: Set up the Organization Profile

In your role as Holly Dickson, Adatum's Enterprise Administrator, you have been tasked with setting up the company's profile for its Microsoft 365 trial tenant. In this task, you will configure the required options for Adatum's tenant. Since Holly has yet to create a personal Microsoft 365 user account (you will do this in Task 3), Holly will initially sign into Microsoft 365 as the default Microsoft 365 MOD Administrator account using the Tenant email address and password that was assigned by your lab hosting provider.

1. When you open your lab hosting provider's Virtual Machine environment, you need to begin with the Client 1 VM (LON-CL1). If your VM environment opens with one of the other machines, then switch to the LON-CL1 VM now.

2. On **LON-CL1**, you must select **Ctrl+Alt+Delete** to log in (your instructor will guide you on how to find this option in your VM environment). Log into LON-CL1 as the local **Admin** (or Administrator) account with the password **Pa55w.rd**. 

3. If you receive a **Networks** warning message asking if you want this PC to be discoverable by other PCs and devices on this network, select **Yes**.

4. On the taskbar at the bottom of the page, select the **Microsoft Edge** icon. Maximize your browser window when it opens.

5. In your browser go to the **Microsoft Office Home** page by entering the following URL in the address bar: **https://portal.office.com/** 

6. In the **Sign in** dialog box, copy and paste in the **Tenant Username** provided by your lab hosting provider (**admin@xxxxxZZZZZZ.onmicrosoft.com**, where xxxxxZZZZZZ is the tenant prefix assigned by your lab hosting provider) and then select **Next**.

7. In the **Enter password** dialog box, copy and paste in the **Tenant Password** provided by your lab hosting provider and then select **Sign in**.

8. On the **Stay signed in?** dialog box, select the **Don’t show this again** check box and then select **Yes.** 

9. If a **Welcome to your new Office, MOD** window appears, there's no option to close it. Instead, to the right of the window, select the right arrow icon (**>**) two times and then select the check mark icon to advance through the slides in this messaging window. 

10. If a **Find more apps** window appears, select the **X** in the upper right-hand corner of the window to close it.

11. In the top right corner of the screen, notice the initials **MA** that appear in a circle. These are the initials of the **MOD Administrator** account, which is the tenant admin account created by your lab hosting provider. If any of the other Microsoft 365 user accounts that were created by your lab hosting provider have a picture associated with the account, that picture will be displayed when the user logs in. When a user such as the MOD Administrator has no picture assigned to it, the user's initials are displayed in place of the picture.  <br/>

	On the **Microsoft Office Home** page, note the column of application icons that appears on the far-left side of the screen. This is the list of applications the user has access to based on their assigned roles. The MOD Administrator account has been assigned the Global Administrator role by the lab hosting provider. This role provides access to all the Microsoft 365 services, including the Microsoft 365 admin center. <br/>

	In this column of app icons, select **Admin**; this opens the **Microsoft 365 admin center** in a new browser tab. 
	
12. In the **Microsoft 365 admin center**, in the left-hand navigation pane, select **Show all** and then select **Settings**. In the Settings group, select **Org settings**. 

13. On the **Org settings** page, the **Services** tab is displayed by default. Select the **Organization profile** tab.

14. In the **Organization profile** tab, select **Organization information** from the list of profile data.

15. In the **Organization information** pane that appears, enter the following information:

    - Name: **Adatum Corporation** (Note: Contoso is originally displayed as the organization name; this was explained in the Introduction section at the start of this lab. In this step you will change it to Adatum Corporation.)

    - Street Address: **555 Main Street**

    - City: **Redmond**

    - State or province: **Washington**

    - ZIP or postal code: **98052**

    - Phone: do not change

    - Technical contact: do not change

    - Preferred language: **English**

16. Select **Save**.

17. At the top of the **Organization information** pane, note the message indicating the changes have been saved. Select the **X** in the upper right-hand corner to close the pane.

18. Back on the **Org settings** page, the **Organization profile** tab is still displayed. In the list of organization profile data, select **Release preferences**.

19. In the **Release preferences** pane that appears, select the **Targeted release for select users** option and then select **Save**.<br/>

    **Note:** One of the benefits of Microsoft 365 is its ability to have the latest features and updates automatically applied to your environment. This process can reduce maintenance costs and overhead for an organization and allow early-adopter users to test new features. By setting up your **Release preferences**, you can control how and when your Microsoft 365 tenant receives these updates. <br/>

    **Note:** The **Targeted release for select users** option enables you to create a control group of users who will preview updates so that you can prepare the updates for your entire organization. The **Targeted release for everyone** option is more commonly used in development environments, where you can get updates early for your entire organization. In non-development environments, such as Adatum, targeted release to a select group of users is the more typical preference as it enables an organization to control when it wants to make updates available to everyone once they've been reviewed by the control group.

20. In the **Release preferences** pane, below the list of release options, select the **Select users** option.

21. In the **Choose users for targeted release** pane that appears, select inside the **Who should receive targeted releases?** field. This displays the list of active users (these are the ten Microsoft 365 user accounts created for your tenant by your lab hosting provider). In this list, select each of the following users (Note: You must select each user, one at a time. After selecting a user, you must select inside the field again to re-display the list so that you can select the next user): 

	- **Alex Wilber**
	- **Joni Sherman**
	- **Lynne Robbins**
	- **MOD Administrator**
	- **Patti Fernandez** <br/>

    **Note:** Alex, Joni, Lynne, and Patti are part of Holly's pilot team. Their accounts will be used throughout the labs for this course.
    
22. Select **Save**.

23. At the top of the **Release preferences** pane, note the message indicating the 5 users were added to the targeted release. Select the **X** in the upper right-hand corner to close the pane. 

24. In the list of organization profile data, select **Custom themes**.

25. In the **Customize theme** pane, you can customize the default theme users see when signed into Microsoft 365, and you can add additional, custom themes. Select the **+Add theme** option.

26. In the **Default theme** pane, the **General** tab is displayed by default. Select the **Show the user's display name** check box. 
 
27. Take some time and review the **Logos** and **Colors** tabs. Note the various theme and branding options that are available for you to update. For the purpose of this lab, you can change any of the options or leave the default values as is. For example, in your real-world environment, you can add the logo of your company and set the background image as the default for all your users. For the purpose of this lab, you can change the colors for your navigation pane, text color, icon color, and accent color. Go ahead and explore the different options for your tenant and make any changes that you wish. <br/>

	**Tip:** Some color patterns aesthetically distract users. If you do change any of the colors, it's recommended that you avoid using high contrasting colors together, such as neon colors and high-resolution colors like bright pink and white.

28. Select **Save** when you are done and then close the **Custom themes** pane.

29. Remain logged into LON-DC1 with Microsoft Edge open to the **Microsoft 365 admin center** for the next task.



### Task 3 - Create a Microsoft 365 Global Admin account

Holly Dickson is Adatum’s Enterprise Administrator. Since a Microsoft 365 user account has not been set up for her, she initially signed into Microsoft 365 as the MOD Administrator account (the default Global admin) in the previous lab (you did this when you began your role as Holly and signed in using the tenant admin account). In this task, you will continue in your role as the MOD Administrator, during which you will create a Microsoft 365 user account for Holly. You will also assign the Microsoft 365 Global Administrator role to Holly's account. This role will give Holly the permissions necessary to perform most administrative functions within Microsoft 365. Following this task, you will perform all remaining labs using Holly's persona. 

**Important:** As a best practice in your real-world deployment, you should always write down the first Global admin account’s credentials (in this lab, it's the MOD Administrator account, whose username is admin@xxxxxZZZZZZ.onmicrosoft.com, where xxxxxZZZZZZ is the tenant prefix assigned by your lab hosting provider) and store it away for security reasons. **This account should be a non-personalized identity** that owns the highest privileges possible in a tenant. Because this account is not personalized, it should **not** be MFA activated. And because the username and password for this first Global admin account are typically shared among several users, this account is a perfect target for attacks. As such, it's always recommended that organizations create personalized service admin accounts and keep as few personal Global admins as possible. For those personal Global admins that you do create in your real-world deployment, they should each be mapped to a single identity (such as Holly Dickson), and they should each have Multi-Factor Authentication (MFA) enforced. That being said, you will not turn on MFA for Holly's account because time is limited in this training course and we do not want to take up lab time by forcing you to log in using a second authentication method every time Holly logs in.

**Note:** While your lab hosting provider has created a custom domain for Adatum (xxxUPNxxx.xxxCustomDomainxxx.xxx), they did not finish the setup process for the domain. In a later lab exercise, you will finish provisioning the new domain. That being said, your lab hosting provider should have left your Microsoft 365 tenant's **xxxxxZZZZZ.onmicrosoft.com** domain as the default domain for Adatum. In this task, you will begin by verifying whether this domain is listed as the default domain. If your lab hosting provider set the new custom domain as the default, you will change it to the xxxxxZZZZZZ.onmicrosoft.com domain. Why is this important? Because when you add a new user account (such as the one for Holly Dickson that you will add in this task) or email addresses for new groups (later in this exercise), you want the xxxxxZZZZZZ.onmicrosoft.com domain to show as the default domain for the user and groups.

1. On the LON-CL1 VM, the **Microsoft 365 admin center** should still be open in your Microsoft Edge browser from the prior lab, and you should be signed into Microsoft 365 as the **MOD Administrator**. 

2. You will begin by verifying which domain is listed as the default domain for Adatum. In the **Microsoft 365 admin center**, under the **Settings** group in the left-hand navigation pane, select **Domains**.

3. On the **Domains** page, you should see the **xxxxxZZZZZZ.onmicrosoft.com (Default)** domain created by your lab hosting provider. The status for this domain should be **Healthy**, which indicates that domain setup is complete. <br/>
	
	**Note:** If a domain titled **xxxUPNxxx.xxxCustomDomainxxx.xxx** appears, do not worry. This is a custom domain that was created by your lab hosting provider. However, it's not needed for any of the labs in this course. That being said, if this domain does exist and it displays **(Default)** next to the domain name, then you must set the **xxxxxZZZZZZ.onmicrosoft.com** domain as the default domain. To do so, select the check box to the left of the **xxxxxZZZZZZ.onmicrosoft.com** domain and then select **Set as default** on the menu bar. In the **Set this domain as default?** dialog box that appears, select **Set as default**. In the list of domains, the **xxxxxZZZZZZ.onmicrosoft.com** domain should now display **(Default)** next to the domain name. 

4. You will now create a Microsoft 365 user account for Holly Dickson. In the **Microsoft 365 admin center**, in the left-hand navigation pane, select **Users** and then select **Active users**. 

5. In the **Active users** window, you will see the list of existing user accounts that were created for you by your lab hosting provider. In this task, you are taking on the role of the MOD Administrator, and as such, you must create a user account for Holly Dickson, who is Adatum's new Enterprise Administrator. In doing so, you will assign Holly the Microsoft 365 role of Global Administrator, which gives Holly global access to most management features and data across Microsoft's online services. This is the same role the lab hosting provider assigned to the non-personalized MOD Administrator account. 

	In the **Active Users** window, select the **Add a user** option that appears on the menu bar above the list of active users. This initiates the **Add a user** wizard.

6. In the **Set up the basics** page, enter the following information:

	- First name: **Holly**

	- Last name: **Dickson** 

	- Display name: When you tab into this field, **Holly Dickson** will appear.

	- Username: **Holly** <br/>
	
		‎**IMPORTANT:** To the right of the **Username** field is the domain field. It should be prefilled with the **xxxxxZZZZZZ.onmicrosoft.com** cloud domain (where xxxxxZZZZZZ is the tenant prefix provided by your lab hosting provider). However, if your lab hosting provider set the custom **xxxUPNxxx.xxxCustomDomainxxx.xxx** domain as Adatum's default domain and you did not change the default domain to the **xxxxxZZZZZZ.onmicrosoft.com** domain earlier in this task, then the custom domain will appear here instead. If that happens, select the drop-down arrow in this domain field and select **xxxxxZZZZZZ.onmicrosoft.com**. You should also perform steps 2-3 in this task to change **xxxxxZZZZZZ.onmicrosoft.com** to the default domain as this is needed in the next task. <br/>
	
		After configuring this field, Holly’s username should appear as:<br/>

		**Holly@xxxxxZZZZZZ.onmicrosoft.com**  
	
	- Clear (uncheck) the **Automatically create a password** check box, which will display a **Password** field. By unchecking this **Automatically create a password** check box, you must manually assign Holly a password at this point in time.

	- In the new **Password** field that appears, enter **User.pw1**. Passwords must include at least one upper case character, one lower case character, one number, and one special character. Select the eye (**Show password**) icon at the end of the field to display the password that you just entered. Verify you correctly spelled the password (**User.pw1**).

	- Clear (uncheck) the **Require this user to change their password when they first sign in** check box. <br/>

7. Select **Next**. If a **Save password** window appears at the top of the page, select **Never**.

8. In the **Assign product licenses** window, enter the following information:

	- Select location: **United States**

	- Licenses: The **Assign user a product license** option should be selected by default; under this option, select **Office 365 E5** 

9. Select **Next.** 

10. In the **Optional settings** window, select **Roles (User: no administration access)**.

11. Under this section, the **User (no admin center access)** option is selected by default. Select the **Admin center access** option instead. By doing so, the most commonly used Microsoft 365 administrator roles are enabled below this option. <br/>

	Select the **Global administrator** check box. <br/>

	**Warning:** Note the warning message that's displayed after selecting the **Global Administrator** role for Holly. Your lab hosting provider created several test user accounts in your Microsoft 365 tenant for this training. In doing so, four of those accounts were assigned the Global Administrator role, which, as a best practice, is the maximum number of recommended accounts for this role. When you just assigned this role to Holly, Adatum now has five Global Administrators, which exceeds this best practice threshold and triggered this warning message. You will continue in this lab having Holly assigned as a Global Administrator. Just keep in mind this best practice when you work in your real-world Microsoft 365 deployment.

12. Select the **Show all by category** option that appears after the list of the most commonly used roles. This displays the complete list of administrator roles sorted by category. 

13. Scroll through the list of roles. In the **Global** category, the **Global Administrator** role should be selected (if you didn't select it in the prior step, then select it now). Continue scrolling down to the **Security & Compliance** category, and then select the **Attack Simulation Administrator** and **Security Administrator** roles. <br/>

	**Note:** The Global Administrator role provides access to most of the standard Microsoft 365 administrative functionality; however, it does not provide access to everything. Therefore, even Global Admins require some additional roles to provide specific permissions that are not included in the Global Admin role.

14. Select **Next**.

15. On the **Review and finish** window, review your selections. If anything needs to be changed, select the appropriate **Edit** link and make the necessary changes. Otherwise, if everything is correct, select **Finish adding**. 

16. On the **Holly Dickson added to active users** page, select **Close**

16. Remain logged into LON-CL1 with the Microsoft 365 admin center open in your browser for the next task.

### Task 4 - Assign RBAC to a Microsoft 365 user account in the Microsoft 365 Defender portal

In the prior task, you successfully created a user account for Holly Dickson, and you assigned her the Global administrator role. This role will provide Holly with the majority of privileges needed to manage Adatum's Microsoft 365 tenant. It's important to note that not every Microsoft 365 role is available for selection when adding a user account in the Microsoft 365 admin center. For example, to assign permissions for archiving, auditing, and retention policies, you must do so in the Exchange admin center. 

Another example is the Organization Management role group, which can only be assigned in the Microsoft 365 Defender portal. This role group provides permissions to manage Exchange objects and their properties in the Exchange organization. Members of this role group can also delegate role groups and management roles in the organization. Holly will require this role group to complete the remaining lab exercises in this course. In this task, you will assign Holly this role group, and you will also assign it to Lynne Robbins so that Lynne can view alerts in the Microsoft 365 Defender portal in a later lab.

1. In your **Edge** browser, you should still have the **Microsoft 365 admin center** open from the prior task. 

2. In the **Microsoft 365 admin center**, in the left-hand navigation pane under **Admin centers**, select **Security**. This opens the Microsoft 365 Defender portal in a new tab.

3. In the **Microsoft 365 Defender** portal, scroll down towards the bottom of the left-hand navigation pane and select **Permissions**.
    
4. In the **Permissions** page, the roles are displayed under two groups - **Azure AD** and **Email & collaboration roles**. Under the **Email & collaboration roles** group, select **Roles**.
    
5. On the **Permissions > Permissions** page, select the check box to the left of the **Organization Management** role.

6. On the **Organization Management** pane that appears, note all the individual roles that are assigned to this role group. Scroll down to the bottom of the pane, and in the **Members** section, select **Edit**.

7. On the **Editing Choose members** page, a message is displayed indicating **The list is currently empty.** Select **Choose members** that appears below this message.

8. On the **Choose members** page, select the **+Add** button.

9. On the **Choose members** list, select **Holly Dickson** and **Lynne Robbins** and then select the **Add** button. 

10. On the **Choose members** page, select the **Done** button.

11. On the **Editing Choose members** page, select the **Save** button.

12. On the **Organization Management** pane, note that Holly and Lynne appear in the **Members** section. Select **Close**.

13. Remain logged into LON-CL1 with the Microsoft 365 admin center open in your browser for the next task.

### Task 5 – Set up Microsoft 365 User Accounts and Groups

After completing the previous task, you should still be signed into the **Microsoft 365 admin center** as the **MOD Administrator** account. In this task, you will begin implementing Adatum’s Microsoft 365 pilot project as Holly Dickson, Adatum’s new Enterprise Administrator. Therefore, you will begin this task by logging out of Microsoft 365 as the MOD Administrator and you will log back in as Holly. When you log in as Holly for the first time, you will be required to change her password, since you configured this option in the earlier task when you created Holly's user account. 

In the prior task, you noticed that your Microsoft 365 trial tenant came equipped with a list of active users. As Holly Dickson, Adatum's Enterprise Admin, you have selected the following users to help with your pilot project: Alex Wilber, Joni Sherman, Lynne Robbins, and Patti Fernandez. 

Each user is a key member of your pilot project team. While their user accounts are already present in Microsoft 365, you need to configure their passwords so that they can more easily sign into Microsoft 365 when needed in the upcoming lab exercises. You will assign **User.pw1** as their user password, just as you did when you created Holly's account. You also need to add a Microsoft 365 group that will be used in a later lab exercise. 

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

14. In the **Microsoft 365 admin center**, in the left-hand navigation pane, select **Teams & groups**, and then under it, select **Active teams & groups**.

15. In the **Active teams & groups** window, select the **Add a group** option that appears on the menu bar. This initiates the **Add a group** wizard.

16. In the **Choose a group type** page, select **Microsoft 365 (recommended)** and then select **Next**.

17. In the **Set up the basics** page, enter **Sales Group** in the **Name** field. You must select the **Description** field to enable the **Next** button. Leave the **Description** field blank and select **Next**. 

18. In the **Assign owners** page, select **+Assign owners**. 

19. In the **Assign owners** page that appears, select **Joni Sherman** in the list of active users that's displayed, and then select **Add(1)**. Select **Next**.

20. In the **Add members** page, select **Next**.

	**Note:** You can add members to a group at the time you create the group (at this step in the process), as well as after you create a group. For the purpose of this lab, you will add members after you've created the group in a later step. This way you can see the two methods of adding group members. So for now, select **Next** to skip through this step and not add members at this time.

21. In the **Edit settings** page, enter **salesgroup** in the **Group email address** field (Note: the domain should be the xxxxxZZZZZZ.onmicrosoft.com domain, which you should have verified in a prior task is the default domain for Adatum). <br/>

	In the **Privacy** field, verify it's set to **Public** (if not, then set it now), and leave the **Create a team for this group** check box selected. Select **Next**.

22. In the **Review and finish adding group** window, review your selections. If anything needs to be corrected, select the corresponding **Edit** option. When everything is correct, select **Create group**.

23. Once the group is created, select the **Close** button in the **Sales group group created** window.

24. This will return you to the **Active teams & groups** window. It may take a few minutes for the Sales Group to appear, so you may need to select the **Refresh** option on the menu bar once or twice. Note that there are four tabs on this page, one for each group type (Microsoft 365, Distribution list, Mail-enabled security, and Security). The **Microsoft 365** tab is displayed by default, which is the group type assigned to the Sales Group. So the Sales Group should be displayed in this tab.

25. Once the **Sales Group** appears in the list of **Microsoft 365** groups, select the **Sales Group** name.

26. In the **Sales Group** pane that appears, the **General** tab is displayed by default. Select the **Members** tab.

	**Note:** While you could have added members to this group at the time you created it, you will instead add members after the group has been created. This will give you experience in how to add members to an existing group. 

27. In the **Members** tab, three sub-tabs (Owners, Members, and Site visitors) are displayed in the left-hand column. The **Owners** sub-tab is displayed by default. In the **Owners** sub-tab, Joni Sherman should appear as the only group owner. Select the **Members** sub-tab.

28. In the **Members** sub-tab, select the **Add members** button. 

29. In the **Add members to Sales group** pane, select in the **Search by name or email address** field. This displays the list of active users. <br/>

	In the list of users, select **Alex Wilber**. Note that you have to select back into the field to display the list of users. Select **Joni Sherman**, select back in the field, and then select **Lynne Robbins**. Once all three users are selected, select the **ADD(3)** button at the bottom of the pane.

30. Once the three new members have been saved in the group, select the **X** in the upper right-hand corner of the **Sales group** pane to close it.  <br/>

	**Note:** You will not add Patti Fernandez to this group. Patti's key role in the pilot project is to test the Privileged Identity Management functionality in the next lab exercise. 

31. Leave the **Microsoft 365 admin center** tab open in your browser and proceed to the next task.


### ‎Task 6 - Enable IRM for SharePoint Online 

In this task, you will turn on Information Rights Management (IRM) for SharePoint Online. 

**Important:** While you will validate IRM for Exchange and SharePoint in Lab 4, you must enable IRM for SharePoint Online now because it can take up to 60 minutes or more for IRM to show up in SharePoint Online. By the time you get to the validation exercise in Lab 4, IRM should have finished its internal configuration and you won’t have to wait for it to be present in SharePoint Online. Keep this time issue in mind if you plan to enable IRM in your real-world deployment.

1. You should still be logged into LON-CL1 as the local **Admin** account, and in your Edge browser, you should still be logged into Microsoft 365 as **Holly Dickson**. 

2. In the **Microsoft 365 admin center**, select **Show all** (if necessary) in the left-hand navigation pane to see all the navigation options. Under **Admin centers,** select **SharePoint**. This will open the SharePoint admin center in a new tab.

3. In the **Welcome to your new home page** window, select **Take the tour**.

4. In the **SharePoint admin center**, in the left-hand navigation pane, select **Settings**. 

5. At the bottom of the **Settings** page is a sentence that says **Can’t find the setting you’re looking for? Go to the classic settings page.** In this sentence, select the hyperlinked text: **classic settings page**.

6. On the classic **Settings** page, scroll down to the **Information Rights Management (IRM)** section. In the options to the right of this section, select the **Use the IRM service specified in your configuration** option, and then select the **Refresh IRM Settings** button.

7. This will return you to the top of the **Settings** page. Scroll down to the **Information Rights Management (IRM)** section and verify the **Use the IRM service specified in your configuration** option is selected and a **We successfully refreshed your settings** message appears below the **Refresh IRM Settings** button. Continue scrolling to the bottom of the page and select the **OK** button. 

8. This will return you to the top of the **Settings** page. In your browser, close the current tab that you're on (the **https://xxxxxZZZZZZ-admin.sharepoint.com** tab). This will return you to the **Settings** page in the **SharePoint admin center**.

9. Do **NOT** close the **SharePoint admin center** tab in your Edge browser. Leave this tab and your browser open for the next task.


### Task 7 – Turn on Audit Logging to enable Alert Policies

In Lab 3, you will create Alert Policies using the Microsoft 365 Defender portal. However, before you can implement alerts, an admin must first turn on Audit Logging for the organization. Since it can take a couple of hours for audit logging to become fully enabled once you turn it on, you will turn it on in this lab so that it's fully enabled by the time you get to Lab 3.

**Important:** If you see an error message that says "Fail to opt in, please refresh", Audit Logging is being enabled in the background and the message can safely be ignored.

1. You should still be logged into LON-CL1 as the local **Admin** account, and in your Edge browser, you should still be logged into Microsoft 365 as **Holly Dickson**. 

2. Select the **Microsoft 365 admin center** tab in your Edge browser. 

3. In the **Microsoft 365 admin center**, under the **Admin centers** section, select **Security**. This will open the **Microsoft 365 Defender** portal.

4. In the **Microsoft 365 Defender** portal, scroll down towards the bottom of the left-hand navigation pane and select **Audit**.

5. In the **Audit** window, wait a minute or so to see if a banner appears towards the top of the page that says: **Start recording user and admin activity**. If this banner appears, then auditing is not turned on for your organization. This banner is your prompt to turn on audit logging. <br/>

	Select this banner now to turn on audit logging. 

6. In the **Audit** window, the banner will disappear once audit logging is turned on. In a later lab, you will return to this page to view audited activities that you completed during your lab work.  
 
7. Leave the Client 1 VM and all the tabs in your Edge browser open and proceed to the next lab. 


### Task 8 – Prepare Users for Content Searches

In Module 8, you will perform a Content Search lab that requires that Joni Sherman and Holly Dickson be members of the eDiscovery Manager role. In this exercise, you will add Joni and Holly to this role. The reason you are doing this now is that it can sometimes take up to an hour or more for newly assigned permissions to successfully propagate through the system. If you waited and assigned Holly and Joni to this role group at the time you performed the Content Search lab in Module 8, you would receive error messages involving parameter fields because their permissions would not have finished propagating. By adding them to this role group now, enough time will elapse for the propagation to complete by the time you get to the Module 8 lab. Keep this time issue in mind when you assign roles for content search in your real-world deployment.

1. You should still be logged into LON-CL1 as the local **Admin** account, and in your Edge browser, you should still be logged into Microsoft 365 as **Holly Dickson**. 

2. In your **Microsoft Edge** browser, you should still have the **Microsoft 365 Defender** portal open from the prior task. Scroll towards the bottom of the left-hand navigation pane and select **Permissions**.

3. In the **Permissions** page, under the **Email & collaboration roles (1)** section, select **Roles**.

4. On the **Permissions > Permissions** page, you want to select the **eDiscovery Manager** role group. <br/>

	**HINT:** To quickly locate a specific role, you can enter the first few characters of the role name in the **Search** field on the menu bar and then select the **Search** icon. For example, let's assume you were looking for the **Mailflow administrator** role. You could enter **mail** in the **Search** field on the menu bar and then select the **Search** icon. This would display the roles starting with **mail**. While the eDiscovery Manager role appears at the top of the list, this technique is good to know if you want a quick way to locate a specific role without having to scroll through the entire list. <br/>

	Select the **eDiscovery Manager** role group.

5. In the **eDiscovery Manager** pane that appears, note the list of roles assigned to this role group. Scroll down to the **eDiscovery Manager** section and select **Edit**.

6. The **Editing Choose eDiscovery Manager** wizard opens. The list of users who are assigned this role should be empty. Select **Choose eDiscovery Manager**.

7. In the **Choose eDiscovery Manager** pane, select the **+Add** button.

8. In the list of users that’s displayed, select **Holly Dickson** and **Joni Sherman**, select **Add**, and then select **Done**. 

9. In the **Editing Choose eDiscovery Manager** pane, select **Save**.

10. In the **eDiscovery Manager** pane, select **Close**.

11. Leave your browser open and do not close any of the tabs.

# Proceed to Lab 1 - Exercise 2
