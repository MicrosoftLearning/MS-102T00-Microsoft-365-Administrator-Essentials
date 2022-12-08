# Learning Path 7 - Lab 7 - Exercise 3 - Create message encryption rules


In this lab, you will take on the persona of Holly Dickson, Adatum’s Enterprise Administrator. You have been tasked with piloting the use of Microsoft 365 message encryption in Adatum’s Microsoft 365 deployment. Since message encryption rules can be created using both Exchange Online and Windows PowerShell, you have decided to test each method to determine which you prefer to use once you go live.

In this exercise you will learn how to create a mail flow encryption rule using both the Exchange admin center and Windows PowerShell.

### Task 1 – Create a Mail Flow Encryption Rule using the Exchange admin center

In this task, you will create an encryption rule for messages inside your Exchange Online environment by using the Exchange admin center. In the next task, you will do the same thing but using PowerShell instead. 

1. On the LON-CL1 VM, you should still be logged into the **Microsoft 365 admin center** as **Holly Dickson**. If you closed your Edge browser or the **Microsoft 365 admin center** tab, then in your Edge browser navigate to **https://portal.office.com**, sign in as **Holly@xxxxxZZZZZZ.onmicrosoft.com**, select the **App launcher** icon (the square made up of 3 rows of dots) that appears above the **Home** icon in the top left corner of the screen, and then in the **Apps** pane that appears, select **Admin**; this opens the **Microsoft 365 admin center** in a new browser tab. 

2. In the **Microsoft 365 admin center**, in the left-hand navigation pane, select **Show all** (if necessary), and then under **Admin centers**, select **Exchange**. This will open the Exchange Online admin center.

3. In the **Exchange admin center**, in the left-hand navigation pane select **Mail flow** to expand this group, and then select **Rules**.

4. On the **Rules** page, select **+Add a rule** on the menu bar to create a new rule. This displays a drop-down menu of actions. Select **Create a new rule.** This initiates the **New transport rule** wizard.

5. In the **New transport rule** wizard, on the **Set rule conditions** page, enter **Encrypt mail for guest@adatum.com** in the **Name** field.

6. Two fields appear below the **Apply this rule if** condition. Select the first field. In the drop-down menu that appears, select **the recipient is**. <br/>

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

In a prior task, you configured a mail flow encryption rule using the Exchange admin center. In this task, you will create a mail flow encryption rule using Windows PowerShell. You must begin by creating a PSSession that establishes a remote connection to Exchange Online through PowerShell and then imports the Exchange Online session into the PowerShell GUI. This is required because the **New-TransportRule** cmdlet used in this task is an Exchange Online cmdlet; therefore, it does not exist in MsolService. As such, you must connect to the Exchange Online session through PowerShell to access this cmdlet.

1. You should still be logged into LON-CL1 as the local **Admin** account, and in your Edge browser, you should still be logged into Microsoft 365 as **Holly Dickson**. 

2. To open Windows PowerShell, enter **powershell** in the **Search** box on the taskbar. 

3. In the menu that appears, right-click on **Windows PowerShell** and select **Run as administrator** in the drop-down menu. 

4. In **Windows PowerShell**, you must begin by installing the **Microsoft Azure Active Directory Module for Windows PowerShell** by running the following command at the command prompt:<br/>

	‎**Install-Module MSOnline** 
	
5. If you are prompted to install the **NuGet provider**, enter **Y** to select **[Y] Yes**. 

6. If you are prompted to confirm whether you want to install the module from an untrusted repository (PSGallery), enter **A** to select **[A] Yes to All.** 

7. Once the installation is complete, the screen will return to the command prompt. You must then run the following command to initiate a connection to Azure Active Directory: <br/>
	
	**Connect-MsolService**  ‎

8. A new window will appear requesting your credentials. Sign in as **Holly@xxxxxZZZZZZ.onmicrosoft.com** (where xxxxxZZZZZZ is the tenant prefix provided by your lab hosting provider) with a password of **User.pw1**.   
	
9. Running unsigned PowerShell scripts from remote computers requires changing the execution policy for PowerShell. You should run the following command that changes the Execution Policy for this PC to **unrestricted**, which sets access to the external authorization for this PC so that it can connect to Microsoft online and load all configuration files and run all scripts:   <br/>

	**Set-ExecutionPolicy unrestricted**  <br/>
	
10. If you are prompted whether you want to change the execution policy, enter **A** to select **[A] Yes to All**.
	‎
11. You must then run the following command to prompt for the username and password of the user who will be running any subsequent commands; this set of credentials will be stored in the $Cred macro: <br/>

	**&dollar;Cred = Get-Credential** <br/>
	
12. A **Windows PowerShell credential request** window will appear. Sign in as **Holly@xxxxxZZZZZZ.onmicrosoft.com** (where xxxxxZZZZZZ is the tenant prefix provided by your lab hosting provider) and a password of **User.pw1**.  
	
13. You must then run the following command to create a PSSession (titled $Session) that establishes a remote connection to Exchange Online through PowerShell. When you create a PSSession, Windows PowerShell establishes a persistent connection to the remote computer. Without the -Credential parameter that invokes the $Cred macro from the prior step, this command would prompt you for the credentials of the user authorizing this command. In this case, by invoking the $Cred macro, it applies Holly’s username and password.<br/>

	**&dollar;Session = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri https://outlook.office365.com/powershell-liveid/ -Credential $Cred -Authentication Basic -AllowRedirection**<br/>
	
	**Note:** It’s important to note that you must connect to Exchange Online PowerShell with an admin account that cannot be enabled for multi-factor authentication (MFA). In a real-world environment, if your admin account is enabled for MFA, you must install the Exchange Online Remote PowerShell Module and use the **Connect-EXOPSSession** cmdlet to connect. For more information, see the following article on how to [Connect to Exchange Online PowerShell using multi-factor authentication](https://docs.microsoft.com/en-US/powershell/exchange/exchange-online/connect-to-exchange-online-powershell/mfa-connect-to-exchange-online-powershell?view=exchange-ps).  
	
14. You should then run the following cmdlet to import commands, such as cmdlets, functions, and aliases, from the PSSession ($Session) created in the prior step. In this case, it imports the Exchange Online session into the PowerShell GUI. <br/>

	**Import-PSSession $Session**   <br/>
	
	‎**Note:** You can ignore the warning message that is displayed regarding unapproved verbs.  

15. You will now create a mail flow rule by using the **New-TransportRule** cmdlet, and you will set the **ApplyOME** encryption parameter to $true. This rule will encrypt all outgoing mail from Adatum that is being sent to Gservices@adatum.com.  <br/>

	To create this rule, run the following command:<br/>

	**New-TransportRule -Name "Encrypt rule for Guest Services" -SentTo "Gservices@adatum.com" -SentToScope "NotinOrganization" -ApplyOME $true**  <br/>
	
	**Note:** This command will take several seconds to complete.

16. To verify the rule exists, minimize your PowerShell window. In your Microsoft Edge browser, you should still be in the **mail flow** window of the **Exchange admin center**, and the **rules** tab should be displayed. The list of rules should only display the **Encrypt mail for guest@adatum.com** rule that you created in the prior task.<br/>

	‎On the menu bar that appears above the list of rules, select the **Refresh** icon. In the refreshed list, the rule that you just created using PowerShell should appear as well.
	
17. Leave your browser session open for the next exercise.


# End of Lab 7
