  1. [Firas.Hachem](index.html)
  2. [FinalOICP 2.3 Integration Guide](FinalOICP-2.3-Integration-Guide_3626500097.html)
  3. [FinalServices](FinalServices_3626500498.html)
  4. [FinalServices Implementation for CPOs](FinalServices-Implementation-for-CPOs_3626500540.html)

#  Firas.Hachem : FinaleRoamingPushEvseData Service

Created by  Stefania Sau on Jan 12, 2024

# eRoamingPushEvseData Service

## Description

At Hubject, we allow you to actively upload all your EVSE data to our backend
system. This service encompasses all Point of Interest (POI) data components
for each of your charging stations, thereby delivering valuable insights to
eMobility Service Providers connecting to your charging stations through our
HUB. Explore the specific details of the [eRoamingPushEvseData
Service](https://hubject.github.io/oicp-cpo-2.3-api-
doc/#tag/eRoamingEvseData/operation/eRoamingPushEvseData_V2.3) using the
linked OpenAPI.

## Process Diagram

## Request

You can use this example to insert a new EVSE and its POI data into the
platform. Adapt the example to include your OperatorID (in the url placeholder
`operatorID` and fields placeholders `HubOperatorID` and `OperatorID`) and
your EVSEID (in field placeholder `EvseID`)

    
    
    curl --location 'https://service-qa.hubject.com/api/oicp/evsepush/v23/operators/{{operatorID}}/data-records' \
    --header 'Content-Type: application/json' \
    --data '{
    "ActionType": "insert",
    "OperatorEvseData": {
      "EvseDataRecord": [
      {
        "Accessibility": "Restricted access",
        "AccessibilityLocation": "ParkingGarage",
        "AdditionalInfo": [
          {
            "lang": "en",
            "value": "This charging station is for testing purposes"
          }
        ],
        "Address": {
            "City": "Berlin",
            "Country": "DEU",
            "HouseNum": "22",
            "PostalCode": "10829",
            "Region": "Berlin",
            "Street": "EUREF CAMPUS",
            "TimeZone": "UTC+01:00"
            },
        "AuthenticationModes": [
         "No Authentication Required"
            ],
        "CalibrationLawDataAvailability":"Local",
        "ChargingFacilities": [
          {
            "Amperage": 32,
            "Power": 22,
            "PowerType": "AC_3_PHASE",
            "Voltage":480,
            "ChargingModes": [
              "Mode_4"
              ]
           }
          ],
        "ChargingStationID": "TEST 1",
        "ChargingStationNames": [
          {
            "lang": "en",
            "value": "ABC Charging Station Test"
          },
          {
            "lang": "de",
            "value": "ABC Testladestation"
          }
        ],
        "DynamicInfoAvailable": "true",
        "EvseID": "{{evseID}}",
        "GeoChargingPointEntrance": {
          "Google": {
            "Coordinates": "52.480495 13.356465"
           }
          },
        "GeoCoordinates": {
          "Google": {
            "Coordinates": "52.480495 13.356465"
            }
          },
        "HotlinePhoneNumber": "+49123123123123",
        "HubOperatorID": "{{operatorID}}",
        "IsHubjectCompatible": true,
        "IsOpen24Hours": false,
        "MaxCapacity": 50,
        "OpeningTimes": [
          {
            "Period": [
              {
                "begin": "09:00",
                "end": "18:00"
              }
            ],
            "on": "Everyday"
          }
        ],
        "PaymentOptions": [
          "No Payment"
        ],
        "Plugs": [
          "Type 2 Outlet"
        ],
        "RenewableEnergy": true,
        "ValueAddedServices": [
          "Reservation"
        ]
       }
      ],
      "OperatorID": "{{operatorID}}",
      "OperatorName": "ABC technologies"
     }
    }'\'''

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

## Status Codes

 **OICP Status Codes**

|

 **Description**

|

 **Additional information**  
  
---|---|---  
  
000

|

Success

|  
  
Any other status code

|

Error

|

[Status Code Page](FinalOICP-status-code_3626501182.html)  
  
## Best Practice

We highly recommend providing information for all fields including optional
fields as this will benefit your [EVSE Data Score.
](https://www.hubject.com/products/evse-data-
score#:~:text=The%20EVSE%20Data%20Score%20checks,and%20provides%20an%20average%20score)Providing
additional details about your stations to EMPs not only boosts your EVSE Data
Score but also elevates your partner profile.

We strongly advise sending a **weekly** PushEvseData request using
`"ActionType": "fullLoad"`, removing charging stations that are no longer part
of your network will increase the reliability for EMPs and improve the
charging experience.

 **Calibration Law** :

  * For operators that are required to inform that their charging stations are compliant with a calibration law, it must be indicated in the field `CalibrationLawDataAvailability`. For further information, you can learn more about our [eRoamingPushEvseData OpenAPI](https://hubject.github.io/oicp-cpo-2.3-api-doc/#tag/eRoamingEvseData/operation/eRoamingPushEvseData_V2.3).

## Attachments:

![](images/icons/bullet_blue.gif)
[PushEvseData.drawio.png](attachments/3626500589/3626500603.png) (image/png)  
![](images/icons/bullet_blue.gif)
[PushEvseData.drawio](attachments/3626500589/3626500606.drawio)
(application/vnd.jgraph.mxfile)  

Document generated by Confluence on Jan 15, 2024 14:10

[Atlassian](http://www.atlassian.com/)

