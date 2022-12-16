# Learning Path 3 - Lab 3 - Exercise 3 - Manage secure user access 

As Holly Dickson, Adatum’s Microsoft 365 Administrator, you have been asked by Adatum’s CTO to deploy Pass-through Authentication (PTA) and Azure AD Smart Lockout as a means of strengthening password management throughout the organization. 

### Task 1: Deploy Azure AD Pass-Through Authentication 

Pass-through Authentication allows users to sign-in to cloud-based services using their on-premises passwords. All user passwords are only stored locally in the on-premises domains and NEVER synchronized to the cloud. When a user signs-in, the PTA agent takes the credentials to your on-premises environment to verify whether the password is correct. It then sends the result back to Azure AD.   

‎Adatum's CTO wants to provide the company's users with a better logon experience (since PTA requires one less password to remember), as well as reduce Adatum’s IT helpdesk costs because with PTA their users are less likely to forget how to sign in. While this can also be achieved by employing Password Hash Synchronization as well as Active Directory Federation Services, Adatum has chosen to test PTA in its pilot project.

1.  You should still be logged into **LON-DC1** as the **Administrator** from the prior task.

2. On LON-DC1, select the **Start** button on the taskbar, and then in the **Start** menu, select the **All Apps** icon to display the list of all installed applications. Select the **Azure AD Connect** program group and then select **Azure AD Connect**. This will initiate the **Microsoft Azure Active Directory Connect** wizard.

3. In the **Welcome to Azure AD Connect** window, you will receive a page indicating the synchronization service scheduler is suspended until this setup wizard is closed. This is because if you start the Azure AD Connect installation wizard (which you did in an earlier task), then the scheduler is temporarily suspended. Select **Configure.**

4. On the **Additional tasks** page, select the **Change user Sign-in** task and then select **Next**. 

5. On the **Connect to Azure AD** page, sign into Azure AD. The **USERNAME** field is already filled with **Holly@xxxUPNxxx.xxxCustomDomainxxx.xxx.** Enter **User.pw1** in the **PASSWORD** field, and then select **Next**.

6. On the **User sign-in** page, under **Select the Sign On method**, select **Pass-through authentication** and then select **Next**. 

7. On the **Enable single sign-on** page, select **Enter credentials**. 

8. In the **Forest Credentials** dialog box, enter **adatum\administrator** as the **User name** and **Pa55w.rd** as the **Password**, and then select **OK**. 

9. When the credentials are verified, a check mark will appear to the right of the **Enter credentials** button. Select **Next**. 

10. On the **Ready to configure** page, select **Configure**. 

11. On the **Configuration complete** page, select **Exit**. Pass-Through Authentication has now been enabled. 

12. To verify that Pass-Through Authentication is successfully enabled, select a new tab in your Edge browser and enter the following URL in the address bar: **https://aad.portal.azure.com**

13. This opens the **Azure Active Directory admin center**. In the navigation pane, select **Azure Active Directory**. 

14. On the **Azure Active Directory admin center** page, in the left-hand navigation pane, select **All services**.

15. On the **All services** page, three groups are displayed - General, Identity, and Security. Under the **Identity** group, select **Azure Active Directory**. 

16. On the **Adatum Corporation | Overview** page, in the middle navigation pane under the **Manage** section, select **Azure AD Connect**.

17. On the **Adatum Corporation | Azure AD Connect** page, in the detail pane on the right, under the **USER SIGN IN** section, verify that the status of **Pass-through authentication** is **Enabled**, and then select **Pass-through authentication**. 

18. On the **Pass-through authentication** page, review the list of servers on which your pass-through authentication agents are installed. This should display **LON-DC1.Adatum.com**.

19. Select the **X** in the upper-right corner of the **Pass-through authentication** page to close it, and then do the same to close the **Adatum Corporation | Azure AD Connect** page. You should now be back to the **All services** page in the **Azure Active Directory admin center**.

20. Leave the **Azure Active Directory admin center** open as you will use it in the next task.
   

### Task 2: Deploy Azure AD Smart Lockout

Adatum’s CTO has asked you to deploy Azure AD Smart Lockout, which assists in locking out bad actors who are trying to guess your users’ passwords or use brute-force methods to get admitted into your network. Smart Lockout can recognize sign-ins coming from valid users and treat them differently than sign-ins from attackers and other unknown sources. 

The CTO is anxious to implement Smart Lockout because it will lock out the attackers while letting Adatum’s users continue to access their accounts and be productive. The CTO has asked Holly to configure Smart Lockout so that users can’t use the same password more than once, and they can’t use passwords that are considered too simplistic or common. 

1. On LON-DC1, select the **Server Manager** icon on the taskbar if it’s already open; otherwise, open it now.

2. In **Server Manager**, select **Tools** in the upper-right menu bar, and in the drop-down menu, select **Group Policy Management.**

3. Maximize the **Group Policy Management** window.

4. You want to edit the group policy that includes your organization's account lockout policy. If necessary, in the root console tree, expand **Forest:Adatum.com**, then expand **Domains**, and then expand **Adatum.com**.  <br/>

	‎Under **Adatum.com**, right-click on **Default Domain Policy** and then select **Edit** in the menu.

5. Maximize the **Group Policy Management Editor** window that appears.

6. In the **Default Domain Policy** tree in the left-hand pane, under **Computer Configuration**, expand **Policies**, expand **Windows Settings**, expand **Security Settings**, and then expand **Account Policies.**

7. In the **Account Policies** folder, select **Account Lockout Policy**.

8. As you can see in the right-hand pane, none of the smart lockout parameters have been defined. You are going to use the **Azure AD admin center** to assign these values.   <br/>

	‎Select the Edge browser icon on the taskbar, which should be displaying the **All services** tab in the **Azure Active Directory admin center**. 

9. In the **Azure Active Directory admin center**, in the left-hand navigation pane, select **Azure Active Directory**.

10. In the **Adatum Corporation | Overview** page, in the middle navigation pane under the **Manage** section, scroll down and select **Security**.

11. In the **Security | Getting started** window, in the middle pane under the **Manage** section, select **Authentication Methods**.

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

16. A new tab will open displaying the **change password** window. Enter **User.pw1** in the **Old password** field, enter **Never4get!!** in the **Create new password** and **Confirm new password** fields, and then select **Submit**. Note the error message that you receive.

17. In your browser, close the **Change password** tab. 

18. You should now test the lockout threshold functionality. In the **Authentication methods - Azure Active Directory admin center** tab, select Holly Dickson's user icon in the upper right corner of the screen, and in the menu that appears select **Sign out**. 

19. Once you are signed out as Holly, the **Pick an account** window will appear. Select **Use another account**. 

20. In the **Sign in** window, enter **laura@xxxxxZZZZZZ.onmicrosoft.com** (where xxxxxZZZZZZ is the tenant prefix assigned to you by your lab hosting provider), and then select **Next**. 

21. On the **Enter password** window, enter any mix of letters and then select **Sign in**. Note the invalid password error message. 

	Repeat this step 2 more times. 
	
	Since you set the **Lockout threshold** to **3**, you should receive an error message indicating that your account is locked. <br/>

	**Note:** If you do not receive this lockout message after the third attempt, then the system has not yet finished propagating this lockout threshold change throughout the service. It may take several minutes for the change to take effect. Wait a few minutes and then sign-in again with a bogus password. Testing of this lab has seen varying results. The change sometimes propagates almost immediately so that you get locked out after the third sign-in attempt. Other times it has taken anywhere from 5 to 10 minutes before the lockout message is displayed. Continue this process until you receive the lockout message, at which point Laura's account will be temporarily locked to prevent unauthorized access. <br/>

	**Note:** You will be prohibited from logging in as Laura until after the **90 second lockout duration** that you set earlier. 

22. Once you've been locked out, wait 90 seconds and then verify that you can sign back in as **laura@xxxxxZZZZZZ.onmicrosoft.com** (where xxxxxZZZZZZ is the tenant prefix assigned to you by your lab hosting provider) and the password **User.pw1**. 

23. Once your log-in is successful, you can close all open applications. This will be your last lab exercise using the LON-DC1 domain controller.
 

# End of Lab 3


