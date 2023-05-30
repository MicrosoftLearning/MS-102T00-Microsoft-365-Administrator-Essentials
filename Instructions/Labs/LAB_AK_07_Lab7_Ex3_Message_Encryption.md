# Learning Path 7 - Lab 7 - Exercise 3 - Create message encryption rules


In this lab, you will take on the persona of Holly Dickson, Adatum’s new Microsoft 365 Administrator. You have been tasked with piloting the use of Microsoft 365 message encryption in Adatum’s Microsoft 365 deployment. Since message encryption rules can be created using both Exchange Online and Windows PowerShell, you have decided to test each method to determine which you prefer to use once you go live.

In this exercise you will learn how to create a mail flow encryption rule using both the Exchange admin center and Windows PowerShell.

### Task 1 – Create a Mail Flow Encryption Rule using the Exchange admin center

In this task, you will create an encryption rule for messages inside your Exchange Online environment by using the Exchange admin center. In the next task, you will do the same thing but using PowerShell instead. 

1. On LON-CL1, in your Edge browser, you should still be logged into Microsoft 365 as **Holly Dickson**. 

2. In the **Microsoft 365 admin center**, in the left-hand navigation pane, select **Show all** (if necessary), and then under **Admin centers**, select **Exchange**. This will open the Exchange Online admin center.

3. In the **Exchange admin center**, in the left-hand navigation pane select **Mail flow** to expand this group, and then select **Rules**.

4. On the **Rules** page, select **+Add a rule** on the menu bar to create a new rule. This displays a drop-down menu of actions. Select **Create a new rule.** This initiates the **New transport rule** wizard.

5. In the **New transport rule** wizard, on the **Set rule conditions** page, enter **Encrypt mail for guest@adatum.com** in the **Name** field.

6. Two fields appear below the **Apply this rule if** condition. Select the first field. In the drop-down menu that appears, select **the recipient**. <br/>

	Select the second field. In the drop-down menu that appears, select **is this person**. For this condition, you must either select an existing name from the user list or type a new email address in the **Select members** field. In this case, enter **guest@adatum.com** in the **Select members** field. Select the **guest@adatum** field that appears, and then select **Save**.

7. You must now add an additional condition, so select the **plus sign (+)** that appears to the right of the **is this person** field.

8. Note how a second condition appears under the **And** heading. In this second condition, select the first field, and then select **The recipient** from the drop-down menu. Select the second field. In the drop-down menu that appears, select **is external/internal.**

9. In the **select recipient location** dialog box, select the drop-down arrow. In the drop-down menu, select **Outside the organization** and then select **Save.** 

10. You now need to define an action to perform when this rule is applied. In the **Do the following** section, select the first field. In the drop-down menu that appears, select **Modify the message security**. Select the second field. In the menu that appears, select **Apply Office 365 Message Encryption and rights protection.**

11. In the **select RMS template** dialog box, select the drop-down arrow, select **Encrypt**, and then select **Save**.

12. You will be returned to the **Set rule conditions** page. Since you will not be defining any exceptions to this rule, you will not update the **Except if** section of the rule. Select **Next**.

13. On the **Set rule settings** page, verify the **Rule mode** is set to **Enforce** (select this option if it isn't already selected). Select the **Severity** field and select **Medium** from the drop-down menu. Select **Next**.

14. On the **Review and finish** page, review the conditions and rule settings. If any value needs to be changed, select either **Edit rule conditions** or **Edit rule settings** to correct the corresponding field. When all conditions and settings are correct, select **Finish**.

15. Once the transport rule is created successfully, select **Done**.

16. This should return you to the **Rules** page. If the new rule does not appear in the list of rules, select the **Refresh** option on the menu bar. 

17. Leave your browser tabs open and proceed to the next task. 
 

### Task 2 – Create a Mail Flow Encryption Rule using Windows PowerShell

In the prior task, you configured a mail flow encryption rule using the Exchange admin center. In this task, you will create a mail flow encryption rule using Windows PowerShell, or more specifically, Microsoft Graph PowerShell. You must begin by cconnecting to the Exchange Online PowerShell module (ExchangeOnlineManagement). This is required because the **New-TransportRule** cmdlet used in this task is an Exchange Online cmdlet. As such, you must connect to the Exchange Online session through PowerShell to access this cmdlet.

1. On LON-CL1, in your Edge browser, you should still be logged into Microsoft 365 as **Holly Dickson**. 

2. If Windows PowerShell is still open on your desktop, then select the PowerShell icon on the taskbar to maximize the PowerShell window. However, if you closed PowerShell after using it the last time, then enter **power** in the **Search** box on the taskbar, and in the menu that appears, right-click on **Windows PowerShell** and select **Run as administrator** in the drop-down menu. 

3. In **Windows PowerShell**, you must begin by installing the Exchange Online PowerShell module (ExchangeOnlineManagement) by running the following command at the command prompt:<br/>

	‎**Install-Module -Name ExchangeOnlineManagement** 
	
4. If you are prompted to confirm whether you want to install the module from an untrusted repository (PSGallery), enter **A** to select **[A] Yes to All.** 

5. You must then connect to the module by running the following command at the command prompt (Note: in the command, you must copy and paste in the Tenant Name provided by your lab hosting provider (xxxxxZZZZZZ.onmicrosoft.com, where xxxxxZZZZZZ is the tenant prefix assigned by your lab hosting provider):

	‎**Connect-ExchangeOnline -UserPrincipalName holly@xxxxxZZZZZZ.onmicrosoft.com**
	
6. In the **Enter password** dialog box that appears, enter the Microsoft 365 tenant admin password provided by your lab hosting provider and then select **Sign in**.

7. You will now create a mail flow rule by using the **New-TransportRule** cmdlet, and you will set the **ApplyRightsProtectionTemplate** property to **Encrypt**, which is one of the available RMS templates. This rule will encrypt all outgoing mail from Adatum that is being sent to Gservices@adatum.com.  <br/>

	To create this rule, run the following command:<br/>

	**New-TransportRule -Name "Encrypt rule for Guest Services" -SentTo "Gservices@adatum.com" -SentToScope "NotinOrganization" -ApplyRightsProtectionTemplate Encrypt**  <br/>
	
	**Note:** This command will take several seconds to complete. Do not proceed to the next step until PowerShell displays the properties of the new rule that you created.

8. To verify the rule exists, begin by minimizing your PowerShell window. In your Microsoft Edge browser, you should still be in the **mail flow** window of the **Exchange admin center**, and the **rules** tab should be displayed. The list of rules should only display the **Encrypt mail for guest@adatum.com** rule that you created in the prior task.<br/>

	‎On the menu bar that appears above the list of rules, select the **Refresh** icon. In the refreshed list, the rule that you just created using PowerShell should appear as well.
	
9. Leave your Edge browser open for the next exercise.


# End of Lab 7
