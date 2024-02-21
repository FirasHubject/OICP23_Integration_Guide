# eRoamingPullEvseStatus Service

## Description

As an EMP, you can actively retrieve EVSE data from any Hubject network
station, including all Point of Interest (POI) components, for valuable
insights through our HUB. When you send an eRoamingPullEVSEStatus request,
Hubject validates your contract for the service type and, if valid, allows you
to download EVSE status data, identifying all currently valid records from all
operators.

Explore the specific details of the [eRoamingPullEvseStatus
Service](https://hubject.github.io/oicp-emp-2.3-api-doc/#tag/eRoamingEvseStatus) using the linked OpenAPI.

## Process Diagram

<img width="507" alt="image" src="https://github.com/FirasHubject/OICP23_Integration_Guide/assets/135227574/2b24846b-54ad-479c-a1a1-6845875b891b">


## Call / JSON Snippet

You can use this example to pull the status of the EVSEIDs existing in the HBS
platform. Adapt the example to include your ProviderID (in the URL placeholder
`providerID`).

    
    
    curl --location 'https://service-qa.hubject.com/api/oicp/evsepull/v21/providers/{{providerID}}/status-records' \
    --header 'Content-Type: application/json' \
    --data '{
      "ProviderID": "{{providerID}}"
    }'

## Response / JSON Snippet

    
    
    {
        "EvseStatuses": {
            "OperatorEvseStatus": [
                {
                    "OperatorID": "DE*ABC",
                    "OperatorName": "ABC-TEST",
                    "EvseStatusRecord": [
                        {
                            "EvseID": "DE*ABC*ETEST*1",
                            "EvseStatus": "Available"
                        },
                        {
                            "EvseID": "DE*ABC*ETEST*2",
                            "EvseStatus": "Available"
                        }
                    ]
                }
            ]
        },
        "StatusCode": {
            "Code": "000",
            "Description": null,
            "AdditionalInfo": null
        }
    }

## Status Codes

| OICP Status Codes | Description | Additional information |
| ----------------- | ----------- | ----------------------
| 000               | Success     |                        |
| Any other status code | Error   |  **[Status Code Page URL](https://github.com/hubject/OICP23_Integration_Guide/blob/main/04_Definitions/OICP-status-code.md)** |
  
## Best Practices

We highly recommend pulling the EVSEStatus every 5 minutes to ensure the
latest charging status synchronizes with your systems and applications.

## Mapping OCPI to OICP

|OCPP|OCPI|OICP|
|---|---|---|
|Available|AVAILABLE|Available|
|Preparing, SuspendedEV, SuspendedEVSE|BLOCKED|Occupied|
|Charging, Finishing|CHARGING|Occupied|
||INOPERATIVE|OutOfService|
||OUTOFORDER|OutOfService|
||PLANNED|-|
||REMOVED|EvseNotFound|
|Reserved|RESERVED|Reserved|
||UNKNOWN|Unknown|


