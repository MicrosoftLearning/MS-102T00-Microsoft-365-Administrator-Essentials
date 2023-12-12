# Learning Path 6 - Lab 6 - Exercise 1 - Prepare for Alert Policies

Alerts are policies designed to automatically notify administrators when key actions have occurred in their Microsoft 365 tenant. Alerts can be an easy way to ensure that change logs are up-to-date and that business policies are being followed inside your Microsoft 365 tenant.

In your role as Holly Dickson, Adatum’s new Microsoft 365 Administrator, you have Microsoft 365 deployed in a virtualized lab environment. One of Adatum’s business requirements is to set up an alert notification system so that targeted administrators are automatically notified through email when certain actions occur. As you proceed with your Microsoft 365 pilot project, you want to test out Microsoft 365’s alert notification system by creating and validating several types of alerts.

There are two requirements to viewing alerts in Microsoft Defender XDR – turning on Audit Logging and assigning the proper Role Based Access Control (RBAC) permissions to the users who will view alerts. 

- **Audit logging.** If you recall, towards the end of Lab 1 you turned on Audit Logging. You performed this task in Lab 1 because it can take an hour or two to propagate that setting through the system before you can successfully implement alerts. This propagation should have completed by now, and you should be ready to go.

- **RBAC permissions.** In this exercise, you will assign the necessary RBAC role group to Lynne Robbins, who is the user that Holly selected for testing alerts in Adatum's Microsoft 365 pilot project. 

### Task 1 – Assign RBAC Permissions for Alert Notification Testing

The alerts a user can see on the **View alerts** page are dependent on the user's assigned RBAC roles, which determine the depth of insight and control a user has. How is this accomplished? The management roles assigned to users (based on their membership in role groups in Microsoft 365) determine which alert categories a user can see on the **View alerts** page (this was covered in the topic on Alerts in the previous module). 

For Adatum’s pilot project, Lynne Robbins has been selected to test the alert notification system. For Lynne to be able to view alerts and receive alert notifications, she must first be assigned appropriate RBAC permissions in Microsoft Defender XDR.

The three alerts that you will create in this lab are assigned to two Alert categories: **Permissions** and **Data Loss Prevention**. The Compliance Data Administrator role group, which includes the Compliance Administrator role, provides permissions for these two alert categories; therefore, assigning Lynne Robbins to this role group will enable her to view the alerts that are created in this lab.


|                               | **Data governance** | **Data loss prevention** | **Mail flow** | **Permissions** | **Threat Management** | **Others** |
|:-------------------------------:|:---------------------:|:--------------------------:|:---------------:|:-----------------:|:-----------------------:|:------------:|
| Compliance Data Administrator | X                   | X                        |               | X               |                       | X          |

Perform the following steps to assign Lynne Robbins the Compliance Data Administrator role group, which includes the Compliance Administrator role.

1. At the end of the prior lab, you were logged into LON-CL2. This lab will use LON-CL1.  <br/>

    Switch to **LON-CL1**. 

2. On **LON-CL1**, in your Edge browser, you should still be logged into Microsoft 365 as **Holly Dickson**. 

3. If necessary, select the **Microsoft 365 admin center** tab in your browser. In the left-hand navigation pane, under the **Admin centers** group, select **Security**. This opens the Microsoft Defender portal in a new tab.

4. In the **Microsoft Defender** portal, scroll down towards the bottom of the left-hand navigation pane and select **Permissions**.

5. On the **Permissions** page, there are four sections - Microsoft Defender XDR, Microsoft Entra ID, Email & collaboration roles, and Cloud Apps. Under the **Email & collaboration roles** section, select **Roles**. 

6. In the list of roles that appears, select the **Name** column heading to sort the roles in ascending alphabetical name order. Select the **Compliance Data Administrator** role group (select the name of the role group and not the check box). 

7. In the **Compliance Data Administrator** pane that appears, note the list of roles that have been assigned to this role group. Scroll to the bottom of the pane and note that there are no members in this role group. Scroll back to the top of the pane and select the **Edit** option. 

8. In the **Edit members of the role group** window, select the **Choose users** button. 

9. In the **Choose users** window, a partial, unsorted list of users appears. Enter **Lynne** in the **Search** field and hit Enter. A list of users appears whose name includes Lynne. Select the check box next to **Lynne Robbins** and then select the **Select** button at the bottom of the pane.

10. In the **Edit members of the role group** window, Lynne's name should appear. Select **Next**.

11. In the **Review the role group and finish** window that appears, note that Lynne also appear here as a member of the role group. Select **Save.**

12. In the **You successfully updated the role group** pane, select **Done**.

13. Leave all tabs in your Edge browser open for the next lab exercise.

You have now added Lynne Robbins to the Compliance Data Administrator role group.


# Proceed to Lab 6 - Exercise 2
