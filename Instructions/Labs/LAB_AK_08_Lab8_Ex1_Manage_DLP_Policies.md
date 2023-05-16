# Learning Path 8 - Lab 8 - Exercise 1 - Manage DLP Policies  

In your role as Holly Dickson, Adatum’s new Microsoft 365 Administrator, you have Microsoft 365 deployed in a virtualized lab environment. As you proceed with your Microsoft 365 pilot project, your next steps are to implement Data Loss Prevention (DLP) policies at Adatum. You will begin by creating a custom DLP policy in this exercise, and then you’ll test DLP policies related to email message archiving and emails with sensitive data. 

### Task 1 – Create a DLP policy with custom settings

In this task you will create a Data Loss Prevention policy in the Microsoft Purview portal to protect sensitive data from being shared by users. The DLP Policy that you create will inform your users if they want to share content that contains IP addresses. 

The policy will contain two rules, or actions, each of which is dependent on the number of IP addresses in the message. If the message contains one IP address, the policy will notify people with a policy tip and still email the message. However, if the content contains two or more IP addresses, then the message will be blocked, an incident email with a high sensitivity level will be sent to the sender, and a policy tip will be displayed that allows the sender to override the email blockage if the sender provides a business justification within the policy tip.

1. On LON-CL1, in your Edge browser, you should still be logged into Microsoft 365 as **Holly Dickson**. 

2. In **Microsoft Edge**, the Microsoft Purview portal should still be open; if not, then open a new tab and navigate to **https://compliance.microsoft.com**.

3. In the **Microsoft Purview** portal, in the left-hand navigation pane, select **Data loss prevention**.

4. On the **Data loss prevention** drop-down, select the **Policies** tab.

5. In the **Policies** tab, select the **+Create policy** option on the menu bar to start the **Create policy** wizard.

6. On the **Start with a template or create a custom policy** page, there are multiple policy categories listed. All the policy categories provide templates that can be used to create a policy, except for the **Custom** category. This category does not provide any specific template; instead, it enables organizations to create custom policies from scratch. The column in the left-hand pane displays the policy categories. When you select a category, the middle pane displays the available templates to choose from for that category. When you select a template in the middle pane, the right-hand pane displays the type of information that is protected in that template. <br/> 

    For example, select **Financial** in the left-hand pane and then scroll through the various templates that you can choose from in the middle pane. Select one or two of the templates to see what type of information it protects. If you want, select each of the remaining categories to see what type of templates are provided. 
  
7. For the purpose of this lab, you will create a custom DLP policy. Select **Custom** in the left-hand **Categories** pane, select the **Custom policy** template in the middle pane, and then select **Next**.

8. In the **Name your DLP policy** page, enter the following information and then select **Next**:

      - Name: **IP Address DLP policy**

      - Description: **This policy detects the presence of IP addresses in emails. End users are notified of the detection and admins receive a notification. Emails with 2 or more IP addresses are blocked from being sent.**

9. On the **Assign admin units (preview)** page, select **Next**. On the **Choose locations to apply the policy** page, verify the **Status** toggle is set to **On** for the following locations (if any of these locations is not set to **On** by default, then set it to **On** now): **Exchange email, SharePoint sites, OneDrive accounts, Teams chats and channel messages**. Set all other locations to **Off**, and then select **Next**.

10. On the **Define policy settings** page, select the **Create or customize advanced DLP rules** option, (if it isn't already selected by default) and then select **Next**. 

11. On the **Customize advanced DLP rules** page, select the **+Create rule** option on the menu bar.

12. On the **Create rule** page, enter the following information:
    
      - Name: **Single IP Address rule**
    
      - Description: **Email contains an IP address**
    
      - In the **Conditions** section, select **+Add condition** and then select **Content contains** from the drop-down menu that appears. Then enter the following condition settings:
    
        - In the **Content contains** field, select the **Add** drop-down menu and then select **Sensitive info types**.
        
        - In the **Sensitive info types** pane, type **IP** inside the **Search** field and then hit Enter.
        
        - In the search results, select the **IP Address** check box and then select **Add**.
        
     - Scroll down to the **User notifications** section, set the **Use notifications to inform your users and help educate them on the proper use of sensitive info** toggle switch to **On**.

    - In the **Policy tips** section, select the **Customize the policy tip text** check box. Microsoft 365's default policy tip says: **Your email message conflicts with a policy in your organization.** Holly wants you to customize the Policy Tip message. <br/>

    Enter the following text in this field: **ATTENTION! You have entered sensitive information (an IP address) in this message. You will not be prevented from sending this message, but please review whether the recipients are authorized to see this sensitive data.** 
    
    - In the **Incident reports** section, verify the **Send an alert to admins when a rule match occurs** toggle switch is set to **On** (if necessary, set it to **On**)

    - Select the **Save** button at the page of the page.

13. On the **Customize advanced DLP rules** page, the **Single IP Address rule** that you just created should now appear. Select the **+Create rule** option to create the second DLP rule. 

14. On the **Create rule** page, enter the following information:
    
      - Name: **Multiple IP Address rule**
    
     - Description: **Email contains two or more IP addresses**
    
      - In the **Conditions** section, select **+Add condition** and then select **Content contains** from the drop-down menu that appears. Then enter the following condition settings:
    
        - In the **Content contains** field, select the **Add** drop-down menu and then select **Sensitive info types**.
        
        - In the **Sensitive info types** pane, type **IP** inside the **Search** field and then hit Enter.
        
        - Select the **IP Address** check box and then select **Add**.

        - Under the **Sensitive Info types** section, the **IP Address** info type is displayed. On the right side of the IP Address row, the **Instance count** setting is set from **1** to **Any**. Change the value of the first field from 1 to **2**. By making this change, this rule will only apply if 2 or more IP addresses appear in the email. 
    
     - In the **Actions** section, select **+ Add an action**. In the drop-down menu that appears, select **Restrict access or encrypt the content in Microsoft 365 locations**. Then enter the following action settings:

        - Select the **Restrict access or encrypt the content in Microsoft 365 locations** check box. Doing so displays the **Block users from receiving email or accessing shared SharePoint, OneDrive, and Teams files** option, which is selected by default. Keep this option selected.

        - Under the **Block users from receiving email or accessing shared SharePoint, OneDrive, and Teams files** option, select the **Block everyone** option.
    
     - In the **User notifications** section, set the **Use notifications to inform your users and help educate them on the proper use of sensitive info** toggle switch to **On**. 

    - In the **Policy tips** section, select the **Customize the policy tip text** check box. Microsoft 365's default policy tip says: **Your email message conflicts with a policy in your organization.** Holly wants you to customize the Policy Tip message. <br/>

    Enter the following text in this field: **ATTENTION! You have entered sensitive information (multiple IP addresses) in this message. You will be blocked if you attempt to send this message. Overriding this block indicates you have authorized sending this sensitive data to the recipients.** 
    
    - In the **User overrides** section, select the **Allow overrides from M365 services** check box. This enables two additional settings that indicate how overrides will be handled. Select each of the check boxes for the following options: **Require a business justification to override** and **Override the rule automatically if they report it as a false positive**.
    
    - In the **Incident reports** section, verify the **Send an alert to admins when a rule match occurs** toggle switch is set to **On** (if necessary, set it to **On**).

    - Select the **Save** button at the page of the page.

15. On the **Customize advanced DLP rules** page, both the **Single IP Address rule** and **Multiple IP Address rule** should now appear. Select **Next**.

16. On the **Test or turn on the policy** page, select the **Turn it on right away** option and then select **Next**.

17. On the **Review your policy and create it** page, review the policy that you just created. If anything needs to be corrected, select the appropriate **Edit** option and make your corrections. When everything appears OK, select **Submit**.

18. On the **New policy created** page, select **Done**.


You have now created a DLP policy that scans for IP addresses in emails and documents that are sent or shared in your organization.


# Proceed to Lab 8 - Exercise 2 
