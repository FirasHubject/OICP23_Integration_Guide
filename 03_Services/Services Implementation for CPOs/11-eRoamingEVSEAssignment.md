
#  eRoamingEVSEAssignment API

## Description

In case you need to assign EVSEs in bulk to a group, you can do so by using the EVSE assignment API.

The API works in a simple way, by asking you to provide the correct name of the network and the group, as well as the list of the EVSE IDs you want to be assigned to that very group: once this information is added to the body and you run the API, a confirmation response is provided via the API and the EVSEs you included in the call are displayed under the selected group on the network detail page.

You can run the API anytime you want, but, depending on the status of the network, it will follow specific behaviors:

If the network is in the draft, each subsequent API call will overwrite previous EVSE assignments: for example, if you initially assigned EVSE DE*12345677 to Group 1 and you run the API again, listing EVSE DE*12345677 under Group 2, the EVSE will be moved from Group 1 to Group 2.
If the network is active, you can run the API only for unassigned EVSEs and all subsequent calls will not overwrite the assignment of EVSEs to groups that you already performed.

## Process Diagram:

## Request:

You can use this example to pull EVSEIDs and POI data from the platform. Adapt
the example to include your ProviderID (in the url placeholder `providerID`).
PullEVSEData supports pagination up to 2000 records in the response. If not
size is not provided, the HBS will provide 20 records by default in the
response.

    
    
 ``` 
 curl --location 'https://service-qa.hubject.com/api/oicp/evsepush/v21/operators/{{operatorID}}/status-records' \
    --header 'Content-Type: application/json' \
    --data '{
  "NetworkName": "Network name",

  "GroupsAssignments": [
    {
      "GroupName": "Group name",

      "Evses": ["EVSEID1", "EVSEID2", "EVSEID3"]
    }
  ]
}
'
   ```
 

## Response / JSON Snippet - Endpoint:

```
{
  "NetworkName": "Network name",
  "GroupsAssignments": [
    { "GroupName": "Group name", "Evses": ["EVSEID1", "EVSEID2", "EVSEID3"] }
  ]
}
```
    
  

## Status Code
  | OICP Status Codes | Description | Additional information |
| ----------------- | ----------- | ----------------------
| 000               | Success     |                        |
| Any other status code | Error   |  **Status Code Page URL** |


## Note:

In order to be linked to tariffs, all EVSEs of a network must be assigned to a group. If one or more EVSEs are not linked to any group their price will be automatically set to zero once the service offer is activated.


