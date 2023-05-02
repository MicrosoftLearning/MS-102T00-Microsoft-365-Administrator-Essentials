# Learning Path 4 - Lab 4 - Exercise 1 - PIM Administrator approval

As part of her Microsoft 365 pilot project, Holly Dickson, Adatum's new Microsoft 365 Administrator, wants to implement Privileged Identity Management (PIM) within Azure Active Directory. PIM is an Azure AD service that enables you to manage, control, and monitor access to important resources in your organization. These resources include not only Azure, but other Microsoft Online Services, such as Microsoft 365 and Microsoft Intune.

One of Adatum's pain points in its existing system is that it has far too many users who have been assigned administrator roles. This has caused concern among management, who recognize this situation as an existential threat to Adatum's data security. They feel that too many people were originally assigned admin roles that shouldn't have been, and as such, these users have access to secure information and resources that could potentially compromise the organization. 

Because there's a need to reduce the number of users with permanent administrator roles and yet still provide admin privileges to selected users when business justification warrants it, Holly has been tasked with implementing Azure Active Directory's Privileged Identity Management service. By implementing PIM, Adatum can reduce the number of users with admin roles and yet still be able to assign users with admin rights on an as-needed basis whenever necessary.

In this lab, you will perform the basic steps involved in implementing PIM for a given admin role:

- Configure the role to require approval and assign an approver
- Assign an eligible user to the role
- Submit a request from the eligible user to be assigned the role
- Approve the request for the role

In this exercise, you will perform these tasks for the Global administrator role. Holly will take on the role of the approver, and Patti Fernandez will be the user requesting access to the role.

**IMPORTANT:** In Task 3, Patti Fernandez will submit a request to be assigned the Global administrator role. The activation request process is set up to require Multi-Factor Authentication (MFA). If you do not have a phone to complete this process, notify your instructor. You can still complete Tasks 1 and 2, and you may be able to partner up with another student to watch them complete the remaining tasks.

**BEST PRACTICE REMINDER:** As a best practice in your real-world deployment, you should always write down the first Global admin account’s credentials (in this lab, it's the MOD Administrator account, whose username is admin@xxxxxZZZZZZ.onmicrosoft.com, where xxxxxZZZZZZ is the tenant prefix assigned by your lab hosting provider). You should store away this account for security reasons. This first Global admin account should be a non-personalized identity that owns the highest privileges possible in a tenant. It should **NOT** be MFA activated because it is not personalized. 

Because the username and password for this first Global admin account are typically shared among several users, this account is a perfect target for attacks; therefore, it's always recommended that organizations create personalized service admin accounts (for example, an Exchange admin, SharePoint admin, and so on) and keep as few non-personalized Global admins as possible. For those personal Global administrators that you do create in your real-world deployment, they should each be mapped to a single identity (such as Holly Dickson, Patti Fernandez, etc.), and they should each have Azure Active Directory Multi-Factor Authentication (MFA) enforced. That being said, you will not turn on MFA for Holly's account because time is limited in this training course, and we don't want to take up lab time by forcing you to log in using a second authentication method every time Holly logs in.


### Task 1 - Configure the Global Administrator role to require approval

Since the Microsoft 365 Global Administrator role provides a user with basically unlimited access to all Microsoft 365 resources, the number of users assigned to this role should obviously be kept to a minimum for security purposes. 

In the Microsoft 365 tenant used by this training course, the lab hosting provider assigned the Global admin role to seven of the predefined user accounts. After you added Holly as a Global admin, eight of the 20 licensed user accounts in your tenant are now global admins, which is not something you would see in a real-world deployment. The best practice guideline that you should follow is to have from two to four Global admins in your real-world Microsoft 365 deployments. The reason this tenant exceeds that number is that it's used by multiple training courses, each of which have their own VM requirements. Some of these other courses require specific users to be Global admins, which explains why there are so many in the tenant.

Holly Dickson, Adatum's new Microsoft 365 Administrator, wants to use Privileged Identity Management to limit access to the Global admin role. To do so, she must first configure the role to require approval before it can be assigned as an eligible role for a user, and then she wants to assign herself as the approver whenever an eligible user requests activating the role.

Holly also wants to update the notification settings for the Global admin role. Privileged Identity Management (PIM) lets you know when important events occur in your Azure Active Directory (Azure AD) organization, such as when a role is assigned or activated. PIM keeps you informed by sending you and other participants email notifications. These emails can also include links to relevant tasks, such as activating or renewing a role. In this task, Holly wants to update the notifications to ensure that approvals are tracked in real-time in a proactive manner.

1. The prior lab exercise used Adatum's domain controller (LON-DC1). This lab will use LON-CL1.  <br/>

    Switch back to **LON-CL1**. 

2. On **LON-CL1**, you should still be logged into the machine as the local **adatum\administrator** account, and in your Edge browser, you should still be logged into Microsoft 365 as Holly Dickson.

3. In your browser, select the **Microsoft 365 admin center** tab. In the left-hand navigation pane under the **Admin centers** section, select **Azure Active Directory**.

4. If a **Sign in to Microsoft Entra** tab opens in your browser displaying the **Pick and account** window, select Holly's account, and in the **Enter password** window, enter the same **Microsoft 365 Tenant Password** provided by your lab hosting provider for the tenant admin account (i.e. the MOD Administrator account). On the **Stay signed in?** window, select **Don't show this again** and then select **Yes**.

5. In the **Microsoft Entra admin center**, the **Home** page is displayed by default. Scroll down towards the bottom of the Home page and in the **Feature highlights** section, select **Privileged Identity Management**.

6. In the **Privileged Identity Management | Quick start** window, in the middle pane under the **Manage** section, select **Azure AD roles**.

7. In the **Adatum Corporation | Quick start** window, in the middle pane under the **Manage** section, select **Settings**. 

8. In the **Adatum Corporation | Settings** window, select the **Global Administrator** role. <br/>

    **Tip:** If the roles are not displayed in alphabetical order, select the **Role** heading to sort them in ascending alphabetical order. This will make it easier to locate the Global administrator role.

9. In the **Role setting details -  Global Administrator** window, scroll through the page and review the information for role activation, assignment, and notification. Then select **Edit** on the menu bar at the top of the page.

10. In the **Edit role setting - Global Administrator** window, the **Activation** tab is displayed by default. In this tab, below the activation slider, verify the **Azure MFA** option is selected by default for the **On activation, require** setting (if it's not selected, then select it now). This will require that the person requesting activation of the role will have to sign in using multi-factor authentication to provide additional verification that they are who they say they are.

11. The window then displays a group of three settings, each of which has a corresponding check box. Select the **Require Approval to activate** check box. By doing so, the **Select approver(s)** section becomes enabled. Do not change the default settings of the other two check boxes.

12. In the **Select approver(s)** section, no specific approver has been selected. Holly wants to assign herself as the approver for this role, so select this section. In the **Select a member** pane that opens on the right, you would normally scroll through the list of users and select **Holly Dickson**. However, since over 200 users were synchronized from the on-premises Active Directory to Azure AD in the prior lab exercise, scrolling through the user list will be too time consuming. <br/>

    Therefore, enter **Holly** in the **Search** box. In the list of users whose first name starts with Holly, select Holly Dickson's user account that pertains to the onmicrosoft.com domain (**Holly@xxxxxZZZZZZ.onmicrosoft.com**). Do NOT select Holly's user account that applies to the custom domain. Then select the **Select** button.

13. In the **Edit role setting - Global Administrator** window, select the **Notification** tab at the top of the page.

14. On the **Notification** tab, note the three activities that can trigger a notification being sent: **Send notifications when...**    <br/>

    - members are assigned as eligible to this role
    - members are assigned as active to this role
    - eligible members activate this role

    For each of these three activities, an alert can be sent (depending on the activity, it will either be a Role assignment alert or a Role activation alert). The default value for each of these alerts is **Admin**, which refers to the Global Administrators and any Privileged Role Administrators. Besides sending this alert notification email to these admins, Holly wants the alert for each activity sent to the MOD administrator account. <br/>

    In the **Additional recipients** field for each of the three alerts (the **Role assignment alert** for the first two activities and the **Role activation alert** for the final activity), enter the MOD administrator's email ID of **admin@xxxxxZZZZZZ.onmicrosoft.com** (where xxxxxZZZZZZ is the tenant prefix provided by your lab hosting provider).

15. At the bottom of the **Edit role setting - Global Administrator** window, select **Update**.

16. Leave all browser tabs open for the next task.


### Task 2 - Assign an eligible group to the Global Admin role

For Adatum's PIM pilot project, Holly has selected Patti Fernandez as the sole user who will be eligible to be assigned the Global admin role. However, to simplify future role assignments, Holly wants to create a security group, assign Patti to the group, and then assign the group to the Global admin role. 

Assigning roles to groups can simplify the management of role assignments in Azure AD. Instead of requiring a Global admin (such as Holly) or a Privileged Role Administrator to assign a role to multiple people individually, they can create a security group and then enable the group to be eligible for that specific role. When people are assigned as members of the group, they indirectly become eligible to be assigned the role. The company's existing governance workflow can then take care of the approval process and auditing of the group's membership to ensure that only legitimate users are members of the group and are thus assigned the particular role. 

In this task, Holly will create a new, role-assignable security group for users who are eligible for the Global admin role. She will then assign Patti to the group, and then enable the group to be eligible for the Global Administrator role.

1. On LON-CL1, in your Edge browser, you should still be logged into Microsoft 365 as Holly Dickson.

2. You will begin by creating a new, role-assignable security group called **PIM-Global-Administrators** in Azure AD, and you will assign Patti as a member of the group. <br/>

    In your **Edge** browser, you should still have the **Microsoft Entra admin center** open in a tab that's displaying the **Adatum Corporation | Settings** window from the prior task. In the left-hand navigation pane, select **Groups**, and then select **All groups**.

3. In the **Groups | All groups** window, in the detail pane on the right, select **New group** in the menu bar.

4. In the **New group** window, enter the following information:

    - Group type - **Security**

    - Group name - **PIM-Global-Administrators**

    - Group description - **Group of eligible users that can be assigned to the Global Administrator role in PIM**

    - Azure AD roles can be assigned to the group - **Yes**

    - Membership type - **Assigned**

    - Owners - Select **No owners selected**. In the **Add owners** pane, enter **Holly** in the **Search** field and select the **Holly@xxxxxZZZZZZ.onmicrosoft.com** user account

    - Members - Select **No members selected**. In the **Add members** pane, enter **Patti** in the **Search** field and select Patti Fernandez's user account

5. Select the **Create** button at the bottom of the page.

6. A dialog box appears at the top of the page that says: **Creating a group to which Azure AD roles can be assigned is a setting that cannot be changed later. Are you sure that you want to add this capability?**. Select **Yes**.

7. You must now make the **PIM-Global-Administrators** group eligible for role assignment. In the left-hand navigation pane, select **Identity Governance** to expand the section, and then select **Privileged Identity Management**.

8. In the **Privileged Identity Management | Quick start** window, in the middle pane under the **Manage** section, select **Azure AD roles**.

9. In the **Adatum Corporation | Quick start** window, the detail pane on the right displays the **Privileged Identity Management** window. This window displays the following sections - Assign, Activate, Approve, and Audit. Under the **Assign** section, select the **Assign Eligibility** button.

10. In the **Adatum Corporation | Roles** window, scroll down through the list of roles and select **Global Administrator**.

11. In the **Global Administrator | Assignments** window, select **+Add assignments** on the menu bar. 

12. In the **Add assignments** window, the **Membership** tab is displayed by default. Under **Select member(s)**, select **No member selected**.

13. In the **Select a member** pane that appears on the right, enter **PIM** in the **Search** field. This will display the list of eligible users and groups whose name starts with **PIM**. Select the **PIM-Global-Administrators** group that appears, and then select the **Select** button.

14. In the **Add assignments** window, select **Next** (this does the same thing as selecting the **Setting** tab). 

15. In the **Add assignments** window, under the **Setting** tab, verify the **Assignment type** option is set to **Eligible**. Also verify the **Permanently eligible** check box is selected (if not, then do so now), and then select **Assign**. 

16. In the **Global Administrator | Assignments** window, note that the **PIM-Global-Administrators** group is an eligible assignment to the Global Administrator role. Because **PIM-Global-Administrators** is a group, it means that all members of this group (which consists of Patti Fernandez) are now eligible to be assigned the Global Administrator role.

    **Note:** Lab testing has shown that it can sometimes take up to 30 minutes for new assignments to appear under the **Eligible assignments** tab. If **PIM-Global-Administrators** doesn't appear immediately, wait a few minutes and then select the **Refresh** option on the menu bar. Continue to select the **Refresh** option every few minutes until **PIM-Global-Administrators** appears in the list of **Eligible assignments**.

17. Leave all browser tabs open for the next task.


### Task 3 - Submit a request for the Global Admin role

Now that the **PIM-Global-Administrators** group has been made eligible for the Global administrator role, the members of the group (in this case, Patti Fernandez) can be assigned the Global Administrator role using Azure AD Privileged Identity Management. Holly wants to test out the PIM process in her pilot project. In this task, you will take on the role of Patti, who will submit a request to be assigned Global administrator role privileges. In the next task, Holly will review her request and approve it.

**NOTE:** The activation request process is set up to require multifactor authentication (MFA). If you do not have a phone to complete this process, notify your instructor. You may be able to partner with another student to watch them complete the remaining two tasks.

1.  In LON-CL1, right-click on the **Edge** icon on the taskbar and in the menu that appears, select **New InPrivate window**. 

2. In your **InPrivate browsing** session, enter the following URL in the address bar: **https://portal.azure.com**

3. You're now going to log into Azure as Patti Fernandez. In the **Sign in** window, enter **PattiF@xxxxxZZZZZZ.onmicrosoft.com** (where xxxxxZZZZZZ is the tenant prefix provided by your lab hosting provider) and then select **Next**. In the **Enter password** window, enter the same **Microsoft 365 Tenant Password** provided by your lab hosting provider for the tenant admin account (i.e. the MOD Administrator account) and then select **Sign in**. In the **Stay signed in?** dialog box, select the **Don't show this again** check box and then select **Yes**.

4. In the **Welcome to Microsoft Azure** dialog box that appears, select **Maybe later** to skip the tour.

5. In the **Microsoft Azure** portal, in the middle of the screen is the section of **Azure services**. This section displays a row of Azure services and their associated icons. At the end of the row, select **More services** (with the forward arrow icon). This opens the **All services** window.

6. In the **All services** window, enter **priv** in the **Search** box at the top of the page. In the list of search results, select **Azure AD Privileged Identity Management**.

7. In the **Privileged Identity Management | Quick start** window, in the **Tasks** section in the left-hand navigation pane, select **My Roles**.

8. In the **My roles | Azure AD roles** window, the **Eligible assignments** tab is displayed by default. Remember, in the prior task Holly assigned Patti as a member of the **PIM-Global-Administrators** group, which Holly later assigned as an eligible group for the Global Administrator role. As such, this role appears in the list of **Eligible assignments**. <br/>

    Under the **Action** column for the Global Administrator role, select **Activate**.

9. In the **Activate - Global Administrator** pane, a warning message is displayed at the top of the pane indicating additional verification is required. Select this message to continue.

10. In the **More information required** window that appears, select **Next**. 

11. On the **Microsoft Authenticator** page, you can download this mobile app or use a different method for MFA verification. For the purposes of this lab, we recommend you use your mobile phone so that you do not have to take time installing the Microsoft Authenticator app that you may not use again after this training class. <br/>

    Select the hyperlinked message at the bottom of the page that says: **I want to set up a different method**. 

12. On the **Choose a different method** dialog box that appears, select the drop-down arrow in the **Which method would you like to use?** field, select **Phone**, and then select **Confirm**. 

13. In the **Phone** window that appears, under **What phone number would you like to use?**, select your country or region, and then in the field next to it, enter your phone number (in the format **nnn-nnn-nnnn**). Verify the **Text me a code** option is selected and then select **Next**.

14. Retrieve the verification code from the text message that is sent to your phone.

15. In the **Phone** window, enter the 6-digit verification code in the **Enter code** field and then select **Next**.

16. Once verification is complete and you receive a message indicating your phone was registered successfully, select **Next**.

17. On the **Success!** page, select **Done**.

18. If you receive a dialog box indicating your sign in has timed out, you will have to enter Patti's password, which is the same **Microsoft 365 Tenant Password** provided by your lab hosting provider for the tenant admin account (i.e. the MOD Administrator account). You will then be sent another verification code to your phone. On the **Enter code** window, enter this new code and then select **Verify**. <br/>

    **WARNING:** If you take too long to complete this process, the **Enter password** window will appear with a message indicating you took too long to complete the sign in process, so you will be timed-out. If this occurs, you must sign in again with Holly's password, which is the same **Microsoft 365 Tenant Password** provided by your lab hosting provider for the tenant admin account (i.e. the MOD Administrator account). Another verification code will be texted to your phone, so enter it in the **Enter code** screen that appears and select **Verify**.

19. In the **Activate - Global Administrator** pane that appears on the right-side of the screen, enter **Testing PIM** in the **Reason** field, and then select the **Activate** button at the bottom of the pane.

20. On the **My roles | Azure AD roles** window, the **Eligible assignments** tab is displayed on the menu bar. Select the **Active assignments** tab that appears next to it. Note the Global Administrator role does not yet appear. While the role has been activated, it has not been assigned to Patti's account since Holly has not yet approved Patti's request.  <br/>

     **Note:** If you recall, back in Task 1 Holly set up the Global Administrator role so that activation to a user account will require approval. What Patti just did was request that the Global Admin role be activated for her user account. This will send a request to Holly, who can then either approve or deny Patti's request for role activation. Holly will review and then approve this request in the next task.

21. Leave the InPrivate browsing session open. You will return to it in the next task once Holly approves Patti's request.


### Task 4 -  Approve the request for the Global Admin role

Back in Task 1, Holly set herself up as the approver for the Global Administrator role. Since Patti has submitted a request to be assigned this role, Holly must review the request and determine whether to accept or deny it. 

1.  In LON-CL1, hover your mouse over the Edge icon on your taskbar to see the two Edge sessions that you have open - the window on the left is the original Edge browser session in which you are signed into **Microsoft 365** as **Holly Dickson**, and the window on the right is the InPrivate Browser session in which you are signed into **Azure AD** as **Patti Fernandez**. <br/>

    Select the window on the left to go back to the original Edge browser session in which you are signed in as **Holly Dickson**. 

2.  In your browser, the **Global Administrator | Assignments** window should be displayed in the **Microsoft Entra admin center**. <br/>

    In the navigation thread at the top of the page (**Home > Privileged Identity Management | Azure AD roles > Adatum Corporation | Roles**), select **Privileged Identity Management | Azure AD roles**.

3. In the **Privileged Identity Management | Quick start** window, in the middle pane under **Tasks**, select **Approve requests**.

4. In the **Approve requests | Azure AD roles** window, in the **Requests for role activations** section, select the check box to the left of the Global Administrator request from Patti Fernandez, and then select the **Approve** button.

5. In the **Approve Request** pane that appears on the right-side of the screen, enter **PIM testing** in the **Justification** field and then select **Confirm**.

6.  Hover your mouse over the **Edge** icon on the taskbar and select the window on the right to go back to the InPrivate Browser session where Patti is signed in. 

7. In the **My roles | Azure AD roles** window, the **Active assignments** tab is currently selected from the prior task, prior to approving Patti's request. <br/>

    Select **Refresh** on the menu bar. </br/>

    Note how the Global Administrator role is now activated for Patti. You have just verified that Patti has been assigned the Global Administrator role using Azure AD Privileged Identity Management.

8. Close the InPrivate browser session.

9. In your Edge browser, leave all the tabs open for the next lab.


# Proceed to Lab 4 - Exercise 2
