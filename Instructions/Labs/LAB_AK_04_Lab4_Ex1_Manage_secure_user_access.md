# Learning Path 4 - Lab 4 - Exercise 1 - Manage secure user access 

**IMPORTANT MFA NOTIFICATION:** Due to a recent change by Microsoft to the Microsoft 365 trial tenants used in this course, we had to make a corresponding change to this lab. <br/>

**Original lab design:** This lab exercise was originally designed so that as Holly Dickson, you created a Conditional Access policy that enabled MFA at Adatum in Task 1. This is the recommended method of enabling MFA, as you learned in the lecture portion of this training. In task 1, you created a Conditional Access policy that enabled MFA for all users, EXCEPT for those who were members of the Microsoft 365 pilot project group that you created in an earlier exercise. To test your policy in Task 2, it then had you log in as a Adele Vance. Because Adele was not a member of the pilot project group, you had to complete the MFA process to sign-in to Microsoft 365. You then signed out as Adele and signed back in as Holly Dickson. Since Holly is a member of the Microsoft 365 pilot project group, she only had to enter her username and password. She did not have to perform a second form of authentication using MFA. These two steps in Task 2 verified your Conditional Access policy - i.e.  only users who were not part of the pilot project group had to use MFA. 

The other ramification of this policy is that you didn't have to use MFA when signing in to the remainder of the labs as the other test users who were also members of the Microsoft 365 pilot project group. While exclusions from MFA can be set for practical reasons depending on a company's business needs, companies should carefully assess the associated risks and apply exclusions sparingly, always aiming to align with security best practices. This lab had you create the pilot project group exclusion for two reasons - so that you could learn how to build an exclusion into a Conditional Access policy, but also as a means of saving time in the training labs when signing in as each test user. <br/>

**Microsoft tenant change:** That being said, Microsoft has since created a Conditional Access policy in the Microsoft 365 trial tenant used in this lab that requires MFA for all user accounts. Unfortunately, Microsoft's Conditional Access policy takes precedence over the Conditional Access policy that you will create in this lab that excludes a specific group. Conditional Access policies in Microsoft Entra are evaluated together, and the highest priority policy that applies to a user is enforced. If there are multiple policies with the same priority, which is the case here, the most restrictive policy applies. In this case, Microsoft's policy is more restrictive than the policy you create, since yours includes user exceptions. <br/>

**Impact on this lab exercise:** Even though Microsoft enforces MFA in this trial tenant through a Conditional Access policy, you will still create your own Conditional Access policy as originally designed in Task 1. The task has been modified slightly from its original version so that you can see the policy that Microsoft built into the trial tenant. But other than that, the policy that you will create has not changed from its original design - it requires MFA for all users, except for the members of the Microsoft 365 pilot project group. However, since the policy that Microsoft built into the lab's trial tenant is the more restrictive of the two policies, that policy takes precedence during enforcement. There are two implications of this scenario. First, Microsoft's policy requires you to use MFA when signing in as each test user through the remainder of these labs. Second, because Microsoft Entra will ignore your policy, there's no point in testing it. As such, we removed the original Task 2 that tested the Conditional Access policy that you created. Now even though you can't test your policy, we still want you to create it in Task 1 so that you gain that experience for your real-world deployments. 


### Task 1: Deploy MFA using a Conditional Access policy

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

10. Note that Microsoft selected the **Directory roles** checkbox. Select the field below this option. In the menu of roles that you can choose to exclude from MFA, the only role that Microsoft selected is **Directory Synchronization Accounts**. This role is used for accounts that are responsible for synchronizing directories between on-premises Active Directory and Microsoft Entra ID. These accounts are typically configured with a long complex password that doesn't expire, and they're granted a special role that has only permissions to perform directory synchronization tasks. <br/>

	Microsoft doesn't require MFA for this role because the synchronization service needs to run continuously without any interruptions that could be caused by MFA prompts. Additionally, these accounts are usually configured with very limited permissions and aren't used for interactive sign-ins, which reduces the security risk. In addition, the synchronization process doesn't support the additional authentication steps required by MFA.  <br/>

	As with the prior step where you tried to change the MFA setting to include no users or selected users, if you try to select other roles to get around the MFA setting, you will experience the same error indicating **Failed to update Multifactor authentication for Microsoft partners and vendors** when you try to save the policy. Microsoft's security firewall doesn't allow any change to this Conditional Access policy that affects those who must use MFA.

11. If you still have the **Multifactor authentication for Microsoft partners and vendors** page open, then select the **X** in the upper corner to close it and return back to the **Conditional Access | Policies** page. Or if you tried saving a change to the policy, your attempt will have failed, and you should already be back on the **Conditional Access | Policies** page.

12. On the **Conditional Access | Policies** page, on the menu bar at the top of the page, select **+New policy**.

13. On the **New Conditional Access policy** window, enter **MFA for all Microsoft 365 users** in the **Name** field.

14. You will begin by defining the MFA requirement for users. Under the **Users** group, select **0 users and groups selected**. Doing so displays two tabs - **Include** and **Exclude**.

15. Under the **Include** tab, select **All users**. Note the warning message that appears. You will address this in the next two steps.

16. Select the **Exclude** tab. To avoid system lockout, as the prior warning message indicated, you want to exclude your Global administrators - in this case, Holly. Holly also wants to exclude the other Microsoft 365 pilot project group members for the sake of expediency when testing. Once Microsoft 365 goes live, Holly will remove the pilot project group from the Exclude list in this Conditional Access policy and simply exclude herself and several other Global admins. But for now, Holly wants to exclude the entire group. <br/>

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

**Note:** As per the earlier discussion, there's no way to test your Conditional Access policy in the current Microsoft 365 trial tenant. Microsoft's Conditional Access policy requires MFA for all users. When you have multiple policies requiring MFA, the most restrictive policy applies. In this case, Microsoft's policy is more restrictive than the one you just created that included exceptions for the pilot project group members. Even though you can't test your policy using this trial tenant, we encourage you to use this experience of creating a Conditional Access policy to require MFA in your real-world Microsoft 365 deployments.


### Task 2: Deploy Microsoft Entra Pass-Through Authentication 

Pass-through Authentication allows users to sign-in to cloud-based services using their on-premises passwords. All user passwords are only stored locally in the on-premises domains and NEVER synchronized to the cloud. When a user signs-in, the PTA agent takes the credentials to the user's on-premises environment to verify whether the password is correct. It then sends the result back to Microsoft Entra ID (formerly Azure AD).   

‎Adatum's CTO wants to provide the company's users with an improved sign-in experience (since PTA requires one less password to remember), as well as reduce Adatum’s IT helpdesk costs because with PTA their users are less likely to forget how to sign in. While this can also be achieved by employing Password Hash Synchronization as well as Active Directory Federation Services, Adatum has chosen to test PTA in its Microsoft 365 pilot project.

1.  In this task, you will be working from Adatum's domain controller, LON-DC1. <br/>

	Switch to **LON-DC1**.

2. On LON-DC1, select the **Start** button on the taskbar, and then in the **Start** menu, select the **All Apps** icon to display the list of all installed applications. Select the **Azure AD Connect** program group and then select **Azure AD Connect**. This will initiate the **Microsoft Azure Active Directory Connect** wizard.

3. In the **Welcome to Azure AD Connect** window, you will receive a page indicating the synchronization service scheduler is suspended until this setup wizard is closed. This is because if you start the Azure AD Connect installation wizard (which you did in an earlier task), then the scheduler is temporarily suspended. Select **Configure.**

4. On the **Additional tasks** page, select the **Change user Sign-in** task and then select **Next**. 

5. On the **Connect to Azure AD** page, sign into Azure AD (Microsoft Entra ID). The **USERNAME** field is already filled with **Holly@xxxUPNxxx.onmicrosoft.com**. In the **PASSWORD** field, enter the same **Microsoft 365 Tenant Password** provided by your lab hosting provider for the tenant admin account (i.e. the MOD Administrator account), and then select **Next**.

6. On the **User sign-in** page, under **Select the Sign On method**, select **Pass-through authentication** and then select **Next**. 

7. On the **Enable single sign-on** page, select **Enter credentials**. 

8. In the **Forest Credentials** dialog box, enter **Adatum\Administrator** as the **User name** and **Pa55w.rd** as the **Password**, and then select **OK**. 

9. When the credentials are verified, a check mark will appear to the right of the **Enter credentials** button. Select **Next**. 

10. On the **Ready to configure** page, leave the check box selected for the **Start the synchronization process when configuration completes** option (if the check box is not selected, then select it now). Select **Configure**. It may take a minute or so for the configuration to complete.

11. On the **Configuration complete** page, note the message indicating the current sign on method for Azure AD is PTA. Select **Exit**. Pass-Through Authentication has now been enabled. 

12. To verify that Pass-Through Authentication is successfully enabled, select the **Microsoft 365 admin center** tab in your Edge browser. In the left-hand navigation pane, under **Admin centers**, select **Identity**.

13. This opens the **Microsoft Entra admin center**. In the left-hand navigation pane, select **Show more**. This displays additional feature groups. Select **Hybrid management** to expand this group, and then select **Microsoft Entra Connect**. 

17. On the **Microsoft Entra Connect | Get started** page, in the middle navigation pane, select **Connect Sync**.

18. On the **Microsoft Entra Connect | Connect Sync** page, in the detail pane on the right, under the **USER SIGN-IN** section, verify that the status of **Pass-through authentication** is **Enabled**, and then select **Pass-through authentication**. 

19. On the **Passthrough Authentication** page, review the list of servers on which your pass-through authentication agents are installed. This should display **LON-DC1.Adatum.com**.

20. Select the **X** in the upper-right corner of the **Passthrough Authentication** page to close it. In the navigation pane on the left, select **Home** to return to the **Microsoft Entra admin center** home page.

21. Remain on LON-DC1 and leave the **Microsoft Entra admin center** open as you will use it in the next task.
   

### Task 3: Deploy Microsoft Entra Smart Lockout

Adatum’s CTO has asked you to deploy Microsoft Entra Smart Lockout, which assists in locking out bad actors who are trying to guess your users’ passwords or use brute-force methods to get admitted into your network. Smart Lockout can recognize sign-ins coming from valid users and treat them differently than sign-ins from attackers and other unknown sources. 

The CTO is anxious to implement Smart Lockout because it will lock out the attackers while letting Adatum’s users continue to access their accounts and be productive. The CTO has asked Holly to configure Smart Lockout so that users can’t use the same password more than once, and they can’t use passwords that are considered too simplistic or common. 

**Note:** You can maintain Account Lockout Policy settings in both the Group Policy Management Editor and in Microsoft Entra through its Smart Lockout feature. This lab task shows you how to access each method, although you will only update the Smart Lockout settings in Microsoft Entra. You must use the company's domain controller (LON-DC1) to access the Group Policy Management Editor. 

1. On LON-DC1, select the **Server Manager** icon on the taskbar if it’s already open; otherwise, open it now.

2. In **Server Manager**, select **Tools** in the upper-right menu bar, and in the drop-down menu, select **Group Policy Management.**

3. Maximize the **Group Policy Management** window.

4. You want to edit the group policy that includes your organization's account lockout policy. If necessary, in the root console tree in the left-hand pane, expand **Forest:Adatum.com**, then expand **Domains**, and then expand **Adatum.com**.  <br/>

	‎Under **Adatum.com**, right-click on **Default Domain Policy** and then select **Edit** in the menu.

5. Maximize the **Group Policy Management Editor** window that appears.

6. In the **Default Domain Policy** tree in the left-hand pane, under **Computer Configuration**, expand **Policies**, expand **Windows Settings**, expand **Security Settings**, and then expand **Account Policies.**

7. In the **Account Policies** folder, select **Account Lockout Policy**.

8. As you can see in the right-hand pane, none of the smart lockout parameters have been defined. Instead of maintaining these lockout parameters in the Group Policy Management Editor, you're instead going to use the Microsoft Entra admin center. While you can use the Group Policy Management Editor, this method is typically used in on-premises Active Directory environments. We showed you this editor so that you could see this alternative. However, for organizations that strictly use cloud-based services like Microsoft 365, or who find using the Microsoft Entra admin center much more user-friendly than accessing the Group Policy Management Editor, using the **Microsoft Entra admin center** to assign corresponding values in the Entra ID context is preferrable. <br/>  

	Also keep in mind that the lockout behavior and customization options differ between the two methods. With the Group Policy Management Editor, you have more granular control over policy settings, including Account Lockout Threshold, Lockout Duration, and Reset Account Lockout Counter After. However, using this method requires familiarity with Group Policy and Active Directory administration. Conversely, the Account Lockout Policy in Microsoft Entra can't be customized as extensively. However, it’s easier to use, even though it lacks some of the fine-tuning options available in Group Policy. <br/>

	For Adatum, Holly has chosen to use the Microsoft Entra admin center to configure the company's Account Lockout policy. ‎On the taskbar at the bottom of your screen, select the **Microsoft Edge** icon, which should be displaying the **Microsoft Entra admin center**. 

9. In the **Microsoft Entra admin center**, in the left-hand navigation pane, select **Authentication methods** under the **Protection** submenu.

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

20. On the **Enter password** window, enter any random mix of letters and then select **Sign in**. Note the invalid password error message that appears. 

	Repeat this step 2 more times. 
	
	Since you set the **Lockout threshold** to **3**, you should receive an error message indicating that this account is locked after the third failed sign-in attempt. <br/>

	**Note:** If you do not receive this lockout message after the third attempt, then the system has not yet finished propagating this lockout threshold change throughout the service. It may take several minutes for the change to take effect. Wait a few minutes and then sign-in again with a bogus password. Testing of this lab has seen varying results. The change sometimes propagates almost immediately so that you get locked out after the third sign-in attempt. Other times it has taken anywhere from 5 to 10 minutes before the lockout message is displayed. Continue this process until you receive the lockout message, at which point Laura's account will be temporarily locked to prevent unauthorized access.

21. You will be prohibited from logging in again as Laura until after the **90 second lockout duration** that you set earlier. <br/>

	Once you've been locked out, wait 90 seconds and then sign back in as **laura@xxxxxZZZZZZ.onmicrosoft.com** (where xxxxxZZZZZZ is the tenant prefix assigned to you by your lab hosting provider). In the **Password** field, enter Laura's password, which is the **User Password** provided by your lab hosting provider. If required, complete the MFA sign-in process. Verify that you are able to successfully sign-in as Laura.

22. Once your log-in is successful, you can close all open applications. This will be your last lab exercise using the LON-DC1 domain controller.
 

# Proceed to Lab 4 - Exercise 2


