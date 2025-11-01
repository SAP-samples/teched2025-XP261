# Exercise 4 - Assign an access package in Microsoft Entra ID

*Estimated Time: **30 min***

In this exercise, you will first provision the newly onboarded employee from SuccessFactors to Entra. In Entra, you will create an [access package](https://learn.microsoft.com/en-us/entra/id-governance/entitlement-management-access-package-first) that contains the groups that represents the role in the SAP S4A system, and the role collection in BTP. By assigning the user to the access package, the user becomes a member in both groups. These group memberships in Entra will assign the user in the upcoming exercises to the role in S4A and the role collection in BTP.


<img src="./images/Intro4.png">



## Table of Contents
- [4.1 SAP authorization assignment in Microsoft Entra ID ](#41-sap-authorization-assignment-in-microsoft-entra-id)
- [4.2 Provisioning to SAP SCI](#42-provisioning-to-sap-sci)
- [Summary](#summary)


## 4.1 SAP authorization assignment in Microsoft Entra ID 

1.    Go back to your browser tab where you logged on to the Entra admin center in the [Getting Started](..\ex0\README.md) section, or [login again](https://entra.microsoft.com) as the Entra administrator user **admin`NNN`@bestruncorp.onmicrosoft.com**.

Replace `NNN` with the number of your seat, for example **admin`045`@bestruncorp.onmicrosoft.com**.  

  <img src="./images/S4-1.png">
  
2.    Select **Enterprise apps** from the navigation menu. 
   
   <img src="./images/S4-2.png">
  
3.    Enter your seat number `NNN` in the search bar, for example `004`.<br><br>Select the enteprise app **SAP SuccessFactors Provisioning `NNN`**.<br><br>Replace `NNN` with your seat number, for example **SAP SuccessFactors Provisioning `004`**  
  
  
<img src="./images/S4-3.png">

4.   Select **Provisioning** from the app navigation menu. 
  
<img src="./images/S4-4.png">
  
5.    Select **Provisioning on demand** from the Provisioning navigation menu.<br><br>In the **Select a user** field, enter your new employee's **person Id** that you entered in the previous step **3.4**.<br><br>Click **Provision**.  
  
<img src="./images/S4-5.png">
 
  
6.   Wait for the **Perform action** report to show the results of the successful creation of your new user account in Entra ID.<br>Click **Close**.  

<img src="./images/S4-6-1.png">
  
  
 7.   On the Entra main navigation menu, scroll down to the **ID Governance** section and expand it.<br><br>Select **Entitlement management** from the submenu. 
 
 <img src="./images/S4-7.png">

8.    Select **Access packages** from the menu.<br><br>Click **New Access Package**.  

<img src="./images/S4-8.png">

9.   Enter the following values:<ul><li>**Name**: SAP `NNN`</li><li>**Description**: Access package for student `NNN`</li></ul><br>Replace `NNN` with your seat number.

<img src="./images/S4-9.png">

Click **Next: Resource roles**. 
  
10.    Click **Groups and Teams**. 

<img src="./images/S4-10.png">
  
11.    In the search bar, enter your seat number with three digits (`NNN`), for example `014`.<br><br>Activate the checkboxes for both groups from the search results.<br><br>Click *Select*.   

<img src="./images/S4-1111.png">

12.    Select **Member** from the **Role** drop-down list for both groups. 

13.    Click **Next: Requests**.

<img src="./images/S4-12.png">

14.   Select the options **For users in your directory** and **All members (excluding guests)**.<be><br>
Set **Require approval** to **No**<br>and **Disable assignment emails** to **Yes**.<br><br>
Click **Next: Requestor information**.  

<img src="./images/S4-14.png">

15.   Click **Next: Lifecycle**.  

<img src="./images/S4-15.png">

16.   Select <ul><li>**Never** for the **Access package assignment expiration**</li><li>**No** for **Users can request specific timeline**</li></ul>**Deactivate** the checkbox for **Require access reviews**.<br><br>Click **Next: Rules**.  


<img src="./images/S4-16.png">

17.   Click **Next: Review + create**. 

<img src="./images/S4-17.png">
 
18.   Click **Create**.  

<img src="./images/S4-18.png">

19.   Select **Assignments** from the navigation menu.
Click **New assignment**.

<img src="./images/S4-19.png">

20.   Select **Initial Policy** from the **Select Policy** drop-down box.
Click **Add users**.

<img src="./images/S4-20.png">

21.    Enter the new user's *person Id* (see step **3.4**). Activate the checkbox for your user **Jane Smith-`<NNN>`** in the search resutls.<br><br>Click **Select**.  

<img src="./images/S4-21.png">

22.   Click **Add**.  
<img src="./images/S4-22.png">

23.   Click **Refresh**. Your user should be listed in the assignments for your access package.  
<img src="./images/S4-23.png">

In a productive setup you would schedule a job to go through the assignments in the Access Package and provision them to the backend applications. In the favor of time, you will provision these groups on-demand to the target solution, the SAP SCI tenant. 

## 4.2 Provisioning to SAP SCI

1. In Microsoft Entra admin center, under **Enterprise apps** search for your SAP Cloud Identity Services tenant by entering your seat number `NNN` in the search bar.<br><br>Select the enterprise app **SAP SCI BestRunCorp Tenant `NNN`** from the list.

<img src="./images/S4-25.png">

2. Select **Provisioning** from the navigation menu.

<img src="./images/S4-26.png">

3. Select **Provisioning on demand** from the navigation menue and search for the first group **TECHED_BTP_FINANCE_ADMIN_`NNN`**.

<img src="./images/S52-31.png">

4. Select **View members only** and select your user from the list.

<img src="./images/S42-41.png">

Click **Provisioning**. 

5. Let's analyze the provisioning details. As the group existed in SAP SCI, it was only updated with the new assignment. 
<img src="./images/S4-291.png">

6. On the other hand, the user did not exist in your SAP SCI tenant, so it was created now.

<img src="./images/S4-30.png">

7. Let's repeat the same steps for **Provisioning another object**, the one corresponding to the SAP S/4HANA system role.

<img src="./images/S4-31.png">

8. Search for the group **TECHED_S4A_PROCUREMENT_ADMIN_`NNN`**

<img src="./images/S4-111111.png"> 


9. Again, select the option **View members only**, and search your user from the list.

<img src="./images/S4-33.png">

Click **Provisioning**.

10. Let's analyze the results. Similar to the previous provisioning, our group was only updated.

<img src="./images/S4-34.png">

11. This time the user creation shows that this entry was skipped. This is expected, because the user was created at the previous provisioning. 

<img src="./images/S4-35.png">

Copy the **User principle name** because you will need it later. 

12. Navigate to your SAP SCI console and navigate to the second tab **Users & Authorizations** and choose **Users**. Choose your newly created users and navigate to the **Group** tab.  You can search by email address (the user principal name from earlier).

<img src="./images/S4-1211.png">

You will notice the two assigned Microsoft Entra groups.

## Summary

You've now provisioned the new employee to Entra, created an access package for her, and assigned her to the package. This made the new employee Jane Smith a member in the group representing the role in SAP S/4 system, and a member in the group representing the role collection in the BTP subaccount. The newly created user with authorizations is now present in SAP SCI. In the next exercise, you will continue the provisioning to the SAP back-end systems.

Continue to - [Exercise 5 - Provisioning to SAP back-end systems](../ex5/README.md), or go back to the [overview](../README.md).


