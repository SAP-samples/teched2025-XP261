# Exercise 4 - Assign SAP access package in Microsoft Entra ID

In this exercise, we will first provision the newly onboarded employee from SuccessFactors to Entra. In Entra, you will create an [access package](https://learn.microsoft.com/en-us/entra/id-governance/entitlement-management-access-package-first) that contains the groups that represents the role in the SAP S4A system, and the role collection in BTP. By assigning the user to the access package, the user becomes a member in both groups. These group memberships in Entra will assign the user in the upcoming exercises to the role in S4A and the role collection in BTP.

| Step   | Description                | Screenshot |
| :----- | :------------------------- | :--------- |
| 4.1    | [Login to the Entra admin center](https://entra.microsoft.com) as the Entra administrator user `adminNNN`. Replace `NNN` with the number of your seat, for example `admin045`. |<a href="./images/4-1.jpg" target="_blank"><img src="./images/4-1.jpg" width="250"/></a>|
| 4.2    | Select **Enterprise apps** from the navigation menu. |<a href="./images/4-2.jpg" target="_blank"><img src="./images/4-2.jpg" width="250"/></a>|
| 4.3    | Enter your seat number `NNN` in the search bar, for example `004`.<br><br>Select the enteprise app **SAP SuccessFactors Provisioning `NNN`**.<br><br>Replace `NNN` with your seat number, for example **SAP SuccessFactors Provisioning `004`** |<a href="./images/4-3.jpg" target="_blank"><img src="./images/4-3.jpg" width="250"/></a>|
| 4.4    | Select **Provisioning** from the app navigation menu.|<a href="./images/4-4.jpg" target="_blank"><img src="./images/4-4.jpg" width="250"/></a>|
| 4.5    | Select **Provisioning on demand** from the Provisioning navigation menu.<br><br>In the **Select a user** field, enter your new employee's **person Id** that you entered in the previous step **3.4**.<br><br>Click **Provision**. |<a href="./images/4-5.jpg" target="_blank"><img src="./images/4-5.jpg" width="250"/></a>|
| 4.6    | Wait for the **Perform action** report to show the results of the successful creation of your new user account in Entra ID.<br><br>Click **Close**. |<a href="./images/4-6.jpg" target="_blank"><img src="./images/4-6.jpg" width="250"/></a>|
| 4.7    | On the Entra main navigation menu, scroll down to the **ID Governance** section and expand it.<br><br>Select **Entitlement management** from the submenu.|<a href="./images/4-7.jpg" target="_blank"><img src="./images/4-7.jpg" width="250"/></a>|
| 4.8    | Select **Access packages** from the menu.<br><br>Click **New Access Package**. |<a href="./images/4-8.jpg" target="_blank"><img src="./images/4-8.jpg" width="250"/></a>|
| 4.9    | Enter the following values:<ul><li>**Name**: SAP `NNN`</li><li>**Description**: Access package for student `NNN`</li></ul><br>Replace `NNN` with your seat number.<br><br>Click **Next: Resource roles**.|<a href="./images/4-9.jpg" target="_blank"><img src="./images/4-9.jpg" width="250"/></a>|
| 4.10   | Click **Groups and Teams**.|<a href="./images/4-10.jpg" target="_blank"><img src="./images/4-10.jpg" width="250"/></a>|
| 4.11   | In the search bar, enter your seat number with three digits (`NNN`), for example `014`.<br><br>Activate the checkboxes for both groups from the search results.<br><br>Click *Select*. |<a href="./images/4-11.jpg" target="_blank"><img src="./images/4-11.jpg" width="250"/></a>|
| 4.12   | Select **Member** from the **Role** drop-down list for both groups. |<a href="./images/4-12.jpg" target="_blank"><img src="./images/4-12.jpg" width="250"/></a>|
| 4.13   | Click **Next: Requests**. |<a href="./images/4-13.jpg" target="_blank"><img src="./images/4-13.jpg" width="250"/></a>|
| 4.14   | Select the options **For users in your directory** and **All members (excluding guests)**.<br><br>Set **Require approval** to **No**, and **Disable assignment emails** to **Yes**.<br><br>Click **Next: Requestor information**. |<a href="./images/4-14.jpg" target="_blank"><img src="./images/4-14.jpg" width="250"/></a>|
| 4.15   | Click **Next: Lifecycle**. |<a href="./images/4-15.jpg" target="_blank"><img src="./images/4-15.jpg" width="250"/></a>|
| 4.16   | Select <ul><li>**Never** for the **Access package assignment expiration**</li><li>**No** for **Users can request specific timeline**</li></ul>**Deactivate** the checkbox for **Require access reviews**.<br><br>Click **Next: Rules**. |<a href="./images/4-16.jpg" target="_blank"><img src="./images/4-16.jpg" width="250"/></a>|
| 4.17   | Click **Next: Review + create**.|<a href="./images/4-17.jpg" target="_blank"><img src="./images/4-17.jpg" width="250"/></a>|
| 4.18   | Click **Create**.|<a href="./images/4-18.jpg" target="_blank"><img src="./images/4-18.jpg" width="250"/></a>|
| 4.19   | Select **Assignments** from the navigation menu.<br><br>Click **New assignment**.|<a href="./images/4-19.jpg" target="_blank"><img src="./images/4-19.jpg" width="250"/></a>|
| 4.20   | Select **Initial Policy** from the **Select Policy** drop-down box.<br><br>Click **Add users**.|<a href="./images/4-20.jpg" target="_blank"><img src="./images/4-20.jpg" width="250"/></a>|
| 4.21   | Enter the new user's *person Id* (see step **3.4**). Activate the checkbox for your user **Jane Smith-`<NNN>`** in the search resutls.<br><br>Click **Select**. |<a href="./images/4-21.jpg" target="_blank"><img src="./images/4-21.jpg" width="250"/></a>|
| 4.22   | Click **Add**. |<a href="./images/4-22.jpg" target="_blank"><img src="./images/4-22.jpg" width="250"/></a>|
| 4.23   | Click **Refresh**. Your user should be listed in the assignments for your access package. |<a href="./images/4-23.jpg" target="_blank"><img src="./images/4-23.jpg" width="250"/></a>|

## Summary

You've now provisioned the new employee to Entra, created an access package for her, and assigned her to the package. This made the new employee Jane Smith a member in the group representing the role in SAP S/4 system, and a member in the group representing the role collection in the BTP subaccount.

Continue to - [Exercise 5 - Excercise 5 ](../ex5/README.md)


