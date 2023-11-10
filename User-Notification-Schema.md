,


```json
{
    "partitionKey": "<aad-b2c-userid>",
    "id": "<unique_message_id_guid>",
    "type": "user_notification",
    "notificationCategory": "<notification_type>"
    "data": {
        "title": "Some Title",
        "message": "A message",
        "link": "<some-optional-link>"
    }
}
```




|  **Field**  |  **Type**  |  **Description**  | 
|  --- |  --- |  --- | 
| partitionKey | string | The user id | 
| id | string | A unique message identifier. | 
| type | string | Type of object: user_pace_device | 
| notificationCategory | string | Category of notification | 
| data.title | string | Title of notification  | 
| data.message | string | Long version of message | 
| data.link | string | Optional link (which can be a universal link to another part of the app) related to the notification | 

Example:


```json
{
    "partitionKey": "<aad-b2c-userid>",
    "id": "<unique_message_id_guid>",
    "type": "user_notification",
    "notificationCategory": "system"
    "data": {
        "title": "Some Title",
        "message": "A message"
    }
}
```



## Notification Categories


|  **Category**  |  **Description**  | 
|  --- |  --- | 
| plant | Plant-related notifications e.g. faults | 
| loadshedding | Loadshedding alerts from Snowflake | 
|  |  | 





*****

[[category.storage-team]] 
[[category.confluence]] 
