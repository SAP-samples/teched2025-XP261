# Getting started
*Estimated Time: **25 min***

We chose this scenario because it follows the best practices for integrating an identity management solution into an SAP landscape. Throughout these exercises you will learn how to setup the identity access management flows between a Microsoft Entra tenant and your SAP landscape. As per our [reference architecture](https://architecture.learning.sap.com/docs/ref-arch/20c6b29b1e), the SAP Cloud Identity Services tenant are positioned in front of your SAP landscape and serve as the designated Identity and Access Management interface for SAP SaaS integrations. 

SAP Cloud Identity Services (SCI) are a group of services of SAP Business Technology Platform (SAP BTP), which enable you to integrate identity and access management between systems. The goal is to provide a seamless single sign-on experience across systems while ensuring that system and data access are secure. SAP Cloud Identity Services include Identity Authentication (IAS), Identity Provisioning (IPS), Identity Directory (IdDS), and Authorization Management (AMS).

## Table of Contents
- [Accessing the landscape](#accessing-the-landscape)
- [Summary](#summary)

## Accessing the landscape
Please follow the steps described in this section to prepare your user account for accessing the systems in this hands-on session. Refer to the attached [XP261 keys.xslx](./images/XP261keys.xlsx) for additional credentials. Press on **Download Raw File** in the window that will open. 

<img src="/exercises/ex1/images/S11.png">

You will get access to the following systems:  
* [Microsoft Entra](#accessing-microsoft-entra) 
* [SAP Cloud Identity Services](#accessing-your-sap-cloud-identity-services-tenant) 
* [SAP SuccessFactors](#accessing-sap-successfactors-tenant) 
* [SAP S/4HANA Private Edition](#accessing-sap-s4hana-cloud-private-edition)  
* [BTP subaccount](#accessing-your-btp-subaccount). 


### Accessing Microsoft Entra

Setup Multifactor Authentication (MFA) for your Entra admin user. This is required to access the Entra admin center.

| Step   | Description                | Screenshot |
| :----- | :------------------------- | :--------- |
| 1    | Open a new browser windows and go to the [Entra admin center](https://entra.microsoft.com/) to setup MFA for your Entra administrator user.<br><br>Enter **admin`<NNN>`@bestruncorp.onmicrosoft.com** for the user name. Replace `<NNN>` with the number of your seat, for example **admin045@bestruncorp.onmicrosoft.com**.<br><br>Click **Next**.|<a href="./images/0-1.jpg" target="_blank"><img src="./images/0-1.jpg" width="250"/></a>|
| 2    | Enter your Entra admin initial login password.<br><br>Replace `<NNN>` at the end of the password with the number of your seat.<br><br>Click **Sign in**.|<a href="./images/0-2.jpg" target="_blank"><img src="./images/0-2.jpg" width="250"/></a>|
| 3    | Click **Next**. |<a href="./images/0-3.jpg" target="_blank"><img src="./images/0-3.jpg" width="250"/></a>|
| 4    | Click **Next**. |<a href="./images/0-4.jpg" target="_blank"><img src="./images/0-4.jpg" width="250"/></a>|
| 5    | Click **Next**. |<a href="./images/0-5.jpg" target="_blank"><img src="./images/0-5.jpg" width="250"/></a>|
| 6    | On your mobile phone, launch the *Authenticator* app.<br><br>Press the **+** button.|<a href="./images/0-6.jpg" target="_blank"><img src="./images/0-6.jpg" width="250"/></a>|
| 7    | Select **Work or school account** and press **Scan QR code**.|<a href="./images/0-7.jpg" target="_blank"><img src="./images/0-7.jpg" width="250"/></a>|
| 8    | Scan the QR Code with your mobile device.|<a href="./images/0-8.jpg" target="_blank"><img src="./images/0-8.jpg" width="250"/></a>|
| 9    | Click **Next**. |<a href="./images/0-9.jpg" target="_blank"><img src="./images/0-9.jpg" width="250"/></a>|
| 10    | A randon number is generated. |<a href="./images/0-10.jpg" target="_blank"><img src="./images/0-10.jpg" width="250"/></a>|
| 11    | Enter the number in the Authenticator app on the mobile device.<br><br>Confirm with **Yes**.|<a href="./images/0-11.jpg" target="_blank"><img src="./images/0-11.jpg" width="250"/></a>|
| 12   | Click **Next**. |<a href="./images/0-12.jpg" target="_blank"><img src="./images/0-12.jpg" width="250"/></a>|
| 13   | Your user account is now setup for MFA.<br><br>Click **Done**|<a href="./images/0-13.jpg" target="_blank"><img src="./images/0-13.jpg" width="250"/></a>|
| 14   | Continue to login to the Entra admin center.<br><br>Click **Yes**.|<a href="./images/0-13.jpg" target="_blank"><img src="./images/0-14.jpg" width="250"/></a>|
| 15   | A new random number is generated.|<a href="./images/0-14-1.jpg" target="_blank"><img src="./images/0-14-1.jpg" width="250"/></a>|
| 16   | Enter it on your Authenticator app.<br><br>Confirm with **Yes**.|<a href="./images/0-15.jpg" target="_blank"><img src="./images/0-15.jpg" width="250"/></a>|
| 17   | Click **Next**.|<a href="./images/0-16.jpg" target="_blank"><img src="./images/0-16.jpg" width="250"/></a>|
| 18   | Click **Done**.|<a href="./images/0-17.jpg" target="_blank"><img src="./images/0-17.jpg" width="250"/></a>|
| 19   | You've successfully logged in the Entra admin center.|<a href="./images/0-18.jpg" target="_blank"><img src="./images/0-18.jpg" width="250"/></a>|

### Accessing your SAP Cloud Identity Services tenant 

1. Search for the internet browser on your computer and navigate to your SCI administrative console. The SAP Cloud Identity Service tenant URL and username are specific for your seat in the workshop room.<br>
URL pattern: https://bestruncorp-NN.accounts.ondemand.com/admin/<br>
Replace `<NN>` with your seat number, for example `05` or `31`.

2. Type the username and password and press **Continue**

   <img src="./images/S0-1.png">

3. You have access to the SAP Cloud Identity Services administrative console.
   
   <img src="./images/S0-2.png" >
   
### Accessing SAP SuccessFactors tenant
1. Search for the internet browser on your computer and navigate to your SAP SuccessFactors (SAP SFSF) tenant.
Unlike the previous exercise, you will use a shared SAP SFSF tenant 

URL: https://hcm-eu10-sales.hr.cloud.sap/login?company=SFLAP062575

 <img src="./images/S0-3.png" >

2. Type the username and password and press **Log in**

 <img src="./images/S0-4.png" >

### Accessing SAP S/4HANA Cloud Private Edition

1. Search for the SAP Logon icon <img src="./images/S17.png" width=10% height=10%> on your desktop. 

2. Search for the connection to system **S4A**. If you don't find it, create a new connection for it

<img src="./images/S0-61.png" >

Click **Next** and manually add the following values: 

<img src="./images/S17-1.png" >

Add the following details:

* Description: TechEd 2025
* System ID: S4A   
* Instance: 00      
* SAProuter String: leave empty      
* Application Server: s4xp261.tdc.sap.com      
* Client: 101

<img src="./images/S0-7.png" >

Click **OK**. 

4. Leave the next configurations as they are: 

<img src="./images/S0-8.png" >

Click **OK**. 

5. Now that you have created the new connection let's log in! 
<img src="./images/S0-9.png" >

Client: 101
User:  **XP261-`<NNN>`**. Replace `<NNN>` with your seat number, for example **XP261-`045`**.

6. Let's check the authorization available on this system. Execute the PFCG transaction

<img src="./images/S0-10.png" >

And search for the **PROCUREMENT_ADMIN** role

<img src="./images/S0-11.png" >

In exercise 5, this role will be assigned in Micrososft Entra to a newly created employee.

### Accessing your BTP subaccount

1. On your internet browser navigate to the global account tenant: https://emea.cockpit.btp.cloud.sap/cockpit/?idp=teched2025-00.accounts.ondemand.com#/globalaccount/4c772782-0751-42ee-93c3-897452fdcb63/ 

2. Login with the user xp261-`<NNN>`@education.cloud.sap from your subaccount's platform identity provider (https://teched2025-00.accounts.ondemand.com).<br>
Replace `<NNN>` with your seat number, for example xp261-`016`@education.cloud.sap for seat 16.<br>
You will find a subbacout that coresonds to your seat number:

 <img src="./images/S0-5.png" >

 3. Press on the subaccount and search under **Role Collections** for the **FINANCE_ADMIN** role collection. 
 
 <img src="./images/S0-122.png" >

 In exercise 5, this role collection will be assigned in Micrososft Entra to a newly created employee. 

## Summary

Congratulations for completing the initial setup steps. Now get started with [Exercise 1 - Import SAP back-end roles in SAP Cloud Identity Services](../ex1/README.md), or go back to the [overview](../README.md).


