


```json
{
    "partitionKey": "<aad-b2c-userid>",
    "id": "<device-serial-no>",
    "type": "user_pace_device",
    "data": {
        "nickName": "<nickname-to-be-set-by-user>",
        "inverterVendor": "GoodWe",
        "address": "<goodwe-address>",
        "goodWePlantId": "<goodwe-plant-id>",
        "municipality": "<municipality>"
        "location": {
            "lat": 0.0,
            "lng": 0.0
        }
    }
}
```




|  **Field**  |  **Type**  |  **Description**  | 
|  --- |  --- |  --- | 
| partitionKey | string | The user id | 
| id | string | The serial number of the device | 
| type | string | Type of object: user_pace_device | 
| data.nickName | string | The nickname of the device - it can be set by the user.noteIt would make sense for this to have a default value on creation e.g. "Home"

It would make sense for this to have a default value on creation e.g. "Home"

 | 
| data.inverterVendor | string | The vendor - so far it can always be GoodWe | 
| data.address | string | The address of the inverter | 
| data.municipality | string | Municipality based on the address | 
| data.goodWePlantId | string | The plant id from GoodWe | 
| location | Location | This can be the geocoded address if there is no way to directly get the lat/lng coordinates. | 

Example:


```json
{
    "partitionKey": "string",
    "id": "95048ESU208W0051",
    "type": "pace_device",
    "data": {
        "nickName": "House Carl Davis",
        "inverterVendor": "GoodWe",
        "address": "5 Steynberg Ave, Discovery, Roodepoort, 1709, South Africa",
        "municipality": "City of Johannesburg Metropolitan Municipality",
        "goodWePlantId": "7cb4d013-f013-4c9f-9661-153deba17dfb",
        "location": {
            "lat": -26.1609482,
            "lng": 27.8845396
        }
    },
    "_rid": "jz9RANyn5TkEAAAAAAAAAA==",
    "_self": "dbs/jz9RAA==/colls/jz9RANyn5Tk=/docs/jz9RANyn5TkEAAAAAAAAAA==/",
    "_etag": "\"0100902e-0000-3000-0000-6302a3360000\"",
    "_attachments": "attachments/",
    "_ts": 1661117238
}
```


These objects will be kept in sync by relying on a web hook from Freshservice that keeps track of asset changes. The device can be linked to a user by checking the requester ID from the main user account object ([[User Schema|User-Schema]]).



This document will be kept in the user collection. This is because this document is to be assigned to a user. Actual device data can be kept in the device collection



*****

[[category.storage-team]] 
[[category.confluence]] 
