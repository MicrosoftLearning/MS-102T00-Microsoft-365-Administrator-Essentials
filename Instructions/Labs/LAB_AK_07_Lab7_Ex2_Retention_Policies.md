# Learning Path 7 - Lab 7 - Exercise 2 - Configure In-place Archiving and Retention Policies  

In this exercise, you will use the the Microsoft Exchange admin center to enable In-place archiving for Holly Dickson's mailbox. You will then configure two retention policies through the Microsoft Purview portal. 

### Task 1 – Activate In-Place Archiving for a new user's mailbox

In this next phase of your Adatum pilot project, you will access the Microsoft Exchange admin center to activate Holly Dickson’s archive mailbox. After Holly's archive mailbox is enabled, the default retention policy that's assigned to her mailbox does the following: <br/>

- Moves items that are two years or older from Holly's primary mailbox to her archive mailbox.
- Moves items that are 14-days or older from the Recoverable Items folder in Holly's primary mailbox to the Recoverable Items folder in her archive mailbox.

1. On LON-CL1, in your Edge browser, you should still be logged into Microsoft 365 as **Holly Dickson**.

2. In Microsoft Edge, in the **Microsoft 365 admin center**, under the **Admin centers** group, select **Exchange** to open the Exchange admin center.

3. In the **Exchange admin center**, the **Manage mailboxes** page appears by default. In the list of users, note the ones who have an **Archive status** that is set to **Active**. These archive mailboxes were enabled when the VM lab environment was built for this training course and these users were preconfigured in the tenant. However, since you added Holly's user account in one of the first labs at the start of this course, her archive mailbox is **Disabled** by default. <br/>

	To enable Holly’s archive mailbox, select **Holly Dickson** in the user list. In the **Holly Dickson** pane that appears, the **General** tab is displayed by default. Select the **Others** tab. In the **Mailbox archive** section, note that Holly's archive mailbox is Disabled. In this group, select **Manage mailbox archive**. 

4. In the **Manage mailbox archive** pane that appears, select the toggle switch for **Mailbox archive status** to change it to **Enabled**. Select **Save** and then close the pane.

5. It might take a few moments to create Holly's archive mailbox. Once a message appears indicating **Mailbox archiving successfully updated**, selec the X in the upper right corner of th pane to close it. 

6. On the **Manage mailboxes** page, select the **Refresh** icon on the menu bar above the list of users. Holly's archive mailbox should now be **Active** once the archive mailbox is created. You may have to wait a minute or two and refresh again until **Active** appears.

7. In your Microsoft Edge browser, leave your Edge browser and all its tabs open for the next task. 
 

### Task 2 – Create an email retention policy for test users

As part of your pilot project for Adatum, you will configure email retention through the Microsoft Purview portal by creating a new retention policy. You will then assign this retention policy to Joni Sherman and Lynne Robbins’ mailboxes. Joni and Lynne are Holly's two test users for compliance testing. Holly wants to use this policy to test email retention for these two test users before creating a second retention policy in the next task that will be applied across the entire organization.

1. On LON-CL1, select the tab for the **Microsoft 365 admin center**. In the left-hand navigation pane, under the **Admin centers** section, select **Compliance**. Doing so will open the **Microsoft Purview** portal.

2. In the **Microsoft Purview** portal, in the left-hand navigation pane, select **Data lifecycle management**, and then select **Microsoft 365**.

3. In the **Data lifecycle management** window, the **Overview** tab is displayed by default. In the list of tabs that appear across the top of the page, select **Retention policies**.

4. On the **Retention policies** tab, select **+New retention policy** on the menu bar. This initiates the **Create retention policy** wizard.

5. On the **Name your retention policy** page, enter **Test user email retention** in the **Name** field and then select **Next**.

6. On the **Policy Scope** page, you can choose the admin units that you want to apply the policy to. Since Holly wants this policy to apply to the entire organization rather than just a select group of admin units, select **Next**.

7. On the **Choose the type of retention policy to create** field, select **Static** and then select **Next**.

8. On the **Choose where to apply the policy** page, note the **Exchange mailboxes** location. It's currently set to include **All mailboxes**. You want to change this to just apply to Joni Sherman and Lynne Robbins' mailboxes. Under **All mailboxes**, select **Edit**.

9. In the **Exchange mailboxes** pane that appears, hover your mouse over **Joni Sherman** and then select her check box. Do the same for **Lynne Robins**. <br/>

	**Tip:** If you select a user's name, the other check boxes that have been selected will be unselected. To select multiple users, you must hover your mouse over each user's name and select their check box that appears. Also, the order of users and groups do not appear to be in any type of alphabetical order. In your real-world deployment, if the number of users and groups is quite large, it may be more efficient to enter the user's first name in the Search box to display the users with that first name. This may make it easier to find certain users or groups. <br/>

	Once Joni and Lynne's check boxes are selected, select **Done**.

10. On the **Choose where to apply the policy** page, the **Exchange email** location should now indicate that **2 mailboxes** are included. <br/>

	Since this policy will only apply to Exchange email for Joni and Lynne, set the **Status** toggle switch to **Off** for all other locations in which it's currently set to On (**SharePoint sites**, **OneDrive accounts**, and **Microsoft 365 Groups**). Select **Next**.

11. On the **Decide if you want to retain content, delete it, or both** page, verify the **Retain items for a specific period** option is selected (if necessary, select it now). Then enter the following information for this option: <br/>

	- Retain items for a specific period - select in this field, and in the drop-down menu that appears, select **Custom**. Three fields will appear - years, months, and days. For testing purposes, Holly wants to test email retention for emails in Joni and Lynne's mailboxes by only retaining emails that are less than one year old. As such, set the time periods to the following values: **Years - 1, Months - 0, Days - 0**.

	- Start the retention period based on - **When items were created**

	- At the end of the retention period - **Delete items automatically**

12. Select **Next**.

13. On the **Review and finish** page, review your selections. If anything needs to be changed, select the appropriate Edit link and make the necessary changes. Once everything is correct, select **Submit**.

14. On the **You successfully created a retention policy** window, select **Done**.

15. Leave the **Data lifecycle management** tab open in your Edge browser as you will create another retention policy in the next task.


### Task 3 – Create an email retention policy for all users

Holly has concluded her testing of email retention on Joni and Lynne's mailboxes using the **Test user email retention** policy that you created in the prior task. Holly now wants to create a retention policy that preserves the content of all Exchange Online mailboxes from deletion for 5 years after the last modification. Since Holly has completed her email retention testing, she wants to first disable the **Test user email retention** policy. By doing so, Joni and Lynne's mailboxes will be governed by the retention policy that you create in this task that applies to all Adatum mailboxes. 

1. On LON-CL1, your Edge browser should still have the **Microsoft Purview** portal open from the prior task, and it should be displaying the **Data lifecycle management** window.

2. In the **Data lifecycle management** window, in the list of tabs that appear across the top of the page, select **Retention policies** (if another tab is selected).

3. On the **Retention policies** tab, select the check box next to **Test user email retention**, and then select **Disable policy** on the menu bar.  <br/>

	Once the policy is disabled, a message will briefly appear at the top of the page indicating the policy is disabled. You can test this out by once again selecting the check box next to **Test user email retention**. Note that the menu bar includes an **Enable policy** option. This option indicates the policy is currently disabled. You can now proceed to the remaining steps in this task to create Adatum's official, organization-wide email retention policy.

4. On the **Retention policies** tab, select **+New retention policy** on the menu bar. This initiates the **Create retention policy** wizard.

5. On the **Name your retention policy** page, enter **Adatum email retention** in the **Name** field and then select **Next**.

6. On the **Policy Scope** page, you can choose the admin units that you want to apply the policy to. Since Holly wants this policy to apply to the entire organization rather than just a select group of admin units, select **Next**.

7. On the **Choose the type of retention policy to create** field, select **Static** and then select **Next**.

8. On the **Choose where to apply the policy** page, this policy will only apply to **Exchange mailboxes**. Ensure that it's **Status** is set to **On**. Set the **Status** toggle switch to **Off** for all other locations that are turned **On** by default. **Exchange mailboxes** should be the only location whose **Status** is set to **On**. <br/>

	**Note:** For the **Exchange mailboxes** location, note that it's currently set to include **All mailboxes**. Do not change this value, since Holly wants this policy to apply to all mailboxes at Adatum.  <br/>

	Select **Next**.

9. On the **Decide if you want to retain content, delete it, or both** page, verify the **Retain items for a specific period** option is selected (if necessary, select it now). Then enter the following information for this option: <br/>

	- Retain items for a specific period - **5 years**

	- Start the retention period based on - **When items were last modified**

	- At the end of the retention period - **Delete items automatically**

10. Select **Next**.

11. On the **Review and finish** page, review your selections. If anything needs to be changed, select the appropriate Edit link and make the necessary changes. Otherwise, if everything is correct, select **Submit**.

12. On the **You successfully created a retention policy** window, select **Done**.

13. In your Edge browser, leave all the tabs open as you proceed to the next exercise.

You have now created a new retention policy in the Microsoft Purview portal that retains all Exchange emails from all mailboxes for 5 years after the last modification.

 # Proceed to Lab 7 - Exercise 3
 
