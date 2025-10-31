# Exercise 4 - Assign an access package in Microsoft Entra ID

In this exercise, you will first provision the newly onboarded employee from SuccessFactors to Entra. In Entra, you will create an [access package](https://learn.microsoft.com/en-us/entra/id-governance/entitlement-management-access-package-first) that contains the groups that represents the role in the SAP S4A system, and the role collection in BTP. By assigning the user to the access package, the user becomes a member in both groups. These group memberships in Entra will assign the user in the upcoming exercises to the role in S4A and the role collection in BTP.


<img src="./images/Intro4.png">



## Table of Contents
- [4.1 SAP authorization assignment in Microsoft Entra ID ](#41-sap-authorization-assignment-in-microsoft-entra-id)
- [4.2 Provisioning to SAP SCI](#42-provisioning-to-sap-sci)
- [Summary](#summary)


## 4.1 SAP authorization assignment in Microsoft Entra ID 

1.    [Login to the Entra admin center](https://entra.microsoft.com) as the Entra administrator user `adminNNN`. Replace `NNN` with the number of your seat, for example `admin045`.  

  <img src="/exercises/ex4/images/S4-1.png">
  
2.    Select **Enterprise apps** from the navigation menu. 
   
   <img src="/exercises/ex4/images/S4-2.png">
  
3.    Enter your seat number `NNN` in the search bar, for example `004`.<br><br>Select the enteprise app **SAP SuccessFactors Provisioning `NNN`**.<br><br>Replace `NNN` with your seat number, for example **SAP SuccessFactors Provisioning `004`**  
  
  
<img src="/exercises/ex4/images/S4-3.png">

4.   Select **Provisioning** from the app navigation menu. 
  
<img src="/exercises/ex4/images/S4-4.png">
  
5.    Select **Provisioning on demand** from the Provisioning navigation menu.<br><br>In the **Select a user** field, enter your new employee's **person Id** that you entered in the previous step **3.4**.<br><br>Click **Provision**.  
  
<img src="/exercises/ex4/images/S4-5.png">
 
  
6.   Wait for the **Perform action** report to show the results of the successful creation of your new user account in Entra ID.<br><br>Click **Close**.  

<img src="/exercises/ex4/images/S4-6.png">
  
  
 7.   On the Entra main navigation menu, scroll down to the **ID Governance** section and expand it.<br><br>Select **Entitlement management** from the submenu. 
 
 <img src="/exercises/ex4/images/S4-7.png">

8.    Select **Access packages** from the menu.<br><br>Click **New Access Package**.  

<img src="/exercises/ex4/images/S4-8.png">

9.   Enter the following values:<ul><li>**Name**: SAP `NNN`</li><li>**Description**: Access package for student `NNN`</li></ul><br>Replace `NNN` with your seat number.

<img src="/exercises/ex4/images/S4-9.png">

Click **Next: Resource roles**. 
  
10.    Click **Groups and Teams**. 

<img src="/exercises/ex4/images/S4-10.png">
  
11.    In the search bar, enter your seat number with three digits (`NNN`), for example `014`.<br><br>Activate the checkboxes for both groups from the search results.<br><br>Click *Select*.   

<img src="/exercises/ex4/images/S4-1111.png">

12.    Select **Member** from the **Role** drop-down list for both groups. 

13.    Click **Next: Requests**.

<img src="/exercises/ex4/images/S4-12.png">

14.   Select the options **For users in your directory** and **All members (excluding guests)**.
Set **Require approval** to **No**, and **Disable assignment emails** to **Yes**.
Click **Next: Requestor information**.  

<img src="/exercises/ex4/images/S4-14.png">

15.   Click **Next: Lifecycle**.  

<img src="/exercises/ex4/images/S4-15.png">

16.   Select <ul><li>**Never** for the **Access package assignment expiration**</li><li>**No** for **Users can request specific timeline**</li></ul>**Deactivate** the checkbox for **Require access reviews**.<br><br>Click **Next: Rules**.  


<img src="/exercises/ex4/images/S4-16.png">

17.   Click **Next: Review + create**. 

<img src="/exercises/ex4/images/S4-17.png">
 
18.   Click **Create**.  

<img src="/exercises/ex4/images/S4-18.png">

19.   Select **Assignments** from the navigation menu.
Click **New assignment**.

<img src="/exercises/ex4/images/S4-19.png">

20.   Select **Initial Policy** from the **Select Policy** drop-down box.
Click **Add users**.

<img src="/exercises/ex4/images/S4-20.png">

21.    Enter the new user's *person Id* (see step **3.4**). Activate the checkbox for your user **Jane Smith-`<NNN>`** in the search resutls.
Click **Select**.  

<img src="/exercises/ex4/images/S4-21.png">

22.   Click **Add**.  
<img src="/exercises/ex4/images/S4-22.png">

23.   Click **Refresh**. Your user should be listed in the assignments for your access package.  
<img src="/exercises/ex4/images/S4-23.png">

In a productive setup you would schedule a job to go through the assignments in the Access Package and provision them to the backend applications. In the favor of time, you will provision these groups on-demand to the target solution, the SAP SCI tenant. 

## 4.2 Provisioning to SAP SCI

1. In your Microsoft Entra admin center, Under **Enterprise apps**  search for the SAP Cloud Identity Services tenant. 

<img src="/exercises/ex4/images/S4-25.png">

2. Click **Provisioning**.

<img src="/exercises/ex4/images/S4-26.png">

3. Clicl **Provisioning on demand** and search for the first groups **TECHED_BTP_FINANCE_ADMIN_NNN**.

<img src="/exercises/ex4/images/S52-31.png">

4. Select **View all users** and search for the user that you created in SAP SFSF.

<img src="/exercises/ex4/images/S42-41.png">

Click **Provisioning**. 

5. Let's analyze the provisioning details. As the group existed in SAP SCI, it was only updated with the new assignment. 
<img src="/exercises/ex4/images/S4-291.png">

6. On the other hand, the user did not exist in SAP SCI so it was created now.

<img src="/exercises/ex4/images/S4-30.png">

7. Let's repeat the same steps for **Provisioning another object**, the one corresponding to the SAP S/4HANA system role.

<img src="/exercises/ex4/images/S4-31.png">

8. Search for the prefix **TECHED_S4**

<img src="/exercises/ex4/images/S4-111111.png"> 



9. Search for the same user

<img src="/exercises/ex4/images/S4-33.png">

and press **Provisioning**.

10. Let's analyze the results. Similarly to the previous provisioning, our group was only updated.

<img src="/exercises/ex4/images/S4-34.png">

11. This time the user creation shows that this entry was skipped. This is expected, because the user was created at the previous provisioning. 

<img src="/exercises/ex4/images/S4-35.png">

Copy the User principle name because you will need it later. 

12. Navigate to your SAP SCI console and navigate to the second tab **Users & Authorizations** and choose **Users**. Choose your newly created users and navigate to the **Group** tab.  You can search by email address (the user principal name from earlier).

<img src="/exercises/ex4/images/S4-1211.png">

You will notice the two assigned Microsoft Entra groups.

## Summary

You've now provisioned the new employee to Entra, created an access package for her, and assigned her to the package. This made the new employee Jane Smith a member in the group representing the role in SAP S/4 system, and a member in the group representing the role collection in the BTP subaccount. The newly created user with authorizations is now present in SAP SCI. In the next exercise, you will continue the provisioning to the SAP back-end systems.

Continue to - [Exercise 5 - Provisioning to SAP back-end systems](../ex5/README.md), or go back to the [overview](../README.md).


