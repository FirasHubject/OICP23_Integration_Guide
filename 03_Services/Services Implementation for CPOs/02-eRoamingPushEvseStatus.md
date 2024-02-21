# eRoamingPushEvseStatus Service

## Description

EMPs must know what the status of your charging stations in order to deliver
great charging experiences to drivers. For example, your charging stations
could be available, occupied or out of service. The status of your charging
stations must be up to date at all times. When the status of your charging
station changes, you must update the status on the Hubject platform. Failure
to do so can lead to EMPs not utilising your charging stations.

You can push the status of your charging stations through the
eRoamingPushEvseStatus service.

Explore the specific details of the [eRoamingPushEvseStatus
Service](https://hubject.github.io/oicp-cpo-2.3-api-doc/#tag/eRoamingEvseStatus) using the linked OpenAPI.

## Process Diagram

![image](https://github.com/FirasHubject/OICP23_Integration_Guide/assets/135227574/2f4a044d-3c4d-4c08-83af-808164107ca7)


## Request

You can use this example to update the status of one of your charging
stations. Adapt the example to include your OperatorID (in the url placeholder
`operatorID` and field placeholder `OperatorID`) and your EVSEID (in field
placeholder `EvseID`)

    
    
    curl --location 'https://service-qa.hubject.com/api/oicp/evsepush/v21/operators/{{operatorID}}/status-records' \
    --header 'Content-Type: application/json' \
    --data '{
        "ActionType": "insert",
        "OperatorEvseStatus": {
            "EvseStatusRecord": [
                {
                    "EvseID": "{{evseID}}",
                    "EvseStatus": "Available"
                }
            ],
            "OperatorID": "{{operatorID}}",
            "OperatorName": "ABC technologies"
        }
    }'

## Response

    
    
    {
        "Result": true,
        "StatusCode": {
            "Code": "000",
            "Description": null,
            "AdditionalInfo": null
        },
        "SessionID": null,
        "CPOPartnerSessionID": null,
        "EMPPartnerSessionID": null
    }

## Status codes

| OICP Status Codes | Description | Additional information |
| ----------------- | ----------- | ----------------------
| 000               | Success     |                        |
| Any other status code | Error   |  **[Status Code Page URL](https://github.com/hubject/OICP23_Integration_Guide/blob/main/04_Definitions/OICP-status-code.md)** |
  
## Best practice

Status changes should be sent one at a time and not in bundles.

We strongly advise sending a **daily** PushEvseStatus request using
`"ActionType": "fullLoad"`, removing charging stations that are no longer part
of your network will increase the reliability for EMPs, and this will improve
the charging experience. Furthermore, this will synchronize the status with
the data of the charging stations

## OCPP to OICP Mapping


|OCPP|OCPI|OICP|
|---|---|---|
|Available|Available|Available|
|Occupied|Occupied|Blocked|
|Unavailable|OutOfService|Inoperative|
|Reserved|Reserved|Reserved|
|Faulted|OutOfService|Out of order|
|Preparing|Occupied|Charging|
|Charging|Occupied|Charging|
|Suspended|Occupied|Charging|
|Finishing|Occupied|Charging|
|Suspended EV|Occupied|Charging|
