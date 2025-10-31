# Exercise 1 - Import SAP back-end roles in SAP Cloud Identity Services 

*Estimated Time: **35 min***

In this exercise, you will import the back-en authorizations to IdDS. For this, you will create IPS source and target systems.  
<img src="/exercises/ex1/images/Intro1.png">

* you will start by creating source systems for importing authorizations in SAP SCI from the SAP S/4 and the BTP subaccount. 
* These authorization will be sent via IPS to the Entra ID tenant in [exercise 2](../ex2/README.md). Entra ID is the IdM solution responsible for centrally managing the assignments, therefore you need the SAP authorizations in the Entra ID tenant. For this purpose, you will create a target system that corresponds to Entra ID. 
* you will create systems for assignment and user provisioning to the SAP solutions



## Table of Contents
- [1.1 Download the JSON files](#11--download-the-json-files)
- [1.2 SAP BTP onboarding ](#12--sap-btp-onboarding)
- [1.3  SAP S/4HANA Cloud Private Edition onboarding ](#13--sap-s4hana-cloud-private-edition-onboarding)
- [1.4  Systems for provisioning to SAP back-end applications](#14--systems-for-provisioning-to-sap-back-end-applications)
- [Summary](#summary)

## 1.1  Download the JSON files 

Save all these  JSON files locally because you will need to import them in the next step. Open the following JSON files in a separate window. 

Open each following JSON files in a separate window. Press on **Download Raw File** in the window that will open. 

<img src="/exercises/ex1/images/S11.png">


1. [BTP CF import source](./images/BTPCFimportsource.json ':ignore :target=_self')
2. [Non-SAP import source](./images/NON-SAPimportsource.json)  
3. [SAP provisioning source](./images/SAPprovisioningsource.json)
4. [S4A import source](./images/S4Aimportsource.json)
5. [BTP CF import target](./images/BTPCFimporttarget.json)
6. [S4A import target](./images/S4Aimporttarget.json)
7. [Non-SAP import target](./images/Non-SAPimporttarget.json)
8. [BTP CF provisioning target](./images/BTPCFprovisioningtarget.json)
9. [S4A provisioning target](./images/S4Aprovisioningtarget.json)



## 1.2  SAP BTP onboarding 

1. Navigate to the SCI administrative console that corresponds to your seat. From the third tab **Identity Provisioning** please choose **Source Systems**.

<img src="/exercises/ex1/images/S121.png">

2. Click on the **Add** button and then click on Browse and search for the **BTP CF import source** file that you previously saved.

<img src="/exercises/ex1/images/S1222.png">

3. Navigate  to the third tab  **Properties** tab  

<img src="/exercises/ex1/images/S123.png">

Notice the red marked properties. The system cannot be saved as long as these properties do not have values. 

<img src="/exercises/ex1/images/S124.png">

For the property *ips.application.id*, you will need to search for the Application ID value of the BTP subaccount in IAS. To find this value, duplicate this browser tab and navigate in the SCI console to the 4th tab **Applications & Resources** and choose **Applications**. 

Search for the application that corresponds to you seat number: XP261_0NN and copy the value of the Application ID. 

<img src="/exercises/ex1/images/S125.png">

For the other properties, please check the **XP261 keys.xslx** file that you saved previously. 

4. Now save your system. 

<img src="/exercises/ex1/images/S126.png">

5. Let's add a target system for this newly created source system. Navigate to the **Target Systems**.

<img src="/exercises/ex1/images/S127.png">

 Click on the **Add** button and then click on Browse and search for the **BTP CF import target** file that you previously saved.

6. For the source system, choose from the drop-down menu the **BTP CF import source** system that you created at earlier. 
This will ensure that the entries coming from the BTP Subaccount will be provisioned to the Local Identity Directory.

<img src="/exercises/ex1/images/S128.png">

7. Navigate to the Properties Tab and add the values for the properties that are marked in red, if any.
8. Save your system. 

9. Let's run the initial load job. Navigate to your **Source Systems**.
10. Choose the source system **BTP CF import source** and navigate to the tab **Jobs**. 
11. Press on **Run Now** for the job type **Read Job**. 

<img src="/exercises/ex1/images/S129.png">

12. Navigate to Provisioning Logs and check the provisioning status and the details. 

<img src="/exercises/ex1/images/S130.png">

Click on the result and inspect the details. Afterwards navigate from the console to the tab **Users & Authorizations**  and choose **Groups**


## 1.3  SAP S/4HANA Cloud Private Edition onboarding 

1. In your SCI administrative console tab Identity Provisioning, please choose **Source Systems**.

2. Click on the **Add** button and then click on Browse and search for the **S4A import source** file that you previously saved.
In the tab **Destinations**, choose from the drop-down menu **ABAP_S4A**

<img src="/exercises/ex1/images/S13-1.png">

3. Navigate  to the third tab  **Properties** tab and fill in the red marked properties: 

<img src="/exercises/ex1/images/S13-22.png" >

For the property *ips.application.id*, similarly with exercise 1.2 step 3, you will need to search for the Application ID value of the S/4HANA Cloud Private Edition in IAS. To find this value, duplicate this browser tab and navigate in the SCI console to the 4th tab **Applications & Resources** and choose **Applications**. Search for the S/4HANA application and copy the value of the Application ID. 

The value for the property abap.role.name.filter is *PROCUREMENT_ADMIN_NNN*. Replace `<NNN>` with your seat number, for example **PROCUREMENT_ADMIN_010**.

4. Now save your system. 

5. Let's add a target system for this newly created source system. Navigate to the **Target Systems** . Click on the **Add** button and then click on Browse and search for the **S4A import target** file that you previously saved.

6. For the source system, choose from the drop-down menu the **S4A import source** system that you created at earlier. This will ensure that the entries coming from the BTP Subaccount will be provisioned to the Local Identity Directory. 

<img src="/exercises/ex1/images/S13-3.png" >

7. Save your system. 

8. Let's run the initial load job. Navigate to your **Source Systems**.

9. Choose the source system **S4A import source** and navigate to the tab **Jobs**.  Press on **Run Now** for the job type **Read Job**. 
<img src="/exercises/ex1/images/S13-5.png" >
 Navigate to Provisioning Logs and check the provisioning status and the details. 

10. Let's check again the **Groups** section. You will notice that the Application Name indicates the source system.

<img src="/exercises/ex1/images/S13-121.png">

## 1.4  Systems for provisioning to SAP back-end applications 
Up until now you have created the connections between SCI and back-end systems for authorization import. Any subsequent user creation and authorization assignment will be performed centrally by Microsoft Entra ID in the SCI and afterwards provisioned to the back-end. It is a bad practice to perform authorization assignments in the back-end systems because the whole landscape will be out of sync. 

In this exercise you will create the necessary connections between SCI and the back-end systems for subsequent provisioning. For this you will need a source system representing the central storage of the SCI and two target systems representing the back-end systems. you will create the source system manually and the target systems, from imported files as you did till now.

1. In your SCI administrative console tab Identity Provisioning, please choose **Source Systems**. Click on the **Add** button and then choose the type **Local Identity Directory**
Give your system a meaningful name. Our suggestion is *SAP provisioning source*.

<img src="/exercises/ex1/images/S14-0.png" >

2. Navigate to the Properties tab and manually add the following standard properties.

<img src="/exercises/ex1/images/S14-1.png" >

For this exercise only the first property is mandatory. In a real scenario an administrator would most likely add the ips.trace* properties as well, because they are used to enhance the logging when troubleshooting. 


| Property Name | Property Value | 
|--------------|:-----:|
| idds.user.filter|  groups.display sw "TECHED_"  |        
| (optional) ips.trace.created.entity|  true  |  
| (optional) ips.trace.created.entity.content|  true  |
| (optional) ips.trace.failed.entity.content|  true  |
| (optional) ips.trace.skipped.entity|  true|
| (optional) ips.trace.skipped.entity.content|  true  |
| (optional) ips.trace.updated.entity|  true|
| (optional) ips.trace.updated.entity.content|  true  |  


3. Save your system.

<img src="/exercises/ex1/images/S14-2.png" >


Now let's proceed with the target systems. 

4.  Let's add a target system for this newly created source system. Navigate to  **Target Systems**. Click on the **Add** button and then click on Browse and search for the **BTP CF provisioning target** file that you previously saved.


5. For the source system, choose from the drop-down menu the **SAP provisioning source** system that you created at earlier. This will ensure that the entries coming from the central SCI storage will be provisioned to the BTP subaccount. 

<img src="/exercises/ex1/images/S14-3.png" >

7. Navigate to the Properties Tab and add the values for the properties that are marked in red. The *ips.application.id* is the one that you found at step 3 in Exercise 1.2. The values of the other properties are in the XP261 keys.xslx file that you saved previously.

<img src="/exercises/ex1/images/S14-4.png" >

8. Save your system. 

9. Repeat steps 4 to 8 for the SAP S/4 target system. Click on the **Add** button and then click on Browse and search for the **S4A provisioning target** file that you previously saved.


10. For the source system, choose from the drop-down menu the **SAP provisioning source** system that you created at earlier. This will ensure that the entries coming from the central SCI storage will be provisioned to the S/4 system. Choose the Destination **ABAP_S4A**.

<img src="/exercises/ex1/images/S14-5.png" >


11. Navigate to the Properties Tab and add the values for the properties that are marked in red. The *ips.application.is** is the one that you found at step 3 in Exercise 1.3.

<img src="/exercises/ex1/images/S14-6.png" >

12. Save your system. 




## Summary

You've now successfully configured your SAP back-end systems for authorization import for SAP SCI and ran the initial load jobs. Also, you have prepared these systems for provisioning of users and assignments, as you will see in exercises 5 and 6. 

Continue to - [Exercise 2 - Provision SAP back-end roles to Microsoft Entra ID](../ex2/README.md), or go back to the [overview](../README.md).



[def]: #exercise-11-ips-source-systems-creation