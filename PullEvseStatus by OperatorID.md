

#  Best Practice: PullEvseStatus by OperatorID

Created by  Stefania Sau on Jan 12, 2024

Retrieve the operational status exclusively from Electric Vehicle Service
Equipment (EVSE) belonging to Charge Point Operators (CPOs) for which you
possess a valid subscription.

 **QA**

    
    
    https://service-qa.hubject.com/api/oicp/evsepull/v21/providers/{{providerID}}/status-records-by-operator-id

**PROD**

    
    
    https://service.hubject.com/api/oicp/evsepull/v21/providers/{{providerID}}/status-records-by-
    
    
    {
        "OperatorID": [
          "{{OperatorID}}"
        ],
        "ProviderID": "{{ProviderID}}"
    }


