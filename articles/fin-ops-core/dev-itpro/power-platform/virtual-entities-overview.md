---
# required metadata

title: Virtual entities overview
description: Finance and Operations apps are a virtual data source in Dataverse, and enable full create, read, update, and delete (CRUD) operations from Dataverse and Microsoft Power Platform.
author: RamaKrishnamoorthy
ms.date: 05/10/2021
ms.topic: article
audience: IT Pro
ms.reviewer: sericks
ms.search.region: Global
ms.author: ramasri
ms.search.validFrom: 2021-05-31
---

# Virtual entities overview

[!include[banner](../includes/banner.md)]

**Important**

This functionality requires version 10.0.12 for Finance and Operations
apps, while service update 189 is required for Dataverse. The release
information for Dataverse is published on the [***latest version
availability
page***](https://docs.microsoft.com/en-us/business-applications-release-notes/dynamics/released-versions/dynamics-365ce#all-version-availability).

**Virtual entities for Finance and Operations apps**

Finance and Operations apps are a virtual data source in Dataverse, and
enable full create, read, update, and delete (CRUD) operations from
Dataverse and Microsoft Power Platform. By definition, the data for
virtual entities doesn't reside in Dataverse. Instead, the data
continues to reside in the application where it belongs. To enable CRUD
operations on Finance and Operations entities from Dataverse, entities
must be made available as virtual entities in Dataverse. The allows CRUD
operations to be performed from Dataverse and Microsoft Power Platform,
on data that resides in Finance and Operations apps.

All Open Data Protocol (OData) entities in Finance and Operations are
available as virtual entities in Dataverse, and therefore also in Power
Platform. Makers can now build experiences in customer engagement apps
with data directly from Finance and Operations with full CRUD capability
and without copying to Dataverse. Power Apps Portals can be used to
build external-facing websites that enable collaboration scenarios for
business processes in Finance and Operations.

**Virtual entities for core Human Resources**

Core Human Resources entities can also be virtualized like Finance and
Operations entities. For more information, see [*Core HR virtual
entities*](https://docs.microsoft.com/en-us/dynamics365/human-resources/hr-admin-integration-common-data-service-virtual-entities).

**Architecture**

Virtual entities are a Dataverse concept that is useful beyond Finance
and Operations. The following illustration shows how the Finance and
Operations provider for virtual entities is implemented. Six primary
methods are implemented by the provider. The first five methods are the
standard CRUD
operations: **Create**, **Update**, **Delete**, **Retrieve**,
and **RetrieveMultiple**. The last method, **PerformAction**, is used to
call OData actions, as described later in this topic. Calls to the
Finance and Operations Virtual Entity Data Provider (shown as "VE
Plugin" in the illustration) will cause a Secure Sockets Layer
(SSL)/Transport Layer Security (TLS) 1.2 secure web call to the
CDSVirtualEntityService web API endpoint of Finance and Operations. This
web service then converts the queries into calls to the associated
physical entities in Finance and Operations, and invokes CRUD or OData
operations on those entities. Because a Finance and Operations entity is
directly invoked in all operations, any business logic on the entity or
its backing tables is also invoked.

![Architecture of virtual entities for Finance and Operations apps](media/image1.png)

During calls, there are two points of translation from Dataverse to
Finance and Operations apps. The first point of translation occurs in
the VE Plugin, which translates concepts such as entity physical names
into Finance and Operations entity names. It also converts some
well-known concepts, such as Company references. The web service call
still uses the EntityCollection, Entity, and QueryExpression objects to
express the operations that are performed, by using the translated
entity names and concepts from the VE Plugin. Finally, the
CDSVirtualEntityAdapterService web API in Finance and Operations
completes the translation from QueryExpression to QueryBuildDataSource
and other internal Finance and Operations language constructs.

All calls between Dataverse and Finance and Operations as part of
virtual entities are done as service-to-service (S2S) calls by using the
Azure Active Directory (Azure AD) application that is specified in the
configuration. The user of this application should have access *only* to
the CDSVirtualEntityAdapterService web API and the Catalog entity,
CDSVirtualEntityListEntity. These privileges are included in the
out-of-box security role that is named CDSVirtualEntityApplication.
During the S2S calls, Dataverse provides the identity of the user in
Dataverse who is invoking the action. The CDSVirtualEntityAdapterService
web API looks up the associated user in Finance and Operations and runs
the query in the context of that user. Therefore, the S2S call doesn't
have to have explicit access to all the Finance and Operations entities.
Instead, it can rely on the privileges of the user who is invoking the
action to determine data access.

** Note**

We always recommend that you have both Finance and Operations and
Dataverse co-located in the same Azure region to ensure optimal latency
in virtual entity calls. When co-located, the virtual entity overhead is
expected to be less than 30ms per call.

Power Apps Portal can also access virtual entities. Because Power Apps
Portal authorization is based on contact records, a mapping between
contact records and Finance and Operations users is maintained in the
msdyn\_externalportalusermapping table in Dataverse. This table should
be editable only by highly privileged users in Dataverse, who have the
rights to control the security access of portal users to Finance and
Operations virtual entities. Any Finance and Operations user who is set
up for Power Apps Portal access must have the
CDSVirtualEntityAuthorizedPortalUser security role assigned, and can't
have the System administrator or Security administrator role assigned.
Regardless of the Power Apps Portal security setting that is applied to
virtual entities, the resulting query to Finance and Operations apps is
always run as the associated Finance and Operations user, and is subject
to that user's entity and row security settings. Anonymous portal access
is also supported. For information about this type of access and how it
can be done, see [*Power Apps Portal
reference*](https://docs.microsoft.com/en-us/dynamics365/fin-ops-core/dev-itpro/power-platform/power-portal-reference).
