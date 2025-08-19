# Learning Path 5 - Lab 5 - Exercise 2 - Implement a Safe Links Policy

Having created a Safe Attachments policy, Holly Dickson now wants to create a Safe Links policy and then validate the policy to ensure that it works properly.

**IMPORTANT:** This lab exercise consists of two tasks. The first task creates a Safe Links policy, and then the second task validates the policy. The problem with this lab is that when you create a safe links policy, it takes at least 30 minutes for the new policy to propagate through the system. **This means that after performing Task 1, you must wait at least 30 minutes before performing Task 2. If you perform Task 2 immediately after performing Task 1, then Task 2 will fail.** After completing Task 1, you should continue with the training class. Your instructor will provide guidance on when you can perform Task 2 depending on the next break that occurs in the class schedule.

### Task 1 – Create a Safe Links Policy

In this task, you will create a Safe Links policy that applies to all users in your tenant. You will then add the **https://tailspintoys.com** URL to the company-wide list of blocked URLs (i.e. the Tenant Block List) that you will define in the Microsoft Defender portal. The blocked URLs and other options defined in the Safe Links global settings are only applied to users who are included in active Safe Links policies. There is no built-in or default Safe Links policy, so you must create at least one Safe Links policy for these global settings to be active.  

1. On LON-CL1, in your Edge browser, you should still be logged into Microsoft 365 as **Holly Dickson**.

2. After finishing the previous task, you should still be in the **Microsoft Defender** portal. If not, then in your browser, enter **https://security.microsoft.com** in the address bar.

3. In the **Microsoft Defender** portal, you should still be on the **Safe attachments** page after completing the previous task. In the navigation thread at the top of the page (**Policies & rules > Threat policies > Safe attachments**), select **Threat policies**. <br/>

    **NOTE:** If you had closed the **Safe Attachments** tab after the prior task, then navigate to the **Threat policies** page by selecting **Email & collaboration > Policies & rules** in the navigation pane, and then selecting **Threat policies**.

4. In the **Threat policies** window, under the **Policies** section, select **Safe Links**. 

5. On the **Safe links** page, select **+Create** on the menu bar. This initiates the **Create safe links policy** wizard.

6. On the **Name your policy** page, enter **LinkPolicy1** in the **Name** field and then select **Next**.

7. On the **Users and domains** page, enter **on** in the **Domains** field. In the menu of suggested domains that appears, select Adatum's **xxxxxZZZZZZ.onmicrosoft.com** domain. Adatum's domain will now appear below the **Domains** field. Select **Next**.

8. On the **URL & click protection settings** page, update the following settings and then select **Next**: 

    - Under the **Email** section, verify that all check boxes are selected (if any are not selected by default, then select them now):
    - Under the **Click protection settings** section:
        - **Track user clicks** - Adatum does not want to track user clicks, so clear this check box if it's selected by default
   
9. On the **Notification** page, verify the **Use the default notification text** option is selected (if necessary, select it now) and then select **Next**.

10. On the **Review** page, review the options that you selected. If any need to be corrected, select the appropriate **Edit** option and make the necessary corrections. Once they all appear correct, select **Submit**. 

11. On the **New Safe Links policy created** page, select **Done**. Once the **LinkPolicy1** policy is created, it will appear in the Safe links list. 

12. In the navigation thread at the top of the page (**Policies & rules > Threat policies > Safe links**), select **Threat policies**.

13. In the **Threat policies** page, under the **Rules** section, select **Tenant Allow/Block Lists**.

14. On the **Tenant Allow/Block Lists** page, the **Domains & addresses** tab is displayed by default. Select the **URLs** tab.

15. On the **URLs** tab, select **+Add** > **Block** on the menu bar. In the **Block URLs** pane that appears, enter **https://tailspintoys.com/** in the field and then select **Add**.

      **Note:** When you enter the URL, make sure you enter the wildcard at the end of it. The * wildcard represents "any characters" and is used to match multiple URLs. When you enter **https://tailspintoys.com/*** , you're telling Microsoft 365 to block all URLs that start with https://tailspintoys.com/, including any subdirectories, paths, or additional characters after the domain. This ensures a broader and more effective block, covering any page or resource under the tailspintoys.com domain. If you enter https://tailspintoys.com without the wildcard (*), Microsoft 365 might interpret it as an exact match to that specific domain. As such, it may fail to block it because URLs on the web typically have paths, query strings, or other parts after the domain name. For example, https://tailspintoys.com/contact or https://tailspintoys.com/shop would not be blocked if you only specify https://tailspintoys.com without a wildcard.

**STOP!!** As mentioned at the start of this lab exercise, now that you have created a Safe Links policy, you must wait at least 30 minutes for the policy to propagate through the system before you can perform the next task in this exercise. 

**Do NOT proceed to the next task!** You can continue with the training course and perform the next task when your instructor feels it's appropriate given the class' training schedule. 

### Task 2 – Validate the Safe Links policy and blocked URL functionality

After having waited at least 30 minutes since completing Task 1, you will now test the blocked URL and the Safe Links policy that you created. There are several tests that you will perform. 

   - First, you will send two emails from Holly Dickson to the MOD Administrator - one that contains an unblocked URL and another that contains the blocked http://tailspintoys.com URL.
   - You will verify that both emails appear in Holly's Sent Items folder.
   - You will then log into the MOD Administrator's Outlook mailbox and verify that the email with the unblocked URL arrived in the MOD Administrator's Inbox and the email with the blocked URL never arrived. The fact that the system sent the email with the blocked URL but it never arrived in the MOD Administrators Inbox verifies the Blocked URL functionality worked. Messages that contain unblocked URLs are held until Safe Links scanning is finished. Messages are delivered only after Safe Links confirms the URLs are safe, which is the case with the email with the unblocked URL. 
   - You will then go back into Holly's Outlook mailbox and open the email in her Sent Items folder that contains the blocked URL. You will select the hyperlinked text and verify the Safe Links policy worked when you try to access this blocked site. Safe Links immediately checks the URL before opening the website. Since the URL is blocked, Safe Links returns a malicious website warning page.

1. On LON-CL1, in your Edge browser, you should still be logged into Microsoft 365 as **Holly Dickson**.

2. In your **Microsoft Edge** browser, select the **Home | Microsoft 365** tab and then in the column of app icons on the left side of the screen, select the **Outlook** icon. 

3. Holly Dickson's **Outlook** mailbox will open in a new tab in your browser, and Holly's **Inbox** will be displayed.
   
4. Select the **New mail** button at the top of the screen.

5. In the email form that appears, enter the following information:

    - To: You will be sending an email to the MOD Administrator, so enter **mod** in the **To** field and then select the **MOD Administrator** email address from the user list.

    - Add a subject: **Test email with an unblocked URL**

    - Body of the message: **This message is linked to an unblocked URL.**
  
6. Select the entire text string that you just added in the body of the message.

7. A row of formatting icons should appear. Select the **Link** icon, which depicts two half-ovals with a line in between. 

8. In the **Insert link** window that appears, the text that you highlighted in the body of the message should be displayed in the **Display as** field. In the **Web address (URL)** field, enter the following URL: **http://adatum.com/aboutus**.

9. Select **OK**. In the body of the email, the message should now be hyperlinked. 

10. Select the **Send** button. Select Holly's **Sent Items** folder to verify the message was sent.

11. Select the **New mail** button in the upper left part of the screen.

12. In the email form that appears in the right-hand pane, enter the following information:

    - To: You will be sending an email to the MOD Administrator, so enter **mod** in the **To** field and then select the **MOD Administrator** email address from the user list.

    - Add a subject: **Free stuff for Adatum users**

    - Body of the message: **Please click on me for free toys from Tailspin Toys.**

13. Select the entire text string that you just added in the body of the message.

14. A row of formatting icons should appear. Select the **Link** icon, which depicts two half-ovals with a line in between. 

15. In the **Insert link** window that appears, the text that you highlighted in the body of the message should be displayed in the **Display as** field. In the **Web address (URL)** field, enter the following URL: **https://tailspintoys.com/aboutus/freetoys**.

16. Select **OK**. In the body of the email, the message should now be hyperlinked. 

17. Select the **Send** button. Select Holly's **Sent Items** folder to verify the message was sent.

18. You now want to go the MOD Administrator's Inbox in Outlook and validate whether the blocked URL functionality that you configured worked on the two emails that you just sent from Holly to the MOD Administrator.<br/>

    To do this, you must first switch to the Client 2 VM (**LON-CL2**). 

19. At the end of Lab 2, you should have logged into LON-CL2 as the local **Admin** account (lon-cl2\admin). <br/>

    If you didn't do this, and you're still logged in as Laura Atkins from the end of Lab 2, then select **Ctrl+Alt+Delete**, select **Switch user**, and then log in as **LON-CL2\Admin** with a password of **Pa55w.rd**.

20. On **LON-CL2**, select the **Microsoft Edge** icon in the taskbar, maximize the window and then enter the following URL in the address bar: **https://outlook.office365.com**

21. In the **Pick an account** window, select **Use another account**, and then in the **Sign in** window, enter the username for the MOD Administrator account (**admin@xxxxxZZZZZZ.onmicrosoft.com**).

22. In the **Enter password** window, enter the MOD admin's password (either the Administrative password provided by your lab hosting provider if you were not required to change the MOD admnin's password the first time you signed in, or the New Administrative Password if you were) and select **Sign in**. 

23. In the MOD Administrator's **Inbox**, perform the following checks:  <br/>

       - Verify that you received the first email that Holly sent that contained the Subject line "**Test email with an unblocked URL**". This email showed that the email system is working, and that an email with an unblocked URL could successfully be sent and not be blocked by Safe Links since it isn't malicious. 

      - Next, verify that Holly's email with the Subject line "**Free stuff for Adatum users**" never arrived in the MOD Administrator's Inbox. Since you already verified from Holly's Sent Items folder that the email was sent, the fact that it never arrived verifies that the email was blocked due to the blocked URL.

24. You now want to go back to Holly's Outlook mailbox, open the email with the subject line "**Free stuff for Adatum users**" that's in Holly's Sent Items folder, and verify the Safe Links policy that you created is working.  <br/>

    To do this, you must first switch back to the Client 1 VM (**LON-CL1**). 

25. On LON-CL1, you should still be in the **Sent Items** folder in Holly's Outlook mailbox. Select the email with the subject line "**Free stuff for Adatum users**" to open the email message, and then select the hyperlinked message in the body of the email. 

26. A new tab should open in your **Edge** browser that attempts to take you to the **https://tailspintoys.com/aboutus/freetoys** site. The web page that appears should display the following warning message: **This website is classified as malicious.** <br/>

    **Note:** In the Safe Links policy that you created, you selected the option to have Safe Links check a list of known, malicious links whenever a user selects a link in an email. So when you selected this link in the email message to the http://tailspintoys.com URL that was on the blocked list, Safe Links returned the malicious website warning page. You just verified that the Safe Links policy that you created is working.

27. You should now prepare LON-CL2 for the next lab that will use it. Switch back to the Client 2 VM (**LON-CL2**). 

28. In LON-CL2, select the circle with the **MA** initials in the top corner of your Edge browser. In the **MOD Administrator** profile window that appears, select **Sign out**.

29. Once you are signed out of Outlook, the Edge browser should close if no other tabs were open. If other tabs were still open, close those tabs now so that your Edge browser closes. LON-CL2 is now ready for use in Lab 6.

30. Switch back to the Client 1 VM (**LON-CL1**). In your Edge browser, close the tab displaying **This website is classified as malicious.** Leave your Edge browser open and proceed to the next lab.


# End of Lab 5

