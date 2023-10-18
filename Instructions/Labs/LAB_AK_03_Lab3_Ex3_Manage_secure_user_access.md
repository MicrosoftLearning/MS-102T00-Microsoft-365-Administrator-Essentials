# Learning Path 3 - Lab 3 - Exercise 3 - Manage secure user access 

As Holly Dickson, Adatum’s Microsoft 365 Administrator, you have been asked by Adatum’s CTO to deploy Microsoft Entra Pass-through Authentication (PTA) and Microsoft Entra Smart Lockout as a means of strengthening password management throughout the organization. 

### Task 1: Deploy Microsoft Entra Pass-Through Authentication 

Pass-through Authentication allows users to sign-in to cloud-based services using their on-premises passwords. All user passwords are only stored locally in the on-premises domains and NEVER synchronized to the cloud. When a user signs-in, the PTA agent takes the credentials to the user's on-premises environment to verify whether the password is correct. It then sends the result back to Azure AD.   

‎Adatum's CTO wants to provide the company's users with a better sign-in experience (since PTA requires one less password to remember), as well as reduce Adatum’s IT helpdesk costs because with PTA their users are less likely to forget how to sign in. While this can also be achieved by employing Password Hash Synchronization as well as Active Directory Federation Services, Adatum has chosen to test PTA in its Microsoft 365 pilot project.

1.  You should still be logged into **LON-DC1** as the local **adatum\administrator** from the prior task.

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

21. Leave the **Microsoft Entra admin center** open as you will use it in the next task.
   

### Task 2: Deploy Azure AD Smart Lockout

Adatum’s CTO has asked you to deploy Azure AD Smart Lockout, which assists in locking out bad actors who are trying to guess your users’ passwords or use brute-force methods to get admitted into your network. Smart Lockout can recognize sign-ins coming from valid users and treat them differently than sign-ins from attackers and other unknown sources. 

The CTO is anxious to implement Smart Lockout because it will lock out the attackers while letting Adatum’s users continue to access their accounts and be productive. The CTO has asked Holly to configure Smart Lockout so that users can’t use the same password more than once, and they can’t use passwords that are considered too simplistic or common. 

1. On LON-DC1, select the **Server Manager** icon on the taskbar if it’s already open; otherwise, open it now.

2. In **Server Manager**, select **Tools** in the upper-right menu bar, and in the drop-down menu, select **Group Policy Management.**

3. Maximize the **Group Policy Management** window.

4. You want to edit the group policy that includes your organization's account lockout policy. If necessary, in the root console tree in the left-hand pane, expand **Forest:Adatum.com**, then expand **Domains**, and then expand **Adatum.com**.  <br/>

	‎Under **Adatum.com**, right-click on **Default Domain Policy** and then select **Edit** in the menu.

5. Maximize the **Group Policy Management Editor** window that appears.

6. In the **Default Domain Policy** tree in the left-hand pane, under **Computer Configuration**, expand **Policies**, expand **Windows Settings**, expand **Security Settings**, and then expand **Account Policies.**

7. In the **Account Policies** folder, select **Account Lockout Policy**.

8. As you can see in the right-hand pane, none of the smart lockout parameters have been defined. You are going to use the **Microsoft Entra admin center** to assign corresponding values in the Entra ID context.  

9. ‎Select the Edge browser icon on the taskbar, which should be displaying the **Microsoft Entra admin center**. 

9. In the **Microsoft Entra admin center**, in the left-hand navigation pane, select **Authentication methods** under the **Protection** submenu.

12. In the **Authentication methods | Policies** page, in the middle pane under the **Manage** section, select **Password protection.**

13. In the **Authentication methods | Password protection** window, in the detail pane on the right, enter the following information:

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

14. Select **Save** on the menu bar at the top of the page.

15. You should now test the banned password functionality. Select Holly Dickson's user icon in the upper right corner of the screen, and in the menu that appears select **Change password**.

16. A new tab will open displaying the **Change password** window. In the **Old password** field, enter Holly's existing password, which is the same **Microsoft 365 Tenant Password** provided by your lab hosting provider for the tenant admin account (i.e. the MOD Administrator account). <br/>

	Enter **Never4get!!** in the **Create new password** and **Confirm new password** fields, and then select **Submit**. Note the error message that you receive.

17. In your browser, close the **Change password** tab. 

18. You should now test the lockout threshold functionality. In the **Authentication methods - Azure Active Directory admin center** tab, select Holly Dickson's user icon in the upper right corner of the screen, and in the menu that appears select **Sign out**.  

19. Once you are signed out as Holly, the **Pick an account** window will appear in the **Sign in to Microsoft Azure** tab. As a best practice when signing out from a Microsoft online service as one user and signing back in as another, close all your browser tabs except for the **Sign out** or **Sign in** tab. In this case, close the other tabs now and leave the **Sign in** tab open.  <br/>

	In the **Pick an account** window, select **Use another account**. 

20. In the **Sign in** window, enter **laura@xxxxxZZZZZZ.onmicrosoft.com** (where xxxxxZZZZZZ is the tenant prefix assigned to you by your lab hosting provider), and then select **Next**. 

21. On the **Enter password** window, enter any random mix of letters and then select **Sign in**. Note the invalid password error message that appears. 

	Repeat this step 2 more times. 
	
	Since you set the **Lockout threshold** to **3**, you should receive an error message indicating that your account is locked after your third failed sign-in attempt. <br/>

	**User:** If you do not receive this lockout message after the third attempt, then the system has not yet finished propagating this lockout threshold change throughout the service. It may take several minutes for the change to take effect. Wait a few minutes and then sign-in again with a bogus password. Testing of this lab has seen varying results. The change sometimes propagates almost immediately so that you get locked out after the third sign-in attempt. Other times it has taken anywhere from 5 to 10 minutes before the lockout message is displayed. Continue this process until you receive the lockout message, at which point Laura's account will be temporarily locked to prevent unauthorized access.

22. You will be prohibited from logging in again as Laura until after the **90 second lockout duration** that you set earlier. <br/>

	Once you've been locked out, wait 90 seconds and then sign back in as **laura@xxxxxZZZZZZ.onmicrosoft.com** (where xxxxxZZZZZZ is the tenant prefix assigned to you by your lab hosting provider). In the **Password** field, enter Laura's password, which is the same **Microsoft 365 Tenant Password** provided by your lab hosting provider for the tenant admin account (i.e. the MOD Administrator account). Verify that you are able to successfully sign-in as Laura.

23. Once your log-in is successful, you can close all open applications. This will be your last lab exercise using the LON-DC1 domain controller.
 

# End of Lab 3


