# Exercise 1 - Sync SAP backend roles in SAP SCI 

In this exercise, we will import the back-end authorizations to IdDS. For this, we will create IPS source and target systems.  

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

2. Save the following JSON files locally because you will need to import them in the next steps:  
* [BestRun Corp IDDS XSUAA](./images/BestRunCorpIDDSXSUAA.json) 
* [BestRun Corp Tenant IDDS](./images/BestRunCorpTenantIDDS.json) 
* [BestRunCorp Tenant](./images/BestRunCorpTenant.json)
* [IdDS to BTPSubaccount XP261](./images/IdDStoBTPSubaccountXP261.json)
* [S4 on Prem](./images/S4onPrem.json) 

### Exercise 1.2.1 Create one IPS target system for provisioning to Entra ID. 
1. Click on the **Add** button and then click on Browse and search for the **BestRunCorp Tenant** file that you previously saved.
2. For the source system, choose from the drop-down menu the **Local Directory** system that you created at earlier. This will ensure that the entries coming from the Identity Directory will be provisioned to this system.
3. Navigate to the Properties Tab and add the values for the properties that are marked in red, if any.
4. Save your system. 

### Exercise 1.2.2 Create two IPS source systems for provisioning to the Local Identity Directory 
1. Click on the **Add** button and then click on Browse and search for the **BBestRun Corp IDDS XSUAAt** file that you previously saved.
2. For the source system, choose from the drop-down menu the **BTP Subaccount XP261** system that you created at earlier. This will ensure that the entries coming from the BTP Subaccount will be provisioned to the Local Identity Directory.
3. Navigate to the Properties Tab and add the values for the properties that are marked in red, if any.
4. Save your system. 
5. Click on the **Add** button and then click on Browse and search for the **BBestRun Corp IDDS** file that you previously saved.
6. For the source system, choose from the drop-down menu the **S4A** system that you created at earlier. This will ensure that the entries coming from S/4 will be provisioned to the Local Identity Directory.
7. Navigate to the Properties Tab and add the values for the properties that are marked in red, if any.
8. Save your system. 

### Exercise 1.2.3 Create two IPS source system for provisioning to the SAP back-end applications
1. Repeat the same procedure from the earlier step for the **IdDS to BTP Subaccount XP261** and the **S4 on Prem** systems. 
2. For both systems the source is **Local Identity SAP Provisioning**
3. After you have added the necessary properties, save your systems. 

 
 ## Exercise 1.3 Initial Load in SAP Cloud Identity Services

Now that we have all the systems in place, let's run the jobs and get the back-end authorizations in the central storage of the SAP Cloud Identity services. 
1. Navigate to your **Source Systems**.
2. Choose the source system **BTP Subaccount XP261** and navigate to the tab **Jobs**. 
3. Run the job.
<img src="/exercises/ex1/images/S19.png" width=50% height=50%>
4. Navigate to Provisioning Logs and check the provisioning status and the details. 
5. Repeat the same steps for the source system **S4A** 
6. Now let's check the imported groups. From the SCI administrative console, tab **Users & Authorizations** choose **Groups**.
<img src="/exercises/ex1/images/S20.png" width=50% height=50%>
7. Let's search for Groups that start with **TECHED_**. You will notice that the Application Name indicates the source system.
<img src="/exercises/ex1/images/S21.png" width=50% height=50%>

## Summary

You've now successfully configured SAP S/4 HANA system and your BTP subaccount as sources for authorizations for SAP SCI. Also, you have prepared these systems for provisioning of users and assignments, as you will see in exercises 5 and 6. 

Continue to - [Exercise 2 - Exercise 2 Description](../ex2/README.md)

