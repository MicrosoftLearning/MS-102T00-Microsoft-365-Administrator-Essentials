# Learning Path 9 - Lab 9 - Exercise 1 - Implement Sensitivity labels with Microsoft Entra ID Protection

In your role as Holly Dickson, Adatum’s new Microsoft 365 Administrator, you have Microsoft 365 deployed in a virtualized lab environment. As you proceed with your Microsoft 365 pilot project, your next steps are to implement Sensitivity Labels with Microsoft Entra ID Protection at Adatum. In this lab, you will create and publish a label, and you will test a published label. However, in doing so, you won't test the label that you create in this lab. You will test a different label.

**Important:** When you publish a new sensitivity label and label policy, it can take them up to 24 hours to propagate through Microsoft 365. As such, you won't be able to test the label that you create in this lab. Instead, you will test a pre-existing sensitivity label named **Project - Falcon**. This pre-existing label is almost identical to the label that you will create, so you'll be able to see basically the same results had you been able to test the label that you created. 


### Task 1 – Install the Microsoft Entra ID Protection Unified Labeling client

To implement Sensitivity labels as part of your pilot project at Adatum, you must first install the Microsoft Entra ID Protection client from the Microsoft Download Center.

**Note:** While the Azure AD to Microsoft Entra ID rebranding is still ongoing, the Azure Information Protection client has not been rebranded as of this writing. It will eventually be rebranded to Microsoft Entra ID Protection client.

1. At the end of the prior lab, you were on LON-CL2. Switch to **LON-CL1**.  <br/>

	You should still be logged into LON-CL1 as the local **adatum\administrator** account, and in your Edge browser, you should still be logged into Microsoft 365 as **Holly Dickson**. 

2. In **Microsoft Edge**, open a new tab and enter (or copy and paste) the following URL in the address bar: **https://www.microsoft.com/en-us/download/confirmation.aspx?id=53018** <br/>

	This will start the download for the Azure Information Protection Unified Label client.

3. In the **Downloads** window that appears at the top right of the page, you will see the **AzInfoProtection_UI.exe** file being downloaded. Once the file has finished downloading, select the **Open file** link that appears below the file name.

4. The **Microsoft Azure Information Protection** wizard will open. If the wizard does not display on the desktop, select the icon for the wizard on the taskbar to display the wizard.

5. In the wizard, on the **Install the Azure Information Protection client** window that appears, clear (uncheck) the **Help improve Azure Information Protection by send usage statistics to Microsoft** check box and then select the **I agree** button.

6. If a **User Account Control notification** dialog box appears that asks whether the app is allowed to make changes to this device, select **Yes**.

7. Once the installation is complete, select **Close**.

8. In your Edge browser, close the **Download** tab that you opened in this task to download the Azure Information Protection client.

You have successfully installed the Azure Information Protection Unified Label client on the LON-CL1 VM.


### Task 2 – Enable sensitivity labels for files in SharePoint and OneDrive

In this exercise you will enable sensitivity labels for supported Office files and PDF files in SharePoint and OneDrive. When this feature is enabled, users see the **Sensitivity** button on the ribbon so they can apply labels. They also see any applied label name on the status bar. For SharePoint, users can also see and apply sensitivity labels from the details pane.

Enabling this feature also results in SharePoint and OneDrive being able to process the contents of Office files and optionally, PDF documents that have been encrypted by using a sensitivity label. The label can be applied in Office for the web, or in Office desktop apps, and uploaded or saved in SharePoint and OneDrive. Until you enable this feature, these services can't process encrypted files, which means that coauthoring, eDiscovery, data loss prevention, search, and other collaborative features won't work for these files.

You will first enable sensitivity labels for Office online files that are stored in SharePoint and OneDrive. You'll then enable support for PDFs.

**Note:** As with all tenant-level configuration changes for SharePoint and OneDrive, it takes about 15 minutes for the change to take effect.

1. On LON-CL1, in your Edge browser, you should still be logged into Microsoft 365 as **Holly Dickson**.

2. In your Edge browser, you should still have a tab open for the **Microsoft 365 admin center**. If not, open a new tab and enter the following URL: **https://admin.microsoft.com**.

3. On the **Microsoft 365 admin center**, if necessary, select **... Show all**. Select **Compliance** under the **Admin centers** group. This opens the Microsoft Purview portal in a new tab.

4. You will begin by enabling sensitivity labels for Office online files that are stored in SharePoint and OneDrive. <br/>

	In the **Microsoft Purview** portal, under the **Solutions** section in the navigation pane, select **Information protection**, and then select **Labels**.

5. On the **Labels** page, the following message should appear in the middle of the page: **Your organization has not turned on the ability to process content in Office online files that have encrypted sensitivity labels applied and are stored in OneDrive and SharePoint. You can turn on here, but note that additional configuration is required for Multi-Geo environments.** <br/>

	Below this message is a **Turn on now** button. Select this button.  <br/>

	**Note:** The command runs immediately and when the page is next refreshed, you no longer see the message or button.

6. You will now enable PDF protection for files in SharePoint and OneDrive. <br/>

	In the **Microsoft Purview** portal, under **Information protection** in the navigation pane, select **Auto-labeling**.

7. On the **Auto-labeling** page, you should see a **Protect PDFs with Auto-labeling** banner in the middle of the page. Select the **Protect PDFs with Auto-labeling** heading to turn on PDF protection for files in SharePoint and OneDrive. 

8. In the **Auto-labeling** dialog box that appears, select **Confirm** to confirm that you want to turn on PDF protection for files in SharePoint and OneDrive. 

	**Note:** The command runs immediately and when the page is next refreshed, you no longer see the **Protect PDFs with Auto-labeling** banner.

9. Leave your Edge browser open along with all the tabs. 


### Task 3 – Create a Sensitivity Label

In this exercise you will create a Sensitivity Label and add it to the default policy so that it’s valid for all users of the Adatum tenant.

1. On LON-CL1, in your Edge browser, you should still be logged into Microsoft 365 as **Holly Dickson**.

2. In your Edge browser, you should still have a tab open for the **Microsoft Purview** portal from the prior task. In the **Microsoft Purview** portal, under the **Information protection** group in the left-hand navigation pane, select **Labels**. 

3. On the **Labels** page, select the **+Create a label** option that appears on the menu bar in the middle of the screen. This initiates the **New sensitivity label** wizard.

4. In the **New sensitivity label** wizard, on the **Provide basic details for this label** page, enter the following information:

	- Name: **PII**
	
	- Display name: **PII**

	- Description for users: **Documents, files, and emails with PII**

	- Description for admins: **Documents, files, and emails with PII**

	- Label color: select one of the colors that you want to assign to your sensitivity labels

5. Select **Next**.

6. On the **Define the scope for this label** page, verify the **Items** check box is selected (select it now if necessary) and then select **Next**.

7. On the **Choose protection settings for labeled items** page, select both check boxes for **Apply or remove encryption** and **Apply content marking**, and then select **Next**.

8. On the **Encryption** page, you will define who can access items that have this label applied. Select the **Remove encryption if the file or email or calendar event is encrypted** option and then select **Next**.

9. On the **Content marking** page, set the **Content marking** toggle switch to **On**. This displays three options that enable you to customize how you want to mark files and emails. <br/>

	Select all three check boxes. Under each setting, select **Customize text**. This opens a pane to customize that particular setting. Enter the following information in the **Customize** pane for each option (select **Save** after entering the settings for each option): <br/>

	- **Add a watermark** 
		- Watermark text: **Sensitive - Do Not Share** (Hint: after entering this value, copy it (Ctrl+C) so that you can paste it (Ctrl+V) in the other two text settings)
		- Font size: **25**
		- Font color: **Blue**
		- Text layout: **Diagonal**
			
	- **Add a header** 
		- Header text: **Sensitive - Do Not Share**
		- font size: **25**
		- Font color: **Red**
		- Align text: **Center**
			
	- **Add a footer**
		- Footer text: **Sensitive - Do Not Share**
		- font size: **25**
		- Font color: **Red**
		- Align text: **Center**

10. On the **Content marking** page, select **Next**. 

11. On the **Auto-labeling for files and emails** page, set the **Auto-labeling for files and emails** toggle switch to **On**. This enables a series of options that you will update in the next steps.

12. Under **Detect content that matches these conditions**, select **+Add condition** and then select **Content contains**.

13. In the **Content contains** window, select the **Add** drop-down arrow and then select **Sensitive info types**.

14. In the **Sensitive info types** window, hover your mouse to the left of the **Name** column heading. Select the check box that appears, which automatically selects all the sensitive information types. Select **Add**, which will add all these sensitive information types to your label.

15. On the **Auto-labeling for files and emails** page, all of the sensitive information types that you selected will be displayed. Scroll to the bottom on the window and update the following settings:

	- When content matches these conditions: select **Automatically apply the Label**

	- Display this message to users when the label is applied: enter **Sensitive content has been detected and will be encrypted**.
		
16. Select **Next**.

17. On the **Define protection settings for groups and sites** page, leave both check boxes blank and select **Next**.

18. On the **Auto-labeling for schematized data assets (preview)** page, do not enable Auto-labeling for schematized data assets (preview). Select **Next**. 

19. On the **Review your settings and finish** page, review the information you entered. If any settings need to be corrected, select the corresponding **Edit** option and make any necessary changes. When all information appears correct, select **Create label**.

20. A **Client Error** dialog box should appear that states the generated rule blob for the label you are attempting to create is too long. The maximum size of sensitive information type selections you can make at one time per rule is **49152**. By selecting all the sensitive information types like you did in the **Sensitive info types** window a few steps back, you have exceeded this limit. <br/>

	**NOTE: We purposely had you select all the sensitive information types so that you would receive this error.** We wanted you to experience this error so that if it happens in your production environments, you will know why you received the error and how you can correct it.  <br/>

	To correct this issue, select **OK** in the **Client Error** dialog box, and then on the **Review your settings and finish** page, scroll down to the **Auto-labeling for files and emails** section and select **Edit**.
	
21. This should return you to the **Choose protection settings for labeled items** page in the wizard. Select **Next** on this page, select **Next** on the **Encryption** page, and then select **Next** on the **Content Marking** page. This will take you to the **Auto-labeling for files and emails** page. 

22. On the **Auto-labeling for files and emails** page, to the right of the **Content contains** condition, select the **trash can icon**. This will remove the existing **Content contains** condition for the **PII** label that you created. <br/>

	In the remaining steps, you will add a new condition that only contains two sensitivity information types rather than all the sensitivity information types like you did originally.

23. On the **Auto-labeling for files and emails** page, under **Detect content that matches these conditions**, select **+Add condition** and then select **Content contains**.

24. In the **Content contains** window, select the **Add** drop-down arrow and then select **Sensitive info types**.

25. In the **Sensitive info types** window, in the list of sensitive information types, only select the **ABA routing number** and the **U.S. Social security Number (SSN)** check boxes, and then select **Add**. Back on the **Auto-labeling for files and emails** page, both of these sensitive information types will appear. Select **Next**.

26. On the **Define protection settings for groups and sites** page, leave the two check boxes blank and select **Next**.

27. On the **Auto-labeling for schematized data assets (preview)** page, do not enable Auto-labeling for database columns. Select **Next**.

28. On the **Review your settings and finish** page, select **Create label**.

29. On the **Your sensitivity label was created** page, select the **Don't create a policy yet** option and then select **Done**. This returns you to the **Labels** page.

30. Now it's time to publish the **PII** label. On the **Labels** page, if the **PII** label does not appear in the list of labels, select **Refresh** on the menu bar. Once the **PII** label appears, select the check box that appears to the left of it. 

31. Select the **Publish label** option that appears in the menu bar above the list of labels. This initiates a **Create policy** wizard.

32. In the **Create policy** wizard, on the **Choose sensitivity labels to publish** page, the **PII** label is already listed, so select **Next**. 

33. On the **Assign admin units** page, select **Next** since you'll be assigning this PII policy to Adatum's full directory rather than just a select group of admin units.

34. On the **Publish to users and groups** page, you can choose whether to make your policy available to all users and groups, or you can limit the policy to selected users and groups. For this lab, you want to make the policy available to everyone. The **Users and groups** option is already selected by default (if not, then select it now). This will make your policy available to all users and groups. Select **Next**.  <br/>

	**Note:** When doing this in your real-world deployment, if you want to limit your policy to a select number of users or groups, then you would select **Edit** and make those selections. 

35. On the **Policy settings** page, select the **Users must provide a justification to remove a label or lower its classification** check box, and then select **Next**. 

36. On the **Apply a default label to documents** page, select **PII** in the drop-down menu that appears, and then select **Next**.

37. On the **Apply a default label to emails** page, select **PII** in the drop-down menu that appears, and then select **Next**.

38. On the **Apply a default label to meetings and calendar events** page, select **PII** in the drop-down menu that appears, and then select **Next**.

39. On the **Apply a default label to Fabric and Power BI content** page, select **PII** in the drop-down menu that appears, and then select **Next**.

40. On the **Name your policy** page, enter **PII Policy** in the **Name** field, and then enter (or copy and paste) the following description for this sensitivity label policy: **The purpose of this policy is to detect sensitive information such as ABA bank routing numbers and US social security numbers in emails and documents, and to encrypt this information when it's discovered. The user must provide an explanation for removing the classification label.** Select **Next**.

41. On the **Review and finish** page, review the information you entered. If anything needs to be corrected, select the corresponding **Edit** option and make the necessary corrections. When all information is correct, select **Submit**.

42. On the **New policy created** page, select **Done**.


### Task 4 – Assign a pre-existing sensitivity label to a document

As outlined in the instructions at the start of this lab, it isn't possible to immediately test the sensitivity label and label policy that you created in the previous task. This is because it takes up to 24 hours for a new label policy to propagate through Microsoft 365 and for its label to become visible in applications like Microsoft Word and Outlook.

Instead, you will test one of Microsoft 365's pre-existing sensitivity labels. For this lab, you will use the **Project - Falcon** sensitivity label, which is a Highly Confidential label. This label is similar to the label that you created in the prior task - the one exception being that it doesn't include a header or footer. Using this pre-existing label will give you a good idea as to how the label that you created would work at Adatum.

1. On LON-CL1, in your Edge browser, you should still be logged into Microsoft 365 as **Holly Dickson**.

2. You will first verify that existence of the **Project-Falcon** sensitivity label. 

2. To validate the **Project-Falcon** sensitivity label, you must first assign it to a document. Select the **Home | Microsoft 365** tab in your browser to return to the Microsoft 365 home page. Select the **Apps** icon on the left-side of the screen. On the **Apps** page that appears, right-click on the **Word** tile and select **Open in new tab**. 

3. In the **Word | Microsoft 365** tab, under the **Create new** section at the top of the page, select **Blank document**.

4. If a **Your privacy option** window appears, select **Close**.

5. If the Word ribbon displays icons for each feature but does not break the icons out by group, then select the down-arrow on the far right-side of the ribbon, and then under **Ribbon layout**, select **Classic ribbon**. This will switch the ribbon to the traditional ribbon style that is broken out by feature group (such as Undo, Clipboard, Font, Paragraph, Styles, and so forth).

6. In the **Word** document, type the following text: **Testing a sensitivity label on a document with personally identifiable information (PII); in this case, a U.S Social Security Number: 111-11-1111.**

7. Because you enabled Sensitivity labels at the start of this exercise, **Word** should display a **Sensitivity** group on the ribbon at the top of the page. Select the down arrow in the **Sensitivity** group. In the drop-down menu that appears, it should display the list of sensitivity label types. Select **Highly Confidential**, and then in the sub-menu that appears, select **Project - Falcon**. <br/>

	**Note:** After 24 hours, the label that you created in the prior task will appear in the Highly Confidential sub-manu, next to the Project-Falcon label. But for now, you will use the **Project - Falcon** label in its place.

8. In the document, note how the label applied a **CONFIDENTIAL - ProjectFalcon** watermark across the top of the document. The Project - Falcon label was configured just like the label that you created, where the watermark was supposed to appear diagonally across the middle of the page. So why does it appear towards the top of the page? The answer is that you are using **Word for the Web**, which by default displays it as you see here. To see how it will appear to someone reading the document, you must view the document in the **Reading View**, which you'll do now. <br/>

	Select the **View** tab and then in the Word ribbon, select **Reading View**. Note how the watermark appears diagonally across the middle of the document. This is how the watermark will appear to someone reading the document. Note that if you use the Word desktop app, it displays the watermark as designated by the label, which in this case would be just as you see it here in the Reading View. <br/>

	To exit Reading View, select **Edit Document** on the menu bar at the top of the page. In the drop-down menu that appears, select **Edit**.

9. In this first validation test, you're going to remove this sensitivity label from being applied to this document. One of the label policy options requires users to provide justification to remove a label or to select a lower classification label. You will now verify whether this setting is functioning properly. <br/>

	In the **Sensitivity** group in the Word ribbon, select the down arrow. In the drop-down menu that appears, note that a check mark appears next to **Highly Confidential**. Hold your mouse over **Highly Confidential** to display the sub-menu. Notice how a check mark appears next to **Project - Falcon**. The check marks identify the current label being applied to the document.  <br/>
 
	To remove the label from this document, select the **Project - Falcon** label that appears in this drop-down menu.
	
10. In the **Justification Required** window that appears, select the **Other (explain)** option. In the **Explain why you're changing this label** field, enter **Testing what happens when a label is removed from a document** and then select **Change**.

11. Note how the watermark in the document has disappeared. In the **Sensitivity** group in the Word ribbon, select the down arrow. In the drop-down menu that appears, note that while **Highly Confidential** > **Project - Falcon** is displayed, no check marks appear next to them. This indicates the sensitivity label is no longer being applied to this document.  

12. To re-apply the sensitivity label to the document, select **Highly Confidential** > **Project - Falcon** in the drop-down menu. Note how the watermark reappears in the document.

13. You will now save the document so that you can share it in the next task. A document name field that contains a drop-down arrow appears at the top-left corner of the page, to the right of the Word icon (Word may display **Document** or **Document1** as the temporary file name). Select the drop-down arrow. In the drop-down menu that appears, confirm the file **Location** says **Holly Dickson > Documents**. <br/>

	In the **File Name** field, rename the file to **ProtectedDocument1** and then select outside of this file name menu (select inside the document). Note the new name assigned to the file appears in the title bar. 

14. Leave the **ProtectedDocument1** tab open displaying the document. You will return to this document in the next task to share the document with Joni Sherman.

You have just successfully created a Word document containing the Highly Confidential label policy titled Project - Falcon. 


### Task 5 – Protect a document using Microsoft Entra ID Protection

In the prior task, you created a Word document and protected it with the **Project - Falcon** sensitivity label. This label inserted a watermark in the document. In this task, you will share the document you created with Joni Sherman, and you will restrict Joni to "View only" permission. This will allow you to see how Microsoft Entra ID Protection protects the document based on the parameters that you configure.

To verify whether the protection that you assigned to the document works, you will first email the document to two persons - to Joni Sherman and to your own personal email address. You will then verify that Joni can only view the document and not edit it, and you will verify that you can't access the document since it was not shared with you. Finally, you will change permission on the document so that Joni can edit it, and you will email this updated document to her for testing. The purpose of the two emails to Joni, one with a document link that provides read-only access and another with a document link that provides the ability to edit the document, is to see how Microsoft Entra ID Protection can provide various levels of document protection. 

1. On LON-CL1, in your Edge browser, you should still be logged into Microsoft 365 as **Holly Dickson** from the prior task with the **Word** tab open.

2. In your Edge browser, select the **Apps | Microsoft 365** tab. 

3. In the **Apps** page, right-click on the **Outlook** tile and select **Open in new tab**. This opens Holly's mailbox in Outlook on the web in a new browser tab. 

4. In **Outlook on the Web**, select **New mail** in the upper left part of the screen.

5. In the right-hand pane, enter the following information in the email form:

	- To: Enter **Joni** and then select **Joni Sherman** from the user list. 

	- CC: Enter your own personal email address (do NOT enter Holly's email address; instead, enter your own personal email address), and then select the **Use this address: <your email address>** message that appears

	- Add a subject: **Protected Document Test - View only permission**

	- Body of the message: enter **Open the protected document attached to this email and try to change it.**

6. In the body of the message, under the text you added in the previous step, you will attach a link to the document that you created in the prior task. However, to do so, you must first share the document with Joni Sherman, and when doing so, you will apply restricted **View only** permissions. To do so, you must leave this email and return to your document and share it with Joni. Once you copy the link that's created during the sharing process, you will return to this email and paste in the link. <br/>

	In your Edge browser, select the **ProtectedDocument1** tab, which should still be displaying the document that you created in the prior task. At the top-right side of the page, below Holly Dickson's name and initials, select the **Share** button. In the drop-down menu that appears, select **Share**.

7. In the **Share "ProtectedDocument1"** window that appears, select the gear (**Link settings**) icon that appears next to the **Copy link** button. 

8. On the **Link settings** window that appears, select the **People you choose** option.
	
9. Under **More settings**, the current option is **Can edit**. You plan to share this document with Joni Sherman, but you only want Joni to be able to view the document. To make this permissions change, select **Can edit**. In the menu that appears, review the available options. You can see that **Can edit** has a check mark next to it, which indicates this is the current setting. To limit Joni to read-only permission, select **Can view** and then select **Apply**.

10. This returns you to the **Share "ProtectedDocument1"** window. Enter **Joni** in the **Add a name, group, or email** Field. A list of users whose name starts with **Joni** should appear. Select **Joni Sherman**.

11. On the **Share "ProtectedDocument1"** window, hover your mouse over the "eye" icon that appears to the right of Joni's name. Doing so should display **Can view**, which is the current setting that you assigned to her for this document. The "eye" icon is the designation for "Can view". Select the **Copy link** button. 

12. Once the **Link copied** message appears at the bottom of the **Share "ProtectedDocument1"** window, then select the X in the upper-right corner of the window to close it.

13. In your Edge browser, select the **Mail - Holly Dickson -Outlook** tab to return back to your email message. In the body of the message, under the text you added earlier, paste (Ctrl+V) in the link to the shared document that you just copied to your clipboard. A link for the file named **ProtectedDocument1.docx** should appear. 

14. Select **Send**.

15. A **Recipients can't access links** message should appear. This message is a result of Microsoft Entra ID Protection recognizing the fact that you included your personal email address in the email, which doesn't have permission to access the document. For the purpose of this lab test, select **Send anyway**.

16. Switch to **LON-CL2**. 

17. On **LON-CL2**, you should be logged into **Outlook on the Web** as **Lynne Robbins** from the previous lab exercise. Sign out as Lynne.

18. In your Edge browser, close all tabs except for the **Sign out** tab. In this tab, enter the following URL in the address bar: **https://outlook.office365.com** 

19. In the **Pick an account** window, select **Use another account**.

20. In the **Sign in** window, enter **JoniS@xxxxxZZZZZZ.onmicrosoft** (where xxxxxZZZZZZ is the tenant prefix provided by your lab hosting provider) and then select **Next**.

21. On the **Enter password** window, enter the **User Password** provided by your lab hosting provider and then select **Sign in**. If required, complete the MFA sign-in process.

22. If a **Welcome** window appears, select the X to close it.

23. In Joni’s **Inbox** in **Outlook on the Web**, you should see the email that Holly just sent whose Subject line indicates the document has View only permission. Open this email.

24. In the email, select the attached file to open it.

25. In the **Your privacy option** window that appears, select **Close**. The document opens in **Word on the Web** in a new browser tab titled **ProtectedDocument1.docx** tab. Note how the document appears in the Reading View in **Word on the Web**. This is Joni's indication that she has View only permission and can't edit the document. To verify this, try to select into the the document. Note the message that appears indicating: **Read only. This document is read-only.** Note the watermark specified in the **Project - Falcon** policy. <br/>

	Once you have finished reviewing the document, close the **ProtectedDocument1.docx** tab. 

26. You will now test what happens when you attempt to open the document that was sent to your personal email address. Use your mobile phone or classroom PC to access your personal mailbox. Open the email that Holly just sent to your personal email address, and then attempt to open the attached file. 

27. Since you don't have permission to access the document, a **Pick an account** window should appear. In a real-world scenario, you could optionally sign in with an account that has permission to access the file, or request access from the **Holly@xxxxxZZZZZZ.onmicrosoft.com** account. <br/>

	For the purpose of this test, you just verified that you can't access the file because it wasn't shared with you. You also verified that Joni was only able to view the file, but not edit it. You will now change the Share permissions on the file by allowing Joni to edit it. You will do so to see how this experience differs from the one you just completed. 

28. Switch to **LON-CL1**. 

29. On LON-CL1, in your Edge browser, you should still be logged into Microsoft 365 as **Holly Dickson**, and you should have tabs open for both **Word** and **Outlook**. Select the **Mail - Holly Dickson - Outlook** tab. 

30. In Holly's mailbox, create another email to Joni Sherman. Do NOT include your personal email address in the CC line. Enter the following information in the email form:

	- To: Enter **Joni** and then select **Joni Sherman** from the user list. 

	- CC: leave blank

	- Add a subject: **Protected Document Test - Edit permission**

	- Body of the message: enter **Open the protected document attached to this email and try to change it.**

31. Just as with the prior email, you must now share the document with Joni, but this time with Edit permission. To do so, perform the following steps: <br/>

	- Select the **ProtectedDocument1** tab in your browser and then on the right-side of the menu bar select the **Share** button. In the drop-down menu that appears, select **Share**. 
	- In the **Share "ProtectedDocument1"** window, enter **Joni** in the **Add a name, group, or email** field and then select **Joni Sherman**.
 	- To the right of Joni's name is a pencil (**Can edit**) icon. This is the default permission when sharing a document. Select the **Copy link** button to see what happens.
 	- Note the **Link copied** message that appears. The message indicates that anyone can edit the document, even though you specifed Joni's name. This isn't what you want, which is to limit Joni as the only person who can edit it. To put that restriction in place, select the gear (**Link settings**) icon next to the **Copy link** button. 
	- On the **Link settings** window that appears, select the **People you choose** option. This option is the key to limiting the permission to selected users. 
	- Under **More settings**, if **Can edit** appears, then select **Apply**. However, if **Can view** appears, then select **Can view**, and in the menu that appears, select **Can edit** and then select **Apply**. 
	- In the **Share "ProtectedDocument1"** window, select the **Copy link** button.
	- Note the **Link copied** message that appears. This time the message indicates that only the people that you specify can edit the document. In this case, editing will be limited to Joni, since she's the only person that you specified. 
	- Select the **Mail - Holly Dickson - Outlook** tab in your browser and then paste the link into the body of the email message. 

32. Select **Send**.

33. Switch to **LON-CL2**. 

34. On **LON-CL2**, you should still be logged into **Outlook on the Web** as **Joni Sherman**. In Joni’s **Inbox**, you should see the email that Holly just sent whose Subject line indicates the document has Edit permission. Open this email.

35. In the email, select the attached file to open it.

36. When Joni had View only permission, the document opened in the Reading View pane. As such, Joni couldn't edit the document. This version of the document provides Joni with Edit permission, so this time the document should open in Word in normal edit mode. Verify that you can enter text in the document. 

	**Note:**  In this task, you just verified that Microsoft Entra ID Protection protected the document based on the PII policy parameters that you configured. When Joni was assigned View only permission, the document opened in the Reading view and she was unable to change it. When Joni was assigned Edit permission, the document opened in Word and she was able to change it. And since Holly didn't share the document with you, you couldn't open it when she sent the document in an email to your personal mailbox. 

## End of Lab 9


# Congratulations! You have just completed the final lab in this course.

