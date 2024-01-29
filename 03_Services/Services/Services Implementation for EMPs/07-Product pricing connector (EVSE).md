# Product pricing connector (EVSE) (EMP-side)
# Flexible/Dynamic: Product pricing connector (EVSE) (EMP-side)

## Description:

Hubject offers a service allowing EMPs to access flexible and dynamic pricing
models, facilitating the download of EVSE pricing data pushed to the HBS by
CPOs. Upon receiving the EMP's request, currently valid EVSE pricing data in
the HBS for the requesting EMP is grouped by OperatorID and sent in response.

Explore the specific details of the [eRoamingPullEvsePricing
Service](https://hubject.github.io/oicp-emp-2.3-api-doc/#tag/eRoamingDynamicPricing/operation/eRoamingPullEVSEPricing_V1.0) using
the linked OpenAPI.

## Process Diagram:

![](attachments/3626501056/3626501070.png?width=760)![](attachments/3626501056/3626501073.png?width=760)

## Call / JSON Snippet - Endpoint:

You can use this example to pull a relation between the EVSEIDs and the
product defined to each one of them from a certain CPO. Adapt the example to
include your ProviderID (in the url placeholder `providerID`). PullEVSEPricing
only works with CPO’s offer that have Flexible/Dynamic as Pricing Model.

    
    
     curl --location 'https://service-qa.hubject.com/api/oicp/dynamicpricing/v10/providers/{{providerID}}/evse-pricing' \
    --header 'Content-Type: application/json' \
    --data '{
        "OperatorIDs": [
            "DE*ABC"
        ],
        "ProviderID": "{{providerID}}"
    }'

## Response / JSON Snippet - Endpoint:

    
    
    {
      "EVSEPricing": [
        {
          "EVSEPricing": [
            {
              "EvseID": "DE*ABC*ETEST1",
              "EvseIDProductList": [
                "AC 1"
              ],
              "ProviderID": "{{providerID}}"
            }
          ],
          "OperatorID": "DE*ABC",
          "OperatorName": "ABC technologies"
        }
      ],
      "StatusCode": {
        "AdditionalInfo": "Success",
        "Code": "000",
        "Description": "string"
      }
    }

## Error Codes:


| OICP Status Codes | Description | Additional information |
| ----------------- | ----------- | ----------------------
| 000               | Success     |                        |
| Any other status code | Error   |  **Status Code Page URL** |
