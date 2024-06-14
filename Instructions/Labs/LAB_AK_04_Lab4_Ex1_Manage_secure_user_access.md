# Learning Path 4 - Lab 4 - Exercise 1 - Manage secure user access 

Holly has then been asked by Adatum’s CTO to deploy Microsoft Entra Multifactor Authentication (MFA), Pass-through Authentication (PTA), and Microsoft Entra Smart Lockout. These three features will help strengthen password management throughout the organization in preparation for Copilot for Microsoft 365. For PTA, you will deploy it using Microsoft Entra Cloud Sync. And for Smart Lockout, you will deploy it using Group Policy Management. 

For MFA, you will create a Conditional Access policy to deploy MFA for all of Adatum's users. You will then modify it to exclude Holly and the selected members of her Microsoft 365 pilot project team. That will save you from having to use MFA when signing in with them, as well as provide you with experience on how to exclude users in a Conditional Access policy. 

**Note:** Excluding specific users from using MFA is not something you would normally do in a real-world scenario. However, for the purpose of saving time in this classroom training lab, we will disable MFA for the test users. 

### Task 1: Create a Conditional Access policy to implement MFA

As your training indicated, there are three ways to implement MFA - with Conditional Access policies, with security defaults, and with legacy per-user MFA (not recommended for larger organizations). In this exercise, you'll enable MFA through a Conditional Access policy, which is the method that Microsoft recommends. Adatum has directed Holly to enable MFA for all its Microsoft 365 users - both internal and external. However, for the purpose of testing Adatum's Microsoft 365 pilot project implementation, Holly wants to exclude the members of the M365 pilot project group from having to use MFA to sign in. Once the pilot project is complete, Holly will update the policy by removing the exclusion of this group from the MFA requirement. The policy will also include two other requirements. It will require MFA for all cloud apps, and it will require MFA even if a user signs in from a trusted location. 

1. In the prior lab exercise, you were working on LON-DC1. In this task, you'll be working back on your Client 1 machine. <br/>

	Switch to **LON-CL1**.

2. On the LON-CL1 VM, the **Microsoft 365 admin center** should still be open in your Microsoft Edge browser from an earlier task. You should be signed into Microsoft 365 as **Holly Dickson**.
   
3. In the **Microsoft 365 admin center**, under the **Admin centers** section in the navigation pane, select **Identity**. Doing so opens the Microsoft Entra admin center in a new browser tab. If a **Pick an account** window appears, select **Holly Dickson's account**.

4. In the **Microsoft Entra admin center**, select **Protection** in the navigation pane, and then select **Conditional Access**.

5. On the **Conditional Access | Overview** page, select **Policies** in the middle navigation pane.

6. On the **Conditional Access | Policies** page, review the default policies available with your Microsoft 365 subscription. Note the policy titled **Multifactor authentication for Microsoft partners and vendors**. This is the Conditional Access policy that Microsoft created that requires MFA for all users on all cloud apps. Select this policy so that you can see how Microsoft is enforcing MFA for all users in this trial tenant.

7. On the **Multifactor authentication for Microsoft partners and vendors** page, under the **Users** group, select **All users included and specific users excluded**. Doing so displays two tabs - **Include** and **Exclude**.

8. Under the **Include** tab, note that **All users** is selected. Just to satisfy your curiosity, let's try changing this policy by turning off MFA. Select **None** and then select the **Save** button. <br/>
	
 	**Note what happened:** A message box briefly appeared at the top of the page indicating **Failed to update Multifactor authentication for Microsoft partners and vendors**. The system then returned you to the **Conditional Access | Policies** page. If you didn't see this message, then repeat this step again.  <br/>

	The same thing happens if, under the **Include** tab, you select **Users and groups** and you select specific users or groups rather than all users. In fact, Microsoft has built in a security firewall so that if you try to make any change to this policy, it will fail when you attempt to save the policy. 

9. Microsoft did build one exclusion into this policy. Let's take a look at it. On the **Policies** page, select the **Multifactor authentication for Microsoft partners and vendors** policy again, and then select **All users included and specific users excluded**. This time select the **Exclude** tab. 

10. Note that Microsoft selected the **Directory roles** checkbox. Select the field below this option. In the menu of roles that you can choose to exclude from MFA, the only role that Microsoft selected is **Directory Synchronization Accounts**. This role is automatically assigned to the Microsoft Entra Connect Sync service account and is not meant to be used otherwise. It's a special role that has permissions only to perform directory synchronization tasks. This role is crucial for synchronizing a local Active Directory Domain Services (AD DS) to Microsoft Entra ID, providing identity coexistence. Microsoft doesn't require MFA for this role because the synchronization service needs to run continuously without any interruptions that could be caused by MFA prompts. Additionally, this service account is configured with very limited permissions, and it isn't used for interactive sign-ins, which reduces the security risk.   <br/>

	As with the prior step where you tried to change the MFA setting to include no users or selected users, if you try to select other roles to get around the MFA setting, you will experience the same error indicating **Failed to update Multifactor authentication for Microsoft partners and vendors** when you try to save the policy. Microsoft's security firewall doesn't allow any change to this Conditional Access policy that affects those who must use MFA.

11. If you still have the **Multifactor authentication for Microsoft partners and vendors** page open, then select the **X** in the upper corner to close it and return back to the **Conditional Access | Policies** page. Or if you tried saving a change to the policy, your attempt will have failed, and you should already be back on the **Conditional Access | Policies** page.

12. On the **Conditional Access | Policies** page, on the menu bar at the top of the page, select **+New policy**.

13. On the **New Conditional Access policy** window, enter **MFA for all Microsoft 365 users** in the **Name** field.

14. You will begin by defining the MFA requirement for users. Under the **Users** group, select **0 users and groups selected**. Doing so displays two tabs - **Include** and **Exclude**.

15. Under the **Include** tab, select **All users**. Note the warning message that appears. You will address this in the next two steps.

16. Select the **Exclude** tab. To avoid system lockout, as the prior warning message indicated, you want to exclude your Global administrators - in this case, Holly. Holly also wants to exclude the other Microsoft 365 pilot project group members for the sake of expediency when testing. Once Microsoft 365 goes live, Holly will remove the pilot project group from the Exclude list in this Conditional Access policy and simply exclude herself, the MOD Administrator, and a few other Global admins. But for now, Holly wants to exclude the entire pilot project group. <br/>

	To do so, select **Users and groups**. 

17. On the **Select excluded users and groups** window that appears, you want to select the Microsoft 365 pilot project group. The **All** tab is displayed by default. To quickly find the pilot project group, select the **Groups** tab. In the list of active groups, select the check box next to the **M365 pilot project** group, and then select the **Select** button at the bottom of the window. Back on the **New Conditional Access policy** window, note the message that appears under the **Users** section. 

18. You will now define the MFA requirement for all cloud apps. Under the **Target resources** section, select **No target resources selected**. Doing so displays two tabs - **Include** and **Exclude**.

19. Select the **Select what this policy applies to** drop-down field to see the various options in the drop-down menu. Select **Cloud apps**. 

20. Under the **Include** tab, note that the default setting is **None**. If you did not change this setting, then no cloud apps would require MFA - and that includes Microsoft 365. So even if you created this policy and selected the option to require MFA for all users, but you left this **Target resources** setting to **None**, then any user signing into Microsoft 365 would not have to use MFA. <br/>

	Under the **Include** tab, select the **Select apps** option. Doing so displays two sections - **Edit filter** and **Select**. Under the **Select** section, select **None**. In the **Select Cloud apps** pane that appears, scroll down through the list of apps to see all the different apps that you could require MFA for. **Do NOT select any of the apps.** We're having you scroll through this list just to get a feel for how granular you can get when requiring MFA should you decide to limit MFA to certain apps.  <br/>

	For Adatum, Holly wants to require MFA for all cloud apps, which is typically a more common business scenario than selecting specific apps. Under the **Include** tab, select the **All cloud apps** option. Adatum will not exclude any cloud apps from MFA authentication. You can select the **Exclude** tab if you want to see the options it provides. It works basically the same as the **Include** tab. You can view this tab, but do NOT select any cloud apps for exclusion. 

21. Finally, you will define the MFA requirement for all user sign-in locations. In some scenarios, organizations may only require MFA if a user signs-in from an untrusted location. However, Adatum wants to require MFA for all included users, regardless of where they sign in. <br/>

	Under **Conditions**, select **0 conditions selected**. Doing so displays a list of potential conditions the policy will check for. For this lab exercise, under the **Locations** condition, select **Not configured**. Doing so displays a **Configure** toggle switch and two tabs - **Include** and **Exclude**. Both tabs are currently disabled.

22. Set the **Configure** toggle switch to **Yes**, which enables the two tabs. 

23. Under the **Include** tab, verify **Any location** is selected (select it if necessary). Select the **Exclude** tab. If your organization recognizes specific IP addresses or ranges of addresses as "trusted", you can exclude the MFA requirement if a user signs in from one of those locations. However, Adatum wants to require MFA for all user sign-in attempts, regardless of their location. This will include both internal and external user sign-ins. Verify the **Selected locations** option is selected, and under the **Select** section, verify it says **None**. By not specifying any selected locations, this setting ensures that no locations are excluded from MFA. 

24. Under the **Access controls** section, under the **Grant** group, select **0 controls selected**. Doing so displays a **Grant** pane.

25. In the **Grant** pane that appears, verify the **Grant access** option is selected (select it if necessary). Then select the **Require multifactor authentication** check box. Note all the other access controls that are available that can be enabled with this policy. For this policy, you will only require MFA. Select the **Select** button at the bottom of the **Grant** pane, which closes the pane. 

26. At the bottom of the **New** window, in the **Enable policy** field, select **On**.

27. Note the option that appears at the bottom of the page that warns you not to lock yourself out. Select the option **I understand that my account will be impacted by this policy. Proceed anyway.** In fact, Holly won't be impacted since she's a member of the M365 pilot project group that is excluded from this policy.

28. Select the **Create** button to create the policy.

29. On the **Conditional Access | Policies** window that appears, verify the **MFA for all Microsoft 365 users** policy appears and that its **State** is set to **On**.

30. Remain logged into LON-CL1 with all your Microsoft Edge browser tabs open for the next task.


### Task 2: Test MFA for both an included and excluded user

To test the Conditional Access policy that you just created, you will sign-out of Microsoft 365 as Holly, and then you'll sign back in as Adele Vance. Adele is not a member of the M365 pilot project group, so Microsoft Entra should require that she use MFA when signing in. Once you sign-in as Adele and verify that MFA works, you will sign-out as Adele and then sign back in as Holly. Since Holly is a member of the M365 pilot project group that was excluded from using MFA in the Conditional Access policy, you should not have to use MFA when signing in as Holly. 

**Important:** To implement MFA, you will need to use your mobile phone to receive a verification code so that you can enter it into your tenant as a second form of authentication. If you do not have a phone, you can still test your Conditional Access policy. When signing in as Adele Vance, the system will require you to sign in with a second form of authentication. At that point, you can simply cancel out of your sign-in and then sign back in as Holly, who will not require MFA. While you will not complete the MFA sign-in, you will still verify that the system forces you to use it when attempting to sign-in as Adele.

1. On the LON-CL1 VM, the **Microsoft 365 admin center** should still be open in your Microsoft Edge browser from the prior task. You should be signed into Microsoft 365 as **Holly Dickson**. You will begin by signing out of Microsoft 365. On the **Microsoft 365 admin center** tab, select Holly's name in the upper right corner of your browser. In the **Holly Dickson** window that appears, select **Sign out.** <br/>
	
	**Important:** Once you are signed out, close your browser session to clear your cache, and then open a new Microsoft Edge browser session. 
	
2. Select the **Edge** icon on your taskbar to open a new browser session. In your browser go to the **Microsoft Office Home** page by entering the following URL in the address bar: **https://portal.office.com/** 

3. In the **Pick an account** window, select **Use another account**. 

4. In the **Sign in** window, enter **AdeleV@xxxxxZZZZZZ.onmicrosoft.com** (where xxxxxZZZZZZ is the tenant prefix provided by your lab hosting provider) and then select **Next**. In the **Enter password** window, enter the Administrative Password provided by your lab hosting provider for the tenant admin account (i.e. the MOD Administrator account) and select **Sign in**.

5. Because MFA is enabled for all users except for the M365 pilot project group members (of which, Adele is not a member), a **More information required** window appears. Select **Next**. This returns the **Microsoft Authenticator** page, which is the starting point for signing in with MFA. <br/>

	**Important:** If you do not have a phone, then this is as far as you can go when attempting to sign-in as Adele. Even though you can't complete the sign-in, you have verified that the first part of your Conditional Access policy is working, since it requires Adele to sign-in using MFA. At this point, close your Edge browser session, and then skip to step #15, at which point you will sign back in as Holly.

6. On the **Microsoft Authenticator** page that appears, you can download this mobile app or use a different method for MFA verification. For the purposes of this lab, we recommend you use your mobile phone so that you do not have to take time installing the Microsoft Authenticator app that you may not use again after this training class. Select the **I want to set up a different method** option at the bottom of the page (**Important:** Do NOT confuse this link with the **I want to use a different authenticator app** that appears above it). 

7. On the **Choose a different method** dialog box that appears, select the drop-down arrow in the **Which method would you like to use?** field, select **Phone**, and then select **Confirm**. 

8. In the **Phone** window that appears, under **What phone number would you like to use?** field, select your country or region, and then in the field next to it, enter your phone number (in the format **nnn-nnn-nnnn**). Verify the **Receive a code** option is selected and then select **Next**.

9. Retrieve the verification code from the text message that is sent to your phone.

10. In the **Phone** window, enter the 6-digit verification code in the code field and then select **Next**. When the **Phone** window displays a message indicating your phone was registered successfully, select **Next**.

11. On the **Success!** page, select **Done**.

12. If a **Stay signed in?** dialog box appears, select the **Don’t show this again** check box and then select **Yes.** 

13. On the **Home | Microsoft 365** tab, select the **Word** icon that appears in the column of app icons on the left-side of the screen. This opens **Microsoft Word** in a new browser tab. Doing so validates that you can access a Microsoft 365 app after signing in using MFA.  <br/>
	**Important:** You have now verified that the first part of the Conditional Access policy that you created works. The policy requires that a user who is not a member of the Microsoft 365 pilot project team must sign-in using MFA. You verified this works when you signed in as Adele. You will now sign out as Adele and sign back in as Holly, during which you will verify that the second part of the Conditional Access policy also works. You should NOT have to use MFA when signing in as Holly, since she's a member of the M365 pilot project group, which is excluded from the MFA requirement in the Conditional Access policy.

14. On the **Microsoft 365 admin center** tab, select the icon for Adele's account in the upper right corner of your browser. In the **Adele Vance** window that appears, select **Sign out.** <br/>
	
	**Important:** Once you are signed out, close your browser session to clear your cache, and then open a new Microsoft Edge browser session. 
	
15. Select the **Edge** icon on your taskbar to open a new browser session. In your browser go to the **Microsoft Office Home** page by entering the following URL in the address bar: **https://portal.office.com/** 

16. In the **Pick an account** window, select **Holly@xxxxxZZZZZZ.onmicrosoft.com** (where xxxxxZZZZZZ is the tenant prefix provided by your lab hosting provider) and then select **Next**. In the **Enter password** window, enter the same Administrative Password provided by your lab hosting provider for the tenant admin account (i.e. the MOD Administrator account) and select **Sign in**.

17. Because MFA is required for all users except for the M365 pilot project team members (of which, Holly is a member), MFA will not be required. Since MFA is not required, the system displays the **Microsoft 365 Home** page. Select the **Admin** icon to navigate to the **Microsoft 365 admin center**. <br/>

	**Important:** You have now verified that the second part of the Conditional Access policy that you created works. The policy excludes members of the Microsoft 365 pilot project group from signing-in using MFA. Holly is a member of this group, and she did not have to sign in using MFA.

18. Remain logged into LON-CL1 with the **Microsoft 365 admin center** open in your browser.


### Task 3: Deploy Microsoft Entra Pass-Through Authentication 

Pass-through Authentication allows users to sign-in to cloud-based services using their on-premises passwords. All user passwords are only stored locally in the on-premises domains and NEVER synchronized to the cloud. When a user signs-in, the PTA agent takes the credentials to the user's on-premises environment to verify whether the password is correct. It then sends the result back to Microsoft Entra ID (formerly Azure AD).   

‎Adatum's CTO wants to provide the company's users with an improved sign-in experience (since PTA requires one less password to remember), as well as reduce Adatum’s IT helpdesk costs because with PTA their users are less likely to forget how to sign in. While this can also be achieved by employing Password Hash Synchronization as well as Active Directory Federation Services, Adatum has chosen to test PTA in its Microsoft 365 pilot project.

1.  In this task, you will be working from Adatum's domain controller, LON-DC1. <br/>

	Switch to **LON-DC1**.

2. On LON-DC1, select the **Start** button on the taskbar, and then in the **Start** menu, select the **All Apps** icon to display the list of all installed applications. Select the **Azure AD Connect** program group and then select **Azure AD Connect**. This will initiate the **Microsoft Azure Active Directory Connect** wizard.

3. In the **Welcome to Azure AD Connect** window, you will receive a page indicating the synchronization service scheduler is suspended until this setup wizard is closed. This is because if you start the Azure AD Connect installation wizard (which you did in an earlier task), then the scheduler is temporarily suspended. Select **Configure.**

4. On the **Additional tasks** page, select the **Change user Sign-in** task and then select **Next**. 

5. On the **Connect to Azure AD** page, sign into Azure AD (Microsoft Entra ID). The **USERNAME** field is already filled with **Holly@xxxUPNxxx.onmicrosoft.com**. In the **PASSWORD** field, enter the **Administrative Password** provided by your lab hosting provider for the tenant admin account (i.e. the MOD Administrator account) that you assigned to Holly's account, and then select **Next**.

6. On the **User sign-in** page, under **Select the Sign On method**, select **Pass-through authentication** and then select **Next**. 

7. On the **Enable single sign-on** page, select **Enter credentials**. 

8. In the **Forest Credentials** dialog box, enter **Adatum\Administrator** as the **User name** and **Pa55w.rd** as the **Password**, and then select **OK**. 

9. When the credentials are verified, a check mark will appear to the right of the **Enter credentials** button. Select **Next**. 

10. On the **Ready to configure** page, leave the check box selected for the **Start the synchronization process when configuration completes** option (if the check box is not selected, then select it now). Select **Configure**. It may take a minute or so for the configuration to complete.

11. On the **Configuration complete** page, note the message indicating the current sign on method for Azure AD is PTA. Select **Exit**. Pass-Through Authentication has now been enabled. 

12. To verify that Pass-Through Authentication is successfully enabled, select the **Microsoft 365 admin center** tab in your Edge browser. Under **Admin centers** in the navigation pane, select **Identity**.

13. This opens the **Microsoft Entra admin center**. Select **Show more** in the navigation pane, select **Hybrid management** to expand this group, and then select **Microsoft Entra Connect**. 

17. On the **Microsoft Entra Connect | Get started** page, select **Connect Sync** in the middle navigation pane.

18. On the **Microsoft Entra Connect | Connect Sync** page, in the detail pane on the right, under the **USER SIGN-IN** section, verify that the status of **Pass-through authentication** is **Enabled**, and then select **Pass-through authentication**. 

19. On the **Passthrough Authentication** page, review the list of servers on which your pass-through authentication agents are installed. This should display **LON-DC1.Adatum.com**.

20. Select the **X** in the upper-right corner of the **Passthrough Authentication** page to close it. In the navigation pane on the left, select **Home** to return to the **Microsoft Entra admin center** home page.

21. Remain on LON-DC1 and leave the **Microsoft Entra admin center** open as you will use it in the next task.
   

### Task 4: Deploy Microsoft Entra Smart Lockout

Adatum’s CTO has asked you to deploy Microsoft Entra Smart Lockout, which assists in locking out bad actors who are trying to guess your users’ passwords or use brute-force methods to get admitted into your network. Smart Lockout can recognize sign-ins coming from valid users and treat them differently than sign-ins from attackers and other unknown sources. 

The CTO is anxious to implement Smart Lockout because it will lock out the attackers while letting Adatum’s users continue to access their accounts and be productive. The CTO has asked Holly to configure Smart Lockout so that users can’t use the same password more than once, and they can’t use passwords that are considered too simplistic or common. 

**Note:** You can maintain Account Lockout Policy settings in both the Group Policy Management Editor and in Microsoft Entra through its Smart Lockout feature. This lab task shows you how to access each method, although you will only update the Smart Lockout settings in Microsoft Entra. You must use the company's domain controller (LON-DC1) to access the Group Policy Management Editor. 

1. On LON-DC1, select the **Server Manager** icon on the taskbar if it’s already open; otherwise, open it now.

2. In **Server Manager**, select **Tools** in the upper-right menu bar, and in the drop-down menu, select **Group Policy Management.**

3. Maximize the **Group Policy Management** window.

4. You want to edit the group policy that includes your organization's account lockout policy. If necessary, in the root console tree in the side pane, expand **Forest:Adatum.com**, then expand **Domains**, and then expand **Adatum.com**.  <br/>

	‎Under **Adatum.com**, right-click on **Default Domain Policy** and then select **Edit** in the menu.

5. Maximize the **Group Policy Management Editor** window that appears.

6. In the **Default Domain Policy** tree in the side pane, under **Computer Configuration**, expand **Policies**, expand **Windows Settings**, expand **Security Settings**, and then expand **Account Policies.**

7. In the **Account Policies** folder, select **Account Lockout Policy**.

8. As you can see in the middle detail pane, none of the smart lockout parameters have been defined. Instead of maintaining these lockout parameters in the Group Policy Management Editor, you're instead going to use the Microsoft Entra admin center. While you can use the Group Policy Management Editor, this method is typically used in on-premises Active Directory environments. We showed you this editor so that you could see this alternative. However, for organizations that strictly use cloud-based services like Microsoft 365, or who find using the Microsoft Entra admin center much more user-friendly than accessing the Group Policy Management Editor, using the **Microsoft Entra admin center** to assign corresponding values in the Entra ID context is preferrable. <br/>  

	Also keep in mind that the lockout behavior and customization options differ between the two methods. With the Group Policy Management Editor, you have more granular control over policy settings, including Account Lockout Threshold, Lockout Duration, and Reset Account Lockout Counter After. However, using this method requires familiarity with Group Policy and Active Directory administration. Conversely, the Account Lockout Policy in Microsoft Entra can't be customized as extensively. However, it’s easier to use, even though it lacks some of the fine-tuning options available in Group Policy. <br/>

	For Adatum, Holly has chosen to use the Microsoft Entra admin center to configure the company's Account Lockout policy. ‎On the taskbar at the bottom of your screen, select the **Microsoft Edge** icon, which should be displaying the **Microsoft Entra admin center**. 

9. In the **Microsoft Entra admin center**, select **Protection** in the navigation pane, and then select **Authentication methods** 

10. In the **Authentication methods | Policies** page, in the middle pane under the **Manage** section, select **Password protection.**

11. In the **Authentication methods | Password protection** window, in the detail pane on the right, enter the following information:

	- In the **Custom smart lockout** section:

		- **Lockout threshold:** this field indicates how many failed sign-ins are allowed on an account before its first lockout. The default is 10. For testing purposes, Adatum has requested that you set this to **3**.

		- **Lockout duration in seconds:** This is the length in seconds of each lockout. The default is 60 seconds (one minute). Adatum has requested that you change this to **90** seconds.

	- In the **Custom banned passwords** section:

		- **Enforce custom list**: select **Yes**

		- **Custom banned password list:** Enter the following values (press Enter after entering each value so that each value is on a separate line):

			- **Password01**

			- **F00tball01**

			- **Se@Hawks1**

			- **Never4get!!**

	- In the **Mode** section, select **Enforced**

12. Select **Save** on the menu bar at the top of the page.

13. You should now test the banned password functionality. Select Holly Dickson's user icon in the upper right corner of the screen, and in the menu that appears select **View account**. 

14. In the **My account** window that appears, in the **Password** tile, select **CHANGE PASSWORD**.

15. A new tab will open displaying the **Change password** window. In the **Old password** field, enter Holly's existing password, which is the same **Administrative Password** provided by your lab hosting provider for the tenant admin account (i.e. the MOD Administrator account). <br/>

	Enter **Never4get!!** in the **Create new password** and **Confirm new password** fields, and then select **Submit**. Note the error message that you receive.

16. In your browser, close the **Change password** tab. 

17. You should now test the lockout threshold functionality. Select Holly Dickson's user icon in the upper right corner of the screen, and in the menu that appears select **Sign out**.  

18. Once you are signed out as Holly, the **Pick an account** window will appear in the **Sign in to Microsoft Entra** tab. As a best practice when signing out from a Microsoft online service as one user and signing back in as another, close all your browser tabs except for the **Sign out** or **Sign in** tab. In this case, close the other tabs now and leave the **Sign in** tab open.  <br/>

	In the **Pick an account** window, select **Use another account**. 

19. In the **Sign in** window, enter **laura@xxxxxZZZZZZ.onmicrosoft.com** (where xxxxxZZZZZZ is the tenant prefix assigned to you by your lab hosting provider), and then select **Next**. 

20. On the **Enter password** window, enter any random mix of letters and numbers and then select **Sign in**. Note the invalid password error message that appears. 

	Repeat this step 2 more times. 
	
	Since you set the **Lockout threshold** to **3**, you should receive an error message indicating that this account is locked after the third failed sign-in attempt. <br/>

	**Note:** If you do not receive this lockout message after the third attempt, then the system has not yet finished propagating this lockout threshold change throughout the service. It may take several minutes for the change to take effect. Wait a few minutes and then sign-in again with a bogus password. Testing of this lab has seen varying results. The change sometimes propagates almost immediately so that you get locked out after the third sign-in attempt. Other times it has taken anywhere from 5 to 10 minutes before the lockout message is displayed. Continue this process until you receive the lockout message, at which point Laura's account will be temporarily locked to prevent unauthorized access.

21. You will be prohibited from logging in again as Laura until after the **90 second lockout duration** that you set earlier. <br/>

	Once you've been locked out, wait 90 seconds and then sign back in as **laura@xxxxxZZZZZZ.onmicrosoft.com** (where xxxxxZZZZZZ is the tenant prefix assigned to you by your lab hosting provider). In the **Password** field, enter Laura's password, which is the **User Password** provided by your lab hosting provider. If required, complete the MFA sign-in process. Verify that you are able to successfully sign-in as Laura.

22. Once your log-in is successful, you can close all open applications. This will be your last lab exercise using the LON-DC1 domain controller.
 

# Proceed to Lab 4 - Exercise 2


