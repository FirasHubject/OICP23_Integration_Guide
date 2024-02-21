# eRoamingChargingNotifications Start Service

## Description

When the charging session commences, the CPO can forward a 'Start'
ChargingNotification to Hubject, which includes details such as ChargingStart,
MeterStartValue, EVSEID, etc. This 'Start' notification is essential for the
EMP, as it allows them to access comprehensive information about the charging
station and session, which they can then relay to their EV customers.

Explore the specific details of the
[eRoamingChargingNotifications](https://hubject.github.io/oicp-cpo-2.3-api-doc/#tag/eRoamingChargingNotifications/operation/eRoamingChargingNotifications_V1.1)
using the linked OpenAPI.

## Process Diagram
![image](https://github.com/FirasHubject/OICP23_Integration_Guide/assets/135227574/383cf8fa-79e2-46f0-b784-b96c8824354c)


## Request

You can use this example to send a notification once the a charging station
has started providing energy to the car. Adapt the example to include your
OperatorID (in the field placeholder `OperatorID`) and your EVSEID (in field
placeholder `EvseID`). In the `SessionID` field, use a sessionID obtained in
the response from a successful AuthoirzeStart request.

    
    
    curl --location 'https://service-qa.hubject.com/api/oicp/notificationmgmt/v11/charging-notifications' \
    --header 'Content-Type: application/json' \
    --data '{
        "CPOPartnerSessionID": "1234XYZ",
        "ChargingStart": "2020-09-23T14:17:53.038Z",
        "EMPPartnerSessionID": "2345ABC",
        "EvseID": "{{evseID}}",
        "Identification": {
            "RFIDMifareFamilyIdentification": {
                "UID": "044A2DAA856280"
            }
        },
        "MeterValueStart": 0,
        "PartnerProductID": "AC 1",
        "SessionID": "3fe7378a-238f-4cf3-bca6-de657881f8c2",
        "SessionStart": "2020-09-23T14:17:53.038Z",
        "OperatorID": "{{operatorID}}",
        "Type": "Start"
    }'

## Response

    
    
    {
      "CPOPartnerSessionID": "1234XYZ",
      "EMPPartnerSessionID": "2345ABC",
      "Result": true,
      "SessionID": "3fe7378a-238f-4cf3-bca6-de657881f8c2",
      "StatusCode": {
        "AdditionalInfo": "Success",
        "Code": "000",
        "Description": "Success"
      }
    }

## Status Code

| OICP Status Codes | Description | Additional information |
| ----------------- | ----------- | ----------------------
| 000               | Success     |                        |
| Any other status code | Error   |  **[Status Code Page URL](https://github.com/hubject/OICP23_Integration_Guide/blob/main/04_Definitions/OICP-status-code.md)** |

  
## Best Practice

We recommend implementing the ChargingNotification Start Service as this will
provide EMPs transparency about a charging session and simplify EMPs'
experience.


