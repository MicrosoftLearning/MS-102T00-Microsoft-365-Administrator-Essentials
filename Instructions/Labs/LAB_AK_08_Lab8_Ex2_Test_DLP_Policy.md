# Learning Path 8 - Lab 8 - Exercise 2 - Test the DLP Policy

Holly Dickson is now at the point in her pilot project where she wants to test the DLP policy related to emails that contain sensitive information that you created in the previous lab exercise. 

**NOTE:** We have intermittently experienced issues in the past where DLP policies and policy tips do not work as expected in this lab exercise. This is due to throttling issues that sometimes occur between our VM lab environment and the Microsoft 365 trial tenant. This is not indicative of the normal experience within Microsoft 365 production environments. It is also not indicative of the normal training experience. We apologize if you run into this issue during this lab exercise.

### Task 1 – Test the first DLP Policy rule

In the previous exercise, you created a custom DLP policy that searches emails for sensitive information related to IP addresses in your Adatum tenant. This policy included two rules - one that checked for emails containing a single IP address, and another that checked for emails containing two or more IP addresses. 

In this task, you will send an email from Holly Dickson to Lynne Robbins that tests the first rule (single IP address). When this rule is triggered, an email policy tip is displayed in the sender's Outlook mailbox that informs the sender the email contains sensitive data. The sender will also receive an email notification, but the email will still be sent to the recipient.

1. On LON-CL1, in your Edge browser, you should still be logged into Microsoft 365 as **Holly Dickson**. 

2. You will now send an email from Holly to Lynne Robbins, and you will include an IP address in the body of the email. <br/>

	In **Microsoft Edge**, select the **Home | Microsoft 365** tab, and then select the **Outlook** icon in the column of app icons on the left-side of the screen. When Outlook on the web opens, you should be automatically logged in as Holly Dickson.  <br/>

	**Note:** If **Outlook on the web** was already open, then verify that you're logged in as **Holly** by checking the user icon in the upper right corner (the **HD** circle). If Outlook was open for any other user, then close the tab and repeat the instructions in this step to open Outlook on the Web for Holly.

3. In the upper left corner of the screen, select **New mail**. 

4. In the message pane that appears on the right-side of the screen, enter the following information:

	- To: enter **Lynne** and then select **Lynne Robbins** from the user list that appears

	- Add a subject: **DLP Policy Test 1**

	- Message area: **Hey Lynne - I will configure this IP address: 192.168.0.1**

	**Note:** When drafting this email with sensitive data (in this case, one IP address), it will trigger the IP address policy that you previously created, and specifically, the single IP address rule. As such, a **Policy tip** should be displayed indicating the email message violates an organizational policy. You'll ignore this policy tip and send the email anyway in order to test the remainder of the DLP policy, which will send a Notification email to Holly.

5. Once the policy tip is displayed, select **Send.**

6. Select Holly's **Sent Items** folder to verify the email was sent.

7. Select Holly's **Inbox** folder. Holly should receive an email from **Microsoft Outlook** with the subject: **Notification: DLP Policy Test 1**. Select this email and review its content. 

8. Switch to **LON-CL2**. 

9. If you need to sign into the VM, the local **administrator** account should appear by default, so enter **Pa55w.rd** in the **Password** field to log in. 

10. On the taskbar, select the icon for the **Edge** browser.

11. In the Edge browser, enter the following URL: **https://outlook.office365.com**

12. In the **Pick an account** window, select Lynne Robbins' account (**LynneR@xxxxxZZZZZZ.onmicrosoft.com**, where xxxxxZZZZZZ is the tenant prefix provided by your lab hosting provider). In the **Enter password** window, enter the **User Password** provided by your lab hosting provider and then select **Sign in**. If required, complete the MFA sign-in process.

13. On the **Stay signed in** window, select the **Don't show this again** check box and select **Yes**.

14. In Lynne's Inbox, verify that she received the email from Holly Dickson that has the subject line: **DLP Policy Test 1**. Select the message to verify the content containing the IP address was not removed. 

15. Leave the Outlook tab open in the Edge browser for the next task.

16. Switch back to **LON-CL1**.

	
### Task 2 – Test the second DLP Policy rule

In the previous exercise, you created a custom DLP policy that searches emails for sensitive information related to IP addresses in your Adatum tenant. This policy included two rules - one that checked for emails containing a single IP address, and another that checked for emails containing two or more IP addresses. 
	
In this task, you will send an email from Holly Dickson to Lynne Robbins that tests the second rule (multiple IP addresses). When this rule is triggered, an email policy tip is displayed in the sender's Outlook mailbox that informs the sender the email contains sensitive data. The email will be blocked, but the sender can override the blocked email and allow it to be sent.  

1. On LON-CL1, in your Edge browser, you should still be logged into Microsoft 365 as **Holly Dickson**. 
	
2. You will now send a second message from Holly to Lynne that contains multiple IP addresses. Repeat the process as before for creating an email to Lynne Robbins with the following information: 

	- Add a subject: **DLP Policy Test 2**

	- Message area: **Hey Lynne - I will test the following IP addresses: 192.168.0.1 and 172.16.0.1**

	**Note:** When drafting this email with sensitive data (in this case, multiple IP addresses), it will trigger the IP address policy that you previously created, and specifically, the multiple IP address rule. As such, a **Policy tip** should be displayed indicating the email message violates an organizational policy. You'll ignore this policy tip and send the email anyway in order to test the remainder of the DLP policy, which will block the email. Once you test the email block, you'll override the blockage by entering a business justification for sending this sensitive data, and then you'll try and send the email again.

3. Once the policy tip is displayed, select **Send**. You should immediately receive a **Send blocked** dialog box that indicates the message includes one or more recipients who aren't authorized to receive sensitive information. Select **OK**. <br/>

	**Hint:** Normally you would override the block before sending it, but in this case we wanted you to experience the block to see how it works. In the next steps, you'll override the block and attempt to re-send the email.

4. Select Holly's **Sent Items** folder to verify the email was not sent.

5. Select Holly's **Inbox** folder. Note that the email message is no longer displayed. Select Holly's **Drafts** folder, which contains a copy of the email. Select the email.

6. To send this email, you must override the block BEFORE you select the **Send** button. To override the block, in the policy tip that appears at the top of the message, select **Show details**.

7. In the detail message that appears in the policy tip, select **Override**.

8. In the dialog box that appears, the **I have a business justification** option is selected by default. Leave this option selected and enter **Lynne must be informed of the IP addresses I'm testing** in the **Enter explanation here** field. Select **Override**.	<br/>

	Note how the policy tip message has changed to indicate you have chosen to send the message even though it appears to contain sensitive information.

9. Select Holly's **Sent Items** folder to verify the email was sent.

10. Select Holly's **Inbox** folder. Holly should receive an email from **Microsoft Outlook** with the subject: **Notification: DLP Policy Test 2**. Select this email and review its content.
	
11. Switch to **LON-CL2**. 

12. You should still be logged into **Outlook on the Web** in the LON-CL2 VM as **Lynne Robbins**. In your **Edge** browser, Lynne’s mailbox should still be open in **Outlook on the web** from when you last used it in the previous task.

13. In Lynne's Inbox, verify that she received the email from Holly Dickson that has the subject line: **DLP Policy Test 2**. Select the message to verify the content containing the IP addresses was not removed. 

14. Leave the Outlook tab open in the Edge browser for the next task.

15. Switch back to **LON-CL1**.


# End of Lab 8
