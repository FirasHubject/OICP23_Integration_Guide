
# Roles of the ecosystem (EMP and CPO) and how the

The two main roles in the HBS ecosystem are, on the one hand, providers of
emobility services (EMP), which want to enable EV drivers to access charging
infrastructure and, on the other hand, charge point operators (CPO), which
want to boost the capacity utilization of their charging infrastructure.

## Charge Point Operator (CPO):

In the HBS, the CPO must perform the following tasks:

  * Upload to the HBS the information about their charging infrastructure (static and dynamic data)

  * Send authorization requests initialized by the charging station (AuthorizeStart request)

  * Be able to receive remote authorizations from the HBS

  * Provide all information related to the charging process at the end of it using a charge detail record (CDR)

  * Use charging notifications to inform the status of the charging process

## eMobility service provider (EMP):

In the HBS, the EMP must perform the following tasks:

  * Get from the HBS the information about charging infrastructure that is in the HBS (static and dynamic data)

  * To receive authorize requests from the HBS and send a proper response indicating if it is authorized or not. 

  * Receive charge detail records that are sent by the CPO and forwarded by the HBS

  * Able to receive charging notifications sent by the CPO and forwarded by the HBS


