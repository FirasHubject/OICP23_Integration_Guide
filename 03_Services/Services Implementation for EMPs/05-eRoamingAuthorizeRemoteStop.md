

# eRoamingAuthorizeRemoteStop Service (EMP)

## Description:

The eRoamingAuthorizeRemoteStop service allows EMPs to send a request to stop
the charging station to end the charging process. Once the EMP sends the
eRoamingAuthorizeRemoteStop, this will be received by the HBS and the request
will be forwarded to the CPO’s endpoint previously configured in the HBS
portal (you can find more information on how to set up your endpoint in [this
article](https://support.hubject.com/hc/en-
us/articles/4403736387089-2-7-Service-type-settings)).

Once the AuthorizeRemoteStop is forwarded to the CPO, the CPO `MUST` provide
the response within a 60-second time frame, otherwise, HBS will close the
connection with a TimeOut error.

Explore the specific details of the [eRoamingAuthorizeRemoteStop
Service](https://hubject.github.io/oicp-emp-2.3-api-
doc/#tag/eRoamingAuthorization/operation/eRoamingAuthorizeRemoteStop_v2.1)
using the linked OpenAPI.

## Process Diagram:

## Call / JSON Snippet - Endpoint :

You can use this example to perform an AuthorizeRemoteStop to an active
charging session. Adapt the example to include your ProviderID (in the URL and
the body request placeholder `providerID`) and the session you want to stop
(in the body request placeholder `sessionID`).

    
    
    curl --location 'https://service-qa.hubject.com/api/oicp/charging/v21/providers/{{providerID}}/authorize-remote/stop' \
    --header 'Content-Type: application/json' \
    --data '{
        "EvseID": "DE*ICE*E0000TEST*6",
        "ProviderID": "{{providerID}}",
        "SessionID": "{{sessionID}}"
    }' 

## Response / JSON Snippet - Endpoint:

    
    
    {
        "Result": true,
        "StatusCode": {
            "Code": "000",
            "Description": "VCP Remote Stop",
            "AdditionalInfo": null
        },
        "SessionID": "8d571ee6-bb6f-4b1b-b82a-318c8866b4d0",
        "CPOPartnerSessionID": null,
        "EMPPartnerSessionID": null
    }

## Error Codes:

| OICP Status Codes | Description | Additional information |
| ----------------- | ----------- | ----------------------
| 000               | Success     |                        |
| Any other status code | Error   |  **Status Code Page URL** |

