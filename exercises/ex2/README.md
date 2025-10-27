# Exercise 2 - Provision SAP back-end roles to Microsoft Entra ID

In the previous exercise we have all the necessary authorizations from our backend systems. Now we have to synchronize them to the identity management solution. In this scenario the identity management solution is your Entra ID tenant.

## Exercise 2.1  Systems for Microsoft Entra ID import  

### Exercise 2.1.1 Create one IPS source system for syncing authorizations to Entra ID

With the previously created systems we are importing in the Identity Directory all the authorizations from the SAP back-end applications. Because we want to sync these authorization to Entra ID, we will add a new source system that will be later chosen as a source for an Entra ID target.

1. Navigate to the SCI administrative console and from the third tab Identity Provisioning please choose **Source Systems**. Click on the **Add** button and then click on Browse and search for the **Non-SAP import source** file. 

2. Navigate  to the third tab  **Properties** tab.  Note that for this system type you do not need to specify connection details. This is because the local store inside this tenant is used. 

5. Set the value on *true* for all properties. Now save your system. 


### Exercise 2.1.2 Create one IPS target system for provisioning to Entra ID. 
1. Navigate to your target systems. Click on the **Add** button and then click on Browse and search for the **Non-SAP import target** file that you previously saved.
2. For the source system, choose from the drop-down menu the **Non-SAP import source** system that you created at earlier. This will ensure that the entries coming from the Identity Directory will be provisioned to this system.
3. Navigate to the Properties Tab and add the values for the properties that are marked in red. 

The values for the properties *ips.application.id.s4* and *ips.application.id.xsuaa* are the ones that you wrote in the previous steps. You can find these values as follows:
* for *ips.application.id.xsuuaa* navigate to your **BTP CF import source**  source system and search for the ips.application.id property, and copy the value. 
* for *ips.application.id.s4* navigate to your **S4A import source**  source system and search for the ips.application.id property, and copy the value. 
4. Save your system. 




## Exercise 2.2 Trigger groups import to Entra ID


1. Navigate to your **Non-SAP import source**.
2. Choose the source system **Local Directory** and navigate to the tab **Jobs**. 
3. Run the job.
4. Navigate to Provisioning Logs and check the provisioning status and the details. You will notice that you have only created groups in your **BestRunCorp Tenant** tenant


## Summary

You've now provisioned the SAP groups to your identity management solution. Continue with the next exercise to assign these authorizations to users. 

Continue to - [Exercise 3 - Excercise 3 ](../ex3/README.md)
