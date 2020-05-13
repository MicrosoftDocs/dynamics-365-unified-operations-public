---
# required metadata

title: Power Platform overview
description: Description goes here.
author: Sunil-Garg
manager: AnnBe
ms.date: 05/20/2020
ms.topic: article
ms.prod:
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

# ms.search.form:
audience: Developer, IT Pro
# ms.devlang: 
ms.reviewer: sericks
ms.search.scope: Operations
# ms.tgt_pltfrm: 
# ms.custom: NotInToc
ms.search.region: Global
# ms.search.industry:
ms.author: sunilg
ms.search.validFrom: 2020-10-31
ms.dyn365.ops.version: 10.0.0
---

# Power Platform overview

[!include[banner](../includes/banner.md)]


Pre-requisite reading
---------------------

Understanding how Common Data Service and virtual entities work will be essential to understanding the architecture of virtual entities for Finance and Operations. The following documentation is a pre-requisite to these related topics.

| Topic                                    | Documentation                                                                                       |
|------------------------------------------|-----------------------------------------------------------------------------------------------------|
| What is Common Data Service?       | <https://docs.microsoft.com/powerapps/maker/common-data-service/data-platform-intro>          |
| Working with entities in Common Data Service             | <https://docs.microsoft.com/powerapps/maker/common-data-service/entity-overview>              |
| Working with entity relationships in Common Data Service | <https://docs.microsoft.com/powerapps/maker/common-data-service/relationships-overview>       |
| Working with virtual entities in Common Data Service     | <https://docs.microsoft.com/powerapps/maker/common-data-service/create-edit-virtual-entities> |
| Working with Power Portals               | <https://docs.microsoft.com/powerapps/maker/portals/overview>                                 |
| Working with Power Apps                  | <https://docs.microsoft.com/powerapps/maker/>                                                 |

Virtual entities for Finance and Operations
-------------------------------------------

Finance and Operations is a virtual data source in Common Data Service allowing full CRUD (Create, Read, Update, Delete) operations from Common Data Service and Power Platform. By definition of virtual entities as described in the pre-requisite reading, the data for virtual entities do not reside in Common Data Service but, it continues to reside in the application where it belongs. As a result, the CRUD operations that are enabled on the Finance and Operations entities by making them available in Common Data Service as virtual entities allows for data operations from Common Data Service and Power Platform on
data that is residing in Finance and Operations, thereby allowing direct interaction.

All OData entities in Finance and Operations are available as virtual entities in Common Data Service and thus also in the Power Platform. Makers are now able to build experiences in applications like Sales, Marketing, Customer Engagement etc. along-side with data directly from Finance and Operations with full CRUD capability. Power Portals can be used to build external facing web sites to
enable collaboration scenarios for business processes in Finance and Operations.

Architecture
------------

Virtual Entities are a Common Data Service concept useful beyond Finance and Operations. This diagram illustrates how the Finance and Operations provider for Virtual Entities is implemented. There are six primary methods implemented by the provider. The first five are the standard CRUD operations of create, update, delete, retrieve, and retrieve multiple. The last, perform action, is used for calling OData actions as described later. Calls to the Finance and Operations Virtual Entity Data Provider (shown as “VE Plugin” in the diagram) will result in a SSL/TLS1.2 secure web call to the CDSVirtualEntityService WebAPI endpoint of Finance and Operations. This web service then converts the queries into calls to the associated physical entities in Finance and Operations, invoking CRUD or OData operations on those entities. Since the Finance and Operations entity is directly invoked in all operations, any business logic on the entity or its
backing tables is also invoked.

[![Architecture](../media/fovearchitecture.png)](../media/fovearchitecture.png)

There are two points of translation from Common Data Service to Finance and Operations during calls. The first is in the VE Plugin, which translates concepts like entity physical names to Finance and Operations entity names, as well as converting some well-known concepts like Company references. The web service call still uses the EntityCollection, Entity, and QueryExpression objects to express the operations being performed, using the translated entity names and concepts from the VE Plugin. Finally, the CDSVirtualEntityAdapterService WebAPI in Finance and Operations completes the translation from QueryExpression to QueryBuildDataSource and other internal Finance and Operations language constructs.

All calls between Common Data Service and Finance and Operations as part of Virtual Entity are performed as Service-to-Service (S2S) calls using the AAD Application specified in the configuration. This application user should have access *only* to the CDSVirtualEntityAdapterService WebAPI and the Catalog Entity, CDSVirtualEntityListEntity. These privileges are included in the out-of-the-box security role named CDSVirtualEntityApplication. During these S2S calls, Common Data Service will provide the identity of the user in Common Data Service invoking the action. The
CDSVirtualEntityAdapterService will look up the associated user in Finance and Operations and run the query in the context of that user. This allows the S2S call to not have explicit access to all the Finance and Operations entities, but instead rely upon the privileges of the user invoking the action to determine data access.

Power Portal is also able to access Virtual Entities. Since Power Portal authorization is based upon the Contact record, a mapping between Contact records and Finance and Operations users is maintained in the msdyn_externalportalusermapping table in Common Data Service. This table should only be editable by highly privileged users in Common Data Service who have the rights to control security access of portal users to Finance and Operations Virtual Entities. Any Finance and Operations user specified for Portal access must have the CDSVirtualEntityAuthorizedPortalUser security role assigned and cannot have the system administrator or security administrator roles assigned. Regardless of what portal security setting is applied to Virtual Entities, the resulting query to Finance and Operations will always run as the associated Finance and Operations user, subject to that user’s entity and row security settings. Anonymous portal access is also supported which is explained in the Portal section on how this can be done. Portal is covered in a separate section.
