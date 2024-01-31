
#  Server Preparations

When a customer of an EMP wants to charge a vehicle at a charging point of a
CPO. The customer needs to authorise at the charging point. To
authorise the charging process, the CPO’s system sends an
eRoamingAuthorizeStart request to Hubject. If Hubject cannot derive the EMP
from the identification data (e.g. with RFID identification), Hubject
identifies all EMPs that are under contract with the CPO and forwards the
eRoamingAuthorizeStart request to all these EMPs.

![image](https://github.com/FirasHubject/OICP23_Integration_Guide/assets/135227574/cb014f4d-e3f5-4407-b60b-a321bbb5a0cb)


So, as an EMP, if there are lots of subscriptions with CPOs, you have to be
prepared to receive many calls to your backend system from Hubject. The good
news is that, from HBS 2.0, positive responses should also lead to the
Provider ID being stored in a ProviderID<->UID mapping store. This way the
respective Provider can be identified quickly for future requests without the
need for a broadcast.


