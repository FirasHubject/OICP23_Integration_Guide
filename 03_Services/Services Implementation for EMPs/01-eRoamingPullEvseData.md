# eRoamingPullEvseData Service

## Description

As an EMP, you have the capability to actively pull any EVSE within the
Hubject network to your backend system, encompassing all Point of Interest
(POI) data components for each charging station and delivering valuable
insights through our HUB.

Explore the specific details of the [eRoamingPullEvseData
Service](https://hubject.github.io/oicp-emp-2.3-api-doc/#tag/eRoamingEvseData/operation/eRoamingPullEvseData_V2.3) using the
linked OpenAPI.

## Process Diagram

<img width="530" alt="image" src="https://github.com/FirasHubject/OICP23_Integration_Guide/assets/135227574/0109b2cc-5164-4abc-9767-a18fd1e0620f">


## Call / JSON Snippet - Endpoint

You can use this example to pull EVSEIDs and POI data from the platform. Adapt
the example to include your ProviderID (in the url placeholder `providerID`).
PullEVSEData supports pagination up to 2000 records in the response. If not
size is not provided, the HBS will provide 20 records by default in the
response.

    
    
    curl --location 'https://service-qa.hubject.com/api/oicp/evsepull/v23/providers/{{providerID}}/data-records' \
    --header 'Content-Type: application/json' \
    --data '{
      
      "GeoCoordinatesResponseFormat": "Google",
    
      "ProviderID": "{{providerID}}"
      
    }'

## Response / JSON Snippet - Endpoint

    
    
    {
        "content": [
            {
                "EvseID": "DE*ABC*ETHISISTEST*1",
                "ChargingStationID": "12",
                "HardwareManufacturer": null,
                "ChargingStationImage": null,
                "SubOperatorName": null,
                "ChargingPoolID": "DE*ABC*PTest",
                "Address": {
                    "Country": "DEU",
                    "City": "Berlin",
                    "Street": "Test Street",
                    "PostalCode": "13627",
                    "HouseNum": "99",
                    "Floor": "1st",
                    "Region": null,
                    "TimeZone": null,
                    "ParkingFacility": true,
                    "ParkingSpot": null
                },
                "GeoCoordinates": {
                    "Google": {
                        "Coordinates": "12.345660 2.345670"
                    },
                    "DecimalDegree": null,
                    "DegreeMinuteSeconds": null
                },
                "Plugs": [
                    "Type 2 Outlet"
                ],
                "DynamicPowerLevel": null,
                "ChargingFacilities": [
                    {
                        "PowerType": "DC",
                        "Voltage": 480,
                        "Amperage": 32,
                        "Power": 120,
                        "ChargingModes": [
                            "Mode_3"
                        ]
                    }
                ],
                "RenewableEnergy": null,
                "EnergySource": null,
                "EnvironmentalImpact": null,
                "AuthenticationModes": [
                    "NFC RFID Classic",
                    "REMOTE",
                    "PnC"
                ],
                "MaxCapacity": 40,
                "PaymentOptions": [
                    "No Payment"
                ],
                "ValueAddedServices": [
                    "Reservation"
                ],
                "Accessibility": "Free publicly accessible",
                "AccessibilityLocation": null,
                "HotlinePhoneNumber": "+49321235123",
                "AdditionalInfo": [
                    {
                        "lang": "eng",
                        "value": "this is a test"
                    }
                ],
                "ChargingStationLocationReference": null,
                "GeoChargingPointEntrance": {
                    "Google": {
                        "Coordinates": "12.345660 2.345670"
                    },
                    "DecimalDegree": null,
                    "DegreeMinuteSeconds": null
                },
                "IsOpen24Hours": false,
                "OpeningTimes": [
                    {
                        "on": "Everyday",
                        "Period": [
                            {
                                "begin": "00:00",
                                "end": "22:00"
                            }
                        ]
                    }
                ],
                "HubOperatorID": null,
                "ClearinghouseID": "12",
                "IsHubjectCompatible": true,
                "DynamicInfoAvailable": "true",
                "deltaType": "insert",
                "lastUpdate": "2021-08-24T13:15:24+00:00",
                "CalibrationLawDataAvailability": null,
                "OperatorID": "DE*ABC",
                "OperatorName": "ABC-Test",
                "ChargingStationNames": [
                    {
                        "lang": null,
                        "value": "Teststation"
                    },
                    {
                        "lang": "en",
                        "value": "Test EVSEID"
                    }
                ]
            }
        ],
        "number": 0,
        "size": 1,
        "totalElements": 2151,
        "pageable": {
            "sort": {
                "sorted": false,
                "unsorted": true,
                "empty": true
            },
            "pageNumber": 0,
            "pageSize": 1,
            "offset": 0,
            "paged": true,
            "unpaged": false
        },
        "last": false,
        "totalPages": 2151,
        "first": true,
        "numberOfElements": 1,
        "StatusCode": {
            "Code": "000",
            "Description": null,
            "AdditionalInfo": null
        },
        "empty": false
    }

## Status Code
  | OICP Status Codes | Description | Additional information |
| ----------------- | ----------- | ----------------------
| 000               | Success     |                        |
| Any other status code | Error   |  **[Status Code Page URL](https://github.com/hubject/OICP23_Integration_Guide/blob/main/04_Definitions/OICP-status-code.md)** |


## Best Practices

We recommend pulling the EVSEData daily to have the latest charging stations
in your system. We recommend executing this request during the night for best
results.

## Mapping OCPI to OICP
|OCPI|OICP|
|---|---|
|country_code|CountryCode|
|party_id|ProviderID|
|id|ChargingStationNames|
|publish|TRUE|
|name|ChargingStationNames|
|address|Address (split in an object: Country, City, Street…)|
|city|City|
|postal_code|PostalCode|
|country|Country|
|coordinates|GeoLocation|
|parking_type|-|
|uid|-|
|evse_id| EvseID|
|status| -|
|capabilities| ValueAddedServices|
|id|ChargingStationID|
|standard|-|
|format|-|
|power_type|PowerType|
|max_voltage|MaxCapacity|
|max_amperage|-|
|tariff_ids|-|
|last_updated|lastUpdate|
|physical_reference|-|
|floor_level|Floor|![image](https://github.com/FirasHubject/OICP23_Integration_Guide/assets/135227574/fd45e96d-cbca-492b-b079-f4a56bbf844d)



