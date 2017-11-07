---
# required metadata

title: Integration patterns and practices
description: This topic is intended to help architects and developers make sound design decisions when implementing integration scenarios with Microsoft Dynamics 365 for
Finance and Operations.
author: Sunil-Garg
manager: AnnBe
ms.date: 11/10/2017
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-platform
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Developer
# ms.devlang: 
ms.reviewer: margoc
ms.search.scope: Operations
# ms.tgt_pltfrm: 
# ms.custom: 
# ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: sunilg
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# Integration patterns and practices

[!include[banner](../includes/banner.md)]

This topic is intended to help architects and developers make sound design decisions when implementing integration scenarios with Microsoft Dynamics 365 for
Finance and Operations, Enterprise edition.

The topic describes:

-   Finance and Operations integration patterns
-   Integration scenarios
-   Integration solutions and best practices

It does not include technical details on how to use or set up each Finance and Operations integration pattern, or sample integration code.


## Integration Patterns Overview**

The following table lists the integration patterns available for Finance and Operations.
  ---------------------------------------------------------------------------------------------------------------------------------------------------------
  **Pattern**                     **Reference**
  ------------------------------- -------------------------------------------------------------------------------------------------------------------------
  OData                           [Odata](odata.md)

  Batch data API                  [Recurring integrations](recurring-integrations.md)
                                  
                                  [Data management API](data-management-api.md)

  Custom services                 [Services home page, Custom services](services-home-page.md#custom-services)

  Consume external web services   [Services home page, Consuming external web services](services-home-page.md#consuming-external-web-services)
  ---------------------------------------------------------------------------------------------------------------------------------------------------------

### Synchronous vs asynchronous integrations

Deciding which integration pattern to use is often based on whether you need to use synchronous or asynchronous processing. 
  
  **Term**       **Definition**
  -------------- -----------------------------------------------------------------------------------------------------------------------
  Synchronous    A blocking request and response pattern, where caller is blocked until callee is done executing and gives a response.
  Asynchronous   A non-blocking pattern, where caller submits the request and continues without waiting for a response.

Inbound patterns

  **Pattern**      **Timing**     **Batch**
  ---------------- -------------- -----------
  OData            Synchronous    No
  Batch data API   Asynchronous   Yes
  Custom service   Synchronous    No

Before comparing synchronous vs asynchronous, you should be aware that all REST and SOAP integration APIs provided by Finance
and Operations can be invoked either synchronously or asynchronously.

The following examples illustrate this point.

  []{#_Hlk495961317 .anchor}**Pattern**   **Synchronous (Programming paradigm)**   **Asynchronous (Programming paradigm)**
  --------------------------------------- ---------------------------------------- ----------------------------------------------------------------------------------------------------------------------------------------------
  OData                                   DbResourceContext.SaveChanges            DbResourceContext. SaveChangesAsync
  Custom Service                          httpRequest.GetResponse                  httpRequest.BeginGetResponse
  SOAP                                    UserSessionService.GetUserSessionInfo    UserSessionService.GetUserSessionInfoAsync
  Batch data API                          ImportFromPackage                        [BeginInvoke](https://docs.microsoft.com/en-us/dotnet/standard/asynchronous-programming-patterns/calling-synchronous-methods-asynchronously)

As shown above, one can’t draw the conclusion that when OData is used
for integration, the caller will be blocked. That is not true, because
it really depends on how the call is made.

Now that we understand the timing nature of calling these APIs, let’s
define what synchronous and asynchronous means in the context of this
integration pattern document.

OData and custom service are synchronous integration patterns because
calling these APIs results in immediate execution of business logic in
Finance and Operations. If OData is used to insert product records, the
records gets inserted immediately as part of the OData call. If custom
service is used to look up on-hand inventory, business logic is executed
immediately as part of the JSON\\SOAP call and an inventory sum number
is immediately returned.

Batch data APIs are asynchronous integration pattern because calling
these APIs results in data being imported or exported in batch mode.
Let’s take ImportFromPackage for example. Calls to ImportFromPackage can
be synchronous, however, it only schedules a batch job to import a given
data package. The scheduling job quickly returns, and the heavy lifting
is done later in a batch job. Therefore, we categorize batch data APIs
as asynchronous.

When to use batch data API
--------------------------

Batch data APIs are designed to deal with large data import\\export.
Depending on what entity is used and how much business logic is being
executed during import\\export, it is very hard to define a generic
number for what large volume is. A rule of thumb is if volume is more
than a few hundred thousand, batch data API is more than likely the
right choice for integration.

Error handling 
---------------

When using synchronous pattern, success\\failure response will be given
to the caller. For example, if OData call is used to insert sales
orders, if a sales order line has a bad reference to a product that does
not exist, caller will get a response containing error indicating the
same. It is caller’s responsibility to handle potential errors in the
response.

When using asynchronous pattern, caller will get an immediate response
for whether the scheduling call was successful. It is caller’s
responsibility to handle potential errors in the response. After
scheduling is done, data import\\export status won’t be pushed to the
caller. Caller need to poll for the result of the corresponding
import\\export process and handle errors accordingly.

**Integration Patterns**
========================

**OData**
---------

### **Scenario – OData Create and Update (Product Information)**

A manufacturer runs Finance and Operations but define and configure
their product with a third-party application hosted on-premise. They
want to move production information from their on-premise application
into Finance and Operations. When a product is defined, or changed in
the on-premise application, the end user would like to see the same
change made in Finance and Operations, and they want it real time.

### Selection thought process

-   Is there a business requirement for the integration to be real time?

    -   Yes

-   What is the peek data volume requirement?

    -   1000/hr, most of the time the volume is small. Occasionally,
        there would be bunch of new or modified production
        configurations made in a short period of time.

-   What is the frequency?

    -   Ad hoc

### Solution

This scenario is best implemented using the OData service endpoints to
create and update product information in Finance and Operations.

In Finance and Operations:

-   Discover all the entities needed for the integration

-   Make sure OData service endpoints are available for the same set of
    entities

On-premise:

-   When product information is created, or modified in the third-party
    application, corresponding OData CRUD call is made to Finance and
    Operations to integrate the same change.

### **Scenario – OData Read (Order Status)**

A company runs Dynamics 365 for Finance and Operations but have a
self-hosted customer portal where customers can check status of their
orders. Order status is maintained in Finance and Operations.

### Selection thought process

-   Is there a business requirement for the integration to be real time?

    -   Yes

-   What is the peek data volume requirement?

    -   5000/hr

-   What is the frequency?

    -   Ad hoc

### Solution

This scenario is best implemented using the OData service endpoints to
read order status from Finance and Operations.

In Finance and Operations:

-   Discover entity needed for checking order status

-   Make sure OData service endpoint is available for the same entity

From the customer portal site:

-   When customer check order status, make a real-time OData call into
    Finance and Operations to read the corresponding order and retrieve
    status from that order.

### **Scenario – OData Action (BOM Approval)**

Company runs Finance and Operations but hosts a PLM system on-premise.
The on-premise PLM system has a workflow that sends the finished BOM
information to Finance and Operations for approval.

### Selection thought process

-   Is there a business requirement for the integration to be real time?

    -   Yes

-   What is the peek data volume requirement?

    -   1000/hr

-   What is the frequency?

    -   Ad hoc

### Solution

This scenario could be implemented with OData action.

In Finance and Operations:

-   Discover entity needed for the integration

-   Make sure OData service endpoints are available for entity

-   Create an action on the entity to execute needed business logic

On-premise:

-   PLM system invokes OData action to approve BOM.

Note

-   An example of such OData action can be found in,
    BOMBillOfMaterialsHeaderEntity::approve.

**Custom service**
------------------

### **Scenario – Custom Service (On-hand Inventory Lookup)**

[]{#_Hlk478998323 .anchor}An energy company has field workers scheduling
installation jobs for heaters. This company uses Finance and Operations
for back office and a third-party SaaS for scheduling appointments. When
scheduling appointments, they need to look up inventory availability to
make sure installation parts are available for the job.

### Selection thought process

-   Is there a business requirement for the integration to be real time?

    -   Yes

-   What is the peek data volume requirement?

    -   1000/hr

-   What is the frequency?

    -   Ad hoc

### Solution

This scenario could be implemented using a custom service.

In Finance and Operations:

-   Create a custom service to calculate physical on hand inventory for
    a given item.

From scheduling application:

-   Make a real time call to custom service endpoint, either thru SOAP
    or REST, to retrieve inventory information for a given item.

### Note

-   You can see an example in Retail Real Time Services implementation
    of the same, RetailTransactionServiceInventory::inventoryLookup

-   There is also an entity available to achieve the same,
    inventorySiteOnHand. Sometimes, there are more than one possible
    ways to expose the same data\\business logic inside of Finance and
    Operations, and there is really no preference on which way is
    better. In this case, it all comes down to which way works best for
    a given scenario and which way is a developer most comfortable with.

**Batch data integration**
--------------------------

### **Scenario – Import (Sales Orders in large volume)**

A company receives large volume of sales orders from a front-end system
that runs on-premise. These orders need to be sent to Finance and
Operations periodically for processing and management.

### Selection thought process

-   Is there a business requirement for the integration to be real time?

    -   No

-   What is the peek data volume requirement?

    -   200K/hr

-   What is the frequency?

    -   Once every 5 minutes

### Solution

This scenario is best implemented with batch data APIs.

In Finance and Operations:

-   Discover entities needed for the integration

-   Make sure data management is enabled on the same set of entities

On-premise:

-   Use REST batch data API to import file into Finance and Operations.

### **Scenario – Export (Purchase Order in large volume)**

A company generates large amounts of purchase orders in Finance and
Operations and use an on-premise inventory management system to receive
products. Purchase orders need to be moved from Finance and Operations
to on-premise inventory system.

### Selection thought process

-   Is there a business requirement for the integration to be real time?

    -   No

-   What is the peek data volume requirement?

    -   300K/hr

-   What is the frequency?

    -   Once every hour

### Solution

This scenario is best implemented with batch data APIs.

In Finance and Operations:

-   Discover entities needed for the integration

-   Make sure data management is enabled on the same set of entities

-   If incremental push is required, make sure change tracking can be
    enabled on the entities.

On-premise:

-   Use REST batch data API to export file out of Finance and
    Operations.

**Call out to external web services**
-------------------------------------

### **Scenario**

It’s quite common for Finance and Operations to call out to an external
web service, hosted on-premise or by another SaaS provider. In this case
Operation acts as the integration client, which is no different than
writing an integration client in any other applications. The same set of
best practices and guidelines applies here. We are not going into this
area in detail here.

You can find a simple example of how to do this
[here](https://ax.help.dynamics.com/en/wiki/dynamics-ax-7-services-technical-concepts-guide/).

### Importance Note

-   Due to security requirements, Finance and Operations production and
    sandbox environments support only secured communication using TLS
    1.2 or above. This means the target web service endpoint Finance and
    Operations is making a call out to has to support TLS1.2 or above.
    If the target service endpoint doesn’t fulfill this requirement,
    calls from Finance and Operations will fail with an exception error
    message similar to this one, “Unable to read data from the transport
    connection: An existing connection was forcibly closed by the remote
    host.” If there is no way to modify the target service to be TLS 1.2
    or above, one can work around this by introducing a broker service
    and making a two-hop call, as illustrated by the activity diagram
    below.
