### Task 2 – Validate the Mailbox Permission Alert

In the prior task, you configured an alert that will notify Lynne Robbins when FullAccess permissions are granted to any mailbox within Adatum. To test this alert, Holly Dickson will change the FullAccess permission on Alex Wilber’s mailbox by granting Joni Sherman FullAccess to his mailbox. This activity should trigger the alert policy that you just created, which should send an alert notification email to Lynne Robbins’ mailbox. You will then log into LON-CL2 as Lynne Robbins and see if she received this email. 

1. On LON-CL1, in your Edge browser, you should still be logged into Microsoft 365 as **Holly Dickson**. 

2. In your Edge browser, select the **Microsoft 365 admin center** tab, and then in the left-hand navigation pane, under the **Admin centers** group, select **Exchange**. This opens the Exchange admin center for Exchange Online.

3. In the **Exchange admin center**, the **Manage Mailboxes** window appears by default (if it doesn't, then in the left-hand navigation pane, under the **Recipients** group, select **Mailboxes**). 

4. In the **Manage Mailboxes** window, select **Alex Wilber** from the list of mailboxes (select Alex's name; do not select the check box to the left of his name).

5. In the **Alex Wilber** pane that appears, the **General** tab is displayed by default. Select the **Delegation** tab.

6. On the **Delegation** tab, there are three mailbox permissions that can be updated: **Send as**, **Send on behalf**, and **Read and manage (Full Access)**. You want to add each of these permissions for Alex's mailbox to **Joni Sherman**. For each permission, perform the following steps to add Joni to that permission: <br/>

	- Select the **Edit** button for the permission. 
	- On the **Manage mailbox delegation** pane, select **+Add members**.
	- In the list of users that appears, select the check box for **Joni Sherman** and then select **Save**.
	- In the **Add delegate permissions?** pane, select **Confirm**.
	- Once the mailbox permission is added to Alex's mailbox, select the back arrow at the top of the pane. 
	- This returns you to the **Delegation** tab on the **Alex Wilber** pane, which displays the three permissions. Repeat these steps for each of the two remaining permissions. 

7. Once you have assigned Joni to each of the three permissions on the **Delegation** tab, select the **X** in the upper right-hand corner to close the **Alex Wilber** pane. 

8. Since **Holly Dickson** has changed the mailbox permissions for Alex Wilber by giving Joni Sherman full access permissions to his mailbox, an alert email should automatically be sent to Lynne Robbins’ Inbox that notifies her of this event. You will verify this email was sent by checking Lynne's Inbox on LON-CL2. <br/>

	‎Switch to **LON-CL2**. 

9. On **LON-CL2**, you should be signed into the machine as the local **administrator** (lon-cl2\admin) account. Select the **Microsoft Edge** icon in the taskbar, maximize the window (if necessary), and then enter the following URL in the address bar: **https://outlook.office365.com**

10. In the **Pick an account** window, if Lynne Robbins account (**LynneR@xxxxxZZZZZZ.onmicrosoft.com**) appears in the user list, then select it now; otherwise, select **Use another account** and sign in as **LynneR@xxxxxZZZZZZ.onmicrosoft.com** (where xxxxxZZZZZZ is the tenant prefix provided by your lab hosting provider). Then enter the same **Microsoft 365 Tenant Password** provided by your lab hosting provider for the tenant admin account (i.e. the MOD Administrator account) as Lynne's password.

11. Lynne Robbins’ **Inbox** should include an email from the Alerts notification system (**Office365Alerts@microsoft.com**) to let her know that Holly Dickson has made a Mailbox permission change. <br/>

	**WARNING:** Lab testing has shown that in some cases, it can take up to 15 minutes or so for the email to be received in Lynne's Inbox. You may need to refresh Outlook one or more times until you receive the email.

12. Once the notification email arrives in Lynne's Inbox, open the email and review the contents. Scroll to the bottom of the email and select the **View alert details** button. This opens the **Microsoft Defender** portal in a new tab.

13. The **Microsoft Defender** portal displays the **Alerts** window, and it automatically opens the **Mailbox permission change** pane for this alert activity that triggered the email notification to Lynne. <br/>

	Scroll down through the **Mailbox permission change** pane and review all the information for this activity. When you are done, select **Close** to close the pane.

14. In your Edge browser, close the **View Alerts - Microsoft 365 security** tab. Leave Lynne's **Outlook** tab open, as you will use that in the next lab exercise.


You have just successfully tested a mailbox permission alert that sent an alarm message on granting FullAccess to a user mailbox.


### Task 2 – Validate the  SharePoint Permissions Alert

In the prior task, you configured an alert that will notify Lynne Robbins when a user is added as a site collection administrator for a site collection. To test this alert, Holly Dickson will add Alex Wilber as a site collection admin to the global SharePoint Communication site. This activity should trigger the alert policy that you just created, which should send an alert notification email to Lynne Robbins’ mailbox. You will then switch to the LON-CL2 VM to see if Lynne received this email. 

1. On LON-CL1, in your Edge browser, you should still be logged into Microsoft 365 as **Holly Dickson**. 

2. In your **Microsoft Edge** browser, open a new tab and enter the following URL in the address bar: **https://xxxxxZZZZZZ.sharepoint.com/_layouts/15/settings.aspx** (replace xxxxxZZZZZZ with the tenant prefix provided by your lab hosting provider). This opens the **Site Settings** for the global SharePoint Communication site.

3. On the **Site Settings** window, under the **Users and Permissions** section, select **Site permissions**. 

4. In the ribbon at the top of the page, the **Permissions** tab is displayed by default. Under the **Manage** group, select **Site Collection Administrators**.

5. In the **Site Collection Administrators** dialog box, the Global administrator account that was assigned by default to this role group is displayed in the data entry field. To the right of this account, enter **Alex**, select **Alex Wilber** from the list of users that appears, and then select **OK**. 

6. Since a new site collection admin has been added, an alert should automatically be sent to Lynne Robbins’ Inbox notifying her of this event. Perform the remaining steps to verify that Lynne received this email. You will verify whether this alert was sent to Lynne's mailbox on LON-CL2.

	‎Switch to **LON-CL2**. 

7. On **LON-CL2**, you should still be logged into **Outlook on the web** as **Lynne Robbins** from the prior task. Monitor Lynne's Inbox to view the email generated by the alert that you just created. <br/>

	**Note:** Lab testing has shown that in some cases, it can take up to 15 minutes or so for the email to be received in Lynne's Inbox. Do not proceed until the email has arrived.

8. Once the email arrives in Lynne's Inbox, open the email and review the contents. Scroll to the bottom of the email and select the **View alert details** button. This opens the **Microsoft Defender** portal in a new tab.

9. The **Microsoft Defender** portal displays the **Alerts** window, and it automatically opens the **Site collection admin permissions** pane for this alert activity that triggered the email notification to Lynne. <br/>

	Scroll down through the **Site collection admin permissions** pane and review all the information for this alert activity. When you are done, select **Close** to close the pane.

10. Leave your LON-CL1 and LON-CL2 VMs open for the remaining exercise in this lab.

You have now successfully tested the SharePoint alert to monitor site collection admin permissions on SharePoint sites. 

### Task 2 – Validate the default eDiscovery Alert

To test this default alert, Holly Dickson will create an eDiscovery search. This activity should trigger the alert policy, which should send an alert notification email to all Tenant Admins. Holly is a Global admin, who by default are members of the Tenant Admin group; therefore, she should receive the email notification generated by this alert. 

1. On LON-CL1, in your Edge browser, you should still be logged into Microsoft 365 as **Holly Dickson**. 

2. In your **Microsoft Edge** browser, select the **Microsoft 365 admin center** tab. 

3. In the **Microsoft 365 admin center**, in the left-hand navigation pane under the **Admin centers** group, select **Compliance**.

4. In the **Microsoft Purview** portal, in the left-hand navigation pane, under the **Solutions** group, select **Content search**.

5. The **Content search** window has two tabs - a **Search** tab and an **Export** tab. The **Search** tab is displayed by default. Select the **+New search** option that appears on the menu bar. This initiates the **New search** wizard.

6. In the **New search** wizard, on the **Name and description** page, enter **Confidential search** in the **Name** field and then select **Next**.

7. In the **Locations** page, the **Specific locations** option is selected by default. There are three groups of locations under this option, each of which can be turned On or Off through its respective toggle switch. Turn the toggle switch **On** for **Exchange mailboxes**, but leave the toggle switches **Off** for the other two locations. 

	**Note:** The **Included** setting is set to **All** by default. This value indicates that all mailboxes will be included in the search. In a real-world deployment, you can optionally select **Choose users, groups, or teams** to choose specific mailboxes if you wish. For this lab, leave the value set to **All** so that it searches all mailboxes.

	**Warning:** At least one of the three locations must be set to **On**; otherwise, you will receive an error.  

8. Select **Next**. <br/>

9. In the **Define your search conditions** page, enter **Confidential** in the **Enter keywords** field and then select **Next**.

10. In the **Review your search and create it** page, review the settings and edit any (if necessary) to make any corrections. Once all the search settings are correct, select **Submit**. 

11. On the **New search created** page, select **Done**.

12. On the **Content search** page, scroll to the far-right side of the page. Note the **Status** of the **Confidential search** is **Starting**. <br/>

	**Important:** When you submit a new search, the system saves the search and then immediately runs it. By saving this eDiscovery search, the eDiscovery alert should be triggered, thereby creating an email notification that should be sent to the Inbox of all users with Tenant Admin permissions. You do NOT have to wait for the Search to finish before testing whether the alert sent the email notification. The alert notification system will process the email at the time the search is created. 
	
13. The search that you created should only take a couple of minutes to complete. You can either proceed to the next step while the search is running, or if you wish, you can select the **Refresh** icon on the menu bar every minute or so until the **Status** changes to **Completed**.
	
14. To test this alert, select the **Outlook** tab in your Edge browser. This should still be displaying Holly's mailbox. If you previously closed Outlook, then in the **Home | Microsoft 365** tab, in the column of application icons, select **Outlook**.

15. In Holly's Outlook mailbox, monitor her Inbox for an **Informational-severity alert: eDiscovery search started or exported** email that was automatically sent by the Alerts notification system. The purpose of this message is to inform Holly that an eDiscovery search was created or exported. If necessary, select the **Refresh** icon to the left of the URL address. Once the email is received, open it and review the contents, then close the message. <br/>

	**Note:** It may take up to 10 minutes or so before the email arrives in Holly's Inbox.

16. In your **Edge** browser, switch back to the **Microsoft Purview** portal (the **Content search - Microsoft Purview** tab) and under the **Solutions** group in the left-hand navigation pane, select **Audit**. 

17. Select the **Search** button to display all recent activity. This will display the activity that created this alert. If an **Add more filters to your search?** dialog box appears, select **Start search**. <br/>

	**Note:** It may take up to 24 hours for the search results to be displayed. If search results do not appear immediately, check again later in the day. If there are still no results, wait until the following day before checking again.

	**Note:** In the list of search results, note how the **User** for the prior alerts is listed as Holly, while the user for the eDiscovery alert is listed as **Service Account**. This is because the eDiscovery alert is a default system alert rather than a custom alert created by an individual user.

18. In your browser, leave the Outlook tab (**Mail - Holly Dickson - Outlook**) open as you will use it shortly in another lab exercise. Leave all your other browser tabs open as well.

You have now successfully tested the Microsoft 365 eDiscovery system alert that monitors the creation of an eDiscovery search or the export of data from a completed search.


### Task 3: Review the attack simulation results

In this task, you will verify whether Adatum has received the email that you configured in the Attack simulation training. You will then review the diagnostic feedback associated with the Spear Phishing attack that you simulated.

1. Switch to **LON-CL2**, where you should be logged into the machine as the local **adatum\administrator** account.

2. On LON-CL2, open your Edge browser and enter the following URL in the address bar: **https://outlook.office365.com**.
 
3. In the **Pick an account** window, select **Use another account**. 

4. In the **Sign in** window, enter **LynneR@xxxxxZZZZZZ.onmicrosoft.com** (where xxxxxZZZZZZ is the tenant prefix ID provided by your lab hosting provider), and then in the **Enter password** window, enter the same Microsoft 365 Tenant Password provided by your lab hosting provider for the tenant admin account (i.e. the MOD Administrator account) and select **Sign in**. 

5. In Lynne's Outlook Inbox, you should see the spear phishing email that was sent by the Attack Simulator. The subject of the message should be **2 Failed messages to you**. Select the email to open it and review the details in the body of the message. 

	**NOTE!** It can take up to 15 minutes for the email to arrive.  Wait for the email before proceeding.

6. Select the **View Returned Messages** button in the email. Even though you know this is a spear phishing attack, this will enable you to see the effect of doing so in the Attack Simulator report that tracks the results of the spear phishing campaign.

7. In the **Sign in** dialog box that appears, enter **LynneR@xxxxxZZZZZZ.onmicrosoft.com** (where xxxxxZZZZZZ is the tenant prefix ID provided by your lab hosting provider), and then enter the same Microsoft 365 Tenant Password provided by your lab hosting provider for the tenant admin account (i.e. the MOD Administrator account) in the **Enter password** window. Select **Sign in**. 

8. This displays a web page that explains how you have been redirected to it as part of a Phishing awareness test being run by your organization. Read through the contents of this site, which uses the landing page template that you selected in the prior task when setting up the attack simulation.

9. Leave the Outlook tab open for Lynne's mailbox in your Edge browser. Do **NOT** sign out or close it. You will access Lynne's mailbox on LON-CL2 in the next lab exercise. 

10. Switch back to **LON-CL1**.

11. In LON-CL1, in your Edge browser session where you are logged in as Holly Dickson, you should still be on the **Attack simulation training** page. If the **PhishingTest1** simulation does not appear in the **Recent Simulations** list, select the **Refresh** icon to the left of the URL on the address bar. The **PhishingTest1** simulation should now appear. Select the **PhishingTest1** simulation to view the diagnostic results that were captured for this simulation.

12. A **PhishingTest1** page should appear. Review all the information collected for this simulated attack. When you're finished, select the **X** in the upper right-hand corner of the window to close it. 

13. Leave your browser open in LON-CL1 and do not close any of the tabs.
    

### Task 2: Review the Drive-by URL attack results

You will now review the results of the Drive-by URL simulation attack that you just launched. In this task, you will verify whether your organization has received the email that you configured in the Attack simulation training. You will then review the results associated with the Drive-by URL attack that you simulated.

1. Switch to **LON-CL2**.

2. On LON-CL2, in the Edge browser, you should have a tab open containing Lynne Robbins' Outlook mailbox from the prior lab exercise. In Lynne's Outlook Inbox, you should see the email that was sent by the Attack Simulator that's from **klemens@tailspintoys.com**. The subject of the email is **Free toy giveaway promotion from Tailspin Toys**. Select the email to open it and review the details in the body of the message. 

	**NOTE:** It can take up to 15 minutes for the email to arrive.  Wait for the email before proceeding.

8. Select the link that is included in the email. Even though you know this is a Drive-by URL attack, this will enable you to see the effect of doing so in the Attack Simulator report that tracks the results of the spear phishing campaign. <br/>

	Selecting this link displays a web page that explains how you have been redirected to it as part of a Phishing awareness test being run by your organization.  Read through the contents of this site, which uses the landing page template that you selected in the prior task when setting up the attack simulation. 

11. In the **Outlook** tab in your Edge browser, select the picture of Lynne Robbins in the upper-right corner of the window. In Lynne's profile window that appears, select **Sign out**.

12. Once Lynne is signed out, close the Edge browser.

13. Switch back to **LON-CL1**.

14. On LON-CL1, in your browser session where you are logged in as Holly Dickson, you should still be on the **Attack simulation training** page. If the **Custom payload** simulation does not appear in the **Recent Simulations** list, select the **Refresh** icon to the left of the URL on the address bar. The **Custom payload** simulation should now appear. Select the **Custom payload** simulation to view the diagnostic results that were captured for this simulation.

15. A **Custom payload** page should appear. Review all the information collected for this simulated attack. When you're finished, select the **X** in the upper right-hand corner of the window to close it. 

16. Leave your browser open in LON-CL1 and do not close any of the tabs.


### Task 3: Disable Multi-factor Authentication for the Global Admin

To use Microsoft's Attack simulation training to simulate phishing attacks, Holly enabled Multi-Factor Authentication (MFA) for her user account. Now that she has completed the Attack simulation training tests, she wants to disable MFA for her account so that she doesn't have to deal with MFA for the remainder of the pilot project.

1. On LON-CL1, in your Edge browser, you should still be logged into Microsoft 365 as **Holly Dickson**. 

2. To disable MFA for Holly Dickson's user account, you must first access the **Active users** list in the Microsoft 365 admin center. If you have the **Microsoft 365 admin center** open in a browser tab, then select that now; otherwise, open a new browser tab, enter **https://portal.office.com** in the address bar, and then on the **Office 365 home** page, select the **Admin** icon that appears in the column of app icons on the left-side of the screen. This opens the **Microsoft 365 admin center** in a new browser tab. 

3. On the **Microsoft 365 admin center**, in the left-hand navigation pane, select **Users** and then select **Active users**.

4. In the **Active users** window, on the menu bar at the top of the user list, select **Multi-factor authentication**.

5. In the **multi-factor authentication** window (may need to select **Legacy per-user MFA**), the **users** tab is displayed by default. Select the check box for **Holly Dickson**, and in Holly's properties pane on the right, select **Disable**.

6. On the **Disable multi-factor authentication?** dialog box, select **yes**. 

7. When the **Updates successful** dialog box appears, select **close**. In the **multi-factor authentication** window, verify Holly's MFA Status has changed to **Disabled**. Close the **Multi-factor authentication** tab in your browser.

8. You must now sign out of Microsoft 365 as Holly and then sign back in as Holly (without MFA). To do so, perform the following steps: <br/>

	- Select Holly's account icon (HD in a circle) at the top-right of the screen and in Holly's profile window, select **Sign out**.
	- Once you're signed out, close your Edge browser. Doing so will clear your cache.
	- Open a new Edge browser session.
	- Enter the **https://portal.office.com** URL.
	- In the **Pick an account** window, select Holly's account and enter the same **Microsoft 365 Tenant Password** provided by your lab hosting provider for the tenant admin account (i.e. the MOD Administrator account) as the **Password**.
	- From the **Microsoft Office Home** page, select the **Admin** icon to navigate to the **Microsoft 365 admin center**.
	
	You are now ready to proceed to the next lab exercise.

# End of Lab 6
