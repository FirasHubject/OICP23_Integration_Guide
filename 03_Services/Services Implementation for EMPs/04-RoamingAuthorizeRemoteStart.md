
# eRoamingAuthorizeRemoteStart Service (EMP)

## Description

The charging process starts at the charging station when the EV driver, a
customer of the EMP, tries to authenticate using the Application as the
authentication method. To confirm the customer's subscription to an offer, the
EMP sends an authorization request to Hubject.

Explore the specific details of the [eRoamingAuthorizeRemoteStart
Service](https://hubject.github.io/oicp-emp-2.3-api-doc/#tag/eRoamingAuthorization/operation/eRoamingAuthorizeRemoteStart_v2.1)
using the linked OpenAPI. _Please note the Optional/Mandatory fields described
in the Service pertain to the fields required once HBS receives the initial
request from the EMP._

## Process Diagram
<img width="527" alt="image" src="https://github.com/FirasHubject/OICP23_Integration_Guide/assets/135227574/3a382148-1a36-4179-bbd7-01285bbb292f">


## Call / JSON Snippet - Endpoint

You can use this example to perform an AuthorizeRemoteStart to any CPO
charging station that is in the HBS platform. Adapt the example to include
your ProviderID (in the url and the body request placeholder `providerID`) and
your EVCOID (in the body request placeholder `evcoID`). In order to perform a
successful AuthorizeRemoteStart, your EMP needs to have an active subscription
in the HBS with the desired CPO.

_Please note: the SessionID is an optional field in the initial request sent
to Hubject, however, it is not required to fill since Hubject assigns the
SessionID once request is received by the EMP._

    
    
    curl --location 'https://service-qa.hubject.com/api/oicp/charging/v21/providers/{{providerID}}/authorize-remote/start' \
    --header 'Content-Type: application/json' \
    --data '{
    	"ProviderID":"{{providerID}}",
    	"EvseID":"DE*ICE*E0000TEST*6",
    	"Identification":{
    		"RemoteIdentification":{
    			"EvcoID":"{{evcoID}}""
    			}
    		}
    	}'

## Response / JSON Snippet - Endpoint

    
    
    {
        "Result": true,
        "StatusCode": {
            "Code": "000",
            "Description": "VCP Remote Start",
            "AdditionalInfo": null
        },
        "SessionID": "8d571ee6-bb6f-4b1b-b82a-318c8866b4d0",
        "CPOPartnerSessionID": null,
        "EMPPartnerSessionID": null
    }

## Error Codes

| OICP Status Codes | Description | Additional information |
| ----------------- | ----------- | ----------------------
| 000               | Success     |                        |
| Any other status code | Error   |  **Status Code Page URL** |

