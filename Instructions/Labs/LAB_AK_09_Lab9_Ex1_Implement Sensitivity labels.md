# Learning Path 9 - Lab 9 - Exercise 1 - Implement Sensitivity labels with Azure Information Protection Unified Labels client

In your role as Holly Dickson, Adatum’s new Microsoft 365 Administrator, you have Microsoft 365 deployed in a virtualized lab environment. As you proceed with your Microsoft 365 pilot project, your next steps are to implement Sensitivity Labels with Azure Information Protection (AIP) at Adatum. In this lab, you will create and publish a label, and you will test a published label. However, in doing so, you won't test the label that you create in this lab. You will test a different label.

**IMPORTANT:** If you recall, back on the first day of this class, you ran a lab setup script that created and published a sensitivity label and sensitivity label policy. Running that script was necessary to support this lab due to a timing issue with sensitivity labels. Once you publish a label policy, it takes 24 hours for the published label policy to propagate through Microsoft 365. As such, you won't be able to test the label and label policy that you create and publish in this lab.

To address this timing issue, you ran that PowerShell script back on day 1 to create and publish a sensitivity label and label policy. Now that you've reached this lab, that label policy will have propagated through the system, and you'll be able to test it.

Because we want you to gain experience creating and publishing a label and label policy using the Microsoft 365 UI, you will still create a sensitivity label and label policy in this lab. However, when you perform the tasks to test the label and label policy, you won't test the ones that you created and published in the UI, since that label and label policy won't be available to test for 24 hours. Instead, you will test the label and label policy that you created and published using the script that you ran back on day 1 of this class.


### Task 1 – Install the Azure Information Protection Unified Labeling client

To implement Sensitivity labels as part of your pilot project at Adatum, you must first install the AIP client from the Microsoft Download Center.

1. At the end of the prior lab, you were on LON-CL2. Switch to **LON-CL1**.  <br/>

	You should still be logged into LON-CL1 as the local **adatum\administrator** account, and in your Edge browser, you should still be logged into Microsoft 365 as **Holly Dickson**. 

2. In **Microsoft Edge**, open a new tab and enter (or copy and paste) the following URL in the address bar: **https://www.microsoft.com/en-us/download/confirmation.aspx?id=53018** <br/>

	This will start the download for the AIP Unified label client.

3. In the Microsoft download center tab, on the notification bar at the bottom of the page, you will see the **AzInfoProtection_UI.exe** file being downloaded. Once the file has finished downloading, select the **Open file** link that appears below the file name.

4. The **Microsoft Azure Information Protection** wizard will open. If the wizard does not display on the desktop, select the icon for the wizard on the taskbar to display the wizard.

5. In the wizard, on the **Install the Azure Information Protection client** page, clear (uncheck) the **Help improve Azure Information Protection by send usage statistics to Microsoft** check box and then select the **I agree** button.

6. If a **User Account Control notification** dialog box appears that asks whether the app is allowed to make changes to this device, select **Yes**.

7. Once the installation is complete, select **Close**.

8. In your Edge browser, close the **Download** tab that you opened in this task to download the Azure Information Protection client.

You have successfully installed the AIP Unified Label client on the Client 1 VM.


### Task 2 – Create a Sensitivity Label

In this exercise you will create a Sensitivity Label and add it to the default policy so that it’s valid for all users of the Adatum tenant.

1. On LON-CL1, in your Edge browser, you should still be logged into Microsoft 365 as **Holly Dickson**.

2. In your Edge browser, you should still have a tab open for the **Microsoft 365 admin center**. If not, open a new tab and enter the following URL: **https://admin.microsoft.com**.

3.  On the **Microsoft 365 admin center**, if necessary, select **... Show all**. Select **Compliance** under the **Admin centers** group.

4. On the **Microsoft Purview** portal, in the left-hand navigation pane, select **Information protection** and then select **Labels**. 

5. On the **Labels** page, a warning message is displayed in the middle of the page indicating: **Your organization has not turned on the ability to process content in Office online files that have encrypted sensitivity labels applied and are stored in OneDrive and SharePoint. You can turn on here, but note that additional configuration is required for Multi-Geo environments.** <br/>

    Select the **Turn on now** button that appears on the right side of this message. This will enable Adatum to apply the Sensitivity labels inside its Microsoft 365 environment. <br/>

    Note how the message has now changed to indicate: **You can now create sensitivity labels with privacy and access control settings for Teams, SharePoint sites, and Microsoft 365 Groups.**	

6. On the **Labels** page, select the **+Create a label** option that appears on the menu bar in the middle of the screen, below the previous message. This initiates the **New sensitivity label** wizard.

7. In the **New sensitivity label** wizard, on the **Name and tooltip** page, enter the following information:

	- Name: **PII**
	
	- Display name: **PII**

	- Description for users: **Documents, files, and emails with PII**

	- Description for admins: **Documents, files, and emails with PII**

	- Label color: select one of the colors that you want to assign to your sensitivity labels

8. Select **Next**.

9. On the **Define the scope for this label** page, verify the **Items** check box is selected (select it now if necessary) and then select **Next**.

10. On the **Choose protection settings for labeled items** page, select both check boxes for **Apply or remove encryption** and **Apply content marking**, and then select **Next**.

11. On the **Encryption** page, you will define who can access items that have this label applied. Select the **Remove encryption if the file or email is encrypted** option and then select **Next**.

12. On the **Content Marking** page, set the **Content Marking** toggle switch to **On**. This displays three options that enable you to customize how you want to mark files and emails. <br/>

	Select all three check boxes. Under each setting, select **Customize text**. This opens a pane to customize that particular setting. Enter the following information in the **Customize** pane for each option (select **Save** after entering the settings for each option): <br/>

	- **Add a watermark** 
		- Watermark text: **Sensitive - Do Not Share** (Hint: after entering this value, copy it so that you can paste it in the other two text settings)
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

13. On the **Content Marking** page, select **Next**. 

14. On the **Auto-labeling for files and emails** page, set the **Auto-labeling for files and emails** toggle switch to **On**. This enables a series of options that you will update in the next steps.

15. Under **Detect content that matches these conditions**, select **+Add condition** and then select **Content contains**.

16. In the **Content contains** window, select the **Add** drop-down arrow and then select **Sensitive info types**.

17. In the **Sensitive info types** window, hover your mouse to the left of the **Name** column heading. Select the check box that appears, which automatically selects all the sensitive information types. Select **Add**, which will add all these sensitive information types to your label.

18. On the **Auto-labeling for files and emails** page, all of the sensitive information types that you selected will be displayed. Scroll to the bottom on the window and update the following settings:

	- When content matches these conditions: select **Automatically apply the Label**

	- Display this message to users when the label is applied: enter **Sensitive content has been detected and will be encrypted**.
		
19. Select **Next**.

20. On the **Define protection settings for groups and sites** page, leave both check boxes blank and select **Next**.

21. On the **Auto-labeling for schematized data assets (preview)** page, do not enable Auto-labeling for schematized data assets (preview). Select **Next**. 

22. On the **Review your settings and finish** page, review the information you entered. If any settings need to be corrected, select the corresponding **Edit** option and make any necessary changes. When all information appears correct, select **Create label**.

23. An **Error** dialog box should appear that states the generated rule blob for the label you are attempting to create is too long. The maximum size of sensitive information type selections you can make at one time per rule is **49152**. By selecting all the sensitive information types like you did in the **Sensitive info types** window a few steps back, you have exceeded this limit. <br/>

	**NOTE: We purposely had you select all the sensitive information types so that you would receive this error.** We wanted you to experience this error so that if it happens in your production environments, you will know why you received the error and how you can correct it.  <br/>

	To correct this issue, select **OK** in the **Error** dialog box, and then on the **Review your settings and finish** page, scroll down to the **Auto-labeling for files and emails** section and select **Edit**.
	
24. This will return you to the **Choose protection settings for labeled items** page in the wizard. Select **Next** on this page, select **Next** on the **Encryption** page, and then select **Next** on the **Content Marking** page. This will take you to the **Auto-labeling for files and emails** page. 

25. On the **Auto-labeling for files and emails** page, to the right of the **Content contains** condition, select the **trash can icon**. This will remove the existing **Content contains** condition for the **PII** label that you created. <br/>

	In the remaining steps, you will add a new condition that only contains two sensitivity information types rather than all the sensitivity information types like you did originally.

26. On the **Auto-labeling for files and emails** page, under **Detect content that matches these conditions**, select **+Add condition** and then select **Content contains**.

27. In the **Content contains** window, select the **Add** drop-down arrow and then select **Sensitive info types**.

28. In the **Sensitive info types** window, in the list of sensitive information types, this time only select the **ABA routing number** and the **U.S. Social security Number (SSN)** check boxes, and then select **Add**. Back on the **Auto-labeling for files and emails** page, both of these sensitive information types will appear. Select **Next**.

29. On the **Define protection settings for groups and sites** page, leave the two check boxes blank and select **Next**.

30. On the **Auto-labeling for schematized data assets (preview)** page, do not enable Auto-labeling for database columns. Select **Next**.

31. On the **Review your settings and finish** page, select **Create label**.

32. On the **Your sensitivity label was created** page, choose **Don't create a policy yet** and then select **Done**.

33. Now it's time to publish the **PII** label. On the **Information protection** window, the **Labels** tab is displayed by default. In the list of labels, if the **PII** label does not appear, select **Refresh** on the menu bar. Once the **PII** label appears, select the check box that appears to the left of it. 

34. Select the **Publish label** option that appears in the menu bar above the list of labels. This initiates a **Create policy** wizard.

35. In the **Create policy** wizard, on the **Choose sensitivity labels to publish** page, the **PII** label is already listed, so select **Next** and select **Next** for **Assign admin units (preview)**.

36. On the **Publish to users and groups** page, you can either select **All** users and groups, or you can select specific users and groups. Select **Choose user or group**.

37. A **Users and groups** pane appears that displays all the Adatum users and groups. Hover your mouse to the left of the **Name** column heading and select the check box that appears. This will automatically select all the check boxes. Select **Done**.

38. On the **Publish to users and groups** page, select **Next**.

39. On the **Policy settings** page, select the **Users must provide a justification to remove a label or lower its classification** check box, and then select **Next**. 

40. On the **Apply a default label to documents** page, select **PII** in the drop-down menu that appears, and then select **Next**.

41. On the **Apply a default label to emails** page, select **PII** in the drop-down menu that appears, and then select **Next**.

42. On the **Apply a default label to Power BI content** page, select **PII** in the drop-down menu that appears, and then select **Next**.

43. On the **Apply a default label to meetings and calendar events** page, select **PII** in the drop-down menu that appears, and then select **Next**.

43. On the **Name your policy** page, enter **PII Policy** in the **Name** field, and then enter (or copy and paste) the following description for this sensitivity label policy: **The purpose of this policy is to detect sensitive information such as ABA bank routing numbers and US social security numbers in emails and documents, and to encrypt this information when it's discovered. The user must provide an explanation for removing the classification label.** Select **Next**.

44. On the **Review and finish** page, review the information you entered. If anything needs to be corrected, select the corresponding **Edit** option and make the necessary corrections. When all information is correct, select **Submit**.

45. On the **New policy created** page, select **Done**.


### Task 3 – Assign a Sensitivity Label to a document

As the instructions at the start of this lab indicated, you can't test the sensivity label and label policy that you just created in the prior task. It will take up to 24 hours for that label policy to propagate through Microsoft 365 before its label appears in Microsft Word, Outlook, and so on. 

**Important:** The label and label policy that you will test in these next two tasks will be the label and label policy that were created when you ran the PowerShell script in Lab 1 on the first day of class. 

**Note:** The label and label policy that you created in the prior task  have the same exact settings as the label and label policy that were created when you ran the PowerShell script in Lab 1. The only difference between the two labels and the two label policies should be their names. The names of these labels and label policies are:

- The label that you created in the prior task was titled **PII**. 
- The label that was created by the script that you ran in Lab 1 was titled **PII - V1**. 
- The label policy that you created in the prior task was titled **PII Policy**. 
- The label policy that was created by the script that you ran in Lab 1 was titled **PII Policy - V1**. 

As you test the **PII - V1** label and the **PII Policy - V1** label policy in these next two tasks, you should see the same results that you configured in the **PII** label and **PII Policy** label policy. 

1. On LON-CL1, in your Edge browser, you should still be logged into Microsoft 365 as **Holly Dickson**.

2. To validate the sensitivity label that you created and published when you ran the PowerShell script in Lab 1 on the first day of class, you must first sign out of Microsoft 365 as Holly and sign back in as Alex Wilber. <br/>

	In your Edge browser, select the **Microsoft 365 admin center** tab, and then select the circle with Holly Dickson's HD initials in the upper right corner of the screen. In the **Holly Dickson** window, select **Sign out**.

3. Once you are signed out, close all the tabs in your Edge browser except for the **Sign out** tab.

4. In the **Sign out** tab, enter the following URL in the address bar: **https://portal.office.com/** 

5. In the **Pick an account** window, select **Use another account**.

6. In the **Sign in** window, enter **AlexW@xxxxxZZZZZZ.onmicrosoft.com** (where xxxxxZZZZZZ is the tenant prefix provided by your lab hosting provider) and then select **Next**.

7. On the **Enter password** window, enter the same **Microsoft 365 Tenant Password** provided by your lab hosting provider for the tenant admin account (i.e. the MOD Administrator account) and then select **Sign in**.

8. If a **Get your work done with Office 365** window appears, select the X to close it.

9. On the **Microsoft Office Home** tab, select the **Word** icon in the column of app icons on the left-side of the screen. This will override the **Microsoft Office Home** tab by opening Microsoft Word Online in this same tab. <br/>

	**Note:** In the next task, you will return back to the **Microsoft Office Home** tab by selecting the **Back** arrow at the top of this **Word** tab.

10. In the **Word** tab, under the **Create new** section at the top of the page, select **Blank document**.

11. If a **Your privacy option** window appears, select **Close**.

12. If the Word ribbon displays icons for each feature but does not break the icons out by group, then select the down-arrow on the far right-side of the ribbon, and then under **Ribbon layout**, select **Classic ribbon**. This will switch the ribbon to the traditional ribbon style that is broken out by feature group (such as Undo, Clipboard, Font, Paragraph, Styles, and so forth).

13. In the **Word** document, type **Testing personally identifiable information (PII).**

14. Because you enabled Sensitivity labels at the start of this exercise, and since the label you created by running the script on day 1 of the course has fully propagated through Microsoft 365, Word should display a **Sensitivity** group on the ribbon at the top of the page. 

	Select the down arrow in the **Sensitivity** group. In the drop-down menu that appears, it should display the **PII - V1** label the script created and published. Since the **PII - V1** label is enabled for this document, a check mark is displayed next to **PII - V1**. <br/>
	
	In this first validation test, you're going to attempt to remove this sensitivity label from being applied to this document. When you created the **PII Policy - V1** policy and **PII** label in the prior task, the same options you selected were applied to the **PII Policy - V1** policy and **PII - V1** label by the Lab 1 script. One of the label policy options requires users to provide justification to remove a label or to select a lower classification label. You will now verify whether this setting is functioning properly. <br/>
	
	To remove the label from this document, select the **PII - V1** label that appears in this drop-down menu.
	
15. In the **Justification Required** window that appears, select the **Other (explain)** option. In the **Explain why you're changing this label** field, enter **Testing what happens when a label is removed** and then select **Change**.

16. In the **Sensitivity** group in the Word ribbon, select the down arrow. In the drop-down menu that appears, note that while **PII - V1** is displayed, it no longer has a check mark displayed next to it. This indicates the **PII - V1** sensitivity label is no longer being applied to this document.  

17. To re-apply the sensitivity label to the document, select **PII - V1** in the drop-down menu. Once again select the drop-down arrow in the **Sensitivity** group. The drop-down menu that appears should display the **PII - V1** label, and it should display a check mark next to it that indicates it is being applied to this document.

18. In the Word document, enter **111-11-1111** below the previous line of text that you entered. This number is the same format as a U.S. Social Security Number.

	**Note**: In Word for the Web, the custom header, footer, and watermark specificed in the **PII - V1** policy do not display by default. To view the custom header, footer, and watermark, select the **View** tab and then in the menu select **Reading View**. Alternatively, in the real world, you could use the Word Desktop App which would display these by default.

	To exit reading view, select the **Edit Document** drop-down menu and then select **Edit**.

19. You will now save the document. On the title bar, to the right of Word, select **Document1**.  In the drop-down menu that appears, confirm the file **Location** says **Alex Wilber > Documents**. <br/>

	In the **File Name** field, rename the file to **ProtectedDocument1** and then select outside of this file name menu (select inside the document). Note the new name assigned to the file in the title bar.

20. On the right-side of the menu bar, select the **Share** button. In the drop-down menu that appears, select **Share**.

21. In the **Send link** window that appears, select **Anyone with the link can edit**. <br/>

	On the **Sharing settings** page that appears, select **People you choose**. Under **More settings**, select **Can edit**. In the menu that appears, select **Can view**, and then select **Apply**. <br/>

	On the **Send link** window, enter **Joni** in the **To: Name, group or email** field. A list of users whose name starts with **joni** should appear. Select **Joni Sherman**. <br/>

	Under the **Copy link** section, select the **Copy** button. 

22. Close the **Link to 'ProtectedDocument1' copied** window that appears.

You have just successfully created an AIP protected Word document that is read-only protected. The document is accessible only by its creator, Alex Wilber, and by Joni Sherman (with Read-only permission), to whom the document was shared.


### Task 4 – Verify your Sensitivity Label policy

In the prior task, you created a Word document and protected it with a sensitivity label. The **PII - V1** label should have inserted a watermark in the document, and it should have restricted permissions on the document. To verify whether the protection that you assigned to the document works, you will first email the document to Joni Sherman and to your own personal email address. You will then test what functionality is possible for both Joni and Alex Wilber.

1. On LON-CL1, in your Edge browser, you should still be logged into Microsoft 365 as **Alex Wilber** from the prior task with the **Word** tab open. 

	**Note**: If the copied link from the prior exercise is no longer in your clipboard, you will need to re-copy the link. To do so, select the **Word** tab, and then on the right-side of the menu bar select the **Share** button. In the drop-down menu that appears, select **Manage Access**. Under **Links giving access** you can copy the link created in the previous task.

2.  In your Edge browser, select the **Word** tab and then select the **Back** arrow. This should display the **Microsoft Office Home** tab. 

3. In the **Microsoft Office Home** tab, select the **Outlook** icon in the column of app icons on the left-side of the screen. This opens Outlook on the web in a new tab. 

4. In **Outlook on the web**, select **New Mail** in the upper left part of the screen.

5. In the right-hand pane, enter the following information in the message form:

	- To: Enter **Joni** and then select **Joni Sherman** from the user list. 

	- CC: Enter your own personal email address (do NOT enter Holly's email address; instead, enter your own personal email address)

	- Add a subject: **Protected Document Test**

	- Body of the message: enter **If you can open the protected and restricted document attached to this email, then try to change it.**

6. In the body of the message, under the text you added in the previous step, paste the link copied to your clipboard from the prior task. A link for the file named **ProtectedDocument1.docx** should appear.

8. Select **Send**.

9. Switch to **LON-CL2**. 

10. On **LON-CL2**, you should be logged into **Outlook on the Web** as **Lynne Robbins** from a previous lab exercise. Sign out as Lynne.

11. In your Edge browser, close all tabs except for the **Sign out** tab. In this tab, enter the following URL in the address bar: **https://outlook.office365.com** 

12. In the **Pick an account** window, select **Use another account**.

13. In the **Sign in** window, enter **JoniS@xxxxxZZZZZZ.onmicrosoft** (where xxxxxZZZZZZ is the tenant prefix provided by your lab hosting provider) and then select **Next**.

14. On the **Enter password** window, enter the same **Microsoft 365 Tenant Password** provided by your lab hosting provider for the tenant admin account (i.e. the MOD Administrator account) and then select **Sign in**.

15. If a **Welcome** window appears, select the X to close it.

16. In Joni’s **Inbox** in **Outlook on the web**, open the email that Alex just sent her by selecting the email in the Inbox. Note the **Sensitive - Do Not Share** watermark that appears in the message. These are the header and footer watermarks were entered in the PII - V1 label created by the PowerShell script, which are the same watermarks that you configured for the label that you created in the prior task.

17. Select the attached file to open it.

18. In the **Your privacy option** dialog box that appears, select **Close**. Review the document, note the custom header, footer, and watermark specificed in the **PII - V1** policy do not display by default. To view the custom header, footer, and watermark, select the **View** tab and then in the menu select **Reading View**. Alternatively, in the real world, you could use the Word Desktop App which would display these by default. <br/>

	Once you have finished reviewing the document, close the document window. 

19. This will return you to **Outlook on the web** with the email still displayed in the right-hand pane. In the body of the email, the document appears in a tile. You want to download the document. Select the down arrow that appears on the right-side of the tile, and in the menu that appears, select **Download**.

20. Once the file has finished downloading, in the notification bar, select **Open file** that appears below the file name.

21. **Microsoft Word** should open along with a **Sign in** window (it may open behind the Outlook window, in which case select the **Word** icon on the taskbar to bring it forward). 

22. If a **Microsoft Office Activation Wizard** window appears, select **Close** and proceed to the next step. <br/>

	However, if a **Sign in** window appears, it's because the file is RMS protected and no AIP unified labeling client is installed on LON-CL2. In this case, you need to use the native RMS features of Word Microsoft Apps and register this installation to Joni’s account. <br/>

	‎In the **Sign in** window, enter **JoniS@xxxxxZZZZZZ.onmicrosoft.com** and then select **Next.** In the **Enter password** window, enter the same **Microsoft 365 Tenant Password** provided by your lab hosting provider for the tenant admin account (i.e. the MOD Administrator account) and then select **Sign in.** <br/>

	In the **Use this account everywhere on your device** window that appears, select **This app only** to register this Office 365 ProPlus installation to **Joni Sherman’s** Microsoft 365 account.

23. The file should open in Word, since you assigned Joni with Read-only permission. Review the three notification bars that appear above the document. 

24. Try to change the file. Word should not recognize any keystrokes, and it should display the following message above the taskbar: **This modification is not allowed because the document is open for viewing only.** <br/>  

	‎**Note:** You have just verified that the permissions assigned to the file are working properly. Joni can read the file (since she was assigned Read-only permission), but she is unable to change it (no one was assigned Edit permission).

25. Close Word.

26. You will now test what happens when you attempt to open the document that was sent to your personal email address. Use your phone or classroom PC to access your personal email address. Open the email that you (in the role of Holly) just sent to your personal email address, and then attempt to open the attached file. 

27. You should receive a message indicating that you are not signed into Office with an account that has permission to access the document. You can optionally sign in with an account that has permission to access the file, or request access from the **AlexW@xxxxxZZZZZZ.onmicrosoft.com** account, or Cancel out of the operation. Select **Cancel**.  <br/>

	‎Since only Joni was assigned permission to read the document, you just verified that Azure Information Protection protected the document based on the PII policy parameters that you configured.

## Congratulations! You have just completed the final lab in this course.


# End of Lab 9
