
#  Description and limitations of remote testing tools and VCP

## Introduction

In a real world eRoaming, there are some cases where CPO needs EMP’s and vice-
versa to perform an operation. When a CPO wants to connect to HBS system, it
must go through an onboarding process. In this process the CPO needs an EMP to
implement their operation like AuthorizeRemoteStart and same for the EMP. To
solve this problem, Hubject come up with **Remote Testing Tool** and **Virtual
Charging Point** solution.

## Remote Testing Too

 **Remote Testing Too** l is a service that works as a dummy EMP. It is
designed for the CPO. It is useful when CPO wants to test its
eRoamingAuthorizeStart requests in QA environment. To use this tool, must have
some registered EVSEIDs/ EVCOIDs.

![](attachments/3626500386/3626500402.png?width=760)

### Limitation

  * CPO can use it only for test purpose. No real EMP behind the Remote Test Tools. It may response with some fake data.

## Virtual Charging Point

 **Virtual Charging Point** is a service that works as a dummy CPO. It is
designed for the EMP partner. It is useful when EMP wants to test
authorizations, contract subscriptions, invoice management etc. on the QA
environment.

![](attachments/3626500386/3626500396.png?width=760)

### Limitation

  * EMP can use VCP only for test purpose. No real CPO behind the Virtual Charging Point. It may response with some fake data.

  * If the EMP has to test invoice management on the VCP, it’s likely that the existing service offer will need to be cancelled and replaced by one that has some actual prices in it; otherwise the generated CDRs cannot be properly rated.

