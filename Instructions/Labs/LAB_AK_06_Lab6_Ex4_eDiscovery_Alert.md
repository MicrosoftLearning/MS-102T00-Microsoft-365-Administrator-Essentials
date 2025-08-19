# Learning Path 6 – Lab 6 – Exercise 4 – Test the Default eDiscovery Alert

In this exercise you will test a default Microsoft 365 alert policy that notifies all tenant administrators, such as Holly Dickson, whenever an eDiscovery search has been created or exported.

**Note:** Creating an eDiscovery alert of this nature is important because an eDiscovery search, when left unregulated, can pull sensitive content that can be exported to an unauthorized source.

### Task 1 – Assign RBAC Permissions for Search Notification Testing

In this task, you will assign Holly Dickson the necessary eDiscovery permissions so she can test the default alert policy.

1. On **LON-CL1**, in your Edge browser, you should still be logged into Microsoft 365 as **Holly Dickson**.  

2. In your browser, open the **Microsoft 365 admin center**. Under the **Admin centers** group, select **Microsoft Purview**. 

3. In the **Welcome to the new Microsoft Purview portal** dialog, select the checkbox next to **I agree to the terms**, and then select **Get started**.  

4. In the **Microsoft Purview** portal, select **Settings**.  

5. In the navigation pane, select **Roles and scopes**, and then select **Role groups**.  

6. In the list of role groups, select **eDiscovery Manager** (select the name, not the check box).  

7. In the **eDiscovery Manager** pane, select **Edit**.  

8. In the **Manage eDiscovery Manager** window, select the **Choose users** button.  
   - In the **Choose users** pane, search for and select **Holly Dickson**, and then select **Select**.  
   - Holly’s name should now appear in the list. Select **Next**.  

9. In the **Manage eDiscovery Administrator** window, select the **Choose users** button.  
   - Search for and select **Holly Dickson**, and then select **Select**.  
   - Holly’s name should now appear in the list. Select **Next**.  

10. In the **Review the role group and finish** window, verify Holly is listed as a member of both role groups, and then select **Save**.  

11. In the confirmation pane, select **Done**.

12. Sign out of Microsoft Purview, and then sign back in as **Holly Dickson**.  
   - This step helps ensure the updated permissions are recognized during the next task.

You have now added Holly Dickson to the **eDiscovery Manager** and **eDiscovery Administrator** role groups.  

### Task 2 – Review the Default eDiscovery Alert

In this task, you will verify whether a default Microsoft 365 alert is triggered when somebody in your tenant creates an eDiscovery search or exports data from an existing search. Since Holly Dickson is assigned the **Global Administrator** role, she is automatically a member of the **Tenant Admins** and will be one of the recipients of this alert.  

1. On **LON-CL1**, in your Edge browser, you should still be logged into Microsoft 365 as **Holly Dickson**.  

2. In your Edge browser, select the **Alert policy – Microsoft Defender** tab. This tab should still be displaying the **Alert policy** window from the prior lab exercise (if not, in the navigation pane, select **Policies & rules**, and then select **Alert policy**).  

3. On the **Alert policy** page, search for the policy named **eDiscovery search started or exported**. In the **Search** field at the top, enter **eDiscovery**, and then press **Enter**.  

4. In the policy list, select the **eDiscovery search started or exported** policy that appears.  

5. An **eDiscovery search started or exported** pane should appear. Scroll down and verify the default settings for this predefined policy are configured as follows:  

   - Status: **On**  

   - Conditions: Select the down arrow for the **Create alert settings** section, then verify the following settings:  
     - Conditions: **Activity is eDiscoverySearchStartedOrExported**  
     - Aggregation: **Single event**  
     - Scope: **All users**  

   - Email recipients: Select the down arrow for the **Set your recipients** section, then verify the following settings:  
     - Recipients: **TenantAdmins**  
     - Daily notification limit: **No limit**  

6. At the top of the pane, select the **Edit policy** button.  

7. On the **eDiscovery search started or exported** window that appears, note that the only setting that can be edited is the **Email recipients** list. You will not change the value here—leave it as **TenantAdmins**.  

   Instead, observe how you could edit this in real-world implementations if needed. Select **Cancel** at the bottom of the window.  

8. On the **eDiscovery search started or exported** pane, select the **X** in the upper-right corner to close it.  

   **Note:** You can also edit a policy’s setting by selecting the vertical ellipsis icon under the **Actions** column at the far-right end of the policy’s row on the **Alert Policy** window.  

You have now reviewed the default Microsoft 365 eDiscovery alert that notifies tenant admins when an eDiscovery search is created or exported.  

### Task 3 – Test the Default eDiscovery Alert

To test this default alert, Holly Dickson will create an eDiscovery search. This activity should trigger the alert policy, which will send an alert notification email to all Tenant Admins. Holly is a Global admin. By default, Global admins are members of the Tenant Admin group; therefore, she should receive the email notification generated by this alert. You will validate whether Holly received the email in **Exercise 7** of this lab.  

1. On **LON-CL1**, in your Edge browser, you should still be logged into Microsoft 365 as **Holly Dickson**.  

2. In your Edge browser, select the **Microsoft Purview** admin center tab.  

3. In the **Microsoft Purview** portal, in the navigation pane, select **Solutions**, and then select **eDiscovery**.  

4. Under **eDiscovery**, select **Content Search**.  

5. On the **Searches** tab, select **Create a search**. This initiates the **New search wizard**.  

6. In the **New search wizard**, on the **Name and description** page, enter **Confidential search** in the **Name** field, and then select **Create**.  

7. In the **Confidential search** window, select **Add sources**.  
   - In the search pane, locate and select the **Sales and Marketing** mailbox (or, if not available, select **All mailboxes**).  
   - Select **Save and close**.  

8. On the **Query** tab, in the condition builder, enter **Confidential** in the keyword field, and then press **Enter**.  

9. Select the **Run query** button.  

10. On the **Choose search results** page, leave the default values, and then select **Run query** again.  

11. Back on the **Confidential search** window, the **Statistics** tab should now display results.  

   **Note:** Running this search should trigger the **eDiscovery alert**, which generates an email notification to all users with Tenant Admin permissions. It may take several minutes for the email to be delivered. Instead of waiting, proceed to the next exercise. You will validate this alert email in **Exercise 7, Task 3**.  

Leave your browser open in **LON-CL1** and do not close any tabs.  

# Proceed to Lab 6 – Exercise 5


