 **Summary** You are required to create a couple of endpoints using functions that query certain information about countries from an external API. The endpoints should have specific paths and return a response in a specific format. There should be error handling on the endpoints.

 **External API Dependency** This assessment relies on an external API from [restcountries.com](https://restcountries.com/). The API offers multiple endpoints relating to querying rich data about countries.

Please ensure that the base URL of the API is made configurable as an app setting named COUNTRIES_API_URL. As opposed to hardcoding the value in the code.

 **Endpoints** You need to create new functions covering each of the below endpoints (ensure to name the path as indicated).



| HTTP Verb | Path | Description | 
|  --- |  --- |  --- | 
| GET | /countries | List all countries | 
| GET | /countries/{iso3Code} | Return a single country using the ISO 3 code | 
| GET | /countries/{iso3Code}/borders | List all countries bordering a specific country identified by the ISO 3 code | 
| GET | /continents/{continentName}/countries/ | List all countries in a specific continent identified by its name | 

 _N.B.: All successful responses should return status code 200_ 


### Response Payloads
Successful responsesSuccessful responses will either be a single country or a list of countries (the list may be empty in some cases).

The country object that your API should return is different from the original payload from [restcountries.com](https://restcountries.com/#api-endpoints-v2-response-example). Please ensure to map fields properly.

 **Single Country Successful Response** 


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
 **List of Countries Successful Response** 

 _N.B.: In certain cases the list may be empty, most cases it will have multiple items_ 


```
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
]] ]></ac:plain-text-body></ac:structured-macro><h4>Error responses</h4><p>There are two main errors that should be catered for:</p><ol><li><p>The country could not be found (via ISO 3 code)</p></li><li><p>The contient could not be found (via continent name)</p></li></ol><p>The payload structure is as follows:</p><ac:structured-macro ac:name="code" ac:schema-version="1" ac:macro-id="d75e5b78-5a8e-4005-aad8-bf89a35037be"><ac:plain-text-body><![CDATA[{
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
