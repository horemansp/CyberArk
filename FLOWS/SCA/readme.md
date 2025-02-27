# SCA related flows
## SCA on demand request approval with teams webhook
Instructions
- Import both flows ```SCA Ondemand-Teams```and ```SCA Ondemand-Teams-Approval-Process```
- Change the custom values for the ```SCA Ondemand-Teams`` flow
  - Update the value for your ```tenantId``` prefix. For example if your tenant prefix is "acme" then then full path to the api's will be https://acme-sca.cyberark.cloud.
    - Update the value for the custom value ```tenantId``` to "acme"
  - Update the value for ```teamsWebHook``` to your teams webhook
  - Updat the value for ```flows-sca-validation``` to the API link of the second flow you have imported ```SCA Ondemand-Teams-Approval-Process```
 
- For both flows update the autorization for the CyberArk related endpoint calls to your authorization towards CyberArk Identity
 
For the flows authorization use for the ```tokenUrl``` https://ABC1234.id.cyberark.cloud/oauth2/platformtoken to aquire a token
