
# eRoamingChargingNotifications End Service

## Description

The CPO can transmit 'End' ChargingNotifications which provides detailed
information of a completed charging session. The EMP relies on receiving this
notification to stay informed about the charging station's details and the
session end, which they can then relay to their EV customers.

Explore the specific details of the
[eRoamingChargingNotifications](https://hubject.github.io/oicp-cpo-2.3-api-
doc/#tag/eRoamingChargingNotifications/operation/eRoamingChargingNotifications_V1.1)
using the linked OpenAPI.

## Process Diagram

## Request

You can use this example to send a notification once the charging station
stops delivering energy to the EV. Adapt the example to include your
OperatorID (in the field placeholder `OperatorID`) and your EVSEID (in field
placeholder `EvseID`). In the `SessionID` field, use a sessionID obtained in
the response from a successful AuthoirzeStart request.

    
    
    curl --location 'https://service-qa.hubject.com/api/oicp/notificationmgmt/v11/charging-notifications' \
    --header 'Content-Type: application/json' \
    --data '{
        "CPOPartnerSessionID": "1234XYZ",
        "ChargingEnd": "2020-09-23T14:17:53.038Z",
        "ChargingStart": "2020-09-23T14:50:53.038Z",
        "ConsumedEnergy": 10,
        "EMPPartnerSessionID": "2345ABC",
        "EvseID": "{{evseID}}",
        "Identification": {
            "RFIDMifareFamilyIdentification": {
                "UID": "044A2DAA856280"
            }
        },
        "MeterValueStart": 0,
        "MeterValueEnd": 10,
        "MeterValueInBetween": {
            "meterValues": [
                0
            ]
        },
        "PartnerProductID": "AC 1",
        "PenaltyTimeStart": "2020-09-23T14:17:53.038Z",
        "OperatorID": "{{operatorID}}",
        "SessionID": "3fe7378a-238f-4cf3-bca6-de657881f8c2",
        "SessionStart": "2020-09-23T14:17:53.038Z",
    	"SessionEnd": "2020-09-23T14:50:53.038Z",
        "Type": "End"
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
| Any other status code | Error   |  **Status Code Page URL** |
  
## Best Practice

We recommend implementing the ChargingNotification Stop Service as this will
provide EMPs transparency about a charging session and simplify EMPs'
experience.

 **Please Note** : In case you have implemented PreAuthorization and do not
send a CDR with 0 consumption (drivers might be blocked by their EMPs as they
allow only one active session at once), therefore ChargingNotification Stop
becomes mandatory as this is the only way for EMPs to register that a session
is not active.



