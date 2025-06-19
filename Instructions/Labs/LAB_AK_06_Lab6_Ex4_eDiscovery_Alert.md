# Learning Path 6 - Lab 6 - Exercise 4 - Test the Default eDiscovery Alert

In this exercise you will test a default Microsoft 365 alert policy that notifies all tenant administrators, such as Holly Dickson, whenever an eDiscovery search has been created or exported.

**Note:** Creating an eDiscovery alert of this nature is important because an eDiscovery search, when left unregulated, can pull sensitive content that can be exported to an unauthorized source.

### Task 1 - Assign RBAC Permissions for Search Notification Testing
1. On **LON-CL1**, in your Edge browser, you should still be logged into Microsoft 365 as **Holly Dickson**. 
1. If necessary, select the **Microsoft 365 admin center** tab in your browser. In the navigation pane, under the **Admin centers** group, select **Microsoft Purview**. This opens the Microsoft Purview portal in a new tab.
1. In the **Welcome to the new Microsoft Purview portal** dialog, select the checkbox next to **I agree to the terms** in the lower-left corner, and then select **Get started**.
1. In the **Microsoft Purview** portal, select **Settings**.
1. In the navigation menu, open **Roles and scopes** and select **Role groups**.
1. In the list of roles that appears, click on the **Name** column heading to select the **Sort ascending** in alphabetical name order display. Select the **eDiscovery Manager** role group (select the name of the role group and not the check box). 
1. In the **eDicovery Manager** pane that appears, note the list of roles that have been assigned to this role group. Scroll to the bottom of the pane and note that there are no members in both eDiscovery Manager and eDiscovery Administrator role groups. Scroll back to the top of the pane and select the **Edit** option. 
1. In the **Manage eDiscovery Manager** window, select the **Choose users** button. 
1. In the **Choose users** pane, a partial, unsorted list of users appears. Enter **Holly** in the **Search** field and hit Enter. A list of users appears whose name includes Holly. Select the check box next to **Holly Dickson** (you may select both if you have multiple accounts in the lab) and then select the **Select** button at the bottom of the pane.
1. In the **Manage eDiscovery Manager** window, Holly's name should appear. Select **Next**.
1. In the **Manage eDiscovery Administrator** window, select the **Choose users** button. 
1. In the **Choose users** pane, a partial, unsorted list of users appears. Enter **Holly** in the **Search** field and hit Enter. A list of users appears whose name includes Holly. Select the check box next to **Holly Dickson** (you may select both if you have multiple accounts in the lab) and then select the **Select** button at the bottom of the pane.
1. In the **Manage eDiscovery Administrator** window, Holly's name should appear. Select **Next**.
1. In the **Review the role group and finish** window that appears, note that Holly also appear here as a member of the role groups. Select **Save.**
1. In the **You successfully updated the role group** pane, select **Done**.
1. Leave all tabs in your Edge browser open for the next lab exercise.
You have now added Holly Dickson to the eDiscovery Manager and eDiscovery Administrator role groups.

### Task 2 – Review the default eDiscovery Alert
In this task, you will verify whether a default Microsoft 365 alert is triggered when somebody in your tenant creates an eDiscovery search or exports data from an existing search. Since Holly Dickson is assigned the Global Administrator role, she is automatically a member of the Tenant Admins and will be one of the recipients of this alert. 

1. On **LON-CL1**, in your Edge browser, you should still be logged into Microsoft 365 as **Holly Dickson**. 
1. In your Edge browser, select the **Alert policy - Microsoft Defender** tab. This tab should still be displaying the **Alert policy** window from the prior lab exercise (if not, then in the navigation pane, select **Policies & rules** and then select **Alert policy**).
1. On the **Alert policy** page, you want to search through the default alert policies for a policy named **eDiscovery search started or exported**. Since there are so many pre-existing alert policies, the easiest way to locate the policy is to search for it. In the **Search** field at the top of the screen, enter **eDiscovery** and then hit Enter. 
1. In the policy list, select the **eDiscovery search started or exported** policy that appears. 
1. An **eDiscovery search started or exported** pane should appear. Scroll down through the pane and verify the default settings for this predefined policy are configured as follows:
	- Status: **On**
	- Conditions: Select the down arrow for the **Create alert settings** section to expand it, then verify the following settings:  <br/>
		- Conditions: **Activity is eDiscoverySearchStartedOrExported**
		- Aggregation: **Single event**
		- Scope: **All users**
	- Email recipients: Select the down arrow for the **Set your recipients** section to expand it, then verify the following settings:
		- Recipients: **TenantAdmins**
		- Daily notification limit: **No limit**
1. At the top of the pane, select the **Edit policy** button.
1. On the **eDiscovery search started or exported** window that appears, the only setting that can be edited for this default policy is the **Email recipients** setting. This window enables you to edit the email recipients who are notified when this policy is triggered. You will not change the value here - you will leave it as **TenantAdmins**. Instead, the purpose of this step is to show you how to change the recipient list in your real-world implementations for any of the default system policies.
	 Select the **Cancel** button at the bottom of the window.
8. On the **eDiscovery search started or exported** pane, select the **X** in the upper-right corner to close it.
	**Note:** You can also edit a policy's setting by selecting the vertical ellipsis icon under the **Actions** column at the far-right end of the policy's row on the **Alert Policy** window. 
9. Leave all the Edge browser tabs open for the next task.
You have now reviewed the default Microsoft 365 eDiscovery alert that notifies tenant admins when an eDiscovery search is created or exported.

### Task 3 – Test the default eDiscovery Alert

To test this default alert, Holly Dickson will create an eDiscovery search. This activity should trigger the alert policy, which should send an alert notification email to all Tenant Admins. Holly is a Global admin. By default, Global admins are members of the Tenant Admin group; therefore, she should receive the email notification generated by this alert. You will validate whether Holly received the email in Exercise 7 of this lab.
1. On LON-CL1, in your Edge browser, you should still be logged into Microsoft 365 as **Holly Dickson**. 
1. Select the **Microsoft Purview** admin center tab in your browser.
1. In the **Microsoft Purview** portal, in the navigation pane, select **Solutions**, and then select **eDiscovery**.
1. Select **Content Search**.
1. The **Content search** window has a few tabs. The **Searches** tab is displayed by default. Select the **Create a search** button that appears on the menu bar. This initiates the **New search** wizard.
1. In the **New search** wizard, enter **Confidential search** in the **Search name** field and then select **Create**.
1. In the **Confidential search** window,click on the **Add sources** button.
1. On the **Search for sources** pane, click on the checkbox near **Select all** in the detail pane to select all users in the tenant.
1. Click on the **Save and close** button.
1. Back on the **Query** tab, in the **Condition builder**, enter **Confidential** in the **Enter a keyword or phrase [...]** field and press **[Enter]**.
1. Click on the **Run query** button.
1. On the **Choose serach results** pane, leave the default value and click on the **Run Query** button once more.
1. Back on the **Confidential search**, your browser should switch to the **Statistics** tab.
1. Wait for some results to appear on the **Statistics** tab (you may see some found results).

	**Note:** When you run a new query, the eDiscovery alert should be triggered, thereby creating an email notification that should be sent to the Inbox of all users with Tenant Admin permissions. It may take some additional time for the email notification to be generated to validate this eDiscovery alert. Instead of waiting for this email to be generated, proceed to the next exercise. You will validate this alert email in Exercise 7, task 3 of this lab.
1.  Leave your browser open in LON-CL1 and do not close any of the tabs.
    
# Proceed to Lab 6 - Exercise 5
