# Learning Path 6 - Lab 6 - Exercise 4 - Test the Default eDiscovery Alert

In this exercise you will test a default Microsoft 365 alert policy that notifies all tenant administrators, such as Holly Dickson, whenever an eDiscovery search has been created or exported.

**Note:** Creating an eDiscovery alert of this nature is important because an eDiscovery search, when left unregulated, can pull sensitive content that can be exported to an unauthorized source.

### Task 1 – Review the default eDiscovery Alert

In this task, you will verify whether a default Microsoft 365 alert is triggered when somebody in your tenant creates an eDiscovery search or exports data from an existing search. Since Holly Dickson is assigned the Global Administrator role, she is automatically a member of the Tenant Admins and will be one of the recipients of this alert. 

1. You should still be in **LON-CL2** after completing the prior lab exercise. You should now switch back to **LON-CL1**.

2. On **LON-CL1**, in your Edge browser, you should still be logged into Microsoft 365 as **Holly Dickson**. 

3. In your Edge browser, select the **Alert policy - Microsoft 365 security** tab. This tab should still be displaying the **Alert policy** window from the prior lab exercise (if not, then in the left-hand navigation pane, select **Policies & rules** and then select **Alert policy**).

4. On the **Alert policy** page, you want to search through the default System policies for a policy named **eDiscovery search started or exported**. Since there are so many pre-existing system policies, the easiest way to locate the policy is to search for it. In the **Search** field at the top of the screen, enter **eDiscovery** and then hit Enter. 

5. In the policy list, select the **eDiscovery search started or exported** policy that appears. 

6. An **eDiscovery search started or exported** pane should appear. Scroll down through the pane and verify the default settings for this predefined policy are configured as follows:

	- Status: **On**
	
	- Conditions: Select the down arrow for the **Create alert settings** section to expand it, then verify the following settings:  <br/>

		- Conditions: **Activity is eDiscoverySearchStartedOrExported**

		- Aggregation: **Single event**

		- Scope: **All users**

	- Email recipients: Select the down arrow for the **Set your recipients** section to expand it, then verify the following settings:  <br/>

		- Recipients: **TenantAdmins**

		- Daily notification limit: **No limit**

7. At the top of the pane, select the **Edit policy** button.

8. On the **eDiscovery search started or exported** window that appears, the only setting that can be edited for this default policy is the **Email recipients** setting. This window enables you to edit the email recipients who are notified when this policy is triggered. You will not change the value here; instead, the purpose of this step is to show you how to change the recipient list in your real-world implementations for any of the default system policies.  <br/>

	 Select the **Cancel** button at the bottom of the window.

9. On the **eDiscovery search started or exported** pane, select the **X** in the upper-right corner to close it. <br/>

	**Note:** You can also edit a policy's setting by selecting the vertical ellipsis icon under the **Actions** column at the far-right end of the policy's row on the **Alert Policy** window. 

10. Leave all the Edge browser tabs open for the next task.

You have now reviewed the default Microsoft 365 eDiscovery alert that notifies tenant admins when an eDiscovery search is created or exported.

**Note:** Rather than waiting up to 15 minutes for the email notification to be generated to validate this eDiscovery alert, you will validate this alert in Exercise 7, task 3 of this lab.

# Proceed to Lab 6 - Exercise 5
