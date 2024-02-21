
#  eRoamingAuthorizeRemoteStart Service

## Description

The AuthorizationRemoteStart service allows EMPs to initiate the authorization
of a charging session via the EMP mobile app. Once the EMP sends the
eRoamingAuthorizeRemoteStart, this will be received by the HBS and the request
will be forwarded to the CPO’s endpoint previously configured in the HBS
portal (you can find more information on how to set up your endpoint in [this
article](https://support.hubject.com/hc/en-us/articles/4403736387089-2-7-Service-type-settings)).

Once the AuthorizeRemoteStart is forwarded to the CPO, the CPO `MUST` provide
the response within a 60 second time frame, otherwise HBS will close the
connection with a TimeOut error.

Explore the specific details of the
[eRoamingAuthorizeRemoteStart](https://hubject.github.io/oicp-cpo-2.3-api-doc/#tag/eRoamingAuthorization/operation/eRoamingAuthorizeRemoteStart_v2.1)
using the linked OpenAPI.

## Process Diagram

![image](https://github.com/FirasHubject/OICP23_Integration_Guide/assets/135227574/850f0c87-ffd3-40ec-9cb5-7a333ad05909)


## Request to receive

Here you can see an example of a request that you will receive from Hubject as
a `POST` for an eRoamingAuthorizeRemoteStart. In order to receive a testing
request, you can use our remote testing tool in the HBS platform. You can find
more information in our [testing tool
article.](https://support.hubject.com/hc/en-us/articles/360013387818-Remote-
Testing-Tool)

    
    
    {
        "CPOPartnerSessionID": null,
        "EMPPartnerSessionID": null,
        "EvseID": "DE*ICE*E0000TEST*9",
        "Identification": {
            "RFIDMifareFamilyIdentification": null,
            "QRCodeIdentification": null,
            "PlugAndChargeIdentification": null,
            "RemoteIdentification": {
                "EvcoID": "DE*ICE*I01000*6"
            },
            "RFIDIdentification": null
        },
        "PartnerProductID": null,
        "ProviderID": "DE*ICE",
        "SessionID": null
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
        "CPOPartnerSessionID": "1",
        "EMPPartnerSessionID": null
    }

## Status Codes
| OICP Status Codes | Description | Additional information |
| ----------------- | ----------- | ----------------------
| 000               | Success     |                        |
| Any other status code | Error   |  **[Status Code Page URL](https://github.com/hubject/OICP23_Integration_Guide/blob/main/04_Definitions/OICP-status-code.md)** |

## Best Practice

If an AuthorizeRemoteStart request cannot successfully be executed, we
recommend adding to the error code, also the Description by referring to the
error code list mentioned in the link **Status Code Page** to provide EMPs
with transparency and improve the charging experience.

