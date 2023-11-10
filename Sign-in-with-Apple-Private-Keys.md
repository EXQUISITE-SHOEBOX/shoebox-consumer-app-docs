

|  **P8**  | MIGTAgEAMBMGByqGSM49AgEGCCqGSM49AwEHBHkwdwIBAQQgSu7MRsYmktciZimrvWqKd8SOijKgeJjUUXeljw9QGWigCgYIKoZIzj0DAQehRANCAARGsWGJsjW3yxQZFwVfeW5nTU23xsVTFxWKh5E7yQbBk3XyT4spq2VIFTHXmf5Iwvkf58glTG1uUdF+CuvIj1YU | 
|  **Signed Token Input**  | 
```
{
  "appleTeamId": "WQZ466VK3U",
  "appleServiceId": "energy.wetility.consumer.signinapple",
  "appleKeyId": "STFH8WKN22",
  "p8key": "MIGTAgEAMBMGByqGSM49AgEGCCqGSM49AwEHBHkwdwIBAQQgSu7MRsYmktciZimrvWqKd8SOijKgeJjUUXeljw9QGWigCgYIKoZIzj0DAQehRANCAARGsWGJsjW3yxQZFwVfeW5nTU23xsVTFxWKh5E7yQbBk3XyT4spq2VIFTHXmf5Iwvkf58glTG1uUdF+CuvIj1YU"
}
```
 | 
|  **Signed Token**  | eyJhbGciOiJFUzI1NiIsImtpZCI6IlNURkg4V0tOMjIifQ.eyJzdWIiOiJlbmVyZ3kud2V0aWxpdHkuY29uc3VtZXIuc2lnbmluYXBwbGUiLCJuYmYiOjE2Nzk1OTkxMTcsImV4cCI6MTY5NTE1MTExNywiaXNzIjoiV1FaNDY2VkszVSIsImF1ZCI6Imh0dHBzOi8vYXBwbGVpZC5hcHBsZS5jb20ifQ._Bi0gHoDCQwfijuy4bsnzDn0w73-plYgsCp7uYvbr864FxvnjD9X22H9y4Nbv3nGIBVb0zs8X5TKvWsip-jenw | 
|  **Expiry**  |  | 

Signed token reference: [https://github.com/azure-ad-b2c/samples/blob/master/policies/sign-in-with-apple/azure-function/run.csx](https://github.com/azure-ad-b2c/samples/blob/master/policies/sign-in-with-apple/azure-function/run.csx)



Important


* Sign in with Apple requires the Admin to renew their client secret every 6 months.


* You'll need to manually renew the Apple client secret if it expires and store the new value in the policy key.


* We recommend you set your own reminder within 6 months to generate a new client secret.


* Follow the guidelines how to [offer Sign in with Apple button](https://docs.microsoft.com/en-us/azure/active-directory-b2c/identity-provider-apple-id?pivots=b2c-custom-policy#customize-your-user-interface).





*****

[[category.storage-team]] 
[[category.confluence]] 
