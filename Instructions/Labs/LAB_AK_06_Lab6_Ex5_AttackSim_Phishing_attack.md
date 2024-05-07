# Learning Path 6 - Lab 6 - Exercise 5 - Conduct a Spear Phishing attack using Attack Simulation training

Holly Dickson is concerned that some users at Adatum may require education about phishing attacks. As part of her pilot project, Holly has decided to use the Microsoft 365 Attack simulation training feature to determine her users' susceptibility to phishing attacks.

**Note:** To use Microsoft's Attack Simulation training feature to simulate a phishing attack, you must first enable Multifactor Authentication (MFA) for either your entire organization or for just the Global administrator who will run the simulation. Because Microsoft requires MFA for all user sign-ins in the lab's trial tenant, you don't need to enable it for this exercise. Keep in mind, however, that in your real-world Microsoft 365 deployments, you will need to implement this MFA requirement if you plan to use Microsoft's Attack Simulation training.

### Task 1: Configure and launch a Spear Phishing attack

Because MFA is already turned on in this trial tenant for all user sign-ins, Holly is ready to run Microsoft 365's Attack simulation training feature and launch a simulated spear phishing attack. This will provide visibility into how well Adatum is prepared to handle this type of security attack. 

Microsoft 365 includes an Attack simulation training feature that enables you to create simulations and run them against all your users or a select group of users. Each phishing attack includes what is referred to as the "payload", which is the message in the system-generated email that contains the malicious component hackers use to gather information, deposit malicious code, and so on. The Attack simulation training feature includes a number of payload templates that you can choose from, and you can create your own payload if you so desire. 

In this lab exercise, you will use one of the existing payload templates. In the next lab exercise, you will create your own custom payload.

1. On LON-CL1, in your Edge browser, you should still be logged into Microsoft 365 as **Holly Dickson**. 

2. You should still have the **Microsoft Defender** portal open in your **Edge** browser from the prior task. If not, enter **https://security.microsoft.com** in the address bar, and then if you receive a dialog box asking for a second form of authentication, proceed through the verification process. If not, sign-in as Holly using the **Administrative username** and **Administrative password** provided by your lab-hosting provider and if required, complete the MFA sign-in process.

3. In the **Microsoft Defender** portal, under the **Email & collaboration** section in the left-hand navigation pane, select **Attack simulation training**. If a **Welcome to Attack simulation training** window appears, select **Close**.

4. On the **Attack simulation training** page, Holly has decided to conduct a simulated account breach in which she will use a URL to try and obtain usernames and passwords. This is referred to in the Attack Simulator as a **Credentials Harvest** attack. <br/>

	Note the tabs that appear across the top of the **Attack simulation training** page (where the **Overview** tab is displayed by default). You can launch this attack either from **Simulations** tab or by selecting the **Launch a simulation** link on the **Overview** tab. Since the **Overview** tab has additional information and is the default page when selecting the **Attack simulation training** service, it is recommended that you launch it from there so that you can learn about the specifics of this type of attack. <br/>
	
	On the **Overview** tab, scroll down to the **Recommendations** section. You may need to scroll up or down in this section to see the **Launch a phishing simulation using other social engineering techniques** recommendation. Under this recommended attack, select **Create another simulation with new technique**. This initiates the **Create Simulation** wizard.

5. On the **Select Technique** page, review the specific information related to the **Credentials Harvest** attack type option. At the bottom of the **Credential Harvest** option, select the **View details of Credential harvest** link. This opens a **Credential Harvest** pane on the right. Review the **Description** and the **Simulation steps** for this type of attack. When you're done, close the **Credential Harvest** pane.

6. On the **Select Technique** page, select the **Credentials Harvest** attack type if it's not already selected by default, and then select **Next**.

7. In the **Simulation** wizard, the steps involved in the simulation are displayed in the left-hand pane. While you can manually create a phishing campaign, it is recommended that you take advantage of the available templates that will prefill most of the information for you. The key to a successful phishing attack is to create a very intriguing, real-world looking email, and the templates provide very creative solutions. <br/>

	On the **Name Simulation** page, provide the following information: 
	- Simulation Name: **PhishingTest1**
	- Description: **This simulation provides insight on targeted email threats against users inside the company**

8. Select **Next**.

9. On the **Select payload and login page** window, select the check box to the left of the **Payment for Package** payload. Select **Next**.

	**Note:** If the **Payment for Package** payload does not appear, select another Payload of your choice. A payload is the link or attachment in the simulated phishing email message that's presented to users. In the real-world, you'd want to use a payload that works best for your organization.

11. On the **Target Users** page, select the **Include all users in my organization** option. This will display all of Adatum's users. Select **Next**, and then on the **Exclude users** page, select **Next** again.

12. On the **Assign Training** page, under the **Preferences** section, the **Assign training for me (Recommended)** option should be selected by default (if not, select it now). Select the **Due Date** field. In the drop-down menu that appears, select **7 days after Simulation ends** and then select **Next**.

13. On the **Select Phish landing page** window, scroll down to the **Global landing pages** tab, which should be displayed by default. This tab displays a list of predefined landing page templates. Select the **Microsoft Landing Page Template 1** name to preview the page. 

14. A preview of the **Microsoft landing page** for this template appears in a new pane. This preview pane provides an example of what the landing page will look like when someone experiences a phishing attack and the simulation uses **Microsoft Landing Page Template 1**. Scroll down through this preview panel and review the features. When you're finished, select the **Close** button at the bottom of the preview pane. 

15. You will now look at some of the other landing page templates until you find one that you want to use for this simulation. On the **Select Phish landing page** window, select one of the other templates (select the name of the template and not its checkbox). Examine the preview pane and note how the landing page for this template is different from **Microsoft Landing Page Template 1**. When you're finished, select the **Close** button at the bottom of the preview pane.

16. Repeat the prior step and select another template. Note how this template is different from the other two you looked at. <br/>

	Repeat this step as many times as you would like until you find a template that you want to use for this simulation. When you're finished reviewing templates, select the checkbox for the template that you want to use on the **Select Phish landing page** and then select **Next**.

17. On the **Select end user notification** page, choose how you want the end user to be notified. For the purpose of this lab, select **Microsoft default notification (recommended)**. In the list of notifications that appears, configure the following notifications:

	 - Microsoft default positive reinforcement notification - set **Delivery preferences** to **Deliver after simulation ends**
	 - Microsoft default training reminder notification - set **Delivery preferences** to  **Weekly**

18. Select **Next**.

19. On the **Launch Details** page, select the **Launch this simulation as soon as I'm done** option and then select **Next**.

20. On the **Review Simulation** page, review the entered information. If anything needs to be changed, select the appropriate **Edit** option to make the change. Once everything is correct, select **Submit**. It may take a few minutes before you receive a confirmation stating **Simulation has been scheduled for launch**. Select **Done**. <br/>

	**Note:** Once the simulated spear phishing attack is launched, it may take up to 15 minutes for the system generate the email and send it to all Adatum users. Rather than waiting for the email to be generated, you will validate the email and review the diagnostic results of the attack in Exercise 7, task 4 of this lab.

21. Leave your Edge browser and all tabs open and proceed to the next exercise.
    
# Proceed to Lab 6 - Exercise 6
