# Learning Path 7 - Lab 7 - Exercise 1 - Initialize Compliance 

In your role as Holly Dickson, Adatum’s new Microsoft 365 Administrator, you have Microsoft 365 deployed in a virtualized lab environment. As you proceed with your Microsoft 365 pilot project, your next steps are to implement archiving and retention at Adatum. You will begin by initializing compliance through the MDM auto-enrollment of new devices in your tenant. You will then configure retention tags and policies, and you will implement archiving with retention policies. 

### Task 1 - Create a security group for Compliance Testing

To test archiving and retention in your Adatum pilot project, you will create a new mail-enabled security group and assign two users to the group – Joni Sherman and Lynne Robbins. This group will then be used in the next task when you configure MDM auto-enrollment for new devices in your tenant. 

1. On LON-CL1, in your Edge browser, you should still be logged into Microsoft 365 as **Holly Dickson**. 

2. In **Microsoft Edge**, select the **Microsoft 365 admin center** tab; if you closed this tab earlier, then open a new tab and go to **https://admin.microsoft.com.** <br/>

	At this point, you may have quite a few tabs open in your browser. If you wish, you can take this opportunity to close every tab except for the **Home | Microsoft 365** tab and the **Microsoft 365 admin center** tab.

3. In the **Microsoft 365 admin center**, in the left-hand navigation pane, select **Teams & groups** and then select **Active teams & groups** below it.

4. In the **Active teams and groups** page, there's a tab for viewing each of the group types. The **Teams & Microsoft 365 groups** tab is displayed by default. To the right of this are tabs for Distribution list and Security groups. Select the **Security groups** tab.

5. On the **Security Groups** tab, select the **+Add a mail-enabled security group** option that appears on the menu bar above the list of groups. This initiates the **Add a mail-enabled security group** wizard. 

6. On the **Set up the basics** page, enter **Compliance Test Users** in the **Name** field. Tab into the **Description** field to enable the **Next** button, and then select it.

7. On the **Assign owners** page, select **+Assign owners**. 

8. In the **Assign owners** pane that appears, select **Holly Dickson** and then select **Add(1)**. 

9. On the **Assign owners** page, select **Next**.

10. On the **Assign members** page, select **+Add members**. 

11. In the **Add members** pane that appears, select the check boxes for **Joni Sherman** and **Lynne Robbins**, and then select **Add(2)**.

12. On the **Add members** page, select **Next**.

13. On the **Edit settings** page, enter **comptestusers** in the **Group email address** field. <br/>

	**Note:** The Group email address domain (to the right of the group email address alias) displays the default domain for the company's Microsoft 365 tenant (in this case, **xxxxxZZZZZZ.onmicrosoft.com**, where xxxxxZZZZZZ is the tenant prefix provided by your lab hosting provider). In a real-world scenario in which a company has multiple domains, you may need to select into this field to select the correct domain. <br/>

	Select **Next**.

14. On the **Review and finish adding group** window, review your selections. If anything needs to be changed, select the appropriate Edit link and make the necessary changes. Otherwise, if everything is correct, select **Create group**.

15. Once the group is created, the **Compliance Test Users group created** window appears. Note the message at the top of the page that indicates it can take up to an hour for the group to appear in the Active teams & groups list. Lab testing has shown that the group normally appears within a few minutes. Select **Close**.

16. This will return you to the **Active teams & groups** page. Remember, the tabs on this page reflect the four types of groups. By default, the **Microsoft 365** tab is displayed, which displays Microsoft 365 groups. Since you created a mail-enabled security group, select the **Mail-enabled security** tab to display this type of group. If the **Compliance Test Users** group does not appear in the list of mail-enabled security groups, select the **Refresh** icon on the menu bar to refresh the list of groups. <br/>

	**Important:** You cannot proceed until the **Compliance Test Users** group appears in the list; therefore, keep refreshing the list every few minutes until it appears.

17. Leave your browser open to the Microsoft 365 admin center and proceed to the next task.


### Task 2 – Configure Mobile Device Management for compliance testing

In this task you will activate MDM auto-enrollment for new devices in your Adatum Corporation tenant. The devices will belong to members of the Compliance Test Users group that you created in the prior task. You will also verify that Intune is set by default as your mobile device management (MDM) authority. 

1. On LON-CL1, in your Edge browser, you should still be logged into Microsoft 365 as **Holly Dickson**. 

2. In the **Microsoft 365 admin center**, in the left-hand navigation pane, select **Show all** (if necessary), and then in the **Admin centers** section, select **Endpoint Manager**. This returns the **Microsoft Intune admin center**.

3. In the **Microsoft Intune admin center**, select **Devices** in the left-hand navigation pane.

4. This returns the **Devices | Overview** page. Under the **Device enrollment** section in the middle pane, select **Enroll devices**.

5. On the **Enroll devices | Windows Enrollment** page, in the **General** section, select **Automatic Enrollment**.

6. This returns the **Configure** window, from which you can configure MDM and MAM settings for Microsoft Intune. For the **MDM user scope** option, select **Some.** This will display a **Groups** option below the **MDM user scope** option. This feature enables you to automatically enroll into Intune the devices that belong to users who are members of groups selected here.

7. To the right of the **Groups** option, select **No groups selected**. 

8. In the **Select groups** pane that appears, select **Compliance Test Users**, and then at the bottom of the pane select the **Select** button. <br/>

	**Note:** You just configured the **MDM user scope** to automatically enroll devices that belong to members of the **Compliance Test Users** group into MDM management with Microsoft Intune. Once Holly tests this feature in Adatum's pilot project, and assuming she is satisfied with the results, she will then set the **MDM user scope** to **All**.
	
9. This returns the **Configure** window. In the middle of the pane, select **Restore default MDM URLs** to ensure the correct URLs are set. 

10. Select **Save** on the menu bar at the top of the page. Wait for the settings to be saved before proceeding to the next step.

11. In the **Microsoft Intune admin center**, select **Tenant administration** in the left-hand navigation pane.

12. In the **Tenant admin | Tenant status** page, verify the **MDM authority** is set to **Microsoft Intune**.

13. In your Microsoft Edge browser, you can close all tabs except for the **Microsoft Office Home** tab and the **Microsoft 365 admin center** tab. Leave these two tabs open for the next exercise.

You have configured automatic enrollment in Intune for devices of users in the Compliance Test Users group, and you have verified the MDM authority for Adatum's tenant is set to Microsoft Intune.


# Proceed to Lab 7 - Exercise 2
