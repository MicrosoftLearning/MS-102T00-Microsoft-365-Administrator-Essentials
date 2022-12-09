# Learning Path 5- Lab 5 - Exercise 1 - Implement a Safe Attachments policy 

You now have a Global admin account set up for Holly Dickson, and you're signed into Microsoft 365 as Holly. In this phase of your pilot project for Adatum, you want to create a Safe Attachments policy and turn on Microsoft Defender for Office 365, which provides advanced threat protection for SharePoint, OneDrive, and Microsoft Teams.

**Note:** You will not be able to validate the Safe Attachments policy. To do so would require that you attach a virus or malware-infected file to an email, which is something that Microsoft does not recommend.

### Task 1 – Create a Safe Attachment policy and turn on Microsoft Defender for Office 365

In this task, you will turn on Microsoft Defender for Office 365, which provides advanced threat protection for SharePoint, OneDrive, and Microsoft Teams. You will also create a Safe Attachments policy that will test email attachments for malware that are sent to recipients within the xxxxxZZZZZZ.onmicrosoft.com domain. You will configure the policy so that if an attachment is blocked, it will be removed from the email that is sent to the recipient, and a copy of the email will be redirected to Joni Sherman for additional review.

1. You should still be logged into your Client 1 VM as the local **Admin** account, and in your Edge browser, you should still be logged into Microsoft 365 as **Holly Dickson**.

2. In your Edge browser, select the **Microsoft 365 admin center** tab. In the left-hand navigation pane, under **Admin centers**, select **Security**. This will open a new tab in your browser for **Microsoft 365 Defender**. 

3. In **Microsoft 365 Defender**, in the left-hand navigation pane select **Policies & rules**.

4. In the **Policies & rules** window, select **Threat policies**.

5. In the **Threat policies** window, under the **Policies** section, select **Safe attachments**.

6. In the **Safe attachments** window, on the menu bar, select **Global settings**.

7. In the **Global settings** pane that appears, set the following options and then select **Save** (if necessary):

    - **Turn on Defender for Office 365 for SharePoint, OneDrive, and Microsoft Teams** - verify the toggle switch is set to **On** (set it to **On** if necessary). This enables Microsoft Defender for Office 365.

    - **Turn on Safe Documents for Office clients** - verify the toggle switch is set to **On** (set it to **On** if necessary)

    **Note:** If both toggle switches are already set to **On**, then the **Save** button at the bottom of the pane will remain disabled since no changes were made. In this case, select **Cancel**.

8. On the **Safe attachments** window, select **+Create** on the menu bar to initiate the **Create Safe Attachments policy** wizard.

9. On the **Name your policy** page, enter **AttachmentPolicy1** in the **Name** field and then select **Next**.

10. On the **Users and domains** page, you're going to define the domain to which the policy applies. Enter **onmicrosoft.com** in the **Domains** field. In the menu that appears showing the suggested domains that include this value, select Adatum's **onmicrosoft.com** domain. Adatum's domain will now appear below the **Domains** field. Select **Next**.

11. On the **Settings** page, select the **Dynamic Delivery (Preview messages)** option. This option will still send the email but will hold the attachment until it has been scanned and marked acceptable.

12. Under the **Redirect messages with detected attachments** section, select the **Enable redirect** check box. 

13. In the **Send messages that contain blocked, monitored, or replaced attachments to the specified email address** field, enter **JoniS@xxxxxZZZZZZ.onmicrosoft.com** (where xxxxxZZZZZZ is the tenant prefix provided by your lab hosting provider), and then select **Next**.

14. On the **Review** page, review the options that you selected. If any need to be corrected, select the appropriate **Edit** option and make the necessary corrections. Once all the settings are correct, select **Submit**.

15. On the **New Safe Attachments policy created** page, select **Done**. The new **AttachmentPolicy1** policy that you just created should now appear in the list of Safe Attachment policies.

16. Leave the Client 1 VM and the Safe Attachments tab in your Edge browser open for the next lab.

**NOTE:** Unfortunately, we are unable to create a training lab in which you can validate the Safe Attachments policy that you just created. To do so, you must send an email that contains a malicious attachment. There are some common test viruses that are available, such as the EICAR test virus. However, with well-known test viruses such as EICAR, the messages in which they are attached get quarantined before they can be processed by Microsoft Defender for Office 365. Since the Safe Attachments functionality is meant to protect against unknown and zero-day viruses and malware, it is very difficult, and not recommended, to create such an attachment.

That being said, after you have defined Safe Attachment policies in your real-world environment, one good way to see how the service is working is by viewing the security-related reports in Microsoft Defender for Office 365. For more information on using these reports to validate your Safe Links and Safe Attachment policies, see [View Defender for Office 365 reports in the Microsoft 365 Defender portal](https://learn.microsoft.com/microsoft-365/security/office-365-security/view-reports-for-mdo).


# Proceed to Lab 5 - Exercise 2

