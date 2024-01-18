
# eRoamingChargeDetailRecord Service

## Description

A ChargeDetailRecord (CDR) is a request that contains all necessary
information related to the charging process such as total consumed energy,
duration of the charging session, EVSEID, and more values. With this
information, the CPO can create an invoice that will be sent to the EMP.

The CDR `MUST` be uploaded to the HBS at the moment a charging session is
finished. When the HBS receives the CDR it will be forwarded to the EMP and
the session will be closed in the HBS.

Explore the specific details of the
[eRoamingChargeDetailRecord](https://hubject.github.io/oicp-cpo-2.3-api-doc/#tag/eRoamingAuthorization/operation/eRoamingChargeDetailRecord_V2.2)
using the linked OpenAPI.

## Process Diagram

## Request

You can use this example to send a charge detail record (CDR) request. Adapt
the example to include your OperatorID (in the URL placeholder `operatorID`
and fields placeholder and `OperatorID`) and your EVSEID (in field placeholder
`EvseID`). In the `SessionID` field, use a sessionID obtained in the response
from a successful AuthoirzeStart request.

    
    
    curl --location 'https://service-qa.hubject.com/api/oicp/cdrmgmt/v22/operators/{{operatorID}}/charge-detail-record' \
    --header 'Content-Type: application/json' \
    --data '{
        "EvseID": "{{evseID}}",
        "SessionID": "3fe7378a-238f-4cf3-bca6-de657881f8c2",
        "Identification": {
            "RFIDMifareFamilyIdentification": {
                "UID": "044A2DAA856280"
            }
        },
        "PartnerProductID": "ALNS-MegaChargePlusMaster-2020-08-04",
        "SessionStart": "2023-08-04T00:29:00+01:00",
        "SessionEnd": "2023-08-04T10:59:00+01:00",
        "ChargingStart": "2023-08-04T11:00:00+01:00",
        "ChargingEnd": "2023-08-04T11:45:00+01:00",
        "ConsumedEnergy": 30.541,
        "MeterValueStart": "0.0",
        "MeterValueEnd": "30.541",
        "MeterValueInBetween": {
            "meterValues": [
                "10.123",
                "20.541"
            ]
        }
    }'

## Response

    
    
    {
        "Result": true,
        "StatusCode": {
            "Code": "000",
            "Description": "SUCCESS",
            "AdditionalInfo": null
        },
        "SessionID": null,
        "CPOPartnerSessionID": null,
        "EMPPartnerSessionID": null
    }

## Status Code

| OICP Status Codes | Description | Additional information |
| ----------------- | ----------- | ----------------------
| 000               | Success     |                        |
| Any other status code | Error   |  **Status Code Page URL** |## Best Practice

Typically, for CPOs, each CDR is transmitted to the Hubject (HBS) in near
real-time (NRT) mode within about one second of closure in the CPO backend
system. The entire process is expected to be completed within ten seconds.

 **Calibration Law:**

For operators that are required to provide in the CDR information related to
the calibration law, there are fields in the CDR that allows them to input
data related to it. For more information on how to provide calibration law
information in the CDR, you can find it the [eRoamingChargeDetailRecord
OpenAPI.](https://hubject.github.io/oicp-cpo-2.3-api-
doc/#tag/eRoamingAuthorization/operation/eRoamingChargeDetailRecord_V2.2)

