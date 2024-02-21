
# eRoamingChargingNotifications Progress Service

## Description

The CPO can transmit 'Progress' ChargingNotifications providing information
about consumed energy values during the charging process or a completed
session. These notifications should be sent at a frequency of 5 minutes or
greater. The EMP relies on receiving these notifications to stay informed
about the charging station's details and session progress, which they can then
relay to their EV customers.

Explore the specific details of the
[eRoamingChargingNotifications](https://hubject.github.io/oicp-cpo-2.3-api-doc/#tag/eRoamingChargingNotifications/operation/eRoamingChargingNotifications_V1.1)
using the linked OpenAPI.

## Process Diagram
![image](https://github.com/FirasHubject/OICP23_Integration_Guide/assets/135227574/a88eba0b-0459-4e46-876f-3d1405339eb1)


## Request

You can use this example to send a notification during the charging process.
Adapt the example to include your OperatorID (in the field placeholder
`OperatorID`) and your EVSEID (in field placeholder `EvseID`). In the
`SessionID` field, use a sessionID obtained in the response from a successful
AuthoirzeStart request.

    
    
    curl --location 'https://service-qa.hubject.com/api/oicp/notificationmgmt/v11/charging-notifications' \
    --header 'Content-Type: application/json' \
    --data '{
        "CPOPartnerSessionID": "1234XYZ",
        "ChargingStart": "2020-09-23T14:17:53.038Z",
        "EventOccurred": "2020-09-23T14:25:53.038Z",
        "ChargingDuration": 48000,
        "ConsumedEnergyProgress": 9,
        "EMPPartnerSessionID": "2345ABC",
        "EvseID": "{{evseID}}",
        "Identification": {
            "RFIDMifareFamilyIdentification": {
                "UID": "044A2DAA856280"
            }
        },
        "MeterValueStart": 0,
        "MeterValueInBetween": {
            "meterValues": [
                9
            ]
        },
        "PartnerProductID": "AC 1",
        "OperatorID": "{{operatorID}}",
        "SessionID": "3fe7378a-238f-4cf3-bca6-de657881f8c2",
        "SessionStart": "2020-09-23T14:17:53.038Z",
        "Type": "Progress"
    }'

In the `SessionID` field, use a sessionID obtained in the response from a
successful AuthoirzeStart request.

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

We recommend implementing the ChargingNotification Progress Service as this
will provide EMPs transparency about a running charging session. This would
allow EMPs to display the charging progress to the EV driver improving
drivers' experience.


