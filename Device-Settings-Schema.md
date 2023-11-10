


# DAO

```json
{
    "partitionKey": "<device-serial-no>",
    "id": "pace_device_settings",
    "type": "pace_device_settings",
    "smartModeEnabled": true,
    "data": {
        "batterySOCMin": 50,
        "goodWePlantId": "<goodwe-plant-id>"
    }
}
```




|  **Field**  |  **Type**  |  **Description**  | 
|  --- |  --- |  --- | 
| partitionKey | string | The device serial number | 
| id | string | pace_device_settingsnoteUniqueness is partition key + id. Hence this can be a constant as it will be one settings object per partition (which is the serial number)

Uniqueness is partition key + id. Hence this can be a constant as it will be one settings object per partition (which is the serial number)

 | 
| type | string | Type of object: pace_device_settings | 
| data.batterySOCMin | string | State of Charge Minimum (linked to batterySOCUnderMinSet from GoodWe) ref: api/RemoteControl/SetBatteryDischargeParameters from GoodWe | 
| data.goodWePlantId | string | The plant id from GoodWe | 


# DTO
Path: GET device/{serialNumber}/settings




## GET

```json
{
    "serialNumber": "<device-serial-no>",
    "smartModeEnabled": true,
    "batterySOCMin": 50
}
```

## POST

```json
{
    "smartModeEnabled": false,
    "batterySOCMin": 20
}
```


This should be stored in the device container.



*****

[[category.storage-team]] 
[[category.confluence]] 
