# Exercise 1 - Import SAP back-end roles in SAP Cloud Identity Services 

In this exercise, we will import the back-en authorizations to IdDS. For this, we will create IPS source and target systems.  

* We will start by creating source systems for importing authorizations in SAP SCI from the SAP S/4 and the BTP subaccount. 
* These authorization will be sent via IPS to the Entra ID tenant in [exercise 2](../ex2/README.md). Entra ID is the IdM solution responsible for centrally managing the assignments, therefore we need the SAP authorizations in the Entra ID tenant. For this purpose, we will create a target system that corresponds to Entra ID. 
* We will create systems for assignment and user provisioning to the SAP solutions
 
<!-- @import "[TOC]" {cmd="toc" depthFrom=1 depthTo=6 orderedList=false} -->
## Table of Contents
- [Exercise 1.1 IPS source systems creation](#exercise-11-ips-source-systems-creation)
    - [Exercise 1.1.1 Create IPS source system for syncing authorizations from back-end](#exercise-111-create-ips-source-system-for-syncing-authorizations-from-back-end)
    - [Exercise 1.1.2 Create one IPS source system for syncing authorizations to Entra ID](#exercise-112-create-one-ips-source-system-for-syncing-authorizations-to-entra-id)
    - [Exercise 1.1.3 Create one IPS source system for provisioning to SAP back-end applications](#exercise-113-create-one-ips-source-system-for-provisioning-to-sap-back-end-applications)
- [Exercise 1.2 IPS target systems creation](#exercise-12-ips-target-systems-creation)
    - [Exercise 1.2.1 Create one IPS target system for provisioning to Entra ID](#exercise-121-create-one-ips-target-system-for-provisioning-to-entra-id)
    - [Exercise 1.2.2 Create two IPS source systems for provisioning to the Local Identity Directory](#exercise-122-create-two-ips-source-systems-for-provisioning-to-the-local-identity-directory)
    - [Exercise 1.2.3 Create two IPS source system for provisioning to the SAP back-end applications](#exercise-123-create-two-ips-source-system-for-provisioning-to-the-sap-back-end-applications)
- [Exercise 1.3 Initial Load in SAP Cloud Identity Services](#exercise-13-initial-load-in-sap-cloud-identity-services)
- [Summary](#summary)

## Exercise 1.1  Download the JSON files 

Save all these  JSON files locally because you will need to import them in the next step. 

[BTP CF import source](./images/BTPCFimportsource.json), 
[Non-SAP import source](./images/NON-SAPimportsource.json)  
[SAP provisioning source](./images/SAPprovisioningsource.json)
[S4A import source](./images/S4Aimportsource.json)
[BTP CF import target](./images/BTPCFimporttarget.json)
[S4A import target](./images/S4Aimporttarget.json)
[Non-SAP import target](./images/Non-SAPimporttarget.json)
[BTP CF provisioning target](./images/BTPCFprovisioningtarget.json)
[S4A provisioning target](./images/S4Aprovisioningtarget.json)

Press on **Download Raw File** in the window that will open. 

<img src="/exercises/ex1/images/S14.png" width=50% height=50%>

## Exercise 1.2  SAP BTP onboarding 

1. Navigate to the SCI administrative console that corresponds to your seat. From the third tab Identity Provisioning please choose **Source Systems**.
<img src="/exercises/ex1/images/S11.png" width=50% height=50%>

2. Click on the **Add** button and then click on Browse and search for the **BTP CF import source** file that you previously saved.

<img src="/exercises/ex1/images/S12.png" width=100% height=100%>

3. Navigate  to the third tab  **Properties** tab and fill in the red marked properties: 
<img src="/exercises/ex1/images/S13.png" width=50% height=50%>

For the property *ips.application.id*, you will need to search for the Application ID value of the BTP subaccount in IAS. To find this value, duplicate this browser tab and navigate in the SCI console to the 4th tab **Applications & Resources** and choose **Applications**. 
<img src="/exercises/ex1/images/S22.png" width=50% height=50%>

Search for the application that corresponds to you seat number: XP261_0NN and copy the value of the Application ID. 
<img src="/exercises/ex1/images/S23.png" width=50% height=50%>

4. Now save your system. 
5. Let's add a target system for this newly created source system. Navigate to the **Target Systems**. Click on the **Add** button and then click on Browse and search for the **BTP CF import target** file that you previously saved.
6. For the source system, choose from the drop-down menu the **BTP CF import source** system that you created at earlier. This will ensure that the entries coming from the BTP Subaccount will be provisioned to the Local Identity Directory.
7. Navigate to the Properties Tab and add the values for the properties that are marked in red, if any.
8. Save your system. 

9. Let's run the initial load job. Navigate to your **Source Systems**.
10. Choose the source system **BTP CF import source** and navigate to the tab **Jobs**. 
11. Run the job.
<img src="/exercises/ex1/images/S19.png" width=50% height=50%>

12. Navigate to Provisioning Logs and check the provisioning status and the details. 

13. Let's search for Groups that start with **TECHED_**. You will notice that the Application Name indicates the source system.
<img src="/exercises/ex1/images/S21.png" width=50% height=50%>


## Exercise 1.3  SAP S/4HANA Cloud Private Edition onboarding 

1. Navigate to the SCI administrative console that corresponds to your seat. From the third tab Identity Provisioning please choose **Source Systems**.
<img src="/exercises/ex1/images/S11.png" width=50% height=50%>

2. Click on the **Add** button and then click on Browse and search for the **S4A import source** file that you previously saved.

<img src="/exercises/ex1/images/S12.png" width=100% height=100%>

In the tab **Destinations**, choose from the drop-down menu **ABAP_S4A**

3. Navigate  to the third tab  **Properties** tab and fill in the red marked properties: 
<img src="/exercises/ex1/images/S13.png" width=50% height=50%>

For the property *ips.application.id*, you will need to search for the Application ID value of the S/4HANA Cloud Private Edition in IAS. To find this value, duplicate this browser tab and navigate in the SCI console to the 4th tab **Applications & Resources** and choose **Applications**. 
<img src="/exercises/ex1/images/S.png" width=50% height=50%>

Search for the S/4HANA application and copy the value of the Application ID. 
<img src="/exercises/ex1/images/S.png" width=50% height=50%>

4. Now save your system. 

5. Let's add a target system for this newly created source system. Navigate to the **Target Systems** . Click on the **Add** button and then click on Browse and search for the **S4A import target** file that you previously saved.

6. For the source system, choose from the drop-down menu the **S4A import source** system that you created at earlier. This will ensure that the entries coming from the BTP Subaccount will be provisioned to the Local Identity Directory. In the tab **Destinations**, choose from the drop-down menu **ABAP_S4A**. 

7. Navigate to the Properties Tab and add the values for the properties that are marked in red, if any.

8. Save your system. 

9. Let's run the initial load job. Navigate to your **Source Systems**.
10. Choose the source system **S4A import source** and navigate to the tab **Jobs**. 
11. Run the job.
<img src="/exercises/ex1/images/S19.png" width=50% height=50%>

12. Navigate to Provisioning Logs and check the provisioning status and the details. 

13. Let's search for Groups that start with **TECHED_**. You will notice that the Application Name indicates the source system.
<img src="/exercises/ex1/images/S21.png" width=50% height=50%>

## Exercise 1.4  Systems for provisioning to SAP back-end applications 
Up until now we have created the connections between SCI and back-end systems for  authorization import. Any subsequent user creations and authorization assignment will be performed centrally by Microsoft Entra ID in the SCI and afterwards provisioned to the backend. It is a bad practice to perform authorization assignments in the back-end systems because the whole landscape will be out of sync. 

In this exercise we will create the necessary systems between SCI and the back-end systems for subsequent provisioning. For this we will need a source system representing the central storage of the SCI and two target systems representing the back-end systems. We will create the source system manually and the target systems as we did till now, from imported files. 

1. Click on the **Add** button and then choose the type **Local Identity Directory**
<img src="/exercises/ex1/images/S15.png" width=50% height=50%>

Give your system a meaningful name. Our suggestion is *SAP provisioning source*.

2. Navigate to the Properties tab and manually add the following standard properties.

| Property Name | Property Value | 
|--------------|:-----:|
| idds.user.filter|  groups.display sw "TECHED_"  |        
| ips.trace.created.entity|  true  |  
| ips.trace.created.entity.content|  true  |
| ips.trace.failed.entity.content|  true  |
| ips.trace.skipped.entity|  true  |
| ips.trace.skipped.entity.content|  true  |
| ips.trace.updated.entity|  true  |
| ips.trace.updated.entity.content|  true  |  


3. Check that your system looks like this and save your system.

<img src="/exercises/ex1/images/S16.png" width=50% height=50%>


Now let's proceed with the target systems. 

4.  Let's add a target system for this newly created source system. Navigate to the **Target Systems** . Click on the **Add** button and then click on Browse and search for the **BTP CF provisioning target** file that you previously saved.

<img src="/exercises/ex1/images/S17.png" width=50% height=50%>

5. For the source system, choose from the drop-down menu the **SAP provisioning source** system that you created at earlier. This will ensure that the entries coming from the central SCI storage will be provisioned to the BTP subaccount. 

7. Navigate to the Properties Tab and add the values for the properties that are marked in red. The *ips.application.is** is the one that you found at step 3 in Exercise 1.2. 

8. Save your system. 

9. Repeat steps 4 to 8 for the SAP S/4 target system. Click on the **Add** button and then click on Browse and search for the **S4A provisioning target** file that you previously saved.

10. For the source system, choose from the drop-down menu the **SAP provisioning source** system that you created at earlier. This will ensure that the entries coming from the central SCI storage will be provisioned to the S/4 system. Choose the DEstination **ABAP_S4A**.

11. Navigate to the Properties Tab and add the values for the properties that are marked in red. The *ips.application.is** is the one that you found at step 3 in Exercise 1.3.

12. Save your system. 




## Summary

You've now successfully configured your SAP back-end systems for authorization import for SAP SCI and ran the initial load jobs. Also, you have prepared these systems for provisioning of users and assignments, as you will see in exercises 5 and 6. 

Continue to - [Exercise 2 - Exercise 2 Description](../ex2/README.md)

