# Exercise 1 - Sync SAP backend roles in SAP SCI 

In this exercise, we will import the back-en authorizations to IdDS. For this, we will create IPS source and target systems.  

* We will start by creating source systems for importing authorizations in SAP SCI from the SAP S/4 and the BTP Subaccount. 
* These authorization will be sent via IPS to the Entra ID tenant in [exercise 3](../ex2/README.md). Entra ID is the IdM solution responsible for assignments, therefore we need the SAP authorizations in the Entra IDtenant. For this purpose, we will create a target system that corresponds to Entra ID. 
* Last but not least, we will create target systems for user and groups assignments 



1	Create IPS source systems: SAP ABAP with filter for reading specific groups, SAP BTP XSUAA 
2	Create IPS target systems: IdDS 
3	Create IPS target systems for central store-based provisioning: SAP ABAP, SAP S/4 on-prem, SAP BTP XSUAA
4	Create two IPS source system for central store-based provisioning: SAP IdDS
5	Enable the Central Store-Based Provisioning option under Applications & Resources -> Application -> Provisioning.
6	Initial load ABAP -> SAP SCI 
7	Initial load SAPBTP XSUAA -> SAP SCI 
8	Verify that new /Groups are created in SAP SCI, belonging to the S/4 PCE and the SAP BTP XSUAA subaccount 


## Exercise 1.1 Create IPS source systems

After completing these steps you will have created...

1. Click here.
<br>![](/exercises/ex1/images/01_01_0010.png)

2.	Insert this line of code.
```abap
response->set_text( |Hello World! | ). 
```



## Exercise 1.2 Create IPS target systems

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

