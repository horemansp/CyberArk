In this tutorial we will explain how to use the CyberArk Identity API gateway to make API calls on the local network without the need to expose those API's over the internet.<br>
The API gatgeway provides a way to make local API calls thanks to a gateway installed on the network.
We demonstrate how to authenticate to PAM-SH and retrieve a list with all safes.

```mermaid
sequenceDiagram
Flows-->>Identity: auth header X-CYBR-ACCESS-TOKEN
Identity-->>API gateway: make call to local API
API gateway-->>Local API endpoint: /path & required body or other parameters
Local API endpoint-->>API gateway: returned data
API gateway-->>Identity: returned data
Identity-->>Flows: returned data
```
