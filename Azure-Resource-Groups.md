Azure Resource Groups to be provisioned and maintained. Infrastructure as Code (IaC) will be used to provision most of the groups and resources.





|  **Component**  |  **Resource Group**  |  **Environment**  |  **Description**  |  **Notes**  |  **IaC**  | 
|  --- |  --- |  --- |  --- |  --- |  --- | 
| Management | [[rm-rg-management-shared|RG--Management]] | shared | Infrastructure as Code management |  |  | 
| Communication | wt-rg-communication-shared  | shared |  |  |  | 
| Common | wt-rg-common-qa | QABlue | Reusable resources |  |  | 
| Common | wt-rg-common-prod | ProdRed |  |  |  | 
| User | wt-rg-user-qa | QABlue |  |  |  | 
| User | wt-rg-user-prod | ProdRed |  |  |  | 
| Financial Risk | wt-rg-financialrisk-qa | QABlue |  |  |  | 
| Financial Risk | wt-rg-financialrisk-prod | ProdRed |  |  |  | 
| CMS | wt-rg-cms-qa | QABlue |  |  |  | 
| CMS | wt-rg-cms-prod | ProdRed |  |  |  | 
| API | wt-rg-api-qa | QABlue |  |  |  | 
| API | wt-rg-api-prod | ProdRed |  |  |  | 
| Data | wt-rg-data-qa | QABlue |  |  |  | 
| Data | wt-rg-data-prod | ProdRed |  |  |  | 



*****

[[category.storage-team]] 
[[category.confluence]] 
