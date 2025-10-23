# Exercise 1 - Sync SAP backend roles in SAP SCI 

In this exercise, we will import the back-en authorizations to IdDS. For this, we will create IPS source and target systems.  

* We will start by creating source systems for importing authorizations in SAP SCI from the SAP S/4 and the BTP Subaccount. 
* These authorization will be sent via IPS to the Entra ID tenant in [exercise 2](../ex2/README.md). Entra ID is the IdM solution responsible for assignments, therefore we need the SAP authorizations in the Entra ID tenant. For this purpose, we will create a target system that corresponds to Entra ID. 
* We will create another source system for assignment and user provisioning to the SAP solutions
* Last but not least, we will create target systems for user and groups assignments 

## Exercise 1.1  IPS source systems creation

### Exercise 1.1.1 Create IPS source system for syncing authorizations from back-end

1. Navigate to the SCI administrative console that corresponds to your seat. From the third tab Identity Provisioning please choose **Source Systems**.
<img src="/exercises/ex1/images/S11.png" width=50% height=50%>

2. Save these ([XP261](./images/XP261.json), [S4A](./images/S4A.json) & [Local Directory](./images/LocalDirectory.json)) JSON files locally because you will need to import them in the next step. Press on **Download Raw File** in the window that will open. 

<img src="/exercises/ex1/images/S14.png" width=50% height=50%>

3. Click on the **Add** button and then click on Browse and search for the **XP261** file that you previously saved.

<img src="/exercises/ex1/images/S12.png" width=100% height=100%>


4. Navigate  to the third tab  **Properties** tab and fill in the red marked properties: 
<img src="/exercises/ex1/images/S13.png" width=50% height=50%>

5. Now save your system. 

6. Now let's add the SAP S/4 HANA private edition system as well. We will repeat steps 3 and 4 and use the **S4A** file. Navigate to the **Properties** tab and fill in the red marked properties: 
<img src="/exercises/ex1/images/S13.png" width=50% height=50%>

7. Now save your system.  

### Exercise 1.1.2 Create one IPS source system for syncing authorizations to Entra ID

With the previously created two systems we are importing in the Identity Directory all the authorizations from the SAP back-end applications. Because we want to sync these authorization to Entra ID, we will add a new source system that will be later chosen as a source for an Entra ID target.

1. We will repeat steps 3 and 4 from the previous section and use the **Local Directory** file. 

2. Navigate  to the third tab  **Properties** tab.  Note that for this system type you do not need to specify connection details. This is because the local store inside this tenant is used. 

5. Now save your system. 


### Exercise 1.1.3 Create one IPS source system for provisioning to SAP back-end applications
We will create this system manually. 

1. Click on the **Add** button and then choose the type **Local Identity Directory**
<img src="/exercises/ex1/images/S15.png" width=50% height=50%>

Give your system a meaningful name. Our suggestion is *Local Directory SAP Provisioning*.

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


3. Check that your system looks like this: 

<img src="/exercises/ex1/images/S16.png" width=50% height=50%>


## Exercise 1.2 IPS target systems creation

Now let's proceed with the target systems. 

1.  From the SCI administrative console, tab Identity Provisioning we now choose **Target Systems**.
<img src="/exercises/ex1/images/S17.png" width=50% height=50%>

2. Save these ([XP261](./images/XP261.json), [S4A](./images/S4A.json) & [Local Directory](./images/LocalDirectory.json)) JSON files locally because you will need to import them in the next step. 

### Exercise 1.2.1 Create one IPS source system for provisioning to SAP back-end applications

### Exercise 1.2.2 Create one IPS source system for provisioning to SAP back-end applications
### Exercise 1.2.3 Create one IPS source system for provisioning to SAP back-end applications
### Exercise 1.2.3 Create one IPS source system for provisioning to SAP back-end applications


## Summary

You've now successfully configured SAP S/4 HANA system and your BTP subaccount as sources for authorizations for SAP SCI. Also, you have prepared these systems for provisioning of users and assignments, as you will see in exercises 5 and 5. 

Continue to - [Exercise 2 - Exercise 2 Description](../ex2/README.md)

