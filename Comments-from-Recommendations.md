



|  **Reference**   |  **Summary**   |  **Description**   |  **Comments from Kholofelo**  |  **Comments from Luke**  | 
|  **General**   |  ** **  |  | 
|   | Requirement & Testing Specification  | ·       We need to document all the different user scenarios for each aspect of the system. This will be used to drive the development team and build out the tests which the system will be tried against. What’s the best way to do this quickly based on what we have so far?  | This process we underwent was a streamlines discovery to understand the current landscape and propose a way forward. As part of the agile way of work, what would need to be defined over and above the architectural recommendation is a more business-focused approach at features and stories. It would be part of the day to day work of the team. |  | 
|   | Component re-use   | ·       Of the existing components, what components can be re-used and what are the pros and cons of re-using them? Particularly, can we re-use the current Good-We integration.    | I think mostly the learnings can be reused, but my understanding is that the current implementation is not in a microservice format, but more of a monolithic approach. So we cannot simply extract out that code and repackage it. The learnings from the current build can however be reused which will accelerate development.  feel free to correct me here. |  | 
|   | Data Migration Plan  | ·       How will we migrate the current data over to the new system? How will we test the quality of this migration?  |  There are standard migration options e.g. from Zendesk to Freshworks ([Migrate from Zendesk App - Freshworks Marketplace](https://www.freshworks.com/apps/freshdesk/migrate_from_zendesk_app/)). Alternatively, integration workflows in Azure can be used to build any integration needed. |  | 
|   | Languages and Framework choices  | ·       How do staffing teams compare for the languages selected? ·       How do platform alternatives measure in terms of cost (minimization in short and long run) and availability of developers for selected platform? ·       What type of training is available for building internal capacity to manage, develop and maintain the proposed architecture? ·       What is the community support like for MS stack vs GCP or AWS?     | <ul><li>For the data access layers, any language can be used, but it would be best to settle on one language to make it easier to work in a team environment.

</li><li>Azure and AWS are fairly common more than GCP and as such are quite well supported. The price points for Azure and AWS are also very similar as the products (particularly PaaS)

</li><li>Both Azure and AWS offer accreditations. It is however not entirely necessary to have the accreditation.

</li><li>Azure and AWS are more common and thus more supported than GCP.

</li></ul> |  | 
|   | Proposed team set up  | ·       What is the proposed team set up to support the proposed infrastructure?  |  This is up to Wetility particularly in terms of how certain functionalities can be phased. On a very high level here are some components that can be used to drive the team compositions:<ul><li>Web front-end

</li><li>Mobile app

</li><li>Backend (API + DALs)

</li><li>Data Science and BI

</li><li>IoT / Hardware interfacing

</li><li>Customer/Employee Engagement

</li></ul> |  | 
|  **Microservices**   |  ** **  |  | 
|   | Service Implementation Concerns  | ·       What type of services will we have (REST or something faster like GRPC)? ·       May we leverage different frameworks for public facing services and private services? ·       What is the architecture of the microservices services?  ·       For each of the identified services, what endpoints or workflows will they have? ·       How will intra communication between services happen? Recommend API gateway for all incoming traffic?   |  Microservices can be implemented in various ways. Our recommendation is not the purest form of microservices but we feel will be the easiest and most maintainable. We are proposing Azure Function Apps, which are automatically scalable and can be written in various different languages. The function apps will mostly use http triggers which can be implemented in a RESTful way.As per the architecture, the function apps will be scoped to a specific functionality and interface directly with the API gateway. Since the function apps will be http triggered, they can use the very same endpoints for communication between themselves. However, we will want to as much as possible keep them isolated. |  | 
|   | Framework recommendations  | ·       What is the recommended framework for the services?   (Flask, etc)·       What are the alternatives and how do they all compare?   |  Function Apps and API gateway. This is a standard PaaS implementation which encapsulates a lot of things you would normally do manually (e.g. via Flask in python or Express in node) |  | 
|   | Thin wrapper around AD-DB  | ·       How will we manage user granular permissions and what interfaces will be used to manage the permission matrix? ·       How will we visualize these permissions? ·       Who will be responsible for managing users?  |  Since Microsoft is already used. The very same active directory can be used and similarly access will be controlled by Wetility. |  | 
|   | Public facing services and integrations  | ·       Could we have an authentication service between all our internal services and Integrations (gateway type of service)? Ideally, we don’t want our services to be exposed over the internet. ·       How will we manage webhooks for the different integrations?  |  API management will be the layer that any external party will connect to. API management further allows for controlling who has access. Webhooks can also be exposed via API management (at least the registration of webhooks) |  | 
|   | Risk of one omnichannel    | ·       Is there risk in having a single point of entry?  |  Yes, there is an inherent risk of any centralised component. However, this is standard practice and the use of an Application Gateway in front of the API management mitigates the risk gravely.  |  | 
|   | Other consumers/channels   | ·       How will we manage access of these other/consumers channels (API keys, rate limiting, permissions, blocking)  |  via API management |  | 
|   | Notifications and Communications  | ·       Can we view a history of communications sent to customers? ·       Is it possible to replay failed messages? ·       How do we cater for bulk communications? ·       Is there a dashboard to interact with this system? ·       What channels will be supported? (SMS, email, we-x to we-x)?  |  Yes. All the above is catered for, however for the dashboard, what we have proposed so far will be using the standard more developer geared dashboard. If we need to build something that is more geared for day to day usage that can also be used.The channels identified as a start are email and push notifications.We haven’t necessarily classified We-X as a communication channel as it will be sitting on a platform (e.g. mobile app or website) |  | 
|   | Separate dashboard for Wetility staff  | ·       From your assessment, would we need to build out a separate dashboard to interact with the system? We did decide we will use the CRM and other external tools to run most business functions. However, based on the architecture, the information we are storing , and some operations like permission management, we would like to get your perspective on whether we should have another frontend (dashboard) to augment the external tools.  |  I think this is something we can grow into. As a start the standard tools should be enough. A CMS might be needed at a later stage where there is a need to manage rich content or even drive marketing content. |  | 
|   | Hyperscale DB  | ·       Why a hyper scale dB instead of a dB per service? Can dB in hyperscale dBs interact? (Should they?)   | The database can be isolated by the use of containers. E.g. there could be a container for microservice which doesn’t interact with other containers. The way the services will connect to the databases will be agnostic whether or not we will create multiple databases or one database. |  | 
|   | API management layer  | ·       What does the API management layer do vs API gateway?   |  API management includes an API gateway [https://azure.microsoft.com/en-gb/services/api-management/](https://azure.microsoft.com/en-gb/services/api-management/) |  | 
|  **Infrastructure**   |  ** **  |  | 
|   | Infrastructure as code  | ·       What option are available for describing out infrastructure?  |  For Azure we are proposing bicep. See below: [[Cloud Infrastructure as Code - Wetility - Confluence (atlassian.net)|Cloud-Infrastructure-as-Code]]  There are other options available such as Terraform.  |  | 
|   | Container orchestration  | ·       Kubernetes for container orchestration?  | We aren’t proposing any containerization at the moment.  However, in future, we may look at Azure Kubernetes Cluster (AKS) for serving machine learning models. |  | 
|   | Devops Set up   | ·       What skillset is required for the devops team to build and manage these different environments?  |  I’m not sure I understand the question here.  We have elaborated on some of the devops principles here: [[DevOps - Wetility - Confluence (atlassian.net)|DevOps]] Basically, it’s a practice that will have to be taken on by the entire team including business, it’s not a specific dev team skill. |  | 
|   | these nightly jobs, where are they defined  | ·       Async vs sync   |  Azure Synapse Analytics contains pipelines which can be setup on whatever frequency would work best. These pipelines can be setup in any way we choose but are largely long-running tasks which can be monitored in real time. [Pipelines and activities - Azure Data Factory & Azure Synapse | Microsoft Docs](https://docs.microsoft.com/en-us/azure/data-factory/concepts-pipelines-activities) |  | 
|   | Code Analysis, Testing Coverage Reports  | ·       Could we include code-analysis tool and coverage baked into our devops. We would like this early on.  E.g., Sonarqube |  Yes. This falls under the CI component as described in the DevOps section. [[Mobile App Continuous Integration - Wetility - Confluence (atlassian.net)|Mobile-App-Continuous-Integration]]  I’m happy for different tools to be recommended. At the end of the day some of the decisions should come organically from the dev team. |  | 
|   | Logging  | ·       What tools are available for log aggregation and searching through logs? (e.g., Elastic Search, Kibana, Log Stash)   |  Azure Application Insights. |  | 
|   | How will we manage database changes?  | ·       How will database changes be managed? Who will be responsible for this?  |  The database we are proposing is NoSQL so it makes it easier to handle changes. Database would be managed by the development team as they arise. |  | 
|   | System Audit Logs  | ·       What's our strategy for audit logs, how may we know who did what and when and how on the system?  |  If we keep to allocating access properly (e.g. not having a generic account that everyone uses), we will get many logs by default from the cloud provider. This is one of the advantages of going the PaaS cloud-native route where we aren’t having to build everything from scratch.  |  | 
|  **Other**   |  ** **  |  | 
|   | third party interactions  | ·       For all the third-party systems (Xero, Freshdesk etc), how do they compare to alternatives in terms of available API integrations with our chosen languages? This is important as API integration is a key element of this system.    |  API integration is not language specific. Any language which can make https calls would be able to connect to the APIs. |  | 
|   | Licencing concerns  | ·       Any licencing concerns with any of the tools we will use? What are the associated costs?  |  In terms of licensing costs the main extra licensing costs that we will see are:<ul><li>Microsoft 365 (which is existing)

</li><li>Microsoft App Center

</li><li>GitHub

</li><li>SendGrid

</li><li>Freshworks

</li></ul> |  | 
|   | Cost  | ·       What is the monthly estimated cost to run this system? (Infrastructure Costs, Licencing Costs, Maintenance costs)  |  Since we are going cloud native. The main cost component will be consumption based. Some services are tiered while some strictly depend on the traffic they get. The main costs will be:<ul><li>Development Cost

</li><li>Operational Cost (Azure + other licenses)

</li></ul>Maintenance will depend on what kind of engagement you will look for. E.g. do you or will you have a technically capable team to keep everything running? |  | 



*****

[[category.storage-team]] 
[[category.confluence]] 
