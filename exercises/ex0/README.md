# Getting started
Please follow the steps described in this section to prepare your user account for accessing the systems in this hands-on session.

You will get access to the following systems: 
* Microsoft EntraID 
* SAP Cloud Identity Services
* SAP SuccessFactors
* SAP S/4 HANA Private Edition 
* BTP subaccount 

**Duration: 5 minutes.**

## Accessing  EntraID 

### Setup Multifactor Authentication (MFA)

| Step   | Description                | Screenshot |
| :----- | :------------------------- | :--------- |
| 0.1    | Open a new browser windows and go to the [My Account Web Portal](https://myaccount.microsoft.com/) to setup MFA for your Entra administrator user.<br><br>Enter *admin\<N\>@bestruncorp.onmicrosoft.com* for the user name. Replace *\<N\>* with the number of your seat, for example admin4@bestruncorp.onmicrosoft.com.<br><br>Click **Next**.|<a href="./images/0-1.jpg" target="_blank"><img src="./images/0-1.jpg" width="250"/></a>|
| 0.2    | Enter the password.<br><br>Click **Sign in**.|<a href="./images/0-2.jpg" target="_blank"><img src="./images/0-2.jpg" width="250"/></a>|
| 0.3    | Click **Next**. |<a href="./images/0-3.jpg" target="_blank"><img src="./images/0-3.jpg" width="250"/></a>|
| 0.4    | Click **Next**. |<a href="./images/0-4.jpg" target="_blank"><img src="./images/0-4.jpg" width="250"/></a>|
| 0.5    | Click **Next**. |<a href="./images/0-5.jpg" target="_blank"><img src="./images/0-5.jpg" width="250"/></a>|
| 0.6    | On your mobile phone, launch the *Authenticator* app.<br><br>Press the **+** button.|<a href="./images/0-6.jpg" target="_blank"><img src="./images/0-6.jpg" width="250"/></a>|
| 0.7    | Select **Work or school account** and press **Scan QR code**.|<a href="./images/0-7.jpg" target="_blank"><img src="./images/0-7.jpg" width="250"/></a>|
| 0.8    | Scan the QR Code with your mobile device.|<a href="./images/0-8.jpg" target="_blank"><img src="./images/0-8.jpg" width="250"/></a>|
| 0.9    | Click **Next**. |<a href="./images/0-9.jpg" target="_blank"><img src="./images/0-9.jpg" width="250"/></a>|
| 0.10    | A randon number is generated. |<a href="./images/0-10.jpg" target="_blank"><img src="./images/0-10.jpg" width="250"/></a>|
| 0.11    | Enter the number in the Authenticator app on the mobile device.|<a href="./images/0-11.jpg" target="_blank"><img src="./images/0-11.jpg" width="250"/></a>|
| 0.12   | Click **Next**. |<a href="./images/0-12.jpg" target="_blank"><img src="./images/0-12.jpg" width="250"/></a>|
| 0.13   | Your user account is now setup for MFA.|<a href="./images/0-13.jpg" target="_blank"><img src="./images/0-13.jpg" width="250"/></a>|
| 0.14   | Close the browser tab.|<a href="./images/0-13.jpg" target="_blank"><img src="./images/0-13.jpg" width="250"/></a>|

Congratulations for completing the initial setup steps. Now get started with exercise [exercise 1](../ex1/README.md), or go back to the [overview](../README.md).

## Accessing SAP Cloud Identity Services 

Now that we know what the SAP Cloud Services are and we understood what the scope of this hands-on session is, let us check the system access. For this session you will need access to a SAP Cloud Identity Service (SCI) tenant and a SAP SuccessFactors instance. 

1. Search for the internet browser on your computer and navigate to your SCI administrative console.

The SAP Cloud Identity Service tenant URL is specific for your seat in the workshop room.  

Seat number in workshop: XY 
URL: https://teched2025-XY.accounts.ondemand.com/admin/ 

| Seat         | SCI tenant | 
|--------------|:-----:|
| 01|  https://teched2025-01.accounts.ondemand.com/admin/   |        
| 02|  https://teched2025-02.accounts.ondemand.com/admin/   |       
| 03|  https://teched2025-03.accounts.ondemand.com/admin/   |        
| 04|  https://teched2025-04.accounts.ondemand.com/admin/   |        
| 05|  https://teched2025-05.accounts.ondemand.com/admin/   |        
| 06|  https://teched2025-06.accounts.ondemand.com/admin/   |        
| 07|  https://teched2025-07.accounts.ondemand.com/admin/   |        
| 08|  https://teched2025-08.accounts.ondemand.com/admin/   |        
| 09|  https://teched2025-09.accounts.ondemand.com/admin/   |        
| 10|  https://teched2025-10.accounts.ondemand.com/admin/   |        
| 11|  https://teched2025-11.accounts.ondemand.com/admin/   |        
| 12|  https://teched2025-12.accounts.ondemand.com/admin/   |        
| 13|  https://teched2025-13.accounts.ondemand.com/admin/   |        
| 14|  https://teched2025-14.accounts.ondemand.com/admin/   |        
| 15|  https://teched2025-15.accounts.ondemand.com/admin/   |        
| 16|  https://teched2025-16.accounts.ondemand.com/admin/   |        
| 17|  https://teched2025-17.accounts.ondemand.com/admin/   |        
| 18|  https://teched2025-18.accounts.ondemand.com/admin/   |        
| 19|  https://teched2025-19.accounts.ondemand.com/admin/   |        
| 20|  https://teched2025-20.accounts.ondemand.com/admin/   |        
| 21|  https://teched2025-21.accounts.ondemand.com/admin/   |        
| 22|  https://teched2025-22.accounts.ondemand.com/admin/   |       
| 23|  https://teched2025-23.accounts.ondemand.com/admin/   |        
| 24|  https://teched2025-24.accounts.ondemand.com/admin/   |        
| 25|  https://teched2025-25.accounts.ondemand.com/admin/   |        
| 26|  https://teched2025-26.accounts.ondemand.com/admin/   |       
| 27|  https://teched2025-27.accounts.ondemand.com/admin/   |        
| 28|  https://teched2025-28.accounts.ondemand.com/admin/   |       
| 29|  https://teched2025-29.accounts.ondemand.com/admin/   |      
| 30|  https://teched2025-30.accounts.ondemand.com/admin/   |       
| 31|  https://teched2025-31.accounts.ondemand.com/admin/   |        
| 32|  https://teched2025-32.accounts.ondemand.com/admin/   |        
| 33|  https://teched2025-33.accounts.ondemand.com/admin/   |       
| 34|  https://teched2025-34.accounts.ondemand.com/admin/   |       
| 35|  https://teched2025-35.accounts.ondemand.com/admin/   |      
| 36|  https://teched2025-36.accounts.ondemand.com/admin/   |   
| 37|  https://teched2025-37.accounts.ondemand.com/admin/   |        
| 38|  https://teched2025-38.accounts.ondemand.com/admin/   |        
| 39|  https://teched2025-39.accounts.ondemand.com/admin/   |      
| 40|  https://teched2025-40.accounts.ondemand.com/admin/   |      


2. Type the username and password and press **Log On**

   <img src="/exercises/ex0/images/S11.png" width=50% height=50%>

3. You have access to the SAP Cloud Identity Services administrative console.
   
   <img src="/exercises/ex0/images/S12.png" width=50% height=50%>
   
## Accessing SAP SuccessFactors  

## Accessing SAP S/4 HANA Private Edition 
## Accessing BTP subaccount


## Summary

Now that you have logged in your systems, continue to - [Exercise 1 - Exercise 1 Description](../ex1/README.md)
