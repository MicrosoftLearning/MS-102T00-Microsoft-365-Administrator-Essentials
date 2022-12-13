# Learning Path 1 - Lab 1 - Exercise 1 - Initialize your Microsoft 365 Tenant 

Adatum Corporation is a subsidiary of Contoso Electronics. Adatum runs its legacy applications (such as Microsoft Exchange Server 2019) in an on-premises deployment. However, it recently subscribed to Microsoft 365, thereby creating a hybrid deployment in which it must synchronize its on-premises and cloud deployments. 

As Adatum's Microsoft 365 administrator, you have been tasked with deploying Microsoft 365 in Adatum’s hybrid deployment using a virtualized lab environment. In this exercise, you will set up Adatum's Microsoft 365 trial tenant, and your instructor will guide you on how to obtain your Microsoft 365 credentials in your lab-hosted environment. You will use these credentials throughout the remaining labs in this course. 

In your lab environment, your lab hosting provider has already obtained a Microsoft 365 trial tenant for you. Your lab provider has also created two admin accounts that you will use in your VM lab environment: 

- A local administrator account for Adatum's on-premises environment (Adatum\Administrator).
- A default tenant admin account in Microsoft 365 (the display name for this user account is MOD Administrator). 

You will log into the Client 1 PC (LON-CL1) using the local Adatum\Administrator account. When you access Microsoft 365 for the first time, you will initially log in using the Microsoft 365 tenant admin account (MOD Administrator). You will then update Adatum's Microsoft 365 organizational profile, and you'll prepare your tenant for Microsoft Azure Active Directory and for a future lab using Microsoft Teams.


### Task 1 - Obtain Your Microsoft 365 Credentials

Once you launch the lab, you'll be able to access the free Microsoft 365 trial tenant provided by your lab hosting provider in the Microsoft Virtual Lab environment. Within this tenant, your lab hosting provider has created a Microsoft 365 user account for a default tenant administrator named MOD Administrator. Your lab hosting provider has assigned this user account a unique username and password, and the account has been assigned the Microsoft 365 Global administrator role. You must retrieve this username and password so that you can sign into Microsoft 365 within the Microsoft Virtual Lab environment. You will also be assigned a unique network IP address and UPN name for your Microsoft 365 blob. You will also use this UPN name in various tasks throughout the labs for this course.

Because this course can be offered by learning partners using any one of several authorized lab hosting providers, the actual steps involved to retrieve the UPN name, network IP address, and tenant ID associated with your tenant may vary by lab hosting provider. Therefore, your instructor will provide you with the necessary instructions on how to retrieve this information for your course. <br/>

You should write down the following information (provided by your instructor) for later use:

- **Tenant prefix.** This tenant prefix is for the Microsoft 365 user accounts that you will use to sign into Microsoft 365 throughout the labs in this course. The domain for each Microsoft 365 user account is in the format of {user alias}@xxxxxZZZZZZ.onmicrosoft.com, where xxxxxZZZZZZ is the tenant prefix. It consists of two parts - your lab hoster's prefix (xxxxx; some hosters use a generic prefix such as M365x, while others use their company initials or some other designation) and the tenant ID (ZZZZZZ; usually a 6 digit number). Record this xxxxxZZZZZZ tenant prefix value for later use. When any of the lab steps direct you to sign into Microsoft 365 as one of the user accounts (such as the MOD Administrator), you must enter the xxxxxZZZZZZ value that you obtained here as the tenant prefix portion of your .onmicrosoft.com domain.

- **Tenant password.** This is the password provided by your lab hosting provider for the tenant admin account.

- **Custom Domain name.** Your lab hosting provider has created a custom domain name for Adatum. You will use this domain when adding a custom domain into Microsoft 365 in a later lab exercise. The domain name is in the format **xxxUPNxxx.xxxCustomDomainxxx.xxx.** You must replace **xxxUPNxxx** with the UPN number provided by your lab hosting provider, and you must replace **xxxCustomDomainxxx.xxx** with the lab hosting provider's domain name. For example, let's assume your lab hosting provider is Fabrikam Inc. If the UPN number it assigns to your tenant is AMPVU3a and its custom domain name is fabrikam.us, then the domain name for your new custom domain would be AMPVU3a.fabrikam.us. Your instructor will provide you with your lab hosting provider's UPN number and custom domain name.  

- **Network IP address.** Write down the **IP Address** value (this is the IP Address of your parent domain; for example, 64.64.206.13).

### Task 2- Set up Adatum's Organization Profile

Throughout the labs in this course, you will role-play by taking on the persona of Holly Dickson, Adatum’s Microsoft 365 Administrator. In your role as Holly, you have been tasked with setting up the company’s profile for its Microsoft 365 trial tenant. In this task, you will configure the required options for Adatum’s tenant. Since Holly has yet to create a personal Microsoft 365 user account for herself (you will do this in the next lab exercise), Holly will initially sign into Microsoft 365 using the default Microsoft 365 tenant admin account and password that was created by your lab hosting provider. This account is the MOD Administrator account, whose alias is "admin". The username for this account is admin@xxxxxZZZZZZ.onmicrosoft.com (where xxxxxZZZZZZ is the tenant prefix assigned by your lab hosting provider); the display name for this account will be MOD Administrator.

1. When you open your lab hosting provider's Virtual Machine environment, you need to begin with the Client 1 VM (LON-CL1). If your VM environment opens with one of the other machines, then switch to LON-CL1 now.

2. Log into LON-CL1 as the local Adatum administrator account that was created by your lab hosting provider (**Administrator**) with the password **Pa55w.rd**. 

3. You may receive two warning messages at this point. If you receive a **Windows License** warning message asking you to activate Windows in Settings, select **Close**. If you receive a **Networks** warning message asking if you want this PC to be discoverable by other PCs and devices on this network, select **Yes**.

4. On the taskbar at the bottom of your screen, select the **Microsoft Edge** icon. If necessary, maximize your browser window when it opens.

5. In your Edge browser, go to the **Microsoft Office Home** page by entering the following URL in the address bar: **https://portal.office.com** 

6. In the **Sign in** dialog box, copy and paste in the **Microsoft 365 Tenant Username** provided by your lab hosting provider (this is the MOD Administrator account). The username should be in the form of **admin@xxxxxZZZZZZ.onmicrosoft.com**, where xxxxxZZZZZZ is the tenant prefix assigned by your lab hosting provider. Select **Next**.

7. In the **Enter password** dialog box, copy and paste in the unique **Microsoft 365 Tenant Password** provided by your lab hosting provider and then select **Sign in**.

8. On the **Stay signed in?** dialog box, select the **Don’t show this again** check box and then select **Yes.** On the **Save password** dialog box that appears, select **Never**.

9. If a **Welcome to your new Office, MOD** window appears, there's no option to close it. Instead, to the right of the window, select the right arrow icon (**>**) two times and then select the check mark icon to advance through the slides in this messaging window. 

10. If a **Find more apps** window appears, select the **X** in the upper right-hand corner of the window to close it. 

11. The **Microsoft Office Home** page appears in your Edge browser. Notice the initials **MA** that appear in a circle in the top-right corner of the screen. These are the initials of the **MOD Administrator** account, which is the tenant admin account created by your lab hosting provider that you just signed in as. The other existing Microsoft 365 user accounts that were created by your lab hosting provider have a picture associated with each of their accounts; therefore, when you sign in as any of these users in later labs, the user's picture will be displayed rather than the user's initials. However, when a user such as the MOD Administrator has no picture assigned to it, the user's initials are displayed in place of the picture. <br/>

	On the **Microsoft Office Home** page, in the list of application icons that appear in the left-hand pane, select **Admin**; this opens the **Microsoft 365 admin center** in a new browser tab. 

12. In the **Microsoft 365 admin center**, select **Show all** in the navigation pane and then select **Settings**. In the **Settings** group, select **Org settings**. 

13. On the **Org settings** page, the **Services** tab is displayed by default. Select the **Organization profile** tab.

14. In the **Organization profile** tab, select **Organization information** from the list of profile data.

15. In the **Organization information** pane that appears, enter the following information: <br/>

    - Name: **Adatum Corporation** (Note: Adatum Corporation is a subsidiary of Contoso Electronics. The Microsoft trial tenant that your lab hosting provider obtained for this lab may have been originally assigned to Contoso. If **Contoso** (or any other value) appears as the organization name, then change it to **Adatum Corporation**.)

    - Street Address: **555 Main Street**

    - City: **Redmond**

    - State or province: **Washington**

    - ZIP or postal code: **98052**

    - Phone: do not change

    - Technical contact: do not change

    - Preferred language: **English**

167. Select **Save**.

17. At the top of the **Organization information** pane, note the message indicating the changes have been saved. Select the **X** in the upper right-hand corner to close the pane.

18. Back on the **Organization profile** tab, in the list of organization profile data, select **Release preferences**.

19. In the **Release preferences** pane that appears, select the **Targeted release for select users** option and then select **Save**.<br/>

    **Note:** One of the benefits of Microsoft 365 is its ability to have the latest features and updates automatically applied to your environment. This process can reduce maintenance costs and overhead for an organization and allow early-adopter users to test new features. By setting up your **Release preferences**, you can control how and when your Microsoft 365 tenant receives these updates. <br/>

    **Note:** The **Targeted release for select users** option enables you to create a control group of users who will preview updates so that you can prepare the updates for your entire organization. The **Targeted release for everyone** option is more commonly used in development environments, where you can get updates early for your entire organization. In non-development environments, such as Adatum, targeted release to a select group of users is the more typical preference as it enables an organization to control when it wants to make updates available to everyone once they've been reviewed by the control group.

20. In the **Release preferences** pane, below the list of release options, select the **Select users** option.

21. In the **Choose users for targeted release** pane that appears, select inside the **Who should receive targeted releases?** field. This displays the list of active users (these are the Microsoft 365 user accounts created for your tenant by your lab hosting provider). In this list, select each of the following users. <br/>

    **Note:** You must select each user, one at a time. After selecting a user, you must select inside the field again to re-display the list so that you can select the next user. 

	- **Alex Wilber**
	- **Joni Sherman**
	- **Lynne Robbins**
	- **MOD Administrator** <br/>

    **Note:** Alex, Joni, and Lynne are part of Holly's Microsoft 365 pilot team. Their accounts will be used throughout the labs for this course.
    
22. Select **Save**.

23. At the top of the **Release preferences** pane, note the message indicating the 4 users were added to the targeted release. Select the **X** in the upper right-hand corner to close the pane. 

24. In the list of organization profile data, select **Custom themes**.

25. In the **Customize Microsoft 365 for your organization** pane, you can customize the default theme that users see when signed into Microsoft 365, and you can add additional custom themes. Select the **+Add theme** option.

26. In the **Default theme** pane, the **General** tab is displayed by default. Select the **Show the user's display name** check box. 
 
27. Select the **Logos** and **Colors** tabs and take some time to review their options. Note the various theme and branding options that are available for you to update. For the purpose of this lab, you can change any of the options or leave the default values as is. For example, in your real-world environment, you can add the logo of your company and set the background image as the default for all your users. For the purpose of this lab, you can change the colors for your navigation pane, text color, icon color, and accent color. Go ahead and explore the different options for your tenant and make any changes that you wish. <br/>

	**Tip:** Some color patterns aesthetically distract users. If you do change any of the colors, it's recommended that you avoid using high contrasting colors together, such as neon colors and high-resolution colors like bright pink and white.

28. Select **Save** when you are done and then close the **Custom themes** pane once your changes are saved.

29. Remain logged into **LON-CL1** with Microsoft Edge open to the **Microsoft 365 admin center** for the next task.

### Task 3 – Install Microsoft Graph PowerShell 

Microsoft Graph PowerShell is required to perform several configuration tasks when installing Microsoft 365. Because future lab exercises will perform several of these tasks using Windows PowerShell, you should begin by installing the Microsoft Graph PowerShell module. This module allows you to perform many of the Microsoft 365 user and organization administration tasks through PowerShell. It’s great for bulk tasks such as password resets, password policies, license management and reporting, and so on.  

1. On LON-CL1, you must open an elevated instance of **Windows PowerShell**. Select the magnifying glass (Search) icon on the taskbar at the bottom of the screen and type **power** in the Search box that appears. In the list of search results, right-click on **Windows PowerShell** (do not select Windows PowerShell ISE) and select **Run as administrator** in the drop-down menu. 

2. Maximize your PowerShell window. In **Windows PowerShell**, type the following command at the command prompt to install the Microsoft Graph PowerShell module from the PowerShell Gallery and then press Enter: <br/>

		Install-Module Microsoft.Graph -Scope CurrentUser

3. You will be prompted to confirm whether you want to install the module from an untrusted repository (PSGallery). Enter **A** to select **[A] Yes to All.**  <br/>

    **Note:** Your response will initiate the installation of all the Microsoft Graph sub-modules. Once all the installation messages (for each sub-module) have finished displaying, it will still take approximately 5 to 10 minutes to complete the Microsoft Graph PowerShell installation. During this time, the cursor will continue to blink below the untrusted repository message. This may be a good time to take a short break.

4. A command prompt will appear once Microsoft Graph PowerShell has been installed. Run the following command to see the complete list of sub-modules that were installed under the Microsoft.Graph primary module:  <br/>

		Get-InstalledModule Microsft.Graph.*  <br/>

	**Note:** The labs that use Microsoft Graph PowerShell in this course will use the following sub-modules: Microsoft.Graph.Identity.DirectoryManagement, Microsoft.Graph.Users, and Microsoft.Graph.Groups. To access the cmdlets for a sub-module, you must first import the sub-module. You can either import all 30+ sub-modules at one time using the "Import-Module Microsoft.Graph" command, or you can import each module that's needed to perform whatever function you're doing (for example, "Import-Module Microsoft.Graph.Users" to perform user maintenance). For the purpose of this training, since only three sub-modules will be used in later lab exercises, you will only import these three sub-modules as they're needed in later labs, rather than importing all 30+ sub-modules.

5. Do **NOT** close your PowerShell window. Leave the Windows PowerShell window open but minimize it for now. Remain logged into LON-CL1 and keep your Edge browser open.


# Proceed to Lab 1 - Exercise 2 
