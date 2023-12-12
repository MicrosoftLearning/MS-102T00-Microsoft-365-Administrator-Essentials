# Learning Path 6 - Lab 6 - Exercise 3 - Implement SharePoint Permission Alert


In this exercise you will configure and test an alert that notifies Lynne Robbins when a user is added as a site collection administrator for a SharePoint site collection.

### Task 1 – Create a SharePoint Permissions Alert

1. At the end of the prior lab, you were logged into LON-CL2. This lab will use LON-CL1.  <br/>

    Switch to **LON-CL1**. 

2. On **LON-CL1**, in your Edge browser, you should still be logged into Microsoft 365 as **Holly Dickson**. In your Edge browser, select the **Alert policy - Microsoft 365 security** tab, which displays the **Microsoft Defender** portal.

3. In the **Microsoft Defender** tab, you should still be in the **Alert policy** window from the prior lab exercise (if not, then in the left-hand navigation pane, select **Policies & rules** and then select **Alert policy**).

4. In the **Alert policy** window, select **+New Alert Policy** on the menu bar. This initiates the **New Alert Policy** wizard.

5. On the **Name your alert, categorize it, and choose a severity** window, enter the following information:

	- Name: **Add user as a site collection administrator**

	- Description: **This alert notifies Lynne Robbins when a user is added to the site collection administrators on a SharePoint site collection.**

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

**Note:** Rather than waiting up to 15 minutes for the email notification to be generated to validate this SharePoint permission alert, you will validate this alert in Exercise 7, task 2 of this lab.

# Proceed to Lab 6 - Exercise 4
