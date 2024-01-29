
# eRoamingAuthorizeStart Service

## Description

The charging process starts at the charging station when the EV driver, a
customer of the EMP, tries to authenticate using various methods. To confirm
the customer's subscription to an offer, the CPO sends an authorization
request to Hubject.

Explore the specific details of the [eRoamingAuthorizeStart
Service](https://hubject.github.io/oicp-cpo-2.3-api-
doc/#tag/eRoamingAuthorization/operation/eRoamingAuthorizeStart_v2.1) using
the linked OpenAPI.

## Process Diagram
![image](https://github.com/FirasHubject/OICP23_Integration_Guide/assets/135227574/afd41ed6-d89c-4951-92f9-3a3c14241b2c)

## Request

You can use this example to send an authorization request. Adapt the example
to include your OperatorID (in the url placeholder `operatorID` and fields
placeholder and `OperatorID`) and your EVSEID (in field placeholder `EvseID`)

    
    
    curl --location 'https://service-qa.hubject.com/api/oicp/charging/v21/operators/{{operatorID}}/authorize/start' \
    --header 'Content-Type: application/json' \
    --data '{
      "EvseID": "{{evseID}}",
      "Identification": {
        "RFIDMifareFamilyIdentification": {
          "UID": "044A2DAA856280"
        }
      },
      "OperatorID": "{{operatorID}}"
    }'

## Response

    
    
    {
        "SessionID": "3b129fb6-c4af-476e-8bec-6e307c8e5d25",
        "CPOPartnerSessionID": null,
        "EMPPartnerSessionID": null,
        "ProviderID": "DE*ICE",
        "AuthorizationStatus": "Authorized",
        "StatusCode": {
            "Code": "000",
            "Description": null,
            "AdditionalInfo": null
        },
        "AuthorizationStopIdentifications": null
    }

## Status Code

 | OICP Status Codes | Description | Additional information |
| ----------------- | ----------- | ----------------------
| 000               | Success     |                        |
| Any other status code | Error   |  **Status Code Page URL** |

  
## Best Practice

In case you can't provide the EVSEID in your AuthorizeStart request (in case it is defined after the RFID authorization at
a charge point), we recommend sending a ChargingNotification Start request
including the EVSEID.

Sharing the EVSEID ensures transparency, helping to prevent transaction
disruptions and potential liability issues, as EMPs rely on accurate location
information to facilitate seamless charging transactions.


