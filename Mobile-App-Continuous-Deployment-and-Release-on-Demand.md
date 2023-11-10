While the mobile app’s final destination is the public app stores (e.g. Google Play Store / Apple App Store), it is important to be able to test before deploying publicly.



Below are different levels of testing that may be used (this will primarily be applicable to non PRODuctionRed environments as listed in [[Deployment Environments|Deployment-Environments]]):


* Local developer testing


* Internal private testing (only available to specific users/devices)


* Public beta testing





Microsoft’s AppCenter allows for build and distribution of the app. The distribution could be either to specific list of people and devices, or it could be to the public app stores. Automation from GitHub is also possible such that if code is merged to a specific branch that is linked to a [[Deployment Environments|Deployment-Environments]] , it will automatically build and optionally distribute).



Below is a diagram showing how the automated process would work:



1001992623071990984791appcenter_automation.drawio11https://palota.atlassian.net/wikiappcenter_automation.drawio0730.9999999999999156.00000000000003

*****

[[category.storage-team]] 
[[category.confluence]] 
