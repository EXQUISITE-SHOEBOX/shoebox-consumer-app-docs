This is a distilled version of the architecture that focuses on the high level logical representations of certain functionalities. A more detailed architecture diagram can be found at [[Proposed Architecture|Proposed-Architecture]] .

* [Architecture Diagram](#architecture-diagram)
* [High-level Components](#high-level-components)
  * [Wetility Omnichannel API](#wetility-omnichannel-api)
  * [Consumer Mobile App](#consumer-mobile-app)
  * [Website](#website)
  * [Other consumers/channels](#other-consumers/channels)
  * [User related Data Access Layers](#user-related-data-access-layers)
  * [Device Data related Data Access Layers](#device-data-related-data-access-layers)
    * [Device Data Sources](#device-data-sources)
  * [Communication System](#communication-system)
  * [ITSM and CRM integration](#itsm-and-crm-integration)
    * [Employee and Customer engagement tools (ITSM & CRM)](#employee-and-customer-engagement-tools-(itsm-&-crm))
  * [Document Management Integration](#document-management-integration)
    * [Document Management System](#document-management-system)
  * [Data Science/Analytics Workspace](#data-science/analytics-workspace)
    * [Data Visualisation and Business Intelligence](#data-visualisation-and-business-intelligence)
  * [Optional Digital Twins Platform](#optional-digital-twins-platform)

# Architecture Diagram


1001990984471995244551logical_architecture.drawio11https://palota.atlassian.net/wikilogical_architecture.drawio0922.4285714285712622.4285714285719noteThe Data Access Layers (DALs) will follow a microservices architecture where every DAL is fit for purpose and scoped only for the specific area it addresses.

The Data Access Layers (DALs) will follow a microservices architecture where every DAL is fit for purpose and scoped only for the specific area it addresses.


# High-level Components
Below are some high level components for the system.


## Wetility Omnichannel API
This will be the main API for Wetility (e.g. [api.wetility.co.za](http://api.wetility.co.za)). It will be versioned and sit behind a layer of API management to allow for subscription based access, tight security control and easy granular monitoring.


## Consumer Mobile App
The consumer mobile app will be a companion application for customers of Wetility. This will be the main We-X interface for users and will further allow customers to manage their accounts and raise any issues (e.g. call-outs)


## Website
The public website will be mostly geared at the general public and potential customers. As such the initial on-boarding will be greatly enabled by this platform. Once a user is onboarded, it would make sense to rather channel them towards the consumer mobile app so they can have the best user experience possible.


## Other consumers/channels
Because of the nature of the omnichannel API, other consumers or channels can also access specific parts of the API. This can, for example, used for on selling purposes. 


## User related Data Access Layers
User related DALs in this logical representation will comprise of a couple of units including:


* Customer Identity and Access Management (CIAM)


* User Data Access Layer 


* Notifications/Communication Data Access Layer



The CIAM layer will also integrate with the other DALs to ensure scoped user access (e.g. on an API level a user shouldn’t be able to run an action that results in them changing data they don’t have access to - e.g. changing another user’s details).


## Device Data related Data Access Layers
This logic representation will comprise of a couple of units including:


* Device Data DAL - e.g. SEMS data and BMS data access


* Shared Data DAL - e.g. Weather data


* Financial Data DAL  - e.g. Credit checks and cost calculators



Depending on the real-time requirements of data, device data DAL may simply proxy data from the source system. For historical data, saved data will be used. Depending on the difference of data sources, the DALs may be further broken down.


### Device Data Sources
This represents the different data sources for data. E.g. GoodWe SEMS API.


## Communication System
This will system will be controlled by workflows which will respond to specific triggers and then communicate with the user on specific channels. E.g. based on a specific trigger a payment reminder could be send by both email and push notification depending on the user’s preferences.


## ITSM and CRM integration
This will be integration and workflows that connect to the ITSM/CRM system and other related employee and customer engagement tools. These workflows will either respond to triggers from the ITSM/CRM (e.g. trigger communication system, when scheduled maintenance date is near), or they will perform actions on the ITSM/CRM (e.g. create a new ticket when a user logs an issue from the mobile app)/


### Employee and Customer engagement tools (ITSM & CRM)
This represents the actual tooling that includes the following:


* ITSM and ITAM


* CRM


* Sales Automation


* Field Services




## Document Management Integration
This is integration that will primarily respond to triggers from the document management system (e.g. SharePoint). As an example, when a specific design file is uploaded onto a specific folder, it could trigger some process on the sales automation workflow (via the ITSM/CRM integration).


### Document Management System
This is the actual document management system (DMS) where certain documents will be maintained and hosted from.


## Data Science/Analytics Workspace
This logical grouping represents a list of units including:


* The main database (a hyperscale database)


* A data lake - this will drive certain Extract Load Transform (ELT) process, particularly for device data which will need to be processed later to gain insights


* Data science and/or machine learning processes (primarily to extract insights from the data)



The data architecture will include hybrid transactional and analytical processing to meet both transactional requirements and analytical requirements.


### Data Visualisation and Business Intelligence
This will be the main interface  for business to view the outputs of data analytics and will feature different dashboards geared at the requirements (e.g. device data dashboards vs customer care dashboards that includes success rates in resolving queries).


## Optional Digital Twins Platform
This is the proposed approach for managing particularly device to user associations. The reason this is marked as optional, is that it can be implemented in a later phase, or at least given less priority as for now it is likely that the associations are very structured and consistent, so they can be managed in standard ways in the database.





*****

[[category.storage-team]] 
[[category.confluence]] 
