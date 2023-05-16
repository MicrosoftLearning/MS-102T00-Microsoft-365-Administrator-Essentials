# Learning Path 2 - Lab 2 - Exercise 2 - Monitor and Troubleshoot Microsoft 365  

In this exercise you will be introduced to some troubleshooting tools in Microsoft 365 that enable you to troubleshoot mail flow issues. You will then analyze Adatum’s Microsoft 365 service health by reviewing several of the key service health queries and reports that are available. You will conclude this exercise by reviewing how to submit a service request with the Microsoft Support team should you ever need assistance with a problem.

### Task 1 - Troubleshoot Mail Flow in Microsoft 365  

Holly Dickson, Adatum's new Microsoft 365 Administrator, wants to prepare herself for any potential mail flow problems that may occur within Adatum’s Exchange environment. As part of her pilot project, she has decided to create two test scenarios to analyze some of the troubleshooting options available to her. One email will be sent to an email address with an invalid domain (@alt.none). Another will be sent to an address with an invalid mailbox in a valid domain (@outlook.com). This task guides Holly though a variety of tools that she can use to troubleshoot different mail conflict scenarios. 

1. You should still be logged into LON-CL1 after having completed the prior exercise, and you should still be logged into Microsoft 365 as Holly Dickson.

2. In your **Microsoft Edge** browser, select the **Home | Microsoft 365** tab to display Holly's Microsoft 365 Home page, which should still be open (if not, navigate to **https://portal.office.com** and log in as **Holly@xxxxxZZZZZZ.onmicrosoft.com** (where xxxxxZZZZZZ is the tenant prefix provided by your lab hosting provider) with the **Microsoft 365 Tenant Password**).

3. In the **Welcome to Microsoft 365** page, select the **Outlook** icon in the column of app icons on the left. 

4. If you're automatically signed into Outlook using Holly's account, then proceed to the next step. However, if a **Pick an account** window appears, select Holly's account of **Holly@xxxxxZZZZZZ.onmicrosoft.com** (where xxxxxZZZZZZis the tenant prefix provided by your lab hosting provider). <br/>

	If an **Enter password** window appears, enter the same **Microsoft 365 Tenant Password** provided by your lab hosting provider for the tenant admin account (i.e., the MOD Administrator account) as Holly's password and select **Sign in**. <br/>

	If a **Stay signed in?** window appears, select the **Don't show this again** check box and select **Yes**.

5. Holly's **Inbox** will be displayed in Outlook. If a **Welcome** window appears, select the **X** in the upper-right corner of the window to close it. <br/>

	In Holly’s mailbox, at the top of the navigation pane, select the **New Mail** button to create a new email.

6. In this email, you will send the mail to an email address in which the domain (alt.none) is an invalid domain. In the email pane that appears, enter **user@alt.none** in the **To** field. In the drop-down menu that appears, select **Use this address: user@alt.none**. 

7. Enter **Testing invalid domain** in the **Subject** field and then send the email.  

8. Wait for the non-delivery report (NDR) message to appear in Holly’s Inbox, then double-click the message to open it in a new window. This will make it easier to copy the text of the message in the next step. 

9. In the message window, scroll down through the message until you reach the body of text that says **Diagnostic information for administrators**. Select the text in the body of the message starting AFTER **Diagnostic information for administrators** through the end of the message. With this text selected, press **Ctrl+C** to copy it to the clipboard, and then close the message window.

10. Open a new tab in your web browser and enter the following URL in the address bar: **https://testconnectivity.microsoft.com**. 

11. This opens the **Microsoft Remote Connectivity Analyzer** portal. In the navigation bar on the left, select **Message Analyzer**. This opens the **Message Header Analyzer** tool.

12. Take a moment to review the **Message Header Analyzer** tool. It consists of two sections: <br/>

	- In the top section, you will paste in the diagnostic data that you copied from the NDR email message.
	- In the bottom section, the tool will display its analysis of this data. 

13. In the **Message Analyzer Header** window, paste the NDR diagnostic data (right-click and select **Paste**, or press **Ctrl+V**) in the field that appears below the **Insert the message header you would like to analyze** row. Then select the **Analyze headers** button. 

14. SMTP message headers contain a wealth of information that allow you to determine the origins of a message and how it made its way through one or more SMTP servers to its destination. Here’s a quick summary of the information found in this header analysis: <br/>

	- **Summary section**: Displays the most important properties and total delivery time at a quick glance. Depending on the diagnostic data (for example, if a message was even sent), this section may or may not appear.

	- **Received headers section**: Displays the more important header properties and delivery time. Enables you to analyze the received headers and displays the longest delays quickly for each discovery of sources of message transfer delays.

	- **Other headers section**: Enables you to quickly detect where the longest message transfer delays occurred. You can sort all headers by occurrence number, name, or value.   

	The primary problem in this example (see the **Other headers** section, Hop 1) is that the DNS domain of the email address **(@alt.none**) does not exist. While you purposely entered an invalid domain for the purpose of this lab exercise, this error is normally caused by a typo in the recipient’s domain name that needs to be corrected to resolve the issue. 

15. Select the **Clear** option that appears to the right of the **Analyze headers** button; this will reset the Message Header Analyzer window. 

16. Select the **Mail - Holly Dickson - Outlook** tab in your browser. In Holly's mailbox, select **New mail** to create a new email.

17. In this email, you will send the mail to a non-existent mailbox in a valid domain (outlook.com). In the **To** field, enter an email address consisting of a random series of numbers followed by your name (for example, **nnnnnnnnYourName@outlook.com**). In the drop-down menu that appears, select **Use this address: nnnnnnnnYourName@outlook.com**.

18. Enter **Testing invalid mailbox** in the **Subject** field and then send the email.  

19. Wait for the non-delivery report (NDR) message to appear in Holly’s Inbox, then double-click the message to open it in a new window. <br/>
	
	**Note:** If you do not receive an NDR reply within a minute (or less) after sending the email, then someone has created that mailbox in the outlook.com domain. If this occurs, then send another email to a different mailbox address that you feel is completely bogus. If necessary, continue trying different email addresses until you receive an NDR reply.

20. In the window for the NDR reply, scroll down through the message until you reach the body of text that says **Diagnostic information for administrators**. Select the text in the body of the message starting AFTER **Diagnostic information for administrators** through the end of the message. With this text selected, press **Ctrl+C** to copy it to the clipboard, and then close the message window. 

21. Select the **Message Header Analyzer** tab in your browser. 

22. In the **Message Analyzer Header** window, paste the NDR diagnostic data in the field that appears below the **Insert the message header you would like to analyze** row, and then select **Analyze headers**.  <br/>

	**Note:** Review the diagnostic information and the time taken for the message to be rejected. In the prior email, the domain of the email address did not exist. In this email, Hop 1 in the **Other headers** section indicates the user's domain (outlook.com) was valid, but the user mailbox was unavailable. 

23. Close both the **Message Header Analyzer** tab and the **Microsoft Remote Connectivity Analyzer** tab in your Edge browser. 

24. Select the **Microsoft 365 admin center** tab. If you had closed this tab, then select the **Home | Microsoft 365** tab in your Edge browser, select the **App launcher** icon (the square made up of 3 rows of dots) that appears above the **Home** icon in the top left corner of the screen, and then in the **Apps** pane that appears, select **Admin**; this opens the **Microsoft 365 admin center** in a new browser tab. 

25. On the **Microsoft 365 admin center** page, in the navigation pane, select **Show all** (if necessary). 

26. Scroll down through the navigation pane, and under **Admin centers,** select **Exchange**. This will open the Exchange admin center in a new tab. <br/>

	- If a **Toolbar** window appears, select the **Next** button twice and then the **Finish** button to navigate through the three windows. 
	- If a **Learn about the new menu** window appears, select the X to close it.

27. In the **Exchange admin center**, in the navigation pane, select **Mail flow**, and then select **Message trace**. 

28. In the **Message trace** window, the **Default queries** tab is displayed by default. In this tab, select **+Start a trace** on the menu bar. 

29. In the **New message trace** pane that appears, both the **Senders** and **Recipients** fields are set to **All** be default. Holly wants to configure the trace to just look for email messages that she sent. In the **Senders** field, enter **Holly**. This displays the list of active users whose name starts with Holly. In the list of users that appears, select **Holly Dickson**.

30. Under the **Time range** section, select the slider bar below **1 day** (don't select the **1 day** heading; you must select on the slider bar itself). Note how the slider circle moved under **1 day**.

31. The drop-down arrow to the right of **Detailed search options** should be selected by default. This displays options such as Delivery status, Message ID, Direction, and others. If this information isn't displayed under **Detailed search options**, then select the drop-down arrow to expand this section.  <br/>

	Holly wants to customize the trace to look for failed messages. Select the **Delivery status** field, and in the drop-down menu that appears, select **Failed**.

32. Note the **Report type** option is set to **Summary report**. This is the report type that you want to create, so leave this option selected. At the bottom of the page, select the **Search** button. 

33. In the **Message trace search results** page that appears, if no failed message deliveries appear in the list, you may need to wait several minutes before selecting the **Refresh** button that appears above the item list. You should see the two failed email messages that Holly sent from Outlook - one to **user@alt.none**, and another to **nnnnnnnnYourName@outlook.com**.

34. Select the date and time values (which are hyperlinked) for the first failed message to view the properties pane for that message. This displays the sender, recipient, status, and error information, as well as the **How to fix it** instructions. Select the down arrows for the **Message events** and **More information** sections to view those sections. Once you've finished reviewing the message information, select the **X** in the upper right corner of the pane to close it. <br/>

	Repeat this step for the second failed message. 

35. In the **Message trace search results** window, note the navigation thread at the top of the screen (**Home > Message trace > Message trace search results**). Select the **Message trace** portion of this navigation thread to display the **Message trace** window. Leave this tab open for the next task.

36. In your Edge browser, close the **Mail - Holly Dickson - Outlook** tab, but leave the remaining tabs open for the next task.
  

### Task 2 - Monitor Service Health and Analyze Reports 

Adatum's CTO is concerned with the service health issues that have recently come to light throughout the organization. He has asked Holly to review several of the key service health queries and reports so that she becomes aware of the information that's available to help Adatum monitor its service health.

1. On the LON-CL1 VM, select the **User Details Panel - Microsoft 365 admin center** tab within your Edge browser. This tab contains the Microsoft 365 admin center. 

2. In the **Microsoft 365 admin center** navigation pane, select **Health** and then select **Service health**. 

3. On the **Service health** page, the **Overview** tab is displayed by default. Select the **Issue history** tab.  

4. In the **Issue history** tab on the **Service health** window, the default option is to display a list of items from the past 7 days (this filter option appears to the right of the **Search** field). In the list of service health incidents, select the **Title** for any entry in the list to see further details about the incident. Close the incident window when you’re done reviewing it. 

5. In the **Microsoft 365 admin center**, in the navigation pane, select **Reports**, and then select **Usage.** 

6. On the **Usage** page, scroll down and locate the **Active users - Microsoft 365 Services** chart. 

7. On the same row as this chart, view the **Email activity** chart.  <br/>

	‎**Note:** There may be little or no data shown due to the limited mailbox usage in the lab environment. 

8. Under the **Email activity** chart, select the **View more** button. This displays the **Exchange** report dashboard. At the top of the dashboard, the **Email activity** tab is displayed by default. Select the **Mailbox usage** tab that appears to the right of it.

9. The default mailbox usage that is initially displayed is **Past 30 days** (this usage factor appears on the far-right side of the row containing the **Mailbox usage** tab). Select the down-arrow that appears next to **Past 30 days** and select one of the other options that appear in the drop-down menu (**7 days**, **90 days**, and **180 days**) to see how the display changes. 

10. Scroll down below the charts to see mailbox details for each of the active users.

11. Scroll back to the top of the page. On the navigation thread at the top of the page (**Home > Usage > Exchange**), select **Usage** to return to the Usage Overview page. 

12. Review the various reports on this page. While there may be limited or no data for each report, you can at least get a feel for the type of reporting that's available. 

13. You now want to review the reports that are available in the **Exchange admin center**. In your browser, you should have the **Message trace - Exchange admin center** tab open from the prior task; if so, select it now. However, if you previously closed this tab, then in the **Microsoft 365 admin center**, under the **Admin centers** group in the navigation pane, select **Exchange**.

14. In the **Exchange admin center**, select **Reports** in the navigation pane, and then select **Mail flow**. 

15. In the **Mail flow reports** window, select **Inbound messages report** (this report has data to view; none of the other reports have data). Review the information displayed for this report. 

16. On the navigation thread at the top of the page (**Reports > Mail flow > Inbound messages report**), select **Mail flow** to return to this reporting page. 

17. In the **Mail flow reports** window, review the various reports that are available. 

18. Once you have finished reviewing several of the reports, close the **Exchange admin center** tab in your Edge browser but leave the other tabs open for the next task.
 

### Task 3 – Submit a Help Request to Microsoft Support

If an organization runs into a situation in Microsoft 365 where it needs assistance with a problem, it must submit a service request to the Microsoft Support team. As part of Adatum's pilot project, Holly Dickson and Patti Fernandez (Adatum's Service Support Administrator) have decided to submit a test request that does not require a call back. They are performing this task to become familiar with the service request process.

1. On LON-CL1, in the **Microsoft 365 admin center** tab of your Edge browser, select **Support** in the navigation pane, and then select **View service requests**. 

	**Note:** If the left-hand navigation pane has been minimized and only displays icons without any text, select the Navigation menu icon (the three horizontal lines) at the top of the navigation pane to expand it and display the accompanying text. <br/>

	The **Service request history** window displays any outstanding service request tickets. You should verify that no service request tickets appear on this page. <br/>

2. In the navigation pane, under the **Support** group, select **Help & Support**.

3. In the **How can we help?** pane that appears, select the **Message** field (which currently displays **Example: Can't install Office**) and type the following message: **Can't install Office**. Then select the forward arrow that appears next to the field. This displays self-help solutions with insights and recommended articles to assist with your request. 

4. Select one of the recommended articles. After reviewing the article, close the Edge browser tab containing the article. This returns you to the **Support article** pane. 

5. If you need further assistance and would like to speak to a Microsoft support agent, select the **headset** icon (the middle icon) at the top of the **Support article** pane to get help from a Microsoft support agent. Select the **headset** icon now.

6. In the **Contact support** pane that appears, do NOT enter any information; instead, just review the information that you would enter to complete this request in a real-world situation. You could also attach any necessary documents before selecting **Contact me** at the bottom of the page.   <br/>

	‎**IMPORTANT: Do NOT complete this form in your lab environment.** If you enter this request with the **Phone** option selected, you will receive a call from a Microsoft 365 support representative. We do not want to bother Microsoft Support specialists with calls from students in a training class. 
	
7. Select the **X** in the upper right-hand corner of the page to close the **Contact support** window.
	
8. Leave LON-CL1 and your Edge browser open for the next lab exercise.  


# Proceed to Lab 2 - Exercise 3
