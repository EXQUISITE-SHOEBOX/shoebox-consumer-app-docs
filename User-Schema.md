


```json
{
    "partitionKey": "<aad-b2c-userid>",
    "id": "<aad-b2c-userid>",
    "type": "user",
    "email": "<aad-b2c-email>",
    "freshsalesLeadId": 0,
    "freshserviceRequesterId": 0,
    "data": {
        "freshworksEmail": "<freshworks-email>"
    }
}
```




|  **Field**  |  **Type**  |  **Description**  | 
|  --- |  --- |  --- | 
| partitionKey | string | The AAD B2C user Id (this is set to the user id to allow for grouping of related user info) | 
| id | string | The AAD B2C user Id | 
| type | string | The type of the document which for this document type should always be user_account | 
| email | string | The AAD B2C email | 
| freshsalesLeadId | int? | Freshsales Lead ID | 
| freshserviceRequesterId | int? | Freshservice Requester ID | 
| data | Object | This is the placeholder for all non-indexed user account data. | 

Example:


```json
{
    "partitionKey": "c896af74-9a8b-4917-94b4-b74a2de1fd90",
    "id": "c896af74-9a8b-4917-94b4-b74a2de1fd90",
    "type": "user",
    "email": "kmmoyaba@gmail.com",
    "freshsalesLeadId": -1,
    "freshserviceRequesterId": -1,
    "dateCreated": "2022-08-17T21:07:05.4683125+00:00",
    "lastSignIn": "2022-08-17T21:55:29.8575836+00:00",
    "data": {
        "freshworksEmail": null
    },
    "_rid": "jz9RANyn5TkCAAAAAAAAAA==",
    "_self": "dbs/jz9RAA==/colls/jz9RANyn5Tk=/docs/jz9RANyn5TkCAAAAAAAAAA==/",
    "_etag": "\"01002d0d-0000-3000-0000-62fd63d10000\"",
    "_attachments": "attachments/",
    "_ts": 1660773329
}
```
The first creation of this document should be triggered by AAD B2C and should set at a minimum the following fields:


* partitionKey


* id


* type


* email





The Freshworks-related fields would be set via a process kicked off from Freshservice as shown below:

1002491023372491023521asset_linking.drawio11https://palota.atlassian.net/wikiasset_linking.drawio0621751

The requesters in Freshservice are created from leads in Freshsales. So we are guaranteed that once we run the Freshservice workflow we can link the Freshsales information too.



*****

[[category.storage-team]] 
[[category.confluence]] 
