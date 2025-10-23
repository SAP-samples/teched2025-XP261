# Exercise 1 - Sync SAP backend roles in SAP SCI 

In this exercise, we will import the back-en authorizations to IdDS. For this, we will create IPS source and target systems.  

* We will start by creating source systems for importing authorizations in SAP SCI from the SAP S/4 and the BTP Subaccount. 
* These authorization will be sent via IPS to the Entra ID tenant in [exercise 2](../ex2/README.md). Entra ID is the IdM solution responsible for assignments, therefore we need the SAP authorizations in the Entra ID tenant. For this purpose, we will create a target system that corresponds to Entra ID. 
* We will create another source system for assignment and user provisioning to the SAP solutions
* Last but not least, we will create target systems for user and groups assignments 



1	Create IPS source systems: SAP ABAP with filter for reading specific groups, SAP BTP XSUAA 
2	Create IPS target systems: IdDS 
3	Create IPS target systems for central store-based provisioning: SAP ABAP, SAP S/4 on-prem, SAP BTP XSUAA
4	Create two IPS source system for central store-based provisioning: SAP IdDS
5	Enable the Central Store-Based Provisioning option under Applications & Resources -> Application -> Provisioning.
6	Initial load ABAP -> SAP SCI 
7	Initial load SAPBTP XSUAA -> SAP SCI 
8	Verify that new /Groups are created in SAP SCI, belonging to the S/4 PCE and the SAP BTP XSUAA subaccount 


## Exercise 2.1  IPS source systems creation

### Exercise 2.1.1 Create IPS source system for syncing authorizations from back-end

1. Navigate to the SCI administrative console that corresponds to your seat. From the third tab Identity Provisioning please choose **Source Systems**.
<img src="/exercises/ex1/images/S11.png" width=50% height=50%>

2. Save these ([XP261](src="/exercises/ex1/images/XP261.json") & [S4A](src="/exercises/ex1/images/S4A.json") ) JSON files locally because you will need to import them in the next step

3. Click on the **Add** button and then click on Browse and search for the **XP261** file that you previously saved.

<img src="/exercises/ex1/images/S12.png" width=50% height=50%>

4. Navigate  to the third tab  **Properties** tab and fill in the red marked properties: 
<img src="/exercises/ex1/images/S13.png" width=50% height=50%>

5. Now save your system. 

6. Now let's add the SAP S/4 HANA private edition system as well. We will repeat steps 3 and 4 and use the **S4A** file. Navigate to the **Properties** tab and fill in the red marked properties: 
<img src="/exercises/ex1/images/S13.png" width=50% height=50%>

7. Now save your system.  

### Exercise 2.1.2 Create one IPS source system for syncing authorizations to Entra ID
1. 

### Exercise 2.1.2 Create one IPS source system for provisioning to SAP back-end applications


## Exercise 1.2 IPS target systems creation

After completing these steps you will have...

1.	Enter this code.
```abap
DATA(lt_params) = request->get_form_fields(  ).
READ TABLE lt_params REFERENCE INTO DATA(lr_params) WITH KEY name = 'cmd'.
  IF sy-subrc <> 0.
    response->set_status( i_code = 400
                     i_reason = 'Bad request').
    RETURN.
  ENDIF.

```

2.	Click here.
<br>![](/exercises/ex1/images/01_02_0010.png)

## Exercise 1.3 Trigger authorization synchronization  

## Summary

You've now successfully configured SAP S/4 HANA system and your BTP subaccount as sources for authorizations for SAP SCI. Also, you have prepared these systems for provisioning of users and assignments, as you will see in exercises 5 and 5. 

Continue to - [Exercise 2 - Exercise 2 Description](../ex2/README.md)

