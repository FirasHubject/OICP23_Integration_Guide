
# eRoamingAuthorizeRemoteStop Service

## Description

The eRoamingAuthorizeRemoteStop service allows EMPs to send a request to stop
the charging station to end the charging process. Once the EMP sends the
eRoamingAuthorizeRemoteStop, this will be received by the HBS and the request
will be forwarded to the CPO’s endpoint previously configured in the HBS
portal (you can find more information on how to set up your endpoint in the
[this article](https://support.hubject.com/hc/en-
us/articles/4403736387089-2-7-Service-type-settings)).

Once the AuthorizeRemoteStop is forwarded to the CPO, the CPO `MUST` provide
the response within a 60 seconds time frame, otherwise HBS will close the
connection with a TimeOut error.

Explore the specific details of the
[eRoamingAuthorizeRemoteStop](https://hubject.github.io/oicp-cpo-2.3-api-
doc/#tag/eRoamingAuthorization/operation/eRoamingAuthorizeRemoteStop_v2.1)
using the linked OpenAPI.

## Process Diagram

![image](https://github.com/FirasHubject/OICP23_Integration_Guide/assets/135227574/3ec558e1-8dd6-44b4-89e7-702a8038d642)

## Request to receive

Here you can see an example of a request that you will receive from Hubject as
a `POST` for an eRoamingAuthorizeRemoteStop. In order to receive a testing
request, you can use our remote testing tool in the HBS platform. You can find
more information in our [testing tool
article.](https://support.hubject.com/hc/en-us/articles/360013387818-Remote-
Testing-Tool)

    
    
    {
        "CPOPartnerSessionID": null,
        "EMPPartnerSessionID": null,
        "EvseID": "DE*ICE*I01000*6",
        "ProviderID": "DE*ICE",
        "SessionID": "58fd3918-d787-46a9-bf3d-0113b0611dbe"
    }

## Response to provide

    
    
    {
        "Result": true,
        "StatusCode": {
            "Code": "000",
            "Description": "Success",
            "AdditionalInfo": null
        },
        "SessionID": "58fd3918-d787-46a9-bf3d-0113b0611dbe",
        "CPOPartnerSessionID": null,
        "EMPPartnerSessionID": null
    }

## Status Code
| OICP Status Codes | Description | Additional information |
| ----------------- | ----------- | ----------------------
| 000               | Success     |                        |
| Any other status code | Error   |  **Status Code Page URL** |
  
## Best Practice

If an AuthorizeRemoteStop request cannot successfully be executed, we
recommend adding to the error code, also the Description by referring to the
error code list mentioned in the link **Status Code Page** to provide EMPs
with transparency and improve the charging experience.
