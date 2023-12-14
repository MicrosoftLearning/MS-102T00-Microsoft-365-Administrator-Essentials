# Learning Path 6 - Lab 6 - Exercise 2 - Implement a Mailbox Permission Alert

In this exercise you will configure and test an alert that will notify Lynne Robbins when FullAccess permissions are granted to any mailbox within Adatum.

**Important:** This lab includes three exercises in which you will create alert notifications (Exercises 2 through 4) and two exercises in which you will implement simulated attack scenarios that also create alert notifications (Exercises 5 and 6). In each of these five excercises, you must perform a final task to validate whether the alert was created or an email was received. In all five exercises, it can take up to 15 minutes for the system to create the corresponding alert or email. Rather than having to wait up to 15 minutes after having created each alert or simulated attack to validate whether the task worked (which is 75 minutes of wait time; 5 exercises x 15 minutes each), the validation tasks for all five exercises have been moved to the final exercise in this lab (Lab 6, Exercise 7). By the time you get to the final exercise, hopefully all alerts and emails for these five exercises have been generated and you will not have to endure any wait time.

### Task 1 – Create a Mailbox Permission Alert

1. On LON-CL1, in your Edge browser, you should still be logged into Microsoft 365 as Holly Dickson. 

2. The **Microsoft Defender** portal should still be open in your Edge browser from the prior task. Select the **Microsoft Defender** tab now. In the left-hand navigation pane, under the **Email & collaboration** section, select **Policies & rules**. 

3. On the **Policies & rules** window, select **Alert policy**. If a dialog box appears indicating the alert policy portal has been updated, select the **Dismiss** button.

4. In the **Alert Policy** window, note the message at the top of the page indicating the fact that mail flow alerts have moved to the Exchange admin center. Mail flow alerts can no longer be maintained in the Microsoft Defender security portal. Since you will be creating a mailbox permission alert and not a mail flow alert, you can continue on with this task in the Microsoft Defender portal. <br/> 

	In the **Alert Policy** window, review the list of preconfigured alert policies that are available in Microsoft 365. Select **+New Alert Policy** on the menu bar. This initiates the **New Alert Policy** wizard.

5. On the **Name your alert, categorize it, and choose a severity** page, enter the following information:

	- Name: **Mailbox permission change**

	- Description: **This alert notifies Lynne Robbins when FullAccess permissions are granted to any mailbox in Adatum Corporation**

	- Severity: **Medium**

	- Category: **Permissions**

6. Select **Next**.

7. On the **Choose an activity, conditions and when to trigger the alert** page, enter the following information:

	- Activity is: You must select a predefined activity. Select in the field, which displays a long list of activities. To filter the list to mail-related activities only, enter **mail** in the field and then select **Granted mailbox permission** from the list of activities containing **mail**. **Note:** This activity implies granting FullAccess permission to a mailbox.

	- How do you want the alert to be triggered?: **Every time an activity matches the rule**

8. Select **Next**.

9. On the **Decide if you want to notify people when this alert is triggered** page, enter the following information:

	- Email recipients: Select the "X" to the right of **Holly Dickson's** account to remove her, then enter **Lynne** in the field, and then select **Lynne Robbins** from the list of users whose first name starts with **Lynne**

	- Daily notification limit: **No limit**

10. Select **Next**.

11. On the **Review your settings** page, review the settings and if anything needs to be corrected, select its corresponding **Edit** option and make the necessary corrections. <br/>

	When everything is correct, under the **Do you want to turn the policy on right away?** setting, select **Yes, turn it on right away**. Select **Submit**.

12. On the **New Alert Policy** window, select **Done**.

13. Verify your new alert policy appears in the list on the **Alert policy** page, its **Type** is set to **Custom**, and its **Status** in **On** (depending on the size of your monitor, you may have to scroll to the right to view the **Status** column).

14. Leave the **Alert policy** tab in your Edge browser open for the next task.

You have now created an activity alert in Microsoft Defender XDR that is triggered when FullAccess permissions are granted to any mailboxes.

### Task 2 – Test the Mailbox Permission Alert

In the prior task, you configured an alert designed to notify Lynne Robbins when FullAccess permissions are granted to any mailbox within Adatum. In this task, you will test this alert by changing the permission on Alex Wilber’s mailbox by granting Joni Sherman FullAccess to his mailbox. This activity should trigger the alert that you created, which should send an alert notification email to Lynne Robbins’ mailbox. You will validate whether the email is generated in Exercise 7.

1. On LON-CL1, in your Edge browser, you should still be logged into Microsoft 365 as **Holly Dickson**. 

2. In your Edge browser, select the **Microsoft 365 admin center** tab, and then in the left-hand navigation pane, under the **Admin centers** group, select **Exchange**. This opens the Exchange admin center for Exchange Online.

3. In the **Exchange admin center**, the **Manage mailboxes** window appears by default (if it doesn't, then in the left-hand navigation pane, under the **Recipients** group, select **Mailboxes**). 

4. In the **Manage mailboxes** window, select **Alex Wilber** from the list of mailboxes (select Alex's name; do not select the check box to the left of his name).

5. In the **Alex Wilber** pane that appears, the **General** tab is displayed by default. Select the **Delegation** tab.

6. On the **Delegation** tab, there are three mailbox permissions that can be updated: **Send as**, **Send on behalf**, and **Read and manage (Full Access)**. You want to add each of these permissions for Alex's mailbox to **Joni Sherman**. For EACH permission, perform the following steps to add Joni to that permission: <br/>

	- Select the **Edit** button for the permission. 
	- On the **Manage mailbox delegation** pane, select **+Add members**.
	- In the list of users that appears, select the check box for **Joni Sherman** and then select **Save**.
	- In the **Add delegate permissions?** pane, select **Confirm**.
	- Once the mailbox permission is added to Alex's mailbox, select the back arrow at the top of the pane. 
	- This returns you to the **Delegation** tab on the **Alex Wilber** pane, which displays the three permissions. Repeat these steps for each of the two remaining permissions. 

7. Once you have assigned Joni to each of the three permissions on the **Delegation** tab, select the **X** in the upper right-hand corner to close the **Alex Wilber** pane. <br/>

	**Note:** This activity should trigger the alert policy that you created, which should send an alert notification email to Lynne Robbins’ mailbox. Rather than waiting up to 15 minutes for the email notification to be generated to validate this mailbox permission alert, you will validate this alert in Exercise 7, task 1 of this lab.
   
8. In your Edge browswer, close the **Exchange admin center** tab. Leave the other tabs open and proceed to the next exercise.


# Proceed to Lab 6 - Exercise 3
