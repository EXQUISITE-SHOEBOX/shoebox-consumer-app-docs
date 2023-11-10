


# CMS




|  **Document Type**  |  **Parent**  |  **Example**  | 
|  --- |  --- |  --- | 
| VAT Types (list) |  _reference-data-repository_  | list of Vat types | 
| VAT Type |  _reference-data-repository/vat-types_  | 
```json
{
  "percentage": 0.15 
}
```
 | 
| BOQ |  |  | 
| BOQ Items |  | 
```json
{
   "name": "Li-ion battery",
   "priceExclVAT": {
   "currency": "ZAR",
   "amount": 1000
   },
   "vatType": {}
}
```
 | 
| PACE Product |  | remove pricing  add BOQ items (elements)
```json
{
  "boq": [{
  "quantity": 2,
  "boqItem": {}
  }]
}
```
 | 




# DAL



# Document (PDF)




*****

[[category.storage-team]] 
[[category.confluence]] 
