

|  **Owner**  |  | 
|  --- |  --- | 
|  **Status**  | In progress | 
|  **Contributors**  |  | 
|  **Approved**  |  | 
|  **Due date**  | Before the end of Sprint 14 | 
|  **Decision**  | Create a messaging queue to store soc settings for offline pace devices | 
|  **On this page**  |  | 




##  Problem statement
The Wetility app allows customers with pace devices to remotely set the ‘depth of discharge’ , which satisfies the following equation:

soc = 100 - dod 

where soc = minimum discharge 



and dod = depth of discharge

of the battery, 

however this action fails if the device itself is offline. Hence there needs to be a way to store the customer request 




##  Research insights
The initial investigation into resolving the issue resulted in several possible tools that could potentially be used 




1. In memory cache 


1. Storage Account Queue


1. Service Bus Queue






1. In memory cache 



This approach has disadvantages 

> If the application itself is restarted or shutdown for any reason, messages stored shall be erased.

>When the application scales up  there could be a duplication of messages.

>When the application scales down messages could be lost





2. Storage Account Queue

This approach is better than an in memory cache because messages will not be lost as a result of the application shutting down or scaling. There are some disadvantages to this approach : 

>The Wetility infrastructure as code is designed in such a way that the the KeyVault for the  Device module runs first then the dal component runs which has both the storage account and the azure function for device. This means that a storage queue using the storage account will not work because the connection string to the queue cannot be stored in then key vault because it is created after the key vault runs.



3. Service Bus Queue

There is a service bus component/module on the Wetility infrastructure as code which is not associated specifically with any module(e.g device, crm, cms etc.) . From this service bus a number of queues can be created and because the service bus component can run before the KeyVault module does then the connection string to the queue can be stored inside azure key vault and used by the device-dal azure function.




##  Solution hypothesis

* Since Azure Service Bus is the chosen solution, the user experience should have the following outputs:


* The user’s request should be processed up to 7 days from the date that the user sent the request.



.




##  Soc Settings Queue


|  |  **Option 1**  | 
|  --- |  --- | 
|  **Overview**  | The Soc Settings messaging queue  will interact with the device DAL component on Azure to accomplish the objective of storing offline messages. | 
|  **Screenshot**  | Type /file to add a screenshot of your design | 
|  **Link**  | [https://learn.microsoft.com/en-us/dotnet/api/azure.messaging.servicebus.servicebusclient?view=azure-dotnet](https://learn.microsoft.com/en-us/dotnet/api/azure.messaging.servicebus.servicebusclient?view=azure-dotnet)[https://learn.microsoft.com/en-us/dotnet/api/azure.messaging.servicebus.servicebussender?view=azure-dotnet](https://learn.microsoft.com/en-us/dotnet/api/azure.messaging.servicebus.servicebussender?view=azure-dotnet)[https://learn.microsoft.com/en-us/dotnet/api/azure.messaging.servicebus.servicebusreceiver?view=azure-dotnet](https://learn.microsoft.com/en-us/dotnet/api/azure.messaging.servicebus.servicebusreceiver?view=azure-dotnet)[https://azure.microsoft.com/en-us/pricing/details/service-bus/](https://azure.microsoft.com/en-us/pricing/details/service-bus/) | 
|  **Benefits and risks**  | Allow battery settings to be set later on for offline or faulty pace devices ServiceBus is very low cost , for the basic tier,  **$0.05**  per million operationsBatched Messaging would have to take into account the number of pace devices that are offlineMessaging depends on the availability of Azure  | 




##  Follow up
Keep track of your design decisions and follow up on open questions.



|  **Decision**  |  **Status**  |  **Next steps**  | 
|  --- |  --- |  --- | 
| Create Messaging Queue to Store battery settings for offline pace devices  | decidedGreen / in reviewYellow / other | 1completeCreate Service Bus on Azure on QA.2completeCreate Service Bus Queue inside created Service Bus on QA.3completeAdd connection strings for created queue to function Device DAL on Azure.4completeUpdate the source code for Device Dal(QA) to store messages inside the queue(QA) for offline devices and to regularly check this queue of stored messages and their corresponding pace devices to see if the devices are online , if so the messages are removed from the queue(QA) and the update is done on the online pace devices.5completeTest functionality locally6completeTest functionality on QA7completeCreate Service Bus on Azure on Production8completeCreate Service Bus Queue inside created Service Bus on Production9completeUpdate the source code for Device Dal(Production) to store messages inside the queue(Production) for offline devices and to regularly check this queue of stored messages and their corresponding pace devices to see if the devices are online , if so the messages are removed from the queue(Production) and the update is done on the online pace devices. | 



1002574254092761031961SOC Messaging Queue Flow11https://palota.atlassian.net/wikiSOC Messaging Queue Flow01184581




##  Source files
[https://github.com/wetility-energy/wetility-func-device-dal](https://github.com/wetility-energy/wetility-func-device-dal)

[https://portal.azure.com/#@wetility.energy/resource/subscriptions/4f83c970-e24f-4137-9403-c4602017b86c/resourceGroups/wt-rg-device-qa/providers/Microsoft.Web/sites/wt-func-device-dal-qa/linkApiManagemen](https://portal.azure.com/#@wetility.energy/resource/subscriptions/4f83c970-e24f-4137-9403-c4602017b86c/resourceGroups/wt-rg-device-qa/providers/Microsoft.Web/sites/wt-func-device-dal-qa/linkApiManagement)





*****

[[category.storage-team]] 
[[category.confluence]] 
