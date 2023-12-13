# Learning Path 6 - Lab 6 - Exercise 3 - Implement SharePoint Permission Alert


In this exercise you will configure and test an alert that notifies Lynne Robbins when a user is added as a site collection administrator for a SharePoint site collection.

### Task 1 – Create a SharePoint Permissions Alert

1. On **LON-CL1**, in your Edge browser, you should still be logged into Microsoft 365 as **Holly Dickson**.

2. In your Edge browser, select the **Alert policy - Microsoft Defender** tab, which displays the **Microsoft Defender** portal.

3. In the **Microsoft Defender** portal, you should still be in the **Alert policy** window from the prior lab exercise (if not, then in the left-hand navigation pane, select **Policies & rules** and then select **Alert policy**).

4. In the **Alert policy** window, select **+New Alert Policy** on the menu bar. This initiates the **New Alert Policy** wizard.

5. On the **Name your alert, categorize it, and choose a severity** window, enter the following information:

	- Name: **Add user as a Site Collection administrator**

	- Description: **This alert notifies Lynne Robbins when a user is added to the Site Collection administrators on a SharePoint site collection.**

	- Severity: **Medium**

	- Category: **Permissions**

6. Select **Next**.

7. On the **Choose an activity, conditions and when to trigger the alert** window, enter the following information:

	- Activity is: select the **Select an activity** field, then in the menu that appears, scroll down to the **Site administration activities** section and select **Added site collection admin**

	- How do you want the alert to be triggered? **Every time an activity matches the rule**

8. Select **Next**.

9. On the **Decide if you want to notify people when this alert is triggered** window, enter the following information:

	- Email recipients: Remove **Holly Dickson** and add **Lynne Robbins**

	- Daily notification limit: **No limit**

10. Select **Next**.

11. On the **Review your settings** page, under the **Do you want to turn the policy on right away?** option, select **Yes, turn it on right away** and then select **Submit**. 

12. On the **New Alert Policy** window, select **Done**.

13. Verify your new alert policy appears in the list on the **Alert policy** page, its **Type** is set to **Custom**, and its **Status** in **On**.

14. Leave all the Edge browser tabs open for the next task.

You have now configured an additional alert policy that monitors when a user is added as a site collection administrator for a SharePoint Online site collection.

### Task 2 – Test the SharePoint Permissions Alert

In the prior task, you configured an alert designed to notify Lynne Robbins when a user is added as a site collection administrator for a site collection. In this task, you will test this alert by adding Alex Wilber as a site collection admin to the global SharePoint Communication site. This activity should trigger the alert policy that you created, which should send an alert notification email to Lynne Robbins’ mailbox. You will validate whether Lynne received this alert notification email in Exercise 7, task 2.

1. On LON-CL1, in your Edge browser, you should still be logged into Microsoft 365 as **Holly Dickson**. 

2. In your **Microsoft Edge** browser, open a new tab and enter the following URL in the address bar: **https://xxxxxZZZZZZ.sharepoint.com/_layouts/15/settings.aspx** (replace xxxxxZZZZZZ with the tenant prefix provided by your lab hosting provider). This opens the **Site Settings** for the global SharePoint Communication site.

3. On the **Site Settings** window, under the **Users and Permissions** section, select **Site permissions**. 

4. In the ribbon at the top of the page, the **Permissions** tab is displayed by default. Under the **Manage** group, select **Site Collection Administrators**.

5. In the **Site Collection Administrators** dialog box, the **Global administrator** account that was assigned by default to this role group is displayed in the data entry field. To the right of this account, enter **Alex**, select **Alex Wilber** from the list of users that appears, and then select **OK**.  <br/>

	**Note:** This activity should trigger the alert policy that you created, which should send an alert notification email to Lynne Robbins’ mailbox. Rather than waiting up to 15 minutes for the email notification to be generated to validate this SharePoint permission alert, you will validate this alert in Exercise 7, task 2 of this lab.

6. In your Edge browser, close the **Permissions: Communication site** tab. Leave the other tabs open and proceed to the next exercise.


# Proceed to Lab 6 - Exercise 4
