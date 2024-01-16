

# Product data (Product Pricing) (EMP-side)

# Flexible/Dynamic: Product Data (Product Pricing) (EMP-side)

## Description:

Hubject offers a service enabling EMPs to access flexible and dynamic pricing
models, facilitating the download of pricing product data. EMPs can filter
requests to differentiate pricing in currencies and customize charges based on
factors such as facility characteristics, EVSE location, and time.

Explore the specific details of the [eRoamingPullPricingProductData
Service](https://hubject.github.io/oicp-emp-2.3-api-
doc/#tag/eRoamingDynamicPricing/operation/eRoamingPullPricingProductData_V1.0)
using the linked OpenAPI.

## Process Diagram:

![](attachments/3626501026/3626501043.png?width=760)![](attachments/3626501026/3626501040.png?width=760)

## Call / JSON Snippet:

You can use this example to pull pricing information from a certain CPO. Adapt
the example to include your ProviderID (in the URL placeholder `providerID`).
PullPricingProductData only works with CPO’s offers that have a
Flexible/Dynamic Pricing Model.

    
    
    curl --location --globoff 'https://service-qa.hubject.com/api/oicp/dynamicpricing/v10/providers/{{providerID}}/pricing-products' \
    --header 'Content-Type: application/json' \
    --data '{
      "OperatorIDs": [
        "{{providerID}}"
      ]
    }'

## Response / JSON Snippet:

    
    
    {
      "EVSEPricing": [
        {
          "EVSEPricing": [
            {
              "EvseID": "DE*ABC*ETEST1",
              "EvseIDProductList": [
                "AC 1"
              ],
              "ProviderID": "DE*XYZ"
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
  
## Attachments:

![](images/icons/bullet_blue.gif) [Screenshot 2023-12-01 at
13.57.19.png](attachments/3626501026/3626501040.png) (image/png)  
![](images/icons/bullet_blue.gif) [Screenshot 2023-12-01 at
13.57.30.png](attachments/3626501026/3626501043.png) (image/png)  



