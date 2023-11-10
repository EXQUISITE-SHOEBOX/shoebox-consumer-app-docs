 **Summary** A module with endpoints.

 **External API Dependency (GoodWe)** 

| HTTP Verb | Path | Function Name | 
|  --- |  --- |  --- | 
| GET | /stats/generation/last-year | GetLastYearGenerationStats | 
| GET | /stats/savings | GetSavingsStats | 
| POST | /stats/usage/period | GetUsagePeriodStats | 

Endpoints

| HTTP Verb | Path | Function Name | 
|  --- |  --- |  --- | 
| GET | /stats/generation/last-year | GetLastYearGenerationStats | 
| GET | /stats/savings | GetSavingsStats | 
| POST | /stats/usage/period | GetUsagePeriodStats | 

 _N.B.: All successful responses should return status code 200_ 

Response Payloads **_Successful responses_** 
1.  **GetLastYearGenerationStats Successful Response** 




```
{
    "name": "South Africa",
    "iso3Code": "ZAF",
    "capital": "Pretoria",
    "subregion": "Southern Africa",
    "region": "Africa",
    "population": 59308690,
    "location": {
        "lattitude": -29.0,
        "longitude": 24.0
    },
    "demonym": "South African",
    "nativeName": "South Africa",
    "numericCode": "710",
    "flag": "https://flagcdn.com/za.svg"
}
```


 **2. GetLastYearGenerationStats Successful Response** 


```json
[
    {
        "name": "South Africa",
        "iso3Code": "ZAF",
        "capital": "Pretoria",
        "subregion": "Southern Africa",
        "region": "Africa",
        "population": 59308690,
        "location": {
            "lattitude": -29.0,
            "longitude": 24.0
        },
        "demonym": "South African",
        "nativeName": "South Africa",
        "numericCode": "710",
        "flag": "https://flagcdn.com/za.svg"
    }
]] ]></ac:plain-text-body></ac:structured-macro><p /><p><strong>3. GetUsagePeriodStats  Successful Response</strong></p><ac:structured-macro ac:name="code" ac:schema-version="1" ac:macro-id="1801bdd0-bca2-43fd-94c0-6c14de216706"><ac:parameter ac:name="language">json</ac:parameter><ac:parameter ac:name="breakoutMode">full-width</ac:parameter><ac:plain-text-body><![CDATA[[
    {
        "name": "South Africa",
        "iso3Code": "ZAF",
        "capital": "Pretoria",
        "subregion": "Southern Africa",
        "region": "Africa",
        "population": 59308690,
        "location": {
            "lattitude": -29.0,
            "longitude": 24.0
        },
        "demonym": "South African",
        "nativeName": "South Africa",
        "numericCode": "710",
        "flag": "https://flagcdn.com/za.svg"
    }
]] ]></ac:plain-text-body></ac:structured-macro><p /><h4 style="text-align: center;"><em><strong><span style="color: rgb(191,38,0);">Error responses</span></strong></em></h4><p>There are two main errors that should be catered for:</p><ol><li><p><strong>Unauthorised User</strong></p></li><li><p><strong>Bad Request</strong></p></li></ol><p>The payload structure is as follows:</p><ac:structured-macro ac:name="code" ac:schema-version="1" ac:macro-id="47dddcc2-6374-4a21-9574-9dc18b87c3ef"><ac:plain-text-body><![CDATA[{
    "message": "<error-message>"
}
```


| Scenario | Error Code | Error Message Example | 
|  --- |  --- |  --- | 
| Country not found | 404 | "The country with ISO 3166 Alpha 3 code 'zar' could not be found." | 
| Continent not found | 404 | "The continent with name 'arica' could not be found." | 





*****

[[category.storage-team]] 
[[category.confluence]] 
