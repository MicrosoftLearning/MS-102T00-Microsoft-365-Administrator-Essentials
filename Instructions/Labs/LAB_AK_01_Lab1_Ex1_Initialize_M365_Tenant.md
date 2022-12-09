# Learning Path 1 - Lab 1 - Exercise 1 - Initialize your Microsoft 365 Tenant 

Adatum Corporation is a subsidiary of Contoso Electronics. Adatum runs its legacy applications (such as Microsoft Exchange Server 2019) in an on-premises deployment. However, it recently subscribed to Microsoft 365, thereby creating a hybrid deployment in which it must synchronize its on-premises and cloud deployments. 

As Adatum's Enterprise administrator, you have been tasked with deploying Microsoft 365 in Adatum’s hybrid deployment using a virtualized lab environment. In this exercise, you will set up Adatum's Microsoft 365 trial tenant, and your instructor will guide you on how to obtain your Microsoft 365 credentials in your lab-hosted environment. You will use these credentials throughout the remaining labs in this course. 

In your lab environment, your lab hosting provider has already obtained a Microsoft 365 trial tenant for you. Your lab provider has also created two admin accounts that you will use in your VM lab environment: 

- A local administrator account for Adatum's on-premises environment (Adatum\Administrator).
- A default tenant admin account in Microsoft 365 (the display name for this user account is MOD Administrator). 

You will log into the Domain Controller VM (LON-DC1) using the local Adatum\Administrator account. When you access Microsoft 365 for the first time, you will initially log in using the Microsoft 365 tenant admin account (MOD Administrator). You will then update Adatum's Microsoft 365 organizational profile, and you'll prepare your tenant for Microsoft Azure Active Directory and for a future lab using Microsoft Teams.


### Task 1 - Obtain Your Microsoft 365 Credentials

Once you launch the lab, you'll be able to access the free Microsoft 365 trial tenant provided by your lab hosting provider in the Microsoft Virtual Lab environment. Within this tenant, your lab hosting provider has created a Microsoft 365 user account for a default tenant administrator named MOD Administrator. Your lab hosting provider has assigned this user account a unique username and password, and the account has been assigned the Microsoft 365 Global administrator role. You must retrieve this username and password so that you can sign into Microsoft 365 within the Microsoft Virtual Lab environment. You will also be assigned a unique network IP address and UPN name for your Microsoft 365 blob. You will also use this UPN name in various tasks throughout the labs for this course.

Because this course can be offered by learning partners using any one of several authorized lab hosting providers, the actual steps involved to retrieve the UPN name, network IP address, and tenant ID associated with your tenant may vary by lab hosting provider. Therefore, your instructor will provide you with the necessary instructions on how to retrieve this information for your course. <br/>

You should write down the following information (provided by your instructor) for later use:

- **Tenant prefix.** This tenant prefix is for the Microsoft 365 user accounts that you will use to sign into Microsoft 365 throughout the labs in this course. The domain for each Microsoft 365 user account is in the format of {user alias}@xxxxxZZZZZZ.onmicrosoft.com, where xxxxxZZZZZZ is the tenant prefix. It consists of two parts - your lab hoster's prefix (xxxxx; some hosters use a generic prefix such as M365x, while others use their company initials or some other designation) and the tenant ID (ZZZZZZ; usually a 6 digit number). Record this xxxxxZZZZZZ tenant prefix value for later use. When any of the lab steps direct you to sign into Microsoft 365 as one of the user accounts (such as the MOD Administrator), you must enter the xxxxxZZZZZZ value that you obtained here as the tenant prefix portion of your .onmicrosoft.com domain.

- **Tenant password.** This is the password provided by your lab hosting provider for the tenant admin account.

- **Custom Domain name.** Your lab hosting provider has created a custom domain name for Adatum. You will use this domain when adding a custom domain into Microsoft 365 in a later lab exercise. The domain name is in the format **xxxUPNxxx.xxxCustomDomainxxx.xxx.** You must replace **xxxUPNxxx** with the UPN number provided by your lab hosting provider, and you must replace **xxxCustomDomainxxx.xxx** with the lab hosting provider's domain name. For example, let's assume your lab hosting provider is Fabrikam Inc. If the UPN number it assigns to your tenant is AMPVU3a and its custom domain name is fabrikam.us, then the domain name for your new custom domain would be AMPVU3a.fabrikam.us. Your instructor will provide you with your lab hosting provider's UPN number and custom domain name.  

- **Network IP address.** Write down the **IP Address** value (this is the IP Address of your parent domain; for example, 64.64.206.13).

### Task 2- Set up the Organization Profile

Throughout the labs in this course, you will role-play by taking on the persona of Holly Dickson, Adatum’s Enterprise Administrator. In your role as Holly, you have been tasked with setting up the company’s profile for its Microsoft 365 trial tenant. In this task, you will configure the required options for Adatum’s tenant. Since Holly has yet to create a personal Microsoft 365 user account for herself (you will do this in the next lab exercise), Holly will initially sign into Microsoft 365 using the default Microsoft 365 tenant admin account and password that was created by your lab hosting provider. This account is the MOD Administrator account, whose alias is "admin". The username for this account is admin@xxxxxZZZZZZ.onmicrosoft.com (where xxxxxZZZZZZ is the tenant prefix assigned by your lab hosting provider); the display name for this account will be MOD Administrator.

1. When you open your lab hosting provider's Virtual Machine environment, you need to begin with the Domain Controller VM (LON-DC1). If your VM environment opens with one of the other machines, either the local client PC (LON-CL1) or Adatum's on-premises Exchange Server (LON-EX1), then switch to LON-DC1 now.

2. On **LON-DC1**, you must select **Ctrl+Alt+Delete** to log in (your instructor will guide you on how to find this option in your VM environment). Log into LON-DC1 as the local Adatum administrator account that was created by your lab hosting provider (**Administrator**) with the password **Pa55w.rd**. 

3.  You may receive two warning messages at this point. If you receive a **Windows License** warning message asking you to activate Windows in Settings, select **Close**. If you receive a **Networks** warning message asking if you want this PC to be discoverable by other PCs and devices on this network, select **Yes**.

4. **Server Manager** will automatically start. Leave it open (it’s used in the next task) but minimize the window for now.

5. On the taskbar at the bottom of your screen, select the **Microsoft Edge** icon. If necessary, maximize your browser window when it opens.

6. In your Edge browser, go to the **Microsoft Office Home** page by entering the following URL in the address bar: **https://portal.office.com** 

7. In the **Sign in** dialog box, copy and paste in the **Microsoft 365 Tenant Username** provided by your lab hosting provider (this is the MOD Administrator account). The username should be in the form of **admin@xxxxxZZZZZZ.onmicrosoft.com**, where xxxxxZZZZZZ is the tenant prefix assigned by your lab hosting provider. Select **Next**.

8. In the **Enter password** dialog box, copy and paste in the unique **Microsoft 365 Tenant Password** provided by your lab hosting provider and then select **Sign in**.

9. On the **Stay signed in?** dialog box, select the **Don’t show this again** check box and then select **Yes.** On the **Save password** diaglog box that appears, select **Never**.

10. If a **Welcome to your new Office, MOD** window appears, there's no option to close it. Instead, to the right of the window, select the right arrow icon (**>**) two times and then select the check mark icon to advance through the slides in this messaging window. 

11. If a **Find more apps** window appears, select the **X** in the upper right-hand corner of the window to close it. 

12. The **Microsoft Office Home** page appears in your Edge browser. Notice the initials **MA** that appear in a circle in the top-right corner of the screen. These are the initials of the **MOD Administrator** account, which is the tenant admin account created by your lab hosting provider that you just signed in as. The other existing Microsoft 365 user accounts that were created by your lab hosting provider have a picture associated with each of their accounts; therefore, when you sign in as any of these users in later labs, the user's picture will be displayed rather than the user's initials. However, when a user such as the MOD Administrator has no picture assigned to it, the user's initials are displayed in place of the picture. <br/>

	On the **Microsoft Office Home** page, in the list of application icons that appear in the left-hand pane, select **Admin**; this opens the **Microsoft 365 admin center** in a new browser tab. 

13. In the **Microsoft 365 admin center**, select **Show all** in the navigation pane and then select **Settings**. In the **Settings** group, select **Org settings**. 

14. On the **Org settings** page, the **Services** tab is displayed by default. Select the **Organization profile** tab.

15. In the **Organization profile** tab, select **Organization information** from the list of profile data.

16. In the **Organization information** pane that appears, enter the following information: <br/>

    - Name: **Adatum Corporation** (Note: Adatum Corporation is a subsidiary of Contoso Electronics. The Microsoft trial tenant that your lab hosting provider obtained for this lab may have been originally assigned to Contoso. If **Contoso** (or any other value) appears as the organization name, then change it to **Adatum Corporation**.)

    - Street Address: **555 Main Street**

    - City: **Redmond**

    - State or province: **Washington**

    - ZIP or postal code: **98052**

    - Phone: do not change

    - Technical contact: do not change

    - Preferred language: **English**

17. Select **Save**.

18. At the top of the **Organization information** pane, note the message indicating the changes have been saved. Select the **X** in the upper right-hand corner to close the pane.

19. Back on the **Organization profile** tab, in the list of organization profile data, select **Release preferences**.

20. In the **Release preferences** pane that appears, select the **Targeted release for select users** option and then select **Save**.<br/>

    **Note:** One of the benefits of Microsoft 365 is its ability to have the latest features and updates automatically applied to your environment. This process can reduce maintenance costs and overhead for an organization and allow early-adopter users to test new features. By setting up your **Release preferences**, you can control how and when your Microsoft 365 tenant receives these updates. <br/>

    **Note:** The **Targeted release for select users** option enables you to create a control group of users who will preview updates so that you can prepare the updates for your entire organization. The **Targeted release for everyone** option is more commonly used in development environments, where you can get updates early for your entire organization. In non-development environments, such as Adatum, targeted release to a select group of users is the more typical preference as it enables an organization to control when it wants to make updates available to everyone once they've been reviewed by the control group.

21. In the **Release preferences** pane, below the list of release options, select the **Select users** option.

22. In the **Choose users for targeted release** pane that appears, select inside the **Who should receive targeted releases?** field. This displays the list of active users (these are the Microsoft 365 user accounts created for your tenant by your lab hosting provider). In this list, select each of the following users. <br/>

    **Note:** You must select each user, one at a time. After selecting a user, you must select inside the field again to re-display the list so that you can select the next user. 

	- **Alex Wilber**
	- **Joni Sherman**
	- **Lynne Robbins**
	- **MOD Administrator** <br/>

    **Note:** Alex, Joni, and Lynne are part of Holly's Microsoft 365 pilot team. Their accounts will be used throughout the labs for this course.
    
23. Select **Save**.

24. At the top of the **Release preferences** pane, note the message indicating the 4 users were added to the targeted release. Select the **X** in the upper right-hand corner to close the pane. 

25. In the list of organization profile data, select **Custom themes**.

26. In the **Customize Microsoft 365 for your organization** pane, you can customize the default theme that users see when signed into Microsoft 365, and you can add additional custom themes. Select the **+Add theme** option.

27. In the **Default theme** pane, the **General** tab is displayed by default. Select the **Show the user's display name** check box. 
 
28. Select the **Logos** and **Colors** tabs and take some time to review their options. Note the various theme and branding options that are available for you to update. For the purpose of this lab, you can change any of the options or leave the default values as is. For example, in your real-world environment, you can add the logo of your company and set the background image as the default for all your users. For the purpose of this lab, you can change the colors for your navigation pane, text color, icon color, and accent color. Go ahead and explore the different options for your tenant and make any changes that you wish. <br/>

	**Tip:** Some color patterns aesthetically distract users. If you do change any of the colors, it's recommended that you avoid using high contrasting colors together, such as neon colors and high-resolution colors like bright pink and white.

29. Select **Save** when you are done and then close the **Custom themes** pane once your changes are saved.



### Task 3 – Prepare for Microsoft Azure Active Directory 

Azure Active Directory is required to perform several configuration tasks when installing Microsoft 365. Because future lab exercises will perform several of these tasks using Windows PowerShell, you should begin by installing the Azure Active Directory PowerShell module. This module allows you to perform many of the Microsoft 365 user and organization administration tasks through PowerShell. It’s great for bulk tasks such as password resets, password policies, license management and reporting, and so on.  

1. On LON-DC1, you must open an elevated instance of **Windows PowerShell**. Select the magnifying glass (Search) icon on the taskbar at the bottom of the screen and type **powershell** in the Search box that appears. In the list of search results, right-click on **Windows PowerShell** (do not select Windows PowerShell ISE) and select **Run as administrator** in the drop-down menu. 

2. Maximize your PowerShell window. In **Windows PowerShell**, at the command prompt type the following command to install the Azure AD PowerShell module from the PowerShell Gallery and then press Enter: <br/>

		Install-Module AzureAD

3. It may take a minute or two, but you will eventually be prompted to confirm whether you want to install the module from an untrusted repository (PSGallery). Enter **A** to select **[A] Yes to All.**  <br/>

    **Note:** If you receive a warning message indicating version 2.0.2.130 of the AzureAD module is already installed in your VM environment and that you can install the next version using the -force parameter, ignore this message.

4. Once the installation is complete, the screen will return to the Windows PowerShell command prompt. You have now installed the Windows Azure Active Directory PowerShell Module. <br/>

	You now must connect to the AzureAD module that you just installed. Type the following command and then press Enter: <br/>

		Connect-AzureAD

5. If a **Sign in** window appears, enter the Microsoft 365 tenant admin username and password provided by your lab hosting provider (this is the MOD Administrator account you used to sign into Microsoft 365).

6. You have installed the AzureAD module and connected to it for your current lab session, so do **NOT** close your PowerShell window. Leave the Windows PowerShell window open but minimize it for now. 

7. Remain logged into LON-DC1 and keep your Edge browser open.


### Task 4 – Prepare for External Access using Microsoft Teams 

When you get to Module 4, you will perform a lab in which you will create a new service request ticketing system. One of the tasks within that lab requires you to collaborate with one of your fellow student's Microsoft 365 tenant through Microsoft Teams. To enable this communication between your Microsoft 365 tenant and your fellow student's tenant, you must turn on the **External Access** functionality within Microsoft Teams so that you can communicate with your fellow student's domain. By default, the system is set to allow access to all external domains. However, for security reasons, Adatum's CTO wants to limit exposure to just the domain of your fellow student, who will take on the role of an external IT consultant who is working with Adatum in the Module 4 lab exercises. 

**Important:** When you modify the External Access feature to limit access to a specific domain, it can take a couple of hours for your system to propagate the change through your tenant. Therefore, you will configure this External Access feature in this task so that the internal changes made by the system have time to propagate through your tenant by the time you eventually get to the Module 4 lab.

**Instructor/Student Note:** To facilitate this lab, your instructor should collect each student's tenant ID (ZZZZZZ) from each of their domains (this would be each student's xxxxxZZZZZZ.onmicrosoft.com domain, where xxxxxZZZZZZ is the tenant prefix assigned to your fellow student by your lab hosting provider; ZZZZZZ is the tenant ID portion of the tenant prefix that is unique to each student). The instructor will then assign to each student the tenant ID (ZZZZZZ) from another student (you can NOT be assigned your own tenant ID). In this task, you will limit external access to the domain associated with the assigned tenant ID from your fellow student (in other words, you will enter the **xxxxxZZZZZZ.onmicrosoft.com** domain, where ZZZZZZ is your fellow student's tenant ID).

By the time you get to the Module 4 labs, External Access should be ready so that you can collaborate with the student whose domain you set up in this task. 

1. On LON-DC1, in your Microsoft Edge browser, you should still be logged into the Microsoft 365 admin center as the MOD Administrator from the earlier task in which you updated Adatum's organizational profile. <br/>

	If you closed the Microsoft 365 admin center, then perform the same steps as before to open it and sign in as **admin@xxxxxZZZZZZ.onmicrosoft.com** (where xxxxxZZZZZZ is the tenant prefix assigned by your lab hosting provider) with the tenant admin password provided by your lab hosting provider.
	
2. If necessary, in the **Microsoft 365 admin center** navigation pane, select **...Show All** to display the full navigation menu.

3. In the **Microsoft 365 admin center**, under the **Admin Centers** group in the navigation pane, select **Teams**.

4. A new tab will open in your Edge browser that displays the **Microsoft Teams admin center**. If a **Welcome to the Teams admin center** window appears, select **Skip tour**.

5. In the **Microsoft Teams admin center** navigation pane, select **Users** and then select **External access**.

6. On the **External access** page, under the **Teams and Skype for Business users in external organizations** section, select the **Choose which external domains your users have access to** field. In the drop-down menu that appears, select **Allow only specific external domains**. 

7. Select the **Allow domains** button that appears to add the external domain you want to allow. 

8. In the **Add external domain** pane that appears on the right side of the screen, enter in the **Domain** field the **xxxxxZZZZZZ.onmicrosoft.com** domain for your fellow student's tenant ID (where ZZZZZZ is your fellow student's tenant ID that was assigned to you by your instructor). This will enable you to communicate with your fellow student once you get to the exercises in the Module 4 labs. Do NOT enter your domain. When you've finished entering your fellow student's domain, select **Done**. 

9. On the **External access** page, under the **Teams accounts not managed by an organization** section, verify the toggle switch is set to **On**. If it's set to **Off**, then set it to **On** now. <br/>

	Below the toggle switch, verify the check box is selected for the option titled: **External users with Teanms accounts not managed by an organization can contact users in my organization**.

10. Under the **Skype users** section, verify the toggle switch uis set to **On**. If it's set to **Off**, then set it to **On** now. 

11. Select the **Save** button at the bottom of the page.<BR/>

13. If a prompt warning that **Changes will take time to take effect** is displayed, select **Confirm**

14. In your Microsoft Edge browser, close the **External access - Microsoft Teams** tab. This should return you to the **Microsoft 365 admin center** tab, which you should leave open as you proceed to the next exercise.


# Proceed to Lab 1 - Exercise 2 
