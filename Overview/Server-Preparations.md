
#  Server Preparations

When a customer of an EMP wants to charge a vehicle at a charging point of a
CPO. The customer needs to authorise at the charging point. In order to
authorise the charging process, the CPO’s system sends an
eRoamingAuthorizeStart request to Hubject. If Hubject cannot derive the EMP
from the identification data (e.g. with RFID identification), Hubject
identifies all EMPs that are under contract with the CPO and forwards the
eRoamingAuthorizeStart request to all these EMPs.

![](attachments/3626500252/3626500262.png?width=760)

So, as an EMP, if there are lots of subscriptions with CPOs, you have to be
prepared to receive many calls to your backend system from Hubject. The good
news is that, from HBS 2.0, positive responses should also lead to the
Provider ID being stored in a ProviderID<->UID mapping store. This way the
respective Provider can be identified quickly for future requests without the
need for a broadcast.


